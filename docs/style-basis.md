# 规范的依据与来源

README 展示日常使用的格式和例子。本文解释这些选择的来源、适用顺序及特殊情况，便于进一步追溯。

## 1. 采用的顺序

1. **ABKGROUP writing_rule 已明确写出的要求，优先执行。**
2. **指南未规定，或文献情况复杂、信息缺失而不能直接套用时，按老师最终定稿处理。**
3. **前两者仍无法解决时，再参考 Andrew B. Kahng 的实际论文。**

第三层用于补足，不用于推翻前两层。正式出版记录用于核对题名、作者、年份、页码和发表状态；格式与书目事实分别判断。

本文整理的是本项目采用的 reference 风格。目标会议如果另有强制要求，应定位具体冲突后处理。

## 2. writing_rule 的明确要求

来源材料为八页的 **ABKGROUP WRITING GUIDELINES**，以下按页码说明。公开仓库保留规则解读，不重新分发私人提供的指南附件。

### 第 3 页：作者连接方式与标题大小写

- 作者列表最后两人使用 `and`，其前没有逗号。
- 标点后保留正常空格。
- 介绍前人工作时，应明确作者或工作，不用孤立引用编号代替句子的主语。原示例把 `[12] introduce ...` 改为 `Smith et al. [12] introduce ...`。
- 标题采用重要单词首字母大写的形式，保护方法名与产品名的既有大小写。

### 第 5 页：手写 bibliography、结构与引用键

- 使用手写 `\bibitem`，不使用 BibTeX。
- bibliography 必须属于论文项目，能在项目目录中完成编译，不依赖未来可能丢失的外部库。
- 指南要求 bibliography 与论文同名并放在同目录；新建时遵循。现有项目若只授权条目修改，不顺带改文件结构；严格核查时可指出此差异。
- 会议条目：作者、引号中的标题、斜体会议名、年份、完整页码。
- 期刊结构：斜体刊名、卷(期)、括号中的年份、完整页码。
- 书籍结构：作者、斜体书名、城市、出版社、年份。
- 页码必须写完整，例如 `123--131`，不缩成 `123--31`。
- 引用键由首作者完整姓氏、其余作者姓氏首字母和两位年份组成；冲突加 `a`、`b`、`c`。
- 每条列出的文献必须主动引用，不能只增加 reference 数量。

期刊的空格结构尤其明确：

```latex
{\em Journal} 36(6) (2019), pp. 580--593.
```

刊名与卷号之间有空格，卷号与期号括号之间无空格，期号与年份括号之间有空格。

指南说条目末尾有一个句号，应结合原例中的姓名首字母、`Proc.`、`pp.` 理解：它规定条目收尾，不是要求删掉所有缩写句点。

### 第 8 页：最终输出检查

- reference 标题大小写保持一致。
- 要在 PDF 中检查实际效果，单看源码可能漏掉断行与字体问题。
- 原文对章节、表、图强调标签引用；文献同样应通过引用命令生成编号。

### 指南没有明确规定的内容

五作者截断阈值、是否显示 DOI/URL、arXiv 格式、仓库 commit 与日期、模型公告、待发表论文、缺页码的处理，以及本项目的文献排序和正文引用位置，不能被说成指南的原文要求。

## 3. 老师最终定稿补足的标准

本项目经过多轮 reference 修订，采用老师亲自修改的最终 PDF 作为第二层标准。该定稿的 reference 包含 42 条，涵盖下列类型。公开仓库整理其取舍和可复用示例，不上传私人稿件全文、截图或本机路径。

| 问题 | 最终采用的写法 | 对应的常见误判 |
|---|---|---|
| 作者很多 | 超过五人列前五人 + et al. | 不恢复几十名全作者，也不由其他论文推导六人/七人阈值 |
| 期刊标题 | 保留论文标题 | 指南示例没写标题，不等于明确禁止 |
| 正式会议/期刊链接 | 不显示 DOI 和 URL | 查元数据用 DOI，不等于出版列表必须印 DOI |
| 未找到会议正式页码 | 在会议和年份后结束 | 不用 PDF 总页数或 `9 pages` 填充 |
| 已接收待发表 | `to appear in Proc. ...` | 不混同预印本与已正式出版 |
| arXiv | 编号、年份、一个摘要页 URL | 编号与入口并列不是重复链接 |
| 基础软件仓库 | 项目名、commit hash、仓库入口 | 不拿最新 HEAD 冒充实验版本 |
| 专用项目仓库 | 机构、项目名、URL | 不机械要求所有资源同样多字段 |
| 软件没有传统出版年 | 不填猜测年、n.d. 或访问日期 | 不为字段齐全而虚构信息 |
| 官方模型公告 | 真实发布日期和官方入口 | 删除访问日期不等于删发布日期 |
| 文章关联分页 | 保留 `348:1--348:35` 等真实形式 | 不把文章号和普通分页混淆 |

