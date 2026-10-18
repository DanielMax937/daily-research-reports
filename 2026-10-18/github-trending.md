# GitHub Trending 源码深读｜2026-10-18

> 今日样本：GitHub Repositories · Daily / Today · All languages / Any · Any spoken language，严格按官方网页当前前十。热度不是质量、安全性或许可证评级。

## 抓取口径、新鲜度与阅读边界

- 官方榜单：[GitHub Trending Daily](https://github.com/trending?since=daily)。直接公开 HTTP GET 于 **2026-10-18 10:20:06 北京时间（02:20:06 UTC）**取得 200 响应，响应 Date 为同秒 GMT，Cache-Control 为 `max-age=0, private, must-revalidate`；页面显示 Language: Any、Spoken Language: Any、Date range: Today
- 原始页含 13 张仓库卡片，只取原顺序前十；未使用搜索缓存、第三方转载或昨日名单补位。HTTP Date 证明响应时间，不证明 GitHub 后台恰在该秒重算；官方未给榜单生成时间
- 所有语言、总 stars、stars today 来自同一次官方卡片快照。stars today 的精确窗口未公开，不等于北京时间零点以来，也不能用两天总 stars 之差替代。排序并不按页面显示的 stars today 数值单调排列
- 源码分别锁定读取时的完整 commit SHA，略晚于榜单，非原子快照。静态读取 README/docs、目录、依赖、入口、核心切面、近期 commits/releases/issues；未运行仓库代码、安装依赖、调用模型或测试性能。维护者的规模/效果宣称与本次确认的实现分开
- 匿名 GitHub API 部分请求遇到共享限流，相关读取转用已连接 GitHub 只读接口及官方 raw；具体覆盖/缺失在各项目说明。文件存在或下载完成不等于逐行审计；闭源宿主、外部服务和模型权重不由仓库公开切面证明
- 昨日基线取自[2026-10-17 完整固定归档](https://github.com/DanielMax937/daily-research-reports/blob/974fcf26a695695336e3be203e71394535508629/2026-10-17/github-trending.md)，已读取全文；连续项目压缩旧背景，重点核实现变化和反馈状态。今日 main 不变的项目明确标注，不制造“今日发版”
- 快照校验：HTML **610,622 bytes**，SHA-256 `6e53bd9a710338818d08a04927ccdb2b08b3695ccbb6386534212ab990d8b702`。这是本次样本标识，不是 GitHub 官方历史榜单存档

## 今日官方前十

| 排名 | 仓库 | Stars | stars today | 页面语言 |
|---:|---|---:|---:|---|
| 1 | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | 41,821 | +1,397 | Python |
| 2 | [MadsLorentzen/ai-job-search](https://github.com/MadsLorentzen/ai-job-search) | 50,512 | +1,365 | Python |
| 3 | [affaan-m/ECC](https://github.com/affaan-m/ECC) | 282,556 | +1,145 | JavaScript |
| 4 | [HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything) | 54,091 | +574 | Python |
| 5 | [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | 52,281 | +878 | Python |
| 6 | [akitaonrails/ai-memory](https://github.com/akitaonrails/ai-memory) | 9,945 | +178 | Rust |
| 7 | [android/skills](https://github.com/android/skills) | 8,446 | +355 | Kotlin |
| 8 | [stablyai/orca](https://github.com/stablyai/orca) | 95,480 | +830 | TypeScript |
| 9 | [anthropics/claude-code](https://github.com/anthropics/claude-code) | 151,796 | +179 | TypeScript |
| 10 | [debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio) | 73,480 | +2,125 | Python |

第 11–13 名为 anomalyco/opencode、ruvnet/ruflo、xerj-org/xerj，不纳入今日十项目深读。

## 1. anthropics/claude-plugins-official

### ① 排名、元数据与源码增量

官方今日第 **1**；[仓库](https://github.com/anthropics/claude-plugins-official)；**41,821 stars，+1,397 stars today，Python**。今日重新读取 main，完整 SHA 仍为 **ea10b213686c90bb1984b2016937310e05336cf3**，提交于 **2026-10-16 02:40:21 UTC**，**与昨日完全相同，没有主干源码增量**。递归树仍为 817 条目、573 文件、未截断；[releases](https://github.com/anthropics/claude-plugins-official/releases)仍为空。它不是一个统一版本的 Python 应用，插件与外部来源应分别核版本和许可证；本次切入的 Hookify README 标注 MIT，不能把它扩展为全目录的授权结论。

### ② 它解决什么问题

这是 Claude Code 的插件分发目录，将 skills、命令、agents、hooks、LSP/MCP 配置组织成可发现的安装单元。连续上榜的背景不再重复展开：今天重点看 **Hookify 如何把自然语言提出的工作规则变成事件匹配，以及规则究竟在哪些地方会失效**。它适合希望减少反复提醒的编码 Agent 用户；替代方式是自己写 hook 或在项目规则中说明要求。自然语言说明、匹配程序和宿主权限系统是三个不同层次。[根 README 与信任边界](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/README.md#L1-L42)、[Hookify README](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/README.md)

### ③ 架构、入口与三个实际机制

**分发层仍是目录。** 今日重新统计的 [marketplace.json](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/.claude-plugin/marketplace.json)含 **315 个条目：53 个字符串形式的本地 source、262 个外部 source 对象**。这个数是注册项数量，不是 315 个服务的源码审计。Hookify 位于本仓 `plugins/hookify/`，运行代码只用 Python 标准库；[hooks.json](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/hooks/hooks.json)将 PreToolUse、PostToolUse、Stop、UserPromptSubmit 分别接到四个 Python 进程，配置超时均为 10 秒。

1. **规则是即时读入的轻量数据，而非编译好的安全策略。** [PreToolUse 入口](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/hooks/pretooluse.py#L27-L51)从 stdin 读 JSON，按工具名区分 bash/file，再加载当前工作目录 `.claude/hookify.*.local.md`。[config_loader](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/core/config_loader.py#L87-L241)自己解析一个有限的 YAML 风格子集，筛掉 disabled 及不匹配事件的规则；不是调用完整 YAML 解析器。简单 pattern 会按事件转换为一个条件，复杂 conditions 列表则保留多个条件。每次 hook 都重新读文件，因此修改规则不依赖长期运行的缓存服务。
2. **匹配和宿主反馈有明确、但有限的语义。** [rule_engine](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/core/rule_engine.py#L35-L180)先累积所有命中规则，block 优先于 warn；同一规则的条件必须全部成立。regex_match 使用忽略大小写的 Python 正则，编译缓存最多 128 项；contains/not_contains 是普通字符串包含关系，tool_matcher 的竖线则仅分隔精确工具名。命中 block 时，PreToolUse 输出 permissionDecision=deny，Stop 输出 decision=block；prompt 等其他事件只返回消息。代码也给 PostToolUse 构造 deny 字段，但其动作已经发生，**不能把事后 hook 写成撤销操作或事务回滚**。[字段提取与正则实现](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/core/rule_engine.py#L182-L273)
3. **失败默认放行，输入编码因此属于规则正确性的一部分。** [pretooluse.py](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/hooks/pretooluse.py#L29-L62)直接 json.load(sys.stdin)，没有在本层强制 UTF-8；异常时返回错误消息并 exit 0。[规则文件读取](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/core/config_loader.py#L244-L274)同样裸 open，解析/解码失败会返回 None、跳过规则。这样设计保护了编码会话的可用性，却意味着一个未加载的 block 规则不会形成拒绝。今天 [#6306 的新评论](https://github.com/anthropics/claude-plugins-official/issues/6306#issuecomment-6244438209)报告韩文 Windows cp949 下 JSON 可成功解析、文本却已损坏，规则静默不命中。**当前源码的默认解码和 fail-open 路径已核；各 Windows 字符与绕过比例来自报告者，本次没有运行复现。**

### ④ 亮点与边界

可借鉴的是把“触发条件”“给 Agent 的说明”“宿主返回协议”拆开，便于团队审查规则文件。边界也应以实现为准，不能将“容易创建 hooks”理解为完整的命令语义分析、可信隔离或强制合规系统。

一个非常具体的文档/实现落差是 [require-tests-stop 示例](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/examples/require-tests-stop.local.md#L1-L22)：它用 not_contains 配合 `npm test|pytest|cargo test`。而当前引擎的 not_contains 是**字面字符串判断**，不会把竖线解释为三个候选命令；即便 transcript 有单独的 pytest，也仍可能命中“不包含整串字符”的阻止条件。该示例默认 disabled，所以不是所有安装者都会受影响。即使改好匹配，它也只能查文本是否出现，不能证明测试真正执行、通过或覆盖了本轮修改。这是静态核到的契约问题，未做宿主实测。

同样，简单 file pattern 被转换为 new_text，而 [Write/Edit 字段分支](https://github.com/anthropics/claude-plugins-official/blob/ea10b213686c90bb1984b2016937310e05336cf3/plugins/hookify/core/rule_engine.py#L235-L244)的 new_text 读取 new_string；Write 的完整正文在 content。复用默认例子前应按真实工具 payload 测试，不能只用一个 Edit 的成功样本代表所有写文件工具。四个入口的错误都偏向不中断会话，安全敏感门禁需另有经过验证的执行层。

### ⑤ 近期活动与热度：事实、推断分开

**事实：**今日 +1,397，main 没变；最新七条提交仍都是外部插件 SHA 指针升级，最近一条为 [incident-io 指针更新](https://github.com/anthropics/claude-plugins-official/commit/ea10b213686c90bb1984b2016937310e05336cf3)。新鲜信息来自问题讨论：Hookify [#6306](https://github.com/anthropics/claude-plugins-official/issues/6306)与 [#6092](https://github.com/anthropics/claude-plugins-official/issues/6092)在今日 01:49–01:51 UTC 继续更新；security-guidance 的资源限制提案 [#6759](https://github.com/anthropics/claude-plugins-official/pull/6759)今日创建后已关闭，但 API 明确 merged=false，不能写成主干已经修复。该提案中的内存测量也是作者报告，而非本次验证。仓库未启用 Discussions。

**推断：**插件分发与低门槛工作流规则可能支撑持续关注，但没有公开传播链或归因证据证明它们导致今天的涨星。**暂无足够公开证据解释今日热度**，不能将旧提交或未合并提案当作今日爆发原因。

### ⑥ 对你的工程栈的价值

对 **AI Agents/coding agents**，今天最有价值的阅读题是：规则缺失、损坏、未命中与明确放行，是否被系统区分？对 **MCP**，目录配置不等于远端服务实现或授权边界；Hookify 当前的 Bash/Edit/Write 字段适配也不能直接套给任意 MCP schema。对 **RAG**，这里没有检索引擎，读取 transcript 只是取原始文本匹配。对 **React/Next/Node 与 Python/Django**，可以复用规则编辑器和事件适配层，但要做编码、工具字段、规则解析、阻断时机、测试结果证据等契约测试；不要只把提示文案改成“必须”就认为门禁建立了。

**今日实际阅读边界：**根 README、marketplace 结构及统计、完整树；Hookify README、manifest、hook 注册、四个入口、config_loader 与 rule_engine 全文、require-tests-stop 示例；最近 12 个 commits、release 空列表、按更新时间排序的 25 条 issue/PR，以及 #6306 评论和 #6759 PR 元数据/正文。没有安装或执行 Hookify，没有逐仓审计 262 个外部 source，没有将昨日 security-guidance 深读冒称为今天新读。

## 2. MadsLorentzen/ai-job-search

### ① 元数据与阅读锚点

- 当日榜单：第 2；Python；50,512 stars；今日 +1,365
- 默认分支 `master`，本次源码锚定 `5d9e0977f01465166f25abf0826bd61e7c8cac25`；[MIT](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/LICENSE)；仓库创建于 2026-03-18
- 最近发布版为 [v1.7.2（2026-09-29）](https://github.com/MadsLorentzen/ai-job-search/releases/tag/v1.7.2)，10 月 17 日仍在持续合并修复；默认分支已经包含发布后修改，以下不把它们混称为 v1.7.2 已发布功能
- 实际阅读：[README](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/README.md)、[目录树](https://github.com/MadsLorentzen/ai-job-search/tree/5d9e0977f01465166f25abf0826bd61e7c8cac25)、`/apply` 和 `/rank` 命令、求职评估/抓取技能、Jobnet CLI、Python 去重/状态/PDF/安全检查脚本、相关测试，以及 commits/releases/issues

### ② 它解决的具体问题

求职的重复劳动不只是“写一封求职信”：候选人资料散落在原始 CV、证书、过去申请中；岗位来自不同门户；同一岗位会重复出现；为不同岗位写的材料容易慢慢偏离真实履历；成功生成 PDF 又不代表 ATS 能读到关键字、日期和完整经历。这个项目把这些步骤组织成可以反复运行、保留状态和证据的本地工作流。

技术定位尤其需要说准：虽然 GitHub 主语言是 Python，它的主入口实际上是 `.claude/commands/*.md` 和技能文件，由 Claude Code 执行编排；Bun/TypeScript CLI 负责获取门户数据，Python 负责确定性校验和状态处理，LaTeX 负责最终交付。它没有自己的 Django/FastAPI 服务，也不是新训练的“求职模型”。[入口与工作流](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/.claude/commands/apply.md#L21-L129)

### ③ 真实架构、数据流与关键实现

数据流是：`/setup` 整理候选人事实与写作偏好 → `/scrape` 调用不同门户 CLI，保存 `job_scraper/seen_jobs.json` → `/rank` 从状态文件选出少量待评分岗位，agent 读取岗位并给出结构化分数/缺口 → Python 验证并回写 → `/apply` 按岗位生成 CV/求职信 → 独立 reviewer 调研公司、核验事实、给出修改 → 编译 PDF 并机械校验 → CSV 记录申请、归档当次实际读取的岗位文本。这里的“apply”核心交付是申请材料及 `drafted` 记录，不能直接理解成已经向雇主完成投递。[申请流程和记录逻辑](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/.claude/commands/apply.md#L233-L416)

1. **把昂贵、易出错的状态搬运从模型移到小程序。** `rank_state.py` 不联网、不判断匹配，只实现 `candidates`、`sweep`、`apply`。默认每次最多选 10 个 `new`/`unreachable` 岗位，排除已经在 tracker 中的 company+role，只把 title/company/url/deadline 等必要字段交给模型；历史 JSON 不必每次全部进入上下文。回写使用同目录临时文件加 `os.replace`，避免半写文件。分数由代码验证范围并计算 technical 30%、experience 25%、behavioral 15%、career 30%，location/eligibility/language 等另作 veto。更重要的是，抓取失败先记 `unreachable`，累计至少 3 次且首末间隔至少 48 小时才放弃，避免把一次门户故障误判为招聘结束；已有截止日期确实过期时则直接退出候选。相关边界有独立测试。[状态实现](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/tools/rank_state.py#L51-L100) · [筛选与回写](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/tools/rank_state.py#L171-L379) · [失败重试测试](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/tests/test_rank_state.py#L616-L744)

2. **门户层有代码契约，不全靠网页让模型猜。** 以 Jobnet 为例，入口用 Bunli/Zod 描述参数；搜索把用户 flags 映射为 `/bff` 查询参数，将门户原始字段映射为共同的 `id/title/company/location/date/url` 契约，并保留外部雇主申请地址。外部 URL 必须是绝对 HTTP(S) 才接受，否则保留 Jobnet 自己的唯一地址，避免破坏去重。HTTP helper 每次请求有 15 秒超时，429/5xx 最多重试 6 次，500ms 起步、封顶 5 秒并加 jitter。跨站去重另有 `job_key.py`：ASCII slug 遇到非拉丁名字、超长标题时追加稳定摘要，避免中文/西里尔文字被归一化成空串后互相覆盖。这些都是垂直 agent 能否长期使用的基础工程。[CLI 依赖](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/.agents/skills/jobnet-search/cli/package.json) · [参数与输出归一化](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/.agents/skills/jobnet-search/cli/src/commands/search.ts#L65-L145) · [重试实现](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/.agents/skills/jobnet-search/cli/src/helpers.ts#L1-L40) · [稳定 key](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/tools/job_key.py#L58-L155)

3. **交付验收针对真正的文档失败，而非“模型说已检查”。** reviewer 在独立上下文中拿到草稿，输出可应用的 `old_string/new_string` 编辑和叙述性意见；drafter 仍需再次核实公司事实。最后用 `verify_pdf.py` 优先 pypdf、失败时回退 pdftotext，检查页数和文本层；`--contains` 做排版字符归一化，但 `--ascii-dates` 故意读原始文本，以免把 ATS 可能丢弃的 en-dash 日期问题隐藏掉。`verify_layout.py` 使用 Poppler 单词 bounding boxes 检测大于 100pt 的空洞、过量底部留白、页脚碰撞和跨页孤立标题。缺少正确的 Poppler 时返回退出码 2 / skipped，不能解释成“布局通过”。[reviewer 与修订](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/.claude/commands/apply.md#L129-L231) · [文本提取实现](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/tools/verify_pdf.py#L147-L266) · [版面检查](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/tools/verify_layout.py#L186-L382)

### ④ 亮点与边界

亮点是“判断交给模型，状态与验收交给代码”划分得比较清楚；事实来源明确，生成过的 tailored CV 只能借鉴表达，不能反过来污染候选人事实库；真实岗位原文、输出文件和 tracker 形成可追溯链。这比单个求职 prompt 更接近可维护的垂直 agent 产品。

边界也明确：核心编排仍是自然语言指令，不是强制执行的工作流引擎或安全沙箱；岗位 prompt injection 的防护主要依赖指令和窄化权限。CI 的 `security_guards.py` 会检查预授权命令 allowlist、个人资料 gitignore 与 npm/Bun install-time scripts，但这不是运行时隔离。个人资料有一部分会进入已经 tracked 的模板文件，不能以为 `.gitignore` 能保护一切；README 已明确建议实际求职使用 private repository，而非把个人履历推到公开 fork。[安全检查源码](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/tools/security_guards.py#L1-L115) · [隐私警告](https://github.com/MadsLorentzen/ai-job-search/blob/5d9e0977f01465166f25abf0826bd61e7c8cac25/README.md#L80-L96)

门户适配主要面向丹麦，迁移到别的市场需要真正重做 API/字段/访问限制适配。LaTeX、Bun、Python 和 agent 订阅/API 也构成实际门槛。截止研究时，公开 [issue #622](https://github.com/MadsLorentzen/ai-job-search/issues/622) 报告 Freehire detail 接受别的网站 `/jobs/` URL 后误取 slug，修复 PR 尚开放；[issue #616](https://github.com/MadsLorentzen/ai-job-search/issues/616) 报告文档中的 region 参数导致无声空结果。这些不是“全项目不可用”，但说明连接器契约仍需逐站验证。

### ⑤ 为什么热：事实与推断分开

事实：今日 +1,365 stars；v1.7.2 专门强化了 PDF 布局、ATS 文本层、门户 URL 校验和 Unicode；最新 [10 月 17 日提交](https://github.com/MadsLorentzen/ai-job-search/commit/5d9e0977f01465166f25abf0826bd61e7c8cac25) 修复薪资工作簿解析，同日还修复抓取状态路径与失败重试。README 中作者自述 69 份定制申请、20 次初面、1 份签约，是作者个人经验，未经本次独立验证，也不能当作用户普遍转化率。

推断：它把大众容易理解的求职痛点与“可以自己持有文件、看见 PDF 成品”的 agent 流程结合，传播门槛低；近期修复又集中在用户真实会踩的坑，可能帮助口碑扩散。但未找到足以证明“今天增长由某次发布/媒体/社交传播触发”的来源，不建立因果。

### ⑥ 对你的技术方向有什么价值

- **AI agent / coding agents：高。** 重点读 `/apply` 的事实审计与 drafter-reviewer，以及 `/rank` 的结构化输入输出。适合借鉴到招标、客户提案、报告生成等“非代码成果也需验收”的 agent
- **RAG：中。** 值得学的是原始资料、派生草稿、证据归档和上下文预算的分层；它本身没有 embedding/向量库检索管线，不能直接当通用 RAG 底座
- **MCP：局部。** Notion/Gmail 同步说明它能消费外部连接器；核心门户实现是 CLI，不是一个通用 MCP server
- **Node / Python：高。** TypeScript adapter + Python deterministic worker 的分工非常实用；Python/Django 项目可迁移状态机和文档校验思想，但这里没有 Django ORM/服务层可复用
- **React/Next.js：低直接复用。** 没有 React 应用主架构；更适合作为“前端按钮背后的垂直 agent 流程”设计样本

## 3. affaan-m/ECC

### ① 排名、元数据与源码增量

官方今日第 **3**；[仓库](https://github.com/affaan-m/ECC)；**282,556 stars，+1,145 stars today，JavaScript，MIT**。main 仍为 **76aaa77df6adc5b889e689007bf99b9a4f74af34**，提交于 **2026-10-15 19:17 UTC**；**与昨日同一 SHA，没有源码 diff**。今日完整递归树仍为 6,355 条目、4,621 文件、未截断。[根 package.json](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/package.json)为 ecc-universal **2.2.3**、Node ≥18，运行依赖仍是 TOML、AJV、YAML 与 sql.js；[最新 v2.2.3](https://github.com/affaan-m/ECC/releases/tag/v2.2.3)仍发布于 **10 月 1 日 23:00 UTC**，没有今日新发行。

### ② 它解决什么问题

ECC 把规划、实现、测试、审查、记忆与重复工作流程包装为可选择的 rules、skills、agents、hooks 和多宿主适配。今天不重复昨日安装授权与 Memory Vault，改读 **continuous-learning-v2 从工具事件到“instinct”，再到技能文件的链条**。这是面向 coding agents 的工程经验再利用，不是更新模型参数的训练系统，也不是保证习惯正确的自动学习器。[README](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/README.md#L130-L157)、[技能定位与工作流](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/SKILL.md#L1-L137)

### ③ 架构、入口与三个实际机制

**入口分层。** npm 的 ecc 进入 [scripts/ecc.js](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/ecc.js#L211-L350)，按固定命令映射启动 Node 子脚本；技能文档本身不会自动变成常驻服务。观察路径则由 [hooks.json](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/hooks/hooks.json)和 [PostToolUse dispatcher](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/hooks/posttooluse-dispatcher.js#L1-L68)接线，standard/strict profile 包含观察任务，经 [observe-runner.js](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/scripts/hooks/observe-runner.js#L95-L165)传给 Bash/Python 组合脚本。**采集与后台分析是两个开关层次**：[config.json](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/config.json)的 observer.enabled 默认 false，只表示后台分析默认不开，不能推断启用相应 hooks 后也不会记录工具数据。

1. **从工具事件形成有项目范围的日志。** [observe.sh](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/hooks/observe.sh#L128-L363)先跳过 disabled/minimal、显式 skip、子代理及已知自动会话路径，防止观察自己的观察器；随后确定项目目录，pre 记 tool_start/input，post 记 tool_complete/output，单个输入/输出截到 5,000 字符，写 observations.jsonl。[项目识别](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/scripts/detect-project.sh#L93-L246)优先识别 Git 根、归一化远端或路径，以 SHA-256 前 12 位作为项目 ID，远端 URL 先去掉内嵌凭据。这个 hash 是组织目录用的标签，不是多用户权限隔离。日志脱敏在持久化前执行，但只覆盖有限关键词模式；“记在本机”不等于“没有存敏感内容”。
2. **后台分析成功要有本轮完成记录，不能只看 exit 0。** [observer-loop](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/agents/observer-loop.sh#L198-L315)默认只抽最后 500 行日志，给模型说明按重复模式写 instinct，次数到 confidence 的映射来自提示词而非统计校准。调用默认 haiku、有限 max-turns、120 秒 watchdog，并跳过自身采集。尤其值得学的是 [结果文件与归档](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/agents/observer-loop.sh#L357-L470)：先打开临时结果文件的描述符再 unlink 路径，防止别的进程替换路径伪造结果；同时要求进程成功且 stdout 最后一个非空行恰好只有一次精确完成 JSON，才归档原观察文件。失败则保留待重试。这是进程/输出契约，**仍不能证明模型确实写了正确知识**。相关测试用 stub CLI 模拟各种完成/失败情况，不是对真实模型学习质量的评测。[归档回归测试](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/tests/hooks/observer-loop-archive.test.js)
3. **“进化”为技能的最后一步其实是词法聚类与模板生成。** [instinct-cli.py](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/scripts/instinct-cli.py#L1149-L1422)把 trigger 切成 ASCII 字母/数字词，去掉英文停用词，以共有词数÷较小集合大小的 overlap coefficient ≥0.5、至少 2 个共有词，贪心加入 cluster；加入后保留共同词交集。至少两个 instinct 成为技能候选，workflow 且 confidence≥0.7 成为命令候选，至少三个且均值≥0.75 成为 agent 候选。只有 --generate 才进入 [模板写文件](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/scripts/instinct-cli.py#L1938-L2058)：提取既有 Action、生成 frontmatter，并处理本批次重名。这里没有 embedding、向量库或模型训练；纯中文 trigger 通常不能产生足够关键词，因此多语言“自动学会工作流”的效果不能由英文示例外推。

### ④ 亮点与边界

值得学习的是 **采集、分析完成、产物发布分别留下可检查状态**，还有防自循环、采样、进程组清理与失败保留。一个任务完成标志放在当前 stdout、而不是靠旧日志找关键词，能减少错误归档。但采样尾部后代码移动的是整个 observations 文件；较早的非采样记录、乃至分析期间新到的记录是否再次进入学习，需要额外的队列/偏移设计。它不是每一条观察恰好处理一次的消息队列；这里指出的是静态数据流边界，没有运行并发场景。

当前还存在直接关系隐私的缺口：[脱敏正则](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/skills/continuous-learning-v2/hooks/observe.sh#L339-L363)需要 api-key/token/secret/password 等词紧接限定分隔符，未内置通用 PEM、裸 token 或 DSN 密码识别。[PR #3568](https://github.com/affaan-m/ECC/pull/3568)拟补 compound key、云访问标识、DSN 和私钥形状，当前仍 **open、merged=false**。本次核到的是当前规则的覆盖边界与拟修复内容；PR 里 25 项通过、16 项此前失败等是提交者测量，不能当作本次测试结果。[现有脱敏测试](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/tests/hooks/observe-secret-redaction.test.js)只覆盖四类合成凭据文本的 pre/post 路径，并在原生 Windows 跳过 shell fixture。

另外，后台模型命令只传 --allowedTools Read,Write，本次看到的调用没有额外的 OS 文件隔离；不要将“允许工具列表”直接等同于“只能写指定 instinct 目录”的安全保证。启用后台分析还意味着日志样本会交给配置的 Claude 模型处理，需按数据敏感性选择采集范围。

### ⑤ 近期活动与热度：事实、推断分开

**事实：**main 最近仍是 [PR burst protection 合并](https://github.com/affaan-m/ECC/commit/76aaa77df6adc5b889e689007bf99b9a4f74af34)，release 仍是命名与发布可靠性更新。社区新报告 [#3625](https://github.com/affaan-m/ECC/issues/3625)和 [#3626](https://github.com/affaan-m/ECC/issues/3626)分别在今日 **00:29、01:48 UTC** 创建，继续指出 OpenCode 2.x 插件形态不兼容。当前 [ecc-hooks.ts](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/.opencode/plugins/ecc-hooks.ts#L151-L158)确实定义 async 函数，[结尾](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/.opencode/plugins/ecc-hooks.ts#L811)将其 default export，源码形态已核；具体 OpenCode 报错、平台复现与 npm 发布包行为来自报告者，本次没有安装验证。

#3626 还报告运行时依赖缺失，但应区分清单：当前根包把 @opencode-ai/plugin 放 devDependencies，专用 [.opencode/package.json](https://github.com/affaan-m/ECC/blob/76aaa77df6adc5b889e689007bf99b9a4f74af34/.opencode/package.json)又另有 peerDependencies。不能仅凭一个清单就断言所有安装渠道都会缺包。把源码与实际安装产物/宿主版本一起锁定，才有可靠兼容性结论。

**推断：**多宿主流程复用、减少重复提示与持续知识沉淀可能支撑关注；上述问题只证明近期使用和维护需求，不能解释当天 +1,145 的来源。**暂无足够公开证据解释今日热度。**

### ⑥ 对你的工程栈的价值

对 **AI Agents/coding agents**，可借鉴“本轮输出完成契约”和失败不丢输入，审查 confidence 的来源而非把 0.85 当正确率。对 **RAG/MCP**，观察日志与生成技能不自动构成安全记忆服务；若封装成工具，应限制项目范围、提供来源和删除/保留策略。对 **React/Next**，可以做观察内容预览、原始证据与 instinct 差异审核；对 **Node/Python/Django**，可学事件接线与后台 worker，但敏感日志最好在采集边界就最小化，再做脱敏。按本次新增证据，接 OpenCode 2.x 前先验证入口加载，而不是假定“hooks 已装”就是“保护已生效”。

**今日实际阅读边界：**根 README 定位/安装段、package、完整树、ecc.js 派发；continuous-learning 的 SKILL/配置、observe 主采集/脱敏/启动/信号路径、project detection 关键段、observer-loop 全文、start-observer 配置与启动段；instinct-cli 聚类/候选/生成段；hook 注册、Node wrapper/dispatcher 接线；OpenCode 清单、exports 与函数入口；现有脱敏测试全文、归档测试主要 mock/断言段；最近 12 commits、5 releases、25 条更新中的 issue/PR、#3568 PR 正文。未安装、未运行仓库代码或测试，未审计其余数百个 skills，未重新穷尽 Discussions。

## 4. HKUDS/CLI-Anything

### ① 排名、元数据与版本锚点

官方第 **4**；[HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything)；**54,091 stars，+574 stars today，Python**。main 固定 **34f519533bc175d2fe287ab8316b0dd99bb9cc43**，最后提交于 **2026-09-22 02:01:28 UTC**，与昨天实际报告一致；完整递归树 **2,582 条目、1,872 文件，未截断**。最新仓库 [release v0.4.0](https://github.com/HKUDS/CLI-Anything/releases/tag/v0.4.0)发布于 **6 月 25 日**，而 [Hub setup.py](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/cli-hub/setup.py)为 **0.4.1**，不能混称今天发布的新版本。根许可证是 Apache-2.0，但 Hub、Krita 包元数据仍写 MIT；采用具体组件时应核对该不一致。

### ② 解决什么问题，适合谁

它把现有应用的 API、工程文件和脚本接口包装成有帮助文档、JSON 输出及 REPL 的 CLI，让 agent 少依赖脆弱的鼠标流程。使用者可以通过 Hub 找现成 harness；开发者则让编码 agent 按方法生成新适配。它替代的是重复编写应用连接层，不会替代 Krita、FreeCAD、QGIS 本身，也不保证任意 GUI 都能自动、完整地被控制。[README 的两类入口与前置条件](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/README.md#L181-L258)

昨天已读 Hub 发现／安装与 GIMP fallback；今天主干未变，换读**“命令完成、文件生成、结果正确”如何跨层传递**，结合新 issue 检查 Krita 与 FreeCAD 的真实导出链。这是阅读增量，不是新增功能。

### ③ 架构、入口与真实数据流

**多包结构。** 根目录包含各应用的 `agent-harness/`、宿主插件／技能、registry 和 CLI-Hub。Krita 与 FreeCAD 都是独立 **1.0.0** Python 包，要求 Python ≥3.10，依赖 Click、prompt-toolkit；console entry 分别指向各自 `*_cli:main`，真实应用仍须另装。[Krita setup](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/krita/agent-harness/setup.py)、[FreeCAD setup](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/setup.py)

**机制一：Krita 把 JSON 转成中间工程，再启动应用，但错误结果在中间层丢失。**

1. [CLI `export render`](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/krita/agent-harness/cli_anything/krita/krita_cli.py#L397-L408)加载项目 JSON，调用 `export_image`，将返回字典输出。异常处理器会把真正抛出的异常转成错误和非零退出；不会自行解读任意结果字典中的失败字段
2. [`build_kra_from_project`](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/krita/agent-harness/cli_anything/krita/core/export.py#L169-L323)写 ZIP，包含 mimetype、XML 和每个 paint layer 的透明 PNG；它跳过其他图层类型，不在这条生成路径执行 filters。更具体的契约差异是 [create_project](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/krita/agent-harness/cli_anything/krita/core/project.py#L113-L144)把尺寸放在 `canvas`，而这里从 `image` 取尺寸、找不到便回默认值。这些是代码直接可见的序列化边界，不能把“ZIP 文件生成”当作原始项目语义已经保留
3. [`krita_backend.export_file`](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/krita/agent-harness/cli_anything/krita/utils/krita_backend.py#L100-L142)通过 argv 启动 Krita，记录 `ok/returncode/stdout/stderr`；[调用末尾](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/krita/agent-harness/cli_anything/krita/utils/krita_backend.py#L174-L215)还记录 `output_exists`。但 [core `export_image`](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/krita/agent-harness/cli_anything/krita/core/export.py#L370-L411)直接丢弃返回值，输出不存在时仍返回 `file_size:0` 和 `method:krita_backend`。普通非零退出和超时被 backend 包成结果而非抛出，就可能走到正常 CLI 输出

因此 [issue #582](https://github.com/HKUDS/CLI-Anything/issues/582)所述 Krita 5.2.2 拒绝临时 `.kra`、随后显示 0 字节结果，是**用户报告**；本次已静态确认的是“后端有失败信息，但上层没有执行失败判定”。没有运行 Krita，不能把其具体格式错误归因或所有版本兼容性写成实测结论。

**机制二：FreeCAD 的项目状态与宏输入不一致，文件检查仍可能放过错误几何。**

1. [CLI `part boolean`](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/freecad_cli.py#L427-L441)先记 undo 快照，再调用 [parts.boolean_op](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/core/parts.py#L465-L537)。后者把两个操作数标为不可见，在 `parts[]` 添加 `type:cut/fuse/common`、引用 `base_id/tool_id` 的结果对象。此时完成的是 JSON 状态编辑，尚未计算 CAD 几何
2. 导出时 [generate_macro](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/utils/freecad_macro_gen.py#L577-L629)依次生成 primitives、booleans、bodies、placements、export。然而 [_gen_parts](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/utils/freecad_macro_gen.py#L145-L212)仅支持基本体及有限镜像，遇 `cut` 只写 WARNING 注释；`_gen_boolean_ops` 又读另一个 `boolean_ops[]`，以 base/tool 名称关联。`part boolean` 没写这个列表，操作就没有进入宏。[_gen_export](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/utils/freecad_macro_gen.py#L517-L569)遍历所有有有效 Shape 的对象，没有按项目 `visible` 或最终依赖关系筛选，源实体仍可能进入导出
3. FreeCAD 后端比上述 Krita 路径有更强的失败判定：[`export_headless`](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/utils/freecad_backend.py#L312-L369)拒绝非零退出与缺文件；[core export](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/core/export.py#L253-L347)再做格式检查。但 STEP 验证主要查文件头，STL 验证查开头或计数字段存在；它们不验证“导出的实体就是用户要求的差集”。进程、文件、格式通过，几何仍可错

[issue #581](https://github.com/HKUDS/CLI-Anything/issues/581)报告 FreeCAD 1.1.4 导出源实体而非切割结果。上述 schema 分裂和导出选择逻辑已从 main 确认；issue 中实际体积仍是报告者的数据，本次没有复现。

### ④ 实质亮点、测试与边界

这套拆分的价值是**状态编辑、应用执行、结果检查可以分别审计**，CLI 参数与返回 JSON 也便于 agent 编排。它的边界同样明确：通用生成规范和统一命令风格，不能自动保证所有 harness 的错误语义、序列化和验收一致。

测试应看断言覆盖哪一层。Krita 的 [PNG/JPEG E2E](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/krita/agent-harness/cli_anything/krita/tests/test_full_e2e.py#L90-L143)直接调用子进程，失败或缺文件时 `pytest.skip`，没有覆盖 core 丢弃失败字典的边界。FreeCAD 的[布尔工作流测试](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/tests/test_full_e2e.py#L241-L278)主要验证状态；[STEP/STL 测试](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/freecad/agent-harness/cli_anything/freecad/tests/test_full_e2e.py#L537-L639)测基本体导出及格式，并非同一条布尔结果的几何验收。以上只描述已读测试，未断言全仓没有其他覆盖。

另一个兼容性信号是 [#583](https://github.com/HKUDS/CLI-Anything/issues/583)：用户报告 QGIS 3.34.4 创建字段失败，而 processing 可用。当前 [字段解析](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/QGIS/agent-harness/cli_anything/qgis/core/layers.py#L30-L69)取得 `QMetaType.Type` 并[传给 QgsField](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/QGIS/agent-harness/cli_anything/qgis/core/layers.py#L157-L222)；[README](https://github.com/HKUDS/CLI-Anything/blob/34f519533bc175d2fe287ab8316b0dd99bb9cc43/QGIS/agent-harness/cli_anything/qgis/README.md#L16-L46)只要求 QGIS/PyQGIS 可用，未列最低 QGIS 版本。可以确认调用形态及版本约束缺口，不能由此宣布某版本一定修复。PyQGIS 编辑与 `qgis_process` 执行本来就是不同路径，一条可用不证明另一条兼容。

### ⑤ 近期活动与热度：事实和推断分开

**事实：**今日仍第 4，stars today 从昨日 +281 变为 +574；main 仍停在 9 月的 README 调整。#581、#582、#583 均发表于 **10 月 18 日 00:42–00:43 UTC**，快照中均 open、无评论。它们是新反馈，不是今天才产生缺陷的证据。

更早的 [PR #577](https://github.com/HKUDS/CLI-Anything/pull/577)于 **10 月 17 日 15:23 UTC** 提议修复 FreeCAD 同类问题：按 ID 从 `parts[]` 生成布尔对象，导出时排除被其他对象消费的中间形状，并新增 STL 体积断言。已读完整 PR diff；读取时 **open、merged:false**，head 为 **478bbec401aa5ac07568444a419cc89de8503df2**。作者声称实测通过不能算本次验证，修复提案也不能当成 main 已具备的保障。

**推断：**把成熟桌面软件变成 agent 工具仍有明显吸引力；这组反馈也说明真正难点往往在应用语义和版本合同，而非命令数量。但没有公开传播链足以将这些问题或 PR 与今日涨星建立因果，**暂无足够公开证据解释今日热度**。Discussions 已启用，本次未取得新的完整讨论样本，不能以没有引用推断没有讨论。

### ⑥ 对你的工程价值

对 **AI Agent/MCP**，应把状态修改成功、后端执行成功、产物存在、语义验收分别返回，并确保失败不会在包装层被吞；`method` 字段只说明选了哪个执行路径。对 **RAG**，技能和命令说明可作为能力检索材料，但检索到一个命令不等于其依赖和输出合同已验证。

对 **React/Next/Node**，前端可展示这几级状态与产物证据，系统应用应放在受限 worker；对 **Python/Django**，最可复用的是 Click→core→backend 的边界设计，最该补的是跨边界契约测试：同一项目从参数写入、宏生成到导出后重读验收。CAD 用实体数量／体积，图像用尺寸／像素／图层语义；只测退出码和 magic bytes 不够。

**本次实际阅读范围：**根 README 的定位、安装、前置条件与生成流程；根许可证、Hub/Krita/FreeCAD setup；Krita CLI 1–145、390–445，project 1–144，export 1–411，backend 1–270，Session 全文，core 测试 272–330、E2E 1–235；FreeCAD CLI 1–313、427–441及导出入口，parts 465–537，Session 全文，macro_gen 1–212、441–629，core export 118–380，backend export_headless，E2E 241–278、537–639、883–926及相关测试索引；QGIS README 前置／运行模型、layers 1–222、backend 1–235；递归树与最近 15 条提交／15 条 issue-PR 列表、3 个 release 元数据；#581–583 完整正文、#577 完整详情与 diff。下载文件不等于全文逐行审计，未审计所有 harness、全部 CAD 特征及预览／动画实现。全程未安装依赖、运行仓库代码或执行测试。

## 5. K-Dense-AI/scientific-agent-skills

### ① 排名、元数据与源码增量

官方今日第 **5**；[仓库](https://github.com/K-Dense-AI/scientific-agent-skills)；**52,281 stars，+878 stars today，Python，MIT**。main 仍为 **a1043ef544e3a100c28e70a736b6cf32554d0677**，最新提交 **2026-10-12 09:43:29 UTC** 更新安全扫描报告；**与昨日固定 SHA 完全一致，无主干代码变更**。今日完整树仍为 3,497 条目、2,780 文件，未截断，实际计数 **177 个 SKILL.md**。[plugin.json](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/plugin.json)和 [pyproject.toml](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/pyproject.toml)均为 **2.72.0**；[最新 release](https://github.com/K-Dense-AI/scientific-agent-skills/releases/tag/v2.72.0)仍是 **10 月 1 日 22:42 UTC**，不是今天发布。

### ② 它解决什么问题

它把科学库、数据源、分析约定和校验步骤包装成 Agent 可加载的技能资料，部分技能附带真正执行计算的 Python CLI。对象包括研究人员和研究工具开发者；替代方式是自行查原始文档、写分析脚本、维护验证案例。今天从昨日的 Autoskill 换到 **科研 CLI 的结果契约与数值正确性**：自然语言技能有明确边界，仍需检查其脚本在尺度变化、阈值相等和退化数据上的行为。[README 的组成、版本与验证说明](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/README.md#L79-L104)

### ③ 架构、入口与三个真实机制

**组织层。** 每项 skill 由 SKILL.md、references、scripts、可选 templates/assets 构成；有 scripts 的技能对应 tests 子目录和依赖条目。根 Python ≥3.13 是仓库工具环境；本次 PK/PD skill 声明 Python ≥3.12、NumPy/SciPy，而 analytical-method-validation 声明 Python ≥3.11、仅标准库。后者甚至在 `_common.py` 中自行实现分布函数，不能把“无依赖”理解为没有统计实现需要核验。[PK/PD 兼容与范围](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/pkpd-modeling/SKILL.md#L1-L48)、[分析验证范围](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/analytical-method-validation/SKILL.md#L1-L46)

1. **数值结果与发现分离，形成 Agent 能读取的执行合同。** [exposure_response.py CLI](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/pkpd-modeling/scripts/exposure_response.py#L236-L349)要求在 Emax/logistic/C-QTc/quartiles 中恰选一个模式，读取表格、核必需列、拒绝非有限数和负 exposure；交对应计算函数后，把结果装入 [Report](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/pkpd-modeling/scripts/_common.py#L197-L334)。JSON 同时含 scalars、tables、findings、notes，不可用数值转 null；表格/TSV 则把诊断送 stderr。退出码 0 表示本次没有产生 finding，1 表示有 finding，2 表示输入不可用。这个合同便于接工具，但 **0 不是科研结论有效、临床安全或所有适用性检查通过的证明**。
2. **Logistic 有输入防线，也暴露优化器与统计误差的耦合。** [fit_logistic](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/pkpd-modeling/scripts/exposure_response.py#L118-L156)拒绝非 0/1 响应、单一结果、固定 exposure，以及一维完全/准完全分离；负对数似然使用 logaddexp 避免 exp 溢出。但随后直接在原始 exposure 上以 BFGS 优化，并从 result.hess_inv 取近似协方差计算 SE。新 [issue #330](https://github.com/K-Dense-AI/scientific-agent-skills/issues/330)报告仅改变 exposure 尺度，就出现收敛标志为否、SE 偏差；本次静态确认了原尺度/BFGS/hess_inv 路径，没有运行报告里的数据。对应 [PR #331](https://github.com/K-Dense-AI/scientific-agent-skills/pull/331)提议中心化/缩放后的 IRLS 与 Fisher 信息协方差，读取时仍 open、未合并。不能把该方案描述成当前实现。
3. **验证规则不是只有一个总阈值，统计组件也必须保持一致。** [check_bioanalytical_run](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/analytical-method-validation/scripts/check_bioanalytical_run.py#L70-L186)要求显式选 modality，分别处理 calibrator、QC、按浓度分组的通过比例及边界标签，缺少 QC/校准样品会产生 incomplete finding；[ISR 与 total error](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/analytical-method-validation/scripts/check_bioanalytical_run.py#L189-L248)走独立输入与计算路径。另一方面，[one_way_components](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/analytical-method-validation/scripts/_common.py#L476-L567)将负的组间方差估计截为零，再构造 repeatability/intermediate SD；[accuracy/precision CLI](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/analytical-method-validation/scripts/check_accuracy_precision.py#L183-L243)为二者分别算区间。新 #328 的价值就在于追到这两条内部数据流，而不止检查输出文件存在。

### ④ 亮点与边界：今天新报告具体暴露了什么

项目可取之处是把输入、模型假设、不可识别、外推和失败发现写进产物，而不是只吐一个估计值；测试也区分数值函数、CLI 退出状态与 JSON 合同。但今天新增的 [#328](https://github.com/K-Dense-AI/scientific-agent-skills/issues/328)揭示了两个容易被“测试很多”掩盖的边界：

- **阈值相等仍可能被二进制浮点推到阈值外。** 当前 calibrator、QC、ISR、total error 的源码直接做 abs(value)≤limit，没有比较容差。报告举例 nominal=3、measured=3.45 算出的偏差为 15.000000000000005，导致界限 15 的判断失败。当前公式和直接比较已核；其整批样本通过率与 CLI 输出来自报告者，不是本次复现。若拿格式化后同为 15.0000 的显示值代替内部值解释判断，会错过根因
- **截断方差后，自由度公式没有同步切换。** 当前 `var_between=max(0, ...)`，但 satterthwaite_df 仍把未截断的 MS_between、MS_within 组合放进分母。报告用两个各含两次测量的组，得到 total SD 与 within SD 相同、自由度却为 8 而非 within 的 2。源码确实存在这条不一致路径；对应 [PR #329](https://github.com/K-Dense-AI/scientific-agent-skills/pull/329)拟在截断情形回到 df_within，并补浮点边界测试，仍 open、未合入

现有 [logistic 测试](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/tests/pkpd-modeling/test_scripts.py#L608-L659)检查方向和大致中点，另有分离拒绝测试，但这不等于已验证单位缩放不变性和 Fisher SE；现有 [方差测试](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/tests/analytical-method-validation/test_scripts.py#L263-L303)验证截断后 SD 相等，没有在该用例里断言有效自由度。**测试存在、测试通过、覆盖关键科学不变量是不同证据。** PR 作者提出的红绿结果本次未执行。

此外，[CI](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/.github/workflows/skill-tests.yml)跑结构合同和标准库-only 套件，并未在每次 PR 上跑全体重科学依赖。[依赖清单](https://github.com/K-Dense-AI/scientific-agent-skills/blob/a1043ef544e3a100c28e70a736b6cf32554d0677/tests/skill-requirements.toml)中 PK/PD 测试钉 NumPy 2.5.3/SciPy 1.18.1，分析验证为空依赖；两者在默认 CI 的执行范围不同。仓库扫描报告也属于另一类安全证据，不能代替数值验证或临床验证。本节只评价软件实现，不提供研究对象的剂量、诊疗或合规结论。

### ⑤ 近期活动与热度：事实、推断分开

**事实：**今日 +878；main 最近两次提交仍为 10 月 12/5 日的扫描报告更新，最新正式版仍是移除另有许可证的四个文档技能及增加图示指南。真正新鲜的是 **10 月 17 日 09:31–09:42 UTC** 创建的 #328/#329、#330/#331，两项修复 PR 均未合并。另有当日 19:57 UTC 提交的 [#332](https://github.com/K-Dense-AI/scientific-agent-skills/pull/332)，提议给 research-lookup 增加可选免 key 搜索/抓取后端；当前 open，本次只读提案正文，**没有把它写成主干已经支持的 MCP 能力**。仓库未启用 Discussions。

**推断：**将科学方法、API 与可执行辅助脚本放进同一技能入口，可能持续吸引研究型 Agent 用户；新问题反映真实使用反馈，却没有证据证明它们驱动当天涨星。**暂无足够公开证据解释今日热度。**

### ⑥ 对你的工程栈的价值

对 **AI Agents/MCP**，最可复用的是自包含 JSON、输入错误与 finding 分开的状态契约，以及把“计算了什么/没检查什么”一起返回。对 **RAG**，应检索相同版本的参考材料、模型假设和验证证据，不能只召回一个 API 示例；skill 集合本身不是向量检索运行时。对 **Python/Django**，可把经过独立验证的精选 CLI 放进隔离 worker，把尺度不变性、阈值边界、退化数据和外部基准对照加入测试。对 **Node/Next/React**，前后端应保留 notes/findings/null 与来源版本，不能将 exit 0 渲染成“科学验证通过”。这一套结果语义比再加一个“科研专家”提示更有实际工程价值。

**今日实际阅读边界：**完整树、根 README 的组成/版本/安全/环境段、plugin/pyproject、测试依赖清单与 CI；两项技能的兼容/范围/相关工作流段；exposure_response.py 全文、PK/PD common 的解析/Report/退出合同段；bioanalytical checker 全文、precision 组件和 CLI 调用段；相关测试的 logistic、JSON、方差、QC/ISR、缺失输入与回归断言段；近期 12 commits、5 releases、25 条更新的 issue/PR，以及 #329/#331 PR 元数据/正文。未执行代码、测试或计算实验，没有通读 177 项，也没有将提案的改进和测量当成主干或独立实测。

## 6. akitaonrails/ai-memory

### ① 元数据与阅读锚点

- 当日榜单：第 6；Rust；9,945 stars；今日 +178
- 默认分支 `main`，本次源码锚定 `995e35d5866973c3176709261e924a67e3c76158`；[MIT](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/LICENSE)；仓库创建于 2026-05-21
- [v3.1.1](https://github.com/akitaonrails/ai-memory/releases/tag/v3.1.1) 发布于 2026-10-17 18:09 UTC；源码 workspace 版本同为 3.1.1，但 HEAD 已含发布后的 TTL 修复
- 实际阅读：[架构文档](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/docs/ARCHITECTURE.md)、[workspace/依赖](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/Cargo.toml)、CLI/serve、hooks/router、sanitizer、store reader/writer/SQL operations、wiki、consolidator、配置、TypeScript companion、评测报告和近期维护记录

### ② 它解决的具体问题

在 Claude Code、Codex、OpenCode 等 agent 之间切换，或同一项目隔几天再回来，丢失的不只是聊天上下文，还有为什么选这个方案、踩过哪个坑、哪些工作尚未完成。单一 `MEMORY.md` 容易无限增长；每轮都调用 LLM 提取事实既贵也可能改写原意；把所有历史直接扔进向量数据库又缺乏可审阅、可编辑的长期知识形态。

ai-memory 的基本单位是带版本的 Markdown wiki 页面。生命周期 hooks 捕获工作过程，SQLite 建立检索与运行状态索引，MCP 给不同 agent 统一访问入口，handoff 明确传递未完成工作。它更接近“coding agent 的可持久化上下文服务”，不能只看成向量数据库包装。[项目目的和数据流](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/docs/ARCHITECTURE.md#L7-L180)

### ③ 真实架构、数据流与关键实现

入口由 Rust CLI 加载配置并启动服务；`serve` 打开 Store、构建 Wiki、配置可选 LLM 和 embedder，再挂载 hooks/MCP/可选 HTTP API 和管理界面。底层主要是 Tokio、Axum、rmcp、rusqlite、git2；wiki 页面是人可编辑、Git 版本化的内容真源，SQLite 支撑页面 FTS、entities、links、向量及 sessions/handoffs 等运行数据。生命周期事件经隐私处理写入 observation，结束会话时先生成无 LLM 的规则摘要页和交接记录；配置 LLM 后可进一步整理成 concepts/decisions/gotchas，后续会话取有界 brief 并按需搜索。[启动组合](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-cli/src/commands/serve.rs#L1197-L1278) · [会话总结落盘](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-hooks/src/router.rs#L4235-L4335)

1. **捕获路径把隐私、背压和恢复作为一等公民。** `Sanitized<NewObservation>` 的字段是私有的，公开构造过程先 scrub，再截断 title/body；body 上限 16KiB。顺序很重要：先截断可能留下半个 token，使正则匹配失败。写入经容量 1,024 的 Tokio mpsc 发往专用 `ai-memory-writer` OS 线程，而不是每个 async handler 各自抢 SQLite 写锁。原生 hooks 先 spool 本地事件并带稳定幂等键，session-end 交给 drain；服务对 key 的完成标记在下游 wiki/handoff 效果之后设置，意味着崩溃恢复优先避免静默丢事件，但完成标记前的副作用仍可能重复，不能宣传成端到端 exactly-once。[隐私类型边界](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-core/src/sanitize.rs#L350-L386) · [单写 actor](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-store/src/writer.rs#L825-L855) · [重放语义](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/docs/ARCHITECTURE.md#L55-L103)

2. **检索比“FTS + embedding”更细，而且能解释排名。** `hybrid_search_inner` 将页面 FTS、向量、可选摘要向量、entity 命中、图邻居和 observation 投票汇入 RRF，常量 k=60；随后施加有界页面 authority 调整，当前版本和 TTL 过滤贯穿各路。embedding 行绑定 `(provider, model, dim)`，配置换模型后不能误用旧向量。一个很具体的修正：某 session 已经由 observation 全文命中投票时，代码将它自身页面 FTS 的贡献置零，避免“同一会话的标题词与正文重复投票”压过真正有答案的会话。`explain` 可返回每一路 rank、贡献和 graph 来源，适合分析检索失败，而不只看一个距离分数。[检索入口](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-store/src/reader.rs#L6344-L6410) · [活动流与筛选](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-store/src/reader.rs#L6590-L6740) · [RRF 与去重投票](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-store/src/reader.rs#L6784-L6951)

3. **handoff 是带所有权检查的状态转换，不是一段随便读的摘要。** `accept_handoff` 在事务内验证 workspace/project、operator 与接收 session，再从 `state='open'` 的记录领取；writer 返回是否由本次成功 claim，失败不得把正文交给 agent。SDK/MCP 同时支持以 `expected_page_id` 做条件更新、`create_only` 避免意外覆盖。并行 agent 的问题因此从“提示模型别抢任务”落到可检查的数据契约。[handoff 事务](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-store/src/ops.rs#L4519-L4708) · [writer 领取契约](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-store/src/writer.rs#L1801-L1822) · [程序化条件写入](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/docs/programmatic-memory.md#L108-L140)

### ④ 亮点与边界

最有价值的是它同时解决“记什么、怎么找、交给谁、怎么恢复”。对长期 agent 而言，模型替换、跨机器、并行会话、过期信息和隐私都是结构性问题，不能靠扩大 context window 一次解决。

几个容易被宣传性描述掩盖的边界：

- **zero-LLM 不等于没有模型计算。** 当前配置对未指定 embedder 的安装默认尝试本地 Candle / all-MiniLM-L6-v2（384 维）；首次后台下载约 87MB，当前启动先用 FTS，下一次启动才启用向量；下载/加载失败则降级。显式 `embedding_provider="none"` 才完全关闭向量。README 的“optional vectors”和部分文档的旧措辞不能直接当默认值，本文以配置/启动实现为准。[默认配置](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-cli/templates/config.default.toml#L143-L149) · [真正的启用/降级分支](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-cli/src/commands/serve.rs#L2790-L2863)
- **向量不是自动更好。** 项目 3.1.0 的 LongMemEval-S 自测在 470 个可回答问题上，FTS hit@5=0.951、p50=12ms；本地 embedding 模式 hit@5=0.940、p50=99ms。说明要按问题分布做消融，而非默认“加向量就提升”。这是指定数据集和 AMD 7950X3D 上的项目自报检索命中，不是本次复测，也不是最终回答准确率或生产延迟承诺；基准代码 SHA 与本次 HEAD 不同。[完整评测及 provenance](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/docs/benchmarks/longmemeval-s-3.1.0-release.md)
- **自动学习会产生写操作。** 无 provider 时不走 LLM 整理；一旦配置 provider，auto-improve scheduler 可审核新结束会话并默认批准有效提案，`require_approval=false` 是当前配置。团队接入应先决定是否改成审核后写入，不能把所有后台功能一概理解成只读或默认关闭。[配置说明](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-cli/templates/config.default.toml#L229-L245)
- **脱敏是 best-effort，Git/SQLite 也不是安全保险箱。** sanitizer 明确不保证识别无结构的高熵字符串；云 embedding 会发送页面内容，LLM rerank 会发送 query 和片段，本地数据也需要 OS 权限与备份策略。页面历史可恢复不等于所有 runtime/audit 数据都能从 Markdown 重建。[脱敏能力边界](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-core/src/sanitize.rs#L1-L45) · [数据处理说明](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/DATA_HANDLING.md)

### ⑤ 为什么热：事实与推断分开

事实：今日 +178；v3.0.0、3.0.1、3.1.0、3.1.1 分别于 10 月 14、15、16、17 日发布。3.1.1 修复 Windows 启动栈、hook spool 暂存文件恢复、OIDC 传输、LLM base URL 丢失、有界 observation 投影等实际运行问题；当前 HEAD 又合入 TTL 过期页面不应参与 lint/curator 的修复。[发布记录](https://github.com/akitaonrails/ai-memory/releases) · [变更内容](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/CHANGELOG.md#L12-L156)

公开讨论也反映用户正在把它放进多 agent 系统：[issue #1281](https://github.com/akitaonrails/ai-memory/issues/1281) 提议 agent-to-human 决策问答/持久等待；[issue #1261](https://github.com/akitaonrails/ai-memory/issues/1261) 提议可检测篡改的 audit hash chain。两者是开放需求讨论，不能写成现有能力。

推断：跨厂商 coding-agent 切换和长期记忆正是重度用户的摩擦点，连续发布、公开消融评测和较细的恢复/安全设计可能增强技术社区关注。未找到能够把今天涨星直接归因于某一版本或某次推广的公开证据。

### ⑥ 对你的技术方向有什么价值

- **AI agents / coding agents：很高。** 优先读 capture → summary → retrieval → handoff 全链，而不是只拿 `memory_query`。它给跨会话、跨 agent 的上下文连续性提供了具体实现
- **RAG：很高。** 重点是可编辑知识真源、派生索引、多路召回解释、TTL、版本过滤及 observation/page 重复证据处理；官方消融结果本身就是“词法基线要做扎实”的好案例
- **MCP：很高。** MCP tools 与 HTTP lifecycle ingress 分开，适合自研 agent 通过 Streamable HTTP 集成；Node 或 Python/Django 后端都可以消费同一 JSON-RPC 契约
- **Node / TypeScript：有现实接入口，但别误写成成熟 npm 包。** `companions/ai-memory-ts` 的 package.json 为 `private:true`、0.1.0、Node>=22，文档说明目前从 checkout 构建。源码包含 typed result/error、scope 预检、条件写入，transport 明确不自动重试并拒绝重定向，避免 bearer 被带往别的 origin。[SDK 状态](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/companions/ai-memory-ts/package.json) · [transport](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/companions/ai-memory-ts/src/transport.ts#L287-L341)
- **React/Next.js：后端能力可用，前端架构借鉴有限。** 自带管理端是 Askama/Tailwind 服务端渲染，不是 React/Next.js；做自己的 dashboard 可通过 API/MCP 接入，但要自行处理权限、过期、增量同步与删除对账

## 7. android/skills

### ① 排名、元数据与固定版本

官方第 **7**；[android/skills](https://github.com/android/skills)；**8,446 stars，+355 stars today，Kotlin，Apache-2.0**。今天重新读取的 main 仍为 **5bda39f154fb859a08d45e2392f3568e049f83fb**，提交于 **2026-10-14 11:24:05 UTC**，与昨天报告完全相同，**没有默认分支源码增量**。递归树为 654 条目、412 文件、30 个 SKILL.md，未截断。[Claude manifest](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.claude-plugin/plugin.json)与 [Codex manifest](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.codex-plugin/plugin.json)均为 **1.0.15**，最新 [release v1.0.15](https://github.com/android/skills/releases/tag/v1.0.15)仍是 10 月 14 日。仓库 pushed_at 晚于 main 提交，并不能据此说主干已有新功能。

### ② 它解决的具体问题

这是面向 Android coding agent 的任务知识包：把构建、平台新 API、迁移、安全和测试中的专门规则、参考文档及少量脚本放到可按需加载的技能目录。它减少开发者反复整理提示和定位官方文档的工作，不代替 Android SDK、Gradle 或设备验证。[README](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/README.md)说优先处理评估中模型表现不好的场景，并明确要求复查 AI 结果。今天不重复昨天 Play Policy Insights 的 Python 扫描链，改读 **testing-setup 如何把项目现状变成测试工程，以及安全示例有没有兑现自己的约束**。

### ③ 架构、入口和实际执行链

**分发层仍是知识与宿主分离。** 两种 plugin manifest 引用同一技能树；宿主按 SKILL 的 name/description 选择加载内容，再使用自身读文件、编辑和 shell 能力执行。选读的 testing-setup 并没有隐藏的 Kotlin 测试生成器，也没有独立服务入口。[更新工作流](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/.github/workflows/update-skills.yml)下载官方技能包、叠加 github-skills 分支、扫描 SKILL.md 更新 manifest，再创建 PR；当前 schedule 仍被注释。这里的可执行程序管理的是内容分发，而不是验证所有技能示例可编译。

**机制一：先盘点依赖和测试层级，再决定产物。** [testing-setup 第 1–3 步](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/testing/testing-setup/SKILL.md#L18-L88)要求从 libs.versions.toml/构建文件识别 DI、JUnit、mock、Robolectric、Compose/Views、截图与 E2E 现状，先输出分析报告；已有测试栈原则上保留。截图路径按 AGP 版本分流，高版本用 test suite，较低版本用旧插件，明确不把 AGP 升级混进本任务。这是条件化迁移计划，而非一套无差别依赖清单。

**机制二：把环境依赖替换为 fake，再按 source set 分层验证。** [第 4–12 步](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/testing/testing-setup/SKILL.md#L90-L183)优先把外部依赖抽成 interface + 原实现 + fake，仅无法做 fake 时再 mock；本地 Compose/Espresso UI 测试放 test，由 Robolectric 执行，要求真实设备时放 androidTest。SQLite 另做设备内存库测试；截图检查尺寸、主题和字体，行为测试检查点击、导航和状态恢复。这套流程的价值是避免把“截图没变”误当“交互正确”，但具体 edits 和运行结果仍由宿主 agent 产生，没有内置权限或验收 gate。

**机制三：安全知识同样需要输入、目标和调用边界。** [Intent 安全技能的手动跳转示例](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/security/android-intent-security/SKILL.md#L134-L184)实际数据流是：读嵌套 Intent → 拒绝 URI 授权 flags → resolveActivity → 检查同包及 exported → 固定 component → 启动。它做了若干真实约束，但**没有检查业务预期的具体目标组件**；不能因为函数名叫 safe 就说已经实现组件白名单。Android 官方 [Intent redirection 指南](https://developer.android.com/privacy-and-security/risks/intent-redirection)的对应示例同时检查预期 package 和 class。这里核实的是样例覆盖边界，不是对任何真实应用完成了可利用性证明。

### ④ 技术亮点、文档合同与边界

可借鉴的是 **“先识别项目条件，再选择工具与测试层级”**，尤其独立处理框架版本、模拟环境、真实设备、截图和行为。但今天重新读到的三个具体落差说明，知识包也需要合同测试：

- [第 2 步](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/testing/testing-setup/SKILL.md#L41-L56)直接要求无 DI 框架的非跨平台项目安装 Hilt，把测试任务扩展成生产架构选择；同包 [Hilt reference](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/testing/testing-setup/references/android/training/dependency-injection/hilt-testing.md#L1-L31)又明确构造函数注入的类可直接传 fake，不一定需要 Hilt。两段并非逻辑上完全互斥，但默认安装的范围明显大于单元测试的最低需要
- SKILL 把 Robolectric UI 测试放 test，Hilt reference 的 [UI setup](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/testing/testing-setup/references/android/training/dependency-injection/hilt-testing.md#L63-L107)却只说把 HiltTestActivity 放 androidTest。照搬两段会留下本地测试宿主所在 source set 的缺口；[状态恢复示例](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/testing/testing-setup/references/android/develop/ui/compose/testing/common-patterns.md#L77-L107)也确实只有 TODO 提示，没有具体状态修改和恢复断言。模板占位本身不是程序错误，但不能当成已完成验证
- [Service caller verification](https://github.com/android/skills/blob/5bda39f154fb859a08d45e2392f3568e049f83fb/security/android-intent-security/SKILL.md#L388-L445)把身份检查放在 LocalBinder 普通方法中；[官方 bound-service 文档](https://developer.android.com/develop/background-work/services/bound-services)明确这种直接调用模型用于同进程，跨进程应使用 Messenger/AIDL 等接口。样例没有实现它声称覆盖的跨应用事务入口。权限技能的 legacy 提示还把 pendingIntent.creatorPackage 用作 sender 认证；官方 [PendingIntent sender 风险说明](https://developer.android.com/privacy-and-security/risks/sender-of-pending-intents)说明创建者与实际发送者不能混为一谈

这些都是选读样例的静态对照，不应扩展为“整个 Android 技能库不安全”，也没有在本次研究中构建或攻击实际应用。

### ⑤ 新反馈、近期活动与热度

**事实：**今天刷新最近 15 条 issues/PR，新增或近期更新的 [#240](https://github.com/android/skills/issues/240)对应 DI/source-set/恢复示例问题，[#237](https://github.com/android/skills/issues/237)对应 Intent/Binder 示例，[#238](https://github.com/android/skills/issues/238)对应权限身份与 URI grant 等问题，读取时均 open；上面的具体代码落差由本次读取确认，不仅转述 issue。今天 main 和 release 均未变化，所以不能把反馈写成已修复功能。

[#241](https://github.com/android/skills/issues/241)于 10 月 17 日报告 coding agent 遇到 UI 不空闲、状态延迟后改测试时钟而不排查生产代码，形成“假绿”。这是值得关注的行为反馈，**本次未复现其 agent 会话、设备电量或卡顿结果**。也不能把任何手动时钟操作一概视为掩盖问题：官方 [Compose 同步测试文档](https://developer.android.com/develop/ui/compose/testing/synchronization)明确允许动画逐帧验证使用 autoAdvance=false；需要证明的是测试还检查原需求、生产错误是否被保留，而不是只查一个 API 名称。

**推断：**官方领域知识、跨宿主安装和更细的 Android 场景可能增加采用率，但本次没有找到与今日 **+355** 直接相连的发布传播证据。**暂无足够公开证据解释今日热度。** 仓库未启用 Discussions，这不是没有反馈的证据，issues 已提供了具体反馈渠道。

### ⑥ 对 AI Agents、RAG、MCP 与你的技术栈的价值

对 **coding agents**，今天最有价值的不是多装一个技能，而是把“测试通过”拆成原需求断言、生产修改、测试改动、实际运行环境四份证据；技能建议改 DI 或构建系统时，先审任务范围。对 **RAG**，它是带版本的领域知识源，适合按技能/参考文档检索，但应保留 SHA、来源日期和未解决 issue，不能把官方来源自动当无误答案。对 **MCP/Agent**，它主要教宿主如何用工具，不是 MCP 服务，也不在提示里实现真正的权限隔离。

对 **React/Next/Node**，fake 外部依赖、组件行为与截图分开、不要为了绿灯删断言，同样适用；对 **Python/Django**，可以用相同思路区分 unit、数据库集成与 API/E2E，并让 agent 报告哪些测试被改以及为什么。这里更适合复用“分层测试计划与审阅清单”，不要机械移植 Android 的依赖选择。

**本次已读与未做：**重新读取 README、两种 manifest、完整递归树、更新工作流全文；testing-setup 全文、Hilt reference 的单元测试/依赖/UI runner/source-set 段、Compose common-patterns 的恢复示例；Intent 安全的手动跳转和 Binder 实现段、权限技能的 sender/URI/rationale 对应段；最新 15 条主干 commits、5 条 releases、15 条 issues/PR 和 #237/#238/#240/#241 正文；另核四份 Android 官方文档。未逐项审计其余 27 个技能，未运行 Android 构建、模型或测试。

## 8. stablyai/orca：把不同 coding agent 放进可监督、可恢复的工作台

### ① 元数据与阅读锚点

今日榜单：TypeScript｜95,480 stars｜今日 +830｜[MIT](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/LICENSE)。排序和 stars 使用同一份 2026-10-18 GitHub Trending 官方今日榜快照；稍后仓库 API 读数为 95,481，这是抓取时间差，不改榜单数字。源码固定在 [`33e6785fe2c36730bc0dfcdf1db6208d471df833`](https://github.com/stablyai/orca/tree/33e6785fe2c36730bc0dfcdf1db6208d471df833)，以下属于公开源码静态阅读，未安装或运行项目。

### ② 具体问题：解决“同时开很多 agent 后，谁在改哪里、谁需要我”的问题

Orca 是跨平台开发工作台：把 Claude Code、Codex、OpenCode 等现有 coding agent，Git worktree、终端、编辑器、浏览器、diff/PR 与手机远程入口放在同一界面。它利用已有 agent 及其账户运行，不提供一套新的基础模型。典型用户是已经在并行使用多个 CLI agent、开始被终端窗口、分支切换、权限提问和远程会话管理拖慢的开发者。[项目 README](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/README.md)

这里的两层能力应分清：普通“多个终端/多个 worktree”覆盖广泛 CLI；实验性的 orchestration 才进一步提供 Run、Task、Dispatch、消息收件箱和 decision gate。支持在终端里运行，不等于支持同等完整的原生聊天、模型切换和权限 UI。[Orchestration 模型与实验状态](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/docs/site/content/docs/cli/orchestration.mdx#L8-L31)、[ACP 能力声明](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/acp/acp-structured-agent-definitions.ts#L20-L46)

**实际使用路径：从一个任务到可检查的工作结果**

常规流程是导入仓库，为一个需求或 bug 创建独立 worktree，选本机或远程执行主机和 agent；各任务分别拥有分支、文件、终端及浏览器页。完成后在工作台看相对起点的 diff、批注交回 agent，再 commit/push/开 PR。worktree 创建中的 fetch/checkout 放在后台并展示进度，支持取消或重试。[Worktree 生命周期及后台创建](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/docs/site/content/docs/model/worktrees.mdx#L7-L28)

更复杂的并行任务采用显式监督流程：创建 Run → 创建带依赖的 Task → worker-start 指定 agent 和工作目录 → coordinator 用 check 等待消息 →处理 Delivery 后 ack → worker 用 taskId、dispatchId 和 outcome 报告结果。worker 可以在现有 worktree 工作，也可以开新子 worktree 或发到其他主机；任务结算后可释放终端，同时保留可读取的输出。完成不是看到终端“安静了”，而是收到归属于当前 Dispatch 的结果。[实际 CLI 工作流](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/docs/site/content/docs/cli/orchestration.mdx#L35-L103)

开发环境仍需自己安排：新 worktree 不会自然带上 gitignored 依赖和 .env。项目提供共享目录、`.worktreeinclude` 复制与 `orca.yaml` 配置；共享 `node_modules` 省空间，但不同分支依赖不一致时仍可能相互影响，后半句是基于共享链接机制的工程判断。[共享目录与复制规则](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/docs/site/content/docs/model/worktrees.mdx#L39-L64)

### ③ 架构与源码：UI 之下是 runtime、提供商适配和持久化任务状态

**总体数据流。** React renderer 的操作经 Electron preload 的 `runtime.call/subscribe` 进入主进程 IPC；主进程在启动时注册 IPC 并初始化服务。CLI 则通过 RuntimeClient 找到本地 runtime 或已配对的远端：本地采用 Unix socket / Windows named pipe，远端走 WebSocket。执行主机掌握仓库、worktree、进程与会话；UI 接收终端、布局与聊天事件。依赖可核验为 Electron、React 19、Zustand、Monaco、xterm、node-pty、ssh2、ws，根 package 的 Node engine 为 24。它是 Electron/Vite 桌面架构，不能因为文档站目录存在就归类为 Next.js agent 框架。[入口](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/index.ts#L110-L149)、[preload RPC 桥](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/preload/api/runtime-bridge.ts#L14-L44)、[RuntimeClient](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/cli/runtime/client.ts)、[本地传输选择](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/runtime/runtime-rpc/runtime-rpc-socket-metadata.ts#L44-L62)、[依赖清单](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/package.json)

手机还有独立的 relay 路径：手机和桌面各自发起出站 WebSocket，由 director 分配 relay cell，再由 cell 转发两端帧；仓库包含 relay 与 push gateway 的源码。远端 Orca Server 则明确由服务器保存项目、终端、账户和会话，笔记本仅提供 UI，因而客户端休眠不应终止服务器上的 agent。手机 relay 与私有网络上的 Remote Orca Server 是不同连接场景。[Relay 架构](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/cloud/README.md#L1-L29)、[远端执行归属](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/docs/site/content/docs/remote-servers.mdx#L8-L35)

**值得读的实现一：任务派发先持久化，避免“重试开出两个 worker”。** `createStartingWorkerDispatch` 在 `BEGIN IMMEDIATE` 事务内核对 mutation receipt 的 caller、requestId、method 和 payload hash；重复请求若参数变化会报 request_mismatch，已有接受记录则返回需要恢复的 operation_unknown，而不是直接重复发起。随后校验 Task 是否 ready 或可合法重试，记录 Dispatch、worker 的 starting/accepted 状态及可选远端归属，再原子更新 Task 为 dispatched。数据库采用 SQLite WAL、NORMAL 同步和 5 秒 busy timeout。这是把网络不确定性与任务状态分开管理，不能夸大成外部工具副作用的全局 exactly-once 保证。[派发事务](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/runtime/orchestration/db/worker-dispatch/worker-dispatch-start.ts#L45-L199)、[数据库初始化](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/runtime/orchestration/db/orchestration-db.ts#L28-L41)

消息消费另有 `consumer_generation` 栅栏：事务内检查当前 Run/Dispatch 与代际，不一致就返回 consumer_fenced，防旧进程在重连或重派后继续消费新主人的信箱。文档规定未 ack 的 Delivery 按 FIFO 重放，worker 的 heartbeat 仅证明存活，不能当作完成。这组边界很适合借鉴到自己的多 agent 调度器。[消费权校验](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/runtime/orchestration/db/messages/mailbox-consumer.ts#L5-L45)、[消息及 worker 合约](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/skill-guides/orchestration/references/worker-contract.md)

**实现二：统一聊天界面，但保留提供商的协议与生命周期差异。** Claude 结构化会话打开 stream-JSON connection，并先验证 provider session ID，外来帧不会直接进入状态；Codex 打开 app-server connection，并通过 journal translator 归一化事件；ACP 另有 JSON-RPC runtime，处理 initialize、session/prompt、权限请求、取消和 session/update。因此不能把整个原生聊天架构只描述为“抓终端文本”。尤其 Codex adapter 先让事件进入 journal，接受后再更新后台任务和向观察者发事件；新 acquisition 公布前先缓冲，已被替代连接的事件不再投递，旨在避免 UI 比持久化事实更早确认结果。[Claude 会话入口](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/claude/claude-structured-session-acquisition.ts#L1-L110)、[Codex 获取连接](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/codex/codex-structured-session-acquire.ts#L80-L148)、[journal-first 与旧连接隔离](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/codex/codex-structured-session-adapter.ts#L103-L150)、[ACP 协议实现](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/acp/acp-session-runtime.ts#L105-L131)

**实现三：worktree 创建不是拼一条 git 命令。** 预备 checkout 先取得带归属的锁，在 fetch/物化间重复校验锁；通过 `reset --hard` 物化预备目录，注释明确是为了避免提交前触发用户 post-checkout hook。最终化时比较预备 HEAD 与实际目标，必要时刷新后再移动，失败时按拥有权清理。这个设计体现并行创建、取消和分支变化下的资源归属处理；这里只读到了实现，未验证性能收益。[预备与最终化逻辑](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/git/worktree-create-preparation.ts#L34-L92)、[提交前再校验 HEAD](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/git/worktree-create-preparation.ts#L134-L198)

### ④ 亮点、边界与采用成本

亮点是把“人监督多个 agent”所需的工作目录、结果审查、权限交互、连接恢复和终端生命周期连成一套。底层大量处理归属、幂等、持久化和崩溃后恢复，比增加一个聊天输入框更接近真实使用的难题。

需要保留的边界：
- **不会因创建 Run 就自动规划或调度。** 当前文档写明 Run 只是命名空间和 coordinator inbox；旧 `orchestration run/run-stop/coordinator-start/coordinator-stop` 已无副作用，用户或协调 agent 必须使用新的任务与 worker 流程。不要依据仓库里还留着的 Coordinator 类，把“自动分解、全自动 DAG 执行”当成现成功能。[当前合约](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/docs/site/content/docs/cli/orchestration.mdx#L17-L31)
- **worktree 是文件/分支隔离，不能据此推断进程沙箱。** agent 所用凭证、网络和操作权限仍取决于执行主机与 provider。Remote Server 官方标为 beta，建议受控私网，并明确不应直接把端口暴露公网；配对链接授予 runtime 访问权。[远端安全要求](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/docs/site/content/docs/remote-servers.mdx#L112-L122)
- **跨 provider 和多设备兼容在快速变化。** 最新 release 仍把 native chat 标为 experimental，并要求同步更新远程 host 才能得到相关功能；10 月 18 日抓取的 PR #30107 尚未合并，描述了 Claude CLI 更新后模型目录竞争导致运行模型被错误替换的问题，不能把该 PR 的修复当成已发布。[v1.4.229](https://github.com/stablyai/orca/releases/tag/v1.4.229)、[尚开放的模型目录修复 PR](https://github.com/stablyai/orca/pull/30107)
- **开源范围不是所有线上服务。** relay 已公开，但 cloud README 指出 API/auth 服务和部分基础设施根目录留在私有 orca-cloud 仓库，不能据此承诺整个托管后端一键完整自建。[明确列出的未公开部分](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/cloud/README.md#L98-L103)

### ⑤ 为什么现在值得看：事实与热度推断分开

事实：今日榜第 8、+830 stars；最新桌面 release v1.4.229 发布于 2026-10-17 06:54 UTC，摘要聚焦原生聊天内联编辑、更多 agent 的共享技能安装、手机工作区同步、SSH 恢复和 Jira 工作流。前一桌面 release v1.4.227（10-16）新增每个原生聊天的独立权限模式；v1.4.224（10-10）强化 SSH 上的 managed Orca server。可以核验的近期主题是把并行 agent 工作台做得更完整，并持续修复跨端使用中的可靠性问题。[三个版本记录](https://github.com/stablyai/orca/releases/tag/v1.4.229)、[v1.4.227](https://github.com/stablyai/orca/releases/tag/v1.4.227)、[v1.4.224](https://github.com/stablyai/orca/releases/tag/v1.4.224)

提交层面，固定 SHA 是 10 月 18 日的依赖安全更新，实际 patch 更新了 smol-toml、KaTeX 等依赖；最近十个提交还包括手机工具调用展示对齐桌面、服务端浏览器客户端/HTTP 修复，以及破坏性操作拒绝含糊主机归属。它们比营销口号更能说明项目当前投入方向。[固定提交及 diff](https://github.com/stablyai/orca/commit/33e6785fe2c36730bc0dfcdf1db6208d471df833)、[服务端 HTTP 修复](https://github.com/stablyai/orca/commit/d71e3e9d45815268c9c08c386599abd0463503f1)、[主机归属修复](https://github.com/stablyai/orca/commit/532cad2cb31b122f6b2f0076650223372cb5c236)

推断：多种 coding agent 普及后，开发者需要跨 agent、跨机器的监督入口；Orca 最近一轮聊天/手机/SSH 更新可能增加了讨论与试用吸引力。但本次没有访客来源、社交传播或 star 增长归因数据，不能证明某个 release、PR 或功能直接造成今日 +830。

### ⑥ 对你的价值：先试工作流，再读可靠性实现

- **AI agents / coding agents：高相关。** 适合用两个独立 worktree 分派“实现”和“测试/审查”，再由你检查结果；源码重点读 Dispatch 事务、generation fencing 和 journal-first，能直接改进自己的监督式 agent 系统
- **React / Next.js / Node：直接可用。** 浏览器 Design Mode 可把选中元素的 HTML、CSS 与截图送回 agent，配合 diff 批注适合前端迭代；Node/TypeScript 开发者还可读 Electron IPC、WebSocket runtime 与跨 provider adapter。但 UI 工作台本身不是 Next.js 模板
- **Python / Django：工作流价值大于库复用。** CLI、Git worktree 和 SSH 都不限定业务语言，适合把后端实现、测试、迁移检查分给不同 agent；数据库、端口、虚拟环境和 .env 仍需按任务隔离，不能因为 worktree 独立就共用会产生冲突的外部状态
- **RAG / MCP：间接相关。** 已读源码有 `.mcp.json`、Cursor/Claude MCP 配置识别与 server 摘要检查；这说明它能帮助观察已有 agent 的工具配置，不足以把它归类为 RAG 检索引擎或通用 MCP server 框架。若你要实现向量检索、召回评测或自己的 MCP 服务，需要另选对应库。[MCP 检查实现](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/shared/mcp-config.ts#L10-L70)、[Design Mode 与 diff 工作流](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/README.md)

建议的最小评估是选一个非敏感仓库、两个不冲突的任务与现有 agent 账户，先检查 worktree 创建、结果审查、重连和清理是否真的降低管理成本，再决定是否启用实验性的 orchestration。不要先把真实生产凭证和全部并行任务搬进去。

## 9. anthropics/claude-code

### ① 排名、元数据与版本锚点
官方第 **9**；[仓库](https://github.com/anthropics/claude-code)；**151,796 stars，+179 stars today，TypeScript**。本次 main 固定为 **dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8**（2026-10-17 23:14:49 UTC），递归树 2,187 条目；最新读取的正式发行是 [v2.1.302](https://github.com/anthropics/claude-code/releases/tag/v2.1.302)，发布于 10 月 16 日 20:53:06 UTC。版本和 main 不等同：main 之后还有公开 mods 改动。

**仓库性质必须澄清：**这不是 Claude Code 整个商业客户端的可自行构建开源仓库。它提供产品 README、changelog、issue、插件示例，以及明确公开的四个 built-in mods 源码。根 [LICENSE.md](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/LICENSE.md)为 All rights reserved、使用受商业条款约束，不能因 GitHub 可读就叫 MIT/Apache 开源。以下深读的是仓库确实公开的扩展实现，不推演未公开引擎。

### ② 它解决什么实际问题
产品把读代码、编辑、工具调用和 Git 工作流接到自然语言任务上；仓库对开发者更直接的用途，是观察宿主扩展契约、可执行插件、兼容性修复和真实用户反馈。对自己的 coding agent，最值得抄的是问题划分与测试思路，而不是假定可以从这个仓库重建完整 Claude Code。

[README](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/README.md)把原生安装作为推荐，npm 安装标为 deprecated；顶部 Node 18+ 徽章不能当成公开仓库的完整依赖清单。公开 mods 使用 TypeScript、宿主提供的 `claude-code` 类型和测试运行时，未见根 package.json 可供构建整个客户端。

### ③ 真实架构与三条可读实现
[mods/README](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/README.md)说明每个 mod 是带 manifest、hooks 配置与 `register(on, options)` 的完整插件。事件函数接 `$` 引擎接口、事件 `e` 与 `next`，沿 hook 链处理。现有四个 mod 为 agents-md、sec-default、diff、telemetry；本次核心深读前两个。它们依赖宿主事件与来源元数据，并不独立实现文件系统权限或 LLM 调用。

**机制一：项目指令是结构化上下文，不是把文件字符串随意拼在 prompt 尾部。** [agents-md/register.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/agents-md/hooks/register.ts)注册 `prompt.context`：默认 `claude-md-or-agents-md` 模式先检查工程自己的 CLAUDE 文件，再按祖先目录查 AGENTS.md；找到后映射为 `kind: project` 的 InstructionFile。宿主负责最终 framing 和对子 agent 的省略规则。`managed-only` 只在这个事件中过滤个人/项目指令，文档明确说引擎在 Read 时自动附的嵌套 CLAUDE 指令仍会到达，不能称它为彻底禁用项目输入的安全边界。

[unseen-files.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/agents-md/hooks/files/unseen-files.ts)按规范路径去重，并拿现有 project/local 文件的 trim 后文本识别 CLAUDE 导入或链接的同内容 AGENTS 文件；空文本不作内容去重依据。注意它新增候选后只加入路径集合，没有把新增文本加到现有文本集合，因此不是任意两个不同路径候选的全文去重器。[with-project-files.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/agents-md/hooks/files/with-project-files.ts)再按导入链根目录计算插入位置，保留宿主原有指令顺序。

**机制二：Read 触发按目录、按 agent 的延迟加载。** 同一 register 的 `tool.call(Read)` 先让真实读取完成；拒绝或错误时不追加上下文，关闭 attachments 的运行也不追加。它将读路径绝对化，检查工程根目录，取得路径上的 AGENTS/CLAUDE 文件，过滤已在全局上下文或该 agent `given` 集合里的文件，再附到读取结果。完整读到指令文件本身时会记为已给，带 offset/limit 的局部读取不会误当全文已注入。新 fork 复制父 agent 的已给集合，resume 不覆盖自身集合。这个状态细节能减少多 agent 重复上下文，又避免半读文件导致后续缺指令；没有测量其 token 节省效果。

**机制三：权限 verdict 不仅比较 allow/ask/deny，还保留决定者和理由。** [sec-default/register.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/sec-default/hooks/register.ts)的 `tool.check` 先拿完整链结果，检查 trace 是否被用户层插件重写；若组织策略要求保留拒绝，就用 `next.to(e, 'append')` 越过用户层重新取 verdict。 [holds-over.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/sec-default/hooks/held-verdict/verdicts/holds-over.ts)比较宽严程度、全部 verdict 字段，以及 rule/hook/setting/decider/ceiling 的来源，而不是只保留一个 decision 字符串。

今天读取到的 [10 月 17 日 22:47 提交](https://github.com/anthropics/claude-code/commit/8a8dff6af07514630d2d4843c7005129633a66f5)新增 [is-person-tightening.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/sec-default/hooks/held-verdict/verdicts/is-person-tightening.ts)：仅将相同 ask 的 decider 从 host 改为 person 视为更严格，可以通过；同时更改其他字段不满足这个例外。这是公开源代码的真实增量。更晚的 main 提交只补充 sec-default 的部署说明，不能把两者都写成新增运行代码。

### ④ 技术亮点与限制
值得借鉴的是**结构化指令来源、agent 私有去重状态、权限裁决来源可追踪**。相同内容不等于相同权限，`ask` 也不等于由谁都能批准；这比在 prompt 里写“不要覆盖规则”更可测试。

但 [sec-default 文档](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/sec-default/README.md)明确承认环境变量 pin 名单不是恶意插件的安全边界。其能力依赖宿主锁定的 tier/provider、受控 `next.to` 和安装位置，不能单独复制几段 TS 就获得同等隔离。[mods/tsconfig](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/tsconfig.json)启用 strict/noUncheckedIndexedAccess 并对公开类型和 tests 检查，但本次静态读了 [agents-md/register.test.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/agents-md/tests/register.test.ts)，测试包含纯 AGENTS 工程、已有 CLAUDE 指令、祖先遍历失败和缺 telemetry provider，但未运行测试。文档还说 function hooks 是 early access，API 可跨版本变化；发行包是否已含当前 main 的每项改动应单独核对。

### ⑤ 近期活动与热度：事实和推断
**事实：**最近 10 条提交以更新 mods 和 changelog 为主；最新 release 2.1.302 的官方说明包含 MCP 协议兼容性、插件加载、异步配置写入、权限模式及 subagent 默认行为变化。它是发行说明证据，不是本次验证的闭源核心实现。例如“最多同时跑 12 个同事件 prompt/agent hooks”来自 release，不能说在上述公开 register 中实现。

公开 [issue #103101](https://github.com/anthropics/claude-code/issues/103101)在 10 月 18 日提出 auto-mode 被分类器拒绝时转人工询问的需求；它说明用户确实关注裁决和交互体验，但只是未解决的功能请求，不证明上述 mod 更新解决了它。[issue #92717](https://github.com/anthropics/claude-code/issues/92717)则报告多端分组不同步，是用户报告而非已确认根因。本次读取按更新时间的 10 条 issue，未做全面缺陷统计。

**推断：**扩展 API 的公开切面、频繁兼容性修复和跨设备工作流可能吸引开发者关注。没有取得能把这几项变化与今天 +179 直接连接的传播证据，**暂无足够公开证据解释今日热度**。

### ⑥ 对你的工程价值
对 **AI Agent/coding agent/MCP**，推荐把权限事件建模为“决定 + 决定者 + 原因 + 来源 + 运行证据”，在 UI 区分模型建议、自动 classifier 和真正人工批准。对 **RAG**，agents-md 是文件系统分层、按需加载的上下文选择器，不是 embedding 检索；但目录边界、去重、fork 继承和 partial-read 语义可以迁移到 repo RAG。

对 **React/Next/Node**，可直接研究 TypeScript 事件中间件和结构化状态，不必假设终端 UI 使用 React/Next。对 **Python/Django**，同一模式可用于后台任务权限层、每个 agent 的已见证据集、以及检查失败时保留 unknown/deny 的策略。由于许可证与宿主依赖，更适合学习设计和在自己的许可条件下重新实现，不能默认复制分发。

**今日阅读覆盖：**完整递归树；README/LICENSE；mods 总说明及 agents-md/sec-default 说明；两个 manifests、hooks 入口配置、tsconfig；agents-md 主入口及文件分组/去重实现；sec-default 主入口、holds-over/is-same-verdict 与新增 is-person-tightening；agents-md register 测试；近期 10 commits、5 releases、10 issues 元数据/正文及最新两条提交 diff。下载其他文件只作定位，不声称已逐行审计；完整商业客户端、四个 mods 全部测试和运行时效果均不在本次验证范围内。

## 10. debpalash/VoiceStudio

### ① 排名、版本与今天真实新增范围

官方第 **10**；[debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio)；**73,480 stars，+2,125 stars today，Python**。本次固定 main 为 **d819ff54d93017bf4a5b34b605833162163c9e3c**，提交于 **2026-10-17 21:52:09 UTC**；递归树 **3,835 条目、3,498 文件，未截断**。根 [package.json](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/package.json)和 [pyproject.toml](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/pyproject.toml)仍是 **0.5.7、AGPL-3.0-only**；最新正式 [release v0.5.6](https://github.com/debpalash/VoiceStudio/releases/tag/v0.5.6)仍为 **9 月 23 日**。main 新能力不能当成 0.5.6 安装包已经包含，也不能说 0.5.7 已发行。

相对昨天 **f47221a1f0af89df27c34747471daa30391a9487**，[固定 compare](https://github.com/debpalash/VoiceStudio/compare/f47221a1f0af89df27c34747471daa30391a9487...d819ff54d93017bf4a5b34b605833162163c9e3c)为 **ahead 113、behind 0，282 个变更文件**。包含较早分支提交及多次 merge，不是一天写了 113 项独立功能。与昨日“只改 README 徽章”明显不同：这次已经合入移动端 companion preview、桌面 UI 测试以及若干后端修复。compare 返回的部分文件没有完整 patch，本次对核心文件另外按 SHA 读取，未冒称审完 282 文件。

### ② 它解决的实际问题

它把语音生成、声音克隆、转录、配音和长音频生产组合成可本地运行的工作台，并向其他应用和 agent 提供 API/MCP。适合希望把模型、声音资产、生成记录和制作流程放在同一环境的创作者和开发者；它替代的是分散的推理脚本与音频工具串联，不是一个新的统一语音基础模型。[README](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/README.md)区分本地工作流、可选远程服务和需同意的 analytics；多语言数量及音质仍是维护者定位，本文未实测。

今天的移动端解决的是**用手机控制自己的 VoiceStudio 后端**。[mobile 文档](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/docs/mobile.md#L1-L27)与 [M1 contract](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/contract/SPEC.md#L1-L17)都明确：推理仍在电脑、容器或服务器，手机端尚无 on-device inference，应用也还不是 App Store/Google Play 正式产品。不能只看后续 PR 标题，把“手机离线克隆/配音”提前写到今天 main 上。

### ③ 架构、入口与三条实现链

**原有主干与新客户端的关系。** 桌面是 Electron main/preload + React renderer，另有 Vite web 构建；[renderer 入口](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/electron/src/renderer/src/main.tsx)选择主工作台或 capture widget。[Electron 主进程](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/electron/src/main/index.ts#L270-L344)注册代理、更新、watch folders 和 capture，创建窗口后异步启动 backend supervisor。Python ≥3.11，FastAPI/uvicorn 提供 API，重推理由各引擎完成；新 Android 客户端使用 Kotlin 2.2.21、Compose、OkHttp、DataStore、WorkManager，iOS 用 SwiftUI。它们共享 API、主题 token 与语言目录，而非把 React UI 直接套到手机上。[Android dependencies](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/gradle/libs.versions.toml)

**机制一：一次配对产生“后端身份范围”，HTTP 和 UI 状态都不能跨范围漂移。**

[StudioViewModel.connect](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/features/src/main/kotlin/com/voicestudio/mobile/features/StudioViewModel.kt#L78-L108)先解析地址并检查 health，必要时交换 session，再调用受保护的 profiles 端点；候选后端确认可用后才切换当前连接。因此公开 health 成功不是认证通过，也不会仅因新地址探测失败就抹掉旧连接。

[VoiceStudioApi](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/core/network/src/main/kotlin/com/voicestudio/mobile/network/VoiceStudioApi.kt#L22-L105)共用一个 OkHttp client 处理 REST、WebSocket、上传、下载与播放：禁止自动重定向，每请求核对 scheme/host/port 与配对 origin，再加 PIN/session header；HTTP DNS 解析若包含非私有地址就拒绝。绝对媒体 URL 也必须同源。[SessionStore](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/core/data/src/main/kotlin/com/voicestudio/mobile/data/SessionStore.kt#L30-L65)将 session/PIN 用 AES-GCM 加密，host 作为附加认证数据，密钥置于 Android Keystore；master API key 只作交换参数，不写入 Secret 数据模型。

网络身份之外，[ViewModel 的旧响应检查](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/features/src/main/kotlin/com/voicestudio/mobile/features/StudioViewModel.kt#L30-L61)比较 API 对象身份，避免 A 后端迟到的 401 断开刚连上的 B；切换时增加 connectionId、清空音频/目录、取消旧 host 的 WorkManager 任务。iOS 的 [HostState](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/ios/VoiceStudioKit/Sources/VoiceStudioKit/Connection/HostState.swift)用 scopeID、任务取消和回写前检查实现同类隔离。这个模式可迁移到多账户、多 workspace 的 agent 控制台。

**机制二：配音是可恢复任务，批准也跟着任务和实际提供方走。**

[DubWorker](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/core/data/src/main/kotlin/com/voicestudio/mobile/data/DubWorker.kt#L81-L160)读取 host+job checkpoint，按“上传/链接导入 → 等准备任务 → 转录 → 每目标语言翻译 → 启动合成 → 等结果”推进。保存 uploaded、prepTask、segments、nextLanguage、renderTask，进程恢复后优先接续已有服务端任务；active host 改变会取消本地 pipeline，checkpoint 写入也检查 host 仍有效。

值得注意的是 [事件等待](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/core/data/src/main/kotlin/com/voicestudio/mobile/data/DubWorker.kt#L59-L79)先检查事件 payload 的 error/cancelled，再接受任务行 done，避免“任务管理器完成”覆盖真实阶段错误。失败按不可达、超时、429 和列明的 5xx 返回 retry，WorkManager 使用指数退避；这不等于所有 POST 获得 exactly-once 语义，断在远端接受请求与本地写 checkpoint 之间仍需另核服务端幂等合同。

[TranslationPolicy](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/core/network/src/main/kotlin/com/voicestudio/mobile/network/TranslationPolicy.kt)把在线提供方、远程或无法确认 loopback 的 LLM 端点视为需要本次 job 批准；保存 provider/category 和 provider+baseURL 的指纹，而不是持久“以后都同意”。[authorizedTranslation](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/core/data/src/main/kotlin/com/voicestudio/mobile/data/DubWorker.kt#L129-L175)不仅在开始时检查，还在耗时上传/转录之后、每次传出文本前重新核对路由；提供方或端点变化便停止复用旧批准。[回归测试](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/mobile/android/app/src/test/kotlin/com/voicestudio/mobile/DubConsentRegressionTest.kt#L86-L145)覆盖本地 LLM 被改成云端、缺批准和暂时设置读取失败。它比只保存一个 consent=true 更适合长期 agent 作业，但仍依赖服务端诚实返回配置。

**机制三：新增桌面 UI 测试把“监测器没有工作”也当失败。**

[desktop-harness](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/electron/tests/desktop-harness.mjs#L64-L136)用 Playwright 启动构建后的真实 Electron，独立含空格/非 ASCII 的 profile，接 fake backend，并跳过真实 Python 启动与 updater；这使本机窗口、preload/IPC、路由和设置持久化可跨平台检查，不需要下载重模型。[request-guard](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/electron/tests/fixtures/request-guard.cjs)预加载到主进程：Chromium 请求可取消，Node http/undici 请求只记录，最终由测试判失败；不能把它说成全网络沙箱。

[收尾检查](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/electron/tests/desktop-harness.mjs#L180-L229)除了拒绝外部请求和 renderer/main errors，还要求 log 里确有 app: 请求。空日志代表 hook 缺失或被替换，不是“没有泄漏”；失败保留 trace、截图和错误日志。新增 [自测](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/electron/tests/desktop-ui.test.mjs#L27-L101)故意制造越界请求和失效监测器，验证 harness 真能让测试失败。这里的工程增量是可观察性本身也有断言。

### ④ 亮点、验证层级与边界

今天最有迁移价值的是 **host 身份、任务恢复、批准范围和测试证据分别建模**。单个 boolean 无法同时表达“已连接”“认证有效”“任务结束”“产物正确”“允许外发”；这套实现已经在多处主动区分它们。

仍需守住四个边界：

- 手机只直接请求配对主机，不意味着文本永远不离开该主机。远程翻译由主机执行，所以需要上述 provider/route 级批准。私有地址允许 HTTP，也不等于通信已加密或局域网天然可信
- 本地停止监控、取消上传或换 host，不自动证明远端长任务已经终止；M1 文档明确允许服务端作业继续，取消语义必须分别看本地与服务端
- [共享 contract 测试](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/tests/test_mobile_contract.py)比较生成的 OpenAPI/theme token、operationId 与字符串命名，能发现资料漂移，但不是两平台全部功能等价的证明。部分本地 token 测试在缺 Bun/deps 时 skip，CI 另有显式检查
- 桌面 UI 测试使用假后端；新 [CI matrix](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/.github/workflows/ci.yml#L218-L294)覆盖 macOS、Windows、Linux，不能证明真实模型的音质、许可证可用性、GPU 稳定性或移动端真机体验。读取时该 SHA 的 [CI run](https://github.com/debpalash/VoiceStudio/actions/runs/39072734125)已 success，三个 Desktop UI jobs 也为 success；这是托管 CI 状态，不是本文执行了测试

### ⑤ 相对昨天的修复、未合入事项与热度

**已合入、源码已核：**昨天仍 open 的 [Supertonic PR #2939](https://github.com/debpalash/VoiceStudio/pull/2939)已于 **10 月 17 日 04:29:20 UTC** 合入。当前 [_normalize_lang](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/engines/supertonic3/sidecar.py#L225-L305)不再将所有字符串截成前两字母，而是映射 31 个已支持全名、保留 ISO code，并只对符合形式且前缀已支持的地区标签取基础 code；未知全名继续交给 SDK 校验。新 [语言测试](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/tests/test_supertonic3_language_names.py)替换 SDK/audio 边界，检查真实 synthesize handler 收到的 lang，不做音频质量测量。#2938 的 preset voice 需求并未因此全部完成。

**仍未合入：**[#2941 HOME 脱敏修复](https://github.com/debpalash/VoiceStudio/pull/2941)仍 open，当前 [scrub.py](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/core/scrub.py#L120-L134)仍使用旧的后界 allowlist；不能因别的修复合入而把昨天的诊断隐私风险一并划掉。新的 [#2969 on-device inference](https://github.com/debpalash/VoiceStudio/pull/2969)在读取时 **open、merged:false**，真正手机端离线推理、下载模型与 native runtime 的描述仅属于该提案；作者列出的测试也不能当成当前 main 或本文实测。

**已合入的移动端**是 [#2965](https://github.com/debpalash/VoiceStudio/pull/2965)，merge 时间 **10 月 17 日 20:34:55 UTC**；随后合入桌面 UI CI 与贡献说明。最近 issues 还有 [#2970 后端暂时无响应](https://github.com/debpalash/VoiceStudio/issues/2970)等使用反馈，本次没有诊断该用户环境或推断统一根因。

**热度判断：**今天有实质源码活动，这是事实；本地语音工作台加原生手机入口可能扩大使用场景，这是推断。没有足够证据把这些合入与当天 **+2,125 stars today** 建立因果，**暂无足够公开证据解释今日热度**。不把分支提交数、CI 通过或 PR 作者测试数当作涨星归因。

### ⑥ 对 AI Agents、RAG、MCP、React/Next/Node 与 Python/Django 的价值

对 **AI Agents**，优先借鉴“操作归属哪个 host”“迟到响应是否还能写回”“重试前批准是否仍对应同一个服务”的状态设计。对 **MCP**，现有 [generate_speech](https://github.com/debpalash/VoiceStudio/blob/d819ff54d93017bf4a5b34b605833162163c9e3c/backend/mcp_server.py#L541-L625)仍通过 API 生成，显式 profile 优先于 client binding；输出可选 files/resources/both，files 模式能避免长 WAV base64 挤占模型上下文。当前默认仍 resources，集成方应主动选择合适模式，而不是假定默认已优化。

对 **RAG**，检索、引用和答案证据放上游，音频任务接收经授权的文本并保留文本与音频关联；仓库本体不是检索系统。对 **React/Next/Node**，真实 Electron + 假后端 + 断言监测器工作的 UI 测试，比只测组件快照更接近完整客户端边界，但不代替真服务测试。对 **Python/Django**，可将重推理放独立 service/worker，HTTP API 只是控制面；对长任务保存阶段与远端任务 ID，对外部服务批准保存目的地指纹并在传输前重核。无需因为加了手机入口就把模型搬到每一个前端运行环境。

**本次实际阅读范围：**README、根/Electron manifests、pyproject 的版本与核心依赖段；完整树和全部 compare 文件清单，核心修复 diff；Electron main 的窗口/后端启动/退出段与 renderer main 全文；backend main 的 router/MCP 装载段；mobile docs、M1 SPEC、Android dependency manifest、HostPolicy/VoiceStudioApi/SessionStore/StudioViewModel/TranslationPolicy/DubWorker 全文，iOS HostState 全文，移动 API/host-switch/consent 回归测试对应段；desktop harness、request guard、local-first allowlist、guard 自测与 UI 场景索引、CI matrix；Supertonic 归一化/dispatch 与新增测试全文、scrub 后界；MCP 输出模式/目录边界/客户端及 generate_speech 段；15 条最近 commits、5 条 releases、20 条 issues/PR，#2939/#2941/#2965/#2969 正文和 merge 状态、当前 SHA 的 CI run/jobs。其他引擎、iOS 全部网络/上传链和移动端未合入 PR 源码未作全面审计；没有安装项目、运行测试、生成音频或测量性能。

## A. 最值得继续深读的三个源码切面

### 1. ai-memory：可解释多路检索，尤其看重复证据如何失真

读 [reader.rs 的召回/筛选/RRF](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-store/src/reader.rs#L6590-L6951)，再读 [handoff 的条件领取](https://github.com/akitaonrails/ai-memory/blob/995e35d5866973c3176709261e924a67e3c76158/crates/ai-memory-store/src/ops.rs#L4519-L4708)。它把页面、原始 observations、entity 和图邻居变成多路证据，但没有任其重复投票无限抬升相同 session；TTL/版本与 embedding 模型标识也参加检索契约。

对你做 RAG/Agent，这比只读“向量相似度查询”更有价值。建议先复现自己的词法基线，再做逐路消融和过期/重复样本测试。项目自报 FTS hit@5 高于本地向量模式，提醒我们复杂度必须由任务数据证明；该结果不是本次复测，也不能外推为向量普遍无用。

### 2. Orca：派发事务与过期消费者隔离

读 [worker-dispatch-start.ts](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/runtime/orchestration/db/worker-dispatch/worker-dispatch-start.ts#L45-L199) → [mailbox-consumer.ts](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/runtime/orchestration/db/messages/mailbox-consumer.ts#L5-L45) → [Codex journal-first adapter](https://github.com/stablyai/orca/blob/33e6785fe2c36730bc0dfcdf1db6208d471df833/src/main/codex/codex-structured-session-adapter.ts#L103-L150)。这里最重要的问题是：请求超时后可否重试？旧进程重连后还可否收新任务？UI 是否先于持久化事实宣布成功？

对 Node/TypeScript agent 后台与 React 控制台，可直接借鉴 operation receipt、generation fencing、持久化后再发布事件；对 Django/Celery 也有同类事务/worker lease 设计价值。不要把创建 Run 误当自动规划器，也不要把局部事务和幂等键误当所有外部副作用 exactly-once。

### 3. Claude Code 公开 mods：谁能改指令，谁能改权限决定

读 [agents-md/register.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/agents-md/hooks/register.ts) → [sec-default/register.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/sec-default/hooks/register.ts) → [is-person-tightening.ts](https://github.com/anthropics/claude-code/blob/dd6bee38458cc3e6dc5f2b16eca1f0f364619ad8/mods/sec-default/hooks/held-verdict/verdicts/is-person-tightening.ts)。一个负责目录化、按 agent 延迟加载的项目指令，一个负责用户插件不能随意重写组织裁决；今天的新变更尤其展示“交给人决定”是权限语义的一部分。

对自研 coding agent/MCP 网关，建议把来源、决定者、理由和读取完整性放进结构化事件，别只保留 allow/deny。这里推荐学习公开设计，**不是推荐复制商业许可代码，也不意味着完整客户端开源**；宿主不可伪造的来源元数据与实际执行边界仍是必要前提。

## B. 今天十个项目支持的五个趋势

1. **Agent 产品开始围绕可验收的具体工作流组织。** ai-job-search 把岗位事实、状态评分、reviewer、PDF 文本层和版面检查串起来；VoiceStudio 把模型进程、音频产物与移动 companion 接起来；CLI-Anything 则把已有桌面软件变成命令接口。共同问题是输入、状态和成果是否可靠，而不只是“能不能发起一次模型调用”
2. **跨 agent 的连续性正被拆成记忆、交接和运行所有权。** ai-memory 将 Markdown 知识、派生索引和 handoff 分开；Orca 将 Run/Task/Dispatch、消息消费代际和 provider 会话分开；ECC 的观察器与适配器展示另一种跨宿主组织方法。不同层不能用单个“memory”或“orchestration”标签替代
3. **完成信号必须由产物与证据支持。** CLI-Anything 的 Krita 导出适配可能丢掉底层失败结果；Android 的测试反馈提醒不能只数绿色测试；求职工作流将跳过的版面检查与通过分开；Orca 的 heartbeat 与终态结果分开。错误传播、缺证据状态、写入后再公布，都是可迁移的可靠性设计
4. **权限、隐私和默认值成为工程接口。** Claude mods 保留 verdict 来源与决定者；官方插件、ECC 的安全相关开放提案显示名单/正则脱敏仍有边界；ai-memory 的本地 embedding 默认与可选 LLM 整理需读配置源码确认。“本地”“官方”“默认安全”均不能代替对实际数据路径和启用条件的核查
5. **热度仍然不等于当日代码增量。** 连续六项中五项 main 与昨日相同，仍有明显 stars today；VoiceStudio 则有真正的合入与移动端变化，Claude Code 新增公开 mod 语义，ai-memory 连续发版。日报需要区分已有实现、新反馈、开放 PR、主干合入与正式发行，不能把它们全都写成今日新功能或涨星原因

以上是本次前十的工程观察；样本集中于 agent 工具，不代表整个 GitHub、语言生态或商业市场的统计趋势。

## C. 与昨天实际报告比较：2026-10-17

已读取[昨日完整报告固定归档](https://github.com/DanielMax937/daily-research-reports/blob/974fcf26a695695336e3be203e71394535508629/2026-10-17/github-trending.md)，不是从记忆复原。昨日快照北京时间 10:26:57，今日 10:20:06，相隔 **23 小时 53 分 9 秒**。昨日前十依次为 claude-plugins-official、scientific-agent-skills、ECC、CLI-Anything、context-mode、ruflo、android/skills、superpowers、cursor/plugins、VoiceStudio。

| 连续项目 | 昨日 → 今日排名 | 昨日 → 今日总 stars | 快照总数差 | 今日 stars today |
|---|---:|---:|---:|---:|
| anthropics/claude-plugins-official | 1 → 1 | 40,651 → 41,821 | +1,170 | +1,397 |
| affaan-m/ECC | 3 → 3 | 281,569 → 282,556 | +987 | +1,145 |
| HKUDS/CLI-Anything | 4 → 4 | 53,543 → 54,091 | +548 | +574 |
| K-Dense-AI/scientific-agent-skills | 2 → 5 | 51,557 → 52,281 | +724 | +878 |
| android/skills | 7 → 7 | 8,100 → 8,446 | +346 | +355 |
| debpalash/VoiceStudio | 10 → 10 | 71,334 → 73,480 | +2,146 | +2,125 |

时间间隔并非完整 24 小时，官方 stars today 窗口也不透明；两列不应相互校正或混为“今日新增”。

- **相对昨日前十新进入四项：** MadsLorentzen/ai-job-search、akitaonrails/ai-memory、stablyai/orca、anthropics/claude-code。ai-job-search 昨日实际页排第 11，今日升到第 2；不应称其“首次上榜”
- **昨日前十、今日前十未出现：** mksglu/context-mode、ruvnet/ruflo、obra/superpowers、cursor/plugins。其中 ruflo 今日实际页仍为第 12，明确不是“退出全部 Trending”；其余只能说不在今日读取的前十
- **主题层面的样本变化：** 新增垂直求职工作流、跨 CLI 的持久记忆、桌面多 agent 调度器和宿主公开扩展源码；昨日 context-mode/Cursor 的上下文与编排话题由其他具体实现接续。这里是十仓样本观察，不代表整个生态占比

### 连续六项的源码基线核对

| 项目 | 昨日固定 SHA | 今日固定 SHA | 可确认变化 |
|---|---|---|---|
| claude-plugins-official | `ea10b213686c90bb1984b2016937310e05336cf3` | `ea10b213686c90bb1984b2016937310e05336cf3` | main 完全相同；新公开问题不等于新合入 |
| ECC | `76aaa77df6adc5b889e689007bf99b9a4f74af34` | `76aaa77df6adc5b889e689007bf99b9a4f74af34` | main 完全相同；正文单独核 adapter/观察器问题 |
| CLI-Anything | `34f519533bc175d2fe287ab8316b0dd99bb9cc43` | `34f519533bc175d2fe287ab8316b0dd99bb9cc43` | main 完全相同；新增 Krita 导出失败反馈与静态证据 |
| scientific-agent-skills | `a1043ef544e3a100c28e70a736b6cf32554d0677` | `a1043ef544e3a100c28e70a736b6cf32554d0677` | main 完全相同；统计计算新问题/修复提案尚未等于主干更新 |
| android/skills | `5bda39f154fb859a08d45e2392f3568e049f83fb` | `5bda39f154fb859a08d45e2392f3568e049f83fb` | main 完全相同；测试完整性反馈不能扩张成已确认通用缺陷 |
| VoiceStudio | `f47221a1f0af89df27c34747471daa30391a9487` | `d819ff54d93017bf4a5b34b605833162163c9e3c` | [固定 compare](https://github.com/debpalash/VoiceStudio/compare/f47221a1f0af89df27c34747471daa30391a9487...d819ff54d93017bf4a5b34b605833162163c9e3c)含 mobile companion、语言修复和 CI 等；详见正文 |

连续六项中五项 main 不变，VoiceStudio 的变化已不能沿用昨天“仅 README 徽章”的判断。比较里的提交数量包含分支历史和 merge，不表示今天独立发布了相同数量的新功能。新进入的四项没有昨日十项目源码基线，本文不补造它们的一日 diff；近期真实提交仍在对应节说明。
