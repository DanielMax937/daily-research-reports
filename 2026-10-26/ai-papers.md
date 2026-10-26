# AI论文日报｜2026-10-26

## 抓取口径与证据边界

- 北京时间2026-10-26 **11:26**（03:26 UTC）在实际云端浏览器访问alphaXiv，先从可见排序选择器切到Likes，再点击可见 **Trending**，核对 `sort=Hot&interval=7+Days` 和页面 **7 days**，刷新后按完整页面顺序取前10。[实际榜单](https://www.alphaxiv.org/?sort=Hot&interval=7+Days)
- 不把默认推荐流、搜索摘要、总点赞排序当今日热榜；中间切换曾暂只呈现6项，重载后读到完整20项，最终采用重载后的前10。此榜是**七日窗口在本次时刻的快照**，不是“今天发表前10”或过去24小时增长榜。
- 页面存在动态加载差异：完整快照后再次读取客户端曾只显示前6项。下表锁定11:26完整快照，不把后续瞬时条目数当“只有6篇”，也不承诺实时排名永久不变。单篇页和榜页若显示不同名次/计数，按各自时间与来源保留，不混拼成一个榜。
- 榜中包含非arXiv技术博客/平台上传稿，保留其实际位置，不替换为个人偏好的论文。非数字平台slug不当作arXiv编号。
- 来源中“论文报告”与本报告分析分开；没有独立复现实验、运行模型或执行未知代码。不能用论文存在自动证明作者所有强结论。
- 已读取10月24日实际归档；10月25日归档目录未见`ai-papers.md`，所以“与昨天相比”不可核。下文只与10月24日比，不宣称连续每日上榜。连续篇压缩旧背景，重点核新版本、代码和热度变化。[10月24日报](https://github.com/DanielMax937/daily-research-reports/blob/main/2026-10-24/ai-papers.md)

## 前10快照

|排名|条目|平台标识|Likes|Views|相对10月24日前10|
|---:|---|---|---:|---|---|
|1|A Fix for Softmax and Cross-Entropy|2610.31642|227|7k|5→1|
|2|Native Real-Time Interactive Omni Intelligence: A Unified Framework|2610.real-time-interactive-omni-intelligence|6|未提供|新入|
|3|Approximate Universal Prediction Under Interaction|2610.universal-prediction-interaction|2|未提供|新入|
|4|Kimi K3.1 Pro Tech Blog|2610.kimi-k3-1-pro|110|4k|1→4|
|5|Action Learning for Scientific Simulations|2610.31585|28|293|7→5|
|6|Agentic World Action Models|2610.30136|141|2k|2→6|
|7|Reading, Writing, Sharing, and Interacting with the World through Video|2610.31668|27|265|4→7|
|8|BeNice! Closing Looping's Inference-Memory Gap via KV-Sharing|2610.31633|20|225|新入|
|9|SuperMimic|2610.28480|271|5k|3→9|
|10|What Survives Eviction? Information Recall Locality in Transformer KV Caches|2610.information-recall-transformer-kv-caches|3|未提供|新入|

Views保留网页缩写，未倒推精确值；未提供不是零。点赞/浏览计数不是独立技术价值或排名算法的解释。

**交叉核验**：11:30–11:31单篇页面确认#1、#2、#3、#7、#8、#9、#10与本快照一致；Kimi详情也显示#4。BeNice网页提取路径一度返回#9/184 views，而云浏览器实时详情明确#8/20 likes，故不采用该异步读取结果覆盖主榜；本报告不把这些不同读取版本混成精确实时流。SuperMimic详情4,729 views与主榜5k分别保留各自显示，不强行视为精确同值。

## 1. A Fix for Softmax and Cross-Entropy：榜位上升，技术判断未因热度升级

### 1. 基本信息与实际阅读范围
作者 Jonathan T. Barron、Dan Gnanapragasam、Michael Tschannen；领域 Training / Numerical Stability / Distillation。[arXiv](https://arxiv.org/abs/2610.31642)本轮仍只列 v1，提交于2026-10-22 17:54:56 UTC，即北京时间10月23日01:54:56。[alphaXiv](https://www.alphaxiv.org/abs/2610.31642)本轮第1、227 likes、7k views；10月24日实际报告为第5、14 likes、363 views。这是两个快照，不能据此计算日增速或声称连续每日上榜。本轮重读原文数值推导、代码和实验表，并读取[作者项目页](https://jonbarron.info/softmaxfix/)；没有确认论文新版本。

### 2. 解决的问题
此前报告已解释两种有限精度错误：高置信度时目标梯度被舍入为零，以及蒸馏接近收敛时两个概率相减损失精度。今天没有证据把这个小规模数值稳定性结论升级为“大模型普遍失效”。[原文§1–3](https://arxiv.org/html/2610.31642v1#S1)

### 3. 核心方法
保留必要识别：硬目标由排除目标的 log-sum-exp 求 margin，再用 softplus，避免近1概率减1；软目标保留 teacher logits，以 logit 差、expm1/log1p 和自定义梯度避免近等概率相减。作者项目页实际展示 JAX `log_softmax`、`cross_entropy`、`soft_target_cross_entropy`，本轮读了这些实现；没有运行，也没有核到独立完整训练仓库。[原文§2–3代码](https://arxiv.org/html/2610.31642v1#S2)、[项目页](https://jonbarron.info/softmaxfix/)

### 4. 最大亮点
仍是可隔离的数值单测：相同 teacher/student 不应漂移，梯度应保持零和。修正浮点求值路径比“换一个损失函数”的宣传更准确；不是新的模型架构。

### 5. 实验能否支持结论
重核表1：模31加法、5 seeds，fp32、epsilon=1e-8，Fixed CE 为100.0±0.0%，Standard CE 为94.3±5.4%。该小任务对照支持算子机制，不代表语言模型性能同幅提升；正文仍未提供真实大型预训练和生产 fused kernel 吞吐验证。本轮未发现独立复现，未将作者的无显著减速表述视为生产验收。[§6表1](https://arxiv.org/html/2610.31642v1#S6)

### 6. 现在为何热门
本轮能确认榜位及平台显示关注量上升，也能确认作者项目页与可读代码存在；未读取足够原始社区讨论来解释此次排名上升的因果。目前只能确认论文热度高，尚无足够公开证据解释传播原因。搜索命中的二手 X 转述没有当作作者原话或热度证据。

### 7. 工程价值
优先把§2–3当作训练/蒸馏数值测试的设计材料：比较高 margin、同 logits、近 logits 三种边界，以及dtype、梯度和与下溢阈值。实现逻辑不长，但跨框架自动微分与融合kernel改造有成本。没有新证据要求立刻替换现有生产损失；应用层 RAG/React/普通API调用不直接受益。

## 2. Native Real-Time Interactive Omni Intelligence: A Unified Framework

### 1. 基本信息与实读范围
- 作者：Yifan Shen、Zhuoqing Zhong、Xinzhuo Li、Jiateng Liu、Bingxuan Li、Wei Cao 等，Ismini Lourentzou 为通讯作者；全文列43位作者。
- [alphaXiv](https://www.alphaxiv.org/abs/2610.real-time-interactive-omni-intelligence)详情页独立显示 **#2 on Trending**；2026-10-25 Submitted，6 likes；11:27北京时间的 More links 显示82 views。Submitted不等于首次公开日期。
- [全文PDF阅读页](https://www.alphaxiv.org/pdf/2610.real-time-interactive-omni-intelligence)，94页；未找到可核验的数字 arXiv 编号或版本历史，**arXiv链接/初版与修订日期待核**，不能把alphaXiv slug当arXiv ID。
- 领域：Multimodal / Agents / AI Systems / Evaluation。性质是**综述与概念框架**，不是已训练的新Omni模型。
- 实读：Abstract、原文p1作者/摘要、p21图6与融合架构、p42表9及§7评估、p51图14及能力保持证据局限；另读官方资源仓库README前部架构/目录与根目录。并非94页逐页通读。

### 2. 解决的问题
流式输出不等于真正交互：模型即使能连续说话，也未必能在新音视频证据、用户打断或工具异步返回后修正当前响应。综述把“理解和推理能力”与“何时说、停、等、改”的控制问题放到同一框架，面向语音助手、实时视频Agent及长期会话系统。

### 3. 核心方法
不是一套可直接执行的训练算法，而是对两条路线的组织：已有语言/Omni骨干加流式接口、模态模块与编排；或训练原生建模时间结构、连续输入输出及交互控制的模型。

原文图6（p21）的工程流程是：**持续输入→更新交互状态→低延迟前台监听/说话/反馈/让出话轮；后台并行检索、工具、推理、记忆→返回结果按当前状态重新验证→使用、延迟、修订或丢弃**。关键不只是并行，而是后台结果可能已经过期，必须具有插入、取消、验证与恢复策略。表9（p42）进一步把连续媒体调度、bounded session state、播放时间戳/队列清空/回滚、任务版本与取消关联到具体失效模式。以上来自[原文p21、42](https://www.alphaxiv.org/pdf/2610.real-time-interactive-omni-intelligence)，不是将AI Overview冒充原文。

### 4. 最大亮点
1. 将首音频延迟与“有证据的实质答案”区分开，避免把快速寒暄当作推理完成。
2. 把异步结果的来源、版本、取消和状态再验证提升为实时多模态系统的核心接口，而非额外补丁。
3. §7按延迟、时机质量、内容质量、鲁棒性、长会话质量、修复六维组织评估。其价值是评估框架，不是新的性能纪录。

### 5. 实验能否支持结论
**支持什么：**综述将已有系统的架构、数据与评测放到统一讨论中，提供可检查的设计问题与失效分类。图6、图14是概念图，不是实验曲线。

**没有证明什么：**p51明确承认已有系统使用不同骨干、训练数据、规模和评测设置，无法隔离单个设计的因果贡献。因此不能据此宣布前后台分离同时提高所有模型的推理能力和交互性，也不能称“能力损失不可避免”。本轮未看到这份框架自身的新模型训练、同骨干消融或统一benchmark成绩；无独立复现。

### 6. 现在为何热门
可确认的是当日详情页第2与10月25日Submitted；不能据此认定昨日才首次发布。官方仓库main读取到的提交为 `b7134cd7d6bdba5d8e020d541ad7fee1e0d14ee6`，作者时间2026-10-15 21:36:58 UTC，早于alphaXiv提交日期，说明平台日期和仓库材料时间不同。详情页本轮未呈现可署名讨论文本，未核实独立X/HN传播链。**目前只能确认论文热度高，尚无足够公开证据解释传播原因。**

### 7. 工程价值
对实时语音Agent、异步RAG工具调用最有价值的是任务版本、证据再验证、播放状态与取消协议，可据此给自己的服务列验收清单。这是阅读和设计收益，不是现成框架安装建议。

[官方仓库](https://github.com/ShenYifanS/Awesome-Interactive-Omni)实读根目录只有README、assets、docs、survey等文档资源，README把模型、数据、benchmark按行为需求编目；不能称它提供新模型训练实现。[已核commit的README](https://github.com/ShenYifanS/Awesome-Interactive-Omni/blob/b7134cd7d6bdba5d8e020d541ad7fee1e0d14ee6/README.md)。实现成本取决于既有音视频与模型服务，不存在本文已验证的统一GPU门槛。

## 3. Approximate Universal Prediction Under Interaction

### 1. 基本信息与实读范围
- 作者：Richard Cornelius Suwandi，香港中文大学（深圳）人工智能学院。
- [alphaXiv详情](https://www.alphaxiv.org/abs/2610.universal-prediction-interaction)独立显示 **#3 on Trending**；Submitted 2026-10-25，2 likes；本轮未核views。
- [原文](https://www.alphaxiv.org/pdf/2610.universal-prediction-interaction)，23页。未取得可核验数字arXiv编号、修订历史或官方代码链接，**arXiv链接/版本待核**。
- 领域：Agent Foundations / Reasoning / Alignment / RL。性质是数学理论论文，不是训练新Agent。
- 实读：p1–2摘要、引言与贡献，p7命题2/推论1/例1，p11定理4及证明，p15例6与§6；未逐行独立验证全部附录证明。

### 2. 解决的问题
在训练行为策略下平均预测损失很小，并不保证Agent规划后主动选择的分支同样准确。模型的乐观误差可能集中在数据很少的分支，规划器反而会追逐它；如果目标任务本身也罕见，误差迁移又多一层问题。这直接影响“世界模型够准所以规划安全”和“人工接管阈值一致所以行为安全”这类推断。

### 3. 核心方法
作者使用有限时域、归一化的因果Bayesian mixture作理想预测器，行为策略β产生训练轨迹，部署策略π选择后续动作；近似预测器ρ满足**总体轨迹KL预算**η，而非仅样本训练loss低。

Previous approach：被动序列→近似混合预测→稀有任务误差界。This paper：**行为策略轨迹→总体KL近似→部署占用比与预测前任务证据→联合迁移系数Γ→预测/规划/转交的条件保证**。

命题2（p7）把联合系数拆成部署与行为的占用比乘上当前历史的任务证据。只有两种最坏情况在同一预测位置对齐时，粗略的任务稀有性与行动覆盖惩罚才一起达到极端；**不是所有任务误差都必然按二者相乘**。定理4（p11）对[0,1]有界回报给出价值误差上界：进入覆盖不足分支的整局概率 δπ(c)，加 `sqrt((ln 2)cη/2)`，再截断到1；即便最大占用比无限也可有非平凡界。[原文p7、11](https://www.alphaxiv.org/pdf/2610.universal-prediction-interaction)。

### 4. 最大亮点
1. 明确“任务何时被识别”决定稀有性成本，而非只把两个最坏倍率机械相乘。
2. 用整局遭遇覆盖失败的概率处理无限最大占用比，避免只要有一个未见分支就让所有界失去解释力。
3. 例6（p15）区分接管决策一致与逐任务安全：两个策略都不请求接管，仍可在同一真实任务上一个成功、另一个必败。

### 5. 实验能否支持结论
**论文证明了什么：**在文中明确的有限时域、归一化因果模型、总体KL、覆盖与规划假设下，给出界、反例及证明。p7例1是三轮构造，p15例6是安全反例，不是实测Agent失败率。

**尚未证明什么：**不能从有限日志的经验loss直接认证总体KL与覆盖系数；定理4原文明确这些量不保证能从任意有限数据集估计。没有现实LLM benchmark、GPU成本或训练消融，不能把最坏情况构造当典型任务风险估计，也不能把结论不加条件延伸到原始Solomonoff半测度或真实无限时域系统。p15强调这不是对Golden Handcuffs原假设下结论的反驳。此次是阅读理论，非独立形式化验证或实验复现。

### 6. 现在为何热门
详情页显示第3、10月25日Submitted；未见可核验署名讨论、代码增长或独立传播证据。**目前只能确认论文热度高，尚无足够公开证据解释传播原因。** 不把“AI安全”主题本身当热度原因。

### 7. 工程价值
偏理论，最值得读的是p7联合证据系数、p11覆盖失败概率、p15接管反例。工程启发是评估coding/tool Agent时分别审计训练策略、实际选择分支、异常中间状态与接管后的行为，而不是只汇报平均任务分。该审计建议是研究者推断，不是本文已交付可运行的安全认证组件。代码、算力门槛未提供可核证据，无需为此立即替换Agent架构。

## 4. Kimi K3.1 Pro：延续发布状态，不把技术博客升级为训练论文

### 1. 基本信息
Moonshot AI，alphaXiv标注2026-10-23；技术博客，无确认arXiv编号或论文版本。领域：LLM / RL / Coding Agents / Multimodal。本轮实际重读[alphaXiv完整条目](https://www.alphaxiv.org/abs/2610.kimi-k3-1-pro)及[官方技术博客](https://www.kimi.ai/blog/kimi-k3-1-pro)正文、Availability、评测脚注。当前第4，110 likes、4k views；10月24日报第1、39 likes、510 views，注意两日间隔，非昨日变化。

### 2. 解决的问题
面向长程工具任务，将代码、建模与文档工作组织成可持续执行的项目，而非单轮答案。其效果依赖模型、工具harness、环境和验收共同作用，不能只把一个模型分数当成工作流质量。

### 3. 核心方法
官方仍描述为K3扩大后训练的版本，联合数百下游领域RL，并联动长上下文推理、rollout调度、沙箱及环境质检。没有公开到可复刻损失、训练数据配比与完整算力的程度。本轮未确认相对10月24日的新算法或新版论文；百万token上下文与Highspeed是产品能力声明，不是长文检索可靠性的证明。

### 4. 最大亮点
最值得读的不是宣传性领先名单，而是脚注显式区分harness、工具、子集及评分规则；它揭示同名benchmark可能不是同条件比较。环境质量控制也是重要工程方向，但当前公开内容不足以归因每个组件的增益。

### 5. 实验能否支持结论
**报告支持**：官方Terminal-Bench 4.0成绩65.7%，脚注说明Kimi用Claude-Code，其他成绩取各博客或官方榜的最大值，属于异源对照；不能说全模型同环境重跑。BenchCAD使用随机1,000例子集而非17,900例全集；alphaXiv所呈图注将92.7标为Voxel IoU，不能译成92.7%项目完整通过。[正文与脚注](https://www.kimi.ai/blog/kimi-k3-1-pro#footnotes)

**未证明**：不同harness/硬件/裁判完全公平、生产可靠性、所有任务重复性或完整成本优势。原文确实有部分多模态评测4–5次运行，不能笼统说所有实验都未重复；但未核到所有关键榜单完整置信区间。这里没有独立复现，也没有执行demo或模型。

### 6. 现在为何热门
可确认发布与今天第4，未确认新的发布事件足以解释今天热度。直接X先前403，本轮遵守停止状态未重试；条目可见嵌入内容不等于已读取原thread。不能将两日累计likes变化解释为单日传播速度或因果。

### 7. 工程价值
当前仍适合隔离的coding/证据型RAG验收，不应据榜单直接迁移生产。官方Availability仍写完整权重将在2026-11-04前发布，未确认已交付可本地复现权重；本轮没有确认新的API价格、配额或兼容变更。先准备同任务、同harness、同预算的验收集，比重复展示榜单更有价值。

## 5. Action Learning for Scientific Simulations（LEAP）：排名上升，未确认方法或代码升级

### 1. 基本信息、版本与阅读范围
Sarah Liaw、Yuanqi Du、Yilun Du；AI for Science / Dynamics / Energy-based Modeling / Inference。[arXiv](https://arxiv.org/abs/2610.31585)、[alphaXiv](https://www.alphaxiv.org/abs/2610.31585)。今日版本页仍只列v1：2026-10-22 17:22:08 UTC＝北京10月23日01:22:08。今日复核§2密度比构造、§4.1表1、默认分支提交和`leap/objective.py`；其余沿用10月24日已交付的§1–5、表1–4及代码审阅，不冒充一次新的全篇精读。

### 2. 解决的问题
这里的action是随机路径的作用量，不是Agent工具调用。局部转移预测可能遗漏整条轨迹依赖；LEAP让观察轨迹变成可评估、可优化的路径目标，供不同端点和约束复用。研究问题与10月24日相同，未确认范围扩展。

### 3. 核心方法
同条件真实路径与参考路径→对比训练密度比修正→参考负对数概率减中心化修正→路径评分或约束优化。[§2](https://arxiv.org/html/2610.31585v1#S2)需要可采样、可算概率且覆盖数据的参考过程。今天重读的[`objective.py`](https://github.com/SarahLiaw/action-learning/blob/6ad1a5a87634c9fac85115c1f3ded0816c27ab24/leap/objective.py)确实将一个正样本和K个参考分数拼接，交叉熵目标设首位，随后按参考均值居中；`action`返回`-reference_log_prob-centered_correction`。没有运行代码。

### 4. 最大亮点
价值仍是把学习路径评分与求解下游条件分开，而非每换端点就重训生成器。它不保证参考覆盖之外的轨迹仍可靠，也不能把全局修正自动解释为局部物理力。

### 5. 实验能否支持结论
今日重核表1：受控double-well漂移MSE为3.3×10⁻⁴，不能外推任意科学系统。保留前报限制：相同累积特征的binary NRE对照优于categorical目标，分子仅给端点时条件生成器也有优势，因此不能把效果全部归因InfoNCE。无新版实验、无独立复现；算力与大规模可用性不作补猜。[实验及限制](https://arxiv.org/html/2610.31585v1#S4)

### 6. 现在为何热门
相对10月24日第7→今日第5；likes 3→28，今日views 293，旧值未显示，不能计算浏览增量。当前仓库HEAD仍为`6ad1a5a87634c9fac85115c1f3ded0816c27ab24`，10月23日README修剪并非新增研究结果。[提交](https://github.com/SarahLiaw/action-learning/commit/6ad1a5a87634c9fac85115c1f3ded0816c27ab24)。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

### 7. 工程价值
仍适合作为可微评分与约束求解的设计参考，不是现成RAG/MCP插件。最值得读`objective.py`和前报已读的[`inference.py`](https://github.com/SarahLiaw/action-learning/blob/6ad1a5a87634c9fac85115c1f3ded0816c27ab24/leap/inference.py)：固定观测与自由变量分离。离散工具轨迹通常不可直接套用连续路径梯度；若将来复现，先做double-well而非直接上分子系统。当前没有理由仅因榜位上升修改采用判断。

## 6. Agentic World Action Models（AW-0）：代码与原文版本均无确认增量

### 1. 基本信息、版本与阅读范围
Zhuoyang Liu、Dantong Niu、Botong Zhang、Boning Shao等18位作者；Robotics / World Models / Multimodal。[arXiv](https://arxiv.org/abs/2610.30136)、[alphaXiv](https://www.alphaxiv.org/abs/2610.30136)。仍仅v1，2026-10-21 17:59:56 UTC＝北京10月22日01:59:56。本轮重核§2、§3.2表2及代码提交；不重复前报完整源码说明。

### 2. 解决的问题
程序规划易复用却缺少物理预测，视频—动作预测又缺少明确技能结构。AW-0把代码、未来视觉和控制共同建模；没有新增证据把这个受限机器人框架提升为通用自主Agent。

### 3. 核心方法
多视角图像、指令、机器人状态与短程序记忆进入三专家；代码使用离散去噪，视频和动作使用连续流匹配，通过代码→视频→动作掩码注意力耦合。程序可以只作条件；hybrid执行是另一层仲裁，不能混同所有预测代码都会执行。[§2](https://arxiv.org/html/2610.30136v1#S2)

### 4. 最大亮点
程序结构同时成为预测条件和可检查技能接口。它值得借鉴的仍是规划表示如何影响感知预测，而非“会生成代码即已经可靠执行”。

### 5. 实验能否支持结论
表2仍为8个实机任务、每任务3×16 rollouts，71.1%是步骤rubric平均，不是整任务成功率。保留前报随机场景泛化与hybrid训练条件的限制；今日没有新测试推翻这些边界。[§3.2及表2](https://arxiv.org/html/2610.30136v1#S3.SS2)。论文报告不等于我们独立复现或安全验收。

### 6. 现在为何热门
相对10月24日第2→第6；likes89→141，views1k→2k保留原缩写，不计算精确增量。名次下降和互动增加可同时发生，不能写成能力下降或已明显降温。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

### 7. 工程价值与源码
今日默认分支最新提交仍是[`7ad228bebb897bf01705cc10171e1d88cf5e9b22`](https://github.com/ZhuoyangLiu2005/agentic-wam/commit/7ad228bebb897bf01705cc10171e1d88cf5e9b22)，与10月24日相同；因此未发现该分支代码升级。延续此前已读的[`generic_mot.py`](https://github.com/ZhuoyangLiu2005/agentic-wam/blob/7ad228bebb897bf01705cc10171e1d88cf5e9b22/src/agenticwam/models/cosmos_mot/generic_mot.py)与[`agenticwam_model.py`](https://github.com/ZhuoyangLiu2005/agentic-wam/blob/7ad228bebb897bf01705cc10171e1d88cf5e9b22/src/agenticwam/models/cosmos_mot/agenticwam_model.py)作为耦合与mask设计入口。无新增证据改变“先小规模表示消融，再谈实机部署”的建议；普通全栈/RAG项目不需直接引入这套机器人训练栈。

## 7. Reading, Writing, Sharing, and Interacting with the World through Video：资源页清理，不是模型升级

### 1. 基本信息、版本与阅读范围
Shengqiong Wu、Meng Luo、Bobo Li、Ziwei Liu、Shuicheng Yan、Ming-Hsuan Yang、Philip Torr、Hao Fei；Video / World Models / Evaluation。是综述而非新可执行模型。[arXiv](https://arxiv.org/abs/2610.31668)、[alphaXiv](https://www.alphaxiv.org/abs/2610.31668)。仍仅v1：2026-10-22 17:59:50 UTC＝北京10月23日01:59:50。今日重核版本、§8.4表19及资源仓库差异；10月24日已定向读方法分类、视频Agent、统一模型评价、挑战和图13，非102页全部引用逐一验证。

### 2. 解决的问题
生成画面顺滑、视频问答正确与可用于控制的世界预测并不是同一能力。综述给这些主张建立分层评测语言；今天没有新增模型可供“跑分”。

### 3. 核心方法
沿用reading / writing / sharing / interacting四类组织框架，将视频观测、真实世界、模型内部状态分开。它是研究分类方法，不存在一个统一训练流程。今日表19仍按目标划分视觉合理性、动作响应、状态持续、延迟与决策效用，避免用一个总分代替全部能力。[§8.4](https://arxiv.org/html/2610.31668v1#S8.SS4)

### 4. 最大亮点
对工程最重要的是明确证据边界：静态重访测不到画面外变化；策略排序不等于执行任务成功；FPS也不等于动作响应延迟。原文未修订，亮点判断不变。

### 5. 实验能否支持结论
综述提供分类与评测索引，未提供统一模型必胜的受控新实验。前报检查的图13为共享开/关实验设计示意，不是结果图。今天未发现新增实验，不能因资料仓有提交就升级证据等级。未逐篇重新验证其引用工作。

### 6. 现在为何热门及真实更新
相对10月24日第4→第7，likes7→27，views113→265。可核的新增事实是配套资源仓于**2026-10-25 08:37:35 UTC＝北京16:37:35**提交[`1772b24063c36dd4c72259e456b9f6fd304825d8`](https://github.com/vid-gen/awesome-video-world-model/commit/1772b24063c36dd4c72259e456b9f6fd304825d8)。实际diff是README与SVG导航清理：移除引用数量标识、更新时间文字，以及资源链接均已验证的笼统措辞。没有模型代码或性能实验升级；也不能推断删措辞的动机。该维护提交是否影响热度没有直接证据。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

### 7. 工程价值
最新[`README`](https://github.com/vid-gen/awesome-video-world-model/blob/1772b24063c36dd4c72259e456b9f6fd304825d8/README.md)仍是文献导航，不是世界模型实现。以前报读到的结构化references作为知识库设计例子时，必须逐链接复核来源；不能沿用旧版“全部已验证”的文字替代自己的验证。优先把表19转成视频Agent验收表，分开验证证据时间戳、隐藏状态与交互延迟。技术判断不变，只更新资源快照与措辞。

## 8. BeNice!：把循环模型的缓存共享从偶然性质变成训练目标

### 1. 基本信息与实际阅读范围
作者 Hayden Prairie、Jacob M. Ryan、Taylor Berg-Kirkpatrick、Daniel Y. Fu；领域 LLM / Inference / Training / AI Systems。[arXiv](https://arxiv.org/abs/2610.31633)仅列 v1：2026-10-22 17:49:44 UTC，即北京时间10月23日01:49:44。[alphaXiv](https://www.alphaxiv.org/abs/2610.31633)本轮第8、20 likes、225 views；未出现在可读10月24日前10。作者[实验室博客](https://sandyresearch.github.io/benice/)标注October21，但没有精确时区，不能把它与arXiv提交混为一个时间。

实际读取：原文摘要、§1–6，尤其§3失败定位、§4方法、§5表3/5与图8–10对应正文，附录N/O配置；项目博客；官方GitHub目录和下列源码。PDF文本可读，PDF截图接口返回Cache miss，未将视觉截图审阅写成成功；图表数字以正文与HTML表格核验。未独立复现。

### 2. 解决的问题
循环模型重复使用同一组权重，参数存储不随循环次数增长，但每次循环单独存KV，推理缓存仍会增长。直接让各次循环共享最后一次KV并不可靠：有些模型保持质量，有些模型困惑度崩坏。目标用户是循环语言模型训练和推理系统研究者，而非把任意现成Transformer打开一个缓存开关。

### 3. 核心方法
**原方案：**输入→前置层→共享权重的多次循环（各存KV）→后置层→预测。**BeNice方案：**逐序列随机采样循环深度预训练→普通多循环预测与“第一次query/residual使用末次KV”的辅助预测共同训练→推理按层只保留一份共享KV。

随机深度促使状态向固定点收敛，但共享缓存可能在首轮引入偏移，收敛到另一个固定点。因此§4并不只要求“状态趋于稳定”，还联合普通语言建模loss与缓存交换辅助loss。代码核对了这一点：`block0_endpoints`捕获首/末轮，`cache_swap_ce`使用首轮query及残差、末轮KV重算，`RecFTModule.forward`组合 `ce + gamma * aux`。[§4](https://arxiv.org/html/2610.31633v1#S4)、[recft/model.py](https://github.com/sandyresearch/parcae/blob/4b86c2a34f6e8ca40d2f5e0bd3fc7925bf3db062/recft/model.py)

推理实现不是只有概念图：`sglang_parcae/planes.py`将`full`的每深度独立缓存索引改成`compress-s1`的每核心层单一索引，并验证索引覆盖和冲突；它清楚区分权重索引与KV存储索引。[源码](https://github.com/sandyresearch/parcae/blob/4b86c2a34f6e8ca40d2f5e0bd3fc7925bf3db062/sglang_parcae/planes.py)

### 4. 最大亮点
- 将“是否可共享”与“共享操作本身”分开，先用首层/首轮的定位及补丁对照解释失败，再设计训练目标；比只报告省显存有更强机制证据。
- 深度共享与数值精度压缩、MLA/KDA的每层状态压缩属于不同轴，原文分别组合测试，而非把不同节省率简单相加。
- 训练端缓存交换与服务端缓存索引都已在公开代码出现，使复核可以落到具体模块，而不只是一句开源承诺。

### 5. 实验能否支持结论
**论文报告支持的范围：**表5对公开Parcae模型做3 seeds微调。在770M上，普通FT不共享/共享PPL分别11.86/21.61；BeNice为11.85/11.86，说明该设置下改善主要是避免共享造成的退化，而不是原有模型突然大幅变强。模型范围包括140M至1.3B，附录配置列2048训练上下文、平均8循环、4步反传、bf16混合精度。[表5、§5.1](https://arxiv.org/html/2610.31633v1#S5.SS1)、[附录N/O](https://arxiv.org/html/2610.31633v1)

**必须分开的系统结论：**§5.3用SGLang、Mooncake请求轨迹、AIPerf，并把GLM等开放权重的中间层循环化构造代理模型。高负载2 req/s时作者报告吞吐+23.6%、p90 TTFT139.2→23.2秒；低负载0.5 req/s并无相应优势。它支持“接近饱和且缓存紧张时，共享可减驱逐/重算”的条件性机制，不证明一个保持同等任务质量的生产模型已实现这一整体收益。[§5.3与图9–10](https://arxiv.org/html/2610.31633v1#S5.SS3)

**尚未证明：**任意架构都可后训练获得共享性质、真实超长Agent任务不丢能力、模型规模扩大仍保持质量，以及用户具体硬件/SLA收益。本轮没有核到可直接引用的完整训练GPU小时；不能凭参数数目估算成本，也不能把“KV缓存相对循环深度不增长”写成总显存恒定。

### 6. 现在为何热门
可靠的新近事件是官方仓库`Add BeNice!`提交，时间2026-10-23 17:27:46 UTC（北京时间10月24日01:27:46），hash `4b86c2a34f6e8ca40d2f5e0bd3fc7925bf3db062`；本轮main即此提交。它证明公开实现交付，不证明今天传播峰值由该提交引起。未核到足够原始社区讨论或可靠Star时间序列，目前只能确认论文热度高，尚无足够公开证据解释传播原因。[提交](https://github.com/sandyresearch/parcae/commit/4b86c2a34f6e8ca40d2f5e0bd3fc7925bf3db062)

### 7. 工程价值
值得做推理系统研究的人深读，优先`recft/model.py`、`sglang_parcae/planes.py`及`recft/settings.py`。源码与权重入口公开；README列出140M–1.3B BeNice检查点，同时明确它们不是指令微调聊天模型。当前代码依赖PyTorch等训练环境，完整预训练有明显资源门槛，较合理起点是小模型共享/不共享质量对照，再验证缓存预算与吞吐；本次未安装或执行。对Agent/RAG产品的启发是把长上下文服务瓶颈拆成质量保持、缓存容量、负载曲线三份验收，不把一项压缩率直接等同于产品速度。[固定README](https://github.com/sandyresearch/parcae/blob/4b86c2a34f6e8ca40d2f5e0bd3fc7925bf3db062/README.md)、[依赖定义](https://github.com/sandyresearch/parcae/blob/4b86c2a34f6e8ca40d2f5e0bd3fc7925bf3db062/parcae_lm/pyproject.toml)

## 9. SuperMimic：无确认新版，训练覆盖仍不等于泛化

### 1. 基本信息、版本与阅读范围
Qiayuan Liao、Yiyang Shao、Junfeng Long、Kevin Zakka、Roberto Horowitz、Pieter Abbeel、Koushil Sreenath；Robotics / RL / World Models。[arXiv](https://arxiv.org/abs/2610.28480)、[alphaXiv](https://www.alphaxiv.org/abs/2610.28480)。仍仅v1：2026-10-20 16:29:30 UTC＝北京10月21日00:29:30。今日读取版本页、[官方项目](https://supermimic.github.io/)计算量、FAQ及评测脚注；原论文方法审查沿用已交付前报，不称今天重新精读全部PDF。

### 2. 解决的问题
许多动作共享身体动力学，逐动作专家或大集群无模型RL可能重复学习。方法尝试用一个可微世界模型摊薄大量动作跟踪训练成本。

### 3. 核心方法
仿真日志拟合世界模型，策略在短想象rollout上反传；世界模型和策略交替更新，不对物理模拟器求导。今日FAQ仍说明世界模型只在单次策略更新内固定，不是训练一次后永久冻结。[方法与FAQ](https://supermimic.github.io/)

### 4. 最大亮点
共享动力学与解析梯度训练闭环是重点，而非把“GPU少”本身当方法创新。没有确认新的架构或算法变更。

### 5. 实验能否支持结论
维持前报判断：单H100三小时超过SONIC发布checkpoint的0.90 normalized return，是作者报告且不同硬件/数据条件；不是同FLOPs对照。129,514项是训练动作覆盖测试，不能由零失败推出未见动作、随机扰动或真机安全率100%。今日项目脚注明确每项从首帧运行一次，固定摩擦、无域随机化及观察噪声，强化了此解释边界；不是新增独立复现。[计算量与评测脚注](https://supermimic.github.io/)

### 6. 现在为何热门
相对10月24日第3→第9，likes184→271，views4k→5k保留缩写。排名变化不能替代技术证据。目前只能确认论文热度高，尚无足够公开证据解释传播原因；未取得可证明这两日传播驱动的独立讨论链。

### 7. 工程价值、代码及门槛
当前项目页可读入口仍以论文、视频与浏览器演示为主，本轮未核到官方完整训练源码入口，不能声称开源可复现，也不能断言全网未发布。未运行演示或未知代码。对用户的价值主要是学习共享动力学与公平算力评估，不是立即替换RAG/Agent组件；下一步仍应等可审训练代码，并核同硬件、未见动作与现实接触误差。

## 10. What Survives Eviction? Information Recall Locality in Transformer KV Caches

### 1. 基本信息与实读范围
- 作者：Sungwon Kim、Daniel Khashabi（Johns Hopkins University）。
- [alphaXiv](https://www.alphaxiv.org/abs/2610.information-recall-transformer-kv-caches)详情页独立显示 **#10 on Trending**；Submitted 2026-10-25，3 likes。原文首页标注 **Published in Transactions on Machine Learning Research (10/2026)**，不能把平台提交日冒充论文初版日。
- [论文PDF](https://www.alphaxiv.org/pdf/2610.information-recall-transformer-kv-caches)43页；[OpenReview](https://openreview.net/forum?id=eAMLpW74rV)由原文首页给出，但本轮访问出现浏览器verification challenge，已停止，未读评审/修订史。数字arXiv编号未核实，不编造链接。
- 领域：Inference / KV Cache / Long-context / Evaluation。
- 实读：原文p1–2引言及图1、p5表1与§3.2–3.3、p10§4.3.2与图6（同时截图实际检查）、p13局限及结论；官方README、requirements.txt、`run_niah.py`、`recall_locality/eviction.py`、`recall_locality/inference.py`。

### 2. 解决的问题
删除源token的KV后，那些信息是否真的不可用了？探针能从剩余表征读到信息，不代表模型自己的生成能用它；反之，原文本缓存消失也不保证其情感影响完全消失。论文控制事实关联和情感关联，测模型实际回答，面向长上下文压缩、RAG缓存管理与记忆可靠性。

### 3. 核心方法
完整上下文prefill→按tokenizer offset定位实体/属性及紧随的标点→删除指定缓存位置→将保留keys的RoPE重新旋转为连续位置→从缩减缓存生成答案。对照包含不删除、删整对、只删实体或属性、保留/删除后续无关实体再提及，以及原本就没有目标内容。

表1（p5）的Synthetic Associations每样本20对实体属性；NIAH把关联放在约4096-token Paul Graham文本里，使用20组needle、43个有效深度×间隔格、5段背景，**每任务4300样本**。NIAH只使用4个4B以上模型，小模型在这个长度的提示敏感性会混淆比较。不是新压缩算法，也没有训练模型。

实现核对：[eviction.py](https://github.com/blindTissue/recall_locality/blob/947a32149180d862a74d89a060176d8a650f1765/recall_locality/eviction.py)深拷贝DynamicCache，各层index_select删除keys/values，并按保留旧位置与新位置之差做RoPE重旋转；Gemma3区分sliding/full attention频率。[inference.py](https://github.com/blindTissue/recall_locality/blob/947a32149180d862a74d89a060176d8a650f1765/recall_locality/inference.py)贪心解码、关闭Qwen thinking、固定chat模板日期，答案字符串匹配评分。[run_niah.py](https://github.com/blindTissue/recall_locality/blob/947a32149180d862a74d89a060176d8a650f1765/run_niah.py)明确共享prefill缓存并分四种条件，减少把prefill有无再提及与缓存保留混淆。

### 4. 最大亮点
1. 用真实生成行为，而不只是外部线性探针，定义“信息仍可被模型使用”。
2. 将源片段删除、后续提及删除、后续提及从未存在分开，控制信息传播与最终缓存可访问性。
3. 事实/情感明显不对称，提示统一token重要性策略可能掩盖不同信息类型的风险；这是实验发现，不是通用最优淘汰策略。

### 5. 实验能否支持结论
**支持什么：**主实验覆盖8个0.6B–8B指令模型、三族；NIAH的4模型43格平均结果见**图6、p10**：不淘汰事实准确率92.3%、情感86.5%；删除needle但保留后续提及后，分别1.1%、64.8%；同时删除needle与提及为0.4%、51.2%。因此后续提及对事实只增加0.7个百分点，对情感约14个百分点；情感是二分类，chance50%，不能把64.8%解释为高可靠恢复。这是论文报告结果，未独立复现。

**尚未证明什么：**p13明确没有70B以上模型，也未测试纯state-space或diffusion语言模型；两种更大的hybrid模型只是补充。还未定位最小信息载体是一个token、短语，还是特定head/layer；没有解释事实与情感差异的完整机制。受控关联与约4K背景不代表全部生产长上下文；这项实验也不等同于对所有压缩器的比较。原文结论把短语感知保留称为值得探索，不能写成已验证的最优解。

### 6. 现在为何热门
可确认第10与TMLR论文正文存在。官方仓库main为 `947a32149180d862a74d89a060176d8a650f1765`，提交时间2026-10-15 11:52:30 UTC（message init），因此不能把今天上榜写成今天刚开源。alphaXiv本轮未呈现署名评论；OpenReview评审因验证页不可读。**目前只能确认论文热度高，尚无足够公开证据解释传播原因。**

### 7. 工程价值
对RAG与长会话缓存很值得深入：回归测试应分别测“必须保留的事实召回”与“删除后是否仍有不希望的情感影响”，不要将删除源KV视作安全遗忘证明。先读`eviction.py`的重旋转和`run_niah.py`的配对对照。

[代码README](https://github.com/blindTissue/recall_locality/blob/947a32149180d862a74d89a060176d8a650f1765/README.md)给出Python≥3.10、每次实验一张48GB GPU、≤8B bf16；这是作者配置不是本轮实测。依赖固定torch2.11.0/transformers5.5.3/accelerate1.13.0/datasets4.8.4；模型有许可门槛，NIAH数据需构建、未随库附送。作者声称代码复现98–100%逐行正确性，本轮未运行，不能把它写成独立验证通过。

## A. 今天最值得深入读的3篇

1. **BeNice!**：最完整地连接问题定位、训练目标、真实缓存索引实现和条件性服务收益。优先§3–5、`recft/model.py`与`sglang_parcae/planes.py`；先核质量保持，再谈高负载吞吐，不能照搬代理模型速度结论。
2. **What Survives Eviction?**：适合长期Agent记忆、KV裁剪及遗忘语义的工程边界讨论。优先方法定义、实体再提及实验及局限；删除原token与彻底删除其后续影响是不同承诺。不是现成安全删除方案。
3. **A Fix for Softmax and Cross-Entropy**：数值故障与修复足够小，可转成明确单测。优先§2–3代码与§6表1；适合训练/蒸馏维护者，对普通模型API应用并非必须迁移。

## B. 从这次榜单得到的研究信号

- **缓存“省掉什么”和“保住什么”应分开验收。** BeNice关注跨循环KV共享的质量保持；What Survives Eviction关注删除位置后信息仍从后续状态读出的残留。二者都反对仅用省显存比例代替能力或遗忘保证。
- **稳定性是多层问题。** Softmax从浮点运算路径出发，Universal Prediction从交互中的覆盖与稀有分支出发；前者修梯度不代表后者的行为分布问题已解决。
- **“实时/世界模型”需要独立评价维度。** Omni与Video两份综述要求分开延迟、连续交互、记忆状态与反馈；AW-0、SuperMimic给出具体机器人框架，但不能由视频质量或训练动作覆盖推到安全自治。
- **新热度不一定代表新技术交付。** 多篇仍v1，Action/AW代码未变；Video只是文档维护，Kimi仍有权重发布承诺。单日样本只支持这些项目中的观察，不据此断言行业长期趋势。

## C. 与昨天相比，以及本次基线

**昨天（10月25日）可核日报缺失，不能给出昨天→今天的新入、连榜天数或涨跌。** 以下仅对照已实际读取的10月24日相同Trending / 7 days快照：

- 本次前10新出现：Omni综述、Universal Prediction、BeNice、What Survives Eviction。这里“新出现”不是首次发表。
- 两个快照均在前10：Softmax 5→1、Kimi 1→4、Action Learning 7→5、AW-0 2→6、Video综述4→7、SuperMimic3→9；不能把中间缺一天叫连续三天。
- 10月24日前10本次不在前10：Humanoid Mobility、FrontierCS 2、RAW-RAG、IQuest-Q1。不在前10不等于技术失效，也不能据此确认讨论明显降温。
- 相对新增主题：循环KV共享、缓存删除后的信息残留、实时多模态交互体系与交互预测覆盖界限。没有足够连续每日数据证明方向“持续升温”。

本次保留榜单顺序、显示指标、原文版本、实际阅读范围、固定代码提交和直接证据链接作为后续基线；不把运行时间更新本身算成新研究事件。所有实验数字均为来源报告而非本报告独立复现。
