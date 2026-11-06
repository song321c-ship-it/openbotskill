---
name: openbot-dashboard
description: 把 OpenBot 各團隊的產出（國際早報、數據快評、突發快評、個股快評、13F 與熱門 ETF 摘要、新標案初篩、資產配置比例）整理成一頁手機也好讀的靜態網頁，用 OpenBot 網頁託管（openbot.site）發布並定時更新同一個網址。給儀表板管家用；遇到「更新儀表板」「發布儀表板」「儀表板網址」「今天有什麼重點」時使用。網址是公開的，只放可以公開的內容。
---

# OpenBot 個人儀表板

## 一、公開範圍（最重要，每次發布前都要檢查）

OpenBot 網頁託管是**公開網址**，任何拿到網址的人都看得到。只放下面這些：

| 可以放 | 不可以放 |
|---|---|
| 國際早報、數據快評、突發快評、個股快評的重點與星等 | 持股金額、成本、損益金額、總資產 |
| 13F 重疊持股、熱門 ETF 換股摘要（公開申報資料） | 帳號、券商、銀行、身分證、電話、地址、Email |
| 新標案初篩清單（公開招標公告） | 公司資格.md 的內容（資本額、實績、人員） |
| **資產配置的類別比例與偏離（只有百分比）** | 持股.csv 的「名稱」與「金額」欄、個股持有張數 |
| 追蹤中的個股代號（公開資訊） | 任何人名（同事、客戶、家人） |

發布前做一次**隱私檢查**：把要發布的 HTML 從頭讀一次，出現「元」「萬」「NT$」「$」後面接持股或資產金額、或出現上表右欄的任何東西，就刪掉再發布。檢查結果寫進更新紀錄。

## 二、資料來源（都在 `~/OpenBot/Shared/`，只讀不改）

| 區塊 | 檔案 | 取什麼 |
|---|---|---|
| 今日重點 | 下面各區塊的 ★★★★ 以上 | 最多 5 則，一句話 |
| 國際市場 | `投資/國際早報-最新日期.md`、`投資/數據快評-最新日期.md` | 早報前 5 則標題與一句重點；最新一筆數據快評（公布值、預期、利多利空） |
| 突發快評 | `投資/突發快評-今天.md` | 依星等排，最多 5 則：星等、標題、資產影響表的「利多／利空」摘要一行 |
| 個股快評 | `投資/個股快評-今天.md` | 依星等排，最多 8 則：星等、公司（代號）、利多／利空／中性、一句理由 |
| 我的追蹤 | `投資/關注清單.md` | 追蹤中的個股代號與名稱 |
| 大師持股 | `投資/持倉/報告/` 最新的 13F 與 ETF 報告 | 被最多家同時持有的前 10 檔（名稱（代號）、家數）；本月 ETF 新增／剔除最多的 5 檔 |
| 新標案 | `標案/標案追蹤.csv` | 狀態「已初篩」且 ★★★ 以上、截止投標還沒過的，依截止日排，最多 10 筆 |
| 資產配置 | `投資/持股.csv` | **只算類別比例**：各類別金額 ÷ 總金額，四捨五入到小數 1 位；和「目標比例」相減得偏離；偏離超過 5 個百分點標紅。只輸出百分比，不輸出金額與名稱 |

找不到檔案或今天沒有資料的區塊，寫「今天沒有更新」，不要用舊資料冒充今天；舊資料要寫出日期。

## 三、網頁規格

- 一個 `index.html`，CSS 寫在檔案內，**不用任何外部程式庫或 CDN**，不用 JavaScript 也能完整顯示
- 大小 300 KB 以內（託管上限：單檔 1 MB、全站 2 MB、最多 20 個檔）
- 手機優先：單欄，寬螢幕時兩欄；字級 16px 以上
- 深淺色都清楚（用 `prefers-color-scheme`）
- 頁首寫「更新時間：YYYY-MM-DD HH:mm（台灣時間）」與「這是研究整理，不是投資建議」
- 星等用 ★ 字元；利多綠、利空紅、中性灰（同時有文字，不只靠顏色）
- 每則附原始來源連結（公告、申報、新聞原文），沒有就不附
- 檔案放在 `~/OpenBot/Shared/儀表板/site/index.html`，每次整檔覆寫

### 範本（照這個結構填內容，可以微調樣式）

