# 格式规则与示例

## 来源标记

- **[W]** writing_rule 明确规定，优先。
- **[F]** 未规定或复杂情况无法照搬，以老师最终 PDF 为准。
- **[K]** 前两者未覆盖，再参考 Kahng 论文。
- **[E]** 两天实际协作经验，约束操作与核查，不冒充出版规范。

原文和实例位置见 [依据与来源](../docs/style-basis.md)。以下实际论文示例来自定稿；说明性模板中的虚构字段不能直接交付。

## 1. 项目内手写条目 [W]

writing_rule：`We do NOT use BibTeX`；bibliography 应在论文项目内，能够 make in place。

```latex
\begin{thebibliography}{99}
\bibitem{FirstauthorST26}
F. M. Firstauthor, N. Secondauthor and A. Thirdauthor,
``This is the Title of the Paper'',
{\em Proc. DAC}, 2026, pp. 123--131.
\end{thebibliography}
```

可放项目内 `.tex` / `.bbl` 由主文件输入，不依赖个人机器外部路径。指南明确要求 bibliography 与论文同名并放在同目录；新建按此执行。现有项目若不满足，应在严格合规核查中指出；仅检查条目时不要顺带擅改文件结构，获准处理时同时更新输入路径。不能把此要求降格为“指南没规定”。`{99}` 是两位数编号宽度样本，不表示有 99 篇。

同一编译路径不能同时启用手写条目和另一套自动 bibliography。未编译的历史 `.bib` 可以保留。[E]

本项目老师定稿按首作者/机构排序，维护已定顺序；新条目按项目约定插入，不擅自改成 IEEE 常见引用顺序。排序不是 writing_rule 的明确要求。[F/E]

## 2. 作者 [W/F]

名字首字母 + 完整姓氏，例如 `A. B. Kahng`；按真实作者顺序。[W]

保留 `T.-D. Ene`、`B.-Y. Wu` 等连字符，保留复姓和重音，如 `Romera-Paredes`、`N. V\~u`。机构作者如 `The OpenROAD Project`、`CODA-Team` 整体保留，不套人名缩写。[F/K]

两名作者缩写同为 `Z. Wang` 不代表重复录入，需查完整作者名单。[E]

**≤5 人全列，最后两人用 and，前面无逗号：**

```latex
A. One and B. Two,
A. One, B. Two and C. Three,
A. One, B. Two, C. Three, D. Four and E. Five,
```

**>5 人列前五人，直接接 et al.：**

```latex
M. Liu, T.-D. Ene, R. Kirby, C. Cheng, N. Pinckney et al.,
```

`and` 来自 [W]；五人截断来自老师意图与最终版 [F]，不是指南原文。老师提供过列七人的 GT2N 例子，是说明精简的人工写法，不推导成固定七人规则。`et al.` 普通字体，不加 `and`，不恢复几十名全作者。

展示截断与引用键的构造是两件事。

## 3. 标题、标点、空格 [W/F]

会议标题双引号，会议/期刊名称斜体。[W] **期刊也保留论文标题**；指南示例省略标题，不是明文禁止，最终版五条期刊均保留。[F]

标题遵循指南的标题式大小写及老师已定用法，保护 `ChipNeMo`、`OpenROAD`、`PreRoutGNN`、`P&R` 等专名。不要机械 Title Case 破坏真实题名。[W/F]

用 LaTeX 成对引号，按指南示例把字段逗号放结束引号之后：

```latex
``A Graph Placement Methodology for Fast Chip Design'',
{\em Nature} 594(7862) (2021), pp. 207--212.
```

老师定稿两条公告的逗号位置略异；不能以孤立写法推翻指南明确示例，也不据此擅自重改已定全文。[W/F]

字段用逗号连接，条目以一个句末句号结束。指南 `exactly one period` 要结合其姓名首字母、`Proc.`、`pp.` 示例理解，不能删除缩写、域名、`et al.` 中的点。[W，解释]

刊名与卷号、期号与年份之间必须留空格。PDF 提取可能把正确源码提成 `Nature594` 或 `”,Proc.`；先看实际渲染，不仅靠提取文本判错。[W/E]

页码完整写起止，`123--131`，不写 `123--31`；LaTeX `--` 表范围。收尾不叠两个句号；URL 内标点不是多余字段标点。[W/E]

## 4. 正式会议论文 [W/F]

### 已有正式页码

```latex
A. B. Kahng,
``New Directions for Learning-Based IC Design Tools and Methodologies'',
{\em Proc. ASP-DAC}, 2018, pp. 405--410.
```

