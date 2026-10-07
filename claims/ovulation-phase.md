---
id: ovulation-phase
claim_zh: 排卵指卵子從卵巢釋出的事件；部分研究顯示，日曆日期不能確認這次事件何時發生
evidence: moderate
evidence_scope: 排卵名稱及需要生理資料的限制；不支持 Wave 確認排卵或提供生育用途
sources:
  - id: official:NHS-menstrual-cycle-2023
    url: https://www.nhs.uk/conditions/periods/fertility-in-the-menstrual-cycle/
    identifier_note: 官方網頁沒有 DOI／PMID；原始研究識別碼見下，不虛構期刊號
    quote: "Ovulation is the release of an egg from the ovaries."
    locator: What happens during ovulation?
    read: full
  - id: PMID:11510707
    doi: 10.1111/j.1471-0528.2001.00194.x
    url: https://pubmed.ncbi.nlm.nih.gov/11510707/
    quote: "Ultrasonography was able to show evidence of ovulation in 283 out of 326 cycles."
    locator: Abstract, Results
    read: abstract
against:
  - id: PMID:29749274
    doi: 10.1080/03007995.2018.1475348
    url: https://pubmed.ncbi.nlm.nih.gov/29749274/
    quote: "Accuracy of ovulation prediction was no better than 21%"
    locator: Abstract, Results; short verbatim excerpt
    read: abstract
    relevance: 反對日曆法確認個人排卵日；數值屬研究所測 App，不是 Wave 的準確率
population: 自然有排卵週期的生理說明；Ecochard 為 18–45 歲、規律有生育力的 107 位女性；Johnson 為尿液 LH 觀測志願者
not_for: [避孕, 備孕指導, 確認個人排卵, 激素避孕, 懷孕, 產後或哺乳的固定分期, PCOS 的固定分期, 圍絕經期的固定分期, 無排卵週期的四段推定]
used_by: [F05, F06, "string:todayPhaseOvulation", "string:todayCycleEstimated", "constant:CycleRules.estimatedLutealLengthDays"]
checked: 2026-10-07
expert: —
---

# 「排卵期」的顯示不能當作事件確認

[NHS 官方衛教](https://www.nhs.uk/conditions/periods/fertility-in-the-menstrual-cycle/)描述排卵事件。[Ecochard 原始研究摘要](https://pubmed.ncbi.nlm.nih.gov/11510707/)用超音波及激素／其他指標比較事件時間，顯示觀測指標之間也有差異。[Johnson 原始研究摘要](https://pubmed.ncbi.nlm.nih.gov/29749274/)說明純日曆估算的不足。沒有找到否定事件定義的研究；反證針對「日曆顯示＝已排卵」這個推論。

## 給 PM

- F06 `todayPhaseOvulation` 的實際字是「排卵期」；F05 把第 L−14 天指定成單日模型區段。這是一個模型日，不是已測量的排卵日，也不等於一段「安全／可受孕」窗口。
- 應同時看到 `todayCycleEstimated`（估算）。不要改成「今天已排卵」、排卵確認、避孕或備孕用途，也不能套用其他 App 的準確率。
- Wave 沒有 LH／BBT／超音波資料。此條引用它們只是說明測量與日期推算不同，不在本輪新增相關記錄／解讀功能。
- 文案候選（待審）：排卵是卵子從卵巢釋出的事件。這裡只依日期估算，沒有確認妳的排卵日。

研究交稿：2026-10-07；`checked`／`expert` 未審。