```html
<!doctype html>
<html lang="zh-Hant">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="robots" content="noindex, nofollow">
<title>每日儀表板</title>
<style>
:root{--bg:#f6f7f9;--card:#fff;--fg:#1d2330;--muted:#5d6675;--line:#e3e6eb;--up:#0f7b4a;--down:#b42318;--flat:#667085;--accent:#2f5bd3}
@media (prefers-color-scheme:dark){:root{--bg:#12151b;--card:#1b1f27;--fg:#e8ebf0;--muted:#9aa3b2;--line:#2b313c;--up:#4cc38a;--down:#f97066;--flat:#98a2b3;--accent:#7c9cff}}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--fg);font:16px/1.6 "Noto Sans TC","PingFang TC","Microsoft JhengHei",sans-serif}
header,main{max-width:1100px;margin:0 auto;padding:16px}
header h1{margin:0;font-size:1.4rem}.meta{color:var(--muted);font-size:.9rem}
main{display:grid;gap:16px;grid-template-columns:1fr}@media(min-width:860px){main{grid-template-columns:1fr 1fr}}
section{background:var(--card);border:1px solid var(--line);border-radius:12px;padding:14px 16px;min-width:0}
section.wide{grid-column:1/-1}h2{font-size:1.05rem;margin:0 0 8px}
ul{margin:0;padding-left:1.1em}li{margin:6px 0}
.up{color:var(--up)}.down{color:var(--down)}.flat{color:var(--flat)}.star{letter-spacing:1px;white-space:nowrap}
table{width:100%;border-collapse:collapse;font-size:.92rem}th,td{text-align:left;padding:6px 4px;border-bottom:1px solid var(--line)}
.scroll{overflow-x:auto}a{color:var(--accent)}.empty{color:var(--muted)}
footer{max-width:1100px;margin:0 auto;padding:8px 16px 32px;color:var(--muted);font-size:.85rem}
</style>
</head>
<body>
<header>
  <h1>每日儀表板</h1>
  <div class="meta">更新時間：2026-11-07 08:00（台灣時間）｜這是研究整理，不是投資建議</div>
</header>
<main>
  <section class="wide"><h2>今日重點</h2><ul><li><span class="star">★★★★★</span> 一句話重點……</li></ul></section>
  <section><h2>國際市場</h2><ul><li>早報第 1 則……</li></ul></section>
  <section><h2>突發快評</h2><ul><li><span class="star">★★★★☆</span> 標題｜<span class="up">美股利多</span>、<span class="down">美元利空</span></li></ul></section>
  <section><h2>個股快評</h2><ul><li><span class="star">★★★★☆</span> NVIDIA（NVDA）<span class="up">利多</span>：理由一句</li></ul></section>
  <section><h2>大師持股與熱門 ETF</h2><div class="scroll"><table><tr><th>公司（代號）</th><th>持有家數</th></tr></table></div></section>
  <section><h2>新標案（★★★ 以上）</h2><div class="scroll"><table><tr><th>截止投標</th><th>機關</th><th>名稱</th><th>符合度</th></tr></table></div></section>
  <section><h2>資產配置（只有比例）</h2><div class="scroll"><table><tr><th>類別</th><th>目前</th><th>目標</th><th>偏離</th></tr></table></div></section>
  <section><h2>追蹤中的個股</h2><p>2330 台積電、NVDA NVIDIA</p></section>
</main>
<footer>資料來自各代理整理的公開資訊；每天 08:00、22:00 自動更新。</footer>
</body>
</html>
```

## 四、發布與更新

工具（OpenBot 內建網頁託管）：`openbot.list_sites`、`openbot.publish_site`、`openbot.replace_site`、`openbot.delete_site`。

1. **第一次**：只有使用者明確說「發布儀表板」時，才用 `publish_site` 發布 `~/OpenBot/Shared/儀表板/site/`；成功後把網址與網站 id 寫進 `~/OpenBot/Shared/儀表板/網址.md`
2. **之後每次更新**：讀 `網址.md`，用 `replace_site` 更新**同一個網站**（網址不變，30 天期限重新計算）；不要每次 publish 新網站（一個人最多 10 個網站）
3. 呼叫前先 `list_sites` 確認網站還在；網站不見了（過期或被刪）就停下，回報「儀表板網站已不存在，請說『發布儀表板』重新發布」，不要自己 publish
4. 使用者說「刪除儀表板」：確認後才用 `delete_site`
5. 託管工具跳出需要確認、或回報錯誤時：不要重試，回報原因，等使用者處理

## 五、更新紀錄

每次在 `~/OpenBot/Shared/儀表板/更新紀錄.md` 追加一行（讀出整檔、加一行、整檔寫回）：

```
台灣時間｜各區塊筆數（重點 N、突發 N、個股 N、標案 N…）｜隱私檢查：通過／刪除了什麼｜發布：已更新／只產生檔案／失敗原因
```

## 六、易錯點

- 把持股金額、名稱放上公開網頁：只放類別比例。
- 每次 publish 新網站：會用光 10 個名額、網址一直變；更新一律 replace。
- 用舊資料冒充今天：沒有今天的檔案就寫「今天沒有更新」或標出資料日期。
- 引用外部 CSS、字型或 JavaScript：託管只收靜態檔，範本已經全部內嵌。
- 沒有使用者明確同意就第一次發布：產生檔案可以，發布要等「發布儀表板」。
