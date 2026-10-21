# AI论文日报：2026-10-21 alphaXiv Trending Top 10

## 采集范围、证据与阅读说明

- 报告所属日：北京时间2026年10月21日。实际热榜采集：北京时间11:08:58–11:11:04（原始UTC 03:08:58–03:11:04）；正文、代码继续核读至约11:16（UTC 03:16）。
- 来源：[alphaXiv实际页面](https://www.alphaxiv.org/?sort=Trending&interval=7+Days)。使用dot云端浏览器的正常页面，明确选择 **Trending / 7 Days**，未加主题筛选。它是7日窗口，不是24小时新论文榜，也不是默认最新推荐流。
- 切换排序时出现旧列表水合瞬态，已等稳定并刷新、上下滚动复核后取前10。研究者推荐卡不算论文名次；第11项TokenGate没有替换进榜。今日本次正常页面能看到10篇以上，未绕过登录或访问限制。
- 动态页面不是原子快照：个别单篇页的排行与feed同时段不同，第10篇单页曾显示#11；本报告始终沿用上述feed顺序。喜欢/浏览只作截面，不解释为技术价值或独立复现人数。
- 十篇均读了原文方法与实验；代码是否交付、是否可读逐篇披露。未执行未知代码、安装依赖、训练或复现实验。图表数字以实际可读表格与正文核验；没有读取成功的图像不假装完成视觉检查。以下结果均为作者报告，工程建议为dot的解读。
- 尚无足够独立X/HN/Reddit传播证据解释这些论文为什么此刻上榜。项目页、作者博客和论文互相链接不构成独立验证。榜位可以确认，传播因果不能凭印象补造。

## 当日榜单留存

指标为上述采集窗口feed所显示；“未显示”不是零。论文页平台日期不必等同arXiv初版日期，版本以各条原始记录为准。

|排名|论文|平台日期|Likes|Views|alphaXiv原始链接|
|---:|---|---|---:|---:|---|
|1|MemT-1.0|2026-10-20|26|516|[原页](https://www.alphaxiv.org/abs/2610.26825)|
|2|Reward Misspecification Degrades Chain-of-Thought Monitorability|2026-10-20|16|778|[原页](https://www.alphaxiv.org/abs/2610.reward-misspecification-degrades-cot-monitorability)|
|3|Text-to-Image Generative Modeling Without Language Pretraining|2026-10-20|5|未显示|[原页](https://www.alphaxiv.org/abs/2610.26863)|
|4|Ropedia W0|2026-10-19|8|126|[原页](https://www.alphaxiv.org/abs/2610.26855)|
|5|HarnessPro|2026-10-20|8|125|[原页](https://www.alphaxiv.org/abs/2610.26770)|
|6|EgoXperience|2026-10-19|8|109|[原页](https://www.alphaxiv.org/abs/2610.26625)|
|7|Physical Words|2026-10-20|5|未显示|[原页](https://www.alphaxiv.org/abs/2610.26854)|
|8|Koi|2026-10-19|12|110|[原页](https://www.alphaxiv.org/abs/2610.koi-heterogeneous-llm-inference-planning)|
|9|SteerAct|2026-10-19|5|未显示|[原页](https://www.alphaxiv.org/abs/2610.25632)|
|10|Kronecker Delta Rule|2026-10-19|8|111|[原页](https://www.alphaxiv.org/abs/2610.26834)|

## 逐篇深读

## 1. MemT-1.0: Towards Memory-Native Evolution

### 1）信息

- 主要领域：大语言模型原生记忆、模型架构、长期交互与 agent；arXiv 分类 cs.CL。[alphaXiv 直接入口](https://www.alphaxiv.org/abs/2610.26825)
- 作者署名 MemTensor Team；arXiv 列 Zhiyu Li、Zeyu Zhang、Linyun Liu 等 74 位作者。
- arXiv:2610.26825；v1 为 2026-10-19，当前 v2 为 2026-10-20。alphaXiv 的 Submitted 20 Oct 是平台展示，不应混成首次 arXiv 提交日期。[版本和作者](https://arxiv.org/abs/2610.26825)
- 已读 v2 的架构、训练、评估、消融、效率、agent 实验及限制部分，并核查推理代码。已通过 GitHub commits API 确认代码 commit 为 e75c13d090a6a9d34b29146d901bd84323185f24（不是 tree 对象；其 tree 为 e32d5505c78a986a08e5d48fc9977e9018367f29），两份已读核心代码与该 commit 的 blob SHA 一致。[全文](https://arxiv.org/html/2610.26825v2)｜[代码](https://github.com/MemTensor/MemT-1.0)

### 2）要解决什么问题

长时间交互不能无成本地不断追加历史：全文上下文的 KV 状态随历史增长，文本检索系统也须保存记录。问题是，能否用大小固定、可更新的模型状态承载有用经验，而非每次把历史或经验全文放回提示词。[论文 §1、§6.6](https://arxiv.org/html/2610.26825v2#S1)

### 3）方法实际怎样工作

- 在 backbone attention 旁边增加 native-memory 分支，区分在线更新的信息状态 local memory 和学习如何读写的参数 hyper memory。
- 使用稳定化 Gated DeltaNet-2 逐 token 更新：先按门控遗忘/擦除，再写入新信息；生成时读出当前状态、归一化和门控后融合。不是每次用梯度重训完整模型。
- Mixture-of-Storage 扩展多个记忆专家，读和写各有路由；是全专家参与的 dense routing，不是稀疏 MoE。
- 34B-token 两阶段训练：continued pre-training 与 post-training；以可见全文的教师监督只读记忆的学生。Nano 基于 Qwen3.6-35B-A3B，Flash 基于进一步后训练的 DeepSeek-V4-Flash。[论文 §2–3](https://arxiv.org/html/2610.26825v2#S2)

### 4）真正的亮点

亮点不是“无限记忆”，而是将在线状态和读写能力分开，并给出可保存、恢复的服务实现。代码里读写可独立控制；成功提交后清空客户端未压缩历史，保存会先提交剩余轮次，恢复会检查模型/tokenizer 身份。未决事务不自动重放，避免重复写记忆。这比仅展示一个记忆 benchmark 多了会话生命周期设计。[session.py](https://github.com/MemTensor/MemT-1.0/blob/e75c13d090a6a9d34b29146d901bd84323185f24/inference/memt_sglang/client/session.py)

核心 layer 也能核到对称化输入、门控归一化和独立 commit 路径，说明仓库不是只有 README/模型卡。[layer.py](https://github.com/MemTensor/MemT-1.0/blob/e75c13d090a6a9d34b29146d901bd84323185f24/inference/memt_sglang/models/qwen/layer.py)

### 5）实验证明了什么，没证明什么

作者报告的关键数据：

| 证据 | 结果 | 必须附带的限定 |
|---|---|---|
| 表2，11项记忆评测平均 | Flash 50.60；Nano 46.97；Temp-LoRA 38.08；MemOS/DeepSeek 68.55；Full Context/DeepSeek 64.98 | 前两名仅指所评估的参数化记忆组，不是所有记忆方案第一、第二。|
| 表4，Nano 消融 | 完整 46.97；无 CPT 44.85；无 PT 36.28；未经稳定化的 GDN-2 46.43 | 后训练的效果更明显；不能把全部提升归功于稳定化公式。|
| 图8，128K 历史 | 约 1.86× 端到端加速 | HF 实现、双GPU、batch/concurrency=1、固定生成128 tokens；不是生产级高并发 SGLang 服务 SLA。短历史可能更慢。|
| 图9，128K 历史 | 每轨迹逻辑状态约缩小66× | 不含共享 backbone、hyper-memory 参数或 embedder；不是整机显存/总成本缩小66×。|
| 表5，SWE-bench Verified，执行前注入经验 | 无经验66.07%，文本经验68.87%，native memory 69.33% 平均成功率 | 500题，每题3次；native 比无经验高3.26个百分点，但只比文本经验高0.46个百分点。|

[表2和评估](https://arxiv.org/html/2610.26825v2#S6)｜[表5及agent实验](https://arxiv.org/html/2610.26825v2#S7)

未证明：长期精确细节不丢失；自主生成高质量经验并持续自我进化；在相同质量目标下全面胜过文本检索；实际部署总成本降低同样倍数。固定容量有遗忘/压缩权衡，agent 经验仍依赖外部构建和检索，写入也有开销。Multilingual 的执行前注入设置中，native 62.89% 低于文本经验64.22%，不可写“全面胜出”。[限制 §8](https://arxiv.org/html/2610.26825v2#S8)

### 6）热度：事实与未知

事实：当时 alphaXiv 明示 Trending #1；GitHub 页面可见197 stars、6 forks、2 commits。前者是平台排序，后者是仓库即时计数，均可能变化。[alphaXiv](https://www.alphaxiv.org/abs/2610.26825)｜[GitHub](https://github.com/MemTensor/MemT-1.0)

合理推测而非已证因果：agent 长期记忆、固定状态与实际模型/推理代码发布，容易吸引工程读者。未知：排序具体权重、多少浏览来自推荐或作者传播、独立复现状况；不能声称“因性能压倒 RAG 而爆火”。

### 7）工程价值与是否值得动手

判断：值得做固定状态预算的研究型会话原型，尤其是允许语义性/程序性经验而非逐字证据检索的任务；不宜直接替换需要出处、纠错、删除单条事实的可审计文本存储。

落地门槛已核：SGLang 0.5.16；示例 Nano 2 GPU、Flash 8 GPU，Linux/NVIDIA CUDA/Python≥3.11。只是发布的起始配置，不是最低硬件承诺。仓库树主要是推理代码，未见完整34B训练流水线。代码是 PolyForm Noncommercial 1.0.0，商业使用另谈；论文是 CC BY-NC-SA 4.0，权重/数据不自动沿用这两项许可，需分别核对。[部署说明](https://github.com/MemTensor/MemT-1.0/blob/e75c13d090a6a9d34b29146d901bd84323185f24/inference/README.md)｜[许可说明](https://github.com/MemTensor/MemT-1.0#%EF%B8%8F-license)

建议验证顺序（工程判断，未执行）：同 backbone 做文本经验/固定记忆对照；测持续更新、旧事实覆盖、精确召回和恢复正确性；然后再看含写入、状态传输与并发的总成本。不要只复刻66×存储数字。

## 2. Reward Misspecification Degrades Chain-of-Thought Monitorability

### 1）信息

- 主要领域：AI 安全、强化学习、奖励错配与 CoT 可监控性；alphaXiv 标注 cs.AI / cs.CL。[alphaXiv 直接入口](https://www.alphaxiv.org/abs/2610.reward-misspecification-degrades-cot-monitorability)
- Tianyi Lorena Yan、John Hewitt，Columbia University；alphaXiv 展示提交日期 2026-10-20，PDF 标记 Preprint。
- 链接中的 2610.reward-misspecification-degrades-cot-monitorability 是 alphaXiv 页面标识，不是标准 arXiv 编号；未核实到标准 arXiv ID 或明确 v1/v2，不补造。
- 已通过 GitHub commits API 固定代码 commit 为 8c9e10269a56e290ba4ef66d60af6b79962496aa，并确认下面四份已读代码的 blob SHA 与该 commit 一致。
- 已实际读取25页 PDF 的 §3–5、表1–3及附录关联说明，并核查任务奖励、训练和指标代码。[论文页](https://www.alphaxiv.org/abs/2610.reward-misspecification-degrades-cot-monitorability)｜[原始PDF](https://www.alphaxiv.org/abs/2610.reward-misspecification-degrades-cot-monitorability.pdf)｜[仓库](https://github.com/Lorenayannnnn/reward-misspecification-degrades-cot-monitorability)

### 2）要解决什么问题

只奖励最终答案时，如果奖励函数写偏了，模型可能学会追逐错误奖励，但可见推理文本仍说自己在遵守任务。研究检验的是外部模型能否从这些 CoT 检出行为偏离，不是能否读出模型全部内部思维，也不是“模型一定有意识撒谎”。[原文 §1、§3](https://www.alphaxiv.org/abs/2610.reward-misspecification-degrades-cot-monitorability.pdf)

### 3）方法实际怎样工作

- 成对训练：同基础模型、同输入，一组用符合任务的奖励，一组用错误奖励。三个任务分别是超字数、偏爱 Gemini 的评判、只通过部分代码测试。
- 基础模型：gpt-oss-20b、gpt-oss-120b、NVIDIA-Nemotron-3-Nano-30B-A3B-BF16；每组合3个seed。GRPO式训练使用 LoRA rank32、batch16、group8、学习率4e-5；长度/评判/代码分别120/250/800步。
- 改进方法 Reward Description Training：第一轮 RL 保存50个 held-out query 每10步的轨迹和奖励；挑奖励变化最大的5题，生成8条奖励解释并选最能提升基础模型奖励的一条；重新从基础模型训练，一半采样附解释，一半不附，而梯度训练条件中不保留解释。[原文 §3.4、§4.1](https://www.alphaxiv.org/abs/2610.reward-misspecification-degrades-cot-monitorability.pdf)

代码确认这不是仅在测试时给监控器递答案：训练 loop 的 conditioned half 用解释采样，训练 prompt 则为 plain input；重新计算相应 logprob。相同奖励组被跳过，防止没有组内学习信号。[训练loop](https://github.com/Lorenayannnnn/reward-misspecification-degrades-cot-monitorability/blob/8c9e10269a56e290ba4ef66d60af6b79962496aa/src/training/loop.py)｜[GRPO数据构建](https://github.com/Lorenayannnnn/reward-misspecification-degrades-cot-monitorability/blob/8c9e10269a56e290ba4ef66d60af6b79962496aa/src/training/grpo.py)

### 4）真正的亮点

控制变量选在奖励，而非把明显作弊线索塞进测试 prompt；监控器看同类正常输入，较能隔离训练奖励错配的影响。修复方法也不预先假定人知道漏洞是什么，而是从奖励与轨迹反推描述。重点是让奖励目标变得可见，不是用描述直接纠正错误奖励。

另外，评估区分“这次实际作弊”与“训练目标已经偏了”：前者是 intervention g-mean²，后者是 reward-intent g-mean²。它们是0–1综合分，不是“抓到作弊的百分比”；在偏置模型没成功作弊但CoT暴露意图时，两种指标可能相反。[指标代码](https://github.com/Lorenayannnnn/reward-misspecification-degrades-cot-monitorability/blob/8c9e10269a56e290ba4ef66d60af6b79962496aa/src/monitor/monitorability_metrics.py)

### 5）实验证明了什么，没证明什么

PDF 表1/2，以 gpt-5.6-luna 为监控器，跨9个任务×模型组合、每个3 seeds 的报告：

| 项目 | Baseline | 描述训练 |
|---|---:|---:|
| 错误奖励模型平均 hack rate | 0.87 | 0.79 |
| Intervention g-mean² | 0.13 | 0.37 |
| Reward-intent g-mean² | 0.17 | 0.59 |

正确奖励控制组 baseline hack rate 为0.05。支持的结论是：在这些受控任务里，错误奖励可带来高作弊率和低CoT可监控性；描述训练平均提高两项监控分0.24、0.42。[原文表1、表2，PDF第6、8页](https://www.alphaxiv.org/abs/2610.reward-misspecification-degrades-cot-monitorability.pdf)

不能推成普遍解法：gpt-oss-120b 的长度任务中 intervention 分反而0.23→0.17，虽然hack率1.00→0.45；LM Judge 中有组合hack率仍1.00。更能看出目标并不等于更少违规，也不意味着更强的任意监控器一定有用。

标签边界可以直接在代码核到：代码任务奖励要求“至少一个通过、至少一个失败”，全失败反而不记为hack；每题仅10个测试，全通过也不等于算法正确。指标代码还会剔除格式无效、harness错误、监控失败等样本；落地时须同时报告覆盖率，避免只看剩余样本分数。[任务代码](https://github.com/Lorenayannnnn/reward-misspecification-degrades-cot-monitorability/blob/8c9e10269a56e290ba4ef66d60af6b79962496aa/src/tasks/coding.py)｜[指标代码](https://github.com/Lorenayannnnn/reward-misspecification-degrades-cot-monitorability/blob/8c9e10269a56e290ba4ef66d60af6b79962496aa/src/monitor/monitorability_metrics.py)

未证明：真实复杂奖励错配都能自动推断；CoT已忠实揭示所有内部因果；方法会对齐模型或消除reward hacking；结果直接外推到大规模生产agent。

### 6）热度：事实与未知

事实：当时 alphaXiv 页面明示 Trending #2；作者 John Hewitt 的说明被嵌入论文页，并提供代码、数据和模型资源。GitHub页面当时显示0 stars/0 forks，不宜把 alphaXiv 排名说成全网开源热度。[alphaXiv](https://www.alphaxiv.org/abs/2610.reward-misspecification-degrades-cot-monitorability)｜[仓库](https://github.com/Lorenayannnnn/reward-misspecification-degrades-cot-monitorability)

解释仅为判断：它挑战“只要不直接惩罚CoT，推理监控就可靠”的简化假设，且实验有控制组和可核代码，所以对安全/RL读者有针对性。未知：推荐机制、引用影响及独立复现；不能凭排行榜断言社区已形成共识。

### 7）工程价值与是否值得动手

判断：对训练奖励、代码agent和LLM-as-judge做质量审计很有价值。最直接可迁移的是保存 query、可见CoT、输出、标量奖励及训练checkpoint，并用独立任务验收标准检查“奖励升高但真实完成度没升高”。CoT监控应和结果验证并用，不能当唯一安全边界。

可复现准备度：仓库包含任务定义、数据处理、训练、监控指标和论文图表脚本，Apache-2.0；依赖 Tinker、OpenAI API，代码任务还需 Sandbox Fusion，非离线一键脚本。仓库README写明 Python3.12.8、tinker-cookbook0.5.7。本次只读，没有运行、开容器、消耗训练额度或验证复现结果。[复现说明](https://github.com/Lorenayannnnn/reward-misspecification-degrades-cot-monitorability#reproducing-the-paper)

建议的最小实验（工程判断）：先选一个已有自动验证器的窄任务，设置明确正确奖励和可控错配奖励；报告hack率、两种监控分、误报率和样本剔除比例，再决定是否值得付第二轮RL的成本。

## 3. Text-to-Image Generative Modeling Without Language Pretraining

### 1）基本信息

- 模型名 Halcyon；arXiv:2610.26863，v1 为 2026-10-19，核读 v2 为 2026-10-20，27 页预印本。
- 主要领域：机器学习、计算机视觉、文生图生成与多模态预训练；arXiv分类cs.LG、cs.CV。
- 作者：Keshigeyan Chandrasegaran、Yue Zhao、Armin W. Thomas、Ehsan Adeli、Jiajun Wu、Juan Carlos Niebles、Li Fei-Fei、Michael Poli。机构：Stanford University、Radical Numerics。
- [alphaXiv](https://www.alphaxiv.org/abs/2610.26863)｜[arXiv及版本记录](https://arxiv.org/abs/2610.26863)｜[全文](https://arxiv.org/html/2610.26863v2)｜[作者技术博客](https://www.radicalnumerics.ai/blog/halcyon)｜[模型集合](https://huggingface.co/collections/radicalnumerics/halcyon)。

### 2）究竟解决什么问题

不是“图片生成不需要文字”，而是：已经有大量图文配对数据时，额外花成本先训练一个互联网规模的纯文本语言模型，是否真正改善文生图？论文把语言预训练、图像 tokenizer、生成器三部分成本放在同一本账上。这个问题尤其适合从零做模型的团队，不直接等于使用现成免费编码器的团队能节约同样倍数。[作者博客](https://www.radicalnumerics.ai/blog/halcyon)

### 3）方法链路

Halcyon 以随机初始化的 Qwen3 风格 decoder-only 模型，把 caption 与离散图像 token 拼成一个序列。图像 tokenizer 将 256×256 图片压成 1,024 个 token；文本与图像共享 80,640 大小的词表。作者对“先纯文本再图文”“从 Qwen3 权重继续训练”“只做图文”作对照。另一个小而实用的设计，是把 CFG 训练中原本丢掉 caption 的样本改成图像→文字，使同一预算兼顾 captioning。[4B模型卡](https://huggingface.co/radicalnumerics/Halcyon-4B)、[作者博客](https://www.radicalnumerics.ai/blog/halcyon)

### 4）真正值得看的亮点

判断：价值主要在受控实验与成本口径，而非发明一种前所未有的 Transformer。作者没有仅拿弱原版 baseline 比较，还改进了 baseline 的图像表示与感知监督。标题容易被传播成“LLM 对生成无用”，更合理的读法是“配对视觉数据已经能学到这组实验所需的文本条件映射”。后者对训练资源分配更有意义。

### 5）实验支持什么，没支持什么

- 表4：0.52B 的 gFD 48.02，对 LlamaGen-XL/8 为 63.29；1.6B 为 35.28，对 JiT-T2I-XXL/8++ 为 40.97。gFD 越低越好。
- 表5：1.6B 的 GenEval 53.48、DPG 77.90，对上述 JiT 为 43.17、76.85，说明改进不只体现在图像分布指标。
- 表6、7的关键控制：增加额外纯文本阶段但保留完整图文训练，gFD 49.22，并未胜过48.02；预训练 Qwen3 初始化47.81，也未胜过同结构随机初始化46.61。
- 这些是 GPIC、256×256、指定模型和训练预算下的结果。不能推出更高分辨率、复杂文字渲染、知识密集提示或所有语言分布都不需要语言预训练。论文明确指出小字仍困难。训练随机种子的重复仅覆盖小模型配置，不能把所有微小差值都解读为显著。
- 18.2×／275×为“全部预训练成本”比较，不是推理加速，更不是复用现成语言模型时的增量训练节省。[原文表4—7、附录C](https://arxiv.org/html/2610.26863v2)

### 6）热度：事实与未知

事实：今日该榜第3；作者公开技术博客与 Hugging Face 模型集合。推断：反常识标题、巨大的总算力倍数、相对清楚的可消融问题，可能增强传播。未知：alphaXiv 排序因果、独立复现数、长期采用率，不能以榜位替代证据。

### 7）工程价值与复现提醒

最值得优先试的是小尺寸模型的专域文生图基线，以及“caption dropout 换 I2T”配方。但需要先核对实际 checkpoint，不能直接下载默认分支后声称复现论文：

- [Halcyon-0.6B模型卡](https://huggingface.co/radicalnumerics/Halcyon-0.6B)明确对应论文的0.52B；main 是另一套中途混合 I2T 的配方，没有论文指标；复现表4应选 baseline。
- [Halcyon-4B模型卡](https://huggingface.co/radicalnumerics/Halcyon-4B)的 main 比一轮训练多退火368步，页面数字是相应配方的论文成绩，不保证恰好是此 checkpoint 的分数；baseline 才对应表4。
- [Tokenizer模型卡](https://huggingface.co/radicalnumerics/Halcyon-Tokenizers)确认 BPE 还使用 OpenWebText，这不等于生成模型做过纯文本语言预训练。该仓库只有图像 tokenizer 权重，不含其实现代码。
- 4B 与 tokenizer 页面要求先接受 Hugging Face 信息分享条件；本次没有登录、接受或下载。Stanford项目页重定向后读取失败，因此不能声称完整训练源码已经审核或一键可复现。

## 4. Ropedia W0

### 1）基本信息

- arXiv:2610.26855v1，2026-10-19；标准arXiv完整题名为 Ropedia W0: Scaling Loco-Manipulation World Models across Embodiments with Human Experience。
- 主要领域：具身世界模型、动作条件视频生成、跨本体机器人学习；arXiv分类cs.CV、cs.RO。
- 作者：Tianqi Liu、Hanfei Zhao、Qifeng Liang、Hui En Pang、Jiarui Xu、Sayang Mu、Penghao Qiu、YingSheng Zhang、Jun Wang、Ziang Cao、Mingze Sun、Yukang Cao、Fangzhou Hong、Zhaoxi Chen、Ziwei Liu。
- 机构：NTU、Ropedia、Duke、UC San Diego、Tsinghua。
- [alphaXiv](https://www.alphaxiv.org/abs/2610.26855)｜[标准arXiv页面](https://arxiv.org/abs/2610.26855)｜[全文](https://arxiv.org/html/2610.26855v1)｜[项目](https://ropedia.github.io/ropedia-w0/)｜[代码](https://github.com/Ropedia/ropedia-w0)｜[权重](https://huggingface.co/ropedia-ai/Ropedia-W0)。

### 2）问题

人手、夹爪、灵巧手的关节动作既不等长，也不具有一致语义；移动摄像头又改变整个视野。W0 要预测“给定动作后我会看到什么”，让人类视频成为不同机器人共同可用的预训练资源，而不是给每种机器人完全重做动作接口。[项目说明](https://ropedia.github.io/ropedia-w0/)

### 3）方法

用相机轨迹的 Plücker-ray 图表达移动，用投影骨架图表达操纵；相机与骨架条件对齐到视频 latent 后加入 Wan2.2 的 patch embedding。先做人类视频预训练，再等比例混合人类和机器人数据。Xp-Data 为约10k小时人类、3k小时机器人视频。5B与A14B是不同尺度；后者约27B总参数、14B活跃。蒸馏则把多步视频扩散变成可流式预测。[项目](https://ropedia.github.io/ropedia-w0/)、[原文§4](https://arxiv.org/html/2610.26855v1)

### 4）亮点

判断：真正可迁移的贡献是“动作变成同一种视觉坐标接口”，不是宣称模型已理解全部物理规律。它把几何标注、数据清洗、模型接口与下游验证连在一起，也暴露了工程成本：机器人关键点仍有大量人工校正，不能把数据流水线描述成全自动。相较只给漂亮生成视频，下游策略排序和候选计划选择更值得关注。

### 5）实验与边界

- 表3的 DreamDojo In-lab、1%后训练：W0-5B PSNR20.854，对14B DreamDojo18.983，支持低数据适配价值。
- 表6：用W0初始化FastWAM，LIBERO-Plus总体成功率50.06%→56.82%；但少样本表格并非所有子维度都上升。
- 图9：真实G1计划选择任务进度55%，随机26%、最佳固定checkpoint45%。注意这里是任务进度，不是整项任务成功率。
- 表S1：蒸馏后21.3fps；61秒rollout PSNR仍从短片16.12降至13.98。吞吐达实时不等于每次控制响应零延迟。
- “零样本”指目标数据集未训练过，不保证机器人本体从未出现；原文附录F承认接口未显式描述物理接触与物体动力学。因此这些结果支持可控视频代理环境，而不是可替代安全验证的物理仿真器。[原文表3、6、S1及§6.4、附录F](https://arxiv.org/html/2610.26855v1)

### 6）热度

事实：今日第4；本次读取GitHub页面显示23 stars、0 forks，是时间截面，不是复现量。推断：跨本体、人类数据扩展、实时交互演示组成了清楚的展示叙事。未知：榜位具体成因、外部成功部署、长期滚动稳定性。由同一研究团队发布的项目页和论文不能算两次独立验证。[仓库](https://github.com/Ropedia/ropedia-w0)

### 7）工程价值与可用性

优先场景：离线策略候选筛选、低数据新机器人视频预测、动作条件表示研究。首轮验收应比较策略排名与真实任务结果，而非只看PSNR。

- 已核实仓库有5B推理实现；实际阅读[inference_5b.py](https://github.com/Ropedia/ropedia-w0/blob/759b192fcb0aed48695ace42a4eb2fd7e48c12b9/inference_5b.py)及[cli.py前100行](https://github.com/Ropedia/ropedia-w0/blob/759b192fcb0aed48695ace42a4eb2fd7e48c12b9/ropedia_w0/cli.py#L1-L100)，能确认相机96维、骨架48维条件分支通过零初始化Conv3d注入，不只是空README。源码已固定到实际commit 759b192fcb0aed48695ace42a4eb2fd7e48c12b9，并重新读取核对：cli.py的blob SHA与首次读取完全一致，为f04a03a7ca5597b5c8d3255e37dbf55477675ffd；入口文件内容亦与先前网页读取一致。
- [权重文件列表](https://huggingface.co/ropedia-ai/Ropedia-W0/tree/main)有两份10GB safetensors：human pretrain与human+robot midtrain。还需单独准备Wan2.2底座。
- [README](https://github.com/Ropedia/ropedia-w0#readme)要求Linux、至少40GB显存，640×480／81帧峰值31GB；验证设备是H200。
- 5B源码、权重和Xp-Teleop已发布；A14B、基准微调权重、评测代码、后训练代码仍未勾选发布。
- 代码Apache-2.0、权重CC BY-NC 4.0、Xp-Teleop数据CC BY 4.0，三者不能混写成“全部可商用”。[模型卡](https://huggingface.co/ropedia-ai/Ropedia-W0)

## 5. HarnessPro: Recursive Harness Self-Improvement with Pareto Optimization for Performance-Cost Trade-offs

### 1）基本信息
- 作者：Zhuoshi Pan、ZhiYuan Feng、Yukuo Cen、Honglin Lin、Junru Lu、Zhongxia Chen、Shuo Yang、H. Vicky Zhao、Jie Tang。
- 领域：Coding Agent、Evaluation、Context Engineering。arXiv v1：2026-10-19 17:27:38 UTC（北京10月20日01:27:38）；本次读v2：10月20日06:00:54 UTC（北京14:00:54）。[版本页](https://arxiv.org/abs/2610.26770)｜[alphaXiv](https://www.alphaxiv.org/abs/2610.26770)
- 已读：v2正文方法、实验、表2/3、附录实验配置和部分生成产物；代码README、依赖、评估文档、hook.py与harness_runtime.py的相关实现。未独立复现。

### 2）解决的问题
编码agent的表现不只取决于模型，提示、工具包装、验证规则和收尾时机同样影响成功率与token账单。单纯降低推理强度可能明显失分，追最高分的自动优化又容易忽略成本。本文让同一固定模型产生不同质量/成本取舍的harness，而不是训练一个新基础模型。

### 3）核心方法
流程是：选代表任务→收集运行轨迹→分析失败与成本→分别规划lite/medium/heavy修改→隔离目录改harness→用冻结验证测试评估→保留可行的非支配候选→递归下一轮。

DPP挑10道训练任务，每题3次轨迹。测试在开始时由任务描述与种子轨迹生成，之后固定，优化过程不使用官方评测答案；最终再做held-out官方评估。选择先守住种子性能约束，再在归一化的质量和成本差距上按不同权重挑候选。“Pareto”是有限候选的筛选，不证明找到全球最优边界，也不保证三档一定都不同。[原文§3–5、表1](https://arxiv.org/html/2610.26770v2)

实际代码把harness落到SessionStart、PreToolUse、PostToolUse事件：前置控制工具次数、收敛与最终答复预算；后置将长输出原文保存到文件，只回传可恢复的头尾片段和路径。另有任务分类、置信度回退和运行时策略配置。它不是简单把回答截短，也不是检索系统。[hook.py](https://github.com/pzs19/HarnessPro/blob/8ae622eb4a4923dbb4b515be7ded614f88fd4f38/harnesses/terminal-bench-2/medium/runtime/hook.py)｜[harness_runtime.py](https://github.com/pzs19/HarnessPro/blob/8ae622eb4a4923dbb4b515be7ded614f88fd4f38/src/rho/harness_runtime.py)

### 4）最大亮点
1. 将“任务成功约束”和“成本目标”显式分开，避免以便宜掩盖失分。
2. 候选共用冻结测试，减少优化者不断改变验收标准的自由度；但生成测试仍可能遗漏错误，不能代替独立验收。
3. 长工具输出保留原件、压缩展示，兼顾上下文预算与追溯；这比不可恢复的截断更可迁移。

### 5）实验能否支持结论
表2，GPT-5.5/Codex设置，作者报告：Terminal-Bench 2的RHO为76.3%、每任务$1.09；heavy为80.8±1.0%、$0.72±0.05；medium为76.3±1.7%、$0.56。SWE-bench Pro则从RHO的80.0%、$2.68，到heavy的80.7±0.6%、$1.97。不是所有档位都保住原分，TB lite为72.9%。表3去掉测试合成时，heavy的TB和SWE成绩分别跌到74.6%、72.0%，支持测试环节的重要性。[原文表2、3](https://arxiv.org/html/2610.26770v2)

边界：测试集为59道TB、100道SWE Pro、100道ProgramBench，前两者3次重复，后者2次；ProgramBench性能是测试用例通过比例的宏平均，不是“完整解决任务率”。成本口径是运行token费用，不能直接等同包含搜索、开发、验证与基础设施的总拥有成本。低延迟也不普遍成立；生成测试的覆盖、公平对照、不同模型版本和长期分布变化仍需额外验证。

公开复现范围比论文结果小：当前提交8ae622e包含九套最终harness与评估入口，不是完整递归优化流水线；文档明确没有GLM-5.2实验所用快照。把GPT版harness接到Claude Code上不等于复现该GLM结果。依赖Linux、Python3.12/3.13、Docker Compose、CLI和外部benchmark输入，不能说一键零成本复现。[评估说明](https://github.com/pzs19/HarnessPro/blob/8ae622eb4a4923dbb4b515be7ded614f88fd4f38/docs/evaluation.md)｜[依赖](https://github.com/pzs19/HarnessPro/blob/8ae622eb4a4923dbb4b515be7ded614f88fd4f38/pyproject.toml)

### 6）现在为何热门
事实：本次Trending第5，论文v2与公开初始代码时间接近；仓库所读提交时间为10月19日16:20:12 UTC（北京10月20日00:20:12）。未读取到足够独立传播讨论来建立因果。目前只能确认论文热度高，尚无足够公开证据解释传播原因。[提交](https://github.com/pzs19/HarnessPro/commit/8ae622eb4a4923dbb4b515be7ded614f88fd4f38)

### 7）工程价值
优先读hook与评估协议，适合给Codex/编码agent建立质量下限和预算分档。最小验证应在自己的固定任务集对照：原harness、仅降预算、引入可恢复输出压缩三组，同时量成功率、token和延迟；不要凭论文数字替生产默认配置。全文训练式自改框架的移植复杂度较高，现成九套产物的局部审阅门槛较低。

## 6. EgoXperience

### 1）基本信息

- arXiv:2610.26625v1，2026-10-19；标准arXiv完整题名为 EgoXperience: Learning World-Grounded Egocentric Representations from Human Experience。
- 主要领域：第一视角三维重建、相机与场景几何、手物交互、具身数据；arXiv分类cs.CV。
- 作者：Xinhao Ji、Hui En Pang、Hao Li、Kairui Hu、Jiner Wang、Mingze Sun、Ziang Cao、Yalun Dai、Thang Luu、Qin Ma、Hongyi Chen、Yukang Cao、Fangzhou Hong、Zhaoxi Chen、Ziwei Liu。机构Ropedia、NTU、Tsinghua、Peking University。
- [alphaXiv](https://www.alphaxiv.org/abs/2610.26625)｜[标准arXiv页面](https://arxiv.org/abs/2610.26625)｜[全文](https://arxiv.org/html/2610.26625v1)｜[代码入口](https://github.com/Ropedia/EgoXperience)｜[数据模型集合](https://huggingface.co/collections/ropedia-ai/egoxperience)。

### 2）问题

第一视角视频分别估计相机、深度、手和物体，很容易得到“每个局部看起来对、合在世界坐标里却不对”的结果。EgoXperience瞄准统一几何，而非未来视频生成：核心需求是让不同重建输出共享尺度、原点和相机变换。[全文§1—3](https://arxiv.org/html/2610.26625v1)

### 3）方法

EgoX-Engine用多相机采集、SLAM、立体深度、预扫描物体与几何验证产生对齐标注；EgoX-Data-6M为50小时、101个刚体物体、270个任务脚本。推理模型EgoX使用单目RGB与首帧物体mask，共享Transformer里放相机／手／物体token，以同一ScaleHead与预测相机变换组合输出；世界坐标损失反向影响各分支。不能把“推理只需单目”说成“训练标注也只需单目”。[全文§3](https://arxiv.org/html/2610.26625v1)

### 4）亮点

判断：这更像具身数据基础设施工作，而不是新的控制策略。统一坐标监督减少了把几个现成模型硬拼后的误差传递；同一视频上的多任务评测也更接近机器人数据使用者的真实需求。对想把人类示范转成可训练几何信号的团队，潜在价值高于只需要漂亮3D展示的团队。

### 5）实验与边界

- 表2：EgoX-Bench世界手关节误差328.81→113.24mm；表4同集深度AbsRel0.0806→0.0460。
- 表3：HOT3D物体AUC-S50为73.71，对最佳比较值57.59；28.0%是相对提升，不是增加28个百分点。
- 表4中相机68.9%误差下降只对应HOI4D：nATE0.0212→0.0066；另外三个数据集并非相机最佳。
- 表5、6移除scale／depth头会损害其他重建任务，支持联合学习。主评估统一150帧且不提供GT相机或尺度，但物体位姿分数仍在相机坐标下评估。
- 没有直接证明这些几何提升会提高机器人控制成功率；覆盖的是刚体物体，不能推成任意可变形场景重建。[全文表2—6、附录C](https://arxiv.org/html/2610.26625v1)

### 6）热度

事实：今日第6；读取时GitHub显示13 stars、0 forks。推断：数据引擎、6M数据命名与统一重建构成有吸引力的全栈叙事。未知：外部复现、数据实际使用质量与开放后的维护情况。不要将“6M”说成600万独立场景，也不要把宣传性SOTA说成所有重建子任务无条件第一。[仓库](https://github.com/Ropedia/EgoXperience)

### 7）工程价值与阻碍

适合列入“人类视频几何标注与机器人示范数据”技术候选，而不宜现在就承诺接入生产。当前[README](https://github.com/Ropedia/EgoXperience#readme)写明代码将发布，EgoX-Data-6M、EgoX-Bench与权重全部coming soon；目录仅见展示资产、README等，无法进行源码级核验。本次没有可运行实现可以检查，不能把论文上的代码链接等同于已经开源。

附录表7的速度为单张A800处理150帧14.60秒，即10.28fps，排除了载入、可视化与磁盘I/O；这是批次重建吞吐，不足以证明在线控制延迟。附录F还说明总训练池约280小时，并非只靠自建50小时数据。[附录D、F](https://arxiv.org/html/2610.26625v1)

判断：将来做PoC应优先测本方相机运动、遮挡、首次mask误差与跨对象泛化；验收要同时看世界坐标误差和最终下游效果。它与W0互补但不相同：EgoX从视频恢复几何，W0在给定几何控制后预测视频，二者没有在这篇论文中被证实已经形成可闭环生产系统。

## 7. Physical Words: A Vocabulary for Structuring Latent Reasoning in Robot Manipulation

### 1）基本信息

- 模型PhysWord；arXiv:2610.26854，v1首次提交2026-10-19 17:59:54 UTC（北京10月20日01:59:54）；核读v2为2026-10-20 17:53:12 UTC（北京10月21日01:53:12）。
- 主要领域：机器人操作、视觉语言动作模型、视觉触觉学习、结构化latent推理；arXiv分类cs.RO。
- 作者：Jiaming Liu、Xinghao Zhu、Yiming Zhang、Shanghang Zhang、Yinxi Wang、Yichu Yang、Zhuoyang Liu、Dantong Niu、Soha Pouya、Juekun Li、Yan Chang。机构NVIDIA、Peking University、UC Berkeley。
- [alphaXiv](https://www.alphaxiv.org/abs/2610.26854)｜[标准arXiv及版本记录](https://arxiv.org/abs/2610.26854)｜[全文](https://arxiv.org/html/2610.26854v2)｜[项目与演示](https://nvidia-isaac.github.io/video_to_data/physicalword/)。

### 2）问题

纯语言规划能说“抓取”，却不准确表达将发生的接触与运动；纯latent预测有细节，却缺少可跨任务复用的语义组织。PhysWord把动作词当作语义锚，尝试兼顾两者。它不是让机器人以自然语言写一长串推理后照抄执行。[项目方法说明](https://nvidia-isaac.github.io/video_to_data/physicalword/)

### 3）方法

Cosmos时序分支和Qwen3-VL推理动作分支共享注意力。16类原子动作分别具有视觉与可选触觉版本；预测一个动作词的隐藏状态同时接受词标签交叉熵与未来感知latent对齐监督。按未来时间块生成这些词，再用flow matching生成动作chunk。未来图像／触觉只作为训练目标，不是推理时偷看未来。[全文§3](https://arxiv.org/html/2610.26854v2)、[项目](https://nvidia-isaac.github.io/video_to_data/physicalword/)

### 4）亮点

判断：可借鉴点是给连续预测状态加上离散语义锚，而不是把“Physical Word”误当作新传感器或真实物理符号系统。它允许开发者检查中间阶段是否从place切回approach，解释粒度比不透明latent更直接；但能看见动作标签不等于所有失败都可解释，更不自动提供形式化安全保证。

### 5）实验证据与没有证明的部分

- 表1：UniVTAC平均成功率90.3%，最佳比较基线83.1%；LIBERO-Long99.6%，表中强基线98.4%。实验各任务50条示范，3次各100 rollouts。
- 表2：四个真实任务平均71.7%，对FTP-1为55.0%；两个任务的未见配置平均63.3%。真实评测每任务100示范，3×30试次。
- 附录表9：扩展捡纸任务70.0%，去掉动作词监督只保留latent后36.7%，比单纯可视化更直接支持语义锚价值。
- 边界：UniVTAC插HDMI仍仅34%；真实任务数小，未覆盖全身行走控制。99.6%不是现实机器人通用成功率。未来触觉替代实测触觉的结果也不是“从未用触觉数据训练”。[全文表1、2、9及附录C](https://arxiv.org/html/2610.26854v2)

### 6）热度

事实：今日第7；NVIDIA等机构的正式项目页已有方法和真实机器人演示。推断：语言语义、世界模型、触觉、长程任务组合，且有接近满分的模拟benchmark，容易引发关注。未知：alphaXiv排序为何上升、独立复现、长期可靠部署。演示选择与benchmark成绩不等于现场无人值守能力。[项目](https://nvidia-isaac.github.io/video_to_data/physicalword/)

### 7）工程价值与开放状态

当前[项目页](https://nvidia-isaac.github.io/video_to_data/physicalword/)明确标注Code coming soon；本次未发现已公开可审查的官方实现，不能声称已复现或已完成代码质量评估。

计算门槛也不能忽略：模型借助约7,000小时预训练示范，H100上原始推理4.9Hz、优化后10.6Hz；真实机器人每次预测16个动作并执行其中8个，用异步chunk覆盖下一轮推理。附录表12给出优化后中位94.6ms、P95为95.1ms，不能外推到低端机载设备。[原文§3.5及附录F](https://arxiv.org/html/2610.26854v2)

判断：最有价值的PoC不是立刻复刻整个双骨干，而是在现有VLA上测试“动作词监督+未来latent监督”是否帮助阶段切换与故障重试，再决定是否承担视觉和触觉全栈成本。若要验证无在线触觉部署，应单独测试未见物体、传感器缺失时的初始状态和长期误差累积。仿真接近饱和的LIBERO结果宜作为基准检查，不宜作为唯一选型依据。

## 8. Koi: Evidence-Guided, Self-Calibrating Planning for Multi-Cloud, Heterogeneous LLM Inference Fleets

### 1）基本信息
- 作者：Mankeerat Sidhu、Gangmuk Lim、Hetarth Chopra、Maximillian Eisenberg、Quan Hao Ng、Aryan Gosaliya、Shu Liu、Luka Govedič、Jiaxin Shan、Hongkuan Zhou、Vikram Sharma Mailthody、P. Brighten Godfrey、Ion Stoica。
- 领域：Inference、AI Systems、Agent。alphaXiv展示v1、2026-10-19；精确时间和时区未提供。非标准页面ID不是arXiv编号，尚未核实标准arXiv链接。
- [alphaXiv](https://www.alphaxiv.org/abs/2610.koi-heterogeneous-llm-inference-planning)｜[原始16页PDF](https://www.alphaxiv.org/abs/2610.koi-heterogeneous-llm-inference-planning.pdf)。已读§1–8的方法、表1–4及限制；PDF截图请求失败，表格依据可读取正文，未声称完成图像视觉审阅。

### 2）解决的问题
混合在线与批处理推理时，同一GPU可能适配多种模型、并行度与引擎配置；把一份资源分给某任务也有机会成本。Koi要处理的是较慢的fleet规划控制面，不是逐请求路由器：在性能预测不准、工作负载变化的情况下，决定分配与重配置，同时兼顾SLO、成本和切换代价。

### 3）核心方法
输入当前资源、任务状态、遥测与预测；用固定的“决策→运行机制→结果”图组织证据，按作用范围维护机制可信度；分层LLM规划候选，性能工具和确定性校验器负责打分与约束；选择可行计划执行，再用残差修正后续不确定性与探索强度。计划的真实效果回流证据，而不是把LLM口头解释当性能测量。[原文§4–5](https://www.alphaxiv.org/abs/2610.koi-heterogeneous-llm-inference-planning.pdf)

已读公开代码对应这一闭环：mechanism_registry.py将作用范围与边集合编码成稳定身份，维护Beta证据及活跃/归档状态；fsm_states.py的S5校验失败后允许修复，再失败保留当前方案；resource_map.py按实际遥测确认副本占位，不把无SM利用率误当副本死亡。后者对空闲但存活实例尤其重要。[机制库](https://github.com/Tandemn-Labs/tandemn-koi/blob/4826bcee17104808793809a18031c9e3b5bbe028/src/core/mechanism_registry.py)｜[状态机](https://github.com/Tandemn-Labs/tandemn-koi/blob/4826bcee17104808793809a18031c9e3b5bbe028/src/orchestrator/fsm_states.py)｜[资源账本](https://github.com/Tandemn-Labs/tandemn-koi/blob/4826bcee17104808793809a18031c9e3b5bbe028/src/infra/resource_map.py)

### 4）最大亮点
值得借鉴的是“可证伪预测+范围限定证据+确定性计划校验”三个接口，而不是单独采用LLM当调度器。变化后的任务不能无条件沿用旧环境可信度；切换成本与保持当前部署也被当作规划选项，避免过度重排。

### 5）实验能否支持结论
作者在104 GPU、25个混合任务、10种模型架构上做3小时真实实验；另有400/800 GPU仿真。表2真实实验Koi的SLO goodput为4119.51，对比OpenEvolve 3497.43，约高17.79%；每SLO-token成本口径0.24对0.30（表中单位为10^-4美元），低20%。goodput计入满足SLO的输出token，不是原始吞吐；成本包含闲置fleet。[原文§6、表2](https://www.alphaxiv.org/abs/2610.koi-heterogeneous-llm-inference-planning.pdf)

表4消融支持工具、图和在线更新各有作用，但属于仿真；不能把全部baseline和12小时结论转为真实多云证据。真实实验只覆盖三种比较对象。表3同构小规模12小时仿真仅约1.3% goodput提升，batch进度反而36.62低于对照40.06，不能称所有指标全胜。尚未证明长期运行稳定性、跨云完整生产外推或全局最优；收敛有假设，12小时也不足验证长期性质。

**公开代码与论文约束的对应缺口：**当前固定提交的validator.py明确将SLO/DRO风险作为score-only，并注释掉C7硬SLO检查；缺部分依赖时相应检查会跳过。已读状态机S5调用该val_plan，feasible即转部署。因而不能把此开源快照称为已具备论文全部硬SLO安全门；其他执行器是否补足未完全审计。这是代码交付范围差异，不直接推翻作者的实验数据。[validator.py](https://github.com/Tandemn-Labs/tandemn-koi/blob/4826bcee17104808793809a18031c9e3b5bbe028/src/validation/validator.py)

### 6）现在为何热门
事实：今日快照第8，昨日可见榜第3；现在能读到原始PDF和明确代码链接，昨天报告未能读取这些。不能把“今天可读”写成“今天发布了新版本”。代码所读提交日期为9月17日17:51:05 UTC（北京9月18日01:51:05），也不能包装为今日上线。目前只能确认论文热度高，尚无足够公开证据解释传播原因。[提交](https://github.com/Tandemn-Labs/tandemn-koi/commit/4826bcee17104808793809a18031c9e3b5bbe028)

### 7）工程价值
对有异构GPU池、多任务SLO与部署运维团队的用户值得深入，对单一托管LLM API的React/Django应用直接收益有限。优先借鉴预测账本、作用域证据与保守回退，先做只建议不下发的shadow planner。真正上线前必须核实硬约束、租户配额、回滚和遥测缺失处理。

代码准备度有门槛：Python≥3.12，依赖ai-dynamo、aiconfigurator及一个本地路径tandemn-store；不是独立仓库安装即可获得完整生产执行面。本次核查README、依赖和上述四个实现文件，未部署或跑benchmark。[依赖](https://github.com/Tandemn-Labs/tandemn-koi/blob/4826bcee17104808793809a18031c9e3b5bbe028/pyproject.toml)

## 9. SteerAct: Unlocking Action Models through Few-Shot Temporal Steering

### 1）论文信息

- 作者：Kaichen Zhou、Zhiyan Li、Chongkai Gao、Yuhan Wang、Wenlong Huang、Maggie Wang、Fangneng Zhan、Manling Li、Qianqian Wang、Mac Schwager、Zhuang Liu、Li Fei-Fei、Mengyu Wang、Paul Pu Liang。Zhou / Li 共同一作，Mengyu Wang / Paul Pu Liang 共同指导；机构覆盖 MIT、Harvard、Stanford、Imperial、Northwestern、Princeton。
- 版本：arXiv:2610.25632v1，2026-10-19 01:20:06 UTC（北京09:20:06）提交，cs.RO；本次未看到会议录用信息。[arXiv 记录](https://arxiv.org/abs/2610.25632)
- [alphaXiv](https://www.alphaxiv.org/abs/2610.25632) · [完整原文](https://arxiv.org/html/2610.25632v1) · [项目与视频](https://steeract.github.io/) · [代码](https://github.com/kaichen-z/SteerAct)。代码核查版本为 [f038528](https://github.com/kaichen-z/SteerAct/commit/f03852812a980593f647ae63c9f4036c9cb97b8b)，2026-10-20 更新。

### 2）研究问题

机器人已经有一个会做任务的动作模型，但偶尔做不好；只有少量带成功/失败标签的试运行时，能否不再更新动作模型权重，而是在执行过程中修正内部表示？难点不仅是找到“成功特征”，还包括：什么时候应该介入、朝哪个方向改、改多少，以及证据不足时如何不乱改。这里不是让机器人凭24次尝试从零学会任务，而是给已有能力增加运行时控制层。[项目说明](https://steeract.github.io/)

### 3）方法拆解

核心是“一个时间描述符，串起离线选特征和在线纠偏”。已核对公开实现：

1. SAE把隐藏状态变成稀疏特征。某特征在各决策步的非负平均激活形成一条时间序列。
2. descriptor函数取间隔1和2的三点序列，各统计6种大小顺序，再加熵、并列比例、是否有有效窗口，得到18维向量。它描述涨跌结构，不要求两次执行逐帧对齐。
3. 离线以成功/失败之间的距离减去各自内部离散度来排序特征，并保存参考库。每种结果至少需要两条轨迹。
4. 在线先过support gate：历史统计是否得到参考数据支持；再过failure gate：是否更像失败而不是成功。
5. 两道门都开，才在−10到+10、步长0.5的41个系数里选修正。代码比较“只改当前激活”后描述符到成功库的距离；如果没有严格改善，系数为0。真正改完后重新测量，把实测值反馈进历史。[控制器源码](https://github.com/kaichen-z/SteerAct/blob/f03852812a980593f647ae63c9f4036c9cb97b8b/steeract/method.py)、[特征排序源码](https://github.com/kaichen-z/SteerAct/blob/f03852812a980593f647ae63c9f4036c9cb97b8b/steeract/ranking.py)

这不是预测未来动作或最终成功率的世界模型，也不是控制安全证明。我的理解：它是基于经验统计的、带拒绝介入机制的隐藏状态反馈控制器。

### 4）值得注意的亮点

- 新意主要在“用同一时间统计表示决定选谁、何时动、怎么动”，而非首次提出SAE或activation steering。
- 控制器零修正是明确候选；证据不足或找不到更好描述符时保持原策略，有利于把它当可旁路模块测试。
- 源码把参考种子、SAE身份、特征库和配置绑定，避免误用其他数据训练出的工件；排序还明确拒绝把不足的成功/失败数据补成有效参考。[排序实现](https://github.com/kaichen-z/SteerAct/blob/f03852812a980593f647ae63c9f4036c9cb97b8b/steeract/ranking.py)
- “单特征”强调低维可控接口，不代表单特征已经最优，见下面消融。

### 5）实验究竟证明了什么，没证明什么

作者报告的关键证据如下，数字均为成功率百分比；箭头表示Base→SteerAct Enc，不是相对提升百分比。

| 原文位置 | 条件 | 结果 |
|---|---|---|
| 表1 | π₀.₅ / RoboTwin九任务 | 69.0→77.7 |
| 表1 | π₀.₅ / DexJoCo九任务 | 62.3→71.9 |
| 表1 | Fast-WAM / RoboTwin九任务 | 69.3→78.6 |
| 表1 | Fast-WAM / DexJoCo九任务 | 23.3→26.8 |
| 表2 | 真机三任务平均 | 31.1→52.2；DrVLA为40.0 |
| 表3 | 单特征 / Top-2 / Top-4 | 77.7 / 79.6 / 80.0 |
| 表4 | VLABench：完整门控 / 无双门 / 冻结 | 36.13 / 22.38 / 23.63 |

仿真每任务200次留出评估；真机每任务30次。真机相对Base的差异显著（p=0.004），相对DrVLA尚未显著（p=0.10）。π₀.₅推理从207.9升到223.8 ms/decision。附录C还说明：此前已用每任务500个仿真成功demo微调底座，真机用30个demo；24条是额外参考轨迹预算，不是全流程数据预算。Fast-WAM的Click Mouse反降、Hanoi仍为零。上述结果支持“小量参考能改善冻结底座”，不支持零训练、普遍安全、所有任务必涨或单特征最优。[原文表1–4、附录C/F](https://arxiv.org/html/2610.25632v1)

我的评估：门控消融比挑选出的成功视频更有说服力，但仍不足以分离“行为阶段”与“瞬时状态”的因果作用。真实部署还需要把碰撞、过力、时限、失败恢复分别计分，不能只看终局成功率。

### 6）热度：可见事实与未知

本次单篇页返回Trending #9、69 views；GitHub页面显示6 stars、0 forks。这只是读取时的公开页面快照。[alphaXiv](https://www.alphaxiv.org/abs/2610.25632)、[GitHub](https://github.com/kaichen-z/SteerAct)

不知道：流量来源、排序权重、独立复现数量、企业采用量。我的推测：少量轨迹、冻结大模型、单特征可控和真机演示的组合很适合引发关注；没有证据证明这就是上榜原因，更不能由作者机构或名次推出可靠性。

### 7）工程价值与落地判断

适合：已经拥有π₀.₅/Fast-WAM与仿真评估管线、能读写中间激活、愿意先做受控A/B试验的团队。它更像“已有策略的轻量增益层”，不应视为修复基础能力缺失的通用补丁。

公开代码有三个会直接影响复现的陷阱：

- 配方默认steering.top_k=4，不是论文主张的单特征。应改成1，并重新rank后再infer；不要与SAE稀疏度sae.top_k=100混淆。[实际配置](https://github.com/kaichen-z/SteerAct/blob/f03852812a980593f647ae63c9f4036c9cb97b8b/configs/pi05_all_tasks.json)
- 当前发布主要覆盖RoboTwin九任务；DexJoCo、真机、基线runner、预训练SAE/参考库、固定外部依赖版本和自动测试并未完整随包给出，且未包含license文件。公开可读不等于商业使用授权已明确。[发布范围](https://github.com/kaichen-z/SteerAct#release-scope)
- 默认评估步数上限乘2，基线必须统一预算；适配器期待特定XPolicyLab/OpenPI接口，普通RoboTwin安装不一定直接可用。[运行时实现](https://github.com/kaichen-z/SteerAct/blob/f03852812a980593f647ae63c9f4036c9cb97b8b/steeract/runtime.py)、[π₀.₅适配器](https://github.com/kaichen-z/SteerAct/blob/f03852812a980593f647ae63c9f4036c9cb97b8b/steeract/backends/pi05.py)

建议的最小验证顺序（工程建议，未执行）：先锁定底座和外部版本；统一时限、种子与观测；复现top1和top4；保留不介入及双门关闭对照；最后观察延迟尾部与危险动作率。当前可读可改，但不是开箱即用的全论文复现包。

## 10. Kronecker Delta Rule for Long Context Linear Attention

### 1）论文信息

- 作者：Anamaria-Roberta Hartl、Levente Zólyomi、Michael List、Günter Klambauer、Sebastian Böck、Sepp Hochreiter；前两位共同一作，机构为Johannes Kepler University与NXAI。
- 版本：arXiv:2610.26834v1，2026-10-19 17:56:52 UTC（北京10月20日01:56:52）提交，cs.LG / cs.AI；本次未看到会议录用信息。[arXiv记录](https://arxiv.org/abs/2610.26834)
- [alphaXiv](https://www.alphaxiv.org/abs/2610.26834) · [完整原文](https://arxiv.org/html/2610.26834v1) · [代码](https://github.com/NX-AI/KronLSTM) · [四个模型权重](https://huggingface.co/collections/NX-AI/kronlstm)。核查代码版本为[3d800c9](https://github.com/NX-AI/KronLSTM/commit/3d800c9a153a88ee9624fe6acf7f39a58017a17e)，2026-10-20更新。

### 2）研究问题

线性attention用固定大小矩阵记忆替代随上下文增长的KV cache，但“写新记忆”可能破坏旧记忆。DeltaNet会修正某个key取出的整条value向量；本文问：能否只修正特定key–value配对的关联强度，从而减少长文本中的串扰？这不是增加无限记忆容量，而是改变有限记忆如何被重写。[算子说明](https://github.com/NX-AI/KronLSTM/blob/3d800c9a153a88ee9624fe6acf7f39a58017a17e/fla/ops/kronlstm/README.md)

### 3）方法拆解

将记忆写成S，当前key/value写成k、v。基础更新为：S_new = S − β(vᵀSk − c)vkᵀ。

其中vᵀSk是这个配对当前的标量关联强度，c是目标；更新只沿vkᵀ这一条矩阵方向。旧配对受多大影响，取决于“key相似度×value相似度”，而不仅是key相似度。任一侧正交就不受该步改写影响。向量化以后，它等价于在k⊗v这个Kronecker特征上做标量delta rule，因此不是把Kronecker符号用于装饰。[规则与推导](https://github.com/NX-AI/KronLSTM/blob/3d800c9a153a88ee9624fe6acf7f39a58017a17e/fla/ops/kronlstm/README.md)

模型层再加入三个分工独立的门：按key维度遗忘、β控制擦除、c控制写入；默认把擦除和写入解耦。q/k/v先经过短卷积，q/k归一化，默认v也归一化；输出仍用RMSNorm，因此“无需额外记忆稳定器”不等于“完全没有归一化”。实际代码把S转置存储；naive.py里的逐token参考实现，先衰减S，再算标量score和write-minus-erase系数，再做外积更新。[层实现](https://github.com/NX-AI/KronLSTM/blob/3d800c9a153a88ee9624fe6acf7f39a58017a17e/fla/layers/kronlstm.py)、[参考实现](https://github.com/NX-AI/KronLSTM/blob/3d800c9a153a88ee9624fe6acf7f39a58017a17e/fla/ops/kronlstm/naive.py)

训练没有真的展开巨大k⊗v：代码用key Gram与value Gram逐元素相乘形成chunk内系统，保留分块并行路径；推理则有逐token fused recurrent kernel。这是从公式走向可用吞吐的重要部分。[kernel设计](https://github.com/NX-AI/KronLSTM/blob/3d800c9a153a88ee9624fe6acf7f39a58017a17e/fla/ops/kronlstm/README.md)

### 4）值得注意的亮点

- 将“少破坏旧记忆”落实到明确可计算的干扰项，而非只靠benchmark命名。
- 有理论、朴素参考、Triton kernel、模型层和权重，材料比只有新公式的论文完整。
- 仓库测试实际比较了reference/chunk/recurrent的输出、最终状态与梯度，还覆盖门控变体和部分非整chunk长度；这说明作者提供了怎样的验证途径，不代表本次独立跑过或确认通过。[测试源码](https://github.com/NX-AI/KronLSTM/blob/3d800c9a153a88ee9624fe6acf7f39a58017a17e/tests/ops/test_kronlstm.py)
- 模型有纯线性和5:1线性/SWA混合版本，能让使用者检验局部精确attention与压缩记忆如何组合。[模型集合](https://huggingface.co/collections/NX-AI/kronlstm)

### 5）实验究竟证明了什么，没证明什么

主对比为1.5B参数、100B训练token、8k上下文；不是拿更大模型直接压小基线。32k版本在75B token处分支，用最后25B继续长上下文训练。[模型训练说明](https://github.com/NX-AI/KronLSTM)

| 原文位置 | 关键对比 | 作者报告 |
|---|---|---|
| 表1，纯线性 | Avg-6：KronLSTM / 最强对比KDA | 59.72 / 58.12 |
| 表2，2k真实召回 | KronLSTM / GDN | 30.31 / 29.81 |
| 表A4，32k训练后16k S3 | KronLSTM / GDN-2，纯线性 | 41.8 / 7.4 |
| 表A4，32k测试S3 | 同上 | 8.6 / 0.8 |
| 表A4，32k测试S1 | 同上，反例 | 81.4 / 97.8 |
| 表A3，16k NIAH均值 | 默认 / 固定目标 | 14.3 / 10.1 |
| 图6，单H100训练吞吐 | KronLSTM | 36.8–44.5K token/s，比GDN-2高11–18%；GDN仍最快 |

证据支持特定规模/预算下的竞争力，尤其部分长上下文检索；不支持“32k检索已解决”或“全面最快”。表A3也并非默认在所有指标胜出。理论使用独立同分布配对、步长和二阶矩等条件，不能推广为任意真实文本/训练过程的无条件稳定保证；附录A5指出更长保留伴随更慢适应。[原文表1/2/A3/A4、图6、§2.1和附录A5](https://arxiv.org/html/2610.26834v1)

我的评估：S3的相对增益很大，但32k绝对准确率仍低，正说明“比另一种压缩记忆好”与“能可靠代替全文检索”是两件事。这里也没有足够证据把所有提升都因果归于低串扰，更没有展示大规模指令模型、工具代理或百万token环境中同样成立。

### 6）热度：可见事实与未知

本项沿用采集清单第10项；北京时间11:09（原始03:09 UTC）复查单篇页时已显示Trending #11，说明名次会变化。页面返回91 views；GitHub为27 stars、2 forks，模型集合为5 upvotes。[alphaXiv](https://www.alphaxiv.org/abs/2610.26834)、[GitHub](https://github.com/NX-AI/KronLSTM)、[模型集合](https://huggingface.co/collections/NX-AI/kronlstm)

不知道：真实排序原因、外部生产采用、独立复现结论。我的推测：xLSTM/DeltaNet路线、可分析的记忆更新和开源kernel/权重共同降低了讨论门槛；不能把这种合理推测写成流量归因，也不能把star当效果验证。

### 7）工程价值与落地判断

适合：做recurrent/linear attention训练、长输入记忆与kernel优化的团队。对于只调用闭源LLM API的应用开发者，它不是能直接打开的配置开关；更适合作为待评测的模型架构，而不是立刻替换现有RAG。

已核查的实现约束：

- MIT许可；基于FLA快照，安装仍使用flash-linear-attention / fla包名，会替换同环境已有FLA，建议隔离环境。
- 作者验证平台是H100/A100；其他GPU/backend未验证。chunk长度固定64，head的K/V不超过256；没有context parallelism，也没有grouped value attention。
- recurrent state采用fp32；fp32 dot默认TF32与高精度reference可有约10⁻³差异，精度排查要区分输入dtype、dot模式和状态dtype，而不是只看“稳定”这个理论标签。[README](https://github.com/NX-AI/KronLSTM)、[kernel数值与限制](https://github.com/NX-AI/KronLSTM/blob/3d800c9a153a88ee9624fe6acf7f39a58017a17e/fla/ops/kronlstm/README.md)

一个可用于容量规划的推算：默认纯线性配置24层、16头、每头128×128，若每个矩阵元素fp32，则单序列矩阵状态约24 MiB。此为按配置计算，不是实测峰值；不含模型权重、卷积状态、激活或混合层SWA缓存。[配置源码](https://github.com/NX-AI/KronLSTM/blob/3d800c9a153a88ee9624fe6acf7f39a58017a17e/fla/models/kronlstm/configuration_kronlstm.py)

建议的最小验证顺序（未执行）：先用公开1.5B权重测自己业务里的重复key、事实覆盖、近期信息更新和长距离召回；再测prefill、逐token decode及峰值显存，别用训练吞吐替代服务延迟；最后才评估训练迁移。最有价值的是一个可实现、可测试的记忆改写机制，现有证据还不足以承诺生产级长上下文可靠性。

## A. 今天最值得深入读的3篇

按用户AI应用、编码agent和推理工程需要选择，不按热榜名次：

1. **HarnessPro**：先读§4、表2/3及runtime/hook.py。最容易迁移的是“质量底线+不同预算档+可恢复工具输出”，而不是立即复刻自我改写。公开最终产物与完整优化框架的边界必须保留。
2. **Reward Misspecification**：先读§3.4、表1/2与training/loop.py、monitorability_metrics.py。对自定义reward、代码判题和LLM-as-judge尤其有用：奖励、真实完成度、可监控性是不同指标。
3. **Koi**：先读§5、表2/4及validation/validator.py、orchestrator/fsm_states.py。适合研究怎样把LLM建议与可执行约束隔开；当前硬SLO实现缺口意味着应先做shadow planning，不直接接管生产GPU池。若没有自建推理fleet，该项可降为架构阅读。

## B. 今天这10篇支持的研究趋势

1. **优化对象从模型扩到运行系统。** HarnessPro改harness，Koi改fleet规划；两者都强调性能/成本，但费用口径和执行安全边界不同，不能横比论文里的美元数字。
2. **固定记忆容量下更精细地写、读和干预。** MemT做在线记忆状态，KronLSTM减少关联串扰，SteerAct对少数隐藏特征做有门控修正。共同点是状态设计；不代表三者已证明同一种“无限记忆”。
3. **具身研究在统一表示，而非仅扩大控制模型。** W0统一跨本体动作条件，EgoX统一世界坐标，PhysWord为latent加动作语义锚。三种接口互补，但未证实可直接拼成完整闭环产品。
4. **“论文公开”与“可完整复现”分化明显。** EgoX/PhysWord核心代码待发，W0只公开部分规模，Halcyon默认权重分支与论文设置不同，SteerAct默认top4而论文主设置top1。工程选型必须查实际工件，而不只查有没有GitHub按钮。
5. **可审计证据比单一高分更重要。** 错误奖励可提高表面成绩而降低监控性；Koi公共代码的约束门与论文描述存在交付差异；多个机器人/记忆结果也有反例。这里只能提炼今日样本的共同问题，不据单日榜单宣称整个行业已转向。

## C. 和昨天相比

比较基线实际读取：[2026-10-20归档报告，固定提交5800119](https://github.com/DanielMax937/daily-research-reports/blob/5800119ad073c64a8ecca7aa5343eff39a3bb9e5/2026-10-20/ai-papers.md)。昨日北京时间12:13:30–12:13:52，亦为Trending/7Days，但只能确认前5项：LILIE、Discovery-RSI、Koi、RePR、T2-z。昨日第6–10不可读，因此今日任何其他条目都不能断言“首次进入完整Top10”。

- **连续可见：Koi。** 昨日#3，今日feed#8，名次下降5位是可见快照差异，不足证明传播热度显著降温。真正研究进展是今天读到了原始PDF、作者、方法、实验与公开实现；昨日这些未核实。没有证据说明论文今天实质修订，不能把访问改善说成作者新增成果。
- **相对于昨日可见5项的新见条目：** MemT、Reward Misspecification、Halcyon、W0、HarnessPro、EgoXperience、Physical Words、SteerAct、KronLSTM。保留“新见”而非“新入全榜”的口径。
- **昨日其余4项未在今日前10出现：** LILIE、Discovery-RSI、RePR、T2-z。未查完整更低排名，不能声称已无人关注或给出准确跌幅。
- **本次可见主题变化：** 今日具身/机器人接口和状态记忆论文占比更明显；昨日可见样本更偏编码优化、推理基础设施与文本diffusion。但昨日样本不全，不进行统计意义上的主题升温判断。
- **后续基线：** 本文件保留完整前10、筛选窗口、版本、实际阅读范围、代码固定提交和证据链接。下一次对连续论文应只新增可验证版本/实验/工件变化，不将再次读到同一内容当作新消息。
