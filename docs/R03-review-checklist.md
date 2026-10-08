# R03 · 算法假設交稿及查證清單

交稿：2026-10-07；收尾更新：2026-10-08。**三條 `checked: 2026-10-07` 已由 Claude 填入；`expert` 仍未簽核。** [正式查證評論](https://github.com/waveperiod/wavepedia/pull/1#issuecomment-6045659263)對應 Reviewer 提交 `04e5463809ebfd280cdd356eec4f433af025af73`，本輪保留該提交及繁體字修正。

本輪依最新 Researcher 規則整理 Vancouver 正文編號與參考文獻，保留健康說法、原句、來源與閱讀層級。既有 ASRM 2026 DOI 的書目補 PMID:42414147。「預估經期前」與 3／2／1 產品規則另補精確 mapping；**新增映射和書目格式待 Claude 複核，既有 checked 日期不涵蓋新增部分。本清單不宣告 F06 pass／done。**

基線：wavepedia `bbf53b284573b15e12ec40be7dba62aa66a47b52`。只涉及本 PR 的三條 claims／本文件，不修改既有 podcast 文章、App 或 PM 共用資料。

## 條目與證據

| 條目 | 支持與限制 | 閱讀層級 |
|---|---|---|
| [estimated-period-length](../claims/estimated-period-length.md) | 五天群體中心值有支持，另一隊列中心值六天；都不支持個人固定五天 | BioCycle、三隊列：abstract；NHS：full |
| [luteal-phase-length](../claims/luteal-phase-length.md) | 十四天的日曆假設及 ASRM 2026 範圍；大型原始研究反對人人固定十四天 | ASRM 2022、2026及 Bull：full；三隊列：abstract |
| [calendar-phase-estimate](../claims/calendar-phase-estimate.md) | 日期法不能確認本次階段；ASRM 亦承認記錄趨勢用途 | Johnson、Fehring：abstract；ASRM：full |

`moderate` 評的是條目內的限定說法，不是替常數或 Wave 的演算法打品質分數。未找到 Wave 貼紙模型的臨床驗證。

## App 精確對應（只讀）

原交稿對照 App HEAD `b51c34a`。本輪對照 [F06 PR #6](https://github.com/waveperiod/ios-app/pull/6) 當前 HEAD `4fa9e56ee5e2aa1bcc445fbf9a9cd0e852689658` 的已提交 `Wave/Localizable.xcstrings`、`WaveKit/Sources/WaveKit/Domain/CycleRules.swift`、`CycleCalculator.swift` 和 `Wave/Features/Today/TodayCycleSection.swift`。只讀 Git 物件；本次未修改 App 或使用者檔案。

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
| `todayPhaseBefore`＝預估經期前 | calendar；`.beforePeriod` 對應的實際 key | 同時顯示「估算」；不確認下次開始日或生理階段 |
| `beforePeriodWindowDays = 3` | calendar 的產品規則段 | 只在估計開始日前 1–3 天顯示；三天沒有被本條驗為臨床有效窗口 |
| `minimumCompletedCyclesForBefore = 2` | 同上 | 至少兩個完整起點間隔／三個產品認定的實際起點；是啟用門檻，不是醫學結論 |
| `recentBleedingGraceDays = 1` | 同上 | 「中」記錄窗口優先於「前」；未記錄不證明出血結束 |

上述 **3／1／2** 已與 F06 HEAD `4fa9e56` 的集中常數及計算分支核對：已完成起點間隔取平均、四捨五入至整天，剩餘 1–3 天才顯示「前」且 `isEstimated: true`；資料不足不借 onboarding 預設補值，也不建立預測起點。這些是產品決策，不是從本稿研究推得的醫學窗口或門檻。起點分組仍依 F05 的產品實作，本輪不宣告其臨床有效性或對後續 App 修改已驗收。

R02 四個名稱條目另見 [PR #2](https://github.com/waveperiod/wavepedia/pull/2)，其四條亦已有 Claude 的 `checked: 2026-10-07`，expert 未簽；兩 PR 本輪更新的審核與 F06 最終狀態由 PM／Claude 處理。

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

- [x] 三條有完整 frontmatter；保留 Claude 的 `checked: 2026-10-07`，expert 均為「—」，沒有由 Researcher 代填。
- [x] 原句、DOI／PMID（官方 NHS 明示不提供）、來源定位與 full／abstract 層級列出。
- [x] 比較支持與不支持，區分個體變異、取樣及測量方法限制。
- [x] F06 PR HEAD 的所有 used_by key 與 5／14／3／2 常數只讀比對，新增 before key 精確對應 calendar-phase-estimate，未修改 App 或共享 PRD／決策。
- [x] 字串／產品窗口的限制與特殊人群交接。
- [x] Claude 2026-10-07 正式核對三條既有內容並填 checked；評論與提交見上。
- [x] 三條正文採 Vancouver 編號，與 frontmatter 來源一一對應；期刊列 DOI／PMID，NHS 列網址與原閱讀日期。
- [ ] Claude 複核本輪新增 before key、3／2／1 產品規則映射及 Vancouver 書目格式；既有 checked 不代替新增部分的審核。
- [ ] 專家簽核 expert。
- [ ] recording 在 iOS 26.0／26.5 操作 App，驗標籤、估算、空／大字狀態並交截圖；Researcher 沒有聲稱論文經 simulator 驗證。

## 給 recording 的驗收案例（未執行）

規律 L=28：第 1／5 天月經期，第 6／13 天濾泡期，第14天排卵期，第15／28天黃體期，四者均顯示「估算」。第29天保留日期計數但階段空；L≤20 的空 phase 是模型限制。真實第6天仍有出血時，現行規律模型仍可能顯示濾泡期，不應宣稱出血結束。

不規律：至少兩個完整間隔／三個起點，依平均值估計開始日前 1–3 天顯示「預估經期前」和「估算」；資料不足不顯前。最近出血（含開始日）後 1 天仍為「中」，超過窗口為「後」；新出血的「中」窗口優先於「前」。未貼貼紙不代表停止出血。本輪只完成靜態 mapping，不能代替 recording 的整合 UI 驗收。
