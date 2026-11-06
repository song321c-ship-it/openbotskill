---
name: tw-official-sources
description: 台灣官方資料來源清單與查法：政府資料開放平臺、主計總處（物價、薪資）、內政部（實價登錄、人口統計）、勞動部、衛福部、健保署、教育部、考選部、經濟部商工登記、財政部（稅務、統一發票）、金管會、中央銀行、氣象署、全國法規資料庫、司法院裁判書、消保會、公平會、各縣市政府，附引用規則。給所有團隊共用；遇到「官方資料」「政府統計」「查法條」「判決」「實價登錄」「公司登記」「統一編號」「CPI」「薪資中位數」「發票中獎」「出處」「附來源」時使用。
---

# 台灣官方資料來源與引用規則

這個技能告訴你：要查台灣的公開資料時，**去哪個官方頁、怎麼查、多久更新、哪裡容易錯**，以及寫報告時**怎麼附出處**。

所有網址都在 2026-11 實際打開確認過。政府網站常改版，打不開時先到該機關首頁用站內搜尋找同名頁面，不要改用轉貼站。

## 一、引用規則（每個團隊都要遵守）

1. **連結要是內容所在的那一頁**：寫 CPI 就附 CPI 新聞稿或統計表頁，不要只附 https://www.stat.gov.tw/ 首頁。查詢型頁面（例如商工登記、裁判書）沒有固定網址時，附查詢頁網址＋寫出查詢條件與查詢日期，例如「經濟部商工登記公示資料查詢，以統一編號 12345678 查詢，2026-11-06」。
2. **法條一定附全國法規資料庫的條文頁**，格式：
   `https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=法規代碼&flno=條號`
   例：著作權法第 9 條 → https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=J0070017&flno=9
   條號有「之一」時 flno 寫成 `31-1`，例：職業訓練法第 31 條之 1 → https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=N0080001&flno=31-1 。全文頁是 `LawAll.aspx?pcode=法規代碼`，沿革是 `LawHistory.aspx?pcode=法規代碼`。
3. **每個數字附：來源機關、頁面網址、資料期間、查詢日期**。例：「115 年 9 月 CPI 年增率 X%（主計總處新聞稿，網址，查詢 2026-11-06）」。
4. **查不到就寫「未查證」**，不要憑記憶補數字、補條號、補金額。查到但不確定是否最新，寫「需查證（原因）」。
5. **民國年與西元年**：西元年＝民國年＋1911。官方頁多用民國年，報告裡兩者並列，例如「115 年（2026 年）」。
6. **不要寫死會變的數字**：最低工資、保費費率、補助金額、稅率級距、考試日期都要每次重查，報告寫「依查詢當日官方頁」。
7. **不給法律、醫療、稅務、投資結論**：可以整理官方規定與資料，個案判斷要寫「請洽律師、會計師、醫師或主管機關」。

## 二、來源清單（網址＋查法）

### 1. 綜合入口

**政府資料開放平臺**（數位發展部）
- 網址：https://data.gov.tw/
- 能查：各機關開放資料集（CSV、JSON、XML 等），幾乎所有部會的統計原始檔
- 怎麼查：首頁輸入關鍵字 → 或用「進階搜尋」指定提供機關、檔案格式 → 打開資料集頁看「提供機關」「更新頻率」「授權方式」「詮釋資料更新時間」→ 下載
- 更新頻率：每個資料集不同，看資料集頁的「更新頻率」欄
- 注意：授權多為「政府資料開放授權條款」（https://data.gov.tw/license），引用要標示提供機關。下載前先看「詮釋資料更新時間」，舊資料集可能已停更；有「預計下架資料集」專區

**我的E政府**（生活服務入口）
- 網址：https://www.gov.tw/
- 能查：依人生大事（出生、就學、就業、就養、終老）整理的申辦服務說明
- 注意：只是導覽頁，引用時要追到實際主管機關的頁面

**行政院公報資訊網**
- 網址：https://gazette.nat.gov.tw/
- 能查：法規命令、行政規則、公告的正式刊登文本與日期
- 用途：確認某項公告「何時發布、何時生效」

### 2. 主計總處（中華民國統計資訊網）

- 首頁：https://www.stat.gov.tw/
- **物價指數專區**：https://www.stat.gov.tw/cl.aspx?n=2663
  - 新聞稿（每月 CPI 發布）：https://www.stat.gov.tw/News.aspx?n=2668&sms=10980
  - 統計表：https://www.stat.gov.tw/cp.aspx?n=2665
  - CPI 年增率指標頁：https://www.stat.gov.tw/Point.aspx?sid=t.2&n=3581&sms=11480
