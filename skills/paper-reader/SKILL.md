---
name: paper-reader
description: |
  Use when user asks to "read paper", "analyze paper", "summarize paper",
  "读论文", "分析文献", "帮我看一下这篇paper", "论文笔记", or provides a PDF file
  that appears to be an academic paper. Specialized for CV/DL papers.

  Also supports Zotero integration: "读一下这篇论文 ...", "快速看一下这篇论文 ...",
  "批判性分析这篇论文 ...", "读一下 Zotero 里的 XXX", "批量读一下 Zotero 里 VLA 分类下的论文"

  **重要触发词**: "读一下 XXX"、"读一下这篇"、"帮我读" → 必须调用此 skill
context: fork
allowed-tools: Bash, Read, Write, Edit, Glob, Grep, WebFetch, WebSearch
---

> **开始前**: 先跟用户打个招呼 🐕

# 学术论文阅读助手 (Paper Reader)

专注 CV/DL 领域，支持 Zotero 集成和 Obsidian 笔记保存。

## Step 0: 读取共享配置

先读取 `../_shared/user-config.json`，如果 `../_shared/user-config.local.json` 存在，再用它覆盖默认值。

显式生成并在后续统一使用这些变量：

- `VAULT_PATH`
- `NOTES_PATH`
- `CONCEPTS_PATH`
- `ZOTERO_DB`
- `ZOTERO_STORAGE`
- `AUTO_REFRESH_INDEXES`
- `GIT_COMMIT_ENABLED`
- `GIT_PUSH_ENABLED`

其中：

- `NOTES_PATH = {VAULT_PATH}/{paper_notes_folder}`
- `CONCEPTS_PATH = {NOTES_PATH}/{concepts_folder}`
- `GIT_PUSH_ENABLED` 只有在 `GIT_COMMIT_ENABLED=true` 时才可能为真

后续统一使用上面的变量。

## 1. 接收论文

| 输入方式 | 示例 | 处理方法 |
|----------|------|----------|
| PDF 路径 | `/path/to/paper.pdf` | 直接 Read |
| arXiv 链接 | `https://arxiv.org/abs/xxxx` | WebFetch |
| IEEE Xplore 链接 | `https://ieeexplore.ieee.org/...` | WebFetch（登录态浏览器可手动辅助） |
| DOI 链接 | `https://doi.org/...` | WebFetch |
| Zotero 分类 | "VLA 分类的论文" | 查询数据库 → 列出 → 用户选择 |
| Zotero 搜索 | "Zotero 里的 π0.5" | 搜索标题 → 找到 PDF |
| 无 PDF | Zotero 条目无附件 | 从网上获取（见下方） |

### 无 PDF 时的获取流程

1. `python3 assets/zotero_helper.py info {item_id}` 获取论文信息
2. 按优先级获取：arXiv HTML > IEEE Xplore/DOI > arXiv PDF > WebSearch 标题
3. 判断 arXiv ID：从 URL / Zotero extra 字段 / 标题搜索
4. 推荐直接 WebFetch `https://arxiv.org/html/{arxiv_id}`，无需下载
5. 跳过条件：既无 PDF 也无在线来源 / 非论文内容

> Zotero 详细操作见 `references/zotero-guide.md`

## 2. 阅读模式

| 模式 | 触发词 | 输出 |
|------|--------|------|
| **快速摘要** | "快速看一下"、"quick" | 3-5 句核心贡献 |
| **完整解析** | "详细分析"、默认 | 结构化笔记（用模板） |
| **批判分析** | "批判性分析"、"critique" | 方法论优缺点评估 |
| **知识提取** | "提取公式"、"技术细节" | 公式 + 算法伪代码 |

## 2.5 论文解析树阅读法（强制，与用户脑图一致）

单篇笔记的**主分析骨架**必须按下面五级结构展开（与「论文解析例 / PPDIA-3D 式」脑图同构），**禁止**用零散段落替代。

### 三层阅读目标（仍适用）

1. **层次 1（读懂细节）**：术语、公式、模块、训练/推理流程可复述
2. **层次 2（理解动机）**：明确论文解决什么问题，为什么这样设计
3. **层次 3（放入文献树）**：明确其在 literature tree 的位置、limitation、是否影响 milestone tasks

