# Wavepedia — Claude 工作指令

## 这是什么

Wavepedia 是 Wave App 的女性健康知识库。拒绝以男性样本为默认的研究体系。

## Git 同步规则

**每次完成知识库更新后，必须 commit 并 push 到：**

```
https://github.com/waveperiod/wavepedia.git
```

分支：`main`

### 操作流程

```bash
# 在 wavepedia 根目录执行
git add .
git commit -m "[简要描述本次更新的内容]"
git push origin main
```

### Commit message 格式

```
add: [新增文章或章节名]
update: [更新的文章名] — [改了什么]
fix: [修正内容]
```

示例：
- `add: nutrition/creatine-women.md — 肌酸与女性全生命周期`
- `update: INDEX.md — 增加BFR训练词条`
- `add: sources/huberman-lab/2026-03-30_breedlove.md`

---

## 知识库结构

```
wavepedia/
├── INDEX.md                    总目录
├── CLAUDE.md                   本文件（工作指令）
├── pharmacology/               药物与物质代谢
├── nutrition/                  营养与补剂
├── lifestyle/                  生活方式
├── training/                   训练方法
├── metabolism/                 代谢健康
├── glossary/                   词汇表
└── sources/                    原始来源档案
    ├── huberman-lab/
    ├── found-my-fitness/
    └── peter-attia/
```

## 每篇文章的必须包含

1. **核心结论（一句话）** — 让用户不用读完就知道这篇的价值
2. **机制说明** — 说清楚"为什么"，不只是"是什么"
3. **月经周期各阶段建议** — 卵泡期 / 排卵期 / 黄体期 / 月经期的具体行动指引
4. **来源链接** — 原始论文或播客的 URL，不是二手转述
5. **常见误解** — 破除"以男性为默认"的错误建议

## 来源质量标准

- ✅ 同行评审研究（PubMed、PMC、Tandfonline 等）
- ✅ 有女性受试者数据（需标注受试者特征）
- ✅ 按月经周期阶段分层分析的研究
- ⚠️ 播客引用 — 需要追溯到一手研究（Rhonda Patrick 等专家的引用通常可靠）
- ❌ 不引用无原始来源的二手科普内容