- **薪資及生產力統計**：https://www.stat.gov.tw/cl.aspx?n=2712
  - 薪情平臺（可查行業、性別、月／年資料）：https://earnings.dgbas.gov.tw/
  - 查詢系統：https://earnings.dgbas.gov.tw/query_payroll_C.aspx
  - 薪資中位數及分布統計：https://www.stat.gov.tw/cl.aspx?n=2715
- **總體統計資料庫**：https://www.stat.gov.tw/cl.aspx?n=3442 （資料庫本體 https://nstatdb.dgbas.gov.tw/dgbasall/webMain.aspx?k=dgmain ）
- **縣市重要統計指標查詢系統**：https://winstacity.dgbas.gov.tw/DgbasWeb/ZWeb/StateFile_ZWeb.aspx
- **統計發布訊息**：https://www.stat.gov.tw/cl.aspx?n=3560
- 更新頻率：CPI、薪資都是月資料；薪資中位數是年資料。確切發布日看新聞稿日期或統計發布訊息（每月發布日需查證，不要自己推）
- 注意：
  - 「總薪資」含非經常性薪資（年終、績效獎金），「經常性薪資」不含，兩者不要混用
  - 「平均」和「中位數」差很多，報告要寫清楚用的是哪一個
  - 新聞稿中的數字可能在下個月修正，引用要寫資料期間與發布日

### 3. 內政部

**不動產交易實價查詢服務網**
- 網址：https://lvr.land.moi.gov.tw/
- 能查：買賣、租賃、預售屋的成交價、單價、面積、樓層、交易日期
- 怎麼查：選縣市、行政區 → 選交易類別（買賣／預售屋／租賃）→ 設定期間、建物型態 → 查詢；可切換地圖或列表
- 開放資料批次下載：https://plvr.land.moi.gov.tw/DownloadOpenData （頁面說明當期資料於**每月 1 日、11 日、21 日**公布）
- 法源：平均地權條例第 47 條 https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=D0060009&flno=47
- 注意：
  - 門牌是區段化（例如 1～30 號），不是精確地址
  - 「備註」欄有親友交易、含車位、毛胚屋等特殊情況，算行情前要排除
  - 車位價是否拆開計算會影響單價；揭露有時間落差，不等於即時行情

**戶政司人口統計**
- 人口統計資料：https://www.ris.gov.tw/app/portal/346
- 人口統計資料庫導覽：https://www.ris.gov.tw/app/portal/674
- 人口資料 GIS 地圖：https://www.ris.gov.tw/app/portal/348
- 能查：戶籍人口數、出生、死亡、結婚、離婚，依縣市／鄉鎮市區／村里
- 更新頻率：月資料為主（以頁面標示為準）
- 注意：這是**戶籍**人口，不等於實際居住人口

### 4. 勞動部

- 首頁：https://www.mol.gov.tw/
- **勞動統計專網**：https://www.mol.gov.tw/1607/71771/normalnodelist
  - 統計查詢：https://www.mol.gov.tw/1607/71771/71799/nodelist
  - 勞動統計月報：https://www.mol.gov.tw/1607/71771/72772/72774/statisticalReportList
  - 職類別薪資調查：https://www.mol.gov.tw/1607/71771/72867/72920/lpsimplelist
- **勞動法令查詢系統**（函釋、解釋令）：https://laws.mol.gov.tw/
- **勞動部勞工保險局**（勞保、就保、勞退、投保薪資分級表）：https://www.bli.gov.tw/
- 常用法條：勞動基準法 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=N0030001 、最低工資法 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=N0030028 、勞工退休金條例 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=N0030020
- 注意：
  - 最低工資金額每年由審議會決定，**一律去勞動部官網查當年度公告**，不要寫死
  - 主計總處和勞動部的薪資統計口徑不同（調查對象、定義），比較時要註明來源
  - 函釋可能被新函釋取代，引用要看發文日期

### 5. 衛生福利部、健保署

**衛生福利部**
- 首頁：https://www.mohw.gov.tw/
- 統計處：https://dep.mohw.gov.tw/DOS/mp-113.html （死因統計、醫療統計、社會福利統計）
- 法令規章：https://www.mohw.gov.tw/np-33-1.html
- 醫事查詢系統（醫事人員、醫事機構、懲戒決議書）：https://ma.mohw.gov.tw/Accessibility
- 長照專區（1966）：https://1966.gov.tw/