### 执行要求（章节不可省略）

生成笔记时，`## 论文解析树` 下必须包含以下**五级标题与子项**（与模板 `assets/paper-note-template.md` 一一对应）：

1. **### 1. 摘要 Abstract**
   - **Task**：本文要解决的任务
   - **Previous methods 的技术难点**：前人方法卡在哪
   - **Key insight / Motivation（一句话）**：核心洞见（区别于 contribution 的“高层想法”）
     - Insight 一句话；收益一句话（可与后文合并，但不得缺）
   - **Technical contributions**：逐项写，每项 **两句**：一句介绍贡献、一句说明收益/优势
   - **Experiment**：摘要中提到的实验结论（一句话即可）

2. **### 2. 引言 Introduction**
   - **Task and application**：任务与应用场景
   - **Previous methods 的技术难点（展开）**：每个 challenge 写清 **Previous method / Failure 或 Limitation / Technical reason（失败的技术原因）**
   - **Our pipeline（解决路径）**：先一句总述关键创新；再按 **Contribution 1, 2, …** 写清「解决什么问题 / 如何实现 / 优势或 insight」
   - **Cool demos / applications**：若有演示、典型应用，单独列出

3. **### 3. 方法 Method**
   - **Overview**：**Input / Output**；**Method steps**（Step 1, 2, 3…）
   - **Pipeline modules**：每个模块写 **Motivation / Implementation / Mechanism（为何有效）/ Technical advantage**

4. **### 4. 实验 Experiments**
   - **Comparison experiments**：与基线对比的结论
   - **Ablation studies**：核心贡献与各 pipeline 模块设计对性能的影响

5. **### 5. 局限性 Limitation**
   - 每条 limitation 必须附带 **为何存在该局限** 的合理解释（不能只列标题）

#### 图表在「论文解析树」中的嵌入规则（与脑图一致、可读性优先）

- **目标**：读者在只读「论文解析树」时，就能 **看到** 论文最关键的 **示意图 / 流程图 / 主结果表**，不必翻到文末才见到图。
- **嵌入位置（按论文实际编号调整）**：
  - **摘要**末尾或 **引言**末尾：可放 **Teaser / Fig.1**（系统总览、任务示意），用 `![Figure 1: …](url)` 或 Obsidian 本地图链。
  - **方法 → Overview** 之后：必须放 **Pipeline / 系统结构主图**（常见为 Fig.2 或论文中的 overview 图），紧接 **1–2 句**说明该图与步骤对应关系。
  - **方法 → Pipeline modules**：若某模块有 **独立结构子图**，可在该 **Module** 小节下嵌入对应 Figure（避免所有图堆在 Overview）。
  - **实验**：在 **Comparison** 下嵌入 **主结果表**（优先 Markdown 表格复现；无法复现时嵌入 Table 截图或 arXiv/IEEE 图链）；在 **Ablation** 下嵌入 **关键消融表/图**。
  - **局限**：若作者用 **图** 说明 failure case，可放在该条 limitation 下。
- **与 `## 关键图表` 的关系**：
  - `## 论文解析树` 内嵌 = **叙事用关键图**（至少：overview + 主实验之一）。
  - `## 关键图表` = **全量清单**（论文中 **每一个** Figure、每一个 Table 仍必须在此 **再次出现**，以满足零遗漏与 `download_note_images.py` 可达性检查；已内嵌的图可写「同上」或重复嵌入，二选一但**不得漏编号**）。
- `## 实验结果`：可与「论文解析树 → 实验」合并为同一叙事，或保留为 **数字摘要**；若合并，须在 `## 关键图表` 仍保留完整表图列表。

以下小节仍必须保留（与流水线质量检查、公式图表零遗漏规则兼容）：

- `## 关键公式`（论文中重要公式全集，规则不变）
- `## 关键图表`（Figure/Table **编号全集**，规则不变；见上「解析树嵌入 + 全量清单」双轨）
- `## 实验结果`（可选；若省略则须在「论文解析树 → 实验」与「关键图表」中覆盖同样信息）

文献联动（短，不替代上文五级解析）：

- `## 文献树定位`
- `## 挑战-洞察映射`

