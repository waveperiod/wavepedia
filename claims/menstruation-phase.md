---
id: menstruation-phase
claim_zh: 月經是血液與子宮內膜排出的過程；部分研究觀察到週期中也可能有出血，出血記錄本身不能確認階段
evidence: moderate
evidence_scope: 生理名稱與出血記錄的解讀限制；不是固定五天或貼紙分組驗證
sources:
  - id: official:NHS-menstrual-cycle-2023
    url: https://www.nhs.uk/conditions/periods/fertility-in-the-menstrual-cycle/
    identifier_note: 官方衛教網頁沒有 DOI 或 PMID；原始研究識別碼見 against，不虛構官方期刊號
    quote: "A period is made up of blood and the womb lining."
    locator: What are periods?
    read: full
against:
  - id: PMID:22350580
    doi: 10.1093/aje/kwr356
    url: https://pubmed.ncbi.nlm.nih.gov/22350580/
    quote: "Only 4.8% of women experienced midcycle bleeding."
    locator: Abstract
    read: abstract
    relevance: 反對任何出血都能確認新的月經期；不是否定月經的定義
population: 自然週期的一般生理說明；反例研究為 BioCycle 的規律經期女性，不能將其發生率外推所有人
not_for: [由貼紙判定出血原因, 證明已排卵, 激素避孕出血的自然階段推定, 懷孕出血分類, 產後或哺乳的固定階段推定, PCOS 的固定階段推定, 圍絕經期的固定階段推定]
used_by: [F05, F06, "string:todayPhaseMenstruation", "string:todayCycleEstimated", "constant:CycleRules.estimatedPeriodLengthDays"]
checked: —
expert: —
---

# 「月經期」表示什麼

[NHS 官方衛教](https://www.nhs.uk/conditions/periods/fertility-in-the-menstrual-cycle/)將月經說明為子宮內膜與血液排出的過程，以開始日作日曆週期第 1 天。[BioCycle 原始研究摘要](https://pubmed.ncbi.nlm.nih.gov/22350580/)也觀察到週期中的出血；沒有否定生理定義的研究，反例針對從出血推定階段。

## 給 PM

- F06 `todayPhaseMenstruation` 的實際字是「月經期」。F05 在規律模式用第 1–5 天顯示它，不能聲稱已確認當天出血或其原因；需要同時顯示「估算」。
- 這個名稱描述子宮的出血过程，會與卵巢的早期濾泡期重疊。四個 App 區段不是四段互不重疊的生理分類。
- 九種出血貼紙與超過十五天的新開始規則是產品分組。點狀出血不一定是新經期；不能把分類輸出當醫療結論。
- 本條不支持出血量判斷、個人出血結束日、食物／運動處方。五天的群體依据另見 R03 `estimated-period-length`。
- 說明文案候選（待審）：月經期是經期出血的階段。這裡依日期估算，貼紙記錄保留妳實際記下的情況。

研究交稿：2026-10-07；`checked`／`expert` 待正式審核。
