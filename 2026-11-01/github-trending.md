# GitHub Trending 源码深读｜2026-11-01

## 榜单来源、时间与研究边界

- **北京时间 2026-11-01 10:19:29（UTC 02:19:29）实际读取云端浏览器中的 [GitHub Trending](https://github.com/trending)。** 筛选为 **Repositories / Date range: Today / Language: Any / Spoken Language: Any**，即 Daily、All languages。以下是该页面前十的原始顺序，未按总 Stars 或搜索结果重新排序。
- 同轮只读网页读取返回“Crawled: today”，顺序与浏览器一致，但总 Stars 略低；**本报告全部榜单指标统一采用浏览器截面**，不混用稍后 API 数值。GitHub 内部刷新时刻和缓存年龄不可见，不能声称秒级实时；stars today 的统计窗口也不等于已核实的北京时间自然日。
- 昨日基线为实际留存的 [2026-10-31 报告](https://github.com/DanielMax937/daily-research-reports/blob/b4cec987501fe71fe841948f9e835437010d5493/2026-10-31/github-trending.md)，抓取时间北京时间 10:23:27（UTC 02:23:27）。只比较两次前十截面；“新进入”不是首次上榜，也不是项目刚发布。未把总 Stars 差冒充 GitHub 今日新增。
- 各仓库采用定向源码阅读，固定已读提交，列明 README、目录树、依赖、入口及核心实现覆盖和不足。**没有安装、执行仓库脚本、运行产品、测试或复现 benchmark**；代码和技能文档均作为研究材料，而非本助手应执行的指令。
- 近期提交、release、issue 只能确认开发活动或作者/用户报告，不自动证明今日涨星因果；没有可靠传播证据时如实说明。未完整扫描 X、HN、Reddit，仓库声称的能力与独立验证明确区分。

| 今日排名 | Repository | Stars | GitHub stars today | 页面语言 | 昨日前十位置 |
|---:|---|---:|---:|---|---|
| 1 | [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | 107,951 | 1,723 | TypeScript | 1 |
| 2 | [mattpocock/skills](https://github.com/mattpocock/skills) | 308,462 | 883 | Shell | 8 |
| 3 | [Donchitos/Claude-Code-Game-Studios](https://github.com/Donchitos/Claude-Code-Game-Studios) | 31,221 | 742 | Shell | 不在前十 |
| 4 | [pingdotgg/t3code](https://github.com/pingdotgg/t3code) | 35,713 | 1,148 | TypeScript | 9 |
| 5 | [Renhuai123/ziwei-doushu](https://github.com/Renhuai123/ziwei-doushu) | 12,327 | 1,092 | TypeScript | 5 |
| 6 | [milind-soni/OpenMausBot](https://github.com/milind-soni/OpenMausBot) | 9,689 | 1,303 | TypeScript | 2 |
| 7 | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | 98,344 | 1,338 | Rust | 3 |
| 8 | [obra/superpowers](https://github.com/obra/superpowers) | 310,096 | 665 | Shell | 不在前十 |
| 9 | [lightpanda-io/browser](https://github.com/lightpanda-io/browser) | 39,287 | 929 | Zig | 不在前十 |
| 10 | [HKUDS/DeepTutor](https://github.com/HKUDS/DeepTutor) | 52,878 | 1,034 | Python | 10 |


## 1. thedotmack/claude-mem

### 1）项目数据
- [仓库](https://github.com/thedotmack/claude-mem)：本次Daily / All languages **#1，107,951 Stars，1,723 stars today，TypeScript**。昨天同为第1；至少10月30日—11月1日三个已观察截面在前十。
- 固定源码 [`70aa40042cfb8157a0d84954b9c0d2b30b50af80`](https://github.com/thedotmack/claude-mem/commit/70aa40042cfb8157a0d84954b9c0d2b30b50af80)，与10月31日报告**完全相同**。本期补读持久捕获、响应入库与检索回填，不将新阅读冒称新功能。

### 2）解决什么问题
为编码Agent提供跨会话的项目记忆：工具调用形成观察、观察压缩成摘要、后续会话再检索相关证据，而不是每次重新探索全部代码。除了“记得住”，真实难点是worker掉线时捕获不丢、模型没有执行过的工作不被写成事实、向量命中与实际数据库状态一致。README描述本地worker与可选托管服务，不能据此认为所有安装路径都完全离线。

### 3）实际实现：从捕获到可检索记忆
1. **入口及事件管线。** [package.json](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/package.json)的CLI是 `dist/npx-cli/index.js`，Node要求 `^20.19.0 || >=22.12.0`、Bun `>=1.1.31`；Express、MCP SDK、Claude Agent SDK等在构建时打包，不可只看直接dependencies判断技术栈。[CLI入口](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/npx-cli/index.ts)动态分派install/runtime/hook/MCP；[hooks](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/plugin/hooks/hooks.json)在SessionStart启动worker、注入上下文，在PostToolUse/Failure异步收集，在Stop总结。这不是单个prompt文件。
2. **掉线捕获不是简单重试HTTP。** [hook-spool-drain.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/worker/hook-spool-drain.ts)将磁盘spool交给与HTTP路由相同的ingest函数，保留事件原始入队时间；fs.watch、主动nudge和30秒安全扫描共同触发single-flight drain。[hook-spool.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/shared/hook-spool.ts)按会话与平台命名事件，交接时写consumed marker；同会话summary/session_end不能越过尚未接受的observation；无效数据与过期数据分别隔离，不静默当作已完成。
3. **先判断模型真的回答了什么，再落库。** [ResponseProcessor.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/worker/agents/ResponseProcessor.ts)在增加会话历史前识别超长、配额、认证和传输拒绝；传输/认证失败保留待处理批次，而不是确认掉。仅对init请求返回的XML不入库——用户提出“请修改”并不是修改已完成的证据。真实批次的files_modified来自捕获到的工具输入，文件读取列表则与模型输出合并。存储成功后先确认批次，再做遥测、Chroma同步及SSE，避免后续集成抛错导致已存记录被整体重播。
4. **向量结果还要回SQLite核验。** [ChromaSearchStrategy.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/worker/search/strategies/ChromaSearchStrategy.ts)逐步扩大候选窗口，按observations/sessions/prompts分别检查分页是否满足，再按项目、平台、类型等条件从SQLite hydrate。被拒绝的ID也缓存，避免不断重复查询；默认候选上界至少1600，达到预算显式返回 `semanticBudgetReached`。日期与doc_type共同处理，不能把不同表的数字ID当全局唯一。[scope-row-ids.ts](https://github.com/thedotmack/claude-mem/blob/70aa40042cfb8157a0d84954b9c0d2b30b50af80/src/services/worker/search/scope-row-ids.ts)缓存过滤后row ID集合供向量fallback使用。

### 4）技术亮点与边界
- **证据产生、记忆写入、索引同步分层。** SQLite记录先成立，Chroma失败可降级；同一批次合并到旧观察时不拿新文本覆盖旧观察的向量。记忆系统不仅是embedding API加数据库。
- **恢复语义可以审查，也有明确上限。** spool交接marker抑制重启后的重复投递，但marker写入失败时实现选择记录错误并继续；因此不能把注释中的exactly-once扩展成所有崩溃情形、所有模型付费调用的严格一次保证。
- **内容失败与基础设施失败分开处理。** 本期读到的是observer响应处理器：第二次非XML回答可能转fallback，若没有可用fallback则显式丢弃并记录失败。它与昨日审查的“My Work拒绝答案不切换agent”属于不同管线；不能把后者泛化成全产品永不自动切换。
- 捕获文件证据、保留完整块并提示截断、schema漂移后重建规范历史，都在降低错误记忆传播；这仍不等于模型生成的叙述已获事实证明。

### 5）今日热度：事实与缺证
最新已读release仍为 [v15.7.0](https://github.com/thedotmack/claude-mem/releases/tag/v15.7.0)，发布于**10月31日02:18:54北京时间／10月30日18:18:54 UTC**；最近5提交也仍是该版本changelog、bundle和默认Haiku/拒绝fallback修复，没有已确认的今天主线增量。因而不能写“今天新发15.7.0导致登顶”。

新开放 [issue #5240](https://github.com/thedotmack/claude-mem/issues/5240)给出Windows上Kaspersky阻断worker启动及账户登录流程困惑的日志；报告者明确未证明检测原因或误报，不能把它定性成木马，也不应建议关闭防护。[PR #5243](https://github.com/thedotmack/claude-mem/pull/5243)提出云会话hook不可达时提示使用connector，仍是开放提案，未进入固定HEAD。[issue #5241](https://github.com/thedotmack/claude-mem/issues/5241)标题重复隐式Codex消耗问题，但正文主要是未填模板，不能作为修复后复发的独立实证。**没有足够公开传播证据解释今日1,723 stars today；release、issue和排名只能作为同期事实。**

### 6）对用户的AI／全栈工程价值
做Node/Python Agent后台，优先借鉴“事件原始时间、交接receipt、持久事实与后续索引副作用分开”，并主动测试交接前后崩溃与marker写失败。做RAG，读ChromaSearchStrategy的候选预算、分类分页和SQLite二次过滤，避免向量库元数据被当成授权或最终事实。做React/Next.js控制台，要区分“捕获已接收、摘要已存、向量尚未同步”，不要只给一个成功绿点。生产接入前先明确provider、云同步及登录边界；本轮仅静态审查，未安装或调用模型。

**实际文件覆盖／限制**：完整递归树（未截断）、README、manifest、hooks、CLI、hook-spool-drain、ChromaSearchStrategy、scope-row-ids全文；hook-spool的enqueue/drain/unlink/过期段；ResponseProcessor的拒绝分类、init屏障、文件证据、存储确认、去重与同步段。读取最近5提交、2个release、3条开放issue/PR全文及昨日对应章节。大型ResponseProcessor与hook-spool不是逐行全审；未运行测试、故障注入、Windows复现或审计托管服务。

## 2. mattpocock/skills

### 1）项目数据
- [仓库](https://github.com/mattpocock/skills)：**#2，308,462 Stars，883 stars today，Shell**；昨日#8，本次升6位。
- 固定[4ae2317ddb22b046e26455e4f9c9b3aaaf62212d](https://github.com/mattpocock/skills/commit/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d)。与昨日 `a496f551` [比较](https://github.com/mattpocock/skills/compare/a496f5513d4a4cf889bc48e189e579f4b0bdf6aa...4ae2317ddb22b046e26455e4f9c9b3aaaf62212d)确为 **+2 commits**，不是从Stars增量推断更新。

### 2）解决什么问题
这是将规格、TDD、review和长期协作写成可组合技能的工程流程库，替代每次重新写长prompt。**没有独立模型推理运行时、任务服务器或RAG引擎**；宿主Agent负责执行，Markdown中的“必须”不是不可绕过的运行时约束。本期新增内容还在 `in-progress`，不能说稳定插件已经全面发布“自动软件工厂”。

### 3）实际实现
- 根 [package.json](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/package.json)是private维护包，版本仍1.3.2，开发依赖为Changesets；目录主体是分组SKILL.md与宿主manifest，而非Node后端。
- 新 [software-factory/SKILL.md](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/in-progress/software-factory/SKILL.md)是一套设计词汇和检查表，区分task、trigger、run、runner及orchestrator。它规定runner不承载跨run记忆，人类反馈通过tracker或git host触发新run；“无等待的人类交接”是拟议架构语义，并没有在仓库实现队列或worker。
- 更新的 [chief-of-staff/SKILL.md](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/in-progress/chief-of-staff/SKILL.md)先找现有共享wiki，避免各Agent另起知识孤岛。wiki按主题与index连接，代码事实绑定仓库、commit和日期，旧事实标为被替代而非偷偷改写；用文件指针给fresh-context子Agent传递信息。
- 同一技能新增对约五分之一子Agent会话做retro的抽样规则，优先异常会话；大块任务转交规格、拆票、implement-spec程序。它的相邻技能路径描述针对安装后的布局，不应把源码中的 `in-progress` 相邻目录直接当已验证可执行布局。

### 4）技术亮点
1. **把自动化的刹车与加速器一起设计**：新词汇技能要求确定性检查、独立自动review、人工review三层门槛，逐步放开触发器并限制重试循环；不是“越多Agent越好”。
2. 每个task必须回答去重、读写范围、后续触发、人类再进入位置，ticket source也需解释如何避免重复建票。对事件驱动Agent后台，这是一张实用架构评审表，但去重机制仍须开发者实现。
3. 持久wiki记录“当时已知事实”，不伪装实时数据库；更适合长任务交接和审计，而非把过期记忆继续当当前事实。

### 5）今日热度：事实与缺证
两项主线更新分别在**10月31日21:47:43、22:23:30北京时间（13:47:43、14:23:30 UTC）**进入；最近release仍是[10月29日18:27:41北京／10:27:41 UTC的v1.3.2](https://github.com/mattpocock/skills/releases/tag/v1.3.2)，不能把这两项新稿说成今天发布的稳定版本。开放 [issue #1364](https://github.com/mattpocock/skills/issues/1364)反馈长期使用后测试套件膨胀、单票运行过多无关测试，作者也未断言一定由技能导致。这揭示流程成本议题，不是性能实测。**暂无足够公开证据解释今日热度**；新增技能与升榜只是同期事实，不能声称因果。

### 6）对用户AI / 全栈工程的价值
最值得带入Node/Python/Django Agent后台的是“每次run可丢弃、状态在外部、所有触发可去重”的设计审查；React/Next.js团队可先采用wiki事实绑定commit和retro抽样，而非先建庞大调度平台。建议把测试选择和固定基线加入任务契约，区分增量检查与最终集成验证，回应issue所揭示的成本问题。

**实际覆盖与限制**：完整递归树、README、package.json、两份上述SKILL全文；最近3提交、2 release和2开放issue正文/条目、昨日compare。其余技能沿用昨日阅读背景但本期未全审；未安装、运行技能或验证宿主兼容性。

## 3. Donchitos/Claude-Code-Game-Studios

### 1）项目数据
- [仓库](https://github.com/Donchitos/Claude-Code-Game-Studios)：**#3，31,221 Stars，742 stars today，Shell**。
- 固定[05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418](https://github.com/Donchitos/Claude-Code-Game-Studios/commit/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418)，最近主线提交为10月19日。昨天前十没有它；**本次新进前十不等于项目刚发布或历史首次上榜**，没有昨日同仓HEAD基线，不编逐日diff。

### 2）解决什么问题
它为单人用Claude Code开发游戏提供设计、开发、QA、制作流程模板，README称49角色、74技能。真正产品是角色定义、技能规范、Shell辅助脚本与hooks，而不是49个自带模型、独立调度集群或可立即游玩的游戏。**无独立模型运行时**；需要宿主Agent，实际构建与截图还依赖项目选定的游戏引擎及工具。

### 3）实际实现
- 根 `project.yaml`提供框架版本1.2.0及配置约定；[settings.json](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/settings.json)将SessionStart、PreToolUse、PreCompact等事件接到Shell脚本。根树没有通用应用package/pyproject；依赖来自Bash、awk、Git及宿主/所选引擎，不应把模板当普通npm服务。
- [dev-story](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/skills/dev-story/SKILL.md)先读取story、ADR状态、配置和依赖，按story类型选择程序员与引擎专员；brief以文件指针给出验收标准。实现后记录观察结果、涉及文件、checkpoint与截图的源码hash。
- [read-guard.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/scripts/read-guard.sh)只产生大小、范围、阈值等TSV观察；[validate-read.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/hooks/validate-read.sh)在指定设计目录中文件超过默认40KB且Read没有offset/limit时用exit 2拒绝，并列最多40个标题。辅助脚本缺失则警告后放行，所以这是上下文成本护栏，不是安全访问控制。
- [review-receipts.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/scripts/review-receipts.sh)比较文件内容hash，而非mtime或用户是否commit；检查receipt里所有已签收路径，删除报GONE，未展开glob报UNRESOLVED，也支持节级hash。无hash工具不把未知判为未变化。
- [story-done](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/skills/story-done/SKILL.md)逐验收项区分代码存在、用户声称通过、亲眼看过截图和待playtest，要求显式选择才关闭。**过期截图的hash提示按当前规范只报告，不改变verdict**，因此不是强制“证据过期就禁止完成”的门禁。

### 4）技术亮点
内容hash的审查receipt可移植到非游戏项目：从“测试曾经绿过”推进到“这份证据究竟对应哪一版输入”。观察脚本与判定技能分离，也便于把同一事实接入不同宿主。不过多个状态文件并不自动形成事务：[set-stage.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/scripts/set-stage.sh)当前先覆盖project.yaml，再写production/stage.txt，第二步失败可留下不一致；静态路径与开放修复提案吻合，本轮未复现。

### 5）今日热度：事实与缺证
[v1.2.0](https://github.com/Donchitos/Claude-Code-Game-Studios/releases/tag/v1.2.0)发布于**10月19日10:44:23北京时间（02:44:23 UTC）**，强调主流程缩短、共享helpers和read guard，不是今日新release。开放 [PR #148](https://github.com/Donchitos/Claude-Code-Game-Studios/pull/148)拟修复双文件stage写入失败，仍未计入当前固定代码；提案者报告的四项测试不是本轮执行。开放 [issue #150](https://github.com/Donchitos/Claude-Code-Game-Studios/issues/150)提议可选素材检测，也不应写成已集成能力。**暂无足够公开证据解释今日热度**；第三方README转载不能证明今日涨星来源。

### 6）对用户AI / 全栈工程的价值
做React/Next前端，可将截图与源码hash绑定，防止改完CSS后仍拿旧截图验收；做RAG可将评估结果与文档/索引版本绑定；Node/Python工作流可复用“观察事实、判定、授权写入”三层结构。最优先读review-receipts与story-done的连接：不仅检查是否发现变化，还要检查变化是否真的影响完成状态。不要为了流程完备照搬全部游戏角色与文档层级。

**实际覆盖与限制**：完整递归树；README开头、项目配置、settings全文；read guard/helper hook、review-receipts、set-stage及story-done全文，dev-story核心阶段与收尾；最近3提交、2 release、2开放issue/PR。未读取49角色全部定义、未装引擎、未运行测试或生成游戏；发布方效果与测试声明不作独立验证。

## 4. pingdotgg/t3code

### 1）项目数据
- Repository：[pingdotgg/t3code](https://github.com/pingdotgg/t3code)；今日排名 **4**；**35,713 Stars**；**1,148 stars today**；主语言 **TypeScript**。以上取11月1日10:19:29北京时间的Daily / All languages真实榜单截面。
- 固定源码 [`481ff3ea89c7358953e8b7ffb762978c31fb3a0b`](https://github.com/pingdotgg/t3code/commit/481ff3ea89c7358953e8b7ffb762978c31fb3a0b)，提交时间11月1日**10:20:09北京时间（02:20:09 UTC）**，稍晚于榜单观测，二者不混作同一时刻。
- 昨日排名9，今日4，升5位；昨日固定 `80a2351` 至今日 `481ff3e` 的 [compare](https://github.com/pingdotgg/t3code/compare/80a2351fcb909034e65a512dfabeb3cdfd367762...481ff3ea89c7358953e8b7ffb762978c31fb3a0b) 确认 **ahead 140 commits**。API文件清单达到300项上限，不能称已完整审计全部变更。

### 2）它到底解决什么问题
T3 Code是跨Web、Electron桌面和手机的编码Agent控制台，不是基础模型。它让用户远程控制拥有工作区的server上的provider进程、终端、Git和文件，减少每种Agent各自维护一套界面与状态的割裂。README声称接入Claude、Codex、Cursor、Grok Build、OpenCode和Antigravity；本轮只核源码，不认证这些服务，也不声称逐一验证兼容性。

### 3）它实际上怎么实现
- **服务端拥有执行、客户端共享领域状态**：根目录含apps、packages、native、infra及pnpm工作区。根manifest使用Vite+与pnpm，server包提供 `t3 -> dist/bin.mjs`，依赖Effect、provider workspace包、Claude Agent SDK、node-pty等。[架构overview](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/docs/internals/overview.md)规定RPC连接认证不等于每个方法均获授权；持久事件、projection、receipt和outbox先事务提交，外部副作用后执行。这里是架构契约，昨天已读EventSink，本期不把旧阅读冒充新增实现。
- **入口快路径避免为每次MCP调用加载整个CLI图**：[bin.ts](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/apps/server/src/bin.ts)先识别文档提取、managed token和acp-mcp-bridge/call，动态导入对应模块；普通命令才加载console stdin与[binCli.ts](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/apps/server/src/binCli.ts)。文档内容拒绝用exit code 2，与可重试OS/进程错误分离。CLI再通过Effect层装配server、auth、thread、project、service等命令。
- **空闲压缩不是“闲着就总结”**：[IdleCompaction.ts](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/apps/server/src/orchestration-v2/IdleCompaction.ts)要求最新run完成、不是上一次压缩本身、当前仍为同一Claude实例/会话、上下文达阈值且明确知道cache到期时间；pending用户请求、merge-back或后台工作会阻止压缩，避免吞掉本应进入下一轮的信息。窗口起点是到期前2分钟，未知TTL或已过期直接放弃。[IdleCompactionService.ts](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/apps/server/src/orchestration-v2/IdleCompactionService.ts)以thread为键维护FiberMap，更新run替换旧timer，醒来重读状态；发送可见的 /compact turn，并用thread+run构造command/message ID防重复。**但timer仍只在内存，当前版本没有启动恢复查询**。
- **回滚先判工作区是否真隔离**：[CheckpointRestoreSafety.ts](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/apps/server/src/orchestration-v2/CheckpointRestoreSafety.ts)规范化realpath，检查当前cwd等于worktree，并遍历活跃和归档thread、checkpoint scopes及尚未停止的provider session；路径包含/被包含都按共享处理。昨日到今日新增的例外仅针对同worktree、无active run、且没有command_execution/file_change/dynamic_tool记录的闲置side chat，不是“所有side chat不影响回滚”。
- **完成信号不能跨层冒认**：今日HEAD的[Cursor adapter关键段](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/packages/provider-cursor/src/server/adapter.ts#L2093-L2130)在finalizeTurn里把仍未收到completion的tool标为interrupted，即使外层turn正常completed；失败/取消则保留对应状态。配套[提交diff](https://github.com/pingdotgg/t3code/commit/481ff3ea89c7358953e8b7ffb762978c31fb3a0b)增添有开始无结束的Read与真正完成Read对照测试。代码有测试不等于本轮运行过测试。

### 4）技术亮点
1. **节省token受语义约束**：缓存截止、待反馈后台工作、当前provider身份、最新run均要同时成立，压缩不是纯计时器。它值得借鉴，但内存timer的重启缺口必须一起看。
2. **恢复文件之前检查共享关系**：不能只看是否存在worktree路径，归档thread、嵌套路径及错误但未stopped会话也可能仍占用它；新例外以工具历史为证据，而非以“聊天窗口闲置”猜安全。
3. **unknown不能染成success**：Cursor修复把turn完成和tool结果完成拆开，适用于所有Agent控制台的状态模型。UI最后一条绿灯不能证明每个外部动作成功。
4. 本期是静态路径审查，未做故障注入、真实provider运行或回滚实验，不把这些局部守卫扩大成全产品安全保证。

### 5）为什么今天火：事实与缺证边界
**发布事实**：昨日报告采样之后，正式版 [v0.1.6](https://github.com/pingdotgg/t3code/releases/tag/v0.1.6) 于**10月31日18:52:24北京时间（10:52:24 UTC）**发布；公告列521项变更，主打side chats、项目置顶/归档、Diff查看本地commits、1Password凭据接入。数字和功能范围为发布方声明，未逐项实测。最新已读预发布 [v0.1.7-nightly.20261031.4004](https://github.com/pingdotgg/t3code/releases/tag/v0.1.7-nightly.20261031.4004) 于**11月1日07:24:23北京时间（10月31日23:24:23 UTC）**发布，仅列2项变化，包含model picker不跳动；不能把nightly写成正式版。
最近3提交分别为Cursor未完成工具状态、Android commit sheet滚动及主题隐藏环境图的提示。开放 [PR #28490](https://github.com/pingdotgg/t3code/pull/28490)提出重启后重建idle-compaction timer；当前已读源码确实只有事件订阅与内存timer，**提案尚未合并，不能算已具备恢复能力**。[issue #28489](https://github.com/pingdotgg/t3code/issues/28489)报告上百skills使菜单挂载/过滤卡顿，其延迟数字是报告者测量，不是本轮基准。[PR #28488](https://github.com/pingdotgg/t3code/pull/28488)提出WSL预览tab headless标记修复，本轮也未验证打包Windows端。
发布与持续修复是同期可核背景；**暂无足够公开证据把今日Trending热度归因于某个版本、社交传播或作者影响力**。Stars体量与stars today都不是因果证据。

### 6）对用户AI / 全栈工程工作的价值
做Node或Python Agent后台时，优先借鉴idle compaction的“执行前再验证状态”与幂等命令，但若需要跨重启可靠性，应将到期时间/待执行意图持久化，启动重建并继续复核，不直接照搬内存FiberMap。做React/Next.js控制台时，将run、provider turn、tool和后台收尾分开显示，避免把外层完成渲染成所有工具成功。做多Agent工作区时，回滚应先核共享占用，再改变文件；对Django同样可以用数据库状态与规范化路径实现原则。它不是RAG库，但“上下文压缩不能吞掉待交付信息”的规则，对长会话RAG助手也有参考价值。

**实际覆盖与限制**：读取昨日对应章节；今日根目录、README、根/server manifests、bin.ts与binCli.ts、架构overview、IdleCompaction、IdleCompactionService及CheckpointRestoreSafety全文；Cursor adapter仅2045–2150行及HEAD实现/测试diff；最近3提交、140-commit compare元数据和300项截断文件清单、2个最新nightly及latest stable公告、3条开放issue/PR正文。递归tree读取未成功，改为根目录和已知路径定向阅读；未获取全树、未全量审查140提交、未安装/执行/构建/登录或修改仓库。

## 5. Renhuai123/ziwei-doushu

### 1）项目
- [Renhuai123/ziwei-doushu](https://github.com/Renhuai123/ziwei-doushu)：今日第 **5**，**12,327 Stars**，榜单显示 **1,092 stars today**，主要语言 **TypeScript**。
- 固定提交 [495b79ecb3524b20b2edc026067d7d0b0f407319](https://github.com/Renhuai123/ziwei-doushu/commit/495b79ecb3524b20b2edc026067d7d0b0f407319)，与昨日实际报告相同，排名也仍为5；不能把新读到的问题当今日新增代码。

### 2）它到底解决什么问题
把传统紫微斗数的历法、排盘规则、流派配置、古籍与示例界面开放出来，替代封闭排盘网站中无法检查的规则实现。它不是已获科学验证的人生预测系统；**传统规则计算的一致性不等于预测效力**。开源UI是演示，README明确完整断语库与线上AI解读/合盘后端不在仓库中，配置模型Key不会补齐缺失接口。

### 3）它实际上怎么实现
- [package.json](https://github.com/Renhuai123/ziwei-doushu/blob/495b79ecb3524b20b2edc026067d7d0b0f407319/package.json)使用Next 16、React 19、iztro与lunar-javascript；不是全部历法和基础排盘从零实现。回归测试通过tsx串行运行，覆盖非法日期、时辰边界、夏令时、立春等。
- [generateChart](https://github.com/Renhuai123/ziwei-doushu/blob/495b79ecb3524b20b2edc026067d7d0b0f407319/lib/ziwei/algorithm.ts)拒绝非整数0–11时辰索引，并用UTC日期回读拒绝不存在的日期；按闰月策略调用iztro的byLunar/bySolar，再组装十二宫、星曜类型、流派亮度、大限和空宫借对宫等结构化信息。输出保留leapMonthPolicy，使后续重建不丢口径。
- [true-solar-time.ts](https://github.com/Renhuai123/ziwei-doushu/blob/495b79ecb3524b20b2edc026067d7d0b0f407319/lib/ziwei/true-solar-time.ts)有经度差与NOAA均时差近似、标准时区中央经线、秒级舍入、跨日偏移和晚子时策略；但**有helper不等于公共入口已消费它**：generateChart只解构year/month/day/hour/gender，不读取longitude来校正。
- [share.ts](https://github.com/Renhuai123/ziwei-doushu/blob/495b79ecb3524b20b2edc026067d7d0b0f407319/lib/ziwei/share.ts)仍按钟表23点换日，却按经度校正后的分钟算时辰；其简化公式只用120°中央经线，不加均时差。今日新读的开放 [PR #65](https://github.com/Renhuai123/ziwei-doushu/pull/65)提议让generateChart消费经度和原始钟表输入，但它仍未合并，而且明确不统一share入口。昨日已读的 [PR #63](https://github.com/Renhuai123/ziwei-doushu/pull/63)亦仍开放。

### 4）技术亮点
价值在领域口径显式化：时辰索引不同于钟表小时，闰月、日界与亮度流派不能混为一个开关；非法日期直接报错，优于静默顺延得到貌似合理的盘。另一方面，这也是很好的集成反例：一个较完整的纯函数模块可以存在，却未进入最终调用链。模块级currentBrightSchool还提示，将浏览器逻辑迁入并发服务前需检查共享可变配置，而不是直接宣称无状态。

### 5）为什么今天突然火
已核事实是今日仍在第5、HEAD不变；最近提交仍是10月31日08:10北京时间（10月31日00:10 UTC）的OURANIC名称/网址文档更新，提交说明代码、数据集、许可不变。最近 [v4.0-13d](https://github.com/Renhuai123/ziwei-doushu/releases/tag/v4.0-13d)发布于10月15日23:24:32北京（15:24:32 UTC），作者称674,976张盘与8,774,688段确定性解读，本轮未下载核验约57GB解压数据。新PR #65是同期社区发现的入口缺口，不是发版。**暂无足够公开证据解释今日热度**；“中文传统文化+AI应用门槛低”最多是产品吸引力假设，不能替代传播证据。

### 6）对用户的价值
做TypeScript/Next.js业务系统，可借鉴其输入校验和显式策略序列化，但应优先做“表单→转换→领域函数→结果”端到端契约测试，特别检查时区/跨日等跨模块语义。做AI/RAG时，可学习规则数据的版本口径、原文来源与许可分层；不要把确定性生成文本当真实世界标注，也不应拿相关健康/命运解读作为医学或人生决策依据。

**实际检查记录与限制**：实读固定提交README、package、完整递归树、algorithm/share/true-solar-time全文，最近3提交、2 release与3条开放PR正文（65、63、58）。未运行测试、安装依赖、下载数据集、访问线上用户数据；本期无已确认源码增量。

## 6. milind-soni/OpenMausBot

### 1）项目数据
- 仓库：[milind-soni/OpenMausBot](https://github.com/milind-soni/OpenMausBot)；本次日榜 **#6**；**9,689 Stars**；页面 **1,303 stars today**；主要语言 **TypeScript**。榜单取北京时间11月1日10:19:29的实际观测。
- 固定提交 [`88d54eb17a3655b968470cbbf3b5097de225a8b5`](https://github.com/milind-soni/OpenMausBot/commit/88d54eb17a3655b968470cbbf3b5097de225a8b5)，提交于 **11月1日06:20:53北京／10月31日22:20:53 UTC**。昨日#2→今日#6；[昨日固定提交到今日](https://github.com/milind-soni/OpenMausBot/compare/7de00e425848d5f1a2a845cb4784851b87d8cad2...88d54eb17a3655b968470cbbf3b5097de225a8b5)前进 **24 commits**，返回300个文件达到API上限，不能当完整变更清单。Stars总量增长与stars today不是同一统计口径。

### 2）解决什么问题
它把本地Agent CLI、电脑、连接应用、多人共享和长任务包装成联系人式聊天桌面：用户面对一组bot，而不是一串终端。React界面通过HTTP命令和SSE事件与Node harness通信，后者拥有provider进程和线程日志。相比普通聊天套壳，关键工程问题是长会话压缩何时发生，以及“看得见一个bot”是否意味着能发消息、改配置或读别人的私聊。本次重点实读这两个新近演进的边界；README中的竞品对比不作为独立验证事实。

### 3）实际实现与源码
1. **入口和执行归属。** [package.json](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/package.json)为0.1.136，要求Node >=24、pnpm 10.33.0，Electron入口为`electron/main.mjs`；依赖包括React19、ws、Zod、Ajv、croner、CUA driver、DuckDB Node API。[server/index.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/index.ts#L5307-L5338)把warm-summary host挂到registry、store、coordinator、waits、routines；订阅turn.started/turn.completed事件，而非由UI计时器猜测空闲。开关同时看autoCompact、环境变量和费用超额，内存余量低于0.3会推迟。
2. **把压缩移到空闲期，但用户新消息优先。** [server/warm-summary.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/warm-summary.ts)维护按thread的pending/run；通常空闲3分钟启动，即将触发原生压缩时10秒启动，忙碌/临近routine则2分钟后重试，50分钟后不再尝试。新turn通常中止后台摘要；唯有本来就会压缩的turn等待正在做的摘要，最长3分钟，不能概括成“永不等待”。[warm-summary-host.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/host/warm-summary-host.ts)排除群聊，检查待处理消息、teammate工作、已触发wait、内存与routine。原生计划的门槛为`min(100000, compactAt/2)`，soon为compactAt的0.8，不是所有模型固定100k。
3. **摘要写入fork，更新会话前重验。** [claude-warm-summary.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/drivers/claude-warm-summary.ts)通过forked session运行Claude的`/compact`，复用live launch contract；没有fork能力就拒绝，结果需有session ID，usage-limit单独标记。执行结束若signal取消或live turn繁忙，不采用fork；host再检查resume cursor仍是原session。最后两次用户消息及其后内容被标为“尚未交给新session”，下轮原样重送，cursor/handed state由store保存。这保住近期原话，不等于整个历史无损。
4. **共享分成可见性、操作权限、输出裁剪。** [shared/bot-access.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/shared/bot-access.ts)定义none/view/chat/edit及旧visibility迁移；[bot-access-gate.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/host/bot-access-gate.ts)除路径目标外，通过parsed-body hook检查body里thread和新建room成员、routine目标。GET/HEAD默认view；聊天写入需chat；改分享需edit；会改变模型/技能等的审批卡也单独要求edit。入口[HTTP gate](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/index.ts#L12895-L12902)先对不可见对象返回404，再运行操作权限403，不能仅依赖前端隐藏按钮。
5. **事件流也按接收人收窄。** [bot-visibility.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/bot-visibility.ts)的memberBot/shownConversations裁掉别人的private thread、消息和选中状态；frameForMember逐类检查message、runtime、screen、routine等事件。bot从可见变不可见时，对曾见过它的流发一次bot.deleted；从未见过则不泄露删除事件。Team admin能管理bot，并不因此得到其他人的私聊。这里是静态检查到的具体防线，不是整个系统安全审计结论。

### 4）技术亮点
- **性能优化服从会话一致性。** 预摘要不是直接覆盖原历史：fork、取消、session前置条件、最近两轮原文重送形成一套竞态处理，费用也按真实摘要调用记账。源码注释的35–60秒案例属于项目自述测量，本轮未复测，不宣称固定提速幅度。
- **授权不止HTTP路径。** 同一请求可在body引用另一个thread，SSE也可能继续泄露撤权对象；该库同时处理请求目标、操作等级和每接收人的输出。这对多租户Agent比“所有人都能调用一套MCP工具”更有借鉴意义。
- **后台工作有资源约束。** 费用超限、内存紧张、即将发生的routine与用户活动都参与调度，避免把空闲优化变成争抢前台的无上限任务。

### 5）今日热度：事实与缺证
昨日只读到v0.1.134；现已新增[v0.1.135](https://github.com/milind-soni/OpenMausBot/releases/tag/v0.1.135)（10月31日15:51:30北京／07:51:30 UTC）和[v0.1.136](https://github.com/milind-soni/OpenMausBot/releases/tag/v0.1.136)（11月1日07:27:12北京／10月31日23:27:12 UTC）。前者把昨天仍在main的自托管home迁移纳入release说明；后者列出Team逐bot分享、空闲长会话摘要、界面窗口框及多项工具/线程修复。最近三提交分别是Mac构建runner更新、0.1.136版本号、窗口框开关。这些是可核发布活动，**不是证明新增Stars来自它们的传播归因；暂无足够公开证据解释今日热度**。

开放[issue #4047](https://github.com/milind-soni/OpenMausBot/issues/4047)报告0.1.131配合Codex 0.165.0启动实例时重复clone已安装插件的marketplace；报告者明确尚未确定配置由谁创建，也未声称在0.1.136复现，不能说“当前版本已确认存在同一缺陷”或把全部流量归因于该库。开放[PR #4046](https://github.com/milind-soni/OpenMausBot/pull/4046)拟放宽Windows冷启动测试等待，正文称CI失败阻止Cloud自动rollout；这是作者说明，**GitHub release已发布不等于所有Cloud已升级**。另有[#4048](https://github.com/milind-soni/OpenMausBot/issues/4048)提议社区bot模板，不应写成现成功能。

### 6）对用户AI／全栈工程的价值
做Node/Python后台Agent时，优先借鉴“后台派生结果只能在原状态仍有效时提交”，用于摘要、RAG索引更新和长任务结果回填；不能把存有摘要文件等同于它覆盖了最新消息。做React/Next.js团队控制台时，优先读bot-access-gate与frameForMember：授权应该在服务器执行，撤权还需同步清理客户端已有状态，私聊过滤不能被admin角色粗暴绕开。Python/Django可以移植同样的状态前置条件和对象级权限，但不是直接复制TS模块就获得隔离。对现有个人助手，首先评估版本/插件来源和更新策略，再决定安装；本轮未更改任何配置或运行仓库。

**实际覆盖与限制**：完整递归tree（未截断）；README与根manifest；server/index.ts入口导入1–130及摘要装配、turn事件、beforeTurn、HTTP gate等定向段；warm-summary、warm-summary-host、claude-warm-summary、bot-access-gate、shared/bot-access全文；bot-visibility权限和投影/事件流实现；最近3提交、最近2 release、3条开放issue/PR正文、昨日到今日compare。一次猜测路径`server/host/bot-visibility-gate.ts`未获取到文件，不用于结论。完整index已获取但仅定向阅读；未逐行审计全仓、未构建、安装、调用模型、进行权限攻击测试或复现性能/issue。compare文件列表截到300项。

## 7. pbakaus/impeccable

### 1）项目数据
- [仓库](https://github.com/pbakaus/impeccable)：**#7，98,344 Stars，1,338 stars today，Rust**；昨日#3，本次下降4位，不代表质量或累计Stars下降。
- 固定[4f956490f0056ae1ff5ea80372cf56e83c001d3c](https://github.com/pbakaus/impeccable/commit/4f956490f0056ae1ff5ea80372cf56e83c001d3c)，相对昨日 `df3a4abe` [前进10 commits](https://github.com/pbakaus/impeccable/compare/df3a4abe7d0840d5f60324812c432e00b66a4e75...4f956490f0056ae1ff5ea80372cf56e83c001d3c)，其中包含3次生成产物同步，不是10项独立功能。

### 2）解决什么问题
它为编码Agent提供设计改进词汇、产品/视觉上下文和确定性UI检查，减少“把页面改好看”式宽泛指令。它**不只是提示词合集**：Rust引擎承担静态/浏览器检查、hooks和live工具；但也**不是独立模型运行时**，设计判断和改代码仍依赖宿主Agent。README展示图不是对所有项目的效果保证。

### 3）实际实现
- [Cargo.toml](https://github.com/pbakaus/impeccable/blob/4f956490f0056ae1ff5ea80372cf56e83c001d3c/Cargo.toml)组织多个crate，共享serde、regex等；[CLI入口](https://github.com/pbakaus/impeccable/blob/4f956490f0056ae1ff5ea80372cf56e83c001d3c/crates/cli/src/main.rs)统一分发动词与退出码，将detect、context、hook、build-phase、live交给各模块，并提供engine-probe握手。
- 今日源码重点是 [cdp.rs](https://github.com/pbakaus/impeccable/blob/4f956490f0056ae1ff5ea80372cf56e83c001d3c/crates/browser/src/cdp.rs)：旧逻辑等待命令响应期间把事件堆进队列，新Connection.next返回Result或Event；Page.send_with_timeout边等待边交给on_event处理，命令后再扫尾。不等命令完成才释放worker auto-attach，也不让页面异常洪水无限占内存；page错误保留上限为50。
- [build_completion.rs](https://github.com/pbakaus/impeccable/blob/4f956490f0056ae1ff5ea80372cf56e83c001d3c/crates/hook/src/build_completion.rs)写会话identity前，逆向查找env文件最后一个有效export，相同就不再追加。它解决每次resume继续膨胀环境文本的问题，而非删除全部重复历史。
- [documenter规范](https://github.com/pbakaus/impeccable/blob/4f956490f0056ae1ff5ea80372cf56e83c001d3c/skill/agents/impeccable-documenter.md)要求依据实际构建写设计系统；已有DESIGN.md必须先获得refresh/overwrite/merge选择，否则不写。已有缺陷不得被包装成以后沿用的设计规范。这里是Agent契约，不是文件系统层强制权限。

### 4）技术亮点
1. **同步协议也必须及时处理事件**：等待RPC响应并非可以停止处理事件；worker等待恢复、客户端等待worker结果会形成互等。此次改动比简单增加超时时间更接近根因。
2. 有限错误样本防止观测系统被坏页面拖垮；相应浏览器测试在找不到浏览器时会直接返回，不能仅凭测试名或测试套件绿灯就断言真实浏览器路径跑过。
3. 最新 [route回归测试](https://github.com/pbakaus/impeccable/blob/4f956490f0056ae1ff5ea80372cf56e83c001d3c/crates/cli/tests/live_server_security.rs)构造同页两处编辑和另一页复用ref，断言只丢弃指定page+ref、保留同胞编辑。不带ref仍是整页丢弃。这次HEAD是补测试，**不是证据表明今天才新增ref撤销实现**。

### 5）今日热度：事实与缺证
上述10项提交发生在10月31日14:41到**11月1日02:13北京时间**（10月31日06:41到18:13 UTC）；最新release仍为[skill-v4.8.0](https://github.com/pbakaus/impeccable/releases/tag/skill-v4.8.0)（10月27日07:41北京／10月26日23:41 UTC）及engine-v0.1.18，不能把main修复当已分发到所有安装。开放 [issue #1268](https://github.com/pbakaus/impeccable/issues/1268)报告Angular绑定被broken-image误判，说明静态规则有框架语法边界；本期未检查该具体规则或复现。开放 [PR #1267](https://github.com/pbakaus/impeccable/pull/1267)拟修复交互安装新宿主被跳过，亦未算入main。**暂无足够公开证据解释今日热度**；持续修复是同期活动，不是涨星归因。

### 6）对用户AI / 全栈工程的价值
React/Next.js用户值得重点看CDP事件处理与设计系统记录；做浏览器Agent、UI验收或爬取器时，必须区分命令应答和异步事件，并给错误收集设置明确上限。Node/Python也可移植该状态机，不必采用Rust。做工具插件时，env注入应幂等、用户原有设计资产应有明确修改选择。不要把规则误报简单归为页面错误，也不要把生成的设计文档当视觉验收替代品。

**实际覆盖与限制**：完整递归树；README功能段、Cargo.toml、CLI main；build_completion与documenter全文；cdp核心连接/事件处理及新增测试、live route新增测试与完整compare diff；最近3提交、比较范围全部10条元数据、2 release、2开放issue/PR。大型cdp文件非逐行全审；未执行浏览器、Rust测试、安装流程或live撤销。

## 8. obra/superpowers

### 1）项目数据
- [仓库](https://github.com/obra/superpowers)：**#8，310,096 Stars，665 stars today，Shell**。
- 固定[2ce8aa15d05bd57213e6f746f953aafb7ded7a8b](https://github.com/obra/superpowers/commit/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b)。昨日未在前十，本次进入；昨日报告已记载它在更早的10月30日前十，所以不能称首次上榜。没有昨日该仓固定HEAD，不虚构日diff。

### 2）解决什么问题
它把澄清需求、写设计、计划、TDD、子Agent实现、分层review与完成验证组织成编码方法。**没有独立模型运行时**；仓库是技能、宿主bootstrap与辅助脚本。不同宿主安装入口不等于所有平台会同样执行每项规则，本期不验证兼容性。

### 3）实际实现
- [package.json](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/package.json)版本7.0.1，没有常规依赖列表，main指向OpenCode插件，另声明Pi extension与skills。Claude入口是 [hooks.json](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/hooks/hooks.json)的startup/clear/compact同步SessionStart hook。
- [session-start](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/hooks/session-start)读取using-superpowers文本，JSON转义并按宿主输出不同context字段；用Bash内建读文件减轻启动时PATH损坏的影响，避免给Claude同时输出多个会被重复读取的字段。它注入指导，不加载新模型。
- [subagent-driven-development](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/subagent-driven-development/SKILL.md)为每个plan创建独立workspace/ledger，以文件brief派发fresh-context实现者。**明确禁止多个实现者并行**以避免冲突；每任务review后再推进，最后whole-branch review，不应把它笼统宣传成“自动并行开发框架”。
- 同一流程在派发前固定BASE，review package包含BASE到HEAD全部提交，而不是HEAD~1，避免多commit任务漏审。reviewer只接brief、报告、固定diff与约束；[task-reviewer模板](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/subagent-driven-development/task-reviewer-prompt.md)分别给spec和quality结论，默认不重复整套测试，对明确风险才做定向检查。

### 4）技术亮点
计划级ledger用Git提交与报告指针恢复状态，减少context压缩后重复派单；固定审查范围及禁止worker私自加reviewer控制重复成本。不过模板一面要求不信实现者报告，一面在Tests段预设已有TDD证据，**没有为缺少RED失败运行证据给出明确严重级别**。这是已读文本中的具体覆盖缺口，不等于所有使用者都会漏测。技能允许对一般歧义写ruling继续，但对破坏性、安全敏感及共享分支等外部副作用要求暂停；实际授权仍应由宿主保证。

### 5）今日热度：事实与缺证
[v7.0.1](https://github.com/obra/superpowers/releases/tag/v7.0.1)发布于**10月22日05:05:11北京时间（10月21日21:05:11 UTC）**，调优brainstorming并拆短长技能以适应context压缩，不能称今天新版本。开放 [issue #2651](https://github.com/obra/superpowers/issues/2651)提出缺失RED证据仍可能通过review；报告者给小样本、单模型非正式实验，并明确未运行提议文本，不能当产品评测结论。开放 [PR #2649](https://github.com/obra/superpowers/pull/2649)只是拟加harnessator来源manifest，不是已上线新集成。**暂无足够公开证据解释今日热度**；大体量Stars和再次进前十不构成传播因果。

### 6）对用户AI / 全栈工程的价值
适合借鉴到React/Next、Node、Python/Django的任务执行流程：记录任务前BASE、持久化ledger、让实现与审查使用相同brief。最值得补强的是测试证据契约：失败命令、失败原因、修复后输出都应可定位，且不能把“理论上会失败”当实际RED。若自己做并行Agent系统，可对照mattpocock的独立worktree/frontier方案，明确本库SDD默认串行，而不是混用两套并发假设。

**实际覆盖与限制**：完整递归树；README说明段、package.json、hooks.json、session-start、SDD SKILL与task-reviewer全文；最近3提交、2 release、2开放issue/PR。未执行hooks、测试或评估；其余平台适配与其他技能未逐一审计，issue的真实项目事故未复现。

## 9. lightpanda-io/browser

### 1）项目
- [lightpanda-io/browser](https://github.com/lightpanda-io/browser)：今日第 **9**，**39,287 Stars**，**929 stars today**，主要语言 **Zig**。
- 固定提交 [cebb8d51e60a68815591a5c7874823b988530aa8](https://github.com/lightpanda-io/browser/commit/cebb8d51e60a68815591a5c7874823b988530aa8)，提交于11月1日09:05:41北京时间（01:05:41 UTC）。昨天前十未出现，不意味着首次登榜；没有昨日同仓HEAD，不编逐日diff。

### 2）它到底解决什么问题
为网页采集、自动化与AI Agent提供有JavaScript执行能力的无头浏览器，试图减少直接运行完整桌面Chrome的资源负担。它不是Chromium fork：Zig实现浏览器层，复用V8执行JavaScript、Libcurl联网和html5ever解析HTML。它有文本型PNG/PDF输出，但不能因此当作Chrome视觉渲染等价替代品。README的“16倍省内存、9倍快”是作者特定工作负载基准，**本轮未复现，不作为普遍性能结论**。

### 3）它实际上怎么实现
- [build.zig.zon](https://github.com/lightpanda-io/browser/blob/cebb8d51e60a68815591a5c7874823b988530aa8/build.zig.zon)标为1.1.0-dev、最低Zig 0.17.0，固定V8 fork、curl、BoringSSL、SQLite、压缩库与zenai等来源/hash；当前源码版本不能等同于最近稳定release。
- [main.zig](https://github.com/lightpanda-io/browser/blob/cebb8d51e60a68815591a5c7874823b988530aa8/src/main.zig)按fetch/serve/mcp/agent等模式分派。fetch创建专用线程，让Browser/V8 isolate的初始化、使用、析构落在同线程；MCP HTTP监听与伴随CDP监听争用主线程时明确拒绝组合，不隐藏资源冲突。
- [ToolSession.zig](https://github.com/lightpanda-io/browser/blob/cebb8d51e60a68815591a5c7874823b988530aa8/src/ToolSession.zig)给每个工具上下文独立Browser/V8 isolate、Session、Notification和节点Registry；同线程交错操作要成对enter/exit isolate。重启session会丢页面、cookie、storage和history，而普通脚本结束并非重启整个session。
- [mcp/tools.zig](https://github.com/lightpanda-io/browser/blob/cebb8d51e60a68815591a5c7874823b988530aa8/src/mcp/tools.zig)在编译期把浏览器工具枚举映射成MCP schema，新增工具必须显式分类副作用。run要求script/path二选一、timeout至少1ms，默认60秒；path经过isPathSafe后读取。执行前记录页面集合，defer关闭本次新开的页面，但保留cookie/storage。console截到64KiB并标明截断，返回值单独保存，避免日志挤掉结果；超时/异常返回isError而非假装完成。
- 同一文件的save将环境机密字面值尽量反向替换成$LP_*占位符再保存；工具说明要求客户端不要内联已解析秘密。这是减漏措施，**不是完整秘密泄漏防护或权限授权机制**。

### 4）技术亮点
最有借鉴价值的是“同一浏览器原语，多种控制面”：MCP、Agent和可回放JavaScript复用工具定义，而不是每个入口重新实现点击/提取。脚本临时页面与会话长期cookie生命周期分离，适合多步骤登录工作流。工具副作用注解也较严谨：导航会写cookie、等待会让页面脚本运行，因而不轻率标read-only；evaluate/click/callPageTool不承诺无害。注解只给客户端提示，不等于服务器授权。README还明确默认发送使用遥测，可用LIGHTPANDA_DISABLE_TELEMETRY=true关闭，评估前应纳入数据治理。

### 5）为什么今天突然火
最近三提交包括hot-code orderfile刷新，以及10月31日23:42:24 UTC（北京时间11月1日07:42:24）合并的MCP脚本path运行支持，当前实现已实读。最近稳定 [1.0.2](https://github.com/lightpanda-io/browser/releases/tag/1.0.2)发布于10月23日17:01:02北京（09:01:02 UTC），包含CDP、Web API和稳定性改进，不是今天发布。开放 [issue #4334](https://github.com/lightpanda-io/browser/issues/4334)报告macOS自带Bash 3.2不支持生成补全脚本里的mapfile；[PR #4336](https://github.com/lightpanda-io/browser/pull/4336)提出兼容修复，作者测试结果非本轮实测，也不能计入已合并能力。轻量浏览器与MCP的结合有场景吸引力，但**暂无足够公开证据解释今日热度**，不能用性能宣传或同期维护替代涨星因果。

### 6）对用户的价值
对Node/Python Agent与网页RAG，可作为有JS页面采集和浏览器工具层的候选，先用自己的目标站点检查Web API/CDP兼容、重定向、cookie、动态内容与失败输出；不要仅按作者基准替换现有Playwright/Chrome。对全栈工程师，优先读runScript的资源回收、预算和错误语义：把模型探索转成可审计脚本可以减少运行期模型依赖，但网站变化仍会使脚本失效，不等于外部网页结果确定。MCP session隔离是浏览上下文隔离，不应直接当多租户身份鉴权或恶意代码安全沙箱。

**实际检查记录与限制**：实读完整递归树、README、build.zig.zon、main入口分派、ToolSession全文、MCP tools生产分派/run/save/session代码及部分测试；最近3提交、2稳定release、3条开放issue/PR。大型main与tools测试部分未逐行全审；未构建、运行浏览器、联网实测目标站点或复现作者benchmark。

## 10. HKUDS/DeepTutor

### 1）项目
- [HKUDS/DeepTutor](https://github.com/HKUDS/DeepTutor)：今日第 **10**，**52,878 Stars**，**1,034 stars today**，主要语言 **Python**。
- 默认main固定提交 [f7aed0744c36c5afef16a4261c31ebee1208cac2](https://github.com/HKUDS/DeepTutor/commit/f7aed0744c36c5afef16a4261c31ebee1208cac2)。[相对昨日1ea7df1的比较](https://github.com/HKUDS/DeepTutor/compare/1ea7df155447f4caf0e3abc86b3ff5395479cd4a...f7aed0744c36c5afef16a4261c31ebee1208cac2)为ahead **357 commits**；返回文件列表300项触及上限，不称全量审计。这是两次固定HEAD之间的历史增量，不声称357提交全在一天写成。

### 2）它到底解决什么问题
把学习资料、RAG、教学对话、笔记、练习和长期学习工作区连起来，而不是一次性PDF问答。今天有真实v1.7.1增量：桌面预览将Python/Node本地运行时与Web UI封装给用户；对工程师，本期重点是“完整AI应用如何交付到本机并可恢复更新”，以及昨天发现的文档索引遗漏如何闭环。功能存在不证明学习成效。

### 3）它实际上怎么实现
- 根[pyproject.toml](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/pyproject.toml)要求Python >=3.11,<3.15，CLI入口deeptutor_cli.main:main；server/web/knowledge/memory等同版本模块分发，full为组合安装。桌面[package](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/apps/desktop/package.json)以Electron 45.1.0启动src/main.mjs，不是把Python翻译成桌面原生代码。
- [runtime.mjs](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/apps/desktop/src/runtime.mjs)区分attach/source/bundled：attach只等待既有loopback服务、owned=false；自有模式以独立runtimeHome启动Python后端，再等/health/ready，接着启动Next前端。构建中API/auth占位符在可丢弃缓存里替换，不修改签名bundle。服务就绪后每10秒探测，连续3次失败进入error并停止自有进程。
- [bundles.mjs](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/apps/desktop/src/bundles.mjs)检查manifest格式、架构/平台、runtimeId、文件名及签名，再校验压缩包SHA-256；解压进.installing，检查必要文件后rename发布。已装同ID但hash/signature不同会拒绝复用。[main.mjs](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/apps/desktop/src/main.mjs)更新前停worker、备份workspace、写testing事务，候选runtime ready后再切active；中断恢复将当前workspace移走，恢复备份和previous manifest。这是显式回滚设计，并非“启动失败就随便重装”。
- 昨日追踪的参考文献缺口已有实际源码变化：[source_pages.py](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/deeptutor/services/rag/source_pages.py)新增_list_item_pieces递归展开字符串/列表，_block_text读取list_items；页眉/页脚/页码排除，且纯页码页面不再通过原生PDF文本fallback重新混入。保留aside_text、page_footnote等有意义文本；缺页码参考文献作为unlocated补充，而不伪造物理页。对应[测试](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/tests/services/rag/test_source_pages.py)检查正文、参考文献、页码、表格caption和缺页定位等路径；本轮只读未跑。

### 4）技术亮点
1. 桌面壳把不可变运行包、可丢弃UI缓存、用户workspace、更新事务分开，适合Python AI后台+Next.js前端的本地交付。
2. [processes.mjs](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/apps/desktop/src/processes.mjs)用shell:false启动，POSIX按进程组停止、Windows用taskkill树；stop幂等，先TERM等候再KILL，防止只杀leader留下后代。attach模式不拥有服务，不能停止他人的进程。
3. Electron内容view启用contextIsolation/sandbox、禁nodeIntegration；shell IPC校验sender、主frame和精确shell URL，外部导航转系统浏览器。它们是可检查的边界，但不是整套产品安全审计结论。
4. RAG输入覆盖修复比“换更强模型”更直接：昨日确实缺list_items，今天实现与回归断言都可核对。[PR #2223](https://github.com/HKUDS/DeepTutor/pull/2223)于10月31日17:54:24北京时间（09:54:24 UTC）已合并；#2224关闭但未合并，不能把两个PR都写成合并。

### 5）为什么今天突然火
[v1.7.1](https://github.com/HKUDS/DeepTutor/releases/tag/v1.7.1)确于**11月1日00:51:40北京时间（10月31日16:51:40 UTC）**发布，桌面预览、多语言、账户控制、检索/文档可靠性是可核发布事件。发布说明同时限制：桌面预览来自dev的成功workflow artifact，需登录且7天到期；Windows预览未签名。不能宣传成已验证的稳定桌面安装包。
最新开放 [PR #2281](https://github.com/HKUDS/DeepTutor/pull/2281)报告Windows多worker旧聊天迁移竞态；本轮直接读[legacy_migration.py](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/deeptutor/services/session/legacy_migration.py)，确认fcntl不可用时锁确实空操作，没有msvcrt分支，支持其静态机制判断，但未复现作者并发测试。#2280与#2279还提出ZIP冲突错误信息、旧编码文件名修复，均不能算已发布。**新版本是同期事实，仍暂无足够公开证据将今日Stars增长归因于该发版**；排名保持第10也不是质量信号。

### 6）对用户的价值
最值得用于Python/Django+Next.js AI产品的，是runtime生命周期、来源签名校验、状态可观察性和升级回滚，不仅是Electron窗口。已有RAG项目则优先补上源元素覆盖测试：解析器产出、chunk实际接收和引用可回原页必须分别检查。此次参考文献修复适合作为昨日问题闭环案例；Windows迁移空锁又提醒跨平台产品不能用“Linux路径有锁”推出整体并发安全。桌面preview可研究，不宜未经自己数据备份与测试便替换学习生产环境。

**实际检查记录与限制**：完整递归树；README与pyproject；桌面package、main/runtime/processes/bundles/config全文及runtime测试；source_pages相关构建函数和test_source_pages全文；legacy_migration全文；最近3提交、2 release、3条开放PR及2223/2224合并状态；昨日→今日compare。未运行Electron、安装模型/模块、执行测试、迁移资料或下载桌面artifact；357提交未逐一审查，源码静态修复不等于端到端效果已复现。

## A. 今天最值得深入看的3个项目

1. **pingdotgg/t3code：先看状态正确性，再看界面功能。** 优先读 [IdleCompaction.ts](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/apps/server/src/orchestration-v2/IdleCompaction.ts)、[IdleCompactionService.ts](https://github.com/pingdotgg/t3code/blob/481ff3ea89c7358953e8b7ffb762978c31fb3a0b/apps/server/src/orchestration-v2/IdleCompactionService.ts) 与 [Cursor adapter本次修复](https://github.com/pingdotgg/t3code/commit/481ff3ea89c7358953e8b7ffb762978c31fb3a0b)。它同时展示“压缩前重验待处理工作”和“外层完成不代表工具完成”；内存timer缺少启动恢复的边界也明确，适合设计可靠Agent后台。
2. **milind-soni/OpenMausBot：看团队权限如何穿过整个数据流。** 打开 [bot-access-gate.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/host/bot-access-gate.ts) 与 [bot-visibility.ts](https://github.com/milind-soni/OpenMausBot/blob/88d54eb17a3655b968470cbbf3b5097de225a8b5/server/bot-visibility.ts)：请求body、对象可见性、操作等级、逐接收人SSE和撤权必须一起处理。对React/Next.js控制台加Node/Python服务端，比只抄一个聊天组件更有学习价值。
3. **HKUDS/DeepTutor：把RAG缺口闭环与产品交付一起读。** 对照 [source_pages.py](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/deeptutor/services/rag/source_pages.py) 和 [test_source_pages.py](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/tests/services/rag/test_source_pages.py)，看昨天的参考文献遗漏如何落到实现与回归断言；再读 [desktop runtime](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/apps/desktop/src/runtime.mjs) 与 [bundle验证](https://github.com/HKUDS/DeepTutor/blob/f7aed0744c36c5afef16a4261c31ebee1208cac2/apps/desktop/src/bundles.mjs)，理解Python后台+Next前端的本地生命周期、更新与恢复。桌面仍是preview，不建议跳过自己的备份和验收直接替换生产环境。

## B. 今天的技术趋势

以下仅是本次前十源码样本的共性，不外推为整个行业或长期趋势。

- **上下文优化开始受运行状态约束，而不是只看token数量。** OpenMaus的fork预摘要会检查用户活动和session前置条件；T3的空闲压缩还检查cache到期、后台工作和待请求。两者都值得学习，不能忽略T3重启后timer恢复仍在提案中的差异。
- **“成功”的粒度正在细分。** T3把没有工具结束信号的动作标为interrupted；claude-mem把捕获、入库、索引副作用分离；DeepTutor把运行包安装、健康就绪、切换active和回滚分开。AI应用应展示可核实的阶段状态，不以一枚完成标记代替所有副作用证据。
- **技能库的核心资产是证据与交接契约，而非角色数量。** Game Studios绑定内容hash与审查receipt，superpowers固定BASE→HEAD审查范围，mattpocock新增外部状态/可丢弃run词汇。不过这些规范有软约束，Game的过期证据不改verdict、superpowers缺失RED证据分级不明确，不能当作强制正确性保障。
- **浏览器工具的协议和生命周期比“能点击”更值得看。** impeccable在等待CDP响应时立即处理异步事件并限制错误样本；Lightpanda将MCP、脚本及浏览器原语统一，区分临时页面与会话状态。二者都不等于网站兼容性或视觉结果已经验证。
- **RAG可靠性仍取决于输入与定位。** DeepTutor新增list_items参考文献读取且抑制页码fallback回流；claude-mem对向量命中再hydrate并做范围过滤。它们说明解析覆盖、真实存储与索引一致性值得独立测试，不是单纯换模型可解决。


## C. 与昨天相比

基线为上方已核验的2026-10-31实际报告；今日为2026-11-01 10:19:29北京时间的浏览器截面。它们相隔约24小时，不是统一时间窗的涨星计量。

| Repository | 昨日→今日 | 可确认的排行变化 |
|---|---|---|
| thedotmack/claude-mem | 1 → 1 | 位置不变 |
| mattpocock/skills | 8 → 2 | 上升6位 |
| Donchitos/Claude-Code-Game-Studios | 前十外 → 3 | 新进入本报告前十；不是新发布或首次上榜 |
| pingdotgg/t3code | 9 → 4 | 上升5位 |
| Renhuai123/ziwei-doushu | 5 → 5 | 位置不变 |
| milind-soni/OpenMausBot | 2 → 6 | 下降4位 |
| pbakaus/impeccable | 3 → 7 | 下降4位 |
| obra/superpowers | 前十外 → 8 | 新进入本报告前十；不是新发布或首次上榜 |
| lightpanda-io/browser | 前十外 → 9 | 新进入本报告前十；不是新发布或首次上榜 |
| HKUDS/DeepTutor | 10 → 10 | 位置不变 |

- **新进入前十3项**：Claude-Code-Game-Studios、superpowers、Lightpanda。昨天前十中的CopilotKit/OpenBot、expo/skills、macro-inc/macro今天不在前十；仅据此不能推断它们失去关注或项目降温。
- **保留7项**：claude-mem、mattpocock/skills、t3code、ziwei-doushu、OpenMausBot、impeccable、DeepTutor。至少连续两个实际观察日进入前十，不把缺失日期推成连续纪录。
- **排名与技术更新不是同一信号**：claude-mem仍第1但HEAD未变；ziwei仍第5且HEAD未变。新阅读可以带来新的工程理解，但本报告不把补读旧代码说成今天新增功能。

- **可确认的代码/发布差异**：mattpocock +2 commits，新增内容仍在in-progress；impeccable +10 commits包含生成同步；T3 +140、OpenMaus +24、DeepTutor +357是两次HEAD之间的历史增量，不代表这么多独立功能或全部一天写成。后三仓compare文件清单均达到300项，已按实际重点文件审查，不冒称全量。T3 v0.1.6、OpenMaus v0.1.135/136、DeepTutor v1.7.1为昨日报告后的可核发布，正式版、nightly与桌面preview各自限定见条目。
- **明确闭环**：DeepTutor昨天的list_items参考文献遗漏，今天已由合并PR #2223及固定实现/测试支持修复；测试未在本轮运行。新主题是浏览器MCP脚本回放与证据hash绑定；它们来自今日新进样本，而非宣称行业今天才出现这些设计。