作者、标题、斜体 `Proc. 会议简称`、年份、页码、句号。[W]

本组正式论文不附 DOI、出版商 URL、作者 PDF 或 arXiv 备用入口。[F] DOI 可用于核实事实，不必显示。

会议简称统一，如 `Proc. DAC`、`Proc. ICCAD`、`Proc. MLCAD`、`Proc. DATE`、`Proc. ASP-DAC`；不混同一会议多个长短名称。[F]

### 缺少正式分页

```latex
A. B. Kahng, S. Kundu and B. Pramanik,
``HELIX: Placement Heuristics Evolution via LLM-Instructed Code Exploration'',
{\em Proc. ICCAD}, 2026.
```

最终版 [5][7][12][13][40] **省略页码，不再保留早期 9 pages**。PDF 总页数和作者版 ACM 引用区的篇幅不是正式连续页码；不能猜 `pp. 1--9`。[F/E]

正式出版记录确实给 `1--9` 则可以保留，不能一刀切删除所有从 1 起的页码。最终版 [20][37][39] 保留此类页码。[F]

### 已接收待发表

```latex
S. Ren, Z. Cheng, Y. Han, L. Shen, L. Jin et al.,
``AgenticPD: A Stage-Aware Agentic Framework for Closed-Loop Physical Design Optimization'',
to appear in {\em Proc. ASP-DAC}, 2027.
```

需要可靠录用/出版依据；只有 arXiv 不能推断录用。年份按会议记录，不因当前是 2026 年就改掉 2027。[F/E]

有真实文章号/电子定位符时按实际结构保留，不把文章号 + 篇幅当普通分页。前两层无示例时，找对应出版记录及 Kahng 同类条目，不臆造固定样式。[K]

## 5. 期刊论文 [W/F]

```latex
A. Mirhoseini, A. Goldie, M. Yazgan, J. W. Jiang, E. Songhori et al.,
``A Graph Placement Methodology for Fast Chip Design'',
{\em Nature} 594(7862) (2021), pp. 207--212.
```

- `{\em Journal} volume(issue) (year), pp. start--end.` [W]
- 刊名与卷号间有空格；卷号与期号括号之间无空格；期号括号与年份括号之间有空格。[W]
- 不批量改成 `vol. 594, no. 7862, ..., 2021`。[W]
- 标题保留，不印 DOI/URL。[F]
- 缺期号只写已知卷号；Early Access 无卷期就保留真实状态，不伪装齐全。[K]
- 缩写全篇一致，定稿采用 `IEEE Trans. Comput.-Aided Des. Integr. Circuits Syst.`、`IETE Tech. Rev.`、`ACM Comput. Surv.`、`Nature`。[F]
- PreRoutGNN 的 AAAI 按会议处理；数据库有 volume/issue 不等于普通期刊。[F/E]
- 最终版 [35] `pp. 348:1--348:35` 保留文章关联分页，不改成 `348` 或普通 `1--35`。[F]

## 6. arXiv / 预印本 [F]

```latex
M. Liu, T.-D. Ene, R. Kirby, C. Cheng, N. Pinckney et al.,
``ChipNeMo: Domain-Adapted LLMs for Chip Design'',
arXiv:2311.00176, 2023,
\url{https://arxiv.org/abs/2311.00176}.
```

作者、标题、arXiv 编号、年份、一个摘要页 URL。编号识别文献，URL 提供入口，并列不是要删除的重复链接。[F]

不统一成 arXiv DOI，不并列 doi.org 与 arxiv.org 两种入口，不只保留隐藏链接的编号；优先 `abs` 页而非 PDF 下载链接。[F]

正式发表状态须从出版商/会议/作者材料核对。可确认同一工作正式出版后再更新类型，不能只凭相似标题或 DOI。arXiv DOI 仍是预印本标识，不能证明同行评审。[E]

“作者提供 DOI 即可、不强求当前打开”可用于证据判断，不改变最终显示格式。作者明确说 DOI 注册未完成则不主动填；网络暂时打不开不证明 DOI 错误。[E]

## 7. 软件仓库与实验版本 [F/E]

### 持续演进、影响实验结果的依赖

```latex
The OpenROAD Project,
``OpenROAD'', commit hash: \texttt{08f67ee5},
\url{https://github.com/The-OpenROAD-Project/OpenROAD}.

The OpenROAD Project,
``OpenROAD-flow-scripts'', commit hash: \texttt{0fcc4186},
\url{https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts}.
```

