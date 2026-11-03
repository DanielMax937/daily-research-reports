# AI论文日报｜2026-11-03

## 今日结论与来源口径

**五项新入、五篇持续。** 今日榜首是Weight-Space Programming研究博客，而非arXiv论文；Mistral Large 4也是官方技术报告。保留实际榜位，不用别的论文替换。最值得分清的是：权重编辑修复循环不等于普遍增智，语言建模loss接近不保证agent任务能力接近，以及运动生成质量不等于机器人安全可执行性。

- **抓取时间**：北京时间2026-11-03 **11:39:06**首次读全前十，**11:43:49**复核留存；原始UTC03:39:06／03:43:49。[实际入口](https://www.alphaxiv.org/?sort=Hot&interval=7+Days)：Trending／Hot，页面显示**7 days**，无额外学科筛选。榜首详情还明确链接“#1 on Trending”。未用搜索缓存或默认最新流替代。
- 云浏览器初始自动安全验证后正常显示，没有解CAPTCHA或登录／注册。首次只懒加载五项，滚动后实际读取到第11项；推荐研究者卡不计榜位。可关闭的注册提示已关闭。筛选菜单列Most Recent／Most Liked／Most Stars，本次未切换到这些排序。
- 下表保留赞数与浏览显示值，`6k/16k/2k/5k`为界面取整，不伪造精确访问量、24小时增量或排名算法。窗口是7天，不代表十项均在24小时内发表。
- 比较基线：[2026-11-02固定报告](https://github.com/DanielMax937/daily-research-reports/blob/76c43e01e363267d45f5ecd45ef3a89a3276538a/2026-11-02/ai-papers.md)。连续项压缩旧背景，保留七项记录，以版本／实验／代码／讨论增量为主；未确认变化即明确说明。所有实验是作者报告，dot未独立复现、未执行外部研究代码。

|今日|条目与原始alphaXiv链接|昨日|赞|浏览原样|
|---:|---|---:|---:|---:|
|1|[Sparks of Weight-Space Programming](https://www.alphaxiv.org/abs/2611.weight-space-programming)|前十未见|118|6k|
|2|[Proving and Improving the Platonic Representation Hypothesis with JEPAs](https://www.alphaxiv.org/abs/2610.39302)|1|324|16k|
|3|[Mistral Large 4](https://www.alphaxiv.org/abs/2611.mistral-large-4)|前十未见|14|177|
|4|[Hierarchical World Models with Implicit Dynamics](https://www.alphaxiv.org/abs/2610.42146)|前十未见|21|324|
|5|[Training Foundation Models with a Single Algorithm](https://www.alphaxiv.org/abs/2610.40564)|2|166|2k|
|6|[Probing Spatial State Representations in Visual Foundation Models](https://www.alphaxiv.org/abs/2610.40636)|3|52|626|
|7|[Hierarchical Residuals: A Minimalist Decoupling of Residual Width from Compute Width](https://www.alphaxiv.org/abs/2610.41711)|前十未见|6|未提供|
|8|[FlatCake: A Flat KVCache Storage Architecture for LLM Serving](https://www.alphaxiv.org/abs/2610.38355)|9|83|5k|
|9|[Movens-Zero: Scaling Humanoid Motion Foundation Models with Large-Scale Human Videos](https://www.alphaxiv.org/abs/2610.41877)|前十未见|10|未提供|
|10|[Training language models in simulation for psychiatric intake](https://www.alphaxiv.org/abs/2610.40476)|4|74|2k|

## 逐篇核验

## 1. Sparks of Weight-Space Programming: LLMs can natively read & write neural network weights

### 1. 基本信息与实读范围

- 作者：Rikiya Takehi、Jayden Teoh、Alex Zhang、Omar Khattab，MIT CSAIL。作者[研究博客](https://rikiyat.github.io/blog/weight-space-programming/)标注2026年11月2日，未给时分或原时区；不能精确换算北京时间。它是研究博客，不是已核验arXiv论文，alphaXiv的`2611.weight-space-programming`是条目slug，不应伪造arXiv链接或v1。
- [alphaXiv原页](https://www.alphaxiv.org/abs/2611.weight-space-programming)：本次7日Hot第1，118赞、6k浏览。领域：LLM、Interpretability、Model Editing、Agent工具协议。
- 实际读到博客实验1–8、Gemma补充反例、相关工作和展望；视觉检查Fig.2注意力对照。代码／日志锁定[4d09ba6d6a7e891dd8063974dfe81b3d78e3494f](https://github.com/RikiyaT/lm_understand-logs/tree/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f)，读README、实验7/8说明、sandbox、apply_edit、修改清单和原始merged结果。未运行、未独立重算，没通读所有1,125轮日志。commit作者时间为10月29日，不当作博客公开时间。

### 2. 解决的问题

一般coding agent修改训练脚本，再让优化器修改权重；这项工作问的是：能否让一个通用模型把权重当成可诊断、可局部修改的对象，直接从自然语言目标提出数值修补？它同时研究“读出行为”“修复特定失败”“从零构造小策略”，不是只提出一个新优化器。值得关注的是工具协议如何限制可用证据，尤其纯权重静态分析与允许激活／前向反馈是不同能力。

### 3. 核心方法与数据流

- 以前：任务／数据 → 损失和梯度 → 优化器 → 新权重。这里：任务描述＋权重＋允许的观测 → LLM提出结构性解释／数值补丁 → 受限Python或直接文本写入 → 有预算的行为检查 → 冻结补丁后评测。
- 小网络实验把权重作为文本输入；大网络实验给CPU权重读取／修改和有预算的前向工具。**没有梯度训练不等于没有试错、数据或推理成本**，实验8明确给GSM8K/MATH训练题及答案，日志还记录714道AIME练习答案。
- Qwen实验的最终修改集中在第15、19层MLP的down projection，每层64列：从特别强地写入重复方向的列中减去该方向。博客口径触及131,072个权重；[实际manifest](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp8_math/runs/p50c/edit/manifest.json)记录bf16舍入后真正比原模型不同的是**130,188**个，两个数字并不矛盾。
- [apply_edit.py](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp8_math/code/apply_edit.py)先验证基模型张量dtype、shape与SHA256，再按稀疏差分或低秩因子重建，最后验证目标张量hash。这里确实有可审计的补丁格式，但本次只是读代码，没有执行hash重建。

### 4. 最大亮点

1. 把行为诊断与极小权重补丁联系起来，同时保留失败案例，适合研究agent如何提出可检验的机制假设。
2. 控制工具权限的分层设计比单一成功率更重要：禁止网络运行的静态分析，与允许attention读取或试题前向的条件分别报告。
3. 公开精确编辑差分、结果文件和大量交互日志，让“只改0.016%”可追到具体张量，不只是宣传比例。不过实验8的完整agent harness／前向服务器并未全部开放，不能称一键完整复现。

### 5. 实验支持什么、没有证明什么

**作者报告且本次对照结果文件确认的内容：**

|实验8同一采样协议|MATH-500|GSM8K|IFEval|MATH-500撞32,768 token上限|
|---|---:|---:|---:|---:|
|原Qwen3.5-0.8B|7.9%|13.8%|21.0%|93.0%|
|10次前向预算编辑|12.3%|25.7%|49.0%|87.2%|
|25次前向预算编辑|14.1%|25.1%|39.9%|86.4%|
|50次前向预算编辑|48.1%|67.1%|62.3%|33.1%|

来源：[实验8协议与数值映射](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp8_math/README.md)、[原模型结果](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp8_math/eval/unedited/merged.json)、[50次预算结果](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp8_math/eval/p50c/merged.json)。MATH-500每题4次、GSM8K/IFEval每题2次取平均，并非pass@4。固定temperature0.6/top-p0.95/top-k20/presence penalty1.5，thinking开启。

**必须一起读的边界：**

- 50“前向”不是50次单样本推理。一调用可生成最多512题或teacher-force读取最多1,024文本；50预算运行有158轮、80次Python执行，墙钟20.3小时，包括4.7小时服务不可达等待。10/25预算也是不同完整运行，不构成普遍单调的budget scaling结论。没有匹配全部成本的微调／简单解码调参对照，不能证明比训练更便宜。
- 主要成功是消除循环障碍。博客补充Gemma 3 270M原分6.8%，50预算后7.0%，未确立能力提升；它原本只有8.5%撞上限。因此“数学成绩6倍”不能直接解释为创造了6倍数学能力，或通用模型均可无训练升级。
- 实验7只看权重的四轮尝试未能可靠分辨迎合模型；放开attention工具后才在三对模型上选对。[实验7协议](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/exp7_sycophancy/README.md)还显示部分轮次提前停止，前三轮强制平局选择只有机会水平；Fig.2展示的是一对模型特定head的注意力差异，不能推出无需任何推理即可安全审计任意模型。
- MinAtar实验5与PPO100M步相比三个游戏都高，但相对500M步只Breakout明显高，Seaquest53.1低于88.9，Asterix53.2略低55.2。作者提供规则和源代码，不能把它等同于无先验从环境交互学习。
- 根README明确只发布文章报告的运行，早期prompt版本试运行未包含。缺完整选择过程、跨编辑器／更大模型／种子统计，不能估计总体成功率。GPQA图里的原模型24.5是149/198题的中途值，完整结果22.7；本报告使用完成版，不拼接中间数。
- 网页提取读取模型页失败后，云浏览器成功读到[HF模型卡](https://huggingface.co/RikiyaT/Qwen3.5-0.8B-weight-space-programming)与[固定提交原始评测文件](https://huggingface.co/RikiyaT/Qwen3.5-0.8B-weight-space-programming/blob/8dc30b6d486b2c4b321380a84ec223d1f1efad61/eval/scores_edited_math500.json)：由akhaliq借助ML Intern进行的11月2日复跑，编辑模型500题×4样本为51.0%，撞上限31.6%，51分钟H200，43.4M生成tokens；基座只做25题smoke test，不是完整500题配对重跑。模型卡说明使用完整多模态checkpoint而原作文本导出，并声称语言张量hash相同。可确认存在发布者署名的单基准复跑与原始结果，不等于全实验独立验证；本次只读summary和部分逐题条目，没有重算／执行，也不把51分钟当作生成权重补丁的耗时。

### 6. 现在为何热门

可核事实是11月2日新博客、公开日志、alphaXiv当前榜首，以及原页嵌入的[作者X线程](https://x.com/rikiyatakehi/status/2117313742891327994)讨论小比例权重编辑、数学和指令遵循改善。实际读到了alphaXiv嵌入的首帖及前两条，不声称读完X全部回复；未核X热度指标。**dot推断**：用agent直接写权重、开放过程且有直观成功案例，是传播吸引力候选，但没有证据量化它对排名的贡献。不能把榜首解释为社区已经验证“训练将被替代”。

### 7. 工程价值

最值得借鉴的是**冻结基模型版本＋显式编辑manifest＋前向预算＋独立留出集＋失败日志**这条审计链，而非立即给生产模型自动改权重。可先读`exp8_math/code/apply_edit.py`、`edit/manifest.json`和结果协议，理解如何把agent产出的数值补丁变成可核验artifact；[sandbox.py](https://github.com/RikiyaT/lm_understand-logs/blob/4d09ba6d6a7e891dd8063974dfe81b3d78e3494f/harness/sandbox.py)展示CPU隔离执行的示例，但它是Go实验工具，不应误称实验8完整harness。若之后单独授权复现，应加入解码参数对照、普通小规模微调对照、模型外能力回归、安全测试和完整编辑成本；本次不执行。

## 2. Proving and Improving the Platonic Representation Hypothesis with JEPAs｜连续，昨日第1

### 1. 标识与版本
Randall Balestriero、Yann LeCun；表征学习／多模态对齐。[arXiv 2610.39302](https://arxiv.org/abs/2610.39302)仍仅v1，2026-10-29 03:49:53 UTC（北京11:49:53），未见修订版。

### 2. 问题
独立训练的模态编码器是否会形成可旋转对齐的表示？研究重点是正样本视图怎样构造，而非只增加参数。[原文§2–4](https://arxiv.org/html/2610.39302v1)

### 3. 方法与今天复核
同一场景的多次观测形成正样本，分别训练JEPA，再检查表示对齐。今天回读§2.1：定理依赖单射观测、共享正样本、总体最优及旋转意义下唯一性；论文明确**不覆盖带学习式预测器、尤其动作条件预测器的世界模型JEPA**。这不是今日新限制，而是v1已有适用范围。[§2.1](https://arxiv.org/html/2610.39302v1)

### 4. 值得保留的亮点
把“表征随规模趋同”改成可检验的数据构造问题。工程上可借鉴视图选择，但不能把理想化定理直接升级为现实多模态世界模型的普遍保证。

### 5. 实验证据与边界
今日核§4.2：21.6M与900M样本分别达到WIT约0.109与0.111；**42×是样本比，文本token比是14×，不是算力比**。两种规模的学习率、batch不同，且未测更早的next-token checkpoint，因此不是精确识别其最小样本需求。未见新实验或表格修订，未独立复现。[§4.2、Fig.1](https://arxiv.org/html/2610.39302v1)

### 6. 热度、讨论与代码增量
今日**#2，324赞／16k浏览**；昨日#1、164／8k，赞+160。名次下降和计数增长同时发生，浏览缩写不换算精确增量。[alphaXiv](https://www.alphaxiv.org/abs/2610.39302)。官方main仍为[a2b9949](https://github.com/galilai-group/prh-proof/commit/a2b9949fa907d4fbe562742d4b1ffa7205ab7427)，[releases](https://github.com/galilai-group/prh-proof/releases)为空。[Issue #1](https://github.com/galilai-group/prh-proof/issues/1)仍open、0评论、更新时间仍11月1日22:54:34 UTC；只是结果收录核验请求，不是作者确认或独立复现。无可确认的新传播因果证据。

### 7. 工程判断与覆盖
不因热度翻升改动训练方案。优先检验目标数据能否构造同场景的不同观测，并区分表示对齐和下游能力。本日实际覆盖：版本历史、main head、releases、issue状态、§2.1及§4.2；不声称重审全仓代码或重跑论文。

## 3. Mistral Large 4：为什么“预训练 loss 正常”仍可能训练出不够好的 Agent

### 1）基本信息与阅读范围

- 名称：**Mistral Large 4**，简称 ML4 / Le Chonk。发布机构及报告 PDF 元数据作者为 Mistral AI；完整贡献者名录见附录 A，不把个别转发者误列为第一作者。
- 这是官方模型技术报告，不是已经核验有 arXiv 编号的论文。alphaXiv 的 `2611.mistral-large-4` 是页面 slug，**不能写成 arXiv:2611.mistral-large-4**。
- 版本必须分开：2026-10-06 是 preview 博客发布日期；Transformers 集成提交日期为 10-29；本次实读的报告来自 11-02 更新的模型仓库，30 页，文件 SHA-256 为 `29e174cbd28b8ed85fa964dc2ab87fc5bf8b266a1672be7501e4a4b17d6a2b56`。仓库当前版本为 [`af26e7869af601441d5cdf75a1272469ddc3d059`](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/commit/af26e7869af601441d5cdf75a1272469ddc3d059)。因此本节采用报告最终表格，不把 preview 分数混进来。
- 实读：§2 预训练、§3 架构惩罚与模型手术、§4.1 任务生产、§4.2–4.5 中训练/SFT/RL/蒸馏、§5 表1–6、§6 推理、§7 结论；视觉核读图6、9、10、16、17及表3–6。另核对模型配置、许可证和 Transformers 的 attention/MoE 实现。[原报告](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/assets/technical_report.pdf)

### 2）它解决什么问题

这不是单点算法论文，而是一份从预训练到线上服务的工程报告。最值得读的问题是：**为了节省 KV cache 做出的结构优化，会不会在语言建模指标上看起来没损失，却伤害长程工具使用？**

ML4 初版把滑动窗口注意力 SWA、相邻全局层 KV 共享 CLA、后半段复用前半段 KV 的 YOCO 叠加，KV cache 相对全注意力基线缩小 16 倍。但中间 checkpoint 做 SFT 后，SWE-bench、BrowseComp 等 Agent 任务表现不及预期。报告把这种现象称为 agentic penalty：同样的 perplexity 不等于同样的多步骤任务能力。这一观察比“又一个万亿参数模型”更有研究价值。[§3、图3–5](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/assets/technical_report.pdf)

### 3）核心方法：模型、数据、训练怎样接起来

**最终模型的数据流。** 文字进入 token embedding；图像经 1.6B 视觉编码器、2×2 patch merge 和投影变成语言模型可用的表示。二者进入 72 层解码器：注意力采用 MLA 式压缩 KV 与 DSA 索引器，索引器为每个 query 选最多 2,048 个 key；MoE 层从 128 个路由专家中选 4 个，再加共享专家。第一层为 dense。总参数约 1T，49B 激活参数不计 embedding/output head，计入二者是 52B，两个数字不是模型不一致。配置给出 hidden size 6,144、KV latent 512、最大位置 1,048,576。[配置](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/config.json)

**关键不是“从头就选对结构”，而是做过模型手术。**

1. 取消原 SWA 层的窗口限制，让它们能看全上下文；取消 CLA 时，为原本借用 KV 的层复制相邻 KV 生产层的权重。
2. 加入可学习旋转频率 LeRoPE 与按头学习的 softmax query scaling（SSMax），帮助原短窗口层适应远距离信息。全尺寸模型保留原 NoPE 全局层的部分 YOCO 共享，不能概括成“全部移除 KV 共享”。
3. 在恢复训练后转为 DSA：先冻结主模型，以约 15.1B tokens 对索引器做 attention 分布 KL 蒸馏；再用 198B tokens 联训主模型及索引器。部分层共享索引器以减少开销。这里把“注意力能访问全上下文”与“每次稀疏读取有限 key”分开了。[§3.2](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/assets/technical_report.pdf)

**Agent 训练数据不是简单生成问答。** §4.1 的流水线把真实/合成 seed 转成可执行环境、任务说明、参考解和 verifier；先做廉价质量检查，再做昂贵的 agent 验证与 reward-hacking 检查，最后用多个 solver 标定难度。失败反馈回到上游修订。软件任务还检查“参考修复前失败、修复后通过”，并保留前后均通过的回归测试；refinement agent 修正题意不清、测试误杀正确解等问题。成功的出题轨迹也进入中训练数据。图9明确画的是带反馈的筛选流程，不是无检查地无限自产数据。[§4.1、图9–10](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/assets/technical_report.pdf)

**RL 与控制推理长度。** 异步 rollout 经验证、组内打分、tokenization/packing 进入 trainer；每累积 7k 条有效轨迹更新一次，使用 CISPO 风格的重要性加权 REINFORCE，处理 policy lag、MoE router replay、重分词不一致。生成中的轨迹可以跨多次权重更新。最后从高推理 checkpoint 出发，用长度奖励训练出不同预算的 teacher，再以三教师 on-policy KL 蒸馏形成同一套 low/medium/high 权重。[§4.3–4.5](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/assets/technical_report.pdf)

### 4）三点真正值得记住的贡献

1. **架构评估从 perplexity 延伸到 Agent。** 它用负结果说明：压缩 KV 的收益不能只在语言建模 loss 上验收。图6中非常接近的训练 perplexity 对应不同 SWE-bench 表现；这不是只发布最好分数。
2. **环境与验证器成为训练系统的一部分。** 有参考解也不够，还要检查题意、测试有效性、难度及可投机性。统一环境接口使 RL、评测、合成数据使用相同环境代码，减少 train/eval 环境语义漂移。
3. **把质量、token预算、服务硬件一起设计。** 多教师蒸馏控制输出长度，DSA/上下文并行/DSpark/NVFP4降低服务成本，但各自的收益有条件，不能直接叠加成一个普遍加速比。

### 5）实验到底支持什么，哪些还没证明

下表来自本次报告 §5，而不是 10-06 preview 博客；百分数均按原表精度。

| 原报告位置 | ML4 | 对照及读法 |
|---|---:|---|
| 表3：AA Coding Agent Index v2 | 48.3% | GLM-5.3 48.9%，说明接近，不是第一 |
| 表3：FrontierCode 2.0 | 19.7% | GLM-5.3 17.8%、DeepSeek V4.1-Flash 1017 19.3% |
| 表3：Terminal-Bench 4.0 | 41.0% | GLM-5.3 40.0%；与 2.1 版本的 90.2%不可混比 |
| 表3：DeepSWE 1.1 | 65.2% | GLM-5.3 66.9%、DeepSeek V4.1-Flash 74.2%，此项落后 |
| 表4：AA Cyber Index | 50.9% | DeepSeek V4.1-Flash 56.8%；单项 CyberGym-E2E-AA 则 ML4 79.0%、对照76.3% |
| 表1：AutomationBench | 57.8% | GLM-5.3 62.2%、DeepSeek V4.1-Flash 66.6%，一般工作流并非普遍领先 |

[表1–6，报告第18–19页](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/assets/technical_report.pdf)

**消融与公平性。** §3 的结构比较明确使用相同训练 token 预算；图4–6支持 SWA/CLA 的 Agent 惩罚及手术恢复，但大模型没有把所有手术方案以同等完整恢复预算重跑。§3.2.2明确说，8×10²² FLOPs尺度允许完整 phase-2恢复时去掉YOCO可恢复；8×10²³尺度只能做较短恢复时保留YOCO更好。因此结论应是“当前恢复预算下的实际取舍”，不是“YOCO先天不可用”。图中的点没有完整数表和置信区间，本日报不从像素估出伪精确百分点。

**真实成本。** 报告§2.3给出3,840张GB200、45天、约415万GPU小时、MFU 36%、goodput 94.1%。§4.4给出RL共536万条rollout、162.5B输出tokens；§4.3峰值26k并行rollout、约20k沙箱，主训练/生成3,104GPU，含评判等服务约4kGPU。它不是小团队可低成本复现的完整recipe。

**推理证据。** §6/图16的条件是50K输入长度；优化上下文并行的+51%与DSpark的+90%指8并发请求下的decode interactivity改善，前者基线为其服务实现，不是相对所有引擎。图17单层步骤从240μs降到153μs，不能直接当整模型端到端降幅。NVFP4混合精度checkpoint为606GB，校准用了200M SFT tokens，报告称评测匹配FP8并能部署于4×GB300；这不意味着普通4卡工作站可运行。[§6、图16–17](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/assets/technical_report.pdf)

**未证明的部分。** 公布了权重与推理集成，不等于公开全部训练数据、环境、训练checkpoint和逐任务RL配置；大表混合外部评测与internal结果，没有在同一个统一预算下重跑所有模型，也没有给出每个小差值的统计显著性。安全表的97.1% B3不能外推为所有提示注入都可靠。报告还主动讨论live-web评测的query-reflection污染及沙箱逃逸事件，提醒读者环境隔离与评测污染仍是未解决问题。[§4.3.3、4.4.5、5](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/assets/technical_report.pdf)

### 6）为什么今天热：事实、推断与缺口

- **事实：** 本次alphaXiv快照第3，14 likes、177 views；官方仓库刚更新技术报告，并已有可访问的FP8/NVFP4模型页和推理代码。这是平台内短时关注信号，不是论文引用量或复现数量。[alphaXiv条目](https://alphaxiv.org/abs/2611.mistral-large-4) · [官方模型页](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B)
- **合理推断：** 热度可能同时来自万亿参数开放权重发布，以及少见公开“架构误判后做模型手术”的经验。前者带来可部署性关注，后者对其他训练团队有直接参考价值。
- **证据不足：** 目前只能确认论文热度高，尚无足够公开证据解释传播原因。本次没有核验足够独立复现实验或可追溯讨论，不能声称业界已认可其结论、用户普遍更喜欢它或已有复现成功。

### 7）工程价值与代码核验

**值得带走的工程判断：** 评估混合/线性/共享注意力架构时，应把目标Agent任务加入早期缩放阶梯；做合成训练数据时，应优先投入可执行验证器与难度校准，而不只提高样本产量；服务选型应同时测单请求延迟、吞吐、并发、上下文长度和输出tokens。报告给的是要测哪些东西，不是迁移后必然获益的承诺。

代码核验截至北京时间11:43：Transformers main为[`49368678c603decb466897f92f63ce1ca4b44903`](https://github.com/huggingface/transformers/commit/49368678c603decb466897f92f63ce1ca4b44903)；ML4目录最近一次提交为[`b5e1cb8b015b6e17162a3efb9fc43dc6bf454612`](https://github.com/huggingface/transformers/commit/b5e1cb8b015b6e17162a3efb9fc43dc6bf454612)，日期10-29。已比较两版本目录blob SHA，相同；实读[`modeling_mistral_large4.py`](https://github.com/huggingface/transformers/blob/b5e1cb8b015b6e17162a3efb9fc43dc6bf454612/src/transformers/models/mistral_large4/modeling_mistral_large4.py)的`MistralLarge4TextAttention`、`MistralLarge4TextIndexer`、`MistralLarge4TextMoE`：确认KV共享、indexer复用、top-k索引、路由与共享专家相加。特别注意eager/SDPA路径把稀疏索引转为dense attention mask，**功能支持不等于获得稀疏算子的速度**。只做源码阅读，没有安装依赖、下载巨量权重或实测推理。

权重附[Mistral Ecosystem Open-Weight License](https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/af26e7869af601441d5cdf75a1272469ddc3d059/LICENSE)，其中对Model-as-a-Service商业用途另设许可条件，不能把它概括成无条件MIT模型。具体商用应按原条款判断。

## 4. Hierarchical World Models with Implicit Dynamics：让高层只选“去哪”，低层负责“怎么到”

### 1. 基本信息与实读范围
- **作者**：Gaoyue Zhou、Yvonne Wu、Zichen Jeff Cui、Nicolas Ballas、Mido Assran、Lerrel Pinto、Yann LeCun；机构包括 NYU Courant、Meta-FAIR、AMI Labs。
- **版本**：arXiv:2610.42146v1，2026-10-30 17:59:25 UTC 提交，即北京时间 10 月 31 日 01:59:25。官方项目页标注 NeurIPS 2026，属于作者项目页所述，未独立核验会议录。
- **链接**：[论文及版本记录](https://arxiv.org/abs/2610.42146v1)｜[全文](https://arxiv.org/html/2610.42146v1)｜[项目](https://id-wm.github.io/)｜[alphaXiv](https://alphaxiv.org/abs/2610.42146)。
- **实际阅读**：正文第 1–5 节，重点第 3 节方法、第 4 节主实验；附录 6.5–6.13 的规划算法、消融、推理开销和基线细节；实际查看图 2、图 4、图 7 的图像，而非只读图注。没有运行代码或复现实验。

### 2. 解决的问题
单层世界模型在长时程规划中同时遭遇两种困难：动作序列搜索空间增长，逐步预测误差累积。简单增大 frameskip 又要把很长动作压成宏动作，可能产生难搜、存在不连续性的潜在空间。本文试图保留连续精细控制，同时让高层搜索不必决定每个具体动作。它研究的是离线数据学出的模型在新目标上的规划，不是用大模型语义直接控制真实机器人的通用方案。[第 1、3 节](https://arxiv.org/html/2610.42146v1#S3)

### 3. Method：完整数据流
1. **训练高层“邻近状态生成器”**：从离线轨迹抽取当前状态与相隔 Δ 的未来状态，以当前状态为条件训练 DDPM 去噪网络。推理时用确定性 DDIM，把初始高斯噪声 z 映射为候选未来状态。z 因而成为可优化的“隐式高层动作”。
2. **训练低层前向动力学**：Transformer 接收状态/动作历史，预测下一状态。这里的“inverse dynamics solver”不是另训一个直接输出动作的逆动力学网络，而是通过搜索低层前向模型，找到通往子目标的动作序列。
3. **高层搜索**：CEM 在多步 z 序列上采样、展开若干子目标，用末端状态与最终目标的距离打分。对过大噪声加入正则，减少优化器钻模型漏洞、产生不可信跃迁。
4. **低层执行**：对每个选定子目标，再用 CEM 搜索原始动作，执行后读入新状态；一轮子目标计划完成后重新规划。默认 Δ=5、每层规划长度 5；frameskip=5，因此一个高层跨越对应 25 个环境步。每层使用 300 个候选、30 个 elite、30 次优化迭代，最多 15 轮重规划。
5. **视觉版本**：高层把 64×64 RGB 图像通过 Stable Diffusion VAE 压成 4×8×8 表示；低层使用 DINO-WM。不是从像素端到端直接预测机器人扭矩。[方法与算法](https://arxiv.org/html/2610.42146v1#S3)｜[图 2](https://arxiv.org/html/2610.42146v1#S3.F2)｜[视觉实验](https://arxiv.org/html/2610.42146v1#S4.SS6)

### 4. 主要亮点
- **把可达性与执行解耦**：高层无需预训练技能库、任务价值函数或全局行为模板，低层则保留动作级动力学。这比单纯把网络做大更直接地改变了规划问题。
- **扩散噪声成为搜索变量**：利用生成模型把规则的高斯搜索空间映射到局部状态分布，避免直接在不受约束状态空间挑子目标。注意“采样一定物理可达”是模型目标和作者的解释，不是对所有分布外状态的形式化保证。
- **控制推理预算的对照**：不仅比成功率，还给单层世界模型更多墙钟预算，仍留下明显差距，有助于区分“层次结构有效”和“只是多花算力”。[附录 6.9](https://arxiv.org/html/2610.42146v1#S6.SS9)

### 5. 实验支持了什么，尚未证明什么
**主实验。** Wall、PushT 与多尺寸 Maze 均为模拟任务；每种环境随机抽取 50 对起点/目标，表 1 报告三个种子的均值与标准差。PushT 成功要求推杆和 T 块都到目标，而 coverage 只衡量 T 块覆盖，不能把两个指标混为一谈。

| 设置 / 指标 | ID-WM | 有代表性的对照 | 含义 |
|---|---:|---:|---|
| PushT 随机目标 SR | 0.77±0.01 | SL-WM 0.21±0.04；GCBC 0.21±0.01 | 新目标比训练固定目标更能体现规划收益 |
| PushT 固定目标 SR | 1.00±0.00 | GCBC 同为 1.00±0.00 | 不是所有设置都需要复杂规划 |
| PushT-Aug 随机目标 SR | 1.00±0.01 | HIQL 0.32±0.06；H-Diffuser 0.27±0.03 | 原表舍入后出现 1.00±0.01，照录，不能解释为每次均成功 |
| Medium Maze SR | 0.99±0.01 | SL-WM 0.97±0.01 | 较容易导航任务上的增益很小 |

以上数值来自[表 1](https://arxiv.org/html/2610.42146v1#S4.T1)。摘要的“整体提升 38.5%”“较单层提升 135%”是作者汇总口径，不应当当作任一具体任务的提升幅度；判断时优先看分项结果。

**视觉和难度边界。** 视觉 PushT 的 d=75 成功率为 0.50，DINO-WM 为 0.00、HWM 为 0.14；随机目标为 0.26、0.00、0.02。但 d=25 时 HWM 0.96 高于 ID-WM 0.90，说明优势主要在长时程，而视觉随机目标仍有大量失败。[表 3](https://arxiv.org/html/2610.42146v1#S4.T3)。图 7 中 ID-WM 随迷宫增大仍明显下降，不能概括成不受规模影响；右图支持长时程比单层更稳，但没有读取曲线上的近似点作为精确数字。[图 7](https://arxiv.org/html/2610.42146v1#S4.F7)

**消融与成本。** 在 PushT-Aug 随机目标中，近似固定总搜索跨度 25，Δ=1、25 个子目标的成功率 0.06，Δ=5、5 个子目标为 0.96，支持“合理分层”，而不是子目标越多越好。单层模型从 15 次改成 45 次重规划，随机目标 SR 仅从 0.21 到 0.28，仍低于 ID-WM 0.77。单 L40S 到达一个目标的推理时间分别为 ID-WM 53.08 秒、SL-WM 16.93 秒、HIQL 5.61 秒；这是整个求解过程时间，不是单步控制延迟。状态模型使用 1–8 张 H200，视觉高层训练使用 32 张 H200，没有足够资料核算完整 GPU 小时或训练美元成本。[表 4–8、附录 6.10](https://arxiv.org/html/2610.42146v1#S6.SS7)

**公平性与证据边界。** 作者说明多数基线使用相同离线数据、目标定义和交互预算；对 HWM 的 DINO-WM 变体是作者自行复现，因为该变体没有官方开源实现。扩散基线不同执行策略也有附录对照，但不能把最慢的逐动作重规划耗时外推到所有优化过的扩散实现。成功轨迹的平均路径长也不总最优：Medium Maze 中 ID-WM 163.9 步，HIQL 34.1 步。当前证据没有真实硬件、多物体接触、复杂 3D 操作或高维状态规模化验证。[基线与路径效率](https://arxiv.org/html/2610.42146v1#S6.SS8)

### 6. 热度事实、推断与不足
- **已核事实**：本次在北京时间 2026-11-03 11:39 记录的 alphaXiv Hot / 7 days 快照中排第 4，21 likes、324 views。这是平台特定时点的排序及计数，不代表全网热度或学术共识。
- **合理推断**：世界模型、长时程规划，以及“扩散噪声作为高层动作”的简洁思路可能有传播吸引力。此为内容推断，不是已验证的流量来源。
- **证据不足**：目前只能确认论文热度高，尚无足够公开证据解释传播原因。没有核实独立复现、引用增长、外部技术讨论质量或读者偏好。不能把榜单位置写成“业界普遍认可”。

### 7. 工程价值与开源核验
**适合借鉴**：已有短时程前向模型、但长动作搜索效果差的模拟规划系统，可以先验证“高层状态提案 + 低层 CEM”的接口。建议以随机目标成功率、固定墙钟预算和路径长度三者一起评估，避免只看训练分布内表现。

**当前可用程度**：截至本次检查，官方项目仍标注代码待发布，没有可核验的官方代码 commit 或训练脚本，因此不能称作可直接复现的开源实现。完整实验规模尤其视觉版本不属于轻量部署；无价值函数的末状态距离目标也不等于最短路径规划。[官方项目](https://id-wm.github.io/)

## 5. Training Foundation Models with a Single Algorithm｜连续，昨日第2

### 1. 标识与版本
Yuda Song、Alvin Zhang等10位作者；训练算法／RL／系统。[arXiv 2610.40564](https://arxiv.org/abs/2610.40564)仍仅v1，2026-10-29 17:42:05 UTC（北京10月30日01:42:05）。

### 2. 问题
把预训练、示范学习和奖励学习写进共同的似然训练视角，使关键选择转向数据比例与时间调度；这不意味着所有有限样本RL实现等价。[原文§3–4](https://arxiv.org/html/2610.40564v1)

### 3. 方法与引用更正
静态样本与在线生成进入共享buffer，按目标token比例抽样，以加权似然更新，异步发布权重。**今日更正昨日代码链接：官方默认分支为release，不是main。** release的head仍为[5b3eaa0](https://github.com/yudasong/unified-training/commit/5b3eaa0f3ce39f695beb5d27a0bb0f92368b3118)，2026-10-30 05:09:51 UTC；与昨日记录的SHA一致。这是分支引用更正，不是新代码、分支变更时间的证据或复现实验。[当前提交入口](https://github.com/yudasong/unified-training/commits/release/)

### 4. 值得保留的亮点
同一训练器可以研究数据组合与调度的影响，有利于将“数据策略”同阶段名称分开；收益仍需区分算法、异步实现及资源预算。

### 5. 实验证据与边界
今日重核D.6：发布间隔4步不限制样本年龄，抽查的可用生成轮次落后12–44步，实际消费样本版本未记录。0%混合的3.7对28.8秒／更新约为7.8×，但用了24对16块GPU，且可重复消费旧生成。这是**更新吞吐**，不是新rollout吞吐或同算力加速；不同实现的有限样本baseline subtraction也未单独隔离。[附录D.6](https://arxiv.org/html/2610.40564v1)

### 6. 热度、讨论与发布
今日**#5，166赞／2k浏览**；昨日#2、104／1k，赞+62。[alphaXiv](https://www.alphaxiv.org/abs/2610.40564)。[releases](https://github.com/yudasong/unified-training/releases)为空；公开仓库`updated:>=2026-11-01`的issue／PR搜索为空，仅代表本次查询范围。未确认新实验、公开复现或足以解释热度的讨论证据。

### 7. 工程判断与覆盖
维持观察，真正可改变判断的信号是消费样本年龄日志、相同资源预算对照或新实现。今日覆盖版本、仓库元数据及release head、releases、近期issues、§4.3及D.6；没有运行训练或测试。

## 6. Probing Spatial State Representations in Visual Foundation Models｜连续，昨日第3

### 1. 标识与版本
Baiqiao Yin、Zhongang Cai、Ruisi Wang、Qiwei Liang、Lei Yang、Ziwei Liu；视觉表征／空间状态评估。[arXiv 2610.40636](https://arxiv.org/abs/2610.40636)仍为v1，2026-10-29 17:58:16 UTC（北京10月30日01:58:16）。

### 2. 问题
“能从特征读出空间信息”是否等于能保持、更新并用于行动？论文用四级冻结特征探针拆分这些能力，不直接训练闭环机器人。[原文§2–4](https://arxiv.org/html/2610.40636v1)

### 3. 方法与代码增量
L1结构→L2物体持久性→L3预测更新→L4行动用途，分别控制历史、运动与目标信息。官方main仍为[a0a9404](https://github.com/yyyybq/Probing_Spatial_State_Release/commit/a0a94043271a7ba19b03970ca8ca0ed885fec57a)。**11月2日已报道的README补充今天没有后续commit，不应再算作今日新增。** [releases](https://github.com/yyyybq/Probing_Spatial_State_Release/releases)仍为空。

### 4. 值得保留的亮点
把目标敏感性与目标实际效用区分开来，比只看探针准确率更接近行动需求；也让“可读出”到“可使用”的论证链可逐项验收。

### 5. 实验证据与复现缺口
今日核§4.5／Fig.5(b)：换目标能使预测方向改变29.8–45.6°，但正确相对打乱目标的正向进展增益仅−2.3至+1.2个百分点，95%区间全部跨零，不能说已有可靠目标效用。[原文§4.5](https://arxiv.org/html/2610.40636v1)。今天重读固定README：作者仍称主表70格中62格可按已有CSV重建，CogVideoX layer20整行及Wan view consistency未补；L4、历史控制、原生预测readout、共同窗口与区间材料仍不在仓库。本次未重算这些格。[Paper and code](https://github.com/yyyybq/Probing_Spatial_State_Release/blob/a0a94043271a7ba19b03970ca8ca0ed885fec57a/README.md#paper-and-code)

### 6. 热度与公开讨论
今日**#6，52赞／626浏览**；昨日#3、35／374，显示值+17赞／+252浏览。[alphaXiv](https://www.alphaxiv.org/abs/2610.40636)。仓库近期issue／PR查询无条目。没有可确认的新独立复现；关注增加不等于缺失实验已补齐。

### 7. 工程判断与覆盖
可参考L1–L3探针设计，依赖L4时仍应等待对应材料。README还说明无公开probe checkpoint或feature cache，复跑不等于直接加载结果。[Resources](https://github.com/yyyybq/Probing_Spatial_State_Release/blob/a0a94043271a7ba19b03970ca8ca0ed885fec57a/README.md#installation)。本日覆盖版本、head、固定README、releases、issues、§4.4–4.5；不运行代码，不声称全结果可复现。

## 7. Hierarchical Residuals：把“存多少信息”与“每层算多宽”分开

### 1）基本信息与阅读范围

- 全名：**Hierarchical Residuals: A Minimalist Decoupling of Residual Width from Compute Width**；简称HiRes。
- 作者：Ziteng Wang、Jianqiao Lu、Xinyu Ma、Jintao Zhang、Jun Zhu、Yiyuan Ma、Jianfei Chen；清华大学与ByteDance Seed，Yiyuan Ma、Jianfei Chen为通讯作者。
- arXiv:2610.41711v1，提交时间2026-10-30 13:18:22 UTC（北京时间10-30 21:18）；本次PDF首页内印日期为11-02。两者如实并列，不把PDF内日期误称v2发布时间。[版本记录](https://arxiv.org/abs/2610.41711)
- 实读正文§1–6，附录A伪代码、B训练配方、C详细结果、D消融、E复杂度、F系统优化、G潜空间解释、H局限；重点核表1–3、5–10、13。视觉核读图1、2、4及表2、3。27页PDF，原文采用[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)；以下为改写与分析，非作者背书。[论文PDF](https://arxiv.org/pdf/2610.41711)

### 2）它解决什么问题

普通Transformer里，跨层保存信息的残差向量宽度与attention/FFN处理的宽度都为d。想让网络“记住更多”往往意味着每层也变宽，计算成本随之上涨。已有HC/mHC/VWN等方法扩展残差状态，但每层混合多条流会带来激活读写和定制kernel负担。

HiRes问：能否保留一条更宽的信息通道，却让绝大多数层仍按原来的d维工作？它不是新attention，也不是增加上下文长度，而是改造**跨深度的信息传输与更新方式**。[§1–2](https://arxiv.org/pdf/2610.41711#page=2)

### 3）核心Method与数据流

把L层分成B个连续块。外部残差为D维，内部计算仍为d维，扩展率n=D/d，默认n=2、B=4。一个token的路线是：

1. embedding得到d维表示，再经E投影成D维外部状态h₀。
2. 第b块用可学习read矩阵R_b，把h_{b−1}从D维读到d维。
3. 在这个d维空间内照常运行L/B层PreNorm Transformer，attention、FFN和内部残差规则不变。
4. write矩阵W_b把整个块的输出从d维写回D维，与原外部状态相加，再做RMSNorm：h_b = RMSNorm(h_{b−1} + W_b Φ_b(R_b h_{b−1}))。
5. 最后由head projection读回d维，经过final norm和LM head输出logits。

因此有两个尺度：块内PreNorm保证常规计算，块间PostNorm约束宽残差的累积幅度。关键是**read/write只在块边界发生**，额外dense投影由逐层Θ(LDd)降到逐块Θ(BDd)。接口初始接近identity嵌入/投影，通过门控逐步学习，减少早期坐标突变。图1和附录A的伪代码对此一致。[§2、图1](https://arxiv.org/pdf/2610.41711#page=3) · [附录A](https://arxiv.org/pdf/2610.41711#page=15)

### 4）三个亮点

1. **把残差宽度变成独立可调变量。** 不是把FFN或attention全体加宽，而是扩大跨块可保存的状态；其“记忆带宽”和“运算宽度”可以分别分配。
2. **提出了可分解验证的简单结构。** HiNorm只保留边界归一化，n=1版本保留接口却不扩宽，冻结read/write、移除外部残差等消融能分别检验收益来源。
3. **追求已有算子就能实现的收益。** dense projection、RMSNorm、相加即可构成方法，论文比较了PyTorch和Triton实现，而不只用理论FLOPs宣称便宜。它的卖点是相对其他扩展残差方法的低开销，不是完全零开销。

### 5）实验支持、消融、公平性与局限

**训练背景。** dense实验基于OLMoE代码，训练语料为OLMo2 stage-1 mixture，Dolma2 tokenizer，4096上下文。相同规模的架构用相同数据顺序和sample-index数组；验证为Paloma的11个域，下游为12项任务。不同dense尺度分别训练30B、50B、100B、200B、350B tokens。训练loss取最后1000步均值，验证/任务结果取最后3次评测的均值。这能减少末点波动，但**不是3个独立随机种子**。[附录B、表4](https://arxiv.org/pdf/2610.41711#page=15)

**最容易被误读的1.30×。** 图2在验证loss=3.00处，由五档模型的loss-compute拟合得到“baseline所需FLOPs/HiRes所需FLOPs=1.30”。模型范围约70M至626M基线参数，拟合使用解析训练FLOPs并计入HiRes额外参数。它不是固定模型每步快30%，也不是所有规模均节省30%计算；换算这一目标loss处节省比例为约23.1%，且仍是拟合估计。[§3.2、图2](https://arxiv.org/pdf/2610.41711#page=5)

**表2的实际质量/开销，d=768、L=12、50B tokens：**

| 指标 | 原始baseline | HiRes | 有代表性的其他方法 |
|---|---:|---:|---|
| validation loss，越低越好 | 3.1941 | 3.1300 | VWN-4为3.1228，更低 |
| 12任务平均accuracy | 46.91% | 47.15% | mHC-4为47.33%，更高 |
| 每token每子层的解析activation I/O | 3d | 4.58d | mHC-4/VWN-4均17d |
| 每GPU峰值显存 | 16.31GiB | 16.86GiB | Block AttnRes-4为17.18GiB |
| 总吞吐 | 0.682M tok/s | 0.625M tok/s | Block AttnRes-4为0.639M tok/s |

这组数据支持“HiRes是质量与开销较好的折中”，不支持“所有指标胜过所有方法”。这里对齐的是内层宽度、深度和tokens，**不是完全相同参数/FLOPs**：表5的baseline为138.433M参数、6.4186×10¹⁹ FLOPs，HiRes为150.235M参数、6.7727×10¹⁹ FLOPs。三尺度优化后的HiRes吞吐为baseline的91.7%–93.1%，显存增加3.3%–3.4%；它事实上比未扩展baseline慢。大一点的(1280,20)尺度，HiRes平均accuracy为52.76%，高于baseline51.90%及这里的其他残差扩展对照。[表2](https://arxiv.org/pdf/2610.41711#page=7) · [表5](https://arxiv.org/pdf/2610.41711#page=16)

**稀疏MoE迁移证据。** OLMoE-1B-7B基线6.9B总参数、1.3B激活参数，训练500B tokens；HiRes增加83.9M参数，约总参数1.2%/激活参数6.5%。表9：训练loss 2.3663→2.3455；验证loss 2.3491→2.3311；12任务均值64.24%→65.38%，提高1.14个百分点。但COPA 87.67→86.67、CommonsenseQA 49.88→49.66、WinoGrande 67.17→67.01，说明并非逐项皆涨。[图4](https://arxiv.org/pdf/2610.41711#page=7) · [表9](https://arxiv.org/pdf/2610.41711#page=19)

**因果证据主要来自消融。** 同一(768,12)/50B设置，完整HiRes验证loss 3.1300；只做HiNorm为3.1714；等宽n=1为3.1573；冻结随机read/write变3.1614；去边界RMSNorm变3.1552；去外部残差变3.1616；取消接口稳定初始化变3.1375。这表明扩宽、可学习接口、归一化和外部残差都在该配置中有贡献，不能把收益完全归于“多加一层norm”。n=2、B=4附近呈现收益/开销拐点，继续增大仍可能改善，但边际收益减弱。[表3](https://arxiv.org/pdf/2610.41711#page=9) · [表10](https://arxiv.org/pdf/2610.41711#page=20)

**系统比较的边界。** 附录F在8GPU、FSDP FULL_SHARD、bf16、4096序列、每GPU microbatch=4下测前向+反向+优化器步，采用同一attention/MLP/测量框架。每种方法由独立优化过程改进，候选需通过输出/梯度正确性检查。HiRes纯PyTorch吞吐91.7%–93.0%，显存+5.5%–5.7%；Triton主要再降显存。由于优化由特定agent搜索驱动、未证明找到每种方法的全局最优实现，不能把本次排名看成所有硬件和工程投入下的最终结论；本次读取段落也未定位到GPU具体型号。[附录F、表13](https://arxiv.org/pdf/2610.41711#page=24)

**尚未证明。** 作者附录H直接承认：尚未在固定算力下联合优化D、d、L；只试等长块，未探索不均匀访问外部状态；宽残差究竟保存什么信息仍缺机制解释。论文也没有超大规模dense模型、长上下文推理、SFT/RL后Agent能力及多随机种子置信区间的充分证据。较少的每层I/O不等于免费推理，更不等于能直接无损改造现成checkpoint。[附录H](https://arxiv.org/pdf/2610.41711#page=27)

### 6）热度：已知什么、不能推断什么

- **事实：** 本次alphaXiv快照第7、6 likes；views未提供，留空而不写0。它是新近提交的架构工作，研究对象正好与HC/mHC/VWN/AttnRes等近期残差扩展方法相交。[alphaXiv](https://alphaxiv.org/abs/2610.41711)
- **合理推断：** “不改Transformer子层、只在块边界投影”容易被现有训练栈试验，且系统开销表直接回应新架构落地痛点，这可能比单个loss数字更吸引工程读者。
- **证据不足：** 目前只能确认论文热度高，尚无足够公开证据解释传播原因。本次未核验到可确认由作者发布的独立项目页/实现仓库，也没有足够独立复现或讨论证据，不能写“代码已开源”“社区已广泛复现”。检索到的ResTok/HiResNets/HiRes-LLaVA均为其他论文，不能借用其代码链接。

### 7）工程价值与当前可复现程度

**值得试的场景是新一轮预训练架构实验。** 对显存/带宽敏感、又不想引入复杂残差kernel的团队，HiRes提供了一个清晰的低复杂度候选。建议验收问题是：同一GPU小时预算下是否胜过加宽/加深baseline？是否只是提升平均loss而损害某些下游任务？增宽状态是否影响激活checkpointing、张量并行、推理缓存与部署代码？这些是后续实验设计建议，不是本次已完成的验证。

**复现材料现状：** 原文有附录A forward伪代码、训练超参、数据来源、各尺度结果、成本推导；原文未给出作者仓库链接。本次对论文全文、arXiv信息和精确标题/作者检索后，仍未确认官方代码，所以**没有可核验的HiRes代码commit、requirements或训练入口**。本文只核读伪代码，不能把“使用OLMoE codebase”写成“HiRes完整代码已公开”。

**一句判断：** 对训练研究者，它比“换全套attention”更容易做受控实验；对只部署既有模型的工程师，目前更值得理解设计原则，而不是立即改线上checkpoint。

## 8. FlatCake: A Flat KVCache Storage Architecture for LLM Serving｜连续，昨日第9

### 1. 标识与版本
Xin Huang、Teng Ma、Zhuoran Li等10位作者；LLM serving／KV存储与I/O。[arXiv 2610.38355](https://arxiv.org/abs/2610.38355)仍仅v1，2026-10-28 06:54:51 UTC（北京14:54:51）。昨日已完整展开，今天重点核版本、代码与端到端结果口径。

### 2. 问题
SSD里的KV不一定来得及送到GPU；host暂存争用、预取撤销及分散布局会把本可命中的缓存变成重算。[原文§2](https://arxiv.org/html/2610.38355v1)

### 3. 方法与变化
DRAM／SSD作为同级后备介质，一次放置；按session顺序落盘，以双队列区分已就绪与SSD准备请求，经GDS合并读取。今天核§4：仍有双缓冲GPU暂存与scatter，**不是完全zero-copy**。未见v1之后的方法修订。[§3–4](https://arxiv.org/html/2610.38355v1)

### 4. 值得保留的亮点
指标从“目录里有缓存”转向“prefill前真正送达GPU”，布局、调度和传输合看；这比仅换成GDS更具有系统设计价值。

### 5. 实验证据与范围
今日回核§5／Fig.6：主端到端仍是Claude Code单轨迹。1QPS时mean TTFT为7.57秒，对Mooncake 12.24秒，约低38%；total token吞吐98.3K/s对61.6K/s，不能改称生成token速度。八条trace是动机分析，不是八份端到端验证；Mooncake-GDS额外对照在Llama-3.1-70B context sweep。[§5.1–5.4、Fig.6/10](https://arxiv.org/html/2610.38355v1)

### 6. 热度与代码可用性
今日**#8，83赞／5k浏览**；昨日#9、20／992，赞+63。[alphaXiv](https://www.alphaxiv.org/abs/2610.38355)。今天重读[共同作者Teng Ma主页](https://stmatengss.github.io/)，FlatCake条目仍只提供arXiv入口；GitHub仓库名搜索无结果。故只能写**尚未定位可核实的官方实现／release**，不能断言绝对未开源，也无法可靠审查其commits或issues。没有新独立复现证据。

### 7. 工程判断与覆盖
适合长上下文、高KV复用服务团队研究，但暂不作为可直接安装的系统。等待代码、重放配置和不同负载实测；此前已具备的详细系统分析不重复算今日工作。本日实际覆盖版本、作者主页、GitHub仓库搜索、§4–5关键实现和对照口径；不下载权重、不安装或运行论文代码。

## 9. Movens-Zero：把互联网人体视频变成可执行的人形机器人动作数据

### 1. 基本信息与实读范围
- **作者**：Wendong Bu、Tinghong Ye、Qizhou Wang、Jiacheng Li、Zhiqi Ge、Yuze Lin、Zhongqi Yue、Yi Su、Jingyu Wang、Kai Shen、Jingdong Liu、Chengyuan Deng、Xiaoxuan Chen、Xin Tan、Jiaming Ji、Wenqiao Zhang、Chenghong Jiang、Tuoyu Li、Siliang Tang、Jun Xiao、Tat-Seng Chua、Yueting Zhuang、Xingxing Wang、Juncheng Li。第一作者组来自浙江大学、宇树及联合实验室等。
- **版本**：arXiv:2610.41877v1，2026-10-30 15:25:49 UTC，即北京时间 10 月 30 日 23:25:49；技术报告，未把它当作已通过同行评审的论文。
- **链接**：[论文与版本](https://arxiv.org/abs/2610.41877v1)｜[全文](https://arxiv.org/html/2610.41877v1)｜[项目](https://movens-zero.github.io/)｜[代码](https://github.com/wendell0218/Movens-Zero)｜[alphaXiv](https://alphaxiv.org/abs/2610.41877)。
- **实际阅读**：正文第 3–6 节数据、benchmark、方法和实验；附录 B–E 的重定向、40 维表示、训练和评测，以及 F.3 失败分析；实际查看图 2、图 7、图 8。静态阅读了当前 commit 中的推理配置、训练损失、RTC 推理实现、训练入口、评测和部署文档。没有下载完整权重/训练集，没有运行任何仓库代码或机器人流程。

### 2. 解决的问题
互联网上人体视频多，不等于适合机器人训练的动作多。遮挡、镜头运动、重建错误、人与机器人的肢体差异，都可能把视觉上合理的动作变成机器人无法跟踪的轨迹。另一难点是把文本、语音、音乐和视频放进同一个动作生成器，又不能牺牲闭环执行连续性。本文的主要投入首先是数据与评测体系，再是统一模型，不能简化成“拿 3B 模型控制机器人”。[第 3、5 节](https://arxiv.org/html/2610.41877v1#S3)

### 3. Method：从视频到闭环执行
1. **视频数据工程**：原视频级拆分、去近重复、AutoShot 切片；质量及人体运动筛选；用视觉语言模型生成分时间段和身体部位的描述；GVHMR/PromptHMR 重建后统一到 SMPL-X。
2. **两轮物理校验**：先检查地面接触、抖动、跌倒风险、穿插和滑步，局部异常用 Kimodo 修补并重新检查；再通过 GMR 初始化、联合优化关节与根轨迹、接触和关节限位约束，重定向到 G1。最后用跟踪器在模拟中验证。完整策略库最多使用四个跟踪器，但**不是每条轨迹都必须四个全通过**；被评估策略中有一个成功即可保留。
3. **统一意图编码**：冻结 Qwen2.5-Omni-3B，预缓存最后一层 2048 维条件 token。文本、音频、视频共用该理解骨干，而不是每种输入独立训一个机器人模型。
4. **动作专家**：flow-matching Transformer 联合注意条件 token、最新机器人状态 token 和带噪动作 token。每帧输出 40 维：29 个关节角、2 维平面根位移、6 维根朝向、1 维根高度、2 维足接触。生成的是可交给跟踪器的参考运动，不是直接输出电机扭矩。
5. **MM-RTC**：50 Hz、每次生成 30 帧，执行 20 帧，保留 10 帧未执行尾部。下一次以新观测状态重新编码这段前缀，并在 10 步 Euler 采样中固定前缀，再生成后续动作。训练随机保留 0–10 帧干净前缀，仅对其余片段计算 flow loss。七种训练任务是文本，以及音乐/语音/视频各自带或不带文字提示，按数据量混合。[图 2](https://arxiv.org/html/2610.41877v1#S1.F2)｜[图 7 与第 5 节](https://arxiv.org/html/2610.41877v1#S5)｜[附录 D](https://arxiv.org/html/2610.41877v1#A4)

### 4. 主要亮点
- **把执行验证纳入数据定义**：Movens-5M 报告 1500 万人体动作、500 万机器人动作、超过一万小时，而不是仅报告视频量。构建流程保留源视频、时间戳、重定向参考和跟踪结果，工程上可审计。
- **共享表示贯穿多模态生成与反馈**：40 维状态/动作约定、chunk anchor、归一化和重叠前缀都明确，减少上层生成和低层执行接口错位。
- **不仅展示 demo，还做质量与规模对照**：原视频级数据子集、不同动作专家大小、等样本量数据清洗消融，分别检验数据覆盖、容量和质量的贡献。仍不能把这些有限范围实验称为已建立可外推的普遍 scaling law。[第 6.4 节](https://arxiv.org/html/2610.41877v1#S6.SS4)

### 5. 实验支持了什么，尚未证明什么
**规模实验。** Movens-Intent 四种输入各 2048 对，总计 8192 个经专家检查的条件/动作对，按源视频与训练集分离。固定 XL 动作专家 910.5M，训练数据从 1% 增至 100%，Text R@3 从 12.72% 到 62.57%，Video MPJPE 从 132.82 到 40.90 mm，Speech R@3 从 13.98% 到 74.30%，Tracking Score 从 0.21 到 0.72。全量数据训练下，动作专家从 64.2M 到 910.5M，相应 Text R@3 为 10.30%→62.57%，Video MPJPE 为 108.50→40.90 mm。表 7 的全量 unique hours 为 12,231，与“超过一万小时”的摘要口径不冲突。[表 7、8](https://arxiv.org/html/2610.41877v1#S6.T7)

**对现有方法的结果不是所有指标碾压。**
- 文本 OMG：R@3 85.06%，最强列基线 HY-Motion 57.71%；但更接近未知来源泛化的 Movens-Intent 上为 62.57% 对 61.87%，只高 **0.70 个百分点**。该 benchmark 的 FID 为 17.65 对 HY-Motion 30.19，采用原表缩放口径，不与其他论文不同单位的 FID 直接混比。[表 3](https://arxiv.org/html/2610.41877v1#S6.T3)
- 语音 Movens-Intent：R@3 74.30% 对最强基线 62.40%，跌倒率 0.00%；但关节越限 4.93%，不如 OMG-XL 的 2.00%。语音 benchmark 是选定文本由 16 个平衡英语 TTS 声音合成，不等于真实噪声环境、口音和开放对话指令测试。[第 4.2 节](https://arxiv.org/html/2610.41877v1#S4.SS2)｜[表 6](https://arxiv.org/html/2610.41877v1#S6.T6)
- 音乐 Movens-Intent：BeatAlign 0.61，最佳基线 0.60；FID-k 58.43，对最佳基线 LODGE 59.43，优势较小；关节越限 **14.72%**，明显差于 GENMO 的 **5.27%**。因此“模拟中不跌倒”不能等同于动作约束全面达标。[表 5](https://arxiv.org/html/2610.41877v1#S6.T5)

**数据消融。** 等样本量、等优化 token 预算下，原始重建到完整流水线使 Video MPJPE 126.82→40.90 mm，Tracking Score 0.41→0.72。物理修补一阶段把 score 0.48 提至 0.58，加跟踪验证到 0.67，再平衡到 0.72。它是逐步累加消融，不是每个部件彼此独立的因果估计。去掉音频对齐而保留动作样本后，视频 MPJPE 从 40.90 升到 66.07 mm，支持跨模态共同训练有帮助，但还不能定位全部改善机制。[表 9](https://arxiv.org/html/2610.41877v1#S6.T9)

**公平性与现实边界。** 作者报告公共测试源去重、统一 G1 表示与模拟/跟踪配置；OMG 部分保留公开基线成绩而不是全部重训。视频 RICH/EMDB 还将 G1 输出反向重定向到 SMPL，指标含表示转换影响。数据集质量比较最多各抽 1000 条完整序列，所有场景被放在平地，没有补回原场景家具、物体和地形，因此不是“拿东西、上楼”等真实任务成功率。论文演示了 G1 硬件案例，但没有给全场景硬件成功率和完整端到端时延分布。附录明确高速接触动作、剧烈镜头运动仍会失败；图 8 是离线渲染姿态对比，不能当成真机测试。[评测协议](https://arxiv.org/html/2610.41877v1#A5)｜[失败分析](https://arxiv.org/html/2610.41877v1#A6.SS3)

**计算成本。** 附录 L 模型配置为 8 GPU DDP、全局 batch 512、最多 100 万步，但注明该步数是上限，不是每个运行都跑满；所读部分没有完整 GPU 型号、训练耗时和成本表。模型规模 64.2M–910.5M 只计动作专家，不包括理解骨干，不能当作端到端系统参数量。部署 README 规定每 chunk 180 ms 截止时间，这是实现要求，不是已验证的普适硬件测速。[训练配置](https://arxiv.org/html/2610.41877v1#A4)｜[部署说明](https://github.com/wendell0218/Movens-Zero/blob/5306ce203eb18db4628850e323a980d9ba6422d0/sim2real/README.md)

### 6. 热度事实、推断与不足
- **已核事实**：本次北京时间 2026-11-03 11:39 的 alphaXiv Hot / 7 days 快照中排第 9，10 likes；views 未提供，不补造。代码页本次显示 6 stars、1 fork，另属 GitHub 时点事实，不和 alphaXiv 计数相加。
- **合理推断**：500 万执行验证动作、多模态单模型、G1 真机演示和代码/权重发布的组合具有传播吸引力。它更像数据基础设施与机器人多模态接口工作，而非单个新网络模块。
- **证据不足**：目前只能确认论文热度高，尚无足够公开证据解释传播原因。未核到独立复现或大规模外部部署，不能以公开视频或小规模点赞推导社区共识。模型卡、代码存在与完整可复现也不是一回事。

### 7. 工程价值与当前发布物核验
**固定版本核验。** 本次 GitHub API 读取的 main 为 **5306ce203eb18db4628850e323a980d9ba6422d0**，提交时间 2026-10-29 01:56:37 UTC。实际存在并静态阅读：
- `configs/inference_xl.json`：40 维、30/20 帧、50 Hz、10 步采样与论文接口一致。
- `movens_zero/model.py` 的 `predict_action_rtc`：每一步及最终都恢复前缀，确实实现硬前缀约束；`rollout_root40.py` 做 anchor 重编码。但离线生成循环用预测状态继续，不能和硬件实际状态反馈混称。
- `training/objective.py`：前缀零噪声、排除前缀损失；`training/train.py` 与 README 提供继续训练流程。
- `evaluation/score_tracking.py` 与评测文档：HoloMotion 跟踪路径及依赖固定哈希；`sim2real` 提供 GPU 服务端和 G1 客户端。[固定 commit](https://github.com/wendell0218/Movens-Zero/tree/5306ce203eb18db4628850e323a980d9ba6422d0)

**复现时要注意的差异。** 公开训练入口默认可更新 Qwen，需显式开启冻结选项，且该入口的学习率调度/数据路径不是论文“冻结特征缓存 + cosine”的完整原始大规模配方。因此有训练代码不等于论文训练全过程开箱复现。部署文档写运动进行中禁用输入修改，也不应直接照摘要宣传成当前公开客户端可任意即时换指令。[训练入口](https://github.com/wendell0218/Movens-Zero/blob/5306ce203eb18db4628850e323a980d9ba6422d0/training/train.py)｜[客户端说明](https://github.com/wendell0218/Movens-Zero/blob/5306ce203eb18db4628850e323a980d9ba6422d0/sim2real/README.md)

**数据与权重确实有发布入口，但需分层看。** [XL 文件页](https://huggingface.co/wendell0218/Movens-Zero-XL/tree/main)列出 21.8 GB 的 `model.safetensors`，提交短哈希 792a44d。中心 [Movens-5M 页面](https://huggingface.co/datasets/wendell0218/Movens-5M)可预览的是 1000 条、5.52 GB，不能误认成只发布 1000 条；数据卡另外指向三份完整数据仓库。本次打开三库，显示约 4.88 TB、4.95 TB、349 GB，但预览器分别有 split/生成错误。因此确认的是文件仓库存在，未核验 500 万记录完整性、可加载性与样本对齐。[分库 0](https://huggingface.co/datasets/OmniHM-5M-0/OmniHM-5M-0)｜[分库 1](https://huggingface.co/datasets/OmniHM-5M-1/OmniHM-5M-1)｜[分库 2](https://huggingface.co/datasets/OmniHM-5M-2/OmniHM-5M-2)

**工程判断。** 研究价值较高，适合优先验证 40 维接口、前缀连续性、固定评测协议和小规模再训练；尚不适合据此承诺工业真机可靠性。仓库 README 还明确项目代码/权重专属许可未确定，数据卡标为 `other`，均不能仅凭公开下载就推断可商用或再分发。现阶段最实际的收益是吸收“先数据执行验证、再规模训练”的流程，并在自己目标机器人及场景上单独验证。[发布许可说明](https://github.com/wendell0218/Movens-Zero/blob/5306ce203eb18db4628850e323a980d9ba6422d0/README.md#license)

## 10. Training language models in simulation for psychiatric intake｜连续，昨日第4

### 1. 标识与版本
Samuel Schmidgall、Tim Strother、Alex Bijamov等56位作者；医疗对话Agent／RL／评估与安全。[arXiv 2610.40476](https://arxiv.org/abs/2610.40476)仍仅v1，2026-10-29 17:10:32 UTC（北京10月30日01:10:32）。

### 2. 问题
模型能否主动问出患者未披露的信息，并完成结构化评估？研究的是模拟训练及受控角色扮演，不是真实患者治疗效果。[原文§1–2](https://arxiv.org/html/2610.40476v1)

### 3. 方法与变化
隐含患者资料→多轮工具交互→临床rubric及安全惩罚→GRPO更新→独立医师评分。今日回读§4.3–4.4，方法未确认变化；训练与评测的惩罚组合也并非完全相同，不能只凭合成reward推断临床可用。[Methods、Fig.7](https://arxiv.org/html/2610.40476v1)

### 4. 值得保留的亮点
评测主动追问信息的过程，同时以人工角色扮演核验模拟收益。对通用Agent最有用的启示是检查遗漏与验证环境迁移，而非照搬医疗部署。

### 5. 实验证据与边界
今日核§2.2／Fig.3：同一自动评分器下，以模拟患者替代医师扮演患者，会把训练模型相对基座的平均优势从0.21放大至0.34。保持此前区分：60.6%是完整性漏问指标，12.9%是对抗急性风险分流不足；二者不是同一安全分数。无新实验，也未证明真实患者安全。[§2.2、Table2、补表7](https://arxiv.org/html/2610.40476v1)

### 6. 热度、讨论与发布
今日**#10，74赞／2k浏览**；昨日#4、51／2k，赞+23。同为2k只是界面缩写，不代表浏览没变化。[alphaXiv](https://www.alphaxiv.org/abs/2610.40476)。未确认新的作者或独立研究者复现实验；聚合站解读不当作独立验证。

### 7. 可用性、工程判断与覆盖
今天重核Data／Code Availability：代码仍明确暂不开放，127例评测资料仍在探索分享；无可核实官方仓库，commits／releases／issues不适用，不能伪造代码审阅。可学习离线评测设计，不能据此推进无人监督临床使用。[数据与代码声明](https://arxiv.org/html/2610.40476v1)。本日覆盖版本、§2.2–2.3、Methods奖励／GRPO及开放声明；未重读全部76页或执行医疗实验。

## A. 今天最值得深入读的三项

1. **Mistral Large 4技术报告**：优先读注意力共享架构消融与agent评价，而非只看参数／排行榜。对coding-agent架构选型最直接的启发，是将长链工具任务作为独立验收轴，不能仅用预训练loss或短题能力替代。具体原文、模型配置和推理实现见第3项。
2. **Weight-Space Programming**：优先读实验8与Gemma反例，再沿`exp8_math/code/apply_edit.py → edit/manifest.json → eval/*/merged.json`核查补丁、计数和结果；同时读实验7静态权重失败案例。它值得研究的是带约束的agent诊断及审计链，不是立刻替代优化器。
3. **Hierarchical Residuals**：先读方法图、投影／提升与宽窄残差连接，再读scaling和消融。相较直接增大所有层宽度，它给自训模型一个可隔离验证的结构假设；但FLOPs拟合收益不能转换成已证实的生产吞吐收益。

这三项是学习／工程研究优先级，不是部署建议。KV密集推理团队可把持续上榜的FlatCake替换为第三阅读优先项，但仍需等可核实实现与多负载验证。

## B. 从今天前十看到的技术方向

1. **模型内部结构与agent行为必须分开验收。** ML4检验注意力共享对agent任务的代价；权重编程在循环修复上成功、在非循环Gemma上未确立增益。共同支持的是“任务级验证不能由局部代理指标代替”，不支持所有任务都能局部编辑解决。
2. **分层与解耦是本日多个设计的具体工具。** Hierarchical World Models把远目标可达性与低层执行分开；HiRes分开残差状态宽度与计算宽度；FlatCake分开就绪与SSD准备请求。这些分别作用于规划、网络结构、系统I/O，不能视为同一种算法或从单日断言长期范式胜出。
3. **视频数据到可执行动作仍有中间验收链。** Movens-Zero用物理验证与重定向筛运动；Spatial State区分读出空间信息和行动用途；ID-WM的视觉随机目标表现仍远弱于状态输入。生成好看、表示可解码、闭环可执行三者不能合并。
4. **公开材料的粒度决定可验证程度。** 权重编程有逐张量差分和部分外部重跑，Spatial仍缺若干实验材料，FlatCake未定位官方实现，精神科代码不开放。论文／报告存在、材料开放、重现通过必须分级记录。

以上仅从今日十项提炼，不代表整个AI领域的统计趋势。

## C. 与昨天相比

对比2026-11-02北京时间11:21:54–11:22:39的实际7日Hot快照，今天11:39–11:44同口径：

- **新入前十五项**：Weight-Space Programming（#1）、Mistral Large 4（#3）、Hierarchical World Models（#4）、Hierarchical Residuals（#7）、Movens-Zero（#9）。“新入”仅指昨日十项中没有，不等于今天首次发表；其中两项是11月2日的博客／报告，其余有10月30日论文版本。
- **持续五项**：PRH #1→#2；Unified #2→#5；Spatial State #3→#6；FlatCake #9→#8；Psychiatric #4→#10。五篇均未核到新arXiv版本或新实验，排名变化不自动更新技术结论。
- **本次前十未见**：SpecSlot、Loop Transformer、Robotic Data Inoculation、Cross-Controller、L3G-World。没有检查它们在全榜的精确名次，不能说热度已下降到某个数或研究价值消失。
- **计数与排名并非同义**：PRH赞164→324同时名次下降；FlatCake20→83且名次上升一位。浏览中的k缩写不能用于精确增量，HiRes／Movens未显示浏览值，不写成零。
- **新的研究主题**：agent直接诊断／编辑权重，以及大型模型注意力共享和agentic能力之间的权衡，今天进入前十；层级规划和残差解耦也成为新增阅读重点。只能确认本次榜单组成变化，不能据一天变化认定方向持续升温。
- **需要修正的既有引用**：Unified Training默认分支是`release`，昨日`main`地址应纠正；固定head仍5b3eaa0，所以不是新代码发布。Spatial昨日README补充今天head未变，不能重复当新进展。

## 覆盖与未验证事项

- 完整保留当前前十，不用榜外材料替换。新入项实际核原文方法／实验及可用代码；持续项重核版本、关键原文和已定位代码增量，具体章节、文件和缺口见各项。未重新全文审查所有持续项。
- 没有把alphaXiv摘要当原论文，博客和技术报告明确区分；未核到的arXiv编号、时分、代码实现、热度传播原因均不补造。
- 社区传播覆盖有限：可读作者内容、公开项目页／issues及原始复跑材料可作证据，没有全站X/HN/Reddit扫描，也没有根据加载失败断言无讨论。
- 所有研究代码仅只读；没有训练、复现、安装、部署或修改模型。报告中“确认”指来源或材料确认，不是dot独立实验。
