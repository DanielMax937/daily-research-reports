# 2026-10-17 AI论文日报：热榜未核实，三篇榜外补充深读

## 结论、抓取窗口与证据边界

- 报告所属日期：北京时间2026年10月17日；本次研究从11:49开始，以下网页、版本和代码状态为本次抓取快照。
- **未获得可验证的当天alphaXiv Trending/Popular/Hot完整前十及筛选时间窗口。** 11:49访问[alphaXiv首页](https://www.alphaxiv.org/)可读，但没有可核的排序控制和窗口。随后访问[Hot入口](https://www.alphaxiv.org/?sort=Hot)返回403；没有绕过拒绝，也没有把默认流、搜索摘要或昨日缓存充作热榜。
- 单篇详情确实显示AutoSFT“#5 on Trending”、Terminal-RSI“#8 on Trending”、Librarian Agents“#19 on Trending”。这只能记录为当次详情徽章，不证明完整榜单及窗口，更不将下列阅读顺序包装成排名。
- 下列是**榜外补充研究**，意为在完整榜单未获核实情况下独立选择的近期论文，不表示确认它们没有上榜。三篇均已读固定v1全文的方法、实验与限制；全部是北京时间10月16日首次提交，不是10月17日新发表。
- 数值均来自作者原文或公开代码记录，**没有独立训练、执行未知源码或复现实验**。原文可读与结论可靠、代码存在与可运行是不同证据层级。
- 直接检查了AutoSFT图1、Terminal-RSI图2以及Librarian成本归一化曲线的原图；其余图表以原文正文、表格与图注核对，不宣称全部图像逐项审阅。

## 榜外补充一：Librarian Agents

### 1. 基本信息与实际阅读范围

- 完整标题：**Librarian Agents: Training LLMs to Curate Long-Context Workspaces that Anticipate Future Queries**。
- 作者：Anikait Singh、Teresa Zhang、Yoonho Lee、Roshen Sanjay Nair、Aviral Kumar、Chelsea Finn。
- arXiv：2610.22273v1，初版2026-10-15 17:35:17 UTC，即北京时间10月16日01:35:17；本次版本历史只见v1，未见修订。
- 领域：Agent / RAG / Memory / Context Engineering / RL。
- 原始来源：[版本与日期](https://arxiv.org/abs/2610.22273v1)、[HTML全文](https://arxiv.org/html/2610.22273v1)、[alphaXiv详情](https://www.alphaxiv.org/abs/2610.22273)、[作者项目](https://librarian-agents.github.io/)。
- 已读摘要、引言、§2.1–2.4方法及正文实验、§3–4、附录A.2–A.9中评测/成本/结构消融/训练配置/工具与提示；不是仅依赖alphaXiv自动综述。
- 代码固定于[27c9d86391b5da9c04e88b920076fa3867782bb9](https://github.com/teresaz05/librarian-agents/tree/27c9d86391b5da9c04e88b920076fa3867782bb9)，该提交时间2026-10-16 19:01:10 UTC，北京时间10月17日03:01:10。

### 2. 问题与瓶颈

跨文档问题会重复支付查找关系的成本。普通检索逐问题工作，固定图谱/摘要树又预设了组织形式。本文让builder在未来问题到来前构造可复用工作空间，优化目标由后续answerer回答质量提供。它不是取消检索，而是学习检索前的知识组织。[§1–2](https://arxiv.org/html/2610.22273v1#S2)

### 3. Method：从原始文档到回答

1. 输入是一组原始文档；builder不看评测问题。状态包括原文、合成文件、层级和来源关系。
2. 四类操作为CreateFile、MergeFiles、Delete、Stop。合成文件保留来源；Delete只移除活跃合成节点，不删除原文。固定内容executor负责生成文件正文，builder学习选什么、怎么组织，而非同时训练所有生成组件。
3. 固定answerer浏览构造结果。训练阶段每8个builder回合探测一次answerability，最多4次，结合变化量和最终正确性训练builder。主实验GRPO、γ=1，**构造成本/导航成本/结构奖励权重均为0**；不能把一般目标里的成本项说成实际优化过。
4. 配置为Qwen3.5-4B builder、rank-32 LoRA、batch 8、group 4、最多32回合/60,000轨迹token；固定Qwen3.5-35B-A3B做内容生成，Gemini 3.1 Flash Lite压缩历史。[附录A.7](https://arxiv.org/html/2610.22273v1#A1.SS7)
5. 与RAG、reranker、late interaction、GraphRAG、Agentic RAG、AutoCompaction及未RL builder比较。answerer冻结能隔离回答模型变化，但不同方法实际消耗仍不同，不等于严格等计算比较。

### 4. 亮点与代码核验

- 亮点一是把长期可复用的外部工作空间作为策略学习输出，而非只训练最终答案。
- 亮点二是内容不变的flatten/shuffle干预，能够更具体地问层级组织究竟贡献什么；它并未证明层级越复杂越好。
- [workspace.py](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/environments/synthetic_fs/workspace.py)已定向读取快照与create/merge/delete/materialize：快照含源路径、节点ID、parent、活跃状态；加载检查重复/隐藏来源/父节点，merge重挂子节点，delete标inactive且删除摘要时提升子节点，不等价于擦除原始材料。
- **重要落差**：[训练入口](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/scripts/train_browsecomp_plus.sh)显式使用`synthetic_only`；[复用推理实现](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/experiments/inference/browsecomp_hierarchy_ablation.py)同样固定该模式。materialize只有`synthetic_plus_raw`才复制原文；[reward.py](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/environments/synthetic_fs/reward.py)另有基于已读合成文件provenance开放原文的分支。因此源码支持回源设计，但**不能推断所有主实验实际启用了回源**。这是复现时应逐协议核对的差别，不据此判整篇无效。

### 5. 实验、消融与成本判断

- BrowseComp-Plus：680训练任务、50留出任务，失败构建仍进分母。正文图4中Qwen answerer为0.75，对最强baseline 0.44；Gemini为0.77，对0.42。“33个百分点”是两组差值平均，并非每个设置恰好提高33。[正文实验](https://arxiv.org/html/2610.22273v1#S2.SS4)
- BRIGHT将检索问题转换为生成问答，150题、3领域各50题、每题4次回答，宏平均pass@1为52.0%，Dense为20.8%；pass@3由4次采样估计，不是一次结果。不是全BRIGHT原始检索指标，也不是无边界跨域保证。[表3、附录A.2](https://arxiv.org/html/2610.22273v1#A1.SS2)
- 结构消融是另一个49语料/435扩展问题协议：原结构55.86%/3,635导航token，flatten后57.70%/5,497，shuffle后51.72%/3,612。支持层级影响导航与语义放置有用，但flatten准确率没有下降；不能宣称层级本身解释全部主结果。[表7](https://arxiv.org/html/2610.22273v1#A1.SS5)
- 443问题复用实验中RL答题消耗9,346 token/题，base为1,238；准确率0.637 vs 0.242。十次复用时“每个预期正确答案”的token比0.662，95%区间[0.504,0.836]，而交叉点约31次[18,54]。**此后base在这个归一化口径更便宜，不是复用越多RL相对优势越大。** 原始每题token始终更高；曲线仅记token，不是墙钟、美元或全训练成本。[附录A.4与原图](https://arxiv.org/html/2610.22273v1/browsecomp_tokens_per_expected_correct.png)
- [REPRODUCING.md](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/REPRODUCING.md)进一步区分178,926 token的跨answerer构造协议与复用协议147,634 token；后者20题摊销约16.8K，不能将前者代入后者说成同一实测。
- 我的判断：证据对固定语料上的回答准确率最强，对一般省钱、省时和动态企业知识库尚弱。小测试集、合成扩展问题、LLM judge、不同checkpoint及多服务成本需另审；没有独立复现。

### 6. 热度证据

11:49详情显示#19 Trending、2个未标明语义的计数；窗口未核。读到Discussion入口不等于读到研究者讨论，本次没有足够原始讨论或传播时间序列解释为什么“今天热”。仅可确认近期论文和代码快照存在。

### 7. 工程价值与门槛

对RAG/全栈Agent最值得先借鉴的是“原文不可变、派生文件可替换、来源可追溯、快照可复用”。MCP可承载受限文件工具，但论文没有直接验证MCP效果。产品应另测增量更新、撤回资料、访问控制继承、过期摘要与注入风险，本文未覆盖这些部署保证。

代码README要求Python≥3.11；训练依赖Tinker、Gemini及Qwen executor服务，baseline生成还需CUDA。CHECKPOINTS只给步55/89与环境变量映射，未在已读材料中给出可直接下载的权重链接。因此“代码开放”不等于一条命令可从零复现。最便宜的第一步是离线审查记录与结构消融设计；随后在授权的测试语料上比较dense、手工摘要和学习构造，分别记准确率、构造token、导航token和实际费用。

## 榜外补充二：AutoSFT

### 1. 基本信息与阅读范围

- 完整标题：**AutoSFT: An Agentic System for Automated Data Research in Supervised Fine-Tuning**。
- 作者：Bingxiang He、Pengqi Sun、Shihao Peng、Shaoxuan Li、Huiyu Xiao、Hongjian Shi、Zixuan Fu、Ziqing Qiao、Yuxin Zuo、Cheng Qian、Xinqiang Yu、Jiayi Li、Xiusi Chen、Yizhen Song、Xiangyang Wang、Iofai Lei、Yudong Wang、Ning Ding、Zhiyuan Liu、Xiaozhi Wang、Chaojun Xiao。
- 2610.22194v1，初版2026-10-15 16:44:34 UTC，北京时间10月16日00:44:34；版本历史未见修订。
- 领域：Agent / Automated Research / SFT / Data Engineering / Coding。
- [arXiv日期](https://arxiv.org/abs/2610.22194v1)、[全文](https://arxiv.org/html/2610.22194v1)、[alphaXiv](https://www.alphaxiv.org/abs/2610.22194)。已读摘要、引言、§2–5、结论、附录B的角色/验证设计及C–E实验与限制；图1原图已检查。

### 2. 问题与瓶颈

让一个研究Agent同时提方案、跑训练、读日志，容易将研究空间缩成反复调整类别配比。单Agent试验33轮中32轮完成评测，最佳在第9轮，后23轮无改善。作者将执行上下文污染与提案缺少视角视为设计动机，但观察停滞不能单独证明上下文压缩是因果。[§3](https://arxiv.org/html/2610.22194v1#S3)

### 3. 核心方法与数据流

- 固定基础checkpoint、trainer和每轮token预算，**每轮从基础模型重新训练**。持续状态是数据池、recipe和研究记录，不是将上一轮权重不断续训。
- Meta选择recipe；独立executor提交训练、转换checkpoint、评测，只返回路径与状态。四个analysis视角分别看训练数据、失败例、学习动态、历史，每个提一项带证据的操作；meta决定是否采用。
- Synthesis检查池中欠缺能力，生成候选，经程序验证、独立语义检查、抽检和n-gram去污染后入池。入池不等于下一轮一定使用。[§4与图1](https://arxiv.org/html/2610.22194v1#S4)
- 六类事后标注动作：mixture、pruning、repair、resupervision、synthesis、ordering。并非强制每轮走六种schema；ordering在实际对比中没有变化，因为训练shuffle seed固定。
- 与基线差异是研究控制组织方式，不是新的SFT优化器；推理时仍用所选微调模型。Agent动作多样性是解释候选，不是被独立证明的唯一因果中介。

### 4. 主要亮点

1. 将研究选择与运行日志隔离，反馈保留可按需读取的artifact，而不是把所有输出塞回决策上下文。
2. 补充视角可以改变真实数据操作类型，不只让同一种重加权得到更长解释。
3. 合成数据以能力缺口与验证为入口；并报告无法提升的能力，避免“更多合成总有效”。

[附录B](https://arxiv.org/html/2610.22194v1#A2)给出角色权限：analysis只提案，不改共享数据池；executor执行固定评测合约。可用于工程设计，但本次代码仓库只有占位README，不能说这些边界已经源码强制实现。[固定README](https://github.com/Thinking-Space/AutoSFT/blob/7c4403a3b36949b836b9b9266eb29e22320d58ac/README.md)

### 5. 实验、预算与未证明部分

- Executor对比同11.5小时快照，meta压缩次数10→5；这测上下文事件，不等于总API费减半。[§5.1](https://arxiv.org/html/2610.22194v1#S5.SS1)
- Analysis对比3M-token、三epoch：第30轮67.10，base前30轮最好60.60，差6.50个百分点；base跑50轮最好62.35。avg@10是同checkpoint十次评测，不是十次独立研究搜索。[§5.2/图8](https://arxiv.org/html/2610.22194v1#S5.SS2)
- Synthesis用100M-token上限：IFEval最好81.58 vs78.15，IFBench51.95 vs49.02。不能把这个实验与3M分析实验直接合并成一条增益曲线。repeat_prompt约40%→75.6%，而odd_even_syllables三轮合成仍0。[§5.3/图9、15](https://arxiv.org/html/2610.22194v1#S5.SS3)
- 代码域742,842个Python指令—代码样本、Qwen3-1.7B-Base、100M-token/三epoch、avg@3；64小时中Base/Analysis各15轮，加入Synthesis仅6轮。Analysis第13轮64.8%，Synthesis第6轮65.8%；轮数轴不能代表相同时间或API成本。[§5.4](https://arxiv.org/html/2610.22194v1#S5.SS4)
- 附录D列训练8×H800、评测1×H800，研究agent GPT-5.5 medium，生成DeepSeek V4 Flash；估算20轮约130 GPU小时和1,900美元API费。**文本又写每轮训练约0.8“GPU-hours on 8 GPUs”**，与总额口径含混；若按0.8墙钟小时×8卡并加0.15评测GPU小时，20轮才约131。报告保留作者估算，不将该单位矛盾自行改成确定事实。[资源段](https://arxiv.org/html/2610.22194v1#A4)
- 作者承认每配置只跑一次搜索、单一1.7B基础模型、代码迁移仅一个额外领域。重复解码评测不覆盖搜索间方差；持续看benchmark反馈也应在产品试验中配独立最终留出集。我的判断是结构设计值得试验，不能直接承诺多Agent必然更优或更便宜。

### 6. 热度与发布证据

详情快照显示#5 Trending、145 views；无已核窗口或增长序列。不能由单次计数归因于社区共识。作者仓库固定提交7c4403a3…为初始化，README仅“Source code coming soon.”，本次没有实际训练源码可读。

### 7. 工程价值

适合有自动评测与反复SFT需求的团队。更普遍的启发是让执行器返回小型状态/产物路径、让不同分析器独立读证据、由单一决策者提交变更。可先在自己的coding/RAG评测数据上做“单Agent vs隔离执行 vs增加分析视角”受控对照，而不立刻购买多卡训练预算。MCP只是可能的工具接口，论文没有MCP特定实验；源码未发布，当前应视为设计论文而非可直接集成框架。

## 榜外补充三：Terminal-RSI

### 1. 基本信息与阅读范围

- 完整标题：**Terminal-RSI: Recursive Self-Improving Terminal Agents via Recursive Self-Rewrite and Policy-Refine**。
- 作者：Junyao Yang、Zongxia Li、Yucheng Shi、Zhongzhi Li、Ruhan Wang、Ruiwen Zhou、Haitao Mi、Shuicheng Yan、Leowei Liang。
- 2610.22192v1，初版2026-10-15 16:43:56 UTC，北京时间10月16日00:43:56；版本历史未见修订。
- 领域：Coding Agent / Terminal Agent / RL / Verification。
- [arXiv](https://arxiv.org/abs/2610.22192v1)、[全文](https://arxiv.org/html/2610.22192v1)、[alphaXiv](https://www.alphaxiv.org/abs/2610.22192)、[作者项目](https://jyyang26.github.io/terminal-rsi/)。已读摘要、§1–5、附录A/B/E/F关键协议、H中Rust–C案例细节；图2原图检查。TB-GAE公式与适用假设已读，但未独立复核全部数学推导。

### 2. 问题与瓶颈

终端Agent需要真正改变环境并通过完整验证。局部检查通过多不等于任务成功；长日志改变token链长度会扭曲credit assignment；SFT更新actor后旧critic可能失准。本文将三个问题合入交替训练流程，而不是将一次成功的自然语言总结直接当能力进步。

### 3. 核心方法

1. RSR从多个harness的成功轨迹产生runbook，审查泄漏/兼容性后在目标harness重新执行，仅保留新执行成功的公共交互做actor-only SFT；私有runbook与review对话移除。
2. RSR期间critic不更新；第一轮以冻结actor的一整个SWR epoch准备critic，每轮RPR前另做4次critic-only校准，再联合PPO。第二轮继承前一轮critic，actor学习率5e-7→1e-7，critic仍1.5e-5。
3. FDR按任务家族校准部分检查分；SPR为严格成功S加P/(P+D′)，失败小于1、成功至少1。该界限不是最大化成功率的数学等价保证，也不证明梯度方差更低。
4. TB-GAE跳过observation递推节点，保留每个生成token自己的value baseline，仅跨交互回合折扣。**原文§2.4明确第一阶段实际用标准GAE、γ=λ=1；不能把设计/恒等式当已验证的独立在线增益。**[方法§2](https://arxiv.org/html/2610.22192v1#S2)
5. 使用Qwen3.8-27B、3,000训练任务（2,400语义验证+600补充）、slime/Megatron/SGLang/Harbor。最终评测单次输入最多96K、单回合输出8,192，32K累计后主动压缩；模型262K容量不等于每次评测实际输入262K。[§3.1、附录A](https://arxiv.org/html/2610.22192v1#S3.SS1)

### 4. 亮点及主张分级

- 值得研究的是成功轨迹重写、actor变化、critic保留与重新校准的明确交接；并非重新发明PPO或GAE。
- 将严格完成、过程分、验证器覆盖拆开报告很有用，尤其是作者主动披露通过测试仍没满足架构要求的例子。
- 整体流水线提升有证据；“critic继承导致提升”“TB-GAE导致提升”“递归在等成本下一定胜过直接PPO”仍未被单独隔离证明。

### 5. 实验可信度、消融和资源

- 表2最终TB4.0/2.1/3.0/Hard为19.84/86.52/16.95/79.00%；四suite等权均值20.68→50.58%。这是Mean@3，即三次评测算术均值，不是pass@3，也不是按总任务数加权。[表2/图5](https://arxiv.org/html/2610.22192v1#S3)
- 同本地step20，RPR-1在TB2.1为77.53，Direct PPO48.31。但前者已经花费发现轨迹和SFT成本，初始化与历史评测协议也不同，非等总算力比较。[§3.2、附录E](https://arxiv.org/html/2610.22192v1#S3.SS2)
- LHTB过程分0.21→0.37，严格完成条目0/46→5/46；不能据紧凑条目推断每次都成功同五题或解集嵌套。SWR100为3→6%，最后三个阶段均6%，存在平台。[§3.3、附录E](https://arxiv.org/html/2610.22192v1#S3.SS3)
- 对同4,352轨迹离线重打分，失败所得奖励份额50.09%→28.72%，得分≥1的失败158→0。它隔离了奖励分配，不是在线重训消融。SPR样本总体奖励标准差反而0.50→0.59，不可宣称所有方差都降低。[§3.4、附录B](https://arxiv.org/html/2610.22192v1#S3.SS4)
- 最终checkpoint之后继续训练会回退；改变学习率、奖励、初始化混在一起，仍缺等计算交替、critic reset对照、独立训练seed与独立TB-GAE对照。附录F还披露分层分析采用替代checkpoint且未完全对齐最终模型，不能混同主表。
- Rust–C案例中最终两阶段均通过两门检查，但一次最终模型通过Python计算表达式，C接口只是链接烟雾测试。**测试输出等价没有证明原生AST实现或完整需求达成。**[§3.5/附录H](https://arxiv.org/html/2610.22192v1#S3.SS5)
- 已读配置有27B、context parallel 4、全局batch256/oversample288、每GPU 8,192 token、critic训练等；没有核得完整硬件数量、总GPU小时或美元成本，不能用“18步/20步”包装低资源门槛。外部闭源模型分数协议未完全对齐，不据此称全面超越。

### 6. 热度与可用性

11:49详情显示#8 Trending、179 views；未核排序窗口、增量及原研究者讨论。作者项目明确“Code soon / Model soon”；论文链接的GitHub仓库读取404，Hugging Face入口此次不可访问。只判断本次没有可用代码/权重核验，不猜404原因，也不声称代码已开源可复现。

### 7. 工程价值

对coding agent可立即借鉴的是验收协议：任务完成必须由受保护外部验证器定义，局部检查分单列；再对测试未覆盖的架构、依赖、授权、安全边界做独立检查。对MCP工具链，工具成功返回不等于用户目标完成，属于本文机制带来的工程推论。训练方案门槛高，先在自己的任务收集“局部通过却整体失败”案例更实际；没有发布实现前不建议按营销数字替换生产模型。

## A. 今天最值得深入读的三篇

1. **Librarian Agents**：优先§2.3、附录A.4/A.5/A.7，配固定workspace.py和复用推理入口。最贴近RAG与上下文工程，能直接学到工作空间、来源与成本协议；重点核`synthetic_only`和回源设计的区别。
2. **AutoSFT**：优先§4、§5.2–5.4、附录D/E。对于Agent编排，执行隔离和独立分析视角比增派Agent数量更具体。当前只读设计，待实际源码发布再判断可集成程度。
3. **Terminal-RSI**：优先§2.2/2.4、§3.5、§5。最有价值的是严格完成与代理指标差别，以及通过测试但未实现架构的反例；不先追高成本训练。

这是三篇实际深读材料的工程阅读优先级，不是已核实热榜前十中的前三。

## B. 当日证据支持的三个局部信号

- **Agent产物正成为可优化对象。** Librarian优化外部工作空间，AutoSFT优化数据recipe，Terminal-RSI优化经验证轨迹与策略；都要求外部可评判反馈。三篇不够代表整个AI热榜。
- **预算与协议决定收益解释。** 每题token、每正确答案token、等回合、等墙钟、已花SFT成本是不同口径，不能交换。本文材料没有支持“更复杂系统普遍更省钱”。
- **状态与验收比叙述更重要。** 查询不可见、固定基础checkpoint、完整验证、来源路径和独立评测各自界定结论。公开代码还暴露模式与论文概念的差别，值得在集成前逐项核验。

## C. 与昨日真实变化

已实际读取[2026-10-16固定提交报告](https://github.com/DanielMax937/daily-research-reports/blob/b9d96b1fdd9f1ddbe4f9143a106148721a2033a9/2026-10-16/ai-papers.md)，文件blob SHA为`2d89f963815ed7ba4ac6f132f00c838281ce4872`。

- 昨日也是未核完整热榜，独立深读Priming、More Methods Better Agents、Scaling Discovery Requires Forgetting。今天没有两日可比排名，因此不能判断新进、连续热门、升降或降温。
- 今天新增覆盖上述三篇。它们是北京时间10月16日发布的近期工作，不称10月17日新论文；本次没有核得三篇的实质修订。
- 内容从昨日训练预算、搜索状态重置，延伸到预构造RAG工作空间、数据研究编排和终端任务验收。这是**报告覆盖变化**，不是热度趋势证据。
- 昨日三篇没有在本次重读并核到新版本或关键新实验，故不重复长篇总结，也不宣称它们“没有新变化”。
- 新的可复查工程事实：Librarian有实际代码快照与训练/评测脚本；AutoSFT只有占位README；Terminal项目明确代码/模型待发布。后续比较应沿本次固定版本/commit，不能拿今日main静态状态推断昨日状态。

## 证据目录、检查程度与尚缺项

### 原论文

- [AutoSFT v1全文](https://arxiv.org/html/2610.22194v1)：方法§2/4、实验§5、实现附录B、实验C、预算D、限制E；[已检查图1](https://arxiv.org/html/2610.22194v1/AutoSFT_V26.png)。
- [Terminal-RSI v1全文](https://arxiv.org/html/2610.22192v1)：方法§2、实验§3、结论§5、训练A、奖励B、协议E/F与H案例；[已检查图2](https://arxiv.org/html/2610.22192v1/terminal_rsi_overall_from_ppt.png)。
- [Librarian v1全文](https://arxiv.org/html/2610.22273v1)：正文§1–4，附录A.2–A.9指定内容；[已检查成本图](https://arxiv.org/html/2610.22273v1/browsecomp_tokens_per_expected_correct.png)。

### 固定代码读取范围

- Librarian commit `27c9d86391b5da9c04e88b920076fa3867782bb9`：README、REPRODUCING、CHECKPOINTS、environments两个README、训练/复用/层级消融三个脚本；workspace.py快照校验与create/merge/delete/materialize；reward.py回源与回答工作空间模式相关分支；browsecomp_hierarchy_ablation.py的工作空间模式。未将长文件全量审计或仓库测试执行冒充已完成。
- [复用脚本](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/scripts/evaluate_browsecomp_plus.sh)明确缺失快照记零；[层级消融脚本](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/scripts/evaluate_hierarchy_ablation.sh)先生成/验证变体再评估并bootstrap，未执行这些命令。
- AutoSFT commit `7c4403a3b36949b836b9b9266eb29e22320d58ac`仅占位README；Terminal源码不可核，不编造commit与代码路径。

### 保留的缺口

完整Top10、热榜筛选窗口、可比昨日名次、真实新增热度、原始讨论传播链、独立复现：全部未完成或未核实。报告以三篇原文与已发布代码的实际证据补充，不凑十篇，不用默认首页排序补榜。本文不包含私密账户资料或内部记录，只含公开研究来源与本次研究判断。
