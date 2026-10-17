# GitHub Trending 源码深读｜2026-10-17

> 范围：Repositories · Daily / Today · All languages / Any · Any spoken language，按当天官方页面实际前十顺序。本文侧重源码能够支持的机制、工程用途与边界，榜单排名不是安全性或质量评级。

## 抓取口径、新鲜度与阅读边界

- 官方来源：[GitHub Trending Daily](https://github.com/trending?since=daily)
- 锁定快照：**2026-10-17 10:26:57 北京时间（02:26:57 UTC）**。直接公开 HTTP 请求成功（200），响应 Date 为 02:26:42 GMT，Cache-Control 为 max-age=0, private, must-revalidate。HTTP Date 是响应时间，不证明后台在该秒重算了榜单；官方页面未显示排名生成时间
- 已读取页面筛选条件、全部 13 张仓库卡片，只取原顺序前十。网页检索工具读取的另一份同日页面顺序相同、总 stars 略低；全文数字只用上述直接 HTTP 快照，避免混用。未用第三方转载、昨日名单或搜索结果补位
- Stars、stars today 和语言均来自同一张 Trending 卡片。stars today 的精确统计窗口未公开，不能等同于北京时间零点以来，也不能以两份快照总数相减替代
- 源码锚定各项目读取时的完整提交 SHA，时间略晚于榜单，不声称为原子快照。只读 README/docs、目录、依赖、入口与关键实现，并核近期提交、发行和公开问题；完整目录不等于逐文件审计，已读切面及失败路径在各节说明
- 访问覆盖：匿名 GitHub REST/raw 部分请求遇到限流或 403 后，核心资料改用已连接 GitHub 只读接口取得。CLI-Anything 的 Discussions 列表来自搜索缓存，单帖 #458 读取失败，故不主张完整讨论覆盖；其余讨论启用状态、抽查内容及缺失各节披露。关闭/未启用讨论不表示没有用户反馈
- 全程静态研究，没有运行研究仓库代码、安装依赖、做模型/性能/音质实测。维护者的效率、使用规模、压缩率等均属其宣称；开放 PR 不当作已合入，分支版本不自动等于发行包
- 快照校验：原始 HTML 612,147 bytes，SHA-256 `55a44881088eda74c0eac4b3f3499aa5958da9a130a5e7733fffcf8b035f0fa6`。仅用于识别本次样本，不代替 GitHub 官方历史榜单

## 今日官方前十

| 排名 | 仓库 | Stars | stars today | 页面语言 |
|---:|---|---:|---:|---|
| 1 | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | 40,651 | +1,552 | Python |
| 2 | [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | 51,557 | +1,158 | Python |
| 3 | [affaan-m/ECC](https://github.com/affaan-m/ECC) | 281,569 | +1,057 | JavaScript |
| 4 | [HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything) | 53,543 | +281 | Python |
| 5 | [mksglu/context-mode](https://github.com/mksglu/context-mode) | 30,258 | +449 | TypeScript |
| 6 | [ruvnet/ruflo](https://github.com/ruvnet/ruflo) | 75,660 | +672 | TypeScript |
| 7 | [android/skills](https://github.com/android/skills) | 8,100 | +36 | Kotlin |
| 8 | [obra/superpowers](https://github.com/obra/superpowers) | 300,710 | +973 | Shell |
| 9 | [cursor/plugins](https://github.com/cursor/plugins) | 11,988 | +278 | TypeScript |
| 10 | [debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio) | 71,334 | +2,301 | Python |

第 11–13 名 ai-job-search、LinkSwift、xerj 不纳入本文，也不替补排名变化的旧项目。

## 1. anthropics/claude-plugins-official

### ① 排名、元数据与版本锚点
官方第 **1**；[仓库](https://github.com/anthropics/claude-plugins-official)；**40,651 stars，+1,552 stars today，Python**。main 固定为 **ea10b213686c90bb1984b2016937310e05336cf3**，提交时间 **2026-10-16 02:40:21 UTC**，与昨日实际报告锚点相同。完整树 **817 条目、573 文件**。没有统一应用版本；releases 列表为空；本次深读的 [security-guidance manifest](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/.claude-plugin/plugin.json) 为 **2.0.14**。各插件及远端源码应分别看许可证，不能将根目录的许可证视为所有外部组件的授权。

### ② 它解决什么实际问题
这是 Claude Code 的插件分发目录，统一描述技能、命令、agents、hooks、LSP 和 MCP 配置，让团队免于手工拷贝多套提示与连接设置。对象是希望扩展编码工作流的使用者和插件维护者，而非训练模型的研究者；替代方案是自行维护项目配置或逐仓安装。它同时容纳提示资料、配置和真正可执行的脚本，不能因为叫“官方目录”就认为全部远端服务的实现和权限已由同一方控制。[README 的结构与信任提示](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/README.md)

### ③ 架构、入口与真实数据流
**分发入口。** [marketplace.json](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/.claude-plugin/marketplace.json)实际列出 **315 项**，其中 **53 项相对路径、262 项外部 source 对象**。外部对象可以携带 git 子目录、ref 和 SHA；这里的数量是条目统计，不是逐个外部仓库的功能审计。[校验工作流](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/.github/workflows/validate-plugins.yml)与 [SHA 更新工作流](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/.github/workflows/bump-plugin-shas.yml)负责目录治理，不构成 Claude Code 宿主运行时。

**本次换一个执行切面：security-guidance 的三层审查。** [hooks.json](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/hooks/hooks.json)把用户提示、Edit/Write 等工具完成、commit/push 完成和 Stop 分发给 Python hook；入口 [main 与事件分流](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/hooks/security_reminder_hook.py#L2512-L2689)从 stdin 读 JSON。编辑后的模式提醒是本地快速检查，Stop 做 diff 审查，commit/push 路径再使用可读相关文件的 agentic reviewer。PostToolUse 的反馈发生在原动作之后，不能把它描述为阻止已发生提交的事务性门禁。

1. **增量审查与并发去重。** [Stop 数据流](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/hooks/security_reminder_hook.py#L2139-L2468)先在锁内取得本轮 baseline、已触达路径、未跟踪文件及既有 findings 的快照，再做 Git/网络慢操作。文件集合来自 Git 状态，而 diff 内容优先相对本轮开始前的 baseline，尽量避免把用户原有未提交内容反复算成本轮改动；hash、历史 finding 和晚到的 commit 审查结果用于去重。审查失败会保留尚未审过的状态，不能把“没有可用 verdict”当成“没有安全问题”。
2. **生成候选后再反证。** [agentic reviewer](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/hooks/llm.py#L1482-L2018)先调查，再对候选做 self-refute；`in_diff` 与 `off_diff` 是证据定位标签，而非立即丢弃所有 diff 外的 sink。只有 1–2 个候选时还可触发第二轮寻找其他问题。[可复用 review API](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/hooks/review_api.py)把提示、结构化 schema、diff 定位和严重性过滤抽出来，便于其他 harness 复用。反证失败时保留候选并不等于候选已经证实，只是避免失败的过滤步骤静默抹掉警报。
3. **工具集合真正收窄。** [工具限制实现](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/hooks/llm.py#L1408-L1422)指出 `allowed_tools` 只是预批准列表，因此额外给内层 CLI 传 `tools=Read,Grep,Glob` 与 strict MCP 配置，并用空的 settings sources。相比单靠“只读审查”的提示，这确实减少 shell、编辑和 MCP 执行能力；仍不是对模型判断正确性的证明。

[状态持久化](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/hooks/session_state.py)在支持 fcntl 的系统上做独占锁，写临时文件后 replace；Windows 分支明确缺乏同样的锁并原地写入，只记录潜在覆盖指标。读取范围：根 README；marketplace 的结构与条目统计；两项工作流；插件 README、manifest、hook 配置；hook 主入口及 Stop 全段；llm 的工具限制、review 调用和候选/反证段；review_api 的 cap、schema、定位与过滤段；session_state 全文；gitutil 的敏感文件过滤段；敏感路径与费用记录测试。未通读整个 llm/gitutil，也未审计全部插件或调用的外部 action。

### ④ 技术亮点与边界
值得借鉴的是**审查状态、证据范围和模型判断分离**：短 hook 进程通过持久状态交接，网络慢操作不持锁；候选和最终反馈各有阶段，不把模型第一轮输出直接当事实。它还显式记录 token/缓存用量和估算费用，避免后台调用完全不可见。但 [隐私、费用与限制说明](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/README.md)说明 diff、相关源码和组织自定义规则会传到用户配置的模型端点；默认模型选择可能变化，目录更新也不能保证行为恒定。它是辅助审查，仍会漏报、误报，不能代替人工 review 或既有安全测试。

一个直接有关使用安全的未完成事项是 [PR #6721](https://github.com/anthropics/claude-plugins-official/pull/6721)：提议把 Claude 自身凭据文件排除出审查。读取时仍 **open**；[当前敏感文件名集合](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/security-guidance/hooks/gitutil.py#L870-L935)确实尚无该 PR 要补的两个精确文件名。只能说当前过滤名单仍有此缺口与对应提案，不能说所有环境都会泄露，也不能把提案写成已修复。已读测试覆盖多种 secret-shaped 文件与重命名，但本次没有执行测试。

### ⑤ 近期活动与热度：事实、推断分开
**事实：**今日榜单显示 +1,552；当前 main 与昨日相同，最近七条 main 提交都是目录 SHA 升级，最新为 [incident-io 指针更新](https://github.com/anthropics/claude-plugins-official/commit/ea10b213686c90bb1984b2016937310e05336cf3)，不是今天发布了新的 Claude Code 核心版本。最新公开活动含 Telegram 行为问题 [#6726](https://github.com/anthropics/claude-plugins-official/issues/6726) 和上述 security-guidance 开放修复提案；issue/PR 活动可以发生在 main 没变化的时候。

**推断：**集中分发、较多厂商接入和可组合工程工作流可能扩大受众，但这些只是产品吸引力分析。没有取得明确的传播链、发布公告或增长归因证据，**暂无足够公开证据解释今日热度**；尤其不能把昨日已存在的提交当成今天涨星的已证实原因。

### ⑥ 对你的工程价值
对 **AI/Agent/MCP**，可学的是只给 reviewer 必需工具、记录异步审查状态、把外部插件 SHA 当供应链版本边界。对 **RAG**，diff 定位与补读相关文件相当于任务驱动的证据检索，不是向量数据库。对 **React/Next/Node**，审查提示覆盖路由、HTML sink、IPC 和跨文件调用；对 **Python/Django**，同样能借鉴后台任务状态、ORM/反序列化审查流程，但效果应在自己的代码和误报成本上评估。最合适的复用单位是一个有边界的 hook/reviewer，而非全目录默认启用。

## 2. K-Dense-AI/scientific-agent-skills

### ① 排名、元数据与版本锚点
官方第 **2**；[仓库](https://github.com/K-Dense-AI/scientific-agent-skills)；**51,557 stars，+1,158 stars today，Python，MIT**。main **a1043ef544e3a100c28e70a736b6cf32554d0677**，最新提交为 **10 月 12 日 09:43:29 UTC** 更新安全扫描报告，与昨日锚点一致。完整树 **3,497 条目、2,780 文件**，实际有 **177 个 SKILL.md**。[plugin.json](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/plugin.json)和 [pyproject.toml](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/pyproject.toml)均为 **2.72.0**；最近正式 [v2.72.0 release](https://github.com/K-Dense-AI/scientific-agent-skills/releases/tag/v2.72.0)发布于 **10 月 1 日**，并非今日新版本。

### ② 它解决什么实际问题
它把科研库、数据源、分析流程与成果校验写成 agent 能按需加载的技能包，减少研究人员反复寻找 API 文档、示例和依赖边界的工作。替代方案是临时查官方文档、自己维护实验笔记与脚本，或者使用较完整但更固定的工作流平台。177 项并非 177 个重新实现的科学计算引擎；许多技能负责指导和编排，真正计算仍由外部包、服务或设备完成。[README](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/README.md)也将各技能版本要求、验证范围与临床决策限制分别描述。

### ③ 架构、入口与真实数据流
**包层。** `plugin.json + skills/` 是 Agent Plugins 形式；每技能由 `SKILL.md` 加可选 references、scripts、templates 组成，测试按技能分目录。根 pyproject 的 Python ≥3.13 是仓库工具环境，不能误写成所有科学依赖的共同兼容版本。[按技能依赖清单](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/tests/skill-requirements.toml)用隔离环境处理冲突；[CI 工作流](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/.github/workflows/skill-tests.yml)默认跑结构合同与标准库-only 技能套件，明确不在每次 PR 上跑包含大型科学依赖的全部隔离测试。

**本次执行切面：Autoskill，从历史活动提出技能草稿。** [技能说明](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/SKILL.md)要求用户主动指定时间窗，依赖已安装的 Screenpipe；[CLI 入口](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/autoskill.py)把 `run/doctor/promote` 分到独立模块。实际流程不是仓库常驻观察用户，而是：

1. [fetch_window](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/fetch_window.py)分页 GET `/search`，检查 `data[]`、total 和 offset，按原始行数推进；只保留 OCR/UI/accessibility/input/audio 时间线类型，排除云结果和图像请求，并设一万页硬上限。[run](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/run.py)先对 text、窗口标题、应用名做 [本地正则脱敏](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/redact.py)，再进入分段。这是已存在 Screenpipe 数据的读取适配器，并不实现屏幕采集。
2. [cluster.py](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/cluster.py)按时间排序，以空闲间隔切 session、滤掉过短 session；每段记录应用首次出现的顺序，再以 `tuple(apps)` **精确分桶**，达到次数阈值才形成 cluster。后续只用应用、时长和示例窗口标题摘要，不把原始 OCR 文本送入合成提示。这也说明它并没有从操作序列学习语义 workflow；同样软件做不同研究会混在一起，相同任务但应用顺序不同也可能被分开。
3. [技能匹配](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/match_skills.py)读现有技能 frontmatter，只取 name/description；本地 embedder 对摘要与每条描述算 cosine，取前五。[合成与输出验证](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/synthesize.py)再让 LLM 选 reuse/compose/novel，并校验草稿名只能是受限 slug、内容非空。[产物分流](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/run.py)把新技能和组合 recipe 放到 proposal 目录，[promote](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/promote.py)才移动到技能目录并拒绝覆盖现有目标；“人工审阅后提升”仍需调用方遵守，不是 CLI 内置的审批系统。

已读范围：根 README 的定位/版本/安装/测试段，目录与 plugin/pyproject；Autoskill 说明的前置、隐私、架构和使用段及 API 契约；上述八个流程模块与 backends/config；测试文件用于查看 mock/输出契约；安全报告和 triage 的当前元数据段，paper-lookup 的 OpenAlex reference。未通读 177 项、未使用真实历史、未载入 embedding 权重、未测科学正确性。

### ④ 技术亮点与边界
优点是把**检测、候选检索、生成、发布**分成可检查阶段：dry-run 在聚类之后停止，甚至不做 embedding 与 LLM 合成；本地优先的 [backend 适配](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/scripts/backends.py)拒绝非 loopback 的明文 HTTP，模型结束原因不正常或结构化输出无效就拒绝生成草稿。迁移到其他 agent 平台时，这种阶段化比一个“自动学习”的长提示更可追踪。

边界也很具体：脱敏只覆盖已列正则，并不去掉所有未发表研究信息；远端 HTTPS 的“local”端点仍会把摘要送出机器，首次 embedding 安装也可能下载模型。`top_k_matches` 每轮遍历描述、现场编码，没有持久向量索引，适合小型技能库但不宜宣传为大型 RAG 检索基础设施。[API 契约文档](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/autoskill/references/api-contracts.md)明确本地测试使用虚构事件、mock transports 和 loopback fixture；不能由这些测试推导出真实 Screenpipe、云模型和科学匹配质量均已验证。

### ⑤ 近期活动与热度：事实、推断分开
**事实：**v2.72.0 在 10 月 1 日移除了另有许可证的四项 vendored 文档技能，使总数从 181 变为 177；今天 main 最新变动只是 10 月 12 日扫描报告。今天重新读取的 [扫描报告](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/docs/security-report.md)写的是 10 月 12 日、177 技能、scanner 2.2.2，而 [人工 triage 文档](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/docs/security-triage.md)的“当前报告”仍是 9 月 13 日、165 技能、scanner 2.1.0；[open issue #324](https://github.com/K-Dense-AI/scientific-agent-skills/issues/324)报告的版本漂移可从文档静态确认。自动扫描数字既不等于已确认漏洞数，也不是安全认证，旧 triage 不能替新扫描逐项背书。

[PR #325](https://github.com/K-Dense-AI/scientific-agent-skills/pull/325)提出修正 OpenAlex 限流和无 key 分页描述，读取时仍 open，说明 API 资料要随上游变化持续校验；不把提案当已合入功能。README 的教程、图解与完整技能目录是可见分发投入，可能让项目易于采用，但没有足够证据把它们与今日 +1,158 建立因果，**暂无足够公开证据解释今日热度**。

### ⑥ 对你的工程价值
对 **AI/Agent**，最值得抄的是技能目录、明确兼容版本、每技能依赖/测试和生成草稿暂存流程；对 **RAG**，Autoskill 给出“短摘要→描述检索→LLM 判别”的小型实现，可用于内部工具推荐，但要改善分桶特征和检索评测。对 **MCP**，它提供工具使用知识与适配脚本，本体不是通用 MCP 服务。对 **Python/Django**，可以将受控科学工作封装为独立 worker，保存输入/版本/输出证据；对 **React/Next/Node**，更适合作为运行结果与人工审阅 UI 的上游知识包，不能把生物/医疗流程直接变成未经验证的用户决策产品。

## 3. affaan-m/ECC

### ① 排名、基础版本与今天的源码锚点

官方今日第 **3**；[affaan-m/ECC](https://github.com/affaan-m/ECC)，**281,569 stars，+1,057 stars today**，主语言 JavaScript，MIT。当前 main 固定为 **76aaa77df6adc5b889e689007bf99b9a4f74af34**，提交时间 **2026-10-15 19:17 UTC**。本次重新取得[完整递归树](https://api.github.com/repos/affaan-m/ECC/git/trees/76aaa77df6adc5b889e689007bf99b9a4f74af34?recursive=1)：6,355 条目、4,621 个文件、未截断。**与昨日固定 SHA 完全相同**，今日排名从昨日第 10 上升不能解释为今天代码变多。

[根 package.json](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/package.json)仍是 ecc-universal **2.2.3**，Node ≥18；运行依赖为 @iarna/toml、AJV、js-yaml、sql.js。[最新 release v2.2.3](https://github.com/affaan-m/ECC/releases/tag/v2.2.3)发布时间为 **10 月 1 日 23:00 UTC**。release 文案里的 pi/core 为 123 skills，而当前 main 的[manifest](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/manifests/pi-core.json)与[生成 README](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/pi/core/README.md)已是 **132 skills、24 commands**：这两个数字描述不同版本切片，不能混用。

### ② 问题、使用者和替代方式

ECC 面向已经使用编码 Agent、但不想在每个任务里重写规划、测试、审查与交接要求的开发者。它把 skills、审查角色、规则、命令、hooks、多宿主适配和本地记忆组织成可选择安装的工程流程。替代方案是维护自己的 AGENTS.md／rules／skills，加宿主原生子代理与少量脚本。ECC 的优势是复用和跨宿主一致性，代价是安装面、运行权限与升级兼容性更复杂。[README 定位与安装路径](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/README.md#L130-L179)

源码必须分成两类理解：skills/、agents/、rules/ 中主要是供模型阅读的材料；scripts/、hooks/、宿主插件才是执行程序。安装一个 memory skill 不会自动把 ecc-memory-mcp 放到 PATH；“工程系统”也不表示存在操作系统级沙箱。[Unified Memory 的前提说明](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/unified-memory/SKILL.md#L15-L36)

### ③ 架构、实际入口与三条值得深读的数据流

**入口与目录。** npm bin 中 ecc → scripts/ecc.js、ecc-install → scripts/install-apply.js、ecc-memory-mcp → scripts/memory-mcp.mjs。[ecc.js](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/ecc.js#L211-L350)先解析命令，按固定映射启动相应 Node 子脚本，保持 cwd、输出和退出状态；安装、资料生成、记忆服务是不同执行路径。

1. **资料如何变成可分发、可审查的包。** [build-pi-core.js](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/build-pi-core.js#L56-L168)先核查每个磁盘 skill／command 是否被 manifest 分类，再按清单复制，验证 frontmatter 的 name／description 和名称唯一性，拒绝 symlink，跳过 Python 派生缓存。随后生成包描述和排除原因清单，并以文本规则检查 URL 主机、下载执行形式、疑似凭据和绝对用户目录。[安全扫描和 --check](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/build-pi-core.js#L256-L391)最终比较文件清单及字节；这让“新增资料必须经过明确策展”和“提交内容可重建”成为可检查的约束。它不是对任意脚本做语义安全证明，规则允许表与正则扫描存在覆盖边界
2. **同意 hooks 必须改变安装计划。** [hook-consent.js](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/lib/install/hook-consent.js#L12-L37)列出自动写源码、命令改写／进程控制、对外 LLM、MCP 活动、权限门禁与会话记录等能力；[withHookConsent/assertHookConsentReady](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/lib/install/hook-consent.js#L259-L323)在拒绝时剔除运行时操作，没有明确决定却仍将落地 hooks 时抛错。OpenCode 会自行发现插件，因此仅删配置注册不够：[禁用入口](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/lib/install/hook-consent.js#L90-L94)刻意生成不导入原模块的空实现，避免模块初始化副作用。这是权限选择落到实际安装产物的好例子
3. **跨宿主记忆不是向量数据库的别名。** [Memory Vault 设计](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/docs/design/ecc-memory-vault.md#L1-L70)以 Markdown 为事实存储，create-only，条目保持 unreviewed；[searchMemories](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/lib/memory-vault.js#L538-L665)做标题、标签、元数据与正文的词法加权，带扫描诊断。按 ID 读取在扫描截断或存在无效文件时返回 incomplete，而不是误报不存在／唯一。[MCP 适配](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/memory-mcp.mjs#L174-L355)使用启动时固定的 harness 身份和单独 user-scope 开关；caller 不能通过 tool 参数冒充其他 harness。harness 路由标签仍不等于个人身份认证，同一 OS 用户的恶意进程也不在其完整隔离范围

**本次已读证据范围。** 全树、package／LICENSE；README 的定位、安装、memory、平台和安全段；ecc.js 命令映射与派发；build-pi-core.js、hook-consent.js、pi/core README、[离线加载测试](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/ci/pi-core-load-test.js)、[构建回归测试](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/tests/scripts/build-pi-core.test.js)全文；memory 设计约束与威胁边界、vault 的读取／评分／搜索／按 ID 读取、MCP 的身份／校验／handler；OpenCode 插件的默认导出。未逐行审计 311 个 skills、全部 hooks、ECC2 或安装写盘层，也未安装、执行测试或运行仓库代码。活动证据读取了最近 10 个提交、5 个 releases、按更新时间排序的 12 条开放 issue／PR 条目，并完整读 #3537、#3614 及 Discussion #3463；未穷尽全部关闭问题和历史讨论。

### ④ 实现亮点与不能忽略的边界

最有价值的是把“内容可复现”“用户选择应落实到执行文件”“检索不完整要显式表达”分开实现。对 Agent 平台而言，这比只堆提示词更接近可靠的分发工程；但 hooks 仍有真实副作用，记忆中的陈述也仍需查原始来源。

**本次发现两个需要实际接入者注意的版本／契约问题：**

- 当前[pi/core README](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/pi/core/README.md#L15-L29)与[生成器](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/build-pi-core.js#L187-L201)仍展示 --extension pi/core；实际[CI 加载脚本](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/ci/pi-core-load-test.js#L5-L18)明确说明该参数只加载 extension 条目，skills+prompts 包应使用 --skill 和 --prompt-template，执行参数也如此。测试会请求 get_commands 并核对命令集合，而不是只看启动退出零。可确认的是文档与真实测试路径不一致，本次没有启动 Pi 重现
- [OpenCode issue #3537](https://github.com/affaan-m/ECC/issues/3537)报告 V2 loader 拒绝旧函数式插件；当前源码默认导出仍是函数。10 月 16 日的[PR #3614](https://github.com/affaan-m/ECC/pull/3614)进一步指出“拒绝 hooks”生成的空函数同样不符合 V2 schema，并拟改为含 id、setup 的对象；读取时 open、未合并。**源码确认了当前导出形态，V2 报错与测试数字来自报告者，未在本次独立运行验证**。不能把“关掉 hooks”直接当作此兼容问题已解决

### ⑤ 今日热度：可证事实、时间关联与推断

**事实：** 最新[main 提交](https://github.com/affaan-m/ECC/commit/76aaa77df6adc5b889e689007bf99b9a4f74af34)仍是 10 月 15 日 PR 提交频率防护的合并；v2.2.3 为 10 月 1 日命名与发布可靠性更新，都不是今日新增 Agent 算法。今天能核到的社区增量包括上述 OpenCode PR，以及[Discussion #3463](https://github.com/affaan-m/ECC/discussions/3463)在 10 月 16 日对多 Agent 共用主机、测试进程负载与条件等待的实践交流；参与者明确是使用者而非维护者，其机器测量不是 ECC 官方性能基准。

**推断：** 多宿主复用、现成工程流程和可检查的低运行时 profile，可能让它持续吸引 Agent 开发者；但源码、release 与讨论只能证明活动，不能证明今日新增 stars 的来源。**暂无足够公开证据解释今日热度**，不把榜单跃升归因于某个未核实传播事件。

### ⑥ 对你的工程栈的价值

对 **AI Agents／MCP**，优先看 hook 的授权计划与 memory 的“上下文不自动成为执行权”边界。对 **RAG**，值得借鉴的是来源记录、扫描完整性、状态与可见范围，而非把简单词法检索误称语义检索。**Node／TypeScript** 能直接阅读这些 CLI 与 JSON-RPC 模块；**Python／Django** 可实现同样的 memory contract 和后台受控工具层。**React／Next.js** 更适合做组件选择、安装差异、记忆来源及 incomplete 状态的审查界面，ECC 并不是可直接部署的 Next/Django 应用模板。

## 4. HKUDS/CLI-Anything

### ① 排名、版本和源码锚点

官方第 **4**；[HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything)；**53,543 stars，+281 stars today，Python**。今天重新锁定 main 为 **34f519533bc175d2fe287ab8316b0dd99bb9cc43**，最后提交时间是 **2026-09-22 02:01:28 UTC**，并非今天。完整递归树 **2,582 条、1,872 个文件，未截断**。项目根许可证为 Apache-2.0；不过 [CLI-Hub setup.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-hub/setup.py)仍写 MIT，组件元数据与根许可证有不一致，不能只抄包分类器当法律结论。Hub 源码版本 **0.4.1**，而最新仓库 [release v0.4.0](https://github.com/HKUDS/CLI-Anything/releases/tag/v0.4.0)发布于 **6 月 25 日**；这两个版本口径要分开。昨日报告前十没有它，**没有昨日固定 SHA 基线，不能据此说它昨日未上全榜或今天刚创建**。

### ② 解决什么问题，适合谁，替代什么

它尝试把有底层 API、脚本接口或工程文件格式的软件，变成 agent 能发现、检查、组合调用的 CLI。面向两类人：已有任务要找可用工具的 agent 使用者，以及愿意读目标软件源码、补命令包装和测试的开发者。它减少鼠标操作、手工拼接文件以及为每个应用重新编写工具 schema 的重复劳动；但并非一个下载后能自动理解任何闭源 GUI 的万能驱动。

[README](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/README.md)明确有两条入口：现成 CLI 由 Hub 发现和安装；新的 CLI 则由宿主编码 agent 执行生成方法。后者的“生成器”主要是 [commands/cli-anything.md](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-anything-plugin/commands/cli-anything.md)和 [HARNESS.md](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-anything-plugin/HARNESS.md)提供的方法与模板，要求输入目标源码路径或仓库 URL；不是把软件名称送给一个确定性编译器就能产出正确适配。

### ③ 真实架构、入口、数据流及三个关键机制

**目录与依赖。** [固定树](https://github.com/HKUDS/CLI-Anything/tree/34f519533bc175d2fe287ab8316b0dd99bb9cc43/)包含独立软件的 `agent-harness/`、Claude/Codex/Cursor 等宿主适配、`skills/`、两个 CLI registry、`cli-hub/` 和 matrix 内容。它是多包集合，不是一个统一 Python 服务。Hub 要求 Python ≥3.10，核心依赖 Click、requests，实际可执行入口为 `cli-hub=cli_hub.cli:main`；GIMP harness 独立打包为 1.0.0，以 Click、prompt-toolkit 为基础，Pillow 是额外依赖，入口为 `cli-anything-gimp=cli_anything.gimp.gimp_cli:main`。[GIMP 包清单](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/gimp/agent-harness/setup.py)

**机制一：把“能力需求”映射到可安装工具，但保留就绪层次。** [registry.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-hub/cli_hub/registry.py)分别取 harness/public registry，缓存一小时，网络失败可回旧缓存；合并时先复制字典再加 `_source`，避免污染缓存对象。[matrix.py 的 preflight](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-hub/cli_hub/matrix.py#L150-L290)检查 provider 声明的环境变量、二进制及 Python package，并区分 available、missing、agent-installable。重要细节是 `covered` 把“已经可用”和“可由 agent 安装的候选”都计入；它是能力规划结果，**不是端到端执行成功证明**，也不验证 API key 真有效、引擎版本真正兼容或远端服务健康。

[installer.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-hub/cli_hub/installer.py#L406-L548)先计算按 capability/recipe/only 裁剪的安装计划，安装时逐项记录 installed/skipped/failed，`--resume` 只重试上一轮失败项，最后按已装状态生成 matrix skill。这个“计划、执行、结果账本”分层适合 agent 恢复工作；但已安装判断依赖本地登记，不应理解成每次都重新验证所有二进制。

**机制二：状态命令和实际软件后端分层。** GIMP 的数据流是：Click 参数 → JSON 项目/Session → 图层、滤镜等 core 操作 → export → GIMP Script-Fu 子进程或 Pillow 路径 → 文件与 JSON 结果。[CLI 入口](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/gimp/agent-harness/cli_anything/gimp/gimp_cli.py#L117-L154)支持 one-shot、REPL、`--json` 和项目路径；one-shot 回调在状态变更且已有保存路径时自动保存，`--dry-run` 只跳过这一步自动保存，**不能把它当所有副作用的全局沙箱**。显式导出仍是单独的代码路径。

[Session](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/gimp/agent-harness/cli_anything/gimp/core/session.py)在修改前 deep-copy 项目作为 undo 快照，最多保留 50 项；save 实际只写项目对象，不把内存 undo 栈落盘。[gimp_backend.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/gimp/agent-harness/cli_anything/gimp/utils/gimp_backend.py#L367-L451)构造 Script-Fu，转义字符串、以 argv 启动真实 GIMP、检查输出文件并返回 `method:gimp-batch`。这是结构化控制面与应用引擎分离的可读样例。

**机制三：从真实命令定义生成 agent 文档。** [skill_generator.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-anything-plugin/skill_generator.py#L34-L79)用 Python AST 解析 Click decorator，支持位置参数/`name=` 中的字符串字面量，保留函数 docstring；[命令分组提取](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-anything-plugin/skill_generator.py#L248-L338)再把父子 group 和 command 映射到技能文档。这比正则截取括号稳健，也避免为了生成文档而导入并执行应用代码；边界是动态注册、非常规包装器和运行时计算名称不必然能被静态提取覆盖。

### ④ 实质亮点与不能忽略的边界

最值得学习的是**“查能力、查前置条件、按范围安装、保留执行状态、暴露机器可读结果”形成一条闭环**。项目还把生成工程文件和调用真实后端分开，适合 Blender、LibreOffice、GIS 等已有成熟引擎的工具化。但 README 的“通用”“可靠”等定位，不能自动推广成每个 harness 都有相同保障。

本次源码读到两处很适合作为审计教材的“规范与实现落差”：

- HARNESS 明确要求真实软件渲染，不允许用 Pillow 替代；但 [GIMP export.render](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/gimp/agent-harness/cli_anything/gimp/core/export.py#L54-L84)只在 GIMP 可用且项目没有 draw ops 时优先走它，而且捕获**任何异常**后都会回退 Pillow。拿到一张输出图，不等于验证了 GIMP 引擎语义；不同后端的滤镜、字体和混合效果需要分别比对
- `_locked_save_json` 的注释说 atomic，但实现是加 `fcntl` 锁后 truncate、json.dump、flush；没有临时文件替换，也会在无 fcntl 或锁失败时继续。它缓解部分协作写入问题，**不能据此宣称崩溃安全、跨平台强锁或事务级原子保存**；CLI 自动保存失败还只发 warning，需要调用者验证持久化结果

此外，Hub 的 [命令执行器](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-hub/cli_hub/installer.py#L67-L93)把 registry 当可信输入，遇管道等操作符使用 shell 执行。工具发现和安装因此也是供应链与权限边界，不应让未知 registry 命令以无限权限运行。项目有 MCP backend 示例，含义是某些 harness 可以**作为 MCP 客户端**包装已有服务器；不是所有 CLI 自动变成 MCP server。[MCP backend 文档](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-anything-plugin/guides/mcp-backend.md)

### ⑤ 近期变化、问题证据和今日热度

**已核事实：**最近 main 提交集中在 9 月 22 日 README 展示调整；此前 8 月 21 日有 Cursor 适配、Hub Windows UTF-8 和 Click AST 元数据提取修复。[今日固定提交](https://github.com/HKUDS/CLI-Anything/commit/34f519533bc175d2fe287ab8316b0dd99bb9cc43)因此不能当作今日功能发布。6 月的 v0.4.0 release 提到 CLI-Matrix 与大量新 harness，是长期产品背景。

今天真正新鲜的是兼容性反馈，而不是主干变化。[issue #565](https://github.com/HKUDS/CLI-Anything/issues/565)在 10 月 16 日报告 Obsidian 含 `#`/`?` 的文件名可能指向错误笔记；当前 [vault.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/obsidian/agent-harness/cli_anything/obsidian/core/vault.py)确实直接插入未经 percent-encode 的 path，[HTTP wrapper](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/obsidian/agent-harness/cli_anything/obsidian/utils/obsidian_backend.py)继续直接拼接 URL。**“缺少编码”的实现已静态确认；作者报告的错写结果本次未运行复现。**

[issue #568](https://github.com/HKUDS/CLI-Anything/issues/568)于 10 月 17 日 00:22 UTC 报告 AdGuard Home 配置端点 405；当前 [log.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/adguardhome/agent-harness/cli_anything/adguardhome/core/log.py)确实读取旧路径，并在写配置时固定发送 `anonymize_client_ip:False`；[stats.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/adguardhome/agent-harness/cli_anything/adguardhome/core/stats.py)也使用旧路径。[修复 PR #569](https://github.com/HKUDS/CLI-Anything/pull/569)读取时仍 open。以上提醒使用者先验证目标软件版本和副作用，不证明所有 harness 都坏了。

**热度推断：**让 agent 接入现有软件的定位、现成 registry 和多宿主技能具有传播吸引力，但本次没有找到足够直接传播证据，把这些活动与当天 +281 建立因果。**暂无足够公开证据解释今日热度。** Discussions 列表只读到少量条目，其中 #458 单帖抓取失败，不能将该入口当完整近期讨论覆盖。

### ⑥ 对 AI Agents、RAG、MCP 与 Web/Python 工程的价值

对 AI Agents，优先借鉴 schema 化能力发现、前置条件检查、失败项恢复，以及输出里的实际 backend/method 标记；别把所有软件都统一成一个过宽的 run-shell 工具。对 MCP，可以将精选 CLI 放在受限 worker 后面，显式区分读写、输入文件和输出目录。对 RAG，它可以连接 Obsidian、Zotero、ChromaDB 等已有软件，但这个仓库自身不是统一检索引擎；尤其笔记 path 编码问题说明连接器正确性同样决定检索及写回可靠性。

对 React/Next/Node，价值主要在服务后端或开发期 agent 工具，不能在浏览器中直接运行这些系统应用；对 Python/Django，Click → core → backend 的拆层可复用，长时间渲染放到独立队列 worker，给子进程设资源、时间和文件访问限制。若只取一个阅读入口，建议先看 registry/matrix 的就绪定义，再看 GIMP 的 fallback 和保存语义，比照着总测试数推断质量更有收获。

**已读范围与证据限度：**完整递归树；README 的定位、安装、新闻和实现列表；Hub setup/registry 全文、cli 命令入口和命令索引、installer 47–220/301–548、matrix 150–292；插件命令与 HARNESS 的流程/真实后端/测试约束；skill_generator AST 与分组提取；GIMP setup、CLI 1–158、Session 全文、export 1–105、backend 1–77/367–451，E2E 测试的 roundtrip/滤镜输出与方法断言索引；上述 Obsidian/AdGuard 模块及相关 issue 正文。获取文件不等于全量逐行审计，其他 harness 未审计；未安装或运行项目、测试、修复代码。

## 5. mksglu/context-mode

### ① 排名、基础版本与源码变化

官方今日第 **5**；[mksglu/context-mode](https://github.com/mksglu/context-mode)，**30,258 stars，+449 stars today**，TypeScript。main 固定 **5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6**，提交于 **2026-10-16 12:06 UTC**；[完整递归树](https://api.github.com/repos/mksglu/context-mode/git/trees/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6?recursive=1)714 条目、599 个文件，未截断。[package.json](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/package.json)为 **1.0.169**，Node ≥22.5，MCP SDK、better-sqlite3、Zod、Turndown／DOM 库为主要依赖，TypeScript/esbuild 输出 CLI 与 server bundle。

相对昨日 **40813fe886798bad07c69a43d2ae00a52b4b934d**，[compare](https://github.com/mksglu/context-mode/compare/40813fe886798bad07c69a43d2ae00a52b4b934d...5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6)严格只有 **1 个提交、1 个文件 stats.json**，变更是安装统计徽章。代码分析以今日 SHA 重新读取，但不能将下面已有机制写成今天新加。许可证是 [Elastic License 2.0](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/LICENSE)，不是 MIT；其文本对向第三方提供包含实质功能的 hosted／managed service 有限制，生产服务复用前需核对。

### ② 它解决什么问题，适合谁

面向经常读日志、网页、测试输出和大量代码的编码 Agent。核心不是把整段材料改写成更短摘要，而是**先在模型上下文之外处理、索引，再按问题取回片段**，并保存会话事件支持 compaction 后恢复。替代方式包括手工 grep／过滤、限制工具输出、自己搭本地 BM25 或向量 RAG。[README 问题与方案](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/README.md#L32-L58)

它比较适合单人开发环境的长工具输出治理；全量信息能被保存，不代表任意查询都能正确找回。宣传中的 98% 是特定演示输入与调用方式下的数字，不能直接当作真实任务费用或正确率的普遍保证。

### ③ 入口、架构和三个关键机制

**整体链路。** [CLI 的默认分派](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/cli.ts#L226-L260)进入 server；[server main](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts#L4851-L4896)清理过期存储、注册退出清理并连接 stdio MCP。src/executor.ts 执行，src/store.ts 索引和检索，src/session/ 保存会话事件，hooks/core 与 adapters 负责宿主接线；[平台矩阵](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/docs/platform-support.md#L1-L55)显示不同客户端的 hooks 能力不同，MCP 可连接不等于自动路由、恢复、输出改写都同样可用。

1. **执行与上下文回传分离。** [ctx_execute handler](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts#L1743-L1950)先做 deny-policy 检查，再交 [PolyglotExecutor](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/executor.ts#L282-L318)把代码写入临时文件，以项目 cwd 启动相应语言进程。正常输出超过 **5,000 bytes 且给出 intent** 时保存并返回匹配标题／预览；超过 **102,400 bytes** 即使没有 intent 也自动索引、只回导航。执行器另有 stdout+stderr **100 MiB** 硬上限，后台进程与退出清理单独处理。[阈值及导航实现](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts#L1958-L2035)、[进程与输出控制](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/executor.ts#L409-L535)
2. **本地双词法索引的融合。** [ContentStore schema](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/store.ts#L465-L503)保存 sources 与两套 FTS5：Porter/unicode61 和 trigram；BM25 对标题权重更高。当前 [searchWithFallback](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/store.ts#L1244-L1404)是“两路 OR 召回 → RRF（k=60）融合 → 标题／词距重排”，没有结果再做拼写纠正重试，**不是先 Porter、失败才 trigram，也不是 embedding RAG**。融合用 source+title 作为键，重排是在截取的候选集合上进行，召回上限与切块标题会影响结果。文件源搜索前可按 mtime/hash 更新，但删除文件保留缓存，用户需要理解来源新鲜度
3. **限流针对 Agent 身份，而不是共享 MCP 进程。** [FloodGuard](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/search/flood-guard.ts)以每个 agent-context key 保存计数窗；[server 接线](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts#L2444-L2484)从会话归属取 key，默认 60 秒内第 4 次起每 query 只返回 1 条，第 9 次起拒绝并引导批量调用。[结果上限](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts#L2649-L2674)正常也最多 2 条／query、总输出有 40 KiB 上限。没有可解析身份时回到共同的 __default__ 桶，不能声称任何宿主的并发子代理都绝不会互相挤占预算；计数 key 最多 4,096，超量淘汰最旧桶。独立[单元测试](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/tests/core/search-flood-guard.test.ts)覆盖十个不同 key 各两次调用，但不等于所有平台已完成身份接线实测

**阅读覆盖。** 本次读 package／LICENSE；README 的方案、tools、检索、隐私与安全部分及平台矩阵；CLI 分派、server 执行／索引／检索限流／网络抓取／启动段；executor 的运行 cwd、spawn、超时与硬上限；store 的 schema、RRF／重排／刷新；unified search、FloodGuard 与对应测试全文。未通读 4,991 行 server、全部 adapter 与 hooks，未运行仓库代码或复现 benchmark。活动证据读取了当前 head、昨日到今日的 compare 和最近 3 个 releases；issues／discussions 当前未启用，故没有可核的近期公开讨论流水。

### ④ 亮点与边界，尤其是 sandbox 的实际含义

它把“保留原材料”“给模型返回多少”“谁在调用”分层得比较清楚；本地 SQLite FTS5 也避免了为日志检索先搭 embedding 服务。对需要反复查询同一长输出的工作，保存加导航比反复重读更有结构。

但这里的 sandbox 是**本地子进程边界**。[工具声明](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts#L1647-L1658)明确具有写入、破坏性和开放网络属性；[执行器](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/executor.ts#L295-L307)所有语言实际在项目 cwd 工作，缺省不设独立服务器计时器。不能把临时目录、环境过滤或 file-read 工具的 project-boundary 检查当成任意代码的 OS 隔离；宿主级 sandbox、网络与凭据权限仍然重要。[README 的边界披露](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/README.md#L1559-L1575)

这次额外深读了[网络获取链](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts#L2838-L3057)：预检和子进程实际 DNS 连接检查配合，重定向逐跳校验，最多 5 次；危险 metadata／link-local 默认阻止，**localhost、RFC1918 默认允许**，CTX_FETCH_STRICT=1 才额外禁止私网。它不是默认“只能访问公网”的服务。另一个具体限制是 [safeText](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts#L3060-L3077)先查 Content-Length，再 await resp.text()，最后按字符串 length 检查 50 MiB 名义阈值：无可靠 Content-Length 时，后置检查无法阻止整个响应先进入内存，字符串长度也不是 UTF-8 字节数。此为静态源码边界，未做恶意响应实测。

共享 DB 的[project 过滤](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/search/unified.ts#L94-L118)依赖 SessionDB 能解析 project→session，旧 session_id='' 内容仍跨项目可见；相关异常会退回部分结果，因此不能把它直接用作多租户授权隔离。README 的“本地”定位也不应理解为执行工具不会联网，源码确实提供网络获取与外部命令能力。

### ⑤ 今日热度：事实与推断

**事实：** 今日 main 相对昨天只更新 stats.json，徽章是项目提供的统计口径，不是独立验证的活跃人数。[最新 v1.0.169](https://github.com/mksglu/context-mode/releases/tag/v1.0.169)仍发布于 **6 月 29 日 18:18 UTC**，聚焦上下文节省与 FinOps 归因；不是今日 release。今日[仓库元数据](https://api.github.com/repos/mksglu/context-mode)显示 has_issues=false、has_discussions=false，公开 issues 查询为空；不能把源码中的历史 issue 编号写成今天仍可核验的开放问题。

**推断：** 工具输出膨胀是实际 Agent 痛点，其索引化回取和多宿主适配可能支撑持续关注。**暂无足够公开证据解释今日热度**，不能以徽章更新、旧 release 或“98%”演示为今日星标增长建立因果。

### ⑥ 对你的工程栈的价值

对 **AI Agents／MCP**，可以直接学习“执行返回导航、后续检索正文”的工具契约和按 Agent 身份计量。对 **RAG**，FTS5+RRF 是无需 embedding 的可读基线，但中文词法召回、候选上限和缺失来源需要自己的评测。**Node／Next.js** 可借鉴后端索引与工具 API，**Python／Django** 可实现同样的存储／召回层；**React** 适合呈现来源时间、命中片段、缺失与截断。若改成多人托管产品，需重新解决授权、进程隔离、存储生命周期及 ELv2 条件，不能把单人本地设计直接搬上公网。

## 6. ruvnet/ruflo

### ① 排名、版本与固定源码

官方今日第 **6**；[ruvnet/ruflo](https://github.com/ruvnet/ruflo)，**75,660 stars，+672 stars today**，TypeScript，MIT。main 固定 **1882006a02487590c8c66a7eec8d7504f6af33c3**，提交于 **2026-10-14 16:21 UTC**；与昨日固定 SHA 相同。[完整递归树](https://api.github.com/repos/ruvnet/ruflo/git/trees/1882006a02487590c8c66a7eec8d7504f6af33c3?recursive=1)9,660 条目、7,837 个文件，未截断。

[根包](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/package.json)仍叫 claude-flow，版本 **3.56.10**，Node ≥20；[CLI 包](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/package.json)也是 3.56.10，cli-core 锁为 3.7.3、memory 为 3.0.5。[swarm 包](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/package.json)则是 3.0.2。多包版本不能拿根版本统一代替。AgentDB、原生 SQLite、RuVector 等有可选依赖面；文件存在不代表安装时全部能力都能用。

### ② 目标问题、人群与替代方案

它给已有编码 Agent 增加协调状态、工作流、记忆、工具发现与插件，面向需要跨任务、跨会话组织工程工作的开发者。简单工作可直接使用宿主的原生子代理；复杂系统也可自己实现任务队列、记录和检索。Ruflo 的产品面很广，选型应从一条实际需要的工作流验证，而不是从工具总数推断能力完整度。[项目解释文档](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/docs/ruflo-explained.md#L23-L61)

模型、skill、MCP 连接、执行 runtime 是四层。它没有提供替代 Claude/GPT 的模型权重；创建 swarm 或 agent 记录也不等于已经启动能够编辑文件、运行测试的编码工作进程。

### ③ 真实入口、执行路径与核心机制

**目录与入口。** 根 bin/cli.js 转发 v3 CLI；v3/@claude-flow 分 CLI、memory、swarm、security 等包，plugins/ 和 ruflo/ 另含插件与包装层。[CLI 入口](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/bin/cli.js#L145-L365)在管道输入和对应参数下直接进入 stdio JSON-RPC；tools/list 从[共享注册表](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/src/mcp-client.ts#L124-L197)取得定义，tools/call 通过 [authorizeMcpTool](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/src/mcp-client.ts#L247-L280)再调 handler。额外工具输出注入筛查仍由 strict guardrail 环境开关 opt-in，不能因有 security 包便假定全部默认打开。

1. **登记、执行、正确性是三种不同结果。** [swarm_init](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/src/mcp-tools/swarm-tools.ts#L261-L341)校验配置并落盘空 agents/tasks 的协调记录。真正 [agent_execute](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/src/mcp-tools/agent-tools.ts#L469-L515)校验 agentId/prompt 和资格后进入共享核心；[executeAgentTask](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/src/mcp-tools/agent-execute-core.ts#L570-L642)读取持久配置，选择模型与 system instructions，标记 busy，再请求 provider。已读 [Anthropic 分支](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/src/mcp-tools/agent-execute-core.ts#L247-L320)是一次 messages 请求并取文本，没有在该函数内提供文件工具循环；这条路径不能等同完整编码代理。provider 路由还支持 OpenRouter／Ollama，不能照旧 tool description 只写 Anthropic
2. **反馈必须写清测量对象。** [执行反馈与完成持久化](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/src/mcp-tools/agent-execute-core.ts#L644-L816)对可重试错误做有预算的替代模型尝试，完成后重新读最新 agent 记录，避免覆盖执行期间用户修改或终止状态。关键是源码明确把当前 success 定义为“API 返回成功”，可选 transcript 的 resolvedSource 也标成 api-success；这不是测试通过、任务正确或人类接受。这个边界对自学习路由比“有学习能力”四个字更重要
3. **消息总线与任务生命周期。** [MessageBus](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/src/message-bus.ts#L137-L259)按四种优先级使用环形 deque，每个 agent 有队列；[调度和投递](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/src/message-bus.ts#L439-L611)把一轮入队合并到 setImmediate，按 agent 每轮至多 10 条，保留 ≥250ms backstop，失败投递有有界退避。另一个导出的 [TaskOrchestrator](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/src/coordination/task-orchestrator.ts#L120-L273)维护任务／依赖图，进行 queued→assigned→in-progress→completed 转换并通知 AgentRegistry。它与 UnifiedSwarmCoordinator 的独立任务实现不能混为一层；当前具体缺陷见下节

**阅读范围。** 全树、根／CLI／swarm／memory manifest 与 LICENSE；README 的概念、安装与演示边界；解释文档的层次、成本与验证章节；CLI stdio 派发、MCP 注册／授权、swarm_init、agent_execute handler 与核心 provider／重试／反馈／落盘段；MessageBus 队列与生命周期、TaskOrchestrator 的创建和状态转换、AgentRegistry assign/complete；[模型别名测试](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/cli/__tests__/agent-execute-models.test.ts)全文、[事件驱动测试](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/__tests__/message-bus.event-driven.test.ts)前 140 行。另读 memory smartSearch 的主要流水线。未审计全部插件、provider、策略引擎或运行完整测试。活动证据读取了最近 8 个提交、3 个 releases 和 12 条开放 issue／PR 条目，完整读 #4235／#4236 的 PR 详情；#4233／#4234 使用开放列表中的正文与固定 main 源码，未读其全部评论。Discussions 抽读列表及 #3165，网页所示抓取时间为两天前，不能据此断言最新讨论状态。

### ④ 亮点，以及源码确认的当前限制

优点是共享工具派发点、明确的 provider 结果、部分执行并发后的状态保护，以及把纯检索与执行组件拆开。RAG 方面，[smartSearch](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/memory/src/smart-retrieval.ts#L486-L575)能在调用者提供的 SearchFn 上做规则 query expansion、RRF、时间权重、MMR 和会话轮转；默认扩展不需要 LLM，也不能由此推断所有 CLI memory search 都自动走此链。其英文关键词提取使用 \w 相关规则，中文适配应另测。

今天值得关注的是“状态一致性与退出行为”，不只是速度宣传：

- **队列溢出可能先丢 urgent。** [removeLowestPriority](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/src/message-bus.ts#L178-L197)先删 low／normal，无这两级时回到 urgent→high 的派发顺序，所以只有 urgent+high 的满队列会先淘汰 urgent。[PR #4235](https://github.com/ruvnet/ruflo/pull/4235)正修正这一点；当前 open、未合并。源码足以定位分支，PR 的测试通过数不是本次实测
- **失败／取消未完整释放 worker 所有权。** [failTask/cancelTask](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/src/coordination/task-orchestrator.ts#L239-L273)把失败任务重新排队或把 agent 状态设为 idle，却没有对应清空 AgentRegistry.currentTask；[registry](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/src/coordination/agent-registry.ts#L207-L235)后续 assign 会因已有 currentTask 拒绝。[PR #4236](https://github.com/ruvnet/ruflo/pull/4236)处理该问题和分配失败回滚，读取时同样未合并。**范围限于导出 TaskOrchestrator／AgentRegistry 及兼容层，不可扩大成所有 Ruflo 编排路径都坏了**
- **ACK 和 shutdown 还需验证。** 当前[ACK map](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/src/message-bus.ts#L420-L437)只以 messageId 查找，而[广播投递](https://github.com/ruvnet/ruflo/blob/1882006a02487590c8c66a7eec8d7504f6af33c3/v3/@claude-flow/swarm/src/message-bus.ts#L527-L560)对每位接收者写同一个键，存在互相覆盖定时器的逻辑；排入 setImmediate 的 subscriber callback 也没有在执行时再次检查 isShutdown。对应今日公开 [PR #4234](https://github.com/ruvnet/ruflo/pull/4234)、[PR #4233](https://github.com/ruvnet/ruflo/pull/4233)均出现在 open 列表；本次没有执行竞态复现

根 package 的 build:ts 和 lint 带“|| true”，所以仅看外层命令成功退出不足以确认下层编译／lint 通过。项目声称的吞吐、模型路由收益、benchmark 数字均未在本次复跑。

### ⑤ 今日热度：事实、近况与因果限制

**事实：** [v3.56.10](https://github.com/ruvnet/ruflo/releases/tag/v3.56.10)于 **10 月 14 日 16:33 UTC**发布，包含 MCP 启动路径、每 session 一个 Node 进程、cwd／daemon、memory 等修复；当前 main 仍为该 release merge。10 月 16 日晚出现 #4233—#4236 等边界修复 PR，是新增维护活动，尚未进入今天固定 main。Discussions 已抽查[工具定义变更记录讨论 #3165](https://github.com/ruvnet/ruflo/discussions/3165)，其发帖在 9 月，不能拿它当今日传播证据；可见页面也不是所有讨论的穷尽检索。

**推断：** 多 Agent、MCP、持久记忆和可视控制台的组合可能吸引开发者，但工具数量／动态图演示不能替代端到端执行验证，也没有足够证据把 stars today 归因于某个新补丁或发布。**暂无足够公开证据解释今日热度**。

### ⑥ 对你的工程栈的价值

对 **Node／TypeScript Agent**，最值得借鉴的是把登记、模型调用、任务验收和观测指标分开，并针对 retry、cancel、overflow、broadcast、shutdown 写状态不变量测试。对 **MCP**，共享授权入口可减少旁路，但大工具目录仍增加审查与上下文成本。对 **RAG**，可单独研究 smart-retrieval，先在自己的语料上测召回与中文支持。**React／Next.js** 可做任务与证据控制台，**Python／Django** 可通过受控 MCP／HTTP 互操作；这里没有已验证的现成 Django 集成。初次采用宜验证一个有明确验收测试的闭环，避免把 API-success、registered 或 running 字样展示成用户需求已完成。

## 7. android/skills

### ① 排名、元数据与版本锚点
官方第 **7**；[仓库](https://github.com/android/skills)；**8,100 stars，+36 stars today，Kotlin，Apache-2.0**。main **5bda39f154fb859a08d45e2392f3568e049f83fb**，提交于 **10 月 14 日 11:24:05 UTC**。完整树 **654 条目、412 文件、30 个 SKILL.md**；[Claude manifest](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.claude-plugin/plugin.json)和 [Codex manifest](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.codex-plugin/plugin.json)均为 **1.0.15**，对应 [v1.0.15 release](https://github.com/android/skills/releases/tag/v1.0.15)于 **10 月 14 日 11:24:10 UTC**发布。Kotlin 是 Trending 标签；本仓并非一个 Kotlin 编译器或 Android runtime，选读的可执行审计链实际是 Python。

### ② 它解决什么实际问题
Google/Android 把模型容易出错的新 API、迁移、构建和专项排查流程写成标准技能，面向用 agent 开发 Android 应用的人。它替代的是反复查阅分散的官方文档和自行整理迁移清单；并不取代 Android SDK、Gradle、模拟器或设备验证。[README](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/README.md)强调优先处理评估中模型表现不足的场景，而非重复基础 Compose 常识；公开贡献目前以 issues 反馈为主，不接受直接公共贡献。

### ③ 架构、入口与真实数据流
**知识分发层。** 目录按 build-system、device-ai、navigation、play、security 等场景分组。不同宿主 manifest 引用同一技能路径；[更新工作流](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.github/workflows/update-skills.yml)拉取官方技能压缩包并叠加 github-skills 分支，扫描 `SKILL.md` 重建列表，保持 marketplace 只做目录、组件放在 plugin manifest。当前定时触发仍被注释，仅 workflow_dispatch 生效。[发布工作流](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.github/workflows/create-release.yml)同步修改两个 manifest 版本，再打 ZIP 和 release，因此版本一致性是明确的分发机制。

**真正带程序的数据流：Play Policy Insights。** [技能协议](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/SKILL.md)定义“事实采集→按目标分析→聚合→critic→报告”流程；[Python 入口](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L1025-L1090)的子命令只有 `init` 与 `aggregate`。`init` 创建工作区 scratch、解析 manifest/Gradle 信息、建立文件清单，再写目标 worker 的输入 JSON 和提示文件。脚本本身不调用某个模型 API；worker/critic 的模型执行交给宿主 agent，缺乏委派能力时由宿主顺序完成。

1. [单次遍历与并行信号扫描](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/scanner.py)先把 manifest、Gradle、源码分类，过滤一些测试/debug/资源路径；遇到 package.json 或 pubspec.yaml 可把扫描根扩展到混合应用根。八线程扫描去掉注释后做配置模式匹配，汇总源码路径、数据类型信号和相关 URL。模式来自 [scanner_config.json](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/resources/scanner_config.json)，这里是启发式文本检测，不是构建后的权限证明或跨过程静态分析。
2. [目标分块与 findings 聚合](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L693-L955)把数据安全证据按每 worker 至多六条分块；生成的 worker JSON 再被加入稳定 finding_id 与来源文件，非 SUGGESTION 的 findings 按每组三项生成 critic 输入。协议以文件作交接，并让宿主先检查产物存在、JSON 有效后再决定是否重试。
3. [报告合成器](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/generate_report.py)读取 findings、critic 决定和 [Play Store 读取器](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/play_store_scraper.py)取得的声明，做分类与展示。确定性体现在脚本处理、排序和模板渲染，不代表 LLM 生成的分析本身是确定的。

作为对照，[AppFunctions](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/device-ai/appfunctions/SKILL.md)只是“发现功能→Kotlin 实现/配置→KDoc→ADB 验证”的指导与示例；[R8 analyzer](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/performance/r8-analyzer/SKILL.md)按 AGP/R8 版本分支选择定量工具或启发式分析，不是仓库自己实现 R8。已读范围：README、四份分发 metadata、两项工作流；Play Policy SKILL、scanner 全文、orchestrator 的身份/分流/聚合/入口段、report 的决定应用/合规状态/渲染段和 scraper 的抓取/发布状态段；AppFunctions 与 R8 说明。未遍历全部参考文档，未构建 Android 应用。

### ④ 技术亮点与边界
值得学的是**把廉价静态事实采集与昂贵 agent 判断拆开**，用 JSON 文件保留可重试中间结果，按证据量而非只按文件数分派工作。发布层把两种宿主 manifest 和技能目录保持一致，也比只复制提示更可维护。

但“报告写出 Compliant”不能等价为完整合规证明。[扫描错误路径](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/scanner.py)对单文件异常可直接跳过；[聚合错误处理](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L848-L879)对坏 worker 文件警告后继续；[缺 critic 默认值](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/generate_report.py#L249-L315)缺少某 finding 的 critic 结果时会设为 VERIFIED（设计意图包含无需 critic 的建议项），并未在此处单独验证“全部应有 critic 都完成”。因此宿主协议中的产物完整性检查非常重要，确定性报告生成不能弥补输入缺失。

还有明确的文档/实现差异：SKILL 的顺序模式示例写 `--aggregate`，而 argparse 注册的是 `aggregate` 子命令；这是静态对照，未执行复现。R8 技能引用的两个脚本在本次完整树中未找到，不能仅凭此仓 ZIP 保证对应定量路径可运行，是否由其他安装渠道补齐未核实。

### ⑤ 近期活动与热度：事实、推断分开
**事实：**[10 月 14 日技能更新提交](https://github.com/android/skills/commit/ac598b694760b11b67cad3eebb87a19ef48203c0)的 manifest diff 新增 parked apps、LiteRT runtime、Compose performance、Glance canonical layouts、Wear widgets 五条路径，随后发布 1.0.15。今天最新 open [PR #235](https://github.com/android/skills/pull/235)提议自动生成 release notes，当前发布说明仍很简短，不能把提案当已实现。

更实用的反馈是 [open issue #226](https://github.com/android/skills/issues/226)：报告者称 `alias(libs.plugins.androidApplication)` 未被识别，导致错误应用 ID、错误 Play Store 查询，仍得到偏乐观报告。[当前别名正则与入口](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L946-L1058)确实只匹配特定命名形态，[当前状态判定](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/generate_report.py#L556-L570)也确实默认从 Compliant 开始再升级风险。现有代码支持其问题路径，但本次没有对该应用复现，不推广为所有项目都会误判。

**推断：**新平台能力和官方资料包可以降低 Android agent 使用门槛，但新增是三天前发生；**暂无足够公开证据解释今日热度**，不把 +36 宣称为某 release 带来的确定增长。

### ⑥ 对你的工程价值
对 **AI/Agent**，最值得学习的是特定任务 skill 的路由、先事实后推断与文件化 worker/critic 交接。对 **MCP**，AppFunctions 的接口描述和最小可暴露功能值得参考，但 Android 平台机制与 MCP 不是同一个运行协议。对 **RAG**，这里更像维护好的领域知识包和有出处的参考资料，并未自带向量索引。对 **React/Next/Node**，原生 Compose 指南不能直接搬用，但混合移动项目的源码信号采集有参考价值；对 **Python/Django**，可借鉴分阶段审计任务与人工复核报告服务，同时把“资料缺失/未验证”作为一级结果，避免生成绿色成功状态掩盖证据不足。

## 8. obra/superpowers

### ① 排名、版本和昨日对照

官方第 **8**；[obra/superpowers](https://github.com/obra/superpowers)；**300,710 stars，+973 stars today，Shell**；MIT。今天重新读取 main，仍为 **bb92a77741419a4ab5f06e711a283343f1ada0c3**，**与昨日固定 SHA 完全一致**。完整树 **306 条、238 个文件，未截断**。[package.json](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/package.json)与插件 manifest 均为 **7.0.0**；[v7.0.0 release](https://github.com/obra/superpowers/releases/tag/v7.0.0)发布时间为 **10 月 10 日 00:28:58 UTC / 北京时间 08:28:58**。今天的源码讨论是对同一版本加深阅读，不包装成新合入功能。

### ② 它解决的问题和适用人群

它给编码 agent 提供需求澄清、设计、计划、TDD、调试、子任务审查、收尾的技能集合，同时用少量 Shell/JS/Python 代码处理宿主注入、任务工件和可视交互。适合希望保留可审查过程、让长任务在上下文压缩后继续的开发者。它替代的是零散提示词、口头“做完了”和容易丢失的上下文；不是新的基础模型，也不是能独立执行全部技能的强制工作流服务。[README](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/README.md)

这一点决定它的实际收益和边界：脚本能强制检查 Git 范围或测试返回码，Markdown skill 里的“先设计”“审查几轮后停”仍需要宿主和模型遵守。对需求已经充分明确的小改动，流程过重本身也会成为成本。

### ③ 架构、入口和三个机制

**宿主入口。** [hooks.json](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/hooks/hooks.json)在 startup/clear/compact 调 [run-hook.cmd](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/hooks/run-hook.cmd)，后者以 Windows batch/Unix shell 双格式找到 Bash 并运行 [session-start](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/hooks/session-start)。它读 `using-superpowers`，用 Bash 内建转义成 JSON，按 Claude/Cursor/其他宿主输出不同字段，避免同一内容重复注入。Windows 优先找已知 Git Bash 路径，再做受约束 PATH 查找；找不到则静默退出。Codex 的 [.codex-plugin/plugin.json](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/.codex-plugin/plugin.json)明确 `hooks:{}`，采用原生 skills 路径，不能声称所有宿主都走同一 SessionStart 链。

**机制一：把任务身份和完成证据落到工作树。** [sdd-workspace](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/subagent-driven-development/scripts/sdd-workspace)按计划文件分配 `.superpowers/sdd/<plan>/`，以物理归一化后的 plan-path 识别归属；重名计划用父目录和计数器消歧，不覆盖已有 `.gitignore`。这防止下一份计划误读旧账本而跳过任务。[task-start](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/executing-plans/scripts/task-start)提取任务 brief 并打印开始 HEAD；[task-done](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/executing-plans/scripts/task-done)执行传入测试命令、保存完整日志，只在退出码为零时追加 ledger。[review-package](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/subagent-driven-development/scripts/review-package)验证 BASE/HEAD 可解析、祖先关系与非空区间，输出 commit list、stat 和 `diff -U10`，避免仅审 HEAD~1 丢掉多提交任务早期改动。

**机制二：需求过程按规模分流，语言约束与代码约束分离。** 当前 [brainstorming skill](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/brainstorming/SKILL.md)允许明确小任务直接做；需求缺关键内容时先开放提问、复述确认，再决定聊天描述还是书面设计。它提供跳过提问的路径，明确 throwaway spike 与正式实施有不同门槛。[writing-plans](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/writing-plans/SKILL.md)记录实现者不能自行推断的接口与约束，[SDD skill](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/subagent-driven-development/SKILL.md)定义控制者、实现者、审查者和修复循环。这是有结构的协作协议；不能因为文档写了停止条件就认定运行时有独立 watchdog 强制执行它。

**机制三：可视 companion 是带访问边界和生命周期的 Node 小服务。** 今天补读了昨日未深入的 [server.cjs](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/brainstorming/scripts/server.cjs)。它用 Node 内建 HTTP、crypto、fs 与自实现 WebSocket 帧处理，默认绑定 `127.0.0.1`；模型写 HTML 到 content 目录，fs.watch 做 100ms debounce，向浏览器广播 reload，浏览器选择回到 events 文件。不是 React/Next 应用，也没有必要为了这个一次性工具引入完整 Web 框架。

- [认证与静态文件检查](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/brainstorming/scripts/server.cjs#L304-L449)：随机会话 token，query key 或 HttpOnly/SameSite cookie 认证，constant-time 比较；WebSocket 还核对 Origin 与 Host。文件只接受 content 目录内普通文件，拒绝符号链接、硬链接和越界 realpath
- [生命周期](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/brainstorming/scripts/server.cjs#L550-L709)：默认四小时闲置退出，定期检查 owner PID；关闭时销毁升级后的 WebSocket，否则 `server.close()` 可能留住进程。端口占用只尝试一次随机端口，fallback 不覆盖原会话的端口/token 文件，减少旧标签页被另一会话破坏

### ④ 最值得迁移的设计与限制

最值得迁移的不是某句强提示，而是**“计划身份 → 任务起点 → 完整 diff → 原始测试输出 → 完成账本”**。这让压缩后的 agent 不必靠自然语言记忆猜测做了什么。可视 companion 则展示了临时 UI 也需要认证、路径边界和退出条件；“只在 localhost”并不代表任意网页都应该能调用。

但 `task-done` 只证明**调用者提供的命令返回零**，不能证明测试覆盖了需求、oracle 独立或测试不会空跑。账本是普通可写文件，不是不可篡改证据库；同一计划在同一 worktree 的并发执行仍共享工件。方案记录等于可恢复，不等于具备事务、权限隔离和调度互斥。

companion 的 token 是会话级访问控制，默认 HTTP，并非互联网多租户服务模板。源码默认远端加载带版本参数的品牌图片；[README 的 telemetry 说明](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/README.md)给出 opt-out，server 也读取相应环境变量。不要把“零 npm 依赖”误解成“绝无外部请求”。测试文档区分普通脚本测试和真实 LLM 行为评测；维护者的行为实验不能代替在你的任务和模型上的复核。[testing.md](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/docs/testing.md)

### ⑤ 近期反馈与今天为何受关注

**事实：**main 和昨日一致，7.0 是一周前 release。新增反馈比“又更新了多少功能”更值得看：

- [issue #2530](https://github.com/obra/superpowers/issues/2530)报告 v7 在已有规格、继续阶段任务时仍问宽泛动机问题。另一用户提供类似 backport 场景，并表示进一步澄清后下一阶段恢复预期。它说明需求澄清与已有上下文复用存在实际摩擦；是具体用户反馈，不是所有模型/所有会话的结论
- [issue #2539](https://github.com/obra/superpowers/issues/2539)提出由独立 agent 先写验收测试、检查 oracle 来源、再交实现者。这与 `task-done` 的零退出码边界相呼应，但它**仍是提议，不是 7.0 已实现能力**；作者给出的失败数和耗时本次没有复测
- [issue #2536](https://github.com/obra/superpowers/issues/2536)指出 Hermes 子代理首轮也获得控制者 bootstrap。当前 [.hermes-plugin/__init__.py](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/.hermes-plugin/__init__.py#L110-L125)确实只判断 `is_first_turn`，没有按 `platform` 排除 subagent；[PR #2540](https://github.com/obra/superpowers/pull/2540)仍 open。**代码条件已核实，子代理一定跑偏未被本次验证**

**推断：**多宿主覆盖和可审查的 agent 开发流程是长期吸引点；7.0 的讨论也提供可见持续关注。不过没有证据说明今天 +973 由某条 release、某个帖子或某项修复直接造成。**暂无足够公开证据解释今日热度。** 仓库 metadata 显示 Discussions 未启用，本次通过 issues/PR/release 查看反馈。

### ⑥ 对你的技术方向的实际价值

对 AI Agents，适合研究在长任务中如何留下外部状态、给 reviewer 最小充分证据；对 MCP/RAG 应用，可把工具权限、输出完整性、检索评测和失败恢复变成任务验收条件。特别是 #2539 提醒：检索结果的评测答案、工具输出检查，不应由被测实现自己生成再拿来证明自己。

对 React/Next/Node，companion 展示一个轻量预览控制面：文件驱动刷新、会话隔离和可靠退出可以直接迁移到开发预览工具。对 Python/Django，Shell 的任务工件机制与语言无关，但若要做真正的长期编排，应把轮次上限、租约、状态迁移和幂等做成服务端代码约束，而不只写在 skill 文本里。

**已读范围与证据限度：**今天固定 SHA 的 README、package/Claude/Codex manifest、hooks 三文件、sdd-workspace/task-brief/review-package/task-start/task-done 全文；brainstorming 全文、writing-plans/SDD 的流程和验收段；server 的认证、文件、消息和生命周期段、start-server 启动配置段；testing 文档及 Hermes 首轮注入；最新 15 个 commits、5 个 releases、15 条按更新时间的 issues/PR，以及 #2530/#2539 评论。完整树不代表全仓审计；没有运行 hooks、服务器、测试或 LLM eval。

## 9. cursor/plugins

### ① 排名、元数据与版本锚点
官方第 **9**；[仓库](https://github.com/cursor/plugins)；**11,988 stars，+278 stars today，TypeScript**。main **09d06eb4b97a1020ab31e84030e38baf1099c7dc**，提交于 **2026-10-17 01:24:48 UTC**。完整树 **1,722 条目、1,117 文件**；[marketplace](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/.cursor-plugin/marketplace.json)列 **109 项**，均为仓库相对路径，包含 third_party 下的集成。仓库没有统一 release，releases 查询为空；本次核心 [Orchestrate 插件](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/.cursor-plugin/plugin.json)为 **1.1.0**，其私有脚本 [package.json](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/package.json)仍为 **0.0.0**，不能混成整个 Cursor 产品版本。根 README 标 MIT。

### ② 它解决什么实际问题
它把 Cursor 的开发流程、团队规则、技能和 SaaS 集成组织为可安装插件，面向希望复用编码与业务工具工作流的开发者。替代方案是自己维护 rules/skills/MCP JSON，或逐个连接服务。本仓不只是提示清单：Orchestrate 含完整 TypeScript 脚本；但大量 third_party 条目仍主要是 metadata 或连接配置，不意味着本仓实现了该 SaaS 服务。

### ③ 架构、入口与真实数据流
**目录层。** [README](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/README.md)描述 marketplace→独立 plugin manifest→skills/rules/MCP 配置。[校验器](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/scripts/validate-plugins.mjs)用 Ajv 验证 schema、存在的目录与 manifest、名称一致性及多份 manifest 版本一致；[CI 工作流](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/.github/workflows/validate-plugins.yml)运行它和生成目录检查，不等价于所有插件功能回归测试。对比两个已读集成：[Playwright MCP 配置](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/third_party/playwright/mcp.json)调用外部 npm 包的 latest；[QuickBooks MCP 配置](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/third_party/quickbooks-online/mcp.json)只声明远端 HTTP URL。后者没有在此实现服务端；前者会受未来 latest 解析变化影响。

**执行切面：Orchestrate。** [README](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/README.md)要求 Bun 和 Cursor API key，Slack 镜像可选；[依赖清单](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/package.json)包括 Cursor SDK、Slack Web API、Commander 与 Zod。[技能入口](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/SKILL.md)声明只在显式 `/orchestrate` 时启动；[CLI 注册器](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/cli/index.ts)注册 task、inspect、comment、andon、forensics 命令。架构把 planner 的计划决策与脚本的执行状态拆开：`plan.json` → schema 校验 → cloud agent → `handoffs/*.md` → `state.json` → 下一批任务。

1. **可恢复调度。** [reconcile loop](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/core/loop.ts)先恢复 running 行，再每十秒扫描依赖已 handed-off 的 pending 任务。新错误默认让循环退出交回 planner；下游保持 pending，不偷偷删掉。达到运行时预算时保存 Git checkpoint 并以特殊退出码 100 要求重入，区别于任务完成。
2. **结果先落盘，再公布完成。** [AgentManager](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/core/agent-manager.ts)通过 SDK create/send 后持久化 agentId/runId；重启可 getRun 重新附着。SSE 错误不直接等同远端失败，会读取权威运行状态再判断。handoff 写入临时文件后 rename，再把 task 设为 handed-off，避免下游看见完成状态却找不到产物；失败则补独立 failure handoff，保留末次活动与错误线索。
3. **分支与验证声明分别建模。** [分支规则](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/core/branches.ts)区分 worker 与合并 worker；[handoff 解析](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/core/handoff.ts)优先读取结果里的 Branch，再退到 SDK/现有状态。验证结果分 `live-ui-verified`、`unit-test-verified`、`type-check-only` 等，旧 `pass` 保守映射为 type-check-only，不自动升级为浏览器验证。[Zod schema](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/schemas.ts)为这些声明及 worker/subplanner/verifier 结构给出显式类型。

已读范围：README、marketplace、三个 manifest/MCP 示例、validator 和 CI；Orchestrate README/SKILL、package/CLI、schemas 的任务/状态/验证段、loop/branches/handoff 全文、manager 的 load/spawn/recover/wait/verification/写状态段；操作边界测试与 cli/util 的树遍历/操作标志段。未通读全部 pstack、agent-manager 的每个辅助方法或所有第三方插件，未实际启动云 agent。

### ④ 技术亮点与边界
最值得学习的是**云运行状态、handoff 文件、验证结论三者分开**，以及失败后仍能恢复和追责的工程处理。若只在模型上下文中记“哪个 worker 做完了”，进程重启或断流很容易丢任务；这里保存了继续定位所需的 IDs、分支和文件。

不过 handed-off 仅表示运行已结束并交回内容，不自动保证验收通过。当前 `waitAndHandoff` 即使 finished 输出缺结构化 Status 也先设 handed-off，再写提醒 sidecar；依赖检查只看该状态，验证结论另存。因此调用方若需要“只有测试通过才启动下游”，还要做显式 gate。pathsAllowed/pathsForbidden 等规划字段也不能仅凭 schema 当作 OS 隔离。部分任务会创建云运行、执行命令和读写 Git，部署前要独立核对预算、权限与退出控制。

退出控制存在具体待修问题：[open issue #641](https://github.com/cursor/plugins/issues/641)称 kill-tree 会漏过已经 handed-off 的 subplanner 分支里的 running 后代。[当前两种树遍历](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/cli/util.ts#L52-L184)静态确认 crawl 对 running/handed-off 都递归，而 collectRunningAgentsInTree 只对 running subplanner 递归。没有实际运行取消操作，所以结论限于代码路径差异；不能宣称“全树取消已可靠覆盖全部后代”。

### ⑤ 近期活动与热度：事实、推断分开
**事实：**今天 [main 合并 #694](https://github.com/cursor/plugins/commit/09d06eb4b97a1020ab31e84030e38baf1099c7dc)新增 Zoho CRM/Desk/Books 的目录 metadata、说明、许可证和图标。已读 [Zoho manifest](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/third_party/zoho-crm/.cursor-plugin/plugin.json)还声明 Cursor 最低客户端 3.19.0；该目录本身没有 MCP 服务端实现。稍早 [#693](https://github.com/cursor/plugins/pull/693)合入 QuickBooks 原生 HTTP MCP 声明；昨天晚间还有 Gusto/TikTok 目录新增。这些是可核验的目录扩展，不是 Orchestrate 核心今天发布新调度算法。

**推断：**持续增加常见工作软件入口可能拓宽受众，而多 agent 工作流对开发者有吸引力。但尚无明确流量/社媒/发行归因证据，**暂无足够公开证据解释今日热度**；+278 只能作为官方榜单计数，与合并在时间上接近不足以证明因果。

### ⑥ 对你的工程价值
对 **AI/Agent**，Orchestrate 的持久化 reconcile、可恢复运行、结构化 handoff 与验证等级最值得单独研究。对 **MCP**，配置目录展示了本地命令与远端 HTTP 的交付差别，也提醒将服务实现、授权和版本锁定单独审查。对 **RAG**，handoff 是面向任务的压缩证据传递，不是自动知识库。对 **React/Next/Node**，TypeScript schema/状态机可作为开发任务后台的参考，交互 UI 宜展示运行状态与验证等级两列；对 **Python/Django**，同样可搬用队列状态、幂等结果交接与断线恢复设计，而不必引入完整 Cursor 宿主。

## 10. debpalash/VoiceStudio

### ① 排名、版本和真实新增范围

官方第 **10**；[debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio)；**71,334 stars，+2,301 stars today，Python**。今天固定 main **f47221a1f0af89df27c34747471daa30391a9487**，提交于 **10 月 16 日 09:02:48 UTC**；完整递归树 **3,550 条、3,343 个文件，未截断**。应用 manifest 与 Python project 版本为 **0.5.7**，AGPL-3.0-only；公开最新 [release v0.5.6](https://github.com/debpalash/VoiceStudio/releases/tag/v0.5.6)仍发布于 **9 月 23 日 08:53:32 UTC**，不能称 0.5.7 已正式发布。

与昨日 **28d18023436229830debe8e65faf3eba4426f31b** 的 [compare](https://github.com/debpalash/VoiceStudio/compare/28d18023436229830debe8e65faf3eba4426f31b...f47221a1f0af89df27c34747471daa30391a9487)为 **ahead 4、behind 0，只有 3 个 README 文件变化**，内容是新增/链接访问量徽章。**今天这个源码区间没有业务代码变化**；下面是对今天 SHA 的真实架构复核和新增问题反馈，不把昨日已存在的引擎/MCP/修复写成今日新增。

### ② 解决什么问题，适合谁

VoiceStudio 是本地优先的语音工作台，组合声音克隆、描述式声音设计、TTS、转录、视频配音、听写和长篇音频制作，面向创作者及要给 agent 接语音的工程师。它把散落的模型脚本、FFmpeg、权重管理、声音资料和桌面 UI 收进同一套应用生命周期；也允许桌面作为远端 VoiceStudio 后端的客户端。[README](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/README.md)

“646 语言”是项目整体能力口径，不是所有引擎都支持同样语言、同样声音和同样效果。本次未做音质或逐语言测试。本地优先也不等于所有安装、权重下载和可选远端引擎都离线。应用代码、各模型权重、声音素材和输出使用权需要分别检查，README 明确声音克隆应取得许可。

### ③ 实际架构、依赖与三条关键数据流

**目录和技术栈。** [STRUCTURE.md](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/docs/STRUCTURE.md)与实树显示：`electron/` 是现行桌面及 Web UI；`backend/` 分 api/core/services/engines；`omnivoice/` 是模型包；`native/desktop-bridge/` 提供 Rust 辅助；测试分别覆盖后端与桌面。旧 Tauri 不是当前架构。[根 package](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/package.json)用 Bun workspace；[Electron package](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/electron/package.json)包含 React 19、Vite、TanStack Query/Router、Zustand 和 Tailwind，**不是 Next.js**。[pyproject](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/pyproject.toml)要求 Python ≥3.11，含 PyTorch/Transformers、FastAPI/Uvicorn、httpx 和 MCP SDK，并对 MLX 等依赖用平台标记。依赖表仍出现 Gradio，不代表现行桌面由它驱动。

**机制一：从用户请求到稳定音频产物。** [Electron main](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/electron/src/main/index.ts#L90-L230)创建窗口、管理退出与本地资源；窗口采用 contextIsolation、关闭 nodeIntegration，但源码的 sandbox 仍为 false，不能笼统称“完整沙箱隔离”。[React 入口](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/electron/src/renderer/src/main.tsx)选择捕获浮窗或主应用。后端 [POST /generate](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/api/routers/generation.py#L1675-L1885)先 NFC 规范化文本，解析指定/默认引擎，检查模型许可与克隆条件，再做设备路由、驻留模型管理和独立加载预算，避免把冷启动下载时间误算为推理超时。

[共同 finalize](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/api/routers/generation.py#L1492-L1638)把普通文件响应和 NDJSON 分块预览收束到同一路径：可选水印 → 独占预留文件名 → 写 WAV → history → 保留策略 → 事件。写文件的线程在 async 取消后不会自动停止，所以代码 shield 并等待真实写入任务结束，再清理未发布文件，避免刚删掉又被后台线程重建。SQLite history 失败尝试修复并重写，仍失败优先把音频返回；**音频可用和历史已持久化是不同成功条件**。水印失败也会透传音频，不能宣称每份输出都有可靠水印。

**机制二：把互相冲突的模型环境拆成受管理子进程。** [TTSBackend](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/services/tts_backend.py#L215-L280)统一可用性、语言、采样率、生成等协议；[SubprocessBackend._spawn](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/services/subprocess_backend.py#L492-L591)选择引擎自己的解释器，校验可执行文件，启动 owned child，独立线程排空 stderr，等待 ready 握手后才开始工作。[线协议与超时](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/services/subprocess_backend.py#L933-L1081)使用四字节长度前缀 JSON、帧大小上限和 op 白名单；watchdog 捕获这次请求的 process 对象，超时只处理该进程，收尾 join 等待回调完成，仍未退出的 owner 进入隔离清理列表，避免旧超时回调杀掉后续重试的新引擎。

这套设计解决的是依赖冲突和生命周期问题，**不是安全沙箱**。子进程继承父进程环境，仍运行本地代码并访问资源；部署时要另行控制文件、网络、模型来源和进程权限。

**机制三：UI 与 MCP 复用业务接口，文件输出有明确边界。** [mcp_server.create_mcp_server](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/mcp_server.py#L434-L625)建立 FastMCP；嵌入模式以 ASGITransport 调同一 app，独立模式走 HTTP。generate_speech 解析 per-agent voice/profile，再调用 `/generate`，并不重新实现推理。默认返回 inline base64 WAV；files/both 模式可返回可访问的音频 URL 及指定目录文件，减轻模型上下文负担。[MCP 文档](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/docs/mcp.md)

[文件输入边界](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/mcp_server.py#L118-L207)先要求 BASE_PATH，realpath/commonpath 检查，再在支持的平台通过 dir_fd 与 no-follow 逐级打开，最后复核已打开 descriptor 仍在目录内。这个细节比只对用户字符串做前缀检查可靠。音频 URL 和文件路径所在机器仍需与调用者部署方式匹配，不能假定返回的本机路径在远端 agent 上也存在。

### ④ 可复用亮点与落地边界

最有价值的是把“模型能出声音”扩展成**可安装、可选择、可取消、可重试、可回收、可保留产物**的应用工程。对多模型 agent 服务，独立冷加载预算、捕获进程身份的超时回调、先确保文件完成再发布 metadata，都比一个泛化 `timeout()` 更值得看。

安全边界要按部署方式读。[main.py 的 middleware](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/main.py#L1803-L1928)有 Bearer gate、浏览器 Origin/Host 防护和 CORS 顺序，默认本地 loopback 调用与配置后的远端调用待遇不同。[api-auth.md](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/docs/api-auth.md)进一步区分消费、管理员、主机文件权限，说明远端应使用受保护传输；这并不是多用户租户隔离和公网生产部署已经一键完成的证据。

更现实的成本是大模型权重、FFmpeg、硬件后端和不同引擎的 API/许可差异。模型语言能力不是 UI 字符串的前两位，错误报告脱敏也不能只用几个常见路径模板。今天的反馈正好暴露了这两个跨层契约。

### ⑤ 今日变化、问题核验与热度判断

**已核事实：**今日相对昨日仅 README 徽章变动，最新正式 release 仍为 0.5.6。下面三个新反馈不能写成已修复：

1. [issue #2938](https://github.com/debpalash/VoiceStudio/issues/2938)报告 Supertonic-3 将 Portuguese 等语言全名截成无效代码。当前 [sidecar._normalize_lang](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/engines/supertonic3/sidecar.py#L224-L240)确实对非 Auto 字符串返回 `s[:2]`；`/generate` 的表单也未提供 preset voice 字段。**截断实现和字段缺失已静态确认，用户音频结果与语言覆盖数未复测。** [PR #2939](https://github.com/debpalash/VoiceStudio/pull/2939)读取时 open
2. [issue #2937](https://github.com/debpalash/VoiceStudio/issues/2937)报告非标准 HOME 在后接句号、逗号、冒号等情况下未脱敏。当前 [core/scrub.py](https://github.com/debpalash/VoiceStudio/blob/f47221a1f0af89df27c34747471daa30391a9487/backend/core/scrub.py#L122-L136)的实际 HOME 匹配只接受斜线、空白、引号或字符串结束作为后界，源码与报告一致；[PR #2941](https://github.com/debpalash/VoiceStudio/pull/2941)仍 open。提交诊断前仍需人工检查，不能将“有 scrub 模块”视为所有私人路径都会被清除
3. [issue #2942](https://github.com/debpalash/VoiceStudio/issues/2942)报告 Windows 0.5.6 在 CPU-only 机器的 cuDNN 探测阶段以 0xC0000005 退出。这是单一安装环境的用户报告，本次未诊断根因，不推广成所有 CPU 安装都失败

**传播证据与推断分开：**[Discussion #2502](https://github.com/debpalash/VoiceStudio/discussions/2502)是 Repository Radar 作者在 **10 月 1 日**发布的自述，称该项目为其九月 Repository of the Month，并链接其报道。这证明此前确有外部推荐线索；其“星标翻倍”等统计为作者陈述，本次未重算，也没有证据将两周前推荐与今天 +2,301 建立因果。[Discussion #2446](https://github.com/debpalash/VoiceStudio/discussions/2446)则显示用户确有“Mac UI + 远端 GPU”需求，并区分 VoiceStudio backend 与普通 LLM endpoint；它是产品使用背景。

本地创作工作台与 agent 语音接口结合有传播潜力，但这仍只是推断。**暂无足够公开证据解释今日热度。**

### ⑥ 对你的工程方向的价值

对 AI Agents/MCP，优先研究 **files 模式、稳定 profile_id、音频任务状态与可取消 sidecar**。不要把长 WAV base64 默认回传给语言模型，也不要把“HTTP 请求结束”当作后台模型或写文件线程已结束。对 RAG，检索与证据生成应在上游；语音层接经授权的文本和声音素材，保持文本引用与音频产物的关联即可，VoiceStudio 本身不是向量检索系统。

对 React/Next/Node，这是一份 React UI 同时面向桌面/浏览器、通过稳定 Python API 调重模型的实际案例；现有 Next 服务可作受控网关，不必把模型加载搬进 SSR 请求。对 Python/Django，把 VoiceStudio 当独立推理服务或任务 worker，借鉴 loading/inference budget 分离、进程身份绑定、文件发布前的真实完成确认。若只看一个实现，推荐 subprocess_backend 的超时收尾和 generation 的 cancel-safe 文件写入；两者都可迁移到其他耗时工具任务。

**已读范围与证据限度：**今天固定 SHA 的 README、根/Electron manifests、pyproject、STRUCTURE；Electron main 的窗口与退出段、React main 全文；main.py 的 MCP/lifespan 索引与鉴权 middleware 1803–1928；mcp_server 的目录限制、HTTP/ASGI 客户端、输出模式和 generate_speech；generation 的入口、路由/加载及 finalize；TTSBackend 抽象/引擎注册索引；SubprocessBackend 启动、线协议、超时与收尾；api-auth/MCP 文档相应段；Supertonic3 归一化与 scrub 实现；最新 15 个 commits、5 个 releases、15 条按更新时间的 issues/PR、两条 discussion 正文及昨日 compare 全部 3 文件 diff。未逐引擎审计、未运行应用、未生成音频或测量性能。

## A. 最值得继续深读的三个项目

### 1. cursor/plugins：Agent 运行、交接和验收如何分离

优先顺序：[loop.ts](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/core/loop.ts) → [agent-manager.ts](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/core/agent-manager.ts) → [handoff.ts](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/core/handoff.ts)，同时核 [schemas.ts](https://github.com/cursor/plugins/blob/09d06eb4b97a1020ab31e84030e38baf1099c7dc/orchestrate/skills/orchestrate/scripts/schemas.ts)。

对你做 Node/TypeScript Agent 后台，这是一个具体的持久化调度纵切面：远端运行 ID、断流恢复、先写 handoff 后发布状态、预算到期 checkpoint，以及分支/验证等级。阅读时重点反问：下游到底依赖“交回来”还是“验收通过”？当前 handed-off 与 verification 分离却未自动形成强验收 gate，恰好能帮助你在自己的系统里把这条不变量写清楚。React/Next 控制台也应分别显示运行状态、交付文件和验证证据。

### 2. android/skills：有文件证据的多阶段审查，以及缺失输入如何产生乐观结论

优先顺序：[Play Policy SKILL.md](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/SKILL.md) → [scanner.py](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/scanner.py) → [orchestrator.py](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py) → [generate_report.py](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/generate_report.py)。

即使你不写 Android，这条 Python 链对 Django 后台审计、RAG 评估、agent reviewer 都有直接设计价值：廉价扫描先产事实，模型按证据分块，critic 再审查，报告独立合成。尤其要读坏 worker 文件、缺失 critic 和错误包名的处理，理解为何“脚本顺利生成报告”仍可能缺证据。迁移时应增加 required-artifact manifest、完整性校验和 unknown 状态，不应仅复制最终的绿色状态逻辑。该推荐是工程模式阅读，不是建议依赖它作合规结论。

### 3. mksglu/context-mode：不用 embedding 的工具输出 RAG 与预算控制

优先顺序：[server.ts](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/server.ts) 的执行/索引/检索转换 → [store.ts](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/store.ts) 的 FTS5/RRF → [flood-guard.ts](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/search/flood-guard.ts)，再核 [executor.ts](https://github.com/mksglu/context-mode/blob/5f6298a9bdc480ebc7c88a29c9fbdf38ae2f8cb6/src/executor.ts) 的真实进程权限。

这条链适合你从本地日志/测试输出的检索开始，比较“直接回全文”和“留存后按需回取”对 token、召回率与任务完成率的影响。分 Agent 限流、缺身份回默认桶、词法融合和输出预算是可以移植的模块；多租户隔离、中文召回、网络边界与 ELv2 许可要另做设计。它今天只有徽章统计变化，推荐理由是已有实现的工程价值，不是新发功能。

## B. 当天证据支持的五个趋势

1. **插件目录已成为工程交付层，但目录不等于服务实现。** Anthropic 的 315 项有大量外部 SHA 引用；Cursor 的 109 项目录将本地命令与 HTTP MCP 配置混合分发；Android 两种宿主 manifest 跟随同一技能树。共同问题是版本、供应链、权限和兼容性，不应靠“官方”或条目数跳过审查
2. **Agent 的“完成”正在被拆成更多状态，验收仍需调用方落实。** Cursor 区分 handed-off 与 verification；Ruflo 明示 api-success 仅指接口成功；Android 的文件化 worker/critic 仍可能遇到缺产物；ECC 记忆写入仍是 unreviewed。这些实现共同支持一个工程判断：UI 和编排层需要显示证据与未知，而不能把单一 success 字段当需求已完成
3. **知识包的维护与执行程序的可靠性同样重要。** K-Dense 177 技能有按技能依赖与测试分层，但扫描报告和 triage 日期会漂移；ECC pi/core 的生成文档与真实加载测试存在参数契约差异；Android 的 SKILL 命令示例和 argparse 子命令也有差异。技能内容应像接口文档一样接受版本、样例和实际入口检查
4. **上下文治理越来越像数据管线。** Context Mode 把长输出索引后取回，Autoskill 先脱敏/分段再描述匹配，Cursor 将长任务压缩成持久 handoff，CLI-Anything 用结构化 CLI 面向 Agent。这里有切块、版本、来源、预算与失败语义；“压缩”“记忆”“聚类”的产品名称不能替代实际算法说明
5. **热度与当日功能更新明显脱钩。** 连续七项中五项 main 完全不变，两项只改统计/README 徽章；Android release 是三天前，CLI-Anything 主干最后提交是九月。今天有可核的 Cursor 目录扩充与多仓新问题/开放修复，但没有足够增长归因证据。日报的阅读增量应来自更深的机制与边界，而不是把上榜重新包装成发版新闻

这些是本日前十样本支持的观察，不是整个 GitHub、开发者生态或市场份额的统计结论。

## C. 与昨天实际报告比较：2026-10-16

已取得并读取[昨天完整报告的固定归档](https://github.com/DanielMax937/daily-research-reports/blob/51fa06996bdd8d8f9dca284ecb473d141a6ff47a/2026-10-16/github-trending.md)，不是根据记忆恢复名单。昨天采样 10:40:30 北京时间，今天 10:26:57，相隔 23 小时 46 分 27 秒。昨日前十依次为 rea、claude-plugins-official、scientific-agent-skills、caveman、VoiceStudio、superpowers、ruflo、context-mode、ghidra、ECC。

| 连续出现的项目 | 昨日 → 今日排名 | 排名变化 | 昨日 → 今日总 stars | 快照总数差 | 今日 stars today |
|---|---:|---|---:|---:|---:|
| anthropics/claude-plugins-official | 2 → 1 | 升 1 | 39,202 → 40,651 | +1,449 | +1,552 |
| K-Dense-AI/scientific-agent-skills | 3 → 2 | 升 1 | 50,573 → 51,557 | +984 | +1,158 |
| affaan-m/ECC | 10 → 3 | 升 7 | 280,475 → 281,569 | +1,094 | +1,057 |
| mksglu/context-mode | 8 → 5 | 升 3 | 29,828 → 30,258 | +430 | +449 |
| ruvnet/ruflo | 7 → 6 | 升 1 | 75,178 → 75,660 | +482 | +672 |
| obra/superpowers | 6 → 8 | 降 2 | 299,973 → 300,710 | +737 | +973 |
| debpalash/VoiceStudio | 5 → 10 | 降 5 | 69,260 → 71,334 | +2,074 | +2,301 |

两次采样并非恰好 24 小时，stars today 的窗口也不透明，不能把总数差和 stars today 当成同一指标。

- **本次前十新进入：** HKUDS/CLI-Anything、android/skills、cursor/plugins。CLI-Anything 在 10 月 15 日报告中曾出现，但不在昨天前十；因此这里仅称相对昨天“新进入”，不称首次走红
- **昨天前十、今天前十未出现：** morluto/rea、JuliusBrussee/caveman、NationalSecurityAgency/ghidra。这不证明它们退出全部 Trending、星标下降或社区不再关注
- **主题变化：** 昨天包含 REA/Ghidra 逆向后端与 Caveman 压缩工具，今天新增 CLI-Anything、Android 技能与 Cursor 插件分发，样本更集中于现有软件的 Agent 接口、平台专用技能及跨宿主分发。VoiceStudio 仍是明显的完整应用切面；不能把这十个样本推成全行业份额变化
- **源码与榜单分开看：** 各项目正文列出今日已读提交和可确认的变化。没有昨天源码基线的新进入项目，不补造一日 diff；版本不变或仅数据文件变化的项目也不包装成今日新能力

### 连续上榜不等于持续发版

今天重新锁定的源码显示：Anthropic 插件目录仍是昨天 `ea10b213686c90bb1984b2016937310e05336cf3`，K-Dense 科研技能仍是 `a1043ef544e3a100c28e70a736b6cf32554d0677`，ECC 仍是 `76aaa77df6adc5b889e689007bf99b9a4f74af34`；Ruflo 也与昨天相同（完整 SHA 见正文）。Context Mode 的今天 main 仅在昨天提交上更新 `stats.json` 徽章统计，不能写成检索或执行架构更新。今天的源码深读可增加阅读切面，但不制造项目新增功能；实际有新提交的应用和目录也需逐个核查内容，不能单靠时间戳归因热度。

Superpowers main 同样与昨日一致；VoiceStudio 相对昨日仅 ahead 4，三份 README 增加访问量徽章，没有功能源码变动（固定 compare 与 SHA 见正文）。因此连续七项中，今天没有经本次证据确认的功能源码增量，排名变化主要是榜单样本变化；这不是判断它们停止维护，近期活动仍需按原始日期理解。
