---
id: follicular-phase
claim_zh: 自然有排卵週期的濾泡期從月經開始延續至排卵邊界，部分研究顯示其長度有變異
evidence: moderate
evidence_scope: 自然週期的分期含義；不是 App 第六天起的固定生理界線
sources:
  - id: PMID:31482137
    doi: 10.1038/s41746-019-0152-7
    url: https://www.nature.com/articles/s41746-019-0152-7
    quote: "At the onset of menses, marking the start of the follicular phase"
    locator: Methods, Identification of ovulation day; short verbatim excerpt
    read: full
against:
  - id: PMID:16700687
    doi: 10.1111/j.1552-6909.2006.00051.x
    url: https://pubmed.ncbi.nlm.nih.gov/16700687/
    quote: "there is considerable normal variability"
    locator: Abstract, Conclusions; short verbatim excerpt
    read: abstract
    relevance: 反對用固定日曆區段確認個人濾泡期邊界；未找到否定生理定義的研究
population: 自然且有排卵的週期之分期含義；Bull 為 18–45 歲、有足夠 BBT 資料的 App 使用者；Fehring 為規律女性
not_for: [單靠日期確認階段, 激素避孕下的自然分期, 懷孕, 產後或哺乳的固定分期, PCOS 的固定分期, 圍絕經期的固定分期, 無排卵週期的四段假設, 激素或飲食運動判斷]
used_by: [F05, F06, "string:todayPhaseFollicular", "string:todayCycleEstimated", "constant:CycleRules.estimatedPeriodLengthDays", "constant:CycleRules.estimatedLutealLengthDays"]
checked: 2026-10-07
expert: —
---

# 「濾泡期」不是從出血結束才開始

原始研究的分期方法從經期起點算濾泡期，以估計排卵日作最後一日；實際排卵日依 BBT／LH 估計。月經出血與這個卵巢階段可以同時存在 [1]。規律女性前瞻研究摘要觀察到長度變異。定義與測量方法要分開看 [2]。

## 給 PM

- F06 `todayPhaseFollicular` 的實際字是「濾泡期」。F05 只把規律模式第六天到 L−14 之前一日顯示為它；這是從完整濾泡期中拆出的產品區段，不是「第六天身體才進入濾泡期」。
- 需要「估算」；第六天標籤不能證明出血已結束。不能據此推定雌激素濃度、精力或訓練表現。
- 研究包含生理觀測，Wave 的日期／貼紙模型沒有這些測量；不能借原研究對其算法的驗證替 Wave 背書。
- 文案候選（待審）：濾泡期從經期開始，延續到排卵前後的分期邊界。這裡只顯示依日期估算的區段。

研究交稿：2026-10-07；Claude 已於同日[正式查證](https://github.com/waveperiod/wavepedia/pull/2#issuecomment-6045658829)並填入 `checked`。`expert` 仍待簽核。2026-10-08 僅整理正文引用與書目，既有健康說法、來源原句與查證日期保留；本輪格式更新待 Reviewer 核對。

## 參考文獻

1. Bull JR, Rowland SP, Berglund Scherwitzl E, Scherwitzl R, Gemzell Danielsson K, Harper J. Real-world menstrual cycle characteristics of more than 600,000 menstrual cycles. NPJ Digit Med. 2019;2:83. doi:10.1038/s41746-019-0152-7. PMID: 31482137.
2. Fehring RJ, Schneider M, Raviele K. Variability in the phases of the menstrual cycle. J Obstet Gynecol Neonatal Nurs. 2006;35(3):376-84. doi:10.1111/j.1552-6909.2006.00051.x. PMID: 16700687.
