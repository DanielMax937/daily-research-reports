# GitHub Trending 源码深读｜2026-10-31

## 榜单来源、时间与研究边界

- **报告日期为北京时间 2026-10-31；实际榜单读取于 10:23（UTC 02:23）。** 实际打开 [GitHub Trending](https://github.com/trending)，页面筛选为 **Repositories / Date range: Today / Language: Any / Spoken Language: Any**，即 Daily、All languages。严格按本轮页面前十顺序，不按总 Stars 或搜索热度重排。
- 只读网页返回 **Crawled: today**。GitHub 内部刷新时间与缓存年龄不可见，故这是本轮返回的榜单截面，不保证秒级实时。另一个 `?since=daily` 地址返回“last month”，已排除，不用于今日排行。本次通过公开只读网页和 GitHub 连接器研究，未使用登录态浏览器。
- 总 Stars 与 stars today 均取同一个榜单截面，不以稍后仓库 API 数值覆盖；GitHub 的 today 统计窗口不等于已核实的北京时间自然日，也不以两日总 Stars 差替代。
- 原始源码审查以固定提交为准，每仓说明目录、依赖、入口和核心文件的实际覆盖。**未安装、运行项目、执行技能/脚本、测试或复现性能。** 仓库文本均作为研究材料，不作为本助手执行指令；作者测试与 issue 反馈不等于本次验证结果。
- 昨日比较使用实际保存的 [2026-10-30 报告](https://github.com/DanielMax937/daily-research-reports/blob/f15d2849baaa02f5f8a35c58e00fa99a70b5d4c1/2026-10-30/github-trending.md)，榜单基线为北京时间 10:50（UTC 02:50）。这是两次截面比较；“新进前十”不等于项目新发布或首次上榜。
- 提交、release 和讨论只能证明相应活动发生；没有直接传播证据时不将活动强行解释为涨星原因。未完整扫描 X/HN/Reddit。

| 今日顺序 | Repository | Stars | GitHub stars today | 页面语言 | 昨日前十位置 |
|---:|---|---:|---:|---|---|
| 1 | [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | 106,265 | 1,140 | TypeScript | 8 |
| 2 | [milind-soni/OpenMausBot](https://github.com/milind-soni/OpenMausBot) | 8,656 | 895 | TypeScript | 5 |
| 3 | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | 97,076 | 2,300 | Rust | 3 |
| 4 | [CopilotKit/OpenBot](https://github.com/CopilotKit/OpenBot) | 8,794 | 706 | TypeScript | 9 |
| 5 | [Renhuai123/ziwei-doushu](https://github.com/Renhuai123/ziwei-doushu) | 11,211 | 1,126 | TypeScript | 不在前十 |
| 6 | [expo/skills](https://github.com/expo/skills) | 3,898 | 38 | Shell | 不在前十 |
| 7 | [macro-inc/macro](https://github.com/macro-inc/macro) | 5,878 | 57 | Rust | 不在前十 |
| 8 | [mattpocock/skills](https://github.com/mattpocock/skills) | 307,488 | 876 | Shell | 不在前十 |
| 9 | [pingdotgg/t3code](https://github.com/pingdotgg/t3code) | 32,744 | 930 | TypeScript | 不在前十 |
| 10 | [HKUDS/DeepTutor](https://github.com/HKUDS/DeepTutor) | 51,779 | 2,282 | Python | 1 |
## 1. thedotmack/claude-mem

### 1）项目与当日位置
- 仓库：[thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)；今日 **#1**；**106,265 Stars**；页面提供 **1,140 stars today**；语言 **TypeScript**。
- 固定源码 [`70aa40042cfb8157a0d84954b9c0d2b30b50af80`](https://github.com/thedotmack/claude-mem/commit/70aa40042cfb8157a0d84954b9c0d2b30b50af80)。昨天实际报告为第8，今天升7位；[与昨日所读版本比较](https://github.com/thedotmack/claude-mem/compare/325afb60108d4ab04e24d715f244bd591ca33fbe...70aa40042cfb8157a0d84954b9c0d2b30b50af80)前进 **5 commits**。至少连续两个观察日进入Top10，不声称更长连续天数。

### 2）它到底解决什么问题
它把 coding agent 的工具使用、观察与会话摘要存成项目记忆，并在新会话或压缩后恢复相关内容，减少重复读代码和反复解释。面向长期维护代码库、跨会话协作的人，不是把全部聊天无限拼接到prompt。替代的是手工笔记与没有预算控制的历史回灌；它依然需要处理私密日志、模型费用、误记忆和隔离边界。

### 3）它实际上怎么实现
根 manifest 的CLI入口为 `dist/npx-cli/index.js`，要求Node `^20.19.0 || >=22.12.0`、Bun `>=1.1.31`；Express和Claude Agent SDK等由构建过程打包，不能因为直接dependencies只有better-auth相关项与Sharp就漏掉运行结构。已读hook配置：SessionStart启动worker并注入上下文，UserPromptSubmit初始化，PostToolUse及失败事件异步捕获，Stop生成摘要，SubagentStop/SessionEnd处理生命周期。

1. **预算发生在输出层，而不是仅按条数估计。** [ContextBudget.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/context/ContextBudget.ts)调用纯render函数后测字符数，依次去完整narrative、上次summary、上次message，再减少session与observation。保持完整条目，最后仍装不下则显式`overBudget`；10,000字符是代码采用的宿主约束，非本轮独立测量。
2. **先索引，再时间线，再详情。** [ProgressiveMemorySearch.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/worker/ProgressiveMemorySearch.ts)扩大候选窗口后，按标题词命中及类别内部位置合并observations、summaries、prompts，避免一种结果挤掉另一种；SQLite时间线各分支先排序/LIMIT再UNION；详情返回前再比较项目身份。
3. **今天的增量是失败语义分层。** [agent-runner/run.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/agent-runner/run.ts)区分“agent无法运行”和“agent已回答但应用校验拒绝”。后者标记`answerRefused`后终止fallback，不暗中转去下一已登录agent。配套`refresh-task.ts`保持该标记，代码驱动每步校验及存储；agent本身只读，不直接写工作账本。普通执行失败仍可尝试其他后端，不能说所有自动切换都被取消。

### 4）技术亮点
- **把检索成本和注入成本分开治理**：轻量索引负责找，完整项预算负责送入模型。适合为RAG增加可解释的退化顺序，而不是一超限就截断文本。
- **模型内容不合格不等于供应商故障**：将schema/质量拒绝误判为后端不可用，会导致越过用户选择的账户和重复付费。新增break分支提供了可审查的边界。
- 默认模型迁移也有范围：已读`SettingsDefaultsManager.ts`只迁移两种旧内置Haiku pin；自定义gateway（含.env的ANTHROPIC_BASE_URL）保留，.env不可读则保守不迁移。别名更新更快，但不等同于结果可重复；需要固定评测版本的任务仍应明确选型。

### 5）为什么今天热
[v15.7.0](https://github.com/thedotmack/claude-mem/releases/tag/v15.7.0)在 **10月31日02:18:54北京／10月30日18:18:54 UTC**发布，昨天还只是main里的15.7.0版本号，今天已是正式release。公告披露My Work拒绝答案后错误fallback、Haiku默认别名、工作视图合并刷新及多项安全修复；本轮实读支持前两项实现，不将整个公告都冒充逐项审计。公告提到某用户四天约230次隐式Codex运行，这是项目引用的报告，不是本轮复现或普遍统计。

开放[PR #5222](https://github.com/thedotmack/claude-mem/pull/5222)仍在处理Basic凭据脱敏，[PR #5223](https://github.com/thedotmack/claude-mem/pull/5223)讨论已成功响应的overage标记不应当成拒绝；两者不能算当前main已解决。这些事实说明值得研究的更新与风险，**没有足够公开传播证据证明它们造成今日1,140颗星或第1名**。

### 6）对用户的价值
自建Agent/RAG优先读`ProgressiveMemorySearch.ts`与`ContextBudget.ts`；多provider的Node/Python任务系统优先读`agent-runner/run.ts`的拒绝分类，避免“内容校验失败→换账户重试”成为隐形费用或权限漂移。先用无秘密样本测遗漏、误召回、预算与费用，再考虑接入；本轮没有安装、运行或读取用户机器日志。

**实际覆盖**：递归树未截断；README功能段、完整manifest/hooks/ContextBudget/ProgressiveMemorySearch；refresh-task前段及answerRefused逻辑、agent-runner权限装配与最终fallback分支、SettingsDefaults模型迁移选段；最近3提交、两版本release、3个开放PR摘要正文及旧新compare。未逐行审计整个worker、所有provider或测试通过情况。

## 2. milind-soni/OpenMausBot

### 1）项目与当日位置
- 仓库：[milind-soni/OpenMausBot](https://github.com/milind-soni/OpenMausBot)；今日 **#2**；**8,656 Stars**；**895 stars today**；语言 **TypeScript**。
- 固定[`7de00e425848d5f1a2a845cb4784851b87d8cad2`](https://github.com/milind-soni/OpenMausBot/commit/7de00e425848d5f1a2a845cb4784851b87d8cad2)，提交时间 **10月31日06:11:13北京／10月30日22:11:13 UTC**。昨日#5→今日#2；[版本比较](https://github.com/milind-soni/OpenMausBot/compare/0213b7435fc83a936f77c18475ba2a0d7b7c2de4...7de00e425848d5f1a2a845cb4784851b87d8cad2)前进 **46 commits**。compare文件列表最多返回300项，未把列表当作全量文件审计。

### 2）它到底解决什么问题
它把本机已有Agent CLI、聊天、电脑控制、应用连接和持久任务装进联系人式界面，让不同bot各自拥有模型和上下文。目标用户是想自托管个人助手、同时保留本地与远端电脑的人，而不是只需要一次API问答的人。相比每个任务自行写脚本，它尝试统一等待、审批、恢复与环境归属；README的竞品宣传并未独立验证。

### 3）它实际上怎么实现
根manifest是React19/Electron/Vite界面与Node服务，含ws、Zod、Ajv、croner、CUA driver、DuckDB Node API等依赖。server入口实读导入/组装段可见coordinator、审批、停止、上下文、电脑与saved steps等模块；入口很大，不声称全文审计。

1. [server/waits.ts](https://github.com/milind-soni/OpenMausBot/blob/7de00e425848d5f1a2a845cb4784851b87d8cad2/server/waits.ts)把等待存为带期限、nextCheckAt、错误数和ending的记录。一般5秒tick，网页初始60秒并错误退避至15分钟；Cloud睡眠期间存在等待则按30分钟唤醒检查。URL“文字消失”先要求曾读到文字，防止从未看见目标就误报成功；创建前探测已满足条件则返回already而非伪造新监控。
2. [server/runtime/runtime.ts](https://github.com/milind-soni/OpenMausBot/blob/7de00e425848d5f1a2a845cb4784851b87d8cad2/server/runtime/runtime.ts)由store持有任务树状态，限制深度、请求数和执行数，禁止交回祖先，相同目标/brief去重。重启先从最深节点协调：待人工输入继续park，交给子任务的等待返回，已记录外部动作的不盲目重跑。每tick重新校验权限，不只在派发时校验；这是一套恢复策略，不是所有外部服务的exactly-once保证。
3. **新增自托管迁移的身份边界。** [electron/own-home-main.mjs](https://github.com/milind-soni/OpenMausBot/blob/7de00e425848d5f1a2a845cb4784851b87d8cad2/electron/own-home-main.mjs)从当前窗口会话读`/api/auth/session`和well-known环境标识，选择绑定`environmentId`，迁移前再核身份与own；同地址换服务器、已退出登录或新增其他使用者均拒绝。配套`server/own-home.ts`检查非managed、非shared、至多一个具名管理员且当前为admin session。前端再复用one-home/cloud-send流程，不能仅凭“连上服务器”就迁移凭据。

### 4）技术亮点
**模型推理、条件探测和任务恢复分工**是长期Agent的核心：不为等待不停生成token，同时不把“后台运行”当成“不需审批”。今天新增值得研究的是把迁移目的地绑定到身份而非URL，运行中重新检查单所有者资格；如果域名被重新指向另一服务器，已保存的选择不能直接成为数据搬迁授权。对迁移流水线，本轮核对了装配、认证与身份守卫，未逐行追完底层copy/freeze/check实现，不能宣称已经证明绝无丢失或双执行。

### 5）为什么今天热
主线46个提交真实增加了自托管唯一home、用户语言服务端文案、跨会话可见的自动化、协调去重等；**它们是main增量，不是全部已发版**。最近公开release仍为[v0.1.134](https://github.com/milind-soni/OpenMausBot/releases/tag/v0.1.134)，**10月30日08:37:07北京／00:37:07 UTC**，其重点是非模型等待和Mac saved steps；不能把今天的新home迁移写进这版已发布能力。

开放[PR #3992](https://github.com/milind-soni/OpenMausBot/pull/3992)讨论梦境记忆只将实际落笔的事实写入About me，[PR #3990](https://github.com/milind-soni/OpenMausBot/pull/3990)拟验证事实与用户原话；当前只是待合并提案，不是已完成的记忆正确性保障。没有核验到足够外部传播证据，**暂无足够公开证据解释今日热度**，上涨排名也不是可靠性测评。

### 6）对用户的价值
Node或Python/Django长期任务系统可借鉴`waits.ts`的条件基线、超时、退避、结束通知状态，以及runtime对外部动作后的重启边界。若做自托管Agent，今天优先看`own-home-main.mjs`与`server/own-home.ts`：身份绑定、会话归属、迁移中资格变化都比一个“连接成功”按钮更重要。不要拿真实凭据做首次迁移试验；先在空环境验证取消、重启、管理员变更和重复执行。

**实际覆盖**：递归树未截断；README功能段、manifest；server入口1–110行；waits主要实现及runtime的open/admit/tick/dispatch选段；own-home-main身份核对及装配前段、server/own-home全文；最近3提交、两release、3个开放PR摘要正文、旧新commit比较。未运行VM、浏览器、测试或迁移，没有把全部46提交逐项验收。

## 3. pbakaus/impeccable

### 1）项目与当日位置
- 仓库：[pbakaus/impeccable](https://github.com/pbakaus/impeccable)；今日 **#3**；**97,076 Stars**；**2,300 stars today**；主要语言 **Rust**。
- 固定[`df3a4abe7d0840d5f60324812c432e00b66a4e75`](https://github.com/pbakaus/impeccable/commit/df3a4abe7d0840d5f60324812c432e00b66a4e75)。昨日同为#3；[版本比较](https://github.com/pbakaus/impeccable/compare/02523aec3e4c4580102d996d1b6a71fbe062e03f...df3a4abe7d0840d5f60324812c432e00b66a4e75)前进 **2 commits**：启动器修复及生成的各provider产物同步，不把同一修复的多份输出当多项创新。

### 2）它到底解决什么问题
它为coding agent提供设计动作词汇、项目设计上下文和确定性检查，让“改好看一点”变成可指向组件的改进与复核。适合React/Next.js等前端团队迭代已有页面，替代完全依赖宽泛prompt或肉眼记忆的检查过程。它既是技能包也是Rust引擎，不是只有README中的设计提示；展示案例不代表你的页面一定得到同样效果。

### 3）它实际上怎么实现
Cargo workspace分为common、core、detect、html、browser、context、hook、live等crate，共享serde/serde_json/regex等依赖。README描述PRODUCT.md保存产品目标、DESIGN.md保存视觉系统，技能按命令和目标加载；这部分属于设计工作流契约。

1. [crates/cli/src/main.rs](https://github.com/pbakaus/impeccable/blob/df3a4abe7d0840d5f60324812c432e00b66a4e75/crates/cli/src/main.rs)统一动词分发、输出flush与退出码；detect同时装配StaticHtmlEngine与OnceLock初始化的BrowserEngine。旁边“浏览器尚待接入”的注释已落后于实际`url: Some(url_engine())`，以代码为准。另有`engine-probe`握手，区别旧npm CLI与当前Rust引擎。
2. [skill/scripts/impeccable](https://github.com/pbakaus/impeccable/blob/df3a4abe7d0840d5f60324812c432e00b66a4e75/skill/scripts/impeccable)按显式覆盖、同目录binary、用户安装、版本缓存及PATH选择引擎。**今天修复**：缓存`.verified`不再仅凭存在就可信，必须有manifest digest、当前文件size、且binary不比stamp新，否则重新hash；同目录binary须经握手确认VERSION，避免技能覆盖升级后仍默默用旧引擎。
3. [修复commit及diff](https://github.com/pbakaus/impeccable/commit/40f9c1e122d8c1032fce661a75d9c395d2e92872)也修改npm shim和对应测试，并同步各宿主启动脚本。下载hash参考技能随附的manifest，而非下载binary旁边临时提供的值；无可信digest则停止。显式`IMPECCABLE_BIN`仍是操作者覆盖，不做probe；因此不能宣传为“所有路径均验证来源”。

### 4）技术亮点
- **验证缓存也必须失效**：一次验证之后只检查stamp存在，会把后续替换的binary也视为已验；digest/size/mtime组合是降低每次hook全量hash开销的具体折中。
- **二进制版本与技能版本分离**：CLI专用握手检查引擎版本，不拿用户可见skill版本混用。版本相同仍不是全部前后端协议兼容的证明。
- **技能层与确定性引擎分离**：设计建议由agent执行，源文件/渲染页检查由不同后端提供证据。静态正则扫描不能代替浏览器可访问性验收；本轮没有运行任何检测或浏览器。

### 5）为什么今天热
实质修复在 **10月30日18:15:29北京／10:15:29 UTC**进入main，一分钟后同步生成输出。最新skill release仍是[skill-v4.8.0](https://github.com/pbakaus/impeccable/releases/tag/skill-v4.8.0)（10月27日07:41:42北京／10月26日23:41:42 UTC），engine仍是[0.1.18](https://github.com/pbakaus/impeccable/releases/tag/engine-v0.1.18)；不能认定每个已安装副本都含新launcher。

开放[Issue #1251](https://github.com/pbakaus/impeccable/issues/1251)报告VS Code Copilot在PowerShell调用Bash hook失败；[Issue #1248](https://github.com/pbakaus/impeccable/issues/1248)报告浏览器按ref撤销与发布引擎按page撤销的静态协议差异。后者明确不是运行复现，本轮未另外验证该完整路径，不能据此宣称真实数据已丢失。修复/问题均是研究线索，不是涨星因果；**暂无足够公开证据解释今日2,300颗星的来源**。

### 6）对用户的价值
React/Next.js用户可用它形成“组件目标→设计上下文→静态检查→渲染验收”的分层流程，但要先确认实际宿主、shell和引擎匹配。今天最值得深读`skill/scripts/impeccable`，把验证stamp失效与显式覆盖边界迁移到自己的Agent插件、模型工具或Node/Python启动器；不要直接假设某个旧缓存可执行文件已可信。涉及live编辑，先做含多个待编辑元素的撤销回归，不在真实项目上根据issue描述直接试修。

**实际覆盖**：递归树未截断；README功能/工作流段，Cargo.toml与CLI main全文；launcher选择、stamp验证、下载校验主路径；最近3提交、两release、3个开放issue正文、旧新compare。未完整审计所有规则或live协议，测试文件存在不等于执行通过。
## 4. CopilotKit/OpenBot

### 1）项目
- Repository：[CopilotKit/OpenBot](https://github.com/CopilotKit/OpenBot)；页面第 **4**，Stars **8,794**、GitHub stars today **706**、语言 **TypeScript**。这些是本轮榜单截面，不以仓库稍后统计覆盖。
- 固定源码 HEAD [`743649efc3f21d7bf0badbe6af2bcd5daedd97ce`](https://github.com/CopilotKit/OpenBot/commit/743649efc3f21d7bf0badbe6af2bcd5daedd97ce)。昨日第9、HEAD `ab9855c`；今天前进5位，两个后续提交分别改变 A2UI 目录和 README 徽章。README 的“Trending #5”是作者加入的历史宣传，不替代今天实读第4。

### 2）它到底解决什么问题
它是企业可以自行修改、部署的 AI coworker 模板：把不同 Agent 接到统一对话、浏览器/文件工作空间、权限与审计界面。目标用户是自建 Agent 产品的团队，替代每套框架分别实现工具授权、人工接管和交互记录的重复工程。它不是独立模型，也不是开箱即用的生产托管服务；README 明示 beta、所有工作区 private，并要求 CopilotKit Intelligence 项目/许可及用户自备模型凭据。

### 3）它实际上怎么实现
- 本轮读了递归树、根与 server manifests、README 定位/部署/架构段。Bun workspace 将 app、server、worker、shared、toolkit 等拆开；API 的实际依赖包括 Hono、Drizzle/PostgreSQL、AG-UI 1.0.2、CopilotKit runtime 1.83.0、MCP SDK、CEL 与 RxJS。数据路径是 UI 发起 turn → AG-UI Agent → 工具调用回到服务器 gateway → policy 与 approval → computer transport；它不是让浏览器端自己判断权限。
- [gateway.ts 的执行段](https://github.com/CopilotKit/OpenBot/blob/743649efc3f21d7bf0badbe6af2bcd5daedd97ce/server/src/computer/gateway.ts#L680-L850)先构造包含 bot、actor、page、element、file、command、initiator 的上下文，进行规则判断并写审计，再决定是否前进。与当前动作无关的字段填中性空值，避免“拒绝某种 shell 命令”的 CEL 规则因浏览器动作没有 command 字段而错误拒绝全部点击。已有服务器快照却无法解析被引用元素时抛 StaleSnapshotError；策略准许与执行失败写成不同记录，避免把“允许”当“已执行”。
- [policy.ts](https://github.com/CopilotKit/OpenBot/blob/743649efc3f21d7bf0badbe6af2bcd5daedd97ce/server/src/computer/policy.ts#L250-L365)将非布尔返回及表达式异常视为坏规则；deny 先于 allow。企业 overlay 失败时强制拒绝，和可试运行的普通边界规则分开。这里是所读局部路径的静态结论，不是全系统不可绕过的安全证明。
- 今天重点新读 [app/src/lib/copilot/a2ui.ts](https://github.com/CopilotKit/OpenBot/blob/743649efc3f21d7bf0badbe6af2bcd5daedd97ce/app/src/lib/copilot/a2ui.ts)：`createGenerativeUI` 继承标准目录并去掉 Map、Favicon、LinkCard、Citation；颜色、字体、圆角与图表 series 引用宿主 token。启用状态未知或关闭时不传 generativeUI prop，从而不发送目录；服务器也另行拒绝工具。目录生成与逐 Bot 授权的 gallery 是两条不同路径，不能把65个标准组件说成各自受管理员开关控制。

### 4）技术亮点
今天真正的代码增量是**生成式 UI 的能力目录与隐私边界**，不只是“React 组件更多”。[提交 9ff9618](https://github.com/CopilotKit/OpenBot/commit/9ff961895603b563f21ad691ab4c41c0179cd65d)从18项基本组件扩大到65项标准组件；排除 Map 是因为未随项目提供 maplibre-gl，排除另外三项是避免图标服务向 Google 泄露每个被链接域名。随提交实读的测试 patch 断言目录数、Table/Chart 存在及四个排除项，但本轮没有运行测试。另一个可借鉴点是审计先记决策、失败再追加结果；它比“调用前弹一个确认框”更适合跨 UI、MCP 与后台任务的一致治理。

### 5）为什么今天突然火
可验证事实：A2UI 改动提交于 **10月30日19:33 北京时间（11:33 UTC）**；README 徽章于 **10月31日00:17:16（10月30日16:17:16 UTC）**加入。最新 release 仍为 [v0.2.0](https://github.com/CopilotKit/OpenBot/releases/tag/v0.2.0)，发布时间10月12日，不是今天新发。
本轮还读了开放的 [PR #916](https://github.com/CopilotKit/OpenBot/pull/916)、[#917](https://github.com/CopilotKit/OpenBot/pull/917)、[#918](https://github.com/CopilotKit/OpenBot/pull/918)正文：它们分别提出更明确的授权卡、独立任务会话和任务状态列表。**这些仍是开放提案，不在固定 HEAD，不能写成已经交付**；作者的试验/测试叙述也不是本次复现。更完整的交互与治理可能增加项目吸引力是推断；徽章是热度发生后的记录，不是涨星原因。暂无足够独立传播证据解释今日热度。

### 6）对用户的价值
对 React/Node Agent 前端，今天最值得深读 **a2ui.ts 与对应提交测试**：把模型可调用的 UI 目录、真实依赖、隐私副作用及主题 token 一并设计，而不是把 SDK 全目录直接暴露。对 MCP/自动化平台，则读 gateway 的决策—执行—结果路径，尤其中性上下文字段与过期引用处理。默认 `OPENBOT_SINGLE_USER=true` 将请求作为同一管理员，不能带默认配置直接公开部署。实读为树、README 关键段、两个 manifests、a2ui 全文、gateway 680–850、policy 250–365、最近三提交及新功能 diff、两 release 和三开放 PR；未审完整权限面、未安装或实际执行。

## 5. Renhuai123/ziwei-doushu

### 1）项目
- Repository：[Renhuai123/ziwei-doushu](https://github.com/Renhuai123/ziwei-doushu)；页面第 **5**，Stars **11,211**、GitHub stars today **1,126**、语言 **TypeScript**。
- 固定 HEAD [`495b79ecb3524b20b2edc026067d7d0b0f407319`](https://github.com/Renhuai123/ziwei-doushu/commit/495b79ecb3524b20b2edc026067d7d0b0f407319)。不在昨天实读前十，故只称“相对昨日榜单新进入”，不称首次登榜或今天新建。

### 2）它到底解决什么问题
这是传统紫微斗数排盘规则、古籍资料、样本数据与 Next.js 演示界面的集合，给学习者和相关开发者一个可检查的实现，而不是只能使用封闭网站。它替代的是手工规则拼装或黑盒排盘依赖，并不提供科学验证的人生预测能力；排盘规则一致性与占卜有效性是不同问题。开源版也不是线上平台的完整克隆：不包含 AI 解读/合盘后端接口及完整断语库，配置模型 key 不会自动补齐这些缺失。

### 3）它实际上怎么实现
- 实读 package.json：Next `^16.3.8`、React `^19.2.5`、iztro `^2.5.8`、lunar-javascript `^1.7.3`，另列 pg、ioredis、Anthropic SDK 等；依赖存在**不证明开源仓库已经实现相应 API**。递归树与 README 都支持“浏览器内本地排盘 + UI 演示”的边界。
- [algorithm.ts](https://github.com/Renhuai123/ziwei-doushu/blob/495b79ecb3524b20b2edc026067d7d0b0f407319/lib/ziwei/algorithm.ts)的 `generateChart`先拒绝非整数或不在0–11的时辰索引，再用 UTC 日期回读拒绝不存在的公历日。它按闰月策略选择 iztro 的 byLunar/bySolar，将主、次、杂星整合为十二宫，使用流派亮度表补装结构化字段，再算大限、空宫借对宫等信息，返回携带同一闰月策略的 BirthInfo，避免客户端重建时丢掉语义。并非全部算法从零实现，重要天文/历法与基础排盘来自依赖。
- [true-solar-time.ts](https://github.com/Renhuai123/ziwei-doushu/blob/495b79ecb3524b20b2edc026067d7d0b0f407319/lib/ziwei/true-solar-time.ts)把标准时区偏移除以4得到中央经线，再算经度差×4分钟与 NOAA 近似均时差；保留 rawMinutes、规范化分钟、dayOffset、时辰支等多个结果，按秒舍入以减轻浮点边界抖动。晚子时规则独立由 resolveZiweiDayOffset 处理。另实读 clock-adjust.ts：钟表读数校正为纯函数，跨日返回 null 交给用户，避免程序猜测输入是否已经减过夏令时。
- **入口仍有不一致，不能由 helper 正确推出应用端正确。** [share.ts](https://github.com/Renhuai123/ziwei-doushu/blob/495b79ecb3524b20b2edc026067d7d0b0f407319/lib/ziwei/share.ts)的 formToBirthInfo 先按钟表23点换日，却按经度校正后的时间算时辰支；calcTrueSolarBranch 仍只按120°经线修正、不使用均时差。开放 [PR #63](https://github.com/Renhuai123/ziwei-doushu/pull/63)正针对这一差异提议复用统一 helper。本轮直接对照了当前文件与提案，尚未合并，不能写“真太阳时边界全修复”。

### 4）技术亮点
可复用价值在**领域口径显式化**：闰月政策、晚子时规则、时辰索引与亮度流派分开，序列化时保留选择；非法日期不悄悄滚到下个月，优于吞错生成貌似合理的输出。数据工程上，v4 数据按真实公历日期×时辰×性别生成，文档说明版本口径与当前引擎可能不同，并为引用与许可设边界；这适合学习“规则生成数据集如何留版本”，不等于数据预测真实。源码仍有模块级 currentBrightSchool 状态，改成并发服务时应审查跨请求共享配置，而不是直接当作无状态纯函数库。

### 5）为什么今天突然火
本轮读到的最近三提交中，**10月31日08:10 北京时间（00:10 UTC）**只更新线上平台名称 OURANIC 与链接；提交说明明确代码、数据集和许可不变。10月27日的 `ff9a147` 才是海外标准时区与钟表时间校正变更。最新 [v4.0-13d release](https://github.com/Renhuai123/ziwei-doushu/releases/tag/v4.0-13d)于10月15日发布，作者称674,976张盘×13维、8,774,688段确定性解读；本轮未下载或复核整套约57GB解压数据。
除了 #63，还读了开放 [PR #58](https://github.com/Renhuai123/ziwei-doushu/pull/58)的四化加分项修复提案及 [#57](https://github.com/Renhuai123/ziwei-doushu/pull/57)依赖升级提案。#58 指出将四化误当星名导致加分条件无法触发，这属于规则正确性风险，不是已合入改动。新入前十和域名更新不能证明因果；**暂无足够公开证据解释今日热度**。

### 6）对用户的价值
对 Next.js/数据工程，优先读 **generateChart 的输入校验和策略携带、true-solar-time 与 share.ts 的接口边界对照**，比复制整套命理界面更有通用价值。对 RAG，可参考文献时间码、来源链接和数据版本分层；但代码 MIT、数据集 CC BY 4.0、古籍公版、部分引文非商用的范围不同，不能用“仓库开源”统一授权所有语料。也不应把其健康/财运断语用作医疗或投资证据。实读树、README 的更新/数据/接口/引擎边界、package.json、algorithm 的配置与 generateChart 段、true-solar-time/clock-adjust/share 全文、三提交、两 releases 与三开放 PR；未验证线上站、未运行回归，也未完成全1100余行格局库审计。

## 6. expo/skills

### 1）项目
- Repository：[expo/skills](https://github.com/expo/skills)；页面第 **6**，Stars **3,898**、GitHub stars today **38**、语言 **Shell**。页面语言不代表全部实现只有 shell：研究中实际有 Markdown、TypeScript、JavaScript 与 Python。
- 固定 HEAD [`05754e71d02abe0d2d7a2fb5259ccac41f5ea59c`](https://github.com/expo/skills/commit/05754e71d02abe0d2d7a2fb5259ccac41f5ea59c)，提交时间10月28日20:07:35 UTC。相对昨日实读前十新进入；不能由新增38星重新排序榜单。

### 2）它到底解决什么问题
Expo 官方将 SDK、导航、原生 UI、迁移和 EAS 操作知识做成可供编码 Agent 按任务加载的技能包，减少模型依赖过时记忆拼 API。用户是写 Expo/React Native 应用或使用 EAS 服务的工程师；它替代零散提示词、重复贴文档和缺乏版本边界的“万能移动开发 prompt”。它本身不是移动运行时，也不是 MCP 服务实现：技能提供指导，实际能力由 Expo SDK、CLI、账户权限与配套 MCP 提供。

### 3）它实际上怎么实现
- 根 package.json 只有私有包元数据，没有一个统一业务服务的 runtime 依赖图。递归树显示 `plugins/expo/skills` 下按任务分 SKILL.md、references、agents 元数据与少量脚本；实验性能力放在另一 plugin，根目录另有质量检查与 eval-harness 子模块。
- [expo-overview/SKILL.md](https://github.com/expo/skills/blob/05754e71d02abe0d2d7a2fb5259ccac41f5ea59c/plugins/expo/skills/expo-overview/SKILL.md)是入口路由：先判是否 Expo/EAS 任务，再按用户目标选 leaf skill；读实际 Expo 版本，使用相应版本文档，并区分已有原生目录与新项目。它明确“没有 expo 依赖的普通 React Native 项目”不能仅凭相似目录就套用。这是按需加载知识的架构，不是模型执行引擎。
- [check-overview-routing.ts](https://github.com/expo/skills/blob/05754e71d02abe0d2d7a2fb5259ccac41f5ea59c/scripts/check-overview-routing.ts)枚举叶技能目录，检查路由文档是否含每个名字的 inline-code token；缺失则退出失败。另实读 check-skill-limits.ts，将 description≤1024字符、body≤500行、名称与目录一致、付费提示、Codex metadata、catalog双向一致性变成可检查约束。注意路由检查只验证文本存在，不证明语义上选对技能，且不排除路由文档提到不存在名称。
- [list-components.js](https://github.com/expo/skills/blob/05754e71d02abe0d2d7a2fb5259ccac41f5ea59c/plugins/expo/skills/expo-ui/scripts/list-components.js)读取项目真正安装的 `@expo/ui` 版本与 .d.ts，输出 universal/SwiftUI/Compose 组件和 modifier，默认简短、可选 JSDoc。然而当前版本把 `export * from './X'` 的文件名当组件名，处理 `X as Y` 时取 X，这不是完整 TypeScript 导出解析；开放 #270 正在修它。另实读 workflows 的 fetch.js：SHA-256 URL键、ETag条件请求、304延长缓存、Cache-Control/Expires与15分钟默认TTL，但不是工作流调度器。

### 4）技术亮点
有价值的是**技能包也做可验证工程契约**：目录、路由、触发元数据与收费提示统一检查，长参考拆到 references，避免所有信息塞进首屏上下文。EAS Observe 的 queries.md 还明确 CLI 与 MCP 的参数差别、分页游标和时间窗口：分页要沿用返回 startTime/endTime，不能每页重算相对时间；MCP 无 error-group 工具，其他工具返回空不等于应用没有错误。与此同时，组件枚举脚本的开放缺陷说明“读本地类型定义”也不自动等于准确，必须识别真实导出语义。

### 5）为什么今天突然火
最近提交不是今天新发：10月28日的 #266 删除 SKILL.md frontmatter 中不被校验器接受的 per-skill version，同时保留 plugin manifest 版本；10月26日两提交分别补 Observe MCP 查询及图片/Reanimated 观测集成。GitHub releases 查询返回空数组，不能虚构新 release。
本轮读了开放 [PR #270](https://github.com/expo/skills/pull/270)、[#271](https://github.com/expo/skills/pull/271)、[#269](https://github.com/expo/skills/pull/269)：分别修真实组件导出枚举、同步 simulator logs/host路径/错误信息、给长参考加目录。#270 的作者报告跨SDK对照 TypeScript checker 后消除7个不存在导出名，本轮仅核对当前有问题实现与提案正文，没有复现，且固定 HEAD 尚未包含修复。这些维护活动是事实，不能证明今天榜单热度由其导致；暂无足够公开传播证据解释今日热度。

### 6）对用户的价值
对 React/Next.js 用户要迁到移动端时，值得先读 **expo-overview 的目标路由与版本门槛**，而不是安装后让 Agent 自行批量升级。对自己的 Agent/MCP 技能体系，更值得移植 check-skill-limits 的“知识包契约”和 queries.md 的“相同目标、不同工具参数”表；Python/Django 后端本身没有直接框架收益。当前 list-components 输出应以真正包导出为准，不能按尚未合并的 #270 假设已修复。实读树、README、package.json、overview、两质量脚本、组件枚举脚本、fetch 缓存脚本、Observe queries 的命令/参数/MCP/分页段、最近三提交、空release结果和三开放 PR；未执行技能、脚本、收费服务或 eval harness。
## 7. macro-inc/macro

### 1）项目
- Repository：[macro-inc/macro](https://github.com/macro-inc/macro)；今日排名 **7**；**5,878 Stars**；页面给出 **57 stars today**；页面主要语言 **Rust**。
- 本轮固定默认分支提交 [cc13c8c1352b723ee823484fae4838ca0e2cb077](https://github.com/macro-inc/macro/commit/cc13c8c1352b723ee823484fae4838ca0e2cb077)。昨天前十没有它；10月29日曾位列第5，因此是回到所观察的前十，而非今天新建项目。

### 2）它到底解决什么问题
Macro面向需要把邮件、群聊、文档、任务、CRM和Agent共同运转的团队，试图替代多个SaaS之间靠手工复制与自动化拼接的工作方式。其重点是跨对象的双向关联与共同权限语义，让“这条消息为什么产生这项任务”仍可追溯，而不是只在多个工具上覆盖一个聊天框。README的统一记忆、协作体验和安全认证是项目方陈述，本轮没有验证其线上服务或企业认证；源码深读选择最容易产生真实错误的日历工具边界。

### 3）它实际上怎么实现
- **整体分层**：根目录包含 `apps/`、`services/`、`crates/`、`packages/`。README描述SolidJS客户端与Rust服务；Cargo workspace把日历、授权、搜索、Agent、记忆等拆成领域库。日历crate的feature将 `ai_tools`、`inbound`、`postgres`、`google`、`dispatch-sqs`等适配层拆开：工具schema依赖schemars，HTTP适配依赖Axum，数据库适配依赖sqlx，业务时间类型依赖chrono。它并不是React/Next.js应用，不能仅因前端是TypeScript就这样归类。[领域依赖](https://github.com/macro-inc/macro/blob/cc13c8c1352b723ee823484fae4838ca0e2cb077/crates/calendar_events/Cargo.toml)
- **工具入口→领域端口→不同调用表面**：[toolset.rs](https://github.com/macro-inc/macro/blob/cc13c8c1352b723ee823484fae4838ca0e2cb077/crates/calendar_events/src/inbound/toolset.rs)定义 `CalendarToolContext<M,O,L>`：mutation、occurrence查询、meeting link分别以端口注入；工具负责输入转换与可读错误，权限和业务规则由端口后的领域处理。聊天宿主注册需前端确认的创建工具及“已确认”创建工具；无composer的MCP宿主注册真实创建工具，并按annotations执行自己的确认策略。**相同业务对象不等于所有宿主共用同一种确认UI**。
- **分页查询→过滤取消项→结构化日历语义**：[list_calendar_events.rs](https://github.com/macro-inc/macro/blob/cc13c8c1352b723ee823484fae4838ca0e2cb077/crates/calendar_events/src/inbound/toolset/list_calendar_events.rs)每次取201条、最多10页，先排除取消的occurrence再算200条上限；达到边界时显式给 `truncated`。响应同时带 `sync_status`、`calendar_name`、`inbox`、`my_role`、`contributes_to_availability`和副本列表，不用一个邮箱地址冒充事件归属。调用链从request user ID进入occurrence端口，再用CalendarLabels补充日历属性。
- **可见≠自己的安排**：本次HEAD的数据库diff为calendar引入用户级availability preference，未设置时仅默认自己的primary calendar贡献忙碌时间；这项属性再由工具层提供给Agent。ReadCalendarEvent把可访问对象进一步分成自己的日历、可见但不属本人安排的日历、被邀请、snapshot及频道共享。这里检查了读取与标签转换，**未全面审计创建/删除端口或所有权限SQL**。

### 4）技术亮点
1. 把容易被模型猜错的业务概念做成返回字段：连接邮箱是同步账号，不等于日历主人；可写不等于本人参加；共享也不等于获得会议加入链接。这种schema比“请注意隐私”的提示词更能让上层做正确判断。
2. 查询上限在排除取消项后计算，避免被取消的重复事件吃满配额，使界面看似“没有更多”。同时保留同步尚未完成和分页截断的独立状态，不将空结果当作完整事实。
3. 同一会议多邮箱副本被显式保留，`confirm_copy`调用领域检查，在无法确定哪一份副本承载操作时返回每个副本的邮箱与角色，而非由Agent默选。它是多账号业务建模的具体范例，不是泛泛的“用了Rust所以安全”。

### 5）为什么今天突然火
可核事实：HEAD在**10月31日09:45:17北京时间（01:45:17 UTC）**修正“把同事日历读成用户日历”；前两个提交涉及随事件结束清理join request和频道mention预览去掉Macro call链接。最近release同时包含CEF编解码器分发包及 `v2026.10.29.1`，前者不能冒充整套应用的新产品发布。[版本记录](https://github.com/macro-inc/macro/releases/tag/v2026.10.29.1)
当前开放 [PR #9255](https://github.com/macro-inc/macro/pull/9255)还在处理搜索结果description中的会议链接，显示相同权限语义需覆盖多个出口；本轮只读到PR正文，不称它已合并或线上修复。上述维护活动与榜单位置可确认，但**暂无足够公开证据解释今日热度**，未建立某次发布、人物推荐与涨星的因果关系。

### 6）对用户的价值
优先读 `calendar_events/src/inbound/toolset/list_calendar_events.rs`，再读 `toolset.rs`：做Agent/MCP连接器时，把“能读取、属于谁、是否构成忙碌、能做什么”拆成稳定字段，是比不断加prompt警告更可迁移的设计。做Django/Node后端也可以复用端口与schema思路，但不能照抄Rust宿主的确认方式或推断MCP天然满足所有授权要求。对于RAG，开放PR提示检索命中后的enrichment也可能泄漏敏感字段，需要在最终输出路径复核，而不只检查检索范围。项目很大，适合抽取一个领域边界学习，不建议仅因入榜就整体替换现有协作栈。

**实际检查记录**：根目录树、README、Cargo workspace成员及相关依赖；日历crate Cargo全文；toolset装配、标签与副本检查片段；ListCalendarEvents全文、ReadCalendarEvent主要实现；HEAD文件清单及日历SQL/接口diff、最近3提交、最近2 release和3条开放issue/PR元数据及正文。大型递归tree未成功返回，未声称全库覆盖；没有编译、连接线上服务或复现权限漏洞。

## 8. mattpocock/skills

### 1）项目
- Repository：[mattpocock/skills](https://github.com/mattpocock/skills)；今日排名 **8**；**307,488 Stars**；页面给出 **876 stars today**；页面主要语言 **Shell**。
- 固定提交 [a496f5513d4a4cf889bc48e189e579f4b0bdf6aa](https://github.com/mattpocock/skills/commit/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa)，最近提交为10月29日。昨天前十没有它，只能说今日进入所比较的前十，不能由此断言首次上榜。

### 2）它到底解决什么问题
它是供编码Agent采用的工程流程技能库，不是新的模型、独立调度服务器或MCP服务。面向希望把需求澄清、规格、任务拆分、TDD、实现和代码审查连成可重复工作流的工程师，替代每轮临时写一份长prompt。其工作流由Markdown规则描述并交给宿主Agent执行，质量仍取决于模型、工具能力和真实项目约束；不能把文字规定当作运行时强制保证。

### 3）它实际上怎么实现
- **内容与分发**：递归树可见 `skills/engineering`、`productivity`、`in-progress`、`misc`、`deprecated`，以及Claude插件manifest与各技能的 `agents/openai.yaml`。根package是private维护包，版本1.3.2，开发依赖主要是Changesets；并没有藏着一套Node推理服务。README区分用户触发技能与模型可自动调用的可复用纪律。
- **规格→依赖图→就绪前沿→集成分支**：[implement-spec/SKILL.md](https://github.com/mattpocock/skills/blob/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa/skills/engineering/implement-spec/SKILL.md)的frontmatter设 `disable-model-invocation: true`。它要求先有spec及tracker配置，把ticket看成带阻塞边的图；每个ticket使用新的implementer上下文和独立worktree，基于integration branch实现，再合入最新integration tip，由merger合并。前沿发生变化才启动新的就绪任务，最后整体code review。重点是上下文指针、每ticket隔离与单一集成目标，而非盲目把所有任务并行。
- **固定diff→两个独立审查轴**：[code-review/SKILL.md](https://github.com/mattpocock/skills/blob/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa/skills/engineering/code-review/SKILL.md)先解析固定点，核验ref及非空diff，使用三点diff对merge-base比较；再分别寻找spec和仓库标准。Standards检查约定与标明为启发式的代码坏味道；Spec检查需求缺失、scope creep和错误实现。两份报告并列，不把它们合成单一“通过”标签，缺spec时明确跳过该轴。
- **维护脚本并非安全安装器**：[scripts/link-skills.sh](https://github.com/mattpocock/skills/blob/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa/scripts/link-skills.sh)通过find收集SKILL.md，跳过deprecated/misc，将源目录链接到宿主skill目录，防止目标本身反向链接回本repo。它明示是维护者dev-only脚本，且遇到同名非symlink目标会删除后替换；本轮仅静态阅读，没有执行，不应作为无风险安装建议。

### 4）技术亮点
1. “任务列表”被提升为依赖图，就绪前沿驱动并行，独立worktree隔离文件操作，integration branch提供统一验收对象。这是可检查的流程结构，但依然需要宿主正确执行。
2. 双轴review避免“代码风格很好”遮住“做错需求”，也避免需求吻合掩盖架构问题；标准引用与spec引用被要求分开，利于追责和人工决策。
3. 新上下文和上下文指针减少历史推理污染；对于已经接近context上限的长任务，这比反复转发完整对话更合理。但库本身不测token预算，也没有证明每种宿主都按它的字面语义实现“fresh”。

### 5）为什么今天突然火
最近主线提交要求每ticket新implementer；前一项相关提交专门强调子Agent使用fresh context，而非fork父对话。**v1.3.2于10月29日18:27:41北京时间（10:27:41 UTC）发布**，列出审查标准文件读取、bug诊断mutation验证等修正；它是近期背景，不是今天的新release。[v1.3.2](https://github.com/mattpocock/skills/releases/tag/v1.3.2)
更有工程价值的是当前开放 [issue #1359](https://github.com/mattpocock/skills/issues/1359)：报告者称双轴review仍放过spec未定义、却被测试固化的fallback/边界行为，建议将其单独标为需人决策。当前已读SKILL确实仅列三类Spec问题，未纳入提案中的第四类；这支持“存在流程覆盖缺口”，不等于复现了报告者生产事故。**暂无足够公开证据解释今日热度**；不以Stars体量或作者名气充当传播证据。

### 6）对用户的价值
最值得借鉴的是 `implement-spec`与 `code-review`的组合：适用于React/Next.js、Node、Python/Django项目，把并行工程工作收敛到同一规格与集成分支；无需把其全部技能装进现有环境。先建立自己项目的“未决需求”清单，把spec没有规定的边界显式留给人决定，而不是看到测试绿了就当产品决策已经完成。对Agent编排系统，可将这些步骤映射成持久状态和权限门槛；不要把prompt中的“创建PR/合并”理解成越过项目真实授权。该库不是RAG实现，价值在工程工作流而非检索算法。

**实际检查记录**：完整递归目录树、README与package.json；implement-spec、code-review及link-skills.sh全文；最近3提交、2 release和3条开放issue/PR的正文。未执行技能、安装脚本或任何仓库写入；其他技能未逐一审计，不声称覆盖整个库。

## 9. pingdotgg/t3code

### 1）项目
- Repository：[pingdotgg/t3code](https://github.com/pingdotgg/t3code)；今日排名 **9**；**32,744 Stars**；页面给出 **930 stars today**；页面主要语言 **TypeScript**。
- 固定提交 [80a2351fcb909034e65a512dfabeb3cdfd367762](https://github.com/pingdotgg/t3code/commit/80a2351fcb909034e65a512dfabeb3cdfd367762)，时间为**10月31日10:16:25北京时间（02:16:25 UTC）**。昨天前十没有它，未获取昨天同项目HEAD，因此不虚构逐日代码diff。

### 2）它到底解决什么问题
T3 Code是本机编码Agent的控制界面，允许Web、Electron桌面和移动客户端控制服务器所在机器上的provider、终端、Git与文件。它想替代只能在单一终端/单一厂商界面里管理会话的方式，而不是提供一个新的基础模型。README列出Codex、Claude、Cursor、Grok Build、OpenCode、Antigravity等接入，但本轮未认证这些服务，也未验证每个provider实际兼容性。

### 3）它实际上怎么实现
- **工作区归属明确**：架构文档将provider进程、终端、Git和文件归于拥有workspace的server；多端共享连接/领域状态位于 `packages/client-runtime`，而不是让手机用自己的文件系统替代远端。契约在 `packages/contracts`，provider差异在adapter后处理。根package使用pnpm工作区与Vite+；server依赖Effect、provider适配包、Claude Agent SDK、node-pty、jose等，CLI bin指向编译后的 `dist/bin.mjs`。[架构边界](https://github.com/pingdotgg/t3code/blob/80a2351fcb909034e65a512dfabeb3cdfd367762/docs/internals/overview.md)
- **命令意图先持久化**：[EventSink.ts](https://github.com/pingdotgg/t3code/blob/80a2351fcb909034e65a512dfabeb3cdfd367762/apps/server/src/orchestration-v2/EventSink.ts)的 `commitCommandEffect`在事务里先以command ID占位；重复命令返回已有结果而不再提交。新命令接着append事件、更新projection、enqueue outbox、保存receipt，提交后才notify effects及publish事件。因此accepted只是意图落库，不是provider任务完成。
- **提交顺序与取消边界**：`commitThenPublish`把transaction和发布串行化，使用semaphore避免不同写入者的事件发布倒序，导致客户端丢弃较早sequence；事务期间可取消，但提交成功后的发布受保护。它还在事务中重新检查待取消的user input请求，防止旧的terminal cleanup覆盖用户刚给出的答案。这些是实际代码控制，不只是架构图。
- **provider能力决定steer/fork/rollback**：[CommandPolicy.ts](https://github.com/pingdotgg/t3code/blob/80a2351fcb909034e65a512dfabeb3cdfd367762/apps/server/src/orchestration-v2/CommandPolicy.ts)将active steer、interrupt-restart和queued messages区分；当run处在preparing/starting，或provider turn已经结束时，auto输入排队而不是错误地steer。native fork要求强身份、同provider及相应能力，否则仅在支持完整上下文handoff时走portable context。rollback还要求provider能回滚对话并返回snapshot，不允许单独改工作区却留下不一致的会话历史。

### 4）技术亮点
1. **持久意图与外部副作用分开**：receipt、事件、projection、outbox原子提交；后续执行再反馈领域事件。这正好解决Agent工具的“收到请求不等于已经完成”问题。
2. **并发正确性落在细节**：发布lane、命令幂等、attempt/owner条件写，以及取消前重读用户输入状态，都围绕重复、迟到和乱序消息设计，而非假定一次请求一次成功。
3. **能力矩阵优于最低共同接口**：fork并不是复制聊天字符串，rollback也不是简单git reset；不同provider的语义差异被编码成可拒绝的能力检查，使客户端不会显示一个实际不能保证的统一操作。
4. 这些设计可用于长任务平台，但本轮未进行故障注入；数据库事务的意图持久化不应被夸大成对所有外部副作用的exactly-once保证。

### 5）为什么今天突然火
本轮最近3提交是Luau diff语法高亮、iOS disabled按钮外观，以及未触及Antigravity配额的rolling reset显示修正。**今日09:23:46北京时间（01:23:46 UTC）**的 [nightly.20261031.3956](https://github.com/pingdotgg/t3code/releases/tag/v0.1.6-nightly.20261031.3956)列出219项变更，涉及截断Markdown预览不覆盖文件尾、删除thread不移除共享worktree及审批显示等；这是发布方changelog，不代表本轮逐项实测，更不是stable版本。另一个recent release是明确不建议普通用户安装的preview。
开放 [issue #27947](https://github.com/pingdotgg/t3code/issues/27947)报告npm安装的Claude路径被误分为native更新通道；[#27946](https://github.com/pingdotgg/t3code/issues/27946)报告同消息内工具稍后生成的图片仍显示不可用。这些说明安装来源和异步资源展示仍有边界问题，但不能将issue报告当已确认漏洞。**暂无足够公开证据解释今日热度**，nightly维护活跃仅是同期背景。

### 6）对用户的价值
做Node/TypeScript Agent后台时，首选读 `EventSink.ts`的事务/outbox/receipt，再读 `CommandPolicy.ts`的能力分派；做React/Next.js控制台时应借鉴“客户端展示服务端真实状态”，不要由组件时钟自行判定任务完成或回滚成功。做Python/Django也可移植同一状态机原则，但需自己的数据库事务、后台worker、幂等key和授权设计。它不是一个即插即用RAG组件，价值集中在多provider与多端控制、长任务恢复、用户输入竞态等基础设施。不能因为README支持某CLI就自动安装或改用户现有认证配置。

**实际检查记录**：根树、README、根与server package、架构overview；CommandPolicy全文；EventSink类型、提交/发布事务、取消防护及commitCommand等关键段（大型文件非逐行全审）；HEAD与最近3提交、2 release及3条开放issue/PR正文。递归tree出现transport错误后使用正常根树定向定位，不涉及权限绕过；无运行、构建或客户端实测。

## 10. HKUDS/DeepTutor

### 1）项目
- Repository：[HKUDS/DeepTutor](https://github.com/HKUDS/DeepTutor)；今日排名 **10**；**51,779 Stars**；页面给出 **2,282 stars today**；页面主要语言 **Python**。
- 固定默认分支 [1ea7df155447f4caf0e3abc86b3ff5395479cd4a](https://github.com/HKUDS/DeepTutor/commit/1ea7df155447f4caf0e3abc86b3ff5395479cd4a)，与昨日相同；实际日榜截面为10月28日第9→29日第4→30日第1→31日第10，连续四个已观察日期仍在前十。**排名下降不等于仓库Stars减少，更不证明产品质量下降。**

### 2）它到底解决什么问题
DeepTutor把学习资料、RAG、教学对话、练习和笔记组织成可持续使用的个人学习系统，替代一次性“上传PDF问几个问题”的工作方式。它的用户是需要围绕材料反复学习的人；对于工程师，更有价值的是资料索引、原页证据、工具权限和中断恢复怎样连接。昨日已深读Agent loop及上下文预算，本期补读索引/页级来源/多租户工具边界；新增阅读不是新增功能，也不代表教学效果已经验证。

### 3）它实际上怎么实现
- **安装边界**：pyproject要求Python `>=3.11,<3.15`，核心依赖包括Pydantic、OpenAI SDK、MCP、aiosqlite和Typer；CLI入口是 `deeptutor_cli.main:main`，knowledge、server、web、memory等是同版本独立模块，`full`是组合档位。GraphRAG和rerank的Python marker更窄，不能把“核心支持3.14”泛化为所有可选组件都支持。
- **输入→journal→候选索引→可用版本**：[indexing_run.py](https://github.com/HKUDS/DeepTutor/blob/1ea7df155447f4caf0e3abc86b3ff5395479cd4a/deeptutor/knowledge/indexing_run.py)为每个KB建立文件锁和原子写journal，记录task ID、PID及进程起始时间、每源文件hash、阶段与候选storage；它不是第二个解析缓存，也不是队列。读取视图发现worker不再活跃时，将在途条目标成unknown/interrupted，而不是猜测成功；新worker检查task ID所有权，安全边界取消，结束时未确认条目仍为unknown。恢复只承诺复用经过验证的解析结果和可恢复checkpoint，未checkpoint的chunk/embedding必须重做。
- **PDF证据不是仅一个文本chunk**：[source_pages.py](https://github.com/HKUDS/DeepTutor/blob/1ea7df155447f4caf0e3abc86b3ff5395479cd4a/deeptutor/services/rag/source_pages.py)的SourceRef同时绑定KB、document key、SHA-256、page index、parser signature及可选crop。打开原页时重新通过知识库访问解析并检查hash，文件更换后要求重建索引；页面目录隐藏本地file_path。旧向量缺页定位时构造独立BM25物理页sidecar，不凭猜测给旧向量补页码；先临时目录构建，再原子发布。
- **每轮工具overlay→dispatch检查**：[scoped_registry.py](https://github.com/HKUDS/DeepTutor/blob/1ea7df155447f4caf0e3abc86b3ff5395479cd4a/deeptutor/runtime/registry/scoped_registry.py)让owner工具留在本turn overlay，不写入按name覆盖的全局registry；与共享工具冲突时丢弃，避免另一租户同名工具被覆盖。更关键的是 `execute`再次检查allowlist，覆盖模型生成未在manifest出现的工具名或文本协议fallback路径。仅过滤展示给模型的manifest不是授权门槛。

### 4）技术亮点
1. 索引状态保守且可解释：已有usable version和本次candidate分离，通知reporter异常不使durable checkpoint失效；中断后保留unknown，不把“有缓存文件”当完整可查询索引。
2. 来源引用绑定文件内容hash和物理页，并在渲染时重新授权；这减少“引用还在但原文件已变/权限已撤销”的错误，适合要求溯源的RAG。
3. 当前源码也暴露了具体覆盖缺口：`build_pdf_documents`只取block的text/content/table_body与若干caption，**没有读取MinerU参考文献的list_items**。这与开放 [issue #2222](https://github.com/HKUDS/DeepTutor/issues/2222)描述一致；是静态代码与报告相互支持，不是本轮PDF端到端复现。只要解析器产出成功就宣称“全篇已索引”是不安全的推论。
4. 工具名冲突隔离与执行时授权是两道不同的防线，适用于多用户MCP/RAG服务；本轮未验证所有调用方都正确构建overlay，不能把这一个类当作全产品安全证明。

### 5）为什么今天突然火
[v1.7.0](https://github.com/HKUDS/DeepTutor/releases/tag/v1.7.0)仍是已读最近版本，发布于**10月28日22:13:12北京时间（14:13:12 UTC）**，包含模块安装、学习工作区、笔记与视频课程。当前HEAD与昨日相同，因此不能说今天又发了新版本引起热度。
近期 [PR #2223](https://github.com/HKUDS/DeepTutor/pull/2223)与[#2224](https://github.com/HKUDS/DeepTutor/pull/2224)提出补齐参考文献与过滤页眉页脚，本轮它们仍出现在开放列表，不能算进已发布能力；报告者的节点数量测试也不是本次实测。**暂无足够公开证据解释今日热度**。榜单daily stars上升而排名下降尤其提醒：Trending不是按本报告的单项数字简单排序，不应用它推导未知推荐算法。

### 6）对用户的价值
Python/RAG最推荐读 `source_pages.py`并为自己的解析流水线建立输入元素覆盖测试：正文、表格、公式、caption、参考文献list、页眉页脚应有明确纳入/排除规则，单看parsed Markdown存在内容不保证embedding阶段接收到了。随后读 `indexing_run.py`，把取消、崩溃、文件改动与旧可用版本作为独立状态。若接入多用户MCP，`ScopedToolRegistry.execute`值得映射成Django/Node后端的真实授权检查，不能只裁剪tool schema。对Next.js界面，使用source_ref呈现可回到原页的证据，比仅显示一条文件名链接更可审计，但仍需自己的访问控制和文件哈希策略。

**实际检查记录**：完整递归树、README开头与既有昨日完整报告；pyproject全文；indexing_run、source_pages、scoped_registry全文；最近3提交、最近2 release与3条开放issue/PR。所有结论为静态审查；未安装、调用模型、重建索引、复现MinerU输入或运行多租户安全测试。
## A．今天最值得深入看的3个项目

1. **claude-mem：先把检索、注入预算和失败语义拆开。** 优先读 [ProgressiveMemorySearch.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/worker/ProgressiveMemorySearch.ts)、[ContextBudget.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/context/ContextBudget.ts)及[agent-runner/run.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/agent-runner/run.ts)。对用户的Agent/RAG工作，价值不是“记住更多”，而是信息怎样检索、怎样有损但显式地退化，以及内容拒绝为何不能直接触发换账户重试。
2. **OpenMausBot：长期任务的恢复和迁移不靠模型记忆。** 优先读 [waits.ts](https://github.com/milind-soni/OpenMausBot/blob/7de00e425848d5f1a2a845cb4784851b87d8cad2/server/waits.ts)、[runtime.ts](https://github.com/milind-soni/OpenMausBot/blob/7de00e425848d5f1a2a845cb4784851b87d8cad2/server/runtime/runtime.ts)和[own-home-main.mjs](https://github.com/milind-soni/OpenMausBot/blob/7de00e425848d5f1a2a845cb4784851b87d8cad2/electron/own-home-main.mjs)。重点是曾观察到的条件基线、外部动作后的重启边界、身份而非URL绑定；对Node/Python后台Agent都有可迁移价值。迁移改动在main，不等于已包含在当前release。
3. **impeccable：把设计技能的运行依赖也当作产品契约。** 优先读 [launcher](https://github.com/pbakaus/impeccable/blob/df3a4abe7d0840d5f60324812c432e00b66a4e75/skill/scripts/impeccable)与[修复diff](https://github.com/pbakaus/impeccable/commit/40f9c1e122d8c1032fce661a75d9c395d2e92872)。验证stamp何时失效、同目录旧引擎如何识别、操作者显式覆盖哪些检查，比“提供了很多设计命令”更值得带回自己的React/Next工具链。

## B．今天值得关注的技术趋势

以下仅归纳本次十仓的工程样本，不将榜单等同于整个行业的统计调查。

- **从“有没有记忆”转向“信息注入和失败的精确语义”。** claude-mem将检索分层、输出预算、内容校验拒绝与后端故障分别处理；同一处自动fallback可能同时影响费用、身份和质量，不只是容错开关。
- **Agent能力目录成为权限、隐私和真实依赖的交界。** OpenBot不直接把标准UI目录全量暴露，因缺依赖排除Map、因外部域名泄露风险排除图标相关组件；OpenMausBot迁移目的地也要检查环境身份和当前所有者，而不只判断连接成功。
- **技能仓库正在增加确定性检查，但检查器仍需验证。** Expo把技能目录、description长度、触发元数据和路由覆盖编入脚本；impeccable对引擎版本与验证缓存作机械检查。Expo当前组件导出枚举的开放问题说明“脚本生成”不自动等于正确。
- **同一领域规则跨入口一致，比新增一个helper更难。** ziwei的真太阳时helper与share入口仍采用不同日界/时辰口径，DeepTutor的结构化源页面转换也有输入形态覆盖缺口（见各节证据）。通用教训是检查端到端数据流，而不是只看一个函数有测试或一个PR宣称修好。
## C．与昨日实际报告比较

**榜单变化只比较两次观测。** 昨日是北京时间10月30日10:50，今日10月31日10:23；榜单统计窗口可能重叠，不当作严格自然日实验。

- **本次进入前十、昨天不在前十：** Renhuai123/ziwei-doushu、expo/skills、macro-inc/macro、mattpocock/skills、pingdotgg/t3code。这里不表示刚发布或历史首次上榜；已保存的10月26日报告曾列ziwei-doushu第7，10月29日报告曾列macro第5，因此这两项至少属于已知回归。
- **留在前十：** claude-mem **8→1**（升7位），OpenMausBot **5→2**（升3位），impeccable **3→3**，CopilotKit/OpenBot **9→4**（升5位），DeepTutor **1→10**（降9位）。排名下降不证明技术质量下降。
- **昨天在前十、今天不在本次前十：** obra/superpowers、JetBrains/thinkrail、nightly-labs/openbot、elayadesign/ai-design-skills、togg53192-cmd/jailbreaks。不写成“离开整个Trending榜”；本次页面在第十之后仍能看到其中若干项目。
- **连续观测边界：** 从已保存10月26–31日报告可核impeccable连续6个每日截面在前十（4→6→5→7→3→3）；DeepTutor在10月28–31日连续4个截面（9→4→1→10）；claude-mem、OpenMausBot、CopilotKit/OpenBot在10月30–31日连续2个截面。更早未纳入核验，不外推完整历史连续天数。

### 已核实的源码变化，而非仅排名变化

| 项目 | 昨日→今日固定版本 | 本期重点与限定 |
|---|---|---|
| claude-mem | `325afb6` → `70aa400`，+5 commits | v15.7.0正式发布；拒绝答案不再按后端故障自动fallback。审查固定实现，不等于所有公告修复均已复现。 |
| OpenMausBot | `0213b74` → `7de00e4`，+46 commits | 单所有者自托管home迁移的会话/环境身份守卫；主线变化晚于当前release。compare文件列表触及300项上限，不称全量审计。 |
| impeccable | `02523ae` → `df3a4ab`，+2 commits | launcher验证stamp失效与同目录版本握手，另一个提交同步生成产物；不是两项独立功能。 |
| CopilotKit/OpenBot | `ab9855c` → `743649e`，+2 commits | A2UI 18→65组件及四项排除；另一提交只是README的历史Trending徽章。 |
| DeepTutor | `1ea7df1` → `1ea7df1`，相同 | 无已确认主线增量；本期新读索引journal、原页引用和scoped tool dispatch，发现仍未覆盖的list_items路径，修复PR未合并。 |

上述链接与逐项证据见各项目章节。对于昨天不在前十的其余五仓，没有把今日近期提交冒称“与昨天源码的已核diff”；macro与ziwei的更早排名只用于说明回归。两日总Stars之差没有替代页面的stars today，也未把“新读到一个模块”当“项目今天新加功能”。