**中央健康保險署**
- 首頁：https://www.nhi.gov.tw/ch/mp-1.html （自動抓取會被安全驗證擋下，要用瀏覽器開）
- 健保特約醫事機構查詢：https://info.nhi.gov.tw/INAE1000/INAE1000S01 （依縣市、鄉鎮、院所層級、加入的計畫查詢）
- 能查：投保、保險費計算、補充保險費、院所查詢、藥品與特材給付、部分負擔
- 法源：全民健康保險法 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=L0060001
- 注意：保險費率、投保金額分級表、部分負擔金額會調整，每次都要查健保署當期頁面。**不做醫療建議**，就醫判斷請洽醫師

### 6. 教育部

- 首頁：https://www.edu.tw/
- 教育部統計處：https://depart.moe.edu.tw/ED4500/ （學校數、學生數、畢業生）
- 學校基本統計資訊：https://depart.moe.edu.tw/ED4500/News.aspx?n=5A930C32CC6C3818&sms=91B3AAE8C6388B96
- 注意：學年度（8 月到隔年 7 月）和曆年不同，引用要寫「XXX 學年度」

### 7. 考選部（國家考試）

- 首頁：https://wwwc.moex.gov.tw/main/home/wfrmHome.aspx
- 考試期日計畫表：https://wwwc.moex.gov.tw/main/exam/wFrmExamInformation.aspx?menu_id=145
- 考畢試題（含測驗題答案）：https://wwwq.moex.gov.tw/exam/wFrmExamQandASearch.aspx
- 詳細查法見 `tw-exam-license` 技能

### 8. 經濟部商工登記

**商工登記公示資料查詢**
- 網址：https://findbiz.nat.gov.tw/fts/query/QueryBar/queryInit.do
- 能查：公司、分公司、商業（行號）、工廠、有限合夥的登記狀態、統一編號、代表人、董監事、資本額、所營事業、地址
- 怎麼查：選「名稱或統一編號」→ 勾資料種類（公司／商業等）→ 登記現況選「全部顯示」才看得到解散、廢止的 → 查詢 → 點進詳細頁
- 注意：頁面有安全驗證，自動抓取常被擋，要用瀏覽器；「核准設立」不代表目前有營業，要看登記現況與最後核准變更日期

**商工行政資料開放平臺**（批次資料與 API）
- 網址：https://data.gcis.nat.gov.tw/
- 用途：大量查公司登記基本資料、董監事資料；使用前看平臺的使用規範

### 9. 財政部（稅務、統一發票）

- 財政部首頁：https://www.mof.gov.tw/
- **財政部稅務入口網**：https://www.etax.nat.gov.tw/ （綜所稅、營業稅、房地合一、稅額試算、書表下載）
- **稅籍登記資料公示查詢**：https://www.etax.nat.gov.tw/etwmain/etw113w1/ban/query （依統一編號、名稱、地址查營業人稅籍）
  - 注意：這頁有**圖形驗證碼**，代理不能代填驗證碼；請改用商工登記查詢，或請使用者自己查
- **統一發票中獎號碼**：https://www.etax.nat.gov.tw/etwmain/etw183w （也可從 https://invoice.etax.nat.gov.tw/ 進入）
  - 開獎：每單月 25 日（統一發票給獎辦法第 3 條 https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=G0340083&flno=3 ）
  - 領獎：開獎日之次月 6 日起三個月內（同辦法第 8 條 https://law.moj.gov.tw/LawClass/LawSingle.aspx?pcode=G0340083&flno=8 ）
  - 獎金金額、扣繳與印花稅規定以當期中獎號碼頁的「領獎注意事項」為準
- **財政統計資料庫**：https://web02.mof.gov.tw/njswww/WebMain.aspx?sys=100&funid=defjsptgl
- 常用法條：所得稅法 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=G0340003 、加值型及非加值型營業稅法 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=G0340080 、稅捐稽徵法 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=G0340001
- 注意：免稅額、扣除額、級距每年公告調整，報告只寫「依當年度財政部公告」並附公告頁；**個案稅務請洽會計師或國稅局**

### 10. 金融監督管理委員會

