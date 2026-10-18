# 2026年10月18日 AI论文日报

## 今日结论与榜单证据

今天成功通过alphaXiv正常页面核实了 **Trending、7 days、前10个研究条目**。最值得优先阅读的工程问题是：什么时候预构造知识空间、什么时候重置Agent搜索状态，以及如何让模型在失败代价不同的任务里选择更合适的退路。榜中包含研究随笔与非标准arXiv编号条目，不把它们伪装成已发表arXiv论文。

- 报告日期：Asia/Shanghai，2026-10-18。
- 榜单核实窗口：北京时间11:02–11:05（原始UTC 03:02–03:05），不是把旧搜索缓存当今日榜单。
- 实际入口：[alphaXiv Trending，7 days](https://www.alphaxiv.org/?sort=Trending&interval=7+Days)。在自己的云端浏览器打开首页，通过Filter feed→Sort看到Most Recent / Most Liked / Most Stars，选择Most Liked后页面露出Trending导航，再点击Trending；地址明确为`sort=Trending&interval=7+Days`，页面显示“7 days”。滚动核对前十，跳过“Researchers to follow”推荐卡。
- 默认首页没有明确排序标签，**未仅凭默认流认定排名**。网页文本读取工具无法读取上述带筛选查询URL，正常浏览器成功；单篇Librarian #4、AutoSFT #9、CALM #3徽章也与该顺序相符。浏览器按滚动呈现部分条目，已结合前后页面核对。
- 7 days是页面显示窗口；具体边界时区、Trending内部计算公式与更新频率未披露。likes/views是当次静态显示，不是24小时新增，也不代表技术质量。
- 研究仅阅读公开原文、作者代码和页面；未训练、执行论文代码或独立复现。实验数值均为作者报告，方法贡献与产品可用性分开判断。

## 当次前十快照

| 排名 | 研究条目 | 站内标识 | Likes | 页面Views |
|---|---|---|---:|---|
| 1 | Generative Representation Learning for Scalable Latent Tokenization | [2610.20533](https://www.alphaxiv.org/abs/2610.20533) | 74 | 1k |
| 2 | T2-z: Test-Time Optimization of Environment Latents for Robotic World Models | [2610.22364](https://www.alphaxiv.org/abs/2610.22364) | 24 | 213 |
| 3 | Stay CALM: Calibrated Online Aggregation for Multi-Horizon Forecasting Under Delayed, Overlapping Feedback | [2610.calm](https://www.alphaxiv.org/abs/2610.calm) | 7 | 未显示 |
| 4 | Librarian Agents: Training LLMs to Curate Long-Context Workspaces that Anticipate Future Queries | [2610.22273](https://www.alphaxiv.org/abs/2610.22273) | 9 | 首页未显示；详情87 |
| 5 | Training Language Models to Fail Gracefully | [2610.20401](https://www.alphaxiv.org/abs/2610.20401) | 34 | 1k |
| 6 | Neural Networks Are Already Clean | [2610.already-clean-goodfire](https://www.alphaxiv.org/abs/2610.already-clean-goodfire) | 108 | 4k |
| 7 | Are We Overthinking One-Step Generation? | [2610.20331](https://www.alphaxiv.org/abs/2610.20331) | 83 | 1k |
| 8 | Learning Self-Orchestration in Decentralized Agent Swarms | [2610.22322](https://www.alphaxiv.org/abs/2610.22322) | 2 | 未显示 |
| 9 | AutoSFT: An Agentic System for Automated Data Research in Supervised Fine-Tuning | [2610.22194](https://www.alphaxiv.org/abs/2610.22194) | 25 | 215 |
| 10 | Scaling Discovery Requires Forgetting | [2610.20563](https://www.alphaxiv.org/abs/2610.20563) | 25 | 394 |

**阅读方式：**下文按实际排序逐项报告。Librarian Agents与AutoSFT昨天已深读，因此压缩背景，重点说明今日版本/代码/排序核验；没有将重复论文包装成新发布。个别全文或代码受限时保留原榜位置，明确缺口。



## 1. Generative Representation Learning for Scalable Latent Tokenization：把 tokenizer 的训练成本算进生成账本

### 1）基本信息与阅读范围

- 主要领域：Representation Learning / Tokenization / Generation / Training
- 全部作者：Alan Baade、Kyle Sargent、Vincent Sitzmann、Eric Ryan Chan、Justin Johnson、Li Fei-Fei、Gordon Wetzstein
- 本次固定版本：[arXiv:2610.20533v1](https://arxiv.org/abs/2610.20533v1)，提交时间 UTC 2026-10-14 17:29:09；北京时间 2026-10-15 01:29:09
- 实读：[全文](https://arxiv.org/html/2610.20533v1)第3–5节数学目标和架构、第6节全部实验及第7节结论；附录A.1伪代码、A.2重建/积分实验、A.3实现和成本口径、A.4理论条件、A.7 scaling原始数值。图1–4及表1、3–5按正文/图注核验

### 2）问题是什么
用于辨别类别的好表征，不一定是适合生成所有细节的好tokenizer：对比学习可能只留下足以区分样本的少数信息；分类器的patch特征还可能缺少直接约束。更现实的问题是：如果连DINO等编码器的预训练也付费，先训练表示、再训练生成器，究竟比直接生成像素划算吗？论文将这两个问题连接起来。[问题与比较范围](https://arxiv.org/html/2610.20533v1#S1)

### 3）工程师可懂的方法数据流
RePR的核心不是新增一种压缩码本，而是训练更适合生成的连续patch表示：
1. 一张图取两个部分可见的视图A、B，再取一个待预测patch p
2. MAR式预测网络分别根据B和A+B预测p；用两种条件下去噪误差的差，估计“多看A之后，预测p多得到多少信息”
3. 表示网络分别编码A、B和B+p；让“A的表示”与“加入p后B的表示增量”的内积，拟合上一步的信息增益。该监督目标停止梯度，避免预测器为迎合表征目标作弊
4. 将大视图的信息量拆成局部增量，降低估计成本；对噪声时间加权，避免高频像素细节主导目标。使用同一噪声做配对估计，32次Monte Carlo积分只占作者估计训练FLOPs的1.3%
5. 预测网络每步更新，表示分支每四步更新一次；后续迭代可把预测目标从像素改为上轮特征。下游通过Latent Forcing先生成表示、再条件生成像素
[第4–5节](https://arxiv.org/html/2610.20533v1#S4)；[算法及实现](https://arxiv.org/html/2610.20533v1#A1)

### 4）最值得关注的亮点
- 将“tokenizer应该保留什么”写成明确的信息增益监督，直接约束patch表示，而非借用分类模型的中间激活
- 主比较把编码器与生成器训练成本相加，并用不依赖外部感知损失/GAN解码器的Latent Forcing隔离表示带来的收益
- 展示编码器尺度增加与下游可生成性改善的关系；但“理论PMI”与实际加权、近似估计之间仍有条件，不能直接等同于有限模型无损保留所有信息

### 5）实验支持什么，不支持什么
- **总训练预算下确有收益**：表4中，像素JiT-L训练600 epochs为3.57×10²⁰ FLOPs、FID-50K 2.36；RePR-78M+JiT-L（生成器440 epochs）为3.49×10²⁰ FLOPs、FID 2.18，IS由298.5到338.4。两者采用引导生成，不能与无引导FID-10K混用
- **迭代特征目标有价值**：表1(e)固定总600 epochs，173M模型的一/二/三轮方案FID-10K为30.68/24.73/23.81；这比只说“训练更久更好”更有解释力
- **目标工程化很关键**：表1(f)直接使用PMI式时间权重得到NaN；调整时间采样与权重后为35.09。它不是把理论公式原封不动丢进训练就能稳定工作的方案
- **7×/8×必须标成外推**：图3和附录A.7把测量曲线拟合后外推到DINOv2/WebSSL水平；附录给出约7.77×和7.96×。不是已训练模型实测达到同等质量后节省这么多算力。最大ImageNet模型200 epochs后出现过拟合
- **公平性边界**：附录A.3按6ND估计FLOPs，明确不计self-attention；是估算训练算力，非端到端GPU时长。若使用第6.5节RAE/GAN+LPIPS路线，则又引入外部模型，其预训练账不能与主路线混淆。部分mask/loss消融以ImageNet top-1做代理指标，不直接证明生成质量
- 水印压力测试支持对特定feature suppression更稳健，不等于对全部数据偏差或分布转移都免疫。论文HTML有表号交叉引用不一致，以上按表标题及实际数值对应
[实验主文](https://arxiv.org/html/2610.20533v1#S6)；[实现及成本](https://arxiv.org/html/2610.20533v1#A1.SS3)；[原始scaling数值](https://arxiv.org/html/2610.20533v1#A1.SS7)

### 6）今日热度
本次北京时间2026-10-18 11:03的alphaXiv Trending 7 days快照中排名第1、74 likes；这是单次累计快照，不是24小时增长。没有核实足够传播链证据，不推测热度原因。[论文页](https://www.alphaxiv.org/abs/2610.20533)

### 7）工程价值与源码可用程度
适合做生成基础设施/表示学习的团队关注：最可迁移的是把tokenizer成本纳入预算，以及对表示做局部、可解释监督。**目前不能按“现成开源实现”安排复现**：作者链接的[官方仓库固定commit](https://github.com/AlanBaade/repr/tree/1061b1d3fc192ab367c0e77157e6f36e7e0f506a)在本次核查时只有MIT LICENSE，没有训练源码、README或权重。实际可用的是论文伪代码与配置表；本次没有运行代码

---

## 2. T2-z：机器人遇到新环境，先拟合32维隐变量

### 1）基本信息与阅读范围

- 主要领域：Robotics / World Models / Test-Time Optimization
- 全部作者：Chenyuan Zhou、Yining Hong、Huang Huang、Yunfan Jiang、Wenlong Huang、David Held、Vitor Campagnolo Guizilini、Yue Wang、Li Fei-Fei、Jiajun Wu、Leonidas Guibas、Yejin Choi
- [arXiv:2610.22364v1](https://arxiv.org/abs/2610.22364v1)，UTC 2026-10-15 17:59:11；北京时间2026-10-16 01:59:11
- 实读：[全文](https://arxiv.org/html/2610.22364v1)第3节算法、第4节全部任务/主表/消融、第5节结论；附录A架构和优化、B数据/预算、C指标协议、D基线、E维度/交互量/效率分析；另直接查看图4的PCA图像；核查官方推理代码、训练代码、摩擦任务配置和README

### 2）问题是什么
相同画面、相同动作，摩擦、重量或门锁硬度不同，结果也会不同。普通视频世界模型不一定能从静态外观判断这些隐藏变量。给模型明确“摩擦系数标签”又要求事先知道有哪些变量。T2-z用少量真实交互，把环境差异反推成一个小向量，再用于预测新动作结果

### 3）工程师可懂的方法数据流
- 输入初始RGB和14维机器人动作序列；基座是BWM初始化、基于Wan2.2-TI2V-5B的视频模型，冻结视频VAE
- 每个训练环境维护一个32维向量z，同环境多条轨迹共享z；不提供物理参数数值，但**需要知道哪些轨迹属于同一环境**
- 两个独立MLP将z投影到3072维：一路作为cross-attention环境token，一路加入动作/时间调制，让每个视频patch受环境条件影响
- 先训练世界模型300步，然后交替“固定模型优化z 200步”和“固定z训练模型200步”，都使用flow-matching预测损失
- 部署时冻结全部共享权重，只根据一至两条支持轨迹优化新z；40步学习率依次为3.0、1.5、0.5、0.15，各10步。之后复用z预测多个候选动作，选择更可能成功者
[第3节](https://arxiv.org/html/2610.22364v1#S3)；[附录A架构与双分支注入](https://arxiv.org/html/2610.22364v1#A1)

### 4）最值得关注的亮点
- 将环境适应从更新大模型参数，缩到优化32个数；共享动力学与环境差异在训练时就分开处理
- 不用固定长度的历史编码器，可把不同数量交互直接放入测试时优化；不是声称完全不需要交互
- 同时测视频预测与“根据预测选择动作后的实际成功”，比单独展示漂亮视频更接近机器人用途

### 5）实验支持什么，不支持什么
- **仿真摩擦任务**，表1：标准模型平均位置误差11.0626像素，T2-z 3.8540；动作成功32%→72%。质量最佳并不覆盖每个指标：重力任务DINOv2 Context位置误差5.9300优于T2-z 7.3408，而T2-z动作成功82.4%高于76.5%
- **真实机器人**，表2：四任务平均跟踪误差19.30→10.85像素，动作成功26.47%→70.80%；门关闭22.22%→55.56%，棍平衡20%→83.33%。Soft Pull中T2-z的LPIPS 0.07580反而差于标准模型0.07207，所以物理/动作收益不等于所有视觉指标都改善
- **不要过度解读摘要总平均**：仿真表混合像素、角度和灯光分数，摘要15.20→7.00不是单一有物理单位的误差。本文优先给分任务值；真实任务平均才统一为像素跟踪量
- **关键消融**：表3共同训练模型和z，摩擦ADE为7.03、成功68%；默认交替方案3.85、72%。直接优化3072维条件token则ADE 94.50、成功24%。附录表12中8/16/32/64/128维成功率44/64/72/64/64%，支持在本任务中选择32维，不能证明所有场景最优
- **成本与比较**：各适应基线收到相同支持交互、同基座，附录训练预算按任务对齐；常见任务每方法2张H200×24小时，复合质量×摩擦为4×48小时。附录E.4在单H200、相同支持和5个查询、25步去噪下报告18.09秒，LoRA为32.73秒、缓存TTT-KQV为37.57秒；不含加载、读数据和写视频，不能称为机器人端到端实时延迟
- PCA呈现因子结构是有趣的描述性证据，不证明通用因果辨识或任意未知因素可分离。测试是限定任务/因素与少量环境；没有由此证明开放世界、长时域闭环安全或跨任务直接泛化
[表1–3及任务结果](https://arxiv.org/html/2610.22364v1#S4)；[附录E](https://arxiv.org/html/2610.22364v1#A5)

### 6）今日热度
2026-10-18 11:03北京时间alphaXiv Trending 7 days快照第2、24 likes。这里只能确认排名与当时累计数，不能称为点赞增长，也不能据此推断传播原因。[论文页](https://www.alphaxiv.org/abs/2610.22364)

### 7）工程价值与源码可用程度
这是三篇中最直接针对“固定模型遇到环境变化怎么办”的设计。适合在受控物理任务做小范围复现；使用门槛仍包含5B视频基座、环境分组数据和测试时梯度计算

[官方仓库固定commit](https://github.com/T2-z-latent-optimization/T2-z/tree/c72f051f5cffcb1f372a32bc488df273556d39b9)包含训练、五种推理方法、任务配置、跟踪/动作评估及数据下载脚本，Apache-2.0。定向阅读[`t2z/inference/ours.py`](https://github.com/T2-z-latent-optimization/T2-z/blob/c72f051f5cffcb1f372a32bc488df273556d39b9/t2z/inference/ours.py)确认冻结模块、支持集loss、分段学习率和context更新；[摩擦配置](https://github.com/T2-z-latent-optimization/T2-z/blob/c72f051f5cffcb1f372a32bc488df273556d39b9/configs/inference/sim_pushbox_friction.yaml)确为40步且将z限制在[0,1]。README提供Wan与BWM初始化下载，但推理要求用户提供训练后的任务checkpoint/context table，因此不是下载仓库就能立即得到论文任务模型。本次只读代码，未验证执行或硬件表现

---

## 3. Stay CALM

### 1. 基本信息与阅读边界

- 主要领域：Online Learning / Forecasting / AI Systems
- 全名：Stay CALM: Calibrated Online Aggregation for Multi-Horizon Forecasting under Delayed, Overlapping Feedback
- 作者：Shivesh Prakash，University of California, Berkeley
- [alphaXiv条目](https://www.alphaxiv.org/abs/2610.calm)标注提交于2026-10-17；未提供小时、时区或版本号，因此不能精确换算UTC/BJT发布日期。检查时点约2026-10-18 03:06 UTC／11:06 BJT
- 这是有27页正文的研究预印本；2610.calm是alphaXiv路径，不能当作标准arXiv编号。未核实同行评审状态
- 实际阅读：[原文PDF阅读器](https://www.alphaxiv.org/pdf/2610.calm)的摘要、方法p4–5、实验设计及结果p7–11、限制及复现p12；额外截图视觉核对图4（第8页）与表2（第9页）的图例、列布局及核心数字；未逐页核验附录证明。下述数字来自PDF正文，未用AI Overview代替正文

### 2. 问题
多步预测的标签到达晚，而相邻预测窗口还重复包含同一批未来观测。关键不只是“迟到”，而是同一冲击被多次计入，使在线调权把相关噪声误当成新证据。论文希望在不重训底层模型、不逐数据集调学习率的条件下，稳定组合多个预测器

### 3. 方法
论文以长期方差／单步方差之比κ衡量重叠反馈的噪声放大。双专家稳态扩散分析导出学习率应随κ缩小；CALM通常用κ=h。它将预测跨度分成12个桶，第一层并行运行选择、汇集较短跨度证据的选择、指数梯度、校准BOA和均匀平均，第二层再校准组合。损失成熟后才更新，避免未来信息泄漏

图3及式(3)给出第一层η=η₀/(估计损失尺度×κ)，基准η₀=1/2；BOA将二阶累计量V换成κV。使用统一常数并不等于完全没有设计超参数。保存专家误差Gram矩阵，可在同一批预测上精确回放45种聚合规则，隔离“预测器不同”和“组合规则不同”的影响。[方法原文](https://www.alphaxiv.org/pdf/2610.calm)

### 4. 三个亮点
1. 将延迟与重叠相关性分开：调权的噪声尺度取决于κ，不能只按等待步数处理
2. 只需要专家预测，适合作为已有模型的外层组合器；闭源模型在接口层面也可作为专家
3. 明确区分75个开发设置与两轮预注册确认实验，并承认更简单的校准BOA常常平均更好

### 5. 证据、图表和未证明项
确认实验共90次运行：第一轮51、第二轮39；主要跨度24/48/96。图4报告CALM在88次中MSE低于Proceed，平均降低6.2%，去掉ETTh2为3.8%；63次显著更低、0次显著更高。检验为5% Diebold–Mariano，采用H、2H、4H、8H中最不利的长期方差带宽。两次未胜出均是Proceed协议的ECL、H=96，差距+0.04%和+1.0%

| 确认实验指标（表2） | CALM | 校准BOA | AdaHedgeD |
|---|---:|---:|---:|
| 单次运行最低误差次数 | 3/90 | 48/90 | 19/90 |
| 排名前三次数 | 59/90 | 73/90 | 63/90 |
| 距当次最佳方法平均误差增幅 | 0.56% | 0.33% | 0.65% |
| 距当次最佳方法最坏误差增幅 | 3.5% | 4.2% | 7.5% |

因此核心证据是“稳健、尾部较好”，不能写成“普遍最强”。图5与表3的gap另以冻结模型MSE的百分点计量，不能和上述百分比混用。p10消融中，固定其他条件、将学习率除以h，平均gap由+3.5变−0.5，最坏由+17.9变+2.9个百分点。[图4、表2、图5及消融](https://www.alphaxiv.org/pdf/2610.calm)

限制：理论不是完整CALM的regret保证；汇集证据及第二层依靠实证。κ=h在误差较快均值回归时可能过大，导致适应偏慢。输出不能越过专家凸包；低漂移时仍可能略逊于不适应（最多0.2%）。对AdaHedgeD的最坏情形优势大部分来自一个重复出现的设置。DynaME仅引用已发表数字，跨运行框架比较；PatchTST只测Proceed协议。期货预测误差改善没有转化为显著优于20日平均量曲线的VWAP计划。[p12限制，p11期货结果](https://www.alphaxiv.org/pdf/2610.calm)

### 6. 热度与讨论
主榜观测：2026-10-18 11:03 BJT，Trending 7 days第3、7 likes；这只是平台快照，不是论文质量或引用指标。本次标题精确检索未找到可核实的独立技术讨论，不能解释为“社区公认”

### 7. 工程价值（分析判断）
适合已有多个互补预测器、线上标签延迟且窗口重叠的服务。最值得先验证的是学习率的重叠校准，以及简单校准BOA与完整CALM的成本收益差异。建议离线回放同时考察平均MSE、长跨度尾部、漂移响应和线上成本，再决定采用哪一层复杂度

成本不能只报聚合的约1ms：论文p12在T4上给出九个内部专家加CALM、iTransformer共35–53ms/步，GD为10–18ms，Proceed为23–38ms。新增专家产生的预测费用、存储与延迟可能主导部署成本

[公开代码仓库](https://github.com/Shivesh777/CALM)已通过GitHub连接器核实可读，默认分支main；读了README、LICENSE、包入口和online.py前100行。[README](https://github.com/Shivesh777/CALM/blob/9c8a95a866b644869ee107de3ca76419a0cdf6f6/README.md)明确写着arXiv链接尚待提供；NumPy包支持CALM、CALMEnsemble及backtest。[源码](https://github.com/Shivesh777/CALM/blob/9c8a95a866b644869ee107de3ca76419a0cdf6f6/calm/online.py)可见学习率除以κ及BOA的κV实现；包版本字段为1.0.0。[MIT许可](https://github.com/Shivesh777/CALM/blob/9c8a95a866b644869ee107de3ca76419a0cdf6f6/LICENSE)已核实（软件许可不能自动当作论文许可）。README说明逐运行指标和图表构建脚本在仓库，约18GB逐origin误差统计需重建；期货数据需自备许可。此次仅静态阅读，未安装、运行或验证完整复现

---

## 4. Librarian Agents：昨日已深读，今日核对版本与代码

### 1. 基本信息

- 主要领域：Agent / RAG / Context Engineering

完整标题：Librarian Agents: Training LLMs to Curate Long-Context Workspaces that Anticipate Future Queries。作者Anikait Singh、Teresa Zhang、Yoonho Lee、Roshen Sanjay Nair、Aviral Kumar、Chelsea Finn。领域Agent / RAG / RL / Context Engineering。当前仍为[2610.22273v1](https://arxiv.org/abs/2610.22273v1)，初次提交2026-10-15 17:35:17 UTC，即北京时间10月16日01:35:17；今天未见修订。今日[alphaXiv详情](https://www.alphaxiv.org/abs/2610.22273)显示#4 on Trending、9 likes、87 views。已重读方法§2、主实验及附录A.2，并核对复现说明与训练入口；昨日的完整实验审阅见[10月17日报](https://github.com/DanielMax937/daily-research-reports/blob/4577fd48c59bf80a1b96856a9615a09f58d62fe5/2026-10-17/ai-papers.md)。

### 2. 解决的问题

同一批文档被反复问不同问题时，逐题检索重复发现跨文档关系。它在问题出现前学习构造可复用工作空间，适用于重复查询的稳定知识集；不代表取消检索。

### 3. 核心方法

原文→builder选择Create/Merge/Delete/Stop→带来源的合成文件层级→冻结answerer导航答题。训练查询对builder不可见；GRPO通过每8轮的回答探测及终局正确性提供反馈。主配置不优化显式成本奖励。[§2](https://arxiv.org/html/2610.22273v1#S2)

### 4. 最大亮点

学习对象是回答前的知识组织；文件来源和不可删除原文设计便于审计。工程上最应借鉴可追溯派生内容，而非先假定需要RL。

### 5. 实验能支持什么

主实验50个留出任务，两种冻结answerer准确率0.75/0.77；最强对照0.44/0.42。[图4](https://arxiv.org/html/2610.22273v1#S2.SS4)支持该协议准确率提升，未证明普遍更便宜。复用实验与跨answerer构造实验的token口径不同，代码说明分别为147,634和178,926构造token；不能混算。未独立复现，动态更新、ACL继承和注入安全仍需产品级验证。

### 6. 为什么现在热门

今天可核七天Trending第4；昨日只核到单篇#19徽章，未核窗口，不能算上升15名。目前只能确认论文热度高，尚无足够公开证据解释传播原因。论文版本和仓库main均未变。

### 7. 工程价值、代码与今日新增核验

仓库main仍为[27c9d86391b5da9c04e88b920076fa3867782bb9](https://github.com/teresaz05/librarian-agents/commit/27c9d86391b5da9c04e88b920076fa3867782bb9)，没有确认新实现。[训练入口](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/scripts/train_browsecomp_plus.sh)明确`answerer_workspace_mode=synthetic_only`，所以“保留原文”不能直接推成主训练时answerer都能读原文。脚本还需外部训练服务、生成服务及压缩服务；不应当作无资源依赖的开箱即用RAG。

[REPRODUCING.md](https://github.com/teresaz05/librarian-agents/blob/27c9d86391b5da9c04e88b920076fa3867782bb9/REPRODUCING.md)公开固定复用语料、失败计分和结构消融验证要求。建议优先借鉴快照、来源、不同成本账本；本报告没有运行这些脚本。今日变化是排序证据改善，不是模型或代码发布。

---

## 5. Training Language Models to Fail Gracefully

### 1）基本信息与实际阅读范围

- 主要领域：LLM / RL / Safety / Evaluation
作者：Daman Arora、Xuecheng Liu、Himanshu Gaurav Singh、Fahim Tajwar、Abitha Thankaraj、Ruslan Salakhutdinov、Haiwen Feng、Yuda Song、Andrea Zanette；CMU / UC Berkeley。arXiv:2610.20401v1，预印本，cs.LG。提交：2026-10-14 16:03:12 UTC＝10月15日00:03:12北京时间；截至本次检查仅v1。[版本记录](https://arxiv.org/abs/2610.20401)
阅读正文§2–5、§7，附录A/B的理论条件、D.1–D.4训练与选模细节；核对算法1、图1/3/4/7及公开源码。不是仅据摘要总结。[全文](https://arxiv.org/html/2610.20401v1)

### 2）要解决的问题
只奖励正确答案会鼓励冒险；但简单给弃答中等奖励，又可能训练出“总是弃答”。真正目标是让安全退路与解题能力同时存在。[问题定义](https://arxiv.org/html/2610.20401v1#S2)

### 3）方法与数据流
采样轨迹→判为成功/回退/错误→按组统计→重加权优势→策略更新。GracefulRL优化(1−c)log p成功+c log(1−p错误)，用ε平滑稀有成功造成的大权重。数学训练混合五档谨慎程度；不同于RLCR先生成置信度再阈值过滤。目标本身是TailRL的三值特例，新增价值主要在优化解释、平滑与fallback实验。[§4/算法1](https://arxiv.org/html/2610.20401v1#S4)

### 4）值得关注的亮点
- 把“失败后怎么办”纳入训练结果空间，适合考虑可验证安全出口的任务
- 理论讨论的是满足有界性、非退化等条件的梯度行为；不是任意神经网络的全局收敛保证
- 我的判断：应联合看成功率和错误率，仅看低错误率可能把全弃答误当成好模型

### 5）实验证据、边界与公平性
AIME错误率79.1%→8.9%，成功率损失3.1个百分点；扫雷c=0.5成功77.4%、错误6.0%，MaxRL为67.4%、17.0%。[图1](https://arxiv.org/html/2610.20401v1#S1.F1)、[图7](https://arxiv.org/html/2610.20401v1#S5.F7)
附录D匹配同尺度RLCR与本方法的数据、步数及采样配置；1.7B选中checkpoint分别600与1500步，不能称最终选中模型经历了相同更新数。作者未验证coding agent、长时程代理或off-policy训练。[训练/选模](https://arxiv.org/html/2610.20401v1#A4)、[局限](https://arxiv.org/html/2610.20401v1#S7)
审读判断：扫雷“安全保留局面”不能证明现实系统已经能正确回滚数据库；落地仍需为fallback写可验证语义。

### 6）热度依据
本轮榜单快照：Trending 7 days #5，34 likes（北京时间11:03）。这是关注度证据；没有可核验传播链，不能断言流行由哪位作者或哪个事件推动。

### 7）工程价值与源码阅读建议
已读[固定commit的safe_maze/rl_gpu.py](https://github.com/Zanette-Labs/failing-gracefully/blob/7e5ee9d11b945e333e5627edc1899ee0bc75860b/safe_maze/rl_gpu.py)：gracefulrl_advantages把奖励降序排列，差分除以rank+ε，逆序累加后还原原采样次序并组内居中；最适合先理解核心估计器。[LLM说明](https://github.com/Zanette-Labs/failing-gracefully/blob/7e5ee9d11b945e333e5627edc1899ee0bc75860b/llm_math/README.md)区分Brier、IDK、在线reward tuning三条配方；已进一步核对[core_algos.py](https://github.com/Zanette-Labs/failing-gracefully/blob/7e5ee9d11b945e333e5627edc1899ee0bc75860b/llm_math/verl/trainer/ppo/core_algos.py)：compute_gracefulrl_outcome_advantage按prompt分组，默认eps=1，再乘group size并施加response mask。
复现提示：README称AIME 2024–2026用于validation，论文D.2称MATH500用于选checkpoint，两者应先对齐；这是一项文档/实验配置待核差异，不能直接推断结果无效。只读源码，未安装、训练或运行实验。

---

## 6. Neural Networks Are Already Clean

### 1. 基本信息与阅读边界

- 主要领域：Mechanistic Interpretability / AI Safety（研究随笔）
Nick Cammarata／Goodfire；[官方研究目录](https://www.goodfire.com/research)日期2026-10-15，没有小时与时区，故不能精确转换UTC/BJT发布时刻。检查约2026-10-18 03:06 UTC／11:06 BJT。[原文](https://already-clean.goodfire.com/)自称非正式研究随笔与工作假设，不是已核实的arXiv论文；作者将语言模型技术配套论文写为未来发布。实际读了原文导论、经典视觉案例、初步审计、SwiGLU案例及相关图注，也读了[LessWrong讨论](https://www.lesswrong.com/posts/x4kvabkF2Jk8GLZp8/linkpost-neural-networks-are-already-clean)

### 2. 问题
许多看似混杂的神经元，究竟任意塞入了无关概念，还是研究者的工具与概念划分误读了它们？[原文](https://already-clean.goodfire.com/)

### 3. 方法
重看神经元正负两极、上下游电路、训练中的演变，并用干预检验解释；提出“递归泛化”：看似分离的反应可能由逐步扩展的相关模式连接。SwiGLU还须区分门与值的符号组合。[原文](https://already-clean.goodfire.com/)

### 4. 两个亮点
- 经典“猫和车”神经元被重新解释为共同形状模式，提醒人们先排查可视化工具造成的误读
- 直接研究原生神经元是值得与SAE并列测试的路线，而非必须先做分解才能开始调查。[原文](https://already-clean.goodfire.com/)

### 5. 数字及证据边界
原文初步估计Qwen3-32B约90%的神经元两极有一个主功能、约7%有两个相关功能、2–4%尚未解释；统计依赖弱激活阈值等定义。视觉模型末层99–100%可解释的结果，不等于同样比例的LLM行为已得到解释。[原文](https://already-clean.goodfire.com/)

以下为阅读后的判断：这些例子能够支持“更好的工具值得重新评估旧解释”；不能单独证明所有模型不存在叠加、所有低强度激活都已理解，或安全对齐已解决。完整审计的抽样方案、评判一致性、反例搜索与独立复现仍是采用宏观结论前需要的证据。这里没有将文章百分比当成标准化benchmark分数

### 6. 热度与真实争议
榜单快照为第6、108 likes（2026-10-18 11:03 BJT）。[LessWrong讨论](https://www.lesswrong.com/posts/x4kvabkF2Jk8GLZp8/linkpost-neural-networks-are-already-clean)读取时有42条评论、页面分数208。[Neel Nanda的本人评论](https://www.lesswrong.com/posts/x4kvabkF2Jk8GLZp8/linkpost-neural-networks-are-already-clean#7wcSqBNzQF2o9SHyY)认可直接神经元调查、agent解释工具和SwiGLU观察的实用性，但不认为这显著改变完整逆向工程的前景；他质疑弱激活和记忆事实是否仍包含大量叠加信息，也质疑视觉模型证据向LLM转移。争论既涉及实验覆盖范围，也涉及“单功能”“叠加”的定义，不能浓缩成“已推翻叠加理论”

### 7. 工程价值（分析判断）
建议把它作为解释工具设计的研究路线，而非安全认证。可在一个具体异常输出上对照原生神经元归因与SAE解释：预先固定问题、做未见样例预测、检查消融能否改变目标行为，以及是否伤害无关能力。不要仅凭top-k激活图给神经元命名；记录弱激活、负极和反例，避免循环论证。若代理能自动提出假设并尝试推翻它们，这类流程才更有可能转成可靠调试工具

原文提供[交互式InceptionV1显微镜](https://already-clean.goodfire.com/microscope/inceptionv1.html?layer=mixed4c&neuron=318)。本次没有核实独立可复现代码仓库，不能称为完整开源实验套件；也没有运行任何模型实验

---

## 7. Are We Overthinking One-Step Generation?：先学重建，再学分布

### 1）基本信息与阅读范围

- 主要领域：Generation / Diffusion / Training / Inference
- 全部作者：Woobin Park、Jaeyeon Kim、Yilun Du、Sitan Chen、Bohyung Han
- [arXiv:2610.20331v1](https://arxiv.org/abs/2610.20331v1)，UTC 2026-10-14 15:14:43；北京时间2026-10-14 23:14:43
- 实读：[全文](https://arxiv.org/html/2610.20331v1)第2节训练/Jacobian分析、第3节三域主实验、第4节预训练与后训练消融、第5节局限；附录B损失实现、C训练/评测协议、D额外结果、E FD-loss；另直接查看图1右侧预训练/后训练FID曲线图像；定向阅读官方损失实现、checkpoint/验证/性能文档

### 2）问题是什么
一步生成省推理，训练却常依赖教师、复杂轨迹目标、CFG或style embedding。作者问：直接做分布匹配难训练，是否只是初始化不合适？Priming Models用“先做带监督重建”给网络准备好自然图像结构，再转为从纯噪声一步生成

### 3）工程师可懂的方法数据流
1. 同一个条件生成网络先接收80%噪声与20%图像混合的输入，预测干净图；ImageNet主配置还加LPIPS和ConvNeXt感知损失，不能简化成只有像素MSE
2. 后训练直接输入纯高斯噪声，单次前向出图；冻结特征编码器，对真实图、生成图、另一组停止梯度的生成图提取特征
3. 在每个类别的特征分布中，用生成—真实吸引项减去生成—生成自相互作用项，兼顾对齐与防坍缩。主方法使用Sinkhorn近似最优传输；运筹中的运输方案停止梯度，梯度经特征网络回到生成器
4. ImageNet用ResNet-MAE、ConvNeXt多个特征分支，25,000次后训练更新。最终推理只保留生成器，不需要这些训练特征网络，也不需要多步扩散教师
[方法与损失](https://arxiv.org/html/2610.20331v1#S2)；[分布目标实现细节](https://arxiv.org/html/2610.20331v1#A2)

### 4）最值得关注的亮点
- 固定噪声重建就能成为有效起点，不必先训练完整的多时间步扩散模型
- 作者不仅给出分数，还用参数Jacobian对分布损失方向的响应解释为什么预训练后更容易优化；这仍是受控实验支持的机制假说，不是因果定理
- “先重建、再匹配分布”兼容多种后训练损失；主要价值是可复用训练组织方式，而非声称只有某个新损失有效

### 5）实验支持什么，不支持什么
- **ImageNet-256，表1**：Priming-L-160 FID 1.19、FDr5 7.10、238.95 EFLOPs；Drifting-L为1.61、12.59、1476.39 EFLOPs。该配对算力比约6.18×，并非精确10×；Priming-L-80为1.27/151.29 EFLOPs，与Drifting-L比较约9.76×，才接近“十分之一”。不要把最优FID和另一配置的成本比拼接
- **不是无条件的一步生成世界纪录**：作者脚注明确排除直接FD-loss优化、FID 0.72的既有配置；自身附录E的Priming-L+FD-loss也可达0.94，但使用不同后训练和FDr6协议。主表结论应限定在所比较的方法/协议
- **文本生成，表2**：固定噪声版本GenEval 0.740、DPG 81.30、293.53 EFLOPs，MeanFlow一步为0.548/76.49/546.64，约1.86×更省；更强的logit-normal版本为0.818/82.16/420.16，不能同时套用1.86×节省。仍低于表中100步Flow Matching的0.873/84.20
- **机器人世界模型，表3**：RT-1中一步Priming FID 3.16、12.37 EFLOPs，对比DriftWorld 8.99/30.71；Bridge-V2为2.82/9.50，对比4.86/37.05。但RT-1的FVD 30.96差于32步Flow Matching的27.24，正文结果段承认这一例外，表标题“全部指标胜出”不能照抄。评测每8帧重新锚定真实轨迹，不代表无锚定长时滚动能力
- **消融，表4与第4.1节**：移除感知损失，FID 1.38→2.07；80 epochs、12,500后训练步时，固定噪声0.8为1.65，而纯噪声1.0达65.08，说明保留可重建信息的重要性。替换OT为energy/Laplacian仍工作（1.95/1.85），但并非达到OT同等FID
- **公平性边界**：训练FLOPs包含两阶段及特征编码器运行，不代表已把外部特征模型预训练也计入。主表FDr5刻意排除训练使用的ConvNeXt；但“换成SigLIP/MAE/Inception后FDr5=6.13”的消融使用了评测特征，不再是独立held-out特征验证。三个seed是同一训练checkpoint的采样复评，不是三次独立训练
[主表1–3](https://arxiv.org/html/2610.20331v1#S3)；[消融与局限](https://arxiv.org/html/2610.20331v1#S4)；[附录C评测口径](https://arxiv.org/html/2610.20331v1#A3)

### 6）今日热度
2026-10-18北京时间11:03的alphaXiv Trending 7 days第7、83 likes。累计点赞多于前两篇并不矛盾，榜单排序不等同于点赞数排序；没有时间序列，不能称为今日新增83。[论文页](https://www.alphaxiv.org/abs/2610.20331)

### 7）工程价值与源码可用程度
对需要低延迟图像生成的团队，这是可以实际检查和复用的方案，但其训练仍依赖大batch、多种特征编码器与昂贵显卡

[官方固定commit](https://github.com/JaeyeonKim01/priming/tree/b29aaf81ca821edfd2a03c9ae6a0871c18e97222)提供ImageNet训练/采样/评测、B/L的80/160 epoch预训练与后训练权重链接，Apache-2.0。定向核查[`losses/discrepancy.py`](https://github.com/JaeyeonKim01/priming/blob/b29aaf81ca821edfd2a03c9ae6a0871c18e97222/losses/discrepancy.py)可见detached Sinkhorn plan和多epsilon混合；[`losses/reconstruction.py`](https://github.com/JaeyeonKim01/priming/blob/b29aaf81ca821edfd2a03c9ae6a0871c18e97222/losses/reconstruction.py)实际使用自适应加权像素MSE及可选感知分支，工程复现应以此和配置为准

README称ImageNet训练需8 GPU和约259GB准备后数据，L后训练建议H200；原始L运行显存超过85GiB。10月17日发布了冻结编码器执行优化及约3× warmed-update加速，属于作者仓库自报，非本次复测。**T2I及world-model代码仍列为10月25日计划发布**，今日不能称三域完整开源；本次没有下载大权重、运行训练或验证性能。[发布范围与资源说明](https://github.com/JaeyeonKim01/priming/blob/b29aaf81ca821edfd2a03c9ae6a0871c18e97222/README.md)

---

## 8. Learning Self-Orchestration in Decentralized Agent Swarms

### 1）基本信息与实际阅读范围

- 主要领域：Multi-Agent / RL / Orchestration
作者：Guowei Xu、Zhenting Qi（共同一作）、Amani Kiruga、Himabindu Lakkaraju、Yilun Du；Harvard University。arXiv:2610.22322v1，cs.MA/cs.AI/cs.CL。提交2026-10-15 17:51:57 UTC＝10月16日01:51:57北京时间；本次仅见v1。[版本记录](https://arxiv.org/abs/2610.22322)
已读正文方法、全部主结果/消融、附录D局限，核表1/2、图5/7/9；静态审读auction、engine、counterfactual_collector与FLOPs计量文件。[全文](https://arxiv.org/html/2610.22322v1)

### 2）要解决的问题
代理会变强，固定调度未必仍合适；谁获得行动机会又决定谁得到训练数据，调度和能力应一起学。

### 3）方法与数据流
每轮各代理竞价，最高者行动；奖励沿历史反向分配，当前代理保留1−bid的份额。恢复同一环境状态后改由次高者行动，比较完整分支回报，训练竞价偏好；行动REINFORCE与竞价学习按4:1交替。不同于固定manager，也不同于只在推理时改路由。[§2](https://arxiv.org/html/2610.22322v1#S2)

### 4）亮点
- 调度、行动、信用分配构成同一个学习闭环
- 固定已训练action policy再换调度，能部分隔离“只是模型更强”的解释
- 我的判断：需要可恢复状态的反事实分支，是方法最关键的部署前提

### 5）实验证据、边界与公平性
三任务held-out结果：crafting 41.5±5.9对20.3±4.1；navigation 1.23±0.18对0.52±0.14；research准确率21.0±4.1%对9.0±2.1%。报告为实例均值±SE，测试量分别32种子、88 episodes、50问题。[表1](https://arxiv.org/html/2610.22322v1#S3.T1)
固定action时，MPT reward41.5对GoA25.4；随机信用分配约31、MPT约42。[表2](https://arxiv.org/html/2610.22322v1#S3.T2)、[图7](https://arxiv.org/html/2610.22322v1#S3.F7)
训练FLOPs包含竞价、行动、反事实分支和更新；推理3→12个代理是增加预算，不能称等推理成本收益。主研究训练3个角色，不能外推大规模异构swarm或不可逆真实交互。[§3](https://arxiv.org/html/2610.22322v1#S3)、[局限](https://arxiv.org/html/2610.22322v1#A4)

### 6）热度依据
本轮快照#8、2 likes，不能把榜位等同广泛采用；暂无足够证据解释传播原因。

### 7）工程价值与源码阅读建议
固定commit：3b56087a2e436e04f077672cf8cffd91b8820b08。
- [auction.py](https://github.com/Embodied-Minds-Lab/MPT/blob/3b56087a2e436e04f077672cf8cffd91b8820b08/src/economy_engine/auction.py)：离散化bid、随机打破平局、处理全员pass
- [engine.py](https://github.com/Embodied-Minds-Lab/MPT/blob/3b56087a2e436e04f077672cf8cffd91b8820b08/src/economy_engine/engine.py)：AlternatingPhase与settle_revenue_share；包含分段reward缩放与participation rent配置
- [counterfactual_collector.py](https://github.com/Embodied-Minds-Lab/MPT/blob/3b56087a2e436e04f077672cf8cffd91b8820b08/src/agent_system/multi_turn_rollout/counterfactual_collector.py)：环境snapshot/restore、备份slot、偏好对构造
- [flops_meter.py](https://github.com/Embodied-Minds-Lab/MPT/blob/3b56087a2e436e04f077672cf8cffd91b8820b08/src/agent_system/multi_turn_rollout/flops_meter.py)：复核预算统计入口；区分algorithm/machine FLOPs，但某些计数异常会保留token数而FLOPs记零，复现应检查日志而非只信汇总数
重要复现差异：正文说全员出价0则跳过；当前apply_bid_pass实际按最小正出价重开竞价，并将这种合成回合排除出反事实候选。应核实验配置/论文描述，而非忽略实现细节或直接宣称实验错误。我的建议是先审这三条边界：全员pass、等价分支、快照恢复一致性；未执行任何代码。

---

## 9. AutoSFT：仍只有占位代码，保留设计价值

### 1. 基本信息

- 主要领域：Agent / SFT / Data Engineering

完整标题：AutoSFT: An Agentic System for Automated Data Research in Supervised Fine-Tuning。作者Bingxiang He、Pengqi Sun、Shihao Peng、Shaoxuan Li、Huiyu Xiao、Hongjian Shi、Zixuan Fu、Ziqing Qiao、Yuxin Zuo、Cheng Qian、Xinqiang Yu、Jiayi Li、Xiusi Chen、Yizhen Song、Xiangyang Wang、Iofai Lei、Yudong Wang、Ning Ding、Zhiyuan Liu、Xiaozhi Wang、Chaojun Xiao。领域Agent / SFT / Data Engineering。仍为[2610.22194v1](https://arxiv.org/abs/2610.22194v1)，首次提交2026-10-15 16:44:34 UTC，北京时间10月16日00:44:34。今天[alphaXiv](https://www.alphaxiv.org/abs/2610.22194)核为#9、25 likes、首页215 views。重读§3–4与附录B.4/C/D，版本页未见修订；完整昨日分析见前述日报。

### 2. 解决的问题

单一研究Agent容易陷入只调数据比例，并被执行日志占满上下文。本文试图丰富数据研究动作，而非换一个更大的微调模型。

### 3. 核心方法

固定基础模型/训练器→meta给数据recipe→独立executor训练评测→不同分析视角提案→必要时合成验证数据→下一轮从基础checkpoint重新训练。模型权重并不逐轮续训。[§4](https://arxiv.org/html/2610.22194v1#S4)

### 4. 最大亮点

把执行状态、完整产物和研究决策隔离；根据实际能力缺口扩充数据操作，而非只增加相同角色数量。对一般Agent工作流也值得借鉴。

### 5. 实验能支持什么

分析组在3M-token设置30轮得到67.10，对照前30轮最好60.60；不是多次独立研究搜索的平均。合成另用100M-token设置，不能将两组直接拼成单一增益。代码域同64小时只完成6轮合成流程，对照/分析各15轮。支持特定协议的改进，尚未证明更省费用或普适收益。[实验§5](https://arxiv.org/html/2610.22194v1#S5)

### 6. 为什么现在热门

今天七天榜#9已核；昨日#5单篇徽章缺窗口，不能解释为下跌。未发现新版本、代码发布或可核原始传播链。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

### 7. 工程价值与代码现状

今日main仍为[7c4403a3b36949b836b9b9266eb29e22320d58ac](https://github.com/Thinking-Space/AutoSFT/commit/7c4403a3b36949b836b9b9266eb29e22320d58ac)，初始化只有“Source code coming soon.”，不能声称已读训练核心实现。论文有角色设计，尚不能确认权限边界由源码强制执行。对全栈AI项目，先借鉴“执行器返回小型状态与产物路径、分析器独立提案”的评测试验；暂不视为可集成框架，也不因论文实验数字直接投入多卡预算。

---

## 10. Scaling Discovery Requires Forgetting

### 1）基本信息与实际阅读范围

- 主要领域：Coding Agent / Automated Discovery / Context Engineering
作者：Shangyin Tan、Ben Zhou、Lakshya A Agrawal、Jialin Zhang、Yilin Chen、Qiuyang Mang、Donghyun Lee、Dennis Jacob、Koushik Sen、Alex Dimakis、Matei Zaharia；UC Berkeley / Stanford / Bespoke Labs。arXiv:2610.20563v1，cs.AI/cs.CL；2026-10-14 17:49:37 UTC＝10月15日01:49:37北京时间。[版本记录](https://arxiv.org/abs/2610.20563)
已读14页PDF的§3–6及附录A/B，目视核对第6页表1/2；HTML不可用，未以摘要替代全文。10月16日报告曾覆盖，10月17日未深读；当前仍仅v1，不能称“今天更新了论文”。[PDF全文](https://arxiv.org/pdf/2610.20563)

### 2）要解决的问题
长时间搜索、独立并行和互通候选均可能平台化；已有失败历史可能让后续搜索过度保守。

### 3）方法与数据流
候选提交→judge评分→reducer决定下一轮可见状态；四代理共享候选commit与分数。每轮结束清空会话及候选历史，只保留全队最佳候选及其分数，三次reset构成四轮。相较只清对话，连workspace搜索历史也移除。[§3，PDF第3–5页](https://arxiv.org/pdf/2610.20563#page=3)

### 4）亮点
- 最佳产物充当保留成果的载体
- 从同一停滞状态分叉比较reset与继续，比单看长跑曲线更有说服力
- 我的判断：这是上下文与搜索状态管理实验，不能读作“长期记忆普遍有害”或“越忘越强”

### 5）实验证据、边界与公平性
Pi+DeepSeek V4.1 Flash，每任务每配置3次；主表按token美元成本匹配。AHC014均分：单体795k、并行964k、forget1103k；VLIW cycles：1426、1220、1097；Q171：64.0、70.2、80.8；nanochat BPB：0.980、0.980、0.961。[表1，第6页](https://arxiv.org/pdf/2610.20563#page=6)
同停滞状态后再30 proposals/agent：团队continue收益1.4%、$24.67；forget收益9.2%、$15.32。[表3，第8页](https://arxiv.org/pdf/2610.20563#page=8)
预算分别$20/$40/$20/$20；这不是包含评测GPU的一切总成本。额外消融等提案数、非等美元；只有一个基础模型、四项任务，尚未证明自动reset时机或最佳保留信息策略。[附录A，第13页](https://arxiv.org/pdf/2610.20563#page=13)
审读判断：主表把communication与forget组合，不能将全部收益归于reset；同状态消融补强因果证据，但不能完全消除任务选择及小样本的不确定性。

### 6）热度依据
当前快照#10、25 likes；“少记一些反而搜索更好”有明显反直觉吸引力属于解读，不是已验证传播原因。

### 7）工程价值与源码情况
论文明确可拆成reducer、append-only候选记录、session控制、judge四模块。此次原文和arXiv元数据未定位到作者发布的对应harness仓库，不能把论文引用的Pi仓库冒充本研究源码，也不能编造commit链接。可复现入口是[附录B的完整首轮/续轮提示及工作区协议](https://arxiv.org/pdf/2610.20563#page=13)。
我的落地建议：在隔离的搜索分支保留验证过的最佳产物，并把被忘历史留作离线审计；不要让实验性的reset删除用户约束、安全要求或不可再生证据。是否保留失败摘要、何时reset，均需另做控制实验；本次未运行实现。

---

## A. 今天最值得深入读的三篇

1. **Librarian Agents**：最贴近企业知识库、RAG与上下文工程。优先读§2、附录A.4/A.5，再看固定commit的训练入口与REPRODUCING。重点不是追逐单一准确率，而是区分构造成本、答题成本、回源模式与访问控制。昨天已经介绍，今天代码未变，不必重复从头读。
2. **Scaling Discovery Requires Forgetting**：适合反复优化代码、提示或方案的Agent。优先读§3状态接口、表3同停滞状态分叉消融及附录B提示。可以设计隔离对照，不能把“重置搜索历史”扩展成删除用户要求或审计证据。
3. **Training Language Models to Fail Gracefully**：优先读§4与附录D，并对照`compute_gracefulrl_outcome_advantage`。对工具调用和自动化最有价值的是明确定义失败与回退；论文没有验证真实系统回滚，工程实现仍须单独验收。

如果当前重点是多模型时间序列服务，CALM的误差回放与重叠校准也值得先看；如果只是开发普通RAG应用，T2-z和生成器训练论文更适合作为方法学习，暂不投入复现成本。以上排序是工程阅读优先级，不替换正文的实际榜单顺序。

## B. 十个条目支持的五个局部研究信号

- **训练或优化的对象正从最终答案扩展到中间结构。** Librarian学习工作空间、AutoSFT调整数据recipe、MPT联合学习行动机会；这三者机制不同，不等于“多Agent普遍更强”。
- **已有状态不一定要无限保留。** Forgetting保留最佳候选、清除搜索历史；T2-z则在部署时更新环境latent。共同点是明确哪些状态可改、哪些固定，不是统一的“记忆越少越好”。
- **平均成绩不能代替尾部表现。** CALM强在最坏相对损失，GracefulRL改变成功/回退/错误的权衡。不同任务的错误代价需要不同指标。
- **成本比较必须对齐计算范围。** CALM聚合耗时不包含全部专家；MPT推理扩容增加预算；RePR拟合外推不等于实测加速；Forgetting主表成本不含全部评测开销。单一“快几倍”不足以决定工程替换。
- **研究发布与可复现实现之间仍有明显距离。** RePR仓库只有许可文件、AutoSFT代码待发布、Priming只开放部分实验实现；公开页面上的GitHub链接不能自动视为完整源码。MPT与GracefulRL的论文/代码描述差异也值得先核配置。

这只是当天七天窗口前十的局部观察，不据一次榜单宣称整个领域发生长期转向。

## C. 与昨天相比

已实际读取[2026-10-17固定归档报告](https://github.com/DanielMax937/daily-research-reports/blob/4577fd48c59bf80a1b96856a9615a09f58d62fe5/2026-10-17/ai-papers.md)，当时没有可核完整榜单与时间窗口，只对Librarian、AutoSFT、Terminal-RSI作榜外补充。

- **可验证的新增是榜单证据。** 今天通过正常浏览器UI核到Trending /7 days完整前十，建立了可以供后续比较的排名基线。昨天未核同窗口，因此不能声称八篇新入榜、某篇上升多少名或连续上榜几天。
- **内容覆盖重合两篇。** Librarian和AutoSFT今天位列第4、第9，仍是昨天的v1，仓库main分别仍为`27c9d86391b5da9c04e88b920076fa3867782bb9`和`7c4403a3b36949b836b9b9266eb29e22320d58ac`；没有确认新实验/新实现。本报告压缩背景保留今日核验。
- **Terminal-RSI今天不在已核前十。** 这不证明降温：昨日的单篇徽章缺少可比窗口，今天列表后部还能看到它。不能将日报未选作深读等同于没有讨论。
- **新增阅读覆盖八项，新增发布数量不等于八。** 多数是10月14–15日原时区提交的近期论文；CALM页面日期10月17日但无时区，Goodfire为研究随笔。每项日期与论文性质单独列出，不将今日阅读包装成今日发表。
- **研究重点变化**：从昨日RAG/数据研究/终端验证，扩展到视觉tokenizer、世界模型适应、延迟反馈组合、回退策略与去中心化调度。这是阅读覆盖变化；没有两天可比排名来证明这些方向持续升温。

完整来源、版本、已读范围与缺口都保留在相应条目。尚缺的独立复现、未发布代码、部分版本时区与真实传播原因没有用推测补齐。
