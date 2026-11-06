# openbotskill：OpenBot 代理技能庫（台灣情境）

這裡放的是給 [OpenBot](https://openbot.run) 代理使用的技能（Agent Skills）。每個技能是一個資料夾，裡面有一份 `SKILL.md`：開頭是名稱與說明，內文是代理照著做的方法、官方資料來源、檢核表和公式。

這些技能搭配「OpenBot 提示詞庫」網站的團隊套組使用。按網站上的「一鍵建立整組」貼給建置員時，建置員會從這裡下載技能原文，自動裝給需要的團員。

## 目前的技能

| 技能 | 給誰用 | 做什麼 |
|---|---|---|
| [econ-calendar](skills/econ-calendar/SKILL.md) | 投資研究室：國際市場情報分析員 | 用不需要登入的財經日曆（Forex Factory 資料檔、Investing.com 香港版）加上官方公布頁，寫美國數據快評、國際早報、一週預告；精準快評自動對時；哨兵來源維護 |
| [tw-official-sources](skills/tw-official-sources/SKILL.md) | 所有情報分析員、法規追蹤 | 台灣官方資料來源清單與查法（主計總處、內政部、勞動部、衛福部、教育部、考選部、財政部、全國法規資料庫等）與引用規則 |
| [tw-pension-calc](skills/tw-pension-calc/SKILL.md) | 退休規劃、個人理財、人資 | 勞保老年給付兩式擇優、勞退個人專戶、國民年金的公式、查法與試算步驟 |
| [tw-ltc](skills/tw-ltc/SKILL.md) | 長照支援、退休規劃 | 長照 2.0 申請流程、四類給付、部分負擔、外籍看護與住宿式機構補助的查法 |
| [tw-tax-invoice](skills/tw-tax-invoice/SKILL.md) | 個人理財、門市、餐飲、民宿、補教、NPO | 營業稅、統一發票與電子發票、綜所稅、扣繳、二代健保補充保費、房屋稅與地價稅 |
| [tw-rental-law](skills/tw-rental-law/SKILL.md) | 租屋生活、法務合規 | 租賃條例、定型化契約應記載及不得記載事項、押金與退租扣款判斷、租金補貼與糾紛管道 |
| [tw-condo-law](skills/tw-condo-law/SKILL.md) | 社區管委會 | 公寓大廈管理條例、區分所有權人會議召集與決議門檻、管理費催收、修繕招標 |
| [tw-privacy-ad-law](skills/tw-privacy-ad-law/SKILL.md) | 法務、診所、行銷、客服 | 個資法、醫療廣告、食品與化粧品廣告、公平法不實廣告，附廣告稿逐句檢查法 |
| [tw-school-admission](skills/tw-school-admission/SKILL.md) | 升大學輔導、國中升學 | 國中會考與免試入學超額比序、大學多元入學（學測、分科、繁星、申請）、四技二專 |
| [tw-labor-law](skills/tw-labor-law/SKILL.md) | 人資、法務、餐飲、門市、診所、補教 | 勞基法工時、加班費、特休、資遣，就服法、性平法、勞健保、職安法，附試算與排班檢核 |
| [tw-exam-license](skills/tw-exam-license/SKILL.md) | 國考證照 | 考選部類科、應考資格、命題大綱、歷屆試題，技能檢定與常見證照查法 |
| [investing-masters](skills/investing-masters/SKILL.md) | 投資研究室：大師觀點審查員 | 十二位投資大師（巴菲特、芒格、葛拉漢、林區、費雪、葛林布萊特、柏格、達利歐、霍華·馬克斯、坦伯頓、吉姆·羅傑斯、哈利·布朗）的檢查清單，審查個股、ETF、債券、商品與資產配置；只做比對、不給買賣訊號、不寫語錄 |
| [holdings-tracker](skills/holdings-tracker/SKILL.md) | 投資研究室：持倉追蹤員 | 從 SEC EDGAR 抓大師基金 13F（波克夏、喜馬拉雅、H&H、Pershing Square、Dalal Street 等，附 CIK），從投信官網抓台灣熱門前 20 大 ETF 成分股；比對新進、出清、加減碼與換股，算重疊持股的家數與權重 |
| [stock-watch](skills/stock-watch/SKILL.md) | 投資研究室：個股哨兵、投資情報分析員 | 公司名或代號對應台美股代號與 CIK；巡台股重大訊息、美股 SEC 8-K／6-K 與新聞 RSS；個股快評的利多／利空／中性、重要性星等與信心度 |
| [company-analysis](skills/company-analysis/SKILL.md) | 投資研究室：個股分析師 | 台股與美股個股深度研究：產業、營收結構、競爭者、護城河、同業中位數比較、近 5～10 年趨勢、估值、風險；附官方來源與公式，不給評等與目標價 |
| [tw-tender-watch](skills/tw-tender-watch/SKILL.md) | 標案作戰室：標案哨兵、招標文件分析師 | 政府電子採購網當日招標與更正公告的查詢網址（不需登入、無驗證碼）、用 OpenBot 共用資料庫記已讀、新案初篩的符合度星等與截標提醒 |
| [openbot-dashboard](skills/openbot-dashboard/SKILL.md) | 儀表板管家 | 把各團隊產出整理成一頁靜態網頁、用 OpenBot 網頁託管早晚更新同一網址；公開範圍與隱私檢查、網頁範本 |
| [tw-inheritance-funeral](skills/tw-inheritance-funeral/SKILL.md) | 身後事與繼承室 | 死亡登記與除戶、殯葬禮俗與契約、勞保國保喪葬與死亡給付、保險理賠、遺產清查、遺產稅申報、拋棄與限定繼承、繼承登記 |
| [tw-insurance-sales](skills/tw-insurance-sales/SKILL.md) | 保險業務室 | 業務員管理規則、招攬與廣告規範、金融消費者保護法的適合度與說明義務、個資、理賠文件與流程 |
| [tw-landlord](skills/tw-landlord/SKILL.md) | 房東管理室 | 出租人義務、租約範本、租賃所得申報、房屋稅與地價稅、包租代管、修繕與押金、拒租的法律界線 |
| [tw-teaching](skills/tw-teaching/SKILL.md) | 教師備課室 | 108 課綱、核心素養與學習表現、教案與學習單、多元評量、特教與 IEP、通報義務、親師溝通與公文 |
| [tw-prepaid-service](skills/tw-prepaid-service/SKILL.md) | 美業工作室、健身工作室 | 美容、瘦身美容、健身中心、健身教練定型化契約，預收款履約保障、解約退費試算、廣告與醫療用語界線 |
| [tw-pet-business](skills/tw-pet-business/SKILL.md) | 寵物店與動物醫院 | 動保法、寵物登記、特定寵物業許可、犬貓美容與寄養契約、狂犬病注射、櫃台不做診斷的界線 |
| [tw-preschool](skills/tw-preschool/SKILL.md) | 幼兒園托育室 | 幼照法、托嬰中心規定、評鑑、準公共化與育兒補助查法、收退費、傳染病與事故通報 |
| [tw-ltc-institution](skills/tw-ltc-institution/SKILL.md) | 長照機構營運室 | 長服法、機構設立標準、評鑑與督考、給付及支付基準與核銷、照服員、感染管制與緊急應變 |
| [tw-temple](skills/tw-temple/SKILL.md) | 宮廟廟務室 | 辦理寺廟登記須知、監督寺廟條例與釋字 573、財團法人、公益勸募、捐款收據與徵信、祭典與道路使用 |
| [tw-new-immigrant](skills/tw-new-immigrant/SKILL.md) | 新住民生活室 | 居留、定居、歸化、工作權、健保、新住民發展基金、子女教育、服務專線與緊急協助 |
| [tw-realestate-broker](skills/tw-realestate-broker/SKILL.md) | 房仲業務室 | 經紀業管理條例、說明書應記載事項、要約書與斡旋金、實價登錄、公平法廣告規範、個資 |
| [tw-gig-worker](skills/tw-gig-worker/SKILL.md) | 零工接案室 | 外送員權益保障及外送平臺管理法、職業工會加保、職災保險、健保身分、所得類別、補充保費、多元計程車 |
| [tw-village](skills/tw-village/SKILL.md) | 里長服務處 | 地方制度法、里辦公處與里鄰規定、公文與陳情案件處理、補助管道、活動安全、選舉期間的中立提醒 |

## 原則

- **只用官方或可公開查證的來源**，網址要是內容所在的那一頁；查不到就寫「未查證」
- **會變動的數字不寫死**：費率、補助金額、法規條文都只寫「去哪裡查」，避免技能過時
- **不給買賣、醫療或法律結論**：推論一律標「推論」並寫依據
- 技能內容是給代理的工作方法，不是專業意見；涉及法律、醫療、稅務、投資的決定請洽專業人員

## 安裝

一般使用者不用手動安裝：網站套組的卡片會帶 `===技能===` 段，建置員會自動下載並安裝。想手動裝的話，把整個技能資料夾放進代理工作區的 `.agents/skills/`。

## 授權

MIT License，見 [LICENSE](LICENSE)。歡迎使用與修改；引用網站內容時請遵守各來源網站的使用條款。