- 首頁：https://www.fsc.gov.tw/ch/index.jsp
- 新聞稿：https://www.fsc.gov.tw/ch/home.jsp?id=96&parentpath=0,2
- 裁罰案件：https://www.fsc.gov.tw/ch/home.jsp?id=131&parentpath=0,2
- 合法金融業網站連結：https://www.fsc.gov.tw/ch/home.jsp?id=153&parentpath=0,9
- 如何申訴（金融消費爭議）：https://www.fsc.gov.tw/ch/home.jsp?id=1044&parentpath=0,5
- 主管法規查詢系統：https://law.fsc.gov.tw/
- 金融市場統計資訊：https://stat.fsc.gov.tw/
- 注意：判斷「某業者是否合法」要用金管會或其所屬局的名單，不能只看業者自己的網站；**不給投資建議**

### 11. 中央銀行

- 首頁：https://www.cbc.gov.tw/tw/mp-1.html
- 理監事聯席會議決議：https://www.cbc.gov.tw/tw/lp-357-1.html
- 新聞稿：https://www.cbc.gov.tw/tw/lp-302-1.html
- 利率及準備率：https://www.cbc.gov.tw/tw/np-296-1.html
- 新臺幣／美元銀行間收盤匯率：https://www.cbc.gov.tw/tw/lp-645-1.html
- 金融統計：https://www.cbc.gov.tw/tw/np-521-1.html
- 注意：理監事會通常每季一次，確切日期看央行公告；收盤匯率是銀行間市場收盤價，不是銀行牌告匯率

### 12. 交通部中央氣象署

- 首頁：https://www.cwa.gov.tw/V8/C/
- 縣市預報：https://www.cwa.gov.tw/V8/C/W/County/index.html
- 氣象資料開放平台：https://opendata.cwa.gov.tw/ （API 說明 https://opendata.cwa.gov.tw/dist/opendata-swagger.html ）
- 注意：API 要先註冊會員取得授權碼，授權碼屬於使用者，不要寫進公開檔案；颱風、地震等警特報以氣象署發布為準，停班停課看各縣市政府公告

### 13. 全國法規資料庫（法務部）

- 首頁：https://law.moj.gov.tw/
- 中央法規查詢：https://law.moj.gov.tw/Law/LawSearchLaw.aspx
- 怎麼查：
  1. 首頁搜尋框輸入法規名稱 → 結果頁點法規名稱 → 網址裡的 `pcode=` 就是法規代碼
  2. 看單一條文：`LawSingle.aspx?pcode=代碼&flno=條號`
  3. 看修正歷程：`LawHistory.aspx?pcode=代碼`
- 注意：
  - 法規名稱旁會標「修正日期」；有些條文已公布但**施行日期另定**，要看頁面上的施行說明
  - 地方自治條例不在這裡，要去各縣市的法規查詢系統
  - 部會的函釋、行政規則有時只在該部會的法規系統（例如勞動法令查詢系統、金管會主管法規查詢系統）

**立法院法律系統**（立法理由、修法歷程）：https://lis.ly.gov.tw/lglawc/lglawkm

### 14. 司法院

- 裁判書查詢：https://judgment.judicial.gov.tw/FJUD/default.aspx
  - 怎麼查：輸入案號（例如「105訴123」）、法院加案號，或法規名稱加條號（例如「民訴法226」）；「更多條件查詢」可限定法院、案件類別、日期、全文關鍵字
- 法學資料檢索系統（判解函釋、大法庭裁定）：https://lawsearch.judicial.gov.tw/
- 憲法法庭：https://cons.judicial.gov.tw/
- 注意：
  - 引用判決要寫「法院＋年度＋字別＋案號＋裁判日期」，例如「臺灣高等法院 113 年度上字第 XXX 號民事判決」，並附裁判書頁網址
  - 地方法院判決可能被上級審改判，要查後續審級
  - 部分案件依法不公開或已去識別化；**單一判決不代表個案結果**，個案請洽律師

### 15. 行政院消費者保護會

- 首頁：https://cpc.ey.gov.tw/
- 消費爭議處理程序：https://cpc.ey.gov.tw/Page/71E988F034956960
- 線上申訴系統：https://appeal.cpc.ey.gov.tw/
- 法規及定型化契約（應記載及不得記載事項）：https://cpc.ey.gov.tw/Page/6A1E96411F78365C
- 法源：消費者保護法 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=J0170001
- 注意：各行業的定型化契約應記載事項由目的事業主管機關公告，要找最新版本

### 16. 公平交易委員會

- 首頁：https://www.ftc.gov.tw/internet/main/index.aspx
- 行政決定（處分書）：https://www.ftc.gov.tw/internet/main/decision/decisionList.aspx?mid=11
- 主管法規查詢系統：https://law.ftc.gov.tw/law/
- 多層次傳銷事業報備名單：https://fair.ftc.gov.tw/fair/report/report_search.aspx
- 法源：公平交易法 https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=J0150002

