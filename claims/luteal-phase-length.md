---
id: luteal-phase-length
claim_zh: 有部分研究說，黃體期長度有個體與週期間變異，十四天只是日曆估算常用假設
evidence: moderate
evidence_scope: 十四天假設的來源及不能視為個人固定值的限制
sources:
  - id: PMID:34815068
    doi: 10.1016/j.fertnstert.2021.10.007
    url: https://www.asrm.org/practice-guidance/practice-committee-documents/optimizing-natural-fertility-a-committee-opinion-2021/
    quote: "presumed to be approximately 14 days."
    locator: 2022 opinion, FERTILITY-AWARENESS METHODS, calendar-method paragraph; short verbatim excerpt
    read: full
  - id: DOI:10.1016/j.fertnstert.2026.06.014
    doi: 10.1016/j.fertnstert.2026.06.014
    url: https://www.asrm.org/globalassets/_asrm/practice-guidance/practice-guidelines/pdf/diagnosis-and-treatment-of-luteal-phase-deficiency.pdf
    quote: "may range from 11-17 days."
    locator: 2026 opinion, page 633, PHYSIOLOGY OF NORMAL LUTEAL FUNCTION; short verbatim excerpt
    read: full
against:
  - id: PMID:31482137
    doi: 10.1038/s41746-019-0152-7
    url: https://www.nature.com/articles/s41746-019-0152-7
    quote: "mean of 12.4 ± 2.4 days"
    locator: Discussion, paragraph beginning Anecdotally; short verbatim excerpt
    read: full
    relevance: 反對人人固定十四天；不是否定黃體期的生理定義
  - id: PMID:32104920
    doi: 10.1111/ppe.12644
    url: https://pubmed.ncbi.nlm.nih.gov/32104920/
    quote: "luteal phase length 11.7 (2.8) days, median 12."
    locator: Abstract, Results; short verbatim excerpt
    read: abstract
    relevance: 不同估計排卵方法及樣本得出不同中心值，不能據此改成個人固定十二天
population: 自然週期的群體參考；大型 App 研究為 18–45 歲、可由 BBT 算法辨識排卵的週期；來源各有排除條件
not_for: [確認個人排卵日, 個人激素濃度判定, 激素避孕, 懷孕, 產後或哺乳, PCOS, 圍絕經期, 無排卵週期, 生育力或疾病判定]
used_by: [F05, F06, "constant:CycleRules.estimatedLutealLengthDays", "string:todayPhaseOvulation", "string:todayPhaseLuteal", "string:todayCycleEstimated"]
checked: 2026-10-07
expert: —
---

# 十四天的來源與限制

[ASRM 2022 官方意見](https://www.asrm.org/practice-guidance/practice-committee-documents/optimizing-natural-fertility-a-committee-opinion-2021/)把十四天寫成日曆法的假設，並在同節說明估算缺點。[ASRM 2026 官方 PDF](https://www.asrm.org/globalassets/_asrm/practice-guidance/practice-guidelines/pdf/diagnosis-and-treatment-of-luteal-phase-deficiency.pdf)列典型 12–14 天、可能 11–17 天；這不是 Wave 的分類門檻。

[Bull 原始研究](https://www.nature.com/articles/s41746-019-0152-7)以 BBT／可選 LH 資料辨識週期，報告的平均黃體期為 12.4 天，存在變異。它排除了未辨識排卵／資料不足的週期，且有公司資助與作者利益關係；不能代表所有女性或替 Wave 驗證準確率。[另一隊列摘要](https://pubmed.ncbi.nlm.nih.gov/32104920/)以黏液高峰估排卵，亦未支持人人固定十四天。群體平均不同不等於黃體期生理機制受到否定。

## 給 PM

- `estimatedLutealLengthDays = 14` 可以記成可替換的估算假設；未查到它能確認個人本次階段的證據。不要把「較少變化」翻成「沒有變化」。
- 總長 L 的模型在第 L−14 天顯示 `.ovulation`，之後至 L 顯示 `.luteal`。兩個名稱都需要「估算」，不推導激素高低、運動／飲食建議或生育用途。
- 2026-10-07 讀到的 luteal deficiency 網頁／PDF 是 **2026 新版**，DOI 尾碼為 `2026.06.014`，不能掛在 2021 的 PMID:33827766 下。2021 只核對了 PubMed 摘要，沒有用它支持新版全文數值。
- 文案候選（待審）：有部分研究說，黃體期長度會變。這裡使用十四天作日期估算，沒有確認妳的排卵日。

研究交稿日期：2026-10-07。`checked`、`expert` 未審。