若用户提供了自定义解析树问题清单，在**不破坏上述五级标题**的前提下优先填充用户清单。

## 3. 笔记生成

**模板**: 严格遵循 `assets/paper-note-template.md`，不可自行简化。

### 核心质量规则

1. **零遗漏**: 论文中所有 Figure、所有公式、所有 Table 必须全部出现在笔记中；其中 **关键图至少嵌入 `## 论文解析树` 对应小节**，**全部图/表** 仍须在 `## 关键图表` 中按编号列全（双轨）
2. **内联概念链接**: 正文中首次出现的技术术语必须用 `[[概念]]` 链接，不仅仅是结尾
3. **严禁 ASCII 流程图**: 用结构化 Markdown 列表 + `$数学符号$` 描述架构
4. **公式完整性**: 每个公式必须有名称（`[[概念|名称]]`）、LaTeX 公式、含义、符号说明
5. **图片外链优先**: arXiv HTML / IEEE Xplore / 项目主页 / GitHub，找不到再本地下载

> 公式/图片/表格的详细质量规范见 `references/quality-standards.md`

### 图片获取流程（多源 fallback）

**目标**: 确保笔记中包含论文的**所有 Figure**，先统计论文 Figure 总数再逐一获取。

1. WebSearch `"{论文标题} arxiv"` 获取 arXiv ID
2. **来源 A — arXiv HTML**（首选）：
   - WebFetch `https://arxiv.org/html/{arxiv_id}` 提取所有 `<figure>` 的标题与 img src URL
   - 统计论文 Figure 总数，确认提取数量是否完整
3. **来源 B — IEEE Xplore / DOI 页面**（若有）：
   - 优先使用已有 `ieee_xplore_url` 或 `doi` 页面查找 figure / graphical abstract / pdf 入口
   - 若页面需要登录，允许用户在浏览器中手动点开；agent 继续使用可访问来源完成笔记
4. **来源 C — 项目主页**（HTML 404、IEEE 无图或图片不全时）：
   - 从摘要/HTML 中查找项目主页 URL（常见模式：`project page`、`github.io`、`our website`）
   - WebFetch 项目主页，提取展示图片（通常包含 teaser / demo 图）
5. **来源 D — PDF 提取**（前面都失败时）：
   - `pdfimages -png` 从 PDF 中提取，筛选 >10KB 的有效图片
6. 笔记中用 `![Figure X](url)` 外链嵌入
7. 验证：外链可加载 / 本地文件 >10KB
8. **URL 去重**：写入前检查 URL 中是否有重复的 arxiv_id 路径段（如 `2603.05312v1/2603.05312v1/`），有则删除重复段。详见 `references/image-troubleshooting.md`

> ar5iv 编号不一定对应 Figure 编号，排错见 `references/image-troubleshooting.md`

### 图片可靠性保障（生成后自动执行）

笔记保存后，运行图片可达性检查脚本，自动将不可访问的外链图片下载到本地：
```bash
python3 ../daily-papers/download_note_images.py "{笔记完整路径}"
```
- 可达的外链保持不动，不可达的自动下载到 `assets/` 并替换为 Obsidian wikilink
- 如有本地化操作，frontmatter `image_source` 自动更新为 `mixed`

### 公式格式

每个公式必须包含：名称（`[[概念|名称]]`）、LaTeX `$$` 块（前后留空行）、含义、符号列表。
`$$` 块前后**必须有空行**否则 Obsidian 不渲染。超长公式用 `aligned` 拆分。

## 4. Obsidian 保存

### 文件命名

只用**方法名/模型名**：`{方法名}.md`（如 `Pi05.md`，不加年份前缀）。
方法名判断：标题冒号前 / Abstract 中 "We propose XXX" / 希腊字母转 ASCII。
不确定时保存到 `_待整理/`。

### 保存路径

按 Zotero 分类层级：`{NOTES_PATH}/{zotero_collection_path}/{方法名}.md`

### YAML frontmatter

