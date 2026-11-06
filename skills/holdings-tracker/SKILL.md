---
name: holdings-tracker
description: 追蹤投資大師基金的美國 13F 持股（巴菲特波克夏、橋水、橡樹、Gotham、喜馬拉雅李錄、Pershing Square Ackman、段永平 H&H、Pabrai、Daily Journal 等）與台灣熱門前 20 大 ETF 的成分股；算出哪些個股被多家同時持有、合計與平均權重，並和上一期比對新進、出清、加碼、減碼與換股。給投資研究團隊用；遇到「13F」「大師持股」「巴菲特買了什麼」「段永平持倉」「ETF 成分股」「ETF 換股」「重疊持股」「哪些股票被很多 ETF 買」「高股息 ETF 調整成分股」時使用。只整理公開申報資料，不推薦買賣。
---

# 持倉追蹤（美國 13F＋台股熱門 ETF）

這個技能教你把公開申報的持股資料抓下來、存成固定格式的 CSV、和上一期比對，再算重疊持股。你只整理事實，不從持股推論「該買什麼」。

## 一、先講清楚的限制（每份報告開頭都要寫）

1. **13F 不是完整持股**：只申報美國 13(f) 證券的多頭部位；不含放空、現金、債券、非美國交易所的股票，也不含部分衍生性部位的細節。
2. **13F 有延遲**：期限是季末後 45 天內。看到時距離期末可能已經一個半月，經理人可能早已換股。
3. **有保密處理**：機構可以申請暫緩揭露部分持股（13F-CTR），申報封面 `isConfidentialOmitted` 為 true 時要寫出來。
4. **人和機構不同**：達利歐已不擔任橋水投資長，橋水持股不等於他個人觀點；芒格已於 2023 年過世，Daily Journal 持股只能當參考。
5. **ETF 換股多半是指數規則**：被動式 ETF 的成分股變動來自指數定期審核，不是經理人看好或看壞。主動式 ETF（台灣 2025 年起）才是經理人自己選股。
6. 這些都是**資訊不是訊號**，報告最後一句固定寫：「這是公開申報資料整理，有延遲且不完整，不是投資建議。」

## 二、美國 13F：追蹤清單與查法

### 預設追蹤的機構（CIK 為 SEC 編號，2026-11-06 查證）

| 經理人 | 申報機構（EDGAR 名稱） | CIK | 備註 |
|---|---|---|---|
| 巴菲特 | BERKSHIRE HATHAWAY INC | 0001067983 | |
| 芒格（已故） | DAILY JOURNAL CORP | 0000783412 | 只當參考 |
| 達利歐（已非投資長） | Bridgewater Associates, LP | 0001350694 | 持股數量多，以 ETF 與大型股為主 |
| 霍華·馬克斯 | OAKTREE CAPITAL MANAGEMENT LP | 0000949509 | 常有 13F-HR/A 修正申報 |
| 葛林布萊特 | Gotham Asset Management, LLC | 0001510387 | 持股檔數多 |
| 李錄 | Himalaya Capital Management LLC | 0001709323 | |
| 段永平 | H&H International Investment, LLC | 0001759760 | |
| Mohnish Pabrai | Dalal Street, LLC | 0001549575 | |
| Bill Ackman | PERSHING SQUARE INC. | 0002026053 | 2026 年起由母公司申報；舊的 Pershing Square Capital Management, L.P.（0001336528）只交 13F-NT |
| Michael Burry | Scion Asset Management, LLC | 0001649339 | **2025-09-30 期之後已不再申報**，只能看歷史資料 |

使用者可以在 `~/OpenBot/Shared/投資/持倉/追蹤清單.md` 增刪機構；新增時先用下面第 1 步確認 CIK 與名稱，查不到不要自己編 CIK。

### 查法（不需要登入）

SEC 要求程式抓取時帶 User-Agent，格式是「名稱 聯絡信箱」。用 `OpenBot holdings-tracker` 加上使用者在追蹤清單裡填的聯絡信箱；沒填就先用 `OpenBot holdings-tracker`，被擋（403）就請使用者在追蹤清單填一個信箱。每秒不要超過 10 次請求。

1. **申報清單（JSON）**：`https://data.sec.gov/submissions/CIK{10 位數 CIK}.json`
   在 `filings.recent` 裡依序取 `form`、`filingDate`、`reportDate`、`accessionNumber`、`primaryDocument`；只看 `form` 為 `13F-HR` 或 `13F-HR/A` 的。
   人看的版本：`https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK={CIK}&type=13F-HR&dateb=&owner=include&count=40`
