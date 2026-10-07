# R03 · 算法假設交稿及查證清單

交稿：2026-10-07；Researcher。**待 Claude 查證，不是 checked／expert／pass。**

基線：wavepedia `bbf53b284573b15e12ec40be7dba62aa66a47b52`。只新增 claims／本文件，不修改既有 podcast 文章，不修改 App、PM 共用資料。

## 條目與證據

| 條目 | 支持與限制 | 閱讀層級 |
|---|---|---|
| [estimated-period-length](../claims/estimated-period-length.md) | 五天群體中心值有支持，另一隊列中心值六天；都不支持個人固定五天 | BioCycle、三隊列：abstract；NHS：full |
| [luteal-phase-length](../claims/luteal-phase-length.md) | 十四天的日曆假設及 ASRM 2026 範圍；大型原始研究反對人人固定十四天 | ASRM 2022、2026及 Bull：full；三隊列：abstract |
| [calendar-phase-estimate](../claims/calendar-phase-estimate.md) | 日期法不能確認本次階段；ASRM 亦承認記錄趨勢用途 | Johnson、Fehring：abstract；ASRM：full |

`moderate` 評的是條目內的限定說法，不是替常數或 Wave 的演算法打品質分數。未找到 Wave 貼紙模型的臨床驗證。

## App 精確對應（只讀）

2026-10-07 對照原 App 的 `Wave/Localizable.xcstrings`、`WaveKit/Sources/WaveKit/Domain/CycleRules.swift`、`CycleCalculator.swift` 和 `Wave/Features/Today/TodayCycleSection.swift`，App 基線 HEAD `b51c34a`；原目錄含使用者未提交工程／圖示，本次未修改。

| 實際 key／常數 | 此稿涵蓋 | UI 應看到的限制 |
|---|---|---|
| `estimatedPeriodLengthDays = 5` | estimated-period-length | 是日期區段，不代表第五天已停止出血 |
| `estimatedLutealLengthDays = 14` | luteal-phase-length | 是假設，不能確認排卵日或激素 |
| `todayPhaseMenstruation`＝月經期 | 五天＋calendar；名稱見 R02 PR #2 | 與「估算」同時顯示 |
| `todayPhaseFollicular`＝濾泡期 | 五天＋calendar；名稱見 R02 PR #2 | 同上；第六天標籤不證明已停血 |
| `todayPhaseOvulation`＝排卵期 | 十四天＋calendar；名稱見 R02 PR #2 | 同上；不能解讀為已排卵 |
| `todayPhaseLuteal`＝黃體期 | 十四天＋calendar；名稱見 R02 PR #2 | 同上；不提供激素／訓練判斷 |
| `todayCycleEstimated`＝估算 | 三條共同限制 | 是模型資訊，未驗證個人階段 |
| `todayCycleDay`＝週期第 %lld 天 | calendar，從認定起點日計數 | 無 phase 時可保留真實經過天數，不自動繞回第 1 天 |
| `todayCycleTitle`＝週期資訊 | calendar | 無經期／不確定選項按既定規則隱藏整卡 |
| `todayPhaseDuring`＝經期記錄中 | calendar 的產品規則段 | 只表示記錄仍在漏記容許窗口 |
| `todayPhaseAfter`＝最近經期記錄之後 | 同上 | 不表示生理出血已結束 |
| `beforePeriod`／「前」新 key | 原 App 尚無；等 cycle／recording 實際新增後補 mapping | 至少三個真實起點、兩完整週期；一定是估算，不是 PMS／黃體期證明 |

2026-10-07 協調 `cycle-status.json` 後續已記錄前 **3 天**、中容許漏記 **1 天**、至少 **2 個完整週期／3 個起點**。這些是產品決策，不是本稿從研究推得的 N；仍待 cycle 交最終實作常數／新 key 核對。兩個過往週期足夠啟用是產品門檻，沒有臨床驗證。15 天新週期分組也不是医学分類。

