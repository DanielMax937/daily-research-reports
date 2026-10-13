# 2026-10-13 AI论文日报

## alphaXiv Hot 前10 论文与代码深读

**今天最值得工程团队细读的是CoTrace、Thinking Inertia和ReplaySSM：分别提醒我们，训练轨迹必须匹配实际运行框架，简短回答与正确回答要分开验收，推理加速必须按并发和硬件条件评估。** 榜首的“递归自我改进”同样值得研究，但原文和代码暴露的归因边界比标题更重要。

### 榜单口径与实际时间

- **实际抓取：2026-10-13约11:48 BJT / 03:48 UTC**，不是凌晨03:00的快照，也不是10月13日结束后的全天榜。
- 来源为[alphaXiv公开根首页](https://www.alphaxiv.org/)。本次正常读取的HTML公开结构化数据名为 **Trending Papers**，并给出明确position；同一响应服务端查询键为 **sort="Hot"、interval="30 Days"**，categories、subcategoryLabels、customCategoryLabels均为空，未设置来源或runnable筛选。本文采用这个可核的Hot顺序，不将搜索结果、最新论文或个人推荐冒称热榜。
- 页面查询状态的 **dataUpdatedAt=2026-10-13 03:43:43.338 UTC / 11:43:43.338 BJT**，dehydratedAt晚15毫秒。它是页面查询缓存记录时间，不保证每个点赞/浏览事件实时入库；实际客户端抓取只报告到可核的分钟精度。
- 已核的时间窗值是“30 Days”，不是“今天发表”，也不是“过去24小时新增热度”。这份HTML未保留可见筛选控件的Publication字样，因此不把未目视见到的UI文字当证据；无类别过滤也不等于每篇都属于同一细分领域。
- 冻结该响应前10篇，跳过研究者推荐卡片；论文、条目位置和计数均来自同一响应的ItemList，不与另一轮网页文本结果拼接。热度计数是平台累计交互字段，不是当天增量、独立访客数、学术质量或可复现性评分。
- 逐篇研究以arXiv版本化HTML、作者项目和公开代码为主。正文区分论文主张、实验能支持的范围、源码发布状态与工程推断；没有运行未知代码、训练模型、操作机器人或独立复现实验。阅读图表正文/图注不等于重新计算原始结果。
- alphaXiv单篇页部分可读、部分403或工具不可读；未绕过拒绝，也未伪造评论。**热榜可核不意味着热度成因可核。** 各篇未取得传播证据时明确说明。

### 固定前10清单

| Hot名次 | 论文 | 同次响应赞 / 浏览 | arXiv已核版本 | 首发日期 BJT |
|---:|---|---:|---|---|
| 1 | [RSI-Anything](https://www.alphaxiv.org/abs/2610.13912) | 30 / 531 | 2610.13912v1 | 10月10日 |
| 2 | [Thinking Inertia](https://www.alphaxiv.org/abs/2610.11765) | 13 / 216 | 2610.11765v1 | 10月8日 |
| 3 | [Embodied Turing Machines](https://www.alphaxiv.org/abs/2610.12369) | 114 / 1649 | 2610.12369v1 | 10月9日 |
| 4 | [ReplaySSM](https://www.alphaxiv.org/abs/2610.13778) | 25 / 223 | 2610.13778v1 | 10月9日 |
| 5 | [Universal Bounds for Self-Normalized KL Estimation](https://www.alphaxiv.org/abs/2610.12851) | 22 / 66 | 2610.12851v1 | 10月9日 |
| 6 | [CoTrace](https://www.alphaxiv.org/abs/2610.10426) | 10 / 74 | 2610.10426v1 | 10月8日 |
| 7 | [Physically Grounded Articulated 3D Assets](https://www.alphaxiv.org/abs/2610.13947) | 13 / 161 | 2610.13947v1 | 10月10日 |
| 8 | [Multi-Agent Self-Supervision / MASS](https://www.alphaxiv.org/abs/2610.12176) | 81 / 1016 | 2610.12176v1 | 10月8日 |
| 9 | [Sonic-AMG](https://www.alphaxiv.org/abs/2610.13300) | 11 / 49 | 2610.13300v1 | 10月9日 |
| 10 | [MagicBeanStalk](https://www.alphaxiv.org/abs/2610.12659) | 24 / 53 | 2610.12659v1 | 10月9日 |

没有一篇因为更符合Agent/RAG兴趣而替换入榜。A/B工程阅读等级只是后文的阅读建议，与以上平台顺序无关。下文所有“今天”均指本次查验日期，不自动等于论文首发、代码首发或新增实验日期。


## #01｜RSI-Anything: Unlocking Recursive Self-Improvement with World Models

### 1）作者、领域、版本与阅读范围
Taoyong Cui等11位作者，PhAI Labs、港中文等；领域是世界模型与Agent自改进。首发2026-10-09 17:50:30 UTC / 北京10月10日01:50:30，今日arXiv仍只列v1，不能把alphaXiv页面更新时间当修订。已读摘要、§1–3、§5–6、表1–4、附录A，目视图2–3，并核公开实现。[arXiv历史](https://arxiv.org/abs/2610.13912) · [alphaXiv](https://www.alphaxiv.org/abs/2610.13912)

### 2）具体解决什么问题
运行补丁、操作界面或做实验才知道结果，反馈昂贵；策略改变后，旧预测器又可能失准。本文要把“预测后筛选”和“保留通过验收的系统更新”接起来，避免只累积日志却称为能力进化。[§1–2](https://arxiv.org/html/2610.13912v1#S2)

### 3）方法、数据流与真实实现
输入任务状态和候选动作，JEPA式预测器编码上下文、预测潜状态，再输出结果分布；只执行预算内候选，保存预测—观察对。反馈可改策略/工作流；预测失准、数据和预算充足才尝试更新世界模型。组件与组合两级验收失败就保留旧版本。

代码修复固定7B coder，每轮四个新补丁；3B预测器对四候选及原程序评分，只有严格高于原程序才替换。源码效用为“整套测试通过概率＋0.25×预测通过比例”。**发布版评估明确optimizer_steps=0**，适配在此前训练阶段完成，不能写测试时在线改权重。[选补丁实现](https://github.com/Gen-Verse/RSI-Anything/blob/main/tasks/code_repair/src/evaluation.py) · [预测头](https://github.com/Gen-Verse/RSI-Anything/blob/main/tasks/code_repair/src/semantic_world.py)

### 4）创新点与我的判断
作者贡献是让世界模型进入反馈选择、可靠性评估及版本保留。我的判断：最有迁移价值的是分开记预测与实测、明确版本兼容性；跨领域共用的是流程，并非一个统一模型已掌握所有领域。[图2与§2.5](https://arxiv.org/html/2610.13912v1#S2.SS5)

### 5）实验、消融与限制
200道CodeContests×3种子、最多3轮：静态verifier26.3%，固定世界模型29.2%，适配后31.2%；在线测试调用均约3.72次。固定世界模型相对静态verifier的配对增益2.83个百分点，95%区间[0.17,5.50]。调用数相近不等于总算力相同。[表2、图3](https://arxiv.org/html/2610.13912v1#S3.T2)

GUI的51%→99%与动作减少39.4%来自100个checkbox实例。官方结果明确最终选中alpha=0，即按policy排序；不能把99%归因于推理时世界模型选动作。实验室46.01%是规划分，非真实操作成功率；化学96.15%对82.16%是指定40次预算内最好产率；免疫候选尚待实验。作者亦承认持续双向多轮提升还需验证。[GUI交叉结果](https://github.com/Gen-Verse/RSI-Anything/blob/main/tasks/gui/docs/RESULTS.md) · [讨论](https://arxiv.org/html/2610.13912v1#S5)

### 6）热度事实与代码状态
固定首页快照：Hot第1，30赞、531浏览；未获取足以解释热度来源的社区讨论或独立传播证据，不能据此判断社区共识。跨域自改进题材可能吸引关注，只是内容推测。

官方仓库和资源卡可读；未运行代码。打包验证仅短训练步，完整重训未跑，严格正交/因子独立检查未通过；不能将资源存在等同复现成功。[复现说明](https://github.com/Gen-Verse/RSI-Anything/blob/main/docs/reproduction.en.md) · [资源卡](https://huggingface.co/datasets/Gen-Verse/RSI-Anything)

### 7）工程迁移与深读建议
**B档：优先读验收机制及实现边界。** coding可先做固定模型的补丁排序对照；RAG可把预测置信、引文核验和最终答案质量分别存储；MCP结果附状态版本、输入与验收证据。全栈先做版本回滚和独立回归集，再考虑训练预测器。门槛是可靠反馈和留出的验收数据；论文没有直接证明RAG/MCP收益。

## #02｜Thinking Inertia: LLMs Keep Thinking When Told Not To

### 1）基本信息与阅读范围
Dianqiao Lei、Kevin Qinghong Lin、Pan Lu、Philip Torr、James Zou；清华、牛津、斯坦福，研究方向是推理控制、输出格式遵从与评测。首发2026-10-08 11:49:37 UTC / 19:49:37 BJT；[arXiv历史](https://arxiv.org/abs/2610.11765)本次只列v1，作者注明NeurIPS 2026录用。[alphaXiv](https://www.alphaxiv.org/abs/2610.11765)单篇页本次不可读，首页元数据已核。

实际读了摘要、§1–5、附录B/C、D/E相关验证，核图1–6、表1–6及数据/解码设置；读[项目页](https://thinking-inertia.github.io/)、README、主评测器的提示/响应分解/汇总代码和答案评分模块。代码快照为[8f8f1cd](https://github.com/thinking-inertia/code/tree/8f8f1cddcea6560df672fb70e83f013ce9f530e3)，最后提交10月9日05:27:45 UTC。本次没有运行模型或人工重标。

### 2）具体解决什么问题
把“thinking开关关闭”“没有think标签”“回答很短”当成没有可见推导，会漏掉普通答案文本里的计算、排除选项等步骤；反之，非空前缀也可能只是客套话。论文研究的是**可观察响应中的直接作答能力**，不读取、不推断模型隐藏思考是否停止。短输出也不能直接证明省了推理算力。[§1–2](https://arxiv.org/html/2610.11765v1#S2)

### 3）方法：输入、模块与数据流
题目Q经过干预包装，送给固定模型；解析响应为最终可解析答案A和前置文本T，再独立评分正确性与三项行为：ETR要求整个输出只含合法答案；QRel用Qwen3-Embedding-4B衡量Q与T相关性；EIR由只看Q/T、不看模型身份/模式/正确答案的盲评模型判断是否有明确推导，并留下证据片段。空T在后两项记零，分母均为全部输出。[§2.3、表1](https://arxiv.org/html/2610.11765v1#S2.SS3)

六种模式分别是原生开启/关闭、关闭后要求逐步推导、允许短前缀、严格仅答、预填答案前缀。预填是结构干预，不能简单排成“比严格提示更强”。没有训练新模型，代价在生成、embedding和judge调用。[表2](https://arxiv.org/html/2610.11765v1#T2)

源码将最后一个boxed/选项/数值答案定位、前后文本合法性、API reasoning字段分开记录；还单列解析失败和请求失败。复用时尤其不要把`empty_t_rate`直接当论文严格ETR，代码同时输出多个边界不同的率。[评测器](https://github.com/thinking-inertia/code/blob/8f8f1cddcea6560df672fb70e83f013ce9f530e3/src/thinking_inertia/eval_thinking_spectrum.py#L562)

### 4）真正值得保留的贡献
作者贡献主要是三层测量协议及答案空间控制实验。我的判断：第一，内容相关与真正推导分开，避免embedding相似度冒充思考检测；第二，同题改布尔/选择/开放形式，比跨数据集直接比较更能控制难度；第三，把最终正确与格式遵从拆开，比一个总成功率更利于定位产品失败。

### 5）实验支持什么，未证明什么
六模型、六基准。两本地Qwen用全量：BoolQ 3,270、StrategyQA 687、MMLU 14,042、MMLU-Pro 12,032、GSM8K 1,319、MATH 5,000；四API模型每模式5,687条，多数数据集抽1,000题。统一8,192 token预算；Gemini的minimal只是near-off，不是彻底off。[附录B](https://arxiv.org/html/2610.11765v1#A2)

- 开放题从原生关闭到严格仅答，五个有真正off条件的模型平均ETR近零→约40%，平均准确率下降约15个百分点；全语料相应EIR 99.69%→62.00%。不能把不同分母的两组平均数合成一个模型结果。[§3.3、图5](https://arxiv.org/html/2610.11765v1#S3.SS3)
- 同一批数值题，Qwen3-32B从选择题改为布尔验证，准确率77.8%→78.9%、ETR10.5%→62.5%；改开放题则准确率52.6%、ETR0%、EIR90.14%。支持答案接口改变可见行为，但提供候选本身也改变了计算任务。[§3.5、图6](https://arxiv.org/html/2610.11765v1#S3.SS5)
- 600输出、5位盲评者，402个非空T；人类与主judge二值推导标签平均一致98.8%，QRel与人类相关性均值0.829。人工空T与严格ETR只94.2%一致，差异来自答案可解析要求。[表5–6](https://arxiv.org/html/2610.11765v1#S3.SS6)

这些支持可见回答行为的规律，未证明内部认知过程、真实计费token或端到端时延必然下降；尚未验证代码、工具调用、多轮、多语言及随机采样。API可能变化，图中的跨模型标准差也不是全套逐结论显著性证明。本次无独立复现。

### 6）热度事实与推测
固定Hot快照第2，13赞、216浏览。未获取足以解释热度来源的社区讨论或独立传播证据。标题与“关闭推理仍产生推导”的直觉冲突可能吸引关注，只是内容推测。项目交互例子明确是预先计算的示意轨迹，不是在线模型demo。

### 7）Agent / RAG / MCP / 全栈工程价值
**A档，低成本评测思想可先迁移。** 对分类、路由、MCP参数生成，分别统计合法输出率、任务正确率、重试率、可见token、实际账单及P95，而非只靠“不要思考”提示。RAG中若最终只要枚举标签，可测试候选可见接口；开放综合题不可为了简短统一压制推导。论文没有直接验证这些工作流。

公开Python3.10+评测器、数据处理和指标目录可读，模型服务/权重由使用者提供；数学评分依赖规范化及math-verify，模型judge和4B embedding另耗资源。先读§2.3→§3.5→附录B/E，再查[benchmark_scorers.py](https://github.com/thinking-inertia/code/blob/8f8f1cddcea6560df672fb70e83f013ce9f530e3/src/thinking_inertia/benchmark_scorers.py)，用一小批真实工具输出校准解析器，而非直接套用论文百分比。

## #03｜Embodied Turing Machines: Stateful Code for Robot Recursive Self-Improvement

### 1）作者、领域、时间与阅读范围
Kairui Hu、Siyuan Hu、Fangzhou Hong、Zhaoxi Chen、Ziwei Liu，NTU与Ropedia，方向为具身智能、机器人代码策略。首发2026-10-08 17:29:08 UTC（北京10月9日01:29），截至本次核查仍仅v1。今天重新读取摘要、引言、§3–6及附录A–C/E，核图3、表2和附录成本、回归边界；PDF实看第6、10页。**这是昨日已报论文的复核，未发现新版本或新实验。** [版本记录](https://arxiv.org/abs/2610.12369) · [原文](https://arxiv.org/html/2610.12369v1)

### 2）具体解决什么问题
作者问的是：对于状态能可靠测量的重复机器人任务，能否把决策提前写成跨episode运行的程序，把大模型成本移到离线开发？COAP不是每一步请模型生成代码，而是上线冻结一套状态测量、操作与恢复逻辑。它更适合已知任务族，不代表机器人已能用纯代码理解任意开放世界。

### 3）输入、模块与训练／推理数据流
输入为三路RGB、关节角、末端位姿、夹爪命令回显和任务指令。NumPy/OpenCV先屏蔽机器人，再分割候选区域，利用已知相机、桌面与物体几何拟合位置和朝向；状态记录还保存测量来源、误差与时间。任务程序调用物体、抓取、规划、碰撞等共享层，执行后核验，失败则重测与换抓法。离线Claude Opus 5.5 coding agents在分支中改代码，经CPU检查及验证集择优；开发时可用模拟器真值调试，测试时不可用。与VLA/在线agent相比，省掉的是运行时模型调用，不是开发成本。[§3与图3](https://arxiv.org/html/2610.12369v1#S3)

### 4）创新与我的判断
作者主张显式状态、可恢复执行和共享库让代码适合递归改进。我的判断：真正可复用的是“状态字段→失败证据→局部补丁→回归测试”，以及默认关闭的新功能参数。论文的兼容条件只覆盖测试fixtures；图7的能力指数增长和baseline发展曲线是示意，不能当实验证明。83%共享代码也不等于新任务零开发。[§3.3](https://arxiv.org/html/2610.12369v1#S3.SS3) · [图7](https://arxiv.org/html/2610.12369v1#S4.F7)

### 5）结果、消融、代价与未证明之处
RoboDojo共42任务，每任务3 seeds×50布局。表2成功率70.24%，最强列出基线PhysicalRSI为31.38%，差38.86个百分点；75.45是进度分。泛化任务标准／随机布局77.3%／54.1%；同一程序测量状态／oracle状态为63%／83%，显示感知仍是瓶颈。旧任务78.4%→79.9%的回归检查p=0.16，只能排除较大退化，不能证明永不退化。[表2](https://arxiv.org/html/2610.12369v1#S4.T2) · [附录A](https://arxiv.org/html/2610.12369v1#A1)

0.3ms是控制调用中位数，多数只是交付已规划动作；每episode约25次感知规划占99.4%决策时间。所谓仅用VLA的0.8–2.4%算力，baseline按模型规模估算，非同机实测。全部结果来自仿真，几何先验、离线搜索与模型baseline训练预算未完全对齐，也没有展示生成轨迹实际提高VLA的实验；本次未独立复现。[附录A.1](https://arxiv.org/html/2610.12369v1#A1.SS1) · [局限](https://arxiv.org/html/2610.12369v1#S5.SS4)

### 6）热度事实、讨论与今日差分
固定Hot／30 Days无类别榜第3，114赞、1,649浏览。alphaXiv单篇页本次403；未获取足以解释热度来源的社区讨论或独立传播证据，不把内容吸引力写成热度原因。HF可读作者旧澄清，仍强调开发未用测试episode及模拟轨迹生成定位；相对昨日报没有新回应。[HF原帖](https://huggingface.co/papers/2610.12369#6ac86c43b5fb17eee6c8c071)

今天新增的核验是官方项目恢复可读；“Code”实际指向页内伪代码演示，已查页面未见完整策略库下载链接。这比昨日“源码状态未核实”更明确，但不能断言互联网所有位置均未发布。[项目及Code区](https://etmcode-bit.github.io/#code)

### 7）Agent／RAG／coding／MCP／全栈迁移
**B档：读状态接口与回归机制，暂不优先复刻机器人系统。** 可把稳定、重复的工具流程沉淀成受测代码；MCP返回成功后再核真实终态，RAG经验库保存适用条件、状态版本与失败反例。上线同时统计开发工时、异常恢复率、P95和每次正确完成的总成本。门槛是可靠状态采集、独立验收及真实回归集，不能只把自然语言记忆换成JSON。这些是工程迁移建议，论文没有RAG/MCP实测。

## #04｜ReplaySSM: Cache SSM Inputs, Not State

### 1）基本信息与阅读范围
Ze-Wei Liou、Harris Nover、Amey Naik、Andrii Skliar、Igor Shovkun、Ido Shahaf、Tri Dao；Princeton与NVIDIA，方向为混合SSM推理、推测解码与状态量化。首发2026-10-09 15:59:40 UTC / 23:59:40 BJT，[arXiv历史](https://arxiv.org/abs/2610.13778)仅v1。[alphaXiv条目](https://www.alphaxiv.org/abs/2610.13778)单页不可读，榜单元数据已核。

已读摘要、§1–9、附录E硬件/计时/批量与精度结果，核图1–6、主表1–2、附表5–7；对照README、低精度README、Mamba2标准kernel及端到端计时脚本。仓库固定[5d3ea59](https://github.com/Johnny-Liou/ReplaySSM/tree/5d3ea597d479ef0c8e9e2eb2845a2adfdb9a8b44)，最后提交9月30日22:51:58 UTC；没有编译或运行GPU代码。

### 2）具体问题
SSM虽把上下文压成固定状态，每token仍读写整块状态，易被显存带宽限制；推测解码拒绝后还需恢复旧状态；若同一低精度状态持续递归，舍入误差会往后传播。论文优化的是服务推理状态管理，不是增加长上下文记忆容量，也不是新的训练方法。[§3](https://arxiv.org/html/2610.13778v1#S3)

### 3）工程化方法与baseline差异
把当前状态表示成较早checkpoint＋最近输入环形缓冲。通常步骤只追加小输入并算输出；窗口满时才把已接受输入折进checkpoint并写回。标准窗口L=16；仍需读状态，不能说不碰HBM。窗口越长，写回越少，重放输入计算和读流量越大。[§4](https://arxiv.org/html/2610.13778v1#S4)

推测时先缓存所有草稿输入，只通过指针提交接受前缀，拒绝后覆盖后缀；output-only公式直接算输出，省去物化每个中间状态。GDN需处理依赖前状态的修正项，作者用小型三角求解，并在高精度flush时重算修正，不能把Mamba2公式原样套过去。[§5–6](https://arxiv.org/html/2610.13778v1#S5)

低精度读副本服务输出，高精度anchor承担下一轮递归，两副本从未舍入累加结果独立生成；因此消除的是低精度读误差的反馈路径，高精度路径仍有误差，当前输出仍近似。源码非flush分支只写输入cache，flush分支才写state，与主要机制一致。[kernel](https://github.com/Johnny-Liou/ReplaySSM/blob/5d3ea597d479ef0c8e9e2eb2845a2adfdb9a8b44/vllm/model_executor/layers/mamba/ops/selective_state_update_replayssm_output_only.py#L275)

### 4）创新及作者主张边界
三点贡献是推迟状态写回、输入缓存支持低成本回滚、读精度与递归精度分离。我的判断：最有价值的是用同一状态表示解决服务系统三个耦合问题，而非孤立kernel提速。数学上等价仍允许浮点差异，不能据此承诺生成完全逐token一致。

### 5）实验、成本及公平性
四混合模型；4B用单H100 80GB，120B级NVFP4权重用单B300、1100W功耗限制，不做张量并行。与同一vLLM build、CUDA graphs开启、调优后的常规kernel比较，性能主实验均FP32状态。[附录E.1](https://arxiv.org/html/2610.13778v1#A5.SS1)

- B=256时kernel1.46–1.80×、整步1.20–1.47×；B=1整步仅0.96–0.99×，不能承诺个人单会话更快。表6另标B=512两个大模型的整步结果受功耗上限放大，不能直接外推。[表6–7](https://arxiv.org/html/2610.13778v1#A5.SS2)
- 推测实验用GSM8K prompt、每请求生成256 token、T=4；B=512相对传统推测吞吐为1.85×/2.10×，接受长度匹配。它是含prefill的指定服务吞吐，不是任意交互Agent的P95。[§7.3、图3–4](https://arxiv.org/html/2610.13778v1#S7.SS3)
- PG-19教师强制到128K，Qwen3.5-4B的NVFP4读＋FP32递归将KL0.136降至0.0038。主表2中，共用NVFP4+SR平均GPQA下降13.05个百分点，分离NVFP4读/FP16+SR递归仍降2.36点，不能称无损。[§7.4、表2](https://arxiv.org/html/2610.13778v1#S7.SS4)

公开[e2e_decode_speedup.py](https://github.com/Johnny-Liou/ReplaySSM/blob/5d3ea597d479ef0c8e9e2eb2845a2adfdb9a8b44/benchmarks/replayssm/e2e_decode_speedup.py)复用同一prompt、强制固定输出长度并取多次最快整轮；原文kernel计时写的是重复launch中位数。这是不同测量层和汇总口径，重测时应分别记录，不能一条脚本输出当所有论文数字的复现。论文未给生产流量完整尾延迟/成本证明，本次也没有独立复现。

### 6）热度与真实采用证据
固定Hot第4，25赞、223浏览。未获取足以解释热度来源的社区讨论或独立传播证据。另有可核工程采用：官方[vLLM PR #48018](https://github.com/vllm-project/vllm/pull/48018)为Mamba2标准解码，状态merged，合并于7月24日；说明该路径并非今天才落地。不能把一个合并PR推成全部量化/推测路径都已进入稳定发行版，也不能证明它造成今日排名。

### 7）工程价值与落地门槛
**A档，适合自托管混合SSM且有足够并发的服务。** Agent长推理、coding/RAG后台批处理可能受益，MCP/全栈应用只有底层服务使用对应架构才直接相关。先profile状态带宽占比，再固定batch、序列长、功耗与正确性比较；无权控制服务栈的API用户不能靠prompt启用它。

仓库是vLLM fork，可读四条Mamba2/GDN标准与推测路径。重要缺口：[低精度CuTe](https://github.com/Johnny-Liou/ReplaySSM/blob/5d3ea597d479ef0c8e9e2eb2845a2adfdb9a8b44/low_precision/README.md)为B300/SM103专用、L=16、特定head形状的独立kernel，**未接入vLLM serving dispatch**；低精度准确率用仿真量化，不能拼成“低精度已端到端无损加速”的产品规格。先读§4–6→表6/2→低精度限制，再考虑部署。

## #05｜Universal Bounds for Self-Normalized Kullback–Leibler Estimation

### 1）基本信息与阅读范围
Buu Phan、Lester Mackey、David Alvarez-Melis；Toronto、Microsoft Research、Harvard，统计学习、重要性采样、推理时对齐。首发2026-10-09 01:20:22 UTC / 09:20:22 BJT，[arXiv](https://arxiv.org/abs/2610.12851)仅v1；[alphaXiv](https://www.alphaxiv.org/abs/2610.12851)单篇页不可读。

读摘要、§1–5全部主论证与实验说明、附录C.1证明框架/D.1–D.2核心推导、J实验，核主图1–2、附图4–11及分布设置表1。没有宣称逐行验证全部证明。原文未列官方代码/项目/demo链接，检索未核到作者发布仓库，公开代码状态留空而非断言不存在。

### 2）具体解决什么问题
从基础分布抽N个候选，再按归一化权重择一，会把输出分布推离基础模型。常用“权重熵”便宜，却不等于真实输出分布KL；旧有限样本界常要求权重有界或高阶矩。本文为这种估计与重采样分布的关系给更弱假设下的保证，不是一个新大模型，也没发明Soft Best-of-N本身。[§1](https://arxiv.org/html/2610.12851v1#S1)

### 3）算法/工程数据流
冻结基础策略q，为每个输入独立采N个候选，reward转换为指数权重，再归一化为λ；按λ随机选候选，而非硬取最大reward。随手可计算D̂=log N−H(λ)。理论把一次候选池中的估计、许多独立池的期望、最终重采样输出分布pN三者明确区分。[§2.1–2.2](https://arxiv.org/html/2610.12851v1#S2)

上界只需候选分数与权重；下界还需额外独立候选池估计隐式密度比，属于嵌套Monte Carlo，成本更高。相对仅由reward取值范围给出的旧界，新界随实际权重分布变化；无需知道Gibbs目标归一化常数。没有模型训练阶段，新增成本来自N次生成、reward评估和跨池重复。

### 4）三个贡献及条件
作者证明：估计的期望超过目标–基础KL的量至多log2；重采样分布KL不超过估计期望，也不超过目标–基础KL；再给辅助采样下界及相对熵编码推论。这里log2为自然对数约0.693 nats，不是2 bits。假设仍包含同支持、有限目标KL；“没有高阶矩要求”不等于没有任何条件。[定理1–3](https://arxiv.org/html/2610.12851v1#S1)

我的判断：最可复用的是给Best-of-N服务加一条分布偏移测量线，并提醒大家别把单池熵值当总体保证。附录D.1通过候选池＋索引联合分布的KL，再经数据处理不等式得到输出界，解释了为什么控制的是随机重采样策略而非任意后处理。[证明](https://arxiv.org/html/2610.12851v1#A4.SS1)

### 5）实验支持与未证明范围
主图2(a)用8结果离散空间精确枚举有限N分布，改变reward与基础概率的对齐关系；D̂期望用50,000独立池估计。新界比仅看reward范围的旧界紧，支持理论在这些受控分布上的意义。[§2.3、图2](https://arxiv.org/html/2610.12851v1#S2.SS3)

图2(b)用1,000点离散高斯，K=1/16/64重复，误差条为2.5–97.5百分位；K=16在测试场景常够稳定，是经验观察，**不是任意生产任务的高置信保证**。参考KL的辅助采样M=2,000、B=50,000，本身有计算预算。[同节](https://arxiv.org/html/2610.12851v1#S2.SS3)

附录J搜索到最大正松弛约0.142（rare-bump、N=320），未超过0.15；0.15只是改进常数的猜想，不是已证明新界。等采样预算4N/8N/16N对比中，下界嵌套估计更不稳定；N=64的一例真实有限N KL约1.895、估计期望1.969、目标KL1.994。[附录J.1–J.2](https://arxiv.org/html/2610.12851v1#A10)

没有LLM、Agent、RAG真实任务胜率或GPU成本实验；统计模拟也没有证明reward正确、答案更真实或系统更安全。单个有限K均值可能低于期望，若用作上线限制需要额外置信控制；多轮相关候选、适应性修改reward亦需另论。本次未独立重算模拟或证明。

### 6）热度事实与推测
固定Hot第5，22赞、66浏览。未获取足以解释热度来源的社区讨论或独立传播证据。它把推理时采样与严格分布界连接起来，可能吸引理论和对齐研究者，只是内容推测，不能据计数推成广泛社区共识。

### 7）Agent / RAG / MCP / 全栈价值
**B档，优先给已有多候选选择器补测量。** 如果Agent并行生成多份计划或RAG答案，再以固定reward软重采样，可离线记录N、温度β、权重熵、任务正确率和总成本，区分更多采样与更激进筛选。候选之间必须符合所用保证的采样假设；相关agent互相讨论后得到的结果不自动满足i.i.d.。

该界不验证MCP动作权限、RAG证据真实性或coding测试完整性，不能替代独立验收。算法片段易实现，可靠reward、候选独立性、重复采样预算与线上置信判定才是门槛。推荐§1三定理→§2.3→附录D.1/J.2；没有核到作者代码，暂不能称可按官方脚本复现。

## #06｜CoTrace: Data Recipes for Training Terminal Agents with Harness–Model Co-Evolution

### 1）作者、领域、版本与阅读范围
Jixuan Chen、Jiaxin Zhang等14位作者，UC San Diego、Salesforce AI Research、UW；终端Agent训练数据与运行框架协同优化。首发2026-10-07 17:06:59 UTC / 北京10月8日01:06:59，当前v1。已读摘要、§1–4/6、算法1、表1–3/5–6/12–13，附录B、C.4–6、E.5/E.9、F.2，并目视扩展流程图6。[arXiv](https://arxiv.org/abs/2610.10426) · [alphaXiv](https://www.alphaxiv.org/abs/2610.10426)

### 2）具体解决什么问题
成功轨迹并非可互换教材：某条轨迹依赖的提示、工具接口和恢复逻辑，可能来自后来被淘汰的harness。混合训练后，模型在部署框架中反而不会正确提交。本文研究数据如何在“改harness”与“训模型”之间流动。[引言](https://arxiv.org/html/2610.10426v1#S1)

### 3）方法、数据流及baseline差异
容器任务包含指令、初始状态、终态verifier。Route把可归因的运行故障送给框架搜索；SFT只取与采用框架的提示/工具/processor指纹一致、通过验证的轨迹，不足再补新rollout。Ratchet交替固定权重或框架评估另一组件。Refresh让已解决且已进入训练集的题退出，再补新题。RL分支直接在采用框架下采样、用DPPO更新，天然匹配运行时。[§2与算法1](https://arxiv.org/html/2610.10426v1#S2)

baseline混合兄弟harness的成功轨迹；本方法同时改变来源、覆盖、新鲜度、每题上限和回放比例，因此不是单一“指纹过滤”消融。

### 4）创新点与我的判断
作者强调数据路由、组件级晋升和课程刷新。我的判断：最实用的是把harness当作数据分布的一部分，模型发布应绑定运行时版本；组件分开验收也让增益更可归因。接受的框架改动主要是循环阻断、预算/自验和依赖守卫，未展示通过发明新工具取得收益。[表3](https://arxiv.org/html/2610.10426v1#S4.T3) · [表13](https://arxiv.org/html/2610.10426v1#A5.SS9)

### 5）真实数字、成本与限制
9B在102题晋升集上78→88，增益拆为harness+4、模型+6；RL到90。该集合反复决定是否接受更新，**不是独立测试集**。混合149–308条轨迹的3次模型更新全被拒；匹配30–50条的5次更新接受2次。每轮47对54 GPU小时，但整链约235对162，不能说总成本更低。[表1–2](https://arxiv.org/html/2610.10426v1#S3.T1)

SWE-Lite固定SFT checkpoint，仅换框架，24.7%→35.0%、无补丁155→64；仍低于base配对37.3%。RL配对41.0%，对base的配对检验p=0.16。TB2.1的SFT在原框架18.3±2.5/89，base18.7±1.5，未见稳定checkpoint泛化。每条链只跑一次，单评约±2题，SFT/RL未匹配算力；评测用8×H200，本次无独立复现。[§4.3](https://arxiv.org/html/2610.10426v1#S4.SS3) · [附录C.4–5](https://arxiv.org/html/2610.10426v1#A3.SS4) · [E.5](https://arxiv.org/html/2610.10426v1#A5.SS5)

### 6）热度与公开交付
首页固定快照第6，10赞、74浏览；单篇缓存显示56浏览，不能混算增长。未获取足以解释热度来源的社区讨论或独立传播证据，不能据此判断社区共识。生产Agent的框架兼容问题可能带来关注，是推测。

原文说发布接受的配置，但本次未在论文及alphaXiv取得可验证的官方仓库/下载链接，故代码与demo可用性未证实，不能称完全可复现。

### 7）Agent / RAG / coding / MCP / 全栈价值
**A档，今天最值得新增深读之一。** 先给轨迹加模型、提示、工具schema、processor和验证器版本；按最早未恢复故障分层归因，再比较同预算的混合池与匹配池。RAG还需固定语料/检索器版本，MCP升级要做参数与响应兼容回归，全栈可先试循环阻断和缺补丁检查。无需先投入8卡训练；先验证运行时契约，留一组从不用于晋升的终测。迁移建议不是本文新增实验。

## #07｜Towards Physically Grounded Articulated 3D Assets: A Multi-Agent Pipeline and Benchmark（Artisan）

### 1）作者、领域、时间与阅读范围
Xudong Cai、Ruijie Zhu、Haoliang Shang、Ruining Li、Marc Pollefeys、Shangzhe Wu、Andrea Vedaldi、Chuanxia Zheng，来自NTU、ETH、Oxford、Cambridge与Microsoft；领域为程序化3D生成、仿真及多Agent。首发2026-10-09 17:59:41 UTC（北京10月10日01:59），仅v1。已读摘要、引言、§3–6、附录A、B.4、C.2、D、E、F，核图2/4、表1–3/11/12及PDF第4、8、28页；另查官方README、配置、数据入口、benchmark运行器及SDK契约。[版本](https://arxiv.org/abs/2610.13947) · [全文](https://arxiv.org/html/2610.13947v1)

### 2）具体解决什么问题
“看起来像”不保证门能打开、抽屉不穿模或物体在重力下不倒。Artisan在Articraft基础上联合生成几何、关节、质量与材料，再把可运行的物理反馈放进修复循环，并用视觉、物理、机器人任务与人评共同验收，避免只优化漂亮截图。

### 3）真实数据流与baseline差异
输入文字及可选参考图。Design Agent给出零件／关节／功能蓝图和多视图设计板；Coding Agent用Python、CAD／Blender及标准铰链、滑轨等组件构造资产；MuJoCo返回碰撞部件、姿态、穿透深度与重力倾斜；Review Agent独立看程序、渲染和证据，写测试、提问题，但不能改资产。Coding据此修复，输出URDF、关节属性、质量及交互标注。与Articraft单agent自评相比，核心是分权评审与外部仿真约束，不是训练新基础模型。[图2与§3](https://arxiv.org/html/2610.13947v1#S3)

### 4）创新与我的判断
作者主张多Agent减少自评偏差，物理验证提升可用性；我更看重两点：物理通过不抵消功能缺失，以及错误报告定位到可修改部件。附录F中搅拌机虽通过24项测试，评审仍发现旋钮被碗挡住；修复保留碗尺寸和关节行程。它证明实例中的独立检查有价值，尚不证明多Agent普遍消除偏差。[附录F](https://arxiv.org/html/2610.13947v1#A6)

### 5）实验、消融、预算与边界
数据覆盖ArtVIP与LightWheel各50资产、50稳定性提示、50 ABO质量对象。GPT-6 Astra版本单／双／多关节碰撞率1.7%／3.7%／13.0%，静止／展开稳定率98%／96%；质量APE 0.260，但ADE 5.86kg并非最优。GPT-5.6 Sol消融去掉物理验证后，单关节碰撞1.9%→35.7%、多关节16.4%→73.2%；去评审反而使多关节碰撞降至11.8%，所以不能笼统写每组件都改善每指标。[表2](https://arxiv.org/html/2610.13947v1#S4.T2) · [表11](https://arxiv.org/html/2610.13947v1#A3.T11)

加入资产后π0.5在RoboTwin／RoboCasa留出原生资产上80%→84%／39%→43%；训练资产及示范数量也增加，并非等数据预算归因。RoboCasa资产能生成示范的比例仍只有44%。同模型比较中Artisan平均$5.79、34.3分钟／资产，Articraft $0.95、5.4分钟，质量提升有明显成本。人评30人、275有效回答，非工业验收；有限姿态采样、仿真材料和已知物体集不构成真实世界安全保证，本次未独立复现。[表3](https://arxiv.org/html/2610.13947v1#S4.T3) · [预算表12](https://arxiv.org/html/2610.13947v1#A4.T12)

还需分清开发门与最终评测：生成时碰撞筛查使用7点关节网格、最多1,500姿态；评测单／双关节使用9点网格，另采200组多关节配置。通过抽样检查不等于整个配置空间均无碰撞。独立评审移除后的部分指标改善，提示“减少自评偏差”应与结构保真、零件数及计算投入一起分析，不能只取一个碰撞分数。整体是系统与评测贡献，尚非真实材质、摩擦和质量已准确恢复的通用证明。[物理协议](https://arxiv.org/html/2610.13947v1#A1.SS3)

### 6）热度事实与推测
固定榜第7，13赞、161浏览。alphaXiv详情403；未获取足以解释热度来源的社区讨论或独立传播证据。多Agent、可交互资产及仿真验收可能吸引读者，只是内容层推测。官方项目、代码README、公开数据元信息及交互demo HTML均可读取；未实际操作demo，不称已端到端验证。[项目](https://physicalvision.github.io/artisan/) · [官方代码](https://github.com/physicalvision/Artisan)

### 7）Agent／RAG／coding／MCP／全栈迁移
**A档：适合借鉴评审权限和证据接口。** 把验收者设为只能读产物、改独立测试；MCP返回结构化缺陷位置、严重度、候选版本哈希；RAG检索标准组件与真实API契约。已读SDK要求报告model_sha256匹配当前代码，并警告整对部件的碰撞豁免可能掩盖新穿模；benchmark运行器区分正常与降级交付。工程门槛是CAD／Blender／MuJoCo依赖、API预算和独立测试质量。代码可读不等于已经复现；本次未安装、运行或核完整生成栈。[SDK契约](https://github.com/physicalvision/Artisan/blob/main/sdk/_docs/model_contract.md) · [运行器](https://github.com/physicalvision/Artisan/blob/main/benchmark/run.py)

## #08｜Recursive Self-Improvement through Multi-Agent Self-Supervision（MASS）

### 1）作者、版本与今日差分
Hyunin Lee等七位作者，UC Berkeley与Sakana AI；多Agent自监督及工作流学习。首发2026-10-08 15:44:02 UTC / 北京23:44:02，今日仍只有v1。**这是昨日已读论文的复核，非今日新论文。** 重读摘要、§1/3/4.1–2/5/7、表1–3/7、附录B.1–2/C.5，目视图1，检查关键源码。[arXiv历史](https://arxiv.org/abs/2610.12176) · [alphaXiv](https://www.alphaxiv.org/abs/2610.12176)

今日main的README、复现说明、覆盖清单与昨日记录的[fb40358快照](https://github.com/SakanaAI/mass/tree/fb403581bed2c974b3f99e7236224169da643079)逐字节相同。提交历史接口限流，未核全仓变化；没有证据表明昨天的复现缺口已关闭。

### 2）具体问题
开放研究没有便宜的硬标签，同模型自评可能共享盲点。MASS试图先改善模型副本之间的分工与信息交付，再把协作轨迹训练进共享权重；两轮有效不保证永远递归进步。[§1](https://arxiv.org/html/2610.12176v1#S1)

### 3）方法与实现
固定当前模型，搜索角色、指令、输出契约及调用顺序；执行后成对自评工作产物，保留较优工作流。每训练任务生成18轨迹，Bradley–Terry排序，最多15条训练、第16条验证。训练时主Agent输入去掉工作流，保留子任务指令；只对assistant输出计算损失，权重更新后再兼任执行、优化和评审。[§3](https://arxiv.org/html/2610.12176v1#S3)

源码核到select隔离训练/验证轨迹，best_checkpoint按最小有效验证损失选择；公开RHI采用固定裸任务参照与冠军仲裁，仍不等同论文直接比较当前最佳产物。[pipeline实现](https://github.com/SakanaAI/mass/blob/main/mass/pipeline.py) · [复现差异](https://github.com/SakanaAI/mass/blob/main/docs/reproduction.md)

### 4）创新与判断
作者主张联合学习调度和局部执行能提高监督效率。我的判断：可审核的输出契约比多开Agent更值得复制。固定base执行器，第一轮改进模型生成的工作流胜率64%，支持工作流本身有价值；同源自评仍不是独立正确性保证。[表1](https://arxiv.org/html/2610.12176v1#S4.T1)

### 5）实验与仍在的边界
首轮实际8题、119轨迹、17.2M存储监督token；6×H100约19小时仅是SFT，不含搜索、采集及评审。三道合成测试任务第二轮对base胜率69.9%，外部LLM评审不等于人类真值。[附录B](https://arxiv.org/html/2610.12176v1#A2)

v1表7的MLR是12题×5次：1.58→2.40、交付31/60→50/60；180次均未委派，按任务聚合配对p=0.2266。README的107题×3次、1.71→2.25属于另一口径；v1正文也提107题，不能拼接。Terminal-Bench37.5%→35.2%、SWE-bench62.6%→61.1%，并非通用编码全面增强。[C.5与表7](https://arxiv.org/html/2610.12176v1#A3.SS5)

公开包缺107题配置和多项适配器；第二轮精确数据/预算清单仍缺，训练与端到端复跑未验证。本次也未独立复现。[覆盖清单](https://github.com/SakanaAI/mass/blob/main/docs/experiment_coverage.md)

### 6）热度与新增证据
固定首页第8，81赞、1,016浏览。昨日41赞/508浏览只是不同时间首页样本，不据此算24小时增长或名次变动。未获取足以解释热度来源的社区讨论或独立传播证据，不能据此判断社区共识。今日新增是三份官方文件的内容一致性核验，没有新论文版本、新实验或缺口修复的证据。

### 7）工程迁移与门槛
**A档机制，今日阅读优先级低于新证据更多的CoTrace。** Agent/RAG先固定模型、预算和不可改验收，比较裸提示、人工契约、搜索契约；MCP交付包含证据和失败状态，全栈同时验功能、结果文件及可重跑性。若再训练，保留调度/执行标签、工具版本和失败反例。评测必须分目录，避免覆盖manifest或把历史判定混进新报表；这是实际复现门槛，不是多Agent数量问题。[运行注意事项](https://github.com/SakanaAI/mass/blob/main/docs/reproduction.md#synthetic-evaluation)

## #09｜Sonic-AMG: Streaming Human Motion Generation from Spatial Audio

### 1）作者、领域、时间与阅读范围
Jingcheng Ni、Zekun Li、Zhiyang Dou、Xiaoyan Cong、Ziyao Zeng、Hongyang Du、Randall Balestriero、Taku Komura、Srinath Sridhar，Brown、MIT、Yale及HKU，领域为音频条件动作生成与实时具身动画。首发2026-10-09 09:47:03 UTC（北京17:47），仅v1。已读摘要、引言、§3–5、附录A–F，核图2/5/6/9、表2–6/8，PDF实看第4、9页；代码与模型的论文承诺是接收后发布。[版本](https://arxiv.org/abs/2610.13300) · [全文](https://arxiv.org/html/2610.13300v1)

### 2）具体解决什么问题
离线动作模型可等完整声音片段与位置序列再生成；真正流式反应不能偷看未来，而且身体一转，声源相对身体的位置就变。论文同时处理“训练用真实动作、推理用自产动作”的历史误差，以及动作改变后空间条件仍沿用真实轨迹的错配。

### 3）输入、模块与训练／推理
主要输入为双耳音频、已知世界坐标声源、反应风格标签及4帧初始真实动作。左右耳log-mel经共享因果CNN形成what token；方向、距离及变化量等11维特征形成where token。二者与动作token交错送入因果Transformer，flow head用10步Euler采样下一16维latent，冻结因果VAE解出4帧30Hz动作；KV cache复用历史，已输出帧不重写。

Rehearsal将全序列teacher forcing与短自回放损失等权结合，采样latent停止梯度；空间反馈从生成的根位姿重算声源相对位置，再条件化下一块。区别于two-forward训练，后面的回放确实依赖前面自己生成的结果。[§3与图2](https://arxiv.org/html/2610.13300v1#S3)

### 4）创新与我的判断
作者称其为首个空间音频流式人体动作框架；已核证据支持因果生成、what／where解耦及闭环训练，但“首个”仍是作者定位。我的判断：最有迁移价值的是动作历史与条件状态必须来自同一条实际轨迹。只让模型练习错误历史、却继续提供理想化状态，会严重高估部署能力。[空间反馈](https://arxiv.org/html/2610.13300v1#S3.SS4)

### 5）数字、消融、算力与公平比较
SAM含27声音场景、3反应风格。相同GT空间协议下，MOSPA FID 8.242、R@1 0.942±0.004；Sonic为6.505、0.957±0.004。更现实的Online主结果FID 8.066、R@1 0.943±0.004，但用了H=32；消融默认H=16，FID为8.714，不能混写。同一GT训练模型直接改Online测试，FID恶化至25.872，说明空间错配影响很大。[表2](https://arxiv.org/html/2610.13300v1#S4.T2) · [表5–6](https://arxiv.org/html/2610.13300v1#S4.SS4) · [H设定](https://arxiv.org/html/2610.13300v1#A6)

A6000 Online每4帧均值50.2ms、P95 53.2ms，低于133.3ms块时长；约193ms首响是输入等待加稳态计算估算，排除音频处理、初始化、渲染与传输，非端到端实测。H=16训练单L40S约63小时／15万步，不含VAE预训练。仅评SAM；30.13秒多事件与G1追踪主要为定性仿真，未证明真实机器人实时闭环。No-SSL仍需训练几何监督，FID 11.917，也不是完全无空间知识。[计时附录](https://arxiv.org/html/2610.13300v1#A3) · [No-SSL](https://arxiv.org/html/2610.13300v1#A4) · [训练设置](https://arxiv.org/html/2610.13300v1#A5)

解耦条件的消融也支持这个解释：合并what／where时Online FID为11.445，分开后8.714；但这不证明在所有多模态任务都应分token。主表Online的检索置信区间与MOSPA重叠，不能写成全面显著领先。计时的700步约93.3秒压力测试只支持该长度下吞吐，不能替代长动作质量评测；多事件连贯性主要依据30.13秒展示，应把两种证据分开。[表6](https://arxiv.org/html/2610.13300v1#S4.SS5) · [连续展示](https://arxiv.org/html/2610.13300v1#A2.SS2)

### 6）热度事实与可用性
固定榜第9，11赞、49浏览。alphaXiv详情与官方项目页本次均403，未取得可用demo证据；未获取足以解释热度来源的社区讨论或独立传播证据，不能据视频式题材推断传播原因。论文明确“接收后发布代码与模型”，本次未核到已可运行实现，未独立复现。[项目入口](https://jingchengni.com/sonic-amg/) · [发布声明](https://arxiv.org/html/2610.13300v1#S5.SSx2)

### 7）Agent／RAG／coding／MCP／全栈迁移
**B档：实时数字人优先，通用Agent读训练—部署一致性即可。** 在工具Agent中，每次动作后重取真实状态，别把理想计划当环境事实；RAG证据应绑定当前实体／版本，避免历史条件漂移。全栈流式应用同时量首个可用输出、稳态吞吐、P95及前端处理，别用GPU生成时间代替用户延迟。门槛是音频同步、坐标系、初始姿态和风格输入；论文没有coding、RAG或MCP性能实验，这些只是结构迁移。

## #10｜MagicBeanStalk: Escaping the RLVR Zero Advantage Trap with Recursive Data Synthesis

### 1）作者、领域、版本与阅读范围
Ximing Lu、Aviral Kumar、Jan Kautz、Yejin Choi、David Acuna；UW、CMU、NVIDIA、Stanford。领域为可验证奖励RL与数据合成；2026-10-08 19:25:48 UTC / 北京10月9日03:25:48首发，当前v1。已读摘要、§1–4/6、表1–10、附录B–D/G，目视图2两面板。alphaXiv单篇未成功取得，榜单身份来自已核首页，下面论证以arXiv全文为准。[arXiv](https://arxiv.org/abs/2610.12659) · [alphaXiv入口](https://www.alphaxiv.org/abs/2610.12659)

### 2）具体问题
组内相对奖励RL若同题采样全对或全错，优势为零。约78K数学题对gpt-oss-120b、32K预算、每题8次时，仅12.2%落在有对有错的区间。**“约88%”只属于该模型、预算和有限样本，不是证明这些题普遍无用或绝对学不会。**[§2与图2](https://arxiv.org/html/2610.12659v1#S2)

### 3）方法、数据流及baseline差异
教师先给难题产出可核答案与解题轨迹，再分解成至多3个子题；通过“加入子题范例能否改善学生解父题”的有效性测试，最多递归3层。随后从叶子造较难变体、向上重新组合，每步核答案；最终用目标模型筛选8次中1–7次正确，且至少一次正确解正常结束于预算内。直接改写难题的baseline没有这套分解和重组约束。[§3](https://arxiv.org/html/2610.12659v1#S3)

金融题把文档视作输入的一部分，在新文档片段上重新落地整棵题树；不能把原文档事实偷带到新题。[附录D](https://arxiv.org/html/2610.12659v1#A4)

### 4）创新点与判断
作者贡献是把难题的推理操作作为合成目标，结合有效性测试、递归组合和目标模型预算校准。我的判断：价值不在“多造题”，而在区分语义正确、真正新颖、难度适中；学生分解测试通过也不能代替最终目标模型筛选。各轮重测有必要，模型成长后同一题会变陈旧。

### 5）实验、消融、算力与限制
16K推理下八数学集均分：gpt-oss61.2→69.8，Goldilocks筛选源题67.0，直接合成66.8；DeepSeek72.4→77.9，论文报未舍入增益5.4。约1,250个难种子的有效后代覆盖74.7%对43.8%。64种子构造预算对照中，直接采样16.0M token、MBS14.3M，同时满足保结构/新颖/适中者13对28个种子，较纯比较题量更有说服力。[表1](https://arxiv.org/html/2610.12659v1#S3.T1) · [附录C表7](https://arxiv.org/html/2610.12659v1#A3)

gpt-oss训练用16×H100，DeepSeek用80×H100；数据集规模、生成成本未完整匹配，Golden Goose未按目标模型重筛，API参照采样数亦不同。质量抽查150数学题有8%被三评审一致否定，不能称全自动真值无误。金融340种子得14.2K题，SecQue32.4→39.3、FinanceBench65.9→68.3，只有基准收益，未证明真实金融决策可靠。本次无独立复现。[§4](https://arxiv.org/html/2610.12659v1#S4)

### 6）热度与发布状态
固定首页第10，24赞、53浏览。未获取足以解释热度来源的社区讨论或独立传播证据，不能据此判断社区共识。“数据多但无训练信号”可能具传播力，只是推测。

论文说数据将在接收后发布；本次未核到官方代码、数据下载或可用demo。依赖持续变化的教师API也使重新合成难以精确复现，不能当即插即用开源项目。[复现声明](https://arxiv.org/html/2610.12659v1#S6.SSx2)

### 7）工程迁移与门槛
**A档数据方法，B档近期落地。** RAG可从有证据的失败问答拆出缺失操作，再换新文档构造题，但必须保留支持片段、正确答案和冲突检查；coding可从失败测试分解成可执行子任务。MCP和全栈需可靠终态验证、隔离执行与预算统计。先做小规模合成质量/成本审计，再考虑RL；论文没有直接评估软件Agent或MCP，这些都是迁移假设。

## A．今天最值得额外深读的三篇

选择标准是对Agent、RAG、coding、MCP和全栈工程的可迁移性、证据清晰度及今天的新阅读价值，不是重排alphaXiv热榜。

### 1. CoTrace：先让训练记录对应真实运行框架
- **为什么读：** 同一模型换prompt、工具协议、恢复策略，学习过的轨迹可能不再可用。它比“把所有成功轨迹丢进训练”更接近真实Agent工程问题
- **先看：** [§2数据接口](https://arxiv.org/html/2610.10426v1#S2)→[§4.3跨框架迁移](https://arxiv.org/html/2610.10426v1#S4.SS3)→[E.5配对统计](https://arxiv.org/html/2610.10426v1#A5.SS5)→[F.2提交路径故障](https://arxiv.org/html/2610.10426v1#A6.SS2)。78→88/90不能被写成独立测试集提升；F.2中丢失提交说明导致的零奖励，也不能先解释成模型能力上限
- **代码状态：** 原文称发布接受的配置，但本次未取得可验证的官方仓库/下载地址；因此先从论文算法1与轨迹字段开始，不虚构代码链接，也不称已能按作者脚本复现
- **最小迁移实验：** 固定模型、任务和总预算，对比“混合多个harness的成功轨迹”与“仅保留当前部署harness的验真轨迹”；用从不参与晋升的测试集，记录正确率、工具参数错误、恢复率和token/时间成本

### 2. Thinking Inertia：简答开关不能替代输出验收
- **为什么读：** 适用于路由、JSON/工具参数、结构化RAG输出等现有系统，能先改善评测而无需训练新模型
- **先看：** [§2.3三层指标](https://arxiv.org/html/2610.11765v1#S2.SS3)→[§3.5同题答案空间实验](https://arxiv.org/html/2610.11765v1#S3.SS5)→[附录B解码口径](https://arxiv.org/html/2610.11765v1#A2)
- **代码入口：** [响应分解与汇总](https://github.com/thinking-inertia/code/blob/8f8f1cddcea6560df672fb70e83f013ce9f530e3/src/thinking_inertia/eval_thinking_spectrum.py)、[答案评分](https://github.com/thinking-inertia/code/blob/8f8f1cddcea6560df672fb70e83f013ce9f530e3/src/thinking_inertia/benchmark_scorers.py)
- **最小迁移实验：** 原生off与严格简答各跑同一小批真实请求，拆报正确率、完整输出格式合法率、重试、真实账单及P95；不使用“可见文本变短”替代“实际计算变少”

### 3. ReplaySSM：让吞吐收益和部署前提同时出现
- **为什么读：** 有自己的混合SSM服务时，状态表示的改动能同时影响带宽、回滚和误差累积；单会话API用户则主要适合了解边界
- **先看：** [§4–6机制](https://arxiv.org/html/2610.13778v1#S4)→[表6批量敏感性](https://arxiv.org/html/2610.13778v1#A5.SS2)→[表2精度代价](https://arxiv.org/html/2610.13778v1#S7.SS4)
- **代码入口：** [标准解码kernel](https://github.com/Johnny-Liou/ReplaySSM/blob/5d3ea597d479ef0c8e9e2eb2845a2adfdb9a8b44/vllm/model_executor/layers/mamba/ops/selective_state_update_replayssm_output_only.py)、[计时脚本](https://github.com/Johnny-Liou/ReplaySSM/blob/5d3ea597d479ef0c8e9e2eb2845a2adfdb9a8b44/benchmarks/replayssm/e2e_decode_speedup.py)、[低精度未接dispatch的限制](https://github.com/Johnny-Liou/ReplaySSM/blob/5d3ea597d479ef0c8e9e2eb2845a2adfdb9a8b44/low_precision/README.md)
- **最小迁移实验：** 固定权重/状态精度/功耗，用真实batch与长度分布测吞吐、尾延迟、正确性和显存；B=1不应预设有收益

## B．由今天榜单支持的五条技术线索

以下是对这10篇的综合分析，不是对整个AI领域的统计趋势，也不把不同论文的数字相加。

1. **Agent改进越来越依赖版本化接口和验收契约。** CoTrace强调运行框架兼容，MASS强调产物/工作流监督，ETM强调显式状态和回归。对应用工程，更值得积累的是带来源、适用接口、失败条件和验收证据的轨迹，不只是成功对话文本
2. **“递归自我改进”需要拆成具体更新路径。** RSI-Anything的不同任务分别支持政策、世界模型或工作流更新，MASS展示有限轮数，MagicBeanStalk更新训练题目分布。它们不是同一个闭环，也没有共同证明无限、稳定、全能力递归提升
3. **减少冗余计算必须说明在哪一层省。** ReplaySSM省状态流量但小batch不占优；Thinking Inertia改变可见输出但不证明隐藏推理成本下降；Sonic-AMG的模型生成/缓冲延迟不能代表包含编码与渲染的用户首响。产品应单列模型、工具、排队、网络和后处理
4. **生成产物需要独立的可用性检验。** Articulated 3D工作把视觉、运动和物理有效性分开，ETM显示状态质量影响控制，CoTrace显示轨迹成功也可能依赖特定harness。对coding和RAG，应分别验执行结果、需求遵从、引用证据和副作用，而不是只看一个judge总分
5. **理论界、仿真分数、公开源码是三种证据。** KL论文证明分布关系却没有真实Agent收益实验；机器人/音频仿真成绩仍受场景和算力约束；有代码也可能缺权重、数据、端到端路径或精确历史配置。使用时分别问“定理条件成立吗”“测试对应目标负载吗”“下载资源能复现哪一段”

## C．与昨天真实报告的对比

### 对比基线与不能计算的变化

本次实际读取[2026-10-12真实报告](https://github.com/DanielMax937/daily-research-reports/blob/main/2026-10-12/ai-papers.md)，GitHub返回内容blob SHA为`922079a8397bd384cd10a29839e5b9720e4868b8`。昨天报告明确自认“公开首页10篇展示样本，不是已确认的Hot前10”，采集约03:13 UTC；不能把它内部引用的10月11日Hot名次误认成10月12日名次。

**今天建立了可核Hot / 30 Days基线，昨天缺同口径榜单，因此不能计算一天榜位升降、留榜率、新入榜或跌出榜。** 可以比较报告覆盖和已核论文版本：

- 两天重复覆盖：ETM、MASS；今天分别为Hot第3、第8。昨天是展示样本第1、第2，这两个编号没有可比较的排名含义
- 今天新增覆盖8篇：RSI-Anything、Thinking Inertia、ReplaySSM、Universal KL Bounds、CoTrace、Articulated 3D Assets、Sonic-AMG、MagicBeanStalk。它们均早于今天首发，不能叫10月13日八篇新论文
- 昨天另8篇没有进入今天冻结的Hot前10。其中同一响应后续位置可核：NCM第13、Balanced Data Diet第14、BrickBench第15、MiMo第16；Data Wall、H-JEPA、Long-WAM、AgentGarten未出现于本次返回的前20，不能据此断言在全站无热度或论文下线
- 今天前10的arXiv版本历史均只有v1；“alphaXiv条目修改时间”并非arXiv修订时间，不用它伪造v2。没有逐篇重算昨天PDF字节，因此不声称跨日文件完全相同

### 连续论文的真正新增信息

| 论文 | 昨日证据 | 今日新核或仍然成立的边界 | 版本/排名结论 |
|---|---|---|---|
| ETM | v1；官方项目页当次不可读，完整库状态未知 | 今日项目页可读，Code区是页内伪代码展示；未核到完整策略库发布；作者HF澄清仍是旧讨论 | 未见新arXiv版本或新增实验；不能计算昨日→今日榜位变化 |
| MASS | v1；已固定10月9日代码SHA；README与论文MLR口径不同，公开覆盖有缺项 | 本次README、复现说明、覆盖清单三个main文件与昨日固定SHA逐字节相同；提交历史访问受限，不能外推整个仓库无更新；复现缺口未见关闭证据 | 未见新arXiv版本；未核到可确认的新实验/新讨论；排名变化不可算 |

ETM与MASS的背景因此压缩，重点保留新增可访问材料、版本状态和未关闭缺口。今天没有证据把它们包装成一次新发布，也没有证据说“热度上升由某个新实验造成”。

### 榜外材料的处理

今天未另增未经完整核验的“重要新论文”来填榜。上文第13–16位仅用于保留同一响应的跨日覆盖证据，不替换前10，不提供未做的全文评价；昨天NCM等欠项也不因今天有排名就自动补齐。

## 证据留存与阅读边界

### 可供后续报告复核的榜单记录

源URL：[https://www.alphaxiv.org/](https://www.alphaxiv.org/)。本次公开HTML字节SHA-256为`b01c341068a8844fe7485809a7e9a0f90e5723720c0a8b1f7fae08f5cf8e044c`。公开页面中关键字段如下；将其留在报告里，是为了之后区分不同筛选/缓存快照，而不是推定网站算法已公开。

```json
{
  "listName": "Trending Papers",
  "numberOfItems": 20,
  "query": {
    "sort": "Hot",
    "interval": "30 Days",
    "categories": [],
    "subcategoryLabels": [],
    "customCategoryLabels": []
  },
  "dataUpdatedAt": 1791863023338,
  "dehydratedAt": 1791863023353,
  "top10": [
    "2610.13912", "2610.11765", "2610.12369", "2610.13778", "2610.12851",
    "2610.10426", "2610.13947", "2610.12176", "2610.13300", "2610.12659"
  ]
}
```

### 明确保留的缺口

- 排序算法的权重与所有互动的精确入库时间未公开核实；本报告只证明该响应的Hot顺序，不宣称了解其因果来源
- 单篇alphaXiv访问并非全部成功；没有把无法访问的评论写成“社区观点”，没有拿搜索摘要冒充原文
- 所有10篇均获得版本化arXiv正文，实际精读范围、重点表图和源码核查分别列在各节；没有宣称逐页视觉审阅所有PDF、逐行审计全部源码或重跑所有实验
- 数字归属于各论文/作者材料，独立复现为零；不同任务、模型、预算、随机种子和统计分母不混合。未报告的置信区间、算力、消融或硬件条件不补造
- Agent/RAG/coding/MCP/全栈迁移建议是工程分析，除明确引用原实验外，尚未由这些论文直接验证

### 补充阅读与源码复核记录

- RSI-Anything：目视原文图2–3；读world.py、semantic_world.py关键编码/读出函数，evaluation.py候选排序和optimizer_steps检查，及validation.json。代码包自述短训练验证不等于全量重训；原文与README图号不完全一致，本报引用采用arXiv图号
- CoTrace：目视附录图6；原文全文可读，官方实现入口未核实。MagicBeanStalk：目视图2两面板，附录表格由HTML单元格核读；未核到已公开可运行代码/数据
- MASS：目视图1；读pipeline.py的rank/select/best_checkpoint、prepare_sft_data.py的重放与assistant掩码、iterate_multi_agent_prompt.py的冠军仲裁。当前README/复现说明/覆盖清单与昨日fb40358版本内容相同，三文件SHA-256分别为d16a1d83edbff0c75d8562d28a438a1713d99452159b8e835e6484cd3a5f998d、1279417cb6a28dc924e2ac495c89bc12bb14560e4fd34eb7ae0ccdde307e3363、2be6b35201259d2e60fc9be1be21891898e2be71fae54129aea015655e8a5198。比对不覆盖其他文件
- ETM：PDF共31页，实际目视第6/10页的图3与表2，正文和图注覆盖详见本篇；PDF SHA-256为bc96bd7de710f593b49a703d66d54515030000d7beef75a5e4d007524618f4e7。昨日无对应PDF哈希，不做字节级跨日结论
- Artisan：PDF共39页，目视第4/8/28页的图2/4及表2/11；PDF SHA-256为049e25d57a70199c0d8c87a0556d14ccc9b04b30c3b7a44556f525da0a3e5f1e。静态阅读README、配置、run.sh、benchmark/run.py、SDK契约及两项evaluate入口；未声称读完全部评测内核。GitHub提交API受限，main链接代表本次读取状态，未固定全仓commit
- [Artisan-Benchmark数据](https://huggingface.co/datasets/mastercai/Artisan-Benchmark)：公开、非gated元信息可核，清单2,083项，版本SHA 17d219e8abea0a5489e2280bf713748aa1e0f6b9，lastModified为2026-10-11T11:28:31Z；未下载或验收全部资产
- Sonic-AMG：PDF共23页，目视第4/9页的图2/5与表3/4，其余重点表图按正文/图注核查；PDF SHA-256为1e9be67c7964e18e4484c841a15a7bd5572871e7eb723fa2ea6c43a3c1b26789。官网403未绕行，代码/模型发布仍以原文声明为准
- Thinking Inertia、ReplaySSM、Universal KL Bounds：采用版本化HTML读取方法、实验和结论，关键表图编号已列在各篇。没有另做全篇PDF视觉检查；前两篇关键实现为静态代码阅读，KL论文未核到作者仓库

研究与代码状态核验截至2026-10-13约12:02 BJT / 04:02 UTC；榜单位次与计数始终冻结于11:48 BJT取得的那份响应，未随阅读过程重排。
