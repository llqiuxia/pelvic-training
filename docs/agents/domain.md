# 领域文档（Domain Docs）

工程技能在探索代码库时应如何使用本仓库的领域文档。

## 探索前先阅读

- **`CONTEXT.md`**（仓库根目录），或
- **`CONTEXT-MAP.md`**（如果存在——指向每个子上下文各自的 `CONTEXT.md`）。阅读与当前主题相关的每个上下文。
- **`docs/adr/`**——阅读涉及你即将修改的领域的 ADR。在多上下文仓库中，同时也检查 `src/<context>/docs/adr/` 下是否有上下文级决策。

如果这些文件不存在，**静默跳过**。不要提示缺失，也不要建议立即创建。生产者技能（`/grill-with-docs`）会在术语或决策实际被讨论时惰性地创建它们。

## 文件结构

单上下文仓库（大多数仓库）：

```
/
├── CONTEXT.md
├── docs/adr/
│   ├── 0001-event-sourced-orders.md
│   └── 0002-postgres-for-write-model.md
└── src/
```

多上下文仓库（根目录存在 `CONTEXT-MAP.md`）：

```
/
├── CONTEXT-MAP.md
├── docs/adr/                          ← 全局决策
└── src/
    ├── ordering/
    │   ├── CONTEXT.md
    │   └── docs/adr/                  ← 上下文级决策
    └── billing/
        ├── CONTEXT.md
        └── docs/adr/
```

## 使用词汇表中的术语

当输出中命名一个领域概念时（在 issue 标题、重构建议、假设、或测试名称中），使用 `CONTEXT.md` 中定义的术语。不要偏离到词汇表明确避免的同义词。

如果你需要的概念不在词汇表中，这是一个信号——要么你在使用项目不用的语言（重新考虑），要么存在一个真实的缺口（记录以备 `/grill-with-docs` 使用）。

## 标记 ADR 冲突

如果输出与现有 ADR 矛盾，明确提出来，而不是静默覆盖：

> _与 ADR-0007（事件溯源订单）冲突——但值得重新讨论，因为…_
