---
id: calendar-phase-estimate
claim_zh: 有部分研究說，即使自述規律，單靠週期日期仍不能確認個人排卵日或當下生理階段
evidence: moderate
evidence_scope: 日曆估算限制；不是 Wave 準確率驗證
sources:
  - id: PMID:29749274
    doi: 10.1080/03007995.2018.1475348
    url: https://pubmed.ncbi.nlm.nih.gov/29749274/
    quote: "Ovulation day varies considerably for any given menstrual cycle length"
    locator: Abstract, Conclusions; short verbatim excerpt
    read: abstract
  - id: PMID:16700687
    doi: 10.1111/j.1552-6909.2006.00051.x
    url: https://pubmed.ncbi.nlm.nih.gov/16700687/
    quote: "The follicular phase contributes most to this variability."
    locator: Abstract, Conclusions
    read: abstract
against:
  - id: PMID:34815068
    doi: 10.1016/j.fertnstert.2021.10.007
    url: https://www.asrm.org/practice-guidance/practice-committee-documents/optimizing-natural-fertility-a-committee-opinion-2021/
    quote: "assist in understanding their own personal cycle characteristics and trends"
    locator: FERTILITY-AWARENESS METHODS, Patients should be empowered paragraph; short verbatim excerpt
    read: full
    relevance: 反對把日曆記錄說成完全無用；了解趨勢不等於驗證本次排卵
population: 對自然週期日曆法的限制描述；原始研究包含規律女性及尿液 LH 觀測志願者，不能直接外推全部人群
not_for: [避孕, 備孕指導, 確認排卵, 診斷, 激素避孕下的自然階段判定, 懷孕, 產後或哺乳的四階段判定, PCOS 的固定階段判定, 圍絕經期的固定階段判定, 無排卵週期的四階段判定]
used_by: [F05, F06, "string:todayCycleEstimated", "string:todayCycleDay", "string:todayCycleTitle", "string:todayPhaseMenstruation", "string:todayPhaseFollicular", "string:todayPhaseOvulation", "string:todayPhaseLuteal", "string:todayPhaseDuring", "string:todayPhaseAfter", "string:todayPhaseBefore", "constant:CycleRules.beforePeriodWindowDays", "constant:CycleRules.minimumCompletedCyclesForBefore"]
checked: 2026-10-07
expert: —
---

# 日期資訊與身體階段要分開

Johnson 原始研究摘要使用尿液 LH 作比較，發現同樣週期長度的排卵日仍會變 [1]。Fehring 前瞻研究摘要也在自述規律的女性中觀察到變異 [2]。兩篇只讀摘要。這支持限制說明，不能計算 Wave 的準確率。

另一方面，ASRM 官方意見肯定日期記錄對了解個人趨勢的用途，同時要求說清日曆法不足 [3]。研究少不等於記錄無用；有記錄也不等於確認排卵。

## 給 PM

- `todayCycleDay` 是從產品認定的開始日算起的日期計數；開始日可能來自自述或貼紙分組，不能稱為經實驗確認的生理週期日。
- 規律模式超出設定 L 或 L≤20 不顯示四階段，是模型容納／過期規則，不是健康判定；不把它當「沒有排卵」。
- 貼紙分組與起點認定依 F05 的產品規則，不能當成醫學分類。**沒有找到原始研究驗證這套貼紙分組或兩週期平均能確認本次身體階段。**
- F06 `string:todayPhaseBefore` 的實際文字是「預估經期前」，由 `.beforePeriod` 顯示並伴隨 `todayCycleEstimated`（估算）。它承接本條的日曆估算限制，不是第五個生理階段，也不是 PMS 或黃體期證明。
- `CycleRules.beforePeriodWindowDays = 3` 只顯示個人估計開始日前 1–3 天；`minimumCompletedCyclesForBefore = 2` 需要至少兩個完整起點間隔／三個產品認定的實際起點。程式以已完成間隔的平均值四捨五入至整天，未用 onboarding 預設長度補資料；不足兩個間隔不顯示「前」。**三天窗口與兩個週期門檻是產品選擇，沒有在本條取得臨床有效性驗證，不能由 `moderate` 推成醫學結論。**
- 「中」只指最近記錄在窗口內；`recentBleedingGraceDays = 1` 的漏記容許窗口優先於「前」。「後」只指窗口外，不能寫成出血已結束、PMS、已進入濾泡期或已排卵。
- 沒有新貼紙不能確認停經、懷孕、出血結束或任何疾病。
- 特殊人群列為「本模型未驗證／不宜直接套用」，不是宣稱她們每個週期都無排卵。Onboarding 現有五選項不能辨識全部特殊人群；交 PM／Claude 決定說明與外部版本策略，不在本輪新增 R04 功能。
- 文案候選（待審）：有部分研究說，日期估算有個體差異。這裡用來理解記錄，不能確認排卵或出血是否結束。

研究交稿：2026-10-07；Claude 已於同日[正式查證](https://github.com/waveperiod/wavepedia/pull/1#issuecomment-6045659263)並填入 `checked`。`expert` 仍待簽核。2026-10-08 整理 Vancouver 引用，並對照 F06 PR HEAD `4fa9e56ee5e2aa1bcc445fbf9a9cd0e852689658` 補「預估經期前」key 與 3／2／1 產品規則；健康說法與來源原句保留。**既有 `checked` 日期不代表本輪新增 mapping 已查證；新增映射及書目格式待 Claude 複核。**

## 參考文獻

1. Johnson S, Marriott L, Zinaman M. Can apps and calendar methods predict ovulation with accuracy? Curr Med Res Opin. 2018;34(9):1587-94. doi:10.1080/03007995.2018.1475348. PMID: 29749274.
2. Fehring RJ, Schneider M, Raviele K. Variability in the phases of the menstrual cycle. J Obstet Gynecol Neonatal Nurs. 2006;35(3):376-84. doi:10.1111/j.1552-6909.2006.00051.x. PMID: 16700687.
3. Practice Committee of the American Society for Reproductive Medicine and the Practice Committee of the Society for Reproductive Endocrinology and Infertility, Penzias A, Azziz R, Bendikson K, Falcone T, Hansen K, et al. Optimizing natural fertility: a committee opinion. Fertil Steril. 2022;117(1):53-63. doi:10.1016/j.fertnstert.2021.10.007. PMID: 34815068.
