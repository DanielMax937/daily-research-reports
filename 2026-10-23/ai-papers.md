# AI论文日报｜2026-10-23

## 抓取口径与阅读边界

- 报告所属日期：北京时间2026年10月23日。使用自己的云端浏览器实页核榜：**11:21:18–11:21:59 BJT（03:21:18–03:21:59 UTC）**；原文与源码补核及报告复核至11:37 BJT。
- [实际榜单](https://www.alphaxiv.org/?sort=Hot&interval=7+Days)：导航标签Trending、URL参数Hot、窗口7 Days，无领域或搜索过滤。为确认新界面的筛选，曾短暂查看Most Liked，随后明确点击Trending并读取其前10；**本文不采用Likes榜，也不把默认推荐流或搜索缓存称为今日榜单。**列表含研究者推荐栏，未将其计为论文。连续滚动确认第11篇Harness Scaling是边界，不列入前10。
- 初始页面懒加载只出现6篇和“无更多论文”，后续滚动加载第7–11，已排除把短暂加载状态当真实榜单结束。热度是7日平台排序，不是过去24小时论文发布时间或学术质量排名。平台未公开本次评分公式。
- **今日7篇新入、3篇连续。**新论文实际读原文方法/实验；连续论文依用户要求压缩背景，重核版本与可用入口，沿用昨日已读证据，不假装重新完成实验。所有性能数字均为作者报告，无独立复现、无未知代码运行、无机器人操作。
- 原文与代码有不同可访问性：LocaLeJEPA原文HTML404、网页PDF体积超限，改为直接读取下载的原PDF；Meta²网页文本工具403，正常云浏览器页面可读，并由其PDF首页链接取得官方项目PDF。没有绕过登录或权限屏障。Meta²未核到数字arXiv编号，明确用原项目PDF，不伪造编号。
- 所有传播原因都区分事实与推断；未获取可归因的X/HN/Reddit传播链。likes/views是页面当时显示值，缩写不还原精确数；未显示不当作0。

## 当天前10快照

|排名|论文|标识|likes|views|与昨日|
|---:|---|---|---:|---|---|
|1|SuperMimic|2610.28480|118|2k|1→1|
|2|Agentic World Action Models|2610.30136|44|535|新入|
|3|Learning the 4D World through Point Trajectory Forecasting|2610.28594|34|459|2→3|
|4|DONIC|2610.29997|7|102|新入|
|5|FrontierCS 2|2610.29932|6|未显示|新入|
|6|SP-HLM|2610.30044|7|未显示|新入|
|7|LocaLeJEPA|2610.28458|15|222|新入|
|8|Meta²|alphaXiv非数字slug，见第8节|32|265|新入|
|9|Sage-A1.5|2610.28578|34|352|4→9|
|10|Looking Ahead|2610.29989|9|未显示|新入|

“新入”只指相对昨天这个7日榜的前10，不等于今天首次发表。

## 1.SuperMimic

### 1. 基本信息与今日版本
Qiayuan Liao等，UC Berkeley。全题为SuperMimic: Scaling Humanoid Whole-Body Control with One Differentiable World Model。今日arXiv仍只列v1，首次提交2026-10-20 16:29:30 UTC，即北京10月21日00:29:30；没有核到v2。CoRL 2026 Oral仍为arXiv作者自述，未另核会议名单。[版本历史](https://arxiv.org/abs/2610.28480)

[alphaXiv入口](https://www.alphaxiv.org/abs/2610.28480)；领域：Robotics / RL / World Model。

### 2. 解决的问题
沿用昨日深读：大量动作共用身体动力学，是否能用一个可微世界模型分摊训练成本，而不是为动作库持续堆砌无模型强化学习算力？

### 3. 核心方法
仿真采样进入滚动数据池；世界模型拟合动力学；策略通过短时域想象rollout的反向传播学习，critic补足远期回报。世界模型和策略交替更新，并非预训练后永久冻结；不对物理仿真器本身求导。[当前项目方法及FAQ](https://supermimic.github.io/)

### 4. 亮点
仍是“共享代理动力学+解析梯度+真实仿真持续校正”的优化路线。比headline更值得复查的是同世界模型下BPTT与PPO的受控比较。

### 5. 实验结论及限制
昨日已核：1 H100×3小时超过SONIC的0.90 normalized return；129,514动作中失败25，2 GPU×9.8小时为0。今日项目仍展示相同结果，并明确这批动作是训练动作覆盖，不是未见动作泛化。硬件、数据规模与终止条件差异仍须保留；实机翻滚展示不等于重复成功率统计。全部数字是作者报告，未独立复现。[项目结果与评价脚注](https://supermimic.github.io/)

### 6. 今日热度增量
第1→第1；likes 30→118，增加88；views 632→页面显示2k。2k是平台缩写，不能还原精确浏览增量或增长百分比。互动增加可确认，但本次没有社交来源或转发链，不能把增长归因于某位作者、活动或特定视频。

### 7. 今日可用性与工程判断
今日项目导航仍主要是论文、视频和网页演示，没有核到可验证训练仓库链接。结论只能是“这次仍未找到官方训练代码入口”，不是“代码绝对未发布”或“相对昨日没有代码变化”。未启动网页demo。优先做同硬件、奖励、数据下的小规模BPTT/PPO复验；训练覆盖率与实机安全需另测。相比昨日没有确认改变工程判断的新论文证据。

## 2.Agentic World Action Models（AW-0）

### 1. 基本信息
作者Zhuoyang Liu、Dantong Niu、Botong Zhang、Boning Shao等，来自UC Berkeley、NVIDIA、University of Pennsylvania。核到版本arXiv:2610.30136v1，2026-10-21。题名中的agentic不是泛指聊天工具调用，而是把程序式技能规划放进世界—动作模型。[论文](https://arxiv.org/html/2610.30136)；[项目页](https://agentic-wam.github.io/)。

已核实[官方代码库](https://github.com/ZhuoyangLiu2005/agentic-wam)及[预训练权重](https://huggingface.co/miniFranka/agentic-wam-pretrain-yamego3k-soup-e1)。仓库称包含预训练与后训练代码，但原始预训练语料和起始Cosmos视频权重不随此发布。因此“公开实现”不等于从零可完整复现；不能把模型卡链接当作已成功下载和验证权重。

补充元数据：[alphaXiv](https://www.alphaxiv.org/abs/2610.30136)；[arXiv版本页](https://arxiv.org/abs/2610.30136v1)。首次提交2026-10-21 17:59:56 UTC＝北京时间10月22日01:59:56。领域：Robotics / Control / World Model / Multimodal。

### 2. 解决什么问题
核心矛盾是：连续世界预测擅长表达物理变化，却不天然携带可组合的任务结构；程序规划有技能与控制流程，却可能缺少物理落地。我的理解是，它尝试在模型内部融合两者，而不是简单给现有VLA外接一个大语言模型规划器。

### 3. 方法与工程路线
原文§2采用代码、视频、动作三个专家，层间共享受掩码约束的注意力，信息顺序为代码→视频→动作；代码用离散掩码去噪，后两者用连续流匹配。默认代码仅作为动作生成条件，并不直接执行；hybrid模式才在有效性和进度检查后调用技能，否则执行动作块。[方法§2](https://arxiv.org/html/2610.30136#S2)

项目页补充了数据工程闭环：先自动生成程序标签、提炼技能库，再冻结库并重用标签；训练连接人类演示、机器人演示与任务后训练。项目展示联合去噪延迟0.23秒，而自回归代码方案0.55秒，测试硬件为RTX 5090。这是特定配置下的推理测量，不是所有平台的实时保证。[项目方法与消融](https://agentic-wam.github.io/)

### 4. 值得注意的亮点
- 真正有意思的是“代码既是监督表示，也是潜在执行接口”，研究与部署之间可以共享技能语义。
- 语义规划在生成过程中持续影响物理预测，不仅是模型开始前的一次性提示。
- 工程可拆解性较好：仓库提供数据准备、标签、后训练和RoboTwin指南，适合检查某个组件的贡献，而不必先复刻全部数据规模。[仓库指南](https://github.com/ZhuoyangLiu2005/agentic-wam)

### 5. 实验支持与边界
表1：RoboTwin clean/random为80.8%/20.6%，两设置平均50.7%；随机设置低于π0.5的27.7%。表2：真实世界8任务的71.1%是分步骤rubric平均分，不是整任务成功率。hybrid随机设置29.2%，但其仿真训练示范另行采集，不能全部归因于推理切换。附录L承认技能覆盖、错误参数、视觉分布偏移及尚无在线自学习。[原文§3及附录L](https://arxiv.org/html/2610.30136)

独立解读：支持较强的是“结构化规划能改善这些后训练任务”，不是“通用机器人已解决”。评价时至少应同时看整任务完成、步骤得分、视觉域外退化和控制接管比例。若只摘71.1%，容易把部分完成夸大成可靠交付。

### 6. 热度与传播
此次榜位第2说明在该站该窗口得到关注，不代表引用量、学界共识或已被独立复现。项目、代码与权重提供了可核实的传播入口；本次未核到社交分享、讨论增速等独立传播证据，不编造“刷屏”原因。

### 7. 工程价值判断
适合已有WAM、可积累演示和维护机器人技能API的团队。优先小规模验证：固定演示集，比较无代码、自然语言子目标和结构化代码，再检查延迟与失败恢复。真正成本在标签质量、参数落地和两种控制渠道的仲裁，而不是把代码文本加入训练输入。对尚无稳定感知和低级技能的团队，直接部署hybrid风险较高；程序语法正确无法替代碰撞、抓取和接触验证。这些是我的工程判断，并非作者新增实验结论。

实际阅读：§2.1–2.4、§3.1–3.3、表1–4、附录B技能示例、附录K、L、项目消融与失败案例、仓库README发布范围。


补充源码定向检查：已读[7ad228b快照generic_mot.py](https://github.com/ZhuoyangLiu2005/agentic-wam/blob/7ad228bebb897bf01705cc10171e1d88cf5e9b22/src/agenticwam/models/cosmos_mot/generic_mot.py)和[agenticwam_model.py的attention mask](https://github.com/ZhuoyangLiu2005/agentic-wam/blob/7ad228bebb897bf01705cc10171e1d88cf5e9b22/src/agenticwam/models/cosmos_mot/agenticwam_model.py)。各expert自带pre_attn/post_attn，coupler仅拼接Q/K/V、执行masked joint attention再拆回，保留各专家自身AdaLN/交叉注意力实现；代码检查层数、head数和head维度一致。mask实现中code为独立信息岛、video读code、action读video及code，和论文的主要条件化路线相符。未运行或验证全部部署路径。

## 3.Learning the 4D World through Point Trajectory Forecasting（VPM）

### 1. 基本信息与今日版本
Byungwoo Jeon、Sunghwan Hong等，KAIST、ETH Zürich、SNU、NYU等。今日arXiv仍只列v1：2026-10-20 17:45:45 UTC，北京10月21日01:45:45。[版本历史](https://arxiv.org/abs/2610.28594)

[alphaXiv入口](https://www.alphaxiv.org/abs/2610.28594)；领域：Multimodal / Robotics / World Model。

### 2. 解决的问题
沿用昨日结论：多视角视频看起来真实，不保证相机看到的是同一个三维运动；用持久物理点轨迹监督把外观预测锚定到一致几何。

### 3. 核心方法
相机条件化多视角世界模型，联合预测视频和点轨迹；轨迹头从共享特征迭代预测位置、深度，再升维为3D；动作扩展加入动作token。不是所有机器人控制都由显式点轨迹经IK直接完成。[项目方法](https://rootyjeon.github.io/video-point-model/)

### 4. 亮点
保留昨日判断：受控V与V+T比较、机器人运动学产出的密集点监督、同时检验外观与几何的VP-WorldBench，比单纯多视角漂亮视频更有工程价值。

### 5. 证据与限制
昨日已读表2：模拟机器人FVD 78.52→67.35，真实机器人296.83→255.19；表5真实任务允许碰障碍时给0.5分，不是纯二元成功率。论文百秒级多视角生成与点轨迹IK定性演示不能宣传为实时通用机器人控制。今日未核到新版实验，不重复全文。[原文](https://arxiv.org/html/2610.28594v1)

### 6. 今日热度增量
第2→第3；likes 16→34（+18）；views 220→459（+239）。排名下降不代表关注减少，因为其他论文同时进入榜单。仓库今日页面27 stars、0 forks，昨日记录21、0；这是两次可见快照，不代表新增star必然由论文传播导致。[仓库](https://github.com/rootyJeon/VPM)

### 7. 今日代码与发布核验
这是三篇中可以做commit级对照的一篇：只读GitHub commits API取得当前main最新SHA为137e9d82df47b6caf945edccb4313409847e72c6，提交时间2026-10-21 06:54:03 UTC，消息Update BibTeX；与昨日日报保存的SHA完全一致。因此可精确说“当前main HEAD未较昨日基线前进”，不能扩大为所有分支、数据集、权重和网页均无变化。[固定commit](https://github.com/rootyJeon/VPM/commit/137e9d82df47b6caf945edccb4313409847e72c6)

今日README与项目仍列训练/推理、10K数据和benchmark入口；VPM-Data-1M与Cosmos3-Super仍为未来计划。沿用昨日源码核验和非商用许可提醒，不把模型仓库存在等同于完整商业授权或已跑通。最适合已有标定多相机管线的研究团队，部署需先核延迟、算力与数据清单。[当前README](https://github.com/rootyJeon/VPM)

## 4.DONIC — Generalist Dexterous Bimanual Tracking Control from Human Demonstrations

### 1. 基本信息
Mingze Sun、Ziang Cao、Yuan Fei、Qiankuan Tao等，机构Ropedia；arXiv:2610.29997v1，2026-10-21。[论文](https://arxiv.org/html/2610.29997)；[项目页](https://ropedia.github.io/DONIC/)。项目页有Code按钮，但本次点击仍回到该项目页，没有核实到独立可下载代码仓库。因此不能写成“已开源可复现”。

补充元数据：[alphaXiv](https://www.alphaxiv.org/abs/2610.29997)；[arXiv版本页](https://arxiv.org/abs/2610.29997v1)。首次提交2026-10-21 16:36:02 UTC＝北京时间10月22日00:36:02。领域：Robotics / Control / RL / Imitation Learning。

### 2. 解决什么问题
这是参考轨迹条件下的双手跟踪，不是从任意自然语言自主完成家务。难点不只是左右手关节数量增加：一只手托住，另一只手转动，两者可能异步接触；若奖励设计不当，一只手的失误会掩盖另一只手的有效探索。我的理解是，论文重点在数据与学习信号，而不是创造一个新的大型视觉语言骨干。

### 3. 方法与工程路线
§4将PPO与经执行验证的行为克隆示范结合；策略围绕下一帧参考给有界残差，交给PD控制。奖励分别维护物体运动和每只手的接触角色。CCA在GAE后按参考片段减去优势均值，不按片段标准差归一化，也不改变critic目标。附录明确这不是无偏策略梯度的证明。[方法§4与附录C](https://arxiv.org/html/2610.29997)

项目页展示BiHOI：32视角采集、1,575条序列、229物体、14.77小时，再重建手和物体并重定向。项目页特别注明所有展示rollout均为Isaac Gym中的DONIC策略执行，不是实体机械手视频。[项目数据与演示说明](https://ropedia.github.io/DONIC/)

### 4. 值得注意的亮点
- 物体结果与各手接触监督分离，适合分析异步双手协作的信用分配。
- 以参考片段为单位的优势中心化是容易加入现有PPO实现的局部改动，值得作为可控消融，而非整套系统推倒重建。
- 成功轨迹需重新播放验证，之后才加入示范池。工程上这比只依据训练时的单次reward峰值收集“成功数据”更稳妥。[项目方法](https://ropedia.github.io/DONIC/)

### 5. 实验支持与边界
表2：53条新轨迹、164条新物体片段上，基础模型SR为86.79%和57.32%；Dexplore-bi为9.43%和11.59%。去CCA后为81.13%和48.17%。SR按轨迹平均误差阈值判断；Comp逐帧判断，并非首次失败前连续完成比例。§6限定为仿真单物体交互，实体迁移仍属后续工作。[§5、表2、附录D](https://arxiv.org/html/2610.29997)

项目还区分公共数据训练与增加BiHOI的配置，强调同一checkpoint无需测试时微调。[项目结果](https://ropedia.github.io/DONIC/) 独立解读：成功率的巨大提升需结合基线从单手方案改造成双手这一范围理解，不宜扩大成超越所有双手操作系统；参考重建、重定向和初始化同样会影响任务难度。部署方还应单列掉物、接触丢失持续时间、碰撞和施力安全，而不只看轨迹均值阈值。

### 6. 热度与传播
本次榜位第4。双手视频和新数据集是可见展示材料，但不是“为何爆火”的因果证据。本次没有独立社交传播统计，也没有第三方复现报告。尤其不能把“generalist”自动等同于开放世界泛化：这里的泛化仍受输入参考和测试对象划分约束。

### 7. 工程价值判断
对已有灵巧手仿真、参考重定向和专家示范池的团队，最值得优先复验的是CCA以及按手分开的接触监督。建议先固定数据和随机种子，记录每个参考片段的优势分布和逐手接触曲线，检查提升究竟来自困难片段学习，还是阈值附近指标变化。若目标是实机，下一步不是照搬百分比，而是补齐感知误差、摩擦变化、动力学和接触观测的落差。对产品团队而言，目前更像技能跟踪研究底座，尚不是现成的双手通用应用。这是工程推断，不是已完成的迁移结果。

实际阅读：§3数据构建、§4.1–4.4、§5.1–5.3、表1–2、§6、附录C.2–C.5和D.1–D.4；项目页Code按钮及仿真声明。

## 5. FrontierCS 2：研究型 coding agent 的验收不应只看平均分

### 1. 基本信息
- 全名：FrontierCS 2: A Benchmark for Computer Science R&D；作者 Qiuyang Mang、Wenhao Chai、Runyuan He、Dongruixuan Li、Zihan Zheng、Yujun He 等，完整作者见[原论文](https://arxiv.org/html/2610.29932v1#Sx1)。领域：Evaluation / Coding Agents / AI Systems。
- [arXiv v1](https://arxiv.org/abs/2610.29932v1)，首次提交2026-10-21 16:04:27 UTC＝北京10月22日00:04:27。[alphaXiv](https://www.alphaxiv.org/abs/2610.29932)今日第5，6 likes，views未显示。
- 实读原文Introduction、§3–7、附录资源与代理设置；GitHub README、依赖、架构文档、Codex提交适配器；未运行评测。

### 2. 解决的问题
能修复软件测试失败，不代表能改进一个已有研究系统。这里不让模型从空白写一段程序，而是在论文作者自己的仓库中删除贡献部分，让agent交补丁，并对比删除前的真实实现。问题从“写出来了吗”转为“在未知工作负载上，所有关键约束都比参考实现达标了吗”。

### 3. 实际方法
[§3–4、图2–3](https://arxiv.org/html/2610.29932v1#S3)：选择已发布论文/代码，删除核心贡献，保留依赖和函数调用；限制可修改文件。agent sandbox只连driver，不能联网重新下载答案。judge另持参考补丁、评分器、held-out workload；开发GPU与实际测量GPU分开。agent在五小时内可多次提交patch，收到开发集得分和去敏消息，最后自己指定一个最终patch，而不是评测方替它挑最好的一次。

旧式路径：题面→单程序→一次分数；本文：残缺真实仓库→补丁与开发反馈迭代→自己选择最终补丁→隔离judge的全指标/全工作负载验收。注意48任务中Structured LWE为原创挑战，是“删除贡献”生成方式的例外。

指标分三层：pass要求每项metric、每个held-out workload都满足阈值；final score是各任务自己的0–100映射；FCI用逐metric结果及相对参考的分数margin做item-response联合拟合，Kimi K2.7作为零点，不是物理意义的能力单位。[§5与附录D](https://arxiv.org/html/2610.29932v1#S5)

### 4. 亮点
1. 把“参考代码”“开发反馈”“最终验收”隔离，减少评分泄漏；最后提交选择本身也是任务的一部分。
2. 多指标通过条件能暴露被平均数掩盖的退化。例如SVG-EAR更快且平均画质更好，仍可能有个别clip不达标。
3. 同时看成功率、代价和案例源码，不把一个总分当研究价值：QuarterPIR节省通信的算法变化未必拿到最高综合分。

### 5. 实验能支持什么
- 作者测48任务、13领域、12个model+harness组合，每组合每任务一次。最佳Claude Opus5.5/Claude Code通过58%，16任务没有任何被测agent通过。**这评的是组合，不是纯模型；没有多seed重复足以估计每个任务的成功概率。**[§1、§5.1](https://arxiv.org/html/2610.29932v1#S5.SS1)
- FCI给90%按任务bootstrap区间；相近agent区间重叠，不支持精确全序。两次provider拒绝计失败，反映产品可用性也进入结果。[§5.2](https://arxiv.org/html/2610.29932v1#S5.SS2)
- 预算曲线在预算耗尽而尚无final时直接记0，不是让模型在每个预算点重跑最优策略。低预算DeepSeek V4.1 Flash领先依赖其token定价下界，不能转成用户真实成本保证。[§5.3](https://arxiv.org/html/2610.29932v1#S5.SS3)
- §6.3中GPT-6 Astra的SVG-EAR所有clip更快、平均更接近full attention，但2个clip画质越线，所以失败。§6.2更快FPGA设计同时增加电路面积，总分未惩罚面积。论文证明特定环境存在有用优化，也证明“更高均分≠验收全过”；未证明自主发现普适新算法或无人监管完成科研。

### 6. 为什么现在热门
实际进入本次Hot7Days第5，原文/开源发布是可核事实；未取得足够独立传播链，**目前只能确认论文热度高，尚无足够公开证据解释传播原因。**“更接近真实研发”是本文的工程相关性判断，不冒充社区共识。

### 7. 工程价值
建议优先读judge隔离和patch提交协议，而非直接用榜单选模型。给自己的coding-agent验收增加“每项关键用例不可回退”“最终artifact固定”“测试环境与agent权限隔离”。[源码快照e989e8c](https://github.com/FrontierCS/FrontierCS-2/tree/e989e8c6826585a336fb999db1b87fa327073c2d)：[提交适配器](https://github.com/FrontierCS/FrontierCS-2/blob/e989e8c6826585a336fb999db1b87fa327073c2d/candidates/codex/frontier_submit.py)、[架构](https://github.com/FrontierCS/FrontierCS-2/blob/e989e8c6826585a336fb999db1b87fa327073c2d/docs/architecture.md)、[依赖](https://github.com/FrontierCS/FrontierCS-2/blob/e989e8c6826585a336fb999db1b87fa327073c2d/pyproject.toml)。仓库可读不代表全部private任务开放或本轮已验证部署。

## 6.SP-HLM — Sparse-Pose-Driven Motion Generation and Whole-Body Control for Humanoid Loco-Manipulation

### 1. 基本信息
Zhaohui Yang、Quanbao Lin、Chengqi Shi等，上海交通大学、摩尔线程、香港大学；arXiv:2610.30044v1，2026-10-21。[论文](https://arxiv.org/html/2610.30044)；[项目页](https://sp-hlm.github.io/)。本次项目页读取未见已验证的代码仓库或权重下载链接；不能据此断言从未发布，但交付中不宣称已开源。

补充元数据：[alphaXiv](https://www.alphaxiv.org/abs/2610.30044)；[arXiv版本页](https://arxiv.org/abs/2610.30044v1)。首次提交2026-10-21 17:03:34 UTC＝北京时间10月22日01:03:34。领域：Robotics / Control / RL / Imitation Learning。

### 2. 解决什么问题
人形机器人高层策略究竟应该输出什么？全关节输出让高层承担协调负担，纯隐变量又难明确指定手脚到哪里。我的理解是，这篇将接口设计作为核心问题：任务几何意图与全身协调先验分别表示，而不是寄希望于单一动作空间同时表达两者。

### 3. 方法与工程路线
§III的链路是SP-VLA→SP-MGM→SP-GMT：五个显式姿态为骨盆、双腕、双踝；生成器补全全身运动，再编码为隐变量，控制器联合两类条件输出关节目标。SP-MGM先离线蒸馏，再用学生实际访问状态做教师纠正及时间平滑。手指目标直接交PD控制。[原文方法](https://arxiv.org/html/2610.30044#S3)

项目页将三部分分别解释为任务目标预测、协调运动恢复、显式与隐式联合跟踪，并展示异步动作块减少执行等待。它不是把“稀疏”理解成仅控制五个点、放弃其他关节，而是把缺失的协调结构交给学习到的运动先验。[项目方法](https://sp-hlm.github.io/)

### 4. 值得注意的亮点
- 显式目标可检查，隐变量负责协调，接口职责比单一黑盒动作向量清楚。
- 蒸馏不仅拟合离线数据，也纠正学生rollout产生的分布偏移，这一训练思路可迁移到别的低延迟生成模块。
- 模块化使错误定位更具体：可以分清目标预测不准、动作生成抖动、还是跟踪时失衡，而不是仅凭最终失败倒推。

### 5. 实验支持与边界
原文表III：标准生成速率7.813Hz，对比Kimodo 5.405Hz；末端平均误差1.812对1.941厘米，但jerk略高，不能写成所有质量指标都更好。表II在两套500动作集上评测，强项是全局误差而非所有局部指标。结论限定于全身协调，没有验证灵巧手级操作。[§IV、表II–III、§V](https://arxiv.org/html/2610.30044)

项目公布八任务仿真整体52.75%，token与joint基线分别33.75%、31.50%，每任务50次。实机Unitree G1四任务各20次：物体放置13/20、货架转移11/20、开柜5/20、踩垃圾桶8/20。去掉稀疏参考的全局误差明显上升；去掉隐式参考则损伤局部跟踪。[项目结果与消融](https://sp-hlm.github.io/)

独立解读：这支持接口的互补性，但还不能说整个系统因接口单一因素胜出。两种GR00T基线使用SONIC后台，而完整系统使用SP-GMT，比较中含控制器差异。实机样本较小，也没有展示持续多小时可靠工作。即便平均末端误差降低，小把手和窄踏板仍可能因瞬时偏差失败，平均误差与产品可用性不是同一个尺度。

### 6. 热度与传播
本次榜位第6。项目具备仿真、实机和消融展示，可确认可见度入口，但未核实第三方转发、复现或讨论增速。不能用“国产算力”“人形机器人热门”等叙事替代传播证据。

### 7. 工程价值判断
对已经有运动追踪器和高层VLA的人形机器人团队，最有价值的是重新审视接口和误差预算，而非立即替换全部模型。建议先比较相同后台下的关节、隐变量和显式稀疏目标，隔离贡献；再测异步推理的真实端到端延迟、目标过期和接触瞬间误差。若任务包含踩踏、单腿下蹲或抓小把手，应把安全停止、支撑稳定与接触精度作为额外门槛。现有结果更适合指导研究系统迭代，尚不足以承诺无人监督日常作业。这些是工程判断，不是作者已经证明的安全能力。

实际阅读：§III全部方法、§IV全部实验、表I–IV、失败分析、§V、附录VI训练与推理；项目页方法、实机与消融结果。

## 7. LocaLeJEPA：防坍塌正则也要尊重局部几何

### 1. 基本信息
LocaLeJEPA: Maximum Entropy Representations under Geometric Priors。Kartik Tandon、Alessio Borgi、Pavel Snopov、Inés García-Redondo、Davide D’Ascenzo、Sebastiano Cultrera di Montesano、Fabrizio Silvestri、Pietro Liò、Francesca Dominici、Randall Balestriero、Claudio Battiloro。[arXiv2610.28458v1](https://arxiv.org/abs/2610.28458v1)，2026-10-20 16:15:06 UTC＝北京10月21日00:15:06，未列新版本。[alphaXiv](https://www.alphaxiv.org/abs/2610.28458)第7，15 likes/222 views。领域：Self-supervised Learning / Representation / Training。实读PDF§1–6、算法与实验消融，并实际渲染查看第9页表2；HTML404、网页PDF体积超限，成功直接下载原PDF后阅读，不是只读摘要。

### 2. 解决的问题
JEPA让不同视图的表示靠近，但可能全部坍塌到同一点。LeJEPA通过把全局表示分布推向各向同性高斯防坍塌；若数据有环面结构，或编码器输出双曲/等变表示，强迫全局形状变高斯可能破坏其几何。LocaLeJEPA改问：能否只在局部扩散、保留邻域之间的位置和整体拓扑？

### 3. 核心方法
[§3–4，公式7–12与算法A.2](https://arxiv.org/pdf/2610.28458v1#page=5)：图像多视图→encoder/projector→每样本跨视图均值→对detach均值做cosine K-means→各视图共享聚类分配→各簇中心化残差→随机一维投影特征函数与均匀球目标做Epps–Pulley差异检验→与JEPA视图一致性损失加权。

簇中心不被拉到公共原点；目标球半径√(d+2)让协方差和标准高斯可比。过小簇剔除，全部不合格时回退全局检验；不是计算真实流形测地线，也不是已知真实语义类别聚类。K既控制局部尺度，也改变有效正则强度λN/K，因此局部性收益必须做强度匹配消融。

### 4. 最大亮点
- 从全局分布匹配改成局部中心化匹配，不靠再叠一个大型teacher网络。
- 证明动机与可算实现分开：流形最大熵提供方向，实际算法用batch内聚类与随机投影近似。
- 认真补了K=1低λ对照，避免把“减弱正则”包装成“局部几何”的全部贡献。

### 5. 实验能支持什么
[表2，第9页](https://arxiv.org/pdf/2610.28458v1#page=9)：ImageNet-1K冻结特征，普通ViT-S/8的LeJEPA原设置linear top1=44.6±0.23，换作者优化设置即51.6±0.28；LocaLeJEPA K4是62.1±0.27。因此合理方法增量相对匹配设置为10.5点，而不是把全17.5点都归给正则。kNN相应38.9→50.1。双曲ViT-S/8匹配设置51.6→61.9，D4-ResNet50 48.8→55.2；ViT-L/14 54.7→61.0，均为该训练配方结果。

强度匹配K1 λ=.025对K4 λ=.1后，ViT-S/8局部性仍增加linear增加2.3点、kNN约2.4点（表19；正文将两项均概述为2.3点）；但“局部Gaussian”的对照同时改了中心化与分布，不能单独识别每个因素。小ViT多数行3个预训练seed，其余架构多为单次，linear probe也仅1seed。前三类小编码器128px、ViT-L/14为238px，多视图、final epoch读出，不应当作所有现代视觉模型SOTA排名。[§5.1–5.2、附录C.4](https://arxiv.org/pdf/2610.28458v1)

证明了这些编码器/数据上的冻结表示分类、七数据集迁移和合成拓扑任务改善；未证明LLM推理、RAG检索、机器人世界模型直接提升，未独立复现。计算代价与batch过小导致邻域统计失效仍需目标硬件实测。

### 6. 现在为何热门
今日Hot第7和开源可确认；目前只能确认论文热度高，尚无足够公开证据解释传播原因。不能把JEPA相关人物名气当作传播因果。

### 7. 工程价值
视觉embedding训练值得小规模复现；通用RAG服务暂不需要为此迁移架构。已读[771361c源码](https://github.com/alessioborgi/LocaLeJEPA/tree/771361c18d37e65df3dc188761ffb26751ce4e37)中的[losses.py](https://github.com/alessioborgi/LocaLeJEPA/blob/771361c18d37e65df3dc188761ffb26751ce4e37/src/losses.py)、[Lightning模块](https://github.com/alessioborgi/LocaLeJEPA/blob/771361c18d37e65df3dc188761ffb26751ce4e37/src/models/lejepa_module.py)、[MINIMAL](https://github.com/alessioborgi/LocaLeJEPA/blob/771361c18d37e65df3dc188761ffb26751ce4e37/MINIMAL.md)、pyproject。local_loss记录configured/effective clusters、kept_fraction、fallback，是可借鉴的实验可观测性设计。最小Imagenette例子比直接上ImageNet合理；本轮未安装运行。

## 8. Meta²：复用“何时该改”的经验，不永久继承每次补丁

### 1. 基本信息
Meta²: Precomputing Reusable Knowledge for Online Harness Evolution in Long-Horizon Agents。Lingzhi Yuan、Yiguang Cai、Weize Liu、Siqi Yang、Feijiang Han、Yongkyun Lee、Udari Madhushani Sehwag、Furong Huang；以原PDF首页8名作者为准。领域：Agents / Harness / Memory / Evaluation。

[alphaXiv真实页面](https://www.alphaxiv.org/abs/2610.meta2-online-harness-evolution)第8，32likes/265views，显示Submitted21Oct2026，**此处是非数字slug，不是可当作arXiv编号的字符串**。未核到数字arXiv编号、精确时间或版本历史，不伪造arXiv链接。[官方项目](https://meta-square.github.io/)和[45页原文PDF](https://meta-square.github.io/paper.pdf)可读；已读§1–6、附录B/C/E/F/I，并渲染第7页表1，未只照alphaXiv AI overview写评审。版本记“本次读取的项目PDF快照”，不能等同v1。

### 2. 解决的问题
固定harness无法预见长任务中才暴露的缺工具、漏约束和错误自检；但盲目在线修改又会打断有效探索。把每次修补永久留给下一任务还可能污染工作流。文章优化的是干预决策知识，而不是学习一个永远共享的万能提示词。

### 3. 核心方法
[§3、图2、附录B](https://meta-square.github.io/paper.pdf#page=4)：离线同任务采集A无evolver、B当前Meta-Skill引导evolver、C仅训练期知道privileged verifier的evolver。按终局结果构造act/avoid/hold方向证据，经REFLECT→AGGREGATE→UPDATE生成文字Meta-Skill。聚合条目需来自至少两个不同训练任务；C轨迹要审计泄漏，不合格不能进知识库。

线上冻结Meta-Skill与模型；evolver在确定checkpoint读取新增轨迹、允许的只读工作区观察、前次edit状态，决定KEEP或通过有限notice/instruction/hook/tool通道EVOLVE。环境和累计进度不重启；终点KEEP接受artifact、EVOLVE发回同一环境继续。任务结束丢弃edit及checkpoint会话，下一任务复用知识、不复用上次具体harness变更。held-out verifier不进入evolver或知识更新。

旧方式：历史任务→共享固定harness；本文：历史对比→冻结干预知识→当前证据→任务内可撤销/有限修改。论文里的接口不是授权agent无限制扩权。

### 4. 亮点
1. “该保持不动”是显式学习目标，avoid不是一律拒绝改动，而是拒绝特定有害干预。
2. 跨任务知识与任务内编辑分离，明确状态寿命，避免把偶然修补积累为全局规则。
3. C条件为A/B都失败的训练任务提供恢复线索；但这是带特权信息的离线构造，不能把训练数据获得成本隐去。

### 5. 实验支持与边界
[表1、附录C表4](https://meta-square.github.io/paper.pdf#page=7)：Terminal-Bench2.1训练29/测试60，每测试5次共300run，mean@5；DeepSWE1.1训练38/测试75，每测试3次共225run，mean@3。GPT-5.6-Terra、相同NexAU初始harness下Meta²=81.00%/44.44%，seed=66.33%/34.67%，Meta-Harness=73.33%/37.33%。不是完整官方测试集leaderboard，也不是“多试几次至少成功一次”的pass@k。

[图4，第9页](https://meta-square.github.io/paper.pdf#page=9)：加evolver=74.67/36.44，自蒸馏知识=77.00/35.56，contrastive知识=81.00/44.44；跨任务保留edit降至78.33/39.11。支持当前设计的消融关联，但整条trajectory结果无法给单个checkpoint建立因果信用分配。第二backbone DeepSeek-V4-Flash-0731另建Meta-Skill后77.67%，不是同一知识零样本跨模型迁移。

成本为**整次evaluation汇总美元**不是每题账单。Meta² Terminal offline110.19+online64.72=174.91，DeepSWE238.52+129.34=367.86；比seed在线更贵，比部分离线harness搜索便宜。L5最优81.00；更频繁L1成本83.41且79.00，更多干预不一定更好。[§4.3–4.4](https://meta-square.github.io/paper.pdf#page=8)。表中的金额是作者特定运行计价，不是当前服务价格建议。局限：仅两类长任务、特定模型和自定split、未独立复现；广域迁移、长期污染与真实部署安全仍未证明。

### 6. 热度
今日Hot8、提交日期及项目公开可核；无充分独立传播证据。目前只能确认论文热度高，尚无足够公开证据解释传播原因。特别不把overview中的推断当作者额外实验。

### 7. 工程价值
最值得借鉴到coding agent/自动化的是：知识条目附来源、允许KEEP、运行结束清理局部edit、保留回滚状态。上线前需要权限边界、回归用例和成本门槛。此次项目页只核到PDF/结果，没有可核下载代码入口，**不声称开源可一键复现**；可先按附录B接口与I条目schema做设计审查，不自动修改现有系统。

## 9.Sage-A1.5

### 1. 基本信息与今日版本
Wenjie Lou、Tianshuo Peng、Shiyang Feng等；Shanghai AI Laboratory模型卡。全题为Sage-A1.5: From Long-Horizon Execution to Scientific Exploration with Capability Composition。今日仍仅v1：2026-10-20 17:32:48 UTC，北京10月21日01:32:48。[版本历史](https://arxiv.org/abs/2610.28578)

[alphaXiv入口](https://www.alphaxiv.org/abs/2610.28578)；领域：Agents / RL / Scientific Exploration。

### 2. 解决的问题
沿用昨日：长任务失败不仅是知识问题，也包括错误假设持续扩散、分工与验证不足。因此训练重点是能力组合、证据检查与策略修订，而不只是扩大模型。

### 3. 核心方法
35B MoE模型结合多领域教师、SFT、结果RL及on-policy蒸馏；通过训练轨迹学习委派、合并结果与自检。今日模型卡再次确认，编排需要宿主实现spawn_subagent，验证需chat-template显式开启，二者默认关闭。[模型卡Advanced Modes](https://huggingface.co/InternScience/Sage-A1.5)

### 4. 亮点
最值得迁移的是结构化子代理返回、可验证训练环境，以及发现问题后改道的训练监督；不是用“模型会反思”替代外部审计。

### 5. 实验证据与限制
昨日已核Table 4最终模型编排使BrowseComp 81.7→82.8、DeepResearch II 43.7→47.5。Table 5验证收益来自验证教师，不能算到最终统一模型；科学案例仍是模拟与历史回放，不是独立确证新发现。今日无新arXiv版本，不新增实验成功叙事。[原文](https://arxiv.org/html/2610.28578v1)

### 6. 今日热度增量
第4→第9；likes 16→34（+18）；views 171→352（+181）。当前关联Agents-A1仓库578 stars/55 forks，昨日574/55，但这是已有旧仓库的累计量，不能当作Sage-A1.5独占热度。没有可靠外部传播因果证据。[关联仓库](https://github.com/InternScience/Agents-A1)

### 7. 今日发布核验与工程价值
今日已重新读Sage-A1.5模型卡的权重、编排与验证说明；关联GitHub README仍以Agents-A1为标题，News最新可见2026-07-14。它不能支撑“Sage-A1.5完整训练代码与数据已公开”的结论。昨日没有保存这个库和模型卡的完整commit/版本基线，本次也未做全量diff，所以不能断言代码或权重完全无变化。

保留昨日工程建议：若试用，固定工具与预算，分别测试普通、编排、验证模式的成功率、总token和墙钟时间；科学与高风险结论保留外部检查。本次确认的是当前入口和配置条件，不是运行验证。[模型卡](https://huggingface.co/InternScience/Sage-A1.5)；[README](https://github.com/InternScience/Agents-A1)

## 10. Looking Ahead：训练时预测更远，推理时不加支路

### 1. 基本信息
Looking Ahead: Modeling Future Evolution in Autoregressive Video Generation；Ruopeng Gao、Yukun Huang、Jiarui Hu、Shuai Wang、Wenbo Hu、Ying Shan、Limin Wang。[arXiv2610.29989v1](https://arxiv.org/abs/2610.29989v1)，首次提交2026-10-21 16:28:46 UTC＝北京10月22日00:28:46；[alphaXiv](https://www.alphaxiv.org/abs/2610.29989)第10，9likes，views未显示。领域：Video Generation / World Models / Training。已读HTML§1–6、附录A/B/C及表1–4，另读官方实现核心loss/config；未复现训练。

### 2. 问题
teacher forcing给模型连续的真实历史，邻近片段高度相似，模型可能只靠局部外观延续完成去噪，而没有足够压力学习物理演变。因此“能接着生成”不能直接证明“理解世界动态”。目标是利用已有视频提供更难的监督，而不是增加外部视觉teacher。

### 3. 方法
[§4、图1–2](https://arxiv.org/html/2610.29989v1#S4)：Wan视频DiT改为chunk-causal生成；从当前clean与noisy chunk提取多层hidden states，拼接经MLP融合，通过逐token AdaLN输入独立的小型DiT预测器。各未来offset独立并行预测，禁止经中间未来分支传递信息，避免“偷看”邻近目标；辅助分支取消显式text cross-attention，让其依赖主干特征。

训练将teacher-forced当前chunk flow loss和远期chunk flow loss一起反传主干；每offset独立噪声/flow time，clean/noisy源共享对应预测器。推理完全丢弃FCP分支，主干生成流程不变。不是推理阶段每次多算若干未来视频，也不是已实现的speculative sampling加速。

### 4. 亮点
- 监督来自同一视频，不新增预训练视觉编码器；重点是切断容易的时间捷径。
- 独立平行未来头区别于串联预测，避免其他未来目标的noisy输入泄漏。
- 训练辅助容量与推理成本解耦；改进质量不必增加部署组件，但训练仍需额外分支算力。

### 5. 实验证据与限制
[表2](https://arxiv.org/html/2610.29989v1#S5)：匹配Wan2.2-TI2V-5B数据/训练设置，Physics-IQ Verified的I2V IQ30.4→33.8，V2V40.6→44.4（5offset）；串联5offset仅31.0/39.9。表4的1.3B27.6→30.9。可支持受控配置中的物理可信性得分改善；不能把跨模型表1差异都归因方法，作者也提醒数据/训练设置不同。

[表3](https://arxiv.org/html/2610.29989v1#S5.SS4)：WorldModelBench总分7.22→7.64；PAI-Bench-G Domain81.13→82.38；PhyGround Physics2.75→2.80。多个指标正向但幅度不一，既不是100%物理正确，也不是机器人规划已获验证。部分benchmark依赖VLM判分，而主要Physics-IQ Verified为参照真实录制的数值评测；图3定性案例只是演示，不代替总体统计。

附录C明确尚未验证from-scratch大规模预训练、辅助头用于推理加速/ensemble等用途；表示可视化结构更清晰不能单独证明学会因果物理。训练/硬件和未知分布仍需目标部署实测，未独立复现。[原文附录C](https://arxiv.org/html/2610.29989v1#A3)

### 6. 热度
实际Hot第10，近期v1和代码/权重发布可确认；目前只能确认论文热度高，尚无足够公开证据解释传播原因。7stars是alphaXiv显示快照，不伪造真实Star增长。

### 7. 工程价值
对视频生成训练团队有直接价值，对普通React/Python RAG应用不应勉强迁移。可先读[PredictiveFlowMatching](https://github.com/TencentARC/Looking-Ahead/blob/210794c758f386d3a1eaf3673b51b7cdd8374dfc/src/model/predictive_fm.py)：按offset构造独立未来噪声/target，检查valid pair数与shape，分别计算clean/noisy来源loss；再看[predictive_causal_model.py](https://github.com/TencentARC/Looking-Ahead/blob/210794c758f386d3a1eaf3673b51b7cdd8374dfc/src/utils/predictive_causal_model.py)和[5B配置](https://github.com/TencentARC/Looking-Ahead/blob/210794c758f386d3a1eaf3673b51b7cdd8374dfc/configs/fcp_wan22_ti2v_5b.yaml)。实读[README/依赖](https://github.com/TencentARC/Looking-Ahead/tree/210794c758f386d3a1eaf3673b51b7cdd8374dfc)确认提供训练/推理和1.3B/5B权重链接；作者测试Linux、H200、Python3.12.3/PyTorch2.10+CUDA12.8，不能据单GPU例子承诺消费卡可跑。

## A. 今天最值得深入读的3篇

1. **FrontierCS 2**：最贴近coding-agent工程实践。优先§3–5和SVG-EAR案例，读提交适配器与隔离judge设计。可立即借鉴“逐项阈值、固定final、隐藏最终工作负载”验收，不必先购买某个榜首模型。
2. **Meta²**：优先§3、附录B与I，核心价值是状态寿命和干预边界。跨任务复用规则、任务内保留修改、结束后清理，适合审视长任务代理。代码未核实开放，先做设计评审而非承诺一键复现。
3. **LocaLeJEPA**：优先§4、表2/19、src/losses.py与MINIMAL.md。可小规模隔离局部性、中心化、目标分布和正则强度，实验设计比泛称“更懂几何”更值得学习。若只做应用层RAG，此篇低于前两篇的直接优先级。

## B. 当天项目支持的研究趋势

1. **世界模型与控制的接口更结构化**：AW-0用代码规划条件，VPM用持久点轨迹，SP-HLM用显式五点+隐式协调。三者不是同一模型路线，但共同把中间表示变成可检查对象。
2. **长任务可靠性从最终均分走向过程与逐项验证**：FrontierCS2用全指标验收；Meta²区分KEEP/EVOLVE与状态寿命；Sage-A1.5将编排与验证模式分开。这是本榜的工程主题，不代表整个行业已形成共识。
3. **训练监督改造可能比推理堆组件更有价值**：Looking Ahead训练辅助预测器在推理丢弃，LocaLeJEPA改变正则而不添加部署teacher；SuperMimic以可微代理改优化路径。不能据此推导三者成本都更低，成本计量各不相同。
4. **机器人论文必须分开模拟、实机与指标语义**：DONIC未做实体迁移，AW-0用步骤rubric，SP-HLM小样本实机成功率仍不高；“generalist”“实时”“成功率”不能互换。这是今天各论文证据直接支持的评审重点。

## C. 与昨天相比

对照的是[2026-10-22已交付报告固定版本](https://github.com/DanielMax937/daily-research-reports/blob/14f16023ffe7ea2c7782547515cca1ce1b3e08eb/2026-10-22/ai-papers.md)，昨日同为Hot/7Days、北京时间11:15:49–11:19:21快照，非搜索缓存。

- 连续3篇：SuperMimic 1→1，VPM 2→3，Sage-A1.5 4→9。三篇arXiv仍v1；VPM main HEAD精确与昨日相同，其余未做完整代码版本对照，不声称全仓库无变化。
- 新入7篇：AW-0、DONIC、FrontierCS2、SP-HLM、LocaLeJEPA、Meta²、Looking Ahead。这里“新”是榜单成员变化；LocaLeJEPA首发10月20日UTC，尤其不是今天的新论文。
- 离开前10：Halcyon（Text-to-Image Generative Modeling Without Language Pretraining）、MemT-1.0、S-Agent2.0、Direct Robot Control、Large Flow Language Models、TokenGate、SolarRenderer。未核其全部当前排名，不能给出虚构下降位数，也不能将离榜自动解释为研究降温或技术被否定。
- 今日新增主题偏向机器人规划/跟踪、研发benchmark、在线harness演化、局部几何表示；昨日前10中更多内存和LLM推理效率论文。只描述两次快照的构成，不用一天榜单推断长期资金、产业或学术趋势。
- 所有热度变化保留原值和缩写；没有确认新版本/实验的连续论文，工程判断暂不变。

## 原文与代码核验索引

- 新论文原文：AW-0§2–3/附录B/K/L，DONIC§3–6/附录C/D，FrontierCS2§3–7/附录资源与代理设置，SP-HLM§III–V/附录VI，LocaLeJEPA§1–6/附录A/C及表2第9页可视核对，Meta²§1–6/附录B/C/E/F/I及表1第7页可视核对，Looking Ahead§1–6/附录A/B/C。没有称读完每一篇所有附录或观看全部demo。
- 固定代码快照：AW-0 7ad228bebb897bf01705cc10171e1d88cf5e9b22；VPM 137e9d82df47b6caf945edccb4313409847e72c6；FrontierCS2 e989e8c6826585a336fb999db1b87fa327073c2d；LocaLeJEPA 771361c18d37e65df3dc188761ffb26751ce4e37；Looking Ahead 210794c758f386d3a1eaf3673b51b7cdd8374dfc。定向已读文件与直接链接在相应条目，未做全仓审计。
- 需保留的缺口：Meta²数字arXiv编号/版本历史及代码；SuperMimic官方训练代码；DONIC独立代码下载入口；SP-HLM代码/权重；社交传播因果链；独立复现与目标硬件成本。公开可读不等于许可适合商用，下载链接存在不等于权重已验证。