### 标题保留为什么不与指南冲突

指南的期刊例子省略论文标题，但没有明确写“不得出现论文标题”。最终定稿保留标题，这是对未明确问题的补足。与之不同，作者最后一对 `and` 和卷期年份结构已有明文要求，继续执行指南。

### 缺信息时为什么省略

条目目标是忠实、可识别。正式页码未知就省略；仓库没有出版年不猜年份；已录用未出版写清状态。字段数量不同并不等于格式不统一。

### 如何看待最终版的局部差异

采用广泛、稳定的结构，不能从个别引号标点差异推导新的全表规则。PDF 文本抽取造成的空格丢失也不是格式规范。遇到明确的 writing_rule 规则时仍按第一层执行。

老师最终稿可作为“本项目如何写”的依据，不替代所有条目都已独立核实的外部事实证据。

## 4. Andrew B. Kahng 的论文实例

以下是参考过的代表论文及可定位条目。不同论文存在作者截断、访问日期和刊名结构差异，应按本节顺序作为补充材料，而不是套用某一篇的全部样式。

| 论文与公开 PDF | 可参考的具体内容 |
|---|---|
| [Solvers, Engines, Tools and Flows: The Next Wave for AI/ML in Physical Design](https://vlsicad.ucsd.edu/Publications/Conferences/404/c404.pdf) | 正式论文使用紧凑的出版字段，在线资源保留入口 |
| [Invited: Agentic AI for Physical Design R&D: Status and Prospects](https://vlsicad.ucsd.edu/Publications/Conferences/423/c423.pdf) | reference [1] 的 arXiv 编号、年份和 URL；[5] 的期刊标题与文章关联分页 |
| [HELIX: Placement Heuristics Evolution via LLM-Instructed Code Exploration](https://vlsicad.ucsd.edu/Publications/Conferences/430/c430.pdf) | [2][9][26] 保留期刊标题；[45][46] 仓库使用 commit hash 与主页 |
| [Automated QoR Improvement in OpenROAD with Coding Agents](https://vlsicad.ucsd.edu/Publications/Conferences/431/c431.pdf) | [2][19] 的仓库 commit；[52] 的源码仓库和归档 snapshot |
| [Netlist Tomography-Based Soft Guide Generation with Refinement Across P&R Stages for Improved PPA](https://vlsicad.ucsd.edu/Publications/Conferences/432/c432.pdf) | [4] 的期刊电子文章定位符，以及会议、期刊不同出版结构 |
| [An Updated Assessment of Reinforcement Learning for Macro Placement](https://vlsicad.ucsd.edu/Publications/Journals/j148.pdf) | 期刊文章中的完整 reference 实例 |

查阅范围还包含会议论文编号 395、396、403、407、410、412、413、414、417、419、424、428。可在 [UCSD Publications](https://vlsicad.ucsd.edu/Publications/) 中定位对应论文。

观察这些实例可以支持“简洁而足够识别、在线资源保留入口、版本按需要提供”的方向，但不能支持“所有 Kahng 论文都不写 DOI”“所有条目都不写 accessed”或“固定列六名作者”等绝对说法。

## 5. 实际修订形成的执行规则

以下是协作经验，不是冒充指南原文的出版条款：

- 读取当前实际编译文件，不能凭 v3/v4 文件名推断内容。
- 每次只改一个条目或一个正文句子，改前比较最新源码。
- 引用键尽量稳定，确需改键时同步正文、图、表、caption 和 TikZ。
- 恢复旧文件必须使用真实历史内容，不用新文件改名冒充。
- 历史文件可以保留，但不得误加入活动编译路径。
- 格式、事实元数据、引用完整性、编译和目视分别检查。
- 暂时打不开的 DOI 不自动算错；可解析 DOI 也不证明引用了正确版本。
- 不为轻微 Underfull 信息加入影响全篇的格式补丁。

完整流程见 [workflow.md](../references/workflow.md)，误判案例见 [lessons.md](../references/lessons.md)。
