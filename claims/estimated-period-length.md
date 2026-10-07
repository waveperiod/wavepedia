---
id: estimated-period-length
claim_zh: 有部分研究說，經期出血天數的中位數約為五天，但群體數字不能確認妳這次出血何時結束
evidence: moderate
evidence_scope: 群體中心值與個體變異；不是每位使用者固定五天的證據
sources:
  - id: PMID:22350580
    doi: 10.1093/aje/kwr356
    url: https://pubmed.ncbi.nlm.nih.gov/22350580/
    quote: "Women bled for a median of 5 days"
    locator: Abstract, Results sentence; short verbatim excerpt
    read: abstract
  - id: official:NHS-periods-2023
    url: https://www.nhs.uk/conditions/periods/
    identifier_note: 官方衛教網頁沒有 DOI 或 PMID；不虛構識別碼，論文識別碼見上
    quote: "it will usually last for about 5 days."
    locator: Overview, opening paragraph on duration; short verbatim excerpt
    read: full
against:
  - id: PMID:32104920
    doi: 10.1111/ppe.12644
    url: https://pubmed.ncbi.nlm.nih.gov/32104920/
    quote: "The mean menses length was 6.2"
    locator: Abstract, Results; short verbatim excerpt
    read: abstract
    relevance: 另一組樣本的中心值不同，反對把五天當所有人的固定長度，不反對經期存在
population: 群體參考；BioCycle 為規律經期女性，另一前瞻隊列為 18–40 歲、沒有已知生育力問題的女性
not_for: [個人出血結束判定, 激素避孕下的自然週期推定, 懷孕, 產後或哺乳期的固定天數推定, 圍絕經期的固定天數推定, PCOS 的固定天數推定, 無排卵週期的四階段推定]
used_by: [F05, F06, "constant:CycleRules.estimatedPeriodLengthDays", "string:todayPhaseMenstruation", "string:todayPhaseFollicular", "string:todayCycleEstimated"]
checked: —
expert: —
---

# 五天是估算預設，不是出血結束日

[BioCycle 論文摘要](https://pubmed.ncbi.nlm.nih.gov/22350580/)報告中位數五天。[NHS 官方衛教](https://www.nhs.uk/conditions/periods/)描述通常約五天及二至七天的概略範圍；此範圍不能當個人健康門檻。不同樣本的[三隊列研究](https://pubmed.ncbi.nlm.nih.gov/32104920/)報告中位數六天，且同一女性不同週期也有變化。

此條評為 `moderate` 的是「有群體參考值而且存在變異」。沒有找到支持「每位女性這次一定在第五天結束」的證據。只讀兩篇論文摘要，不能宣稱已審全文。

## 給 PM

- 實際程式把規律模式的第 1–5 天分到 `.menstruation`；第六天可能已顯示「濾泡期」，即使當天仍有出血貼紙。這是產品區段，不是記錄證明出血已停。
- 「月經期」及接下來的「濾泡期」必須伴隨 `todayCycleEstimated`（估算），不能用此常數刪改真實記錄。
- 五天不可用作不規律模式「中」的固定出血期，漏記也不代表結束；「中／後」依批准的記錄窗口另定。
- 文案候選（待產品／Claude 審）：有部分研究說，經期天數因人而異。這裡依日期估算，不代表出血已結束。

研究交稿日期：2026-10-07。`checked` 待 Claude 逐句查證；`expert` 待專家簽核。