### 17. 各縣市政府

- 六都：臺北市 https://www.gov.taipei/ 、新北市 https://www.ntpc.gov.tw/ 、桃園市 https://www.tycg.gov.tw/ 、臺中市 https://www.taichung.gov.tw/ 、臺南市 https://www.tainan.gov.tw/ 、高雄市 https://www.kcg.gov.tw/
- 其他縣市：搜尋「縣市名＋政府全球資訊網」，**確認網域是 .gov.tw** 再用
- 能查：地方補助、停班停課、自治條例、地方稅（房屋稅、地價稅由地方稅務局處理）
- 縣市比較用主計總處縣市重要統計指標查詢系統（見第 2 項）
- 注意：同一項補助各縣市金額與資格不同，一定要寫是哪個縣市、哪一年度的公告

## 三、常見情境作法

**A. 查一個統計數字（例如最新 CPI 年增率）**
1. 到主計總處物價指數新聞稿頁，打開最新一則
2. 抄下：資料期間、數值、發布日期；有修正前月數字也一起記
3. 需要歷史序列時，到總體統計資料庫或政府資料開放平臺下載
4. 寫成：「數值（資料期間）｜來源：新聞稿網址｜查詢日期」

**B. 查一家公司是否存在、誰是負責人**
1. 商工登記公示資料查詢，用統一編號查（名稱可能重複）
2. 記下登記現況、代表人、核准設立日期、最後核准變更日期
3. 需要稅籍狀態時，請使用者自行到財政部稅籍登記公示查詢（有驗證碼）
4. 判斷是否為合法金融業者，另查金管會名單

**C. 引用一條法律**
1. 全國法規資料庫找到法規 → 記 pcode
2. 打開條文頁確認條號與內容、看修正日期與施行日期
3. 報告寫「法規名稱第 X 條（修正日期）」＋條文頁網址
4. 需要實務見解時，再查司法院判決或主管機關函釋，並註明「實務見解，非通案結論」

**D. 查房價行情**
1. 實價登錄網，限定區域、期間（建議近 1～2 年）、建物型態
2. 排除備註有特殊交易的案件
3. 寫出筆數、單價區間、中位數（自己算的要標「自行計算」）
4. 註明「實價登錄有揭露時間差，不代表即時行情」

## 四、交付前檢核表

- [ ] 每個數字都有：來源機關、內容所在頁網址、資料期間、查詢日期
- [ ] 法條附了全國法規資料庫條文頁（LawSingle），確認過修正日期
- [ ] 沒有寫死會變動的金額、費率、日期；有的話都附當期官方頁
- [ ] 民國年與西元年換算正確
- [ ] 查不到的寫「未查證」，不確定的寫「需查證」
- [ ] 統計口徑寫清楚（平均或中位數、總薪資或經常性薪資、戶籍或實際人口）
- [ ] 沒有用轉貼站、懶人包或新聞截圖代替官方來源（新聞可補充，但數字要回官方核對）
- [ ] 涉及個案的法律、醫療、稅務、投資問題，已提醒洽專業人員

## 五、易錯點

1. **只附首頁**：讀者找不到數字在哪。要附到新聞稿、統計表或條文頁那一層。
2. **把新聞報導的數字當官方數字**：新聞常四捨五入或用錯期間，一律回官方頁核對。
3. **法條版本過期**：記憶中的條文可能已修正。每次都打開條文頁看修正日期。
4. **把「公布」當「施行」**：有些法律公布後另定施行日，要看頁面說明。
5. **混用統計口徑**：主計總處與勞動部的薪資、平均與中位數、名目與實質，不能直接比。
6. **把查詢型頁面的網址當結果網址**：商工登記、裁判書的結果頁網址常帶暫時參數，別人打不開；改附查詢頁＋查詢條件。
7. **遇到驗證碼或安全驗證硬闖**：有圖形驗證碼的頁面不能代填，改用替代來源或請使用者自己查；安全驗證頁在一般瀏覽器通常會自動通過，不要嘗試繞過。
8. **縣市資料張冠李戴**：補助、停班停課、地方稅都是各縣市不同，標題就要寫縣市名。
9. **把單一判決當通案規則**：判決只對該案有拘束力，寫「某法院曾認為」而不是「法律規定」。
10. **網址失效就亂找替代**：先在同機關網站站內搜尋；找不到就寫「原頁面已失效，未查證」，不要改用來路不明的網站。