```yaml
---
title: "论文标题"
method_name: "MethodName"
authors: [Author1, Author2]
year: 2025
venue: arXiv
tags: [tag1, tag2]  # 小写连字符，3-8 个
zotero_collection: 3-Robotics/1-VLX/VLA
image_source: online
created: YYYY-MM-DD
---
```
读论文
Tags 判断：看 Related Work 小标题 + Abstract 关键词。第一个 tag 是最核心主题。

### 保存后自动执行

1. 只有在 `AUTO_REFRESH_INDEXES=true` 时才刷新目录页：
   ```bash
   python3 ../_shared/generate_concept_mocs.py
   python3 ../_shared/generate_paper_mocs.py
   ```
2. 只有在 `GIT_COMMIT_ENABLED=true` 时才做 git：
   - 先确认 `VAULT_PATH/.git` 存在
   - `git add {新增文件} {paper_notes_folder}/` 后必须真的有 staged changes
   - 满足条件后再执行：
   ```bash
   cd {VAULT_PATH} && git add {新增文件} {paper_notes_folder}/ && git commit -m "add paper note: {方法名}"
   ```
   - 只有在 `GIT_PUSH_ENABLED=true` 且仓库已配置远端时才 push

## 5. 概念库维护（每篇论文必做）

概念库位置：`{CONCEPTS_PATH}`

### 流程

1. **扫描**论文笔记中所有 `[[概念]]` 链接
2. **检查**每个链接对应的概念笔记是否存在（`ls` + `find`）
3. **创建**不存在的概念（不可跳过），自动归类到对应子目录

> 分类规则和模板见 `references/concept-categories.md`

### 自检

- [ ] 笔记中所有 `[[概念]]` 链接的概念笔记都存在？
- [ ] 概念笔记包含本论文作为"代表工作"？

## 5.5 文献树与挑战洞察树联动（每篇论文必做）

在保存单篇笔记后，同时更新 `{NOTES_PATH}` 下两个本地树文件：

- `SLAM-文献树.md`
- `SLAM-挑战洞察树.md`

规则：
1. 将论文归入至少一个“技术路线”节点（激光SLAM/视觉SLAM/多传感器/语义建图/神经隐式建图）
2. 给出创新性等级（S/A/B/C）与一句理由
3. 将论文映射到至少一个挑战节点，并补一句可复用洞察
4. 若论文改变了研究优先级，更新 `Milestone Tasks` 勾选项或新增任务

## 6. 完成后自检（合并 checklist）

- [ ] `## 论文解析树` 下五级结构（摘要/引言/方法/实验/局限）已填满，且 contribution 均为「介绍 + 收益」成对出现？
- [ ] **论文解析树内已嵌入**至少 **系统总览/Teaser 图** 与 **Pipeline/方法主图**，且 **实验小节** 含 **主结果图或表**（外链或本地均可）？
- [ ] `## 关键图表` 仍包含 **全部** Figure/Table 编号（与论文一致、无遗漏）？
- [ ] 引言中每个 challenge 是否具备 **Previous method / Limitation / Technical reason** 三要素？
- [ ] 方法中每个模块是否具备 **Motivation / Implementation / Mechanism / Technical advantage**？
- [ ] 所有 Figure 都在笔记中（数量与论文一致）？
- [ ] 所有公式都在笔记中（变量一致、无冲突）？
- [ ] 所有 Table 完整保留（所有行列）？
- [ ] 正文中技术术语有 `[[概念]]` 内联链接？
- [ ] 概念库已更新（缺失的概念已创建）？
- [ ] 图片可用（外链可加载 / 本地 >10KB）？

## 7. 交互式功能

完成解析后询问：深入解释？对比其他论文？保存到 Obsidian？
保存后自动创建缺失概念笔记，报告新增概念数量。

## 8. 批量处理

支持 Zotero 分类批量处理（默认递归子分类）。流程：递归获取论文 → 去重 → 跳过已有笔记 → 依次处理 → 汇总。

## 参考文件（按需查阅）

- **`references/zotero-guide.md`** — Zotero 查询、分类、PDF 路径获取、智能分类判断
- **`references/image-troubleshooting.md`** — ar5iv 图片编号对应、PDF 提取备选
- **`references/concept-categories.md`** — 概念自动归类的 16 个子目录规则 + 模板
- **`references/quality-standards.md`** — 公式/图片/表格的详细质量规范 + 自检清单
