# 知识库规则

## 领域范围

本知识库用于整理一个科研方向的领域知识库，覆盖从文献收集、论文笔记、概念整理、方法比较、数据集与指标梳理，到研究空白发现、创新点评估和实验验证的全过程。

使用前，先在本文件的”领域范围”中填写当前研究方向，并根据需要调整”标签体系”。

## 三层结构

```text
wiki/
├── SCHEMA.md
├── index.md
├── log.md
├── README.md
├── overview.md
├── raw/             # 原始资料层：不可变来源材料
│   ├── articles/
│   ├── papers/
│   ├── transcripts/
│   └── assets/
├── entities/                 # 人物、机构、模型、系统、项目
├── concepts/                 # 关键术语、理论问题、机制
├── comparisons/                 # 方法、系统、论文、路线对比
├── queries/             # 值得保留的问题回答和综合分析
├── problems/             # 研究问题与任务定义
├── methods/                 # 方法族与技术路线
├── datasets/               # 数据集、评测基准、数据构造方式
├── baselines/              # 必须比较的基线方法与比较协议
├── metrics/                 # 指标定义、适用边界和常见误用
├── failure-cases/             # 失败案例、负结果、方法边界
├── gaps/             # 候选研究空白
├── _meta/             # 主题地图、维护报告、检查结果
└── _archive/                 # 已废弃或被替代页面
```

## 命名规范

- 目录名和文件名使用小写英文、数字和连字符，例如 `generated-evidence-selection.md`。
- 目录名和文件名不使用空格、中文或特殊符号。
- 页面标题可以是中文。
- 一个页面只覆盖一个清晰概念、问题、方法或研究空白。
- 页面超过约 200 行时应拆分成子页面。

## 页面元数据

每个知识页必须以 YAML 元数据开头。字段名保持英文，字段含义使用中文解释：

```yaml
---
title: 页面标题
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | problem | method | dataset | baseline | metric | failure-case | gap | overview
tags: []
sources: []
confidence: high | medium | low
status: draft | active | needs-review | archived
---
```

字段说明：

- `type`：页面类型，枚举值保留英文，便于工具校验。
- `tags`：只能使用“标签体系”中已有标签；需要新标签时先更新本文件。
- `sources`：引用的原始材料、论文笔记、实验记录或外部链接。
- `confidence`：当前页面主张的可信度，含义分别为高、中、低。
- `status`：页面状态。未核验页面用 `needs-review`。

## 原始资料元数据

`raw/` 下的来源材料也应有元数据：

```yaml
---
source_type: paper | article | transcript | meeting | code | dataset | other
source_url:
ingested: YYYY-MM-DD
sha256:
notes:
---
```

`raw/` 是原始资料层，默认不修改正文。若来源变动，新建版本或在 `log.md` 中记录。

## 标签体系

初始标签：

- `literature`：文献与综述
- `paper-note`：论文笔记
- `problem`：研究问题
- `method`：方法族
- `dataset`：数据集
- `baseline`：基线方法
- `metric`：评估指标
- `gap`：研究空白
- `idea`：创新点
- `experiment`：实验
- `failure-case`：失败案例
- `evidence`：证据与来源
- `provenance`：来源追踪
- `review`：审稿人视角
- `needs-verification`：待核验

规则：页面中使用的新标签必须先加入本节，避免标签膨胀。

## 页面创建规则

创建新页面的条件：

- 一个概念、实体或方法在 2 个以上来源中反复出现。
- 或者虽然只出现一次，但它是当前研究问题的核心。
- 或者它会影响 gap 判断、实验设计或论文论证。

不要创建页面的情况：

- 只是过路术语。
- 与当前研究方向无关。
- 没有来源支撑的临时想法。临时想法应先放到 `ideas/` 或 `queries/`。

## 页面类型要求

### 实体页 `entities/`

用于人物、机构、模型、系统、项目、工具。

应包含：
- 它是什么；
- 关键事实；
- 与哪些概念、方法、论文相关；
- 来源链接。

### 概念页 `concepts/`

用于关键术语和机制。

应包含：
- 定义；
- 领域中的作用；
- 相关论文；
- 未解决问题；
- 相关页面链接。

### 问题页 `problems/`

用于研究问题或任务定义。

应包含：
- 问题定义；
- 为什么重要；
- 已有解决路线；
- 现有不足；
- 相关研究空白。

### 方法页 `methods/`

用于方法族和技术路线。

应包含：
- 方法假设；
- 代表论文；
- 适用场景；
- 局限性；
- 必须比较的基线方法。

### 数据集页 `datasets/`

应包含：
- 数据来源；
- 任务设置；
- 许可和可用性；
- 常用指标；
- 已知偏差和限制。

### 研究空白页 `gaps/`

应包含：
- 一句话研究空白；
- 已有工作做到哪里；
- 还缺什么；
- 为什么重要；
- 可验证实验；
- 基线、数据集和指标；
- 审稿人可能质疑什么；
- 当前判断。

## 交叉引用规则

- 每个知识页至少包含 2 个 `[[wikilinks]]`，除非是刚创建的草稿页。
- 新页面创建后必须加入 `index.md`。
- 每次新增、更新、归档页面都要写入 `log.md`。
- 重要综合页面应追溯到 `wiki/raw/`、`literature/paper-notes/` 或 `experiments/`。

## 冲突与低可信内容

当新资料与旧页面冲突时：

1. 不要直接覆盖旧结论。
2. 记录两个说法的来源和日期。
3. 将页面 `status` 改为 `needs-review`。
4. 将 `confidence` 降为 `low` 或 `medium`。
5. 在 `log.md` 记录冲突。

## 输出语言

除原始论文标题、术语、代码名和引用外，Wiki 页面默认使用中文。
