---
title: "{Title}"
method_name: "{MethodName}"
authors: [{Authors}]
year: {Year}
venue: {Venue}
tags: [{tags}]
zotero_collection: {zotero_path}
image_source: online  # online（默认）/ mixed / local
arxiv_html: {arxiv_html_url}  # 如有
ieee_url: {ieee_url}  # 如有
doi: {doi}  # 如有
created: {date}
---

# 论文笔记：{Title}

## 元信息

| 项目 | 内容 |
|------|------|
| 机构 | {Affiliations} |
| 日期 | {Month Year} |
| 项目主页 | {project_page_url} |
| 链接 | [arXiv]({arxiv_url}) / [IEEE]({ieee_url}) / [DOI](https://doi.org/{doi}) / [Code]({code_url}) |

---

## 论文解析树

> 以下五级结构与「论文解析例」脑图一致：**摘要 → 引言 → 方法 → 实验 → 局限**。  
> Contribution 每项必须 **两句**：一句介绍、一句收益/优势。  
> 引言中的每个 challenge 必须写清：**Previous method / Limitation / Technical reason**。  
> **图表**：在对应小节内嵌入 **关键图/表**（`![](url)` 或 `![[本地.png]]`）；**全部** 图/表仍须在文末 `## 关键图表` 按编号列全。

### 1. 摘要 Abstract

- **Task（任务）**:
- **Previous methods 的技术难点**:
- **Key insight / Motivation（一句话）**:
  - Insight 一句话:
  - 收益一句话（可选，若后文已写可写「见贡献 1」）:
- **Technical contributions**
  - **Contribution 1**: （一句介绍） / （一句收益）
  - **Contribution 2**: （一句介绍） / （一句收益）
  - **Contribution 3**: （一句介绍） / （一句收益）（按需增减）
- **Experiment（摘要中的实验结论）**:

<!-- 可选：Teaser / 任务示意图（常见 Fig.1），无则删本节 -->
**图示**:

![Figure 1: {一句话}]({arxiv_or_project_image_url})

### 2. 引言 Introduction

- **Task and application**:
- **Previous methods 的技术难点（展开）**
  - **Challenge 1**
    - Previous method:
    - Limitation / Failure cases:
    - Technical reason（失败的技术原因）:
  - **Challenge 2**
    - Previous method:
    - Limitation / Failure cases:
    - Technical reason:
  - **Challenge 3**（按需增减）:
    - Previous method:
    - Limitation / Failure cases:
    - Technical reason:
- **Our pipeline（解决路径）**
  - 一句话总述关键创新/insight:
  - **Contribution 1**: 解决什么问题 / 如何实现 / 优势或 insight
  - **Contribution 2**: 解决什么问题 / 如何实现 / 优势或 insight
  - **Contribution 3**（按需增减）:
- **Cool demos / applications**:

### 3. 方法 Method

- **Overview**
  - **Specific task**: Input: … / Output: …
  - **Method steps**: Step 1: … / Step 2: … / Step 3: …

**Pipeline / 系统主图**（常见 Fig.2，与上列 Step 对应）:

![Figure 2: {pipeline 标题}]({arxiv_or_project_image_url})

> 读图说明：图中 A/B/C… 模块分别对应上文 Step …。

- **Pipeline modules**
  - **Module 1: {名称}**
    - Motivation:
    - Implementation:
    - Mechanism（为何有效）:
    - Technical advantage:
  - **Module 2: {名称}**
    - Motivation:
    - Implementation:
    - Mechanism:
    - Technical advantage:

<!-- 若某子模块有独立结构图，紧接在该 Module 下插入：![Figure N: …](url) -->

<!-- 正文中首次出现的技术名词用 [[概念]] 内联链接 -->

### 4. 实验 Experiments

- **Comparison experiments**
  - 结论要点（与 SOTA / 主表一致）:
  - **主结果图或表**（嵌入一张最具代表性的；其余见文末「关键图表」全量）:

![Figure {N}: main results]({url})

| Method | … |  … |
|--------|---|-----|
| … | … | … |

- **Ablation studies**
  - 各贡献/模块去掉后的影响:
  - **关键消融图/表**（可选嵌入）:

![Figure {N}: ablation]({url})

### 5. 局限性 Limitation

- {局限 1} — **为何存在**:
- {局限 2} — **为何存在**:

---

## 关键公式

<!-- 论文中所有重要公式必须出现在此；每项含 [[概念|名称]]、$$…$$、含义、符号说明 -->

### 公式1: [[{概念名}|{公式用途}]]

$$
{公式内容}
$$

**含义**:

**符号说明**:

{… 列出论文中所有重要公式 …}

---

## 关键图表

<!-- 全量清单：论文中每一个 Figure、Table 必须在此按编号列出（零遗漏）。解析树内已嵌入的图可重复出现或写「同 Figure N 见上文」。 -->

### Figure 1: …

![[{MethodName}_fig1_….png]]

**说明**:

### Table 1: …

| … |
|---|

**说明**:

{… 列出论文中所有 Figure/Table …}

---

## 实验结果

<!-- 与「论文解析树 → 4. 实验」呼应：侧重数字、主表、主图结论；可引用上节图表 -->

### 对比实验（要点）

### 消融实验（要点）

---

## 文献树定位

- 在 literature tree 中的位置（技术路线 / 创新等级 S-A-B-C）:
- 是否影响 Milestone Tasks:

## 挑战-洞察映射

- **Challenge** → **Insight** → 与本论文的关联:

---

## 关联笔记

### 基于
- [[{前置工作}]]:

### 对比
- [[{对比方法}]]:

### 方法相关
- [[{核心技术}]]:

---

## 速查卡片

> [!summary] {Title}
> - **Task**:
> - **Key insight**:
> - **Main contribution**:
> - **Limitation**:

---

*笔记创建时间: {timestamp}*
