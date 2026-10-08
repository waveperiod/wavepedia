---
id: luteal-phase
claim_zh: 自然有排卵週期的黃體期是排卵後黃體發揮作用的階段；部分研究顯示其長度與激素表現有變異
evidence: moderate
evidence_scope: 生理含義與不能從日期推定個人激素的限制
sources:
  - id: PMID:31482137
    doi: 10.1038/s41746-019-0152-7
    url: https://www.nature.com/articles/s41746-019-0152-7
    quote: "the corpus luteum forms"
    locator: Methods, Identification of ovulation day; short verbatim excerpt
    read: full
  - id: DOI:10.1016/j.fertnstert.2026.06.014
    doi: 10.1016/j.fertnstert.2026.06.014
    url: https://www.asrm.org/globalassets/_asrm/practice-guidance/practice-guidelines/pdf/diagnosis-and-treatment-of-luteal-phase-deficiency.pdf
    quote: "Progesterone levels peak in non-pregnancy cycles 6–8 days after ovulation."
    locator: 2026 opinion, page 633, PHYSIOLOGY OF NORMAL LUTEAL FUNCTION
    read: full
against:
  - id: PMID:32104920
    doi: 10.1111/ppe.12644
    url: https://pubmed.ncbi.nlm.nih.gov/32104920/
    quote: "within-woman variability in the follicular and luteal phases."
    locator: Abstract, Conclusions; short verbatim excerpt
    read: abstract
    relevance: 反對個人的黃體期每次都相同；不是否定黃體的生理機制
population: 自然且有排卵的非懷孕週期生理；來源樣本的年齡與排除條件不同，不外推為個人激素資訊
not_for: [單靠日期確認已排卵, 判定個人孕酮, 生育力或疾病判定, 激素避孕, 懷孕, 產後或哺乳的固定分期, PCOS 的固定分期, 圍絕經期的固定分期, 無排卵週期的四段推定]
used_by: [F05, F06, "string:todayPhaseLuteal", "string:todayCycleEstimated", "constant:CycleRules.estimatedLutealLengthDays"]
checked: 2026-10-07
expert: —
---

# 「黃體期」表示什麼

原始研究的分期方法以排卵日後到下一次經期前一天作黃體期 [1]；ASRM 2026 官方意見說明黃體與孕酮的生理作用及測量限制 [2]。三隊列原始研究摘要觀察同一女性不同週期的變化 [3]。

## 給 PM

- F06 `todayPhaseLuteal` 的實際字是「黃體期」；F05 在估計排卵日之後至設定 L 顯示這個模型區段。必須有「估算」，不能解讀為已確認排卵、孕酮較高或個人身體狀態。
- 生理說明只適用「已發生排卵」的自然週期；自述規律及有出血記錄不能由 Wave 證明這一前提。
- ASRM 是官方生理／臨床意見，不是對 Wave 的驗證。引用其中生理不等於採用疾病門檻、檢測或治療建議。
- 十四天預設的支持及反例另見 R03 `luteal-phase-length`；不以另一研究的平均數替換成人人固定十二天。
- 文案候選（待審）：黃體期是排卵後的階段。這裡依日期估算，不能確認妳已排卵或激素濃度。

研究交稿：2026-10-07；Claude 已於同日[正式查證](https://github.com/waveperiod/wavepedia/pull/2#issuecomment-6045658829)並填入 `checked`。`expert` 仍待簽核。2026-10-08 僅整理正文引用與書目，既有健康說法、來源原句與查證日期保留；本輪格式更新待 Reviewer 核對。

## 參考文獻

1. Bull JR, Rowland SP, Berglund Scherwitzl E, Scherwitzl R, Gemzell Danielsson K, Harper J. Real-world menstrual cycle characteristics of more than 600,000 menstrual cycles. NPJ Digit Med. 2019;2:83. doi:10.1038/s41746-019-0152-7. PMID: 31482137.
2. Practice Committee of the American Society for Reproductive Medicine and Practice Committee of the Society for Reproductive Endocrinology and Infertility, Gracia C, Jain T, Kalra S, Pier B, Sakkas D, et al. Diagnosis and treatment of luteal phase deficiency: a Committee Opinion. Fertil Steril. 2026;126(4):633-9. doi:10.1016/j.fertnstert.2026.06.014. PMID: 42414147.
3. Najmabadi S, Schliep KC, Simonsen SE, Porucznik CA, Egger MJ, Stanford JB. Menstrual bleeding, cycle length, and follicular and luteal phase lengths in women without known subfertility: A pooled analysis of three cohorts. Paediatr Perinat Epidemiol. 2020;34(3):318-27. doi:10.1111/ppe.12644. PMID: 32104920.
