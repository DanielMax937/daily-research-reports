# alphaXiv 研究日报｜2026-10-12
## 热榜核验受限：以下是公开首页的10篇展示样本，不是已确认的Hot前10

**今天最有工程价值的线索是：工具与验收如何限制Agent“看起来做对”、层级世界模型怎样缩短规划，以及重复数据训练中“损失变差”是否都等于能力退化。** 但今天未完成指定热榜筛选的核验，不能交付一份冒充已验证的热门排名。

### 采集口径与新鲜度

- 首次实际访问：[alphaXiv公开根首页](https://www.alphaxiv.org/)，约2026-10-12 **03:13 UTC / 北京时间11:13**。样本固定为该次返回中前10个论文条目，跳过“Researchers to follow”卡片；下面的编号是展示顺序，不是已确认的热榜排名
- 页面标题为Explore，返回文本未显示已选排序、Publication筛选或类别。显式Hot查询出现403或无法访问，未继续绕路重取被拒目标。因此**Hot/Trending/Popular中的实际选项、时间筛选及全类别状态都未核实**
- 另一次普通Explore入口重定向到根首页，却返回不同顺序与计数，且部分计数更低；没有响应头或后端时间戳可判断缓存年龄。“Crawled today”不能证明秒级实时。本报告不拼接两份结果、不选自己偏爱的顺序，也不把默认推荐当热榜
- 这是当天实际取得的网页响应，但精确数据生成时间未知。后续所有论文研究均围绕第一次返回的样本开展；今天新收入报告的条目不等于今天首发或新入热榜
- 昨日已读真实报告的口径是Hot / Publication 30 Days / All，快照时间2026-10-11 03:21:16 UTC。今天缺少筛选证据，**不计算榜位升降或“新增/跌出热榜”**
- 重复论文压缩旧背景，重新核arXiv版本和可读的官方发布信息。原文、项目说明、作者报告的实验与我的工程推断分开；未运行仓库、训练模型、复现实验或操作机器人
- 今日可读原文的覆盖以各篇为准。PDF/HTML的页面读取不等于逐行通读，网页表格核对不冒称视觉复现。原文或代码取不到的项目明确留下缺口

### 固定样本清单

| 样本编号 | 条目 | 首次首页显示赞 / 浏览 | 昨日报是否覆盖 |
|---|---|---|---|
| 01 | [Embodied Turing Machines](https://www.alphaxiv.org/abs/2610.12369) | 78 / 1k | 是，昨Hot #1 |
| 02 | [Recursive Self-Improvement through Multi-Agent Self-Supervision](https://www.alphaxiv.org/abs/2610.12176) | 41 / 508 | 是，昨Hot #3 |
| 03 | [MiMo-V2.6](https://www.alphaxiv.org/abs/2610.11959) | 72 / 867 | 是，昨Hot #2 |
| 04 | [Overfitting or Overconfidence at the Data Wall?](https://www.alphaxiv.org/abs/2610.overfitting-overconfidence-data-wall) | 2 / 未显示 | 否 |
| 05 | [BrickBench](https://www.alphaxiv.org/abs/2610.12452) | 18 / 156 | 是，昨Hot #9 |
| 06 | [NCM: Next-Concept Modeling](https://www.alphaxiv.org/abs/2610.next-concept-modeling-parallel-generation) | 33 / 298 | 否 |
| 07 | [H-JEPA](https://www.alphaxiv.org/abs/2610.06805) | 277 / 5k | 否 |
| 08 | [Long-WAM](https://www.alphaxiv.org/abs/2610.10528) | 100 / 1k | 是，昨Hot #4 |
| 09 | [A Balanced Data Diet](https://www.alphaxiv.org/abs/2610.12465) | 29 / 215 | 是，昨Hot #10 |
| 10 | [AgentGarten](https://www.alphaxiv.org/abs/2610.12374) | 42 / 477 | 是，昨Hot #5 |

计数均取第一次根首页返回，不用论文详情或搜索结果补齐。k为页面缩写，不换算成精确整数；“未显示”不等于零。它们不是当天新增量、独立访客数或质量分。缺少独立传播轨迹和已读讨论，因此不声称已查明热度成因。

## 样本01｜Embodied Turing Machines: Stateful Code for Robot Recursive Self-Improvement

### 1）基本信息、版本与今日差分
Kairui Hu、Siyuan Hu、Fangzhou Hong、Zhaoxi Chen、Ziwei Liu；NTU与Ropedia，具身Agent、代码策略。首次提交2026-10-08 17:29:08 UTC，今日历史仍只有v1。复读§3.1–3.4、§4.1–4.3及表2；没有重新计算PDF哈希，不把持续关注当新实验。[版本记录](https://arxiv.org/abs/2610.12369)

### 2）解决什么问题
能否把重复机器人任务中的决策固化为共享代码，用显式状态执行，将大模型投入移到离线开发？作者旧澄清强调模拟轨迹生成价值，并表示开发没有使用测试episode；今天仍可读，不是新发布回应。[作者说明](https://huggingface.co/papers/2610.12369)

### 3）方法与真实数据流
RGB、本体感知及指令进入状态更新器；冻结代码读环境、机器人与任务状态，输出轨迹。感知依赖已知相机、物体形状等几何常量，并非无先验视觉理解。离线coding agents分支改代码，经数值/碰撞检查与验证布局择优；默认关闭扩展对测试fixtures约束旧行为，并非所有未知状态的形式保证。[§3](https://arxiv.org/html/2610.12369v1#S3)

### 4）值得保留的亮点
我的工程判断：显式状态使错误能落到具体字段和代码分支，支持局部修复、回放与回归测试。阅读时分开评价状态可信度、控制稳健性与开发搜索成本；某一项提高不能替代另两项验收。

### 5）实验支持与局限
RoboDojo有42任务，每任务3个seed、每seed50布局；表2整体成功率70.24%，最强列出基线31.38%，75.45是进度分。泛化任务标准/随机布局77.3%/54.1%；同一程序测量状态63%、oracle83%，状态质量仍是瓶颈。[表2及§4](https://arxiv.org/html/2610.12369v1#S4)

这些比较支持已知任务族中的显式代码很强，但未隔离代码表示、几何先验和离线开发预算的贡献。在线不调模型不能推出全生命周期便宜，有限回归通过也不能保证未知场景不退化。本次未独立复现或重算置信区间。

### 6）热度与交付缺口
首次首页样本78赞/1k浏览，昨日真实Hot榜第1、50赞/866浏览；今天没有同口径排名证据。独立HF页显示20票、作者澄清标3天前，不能把不同平台计数合并或据此解释热度。[HF原讨论](https://huggingface.co/papers/2610.12369)

[官方项目页](https://etmcode-bit.github.io/)今天未能访问。昨天没有找到完整策略库，但今天应写“完整源码发布状态未核实”，不能断言今天仍未开源。在线无模型与递归改代码可能吸引读者，是内容推断。

### 7）工程价值
**B档，显式状态与回归机制值得读；原实验复制优先级有限。** 可先把状态稳定、重复率高的工具子流程变成受测代码。每次执行保存观察来源、状态版本、前置条件和终态验收，失败后重新测量，避免盲目重试。

RAG经验库应保存可重跑测试、适用条件与失败反例，而不是只收成功故事。MCP调用成功还需独立检查最终状态。试点同时量开发工时、回归成本、异常恢复、P95时延及每次正确完成的总成本。论文没有RAG/MCP实验，这些是迁移建议。先读§3状态接口→§4泛化结果→附录成本与回归边界，再决定是否值得搭机器人栈。

## 样本02｜Recursive Self-Improvement through Multi-Agent Self-Supervision（MASS）

### 1）基本信息、版本与今日差分
Hyunin Lee等七位作者，UC Berkeley与Sakana AI；多Agent自监督、工作流搜索及权重更新。首次提交2026-10-08 15:44:02 UTC，今天[arXiv历史](https://arxiv.org/abs/2610.12176)仍只有v1。复读§3、实验设置、表1、附录B.3/C.1–5及表7；核官方项目、README、复现和覆盖说明，没有声称重新通读39页。[原文](https://arxiv.org/html/2610.12176v1) · [项目](https://pub.sakana.ai/mass/)

当前main为[fb40358](https://github.com/SakanaAI/mass/commit/fb403581bed2c974b3f99e7236224169da643079)，10月9日22:49:21 UTC，仅改README拼写及来源清单；前一提交添加论文链接。未见10月11日后提交。昨日报未固定MASS SHA，不能声称完成昨日/今日文件级diff。

### 2）具体解决什么问题
开放研究缺便宜、可靠的正确性标签，同模型兼任执行、评审和改进者也可能强化自身错误。MASS尝试从协作结构制造自监督，再更新共享权重。它只展示两轮，不能据此推断无限持续进步。

### 3）方法与真实数据流
同模型实例扮主Agent、子Agent、评审及优化器，搜索角色、指令、输出契约和调用顺序。产物成对比较，反馈改下一工作流；每任务采18条候选、自评排序，最多15条训练、1条验证。SFT时删除主Agent输入中的优化工作流，尝试让权重从任务本身学会组织工作，再进入下一轮。[作者方法说明](https://pub.sakana.ai/mass/)

实现与论文有差异：公开RHI先与固定裸任务参照比，再做冠军仲裁；论文直接与保留最佳产物比。官方承认可能选出不同工作流，公开驱动并非精确逐步重现。[复现说明](https://github.com/SakanaAI/mass/blob/fb403581bed2c974b3f99e7236224169da643079/docs/reproduction.md)

### 4）值得保留的亮点
我的工程判断：比角色名称更值得复用的是交付什么文件、附哪些证据、下一阶段验什么。把调度和局部执行都保留为训练对象也值得检验。表1固定执行模型比较工作流胜率64%，比整套系统总分更有归因价值，但不代表各组件独立有效。[表1](https://arxiv.org/html/2610.12176v1#S4)

### 5）实验、消融与复现边界
v1表7的MLR为12题×5次：均分1.58→2.40，交付31/60→50/60；180次执行没有调用委派工具，不能直接将增益归于测试时多Agent协作。按任务聚合的配对检验p=0.2266，统计单位影响结论。[附录C.5](https://arxiv.org/html/2610.12176v1#A3.SS5)

当前README另报107题×3次、1.71→2.25，不能与v1小集拼接；同时Terminal-Bench37.5%→35.2%、SWE-bench62.6%→61.1%，并非通用编码全面提升。[固定README](https://github.com/SakanaAI/mass/blob/fb403581bed2c974b3f99e7236224169da643079/README.md)

公开MLR配置仍是12题；107题配置及AstaBench、DSBench、Terminal-Bench、SWE-bench适配器未包含。第二轮完整数据/预算溯源未验证，多项消融缺运行器。[实验覆盖](https://github.com/SakanaAI/mass/blob/fb403581bed2c974b3f99e7236224169da643079/docs/experiment_coverage.md) 因此“部分阶段可跑”不能替代全量复现；每输出token得分也不等于总训练成本收益。

### 6）热度与今日新增证据
首页样本41赞/508浏览；昨日报真实Hot第3、19赞/220浏览。今天榜单筛选未核，不称排名上涨。没有今日alphaXiv单篇讨论证据；多Agent、自改进与权重更新结合有传播吸引力只是推断。

今天新增的是代码快照及提交内容核查，未找到新论文实验或完整复现缺口已关闭的证据。

### 7）Agent / RAG / MCP / 全栈价值
**A档深读，先试工作流契约，再决定是否训练权重。** 固定模型、任务、预算与不可修改验收标准，比较裸提示、人工契约、搜索契约；分别记交付完整率、正确性、证据覆盖和成本。RAG可拆检索、冲突核查与引用交付；MCP可约定结构化输出和失败回报。以上均为迁移建议。

官方说明rollout会覆盖manifest，report会累计目录旧判定，比较实验应分目录，避免混池；第二轮1,624步是重建选择，历史精确清单缺失，GPU训练及端到端复跑未验证。[复现说明](https://github.com/SakanaAI/mass/blob/fb403581bed2c974b3f99e7236224169da643079/docs/reproduction.md) 阅读顺序：§3→C.5→实现差异与覆盖清单。真正适合照搬的是可审核的交付与验证契约，不是“多开几个Agent就自我进化”的口号。

## 样本03｜MiMo-V2.6: Scaling Reinforcement Learning Towards Self-Improvement

### 1）基本信息、版本与今日差分
Xiaomi LLM-Core Team，领域为多模态模型与Agent强化学习。首次提交2026-10-08 13:41:53 UTC；今天[arXiv历史](https://arxiv.org/abs/2610.11959)仍仅v1。重读RL方法、GAR、训练设置、router实验及表6–7；核两仓README、环境实现和配置，未重新通读43页或计算PDF哈希。[原文](https://arxiv.org/html/2610.11959v1)

官方公开分支与昨日一致：verl/mimo-oss仍为[a2ad9f6](https://github.com/XiaomiMiMo/verl/commit/a2ad9f6160b03ff2d47e59832bfb6b289f37c917)，最后提交9月26日；mimoagent/mimo-oss仍为[467f0a1](https://github.com/XiaomiMiMo/mimoagent/commit/467f0a19016f0ac4d63b8d17a1f0da9ba07f232c)，最后提交9月21日。这不证明容器镜像或其他分支未变。

### 2）具体解决什么问题
长程Agent的“通过测试”不一定等于正确完成任务；长轨迹、慢工具和不同执行框架也让训练难以稳定扩展。本文把奖励质量与系统工程同时处理，不能据标题理解为已实现无限递归自改进。

### 3）方法与真实数据流
每步1,568个prompt、每题16条rollout；异步GRPO结合多环境、多harness及router冻结。GRS离线生成rubric，GAR在线比较同题轨迹，将正advantage向质量较高的成功解重分配；确认作弊先归零。[§4–5](https://arxiv.org/html/2610.11959v1#S4)

开放实现分离Agent、模型协议、环境后端与数据集/评分器，统一轨迹、在任务环境原地验收。代码任务用uni-agent做模型网关/轨迹传输，其他几类通过verl AgentLoop调mimoagent。公开小模型起点与工业模型训练栈不能混为一谈。[mimoagent README](https://github.com/XiaomiMiMo/mimoagent/blob/467f0a19016f0ac4d63b8d17a1f0da9ba07f232c/README.md) · [verl README](https://github.com/XiaomiMiMo/verl/blob/a2ad9f6160b03ff2d47e59832bfb6b289f37c917/README.md)

### 4）值得保留的亮点
我的工程判断：
1. 功能通过以外，还需验范围、异常处理及副作用
2. 环境、轨迹、grader解耦，方便追究为什么得分
3. 开放环境的价值也包括让外部找漏洞；公开与可信应分别评估

### 5）实验、代价与未闭合反证
9B的SFT→领域RL，SWE-Pro44.6→47.6、Terminal-Bench2.1为37.1→52.8。GAR消融显示持续训练更稳，但token仍增加；不能说越训绝对越短。主模型RL分别花260万/90万美元，不是完整研发成本。[原文表6及§4](https://arxiv.org/html/2610.11959v1)

[官方模型卡](https://huggingface.co/XiaomiMiMo/MiMo-V2.6-Distill-Qwen-9B)明确公开权重是SFT起点，不是上述领域RL终点。不能以论文末端成绩给下载到的checkpoint标性能。

重要反证仍是[Vals AI原始审计](https://www.vals.ai/blogs/mimo-reward-hacking)：10月7日报告2,698个开放coding任务中1,795个保留可读修复对象。67%是环境泄漏比例，与论文“检测到的作弊轨迹低于2%”分母不同，也不足以证明全部benchmark均虚高。

今日核[固定HEAD环境实现](https://github.com/XiaomiMiMo/mimoagent/blob/467f0a19016f0ac4d63b8d17a1f0da9ba07f232c/src/mimoagent/environments/datasets/opensource_code.py)，默认运行时清理关闭，setup检查可达历史，清洁镜像被当作构建阶段前提。因此所查分支无新修复提交证据；镜像是否已重建未知，本次未运行镜像或独立重做审计。

### 6）热度与今日结论
首页样本72赞/867浏览；昨日真实Hot第2、35赞/510浏览。筛选未核，不能报今天排名或24小时增长。没有新alphaXiv讨论证据；开放资源与奖励漏洞审计都是可核关注素材，但是否导致流量变化尚无证据。

今天的结论是版本和所查分支稳定、环境可信度仍需审计，不是一次新模型发布。

### 7）工程价值与门槛
**B档，先读奖励与环境审计，再考虑RL复现。** Agent/MCP可以固定任务集，对照功能验收和“功能＋副作用”验收，记失败分类、token与墙钟；RAG分开衡量答案质量与证据使用，全栈分开验功能、需求遵从和视觉品质。这些是迁移建议，原文没有独立RAG消融。

[参考配置](https://github.com/XiaomiMiMo/verl/blob/a2ad9f6160b03ff2d47e59832bfb6b289f37c917/scripts/code/env.example)使用8节点×8GPU、262K上下文及独立任务pod配额，并非已验证最低硬件。先读§4.3的GRS/GAR→§6系统→表6，再读环境实现与审计；继续受关注不是提高立即全量复现优先级的理由。

## 样本04｜Overfitting or Overconfidence at the Data Wall?

### 1）基本信息、版本与阅读范围
Hanyu Yang，独立研究者；数据受限训练、概率校准与scaling-law测量。**本次没有核到该题名的arXiv记录，不给它编arXiv号或修订史。** 实际发布链为CALREP：代码与结果1.0.0标注2026-10-10发布，1.1.0于10月11日加入短论文，作者说明代码和结果未改。[首版引用记录](https://github.com/SeverinVisionary/calrep/blob/ce889c942e3f5d108c6bdaef65ee5f85da24f849/CITATION.cff) · [当前版本](https://github.com/SeverinVisionary/calrep/blob/main/CITATION.cff) · [1.1.0提交](https://github.com/SeverinVisionary/calrep/commit/bb6bbba769041f7bc3b49b05a62e01e804f422f8)

今日读取作者LaTeX全文各节、表1–4及图注，对照预注册、偏离记录、评估代码和结果JSON；未运行代码或做PDF版式核验。[论文源文件](https://github.com/SeverinVisionary/calrep/blob/main/paper/calrep_note.tex) · [alphaXiv条目](https://www.alphaxiv.org/abs/2610.overfitting-overconfidence-data-wall)

### 2）具体解决什么问题
[Lovelace等原研究](https://arxiv.org/abs/2605.01640)用额外惩罚项描述重复数据训练造成的损失，讨论模型规模与轮数分配。Yang追问其中多少损失能仅通过校正概率消除：验证NLL上升是否全部代表能力退化？这是诊断问题，不是证明重复训练无害。[研究问题与预注册](https://github.com/SeverinVisionary/calrep/blob/main/PREREGISTRATION.md)

### 3）方法与真实数据流
输入已有checkpoint和固定C4验证片段，权重不更新。文档按奇偶序号分A/B；同一次模型前向得到logits，累计不同温度的NLL。在A拟合温度、B评分，再反向交换，按token加权合成cross-fitted TS-NLL。分别用raw NLL和TS-NLL重拟合两阶段scaling law，比较惩罚系数。[预注册流程](https://github.com/SeverinVisionary/calrep/blob/main/PREREGISTRATION.md)

实际实现改为九点log-temperature网格加三次样条，边界命中时扩网格重算；不是预注册的直接标量优化。它避免保存完整词表logits，也不需每个温度重做模型前向。[评估代码](https://github.com/SeverinVisionary/calrep/blob/main/code/calrep_eval.py) · [D1/D1b变更记录](https://github.com/SeverinVisionary/calrep/blob/main/DEVIATIONS.md)

### 4）最值得保留的亮点
我的判断是贡献在测量设计，而非新校准算法：把概率过尖与其他泛化损失分开，且同时观察全局拟合系数与固定模型/数据单元的后期损失上升。

正温度缩放不改变同一上下文的logit排序，分数改善本身不证明知识增加或任务正确率提高；全局系数缩小也不等于所有checkpoint同等受益。[论文表3/4与结论](https://github.com/SeverinVisionary/calrep/blob/main/paper/calrep_note.tex)

### 5）实验支持、预注册失败与敏感性
覆盖125个C4 checkpoint，7M–2.8B参数、最多64轮。主要对照是相同模型与token上的校准前后。主惩罚系数0.003633→0.002478，剩余比例0.682；1,000次bootstrap的95%区间0.580–0.858，**不支持预注册“至少减半”**。[点估计](https://github.com/SeverinVisionary/calrep/blob/main/results/step2_point.json) · [bootstrap结果](https://github.com/SeverinVisionary/calrep/blob/main/results/step2_boot.json)

删去作者定义的11个发散run后，剩余比例升至0.811；替换惩罚形式也保留更多惩罚。“消除45%升幅”是七个不含发散run的上升单元的中位数，不能写所有过拟合减半。[敏感性与逐单元结果](https://github.com/SeverinVisionary/calrep/blob/main/RESULTS.md)

更重要的限制是评估器一致性：只有86.4%运行通过预注册核验，低于95%门槛；之后改用事后标准，结论属于探索性。连事后标准也失败的两个run仍留主分析。结果分片还缺评估代码版本记录，发布说明有勘误。作者报告CPU评估、无GPU，本次未重跑或核总核时。[原始检查](https://github.com/SeverinVisionary/calrep/blob/main/results/harness_check.json) · [D7偏离记录](https://github.com/SeverinVisionary/calrep/blob/main/DEVIATIONS.md) · [复现与勘误](https://github.com/SeverinVisionary/calrep/blob/main/README.md#records-and-errata)

因此更稳妥的结论是：在这批C4模型中，温度校准能改变重复训练损失的解释，但大量惩罚仍在，且评估协议不确定性不能忽略；不能外推到更大模型、其他语料或任务正确性。

### 6）热度证据
首页样本2赞，浏览未显示，不记为零。它没有出现在昨日报告的十篇里，但今天未核排序，不能叫新入热榜。可见讨论未返回正文，不声称社区支持或反对。相比鲜明标题，今天更有价值的是能检查作者完整的预注册和偏离记录。

### 7）工程价值
**A档诊断型深读，C档直接生产替换。** 有限领域数据反复训练时，可在面板同时显示raw NLL、校准NLL和真实任务成功率。RAG可以借鉴独立数据校准置信度、再测拒答/升级人工的决策质量；本文没有验证召回或引用忠实性。Agent概率更保守也不自动等于工具调用更可靠。

对MCP/全栈，直接算法收益未证实，更值得学的是把评估器版本、数据切片、失败检查和事后改动做成可追溯产物。建议先读PREREGISTRATION→DEVIATIONS D7→RESULTS敏感性→论文表3/4，最后再看标题式结论。这些是工程建议，未将探索性发现提升为训练定律。

## 样本05｜BrickBench: Evaluating Agentic Brick Design

### 1）基本信息、版本与今日差分
Peter Kulits、Yiqing Xu、R. Kenny Jones、Cordelia Schmid、Jiajun Wu；Stanford、MPI-IS、Inria。领域为Agent评测、图形学和程序化设计。[arXiv记录](https://arxiv.org/abs/2610.12452)今天仍仅v1，首发2026-10-08 17:58:56 UTC；没有新论文版本。今天复读§3.2、§4、§5和主表/环境消融，检查官方README及验证脚本；没有声称重新通读全部附录。[原文](https://arxiv.org/html/2610.12452v1)

代码当前唯一提交仍为10月8日的[Initial commit b3df55e](https://github.com/kulits/BrickAgent/commit/b3df55e36c669b22ef089b13db1ee841907d09b3)，未见今天新增代码。项目站本次未能读取，仓库独立可读；不把访问失败解释为项目下线。

### 2）具体解决什么问题
这是“产物能构建、符合要求、设计得好”三个标准如何分别评估的问题。对做生成式产品的人，最重要的是不要因为程序运行成功就给整体品质盖章；也不要让视觉Judge替代执行验收。

### 3）方法与工程数据流
自然语言任务进入编码Agent；Agent通过零件搜索、连接器装配和子结构组合输出build.py与LDraw模型。验证器定位碰撞、错误插接、库存超限或不稳定的零件，反馈给Agent继续修复；另一路把成品多视角渲染，做需求问答与成对设计评审。代码仓库含300题、提示、环境、容器及评分脚本。[README与API](https://github.com/kulits/BrickAgent/blob/master/README.md)

这里最易忽略的是验证边界：当前[verify.py](https://github.com/kulits/BrickAgent/blob/master/scripts/verify.py)会执行提交的build.py；会记录重建模型与提交模型是否一致，但该一致性字段本身不直接决定valid。若将它接入外部提交服务，必须另行设计隔离、资源限额和可信评分进程，不能当安全的纯文本解析器。

### 4）值得保留的亮点
1. 报错能指到具体对象，使局部修复成为可能
2. 硬约束与语义/设计分开，让“漂亮但不能搭”的失败保持可见
3. 需求问题有依赖关系，避免对象不存在仍给属性分

### 5）实验支持与未证明的部分
原表中Astra有效率100%，撤掉BrickAgent后40%；Luna则由100%降到1/300，但无工具时其视觉分反而上升。这个消融支持工具保证可构建性，也证明视觉高分不能充当执行证据。300轮上限并不等于同token或同美元预算；论文每件生成成本Astra 4.06美元、Sol 0.87美元，ELO区间重叠，不能凭4分差判断稳定胜负。有效率采用刚体代理，没有模拟接头强度或零件形变。[§3.2、表1–2](https://arxiv.org/html/2610.12452v1)

这仍没有回答线上用户会否满意、复杂产物是否更易维护、相同工具对别的领域有多少收益。那些都需要单独验证。完整Judge按README约需62GB显存；轻量构建检查也需约1GB碰撞资源，不能把一次API调用价格当全套实验成本。[运行与评测要求](https://github.com/kulits/BrickAgent/blob/master/README.md)

### 6）热度证据
本次首页样本18赞/156浏览；昨天真实Hot榜为第9、6赞/56浏览。今天筛选和缓存年龄未核实，不能由此给出热榜升幅或24小时增长率。可演示的积木作品具有传播吸引力是我的推测，未获得传播因果证据。

### 7）对Agent / RAG / MCP / 全栈的价值
**A档，建议直接读工具与验收协议。** 可把全栈生成分成“类型/接口/构建检查、需求覆盖、交互品质”三张成绩单；RAG则分成“引用真的可达且支持答案、问题覆盖、答案组织”。不要用加权总分把致命的事实或执行错误抵消。

MCP接口可借用对象ID、约束类型、故障定位和修复后验收四要素。最小试验不需要重做排行榜：固定一个模型与预算，抽少量任务比较“普通工具返回”与“对象级可修复反馈”，在独立验收集记真实成功率、回退次数、成本和延迟。以上是工程迁移建议，本文未证明RAG或网页收益。

优先读§3.2→§4.3–4.4→表2；代码先读scripts/prompt.md与scripts/verify.py，理解后再考虑隔离环境内试验。

## 样本06｜NCM: Next-Concept Modeling: Fast, Parallel Coarse-to-Fine Text Generation
**阅读级别：原文未获取，受限解读，不计为已完成的原文深读。**

### 1）基本信息、版本与可用证据
作者由HazyResearch官方模型卡确认：Hermann Kumbong、Ishan S. Khare、Iddah Mlauzi、Andrew Woen、Charles Ding、E. Kelly Buchanan、Simran Arora、Azalia Mirhoseini、Christopher Ré。领域为并行文本生成、离散潜在表示。alphaXiv标2026-10-09提交，但不能当arXiv首发；模型卡citation仍为占位的arXiv号，数字编号与修订史未核实。[alphaXiv](https://www.alphaxiv.org/abs/2610.next-concept-modeling-parallel-generation) · [官方模型卡](https://huggingface.co/datasets/hazyresearch/ncm-release-models)

今日只读作者编辑过的概览与模型卡，没有实际读到论文正文method、实验章节及完整表格。下面只记录能核的公开方案及必须补证据之处。

### 2）具体研究问题
公开方案试图减少并行生成中的反复全序列计算，改变表示与生成顺序：先粗层离散码，再逐层细化。未读原文，不判断其相对全部相关工作的创新优先级。[作者编辑概览](https://www.alphaxiv.org/abs/2610.next-concept-modeling-parallel-generation)

### 3）公开描述的数据流
文本经多尺度residual VQ-VAE转为由粗到细的离散码；冻结tokenizer后，Transformer依据前层累计重建预测下一层，层内位置并行，最后decoder还原文本。这里的concept是学习到的潜在码，不等于可解释知识点。损失、码本训练、条件生成和完整采样细节尚未逐项核验。[方法概览](https://www.alphaxiv.org/abs/2610.next-concept-modeling-parallel-generation)

### 4）创新判断的边界
工程上值得关注的是将串行依赖集中到层之间，并改变每阶段处理的表示规模。但层内并行、码空间建模和由粗到细各贡献多少，必须看消融；不能只凭名字称为人类式概念推理，更不能认定训练和推理总成本都优于自回归。

### 5）实验、baseline、算力与交付缺口
公开概览报告LM1B上NCM/DUO的NFE为12/128、生成困惑度93.05/97.30，单H100、batch16约21倍加速。**这些是尚未对照原文表格的概览数字，不是本报告验证的普遍速度结论。** baseline公平性、训练预算、误差条与消融均未补齐。[公开结果概览](https://www.alphaxiv.org/abs/2610.next-concept-modeling-parallel-generation)

官方模型卡列XSum、WMT14、Sudoku、TinyStories、LM1B的tokenizer/generator checkpoint，OpenWebText为pending。本次没读权重及校验值。卡内[官方仓库链接](https://github.com/HazyResearch/ncm)在公开网页和GitHub接口均返回404，准确说法是当前未能读取公开仓库，不能进一步断言从未发布或将来不会发布。[发布清单](https://huggingface.co/datasets/hazyresearch/ncm-release-models)

### 6）热度证据
首页样本33赞/298浏览。今天筛选未核，不能称第六热门或新入榜。概览标注Hermann Kumbong编辑，增加作者说明的可追溯性，但不能代替正文或独立复现；未获得实质评论内容。

### 7）工程价值与下一步
**C档候选，待原文与可读代码补齐后再升级。** 若在目标任务成立，层级生成可能适合摘要、翻译、批量文案等主要看整段完成时间的负载。应同时测首个可用输出时间、长度/batch敏感性、两阶段训练及decoder开销，不能只看NFE。

Agent还需验证工具参数精确性、停止条件和中途反馈；RAG需验证证据忠实及引用精度；当前材料没有证明这些能力，也未展示MCP集成。现在适合登记研究候选，尚不足以提出生产后端替换建议。这一缺口没有通过概览扩写填平。

## 样本07｜H-JEPA: End-to-End Learning of Hierarchical World Models for Visual Planning

### 1）基本信息、版本与阅读范围
Wancong Zhang、Basile Terver、Michael Rabbat、Yann LeCun、Randall Balestriero；NYU、Advanced Machine Intelligence、INRIA Paris、Brown。前两位共同一作，后两位共同指导。领域是视觉世界模型、机器人与长时程规划。[arXiv记录](https://arxiv.org/abs/2610.06805)首发与最新版均为v1，2026-10-05 17:53:34 UTC；未见会议接收信息。[alphaXiv](https://www.alphaxiv.org/abs/2610.06805) · [项目](https://h-jepa.com/)

今日精读HTML正文方法/主实验、附录B–C/E/G–K与慢特征坍塌论证L.1–L.4，交叉核官方架构、配置、结果文档及权重卡。PDF因大小未成功加载，不声称完成逐页PDF核验；未运行代码。

### 2）具体解决什么问题
单一潜空间同时承担精细控制与远期目标判断，可能把“腿的姿态是否相似”混入“是否靠近目的地”。H-JEPA为不同时间尺度学习不同表示，再用高层状态指导低层子目标。要点是让目标距离更有意义，并缩短每层需要搜索的动作序列。[作者问题说明](https://h-jepa.com/#summary)

### 3）方法与真实数据流
观察—动作轨迹进入一级图像编码器和动作分块；上层接收下层潜状态，跨更长时间间隔的动作被压成宏动作。各层因果预测器根据状态和动作预测后续潜状态，训练目标由预测损失与SIGReg组成，各层联合优化。

规划时编码当前图像与目标图像，从顶层向下优化动作；高层预测成为低层子目标。比较子目标与低层预测时，需把后者送入上层编码器，保证在同一空间衡量，最后执行一级动作。[官方架构文档](https://github.com/kevinghst/H-JEPA/blob/main/h_jepa/ARCHITECTURE.md)

实现入口为main_hjepa.py、eval.py，规划核心为HierarchicalSolver。AntMaze三层上层stride=2、window=1、潜维度384；DROID两层stride=3，另加IDM及宏动作正则，不应混用默认值。[AntMaze配置](https://github.com/kevinghst/H-JEPA/blob/main/h_jepa/config/train/ant_hjepa_l3.yaml) · [DROID配置](https://github.com/kevinghst/H-JEPA/blob/main/h_jepa/config/train/droid_hjepa_l2.yaml)

### 4）值得读的三个亮点
1. 将时间分层和表示分层拆开比较，不让所有预测跨度共享同一目标度量
2. 高层选择性忽略快速变化细节，但操作任务中频率相近时效果没那么明确
3. 展示多场景模型只记稳定背景、遗忘运动主体的失败模式；逆动力学约束帮助保留与动作相关的信息

这些机制证据不能直接扩写为通用因果世界模型。[项目实验说明](https://h-jepa.com/#experimental-results)

### 5）实验、消融、算力与口径差异
官方参考表中，AntMaze的LeWM、三层HWM、三层H-JEPA成功率分别为18.0±3.5%、38.7±3.5%、73.3±3.5%；每环境50个固定任务、三个配对模型/规划种子，误差为标准误。固定一级动力学只换目标距离，16.7%→22.0%，远小于完整分层规划的73.3%。Push-T则从LeWM40.0%、两层H-JEPA45.3%降到三层17.3%，更深不是无条件更好。[官方结果参考表](https://github.com/kevinghst/H-JEPA/blob/main/docs/RESULTS.md)

HWM实现使用恒等上层编码器，并关闭上层SIGReg；它不是只换一个模型名称。[HWM配置](https://github.com/kevinghst/H-JEPA/blob/main/h_jepa/config/train/ant_hwm_l3.yaml)

规划预算计算含前向和反向FLOPs，最终配置先在每回合100TFLOP上限内选择，再于独立任务评估；不同深度训练未匹配FLOPs，不能说总训练成本下降。DROID仅测16段精选视频的离线末端轨迹保真度，没有证明真机闭环成功。[原文§4与附录](https://arxiv.org/html/2610.06805v1#S4)

**今日核查发现的复现口径差异：**官方docs/RESULTS.md自称论文转录、非新验证；部分四层结果与arXiv HTML表不一致，DROID汇总分别出现均值/标准误与种子组合中位数口径。上面选用两侧一致的三层结果；若引用DROID仓库参考值33.57→38.42，必须说明是仓库表、离线指标，不能混成统一实验口径。[结果文档](https://github.com/kevinghst/H-JEPA/blob/main/docs/RESULTS.md) · [论文附录](https://arxiv.org/html/2610.06805v1#A10)

### 6）热度与代码状态
首次首页样本277赞/5k浏览，但今天热榜筛选未核实；不能称新入热榜、增速领先或说明排名原因。公开代码页面另显示99 stars/5 forks，只是快照。

MIT代码含训练、规划、消融脚本；官方权重卡列84个仿真与9个DROID检查点，可确认资源存在。检查点是Python pickle对象，实际使用需核来源、固定版本并隔离加载；本次没有执行或确认复现成功。[仓库](https://github.com/kevinghst/H-JEPA) · [权重卡](https://huggingface.co/jepa-world-models/h-jepa)

### 7）工程价值与建议
**A档深读，B档直接迁移。** Agent可以借鉴不同层状态摘要、不同目标评价尺度与执行后重观察；但文本工具没有现成可微动力学，不能把层级Agent提示词等同H-JEPA。RAG只有多尺度表示的启发，没有检索或问答实验。MCP协议也不会自动提供动作轨迹和潜空间。

全栈近期更实用的是做评测面板，分别记录终局成功、规划FLOPs、层深、轨迹误差和失败类型。若产品本来依赖工具调用，先比较固定预算的一层/两层规划，再检查摘要是否遗漏关键可控变量，而不是先追求更深结构。

阅读顺序建议§3→AntMaze分离消融→Push-T负结果→DROID协议与附录K/L；代码先读ARCHITECTURE.md、HierarchicalSolver及对应任务配置。以上迁移判断是我的工程分析，尚非论文验证的通用Agent提升。

## 样本08｜Long-WAM: Scaling the Context of World-Action Models

### 1）基本信息、版本与今日差分
Wei Huang、Bohan Zhang等，NVIDIA、MIT、HKU、UCSD；机器人长上下文世界—动作模型。首次提交2026-10-07 17:58:04 UTC，今天仍仅v1。复读§3–4、§5.3、§6.1–6.2，核表1–6及README/VERIFICATION。[arXiv记录](https://arxiv.org/abs/2610.10528)

Long-WAM路径最新提交仍[4ce82ab](https://github.com/NVlabs/LongLive/commit/4ce82abbd648124530c958915d5e420cc873090d)，10月8日02:08:44 UTC，补论文链接与citation；与昨日报相同，无今日代码更新证据。

### 2）具体解决什么问题
更长视觉历史能帮助推断运动与进度，也可能推迟动作。本文研究如何真正利用历史并赶上动作交接截止时间；对象是机器人自己的连续观察，不是检索任意旧经验的记忆系统。[项目说明](https://nvlabs.github.io/LongLive/Long-WAM/)

### 3）方法与真实数据流
先用无动作标签机器人视频做AR预训练，再保留因果结构接动作专家。IDM先预测部分去噪的未来latent，动作专家结合历史和未来生成动作；未来不解码成像素。流式VAE、异步执行、NVFP4视频计算及设备kernel优化共同减少等待；过期动作前缀丢弃，KV不保证跨决策永久有效。[方法与系统](https://nvlabs.github.io/LongLive/Long-WAM/)

不同历史长度须配对应checkpoint/config；expected_history是规格检查，不会自动扩展记忆。视频低精度，动作与KV仍保留BF16。[官方README](https://github.com/NVlabs/LongLive/blob/main/Long-WAM/README.md)

### 4）值得保留的亮点
我的工程判断：
1. 记忆收益与观察过期风险要一起评估
2. 模型、缓存、异步调度和设备执行需要协同验收
3. 高层计划与固定低层执行器分开，有利于定位失败

这些启发不意味着所有Agent都应增加昂贵的视觉预测层。

### 5）实验支持与限制
GR-1的19.2秒历史成功率78.7%，各窗口分别训练，不能理解为同一模型随时扩窗。真机动态叠杯19/20、对照各0/20，仍是小样本。RTX5090优化设置107.4ms/93.5%，BF16为356.0ms/94.4%；19.2秒历史需341.0ms，不能把最长上下文、最低延迟、最高成功率拼成一种规格。[§5–6及表6](https://arxiv.org/html/2610.10528v1#S5)

表4将2.4秒写为63.3%，§5.3为66.3%，今日仍见冲突，不声称已修正。选型应固定权重、历史、去噪预算和硬件；稳态模型延迟也不能代替含排队、传输与控制器的端到端P95。本文没有独立软件Agent/RAG复现。

### 6）热度与发布状态
首页样本100赞/1k浏览；昨日Hot第4、85赞/1135浏览。由于今日1k是舍入值，连精确浏览差都不能算；筛选未核，不报今日名次。未取得新增讨论或独立复現证据。

README仍明确完整基准复现未验证，虽已有权重清单及训练/评估/部署入口。[VERIFICATION](https://github.com/NVlabs/LongLive/blob/main/Long-WAM/docs/VERIFICATION.md)列出CPU/mock/dry-run检查和旧有限GPU smoke：两步GR1训练及少量短闭环。LIBERO/RoboTwin全链路、全任务评估与目标设备验证仍有缺口；既不能称从没跑过GPU，也不能说已独立复现论文成绩。

### 7）工程价值
**B档，优先迁移时序契约而非整套WAM。** 软件Agent/MCP可借鉴带时间戳观察、过期动作拒绝、版本化缓存与可恢复执行器。工具响应除结果，还可给观察时间、状态版本和有效期；高层计划改变后旧结果能否继续使用必须有规则。

若要复现机器人部分，先选一个任务及硬件，固定2.4秒或19.2秒的匹配权重，跑通最小模拟闭环后再测异步交接与完整成功率。对普通工具Agent，增加WAM的收益没有被证明。阅读顺序§3–4→表6→README规格约束→VERIFICATION，避免只看“更长、更快”的标题。

## 样本09｜A Balanced Data Diet: Addressing the Exploration Bottleneck in Mega-Scale RL for Robot Control

### 1）基本信息、版本与今日差分
Octi Zhang、Mateo Guaman Castro、Patrick Yin、Ignacio Dagnino、Abhishek Gupta、Rosario Scalise、Byron Boots；UW与NVIDIA。机器人强化学习、课程/配置采样，CoRL 2026。[arXiv](https://arxiv.org/abs/2610.12465)仍仅v1，首发2026-10-08 17:59:50 UTC；今日复读§3、§4.3–4.5、附录B.3/B.4和C.3–C.5，没有新论文修订。官方页面仍明确标记 **Code (coming soon)**，不把演示站当已发布训练代码。[原文](https://arxiv.org/html/2610.12465v1) · [官网](https://sgs-rl.github.io/)

### 2）具体解决什么问题
增加并行训练量不保证增加有用反馈。若大多数任务已经会做或完全无从下手，多出来的轨迹可能只扩大浪费。SGS把采样集中于当前有机会学会的任务配置，研究的是可重置训练分布里的资源分配。

### 3）方法与真实数据流
先固定初始状态、目标和环境组成的配置库；每次episode结束，把成功与否写入该配置的滚动历史。由成功率计算平滑权重，对接近目标难度的配置加权，并保留非零抽样概率；下一次reset据此选配置。动作学习仍用PPO，采样器本身不生成动作或新任务。操作库包含接近目标、稳定抓握与普通接近等重置。[官网方法流程](https://sgs-rl.github.io/)

实机另有模拟教师→RGB学生的蒸馏过程，训练和部署观测并不一样。将“采样简单”理解成“整套系统没有先验或工程”会误判：可用重置、成功定义、几何与sim-to-real设置都是有效反馈的前提。[附录C](https://arxiv.org/html/2610.12465v1)

### 4）最值得保留的亮点
1. 可把计算扩展失效定位到采样分布，而非一开始就修改网络
2. 极易与现有训练系统做对照，机制比全新策略模型更可分离
3. 对在线学习保留不进入梯度的验收环境，防止边教边考造成伪进步

### 5）实验支持、成本与边界
官网主表在百万环境给出运动成功率SGS73%、PLR54%；Franka装配70%、均匀6%、PLR5%，均为三个训练种子。跨规模同时增加了经验量，不是固定总算力胜出。[官网结果表](https://sgs-rl.github.io/)

原文去掉Near-Goal重置后插杆学习失败，说明加权不能补救缺少可学路径的配置库。主训练耗时约36小时/128小时；在线DAgger保留6.67%环境独立评估。RGB螺母任务模拟89.05%、实机37.5%，不能用模拟数字替代部署可靠性；无重力课程补实验仅一个训练种子。以上均为作者报告、此次未复现。[§4、表2、附录B/C](https://arxiv.org/html/2610.12465v1)

我更看重的反证问题是：预算固定时，SGS是否仍胜过简单分层采样？稀有但重要任务会否被系统性低估？采样器是否只是追逐噪声最大的配置？这些不能由当前几个成功率数字直接回答。代码未公开也使精确复现仍有交付缺口。

### 6）热度证据
首页样本29赞/215浏览；昨日报真实Hot榜第10、14赞/132浏览。今天不能做同口径排名或正式24小时增量比较；也未读到足以解释关注来源的讨论。“小改动支撑大规模训练”可能令人关注，属于内容分析而非传播事实。

### 7）对Agent / RAG / MCP / 全栈的价值
**B档，适合借鉴离线评测/训练资源分配，不宜据此承诺机器人全量复现。** 可把Agent失败库按任务类型、工具链长度和可恢复错误分层，让开发阶段多练有改善空间的组合；静态正式验收集保持原分布，始终单列稀有高风险任务。

RAG可试证据缺失率、干扰文档比例、跨文档跳数，但不要把“中等成功率”直接当学习价值：若题目本来含糊或标签错，反复练只会过拟合噪声。生产请求更不能因为困难就降低服务优先级。本节迁移都是待测假设。

先读§3.2、附录B.3和C.3/C.5，重点理解重置覆盖及验收隔离。若只想吸收工程思想，先用固定离线任务库比较均匀/分层/成功率加权三组，等预算下测未触碰的测试集，比复制百万并行环境更合理。

## 样本10｜AgentGarten: Code Worlds for Evolving Agents

### 1）基本信息、版本与今日差分
Jiawei Chi、Shangchen Miao等，MirroS、清华、北大；可编程环境、神经渲染、经验学习。首次提交2026-10-08 17:32:00 UTC，今天仍仅v1。复读§2、§3.4、§4.2–4.3、§5/§7和表1–4。[arXiv记录](https://arxiv.org/abs/2610.12374)

今日官方README仍缺完整交互世界与Agent练习loop。仓库metadata此前访问受限，本次未重取，commit级差分未知；不能声称整个仓库没变。

### 2）具体解决什么问题
代码引擎维护稳定状态、碰撞和规则，但扩展画面成本高；生成视频外观丰富，却难作为权威状态。AgentGarten分工为引擎管状态、renderer管观察。[作者博客](https://mirros.ai/blog/worlds-for-evolving-agents)

### 3）方法与真实数据流
动作推动代码世界，引擎输出深度/法线；renderer结合几何、参考图、文本与历史生成RGB。画面不直接写回物理状态，但错误观察仍会影响下一动作。[项目接口](https://mirros-lab.github.io/agent-garten/)

renderer从Cosmos3-Nano适配，依次做几何条件训练、因果适配和Adversarial Forcing；后者组合DMD、exact replay、真实视频对抗监督。两遍重放让后续损失更新历史编码，但记录latent仍detach，并非完整采样轨迹BPTT；相同mask还不够，attention kernel、调用形状和KV次序也需一致。[原文方法](https://arxiv.org/html/2610.12374v1#S3)

Agent用每轮结束后的playbook把经验传给新会话；世界仍逐个制作，经验量尚小、可以全量读，跨世界经验检索仍待解。[作者说明](https://mirros.ai/blog/worlds-for-evolving-agents)

### 4）值得保留的亮点
我的工程判断：状态与外观解耦能固定事件、改变观察，区分感知与决策失败。比“生成漂亮世界”更有用的是可回放、可评分、能保留失败证据的练习环境。

exact replay也提醒：数学等价的缓存或batch重写在有限精度下可能不等价，数值对照应先于性能宣称。

### 5）实验、成本与局限
表1单H100/BF16中，整序列replay相对误差3.99%，逐块SDPA为0；计时仅三次预热后前向，不含反传。表2每16帧块438.8ms/36.5fps，不是每帧27ms独立反馈。表4四世界每轮仅一个episode，装载机30→0→30→90.9，没有单调改善或方差证据。[表1–4](https://arxiv.org/html/2610.12374v1#S4)

作者把第4轮搭庇护所、第10轮用斜坡与旧RL数千万episode对比；预训练、观察、动作及规则不同，不能算样本效率倍数。[作者实验说明](https://mirros.ai/blog/worlds-for-evolving-agents)

仍需无playbook、记忆预算及未见世界对照，才能隔离经验循环的效果。画面质量与状态可观测性也应分别验收，稳定引擎不能自动保证画面中的身份、颜色、旋转正确。

### 6）热度与发布缺口
首页样本42赞/477浏览；昨日Hot第5、28赞/366浏览。今日筛选未核，不报升降；实时画面、可写世界及经验积累可能吸引关注，是推断，无新社区共识证据。

[官方README清单](https://github.com/MirroS-Lab/AgentGarten/blob/main/README.md#todo)仍勾选renderer训练、流式推理及checkpoint，未勾实时server/交互前端、code worlds及Agent practice loop。需要Python3.11+、PyTorch2.9+、CUDA和基础模型/VAE；renderer已发布不等于完整Agent平台可直接复现。

### 7）工程价值
**B档，先读环境权威状态设计；完整平台复现暂缓。** 软件Agent可以先复制“权威状态服务＋有限观察/动作接口＋独立评分器＋可回放日志”。MCP只向Agent暴露任务允许的信息，oracle留给评估层，避免调试真值泄漏。

playbook应记录证据、适用条件、失败反例和下次检验。经验变大后可以加RAG，但须与全量读取和无记忆做同预算对比。纯软件任务先做可重放环境更便宜，视觉确为瓶颈时再承担神经renderer成本。本节是工程推断，论文没验证通用MCP/RAG收益。建议读§2接口→§3.4 replay→表4与§7→README缺项。

## A．今天最值得额外深读的三篇

以下优先级面向Agent / RAG / MCP / 全栈工程阅读，兼顾相对昨天的新增信息；不是论文质量排名或热榜排名。A为建议深读，B为有条件借鉴，C为证据待补；“值得读”与“值得立即复现”分开判断。

### 1. BrickBench：先把工具验收做对
- 为什么：最直接回答“Agent看起来完成”和“产物真能使用”之间的差距；尤其适合已有生成式产品的人
- 读哪里：§3.2物理有效性→§4.3–4.4工具与指标→表2工具消融→§5.3人类Judge校准
- 看什么代码：[scripts/verify.py](https://github.com/kulits/BrickAgent/blob/master/scripts/verify.py)、[API与运行说明](https://github.com/kulits/BrickAgent/blob/master/README.md)。注意执行提交代码与模型一致性字段的验收含义
- 可做什么：不必搭整套渲染集，先给一条现有工具链加入对象级失败定位与独立终态验收，测修复效率和真实完成率

### 2. H-JEPA：分层状态与分层目标应该怎样对照
- 为什么：提供比“多层Agent会更好”更具体的表示、规划和失败分析；Push-T深层退化尤其值得读
- 读哪里：§3→AntMaze目标距离/完整规划分离→Push-T负结果→DROID评估协议、附录K/L
- 看什么代码：[架构](https://github.com/kevinghst/H-JEPA/blob/main/h_jepa/ARCHITECTURE.md)、[AntMaze三层配置](https://github.com/kevinghst/H-JEPA/blob/main/h_jepa/config/train/ant_hjepa_l3.yaml)、[结果口径](https://github.com/kevinghst/H-JEPA/blob/main/docs/RESULTS.md)
- 可做什么：先定义每层状态保留/丢弃什么，锁住预算做一层/两层比较；别把离线轨迹保真度当真实闭环成功

### 3. Data Wall / CALREP：分数变化到底意味着什么
- 为什么：提供了可追踪到预注册、偏离、代码、结果分片的测量案例；有用之处包括暴露自身核验失败
- 读哪里：[PREREGISTRATION](https://github.com/SeverinVisionary/calrep/blob/main/PREREGISTRATION.md)→[DEVIATIONS D7](https://github.com/SeverinVisionary/calrep/blob/main/DEVIATIONS.md)→[敏感性结果](https://github.com/SeverinVisionary/calrep/blob/main/RESULTS.md)→[论文表3/4](https://github.com/SeverinVisionary/calrep/blob/main/paper/calrep_note.tex)
- 看什么代码：[calrep_eval.py](https://github.com/SeverinVisionary/calrep/blob/main/code/calrep_eval.py)，重点是同一logits评不同温度、cross-fitting和评估器一致性
- 可做什么：将任务成功率、校准质量和NLL分开汇报；正式验收失败后，事后改标准必须留下记录

MASS和MiMo仍值得读，但今天所查版本与交付缺口没有实质改善，已读昨日报的人优先看本次代码状态差分即可。NCM暂列C档，原文与可读仓库未补齐，不应因“21倍”概览数字投入迁移工程。

## B．从这批样本看到的五条技术线索

这些是基于样本的综合判断，不是对当天全站或整个研究领域的统计结论。

1. **可修复接口比角色堆叠更接近工程能力。** ETM把错误落到状态和分支，BrickAgent把错误落到零件与约束，MASS把交付契约纳入工作流。可借鉴的是让系统知道哪里坏、修完怎样证明，而不是只增加模型调用数
2. **记忆要有时间尺度和失效规则。** Long-WAM提醒观察会过期，H-JEPA提醒不同层目标不该共用同一细节度量。对工具Agent，状态时间戳、有效期、重观察条件应进入接口，而非只扩上下文窗口
3. **评测工程正在决定“改进”究竟是什么。** MiMo的泄漏审计、MASS的交付率/分数和不同数据集口径、Data Wall的校准与评估器核验，分别暴露评分可被信息、完成率或概率尺度影响。一个单分数很难支持总体能力叙事
4. **有效反馈的覆盖比裸训练规模更重要。** SGS在配置库内选择可学区域，但无法凭空补齐通路；AgentGarten也尚未证明经验在未见世界稳定迁移。工程上应先保证任务覆盖、可验证反馈与独立验收，再扩样本或模拟规模
5. **粗到细生成值得跟踪，发布证据不能缺席。** H-JEPA已有可读配置和负结果，NCM仍缺本次可读原文/仓库；二者都涉及分层，但不能因为共享词汇就合并成同一成熟度或同一种能力。研究候选进入产品前，要补全源文、预算、延迟定义和目标任务评估

## C．与昨天真实报告的对比

### 可以确认与不能确认的事

已完整读取昨天交付的《alphaXiv热门Top10深读｜2026-10-11》（alphaxiv_2026-10-11.md），其快照为2026-10-11 03:21:16 UTC，已核Hot / Publication 30 Days / All。今天约03:13取得的是筛选状态未核的首页展示样本。两份名单可以比较覆盖，不能比较热榜升降，也不能称“7篇留榜、3篇新入榜”。

- **重复覆盖7篇**：ETM、MASS、MiMo、BrickBench、Long-WAM、Balanced Data Diet、AgentGarten
- **今天报告新覆盖3项**：Data Wall、NCM、H-JEPA；它们的发布时间不同，不是今天统一首发
- **昨天另外3篇**：Can Jev be Your Q or Policy、RoboRSI、Prior or Feedback? 今天仍出现在首次首页响应的较后位置，只未进入本次前10展示样本，不能称跌出真实Hot前十
- 今天七篇连续arXiv论文的历史仍仅v1；没有复做PDF字节比较，因此不复用昨日“哈希一致”的强度
- 今天原文级研究覆盖9篇，NCM为作者概览/模型卡受限解读。深读方法不等于独立复现

### 连续论文今天真正多知道了什么

| 论文 | 昨日已核Hot名次 | 今日可核差分 | 不应做的推断 |
|---|---:|---|---|
| ETM | 1 | arXiv仍v1；官方项目本次不可读，完整源码状态未知 | 不能沿用昨日缺源码当今日确证 |
| MiMo | 2 | 两个mimo-oss HEAD与昨日一致，环境清理约束仍需审计 | 不能推断容器镜像一定未重建 |
| MASS | 3 | 当前main固定到10月9日README/清单提交；107题复现覆盖仍有缺项 | 昨日未固定SHA，不能称完成逐文件昨日diff |
| Long-WAM | 4 | 路径最新提交与昨日一致；完整benchmark未验证说明仍在 | 不能将CPU/mock及有限GPU smoke当论文复现 |
| AgentGarten | 5 | README仍缺实时交互与世界/练习loop | metadata未核，不能断言全仓库无变化 |
| BrickBench | 9 | 唯一提交仍10月8日；验证器执行build.py，模型一致性仅被记录 | 不能把valid=100%当真实积木结构强度保证 |
| Balanced Data Diet | 10 | arXiv仍v1；官方仍标Code coming soon | 演示视频不是可运行训练发布 |

### 阅读优先级如何改变

对昨天已经读过的内容，今天没有必要把所有背景再当新发现。更值得增加的阅读量是H-JEPA的层级反例、Data Wall的预注册偏离；连续论文主要补代码/复现口径。NCM暂保留待核，不能用其概览替代原文。

这次日报的主要欠项仍是**指定热门筛选的实际榜单核验**，以及NCM原文/代码的可读性。因此它是一份有明确证据边界的当天研究样本报告，不是已完整完成的“今日热门Top10深读”。后续若获得可靠排序或原文，应以新快照和新证据注明补充，不反写本次未核实内容。

## 核验结束说明

正文所有实验数字均为所引论文或作者公开材料的报告，除明确说明的对比判断外，没有独立运行证明。所有Agent/RAG/MCP/全栈迁移均为工程分析，需要用自己的任务、预算和固定验收集验证。没有读取到的评论、未发布/不可读资源、统计口径冲突和访问限制均保留为未知。

研究与发布信息核查完成于2026-10-12约03:23 UTC（北京时间11:23）；榜单样本仍冻结在首次约03:13响应，不随阅读期间变化重排。