只填真实实验 commit/tag，不用最新 HEAD 冒充。这两个 SHA 属于本项目，不能用作其他论文默认。论文使用多个版本时按实验分别核对，不强行全文统一。[E]

短 SHA 应可识别且已核实。老师用主页 + `commit hash:`；不必强制改链接到 commit 页面。[F]

最终仓库条目没有出版年、`n.d.`、`software repository` 或 accessed，不补齐这些字段。[F]

`n.d.` = no date，不是 GitHub 必填。手写条目删掉后不应自动复生；自动样式生成它时查真实来源。键名 `nda` 不控制显示日期。[E]

### 小型专用项目

```latex
ASU VDA Lab,
``TimingECOAgent: LLM-Driven Post-Place-and-Route Timing ECO'',
\url{https://github.com/ASU-VDA-Lab/TimingECOAgent}.

CODA-Team,
``ChipEvolve'',
\url{https://github.com/CODA-Team/ChipEvolve}.
```

本用户明确接受这两项仓库入口，不要求版本，也不在说明中列“缺 commit”。新项目据复现需要判断，不能扩展成所有软件都不要版本。[F/E]

### artifact 和论文是不同对象

只存在归档的在线资源可保留 Zenodo artifact DOI；不受正式论文不印 DOI 的规则一刀切。[K]

但最终版 [42] CERBERUS 是 `Proc. MLCAD, 2026`，不能从早期稿恢复“只引 Zenodo 1.1.0”。真要引特定 artifact，先分清对象，再决定是否另列；不默认双引。[F/E]

## 8. 官方网页和模型公告 [F]

```latex
OpenAI,
``Introducing GPT-5.3-Codex'', official model announcement,
February 5, 2026,
\url{https://openai.com/index/introducing-gpt-5-3-codex/}.
```

保留机构、真实标题、可识别资源类型、实际发布日期和官方入口。Claude 公告的定稿日期为 September 29, 2025。不加访问日期；删除 accessed 不等于删发布日期。[F/E]

模型名/版本变更时核对本论文用的对象，不自动换最新模型。[E]

## 9. 书籍与其他类型 [W/K]

书籍按 writing_rule：作者，斜体书名，城市，出版社，年份。书名不用双引号。[W]

```latex
F. M. Firstauthor, N. Secondauthor and A. Thirdauthor,
{\em This is a Book Title}, City, Publisher, 1996.
```

学位论文、标准、数据集、章节等无本项目统一模板。先确认类型，查 Kahng 真实同类条目，保留必要识别字段；用学校/标准机构/出版商记录核事实，不臆造会议身份。[K]

## 10. 引用键和正文位置 [W/E]

指南：首作者完整姓氏 + 后续作者姓首字母 + 两位年份；冲突加 a/b/c，如 `KahngM96a`。[W]

现有合法键不为美观全改；新增按规则。展示五人截断不要求键也截到五人。机构可用稳定语义键如 `OpenROADProjectRepo`。[F/E]

- Related Work 引用紧跟工作名称/标志词，如 `ChipNeMo~\cite{...} ...`。[E，用户要求]
- 不能用孤立的 `[12] introduce ...` 作句子主语；指南示例要求改成 `Smith et al.~\cite{...} introduce ...`。介绍具体方法时也需明确所指工作，不把引用编号当作作者名。[W]
- 其他章节一般在相关句末；明确介绍具体工作可紧跟名称。不可挪到看似支持其他无关断言的位置。[E]
- 图、caption、TikZ、表格中引用也检查，不只 main.tex。[E]
- 每条文献必须主动引用，每个活动引用须有唯一条目。[W]
- `\nocite{*}` 不证明正文已引用；注释、备份和未编译源不计。图中真实引用计入。[W/E]
- 不用手写编号修复失效引用。[E]

## 11. 版式边界 [E]

默认保持模板字号、缩进、行距、双栏，不为缩短一行引入负间距、逐项 vspace、sloppy、强制断词或另一套样式。

指南老版本虽列压缩技巧，不代表每轮都要用；遵守当前会议约束和已定版式。

References 标题在左栏，右栏续条目与其高度接近是正常双栏结构。页尾平衡、奇偶 running header 并非 reference 错误，不因此挪条目。

长 URL 自然断行、短条目疏密不同、两端对齐造成某行字距大，要目视判断。Underfull 单独不证明缺陷；Overfull、裁切、重叠、丢字则定位处理。
