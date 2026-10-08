# R02 · 四個名稱的查證及 App 對應

交稿：2026-10-07；收尾更新：2026-10-08。**四條 `checked: 2026-10-07` 已由 Claude 填入；`expert` 仍未簽核。** [正式查證評論](https://github.com/waveperiod/wavepedia/pull/2#issuecomment-6045658829)對應 Reviewer 提交 `2d735db57506624fbd63223903e21570c495e7f9`，本輪保留該提交及繁體字修正。

本輪依最新 Researcher 規則整理 Vancouver 正文編號與參考文獻，保留健康說法、來源原句、閱讀層級、人群與 `checked` 日期。ASRM 2026 的既有 DOI 補入其 PubMed 書目 PMID:42414147，沒有增加健康說法。**新增書目格式及跨 PR「前」映射交接待 Claude 核對；本清單不宣告 F06 pass／done。**

獨立分支從 wavepedia `bbf53b284573b15e12ec40be7dba62aa66a47b52` 出發，不堆在 R03。只涉及四條 claim／本清單；既有文章不改。R03 的常數與估算限制見另一個 PR：<https://github.com/waveperiod/wavepedia/pull/1>。

## 逐名稱 mapping（只讀原 App）

原交稿基線 App HEAD `b51c34a4dfcf239b4b54a5c5f5b5de66726a00a6`。本輪對照 [F06 PR #6](https://github.com/waveperiod/ios-app/pull/6) 當前 HEAD `4fa9e56ee5e2aa1bcc445fbf9a9cd0e852689658` 的已提交 `Wave/Localizable.xcstrings`、`TodayCycleSection.swift`、`CycleRules.swift`／`CycleCalculator.swift`；以下四個名稱及「估算」仍相符。只讀 Git 物件，未修改 App checkout 或使用者檔案。

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

F06 HEAD `4fa9e56` 已有 `string:todayPhaseBefore`＝「預估經期前」，由 `.beforePeriod` 顯示，且 `isEstimated: true` 使「估算」同時顯示。其依據對應 R03 `calendar-phase-estimate`，不作第五個生理階段定義。

`CycleRules.beforePeriodWindowDays = 3` 為個人日期估值前的 1–3 天；`minimumCompletedCyclesForBefore = 2` 需要至少兩個完整起點間隔／三個實際起點。`recentBleedingGraceDays = 1` 的「中」記錄窗口優先於「前」。這些是產品顯示規則，不是醫學結論或臨床有效性門檻；R03 已補精確 `used_by` 與限制，**新增映射待 Claude 複核**。

## 檢查清單

- [x] 四個條目各有完整 frontmatter、支持與限制來源、短原句、read 層級、population／not_for、實際 used_by。
- [x] 四條保留 Claude 的 `checked: 2026-10-07`；`expert` 均為「—」，沒有由 Researcher 代填。
- [x] 四個 key 與「估算」逐個對原 App String Catalog；沒有套用 role 示例中的假 `phase.luteal.desc` key。
- [x] 解釋月經與濾泡期重疊，App 四區段只是呈現。
- [x] 不輸出個人激素判定、運動／飲食處方或生育用途；不新增 R04／F08 後功能。
- [x] Claude 2026-10-07 正式核對四條既有內容並填 checked；評論與提交見上。
- [x] 四條正文採 Vancouver 編號，與 frontmatter 的來源一一對應；參考文獻列 DOI／PMID，NHS 列官方網址與原閱讀日期。
- [ ] Claude 核對本輪 Vancouver 格式及 R03 新增「前」mapping，不能由既有 checked 日期推定已審新增部分。
- [ ] 專家簽 expert。
- [x] 對照 F06 PR HEAD 的 before 字串與 3／2／1 常數，交 R03 `calendar-phase-estimate` 承接；此項為 Researcher 靜態對照。
- [ ] recording 在 iOS 26.0／26.5 實際 launch／操作／UITest，檢查正常、空、最大字級並交截圖。Researcher 本次沒有 simulator 測試／截圖，不聲稱文獻可由 simulator 驗證。

## UI 核對案例（交 recording，未執行）

正常 L=28：月經期（1、5），濾泡期（6、13），排卵期（14），黃體期（15、28），每個都應有「估算」。第29天只保留日期日數、phase 空；L≤20 不顯示四區段，這是模型限制。

同一畫面和 VoiceOver 必須讀到階段的估算性質；最大字級「估算」不能丟失或被裁掉。無經期／不確定應按現有產品規則隱藏整卡，不只隱藏 phase。

不規律資料不足不顯「前」；資料足夠的前3天標估算。最新出血日之後1天仍「中」，2天後「後」，不聲稱已停血；新出血在「前」期間發生時按實際記錄優先。最終以 cycle 的集中規則與測試案例為準。
