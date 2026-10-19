# GitHub Trending 源码深读｜2026-10-19

> 今日样本：GitHub Repositories · Daily / Today · All languages / Any · Any spoken language。严格按官方页面顺序前十；热度不是质量、安全性或许可证评级。

## 抓取口径、新鲜度与访问边界

- [官方 Trending Daily](https://github.com/trending?since=daily)直接公开 HTTP GET 于 **2026-10-19 10:17:38 北京时间（02:17:38 UTC）**取得 HTTP 200；响应 Date 为同秒 GMT。页面显示 Language: Any、Spoken Language: Any、Date range: Today。13 张仓库卡片中只取前十，不以搜索缓存或第三方榜单补位
- HTTP Date 表示响应时间，不证明 GitHub 后台在该秒重算；官方未给榜单生成时间。官方 stars today 窗口不等于北京时间零点起，也不等于两次总 stars 的差。语言是卡片主语言，不是完整技术栈；今天排序也不按显示的 today 数值单调递减
- 原始 HTML **606,637 bytes**，SHA-256 `bc0affca536d9805264bca604cf0f470cd792961f42497a933598072fbb3824b`。这是本次响应的校验标识，不声称官方历史榜单已有不可变存档
- 各仓源码在榜单后分别读取并固定完整 SHA，非跨仓原子快照。README/docs、目录、依赖、入口、核心实现、近期 commits/releases/issues 的真实覆盖逐项列明；读取部分文件不等于审计全部仓库。涉及测试仅静态读其设计，未运行陌生代码、安装依赖、调用模型或连接用户服务
- 匿名 GitHub API 遇共享限流时，改用已连接 GitHub 只读接口与官方 raw；Orca 树分拆读取补齐，compare 的300文件上限如实保留。闭源宿主、外部服务、模型权重、运行性能及热度归因不能由这次源码阅读证明
- 昨日基线已读取真实完整报告：[2026-10-18 固定归档](https://github.com/DanielMax937/daily-research-reports/blob/984ca83e701eb8e3a2e05606f08eaa5398be3f9f/2026-10-18/github-trending.md)。连续项目保留六项，压缩背景，强调真实 diff/新反馈；不把尚未合并的 PR、release 分支或未发版主干当正式发布
- 阅读收口为 **2026-10-19 10:30 北京时间附近**。本报告只包含公开资料与为你生成的分析，不包含账户信息、凭据、私人项目代码或实际个人会话

## 今日官方前十

| 排名 | 仓库 | Stars | stars today | 页面语言 |
|---:|---|---:|---:|---|
| 1 | [MadsLorentzen/ai-job-search](https://github.com/MadsLorentzen/ai-job-search) | 53,453 | +2,232 | Python |
| 2 | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | 42,751 | +1,175 | Python |
| 3 | [anomalyco/opencode](https://github.com/anomalyco/opencode) | 216,678 | +1,414 | TypeScript |
| 4 | [cursor/plugins](https://github.com/cursor/plugins) | 12,771 | +350 | TypeScript |
| 5 | [ruvnet/ruflo](https://github.com/ruvnet/ruflo) | 76,562 | +513 | TypeScript |
| 6 | [akitaonrails/ai-memory](https://github.com/akitaonrails/ai-memory) | 10,542 | +512 | Rust |
| 7 | [stablyai/orca](https://github.com/stablyai/orca) | 96,769 | +1,146 | TypeScript |
| 8 | [HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything) | 54,638 | +589 | Python |
| 9 | [debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio) | 75,550 | +2,082 | Python |
| 10 | [android/skills](https://github.com/android/skills) | 8,804 | +375 | Kotlin |

以下按官方顺序展开；重点是可定位的实现、边界和变化，而非排行榜简介。

## 1. MadsLorentzen/ai-job-search：今天看连接器契约和个性化 fork 的维护成本

### ① 排名、元数据与真实增量

官方今日第 **1**，**Python，53,453 stars，+2,232 stars today**。[仓库](https://github.com/MadsLorentzen/ai-job-search)默认分支 `master`，今日固定 SHA 为 **`0f6480d32e59d7651d920a5ec6d78ede2f4113bf`**，提交于 **2026-10-18 19:38:40 UTC**；许可证 [MIT](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/LICENSE)。与昨日 `5d9e0977f01465166f25abf0826bd61e7c8cac25` 的[官方 compare](https://github.com/MadsLorentzen/ai-job-search/compare/5d9e0977f01465166f25abf0826bd61e7c8cac25...0f6480d32e59d7651d920a5ec6d78ede2f4113bf)相较，提交图前进 **27 个 commits、68 个文件变化**，并非原地涨星。最新 release 仍是 **[v1.7.2（9 月 29 日）](https://github.com/MadsLorentzen/ai-job-search/releases/tag/v1.7.2)**；本文的新修复属于默认分支，不能说发布版已经包含。

今日完整递归树为 **335 条目、270 文件，未截断**。连续项目不重讲昨天的 rank 状态机和 PDF 验收，转向今天真正变化的三个切面：获取数据时是否真的省成本、参数错误是否会伪装成有效结果、用户改过的 fork 如何继续更新。

### ② 它解决什么问题，怎么使用

这是把 Claude Code 组织成求职工作流的模板：整理事实履历 → 多门户查岗位 → 筛选/评分 → 起草 CV 与求职信 → 独立 reviewer 检查 → 生成 PDF 和归档。它的主入口是 Markdown commands/skills；Python 做确定性状态、校验与维护，Bun/TypeScript 做门户 CLI，LaTeX 负责交付。`/apply` 产出申请材料，不能仅凭命令名理解成已经替用户向雇主投递。[README 工作流与入口](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/README.md#L40-L67) · [apply 指令](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.claude/commands/apply.md)

适合把求职当成持续、有资料积累的项目来做的人，而非只需要一次简历润色的人。通用工作流可以换语言和市场，但丹麦门户适配、Bun/Python/TeX 环境和实际 agent 账户仍是采用成本。新增门户不能只改 prompt，必须兑现搜索参数、详情 URL、日期、错误码等数据契约。

### ③ 架构与三个新机制切面

**总体结构。** `.claude/commands` 编排任务，`.agents/skills/*/cli` 负责外部来源，`tools` 处理状态/文档/安全与升级检查，`tests` 对这些契约做回归。今日重点读取的 Freehire CLI 入口为 `src/cli.ts`，清单明确 **零运行时依赖**，只靠 Bun/fetch；TypeScript 和 Bun types 是开发依赖。这与使用 Bunli/Zod 的其他门户并不相同，不能给所有 adapter 套同一依赖描述。[Freehire package](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.agents/skills/freehire-search/cli/package.json)

1. **“少给模型正文”现在也改变取数端点，而不只是拿完再扔。** 默认搜索仍调用 `/api/v1/agent/jobs/search` 获取完整岗位说明；`--no-description` 则改走 `/api/v1/jobs/search`，随后把结果的 description 置 null，连短预览也不进入模型上下文。query builder 不再发送维护者指出服务端不读取的 `semantic_ratio`、`include_description` 参数；仅在请求正文时发送 `description_format`。代码可确认的是端点选择、参数和输出收缩；“避免服务端逐项读取完整正文”是维护者对 API 的解释，本次没有审计 Freehire 服务端或测量省了多少流量/时间。搜索端点 404 仍返回 `SEARCH_FAILED`，而不是把配置不兼容伪装成“没有岗位”。[搜索实现](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.agents/skills/freehire-search/cli/src/commands/search.ts#L3-L68) · [分支与输出](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.agents/skills/freehire-search/cli/src/commands/search.ts#L113-L153) · [本次提交](https://github.com/MadsLorentzen/ai-job-search/commit/0f6480d32e59d7651d920a5ec6d78ede2f4113bf)

2. **错误参数必须在联网前失败，不能悄悄放宽搜索。** 新入口对 query/company/country/region/city/seniority/category/skill/description-format 检查“出现但缺值、空串、纯空白”，统一 `BAD_ARG` 与非零退出。测试启动本地 stub，除检查退出码和错误正文，还断言请求数组为空；正向样例核对重复 country/skill 参数和 lean endpoint。这是 agent 工具的重要契约：空结果、合法无过滤搜索、非法参数是三件事。输出也新增 `contractDate`，把 ISO 时间戳的 `YYYY-MM-DD` 前缀归一到其他门户的日期形状；这只是格式提取，不是完整日期有效性或时区转换。User-Agent 则从标识 API 自身改成标识本项目，方便服务运营者联系调用方。[参数预检](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.agents/skills/freehire-search/cli/src/cli.ts#L172-L188) · [联网前拒绝的回归测试](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.agents/skills/freehire-search/cli/tests/required-search-values.test.ts#L4-L78) · [日期映射与 UA](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.agents/skills/freehire-search/cli/src/helpers.ts#L159-L185)

3. **个性化 fork 的升级判断开始区分“你删过的功能”和“上游新增的功能”。** `upstream_triage.py` 先用稳定 patch-id 或相同 commit subject 识别可能已 cherry-pick 的改动，再用 merge-base 判断路径是否原本存在：本地缺失、共同基线也没有的路径是上游新增，应提示审查；基线有而本地没有，则可能是 fork 主动删掉的功能。没有共同基线时不擅自推断删除。只剩 CHANGELOG 相关的变化会降级，建议的 cherry-pick 按依赖方向输出；脚本自己不 merge/push/改文件。配套 `check_upstream_updates.py` 对缺失上游文件/读取失败显示 incomplete，避免最终误报“全部最新”，交叉命令也保留用户选定 remote/branch。[相关性与已应用判断](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/tools/upstream_triage.py#L150-L191) · [只报告、祖先优先的建议](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/tools/upstream_triage.py#L193-L219) · [不完整检查不能报 OK](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/tools/check_upstream_updates.py#L130-L194)

这个第三点也有诚实边界：相同 subject 只是启发式，不证明 patch 相同；“路径本地缺失”也不能理解用户的全部意图。今日仍开放的 [#656](https://github.com/MadsLorentzen/ai-job-search/pull/656)进一步处理“上游在 fork 已删目录里新增文件”的情形，不能把未来提案算进当前算法。

### ④ 亮点、风险与尚未闭环的问题

今天的亮点是把“模型工作流维护”落到工具实际输入输出和 Git 变更语义。另一个具体修补是 `.gitignore` 从 `node_modules/` 改成 `node_modules`，覆盖同名符号链接/普通文件；新 guard 使用 Git tracked 路径检查，拒绝任何带 node_modules 路径组件的已跟踪项，避免贡献者本机依赖链接进入模板。它仍是审查/CI 检查，不是运行时沙箱。[guard 实现](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/tools/security_guards.py#L283-L315)

昨日提到的两个问题仍未闭环：[#622](https://github.com/MadsLorentzen/ai-job-search/issues/622)仍 open，当前 `normalizeSlug` 仍直接从任意输入匹配 `/jobs/…`，没有检查 host；因此雇主 URL 可能被误当 Freehire slug。另 [#616](https://github.com/MadsLorentzen/ai-job-search/issues/616)关于 `--region us` 的问题仍 open；合法非空不代表语义合法，今天增加的空值预检没有解决这个层次。[当前 slug 提取](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.agents/skills/freehire-search/cli/src/helpers.ts#L249-L257)

新 [#655](https://github.com/MadsLorentzen/ai-job-search/issues/655)报告 Windows Git Bash 把 Git 自带、不支持 bbox 的 xpdf `pdftotext` 排在已安装 Poppler 前面，使布局检查返回 skipped/exit 2。报告者给出了两个 shell 的对照和复现环境，本次没有独立执行；它提醒“系统装了依赖”和“agent 的 PATH 真正调用对了依赖”不同，skipped 不能当验证通过。

隐私边界不变：真实 profile 会写进部分 tracked 文件，README 明确建议实际求职使用私有仓库；岗位正文是不可信输入，工作流中的反注入说明不提供 OS 隔离。[隐私和输入边界](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/README.md#L80-L136)

### ⑤ 近期活动与热度：可核事实和推断

**事实：**今日 +2,232，27 个新 commits 涉及门户参数/日期/段落保留、Unicode 薪资数据、reset、框架升级检查与依赖路径 guard；最近发布版没有变化。开放提案 [#632](https://github.com/MadsLorentzen/ai-job-search/pull/632)才准备让 Freehire 尊重 Retry-After；当前 helper 仍以固定指数退避加 jitter 重试 429/5xx，不能把该提案写成已实现。[当前重试](https://github.com/MadsLorentzen/ai-job-search/blob/0f6480d32e59d7651d920a5ec6d78ede2f4113bf/.agents/skills/freehire-search/cli/src/helpers.ts#L32-L78)

**推断：**可直接产出求职材料、持有本地文件、逐步修复真实使用反馈，可能让项目持续获得关注；但没有足够公开证据把今日涨星归因于这批补丁、某次视频或作者个人求职故事。README 的个人求职转化经历不构成本项目普遍效果的实验数据。

### ⑥ 对你的技术方向的价值

- **AI agents/coding agents：高。** 最值得移植的是“空结果≠参数错误≠依赖缺失”和先粗筛、后取正文的两段获取流程，适用于招聘、采购、商机与研究 agent
- **RAG：中。** 这里不是向量库框架，但 lean/full 模式和可追溯原文教的是上下文预算与取数成本；省 token 应看数据源、网络、模型输入三个层次
- **MCP：局部。** 核心门户是 CLI；Notion/Gmail 是外接能力。要包装成 MCP，仍应保留严格参数 schema、错误码和 source 身份，而不是只把 CLI 输出塞进文本
- **Node/Python/Django：高方法价值。** Bun adapter 与 Python 校验的边界容易移植；个性化模板/客户定制版本可借鉴基于 merge-base 的升级报告，但启发式结果仍需人工审查
- **React/Next：低直接复用。** 本仓不是前端应用模板，可作为你的 UI 背后垂直 agent 流程样本

**今日阅读边界：**README 相关工作流/安装/隐私章节、完整目录树、Freehire skill/package/CLI/search/helpers 与相关测试；apply 入口、upstream triage/version 检查、安全 guard；官方 27-commit compare、最近 12 commits、4 releases、25 条更新中的 issue/PR，以及 #616/#622/#655 正文。下载的其他变更文件不等于逐行审计；未安装、运行门户 CLI、访问求职服务或执行测试。

## 2. anthropics/claude-plugins-official

### ① 排名、元数据与版本锚点
官方第 **2**；**42,751 stars，+1,175 stars today，Python**。今天重新读取的 main 仍为 **ea10b213686c90bb1984b2016937310e05336cf3**（10 月 16 日 02:40:21 UTC），与昨天完整报告相同，**没有默认分支源码增量**。递归树 817 条目且未截断；release 列表仍为空。这里是插件目录，不是统一版本的 Python 应用。[marketplace](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/.claude-plugin/marketplace.json)依旧包含本地插件与外部 source，外部服务的实现、许可和权限不能由目录背书。今天深读的 [session-report 许可证](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/session-report/LICENSE)为 Apache-2.0，不能推广给所有条目。

### ② 它解决的实际问题
昨天已读 Hookify 的事件规则；今天换一个实际问题：**大量 coding-agent 会话的 token 花在哪里，怎样避免把拆分输出、重放历史和子代理活动重复计算？** session-report 用 Node 分析本地 JSONL，再由 skill 将数据装入 HTML 模板、补充自然语言发现。它是使用情况分析工具，不是账单核对 API，也不是一个真正测量“任务价值”的评估器。[SKILL 工作流](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/session-report/skills/session-report/SKILL.md)

适合维护编码工作流、怀疑上下文或后台任务成本失控的人；相比让模型直接读全部聊天，先用确定性程序做聚合更可控。此处仅阅读公开程序，没有读取用户的实际会话目录或生成其使用报告。

### ③ 架构、入口与三个实现机制
**入口和依赖。** skill 指示运行同目录 `analyze-sessions.mjs --json --since 7d`，读取 JSON，复制 template.html，再编辑数据和 findings。分析器只用 Node 的 fs/os/path/readline，无独立 npm 服务依赖；输入目录可由 --dir 指定，默认是宿主 Claude 的 projects 目录。数据路径是 JSONL→去重/归因→多层聚合 JSON→HTML，叙述性建议由 agent 另外写入，不是分析器计算结果。[分析器](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/session-report/skills/session-report/analyze-sessions.mjs#L1-L190)

1. **两层去重避免把内容块当 API 请求。** `processFile` 流式读取 UTF-8 JSONL，损坏 JSON 行跳过；先用全局 entry UUID 防恢复会话重复，再在文件内按 requestId / message.id 合并分拆的 assistant 内容块，保留 output_tokens 最大的 usage，最后用全局 request ID 集合避免跨文件重复记账。主会话先处理，子代理按 birthtime 排序，以便父会话先建立 tool_use→agentId→prompt 的对应。这个实现确实处理了常见的重复计费统计假象，但依赖日志字段和排序约定，不能据此保证所有未来宿主格式都正确。[读取与使用量结算](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/session-report/skills/session-report/analyze-sessions.mjs#L191-L418)、[文件处理顺序](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/session-report/skills/session-report/analyze-sessions.mjs#L535-L598)
2. **子代理与 skill 归因来自事件连接，不是每个文件孤立求和。** Agent/Task 的 tool_use 记录类型及当前 prompt，tool_result 再提供 agentId；子代理文件继承其发起 prompt，并把 token 汇总回项目和整体。skill 调用则改变当前归因标签。这里最容易误读的数字是 `subagent.calls`：源码在每个有范围内内容的子代理文件结尾只加一次，**实际是子代理运行/文件计数，不是子代理中的 API 调用次数**；同一 JSON 又有真正的 api_calls。求平均时分母选错，会把“每次运行 tokens”误写成“每次模型请求 tokens”。[计数和输出字段](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/session-report/skills/session-report/analyze-sessions.mjs#L409-L418)、[summarize](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/session-report/skills/session-report/analyze-sessions.mjs#L616-L649)
3. **明细截断和总体指标不是同一口径。** cache break 的定义是单次 input_uncached+cache_create 超阈值，默认 100,000；它不是自动识别缓存失效根因。JSON 将明细按 uncached 排序后只留前 100 条，却没有标明截断，也没有输出全部 cache-break 的 uncached 总和；overall 只保留完整事件数量。因此对明细求和可能少算，但不能进一步把这些 token 都算成可节约的美元成本。`buildByDay` 又把跨午夜会话全部 tokens 归到本地首条消息那天，时间图不是逐请求的自然日账单。[截断与日期归桶](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/session-report/skills/session-report/analyze-sessions.mjs#L651-L720)

### ④ 技术亮点与边界
亮点是先保留可重复计算的 JSON，再用模板渲染、让 agent 做解释；对大量 trace 的去重和父子归因也比简单累加日志成熟。今天的 [issue #6786](https://github.com/anthropics/claude-plugins-official/issues/6786)指出前述截断、calls 命名及叙述排名问题：前两项已在当前源码确认，报告者具体的 7 天 token 数没有独立复算；“最大可回收成本”的判定也没有在代码里强制验算。

另外，active time 是相邻事件间隔小于五分钟才相加，wall-clock 是各文件跨度相加；并行子代理下它们不等于人的工作时长。提示预览、项目名和会话上下文会进入 HTML JSON，分享生成报告前需检查敏感信息。模板可交互不意味着材料已脱敏，token 总量也不直接等于费用，缓存读/写、模型单价和套餐计费仍有区别。

昨天 Hookify 的问题没有因今日关注转向而消失。今天更新的 [#6339](https://github.com/anthropics/claude-plugins-official/issues/6339)指出 cwd 漂移后规则消失；当前 [load_rules](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/core/config_loader.py)确实用相对 `.claude/hookify.*.local.md` glob，而非固定项目根。静态代码证实路径依赖，具体宿主切目录复现来自用户报告，本次未执行。

### ⑤ 近期活动与热度：事实、推断分开
**事实：**今日从第 1 降到第 2，仍显示 +1,175；最近 main 提交仍是外部插件 SHA 更新，release 为空。新 [#6796](https://github.com/anthropics/claude-plugins-official/issues/6796)希望 Playwright 配置通过 userConfig 暴露；当前 [.mcp.json](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/external_plugins/playwright/.mcp.json)确实是 npx + `@playwright/mcp@latest`，[manifest](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/external_plugins/playwright/.claude-plugin/plugin.json)没有该选项。这里的 @latest 是外部依赖解析，不受本仓固定 SHA 完全锁定，未读取外部 MCP 的具体版本实现。

**推断：**插件分发、使用分析和浏览器连接的实用性可能延续关注，但新 issue 只证明需求和反馈存在。**暂无足够公开证据解释今日热度**，没有把未更新的代码描述成今天发布，也没有将 issue 中的安装链接或未知命令当作可信来源执行。

### ⑥ 对你的工程价值
对 **AI/coding agents**，session-report 最值得学的是去重、父子归因和明细/总量分层；最该补的是指标单位、截断标志、总量校验与“结论必须由数据支持”的验收。对 **RAG**，这是 trace 的结构化归因，不是向量检索；原始证据和派生摘要应分开。对 **MCP**，安装目录、运行参数和实际服务版本要分别锁定。对 **React/Next/Node**，可借鉴分析器→JSON→可交互报表，但应由代码生成关键百分比和排序，避免模型手填；对 **Python/Django**，同样适用于任务审计与管理看板，不要把并行 worker 时长之和显示成用户在线时长。

**实际阅读覆盖：**根 README、完整树、marketplace；session-report SKILL/LICENSE、分析器文件发现/流式读取/去重/归因/汇总/JSON/日期段，HTML 模板结构；Hookify 当前入口、配置加载与 hook 注册；Playwright 两份配置；12 commits、空 releases、15 条按更新时间 issues/PR，以及 #6339/#6786/#6796 完整正文。没有运行分析器、读取真实会话、审计所有外部插件，未把昨日已读内容当作今天新功能。

## 3. anomalyco/opencode

### ① 排名、元数据与源码锚点
官方第 **3**；**216,678 stars，+1,414 stars today，TypeScript，MIT**。[仓库](https://github.com/anomalyco/opencode)默认分支是 **dev，不是 main**；本次固定 **8c9c85c26304bf17694125aabacf546da19cc9e6**（10 月 19 日 02:10:01 UTC），完整树 9,502 条目、未截断。[根 package](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/package.json)及 core/cli/app/desktop 均为 **2.0.32**，workspace 采用 Bun 1.4.2。[GitHub release 列表](https://github.com/anomalyco/opencode/releases)本次最新返回的是 10 月 16 日的 **v1.19.3**；这与 dev 的 V2 代码是不同版本通道，不能拿 V1 release 说明给 V2 源码背书，也未额外核 npm 当前分发内容。

### ② 它解决的实际问题
OpenCode 提供可读、可扩展的 coding-agent 运行时：同一个工作目录、会话、工具、权限和 provider 逻辑，可以通过终端、桌面和 API 使用。与只提供一组提示或封闭客户端不同，本次确实能读到会话循环、工具执行、权限等待与失败恢复的核心代码。

对用户最现实的问题是：模型输出到一半断了，工具是否已经执行？同一会话同时收到两个继续请求，是否开两条互相覆盖的循环？用户拒绝一个工具，系统是停止还是把拒绝当一般工具错误再尝试？这些问题比换一个 UI 更决定 coding agent 是否可靠。[README](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/README.md)已有 build/plan/general 等入口说明，但下面以真实 V2 实现为准。

### ③ 架构、入口与三条关键机制
**实际结构。** `packages/cli` 处理命令和进程；`packages/core` 提供 Effect 服务、session/tool/permission/provider/MCP；`packages/server` 提供服务入口，client/schema/protocol 分包；app 是 SolidJS/Vite，desktop 是 Electron 44 的封装，**不是 React/Next，也不是此版本的 Tauri 架构**。core 采用 Effect、Drizzle、SQLite 适配层、模型提供商库和 MCP client/core 2.0.0；不同 runtime 的 sqlite/pty 实现由 package imports 条件选择。[CLI 入口](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/cli/src/index.ts)、[core 依赖与适配](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/package.json)、[桌面 package](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/desktop/package.json)

请求经 CLI/server 进入 location/session 服务，选模型并准备工具 schema，runner 消费 provider 流，工具事件进入发布器后才启动本地执行，工具结果与终态再送回会话。SQLite/Drizzle 保存 session/message 等数据；UI 订阅事件而不直接拥有工具执行循环。以下三个切面构成这个数据流的可靠性骨架。

1. **每会话串行，清理与新工作明确分界。** [run-coordinator.ts](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/session/run-coordinator.ts)用 Map<Key, Execution> 保证同 key 只有一段 busy period，不同 key 可并行；run 加入当前 Deferred，而 wake 设置可合并的 pendingWake“门铃”。drain 最后一次检查与变为空闲之间收到的 wake 不会消失：settle 看见它就开 successor。中断清掉旧意图已经登记的 wake，但清理期间新到的 wake 被视为新工作；interrupt 默认只确认已接受中断，awaitSettlement 等这一轮清理，awaitIdle 还追随 successor。这样调用方可以明确区分“停止请求已收到”与“资源真正释放”，而非一个 cancelled 布尔值。[回归测试](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/test/session-run-coordinator.test.ts)覆盖 join、合并 wake、settlement 窗口、清理期间新工作与错误释放；本次只读未执行。
2. **流式失败后，是否已有持久输出决定重试方式。** [step.ts](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/session/runner/step.ts#L70-L280)将 provider 流与工具 fiber 分开，但本地工具只有在 Tool.Called 发布完成后才启动；结束时等工具并补齐未结算调用。上下文溢出只在没有 outputStarted 时进入压缩恢复；未产生输出的可重试错误走 Retry，有输出后的断流则走 Continue，而不是一概从头重发。若用户拒绝或工具被中断，不进入这条继续重试路径。provider 已执行的 tool-call 不会再交给本地执行。这里不是“副作用绝对一次”的证明，却确实减少把有副作用的部分执行当成空请求重放的机会。

[model-retry.ts](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/model-retry.ts)还限制普通指数退避次数、每段基础等待与 jitter，provider 的 retry-after 封顶 15 分钟，timeout 最多允许三次重试；[session retry hook](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/session/runner/retry.ts)会把计划重试时间发事件并等待，但插件可以调整决定和 delay。因此默认上限不能被宣传为包含任意插件后仍不可改变的全局硬期限。
3. **权限结果不仅控制返回值，还控制并行步骤的命运。** [permission.ts](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/permission.ts#L91-L325)采用 last-matching rule；先检查 agent/session 的显式 deny，命中即返回，不让 saved allow 或 evaluate hook 覆盖它。缺失 agent 权限用 deny-all；其余结合项目范围的 saved allow，未决资源 ask，再由 Deferred 等答复。拒绝一项会拒绝同 session 其他 pending asks；带反馈拒绝成为 CorrectedError，可向模型解释并继续，不带反馈的 DeclinedError 则通过专门错误路径防止被通用工具 mapError 吞成普通文本后继续重试。

选择 always 时保存的不是任意请求原文，而是该请求声明可保存的 action/resources；后续 pending 项要重新 evaluate 才获允许。[saved.ts](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/permission/saved.ts)目前提供 list/add/remove，数据库按 project 分隔。这仍是应用层策略，不能直接等同 OS 沙箱或证明每一个插件都没有旁路执行能力。

### ④ 技术亮点与边界
亮点在于 **execution ownership、事件完成、模型恢复、人工拒绝各有独立契约**。对未知插件错误，[tool/runtime.ts](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/tool/runtime.ts#L31-L97)统一包装为 Tool.Error，防止调用永远悬而未决；同时验证声明的 output schema，缺 output 不能假装成功。输入 JSON schema 无法转换成 codec 时存在返回原值的 fallback，所以“所有 schema 都强校验”也不是准确描述。

MCP 是独立的 location-scoped 连接服务，维护工具、资源、认证及服务状态；远端相同 endpoint 的启动用 keyed mutex 减少并发连接突发。[MCP 状态与连接范围](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/mcp/index.ts#L78-L104)也表明它不是一个只把 MCP JSON 塞进 prompt 的轻封装。本次未完整审计 OAuth、所有传输重连和全部工具权限；工作目录与会话隔离不能直接推导为多租户服务安全。

V2 的 Effect 分层可读性与学习成本并存；Bun/Node/workerd 条件适配、原生 pty、Electron 和模型提供商都引入环境差异。今天的 release 信息又跨 V1/V2，采用时必须锁定通道、插件接口与安装产物，不能仅看 stars 或 package 名相同。

### ⑤ 近期活动与热度：事实、推断分开
**事实：**今日新进前十第 3，昨天实际页为第 11。最新 [提交 8c9c85c](https://github.com/anomalyco/opencode/commit/8c9c85c26304bf17694125aabacf546da19cc9e6)仅为被策略移除且原本 enabled 的 provider 增加 debug 日志，避免 deny-all 输出整个模型目录；它不是新发明了 provider policy。10 月 18 日 [README 更新](https://github.com/anomalyco/opencode/commit/501b15af26915ba52682e20e220e7e137e89e92f)将推荐安装指向 V2，是可以核实的入口变化。

开放 [PR #56659](https://github.com/anomalyco/opencode/pull/56659)提议允许编辑 saved permissions；当前实现只有 list/add/remove，不能把提案写成已可用。新 [#56921](https://github.com/anomalyco/opencode/issues/56921)请求 TUI 图片预览及 computer-use，这只是需求，不是本次确认的内置能力。按更新时间列表里还有一批旧问题被关闭，关闭不自动证明全部已修复，更不能当作今天新发现的故障。

**推断：**V2 的分层运行时、开放核心实现与多端入口可能增加开发者关注；但没有取得将某条提交、宣传或 release 与今日 +1,414 直接关联的证据。**暂无足够公开证据解释今日热度。**

### ⑥ 对你的技术方向的价值
对 **coding agents/AI Agent**，优先读 run-coordinator 和 step：这是把“继续、停止、重试、终态”写成可测试状态的具体案例。对 **MCP**，可借鉴连接归属、认证状态和工具 schema 接入，但新协议与旧服务器兼容须实际验证。对 **RAG**，这里主要是会话上下文和代码工具循环，不是一个现成向量检索引擎；你可把自己的检索工具作为结构化输入来源，保留权限和结果错误通道。

对 **Node/TypeScript**，Effect/Deferred/fiber 与 SQLite 数据层有直接阅读价值；对 **React/Next**，可借鉴事件驱动控制台和跨端 client，但现行 UI 是 Solid。对 **Python/Django**，可迁移同 session 串行、取消后的资源结算、拒绝与失败分型，而不必照搬 TS 框架；通过 API 集成时仍应把业务授权放在自己的服务边界。

**阅读覆盖：**根 README/LICENSE、根及 core/cli/server/app/desktop manifests、完整树；CLI 和 serve 入口；run-coordinator 全文及重点回归测试；runner index/step/retry、model-retry；permission/saved 全文及部分测试；tool/runtime 前置输入输出契约；session store 与 MCP 连接/状态相关段；近期 12 commits、5 releases、15 issue/PR，最新提交完整 patch。其余提供商、UI、数据库迁移和 MCP 全传输实现未全面审计；没有安装、运行程序或测试。

## 4. cursor/plugins

### ① 排名、元数据与版本锚点
官方第 **4**；**12,771 stars，+350 stars today，TypeScript**。默认分支本次锚点 **6b78e9f4e46c75d1697d837e51f07c2692e60b24**（10 月 19 日 01:51:15 UTC），完整树 1,774 条且未截断，release 列表为空。它是 **插件市场、agent skills 与跨宿主适配资源仓库**，并非 TypeScript 写成的 Cursor 编辑器。pstack [manifest](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/pstack/.cursor-plugin/plugin.json)为 0.15.27，声明 MIT；各第三方插件有各自版本及许可。昨天实际 13 条榜单里没有它；与 10 月 17 日已读 SHA 的比较只能称跨两日报告比较，不能称昨日源码差分。

### ② 它解决的实际问题
让编码代理拥有可复用的审查、设计、验证流程，同时避免同一套 skill 在 Cursor 和 Claude Code 各自手工维护而漂移。今天最具体的改动是“生成形式化验证 skill”：将高风险并发/状态机问题绑定到真实代码和可复验命令；此外新增 Meta Ads 远程 MCP 的分发配置。两者都是接入与流程层，仓库没有提供编辑器内核、形式化求解器或广告服务实现。

### ③ 架构、数据流与真实实现
入口是 [.cursor-plugin/marketplace.json](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/.cursor-plugin/marketplace.json)的 source→每项 plugin.json→skills/MCP 配置。pstack 的源内容在 `pstack/`，Claude Code 分发副本在 `harness/pstack/claude-code/`。实际可执行的核心是 Node 构建与校验脚本，不是所有 Markdown 背后都有独立程序。

1. **单一内容源→确定性宿主适配→提交物一致性检查。** [generate-pstack-harness-trees.mjs](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/scripts/generate-pstack-harness-trees.mjs)只用 Node 标准库，枚举 skills/agents/guide 等白名单树，核 skill 目录名与 frontmatter name 一致，识别 Cursor 特有的 Task、AskQuestion、环境及模型用法；包含这些术语的技能必须有可插入适配提示的 H1，adapter 文档也必须覆盖检测到的术语。它复制源文件及可执行位，并在需要的技能标题后加“读取适配说明”的提示。输出放在 pstack 之外，避免 Cursor 安装原始包时顺带读到重复技能。`--check` 比较预期字节、磁盘字节及执行位，发现漂移退出失败；不是重新调用 LLM 生成一份近似文档。
2. **验证提示要求“能失败”，但还不是已完成的证明。** 今日 [create-formal-verification-skill](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/pstack/skills/create-formal-verification-skill/SKILL.md)把问题分成顺序/并发模型与代码本身性质：前者默认 TLA+，后者优先对实际语言运行 verifier；不存在合适工具时明确承认，并对真实代码做生成式性质测试，不能拿手写函数模型替代。模型原子步骤必须映射代码原子步骤，性质要用故意破坏的版本展示反例，发现当前代码错误不能降低性质使其通过；最后要求在真实破坏性 scratch 变更上走一遍生成 skill，未运行只能交草稿。这些是给代理的工作规约，仓库不会自动证明代理遵守了它，也没有一键证明所有项目的能力。
3. **分发校验与文档校验职责分离。** [validate-plugins.mjs](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/scripts/validate-plugins.mjs)借 AJV/ajv-formats 核 Cursor marketplace/plugin JSON schema、source 目录、manifest 名字及跨宿主版本一致性；Claude marketplace 分支检查存在性/名字，不能概括成与 Cursor 完全同等 schema 验证。[check-pstack-docs.mjs](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/scripts/check-pstack-docs.mjs)从目录枚举 skill/playbook/agent，对文档中的数量、命令、相对链接/锚点和模型名做交叉检查，并将宿主内置命令列为显式白名单。不过当前 [CI workflow](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/.github/workflows/validate-plugins.yml)只运行插件校验与生成树 `--check`，没有调用该 docs checker；“脚本存在”不等于“每次 PR 必跑”。本次只读，未运行这些脚本。

### ④ 技术亮点与边界
可借鉴的是把跨宿主 prompt 资产当构建产物管理：内容源、适配规则、生成副本、漂移检测相互分离。生成器还会把未纳入副本的 assets/automations 相对链接改为 GitHub `main` 链接，因此固定插件 commit 不代表这些外链目标也固定；对严格复验的团队，应进一步使用版本化链接。

新增 [Meta Ads mcp.json](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/third_party/meta-ads/mcp.json)只是 HTTP 远程端点与公开客户端 ID；[manifest](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/third_party/meta-ads/.cursor-plugin/plugin.json)要求 Cursor 3.13.0，版本 1.0.0；没有把 secret 放在仓库中。[README](https://github.com/cursor/plugins/blob/6b78e9f4e46c75d1697d837e51f07c2692e60b24/third_party/meta-ads/README.md)明确服务仍 beta、按广告账号和工具开放，可以创建广告及修改预算，工具名/schema 以远程服务为准。已合并 [PR #720](https://github.com/cursor/plugins/pull/720)还说明当时 Meta 应用处于 development mode，只允许有 app role 的用户登录；这只是提交时说明，本次没有登录核实时服务是否已开放。不能将“市场已收录”解释为“所有用户即可用”，更不能将接入许可当预算操作许可。

### ⑤ 近期活动与热度：事实、推断分开
**事实：**今日 head 直接修改形式化验证 skill 的工具选择；近日合并 Meta Ads 和 Zoom 登录配置文案更正。[commit](https://github.com/cursor/plugins/commit/6b78e9f4e46c75d1697d837e51f07c2692e60b24)不是运行时 solver 更新。按更新时间读取的 [PR #716](https://github.com/cursor/plugins/pull/716)提出维护已有验证 skill，[#723](https://github.com/cursor/plugins/pull/723)提出 scope/grounding 审查，[#722](https://github.com/cursor/plugins/pull/722)提出外部调用超时/重试边界，抓取时均 open，不能写成已有功能。与 10 月 17 日报告锚点的 compare 为 ahead 24；它不是昨天前十项目，昨天没有逐仓源码基线。

**推断：**验证规约与商业 MCP 集成扩展可能增加实际使用需求，但没有曝光、安装或流量归因证据。**暂无足够公开证据解释今日 +350 的原因**；不能因为今天新增广告连接就断言它带动上榜。

### ⑥ 对你的工程价值
对 **coding agents**，最值得复制的是“代码对应、可失败、受限范围、复验命令”四项验收，以及内容生成树的 byte-for-byte 检查。对 **MCP**，必须同时检查客户端最低版本、远程服务开通状态、OAuth 权限和具体写操作确认。对 **RAG**，skill 是可维护的操作知识，不等同检索或记忆系统；发布时可将技能版本/来源作为检索元数据。对 **React/Next/Node/Python/Django**，可以把关键异步任务、支付回调幂等、状态转换挑成小范围验证对象；不要要求代理证明整套 Web 应用，更不要将模型层证明直接推广到数据库隔离、网络和部署。

**实际阅读覆盖：**根 README、完整树、marketplace、pstack README/manifest、源及生成版 formal skill、生成脚本全篇、插件校验及 docs checker 全篇、CI workflow、Meta Ads manifest/MCP/README、12 commits、空 releases、15 条最新更新 issues/PR。没有运行验证器、安装插件、授权广告账户；远程服务实现和运行可用性不在本次覆盖内。

## 5. ruvnet/ruflo

### ① 排名、元数据与版本锚点
官方第 **5**；**76,562 stars，+513 stars today，TypeScript**。已读 SHA **b93144803bb171b12993b715fe7b2dd936b6edd5**，10 月 18 日 00:47:54 UTC；完整树 9,703 条且未截断。根与 CLI [package.json](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/v3/@claude-flow/cli/package.json)为 **3.57.0**，本次最近 release [v3.57.0](https://github.com/ruvnet/ruflo/releases/tag/v3.57.0)发布于 10 月 17 日 22:38:55 UTC。昨日榜上是第 12，未入前十深读；今天不能伪造它与昨日“逐模块比较”。最近四个默认分支提交集中在下载统计徽章/文档，不能当新 runtime 功能。

### ② 它解决的实际问题
Ruflo 将多代理工作、MCP 工具、策略与记忆组织到 CLI/服务中。今天不复述大而全能力表，聚焦三个落地问题：初始化不能悄悄放宽用户权限；监听 localhost 的 MCP 也可能被恶意网页访问；审计账本若把锚点和数据放在同一可改文件里，删除历史仍可能自证“校验成功”。这些问题比代理数量和宣传性能数字更影响可部署性。

### ③ 架构、数据流与真实实现
根 [bin/cli.js](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/bin/cli.js)将调用代理给 `v3/@claude-flow/cli/bin/cli.js`。CLI 依赖内部 security/shared/mcp/memory/codex 包、Zod/AJV、Express、sql.js 等；其中 [MCP bridge package](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/ruflo/src/mcp-bridge/package.json)是独立 Node≥20、Express 模块，不能混同所有 MCP server。本文深读其 HTTP guard、Codex initializer 与 CLI policy services。

1. **初始化的“默认权限”与“已有配置”分开处理。** [initializer.ts](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/v3/@claude-flow/codex/src/initializer.ts)中 trust 解析顺序为显式参数→`RUFLO_CODEX_TRUST`→standard；未知值退回 standard 并警告。新建 `.codex/config.toml` 时 standard 产生 workspace-write、on-request、cached；full 才产生 danger-full-access、never、live。已有 `.codex/config.toml` 即使 `--force` 也保留，只对检测到的宽松值提醒。由此避免工具升级覆盖用户审批选择。该实现还把安装 hooks 与已获 trust 区分，安装后提示用户审阅，不将存在文件等同已激活。边界：已有宽松配置不会自动收紧，环境显式 full 仍可能扩大权限；这是一套配置生成规则，不是 Ruflo 自己实现的 OS 沙箱。
2. **CORS 之外先挡不可信 Host/Origin。** [bridge index.js](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/ruflo/src/mcp-bridge/index.js#L889-L961)在 CORS 中间件之前调用 localBrowserGuard。当未设 `MCP_AUTH_TOKEN`，Host 必须解析为 localhost/127.0.0.1/IPv6 loopback或 `.localhost`；若有 Origin，则必须同样是 loopback，或精确匹配非通配 allowlist。这样即便跨源简单 POST 不需 preflight，也会在 handler 前被拒绝；非 loopback Host 针对 DNS rebinding。设置 token 后跳过这一 guard，交给 bearer 比较处理；health 是认证例外。仓库 [wire-level 测试](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/ruflo/src/mcp-bridge/test-local-browser-guard.mjs)覆盖原生无 Origin、外国 Origin、preflight、伪 Host、本地 Origin、allowlist与 token 模式，但本次未执行，不能称独立测试通过。允许任意本地 Origin也不是每个本地应用的身份认证。
3. **独立锚点＋按快照边界流式重放，而不是只给 state.json 自身算 hash。** [policy-ledger-anchor.ts](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/v3/@claude-flow/cli/src/services/policy-ledger-anchor.ts)把 append-only anchor chain 放在项目文件，另将头镜像放到项目之外的用户配置目录；项目真实路径 hash 用来隔离镜像。校验状态与日志/镜像的长度、头 hash、归档边界，回滚或缺失不能只改 state 文件蒙混过关。重要限制是默认路径仅核归档 tip，不能发现不改变 tip 的归档内部修改，必须 `--full`。[policy-runtime.ts](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/v3/@claude-flow/cli/src/services/policy-runtime.ts#L681-L721)在 writer lock 内捕获已核状态及归档 FD/字节上限，释放锁后做完整历史核验。[policy-ledger-audit.ts](https://github.com/ruvnet/ruflo/blob/b93144803bb171b12993b715fe7b2dd936b6edd5/v3/@claude-flow/cli/src/services/policy-ledger-audit.ts)以 64KiB 块读 JSONL、限制单条大小，使用私有临时目录里的 48-byte 固定宽索引记录 offset/length/hash，逐条认证、去重后按 sequence 回放 previousReceiptHash；后续正常追加不纳入本次快照。重复记录还比较完整 canonical 值，不只相信弱“出现过”的标志。其内存不随全部历史字符串线性增长，但磁盘临时索引及总耗时仍随历史增长。

### ④ 技术亮点与边界
亮点是安全边界落在独立可读的组件中，尤其审计同时处理裁剪历史、崩溃追赶、重复记录、字节上限和锁持有时间。源码明确威胁模型：外部镜像可检测仅能改项目目录的对手，**不能抵挡能同时重写项目和用户 home 信任材料的人**；也不是区块链式外部公证。默认验证与 full 验证覆盖不同，不能用“hash-chained”一词承诺全历史每次都查过。完整核验捕获 FD 防路径替换，并在读取及重读中校验内容；这仍需配合真正的文件权限和签名密钥管理。

近期 [open PR #4280](https://github.com/ruvnet/ruflo/pull/4280)指出 RVF native 分支 API 用法错误、计划删除而非启用；[open PR #4276](https://github.com/ruvnet/ruflo/pull/4276)报告旧 mission ledger 的无 cwd 记录仍可能跨项目进入上下文。本文没有完整审计这两条实现，保留为未合并反馈，不能将拟修补行为归入当前版本，更不能引用 native 性能宣传当本机实测。

### ⑤ 近期活动与热度：事实、推断分开
**事实：**昨日官方位置 12，今日 5，显示 +513；3.57.0 release 提及 safe Codex defaults、loopback browser guard、归档审计，本次已在上述源码找到对应实现。release 说明与包版本可能存在发布列车差异：当前根依赖 codex **3.0.5**，不能只照 release 中某个旧包号写全仓。最近默认分支 head 是文档改动。按更新时间读取的 [#4230](https://github.com/ruvnet/ruflo/issues/4230)讨论环境变量 denylist 缺口，仍 open，说明防护仍在演进，不证明系统已全面安全。

**推断：**多宿主接入和治理修补可能增加采用意愿；但本次没有独立流量/宣传传播/安装转化证据，**暂无足够公开证据解释今日热度**。没有把安全修复宣传当已经验证的攻防效果。

### ⑥ 对你的工程价值
对 **AI agents/MCP**，先学 init 不覆盖审批、localhost guard、跨项目上下文隔离，而非一开始堆更多 agent。对 **RAG/记忆**，记录 provenance 与审计不等同检索质量；索引可重建，授权与真实历史不能靠同一份可改数据自证。对 **Node/Next/Django/Python** 服务，Host/Origin检查要在业务副作用之前，CORS不是写请求授权；worker审计可以借鉴短锁捕获快照后流式重放。对 **React** 管理界面，建议把“默认快速校验”和“完整审计”的覆盖范围、最后完成时间单独展示，不用一个绿色通过掩盖不同保证。

**实际阅读覆盖：**README、完整目录树、根/CLI/bridge依赖，根CLI入口、Codex initializer权限生成/已有文件保护/hook提示，bridge auth/Host/Origin及对应测试源码，anchor威胁模型/路径/评估/发布、full audit全篇及runtime调用段；12 commits、5 releases、15最新更新issues/PR。没有运行桥接服务、CLI或安全测试，没有全面审计联邦/向量/mission实现；文中性能仅解释算法内存/IO特征，不宣称基准跑分。

## 6. akitaonrails/ai-memory：今天最重要的是记忆服务的权限边界，以及中文检索缺口

### ① 排名、元数据与真实增量

官方今日第 **6**，**Rust，10,542 stars，+512 stars today**。[仓库](https://github.com/akitaonrails/ai-memory)默认分支 `main`，固定 SHA **`b18f22a7c2f3068575c70d37f13d167fed3476bb`**，提交于 **2026-10-18 17:46:47 UTC**；[MIT](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/LICENSE)。与昨日 `995e35d5866973c3176709261e924a67e3c76158` 的[比较](https://github.com/akitaonrails/ai-memory/compare/995e35d5866973c3176709261e924a67e3c76158...b18f22a7c2f3068575c70d37f13d167fed3476bb)为提交图前进 **86 commits、52 个文件变化**。其中有分支合并与重复记账，不能换称“新增 86 项功能/修复”。完整树 **1,388 条目、1,203 文件，未截断**。

最新发布仍为 **[v3.1.1（10 月 17 日 18:09 UTC）](https://github.com/akitaonrails/ai-memory/releases/tag/v3.1.1)**；workspace version 也还写 3.1.1，但今日重点修复位于 [CHANGELOG 的 Unreleased](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/CHANGELOG.md#L12-L89)。版本号相同不证明下载的 release 包已有补丁。

### ② 它解决什么问题

它为跨 Claude Code、Codex 等工具的 coding-agent 工作提供持久上下文：hooks 采集事件，Markdown wiki 保存人能审查的知识，SQLite 建立检索/会话/交接状态，MCP 和可选 HTTP/Web 提供访问。重点是“项目决策、坑、未完成工作能否跨会话续上”，不是单独的 embedding API 包装。[README](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/README.md) · [架构与数据流](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/docs/ARCHITECTURE.md#L16-L40)

昨日已讲单写 actor、多路 RRF 与有归属的 handoff；今天换一个更实际的问题：当“我电脑上的记忆工具”变成多人共享、调用外部 provider 的服务，哪些原本不起眼的字段已经越过信任边界？

### ③ 架构与三个实际机制

**入口与依赖。** Rust workspace 将 core/store/wiki/hooks/mcp/llm/consolidate/web/cli/workstream 拆成 crate；CLI `serve` 组合 Store、Wiki、provider/embedder 及服务路由。核心依赖包含 Tokio、Axum、rmcp、rusqlite、git2；wiki Markdown 是知识内容真源，SQLite 还承载不能只靠 Markdown 还原的会话/交接运行状态。今日依赖清单要求 Rust 1.95、edition 2024，未运行构建。[workspace](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/Cargo.toml) · [serve 组合入口](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-cli/src/commands/serve.rs)

1. **权限不能只在 HTTP 入口检查；三个“顺手做的副作用”今天被收紧。** 新 `same_origin_redirects` 比较每次跳转的 scheme/host/port，只保留同 origin 路径重写，跨 origin 报错；Anthropic、OpenAI-compatible 和 embedding 客户端接入该策略。修复理由是通用 HTTP client 的跨主机处理不能自动覆盖 `x-api-key`、`x-goog-api-key` 和 operator 自定义 header。另一条修复让服务器解析 hook payload 时不再读取 `artifactDirectoryPath`/`transcriptPath` 指向的服务器文件：Antigravity 输出应由执行工具的客户端读取，作为 tool_response 传入。第三条在 session-start 单独检查项目 Write grant，再决定能否持久化 project-wide profile_contribute/profile_consume；Read 用户可收窄自己会话，不能改变其他人的继承设置。这是三个不同边界：凭证的网络目的地、远端输入与本地文件权限、读请求暗含的项目级写入。[重定向策略](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-llm/src/redirect.rs#L1-L34) · [hook 解析移除服务器文件读取](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-hooks/src/payload.rs#L654-L676) · [profile 写授权](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-hooks/src/router.rs#L1662-L1683)

   相关回归测试用两个本地 HTTP origin 检查凭证重定向，并用服务器端 sentinel 文件检查 ingest 不会把它写入 observation。这里确认的是实现与测试存在，本次没有运行测试或对任何在线部署尝试利用，也不据此宣布“系统安全审计通过”。[重定向测试](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-llm/tests/suite/redirect_credentials.rs) · [hook ingest 回归](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-hooks/src/router.rs#L5566-L5652)

2. **检索正确性还取决于查询重写和“过期”在每个派生视图中一致。** `fts_query.rs` 遇到 `ai-mem*` 这类带标点的词，需要引号保护 FTS 语法，但 `*` 若留在引号内就变成字面分隔符；今日修复把前缀操作符放到每个闭引号外。`title:ai-memory` 则保留 title 列过滤，不把 title 一起引成普通检索词。另一方面，TTL 已在检索/维护中起作用，但健康统计、project/workspace 页面计数和最新时间、跨项目 link degree 原先还可能计入已过期页；新查询把 latest 与 not_expired 同时用于关联两端和聚合。对产品而言，搜索说“没有”、dashboard 却说“仍有大量旧知识”的不一致也会损害可信度。[FTS 重写](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-store/src/fts_query.rs#L219-L304) · [统计过滤](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-store/src/reader.rs#L9326-L9360) · [link 两端的版本/TTL](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-store/src/reader.rs#L13498-L13557)

3. **“没有 LLM 的记忆提取”同样需要语言和失败语义测试。** 自动 handoff 会过滤简短的确认话，但旧判断会把“好的，接下来写单元测试”、`kubectl` 等真正指令当确认话丢掉。当前实现只接受完整确认短语与分隔符组成的短串，最长匹配并要求 ASCII 词边界；不匹配的余串保留为请求。相同修复批次还避免把最后一次 prompt 同时重复放进 summary 与 open questions。这不是大模型推理改进，而是低成本启发式的语义修正。[确认话解析](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-hooks/src/router.rs#L4779-L4812) · [中文/命令负例测试](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-hooks/src/router.rs#L20411-L20452)

   外部 embedding 的失败路径也更可观测：OpenAI-shape 调用现在对 429/503 重试，读取整数秒 Retry-After，单次等待上限 32 秒、累计等待预算 62 秒、最多五次新增尝试；HTTP-date 形式不支持，回退原指数等待。CLI embed 处理完仍有失败页时会失败退出，避免“打印了失败数但自动化看到成功”。62 秒只是累计 sleep 预算，不是含网络超时的总调用时限。[重试实现](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-llm/src/embedding.rs#L279-L377) · [CLI 状态](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-cli/src/commands/embed.rs)

### ④ 最值得你注意的边界：中文 RAG 不能照搬英文结果

今日 **01:58 UTC** 新建的 [issue #1433](https://github.com/akitaonrails/ai-memory/issues/1433)报告：页面含“今天把支付服务部署到了生产环境”，查询“部署”“支付服务”“生产环境”不命中；完整标题“上线记录”可以匹配，标题子串“上线”不行。报告者给出了 Rust/SQLite 复现和拟议 CJK bigram 方案，当前仍 open、没有评论；不能把提议写成已实现。

本次源码核到：当前 [V17 pages_fts](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-store/migrations/V17__pages_fts_index_path.sql)及 [V12 observations_fts](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-store/migrations/V12__fts_remove_diacritics.sql)确实使用 `unicode61 remove_diacritics 2 tokenchars '/_-'`，而今日查询重写修的是标点/前缀/列过滤，并未加入中文分词。**具体命中结果仍是报告者的测试，本次未复现；不能因此宣称所有检索模式完全失效。** 默认配置已有本地 embedding 路径，issue 中“zero-LLM 默认主要靠 FTS”的说法不能覆盖每台安装的实际运行状态；本地向量是否有效、是否适合你的中文语料也需另测。[默认 embedding 配置](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-cli/templates/config.default.toml#L143-L149)

更一般的采用边界：上述权限修复尚未形成新 release；若用于共享服务，应先核实际二进制是否含对应提交。云 embedding 会把页面正文发给配置的 provider，改用云端并补建索引可能影响已有语料；脱敏是 best-effort，Markdown/Git/SQLite 不是加密保险箱。今天修了 redirect，不代表给正确 provider 发送页面本身就符合你的数据政策。[数据处理说明](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/DATA_HANDLING.md)

### ⑤ 近期活动与热度：事实和推断

**事实：**今日 +512、没有新发布；10 月 18 日主干集中合入授权、provider 传输、UTF-8、Windows 路径、FTS、TTL 与 UI 可访问性修复。昨天的 [#1281 agent-to-operator 决策请求](https://github.com/akitaonrails/ai-memory/issues/1281)仍 open，今天新增 [#1428 measured/reported/inferred 消息标签](https://github.com/akitaonrails/ai-memory/issues/1428)和 [#1429 规则所有者/复查日期](https://github.com/akitaonrails/ai-memory/issues/1429)也只是需求；[Antigravity 更完整生命周期 PR #1416](https://github.com/akitaonrails/ai-memory/pull/1416)已于 10 月 18 日 17:56 UTC 合并，但目标是 `release/3.2` 分支，不是本次固定的 main，也不是 v3.1.1 已发布内容。

**推断：**跨 agent 的上下文连续性、可编辑知识与持续工程修补可能支撑技术用户兴趣；没有足够公开归因证据解释今日 stars 增长。尤其不能把安全修复或中文问题报告本身说成涨星原因。

### ⑥ 对你的技术方向的价值

- **AI agents/coding agents：很高。** 今天值得抄的是明确区分“事件采集权限”“读取上下文权限”“改变整个项目设置的权限”，以及别让服务端读取客户端随 payload 提交的本地路径
- **RAG：很高，但要用你的语料测。** 加入中文句中词、英文标识符、带连字符前缀、TTL 边界、旧模型向量等回归样本，比只复述一个英文 benchmark 更有价值
- **MCP：很高。** 工具入口只是协议表面，授权要覆盖辅助副作用、错误码与 ID 解析；消息/交接和知识写入需要不同生命周期契约
- **Node/Python/Django：高集成价值。** 可以通过 MCP/HTTP 消费 Rust 服务；若自己实现，HTTP redirect 策略、项目级权限与异步工作失败退出码都能直接借鉴。不要把自动跳转当透明、无风险的网络便利
- **React/Next：后端能力为主。** 可自建仪表盘，但搜索、计数、健康报告必须共享相同 TTL/权限过滤；本仓 Web 是服务端模板方向，不是 Next 应用底座

**今日阅读边界：**README/ARCHITECTURE、完整树、Cargo workspace、serve 组合与默认配置；redirect、各 provider 接入 diff、embedding 重试、hook payload/profile/handoff、FTS query、TTL SQL、相关测试和 V12/V17 migration；86-commit compare、最近 12 commits、4 releases、30 条最近更新 issue/PR、#1433 正文及空评论列表、#1416 合并与目标分支元数据。未运行二进制/测试、下载模型或接入真实用户记忆；没有把“测试已写”说成“本次测试通过”。

## 7. stablyai/orca：今天看跨主机归属、浏览器会话切换和命令参数保真

### ① 排名、元数据与真实增量

官方今日第 **7**，**TypeScript，96,769 stars，+1,146 stars today**。[仓库](https://github.com/stablyai/orca)默认分支 `main`，源码固定 **`bf866505e8716a1b531b7823c0dc6bf93889e1f8`**，提交于 **2026-10-19 02:01:49 UTC**；[MIT](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/LICENSE)。相对昨日 `33e6785fe2c36730bc0dfcdf1db6208d471df833` 的[官方 compare](https://github.com/stablyai/orca/compare/33e6785fe2c36730bc0dfcdf1db6208d471df833...bf866505e8716a1b531b7823c0dc6bf93889e1f8)显示提交图前进 **169 commits**；返回的 changed-files 列表正好达到 API 的 300 项上限，**不能据此声称只改了 300 文件**。完整树通过根目录与各子树分拆读取，合计 **38,456 条目、37,568 文件**；取得目录索引不等于全仓逐行审计。

最新桌面 release 仍是 **[v1.4.229（10 月 17 日 06:54 UTC）](https://github.com/stablyai/orca/releases/tag/v1.4.229)**，没有新桌面发布。下面的主干增量不等于用户当前安装版已提供；尤其本轮很多布局/侧栏提交有明确构建开关限制。

### ② 它解决什么问题

Orca 是把多个现有 coding agent、Git worktree、终端、原生聊天、浏览器、diff/PR 与远端主机放进同一监督界面的桌面工作台。它解决的是“并行开了很多 agent 后，在哪个目录运行、谁占着输入、结果如何检查、断连后如何恢复”，不提供新基础模型。[README](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/README.md)

普通并行工作区与实验性 orchestration 要分开：后者有 Run/Task/Dispatch、收件箱、worker completion 和 decision gate；当前文档仍明确 **Run 不调度或放置 worker**。通常是人为或 coordinator 创建任务、显式启动 worker、按 dispatchId 认领结果，不能仅凭“AI Orchestrator”标题理解成自主规划并全自动运行整个 DAG。[当前编排合约](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/docs/site/content/docs/cli/orchestration.mdx#L8-L31)

### ③ 架构与三个真实增量切面

**入口与数据流。** React renderer 经 preload runtime call/subscribe 到 Electron 主进程；执行主机负责仓库、PTY、浏览器与 agent 会话，UI 订阅状态。目录还有 CLI、mobile、cloud、native 和共享协议。依赖可核到 Electron/Vite、React/Zustand、Monaco/xterm、node-pty、ssh2、ws，Node engine=24；这仍是桌面/远端 runtime 架构，不是 Next.js 应用模板。[入口](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/main/index.ts) · [preload 桥](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/preload/api/runtime-bridge.ts) · [package](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/package.json)

1. **工作区身份不应等于当前 UI 选中的服务器。** 同一 repo/path 可同时出现在两台机器，旧 resolver 把 ambiguous、missing、本地/SSH 等多种情形折成 null，调用方容易把“不知道”当成本机。`resolveOwner` 返回 resolved/missing/ambiguous，并构造不读取 Active Server focus 的 state；冲突的 folder twin 无法靠用户当前选中的 server 随便消歧。今日迁移用的 adapter 对有 host 证据/明确 host 的记录保留新语义，缺失或未 stamped 的旧记录仍保留旧 fallback，说明这是渐进迁移，不能写成全项目已彻底消除 focus fallback。最新提交把 13 个侧栏、hook、聊天和文档读取点迁过来；文件搜索对 ownerIsTwin 直接不发起搜索，避免给用户展示另一台机器的结果。[三态 owner 与 focus-free](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/renderer/src/lib/resolve-owner.ts#L42-L115) · [兼容适配边界](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/renderer/src/lib/worktree-runtime-owner.ts#L265-L306) · [搜索明确拒绝歧义](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/renderer/src/components/right-sidebar/useFileSearchRunner.ts#L47-L95)

2. **浏览器切 profile 变成带代际和恢复路径的替换流程。** 新 `switchBrowserClientPageProfile` 先校验页面 authority、generation 和 profile，再创建 staged guest，要求新旧 partition 不同；准备阶段不先销毁原 guest。停旧 automation 后再次检查 abort/renderer/归属，绑定替代 guest、导航回原 URL，最后确认两者 lifecycle claim 仍有效才 commit。失败时若旧 guest 还活着，先重新绑定再清理 staged 资源，避免误取消页面下载；成功后才退休旧 guest。主机侧还保留 reservation 与 command ledger：调用方超时不代表客户端没切成功，晚到成功仍会在归属有效时接纳，失去归属则关闭替代页并释放 grant。这是处理“结果未知”的显式代码，不是宣称跨网络分布式事务绝对原子。[客户端 staged replacement](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/main/browser/browser-client-page-profile-switch.ts#L18-L155) · [主机 late-result 恢复](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/main/runtime/browser-host/browser-host-client-profile-switch.ts#L105-L176) · [恢复测试](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/main/runtime/browser-host/browser-host-profile-switch-recovery.test.ts)

3. **prompt 进入 CLI 前，跨 shell 仍可能丢字或改变含义。** 新 PowerShell wrapper 在运行时读取 PSNativeCommandArgumentPassing，区分 Standard、Windows 模式与 legacy；是否经 `.cmd/.bat`、是否 Windows PowerShell 5.x 决定如何保留嵌入双引号和尾部反斜杠。对 cmd shim 不能简单统一写成反斜杠加引号，否则可能改变 cmd 的引号配对，让后面的 `&` 被解释成操作符。对应测试真的用一个 native 子进程记录 argv，而非只比生成的命令字符串；还覆盖多行 prompt、末尾反斜杠、含双引号和 `&` 的文本。这些是项目回归测试的设计，本次没有在 Windows 执行，也不构成对所有命令注入路径的保证。[参数编码实现](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/shared/powershell-native-argument.ts#L22-L46) · [实际 argv 测试](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/shared/powershell-native-argument.windows.test.ts#L74-L150) · [本次 commit](https://github.com/stablyai/orca/commit/5df4fef9177fda93446fa35e38ab7b44fedb3e16)

### ④ 亮点、发布边界与未解决反馈

今天的工程亮点不是增加一个按钮，而是把 owner、generation、pending/late result 和 argv 当成不可丢失的状态，防止 UI 显示、网络恢复和真正执行发生分歧。React 状态管理也不只是本地组件问题：用户切到另一台服务器，旧搜索/旧页回包不能据此获得新归属。

**最重要的发布边界：大量带 dark 标记的提交并未对普通构建启用。** `config/dark-build-switches.cjs` 只有在构建变量 `ORCA_LAYOUT_OWNER` 或 `ORCA_SIDEBAR_INPUTS` 等于 main 时才编入相应路径，默认值是 window；这类构建还留下 marker，打包函数会拒绝带开关/marker 的发布。因此“主干里已有主进程维护布局/侧栏顺序”不等于普通用户当前能开启，也不能概括为 v1.4.229 今天发布了这些能力。[构建开关和打包拒绝](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/config/dark-build-switches.cjs)

反馈也未全部闭环：昨日跟进的 [Claude 模型目录竞争 PR #30107](https://github.com/stablyai/orca/pull/30107)今日仍 **open、merged=false**。今日 **02:14 UTC** 新 [#30486](https://github.com/stablyai/orca/issues/30486)则有 macOS/v1.4.229 用户报告 saved-session 验证失败导致终端持续无法安全重连；它是用户报告，本次没有复现，也不能凭主干大量 reconnect 改动断言已修。

采用成本不变：worktree 隔离文件/分支，不等于 OS 进程沙箱；数据库、端口、依赖目录、环境变量和 credentials 仍需按任务考虑。Remote Server 文档要求受控网络，原生聊天/远端能力还取决于宿主版本。cloud 目录公开 relay 等部分，但 API/auth 和部分基础设施仍在私有仓库，不应承诺整个托管后端已可完整自建。[远端运行边界](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/docs/site/content/docs/remote-servers.mdx) · [cloud 开源范围](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/cloud/README.md#L98-L103)

### ⑤ 近期活动与热度：事实和推断

**事实：**今日 +1,146、主干 +169 commits，但桌面最新 release 不变。除上述切面，主干还有 OpenCode 2 原生聊天/首次消息前模型发现、终端转原生聊天恢复、手机任务分页与输入体验等修改；[OpenCode 2 commit](https://github.com/stablyai/orca/commit/e43f3e7e04596b0bd13bb854445ed10db416bcb6)和当前 [ACP launch specs](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/main/acp/acp-launch-specs.ts#L209-L272)可核到独立 opencode2 命令和共享历史/账户策略。它们仍应与已发布桌面包、用户主机上的实际 CLI 版本分别验证。

**推断：**跨 agent、跨机器、跨手机的监督需求可能推动兴趣，持续兼容性修补也显示维护投入；本次没有外部传播链或星标来源数据证明这些改动造成今天的增长。169 commits 的数量也不能直接当作质量、稳定性或采用建议。

### ⑥ 对你的技术方向的价值

- **AI agents/coding agents：高。** 适合借鉴“工作区所有者是明确数据，不是 UI focus”，尤其当你将任务分到本机、SSH 与云端时
- **React/Node：很高。** owner 三态、过渡兼容 adapter、staged guest、late-result 收敛是复杂桌面/实时 UI 的具体范本；直接阅读 source 比把它当多 agent 宣传样板更有收获
- **Next.js：工作流价值高，底座不同。** Design Mode 可把真实元素上下文交给 agent，再配合 diff 审查；你的 Next 应用并不需要搬入 Electron 架构
- **Python/Django：工作流通用。** 两个 worktree 可以分别实现/验收后端修改，但独立目录不自动产生独立测试数据库或端口。把 executor host 和服务资源一起纳入任务身份更重要
- **MCP/RAG：间接价值。** 这里不是检索引擎或通用 MCP server；可借鉴工具调用经过多层协议/终端后的参数保真、结果归属和取消语义。不要用“模型收到了完整 prompt”代替验证最终进程实际收到的 argv

**今日阅读边界：**README 相关功能、完整分拆树、package/主进程/preload、orchestration/remote/cloud 文档；owner resolver/兼容 adapter/搜索调用者、profile 双端切换与恢复测试、PowerShell 编码及 native argv 测试、ACP OpenCode 2 launch 切面、dark build 开关；169-commit compare（文件列表有 300 上限）、最近 12 commits、4 releases、25 条最新 issue/PR、#30107 PR 元数据及 #30486 正文。六个重点 commit 的完整 API metadata/diff 已保存；未安装运行 Orca、操作任何账户、连接远端主机或验证端到端性能。

## 8. HKUDS/CLI-Anything

### ① 排名、版本与今日增量

官方第 **8**；[HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything)；**54,638 stars，+589 stars today，Python**。main 仍为 **34f519533bc175d2fe287ab8316b0dd99bb9cc43**，最后提交于 **2026-09-22 02:01:28 UTC**，与 10 月 18 日报告完全相同，**没有默认分支源码增量**。重新取得的递归树为 **2,582 条目、1,872 文件，未截断**；最新 [release v0.4.0](https://github.com/HKUDS/CLI-Anything/releases/tag/v0.4.0)仍是 6 月 25 日，Hub 的 [setup.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-hub/setup.py)仍写 0.4.1。根 [LICENSE](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/LICENSE)是 Apache-2.0，部分包元数据仍列 MIT，组件采用前应核对这一不一致。

昨天已分析 Krita/FreeCAD 导出链，今天换读 **ChromaDB 与 WireMock 的 HTTP 合同**：一处把只读请求发成错误方法，另一处把已经成功的写入报成失败。新增的是公开反馈与本次阅读切面，不是这些实现今天才出现。

### ② 解决什么问题，适合谁

CLI-Anything 将现有应用的 API、文件格式和脚本入口包装成自描述命令与结构化输出，让 coding agent 不必为每项工作重写集成。使用者通过 Hub 找现成 harness；开发者通过插件/skill 生成新 harness。今天两项适配分别面向向量库操作和 HTTP mock 管理，适合 RAG 工程师、测试开发者和需要可脚本化工具的 agent 团队。它们替代的是手工拼接 HTTP 与输出处理，不替代 Chroma 数据库或 WireMock 服务。[根 README 两类入口及前置条件](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/README.md#L181-L258)

### ③ 架构、入口与三个具体机制

**独立包，而非统一后端。** 两个 harness 都要求 Python ≥3.10、依赖 Click 与 requests；ChromaDB 1.0.0 加 prompt-toolkit，WireMock 0.1.0 加 Rich。console entry 分别是 chromadb_cli:main 与 wiremock_cli:cli。Chroma 的入口建立 requests.Session、注册 server/collection/document/query 分组，并提供 REPL；WireMock 从环境和 CLI 参数构建 host/port/scheme/basic-auth，再将命令交给各 manager。服务器要单独运行，包版本不能当服务器版本。[Chroma setup](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/chromadb/agent-harness/setup.py) · [入口](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/chromadb/agent-harness/cli_anything/chromadb/chromadb_cli.py#L16-L42) · [WireMock setup](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/wiremock/agent-harness/setup.py)

**机制一：Chroma 把名称解析、REST 调用和机器输出分开，但 count 的方法错了。** [document count](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/chromadb/agent-harness/cli_anything/chromadb/core/documents.py#L125-L146)先以 collection 名称查 ID，再调用 backend，成功输出 collection/count，异常输出 error 并退出 1。分层本身清楚；问题在 [count_documents](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/chromadb/agent-harness/cli_anything/chromadb/utils/chromadb_backend.py#L121-L128)实际 POST 一个空 JSON 到 count 路径。

这不是只凭 issue 猜测：已对照 Chroma **1.5.9** 官方固定源码，其 [_count](https://github.com/chroma-core/chroma/blob/11f3c7435e71024aa0a2b53710a28d3289d922d1/chromadb/api/fastapi.py#L491-L504)用 GET 调同一路径。当前 [单测](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/chromadb/agent-harness/cli_anything/chromadb/tests/test_core.py#L216-L223)恰好 mock 了 post，因此会验证错误实现与错误假设彼此一致；[E2E 文件](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/chromadb/agent-harness/cli_anything/chromadb/tests/test_full_e2e.py)覆盖帮助、server、collections 和 JSON 可解析性，没有 document count 场景，服务器不可达时整文件 skip。[#587](https://github.com/HKUDS/CLI-Anything/issues/587)中的真实 405 是报告者实测，本次确认的是方法合同及测试覆盖缺口，没有启动 Chroma。

**机制二：WireMock 成功导入后，JSON 解析失败被包装成整个操作失败。** [StubsManager.import_stubs](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/wiremock/agent-harness/cli_anything/wiremock/core/stubs.py#L46-L49)依次 POST、raise_for_status、r.json。WireMock **3.13.1** 官方 [ImportStubMappingsTask](https://github.com/wiremock/wiremock/blob/1a9a61507fbca5c7d6da72de4b22d54ceef48760/src/main/java/com/github/tomakehurst/wiremock/admin/ImportStubMappingsTask.java#L26-L33)先执行 importStubs，再返回不附 JSON 的成功响应。CLI [stub import](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/wiremock/agent-harness/cli_anything/wiremock/wiremock_cli.py#L230-L248)捕获随后发生的解码错误，交给 [error](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/wiremock/agent-harness/cli_anything/wiremock/utils/output.py#L42-L48)打印错误并退出 1。

所以它不是“服务端拒绝写入”的同义词：写入可已完成，只是客户端错误解释响应。若 agent 见非零退出就无条件重试，无稳定 ID 的导入可能重复创建数据；这是由操作顺序推出的重试风险，不能将每种导入配置都说成必定重复。[#589](https://github.com/HKUDS/CLI-Anything/issues/589)报告了“CLI exit 1，但刚导入的 mock endpoint 已返回 201”的实例。当前 [单测](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/wiremock/agent-harness/cli_anything/wiremock/tests/test_core.py#L247-L253)却给成功导入伪造 JSON body，掩盖了空响应这条路径。

**机制三：机器输出与人类表格是两种消费者，不能只测一种。** WireMock 的 [request list](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/wiremock/agent-harness/cli_anything/wiremock/wiremock_cli.py#L260-L289)在 JSON 模式直接透传响应，人类模式却读取 serveEvents 和顶层 total；官方 [GetServeEventsResult](https://github.com/wiremock/wiremock/blob/1a9a61507fbca5c7d6da72de4b22d54ceef48760/src/main/java/com/github/tomakehurst/wiremock/admin/model/GetServeEventsResult.java)序列化的是 requests 和 meta。stub list 的总数同样应读 [meta.total](https://github.com/wiremock/wiremock/blob/1a9a61507fbca5c7d6da72de4b22d54ceef48760/src/main/resources/swagger/examples/stub-mappings.yaml)，而不是顶层 total。

find/unmatched 又是另一种 schema：官方 [FindRequestsResult](https://github.com/wiremock/wiremock/blob/1a9a61507fbca5c7d6da72de4b22d54ceef48760/src/main/java/com/github/tomakehurst/wiremock/verification/FindRequestsResult.java)返回 LoggedRequest 列表，[官方样例](https://github.com/wiremock/wiremock/blob/1a9a61507fbca5c7d6da72de4b22d54ceef48760/src/main/resources/swagger/examples/requests.yaml)把 method/url 放在每项顶层；当前 [表格分支](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/wiremock/agent-harness/cli_anything/wiremock/wiremock_cli.py#L293-L367)却再套一层 request，甚至给 find 加没有对应响应来源的 Status 列。不能把正常解析的 JSON、空表格和真的零请求混为一谈。

### ④ 亮点、实际修复提案与边界

亮点仍是轻量的 CLI→manager/backend→现有服务分层，能够逐层替换和验证；今天的反例说明，“统一命令格式”与“统一且正确的操作语义”是两回事。

新 [PR #588](https://github.com/HKUDS/CLI-Anything/pull/588)把 count 改为 GET，并加入新建空 collection 后核 count=0 的实服务 E2E；固定 head **e231bc75f1c3da98c3ec5a3c7d6389b87d22b1d9**。新 [PR #590](https://github.com/HKUDS/CLI-Anything/pull/590)不再解析 import 的空 body，明确返回 status=ok，修正表格字段，同时修改单测、加入真实服务的 import/表格断言；固定 head **2cd3644f28f6dc27d26c29e8a8ce98f975b68da7**。两者均已读完整文件 diff，**均 open、merged=false**；作者报告的通过数和真实服务版本是作者证据，不是本次执行结果。

还有两个应带进采用评估的合同问题：Chroma [backend](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/chromadb/agent-harness/cli_anything/chromadb/utils/chromadb_backend.py)请求没有显式 timeout，WireMock [client](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/wiremock/agent-harness/cli_anything/wiremock/utils/client.py#L7-L34)则默认 30 秒，说明不能用一个 harness 的可用性保障代表全仓。Chroma 的 [SOP endpoint 表](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/chromadb/agent-harness/CHROMADB.md)也仍把 count 写成 POST，而 #588 文件清单没有改这份表；代码修正提案不自动意味着 agent 读到的知识已同步修正。

### ⑤ 近期活动与热度，事实和推断分开

**事实：**相较昨日第 4，今日排第 8；+589 是今日卡片窗口值，不用总 stars 的两日差来替代。main 与 release 均未改变；#587/#588 于 **10 月 18 日 16:36–16:40 UTC**、#589/#590 于 **16:59–17:03 UTC**出现或更新，是昨日榜单快照之后的新反馈和修复提案。昨天涉及的 FreeCAD/QGIS 也出现新的 [#584](https://github.com/HKUDS/CLI-Anything/pull/584)、[#585](https://github.com/HKUDS/CLI-Anything/pull/585)，读取时仍未合入，不能宣布昨天的缺陷已经在 main 修好。

**推断：**把数据库与测试服务变成 agent 工具，有持续使用价值；这批反馈显示 API 方法、空响应、schema 和重试副作用是适配层的真实难点。但没有传播链证明这些新 issue/PR 导致当天涨星，**暂无足够公开证据解释今日热度**。已启用 Discussions；本次刷新重点是 issues/PR，未取得新的完整 Discussions 样本。

### ⑥ 对你的技术栈的价值

对 **AI Agents/coding agents/MCP**，错误合同至少要区分“操作未执行”“已执行但响应解读失败”“执行结果未知”；重试要基于幂等键或读后核验，不能只看 exit code。对 **RAG**，这里有真实 Chroma 管理入口，但并不包含端到端检索质量保障、embedding 模型治理或引用校验；count 正确也不证明召回正确。

对 **React/Next/Node**，API adapter 和表格 renderer 应分别用官方响应样本做合同测试，空数据不能当容错默认值掩盖字段漂移。对 **Python/Django**，可以复用 manager/client 分层，把 HTTP 方法、状态码、空 body、鉴权、timeout、跨版本响应和副作用验收做成共享测试矩阵；mock 数据应来源于真实协议，避免照着被测实现重新编造。

**实际阅读范围：**根 README 定位/两类入口/前置条件/架构与测试段、根 LICENSE、Hub/Chroma/WireMock setup、完整递归树；两项 harness README/SOP、Chroma CLI、document/query/backend 全文，count 单测和 E2E 全文；WireMock stubs/requests_log/session/client/output 与 CLI 对应分组、导入单测/E2E 对应段；15 条近期 commits、3 条 releases、25 条按更新时间排序 issue/PR、#588/#590 完整 diff、#584/#585 merge 状态；额外对照固定 SHA 的 Chroma 1.5.9 count 实现、WireMock 3.13.1 导入/响应模型与官方样例。未安装、运行代码或服务，未将选读范围扩大为全仓验证。

## 9. debpalash/VoiceStudio

### ① 排名、版本与真正的一日变化

官方第 **9**；[debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio)；**75,550 stars，+2,082 stars today，Python**。当前 main 仍是 **d819ff54d93017bf4a5b34b605833162163c9e3c**，提交于 **2026-10-17 21:52:09 UTC**，与昨日完整报告一致，**今天没有新的主干 diff**。递归树仍是 **3,835 条目、3,498 文件，未截断**。根 [package.json](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/package.json)和 [pyproject.toml](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/pyproject.toml)写 0.5.7、AGPL-3.0-only；最新正式 [v0.5.6](https://github.com/debpalash/VoiceStudio/releases/tag/v0.5.6)仍为 9 月 23 日。昨天已分析的移动 companion 与桌面 UI CI 不能再包装成今天新合入。

今天重点是三个新修复提案揭示的边界：**MCP 传输入口、前端清空语义、跨进程模型配置**。它们目前都尚未成为主干修复。

### ② 它解决的实际问题

VoiceStudio 把语音克隆、合成、转录、配音、长篇音频和模型管理组合为本地优先工作台，向其他应用与 agent 开放 API/MCP。适合需要统一声音资产、工作流和多个引擎的创作者及开发者；它是应用编排层，不是一个新的通用语音基础模型。[README](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/README.md)中的 646 语言等定位是维护者宣称，本次未测覆盖率、音质或速度。

原有架构不变：Electron + React/TypeScript UI，另有 Vite web 构建；Python ≥3.11 的 FastAPI/uvicorn 负责 API，各推理引擎或 sidecar 做重任务。[Electron manifest](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/electron/package.json)可见 TanStack Query、React、Vite、Vitest 等依赖；Python manifest 的 MCP 范围为 ≥1.28.1、<2，[锁文件](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/uv.lock#L3166-L3185)实际锁定 1.29.0。

### ③ 入口、数据流与三个实现机制

**机制一：同一个 MCP server builder，并不意味着三种启动路径都测试到。** [_ensure_mcp/create_mcp_server](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/mcp_server.py#L411-L459)延迟导入 SDK；嵌入主 API 时，工具可通过 ASGI 在进程内调用后端，独立运行则通过 HTTP 调后端。[mount_mcp](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/mcp_server.py#L921-L948)取得 streamable_http_app，挂载 /mcp，并处理裸 /mcp 路径；SDK 缺失/集成初始化异常只禁用这项能力，不把整个后端退出。

独立 [CLI main](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/mcp_server.py#L953-L990)默认 stdio，--sse 分支却调用 mcp.run(transport="sse", port=args.port)。已对照锁定版本 **MCP Python SDK v1.29.0** 的 [FastMCP.run 签名](https://github.com/modelcontextprotocol/python-sdk/blob/98b7159cb89274964055d2c016e3360a551280d0/src/mcp/server/fastmcp/server.py#L282-L303)：只接受 transport/mount_path，没有 port；其 [SSE runner](https://github.com/modelcontextprotocol/python-sdk/blob/98b7159cb89274964055d2c016e3360a551280d0/src/mcp/server/fastmcp/server.py#L765-L778)实际从 settings.port 建 uvicorn。这里的参数合同不相容已静态确认，[#2995](https://github.com/debpalash/VoiceStudio/pull/2995)报告的启动 TypeError 有对应源码依据。

修复提案把端口先写入 settings，再调用 run。新增测试 stub 的是 SSE serve loop，验证 CLI 参数到实际 server settings 的传递；它不是一次真实网络握手测试。**问题范围是独立 --sse 入口，不能写成所有 MCP 或已挂载 /mcp 均不可用**。当前 [graceful-degradation 测试](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/tests/test_mcp_graceful_degradation.py)原本聚焦缺依赖和退出语义，不能代替各 transport 的成功启动测试。

**机制二：保存默认声音时，UI 的 null 与后端的“保留旧值”撞车。** [MCP binding service](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/services/mcp_bindings.py#L37-L72)采用单条 SQLite INSERT…ON CONFLICT UPDATE，将并发首次保存和局部编辑交给数据库处理；参数 None 表示保留已有字段，空字符串表示清空 profile/engine 为 NULL。这比先读整行再回写更能避免覆盖其他客户端刚做的局部修改，现有 [交错编辑/清空测试](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/tests/test_mcp_bindings.py#L43-L103)也明确了合同。

但 [React save handler](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/electron/src/renderer/src/features/settings/mcp-bindings-settings.tsx#L53-L78)把 Default voice 转为 null，把空 label 也转为 null；[REST body/router](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/api/routers/mcp_bindings.py#L23-L46)原样传下去。因此同一 client_id 已绑定声音时，再保存 Default voice 会保留旧绑定，而不是清掉。API 仍可成功返回，问题是前后端对操作意图理解不同。

这会影响后续工具调用：[resolve_voice](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/services/mcp_bindings.py#L96-L116)按显式 profile→client binding→后端默认解析；[generate_speech](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/mcp_server.py#L525-L603)从 HTTP request header 获取 client ID，再查这条记录。stdio 没有该 HTTP 身份时返回 None，不能假定所有传输都自动带同一客户端绑定。[#3000](https://github.com/debpalash/VoiceStudio/pull/3000)拟让 UI 明确发送空字符串并新增组件请求体断言。一个 SQL 层正确且有测试的功能，仍可能被 UI 的值映射破坏。

**机制三：隔离 native crash 的 sidecar，也隔离了不在协议中的配置。** [SubprocessASRBackend](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/services/subprocess_asr.py)把转录作为子进程任务：锁内启动/复用 sidecar、发送长度前缀 JSON、等待结果；无响应时关闭旧进程并区分超时与 crash，下次请求可重生。来自 GPU pool 的请求不再次占位，其他调用才占槽并在 finally 释放，避免单 worker 池内自锁。[_asr_sidecar](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/engines/_asr_sidecar/main.py)把协议输出放到复制的私有 fd，再将普通 stdout 转向 stderr，防止模型库日志破坏二进制帧。这是有价值的故障隔离设计，**进程隔离不是权限沙箱**。

新的配置问题沿三处代码可追清：

- [select_faster_whisper_model](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/services/asr_backend.py#L3872-L3902)把选择写到 prefs 的 asr_model_faster，并更新当前进程环境，关闭旧隔离实例；父进程解析模型时会读这个 preference
- 重启时 [restore_env](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/core/prefs.py#L138-L156)只恢复 env.* 项，这个 key 不在其中；[spawn](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/services/subprocess_backend.py#L492-L520)只是复制当前 os.environ
- 当前 [transcribe 请求](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/services/subprocess_asr.py#L139-L157)没有 model 字段；子进程 [_get_model](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/engines/_asr_sidecar/main.py#L84-L102)只读 ASR_MODEL_FW/ASR_MODEL_FASTER，缺失便选 large-v3。因此在没有外部模型环境变量、只靠 UI preference 的重启场景，父子进程可使用不同模型

[#2997](https://github.com/debpalash/VoiceStudio/pull/2997)的提案将父进程解析后的模型放进 transcribe frame，并验证子进程收到的模型名；保留 sidecar 专用环境 override 的优先级。作者报告替身模型测试发现重启后退回 large-v3；“未缓存时可能意外下载较大模型”是由加载路径及报告支持的风险，本次没有下载权重，也未测其实际大小或运行耗时。

### ④ 亮点与验证边界

最值得迁移的是 **故障隔离、并发局部更新、配置解析和传输启动分别建模**，再把跨边界的数据合同变成测试。今天三个问题的共同点是某一层“看起来成功”，无法证明整条链兑现了同一意图：server builder 可创建不代表 SSE CLI 可启动，SQL upsert 正确不代表 UI 可清空，父进程已保存模型不代表子进程重启后用的是它。

采用时仍要区分应用授权与模型/声音资产条件；[README 的说明](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/README.md#L150-L153)明确模型权重、声音和输出条件另算，声音克隆需取得许可。代码静态检查不证明声学效果、真机支持或所有 native 依赖稳定。隔离 ASR 的 [文档](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/docs/engines/faster-whisper-isolated.md)还明确该引擎是 opt-in，不由自动检测默认选择；不能将选读问题推广为所有 ASR 路径都必受影响。

### ⑤ 近期修复状态与热度

**事实：**今日第 9、+2,082；main/release 均与昨日相同。10 月 18 日新提的三个 PR 读取时均 **open、merged=false**：#2995 head **5dbb1720ad75e777dadc0a9f9e466bf56c175199**，#3000 head **5a57e2c61d00d4c567d93b621af36435620063d6**，#2997 head **00b63802d9e390a140bb2c25a033d30ae1107213**。已读三个完整 diff 和新增测试，不能把作者的“after”运行记录当成主干现状或本文实测。

昨日追踪的 [#2969 手机本地推理](https://github.com/debpalash/VoiceStudio/pull/2969)仍未合入，head 已为 **b3ce49936d0abf25287e52200522e3e40f7913bd**，其正文也说明真机验证和 iOS 签名仍待完成；当前 main 的 [mobile 文档](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/docs/mobile.md#L1-L27)仍是配对后端的 companion preview。[#2941 HOME 脱敏](https://github.com/debpalash/VoiceStudio/pull/2941)仍 open、未合入。今天榜单之外的评论/PR活动，不构成“新正式发布”的证据。

**推断：**本地语音制作、agent 接入和手机入口可能拓宽受众，但未找到可以将它们与当日涨星直接连起来的传播证据，**暂无足够公开证据解释今日热度**。

### ⑥ 对你的工程栈的价值

对 **AI Agents/MCP**，应给 stdio、SSE、Streamable HTTP 分别做启动与握手测试，记录身份从哪里来；client ID 是声音选择标签，不能代替鉴权。对 **RAG**，VoiceStudio 可接在检索与有证据的回答之后做语音输出，仓库本体不负责检索真实性；文本来源、声音授权和音频产物应保留关联。

对 **React/Next/Node**，今天最直接的例子是“未提供、清空、设置值”三态不能随手都压成 null；组件测试要核出站 payload，并与 API 合同测试衔接。对 **Python/Django**，模型/设备/授权/超时配置应显式进入 worker 或 sidecar 的请求协议，在重启、重试和切换后重核；“数据库已保存”与“执行器已采用”应分别可观察。进程隔离可保护主服务可用性，但不能替代任务权限控制与模型资源限制。

**实际阅读范围：**README、根/Electron manifests、pyproject 核心依赖段、uv.lock 的 MCP 条目、完整树；MCP builder/身份/生成/挂载/CLI 段，binding router/service 全文、React 组件 save/列表相关段、相关原有测试；subprocess_asr 与 ASR sidecar 全文、父类 spawn/ready 段、asr_backend 模型选择/解析及 prefs 恢复段、隔离引擎文档；15 条近期 commits、5 条 releases、25 条近期 issue/PR，#2995/#3000/#2997 完整 diff，#2969/#2941 正文和 merge 状态；另对照 MCP SDK v1.29.0 固定源码。未运行依赖安装、测试、模型推理或 UI，不把下载的巨大文件视为逐行审计。

## 10. android/skills

### ① 排名、版本与源码基线

官方第 **10**；[android/skills](https://github.com/android/skills)；**8,804 stars，+375 stars today，Kotlin，Apache-2.0**。main 仍为 **5bda39f154fb859a08d45e2392f3568e049f83fb**，提交于 **2026-10-14 11:24:05 UTC**，与昨日报告完全相同，**无主干源码增量**。递归树 **654 条目、412 文件、30 个 SKILL.md，未截断**；两种 plugin manifest 均为 1.0.15，最新 [release v1.0.15](https://github.com/android/skills/releases/tag/v1.0.15)仍是 10 月 14 日。

昨天读 testing-setup 与安全示例，今天重点检查新问题指出的 **“安装成功是否真的发现技能”“审计对象身份是否被错误覆盖”“多 agent 产物是否有确定的名字”**。这三层都在模型回答之前或之外，值得独立验证。

### ② 解决什么问题，适合谁

这是 Google/Android 提供的任务知识包，含 Android 构建、迁移、测试、安全、设备能力等专业指令、参考资料和部分 Python 工具，帮助 coding agent 处理模型单靠通用知识容易失误的场景。入口是 Android CLI 安装或宿主 plugin，之后由宿主发现与按任务加载 SKILL。它不代替 SDK/Gradle、不会仅凭安装就自动验证 Android 应用。[README](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/README.md)也明确要求复查 AI 结果，并说明目前不接受公众直接贡献。

### ③ 架构、入口与三个实际机制

**机制一：发现技能依赖宿主 manifest schema；这个错误不发生在模型推理阶段。** 当前 [.codex-plugin/plugin.json](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.codex-plugin/plugin.json#L24-L176)把 skills 写成 30 个 source.path 对象；[Claude manifest](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.claude-plugin/plugin.json)则使用路径字符串。

新 [#245](https://github.com/android/skills/issues/245)报告 Codex CLI 0.163.0 可安装插件但发现零技能。本次不仅转述：已读取 **openai/codex rust-v0.163.0** 对应固定 SHA **83086188ae0614bd882818ff1aa23f3194962012** 的 [RawPluginManifestPaths](https://github.com/openai/codex/blob/83086188ae0614bd882818ff1aa23f3194962012/codex-rs/core-plugins/src/manifest.rs#L134-L140)，其合法形状只有字符串或字符串数组；[resolve_manifest_paths](https://github.com/openai/codex/blob/83086188ae0614bd882818ff1aa23f3194962012/codex-rs/core-plugins/src/manifest.rs#L581-L604)遇 invalid 值会写 warning 并返回空路径列表。**静态可确认 manifest/该版本解析器不相容**；Windows 新 profile 的完整安装复现和 Android CLI 直装对照是报告者的结果，本次未启动 Codex，不扩张成所有历史/未来宿主版本都失败。

[update-skills 工作流](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.github/workflows/update-skills.yml#L65-L131)扫描 SKILL.md 后，为 Claude 写字符串数组，却再次给 Codex 生成 source.path 对象数组。因此只手改一次 manifest 而不改生成器，下一次同步仍可能重引入错误；真正验收应包含“新会话枚举到哪些技能”，不能停在插件记录存在或版本号正确。

**机制二：Play Policy 的身份解析有优先级，但跨平台 fallback 破坏了它。** [play-policy-insights/SKILL](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/SKILL.md)的执行链是 Python init 做文件盘点/静态信号/应用身份 → 生成各领域 worker prompt → 宿主并行或顺序执行 → 聚合 findings → critic → 生成报告；不是单靠 Kotlin 示例，也不是完整 Gradle 编译器或确定性的政策判定器。

[determine_primary_identity](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L399-L491)先取 app module 的 applicationId/targetSdk，再补全局 properties 和 manifest。到了 Flutter/React Native 分支，入口条件是“ID 或 SDK 任一缺失”，但 pubspec name/package.json name 都无条件赋给 primary_id。因此已经正确解析的 Android applicationId，只因 target SDK 未解析，仍可被 Dart/npm 包名覆盖；下面 MAUI 分支则用 old_value or fallback，仅填缺项。这个差异在当前源码中确实存在，对应新 [#242](https://github.com/android/skills/issues/242)。

后果不只是报告标题难看：[generate_report](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/generate_report.py#L684-L702)在缺本地商店资料时按 manifest_details.package_name 查询 Play Store。错误身份可能查不到或查到不相干对象，影响后续对照。这里是静态数据流支持的风险，没有对任何真实用户应用发查询，也未证明某份实际报告已产生错误结论。

**机制三：多 agent 工作流的输出路径应由程序绑定，不能留下待模型猜的占位符。** [write_agent_prompts](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L690-L846)按扫描信号生成 goals；data_safety 有证据时每批最多 6 条，先做每文件/数据类型的取样限额，再为每个 part 写 GOAL_NAME。单次目标分支直接使用 base_context，却没有设置 GOAL_NAME。

[template_engine.VarNode](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/template_engine.py#L59-L74)遇未知变量会保留原标签；三个 [goal 模板](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/resources/goal_user_account.md#L88-L90)末尾又都用 worker_{{GOAL_NAME}}.json。于是单次 prompt 内确实可能保留同一个未解析文件名，对应新 [#243](https://github.com/android/skills/issues/243)。后续 [aggregate](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L849-L890)只是 glob worker_*.json、解析并编号，不按 activated_goals 清单核每个目标结果齐备，单靠这个 collector 不能发现所有缺失/覆盖。

边界也要说全：SKILL 的 [Mode A/B](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/SKILL.md#L115-L169)另行明确传入具体目标文件名，并要求检查文件存在/JSON 有效；严格执行外层指令的宿主可能补上缺口。因此能确认的是生成 prompt 与外层合同冲突、程序聚合缺少清单核验，不能断言每次审计都会丢结果。由 agent 自己猜对路径并不能成为确定性保障。

### ④ 亮点与新问题的证据边界

可借鉴的亮点是按信号缩小上下文、区分静态证据与领域判断、将 worker/critic/报告分阶段保存；当前选读脚本大多使用 Python 标准库，模板引擎自建 AST 处理条件和循环。边界在于：证据完整性、身份来源、模板变量与产物清单也属于正确性，不该全部交给自然语言“必须检查”。

新 [#244](https://github.com/android/skills/issues/244)报告 Windows 路径导致测试文件和非 Play flavor 过滤失效。[scanner.collect_target_files](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/scanner.py#L83-L151)确实把 os.path.join 的结果与 /debug/、/test/ 等正斜杠子串比较；[两处 flavor 过滤](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L289-L316)及 [key-file 路径过滤](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L1118-L1138)也有同类前提。在 Windows 反斜杠路径下，这些条件不匹配，扫描范围可能混入测试/非目标变体。

但不能照抄 issue 的所有结论：下游 [manifest 汇总循环](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/play/play-policy-insights/scripts/orchestrator.py#L1177-L1195)已经先把反斜杠改成正斜杠，再跳过 debug/test/androidTest/testFixtures。**这是一条真实的后续防线，因此不能仅凭上游 inventory 缺口，断言 debug-only 权限必然污染最终 manifest_details。** 当前可确认的是多处路径归一化不一致、源代码信号和非 Play flavor 过滤风险；最终报告影响仍需按每条数据流实测。本次未运行 Windows 项目。

### ⑤ 新反馈、发布状态与热度

**事实：**main 和 v1.0.15 均未变化，昨日测试/安全示例的问题不能标为已修复。#242、#243、#244 于 **10 月 18 日 09:10 UTC**左右创建，#245 于 **22:51:21 UTC**创建，均晚于昨日榜单快照，读取时均 open。今天还可见 [#235](https://github.com/android/skills/pull/235)发布说明生成提案继续更新，但 open 提案不是新 release。

**推断：**官方领域知识与跨宿主分发可能支撑关注；与此同时，新反馈说明“内容正确”之前还要先保证内容被发现、审计对象是对的、工作结果齐备。没有来源证明这些变化导致今日 +375，**暂无足够公开证据解释今日热度**。仓库未启用 Discussions，本次反馈证据来自 issues/PR。

### ⑥ 对 AI Agents、RAG、MCP 与你的技术栈的价值

对 **coding agents**，应将安装完成拆成下载、manifest 校验、宿主发现、实际激活四项；知识包的版本更新最好带宿主版本兼容矩阵。对 **RAG**，可将这些带 SHA 的领域资料当知识源，但还要保留来源、版本和开放问题，尤其不要把 npm/Dart package name 当 Android applicationId 的等价标识。

对 **MCP/多 agent 系统**，任务 ID、输入清单、输出路径与 schema 应由执行层绑定；聚合器按任务清单收齐结果、拒绝重复和未知产物，不能依赖 glob 命中的文件就是正确集合。这里主要是 skill 与宿主工具协作，不是自带 MCP server 或强制权限隔离。

对 **React/Next/Node**，可迁移“有效值不被 fallback 覆盖”和跨平台路径归一化；对 **Python/Django**，把模板未知变量视为生成阶段错误，使用 pathlib/统一路径表示，给单次/分块、Windows/POSIX、身份部分缺失和缺 worker 文件分别写合同测试。借鉴的是这类工程护栏，不是把 Android 专属依赖直接移进 Web 项目。

**实际阅读范围：**根 README、两种 manifest、完整递归树、更新工作流全文；Play Policy SKILL、scanner/template_engine 全文，orchestrator 的身份解析、prompt/aggregate、flavor/manifest 管线段，goal 输出模板与 generate_report 商店查询入口；15 条近期 commits、5 条 releases、25 条近期 issue/PR、#242–245 正文；额外核对 Codex 0.163.0 固定源码的 manifest shape 和解析路径。没有安装插件、执行审计、发起模型请求、运行 Android 构建或测试；没有把政策相关技能阅读当成对真实应用合规性的法律结论。

## A. 今天最值得深读的 3 个源码模块

1. **OpenCode V2：session/run-coordinator + runner/step。** [并发入口](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/session/run-coordinator.ts) → [步骤执行](https://github.com/anomalyco/opencode/blob/8c9c85c26304bf17694125aabacf546da19cc9e6/packages/core/src/session/runner/step.ts)。关注同一会话互斥、wake 丢失、interrupt 与新请求交错，以及已输出之后重试为何不能像零输出失败一样重来。适合你的 agent runtime；验收题是“取消中来了新请求，会不会丢工作或重复副作用”
2. **ai-memory：redirect + hook router + FTS migration。** [redirect](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-llm/src/redirect.rs)、[授权路径](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-hooks/src/router.rs)、[FTS schema](https://github.com/akitaonrails/ai-memory/blob/b18f22a7c2f3068575c70d37f13d167fed3476bb/crates/ai-memory-store/migrations/V17__pages_fts_index_path.sql)。这组最贴近中文 RAG/共享记忆：身份、请求目的地、项目级写入与分词覆盖必须分开验收；main安全补丁尚未进入新release，不能仅看3.1.1版本号
3. **Orca：resolve-owner + browser profile 双端切换。** [owner三态](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/renderer/src/lib/resolve-owner.ts)、[客户端替换](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/main/browser/browser-client-page-profile-switch.ts)、[晚到结果处理](https://github.com/stablyai/orca/blob/bf866505e8716a1b531b7823c0dc6bf93889e1f8/src/main/runtime/browser-host/browser-host-client-profile-switch.ts)。最适合 React/Node 多执行器界面：missing/ambiguous不可等价本机，UI focus不可充当数据归属，调用超时也不可等价操作没发生。它们是源码范本，不代表已发布桌面版本全部包含

## B. 由今天项目实际支持的 5 个趋势

1. **Agent 集成的难点正在落到确定性的协议合同。** ai-job-search联网前拒绝空参数；CLI-Anything暴露HTTP方法/空body/schema错误；VoiceStudio暴露null清空语义与sidecar配置漂移。可操作结论：为每个工具保留错误种类、请求样本、响应样本和副作用核验，不把“JSON能解析”当集成完成
2. **多宿主技能从文档集合变成需要构建与兼容测试的资产。** Cursor以单源生成Claude副本并检查字节漂移；Android同样由工作流生成manifest，却与特定Codex解析器不相容。应测发现、激活、参数、产物的完整链，而不是只看安装记录；形式化验证skill也需证明能抓住真实破坏，不能只写一份漂亮指令
3. **共享记忆/工具服务需要把辅助副作用纳入权限模型。** ai-memory收紧跨origin凭证、hook服务器文件读取及profile项目写入；Ruflo保护初始化审批设置和loopback浏览器访问；OpenCode在保存允许规则之前保留显式deny优先。它们支持“边界检查更细”的观察，不证明这些项目已通过全面安全审计
4. **并发 agent 的关键抽象是归属、取消和未知结果。** OpenCode分离active execution/pending wake，Orca保留owner三态与late-result，CLI-Anything的写入成功后解码失败提醒重试风险。工作流的状态模型至少应区分未执行、执行中、完成、结果未知，不能让一次timeout或UI切换决定真实世界状态
5. **可观察数据也需要自己的正确性规范。** Anthropic session-report的子代理calls单位、前100明细截断和日期归桶，ai-memory的TTL计数与中文FTS，Ruflo的快速tip验证和完整历史重放，都显示“有数字/有审计”不等于口径完整。仪表盘要写单位、覆盖、截断、版本与未验证项。这是今日样本共同暴露的工程趋势，不是整个行业的统计结论

## C. 与 2026-10-18 实际报告的榜单、源码与反馈对比

基线是上方固定归档，榜单时间为昨日 **10:20:06 BJT**，今天 **10:17:38 BJT**，间隔 **23小时57分32秒**。以下“总星变化”只是两次快照差，不替代官方 stars today。昨天完整前十为 claude-plugins-official、ai-job-search、ECC、CLI-Anything、scientific-agent-skills、ai-memory、android/skills、orca、claude-code、VoiceStudio。

| 今日项目 | 昨日→今日位置 | 总stars快照差 | 实际源码比较 |
|---|---|---:|---|
| ai-job-search | 2→1 | +2,941 | `5d9e097…`→`0f6480d…`；官方compare ahead27、68文件；Freehire端点/参数与fork升级检查有增量 |
| claude-plugins-official | 1→2 | +930 | `ea10b21…`→同SHA；无主干变化。今天新增session-report深读与新问题，不是假发版 |
| opencode | 11→3 | 未在昨日前十表作同口径总星比较 | 昨日榜第11但无逐仓源码基线；今日读取dev `8c9c85c…` 的V2实现，不能称一日架构重写 |
| cursor/plugins | 昨日13卡片未出现→4 | 不补造 | 昨日无源码基线；10月17→今日ahead24是跨两日比较，不能冒充昨日diff |
| ruflo | 12→5 | 未在昨日前十表作同口径总星比较 | 昨日榜第12但无逐仓源码基线；今日`b931448…`，最近head文档改动，3.57.0不是今天刚发布 |
| ai-memory | 6→6 | +597 | `995e35d…`→`b18f22a…`；ahead86、52文件。安全/FTS/TTL在Unreleased；#1416合至release/3.2不等于main |
| orca | 8→7 | +1,289 | `33e6785…`→`bf86650…`；ahead169，compare文件列表触300上限。无新桌面release，dark构建不可当默认发布 |
| CLI-Anything | 4→8 | +547 | `34f5195…`→同SHA；新HTTP合同问题与修复PR，尚未合入 |
| VoiceStudio | 10→9 | +2,070 | `d819ff5…`→同SHA；MCP/绑定/ASR提案尚未合入，移动端也未宣布真机完成 |
| android/skills | 7→10 | +358 | `5bda39f…`→同SHA；新发现/身份/模板问题，并保留下游路径防线的反证 |

**榜单变化：**7个连续项目，3个进入今日前十（OpenCode、Cursor plugins、Ruflo）；ECC、scientific-agent-skills、claude-code退出前十。退出只表示本次前十没有，不表示停止维护或价值下降。OpenCode/Ruflo是从昨日可见的第11/12进入；Cursor昨日13卡片未出现，不推断其更低名次。

**源码变化：**7个连续项目中，3个默认分支确实前进（ai-job-search、ai-memory、Orca），4个SHA完全不变。前三者的compare提交数量包含合并历史，不能当功能数；后三类的发布与源码状态仍须分开。本报告每项均给40位固定源码链接，表中短SHA仅帮助阅读。

**反馈变化：**昨天尚未闭环的ai-job-search URL/region问题、Orca #30107、VoiceStudio移动推理与HOME脱敏，今天仍明确保留；CLI/Android/Voice的今日反馈没有合入main。持续热度与持续代码变化不是同义词。今天最有用的新信息是接口与权限边界被具体定位，而非给相同README换写一遍简介。
