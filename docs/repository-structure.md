# 仓库结构

## 顶层目录

| 路径 | 用途 |
| --- | --- |
| `literature/` | 检索记录、元数据、筛选记录和结构化论文笔记。 |
| `wiki/` | 按问题、方法、数据集、基线、指标、失败案例和研究空白组织的领域知识库。 |
| `ideas/` | 候选研究想法、创新点评估和审稿风险分析。 |
| `experiments/` | 实验代码和脚本。每个实验一个子目录，含实验日志和配置。 |
| `data/` | 实验最终输出的结果数据，例如评测结果表和指标汇总文件。 |
| `meetings/` | 组会记录、反馈和后续待办事项。 |
| `writing/` | 论文、报告、返修回复和汇报材料。 |
| `templates/` | 可复用模板。 |

## 命名规范

- 目录名和文件名保持英文，便于跨工具检索、版本管理和 GitHub 展示。
- 面向人阅读的标题、说明、模板字段和汇报内容使用中文。
- 带日期的记录使用 `YYYY-MM-DD` 前缀。
- 实验使用稳定编号，例如 `exp-001`。
- 知识库页面保持一页一个概念。

## 示例

```text
literature/paper-notes/2026-graph-rag-survey.md
wiki/methods/graph-rag.md
wiki/gaps/generated-evidence-selection-bias.md
ideas/idea-001-evidence-selection-failure.md
experiments/exp-001-generated-evidence-usage/
meetings/2026-06-29-group-meeting.md
```

## Git 管理策略

Git 只管理文本、配置、模板和小型元数据。

Git 不管理：

- 论文全文
- 数据集
- 模型权重
- 原始日志
- 生成图表和输出
- 密钥

大型文件使用外部链接、文献管理工具、数据版本工具、发布资产或云存储管理。
