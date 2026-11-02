# AI论文日报｜2026-11-02

## 今日结论与来源口径

**九篇连续、一篇新入。** 新入FlatCake把LLM的KV复用问题推进到SSD布局与传输调度；Spatial State官方README新增可复现覆盖说明，需收紧“已开源即能完整复现”的判断。其余连续论文优先核对版本／代码／公开讨论增量，不重复昨日长篇介绍。

- 抓取：北京时间**2026-11-02 11:21:54–11:22:39**，原始UTC **03:21:54–03:22:39**。云端浏览器实际访问[alphaXiv Trending／Hot](https://www.alphaxiv.org/?sort=Hot&interval=7+Days)，页面显示**7 days**，无额外学科筛选；不是默认最新流或搜索缓存。
- 使用昨日实际核验的Hot入口，今天重新打开并滚动读取。Cloudflare初始自动验证后正常显示；可关闭的注册提示已关闭，无登录或新注册。页面初始仅加载五项，滚动后读取到第11项；只取前十，Researchers推荐卡不计榜位。
- 排序算法及赞／浏览的累积窗口未另行公开核实。下表为页面原始显示；`8k/1k/2k`保留取整形式，不伪造精确值或24小时浏览增量。排名变化仅相对昨日同口径快照，不等于全网热度变化。
- 已读取[昨日固定归档报告](https://github.com/DanielMax937/daily-research-reports/blob/eb2fa6204f3d601290e33b661d0b8d4e08c563e7/2026-11-01/ai-papers.md)。连续论文按要求压缩为七项增量记录，昨日已读方法不冒充今日重新全审；新入论文完整展开。所有实验数字是论文报告，未独立复现；代码仅只读。

|今日|论文／alphaXiv原页|昨日|赞|浏览原样|
|---:|---|---:|---:|---:|
|1|[Proving and Improving the Platonic Representation Hypothesis with JEPAs](https://www.alphaxiv.org/abs/2610.39302)|1|164|8k|
|2|[Training Foundation Models with a Single Algorithm](https://www.alphaxiv.org/abs/2610.40564)|2|104|1k|
|3|[Probing Spatial State Representations in Visual Foundation Models](https://www.alphaxiv.org/abs/2610.40636)|3|35|374|
|4|[Training language models in simulation for psychiatric intake](https://www.alphaxiv.org/abs/2610.40476)|4|51|2k|
|5|[Read, Allocate, Route: Role-Coupled Tokenization for Pixel-Space Generative Transformers](https://www.alphaxiv.org/abs/2610.40647)|6|22|179|
|6|[How to Loop Your Transformer: Loop Scaling, Specialization, and Parallel Inference](https://www.alphaxiv.org/abs/2610.40325)|7|34|328|
|7|[Robotic Data Inoculation](https://www.alphaxiv.org/abs/2610.39054)|8|19|177|
|8|[Cross-Controller Transfer via In-Context Behavior Adaptation](https://www.alphaxiv.org/abs/2610.39280)|5|30|261|
|9|[FlatCake: A Flat KVCache Storage Architecture for LLM Serving](https://www.alphaxiv.org/abs/2610.38355)|前十未见|20|992|
|10|[L3G-World: Real-Time Infinite World Generation with Latent 3D Gaussian Memory](https://www.alphaxiv.org/abs/2610.40614)|9|24|242|

## 逐篇核验

## 1. Proving and Improving the Platonic Representation Hypothesis with JEPAs

1. **必要标识／版本：** Randall Balestriero、Yann LeCun；领域：Representation Learning／Multimodal；[arXiv 2610.39302](https://arxiv.org/abs/2610.39302)今日仍只列v1，提交时间2026-10-29 03:49:53 UTC／北京时间10月29日11:49:53，无v2。
2. **问题／方法：** 仍是用“同一场景多观测”的正样本改善独立编码器对齐；今日不重复昨日方法介绍。
3. **代码增量：** main仍为[a2b9949fa907d4fbe562742d4b1ffa7205ab7427](https://github.com/galilai-group/prh-proof/commit/a2b9949fa907d4fbe562742d4b1ffa7205ab7427)，与昨日完全相同；不存在可称作今日新增的代码diff。
4. **新增讨论：** 2026-11-01 22:54:34 UTC／北京时间11月2日06:54:34新建[Issue #1：Verify evals on Papers with Code](https://github.com/galilai-group/prh-proof/issues/1)，发帖者称已收录三项论文原生评价，请作者核对分数、协议和开放信息；检查时为open、0条评论。这是**结果收录／核验请求，不是第三方复现实验，也不是作者确认**。
5. **实验结论：** 本次未发现新增实验或修订表格。昨日的关键限制仍保留：42×是样本数而非算力比，理想化旋转定理不能直接覆盖现实有损观测；不因收录请求上调证据等级。[未变的v1原文](https://arxiv.org/html/2610.39302v1)。
6. **热度变化：** 11月2日已核alphaXiv 7日Hot：**#1不变，164赞、8k浏览**；昨日60赞／773浏览，即赞+104。8k是界面缩写，不换算精确浏览增量；不能据此断言具体传播原因。
7. **工程判断：** 暂无需要迁移的代码或重跑理由。若参考外部榜单，仍应回到固定版本及对应评价协议；新增issue尚未解决，不能代替实验验收。

## 2. Training Foundation Models with a Single Algorithm｜连续，排名不变

1. **身份／版本。** Yuda Song、Alvin Zhang等10位作者；Training／RL／AI Systems。[arXiv版本历史](https://arxiv.org/abs/2610.40564)今日仍仅v1：2026-10-29 17:42:05 UTC／北京时间10月30日01:42:05。原始完整方法评审见[昨日固定报告](https://github.com/DanielMax937/daily-research-reports/blob/eb2fa6204f3d601290e33b661d0b8d4e08c563e7/2026-11-01/ai-papers.md)。
2. **问题定位不变。** 用统一似然目标连接静态文本、示范与奖励加权生成，把阶段划分变成数据调度问题；不是所有RL目标与有限样本实现都完全等价。
3. **方法／代码变化。** 今日核[官方提交列表](https://github.com/yudasong/unified-training/commits/main/)最新仍`5b3eaa0f3ce39f695beb5d27a0bb0f92368b3118`（10月30日05:09:51 UTC／13:09:51北京），与昨日一致；没有新实现diff。继续保留“静态与在线样本→共享buffer→加权token似然→异步权重发布”的理解，不重复宣称再次全量审代码。
4. **亮点判断不变。** 值得研究的是训练器／样本权重／数据新鲜度的分离，而不是仅凭统一接口宣称算法必胜。
5. **实验增量：无确认变化。** 今日重核[附录D.6](https://arxiv.org/html/2610.40564v1)：抽查生成轮次滞后12–44次更新，仍未记录实际消费样本年龄分布；4步发布间隔并不是4步滞后上限。旧的吞吐／GPU预算差异继续存在，不能因上榜就提高结论确信度。未独立复现。
6. **热度／讨论。** 连续两次已核7日Hot第2；今日104赞、浏览原样显示`1k`，昨天57／652。可确认页面累计快照变化，不能把四舍五入浏览数换算精确增幅，也不能当成算法验证。今日GitHub公开issues读取返回空列表，仅说明该次查询无条目，不等于全网无人讨论。未获得新的独立传播因果证据。[alphaXiv](https://www.alphaxiv.org/abs/2610.40564)
7. **工程行动。** 保持“读`hf_trainer.py`与数据新鲜度记账，不立即迁移生产训练栈”的判断。后续触发点是消费年龄日志、原始语料发布、同算力对照或新commit，而非总赞数。今日覆盖：版本记录、官方commits/issues、原文D.6；既有方法／代码认识来自昨日实际深读。

## 3. Probing Spatial State Representations in Visual Foundation Models

1. **必要标识／版本：** Baiqiao Yin等；领域：Evaluation／视觉空间状态；[arXiv 2610.40636](https://arxiv.org/abs/2610.40636)仍为v1，2026-10-29 17:58:16 UTC／北京时间10月30日01:58:16；论文没有新版本。
2. **问题／方法：** 冻结特征的四层空间诊断不变；今日重点转到**论文与公开代码到底覆盖到哪里**，不把文档改动称为方法升级。
3. **真实增量：** main从昨日`33e603ca612159d45e24fa783ea767d64f1755b9`变为[a0a94043271a7ba19b03970ca8ca0ed885fec57a](https://github.com/yyyybq/Probing_Spatial_State_Release/commit/a0a94043271a7ba19b03970ca8ca0ed885fec57a)，提交于2026-11-01 18:48:57 UTC（北京时间11月2日02:48:57）。只改README，**+120/-29行，1个commit**；训练代码和结果CSV没有变化。[固定compare](https://github.com/yyyybq/Probing_Spatial_State_Release/compare/33e603ca612159d45e24fa783ea767d64f1755b9...a0a94043271a7ba19b03970ca8ca0ed885fec57a)。
4. **新增披露：** 新增“Paper and code”对照，明确仓库只覆盖**L1–L3，L4不在其中**。作者称主表70格中62格能由现有CSV按四个prefix均值重建并与印刷精度一致；未发布的8格是CogVideoX layer20整行7格及Wan view consistency。此处是作者披露，**本次没有执行代码重算62格**。[新README固定段落](https://github.com/yyyybq/Probing_Spatial_State_Release/blob/a0a94043271a7ba19b03970ca8ca0ed885fec57a/README.md#paper-and-code)。
5. **实验／复现边界：** README还首次集中列明未发布的代码及输出：匹配输入／历史控制、原生预测特征readout、两种L4动作实验、跨层级比较、运动组合、171共同窗口比较、scene-bootstrap区间和图。layer sweep另缺MiniMax-H3 layer10的C1/C2。**没有新增实验结果，也不能把“有开源仓库”写成“全部关键结论可公开复现”。**[完整新增diff](https://github.com/yyyybq/Probing_Spatial_State_Release/commit/a0a94043271a7ba19b03970ca8ca0ed885fec57a)。
6. **热度变化：** 今日已核：**#3不变，35赞／374浏览**；昨日20／229，分别+15／+145。这是关注度增长，不是上述缺失材料已经补齐的证据。
7. **工程判断：** 新文档提高了复现边界的透明度，但没有提高公开实验覆盖率。若项目仅需L1–L3探针可沿原计划评估；若依赖“目标有用性”、历史控制或显著性区间，应把对应材料未公开列为验收前置项，而非直接宣布复现完成。本次按三个仓库的`updated:>=2026-11-01`检索，未发现该仓库新增／更新issue记录。

## 4. Training language models in simulation for psychiatric intake｜连续，排名不变

1. **身份／版本。** Samuel Schmidgall、Tim Strother、Alex Bijamov等56位；Agent／RL／Evaluation／Safety。[arXiv](https://arxiv.org/abs/2610.40476)仍仅v1：2026-10-29 17:10:32 UTC／北京时间10月30日01:10:32；没有确认修订版。[alphaXiv](https://www.alphaxiv.org/abs/2610.40476)
2. **问题定位。** 检查模型能否主动问出未披露信息，而不只是回答已给出的医学问题；不是临床产品安全认证。
3. **方法变化：未确认。** 昨日读到的“隐藏患者状态→多轮工具访谈→临床rubric／安全惩罚→GRPO→独立医师角色扮演评估”仍为v1方案。本轮不把旧实验重新包装成新增成果。
4. **亮点保留。** 过程遗漏评估和模拟—人工交叉核验对通用Agent测试有启发；把方法移植到客服／需求澄清的收益仍需独立验证。
5. **今日重点复核。** [原文§2.2及补表7](https://arxiv.org/html/2610.40476v1#S2.SS2)仍区分：60.6%是至少漏问一个必要主题的完整性指标，不等于急性安全错误率；12.9%是特定对抗场景中的急性风险分流不足。不能把二者混为一个安全分数，也不能用自动评分提升推出真实患者疗效。无新实验或独立复现证据。
6. **热度。** 今日第4，51赞、浏览显示`2k`；昨天第4、33／903。只确认该平台快照关注增加，传播原因仍缺直接证据；未获得足够可读的新作者／专家讨论，不凑观点。
7. **可用性与行动。** 今日实际重读[Code/Data Availability](https://arxiv.org/html/2610.40476v1)：代码仍明确暂不开放，127例评测资料仍是探索分享，并非已提供完整可下载环境。保留“离线评测设计可读、无人监督医疗部署不可据此推进”的判断。今日覆盖版本页、§2.2、补表7、数据代码声明；未重新精读全部76页，未执行任何医疗实验。

## 5. Read, Allocate, Route: Role-Coupled Tokenization for Pixel-Space Generative Transformers（SpecSlot）

1. **必要标识／版本：** Jiongfan Yang等；领域：Diffusion／像素生成／高效Transformer；[arXiv 2610.40647](https://arxiv.org/abs/2610.40647)仍为v1，2026-10-29 17:59:21 UTC／北京时间10月30日01:59:21；状态仍写under review at ICLR 2027，不是已录用。
2. **问题／方法：** 最低频carrier负责全局通信、其他频带局部处理的设计不变；不重复完整架构。
3. **代码增量：** main仍为[883d7ca061b34493fece8ddfe588b29c10c2f7a5](https://github.com/JiongfanYang/SpecSlot/commit/883d7ca061b34493fece8ddfe588b29c10c2f7a5)，与昨日相同；没有新的实现／实验diff可读。
4. **讨论检查：** 公开GitHub issue／PR检索条件为`repo:JiongfanYang/SpecSlot updated:>=2026-11-01`，本次返回空。不等于全网无讨论，只能说本次所查仓库近期讨论无新增记录。
5. **实验判断：** 未发现新实验或分数修订，昨日结论不变：ImageNet-256相对JiT-CM差异不足以称显著胜出，文生图DPG领先但GenEval落后；整体仍是质量—成本折中，不升级为全面SOTA。[未变v1原文](https://arxiv.org/html/2610.40647v1)。
6. **热度变化：** 今日已核：**#5（昨日#6，上升1位），22赞／179浏览**；昨日13／106，分别+9／+73。排名升高不能包装成新的技术突破。
7. **工程判断：** 没有新补丁需要应用，也未新增可验证的部署成本证据。沿用昨日“在目标硬件、batch、CFG和采样步数下单独复测”的建议即可。

## 6. How to Loop Your Transformer: Loop Scaling, Specialization, and Parallel Inference（连续上榜）

1. **身份、版本与排名。** Chanakya Ekbote、Artidoro Pagnoni、Devendra Singh Sachan、Shruti Bhosale、Mike Lewis、Maryam Fazel-Zarandi、Shashank Rajput、Sujan Kumar Gonugondla；领域：LLM架构／Training／Inference。今日第6、昨日第7；统一榜单快照34赞、328浏览。今天重读[arXiv版本历史](https://arxiv.org/abs/2610.40325)：仍仅v1，2026-10-29 15:56:09 UTC／北京时间10月29日23:56:09。没有已核新版本，不把上升一位称作能力突破。[alphaXiv原页](https://www.alphaxiv.org/abs/2610.40325)
2. **问题不变。** 研究重复使用权重如何在参数、训练FLOPs及解码依赖之间取舍；不是给现成聊天模型直接加循环即可无代价增强。完整背景已在昨日报告说明。
3. **方法增量。** 无确认新增。昨日已读的核心是循环位置、少量轮次专属低秩参数，以及把前token状态与当前embedding分别归一化再混合的并行接口。今天重点回读[附录G](https://arxiv.org/html/2610.40325v1#A7)，确认未把依赖重排等同于减少计算。
4. **亮点判断是否改变。** 不改变：价值在于把参数节省、训练成本和推理调度分开控制与比较，而非宣称循环通吃。标题中的“Parallel Inference”仍是可并行计算图的论证。
5. **实验／限制增量。** 无新实验。附录G明确没有测wall-clock解码延迟或吞吐，训练仍执行全部循环；所以昨日“等待真实端到端推理测量”的条件未满足。该节质量多用teacher-forced BPB，不是开放生成成功率；本轮只核查版本及关键限制，不重读149页全部重复曲线，不宣称独立复现。[原文附录G](https://arxiv.org/html/2610.40325v1#A7)
6. **热度与讨论。** 平台名次7→6是可确认的关注度位置变化，不是全网热度因果证据。论文正文的链接检查及标题检索仍未定位作者明确发布的本作实现；未把PLT前作仓库或自动生成解读当本作代码／独立研究人员认可。没有足够公开证据解释今日传播原因。
7. **工程动作。** 维持观察，基础模型团队可沿附录G做实现规划；应用团队暂无需改API或Agent架构。下一有意义信号是作者代码、同硬件/同质量/同cache条件的prefill与decode实测，不是继续重复参数或BPB宣传。今天实际读取：版本页、原文附录G开头及G.1控制解释、全文代码链接位置；不运行代码。

## 7. Robotic Data Inoculation（昨日#8）

1. **身份／版本。** Qiyang Li、Zhiyuan Zhou、Charles Xu、Sergey Levine，UC Berkeley；机器人数据采集、共享控制、离线RL。今日版本记录仍仅v1：2026-10-28 23:31:24 UTC（北京10月29日07:31）。[版本页](https://arxiv.org/abs/2610.39054)

2. **问题。** 干净遥操作示范缺少策略犯错后的恢复状态；研究的是如何改造真实数据采集，而不是新造一个更大的自主策略。[原文§1–4](https://arxiv.org/html/2610.39054v1)

3. **方法。** 人类指令+在线RL有界残差→真实执行→人持续纠正→训练BC/离线RL；残差以任务奖励为目标，不是对抗性破坏。区别于随机噪声，在于扰动依状态和学习进程变化。[方法§4](https://arxiv.org/html/2610.39054v1)

4. **保留亮点。** 把恢复数据主动纳入采集过程，且收益同时覆盖BC与离线RL；这是值得继续跟踪的工程切入点。本日没有新版本支持更强结论。[原文§6–7](https://arxiv.org/html/2610.39054v1)

5. **实验／讨论重点。** 今日重核表1：Cable离线RL为Clean **35±7%→DI 67±6%**，T-cube **42±6%→59±2%**，Keycap **81±6%→84±6%**；分别5/9/5个采集seed，每seed20次。仍须保留反证：表5全程采集成功率DI低于Clean，Cable **94.2% vs 96.9%**；“数据更有用”不等于“采集全程更成功”。作者仍明确人类全程在环、初期扰动近随机；未来错误模拟的机制尚缺直接因果隔离。[表1、5及§7](https://arxiv.org/html/2610.39054v1)

6. **热度增量。** 今日第7，**19赞、177浏览**；昨日10赞、102浏览，显示值增加9/75。只能称本平台本窗口名次上升、计数增加；未核实推动传播的具体事件。[alphaXiv](https://www.alphaxiv.org/abs/2610.39054)

7. **工程／代码。** 判断不变：适合已有遥操作管线团队做有人监督的小规模对照，优先核算有效数据/人时和安全边界。原实验2×RTX4090，持续人力仍是门槛。[附录A](https://arxiv.org/html/2610.39054v1)。昨日项目页未见代码入口；今日[项目页](https://data-inoculation.github.io/)不可通过本工具访问，限定GitHub的论文题名搜索未找到可确认为作者发布的实现，故写**“未核实新代码发布”**，不是“确认未开源”。

## 8. Cross-Controller Transfer via In-Context Behavior Adaptation（昨日#5）

1. **身份／版本。** Jonathan Yang、Chelsea Finn、Dorsa Sadigh，Stanford；VLA、跨控制器模仿学习。今日仍仅v1：2026-10-29 03:31:22 UTC（北京11:31）。[版本页](https://arxiv.org/abs/2610.39280)

2. **问题。** 同一动作向量在不同控制器上含义不同；动作转换不自动解决接触策略改变。[原文§III](https://arxiv.org/html/2610.39280v1)

3. **方法。** 部署控制器下3条交互轨迹抽128个状态转移，压成256个上下文token条件化π0.5；结合动作重标注与flow matching训练，推理不再训练。比SysID多提供实际行为证据，而非只给动力学参数。[原文§IV–V](https://arxiv.org/html/2610.39280v1)

4. **保留亮点。** 把跨控制器迁移拆成“动作语义+行为策略”；固定token及KV缓存也提供可实施的上下文复用路径。但没有今日新增实验可将其扩大到通用跨机器人结论。[原文§IV、VII](https://arxiv.org/html/2610.39280v1)

5. **实验／讨论重点。** 今日复核图5、7对应正文：未见控制器成功率 **50.3% vs 混训17.5%（+32.8个百分点）**；未见增益52%；工具插入上下文迁到USB绝对成功率仅35%。图6接触上下文50%、自由空间约30%，支持接触信息有用；实验仍限单实验室WidowX、单π0.5，不能写成跨任意硬件的成熟适配器。[§V–VII](https://arxiv.org/html/2610.39280v1)

6. **热度增量。** 今日第8，**30赞、261浏览**；昨日22赞、206浏览，显示值增加8/55。**名次下降与计数增长同时发生**，只能说明榜单相对位置改变，不能称全网关注降温。[alphaXiv](https://www.alphaxiv.org/abs/2610.39280)

7. **工程／代码。** 价值仍是已有多控制栈数据的兼容性实验；要有同步的指令/实际运动及接触记录，且还需微调集成。[原文§IV–V](https://arxiv.org/html/2610.39280v1)。今日直接复查昨日官网指向的[官方代码地址](https://github.com/JonathanYang0127/icl_cross_controller)，仍返回404；这不能区分未公开、迁移或删除。今日[项目页](https://controller-transfer.github.io/)不可访问，因此只确认旧地址不可用，不能排除另址发布。

## 9. FlatCake: A Flat KVCache Storage Architecture for LLM Serving｜新入

**先读结论：** 这篇值得LLM serving工程团队精读，因为它追查的不是“SSD带宽不够”这个表面症状，而是：SSD已有的KV为何仍会被当成miss重算？答案涉及host staging争用、预取取消、碎片化落盘与调度。最强结果来自高复用、长会话的Claude Code轨迹；不能泛化成所有LLM负载统一提速，更不能把total token throughput当成生成token速度。

### 1. 元信息、版本与可追溯入口

- **标题：** FlatCake: A Flat KVCache Storage Architecture for LLM Serving。
- **作者：** Xin Huang、Teng Ma、Zhuoran Li、Yibo Zhao、Zhaoshi Li、Qianchao Zhu、Wei Yang、Chenxi Wang、Tao Xie、Youwei Zhuo。论文署名机构包括复旦大学先进计算系统研究所、北京大学集成电路学院、MetaX、中科院计算所及独立研究者；通讯作者Youwei Zhuo。
- **版本：** arXiv:2610.38355 **v1**；2026-10-28 06:54:51 UTC提交，即**北京时间2026-10-28 14:54:51**。核查时版本历史仅v1，不把聚合站的抓取/更新日期当新版本。PDF 14页、10幅图；预印本，分类cs.DC / cs.OS。
- **领域：** LLM推理系统、prefix reuse、KV offloading、异构存储、I/O调度，不是模型训练算法。
- **一手入口：** [摘要与版本历史](https://arxiv.org/abs/2610.38355)、[HTML正文](https://arxiv.org/html/2610.38355v1)、[PDF](https://arxiv.org/pdf/2610.38355v1)、[共同作者Teng Ma主页](https://stmatengss.github.io/)。作者主页公告确认这是一篇新预印本，但只链接arXiv；本次未核实到官方FlatCake代码仓库、release或安装说明。

### 2. 具体问题：有缓存却用不上，比“缓存容量不足”更隐蔽

常见路径是GPU HBM→host DRAM→SSD，KV先进入DRAM，冷了再淘汰到SSD；恢复时SSD→host暂存→GPU。这隐含两个前提：DRAM能有效过滤冷热、host中转能隐藏SSD读取代价。作者认为生产KV访问不总满足它们：

- **稀疏复用型：** 普通API/对话轨迹大量块只访问一次，可复用prefix反而要隔很久才再次出现；LRU会被一次性块污染。
- **会话密集复用型：** agent反复追加工具结果和文件，下一轮立刻复用，但并发session总体太大，DRAM装不下。

因此SSD不是偶尔访问的“冷库”，而是大量命中的正常读路径。长prefix恢复占住host staging，负载升高会取消预取、回退GPU重算；按LRU淘汰顺序写SSD又打散同一session各层的块，单纯换成GDS也无法把非连续LBA变成一次顺序读。**FlatCake的目标是提高实际送达GPU的命中率，而非只提高“目录里查到键”的命中率。** [原文§1–2，Fig.1–2](https://arxiv.org/html/2610.38355v1)

### 3. 方法：写入位置、请求队列与读取布局一体设计

#### 3.1 数据流总览

`新生成KV → 判断session/reuse scope → 一次性绑定DRAM或SSD → 发布64位GVA`

`下一请求查prefix → key查GVA → 按最慢所需介质进队列 → DRAM直接H2D / SSD合并GDS读取 → GPU暂存+scatter → attention消费`

这里的“flat”是**host DRAM与SSD作为同级后备介质**，并不是GPU HBM也消失了，也不是SSD与DRAM具有相同带宽；论文测得host H2D约25–32GB/s，SSD每worker约5.5–6.5GB/s。[§3，Fig.3](https://arxiv.org/html/2610.38355v1)

#### 3.2 FC-GVA：一次放置、地址稳定、按session回收

利用KV块写一次后不可变的性质，在生成时选定归属，之后不跨DRAM/SSD迁移。Table2的启发式为：共享prompt（radix引用计数>1）和短回复的多轮chat进DRAM；长context/agent、长回复、未共享单次API、DRAM已满的写入进SSD。新一轮增量沿用session scope，以免同一会话落盘被其他会话打散。

第一层并发hash把`session ID、layer、token range`映射到GVA；64位地址分4位介质、12位节点、48位偏移。写入完成回调之后才发布索引，避免读取尚未写完的KV。读取按地址字段选cudaMemcpyAsync/RDMA/GDS/NVMe-oF，不逐层探测。SSD容量达到高水位时回收最老、无活跃reader的整个session extent，而非FIFO bucket一次切坏多个session的prefix。**“不迁移”不等于“永不淘汰”；仍有session级容量回收。** [§3.2，Table2](https://arxiv.org/html/2610.38355v1)

#### 3.3 FC-MAS：慢I/O不挡住已就绪请求，长请求也不无限靠后

全DRAM命中进DRAM-Ready队列；只要有SSD块，包括“共享DRAM系统提示词+SSD会话历史”的混合请求，就进SSD-Preparing队列。前者可先执行，后者后台预取。SSD队列使用带等待年龄的size-aware HRRN优先级`1 + wait_time / KV_size`；完成后按**原始到达时间**重新插入ready队列，而非无条件排尾。该设计避免共享FCFS的队头阻塞，也缓解严格DRAM优先可能带来的长SSD请求饥饿。[§3.3，Fig.4](https://arxiv.org/html/2610.38355v1)

#### 3.4 FC-CIO：写时顺序布局，读时合并，GPU窗口流水

- **写时：** 每个session scope映射到预分配的连续NVMe文件；每轮写batch采用layer-major次序，让同层token块连续，后续turn追加到同一GPU File。
- **读时：** radix tree给出page级描述符后，按`file ID、offset`排序合并相邻范围；允许跨越小于64KiB的未请求间隙，以少量额外顺序字节换少发I/O命令。多个worker使用独立cuFile handle与CUDA stream提交batch。
- **送入GPU：** GDS读进**预注册、双缓冲HBM staging窗口**，随后GPU scatter kernel把连续片段搬进SGLang非连续的256-token KV页；当前层计算与下一层I/O交叠。窗口满时等待CUDA事件，而不是撤销已有预取并重算。

所以它不是完全zero-copy：**取消的是host DRAM staging，仍存在GPU staging和GPU内scatter。** 论文描述理想读取命令数从“层数×块数”降到“层数”，这是连续范围齐备时的目标；多turn、部分prefix命中和extent边界仍需具体实现/测量确认，不能把所有任意请求都视为一次连续读。[§3.4，Fig.5](https://arxiv.org/html/2610.38355v1)

#### 3.5 实现与训练/推理边界

无需重新训练模型。作者报告约8.8K行C++17/CUDA、7.1K行Python，接SGLang `HiCacheStorage` 的`exists/get/put`接口，不改model runner或attention kernel。启动阶段分配并pin 2MB hugepage host pool；XFS/RAID0上用`fallocate`预分配、`O_DIRECT`打开文件，offset和buffer做4KiB对齐；固定HBM window只注册一次，减少BAR1/IOMMU映射成本；索引以64位CAS实现。这些是论文实现细节，**不是本次已审计的公开源码**。[§4](https://arxiv.org/html/2610.38355v1)

### 4. 三个最有价值的亮点

1. **改变介质关系，而非再设计一个LRU。** 不把所有KV都先挤进DRAM；热/冷并非唯一信息，session范围、不可变性与消费顺序也是存储设计信号。
2. **优化“交付命中”而非名义命中。** 存在SSD不保证用得上；把staging耗尽、取消预取和重算接成因果链，解释了为什么加大SSD容量仍救不回吞吐。
3. **说明GDS只是传输原语，不是完整架构。** 物理落盘布局、读描述符合并、GPU分页布局和调度必须一起考虑。这也是Mooncake-GDS对照最重要的作用，而非仅展示一个更慢的baseline。[§3–5](https://arxiv.org/html/2610.38355v1)

### 5. 实验证据、消融、公平性与没有证明的事

#### 5.1 工作负载观察不是八份端到端验证

Table1分析Mooncake三条、Qwen Bailian四条、Claude Code一条，共八条trace，且按各自原生块大小512/16/64 tokens统计；不同trace数值不应直接当统一page配置的排行榜。前七条一次性块占53.2%–94.0%；Claude Code仅16.6%，无限容量命中率98.31%、平均重用距离0.85个请求。Claude Code含98,827个请求、393个session、216亿输入tokens，平均每请求约21.9万输入tokens。

**主要端到端重放只有Claude Code这一条高复用agent轨迹。** 八条trace支持动机，不代表八种负载上都已实测FlatCake优势。[§2.2、5.1，Table1](https://arxiv.org/html/2610.38355v1)

#### 5.2 主实验设置与真实量级

主平台8×B200（各180GB HBM3e）、3TB host DRAM、8×3.84TB PM9A3 RAID0；各系统预算统一为**1TiB host KV、4TiB SSD KV**。软件为SGLang0.5.19、Mooncake0.3.13、CUDA13.1、GDS1.16.1。模型DeepSeek-V4-Flash-0731（284B MoE、43层混合MLA、FP8 KV、256-token页）；0.1–1.0QPS按原到达顺序回放、无cache warmup。比较DRAM-only HiCache、三层Mooncake和FlatCake；额外的Mooncake-GDS主要出现在Llama/A100 context sweep，不是主B200端到端负载曲线中的第四条完整对照。[§5.1，Table3](https://arxiv.org/html/2610.38355v1)

**Fig.6：1.0QPS端到端结果**

| 指标 | DRAM-only HiCache | Mooncake | FlatCake |
|---|---:|---:|---:|
| mean TTFT（秒，低好） | 17.51 | 12.24 | **7.57** |
| P50 TTFT（秒，低好） | 18.39 | 11.45 | **6.26** |
| total token throughput | 43.2K/s | 61.6K/s | **98.3K/s** |
| delivered cache hit rate | 53.30% | 约64.26% | **94.16%** |

相对Mooncake，mean TTFT比值约1.62，换成降幅是约**38%更低**，不是“降低160%”；吞吐约1.60倍。FlatCake全负载范围hit rate为94.16%–94.57%，Mooncake从0.1QPS的87.9%掉到0.5QPS及以上约64.26%。这里的命中按**prefill前实际送达HBM的块**计数。论文称吞吐为total token throughput，没有在这组结果中细分输入/输出token计数；不能改称98.3K“生成tokens/s”或decode阶段快1.6倍。[§5.2，Fig.6](https://arxiv.org/html/2610.38355v1)

另外，动机Table1的无限容量98.31%与Fig.6使用的source-prefix ceiling94.72%不是同一个数；原文没有在实验段完整交代换算，日报分别保留口径，不把它们混成“距离理论最优仅0.6个百分点”的同一基准。

#### 5.3 机制证据与对照强弱

- **调度独立消融：** FlatCake-w/o-FC-MAS保留GVA与CIO，仅改回共享FCFS。恢复双队列后mean TTFT降低10%–11%、P99降低27%、total吞吐提高12%。这比“只看三套整系统”更接近隔离调度作用；不过这些消融百分比在正文报告，未给完整逐负载P99绝对值表。[§5.3](https://arxiv.org/html/2610.38355v1)
- **I/O交付：** Fig.8的1QPS每worker SSD带宽为5.03 vs2.69GB/s；平均预取时间1.64 vs9.50s。它支持顺序读和减少无效恢复带来的收益，但并非SSD设备物理峰值提高了5.8倍。[Fig.8](https://arxiv.org/html/2610.38355v1)
- **读写放大：** Fig.9以FlatCake=1归一化，Mooncake读量/放大指标为6.51–6.72倍，写指标仅1.007–1.018倍。主要收益不是SSD写量下降几倍。尤其FlatCake读时允许64KiB gap bridging，不能由归一化的1.0推出“任何工作负载都完全没有多读字节”；也不能把相对读流量、SSD内部NAND write amplification混为一谈。[Fig.9、§3.4/5.3](https://arxiv.org/html/2610.38355v1)
- **跨模型、GDS-only对照：** Fig.10是4×A100、Llama-3.1-70B TP4、8K–128K上下文。16K时Mooncake-GDS与FlatCake **2.31 vs2.32s**，基本持平、后者略慢；64K拉开为**6.60 vs3.74s**，吞吐**8.6K vs14.0K/s**。这支持“长context下单换GDS不够”，也提醒不要把作者“所有长度最低”写成逐点严格优势。相对重算的TTFT倍数2.3–4.9、相对Mooncake1.5–2.4，应保留各自baseline。[§5.4，Fig.10](https://arxiv.org/html/2610.38355v1)

#### 5.4 公平性、成本与局限：落地前必须补证

**比较做得较好的部分：** 相同引擎和存储预算，明确版本；无预热主重放；另有保留tiered布局但更换GDS传输的对照；MAS有单组件移除。硬件数、内存预算和绝对TTFT均报告，避免只给相对倍数。

**尚不能推出的结论（阅读者评估）：**

1. **泛化范围有限。** 主性能负载是高reuse的agent coding，不能外推到几乎全一次性API、短prompt、低复用、超高并发等；没有与LMCache、Bidaw、Tutti等所有相关系统实测比较。
2. **收益来源还未完全正交隔离。** GVA、CIO、session回收和预取取消行为共同变化；除MAS外未见完整组合消融。若仅修复baseline的staging预算/取消策略能追回多少，本文没有给完备控制。
3. **部署成本不是零。** B200平台、TB级host内存、NVMe阵列、GDS、hugepages、预注册buffer和后台线程都是条件；未报告功耗、总拥有成本、CPU/core开销、metadata总量、启动预分配时间、SSD长期寿命或fault recovery成本。
4. **配置可复现性有缺口。** 放置规则有短回复阈值τ、agent context阈值L_agent，但正文未见具体取值/敏感性；固定GPU window的字节容量、并发stream上限、文件尺寸/高水位也未完整列出。两层KV的实际字节量本来依赖context；文中“O(1)窗口”应理解成受控预分配资源，不要当作任意长度/并发都不需更多存储的证明。
5. **扩展与稳定性未全面验证。** GVA字段能编码4096节点、设计提到远端RDMA/NVMe-oF，不等于完成4096节点或多机端到端测试；正文结果来自单服务器。没有完整报告p99.9/SLO-goodput、极端混合负载的公平性曲线、崩溃恢复、断电、索引重建和租户隔离。
6. **不可变/会话识别前提要成立。** 错放SSD主要是带宽代价，不需要迁移，但未来突然变热也不能自动迁回DRAM；整个session回收又是另一种取舍。shared-prefix、分叉session、跨模型/adapter隔离和版本失效规则需在实现层确认。论文并未给模型输出质量/数值一致性复验，不能因“不改attention kernel”就声称所有缓存正确性场景已覆盖。

以上不是声称系统必然失败，而是把论文已测的范围与生产上线还需验证的事项分开；原文没有独立的limitations章节。[正文§3–6](https://arxiv.org/html/2610.38355v1)

### 6. 热度：只写可核事实，不替热榜编因果

本报告2026-11-02的alphaXiv **7日Trending/Hot**统一快照：**第9，20赞、992浏览**。这是平台时间点快照，不是24小时新增论文榜，不是点赞增长率，也不能用它证明技术成熟度。[榜单入口](https://www.alphaxiv.org/?sort=Hot&interval=7+Days)

可核的一手传播迹象仅有共同作者主页2026.10公告及arXiv链接；没有核实到官方代码star、下载量、独立复现或传播来源分析，因此不写“因为某人转发/开源暴涨所以热门”。[作者主页](https://stmatengss.github.io/)

### 7. 工程价值、进入路径与门槛

**值得优先跟进：** 已经做SSD KV offload、agent长会话服务、SGLang/HiCache backend或GPU存储I/O的团队。应先问自己的cache miss有多少是“确实无数据”，多少是“SSD有数据但staging/排队超时送不来”，再决定是否重构整个层级。对只调用托管API的应用团队，这是理解成本/延迟来源的材料，不是一个立即可安装的加速插件。

**最小验证路线（建议，未执行）：**

1. 先在自己的匿名化trace记录reuse distance、session KV footprint、DRAM/SSD/HBM命中贡献、prefetch取消数与实际delivery hit rate。
2. 固定模型、page大小、KV dtype、GPU/host/SSD预算，至少比较host-staged、GDS-only原布局、GDS+session/layer布局三路；另切换MAS，避免只在两套整系统间归因。
3. 分别统计TTFT p50/p99、decode ITL、SLO goodput、读写字节、I/O命令大小、host/HBM staging峰值和CPU成本；吞吐明确区分输入/输出tokens。
4. 加入冷启动、低reuse、session增长/分叉、混合长短请求、存储压力和故障回收；验证输出/缓存键一致性，然后才计算成本收益。

**入口与现状：** 目前可读的是[论文§3–4实现说明](https://arxiv.org/html/2610.38355v1)和[作者主页](https://stmatengss.github.io/)。论文报告有原型实现不等于代码已公开；本次未找到作者明确发布的仓库，故没有源码级核验、安装命令或独立性能复现。不要把Mooncake/SGLang上游仓库当成本作已发布代码，也不要因论文给出15.9K行实现就称“一行开关即可启用”。

---

#### 阅读覆盖与材料边界

实际读取了arXiv v1 HTML的正文§1–7、Table1–3、Fig.1–10对应描述与数字，并用14页PDF文本交叉核对版本、主结果、I/O结果和context sweep；没有依赖alphaXiv自动摘要冒充原文阅读。工具的PDF图像输出未作为逐像素视觉证据，未从无数值曲线臆造精确点；只使用原文明确列出的数值。公开实现未确认，故仅做论文实现级分析，不声称代码审计。没有执行未知项目代码、外部写入或操作用户电脑。

## 10. L3G-World: Real-Time Infinite World Generation with Latent 3D Gaussian Memory（连续上榜）

1. **身份、版本与排名。** Jinhyeok Choi、JoungBin Lee、Jongmin Lee、Minkyeong Jeon、Jiyoung Kim、Kaeun Han、Yoonjin Yoon、Seungryong Kim；领域：World Model／Multimodal／3D Memory。今日第10、昨日第9，统一榜单24赞、242浏览；关联GitHub快照37。今天[arXiv历史](https://arxiv.org/abs/2610.40614)仍仅v1，首投2026-10-29 17:54:42 UTC／北京时间10月30日01:54:42。[alphaXiv原页](https://www.alphaxiv.org/abs/2610.40614)
2. **问题不变。** 持久场景记忆如何支持回访一致性且不按每帧无差别累积；不把“Infinite”理解为已证明无限时空或动态物理可靠性。
3. **方法增量。** 无确认新增。保留“按新区域新增、对可见旧高斯修正、直接渲染latent供生成器使用”的状态读写闭环；详细结构沿用昨日原文深读，不重复整段架构。
4. **亮点判断是否改变。** 不改变：空间记忆与生成器latent接口直接对齐，是可借鉴的工程设计；代码未发布时仍只是论文层面的方案审查，不能当已可集成模块。
5. **实验／限制增量。** 无新实验。今天回读[原文§4及表1–2](https://arxiv.org/html/2610.40614v1#S4)：9.02FPS的成本表在单H100测400帧；最高质量teacher与实时Fast不能合成同一性能点，RealEstate10K的Fast自一致PSNR16.19低于teacher18.36、FID49.94高于36.09。回环自一致不证明真实未见场景的物理正确性。未重新读全篇或逐帧评估演示，也未独立复现。
6. **热度与讨论。** 一位下降不能推出全网降温。今天额外读到[Issue #1](https://github.com/cvlab-kaist/L3G-World/issues/1)：NielsRogge于10月31日01:16:04 UTC／北京时间09:16:04提出未来在Hugging Face托管权重的建议，当前0回复。它发生在昨天报告之前，是今日补核的旧讨论，不是新发布、官方承诺或传播因果证明。GitHub本次首页43 stars与alphaXiv37的不同快照不能作为短时增长计算。
7. **工程可用性／代码核查。** 实际检查提交历史、完整目录树及[固定README](https://github.com/cvlab-kaist/L3G-World/blob/de9f7bcacc70c77d4bd06b2b49b1ef0abb364d54/README.md)：main最新仍为`de9f7bcacc70c77d4bd06b2b49b1ef0abb364d54`，2026-10-30 05:06:38 UTC／北京时间13:06:38；目录仅README、许可/NOTICE、gitignore与teaser资产，Mem/Gen代码及权重、推理代码、Fast权重四项发布计划均未勾选。**没有11月1日报告后的新提交，仍不能复跑。** README注明Mem权重非商业许可，不能以MIT仓库标签替代全部权重条款。维持等待正式发布与同配置速度—质量曲线的判断，不执行安装、不下载权重、不替作者生成未存在的运行命令。

两篇本轮公开来源核查时间：2026-11-02 03:23–03:24 UTC／北京时间11:23–11:24；排行使用本日报统一浏览器快照。结论是“未确认研究或可部署状态新增”，不是“网站没有讨论”。

## A. 今天最值得深入读的3篇

1. **FlatCake（#9）：优先研究服务成本，而不是直接替换线上缓存。** 本日唯一新入。重点读§3–4布局／GPU staging／eviction与§5评测，把TTFT、总吞吐、decode吞吐分开；工程上先用自己的会话长度、并发、复用率和SSD规格重建成本模型。没有已核官方实现，不能提供“安装即用”的命令。
2. **Spatial State（#3）：先读新增README的Paper and code对照，再决定可复现范围。** 新信息不是更强模型，而是公开材料不覆盖若干关键因果控制与L4。对Agent评测最有价值的是把“论文报告”“发布了代码”“可按公开材料重建结果”三个状态分开。下一步是核缺失材料，不是直接把62/70当自己复现通过。
3. **Unified Training（#2）：保留为训练系统学习材料，不重复炒作。** 附录D.6与固定`src/unified_training/hf_trainer.py`仍适合学习异步数据、loss归一化与样本年龄。今日无新版；已有阅读者可跳过背景，等新的数据、日志或同算力证据。

## B. 本日样本支持的研究方向

- **状态存储与消费路径比“记住更多”更具体。** FlatCake按session/layer布局KV，L3G直接render latent记忆；一个服务LLM复用、一个服务视觉生成，不能跨论文比较加速倍率，但都提示先测读写接口瓶颈。
- **效率必须带完整测量边界。** FlatCake的总吞吐不等于decode-only；Loop没有实测wall-clock；SpecSlot与L3G都有质量—计算折中。今天的新入论文强化这一工程问题，并未证明整个行业已完成范式转移。
- **过程评测与可复现性应并行审计。** Spatial State的历史/目标控制、精神科模拟的遗漏检查、DI的数据采集过程都超出单一最终分数；但开放材料是否足以检查这些结论，是另一个必要条件。Spatial的新README恰好暴露二者差距。

以上是今日前十的三组共同问题，不从两天榜单推断长期产业趋势。

## C. 与昨天相比

基线：北京时间2026-11-01 11:21:26–11:22:05的同一7日Hot榜，保存于[昨日固定报告](https://github.com/DanielMax937/daily-research-reports/blob/eb2fa6204f3d601290e33b661d0b8d4e08c563e7/2026-11-01/ai-papers.md)。今日快照距昨日约24小时。

- **新入前十：** FlatCake（#9）。其论文并非今天首次发表；“新入”只指相对昨日已核前十。
- **连续两次已核前十：** 其余九篇。前三与精神科模拟保持1–4；SpecSlot6→5、Loop7→6、DI8→7；Cross-Controller5→8、L3G9→10。
- **退出前十：** ScheduleGen昨日#10；未核它今日具体后续名次，因此不编下降多少，也不把退出解释为研究价值降低。
- **最有信息量的状态变化：** Spatial State新增README明确论文／代码覆盖缺口；PRH新增结果收录核验issue，尚非复现或作者认可。其他论文版本／已查主分支无确认实质增量；机器人项目页不可读取的部分单独标未核实，不冒充无变化。
- **新技术主题：** SSD上的LLM KV cache布局／I/O调度进入本次前十。不能凭此称该方向持续升温；目前只有一次新入观察。
- **不推断全网降温：** Cross-Controller与L3G名次下降时显示赞/浏览仍增加，相对排名与绝对关注快照不是一回事。

### 留存与后续核验条件

本文及本地榜单证据保留十篇ID、顺序、7日Hot条件、抓取时刻、指标原样、版本、已读源码commit、判断及来源。后续优先核：FlatCake官方代码和独立硬件复现；Spatial缺失控制／L4材料；Loop实际延迟；L3G正式代码权重；Unified消费年龄日志与数据发布。没有新证据的连续条目继续压缩，不靠配额重讲背景。

### 访问与研究边界

热榜来自云浏览器正常页面；论文来自arXiv原文与版本页；代码／讨论来自公开官方仓库。部分机器人项目页今日工具不可访问、Cross-Controller旧代码URL为404，已保留缺口。新入FlatCake按实际可读取内容深读，其余主要为版本与增量复核，详细范围见各项；不宣称全网X/HN/Reddit完整扫描。未执行论文代码、训练或临床实验，未以AI自动摘要代替作者原文；所有性能为作者报告，非本次独立复现。
