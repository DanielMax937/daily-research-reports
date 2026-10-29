# AI 论文日报｜2026-10-29（受限榜单＋三篇原文与代码研究）

## 先读结论与实际覆盖

**今天没有足够证据交付“alphaXiv 当日热门 Top10”。** 本报告保留这个缺口，提供三篇清楚标注的补充研究，而不是用推荐流、搜索结果或旧缓存补足十篇。

- 报告日期：Asia/Shanghai 2026-10-29；正常首页抓取约北京时间 **11:46**（原 UTC **03:46**）；原文/代码核验截至 **11:51**（UTC **03:51**）。
- 实际读取：[alphaXiv 正常首页](https://www.alphaxiv.org/)，标题 Explore / Follow the latest research。页面没有足以核验的热门排序名称、筛选条件和时间窗口。既有 Most Liked / 7 Days 入口受验证限制，本轮没有绕过或重试受限入口。
- EAT 的单论文页显示 `#1 on Trending`；这一标记不能证明首页就是同一排序，也不能推出其余九名。完整榜单排序与新鲜度仍未核实。
- 因而下文编号是**报告阅读顺序，不是热榜名次**。EAT 来自实际首页；HRP 与 CTXAgent 是独立检索后核读原文的榜外补充。它们均不是10月29日首发，未发现可确认的新 arXiv 修订。
- 三篇均读了原论文方法/实验和公开代码关键模块；没有执行未知代码、安装依赖、模型调用或独立复现。没有把 alphaXiv 的 AI overview 当论文证据。具体未读范围见各项。
- AutoVend 的 arXiv HTML 首次访问返回404，未据摘要编写深评；昨天 Work Agents 的原文缺口也没有因此被消除。

## 可见页面记录（不是榜单）

首页前部实际出现 Evolving Agent Teams、ThinkWorld、Learning Force-Reactive Humanoid Loco-Manipulation，中间穿插关注作者和会议内容；后面也出现 Work Agents、EBench、PhysLadder。布局混合内容本身不支持把前十张论文卡强行解释为热门前十。单页 EAT 当时显示30票/570浏览，首页卡片显示31/570，不能把这两个读数的差当真实增长。[首页](https://www.alphaxiv.org/) · [EAT 单页](https://www.alphaxiv.org/abs/2610.36848)

## 补充 1：Evolving Agent Teams（EAT）

### 1. 基本信息
- 作者：Shiyi Cao、Ziming Mao、Dacheng Li、Joseph E. Gonzalez、Ion Stoica。
- [arXiv 原文](https://arxiv.org/abs/2610.36848)；[alphaXiv 页面](https://www.alphaxiv.org/abs/2610.36848)。v1 提交：2026-10-27 08:46:21 UTC / 北京时间 16:46:21。领域：Agent、coding agent、GPU kernel optimization。
- 已读正文 Introduction、Related Work、Method、Experiments、Conclusion，以及表 1–2、图 1/3/6 的文字说明；未逐像素检查曲线，也未独立运行实验。下列是有限范围评审，不是完整复现。

### 2. 解决的问题
固定角色团队可能一直优化同一条错误路线。EAT 把“如何组织搜索”也变成可调整对象，而不只迭代候选程序。

### 3. 核心方法
论文流程：任务与正确性约束 → supervisor 诊断停滞 → 改角色/协作/知识管理 → coding agents 执行 → 反馈与持久文件 → 下一团队；不涉及重新训练模型。[方法 §3](https://arxiv.org/html/2610.36848v1#S3)

**实际代码核验**：固定到 [8f04f0181b791493bbf71bf7c3c0b943fa1f5d76](https://github.com/caoshiyi/EAT/tree/8f04f0181b791493bbf71bf7c3c0b943fa1f5d76)。读了完整目录树、README、`SUPERVISOR.md`、`parse_team_config.py` 和 `launch_team.sh`。
- [parse_team_config.py](https://github.com/caoshiyi/EAT/blob/8f04f0181b791493bbf71bf7c3c0b943fa1f5d76/agent_team/parse_team_config.py) 将 supervisor 的 Markdown TEAM_CONFIG 拆成角色提示、可选模型/超时与阶段。解析以角色结构定位，避免角色正文里的标题误作全局 Workflow；缺角色时回退 optimizer，超过队伍上限截断，未排程角色追加末阶段。
- [launch_team.sh](https://github.com/caoshiyi/EAT/blob/8f04f0181b791493bbf71bf7c3c0b943fa1f5d76/agent_team/launch_team.sh) 同阶段并发、阶段间等待；角色模型须在允许集合，结束后由 harness 另跑 official eval，而不是直接信任 agent 自报分数；最后汇总成本与产物。
- 已读实现主要是 Bash/Python 编排并依赖 Claude Code CLI；目录树没有通用 package.json/pyproject.toml 依赖锁文件。未审查 `launch_stateless.sh`、clean-room 实现、独立 kernels 仓库和全量轨迹，不能称整套已审计。

### 4. 最大亮点
有价值的是把团队重构与可追踪实验产物结合。代码中的独立评测、阶段化协作比“多开几个 agent”更具体。研究判断：这值得借鉴，但 supervisor 的归因也可能错误，需用受控消融而非成功故事检验。

### 5. 实验能否支持结论
表 2 的同模型、800 美元推理预算、H100/47 workloads 对比：EAT 两次为 0.721×/0.685×，K-Search 为 0.602×/0.598×；都仍慢于该生产基线。正文另述扩预算结果，不应混成同预算成绩。主设置 best-of-two、若干扩展仅一次。§4.1 写固定团队 Opus 4.7、EAT 4.6，却在 §4.5 称同模型，这一不一致使纯组织效应解释需谨慎。[实验 §4 与局限 §5](https://arxiv.org/html/2610.36848v1#S4)

**证明边界**：作者报告支持特定搜索任务上的收益；没有证明任意 coding 项目、多次运行的稳定期望收益或实际采购成本优势。本报告没有独立复现。

### 6. 现在为何热门
11:46 左右北京时间读取的单论文页显示 `#1 on Trending`，但没有可核的完整榜单/时间窗；这是单页观察，不是本报告重建了当天 Top10。项目最新已读 commit 在北京时间 10 月 29 日 06:46:49（原 UTC 10 月 28 日 22:46:49）更新 README/曲线中模型尺寸表述，仅能确认维护活动，不证明传播原因。目前只能确认该页面的热度标记，尚无足够公开证据解释传播原因；未读取可归因的 X/HN/Reddit 讨论。[页面](https://www.alphaxiv.org/abs/2610.36848) · [commit](https://github.com/caoshiyi/EAT/commit/8f04f0181b791493bbf71bf7c3c0b943fa1f5d76)

### 7. 工程价值
优先借鉴 `parse_team_config.py` 的结构校验和 `launch_team.sh` 的独立评测/成本产物，而不是直接安装运行。该启动脚本使用跳过权限提示的 CLI 参数，角色超时强制执行默认未开启；复用前必须自行补齐隔离、预算、工具权限和可靠终止边界。GPU kernel 重现还需要相应硬件、评测环境和模型预算，不能以普通全栈应用门槛估计。对工作流自动化而言，先做“固定验收 + 有依据的角色调整”小实验比照搬长程自主执行更稳妥。


## 补充 2：Your Policy Is Secretly a Harness: The Decision Geometry of Agent Interfaces

> 本项为独立原文研究，不占用、也不冒充 alphaXiv 热榜位置。阅读截止：北京时间 2026-10-29 11:49（UTC 03:49）。未执行代码或独立复现。

### 1. 基本信息

- 作者：Jian Mu、Ruibo Shen、Yao Shu；领域：Agent、Evaluation、RL、AI Systems。
- [arXiv 2610.37255v1](https://arxiv.org/abs/2610.37255)：初版 2026-10-27 13:52:25 UTC，即北京时间 21:52:25；当前页面未显示后续修订。不是10月29日首发。
- [论文 HTML](https://arxiv.org/html/2610.37255v1)；[alphaXiv 对应链接](https://www.alphaxiv.org/abs/2610.37255)仅提供定位，本轮未读取、未确认热度。
- [作者代码 HRP](https://github.com/2020-qqtcg/HRP)，本轮代码固定至 `c91d859c21f38f10e358091265eea6e571e23e47`。

### 2. 解决的问题

更换 Agent 的工具、提示或控制循环，收益变化究竟来自接口能力还是模型不适应？论文把二者分开，不把冻结模型的一次框架比较当成框架能力上限比较。[正文§3–5](https://arxiv.org/html/2610.37255v1)

### 3. 核心方法

在 KL 正则控制设定中，返回值拆成 `J=C−M`：接口可达上限减去占用分布加权的策略失配。工程流程是“保存决策状态→重复采样目标/teacher→对齐语义操作→估计失配及返回代理”；真实 coding 场景的 teacher 不是最优策略真值。[§3、§6、附录F.7](https://arxiv.org/html/2610.37255v1)

### 4. 最大亮点

价值主要是可检验的归因框架，以及把接口重编码与语义能力变化分开控制的实验设计；不是证明模型权重里存有字面上的 harness 程序。[§4–6](https://arxiv.org/html/2610.37255v1)

### 5. 实验能否支持结论

- **支持局部敏感性：**表1/F.2，576个 MiniWoB 测试任务上，同一 Qwen3.5-2B 仅反转观察字段，成功率从85.0%降至19.2%；语义操作与任务信息不变。
- **尚不能证明普遍框架优劣：**coding 研究只有39任务、5种 harness，各3次运行；表2的±是运行间样本标准差。失配探针仅3任务，合并为13类操作，丢失参数细节；部分轨迹缺完整探针。teacher-relative 分数不等于精确最优性差距。
- MiniWoB 的 task bootstrap 不代表跨训练随机种子稳定性。本报告未复现。

来源：[表1、表2、附录F.2/F.7](https://arxiv.org/html/2610.37255v1)。

### 6. 现在为何热门

未核实热榜、X传播或独立讨论，不能确认“热门”。能够确认的时间线仅是：[代码初次提交](https://github.com/2020-qqtcg/HRP/commit/1a21e56a4028fe1cf3605d7028ec5cd5b8ed4c56)为2026-10-27 16:27:17 UTC（北京时间10月28日00:27:17）；[最新提交](https://github.com/2020-qqtcg/HRP/commit/c91d859c21f38f10e358091265eea6e571e23e47)为10月28日04:56:47 UTC（北京时间12:56:47），提交说明只涉及 README 的 arXiv 徽章，不是新方法发布。没有足够公开证据解释传播原因。

### 7. 工程价值与实际代码检查

**我的工程判断：**值得先借鉴“决策快照＋语义映射＋缺失信息显式保留”，而不是直接把论文分数部署成框架推荐器。RAG/coding agent/MCP 工具升级可以增加保持语义不变的字段顺序、工具编码回归测试；这是从研究得到的测试建议，不是已经验证适用于用户项目的收益。

已读固定 commit 的实现，而非只读 README：

- [`src/__main__.py`](https://github.com/2020-qqtcg/HRP/blob/c91d859c21f38f10e358091265eea6e571e23e47/src/__main__.py)：CLI 导入 `module:callable` 实验工厂，验证 `Experiment`，调用 `run_experiment` 输出 JSON。只是实验入口，不是现成线上 Agent 服务。
- [`src/hrp/models.py`](https://github.com/2020-qqtcg/HRP/blob/c91d859c21f38f10e358091265eea6e571e23e47/src/hrp/models.py)：`DecisionStep` 保存动作前状态、有限语义动作及无损 `concrete_action`；`HarnessAdapter` 分离 rollout 与同状态 action sampling；`Trajectory.truncated` 和结果中的尾部占用质量使超预算截断不被静默丢弃。移植到自有产品最难的部分是完整重建状态与验证语义映射，不是计算一个 KL。
- [`src/hrp/core.py`](https://github.com/2020-qqtcg/HRP/blob/c91d859c21f38f10e358091265eea6e571e23e47/src/hrp/core.py)：`smoothed_probabilities` 在已登记动作集合上做加性平滑；`quotient_energy` 对 `tau*log(p)` 去均值；`_combine_state_probe` 保存 teacher/target 计数、概率、残差与 reverse KL。`evaluate_candidate` 汇总占用权重、teacher 返回代理和 energy proxy，实际排序分数是二者之差。这里的选择不是按 teacher-return 置信下界排序，不能把输出误读成保守性能保证。
- [`src/hrp/native_measurement.py`](https://github.com/2020-qqtcg/HRP/blob/c91d859c21f38f10e358091265eea6e571e23e47/src/hrp/native_measurement.py)：开放式工具调用诊断保留完整参数与调用顺序，用 JSON Schema 检查格式；发现集与估计集分离，报告覆盖率、未解析质量和有支撑的动作对。跨工具等价需要同状态快照、反馈、退出状态、副作用及契约证据，不能仅凭相同文件 diff 合并。其 `predicted_success`、`harness_rank`、`full_space_hrp_energy` 明确留空。这一“拒绝过度推断”的接口设计比直接复用一个排名更值得学。
- [`pyproject.toml`](https://github.com/2020-qqtcg/HRP/blob/c91d859c21f38f10e358091265eea6e571e23e47/pyproject.toml)：Python≥3.12；依赖 Harbor、LangChain、HTTPX、tree-sitter-bash、jsonschema 等；DeepAgents 与 mini-SWE 使用仓库内 editable 路径。仓库有锁文件，但本轮未逐项审计锁定依赖、vendored 框架或许可链。

**资源与可用性：**[README](https://github.com/2020-qqtcg/HRP/blob/c91d859c21f38f10e358091265eea6e571e23e47/README.md)说明 coding 实验涉及 Docker、Linux、NVIDIA GPU 与 vLLM，部分 harness 需要 Node24/Corepack；因此不是无资源成本的即插即用评估。代码公开已确认；可安装、可复现实验未确认。本轮没有运行未知代码、安装依赖或调用模型。

### 阅读证据与边界

- 原文实际读取：Abstract、Introduction、§3–6、表1/2、附录F.2/F.3/F.6/F.7/F.8及其中表格；未逐页核查所有数学证明，未做PDF图像视觉复核，图示结论不作为独立证据。
- 仓库实际读取：主页 README、目录树、依赖定义、入口、完整 `models.py`/`native_measurement.py`，以及 `core.py` 中采样/平滑、能量残差、候选评估、状态合并、选择函数。未声称全仓审计。
- GitHub 网页目录一次返回 Cache miss；随后正常只读 GitHub 连接器成功读取目录与文件，无访问控制绕过。
- 适合优先读：§4/F.2 的重编码实验、§6/F.7 的 teacher 代理边界、`native_measurement.py` 的证据分层。

## 补充 3：CTXAgent — Self-Controlled Context Management of LLM Agents

### 1. 基本信息与实际覆盖
- 作者：Matthias Busch、Marius Tacke、Roland C. Aydin、Christian Feiler、Christian J. Cyron。
- [arXiv](https://arxiv.org/abs/2610.34425) / [v1 全文](https://arxiv.org/html/2610.34425v1) / [alphaXiv 地址（本轮未读取）](https://www.alphaxiv.org/abs/2610.34425)。领域：Agent、Context Engineering、Evaluation、AI Systems。
- v1 提交：2026-10-25 16:30:56 UTC，即北京时间 2026-10-26 00:30:56；不能把 10 月 28 日搜索线索日期当发布日期。当前原文仅见 v1。
- 本轮核验时间：北京时间 2026-10-29 11:49（UTC 03:49）。读取 Abstract、Introduction、Related Work、Method、Results、Discussion、Conclusion；读取 Table 1–2、图 1–7 的文字说明与结果段，**未进行图像视觉审查、未独立复现**。不属于已核实热榜 Top10。

### 2. 解决的问题
固定 token 阈值不知道任务何时结束；缩短上下文也可能破坏缓存。本文研究把删减决策交给模型的收益与失败边界，而非证明上下文越短越好。[原文 §3–5](https://arxiv.org/html/2610.34425v1)

### 3. 核心方法与真实代码
论文比较模型自选压缩与无管理、不同 harness。传统：历史累积→阈值触发；本方案：模型判定→摘要或工具结果整理→后续请求。以下细节由**实际读取的公开代码**确认，不冒充论文实验版本。

公开 main 在本轮解析为 [`77ec7a9e9127e3258b035af32dc7f13730979902`](https://github.com/MatthiasHBusch/CTXAgent/commit/77ec7a9e9127e3258b035af32dc7f13730979902)，提交时间 2026-10-25 16:00:34 UTC（北京时间 10-26 00:00:34）。论文 Table 2 使用短 SHA `2a407b9`，但连接器读取该 SHA 返回 **422 / No commit found**。故尚不能确认公开快照与实验代码完全一致。

- [`manual.py`](https://github.com/MatthiasHBusch/CTXAgent/blob/77ec7a9e9127e3258b035af32dc7f13730979902/ctxagent/compaction/manual.py)：`compact()` 接收模型写好的 summary、keep_from、keep_ids。切点不越过当前运行的工具批次，保留指定段所在整组；摘要至少 200 字符，且必须实际减少 token。被替换段先调用 `archive_segments`，再插入摘要；索引最多列出 60 条归档工具结果。`dry_run` 仅返回影响估计，不修改会话。
- [`curate.py`](https://github.com/MatthiasHBusch/CTXAgent/blob/77ec7a9e9127e3258b035af32dc7f13730979902/ctxagent/compaction/curate.py)：候选仅为非冻结、非当前批次的工具结果。指定项先写 blob，再换成模型 note 与 recall 句柄；未指定项默认保持原文。`rest='auto'` 是额外分支，不能把默认行为说成自动删除全部旧输出。提交 review 后冻结已审区间、重置计数。
- [`engine.py`](https://github.com/MatthiasHBusch/CTXAgent/blob/77ec7a9e9127e3258b035af32dc7f13730979902/ctxagent/compaction/engine.py)：逐级执行去重、mask/offload、压力下摘要、深压缩；agent 策略下软触发先加提示，逾期或高压力才走自动后备路径。`_rewrite_verdict()` 比较预计节省与失效后缀成本，不划算时恢复原状态。深摘要过长会在本地裁剪；没有净缩减则保留原上下文。
- [`pyproject.toml`](https://github.com/MatthiasHBusch/CTXAgent/blob/77ec7a9e9127e3258b035af32dc7f13730979902/pyproject.toml)：Python ≥3.11；FastAPI/Uvicorn、httpx、Pydantic、tiktoken 等；CLI 指向 `ctxagent.launch:main`。MCP 是可选依赖，不能据此声称已深读 MCP 实现。未运行安装、测试或模型调用。

### 4. 最大亮点
1. **可撤回的上下文删减**：代码不是销毁信息，而是将原文转入归档、保留句柄；这是值得借鉴的工程抽象，不等于模型一定会主动正确召回。
2. **协议完整性**：保护工具调用—结果分组，避免压缩产生孤立工具输出；仅靠“摘要质量”无法解决这类 API 合法性问题。
3. **缓存经济性可见**：同时报告 token 节省与 cache rewrite 范围。注意 manual/curate 的回本估计含硬编码 `1.15`、`0.1` 比例，engine 另有可配置 cost ratio；它们不是供应商当前报价或通用收益保证。

### 5. 实验支持什么、不支持什么
**作者报告**：七模型、四类会话；混合/困难组各三 seed，最长 212 轮。Opus 对 Claude Code 显式 200k 配置混合任务成本低 34%；Sol 对 Codex 同配置却高 16%，长会话为 $26.29 对 $12.14。它支持“收益依模型与 harness 而异”，不支持统一替换建议。[Table 1–2、§4.2、§5.3](https://arxiv.org/html/2610.34425v1)

**未证明**：记忆探针接近满分，不能据此排列长期记忆能力；运行数少、跨厂商比较混杂模型与 harness、价格依单一快照。没有独立复现、真实用户全工作流或安全保证。

公开 [`bench/results/README.md`](https://github.com/MatthiasHBusch/CTXAgent/blob/77ec7a9e9127e3258b035af32dc7f13730979902/bench/results/README.md) 确认结果按 session 存 JSONL，且同 tag 后行覆盖前行；本轮读到索引，**未逐行重算结果**。复核时需先按 tag 去重，不能把重复行误当独立样本。

### 6. 现在为何热门
alphaXiv 当前榜单、讨论及传播链未核实；不能断言热门或突然走红。作者仓库普通页面本轮显示 0 stars，单次值不构成增长或传播证据。仅能确认论文与公开代码可读取，以及实验 SHA 尚无法解析。[作者仓库](https://github.com/MatthiasHBusch/CTXAgent)

### 7. 工程价值
优先读 `manual.py`、`curate.py` 的边界和归档操作，再审 `engine.py` 的冻结与回滚。对 coding agent、长工作流适合借鉴“保留可召回原文＋完整工具分组＋缓存成本观测”，不建议只接一个摘要工具便默认省钱。

**本报告推断／可选验证方案**：在隔离的小型自有任务集上，比较固定阈值与模型自选策略，分别记录成功率、摘要输出量、缓存读写、请求数及实际账单；增加跨任务依赖与原文召回失败用例。应用侧依赖、持久化与协议边界使集成复杂度中等以上；全基准还需多模型预算与容器环境，本轮不估造硬件成本。先向作者核清实验 SHA，再决定是否完整复现。

### 留存边界
- 已核读代码固定为公开 SHA `77ec7a9e9127e3258b035af32dc7f13730979902`；论文实验 SHA 未核通，不合并二者身份。
- 未读取完整代理入口、全部 tests、原始 JSONL、实际图像、alphaXiv 讨论或 X 传播；不声称全面源码审计或实验复现。


## A. 今天最值得深入读的三篇（仅在实际研究样本中选择）

1. **CTXAgent**：先看 `manual.py` / `curate.py` 的工具分组、归档与缓存代价，再读论文 §4–5。对长程 coding agent 最容易转化成有边界的小实验；先解决实验 SHA 不可解析问题。
2. **HRP**：先看 §4/F.2 的等价重编码实验，以及 `native_measurement.py` 为什么拒绝输出全局排名。价值是让工具接口迁移和 Agent 评测少犯归因错误，不是买一个“最佳框架”结论。
3. **EAT**：先看 §3 的组织演化和表2，再读配置解析/阶段启动代码。对已有稳定评测的程序优化任务值得借鉴；没有固定验收和预算边界，不应先上长程自主团队。

以上是工程阅读建议，不是经核热榜前三，也不是已实施改造。

## B. 今天样本支持的三个研究主题

- **Agent 外层运行环境是实验变量**：HRP 区分接口与策略适配，EAT 改团队组织，CTXAgent 改上下文整理。三者共同提示模型权重不能独自解释终端成绩，但不能据此判断整个行业已转向。
- **保留中间证据优于只留最终分数**：HRP 保存决策快照与未解析质量，CTXAgent 归档被替换工具内容，EAT 将 official eval 与 agent 自述分离。可复用的是可核查记录结构，不是泛化的性能保证。
- **成本与比较口径决定结论**：EAT 同预算与扩预算必须分开；CTXAgent 缓存重写可能抵消 token 减少；HRP teacher 代理与精确上限不同。今天仅有三篇选择性样本，不列第四、第五条虚构趋势。

## C. 与昨天相比

基线是已读取的 [2026-10-28 实际报告](https://github.com/DanielMax937/daily-research-reports/blob/daabfb07728643be093fd101e65bdd8b77fbb5c4/2026-10-28/ai-papers.md)，不是记忆中的榜单。

- **无法判断新入榜、连续热门或名次升降**：昨天与今天都没有完整经核热门排序，不能把首页位置改变写成排行变化。
- **持续可见，不等于持续升温**：昨天报告中的 Learning Force-Reactive、Work Agents、PhysLadder、EBench 今天仍在普通首页可见。没有本轮核实的新版本/原始讨论证据，故不重写其完整背景，不宣称它们降温或升温。
- **本报告新覆盖**：EAT、HRP、CTXAgent 三篇的原文与核心代码；这是研究覆盖新增，不是论文今天发布或确认新进热榜。
- **新的工程核验事项**：CTXAgent 论文实验 SHA 与公开可读 SHA 尚未对齐；EAT 固定团队模型描述存在不一致；HRP 开放动作诊断明确不承诺全局 harness 排名。下一轮只有原文修订、作者澄清、可核新实验/代码或完整榜单恢复，才更新这些结论。

## 证据清单与留存口径

|对象|版本/快照|实际核读|仍缺失|
|---|---|---|---|
|alphaXiv|10-29 11:46 BJT 普通首页、EAT单页|可见论文卡、单页Trending标记|完整热门Top10、排序时间窗、传播归因|
|EAT|arXiv v1；代码 `8f04f0181b791493bbf71bf7c3c0b943fa1f5d76`|正文§1–5、表1–2及图说明；目录/README/3个核心文件|逐图审查、全仓/轨迹/独立实验|
|HRP|arXiv v1；代码 `c91d859c21f38f10e358091265eea6e571e23e47`|正文与关键实验附录；入口/依赖/数据模型/诊断模块/核心函数|全部证明、完整依赖审计、独立复现|
|CTXAgent|arXiv v1；公开代码 `77ec7a9e9127e3258b035af32dc7f13730979902`|正文§1–6、表/图说明；压缩模块/依赖/结果索引|论文实验SHA `2a407b9`、逐图审查、原始JSONL重算|

所有数字均为作者或页面报告，不是本报告独立测量；直接来源位于对应段落。没有证据解释热度的项目不以机构声望、总Star或想象的社区反应补齐。全文归档只含公开研究内容。