R02 四個名稱條目已另交 [draft PR #2](https://github.com/waveperiod/wavepedia/pull/2)，同樣未 checked／expert；兩項不因開 PR 而解除 F06 gate。

## 來源定位與版本

- PMID:22350580／DOI:10.1093/aje/kwr356：PubMed Abstract。PMC 網頁有瀏覽檢查，全文未作此條的引用依據。
- PMID:32104920／DOI:10.1111/ppe.12644：PubMed Abstract 的 Methods／Results／Conclusions。PMC／Europe PMC 開啟未成功，只標 abstract。
- PMID:31482137／DOI:10.1038/s41746-019-0152-7：[出版社原文](https://www.nature.com/articles/s41746-019-0152-7)讀 Abstract、Results、Discussion、Methods（含 Inclusion/exclusion）、利益關係。樣本僅辨識為排卵且資料足夠的週期；排除激素避孕、PCOS／甲狀腺低下／內膜異位自述及更年期症狀等。作者公司利益與排卵算法限制不能忽略。人口平均不能當個人參數。
- PMID:34815068／DOI:10.1016/j.fertnstert.2021.10.007：[ASRM 官方全文](https://www.asrm.org/practice-guidance/practice-committee-documents/optimizing-natural-fertility-a-committee-opinion-2021/)，FERTILITY-AWARENESS METHODS；網址尾碼 2021，刊出年份 2022。只使用估算假設與限制，不把備孕指導搬進 Wave。
- DOI:10.1016/j.fertnstert.2026.06.014：[ASRM 2026 官方 PDF](https://www.asrm.org/globalassets/_asrm/practice-guidance/practice-guidelines/pdf/diagnosis-and-treatment-of-luteal-phase-deficiency.pdf)，633頁生理、634頁人群、635頁變異／測量、636–637頁診断／治療限制。PDF 首頁核對 DOI，2026-07-07 online、2026-10期。與 2021 PMID:33827766 不混用；不引用疾病門檻到 App。
- PMID:29749274／DOI:10.1080/03007995.2018.1475348、PMID:16700687／DOI:10.1111/j.1552-6909.2006.00051.x：PubMed 原始研究摘要；前者有產業作者隸屬，後者電子尿液激素監測而非 Wave 的純日期法。
- NHS Periods：官方衛教全文，頁面標示 last reviewed 2023-01-05，review due 2026-01-05；網站未給 DOI／PMID，以官方識別符另列，不偽造期刊號。其數字是概略衛教資料，並非算法驗證。

所有來源親自讀到引用的短英文片段；摘句保留其文意。引用／來源識別符的格式檢查不代替 Claude 的逐句查證。

## Researcher 本次已執行

- [x] 三條有 claim、evidence／scope、sources、against、population、not_for、used_by、checked／expert 未審。
- [x] 原句、DOI／PMID（官方 NHS 明示不提供）、來源定位與 full／abstract 層級列出。
- [x] 比較支持與不支持，區分個體變異、取樣及測量方法限制。
- [x] 原 App key 與 5／14／15 常數只讀比對，未修改 App 或共享 PRD／決策。
- [x] 字串／產品窗口的限制與特殊人群交接。
- [ ] Claude 核對原句、等級、人群及 used_by，填 checked。
- [ ] 專家簽核 expert。
- [ ] recording 在 iOS 26.0／26.5 操作 App，驗標籤、估算、空／大字狀態並交截圖；Researcher 沒有聲稱論文經 simulator 驗證。

## 給 recording 的驗收案例（未執行）

規律 L=28：第 1／5 天月經期，第 6／13 天濾泡期，第14天排卵期，第15／28天黃體期，四者均顯示「估算」。第29天保留日期計數但階段空；L≤20 的空 phase 是模型限制。真實第6天仍有出血時，現行規律模型仍可能顯示濾泡期，不應宣稱出血結束。

不規律：「前」只在記錄足夠時依平均估，顯示「估算」；記錄不足不顯前。最近出血（含開始日）在批准 N 天内為「中」，N+1 為「後」；未貼貼紙不代表停止出血。前／中／後的最新 key 和窗口值由 App 返修會話交回後補查，不能以本稿舊 key 靜態核對代替整合验收。
