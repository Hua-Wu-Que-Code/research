# 科研流程知识库

这是一个公开的科研流程模板仓库，用来管理从找文献到构建领域知识库、发现研究空白、评估创新点、设计实验和整理写作材料的完整流程。

## 总流程

```text
找文献 -> 整理论文 -> 构建领域知识库 -> 发现研究空白
-> 评估创新点 -> 做实验 -> 写作与复盘 -> 回写知识库
```

这个仓库不用于保存论文全文、大型数据集或模型权重，而是用于保存研究过程中的结构化记录，让每个判断都能追溯到文献、知识库页面或实验记录。

## 目录结构

```text
research/
├── README.md
├── AGENTS.md
├── TODO.md
├── literature/
│   ├── searches/
│   ├── metadata/
│   ├── paper-notes/
│   └── screening/
├── wiki/
│   ├── SCHEMA.md
│   ├── index.md
│   ├── log.md
│   ├── overview.md
│   ├── raw/
│   │   ├── articles/
│   │   ├── papers/
│   │   ├── transcripts/
│   │   └── assets/
│   ├── entities/
│   ├── concepts/
│   ├── comparisons/
│   ├── queries/
│   ├── problems/
│   ├── methods/
│   ├── datasets/
│   ├── baselines/
│   ├── metrics/
│   ├── failure-cases/
│   └── gaps/
├── ideas/
├── experiments/
├── data/
├── meetings/
├── writing/
├── templates/
└── docs/
```

## 快速开始

Fork 或 clone 本仓库后，在仓库根目录打开 Codex，把研究方向告诉它：

```
我的研究方向是 [在此填写方向]，帮我填写 wiki/overview.md，并完成 TODO.md 中的初始化任务。
```

Codex 会自动读取 `AGENTS.md` 中的规则，引导你完成初始化。

## 使用方式

1. 在 `wiki/overview.md` 中填写当前研究方向。
2. 在 `literature/searches/` 中保存第一份检索记录。
3. 将 3 到 5 篇代表论文整理到 `literature/paper-notes/`。
4. 从论文笔记中抽取页面，写入 `wiki/problems/`、`wiki/methods/`、`wiki/gaps/`。
5. 选择一个研究空白，在 `ideas/` 中写创新点评估。
6. 如果创新点值得继续，在 `experiments/` 中创建实验记录。
7. 将实验结果、组会反馈和下一步任务回写到知识库和 `TODO.md`。

## 版本控制规则

建议纳入版本控制：

- 文献笔记、领域知识库页面、检索记录、实验记录和模板。
- 允许公开的轻量元数据。
- 用于复现实验分析的轻量脚本和配置。

不要纳入版本控制：

- 受版权保护的论文全文。
- 大型数据集、模型权重、原始实验输出、运行日志。
- 接口密钥、私人评审材料或个人隐私数据。

大型文件和受版权保护的材料应放在外部存储、文献管理工具、数据版本工具或云盘中，并在仓库中保存索引和说明。
