# R02 · 四個名稱的查證及 App 對應

交稿：2026-10-07。Researcher 查來源與名稱；**Claude 尚未 checked，expert 尚未簽核，F06 仍有研究 gate。**

獨立分支從 wavepedia `bbf53b284573b15e12ec40be7dba62aa66a47b52` 出發，不堆在 R03。只新增四條 claim／本清單；既有文章不改。R03 的常數與估算限制是另一個待審 PR：<https://github.com/waveperiod/wavepedia/pull/1>。

## 逐名稱 mapping（只讀原 App）

基線 App HEAD `b51c34a4dfcf239b4b54a5c5f5b5de66726a00a6`。讀 `Wave/Localizable.xcstrings`、`TodayCycleSection.swift`、`CyclePhase.swift`、`CycleRules.swift`／`CycleCalculator.swift`，未修改原 checkout 或使用者未提交檔案。

| F05 enum | F06 實際 string key／文字 | R02 條目 | 模型顯示與限制 |
|---|---|---|---|
| `.menstruation` | `todayPhaseMenstruation`／月經期 | [menstruation-phase](../claims/menstruation-phase.md) | 規律第 1–5 天；不代表已確認出血或出血來源 |
| `.follicular` | `todayPhaseFollicular`／濾泡期 | [follicular-phase](../claims/follicular-phase.md) | 第 6 天至 L−14 前一天；生理濾泡期其實從經期開始，與月經重疊 |
| `.ovulation` | `todayPhaseOvulation`／排卵期 | [ovulation-phase](../claims/ovulation-phase.md) | 第 L−14 天是單日模型；不能解讀為排卵確認或生育窗口 |
| `.luteal` | `todayPhaseLuteal`／黃體期 | [luteal-phase](../claims/luteal-phase.md) | 第 L−14 後一天至 L；不能證明已排卵或孕酮水平 |

四者都對應 `string:todayCycleEstimated`＝「估算」。這個字描述模型性質，不能替代可讀的估算限制說明。條目里的文案候選尚未進 String Catalog、未被採用；由 PM／Claude 審其呈現，不讓 Researcher 改 App。

## 來源閱讀與兩邊證據

| 原始／官方來源 | DOI／PMID 與定位 | 本次閱讀 | 支持或限制 |
|---|---|---|---|
| NHS Periods and fertility in the menstrual cycle | 官方網頁無 DOI／PMID，明示在 frontmatter；What are periods?／What happens during ovulation? | full | 月經與排卵的名稱；不當作個人固定日期依據 |
| Dasharathy 2012 BioCycle | PMID:22350580；10.1093/aje/kwr356；Abstract | abstract | 週期中也能有出血，反對任何出血就是新月經的推論 |
| Bull 2019 | PMID:31482137；10.1038/s41746-019-0152-7；Methods, Identification of ovulation day／Study design | full | 濾泡／黃體分期。樣本及公司利益、BBT／LH 算法限制見原文，不能借給 Wave 驗準 |
| Fehring 2006 | PMID:16700687；10.1111/j.1552-6909.2006.00051.x；Abstract | abstract | 規律女性也有分期變異，不能把固定區段當生理邊界 |
| Ecochard 2001 原始多中心研究 | PMID:11510707；10.1111/j.1471-0528.2001.00194.x；Abstract | abstract | 使用超音波／生理標記比較事件；並未驗證純日期法 |
| Johnson 2018 原始研究 | PMID:29749274；10.1080/03007995.2018.1475348；Abstract | abstract | 日曆法的個人排卵估計限制；研究所測 App 的數字不能叫 Wave 準確率 |
| ASRM 2026 官方意見 | 10.1016/j.fertnstert.2026.06.014；官方 PDF 633頁生理、635頁測量限制、637頁總結；首頁 DOI | full | 黃體／孕酮机制及限制；不是2021版，沒有把疾病／治療內容搬入 App |
| Najmabadi 2020 三隊列原始研究 | PMID:32104920；10.1111/ppe.12644；Abstract | abstract | 同一女性的分期仍有變異 |

**反面研究針對從 App 日曆標籤推定身體階段的越界，不是為了假造對生理名稱本身的爭論。** 未找到否定月經、濾泡期、排卵、黃體期這些生理定義的來源。

`moderate` 的限定範圍已逐條寫明；沒有宣稱系統綜述一致或個人推算準確。特殊人群的 `not_for` 表示「不能直接套用此固定分期模型」，不表示每位特殊人群一定沒有排卵。

## 給 cycle／recording 的產品規則交接

原 App 的 `todayPhaseDuring`＝「經期記錄中」、`todayPhaseAfter`＝「最近經期記錄之後」不是上表四種生理階段。本次[ R03 PR #1](https://github.com/waveperiod/wavepedia/pull/1) 的 `calendar-phase-estimate` 提供其讀取限制；「後」不能翻成出血已結束。

2026-10-07 協調 `cycle-status.json` 已記錄前窗口 **3 天**、中容許漏記 **1 天**、至少 **2 個完整週期／3 個起點**。這是產品顯示決策，不是醫學結論；待該會話實作完成後對其最終常數／新「前」key 補核對。目前原 App 尚無 before key，不能編造 `used_by` 名稱或聲稱已覆蓋新版本。

## 檢查清單

- [x] 四個條目各有完整 frontmatter、支持與限制來源、短原句、read 層級、population／not_for、實際 used_by。
- [x] 全部 `checked`／`expert` 保持「—」。
- [x] 四個 key 與「估算」逐個對原 App String Catalog；沒有套用 role 示例中的假 `phase.luteal.desc` key。
- [x] 解釋月經與濾泡期重疊，App 四區段只是呈現。
- [x] 不輸出個人激素判定、運動／飲食處方或生育用途；不新增 R04／F08 後功能。
- [ ] Claude 核對來源識別符、短原句、等級、人群及 mapping，填 checked。
- [ ] 專家簽 expert。
- [ ] App 返修會話交最新 `beforePeriod` 新字串與常數，再補 mapping。
- [ ] recording 在 iOS 26.0／26.5 實際 launch／操作／UITest，檢查正常、空、最大字級並交截圖。Researcher 本次沒有 simulator 測試／截圖，不聲稱文獻可由 simulator 驗證。

## UI 核對案例（交 recording，未執行）

正常 L=28：月經期（1、5），濾泡期（6、13），排卵期（14），黃體期（15、28），每個都應有「估算」。第29天只保留日期日數、phase 空；L≤20 不顯示四區段，這是模型限制。

同一畫面和 VoiceOver 必須讀到階段的估算性質；最大字級「估算」不能丟失或被裁掉。無經期／不確定應按現有產品規則隱藏整卡，不只隱藏 phase。

不規律資料不足不顯「前」；資料足夠的前3天標估算。最新出血日之後1天仍「中」，2天後「後」，不聲稱已停血；新出血在「前」期間發生時按實際記錄優先。最終以 cycle 的集中規則與測試案例為準。
