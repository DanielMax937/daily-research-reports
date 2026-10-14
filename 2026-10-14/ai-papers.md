# 2026-10-14 AI论文日报

## alphaXiv Hot 前10：论文原文、代码可用性与跨日变化

**今天的新增阅读重点是行为监督、训练—推理分布差异，以及能否用更便宜的诊断解释模型退化。工程上优先深读Vela、Vocabulary Bias诊断和ReplaySSM：分别对应Agent训练数据、后训练回归诊断、自建推理服务。** 这不是按兴趣重排热榜；实际前10严格保留平台快照顺序。

### 榜单口径、时间与证据边界

- 实际获取：**2026-10-14约11:49 BJT / 03:49 UTC**。报告属于北京时间10月14日，不是全天结束榜，也不是仅收录今天发表的论文
- 先访问[alphaXiv公开首页](https://www.alphaxiv.org/)，并用云端浏览器核对可见列表和筛选菜单；独立正常获取的同份公开HTML，其JSON-LD明确标为 **Trending Papers**，有20个顺序位置。对应查询键是 **infinite-trending-papers，sort="Hot"，interval="30 Days"**，三个分类数组均为空，source/runnable未设置。本文采用这份可核服务端Hot响应，不将搜索缓存、个人推荐或Most Recent冒充热榜
- 当前可见Sort菜单只列Most Recent、Most Liked、Most Stars，没有显示“Hot已勾选”；因此Hot和30 Days的证据来自同份公开响应的查询状态，不能夸称在UI看见了不存在的选中标签。页面查询dataUpdatedAt为**2026-10-14 11:49:28.485 BJT**，dehydratedAt晚14毫秒。这是查询状态时间，不证明所有互动实时入库
- 排名、赞和浏览均冻结于这一次ItemList。跳过研究者推荐卡片，不混入稍后详情页徽章，也不因读到论文新版而重排。部分详情页的Trending数字与首页不同，报告以冻结首页为准
- 30 Days不是过去24小时互动增量。赞/浏览是平台累计计数字段，不是独立人数、学术质量或可复现性评分；跨日差值也只表示两快照的字段差，无法识别流量来源或审核调整
- 逐篇区分arXiv版本、alphaXiv条目版本、Zenodo版本和仓库提交。尤其自定义alphaXiv slug不是arXiv编号，不能把条目更新时间当论文首发或修订。新入前10也不等于新论文
- 本报实际读取论文正文、方法、实验、讨论及所列关键附录，结合静态源码与项目资源核查。没有运行未知源码、训练模型或独立复现实验。公开演示、作者验证与独立复现是不同证据；未核内容均标明

### 冻结前10

| Hot名次 | 论文 | 赞 / 浏览 | 相对昨日同口径前10 |
|---:|---|---:|---|
| 1 | [Correction Training for Diffusion Models](https://www.alphaxiv.org/abs/2610.correction-training-diffusion-models) | 25 / 477 | 新入本次前10 |
| 2 | [Vela: User Behavior as Supervision Sparks LLM Intelligence](https://www.alphaxiv.org/abs/2610.vela-user-behavior-supervision) | 12 / 145 | 新入本次前10 |
| 3 | [Designing Protein Structures from Natural Language](https://www.alphaxiv.org/abs/2610.13917) | 15 / 251 | 新入本次前10 |
| 4 | [Scaling Empowered Agents](https://www.alphaxiv.org/abs/2610.13002) | 21 / 184 | 新入本次前10 |
| 5 | [RSI-Anything](https://www.alphaxiv.org/abs/2610.13912) | 63 / 1,080 | 1→5 |
| 6 | [ReplaySSM](https://www.alphaxiv.org/abs/2610.13778) | 41 / 878 | 4→6 |
| 7 | [Thinking Inertia](https://www.alphaxiv.org/abs/2610.11765) | 33 / 664 | 2→7 |
| 8 | [Anomaly Detection in LLM-Based Systems: A Survey](https://www.alphaxiv.org/abs/2610.anomaly-detection-llm-systems) | 7 / 49 | 新入本次前10 |
| 9 | [Is Forgetting in Post-Trained Language Models Just a Shift in Vocabulary Bias?](https://www.alphaxiv.org/abs/2610.language-model-forgetting-vocabulary-bias) | 5 / 48 | 新入本次前10 |
| 10 | [MagicBeanStalk](https://www.alphaxiv.org/abs/2610.12659) | 34 / 322 | 10→10 |

**4篇连续、6篇新入前10。** 连续论文压缩背景，保留七项评价，并优先记录新增材料或“没有新变化”。完整跨日基线、离开前10的论文和计数差见末尾C节。

## #01｜Correction Training for Diffusion Models

### 1. 作者、领域与版本

- 作者：Donghoon Ahn、Runqian Wang、Alexei A. Efros（UC Berkeley）；Taesung Park、Yash Belhe（Reve）
- 领域：扩散/流匹配图像生成、推理时迭代修正；arXiv 官方分类为 cs.AI
- 官方 arXiv：**2610.14136v1，2026-10-09 13:31:52 UTC / 北京21:31:52首发**，本次官方历史仅显示 v1，未核到后续修订。alphaXiv 自定义 slug 页显示 Submitted 2026-10-13、v1，这是平台显示时间，不能替代 arXiv 首发日。作者旧项目页仍写 arXiv Coming soon，但官方 arXiv 已可访问，以官方记录为准
- 版本一致性缺口：alpha与arXiv的标题、作者和已核主结果一致，但未取得alpha PDF做逐页/字节比对；无法确认两入口全文完全相同
- 阅读版本：arXiv v1，50 页；[官方元数据](https://arxiv.org/abs/2610.14136)、[HTML 原文](https://arxiv.org/html/2610.14136v1)、[原文 PDF](https://arxiv.org/pdf/2610.14136v1)、[alphaXiv](https://www.alphaxiv.org/abs/2610.correction-training-diffusion-models)

### 2. 具体解决什么问题

训练时，去噪器看到的是“真实图片 + 人工噪声”；生成时，它看到的是此前自身预测产生的中间状态。早期形状错误可能被后续步骤不断细化而非纠正。单纯增加积分步数主要改善数值误差，不能保证修复模型误差；常用 CFG 虽改善画质，也可能减少多样性、增加过饱和。作者尝试直接训练一个会修改模型自身预测的 corrector。[原文 §1–2](https://arxiv.org/html/2610.14136v1)

### 3. 方法、数据流及与 baseline 的差异

1. 从真实图像 x、噪声和时间 t 构造 noisy state；去噪器 D 输出当前的“干净图像预测”
2. corrector C 接收 D 的预测、原时间与条件，仍用同一真实图像 x 监督。传入预测经过 stop-gradient，因此 correction loss 不沿此路径更新独立去噪器；D 仍接受自己的 denoising loss。主要实验从公开预训练模型复制出 D/C，再联合微调
3. 训练只监督一次 correction。推理时，每个去噪步骤先调用 D，再固定噪声时间重复调用 C 共 K 次；将最后一次修正结果交给原采样器，推进到下一个噪声水平
4. K 增大增加调用次数，因此 matched-NFE 实验相应减少去噪步数。它不是“零算力的后处理”，也不是简单把网络加深一次
5. 可让 D/C 共享主干、只保留轻量输入模块；也可把多次修正后的 teacher 预测蒸馏回原结构 student，把额外计算移到训练阶段

与 baseline 的关键差异是“学习修改自己的预测并复用 corrector”，而不是仅改变采样器、增加 CFG 强度或额外输入原 noisy state。实际实现针对 ε/v/x prediction 做适配，不能把论文简化示意式直接当成每个模型完全相同的实现。[原文算法 1–2、§2.3–2.4、§3.3、附录 B](https://arxiv.org/html/2610.14136v1)

### 4. 创新主张与证据边界

- **单步监督可以支持多次推理修正**：跨 DiT、SiT、SiT-REPA、JiT 有正面结果；但 K 并非越大越好，过度修正会损失细节、多样性，甚至放大不自然纹理
- **收益不只是额外参数**：相同参数/层执行预算实验支持反复修正更有效，但 NFE/层执行数仍不等于端到端墙钟时间、显存和能耗完全相等
- **可能缩小训练—推理分布差距**：分类器更难区分真实加噪状态与生成状态，支持这一解释；与此同时训练分布上的平方重建误差可能升高。因此它是经验支持的机制假说，不是完整因果证明或理论保证

### 5. 实验、消融、成本与未支持之处

**原文表 1，ImageNet-256，FID@50K，越低越好，约 250 NFE：**

| 模型 | Unguided | Correction，无 CFG | CFG reference |
|---|---:|---:|---:|
| DiT-XL/2 | 9.58 | 2.07 | 2.51 |
| SiT-XL/2 | 8.55 | 1.92 | 2.11 |
| SiT-REPA-XL/2 | 5.53 | 1.31 | 1.35 |
| JiT-L/16 | 14.86 | 2.96 | 2.35 |

这支持“稳定改善 unguided”，不支持“所有模型都胜过 CFG”。DiT precision：0.668→0.811，CFG 为 0.818；recall：0.676→0.603，CFG 为 0.581。画质与覆盖率有权衡，不能说相对 unguided 完全不损失多样性。[PDF p5 表1](https://arxiv.org/pdf/2610.14136v1#page=5)

- 无条件 SiT-REPA：FID 24.82→5.37（K=4），autoguidance 9.37；recall 为 0.699→0.595，autoguidance 0.630。均 250 NFE、50K additional updates（[表2，p7](https://arxiv.org/pdf/2610.14136v1#page=7)、[表14，p25](https://arxiv.org/pdf/2610.14136v1#page=25)）
- 文生图、同 checkpoint、约 matched NFE：无 CFG 的 GenEval 28.30→50.09，DPG-Bench 70.71→76.82（250→245 NFE）；CFG w=4 时 68.08→70.48、83.38→83.69（250→246 NFE）（[表3，p8](https://arxiv.org/pdf/2610.14136v1#page=8)、[表13，p25](https://arxiv.org/pdf/2610.14136v1#page=25)）
- 参数控制：D28 675M 参数与 D14+C14 681M 参数，同为 6,720 层执行。FID@8K 为 8.93 vs K=1 的8.74；将 K=3、步数240降到120，FID为5.66。另一个同有效深度实验 D7+C7 346M 对 D28 675M，FID@50K 4.21 vs4.88（[表7，p10](https://arxiv.org/pdf/2610.14136v1#page=10)）
- 组件消融 JiT-B/16：输出空间修正、stop-gradient、单次训练，在 K=3 时 FID 13.35；无 stop-gradient 的最佳 K=2 为12.88，但 K=5 恶化到28.92；隐藏状态迭代到K=5为339.93。支持“输出空间迭代有效、stop-gradient更稳健”，不支持 stop-gradient 在所有配置上必然最优（[表10，p20](https://arxiv.org/pdf/2610.14136v1#page=20)）
- 蒸馏：SiT teacher 1.35B、249 NFE、FID1.92；student 0.68B、83 NFE、FID2.26；同 student 250 NFE时2.04。是约67%少调用换来接近而非完全相同质量（[表6，p9](https://arxiv.org/pdf/2610.14136v1#page=9)）
- 人类偏好：80个GenEval单物体prompt，每项800票；quality60.75%、diversity60.25%偏好correction。对照 CFG w=6，而实验方案 w=4、K=8，不能将它解释为仅有一个变量变化的严格消融（[表4，p9](https://arxiv.org/pdf/2610.14136v1#page=9)、[附录C.3](https://arxiv.org/html/2610.14136v1)）
- 训练成本：ImageNet额外50K–100K updates，batch256或1024；T2I额外50K updates、batch1024。SiT独立D+C约1.35B参数，共享版约0.68B。未找到明确GPU型号×小时或端到端吞吐对比，不把“1.25%额外更新数”换算成“1.25%总训练成本”。[表12，p24](https://arxiv.org/pdf/2610.14136v1#page=24)

其他限制：结果集中在256×256及所测模型；视觉图中有固定步数而非固定NFE的比较；CDF/FID改进不是所有复杂提示词、审美或安全指标都提升的证据。[原文 §3–4、附录 A–C](https://arxiv.org/html/2610.14136v1)

### 6. 为什么传播

冻结榜第1，25赞、477浏览。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

作者在 alphaXiv 留有项目/代码链接，是可核验的发布行为；简单的纠错循环和直观图像对比可能有助于理解，但这只是传播潜力判断，不能当作榜单热度的因果证据。[作者项目页](https://sunovivid.github.io/correction-training/)

### 7. 代码、资源门槛与工程价值

- [官方仓库](https://github.com/sunovivid/correction-training) README 本次核到：**采样、训练及文生图代码仍 Coming soon**；已有下载工具，以及 JiT、SiT、SiT-REPA 的[公开 checkpoint release](https://github.com/sunovivid/correction-training/releases/tag/imagenet-checkpoints-v1)。checkpoint 不含 optimizer restart state，不能标注为完整可复现实验包
- 适合有扩散模型训练/评测设施的团队试验；普通应用层工程师当前更适合读算法与接口位置、等待代码，而不是承诺一键复现
- 对 agent/RAG/coding/MCP：没有这些任务的直接实验。可借鉴“在会累积错误的中间产物上训练纠错器”这一设计思想，但不能直接推断对工具调用、代码或文本推理有效。对包含图像生成的全栈产品，最值得测的是质量、多样性、延迟、显存的联合曲线

## #02｜Vela: User Behavior as Supervision Sparks LLM Intelligence

### 1. 作者、领域与版本

- AllSpark Team；官方仓库明确为 **AllSpark at Xiaohongshu**。Yang Xiao、Yusong Sun共同一作；Chengyue Jiang为project lead。其他作者：Haoyi Wu、Wenyang Hui、Weiqiang Hang、Luqing Wang、Zejian Wang、Zirui Tu、Jingsheng Mao、Shaobo Hu、Yang Luo、Jiale Guo、Jin Zhang、Yudan Liu、Zhaokai Luo、Ren Huan、Yao Hu、Wenjie Li、Chuan Mu。alphaXiv标有香港理工大学，不据此把全部作者归到该校
- 领域：用户建模、行为监督、SFT/RL、长上下文个性化；arXiv cs.CL、cs.AI
- 官方 **arXiv:2610.14709v1，2026-10-10 08:28 UTC / 北京16:28首发**；本次官方历史仅v1。手稿首页日期2026-10-07；alphaXiv显示2026-10-13、v2。这三种日期/版本分别是手稿署日、arXiv记录及平台标签，未核实映射关系，不能合并为“arXiv v2修订于10/13”
- 版本一致性缺口：alpha PDF文本与arXiv v1的关键方法/主表数字相符，但未完成两份全文逐页比对；alpha v2具体修改内容仍未核实
- [官方元数据](https://arxiv.org/abs/2610.14709)、[22页原文PDF](https://arxiv.org/pdf/2610.14709v1)、[原文HTML](https://arxiv.org/html/2610.14709v1)、[alphaXiv](https://www.alphaxiv.org/abs/2610.vela-user-behavior-supervision)

### 2. 具体解决什么问题

个人助手、推荐和广告任务需要从一个人跨周到跨年的行为中找证据、判断偏好变化并预测后续行为；只训练静态文本或合成答案，未必学到这种能力。Vela的问题是：如何把杂乱真实行为变成可监督、可评分的训练任务，以及这种训练是否只改善用户任务、还是也帮助通用能力。[原文 §1](https://arxiv.org/html/2610.14709v1)

### 3. 方法、数据流及与 baseline 的差异

1. 输入为10万用户的匿名时间序列：浏览、搜索、购买、发帖、关注、不喜欢。作者称已移除直接标识及含PII记录，并获平台授权、隐私/伦理审查；这不等于无再识别风险或差分隐私保证
2. 按72K–120K tokens切段，约前2/3可见、后1/3隐藏；不切断完整行为记录。91模板构造10万组合任务：28 Objective、22 Open-prediction、12 Open、29 Attribution
3. 预测类的答案来自真实未来行为，Objective精确匹配，Open-prediction先语义归一再算set-F1；Open/Attribution用依据历史的rubric评分。Attribution会披露未来事件，因此同一未来事件不能同时出预测题，避免泄漏
4. base模型每题出4答案，平均分在[0.2,0.8]才保留。再由teacher生成4条轨迹，仅选最高分且超过过滤均分的轨迹。Vela-Instruct约75K条，由Qwen3.8-2.4T-A95B生成；Vela-RFT 9,375条，由base自己生成。两者不能当成等量数据的teacher/self比较
5. 微调Qwen3.6-35B-A3B；推理仍为给历史/问题生成答案，不需要在线访问“隐藏未来”。随后另做GSPO，比较base或18.8K样本Vela SFT checkpoint作为起点

主要baseline是未做Vela微调的同一base；P5、RLPF是相关工作，论文未做同计算量直接对打。关键工程资产是时间切分、答案隔离、模板/评分器和轨迹筛选管道。[原文 §2–4](https://arxiv.org/html/2610.14709v1)

### 4. 创新主张与证据边界

- **真实行为可成为跨任务监督信号**：五个用户基准上，主模型均提升；未用等量通用/纯合成SFT数据控制，不能断言真实行为本身优于其他所有监督源
- **收益扩展到通用能力**：五个通用基准主模型均提升，但平均数混合了不同任务指标；不能等同一个统一“智力分数”
- **帮助后续RL**：相同RL数据/配置下Vela起点更强，支持该checkpoint是更好的起点；不证明每种行为数据或每种RL算法均适用

### 5. 实验、消融、成本与未支持之处

原文表1：VelaBench为982个held-out任务，训练/评测用户分离；但与训练共用91模板，所以属in-domain。主要结果如下，均为base→75K Vela-Instruct：

| 基准 | Base | Vela | 差值 |
|---|---:|---:|---:|
| VelaBench | 51.5 | 63.0 | +11.5 |
| PurchaseIntent（recall@20） | 43.8 | 44.0 | +0.2 |
| ProfileSummary（rubric） | 20.4 | 30.5 | +10.1 |
| PersonaBench（macro-F1） | 50.0 | 53.2 | +3.2 |
| AdRecommendation（rubric） | 51.1 | 62.3 | +11.2 |
| 用户OOD均分 | 41.3 | 47.5 | +6.2 |
| AIME 2026 | 91.8 | 92.6 | +0.8 |
| GPQA-Diamond | 82.8 | 87.4 | +4.6 |
| IFBench | 62.5 | 69.2 | +6.7 |
| CL-bench | 26.7 | 29.1 | +2.4 |
| CL-bench Life | 7.2 | 12.8 | +5.6 |
| 通用OOD均分 | 54.2 | 58.2 | +4.0 |

大模型参照并非全输：例如VelaBench Kimi-K3为64.0，高于Vela63.0；用户OOD均分Kimi50.7、Qwen3.8 49.5也高于47.5。Vela-RFT通用均分保持54.2，但GPQA82.8→80.8、CL-bench26.7→26.0，不能把“平均不降”写为“全部不降”。[PDF p6 表1](https://arxiv.org/pdf/2610.14709v1#page=6)

- **数据量（图5）**：4.7K→75K，VelaBench59.2→63.0；用户OOD43.5→47.5，但37.5K时47.6；通用OOD18.8K时59.0高于75K的58.2。只支持总体收益与局部饱和，非所有指标严格单调。[图5，p7](https://arxiv.org/pdf/2610.14709v1#page=7)
- **过滤消融（表2）**：37.5K样本量匹配，有/无难度过滤的VelaBench同为62.4；PurchaseIntent44.6→45.4，ProfileSummary29.0→30.5，PersonaBench51.5→52.7，AdRecommendation61.0→61.9，四项平均约+1.1。轨迹生成、接受标准与SFT设置相同。[表2，p9](https://arxiv.org/pdf/2610.14709v1#page=9)
- **RL（图6）**：Vela起点VelaBench61.9→66.2，base51.5→58.5；ProfileSummary Vela30.5→37.6，base20.4→29.9。两组RL最终相差7.7。**base→RL本身也提升**，只是最终低于Vela SFT/RL起点/结果；alpha概述中“base RL低于其自身pre-RL”的说法不符合原图。[图6与§4.1，p8](https://arxiv.org/pdf/2610.14709v1#page=8)
- **成本**：SFT用Swift，packed length131,072、2 epochs、learning rate1e-5。附录E：RL总48 GPUs，32训练/16 rollout，GSPO每prompt16响应、400 configured rollout iterations；使用Megatron-LM与SGLang。GPU型号、总GPU小时及大量teacher生成/评分费用未见完整核算。[§3.1，p6](https://arxiv.org/pdf/2610.14709v1#page=6)、[附录E表4，p22](https://arxiv.org/pdf/2610.14709v1#page=22)
- **公平性**：多项开放评分与数据生成共用Qwen3.8 teacher/scorer，存在需额外独立评审检验的同源评估风险；没有对通用合成SFT作等token/等算力实验；未提供线上用户满意度、真实agent工具成功率或长期干预实验。主结果表未给置信区间，0.2分的小幅变化不能自行宣称统计显著

### 6. 为什么传播

冻结榜第2，12赞、145浏览。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

“用户行为能改善通用模型”和“35B模型对比更大模型”是醒目的论文主张，但未核得足以解释热度的公开转发链或流量归因。

### 7. 代码、资源门槛与工程价值

- [官方仓库](https://github.com/AllSpark-Research/Vela) 当前实际公开**74个选定模板**（23 Objective/18 Open-prediction/9 Open/24 Attribution）、中英文composer/scorer prompts及论文。74是91中的子集，不能说全部模板、10万用户原始记录、75K轨迹和完整训练/评测代码已公开
- **可立即借鉴**：用获得授权的历史日志做离线时间回放测试，建立“过去可见、未来只给评分器”的数据契约；将无证据的偏好推断列为评分失败。无需先复现35B/48GPU训练，先用模板评估现有助手
- **agent/RAG**：高相关，尤其长期记忆检索、过时偏好、证据归因；但论文没有证明RAG结构或MCP能力本身被改善。归因解释是“历史支持”而非因果结论
- **coding/MCP/full-stack**：可将前端用户反馈、事件日志、检索证据与离线评测闭环接起来；这些是本文启发的工程建议，不是已测收益。采用真实行为需先处理授权、数据最小化、保留周期、用户级切分及访问控制

## #03｜Designing Protein Structures from Natural Language

### 1. 基本信息与阅读范围

- 作者：Joseph Lee、Yanjing Li、Bo Qiang、Gregory Lau、Allyson Ettinger、Noah A. Smith、Rory Donovan-Maiye、David Baker、Hanna Hajishirzi、Pang Wei Koh；主要机构为 University of Washington、National University of Singapore、Ai2、HHMI
- 领域：机器学习 × 蛋白质结构生成，arXiv 分类 cs.LG / q-bio.BM；模型名 Prompteina
- arXiv 首发：2026-10-09 17:51:55 UTC / 北京10月10日01:51:55，v1；当前修订：2026-10-13 04:11:41 UTC / 北京12:11:41，v2；54 页、9 图。本文解读采用 v2，不能把 10 月 13 日写成论文首次发表日，也不声称正式同行评审已完成
- [alphaXiv 条目](https://www.alphaxiv.org/abs/2610.13917)；[arXiv 版本记录](https://arxiv.org/abs/2610.13917)；[v2 完整正文](https://arxiv.org/html/2610.13917v2)；[项目页](https://jxlee.me/prompteina/)
- **v2真实变化：** 对版本化v1/v2全文正文做归一化文本比较，确认v2新增Table22「Target-level head-to-head win rates」，是原20目标的逐目标胜率统计；“各baseline至少13/20目标领先”限于self条件，MPNN重设计时对部分baseline仅赢9–12/20；后续表号调整。主文明确写出top-8增益57%，但其依据+0.105/+0.067已在v1旧Table29中，GM2A的107nM、89受测/9结合也在v1已有。未见公开changelog，未做图像或源码级全面差异审计；因此不将这些旧结果说成v2新实验。[v1](https://arxiv.org/html/2610.13917v1) · [v2附录G](https://arxiv.org/html/2610.13917v2#A7)
- 阅读覆盖：摘要、引言、§2 方法、§3 全部实验、§5 讨论，以及附录 B/C/D/E/F/G/H/I 的关键数据、算力、消融、评价校准和实验验证。v2 HTML 已完整获取；目视检查图 2 方法结构与图 6 实验结果。v2 PDF 抓取失败，但不影响已获取版本化 HTML 的正文核验

### 2. 它解决什么具体问题

现有结构生成器通常为每种要求单独定义输入：一种标签表示折叠类别，一串逐残基标签表示二级结构，另一些格式表达局部约束。这样的接口容易丢掉上游 agent 通过文献研究得到的丰富设计意图。

Prompteina 的研究问题是：能否把全局性质和局部结构性质放进一个自然语言条件接口，并让结构生成器本身学会这些文字与输出结构的对应关系？它不是仅让聊天模型给已有程序写参数，也不是只生成序列后再折叠。作者让专用模型联合生成序列与全原子结构。本文是文献评价，不提供生物实验操作配方。[§1–2](https://arxiv.org/html/2610.13917v2#S1)

### 3. 工程师视角：输入、组件、数据流与训练/推理

1. 数据侧：从 PDB、AlphaFold Database 和 Teddymer 取得约 180 万条按链计数的结构条目，抽取数据库及几何性质，再由 Qwen3-235B-A22B 将不同属性子集写成文本，得到 5240 万条 captions。Table 5 分别是 PDB 61.1 万条/1950 万 captions，AFDB 28.87 万/750 万，Teddymer 90.3 万/2540 万；“180 万结构”不能简单等同于 180 万个独立实验测得蛋白
2. 表示侧：冻结 Qwen3-Embedding-8B 产生 pooled 文本向量，经 AdaLN 给所有残基提供全局信号；冻结 Qwen3-8B 产生 token states，通过新增 cross-attention 给不同残基提供局部信号。Complexa 去噪器生成骨架坐标与侧链 latent，冻结 VAE 将其解码为全原子结构和氨基酸序列
3. 对齐侧：用规则和 TF-IDF 匹配 caption 的短语与已有残基注释，形成稀疏 token–residue 对齐监督；没有可靠匹配的样本仍可用于文本条件训练，但不强行加对齐标签
4. 训练侧：先冻结去噪器，热启动文本模块；再解冻做 flow-matching 持续预训练；随后主要对文本投影和晚层 cross-attention 的 value/output 路径做对齐微调；binder 阶段继续训练。对齐头仅用于训练，推理无需保留它
5. 推理侧：输入自然语言、长度；binder 任务另提供目标结构与可选接触条件。模型在条件去噪过程中直接读文本，通过 classifier-free guidance 调节条件强度，最后输出结构和序列
6. agent 侧：先研究目标，得到可复用 dossier；再依据各模型支持的接口生成规格；结构生成与独立预测器评价之后，把历史规格和分数送回 agent 进行下一轮计划。静态代码中 research 与 expand 是分离的，dossier 在模型之间复用；目标查询工具把几何/数据库事实压缩成结构化文本，避免直接把海量坐标塞入上下文

与 baseline 的核心差别：Chroma(text) 用外部结构描述器在推理时引导；Pinal/BioMatrix 先产序列再用 ESMFold 折叠；Prompteina 将文本条件直接训练进全原子生成模型。不能把这项差异全部归因为“自然语言比 JSON 好”：训练数据、条件容量和底层模型也变了。Table 9 有同底座、同结构数据、同训练预算的专门标签对照，能局部支撑双通路条件设计，但不能替代整个系统的等资源比较。[§2、App. B–D](https://arxiv.org/html/2610.13917v2#S2)；[agent 代码](https://github.com/jleechung/prompteina/blob/main/src/proteinfoundation/agent/design_agent.py)；[工具封装](https://github.com/jleechung/prompteina/blob/main/src/proteinfoundation/agent/target_tools.py)

### 4. 最值得注意的 3 个贡献：主张与证据分开

- 广而可组合的条件接口：作者主张一套语言接口支持比任一 baseline 更广的结构要求。证据是 18 个任务中 15 个领先，涵盖全局与局部性质；但 RFdiffusion 的 strand/sheet 数量控制更好，因此不能写“所有结构任务全面超过专用方法”
- 细粒度文字–对象对齐：Table 10 对齐前后二硫键数量相关系数由 0.054 到 0.294，盐桥由 0.566 到 0.663；CATH class 94.0%→96.0%，architecture 55.5%→51.1%。这是有代价的局部控制改善，非所有指标同时上升；顺序微调额外用了训练步数，不能等同严格同算力消融
- 更宽的工具接口使反馈更可执行：相同 agent 的迭代搜索在难目标上取得更大代理分数增益；另外提供了单个目标 GM2A 的前瞻实验验证。前者证明的是计算评价改进，后者才提供实际结合证据；两类证据不能混写成“20 个目标都经实验验证”

### 5. 实验数字、消融、成本与证据边界

| 问题 | 精确结果与出处 | 如何解读 |
|---|---|---|
| 结构控制 | Table 1/11：18 项中 15 项领先；CATH class 96.0%±3.0，Proteina 96.7%±3.0；CATH architecture 51.1%±1.6，Proteina 27.5%±1.4；strand/sheet 的 Spearman ρ 为 0.88/0.64，RFdiffusion 为 0.92/0.82 | 同文字 baseline 用相同 prompts；专用 baseline 用原生结构化输入，只比较其支持的属性。误差为文中定义的 bootstrap 区间，不能据数值大小直接断言所有差异显著 |
| 功能描述 | Table 2：122 个家族、4 类提示，每类每家族 50 个设计；置信度加权 ProTrek sequence similarity 7.12±0.88，Pinal 5.98±0.70，BioMatrix 3.70±0.58 | ProTrek 是相似度代理，不是实际功能测定。附录 F 说明，与 Pinal 的加权结构相似度差异置信区间仍跨 0；未加权两项差异也未解决。不能写“已证明功能更强” |
| binder 比较 | Table 3：20 个目标，每方法每目标 200 个设计。self 条件 expected top-k ipSAE_min：0.455 对 Complexa 0.400；MPNN：0.584 对最强 baseline 0.577；MPNN-FI：0.549 对 0.510 | 摘要“14%提升”约对应 self 的 13.75%相对提高，不是所有序列条件统一提升14%。MPNN后优势明显缩小；App. G.5 中极小或较大保留预算下其他模型可领先 |
| 接口内容消融 | Table 4：fold-only 0.362；fold+shape 0.364；再加 interface 属性 0.455，均为 self expected top-k ipSAE_min | 改善主要来自接口允许表达的属性，而非仅给模型加一个 agent。三个设置都是20目标、每目标200设计 |
| 迭代反馈 | Table 30：每目标4轮×50个设计；最难7目标 top-8 增益 Prompteina +0.105，BoltzGen +0.067，RFdiffusion3 +0.028；0.105/0.067−1≈56.7%。全20目标 top-1 改善17/20，top-8改善20/20 | “57%”是相对非迭代基线的增益之比，不是命中率增加57个百分点；难度分组由 i.i.d. 结果定义，附录另做不重叠子集检查 |
| 实验验证 | §3.3、Fig. 6：生成1000个候选，选90个测试，89个成功表达并进入SPR检测；9个被判定结合，8个有拟合 apparent K_D；6个亚微摩尔；最强跨3次重复的总体 apparent K_D 为107 nM | 9/89是被检测集合的结合计数；文中6.7%指6个亚微摩尔候选/90个送测，不可混为同一分母。Fig.6中68.8 nM只是最强候选的一次重复，不能替代107 nM总体值 |

公平性与未证实之处：

- binder 比较对各方法采用相同长度分层、相同候选数、相同研究 dossier，并在 self、完整序列重设计、固定界面重设计下评价；这是有价值的控制。不同模型的底座、采样成本、可表达属性并不相等，200个候选相同不代表 GPU/API 总成本相同
- ipSAE_min 的校准资料并非完全独立：部分资料已被旧过滤规则使用，另一组曾按同类分数筛选；作者因此使用连续分数和不依赖阈值的统计。校准主要来自单链目标，对多链目标的推广和新 campaign 绝对命中率仍未建立
- 文本数据质量只抽80条 caption 由 LLM judge核验；报告 precision 89.8%、recall 97.8%，不能据此认为5240万条无错误
- App. C 报最终模型训练约12900 H100-equivalent GPU-hours，约一台8×H100节点67天；不含消融、数据建设或评价。caption 生成另估约3700 H200 GPU-hours，两者硬件口径不同不直接相加
- 功能控制大部分是代理分数；实验仅覆盖一个目标的精选候选，不构成多目标实测 superiority、治疗有效性或安全性证明。本次未发现独立复现，且没有运行任何实验

来源：[v2 实验与表1–4](https://arxiv.org/html/2610.13917v2#S3)、[附录 F](https://arxiv.org/html/2610.13917v2#A6)、[附录 G](https://arxiv.org/html/2610.13917v2#A7)、[附录 H](https://arxiv.org/html/2610.13917v2#A8)、[图6](https://arxiv.org/html/2610.13917v2/figures/fig3.3.png)

### 6. 热度与传播：能确认什么

冻结Hot / 30 Days第3，15赞、251浏览；代码仓库在本次读取时显示24 stars、2 forks，只是时点快照。检索出现一些转述/自动摘要页面，但未找到足以把某次传播事件、讨论观点或流量来源与本次排名建立联系的直接证据。项目演示、自然语言到蛋白结构的叙事和实验验证可以解释“为何值得关注”，不能据此断言它们就是“为何走红”。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

### 7. 代码状态、门槛与对 agent / RAG / coding / MCP / 全栈的价值

- [代码](https://github.com/jleechung/prompteina)已公开；README 提供生成、评价、agent、训练入口。许可证分开：代码 Apache 2.0，模型 NVIDIA Open Model License，仓库数据资产 CC BY 4.0，不能统一写成“全部Apache”
- [模型文件](https://huggingface.co/jleechung/prompteina/tree/main)可见 monomer/binder 两个 checkpoint，约1.86/1.85 GB，共3.71 GB；[模型卡](https://huggingface.co/jleechung/prompteina)明确这些是 inference-only，不能恢复训练，另需下载基础autoencoder和文本编码器
- [训练数据](https://huggingface.co/datasets/jleechung/prompteina-data)仍显示 empty / preparing for public release。公开训练入口与论文附录不能弥补完整数据未发布，因此目前适合读代码和尝试推理，不能称作已具备完整从头复现实验包
- 环境门槛：README要求Python 3.12、CUDA 12.6；仅两个冻结文本编码器就约32GB显存，完整推理另有模型与结构开销。编码后可offload文本模块，但README没有给出端到端最低显存保证。ESMFold2/AlphaFold3评价后端需另行安装
- 对用户最直接的价值是 agent 工程：可读 [design_agent.py](https://github.com/jleechung/prompteina/blob/main/src/proteinfoundation/agent/design_agent.py) 的“研究一次、跨工具复用 dossier、按工具能力生成规格”架构，以及 [target_tools.py](https://github.com/jleechung/prompteina/blob/main/src/proteinfoundation/agent/target_tools.py) 的领域事实查询封装。静态代码核验了 research/expand分离、可复用dossier、方法专属能力文件和输出契约；这是可以迁移到代码生成、数据分析工具链的设计模式
- 对 RAG/MCP/全栈的迁移是推论：让检索证据、工具能力说明与结构化硬约束各有清晰路径，保留丰富意图，再用可验证反馈评价输出；论文没有RAG、SWE-bench、MCP协议或网页应用实验，不能宣传为这些任务的已验证提升。也不应把自由文本替代所有typed schema：身份、权限、资源上限和格式契约仍应机器校验
- 推荐深读顺序：§2.2 + Fig.2（文本通路）→ §3.2.2/Table4（接口消融）→ App.H/Table30（反馈与预算）→ agent代码。若日报最终只能选3篇，本文可作为“专用工具怎样接住agent丰富意图”的跨领域候选；普通全栈开发者不必复训蛋白模型

## #04｜Scaling Empowered Agents

### 1. 基本信息与阅读范围

- 作者：Catherine Ji、Vivek Myers、Joshua Lin、Alexandra Wingate、Sergey Levine、Benjamin Eysenbach；机构为 Princeton University 与 UC Berkeley；Joshua Lin、Alexandra Wingate标注同等贡献
- 领域：无监督强化学习、技能发现、内在动机与可控制性，arXiv cs.AI / cs.LG。标题的 agents 指在模拟环境中训练的RL策略，不是已经训练好的LLM工具agent
- arXiv 首发：2026-10-09 05:04:30 UTC / 北京13:04:30，当前仅见v1；30页、13图；未见修订版本记录，不能把日报日期当发表日
- [alphaXiv条目](https://www.alphaxiv.org/abs/2610.13002)、[arXiv版本记录](https://arxiv.org/abs/2610.13002)、[v1正文](https://arxiv.org/html/2610.13002v1)、[作者项目页](https://empowerment-geometry.github.io/scaling-empowerment/)
- 阅读覆盖：摘要、引言、§3定义、§4方法、§5全部实验、§6讨论、App.A/B/C/D的算法/预算/基线/消融；下载了v1 PDF，目视核对pp.8–9的Fig.2/3，并查看方法页。没有可读取的已公开代码实现可核验

### 2. 它解决什么具体问题

技能发现能学到多种动作，并不保证主体主动走到“接下来有更多有意义选择”的状态。精确计算任意状态的empowerment需要知道从那里能做出哪些可区分的未来，状态空间一大就难算。

SEE（Skills Estimate Empowerment）把问题拆成两部分：先用可扩展的技能学习估计某个状态的可控性，再学另一条策略去到这种估计值高的状态。例如，走近球会增加可执行的控球技能；仅原地执行一堆微小动作未必有用。这是本文区别于一般“鼓励新奇探索”或“学很多技能”的核心。[§1、§3–4](https://arxiv.org/html/2610.13002v1#S3)

### 3. 工程师视角：输入、组件、训练与执行

1. 输入不是文字，而是模拟器状态/观测、可用动作和互动轨迹；不依赖任务成就的外部奖励。技能用latent z标识，技能策略还可以读取技能开始的状态s0和当前状态s
2. 内层π_eff学技能：以CSF为基础，用InfoNCE训练分类器，判断从起点到未来状态的变化是哪个技能造成的；未来状态的时间跨度按几何分布取样，使信号跨越多步。双线性的“状态表示差×技能向量”约束让分类器不容易通过无意义细微变化作弊
3. 状态价值：对多个随机技能的价值求平均，作为该状态empowerment的估计/在理论条件下的下界；实现中用8次技能采样。不是直接枚举真实技能总数，也没有保证神经网络估计处处精确
4. 外层π_pot把此估计当内在奖励，学会去到具备更多可控后续行为的状态。每条轨迹先执行外层策略，再切换到一个技能策略，内外层共同改进
5. 实际实现有重要近似：连续任务用joint-MI变体、SAC、不同经验池和HER；Craftax用条件MI、PQN与LSTM，并从复制的模拟器状态额外分支采样。连续分类器训练加入噪声瓶颈；Craftax只让empowerment关注inventory，策略本身仍可看到更完整的观测
6. 训练初期先不加入完整归一化惩罚，鼓励探索，随后逐渐恢复归一化项。始终不归一化可以拿到更多游戏成就，但最终值函数就不再具备相同的empowerment下界解释

与baseline区别：VIM、LatentGCE估计的是开环动作序列控制；SEE使用闭环、可根据当前状态反馈的技能。普通MISL没有本文外层“去哪里”的策略，因此作者没有将其直接纳入主要potential-empowerment比较，而以技能切换等消融补充。这里既有算法工程差异，也有目标定义差异，不能视为只替换一个估计器的纯净对照。[§4](https://arxiv.org/html/2610.13002v1#S4)、[App.A/Algorithm1](https://arxiv.org/html/2610.13002v1#A1)

### 4. 最值得注意的 3 个贡献：主张与证据分开

- 把技能库转成状态价值，再学一个寻求好起点的策略：理论连接与双策略工程相互支撑，适合启发长时程agent架构；“适用任意技能学习方法”是通用配方主张，本文具体实验主要建立在CSF式学习上，并未系统测遍所有技能算法
- 在较大的离散和连续模拟环境展示资源收集、工具使用、环境改造：Craftax出现“房屋”式围挡、制作工具和生存行为；Fig.5的“房屋”由植物和工作台组成，定性示例不能夸张为学会现实建房或通用规划
- 消融主动暴露指标投机：高MI并不自动等于有意义行为。世界表示、分类器表达能力和归一化决定策略学到什么；这比“自发涌现智能”口号更值得工程师读

### 5. 实验数字、消融、成本与证据边界

| 问题 | 精确结果与出处 | 如何解读 |
|---|---|---|
| 离散开放世界 | §5.1/Fig.2：Craftax-Classic在约10亿live环境步后每条rollout完成22项成就中的7–8项；5个训练种子、128个随机评估环境；训练曲线延伸到20亿步 | 作者与既有文献约5.5项比较，不是本图中统一重跑所有探索baseline；不属于LLM benchmark |
| 连续控制 | Fig.3：Ant、AntSoccer、BuilderBench；SEE/LatentGCE各5种子，VIM 3种子，128个随机评估环境；观察state visitation以及外层结束时距中心/球/方块距离 | 图形支持SEE在多个任务中学到所需行为；BuilderBench距离曲线有明显波动和区间重叠，不能编造整齐的统一提升百分比。VIM的访问格子多也不等于可靠的外层控制 |
| 预算 | App.B Table1：Ant/AntSoccer每种子5亿步，BuilderBench1亿步；外层/技能阶段100/300步 | “scalable”指能在更高维任务训练成功，不表示少量样本、廉价训练或低延迟产品化 |
| 隐含模拟成本 | App.B Table2：Craftax每种子20亿live步，外层/技能100/900步；每live步另有0.9个编码器分支模拟步，未计入live-step预算 | 20亿live步约对应额外18亿分支步，合约38亿模拟步/种子，仅按表中比例推算；因此相同live预算不等于相同总模拟成本。未找到可核验GPU小时、硬件总价或墙钟训练时间 |
| 归一化消融 | App.A.3/D.4/Fig.12：不归一化λ=0可超过9项成就；全程归一化学到更少；逐渐归一化换取更符合empowerment解释的最终估计 | 论文不是直接把游戏成就刷到最高的算法；理论可解释的量与外部任务表现之间存在取舍 |

关键消融与公平性：

- 不在同一rollout中从π_pot切换到技能，内层仍可从初态学技能，但外层找好起点变得不稳定；说明覆盖到外层实际到达的起点很重要
- 条件MI在Craftax更强；连续Ant中可能对起点和细微扰动过拟合，产生高MI但贫乏行为；joint-MI在连续任务更实用，代价是离理想定义更远
- 更自由的分类器反而训练更不稳；连续任务的噪声瓶颈、经验池分离、HER都有实际作用，HER也被作者承认会引入偏差/部分技能坍缩
- 连续任务baseline是作者重新实现：VIM无完整公开代码，LatentGCE公开实现不含论文的全部latent版本。作者在简易pendulum/ball-in-box验证实现，并给相同主训练步数，但控制器PPO与SEE的SAC不同，网络大小不同，VIM更短的probe horizon（30对LatentGCE100），种子数也不同；不能断言所有原算法充分调优或算力严格等价
- Fig.4轨迹示意为一个种子、四个技能分支；Fig.5各行为为单种子例子，附录有更多例子。它们说明“观察到行为”，没有提供房屋建造成功率或跨任务泛化的完整统计
- 成就评价在整个两段rollout上统计，不能全部归功于外层策略独自完成。inventory等关注维度由人挑选，因此“无需成就奖励”不等于没有人为归纳偏置
- 独立复现未确认；未涉及语言理解、网页工具调用、RAG检索、编码成功率或MCP互操作性。作者讨论也承认对世界表示敏感、工程设计仍可简化

来源：[正文§5与图2–5](https://arxiv.org/html/2610.13002v1#S5)、[App.A–D完整正文](https://arxiv.org/html/2610.13002v1)、[v1 PDF](https://arxiv.org/pdf/2610.13002v1)

### 6. 热度与传播：能确认什么

冻结Hot / 30 Days第4，21赞、184浏览；作者项目页有行为动画与图表。但本次检索没有获得足够的作者发帖互动、独立讨论、流量或转发链证据来解释排名。不能把“agent会自发建房”这一易传播叙事当作已证实的热度原因。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

### 7. 代码状态、门槛与对 agent / RAG / coding / MCP / 全栈的价值

- [项目页](https://empowerment-geometry.github.io/scaling-empowerment/)在读取时明确标注“Code (coming soon)”；其真实代码链接[github.com/cj7280/scaling-empowerment](https://github.com/cj7280/scaling-empowerment)返回404。论文声称提供开源实现，不能覆盖实际访问状态；此刻只能确认伪代码、超参数和演示已公开，不能称代码已可下载/可复现
- 不提供伪造的README或实现入口。现阶段先读App.A.4 Algorithm1、App.B预算和App.D消融；项目页可看两段轨迹与演示。后续代码公开后才适合进一步核验依赖、license、默认config和复现实验脚本
- 门槛是可高吞吐运行、能复制状态并分支的模拟器，加上数亿至数十亿互动步；真实网页与外部API通常不能廉价回滚并复制状态。把算法直接搬到生产浏览器agent并不现实
- 对长期agent最有价值的迁移是推论：区分“先准备一个能做更多有用事的工作状态”和“执行某项技能”，例如先建立可验证上下文、测试环境或索引，再做后续任务；以及为“可做的事”设计受限且有业务意义的度量，避免模型只刷代理指标
- RAG可借鉴“增加下一步有用选择”的评估思路，coding可借鉴技能准备/执行的分层结构，MCP可借鉴能力描述与状态观测；本文对这些都没有直接实验。更高自主可控性不等于更符合用户目标，迁移时必须受原有任务权限、成本与安全约束，不能把“自行扩大工具权限”当成优化目标
- 推荐深读顺序：§3–4（定义与双策略）→ App.A.3（归一化/HER等现实折中）→ §5.2/App.D（高MI不等于有用）→ App.B Table2（隐藏采样成本）。如果最终选3篇偏工程实用的论文，本文偏中长期方法启发；代码尚未开放使“今天就上手”的优先级下降

## #05｜RSI-Anything: Unlocking Recursive Self-Improvement with World Models

### 1）作者、领域、版本与今日增量
Taoyong Cui、Pinxian Zeng等11位作者；PhAI Labs、香港中文大学等。世界模型与Agent递归改进。arXiv **2610.13912v1**，首发2026-10-09 17:50:30 UTC / 北京10月10日01:50:30；今日版本历史仍仅v1。昨日Hot第1，今日第5。今天新增的是**作者仓库实验室规划流程澄清**，不是新论文版本或新实验分数。[arXiv历史](https://arxiv.org/abs/2610.13912) · [alphaXiv](https://www.alphaxiv.org/abs/2610.13912) · [10月13日文档提交](https://github.com/Gen-Verse/RSI-Anything/commit/8ba44cd73ec6f57b151ec06e2f71a0726adfb687)

### 2）具体问题
真实执行候选补丁、GUI动作或科学实验才能得到反馈，但成本高；策略更新后，旧结果预测器又可能失准。要解决的是：怎样用预测挑选值得执行的候选，并仅保留有实测依据、互相兼容的系统更新。[§1–2](https://arxiv.org/html/2610.13912v1#S2)

### 3）方法与数据流
任务状态＋候选动作进入JEPA式上下文编码器和潜状态预测器，再由结果读出头打分；执行选中的候选，保存预测—观察对。反馈支持策略/工作流更新；世界模型只有在可靠性不足且数据、预算充足时适配。组件验收和组合验收都过关才替换旧版本。这里的“通用”指流程跨领域复用，不是同一个模型包办全部任务。

代码修复用固定ReasonFlux-Coder-7B每轮提出4个补丁，3B世界模型连同原程序共评5项；效用为整套测试通过概率＋0.25×预测通过比例，新候选必须严格胜过原程序才替换。当前评估文件明确写 **optimizer_steps=0**，并在600次决策封存后才开隐藏测试；不能把离线训练后的评估讲成边测边学习。[选择与封存实现](https://github.com/Gen-Verse/RSI-Anything/blob/8ba44cd73ec6f57b151ec06e2f71a0726adfb687/tasks/code_repair/src/evaluation.py)

### 4）核心亮点：主张与证据
1. 作者将预测选择、反馈学习与版本保留连接起来；能迁移的是证据和版本管理，而不只是“加一个world model”
2. 今日README补充：学习任务给四候选实测评分，训练策略并重拟合世界模型；验证集验收模型对，**与F200测试任务不重叠**；公开命令覆盖冻结推理阶段。这是作者对流程/划分的可核声明，未提供新独立复现，也不补足完整多轮训练公开执行链的证据。[更新后的规划说明](https://github.com/Gen-Verse/RSI-Anything/blob/8ba44cd73ec6f57b151ec06e2f71a0726adfb687/tasks/laboratory_planning/README.md#rsi-workflow)

### 5）实验支持什么、没支持什么
表2：200道CodeContests×3种子、最多3轮，静态verifier26.3%、固定世界模型29.2%、适配模型31.2%；在线测试调用约3.71–3.72次/题。固定模型相对静态verifier配对增益2.83个百分点，95%区间[0.17,5.50]。相同执行次数不等于相同模型推理和训练总成本。[表2/图3](https://arxiv.org/html/2610.13912v1#S3.T2)

GUI 51%→99%、动作5.30→3.21来自100个checkbox实例；公开结果说明选中控制器alpha=0，按policy排序，不能把99%直接归因于推理阶段world-model排序。实验室21.80%→46.01%是五个版本的规划评分，非真实仪器成功率；作者讨论明确还需同一任务内持续双向多轮验证。[GUI结果及交叉组合](https://github.com/Gen-Verse/RSI-Anything/blob/8ba44cd73ec6f57b151ec06e2f71a0726adfb687/tasks/gui/docs/RESULTS.md) · [§5–6](https://arxiv.org/html/2610.13912v1#S5)

### 6）热度事实与传播证据
冻结榜第5，63赞、1,080浏览；昨日第1，30赞、531浏览。名次下降与累计计数上升可以同时发生。**目前只能确认论文热度高，尚无足够公开证据解释传播原因。** 本次新增可核文档澄清不证明它导致流量增加。

### 7）工程复现与应用价值
公开代码和资源说明可读，代码修复评估档约64MB、训练补充约236MB；基础模型约6.2GB（评估）或21.4GB（完整档），不是GPU显存估算。需Linux隔离执行、模型服务和回归数据；作者打包仅运行四阶段各3步训练检查，完整epoch重训未做，参考权重严格正交/因子独立检查未通过。本日报未运行源码或独立复现。[复现范围](https://github.com/Gen-Verse/RSI-Anything/blob/8ba44cd73ec6f57b151ec06e2f71a0726adfb687/docs/reproduction.en.md)

**工程判断：** coding先做固定coder的候选排序对照；RAG将预测置信、引文核验和答案正确性分存；MCP工具结果携带状态版本与验收证据；全栈为候选配置留回滚路径和独立测试集。以上RAG/MCP建议是迁移分析，原文没有直接收益实验。

## #06｜ReplaySSM: Cache SSM Inputs, Not State

### 1）作者、领域、版本与今日增量
Ze-Wei Liou、Harris Nover、Amey Naik、Andrii Skliar、Igor Shovkun、Ido Shahaf、Tri Dao；Princeton、NVIDIA。混合SSM推理内核、投机解码与状态量化。arXiv **2610.13778v1**，首发2026-10-09 15:59:40 UTC / 北京23:59:40，未见v2。昨日第4、今日第6；今日新核的是传播/集成材料与README更新，而非实验数字更新。[arXiv](https://arxiv.org/abs/2610.13778) · [alphaXiv](https://www.alphaxiv.org/abs/2610.13778)

### 2）具体问题
SSM虽只有固定大小状态，但每个token整块读写仍吃带宽；投机解码被拒绝后恢复旧状态昂贵；低精度状态反复参与递推会累积误差。这三个问题来自把“本次输出”和“永久更新状态”绑在每一步执行。[§1、3](https://arxiv.org/html/2610.13778v1#S3)

### 3）方法与数据流
把历史表示为checkpoint＋最近输入的有界buffer。普通步骤追加新输入，从checkpoint和buffer直接算输出，不写回完整状态；buffer满才flush。投机验证只移动已接受前缀指针，拒绝部分随后覆盖；无需每个draft保存状态快照。低精度扩展将读出checkpoint和高精度递推checkpoint分离，避免低精度读出误差回流。它仍每步读取checkpoint，不能写成“免状态读取”或“消灭全部误差”。无需重新训练基础模型。[§4–6](https://arxiv.org/html/2610.13778v1#S4)

### 4）核心亮点：主张与证据
- 用同一状态表示支持少写回、指针回滚和双精度路径；区别于只在回滚时重放输入的方案
- 等价性是在浮点误差范围内；§6与表2支持减轻量化误差，不保证任意精度、模型或长度上零损失
- 已静态查看Mamba输出内核的non-flush buffer追加与flush重构分支，以及标准解码计时脚本；这比只读README更能确认实现边界。[核心kernel](https://github.com/Johnny-Liou/ReplaySSM/blob/73a9592e9d8a2268620e8883a82f5cec7442ed36/vllm/model_executor/layers/mamba/ops/selective_state_update_replayssm_output_only.py)

### 5）实验、消融、算力与公平性
图2：batch=256、window=16、FP32状态，4个模型的整步加速1.20–1.47×，kernel为1.46–1.80×；4B模型1×H100 80GB，120B级NVFP4模型1×B300。对照是调优后的vLLM、同构建且开CUDA Graph。表6中batch=1整步仅0.96–0.99×，**单请求可能略慢**；B300 batch=512部分值受1100W功耗上限放大。[图2](https://arxiv.org/html/2610.13778v1#S5.T1.fig2) · [附录E.1–E.2、表6](https://arxiv.org/html/2610.13778v1#A5)

图3：GSM8K prompts、每请求256个生成token、window16、验证4token、batch512，两款120B级模型相对vLLM投机吞吐为1.85×/2.10×，计入prefill且匹配接受长度；不是单请求延迟缩短一半。表2中共享NVFP4+SR状态的GPQA平均损失13.05点，分离NVFP4读出/FP16+SR递推降至2.36点，仍非零。低精度准确率用模拟量化路径，延迟用另一个CuTe内核，不能将两组结果直接合成为已上线端到端配置。[图3–4](https://arxiv.org/html/2610.13778v1#S6.F4) · [表2](https://arxiv.org/html/2610.13778v1#S7.T2)

### 6）热度与实际传播线索
冻结榜第6，41赞、878浏览，较昨日＋16赞、＋655浏览。找到**10月12日作者署名NVIDIA技术博客**及Dao AI Lab详细讲解；10月13日README新增这些链接。它们是可确认的发布渠道，不能据此量化“多少浏览由博客带来”，也不是独立复现。[NVIDIA原文](https://developer.nvidia.com/blog/replayssm-rethinking-state-storage-for-faster-hybrid-model-decoding/) · [Dao原文](https://dao-lab.ai/blog/2026/replayssm/) · [README提交](https://github.com/Johnny-Liou/ReplaySSM/commit/73a9592e9d8a2268620e8883a82f5cec7442ed36)

另核vLLM FlashInfer后端PR #52506、MTP PR #52928均已合并，但合并时间分别9月1日和9月30日。**这是今天新核实的旧集成，不是今天刚合并。** 作者称已部署于产品是采用证据，不能替代独立性能测试。[#52506](https://github.com/vllm-project/vllm/pull/52506) · [#52928](https://github.com/vllm-project/vllm/pull/52928)

### 7）工程复现与应用价值
公开仓库固定到73a9592；标准/投机路径和benchmark可检查。B300/SM103低精度CuTe kernels仍是standalone，未接入vLLM serving dispatch，且限定窗口及shape；不能说所有precision路径已即插即用。旧Dao博客和论文的数字口径不同，本报实验数字取版本化论文。[低精度限制](https://github.com/Johnny-Liou/ReplaySSM/blob/73a9592e9d8a2268620e8883a82f5cec7442ed36/low_precision/README.md) · [标准解码benchmark](https://github.com/Johnny-Liou/ReplaySSM/blob/73a9592e9d8a2268620e8883a82f5cec7442ed36/benchmarks/replayssm/e2e_decode_speedup.py)

**自建混合SSM服务值得A档深读，API应用为B档背景。** Agent/coding长输出负载可能受益，但需测真实batch、长度、显存和P95；RAG的检索质量和MCP协议没有因此改善。先核线上backend与kernel路径，再评吞吐，不因“已集成”默认所有模型生效。未独立跑实验。

## #07｜Thinking Inertia: LLMs Keep Thinking When Told Not To

### 1）作者、领域、版本与今日增量
Dianqiao Lei、Kevin Qinghong Lin、Pan Lu、Philip Torr、James Zou；清华、Oxford、Stanford。LLM输出控制与推理评测。arXiv **2610.11765v1**，首发2026-10-08 11:49:37 UTC / 北京19:49:37；仍仅v1，代码main仍是昨日已核8f8f1cd。昨日第2、今日第7。**未见新版本、新代码或新实验；今天只补核一条公开讨论，不重复包装成新发布。**[arXiv](https://arxiv.org/abs/2610.11765) · [alphaXiv](https://www.alphaxiv.org/abs/2610.11765)

### 2）具体问题
设置think-off、去掉think标签、缩短输出，都不能证明模型只给最终答案。研究问题是如何区分严格简答、相关但非推理的前言与显式推导，以及输出约束何时损害正确性。[§1–2](https://arxiv.org/html/2610.11765v1#S2)

### 3）方法与数据流
将可见响应拆为答案前文本T和最后可解析答案A。ETR检查完整输出是否严格answer-only；QRel用instruction-aware Qwen3-Embedding-4B度量问题与T相关性；EIR由盲评GPT-5.5判断T是否含明确推断。A单独评分。六种干预、六个模型覆盖BoolQ/StrategyQA、MMLU/MMLU-Pro、GSM8K/MATH，并把同题改成不同答案空间控制混杂。不是训练一种新“停止思考”模型。[§2.3–3.1](https://arxiv.org/html/2610.11765v1#S2.SS3)

### 4）核心亮点：主张与证据
将格式合规、语义相关、明确推断与正确性分开；同题改写比跨基准比较更能隔离答案界面的影响。ETR关注整段输出，不能只检查答案前是否为空；QRel只是相关性，不能替代推理检测，更不能推断模型内部没有计算。静态源码可见其最后答案定位、T抽取、parse failure及多口径汇总路径。[评估实现](https://github.com/thinking-inertia/code/blob/8f8f1cddcea6560df672fb70e83f013ce9f530e3/src/thinking_inertia/eval_thinking_spectrum.py)

### 5）实验、验证与限制
图6同一批Qwen3-32B数值题、M2：MCQ→Boolean，准确率77.8%→78.9%、ETR10.5%→62.5%、EIR86.95%→36.90%；改开放题则准确率52.6%、ETR0%、EIR90.14%。图5中可关闭thinking的五模型，开放题M2→M5平均ETR近0→约40%，准确率约降15点；这不是证明隐藏计算被减少15%。[图5–6、§3.3–3.5](https://arxiv.org/html/2610.11765v1#S3.SS3)

600输出、5标注者的人类验证：主judge二元一致率98.8%，跨家族judge96.7%；这支持该标注方案，不等于所有任务普遍可信。API模型的部分指标来自保留子集，不能把不同分母当配对样本。论文未直接量总计算、账单或延迟，未证明多轮coding/tool-use/MCP上的同样效果；全量复验要承担模型、embedding及judge调用成本，闭源端点更新也影响复现。[§3.6](https://arxiv.org/html/2610.11765v1#S3.SS6) · [§5.1限制](https://arxiv.org/html/2610.11765v1#S5.SS1)

### 6）热度与传播证据
冻结榜第7，33赞、664浏览，较昨日＋20赞、＋448浏览。alphaXiv有一条真实评论询问机制分析或steering方法，没有取得作者答复或传播链条。**目前只能确认论文热度高，尚无足够公开证据解释传播原因。** 一条提问不是社区共识。[公开讨论所在页](https://www.alphaxiv.org/abs/2610.11765)

### 7）工程复现与应用价值
MIT代码公开，评估器支持OpenAI-compatible endpoint，需自备模型/端点；已核评估与答案评分源码，未运行。公开轨迹入口存在，但未下载验收全部数据。适合先做小批已有日志复评，避免一开始重跑六模型全量矩阵。[README及资源](https://github.com/thinking-inertia/code/blob/8f8f1cddcea6560df672fb70e83f013ce9f530e3/README.md) · [答案评分器](https://github.com/thinking-inertia/code/blob/8f8f1cddcea6560df672fb70e83f013ce9f530e3/src/thinking_inertia/benchmark_scorers.py)

**可马上用于Agent/RAG/coding的输出验收：** 分开记录正确、格式、解析失败、重试、实际token账单与P95；MCP参数用schema校验，不能依赖“请勿解释”一句prompt。这些是工程推论，论文没有直接测MCP收益。

## #08｜Anomaly Detection in LLM-Based Systems: A Survey

### 1. 作者、领域与版本

- Chiming Duan、Tong Jia、Minghua He、Lingzhe Zhang、Haobo Wang、Ying Li；原文均署北京大学，Tong Jia与Ying Li为通讯作者
- 领域：软件可靠性、AIOps、运行时异常检测、agent/RAG安全。原文CCS覆盖软件容错、入侵/异常检测与机器学习
- alphaXiv显示 **2026-10-12、v1**。本次未核到独立arXiv编号、正式发表日期或修订历史；不把“2610.anomaly-detection-llm-systems”当作arXiv编号
- 阅读34页原文的文本层；[alphaXiv元数据](https://www.alphaxiv.org/abs/2610.anomaly-detection-llm-systems)、[原文PDF](https://www.alphaxiv.org/abs/2610.anomaly-detection-llm-systems.pdf)

### 2. 具体解决什么问题

同一个用户目标可以通过不同检索、计划和工具序列完成；反之，看起来像历史“正常轨迹”的调用也可能违反当前要求。只学历史统计边界会把合法新路径误报，把形式正常但目标错误的路径漏报。文章称这种有效/异常分布重叠为chaotic boundary，并与系统变更造成的boundary drift区分。这是综述的概念框架，不是一个新检测器的性能证明。[原文 §1–2，p1–7](https://www.alphaxiv.org/abs/2610.anomaly-detection-llm-systems.pdf#page=1)

### 3. 方法、数据流及与 baseline 的差异

本文没有统一训练和推理算法，而是按“判定条件如何形成”把已有方法分成两大类：

- **Boundary-Modeling AD**：从历史正常/带标签日志、trace、metrics、表示和置信度等拟合预先定义的边界，再判定当前轨迹是否越界；下分分布式边界建模、特征边界建模等。学习型检测器、固定规则映射、验证特征也可能属于这一类，不能按“用了LLM/规则”简单分类
- **Alignment-Based AD**：输入是当前request、执行上下文、SLO/意图/安全要求及运行观测。五个环节依次是：实例化本次要求；组织相关行为证据；建立要求与行为的动态对应及检查条件；用评分器/谓词/符号验证等评估；随新工具结果、证据和权限状态更新模型
- 每条条件保留满足、违反或尚未可判定的结果。某些目标需到任务结束/截止点才能裁决；没有证据不应硬判为通过。强制约束违规不能被其他目标得分抵消

工程例子：RAG不能只看答案流畅或与历史答案embedding接近，还要连到本次证据；工具调用不能只看JSON/schema合法，还要检查目标、参数、权限、当时状态；预算异常应结合语义进度。这里的“alignment”指运行时要求对齐，不等于给基础模型做RLHF。[原文 §3–4、图8、式7–11，p8–22](https://www.alphaxiv.org/abs/2610.anomaly-detection-llm-systems.pdf#page=15)

### 4. 创新主张与证据边界

- **重组异常检测的分类坐标**：从异常类型/技术名称转向判定依据，帮助把幻觉、工具误用、资源异常放进同一架构；证据来自文献整理，非新benchmark胜出
- **给需求对齐型检测一个五阶段框架**：明确需求、证据、裁决及版本演进；可做系统设计检查表，但框架本身没有直接给出已验证的误报率下降
- **提出多要求冲突及干预时机问题**：识别“安全、意图、成本可能冲突”和过早阻断会破坏探索/自纠的风险；这些是研究议程，不是已经解决的问题

### 5. 数据、图表与实证边界

- 检索覆盖ACM DL、IEEE Xplore、Scopus、Web of Science、arXiv；时间范围从2022-01起，**检索截止2026-07-10**。不能写成全面覆盖到本次10月报告日
- 筛选漏斗：5,658记录→去重4,157→标题摘要初筛1,295→方法候选662→正文181个有代表性的分类示例
- 图2：Boundary-Modeling108例（59.7%），Alignment-Based73例（40.3%）；时间趋势图只纳入截至2026Q2有日期的173例。作者按方法差异和分类覆盖选例，这不是全领域论文总量或市占率
- 图8/§4给五阶段的形式化流程；§5/6明确需求歧义、多要求冲突、表示失真、额外检索/验证成本及干预破坏自纠等局限
- **没有统一对照实验、端到端accuracy/F1/AUROC提升、新benchmark消融或新增GPU-hour数据**。不能虚构“比传统异常检测高X%”“更便宜”“已防住prompt injection”。所引各方法也不在同一数据/预算下，不能把跨文献分数做公平排行榜

阅读边界：已读摘要、引言、筛选方法、§2背景、§3/4核心分类与流程、§5挑战、§6结论，并核图2/图8文字与caption；公开PDF文本可读，但直接下载与截图接口失败，因此没有宣称逐像素检查34页全部图表。[原文 p3–4、p15–16、p23–24](https://www.alphaxiv.org/abs/2610.anomaly-detection-llm-systems.pdf)

### 6. 为什么传播

冻结榜第8，7赞、49浏览。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

### 7. 代码、资源门槛与工程价值

- 本次在论文/alphaXiv及精确标题检索中未找到作者提供的统一可运行代码入口。综述本来就不是一个可下载训练的新检测模型，不能把其引用的181个示例当成同一开源产品
- **agent/MCP/full-stack最直接适用**：先把request、工具参数/结果、权限来源、模型/策略版本、时间、latency、tokens和cost连成trace，再分别验证意图、证据与强制权限条件；判断失败要能指向具体事件，不能只给一个总风险分
- **RAG**：适合要求claim→source关系可追溯，并区分缺证、矛盾与尚待检索；**coding agent**：把patch/test/build是否满足任务要求，与执行权限、安全边界分开检查
- 资源门槛取决于检查器：schema/预算/权限规则较轻量，LLM judge、额外检索与重放可能明显增加费用与延迟。推荐先做只观察不阻断的离线/影子评估，测误报、漏报、检测延迟和任务最终成功率，再决定哪些条件适合拦截。这是工程建议，非论文已验证部署方案

## #09｜Is Forgetting in Post-Trained Language Models Just a Shift in Vocabulary Bias?

### 1. 作者、领域与版本

- 作者：Hanyu Yang，ORCID 0009-0005-0419-4070；Zenodo作者元数据未列机构，不补写机构
- 领域：语言模型后训练遗忘、继续预训练、输出校准、logit bias诊断
- **原始出版入口是Zenodo，不是已核实的arXiv**：DOI 10.5281/zenodo.23312067，发表日2026-10-12，version1.0；官方API标记这是当前最新版本。alphaXiv同日显示v1。手稿首页仅写October2026。代码/数据另于10月11日归档为version1.0.0
- [论文Zenodo记录](https://zenodo.org/records/23312067)、[官方元数据API](https://zenodo.org/api/records/23312067)、[9页原文PDF](https://zenodo.org/api/records/23312067/files/prior-shift-forgetting.pdf/content)、[alphaXiv](https://www.alphaxiv.org/abs/2610.language-model-forgetting-vocabulary-bias)

### 2. 具体解决什么问题

模型做SFT、DPO或数学/代码继续预训练后，标准网页文本的cross-entropy可能变差。这种“遗忘”是否只是某些词的全局输出偏好变了，给词表加一个固定bias或调温度即可修回？同时，若一个简单校准器恢复了部分loss，是否能据此推断遗忘的成因就是表层偏置？这篇主要是诊断和反例研究，不是一个通用遗忘修复算法。[原文 §1–2](https://zenodo.org/api/records/23312067/files/prior-shift-forgetting.pdf/content)

### 3. 方法、数据流及与 baseline 的差异

1. 使用共享tokenizer的base/derived模型对，对同一DCLM shard的完整文档做next-token scoring；100万token FIT拟合校准器，另100万token EVAL评测
2. 固定模型权重，仅修改输出logits：词表bias给每个token一个与上下文无关的加减项；bias+temperature另加一个统一置信度参数。bias用iterative proportional fitting，temperature用golden-section search，每个温度点重新拟合bias
3. 完整词表bias一轮后使FIT留出的1/10验证loss恶化，因此主结果限制到FIT最高频4,096 tokens并early-stop。这是具体优化程序的结果，不是所有词表bias的理论最优上界
4. 同样的校准器类型分别拟合base和derived。净恢复比例为“derived的loss改善−base的loss改善”，再除以原本derived相对base增加的loss，避免把任何模型适配评测域都能得到的收益算成遗忘恢复
5. 再造出已知成因的合成场景：只植入bias、只植入温度、随机破坏输出权重、评测文本prior不匹配，测试恢复指标能否识别真正原因

推理上仅多一个logit变换，训练主体不动；但研究需要访问logits与base模型，只有文本API通常无法直接复现。没有temperature-only实验，不能把联合效果拆成两项独立贡献。[原文表1、§2–4](https://zenodo.org/api/records/23312067/files/prior-shift-forgetting.pdf/content)

### 4. 创新主张与证据边界

- **对“只改词表bias就能解释遗忘”作直接量化测试**：14对、1B–7B，所试top4K校准恢复少；结论限定于这些模型、这份文本和拟合方式
- **对base作对称校准**：减少目标语料适配带来的虚假“恢复”，但两个改善相减也可能抵消不同机制，因此小净值不是“绝无prior变化”的证明
- **恢复率不等于因果诊断**：纯随机context-dependent损伤也出现显著bias+temperature恢复，构成有力反例；不证明真实后训练遗忘就是随机损伤，也不把29%定义为普适阈值

### 5. 实验、消融、成本与未支持之处

原文表2，Δ为EVAL增加的nats/token，恢复比例已作base对称校正：

| 模型对 | Δ | Bias-only恢复 | Bias+T恢复 | T derived/base |
|---|---:|---:|---:|---:|
| OLMo-2 7B→Instruct | 0.354 | 3.9% | 35.9% | 1.276/1.006 |
| Qwen2.5 7B→Instruct | 0.050 | 9.8% | 28.8% | 1.080/1.013 |
| Qwen2.5 7B→Math | 0.485 | 0.4% | 1.3% | 1.056/1.013 |
| Qwen2.5 1.5B→Math | 0.796 | 0.9% | 1.2% | 1.038/1.010 |
| Qwen2.5 7B→Coder | 0.135 | 0.0% | 0.3% | 1.018/1.013 |
| Qwen2.5 1.5B→Coder | 0.127 | 0.0% | −0.1% | 1.004/1.010 |
| SmolLM2 1.7B→Instruct | 0.114 | 0.7% | 3.6% | 1.045/1.004 |

- 14对中bias-only最高9.8%，其余13对均<7%；即使在评分文本上拟合的一步bias最高15.8%，也不能作为充分迭代的上界
- OLMo-2 1B SFT→DPO联合恢复8.9%→23.4%；7B为17.5%→33.5%。该模式并非所有instruction tuning通用规律，Qwen1.5B Instruct联合仅5.8%
- 合成表3：400词、600文档×64tokens。植入global bias：bias/联合均恢复96%；只将logits加倍：3%/100%；随机输出权重损伤：8%/29%，拟合T1.44；proxy文本场景对称恢复8%/30%，derived-only则25%/47%。这说明对称校正和因果反例都重要。[表3、图4，p7](https://zenodo.org/api/records/23312067/files/prior-shift-forgetting.pdf/content#page=7)
- 图1给95% document-bootstrap区间，但校准器在重采样时固定，未覆盖重新拟合的不确定性；仓库也提醒拟合选择的差异可能大于bootstrap区间
- 局限：单一DCLM shard、三模型家族、最大7B；OLMo-2可能见过这些训练数据；special/added tokens从softmax移除，因此EOS/chat模板概率转移导致的损失不可见。没有改变top4K支持集或early-stop规则，某headline fit到迭代上限时仍缓慢改善；也没有通用任务能力或更大模型实验
- 成本：作者报告约13.5 A100-hours。仓库补充全部配对在一张A100-80GB运行；7B时约21GB GPU和26GB host memory为作者人工读数、没有日志记录，不能当成严格最低配置

数值来自原文表2/3与图1，不混用README里full-vocabulary和top4K两种联合拟合结果。[原文 p3–8](https://zenodo.org/api/records/23312067/files/prior-shift-forgetting.pdf/content)、[README方法与限制](https://github.com/SeverinVisionary/prior-shift-diagnostic/blob/main/README.md)

### 6. 为什么传播

冻结榜第9，5赞、48浏览。目前只能确认论文热度高，尚无足够公开证据解释传播原因。

### 7. 代码、资源门槛与工程价值

- [GitHub代码](https://github.com/SeverinVisionary/prior-shift-diagnostic)、[Zenodo代码/数据归档](https://zenodo.org/records/23304208)。已核官方README及归档元数据：提供诊断代码、14对每文档loss汇总、哈希/token counts、CPU重算脚本与合成测试；不含原语料文本，fitted bias vectors也未保存。所有文件CC-BY-4.0，代码另可用MIT
- CPU验证可重算点估计并检查损坏输入，**不重跑模型、不重算置信区间/温度/拟合轨迹，也不能证明存档数据确由这些代码产生**；完全复现仍需GPU和模型。数据shard用main而非固定commit，重跑要检查文档哈希漂移
- **coding/领域微调**：适合把base与adapter/微调版本放到同一retention suite，加入校准对照，避免将通用语料loss恶化全归结为“模型忘了事实”或“只是措辞变了”
- **agent/RAG/MCP/full-stack**：间接相关。应用层检索增强无法由这篇直接推出能修复参数遗忘；MCP或工具正确率没有被测。最可用的原则是：改进一个代理指标不等于找到根因，既检查旧分布loss，也评估实际任务、工具安全和新领域收益

## #10｜MagicBeanStalk: Escaping the RLVR Zero Advantage Trap with Recursive Data Synthesis

### 1）作者、领域、版本与今日增量
Ximing Lu、Aviral Kumar、Jan Kautz、Yejin Choi、David Acuna；UW、CMU、NVIDIA、Stanford。RLVR训练数据合成。arXiv **2610.12659v1**，首发2026-10-08 19:25:48 UTC / 北京10月9日03:25:48；今日仍v1，连续两天第10。**没有核到新版本或新发布资源**；今天进一步核了附录G组件分析，不将同一v1内容称为新实验。[arXiv](https://arxiv.org/abs/2610.12659) · [alphaXiv](https://www.alphaxiv.org/abs/2610.12659)

### 2）具体问题
组内相对奖励训练碰到全对/全错组，优势信号为零。约78K数学题对gpt-oss-120b、32K预算、每题8次时，只有12.2%出现有对有错。有效难度属于“题目＋模型＋预算”的组合；8次全错不是数学上不可解的证明。[§2/图2](https://arxiv.org/html/2610.12659v1#S2)

### 3）方法与数据流
教师先为难种子题提供核验答案和轨迹，拆成至多3个子题；学生得到子题例子后必须提高解父题的成功率，才保留分解，最多3层。自叶子生成更难的新题，按原结构向上重组，每步验答案；最终用目标模型筛出8次中1–7次正确且至少一次正常结束于预算内的题。金融问题还要在新文档和实体上重落地，不能只换名字继承旧事实。[§3](https://arxiv.org/html/2610.12659v1#S3)

### 4）核心亮点：主张与证据
亮点不是简单增加题量，而是同时约束推理结构、新颖性和预算内可学性。附录G表10中22个teacher-valid分解仅6个通过有效性测试；说明“答案看似正确”与“能帮助学生”是不同门槛。但这些构造阶段消融没有完整逐项重训，不能把最终性能增益全部归因于某个组件。[表10](https://arxiv.org/html/2610.12659v1#A7.T10)

### 5）实验、消融、算力与公平性
表1，16K推理、8数学集平均：gpt-oss 61.2→69.8，源题Goldilocks67.0、直接合成66.8；DeepSeek 72.4→77.9，论文以未舍入值报＋5.4。Golden Goose未按目标模型重筛；API参照4次、gpt-oss16次、DeepSeek1次采样，跨行不是完全匹配的成本赛跑。[表1](https://arxiv.org/html/2610.12659v1#S3.T1)

约1,250个困难种子，合格后代覆盖74.7%对43.8%；附录C的64种子预算对照为14.3M对16.0M token，能同时满足结构/新颖/难度条件的种子28对13。表10等四次教师调用时覆盖63.0%→71.5%，递归深度增加额外覆盖116个种子；更难叶子的1/10→3/10样本很小，勿夸为稳健大规模结论。[§4.1](https://arxiv.org/html/2610.12659v1#S4.SS1) · [附录C](https://arxiv.org/html/2610.12659v1#A3) · [附录G](https://arxiv.org/html/2610.12659v1#A7)

gpt-oss训练16×H100，DeepSeek80×H100；完整生成/训练总成本未统一配平。150数学题质量抽查有8%被三judge一致否定，标签并非无误。金融SecQue32.4→39.3、FinanceBench65.9→68.3仅说明基准提升，不证明金融决策可靠。[§4.2–4.3、表3–4](https://arxiv.org/html/2610.12659v1#S4)

### 6）热度与传播证据
冻结榜第10，34赞、322浏览；较昨日＋10赞、＋269浏览，名次不变。**目前只能确认论文热度高，尚无足够公开证据解释传播原因。** 未把理论吸引力或合成数据题材当实测传播来源。

### 7）工程复现与应用价值
原文仍说接收后发布数据；本次没有核到官方可运行仓库、模型或数据下载。教师API会变化，重新合成不保证字节级一致。小团队可以先复用“验证分解是否真有帮助”的数据筛选思想，完整训练门槛高；本次无独立复现。[复现与伦理声明](https://arxiv.org/html/2610.12659v1#S6)

RAG可从失败问答拆出缺失操作，再绑定新文档证据合成题；coding可从失败测试拆成可执行子目标；MCP和全栈需可验证终态、隔离执行、成本记录。上述是迁移建议，原文没有软件Agent/MCP实验；应先审计一小批题的真值与重复率，再考虑RL。

## A．今天最值得深读的三篇

选择依据是对Agent/RAG/coding/MCP和全栈工作的可迁移性、证据清晰度及今天的新信息价值。它不是热榜重排，也不要求立即投入论文级训练。Vela与Forgetting是本次新入前10；ReplaySSM连续上榜，今天新增可核的发布/集成材料。

1. **Vela先读§2.2–2.4，再读表1/表2与§4.1、附录E**。重点是任务证据边界与评测合同，不必先复现大规模SFT。代码阅读入口：
   - [purchase_intent_ecom_goods.md](https://github.com/AllSpark-Research/Vela/blob/main/templates/objective/purchase_intent_ecom_goods.md)：已实读。正例要求购买计数>0；曝光/点击/加购不等于购买；gold与未来购买计数不能泄漏，候选至少有两个合法干扰项。可以用来审查产品埋点的事件语义是否把弱行为升级为强意图
   - [composer.en.txt](https://github.com/AllSpark-Research/Vela/blob/main/prompts/composer.en.txt)：已实读。历史不满足模板就空候选；Open只能用可见历史；Attribution只披露指定结果；不能发明缺失信息或隐含评分要求。检查生成的数据是否靠题面捷径得高分
   - [scorer.en.txt](https://github.com/AllSpark-Research/Vela/blob/main/prompts/scorer.en.txt)：已实读。按subtask_id对齐；Objective仅提取答案，程序计算F1；开放预测一对一语义匹配且保留误预测/遗漏；rubric等权，先逐项判断。仅有prompt还需要程序供给输入、校验JSON与计算指标，仓库不是完整运行器
2. **Forgetting先读§2和表2，再读§4的反例、§6限制**。适合有领域微调/模型回归评测的工程师，代码比整套训练更轻量：
   - [METHODS.md](https://github.com/SeverinVisionary/prior-shift-diagnostic/blob/main/METHODS.md)：已实读。文档按顺序切FIT/EVAL、每文档截断到2047正文tokens；校准只用FIT前90%并在后10%选停。澄清全词表、top4K、closed-form与affine的区别
   - [code/prior_shift.py](https://github.com/SeverinVisionary/prior-shift-diagnostic/blob/main/code/prior_shift.py)：已读L1–380。重点函数build_splits、regular_vocab_mask、cache_hidden、ce_terms、fit_bias_ipf、fit_affine、score、stats_from_docsums。输出变换实际为softmax(z/T+b)；IPF最多20轮、patience3；T搜索0.25–4、14点评估，且未明确包含T=1或证明目标单峰。因此别将拟合结果当作最优可恢复量
   - [code/test_prior_shift.py](https://github.com/SeverinVisionary/prior-shift-diagnostic/blob/main/code/test_prior_shift.py)：已实读。ctx案例在W上加0.25尺度高斯扰动，固定hidden-state分布，得到上下文相关logit损伤；同一案例不是所有遗忘机制的下限或“噪声地板”定理。测试对full-vocabulary恢复有断言，top-K只计算未作known-answer恢复断言
   - [verify_data.py](https://github.com/SeverinVisionary/prior-shift-diagnostic/blob/main/verify_data.py)、[reproduce.sh](https://github.com/SeverinVisionary/prior-shift-diagnostic/blob/main/reproduce.sh) 是README确认的CPU重算入口；本次只读，未执行。先审计固定校准后的统计重算，再决定是否授权完整GPU复现

3. **ReplaySSM：优先为真实服务负载判定适用性，再读加速倍数。** 从[§4–6](https://arxiv.org/html/2610.13778v1#S4)理解checkpoint/buffer/双精度三条路径，再读[附录E表6](https://arxiv.org/html/2610.13778v1#A5)的batch敏感性和[表2](https://arxiv.org/html/2610.13778v1#S7.T2)的精度代价
   - 已读的[标准输出kernel](https://github.com/Johnny-Liou/ReplaySSM/blob/73a9592e9d8a2268620e8883a82f5cec7442ed36/vllm/model_executor/layers/mamba/ops/selective_state_update_replayssm_output_only.py)：关注non-flush如何读checkpoint、追加输入，以及flush何时重构/写回；别把“缓存输入”误解为无重算
   - [e2e_decode_speedup.py](https://github.com/Johnny-Liou/ReplaySSM/blob/73a9592e9d8a2268620e8883a82f5cec7442ed36/benchmarks/replayssm/e2e_decode_speedup.py)：同一prompt复制到batch、独立子进程、warmup和状态精度约束是理解该microbenchmark的必要条件；与生产异构请求有差距
   - [low_precision/README.md](https://github.com/Johnny-Liou/ReplaySSM/blob/73a9592e9d8a2268620e8883a82f5cec7442ed36/low_precision/README.md)：先确认B300/SM103、固定shape、尚未接serving dispatch，再判断能否纳入现有服务
   - 最小后续实验应固定权重、backend、状态精度、功耗和真实请求分布，同时测正确性、吞吐、峰值显存、首token与P95；本报未运行该实验。仅使用托管API时，这篇的近期优先级低于Vela的数据契约或Forgetting的诊断方法


## B．仅由今天10篇样本支持的五条技术线索

这些是本榜单样本内的归纳，不是对整个AI领域的统计判断。

1. **训练反馈越来越贴近系统实际经历的状态。** Correction用模型自己的中间预测训练修正；Vela用历史行为之后的真实行动作监督；RSI保留预测—观察配对；MagicBeanStalk按当前模型和预算筛题。共性是显式处理“训练输入和部署过程是否一致”，并非四篇证明了同一个通用自改进算法
2. **中间指标必须与最终可用性分开。** Thinking Inertia区分简答合规、相关性、推断和正确性；Vocabulary Bias诊断显示NLL可恢复也未必解释遗忘来源；SEE高MI/更多成就不自动等于有意义可控性；Prompteina代理分数高也不等于实测功能可靠。工程上应并列报告格式、任务结果、成本和失败类型
3. **更丰富的语言接口需要可靠的条件绑定。** Vela把时间序列历史组织成可验证任务，Prompteina把全局/局部文字绑定到对象，异常检测综述把当前要求与历史正常行为分开。对RAG和MCP的启发是记录证据、时间、对象、工具能力与硬约束，不能只把一大段文本塞进上下文；这些迁移没有共同的跨论文性能验证
4. **“同预算”应展开为一张成本账。** ReplaySSM大batch吞吐收益不能外推单请求；SEE额外branch simulator steps未计live预算；Vela长上下文训练和RL设备显著；Prompteina同候选数不等于同采样算力；MagicBeanStalk教师/学生筛选也有成本。API次数、token、GPU小时、环境步和端到端延迟不能互相替代
5. **可复现性是分层发布状态，不是有无GitHub图标。** Correction有权重工具但核心训练/采样发布未齐，Vela开放任务/提示资源不代表用户日志可得，Prompteina缺完整训练数据，SEE代码尚未上线；ReplaySSM不同backend/precision路径开放范围不同。先确定今天能验证哪一段，再决定是否投入复训

## C．与昨天真实归档报告的对比

### 1）固定对比基线

实际读取[2026-10-13完整日报，固定提交b27d217](https://github.com/DanielMax937/daily-research-reports/blob/b27d217158a728839daafd317d32341374bb0a43/2026-10-13/ai-papers.md)，文件blob SHA为`ad693d9a68562d6dee538d65e1b3525ab2db3e0a`。它的原始归档提交是[6f1901e](https://github.com/DanielMax937/daily-research-reports/commit/6f1901ee721a8a9fc3113961841020d7a605658e)。昨日榜单是约11:48 BJT抓取的Hot / 30 Days无分类过滤，和今天11:49 BJT同口径；可以比较这两个快照，但不是全天累计“日榜结算”。

### 2）连续热门：排名与计数变化

| 论文 | 昨日→今日Hot名次 | 赞：昨日→今日（差值） | 浏览：昨日→今日（差值） | 版本/实际新增材料 |
|---|---:|---:|---:|---|
| RSI-Anything | 1→5 | 30→63（＋33） | 531→1,080（＋549） | arXiv仍v1；新增仓库规划流程说明，解释学习/验证/F200划分与冻结推理范围，非新增实验 |
| ReplaySSM | 4→6 | 25→41（＋16） | 223→878（＋655） | arXiv仍v1；README新增论文/博客/集成链接；今天核实的两个vLLM合并实际发生在9月 |
| Thinking Inertia | 2→7 | 13→33（＋20） | 216→664（＋448） | arXiv仍v1；仓库main SHA与昨天相同，未见新代码/实验；补核公开机制提问 |
| MagicBeanStalk | 10→10 | 24→34（＋10） | 53→322（＋269） | arXiv仍v1；未核到新代码/数据发布，附录消融属于原v1已有内容 |

**四篇均没有新arXiv版本。** 前三篇排名下移，累计互动仍上升；不能据排名下移就断言阅读量下降或研究失去价值。MagicBeanStalk名次没有变化，今天不制造“再次突破”的叙事。

### 3）新入前10与离开前10

- 新入本次前10的6篇：Correction、Vela、Prompteina、Scaling Empowered Agents、Anomaly Detection Survey、Vocabulary Bias诊断。这里只能确认昨日不在前10；不声称首次登上全站榜或今日首发
- Prompteina今天读到arXiv v2；v2新加逐目标胜率汇总和文字澄清，57%与GM2A实验基础数据在v1已有。alpha首页的版本痕迹不能代替arXiv版本史
- 昨日前10其余6篇仍能在**今天同一份20条响应**找到：Universal KL Bounds **5→11**、Sonic-AMG **9→13**、CoTrace **6→14**、Articulated 3D Assets **7→15**、ETM **3→16**、MASS **8→20**。这是离开前10/相对名次后移，不是下线，也不是质量结论
- 没有用ETM、MASS或CoTrace替换今天不那么贴近coding兴趣的论文。它们这里只用于跨日对照，今天没有再次提供未实际进行的全文审查结论

### 4）今天更值得跟进的变化

1. **版本核对：** Prompteina原始版本和alpha条目不完全同步；报告采用已读v2，并保留v1/v2差异边界
2. **发布状态核对：** SEE论文中的开源表述与项目页coming soon不一致；Correction/Vela公开的资源类别有限。应按实际资源决定复现计划
3. **新材料归因：** RSI文档澄清、ReplaySSM技术博客、Thinking Inertia评论均是真实材料，但只有链接和时间还不足以建立“这些材料导致热度变化”的因果关系

## 证据记录、阅读范围与仍存缺口

### 榜单可复核记录

公开源：[alphaXiv首页](https://www.alphaxiv.org/)。本次保存的公开HTML SHA-256：`ba7f6e59d761a3a068e3bfa97ecec404347d11995cc447f19d1a2f3ce4226dda`。

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
  "dataUpdatedAt": 1791949768485,
  "dehydratedAt": 1791949768499,
  "top10_alpha_ids": [
    "2610.correction-training-diffusion-models",
    "2610.vela-user-behavior-supervision",
    "2610.13917", "2610.13002", "2610.13912", "2610.13778",
    "2610.11765", "2610.anomaly-detection-llm-systems",
    "2610.language-model-forgetting-vocabulary-bias", "2610.12659"
  ]
}
```

这段记录保存的是平台返回的排序/过滤/身份字段，不能用于反推出未公开的Hot权重或真实推荐因果。

### 实际正文与代码覆盖

- 新入六篇：各篇第1、5、7节列出了已读原文版本、章节、关键表图、静态代码或无法访问的具体范围。Prompteina采用v2 HTML；SEE读取v1 PDF并目视图2/3。没有将alphaXiv AI Overview当作论文原文，也没有把“代码coming soon”写成可用实现
- RSI-Anything：重新读取v1 Abstract、§1–3、§5–6、表1–4和图注；静态核evaluation.py选择/封存路径、GUI结果，以及10月13日规划README差异。未逐页视觉检查PDF，也未重跑任何训练阶段
- ReplaySSM：重新读取v1 §1–7/9、附录A和E的预算/消融；目视PDF第6–7页图2–4，核标准输出kernel及benchmark，另读low_precision README。35页PDF SHA-256为`749c459895ed93a348cd0186c779592842e29808c7c616463a7ce8ef969cad35`
- Thinking Inertia：重新读取v1 Abstract、§1–3/5、关键验证和限制；目视PDF第12页表4/图6，静态读输出分解/汇总代码与答案评分器。37页PDF SHA-256为`2e5c3ae37a225dedbf38d92c8ed4ec43b99ac998ca182085ee89849e9e12890e`
- MagicBeanStalk：重新读取v1摘要、§1–4/6及附录C/G、主要表格；目视PDF第19页表10，未核到官方可运行源码。19页PDF SHA-256为`8194f274c654885ced12fb3e02149fda1c3c567ef8d6851e11d5353f98225a1e`
- 论文HTML存在内部交叉引用/编号转换错误时，引用以可见表图标题及实际PDF核查为准；未宣称所有PDF逐页检查，也未把源码静态阅读称为运行验证

### 保留的访问与推论边界

- Prompteina、SEE的alphaXiv单篇访问失败；身份/计数来自已核首页，论文论证来自arXiv/作者来源。没有因单篇访问失败虚构alpha评论
- 详情页徽章和首页冻结排名有不同步现象；Vela等条目版本与出版源版本也需分别记录。除已说明的正文差异核查外，没有对所有跨站PDF做字节一致性证明
- 社区传播证据大多不足：不以作者名气、题材吸引力、仓库总star数推断“突然爆火原因”，也不把一个评论推成普遍共识
- 所有实验数字仍是作者报告；本次独立复现为零。缺失的GPU小时、成本、置信区间或失败率不补造；不同模型、预算、样本分母及版本的结果不混合
- Agent/RAG/coding/MCP/全栈迁移建议是面向工程的分析；除逐篇明说的原文实验外，不代表这些应用已获同样提升

### 新入论文补充阅读证据

| 论文 | 实际阅读范围 | 关键图表核查 | 代码入口状态 |
|---|---|---|---|
| Correction | 50页v1的摘要、§1–4、§6、附录A/B/C关键段；非仅alpha概述 | 表1/2/3/4/5/6/7/10/12/13/14；图12等文字；本地渲染并目视核表1 | README明确训练/采样coming soon，权重release已公开 |
| Vela | 22页v1的摘要、§1–6、伦理/复现声明、附录E | 表1/2/4；图2/3/5/6；本地渲染并目视核表1 | 已核74模板、4个双语角色prompt；未称完整训练包 |
| Anomaly survey | 34页PDF文本的摘要、§1–6关键章节及筛选方法 | 图2计数、图8流程及caption；截图失败，未声称完整视觉核验 | 本次未找到统一作者实现仓库 |
| Forgetting | 完整9页PDF正文§1–6、data/code；官方Zenodo元数据及README | 表1/2/3、图1/2/4；本地渲染目视核表2 | GitHub+Zenodo归档，已核许可与复现边界；未执行代码 |

三个重要校验结论：①alpha自定义slug不可转换猜测arXiv号码；Correction与Vela的号码已由官方页确认，另两篇未杜撰。②alpha AI Overview不是原文，Vela RL对照已经按原图纠正。③公开仓库存在不等于训练代码、数据、权重与可复现环境全部齐备。

研究与代码状态核验截至2026-10-14约12:02 BJT / 04:02 UTC；排名与计数始终冻结于11:49 BJT的同一份Hot响应，未随阅读过程重排。
