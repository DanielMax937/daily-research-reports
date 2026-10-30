# AI论文日报｜2026-10-30：榜单受限与三项独立原文研究

## 核心结论、抓取口径与实际覆盖

**本轮仍未取得可核实的alphaXiv热门Top10，因此不发布伪造的十名榜单。** 提供三项独立补充研究；编号仅表示阅读顺序，不代表排名。今天最关键的区分是：性能结果取决于具体预算/调度；论文中的代码链接不保证实现已交付；博客被推荐不等于论文刚发布。

- 报告所属日期：北京时间2026-10-30。正常首页读取约 **11:35（原时区UTC03:35）**；研究核验截止时间见各项。来源为实际打开的[alphaXiv正常首页](https://www.alphaxiv.org/)，返回页标记Crawled today，但内部刷新时间不可见，不保证实时。
- 实际页面标题为Explore / Follow the latest research，论文卡之间穿插Researchers to follow和会议内容。没有可核实的热门排序名称、筛选条件、时间窗口；既有热门入口仍受访问验证限制，本轮未绕过，也未重新尝试受限浏览器。
- 页面前部可见EAT、One-Step Language Model博客、NyoomFloat12、ThinkWorld、k-Diff、GEPA-Curator、EmbeddingGemma2、Timestral等。**这是普通页面可见内容，不是热门名次表**，没有用推荐流前十替代热榜。
- NF12与GEPA-Curator单页分别显示#4、#6 on Trending；One-Step博客页显示#2。这些局部标记没有共同时间窗及完整名单证据，不能拼成Top10。
- 昨日基线读取了[2026-10-29实际报告](https://github.com/DanielMax937/daily-research-reports/blob/98c6e7c74da489cb4102a98485aed63d7fb2abfd/2026-10-29/ai-papers.md)和保存状态：仅EAT、HRP、CTXAgent三项受限补充，没有完整排行。今天不把新阅读角度误称昨日论文的新版本。
- 本轮研究只读，未安装/运行任何研究代码或独立复现；数字均注明作者报告。首页与单页的views截面可能不同，未据此计算增长。AI Overview仅用于定位，不替代论文方法和实验。未检查的图、证明、代码及传播证据逐项标明。


## 补充一：NyoomFloat12｜独立原文研究

核查时间：北京时间2026-10-30 11:37（原UTC03:37）。**不是已验证的 Most Liked／7 Days／Top 10 条目。**以下实验以实际 PDF 为准，没有把 alphaXiv 的 AI Overview 当原文。

### 1. 基本信息、作者与版本

- 标题：*NyoomFloat12: Accelerating LLM Inference via Lossless 12-Bit Weight Compression*。
- 作者：Sylvie Liberman、Xinyu Fang、Tianyi Zhang、Tri Dao、Daniel Y. Fu；机构：Together AI、UC San Diego、Princeton。
- alphaXiv 页面标注提交 **2026-10-28、v1**；实际 PDF 首页日期为 **2026-10-27**。它是 23 页正文与附录文件。
- [论文页面](https://www.alphaxiv.org/abs/2610.nyoomfloat12) · [已读 PDF](https://www.alphaxiv.org/abs/2610.nyoomfloat12.pdf) · [View Paper 页面](https://www.alphaxiv.org/pdf/2610.nyoomfloat12)。不要把该自定义 alphaXiv slug 自动拼成已验证的 arXiv ID。
- [NeurIPS 官方 2026 名单](https://neurips.cc/Downloads/2026)列有本标题；具体 poster 页面本次抓取失败，未进一步核实展示安排。
- 搜索还返回标题不同的 [早期 OpenReview PDF](https://openreview.net/pdf?id=yYFj1E1mSZ)，摘要指标也不同；其论坛触发浏览器验证。本次不混用旧版结果，也不把它当作当前稿的完整版本历史。

### 2. 要解决什么问题

目标不是更激进的有损量化，而是把 BF16 的冗余转化为实际推理收益：既减少搬运权重的带宽，又释放可容纳更多 KV cache 的显存。主要竞争对象是压得更小、却解码较慢的变长无损编码。[作者摘要](https://www.alphaxiv.org/abs/2610.nyoomfloat12)

### 3. 方法怎么工作

按矩阵作二次幂缩放，让绝大多数权重的高四位指数相同；保留低字节，把两权重剩余高位合成一个 meta 字节。每八权重由 16 字节变成 12 字节；异常组走原值逃逸缓冲。固定长度避免线程变长解析。小批量将解码融合到 GEMV；批量路径先还原到 HBM 再用 cuBLAS。[作者摘要](https://www.alphaxiv.org/abs/2610.nyoomfloat12)、[原文 §4／Algorithm 1](https://www.alphaxiv.org/abs/2610.nyoomfloat12.pdf)

### 4. 亮点与阅读判断

**我的判断：它值得关注的不是“12-bit”这个数字，而是比较设计。**评审此类系统应同时问三件事：保存多少字节、付出多少解码成本、释放的容量能否真的改变调度结果。只报压缩率，或只拿一个较弱库函数作基线，都不足以回答部署问题。

因此，比宣传标题更值得看的是原文的 matched-BF16 对照和 KV 容量受限对照。前者帮助隔离算子实现质量，后者帮助区分“解码更快”和“可以同时跑更多请求”。这是我对证据结构的评价，不是独立复现背书。

### 5. 实验支持什么，不支持什么

以下均为**作者报告**；主要平台为 H100 80GB。核函数锚点是 Llama-3.3-70B gate/up，端到端为 Qwen3-32B。[§5、表 1/4/12](https://www.alphaxiv.org/abs/2610.nyoomfloat12.pdf)

| 核查项目 | 原文结果 | 定位 |
|---|---|---|
| GEMV 延迟：NF12／匹配 BF16／cuBLAS | 245／308／330 μs | 表 1 |
| 单请求生成：BF16→NF12 | 42.1→51.6 tok/s；1.23× | 表 4 |
| rollout 峰值：BF16→NF12 | 310→787 tok/s；2.54× | 表 12 |
| 限制 NF12 的 KV 容量 | 99–127 tok/s；至多 0.41× BF16 | 表 12 |

**支持的结论**：存在有收益的无损推理运行区间；容量和解码成本必须一起算。**不支持的外推**：所有模型或所有请求都快 2.54×、小模型必然受益、等容量也快、无需处理数值内核差异就能宣称输出完全一致。

两个复现警示：附录 F 与 G 的预热／缓存叙述需要作者澄清；附录 B 的 worked example 数量与容量算术也应再核对。它们是我读原文发现的核查问题，不直接推翻主表结论。截图接口未能完成视觉核验，不能排除抽取问题。[附录 B/F/G](https://www.alphaxiv.org/abs/2610.nyoomfloat12.pdf)

### 6. 热度证据

当前论文页显示 **“#4 on Trending”与 216 views**；另有无清晰文字标签的数字 14，不能擅自命名为点赞量。没有验证 Trending 的统计窗口、排序定义或完整榜单，因此这只是页面即时热度证据，**不是 Most Liked／7 Days／Top 10 的证明**。[alphaXiv 页面](https://www.alphaxiv.org/abs/2610.nyoomfloat12)

### 7. 工程价值与代码可用性

PDF 附录 K 提供 PTX／CUDA C++ 等算法清单，但本次没有定位到可验证的公开 GitHub 仓库；全文搜索 `github` 也没有结果。不能据此断言“没有开源”，只能说**仓库、许可证、可安装版本、复现命令未核实**。[附录 K](https://www.alphaxiv.org/abs/2610.nyoomfloat12.pdf)

**我的工程建议**：把它列为“需要 BF16 保真、又受显存／带宽约束”的候选方案，而不是现在就作为通用替换件上线。首次评估应分别验权重逐位往返、固定内核的输出一致性、冷／热缓存、短／长输出、吞吐与首 token 延迟；同时固定调度器、KV 预算和基线内核。若只能拿到论文伪代码，优先做接口与成本评审，不应把算法清单等同于可维护的生产插件。

本次只读审阅，未运行论文代码、基准或模型。

### NF12额外阅读覆盖

1. https://www.alphaxiv.org/abs/2610.nyoomfloat12 ：作者、机构、提交日期、v1、链接、即时页面热度。AI Overview 不作论文证据。
2. https://www.alphaxiv.org/pdf/2610.nyoomfloat12 ：View Paper 落点，仅显示 Loading PDF。
3. https://www.alphaxiv.org/abs/2610.nyoomfloat12.pdf ：真实 23 页 PDF，文本提取读取。
   - 首页与 §1–3：问题、背景、分布观察。
   - §4.1–4.3、Algorithm 1：格式、解码、缩放、异常组。
   - §5.1–5.3、Tables 1–5：正确性、算子、端到端。
   - §7：限制。
   - Appendix A–D：分布、异常组、数值与能耗口径。
   - Appendix E–I、Tables 8–12：小批 GEMM、预热、调度敏感性、跨卡、容量归因。
   - Appendix J：训练 rollout 结果；未在报告中推广为普适稳定性结论。
   - Appendix K、Algorithms 2–7：寄存器算法／PTX／CUDA 形式；未执行。
4. https://neurips.cc/Downloads/2026 ：官方名单检索到标题，链接 /virtual/2026/poster/153072。


## 补充二：GEPA-Curator｜独立原文研究

核验时间：2026-10-30 03:37 UTC（北京时间11:37）；代码固定版本补核于03:40 UTC（北京时间11:40）。直接读了 arXiv v1 正文、实验和 PDF 附录；没有把 alphaXiv 的 AI Overview 当作论文证据。

### 1. 基本信息

**GEPA-Curator: Curated Learning for Self Improving Agents**。作者：Zack Yu、Nicholas Lee、Minjae Lee、Lakshya Agarwal、Luca Manolache、Wonjun Kang、Matei Zaharia、Michael W. Mahoney、Kurt Keutzer、Sehoon Kim、Amir Gholami。机构包括 UC Berkeley、ICSI、LBNL、Furiosa AI、KAIST。当前记录仅 v1，提交于 **2026-10-27 17:58:11 UTC（北京时间10月28日01:58:11）**；PDF 标注 Under Review，不等于已接收。[arXiv 元信息](https://arxiv.org/abs/2610.37651) · [v1 正文](https://arxiv.org/html/2610.37651v1) · [25 页 PDF](https://arxiv.org/pdf/2610.37651v1) · [alphaXiv](https://www.alphaxiv.org/abs/2610.37651)

### 2. 要解决的问题

失败未必意味着提示词有错：工具缺失、环境故障和裁判噪声都可能让反思优化器学到错误规则。本文把“哪些经历值得学习”与“如何修改提示词”分开。[§1、§3](https://arxiv.org/html/2610.37651v1)

### 3. 方法

外层 Curator 保存逐任务历史，决定本轮运行或暂缓；再为失败任务选择同任务历史成功作为反思参照。不确定时继续运行，暂缓任务会复查；不可靠的成功可以不选。PDF 附录 B.2 要求成功参照另有独立干净成功佐证。实际主实验采用去掉 Pareto 候选选择的贪心 GEPA，而非原封不动的完整搜索。[§3–4.1、附录 B.2](https://arxiv.org/pdf/2610.37651v1)

### 4. 亮点与判断

**我的判断：最值得借鉴的是故障归因边界，而非“又多一个 agent”。** 成功也可能是裁判误判；难题也不该因连续失败就永久删除。任务筛选与成功参照分别作用于训练输入和反思证据，工程上能够单独审计。它更像数据治理层，而不是能保证递归自我改进的通用算法。

### 5. 实验证据及边界

主实验 actor 为 gpt-oss-120b，两个优化器为 Gemini 3.1 Pro Preview、Claude Opus 5；报告五次重复结果。GoBrowse 使用 3:1:1 划分，每网站每方法 5,000 rollouts。以下为成功率 %±标准差；**相减结果应称百分点，而非相对百分比**。[§4.1、表1–3](https://arxiv.org/html/2610.37651v1)

|定位与设置|GEPA|GEPA-Curator|解读|
|---|---:|---:|---|
|表1：GoBrowse overall，Gemini|78.7±0.6|82.1±1.7|+3.4 个百分点|
|表1：GoBrowse overall，Opus|79.5±1.2|84.5±1.0|+5.0 个百分点|
|表2：AppWorld Test-N，Gemini|38.0±2.3|58.7±1.9|+20.7 个百分点|
|表2：AppWorld Test-C，Opus|32.5±2.7|46.4±1.1|+13.9 个百分点|
|表2：τ-bench，Opus|82.9±2.0|82.9±2.9|均值持平|
|表3：GitLab 消融|82.8±1.6|88.6±2.0|仅筛选84.2±2.9；仅检索84.7±3.1|

**不能外推的结论：**

- 表3是200题验证集结果，不是独立测试；τ-bench 被改为静态请求，不能直接代表原多轮交互任务。
- 附录E的 HotpotQA 从66.3降至65.0；“所有任务都更好”不成立。
- “五次重复”不足以自行断言五次独立完整优化；论文没有清晰拆分全部优化随机性与评估随机性。
- 表8成本是高效变体的估算：非WebArena总额 GEPA $132.65、Curator $173.98、ACE $768.69；不含最终测试和WebArena托管。**不是比GEPA更省钱的证明。**[§4.3、§5.4、附录E](https://arxiv.org/html/2610.37651v1)

我的评价：主表支持这组设置下有实际收益；尚不能据此宣称普遍统计显著、零额外开销、稳定生产收益或独立复现成功。

### 6. 热度证据

本次公开页面显示“#6 on Trending”和177 views；附近数字21没有明确文字标签，**不当作点赞数**。单篇页面标签不能替代指定榜单、时间窗口及排序的核验，因此仍只作独立补充，不冒充已核验 Top 10。技术价值与浏览热度分别判断。[alphaXiv 当次页面](https://www.alphaxiv.org/abs/2610.37651)

### 7. 工程价值与代码检查

**核验范围：**正文附录F列出的是上游 GEPA、Meta-Harness、ACE 等；未找到明确属于本论文的官方实现链接。检索结果中的 Bespoke Labs Curator/GEPA 集成不能凭名字认作本论文代码。

已只读检查[上游GEPA仓库](https://github.com/gepa-ai/gepa)、目录及[`src/gepa/api.py`固定版本](https://github.com/gepa-ai/gepa/blob/80a62c879ecdeb8741faac72a844dceb1c18691f/src/gepa/api.py#L53-L115)：存在自定义 `BatchSampler`、候选选择、反思模板、`reflective_dataset_enricher` 等扩展入口，并核查其[传入ReflectiveMutationProposer的接线](https://github.com/gepa-ai/gepa/blob/80a62c879ecdeb8741faac72a844dceb1c18691f/src/gepa/api.py#L446-L463)。03:40 UTC通过GitHub连接器确认当时main与提交 `80a62c879ecdeb8741faac72a844dceb1c18691f` 完全相同（ahead/behind均为0）；随后按此SHA重新读取文件，blob SHA为 `d15c91dc7a2b98bc0a16a727757bca6ee8d54a23`。**这是实现可行性的线索，不是已核验论文复现。**未克隆、安装或执行任何论文/仓库代码。

**建议的工程试验（我的推断）：**先给现有日志增加任务ID、提示词版本、环境状态、裁判版本、暂缓原因和成功参照ID；在冻结测试集及相同总美元预算下，比较无筛选／仅筛选／仅成功参照／二者组合。另设被暂缓任务的回访集，避免指标上涨只是难题被隐藏。若裁判本身不稳定，应先校准裁判，而不是直接让新模型替它背书。

---

### 证据覆盖与未完成项

|材料|已读/已核查范围|限制|
|---|---|---|
|arXiv abstract|作者、日期、v1提交历史|没有已接收证据|
|arXiv HTML|§1–5.4；表1–3、5–8；附录A、C–F|B.2提示词在HTML提取中缺失，转读PDF|
|arXiv PDF|§4.1重复次数；附录B.2完整决策与成功选择提示词|未声称逐页图形复核或复现实验|
|alphaXiv|标题、页面趋势标签、views|未核验指定热门榜、点赞标签或增长趋势|
|GitHub|GEPA README、src目录、api.py关键配置与接线|仅上游静态检查；未发现论文专属实现；未运行代码|

额外审稿关注：附录B.1承认不同优化器实验使用不同GPU节点，WebArena时间敏感可能造成速度差异；因此跨优化器绝对分数不可简单归因为优化器能力。§5.3的Meta-Harness扩展每方法/设置仅一次优化，不能与五次重复主表混写。图2标题称validation curves，但图注明确在训练集评估，应按训练曲线解释。[论文原文](https://arxiv.org/html/2610.37651v1)

## 补充三：DBTM——把博客曝光与新论文分开

### 1. 基本信息
Sophia Tang、Shiyi Wang：《Discrete Beckmann Transport Models for One-Step Language Modeling and Reasoning》。领域：生成模型、语言建模、推理。初版2026-09-14 17:19:47 UTC（北京09-15 01:19:47），v2为09-15 14:23:01 UTC（22:23:01）。本次依据[v2原文](https://arxiv.org/html/2609.15903v2)，不是10月30日新论文。[arXiv版本记录](https://arxiv.org/abs/2609.15903) · [alphaXiv论文页](https://www.alphaxiv.org/abs/2609.15903)。

### 2. 解决的问题
少步并行文本生成面临位置之间的相关性与蒸馏成本。DBTM研究如何直接训练终点映射，而非先训练教师、再压缩采样轨迹；不能将“一步输出完整序列”误解为一步就能可靠解题。

### 3. 核心方法
旧路径：教师流→蒸馏→少步采样。新路径：数据/噪声→自治流的守恒约束→直接训练映射→提交可信token、对其余位置重新加噪并细化。训练结合自回归目标（此处指self-regression，不是左到右生成）、边界和anchor约束；额外NFE用于修正完整候选而非细分ODE时间。参见[原文§3–5](https://arxiv.org/html/2609.15903v2#S3)及[作者技术博客§2–4](https://sophtang.github.io/discrete-beckmann-transport/blog/)。

### 4. 最大亮点
值得研究的是无教师终点学习，以及把采样时实际出现的上下文纳入训练。理想自治流的收敛性质不等于有限网络对所有输入都可靠；这也是不能将理论保证直接包装成生产能力的原因。

### 5. 实验能否支持结论
作者表2报告：困难Sudoku在4 NFE为84.6%，GSM8K在32 NFE为16.8%；后者仍低于其AR基线。表1必须同时看困惑度与熵，避免把重复输出误判优质。支持特定少步生成设置，不证明通用Agent能力或端到端服务成本优势；本轮没有独立复现。[§6、表1–2](https://arxiv.org/html/2609.15903v2#S6)。训练算力、误差显著性和全量消融未完成独立复核。

### 6. 现在为何可见
今日alphaXiv展示的是[讲解博客卡片](https://www.alphaxiv.org/abs/2610.discrete-beckmann-transport)，标记Published 28 Oct及单页#2 on Trending；[作者博客](https://sophtang.github.io/discrete-beckmann-transport/blog/)自身却写Oct 9。两种日期未对齐，不能认定10月28日首发，更不能认定新实验。本轮未读X原帖，不能用嵌入的摘录充当传播链验证。仅确认单页标记，不推导完整榜单或热度原因。

### 7. 工程价值与代码状态
对应用开发者目前以阅读为主，不是可直接替换LLM API的插件。[公开仓库](https://github.com/sophtang/DBTM)只有README与assets，README明确implementation coming soon。固定提交[c0a07a5fd1d74714c7566f634a76e3f9556de197](https://github.com/sophtang/DBTM/commit/c0a07a5fd1d74714c7566f634a76e3f9556de197)为09-15 16:59:40 UTC（北京09-16 00:59:40），没有核心训练代码、依赖定义或可验证实现可深读。论文“Code Availability”链接不等于代码已经交付。实现门槛涉及训练与推理内核，不是React/RAG应用级接入；先等实际代码，再评估重现。

**实际阅读边界：**已读v2摘要/Introduction、§3–7与表1–2、作者博客方法说明、项目页及唯一提交/README；未逐条验证证明、逐像素检查图像、执行交互动画、训练或运行代码。首次误开v1只用于识别版本，正文结论最终以v2为准。

## A. 今天优先深入阅读的三项（仅限本报告实际样本）

1. **GEPA-Curator：**优先方法中的任务历史筛选、成功轨迹检索及对应消融。对Agent/RAG工作流优化，先判断失败是否真是可学习信号，而不是自动把每次失败都写进长期指令。
2. **NyoomFloat12：**优先格式设计与容量/带宽实验，以及附录中的调度控制。对推理服务工程，先确定瓶颈究竟是权重带宽、KV容量还是计算，再谈是否有收益；不能直接搬用最高加速倍数。
3. **DBTM：**优先§4–5与表2，再看作者博客的直观解释。适合研究少步生成；应用团队暂以观察为主，公开仓库尚无训练实现，不建议安排依赖现成代码的复现计划。

这里的三项是工程阅读顺序，不是热门前三或已经完成的部署建议。

## B. 本轮样本支持的研究主题

- **“少做工作”与“提高结果质量”需要分别验证。** GEPA-Curator改变学习材料，NF12减少存储/流量，DBTM减少函数求值次数；三者的成本指标不可互换，更不能合并成统一降本比例。
- **收益依赖被控制的实验条件。** NF12的容量与调度、DBTM的熵/NFE、GEPA-Curator的噪声与优化器设置，均应与最终分数一起记录。工程上应保留条件而非只记headline。
- **公开材料有不同成熟度。** 原文、博客、仓库占位与可运行实现不是同一种交付。本轮DBTM提供了明确反例：有代码链接但实现仍待发布。

样本只有三项补充，不把它们外推为整日十篇或行业长期趋势；不凑第四、第五条。

## C. 与昨天相比

- 昨日和今日均缺完整可核实热门排序与共同时间窗口，**不能判断新入榜、连续热门、升降或降温**。
- 今天新增的是NF12、GEPA-Curator以及DBTM/相关博客的阅读覆盖，不等于这些研究今天首发。DBTM最新论文版本仍是9月，博客日期存在来源差异。
- EAT仍在正常首页可见；没有本轮核实的新论文修订、实验或源码证据，不重复昨天完整背景，也不宣称结论已反转。HRP、CTXAgent今天未重审，昨日的接口失配、实验SHA等结论不视为已解决。
- 仍待核：完整热门榜单及窗口；各项独立复现、真实传播因果；DBTM代码交付。访问受限不等于无新论文或无讨论。

## 留存与证据解释

本文保存了实际页面、原文版本、已读章节及代码状态，供下一次比较。所有直接链接位于对应条目。论文作者的结论被明确归为作者报告，不代表本报告复现或背书。没有为了补足十篇复制旧报告，也没有用摘要填补未读方法或实验。