2. **該次申報的檔案目錄**：`https://www.sec.gov/Archives/edgar/data/{CIK 去掉前導 0}/{accession 去掉連字號}/index.json`
3. **封面**：同目錄的 `primary_doc.xml`，取 `periodOfReport`、`tableEntryTotal`（持股筆數）、`tableValueTotal`（總市值）、`isConfidentialOmitted`
4. **持股表**：同目錄中 **primary_doc.xml 以外的那個 .xml**（檔名每次不同，一定要從 index.json 找，不要猜）
5. 同一期有 13F-HR/A 時：修正申報可能是「補充」（只列新增部位）或「取代」（整份重報），看封面 `amendmentType`；取代就用修正版，補充就合併。

### 13F 持股表欄位

每列一筆部位：`nameOfIssuer`（發行人）、`titleOfClass`（類別）、`cusip`、`value`（**2023 年起單位是美元**，之前是千美元）、`shrsOrPrnAmt/sshPrnamt`（股數）、`shrsOrPrnAmt/sshPrnamtType`（SH 股／PRN 本金）、`putCall`（有值代表選擇權）、`investmentDiscretion`、`votingAuthority`。

**整理規則**：
- 同一 CUSIP 可能有多列（不同投資裁量或經理人），要**加總股數與市值**後再比較
- `putCall` 有值的列另外列在「選擇權部位」，不併入持股、不算權重
- 權重 = 該部位市值 ÷ 該機構這期 13F 總市值（不含選擇權列）
- 比較前後期用**股數**判斷加減碼，不用市值（市值會隨股價變）

官方規則：SEC 13F 常見問答 https://www.sec.gov/rules-regulations/staff-guidance/frequently-asked-questions-about-form-13f ；13(f) 證券清單 https://www.sec.gov/rules-regulations/staff-guidance/official-list-section-13f-securities

## 三、台股熱門前 20 大 ETF：清單與查法

### 誰算「熱門前 20 大」

預設用**受益人數**排名（代表多少投資人持有），使用者也可以改成**資產規模**；在追蹤清單寫明用哪一種，報告也要寫。
- **證交所 e添富 ETF 篩選器**：https://www.twse.com.tw/zh/ETFortune/products 有資產規模與受益人次，可排序、可下載 CSV，每日更新。只含上市 ETF，不含上櫃債券 ETF。
- **集保結算所開放資料（股權分散表）**：https://opendata.tdcc.com.tw/getOD.ashx?id=1-5 每週更新，持股分級 17（合計）的人數可當受益人數。
- 排名每季重排一次即可，換榜時在報告寫出「新進榜／掉出榜」。

### 成分股從哪裡抓

證交所與投信投顧公會**沒有**每日統一的 ETF 全部持股頁，要到各發行投信官網：

| 例子 | 持股頁 | 備註 |
|---|---|---|
| 元大 0050 | https://www.yuantaetfs.com/product/detail/0050/ratio | 全部持股，可匯出；其他元大 ETF 把代號換掉 |
| 國泰 00878 | https://www.cathaysite.com.tw/ETF/detail/ECN?tab=etf3 | 全部持股，可匯出 |
| 群益 00919 | https://www.capitalfund.com.tw/etf/product/detail/195/portfolio | 網址用內部編號，不是 ETF 代號 |
| 群益 00982A（主動式） | https://www.capitalfund.com.tw/etf/product/detail/399/portfolio | 主動式每日公告持股 |

其他投信：從 e添富產品頁或發行投信官網找該檔的「持股權重」「投資組合」頁，**把實際打開的網址記進追蹤清單**，下次直接用。找不到全部持股時，退而用投信投顧公會每月的基金前十大投資標的 https://www.sitca.org.tw/ROC/Industry/IN2629.aspx ，並在報告標「只有前十大」。

被動式 ETF 的換股時程：臺灣指數公司技術公告 https://taiwanindex.com.tw/downloads/technical_notice （每月審核日程與結果）；臺灣 50 指數由富時與證交所編製，每年 3、6、9、12 月審核。換股報告可附上對應的審核公告。

## 四、檔案格式（固定，方便下次比對）

全部放在 `~/OpenBot/Shared/投資/持倉/`：

