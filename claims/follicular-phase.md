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
checked: —
expert: —
---

# 「濾泡期」不是從出血結束才開始

[原始研究的分期方法](https://www.nature.com/articles/s41746-019-0152-7)從經期起點算濾泡期，以估計排卵日作最後一日；實際排卵日依 BBT／LH 估計。月經出血與這個卵巢階段可以同時存在。[規律女性前瞻研究摘要](https://pubmed.ncbi.nlm.nih.gov/16700687/)觀察到長度變異。定義與測量方法要分開看。

## 給 PM

- F06 `todayPhaseFollicular` 的實際字是「濾泡期」。F05 只把規律模式第六天到 L−14 之前一日顯示為它；这是從完整濾泡期中拆出的產品區段，不是「第六天身體才進入濾泡期」。
- 需要「估算」；第六天標籤不能證明出血已結束。不能據此推定雌激素濃度、精力或訓練表現。
- 研究包含生理觀測，Wave 的日期／貼紙模型沒有這些測量；不能借原研究對其算法的验证替 Wave 背書。
- 文案候選（待審）：濾泡期從經期開始，延續到排卵前後的分期邊界。這裡只顯示依日期估算的區段。

研究交稿：2026-10-07；`checked`／`expert` 未審。