```
追蹤清單.md                  13F 機構（經理人｜機構｜CIK）、ETF 名單（代號｜名稱｜持股頁網址）、排名方式、聯絡信箱
13F/申報紀錄.csv             cik,機構,期間,申報日,form,accession,筆數,總市值美元,是否保密
13F/{CIK}/{期間}.csv          cusip,發行人,類別,股數,市值美元,權重,選擇權
ETF/{代號}/{資料日期}.csv     代號,名稱,權重,股數
ETF/排名-{YYYY-MM-DD}.csv     名次,代號,名稱,受益人數,規模
報告/13F-{期間}.md、報告/ETF-{YYYY-MM}.md
```

## 五、比對與重疊的算法

用 Python 算（算式寫在報告裡，不心算）。下面是參考程式，照實際檔案路徑調整：

```python
import csv, pathlib, collections
base = pathlib.Path.home() / "OpenBot/Shared/投資/持倉"

def load(p):
    with open(p, encoding="utf-8") as f:
        return {r["cusip"]: r for r in csv.DictReader(f)}

# 1) 單一機構前後期比對（用股數）
def diff(prev, cur, pct=0.10):
    out = {"新進": [], "出清": [], "加碼": [], "減碼": []}
    for k, r in cur.items():
        if k not in prev:
            out["新進"].append(r)
        else:
            a, b = float(prev[k]["股數"]), float(r["股數"])
            if a and (b - a) / a >= pct: out["加碼"].append((r, a, b))
            elif a and (a - b) / a >= pct: out["減碼"].append((r, a, b))
    out["出清"] = [r for k, r in prev.items() if k not in cur]
    return out

# 2) 多家重疊（13F 用 cusip，ETF 用股票代號）
def overlap(holdings):  # holdings: {機構或ETF: {key: row}}
    cnt = collections.defaultdict(list)
    for who, rows in holdings.items():
        for k, r in rows.items():
            cnt[k].append((who, float(r["權重"])))
    rows = [(k, len(v), sum(w for _, w in v), sum(w for _, w in v) / len(v), v) for k, v in cnt.items()]
    return sorted(rows, key=lambda x: (-x[1], -x[2]))  # 先比被幾家持有，再比合計權重
```

- **加碼／減碼門檻**：股數變動 ≥ 10% 才列（〔操作化〕，使用者可在追蹤清單改）
- **重疊比例**：被 N 家持有 ÷ 追蹤家數；另列「合計權重」與「平均權重」（只在有持有的機構間平均）
- **ETF 換股**：前後兩期成分股代號集合相減 → 新增、剔除；權重變動 ≥ 1 個百分點的另列

## 六、報告格式

```
# 13F 持倉追蹤：2026 Q2（期末 2026-06-30）
限制：13F 只含美股多頭、延遲最多 45 天…（第一節六點，精簡成三行）

## 本期已申報／未申報
| 經理人 | 機構 | 申報日 | 筆數 | 總市值（美元） | 保密 |

## 各家變動（每家最多列 10 筆，依市值排序）
### 巴菲特（BERKSHIRE HATHAWAY INC）
- 新進：…（股數、市值、權重）
- 出清：…
- 加碼／減碼：…（前期股數 → 本期股數，變動 %）

## 重疊持股（被 2 家以上持有）
| 發行人 | CUSIP | 持有家數／追蹤家數 | 持有者 | 合計權重 | 平均權重 |

資料來源：每家的 EDGAR 申報索引頁網址
這是公開申報資料整理，有延遲且不完整，不是投資建議。
```

ETF 報告同樣格式：排名（受益人數或規模）、每檔新增／剔除、權重大變動、被 N 檔同時持有的個股與合計權重、主動式 ETF 另外標出。

## 七、易錯點

- 用市值變化判斷加減碼：錯，要用股數。
- 同一 CUSIP 多列沒加總：會把同一檔股票當成多筆。
- 選擇權（putCall 有值）算進權重：錯，另外列。
- 2023 年以前的 13F 金額是千美元，跨年度比較要換算。
- 把 13F-NT 當成「沒持股」：13F-NT 代表持股由別的機構合併申報（例如 Pershing Square 改由母公司申報）。
- 被動 ETF 換股寫成「投信看好」：錯，寫「指數定期審核調整」並附公告。
- 持股表檔名用猜的：一定要從 index.json 找。
- 只有前十大資料卻算重疊比例：要標「只用前十大計算，低估重疊」。

## 八、需查證（維護者用）

- CIK 與申報機構可能改名或改由母公司申報（Pershing Square 就是例子），每季檢查一次追蹤清單。
- 各投信持股頁網址會改版；打不開時重新從投信官網找，並更新追蹤清單。
- 主動式 ETF 每日公告持股的法源條號尚未確認，目前依證交所主動式 ETF 頁的說明。
