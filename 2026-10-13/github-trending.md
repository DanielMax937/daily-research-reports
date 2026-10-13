# GitHub Trending 源码深读日报

## 2026年10月13日 · 北京时间

本期最值得带走的三件事：工具结果要能回查原始证据；所谓sandbox必须核对真实工作目录和写权限；模型/图形产物“格式合法”不等于语义正确。研究目标是官方日榜前10，但本次官方完整HTML只返回9项，因此下文完整研究这9项，**第10项缺失，不补榜、不凑数，也不称已经覆盖完整前10**。

## 榜单范围、时间与证据口径

- 唯一排名来源是 [GitHub Trending 官方日榜](https://github.com/trending?since=daily)。页面筛选：Repositories、Spoken Language: Any、Language: Any、Date range: Today；未使用搜索排名、累计stars排序或第三方历史榜替代
- 本次直接读取官方HTML的记录时间为 **2026-10-13 02:56:59 UTC，即北京时间10:56:59**；响应HTTP 200，源站响应头Date为 **02:56:30 UTC**，Cache-Control为max-age=0/private/must-revalidate。报告采用这次HTML里的顺序和数字。服务器Date证明响应时间，不能证明GitHub内部Trending计算刚好在这一秒刷新
- 完整HTML提取到 **9个article.Box-row**；当天网页文本读取也只有相同9项。北京时间 **11:12:26** 再次直接读取官方无参数页，HTTP Date为03:12:26 UTC，仍是同一顺序9项；此复核只检查数量/顺序，不替换10:56快照计数。未发现可核验第10项，无法进一步判定是官方此时只展示9项还是返回链路缺项。另一次网页读取的since=daily版本标记“上个月抓取”，明确排除，绝不拼接到今日榜单
- 累计stars、stars today、榜单语言全部来自上述同一快照；GitHub的stars today窗口未确认，**不等于北京时间自然日，也不等于两天累计stars之差**。源码读取时间稍后，统一固定完整commit SHA；榜单是热度样本，不是源码质量排名
- 已实际读回[10月12日已交付报告的固定存档](https://github.com/DanielMax937/daily-research-reports/blob/e5df9a6eb13b042913d86b4283eb8c098d5ef464/2026-10-12/github-trending.md)，作为唯一昨日报告基线。它只有8项可核验项目，且当时是“Crawled today”网页文本、没有HTTP Date；今天与昨天的新鲜度等级不同
- 逐仓区分README/设计文档、Skill规范、可执行源码与作者/用户测试报告。源码均可访问；大型文件按关键函数深入选读，未声称全仓审计。所有“新增研究发现”与“今天新增代码”分开
- 本轮完全只读：未安装依赖、执行第三方仓库代码、跑模型/benchmark、启动用户电脑或修改研究仓库。公开API/源码、固定版本、compare与原始讨论构成证据；测试源码存在、作者说测试通过，都不等于本轮执行通过

### 同一快照的可见顺序

| 顺位 | 项目 | 页面语言 | 累计 stars | stars today |
|---:|---|---|---:|---:|
| 1 | [morluto/rea](https://github.com/morluto/rea) | TypeScript | 163,731 | 45,327 |
| 2 | [bilawalsidhu/gods-eye-view](https://github.com/bilawalsidhu/gods-eye-view) | JavaScript | 53,849 | 1,895 |
| 3 | [mksglu/context-mode](https://github.com/mksglu/context-mode) | TypeScript | 27,380 | 246 |
| 4 | [storytold/artcraft](https://github.com/storytold/artcraft) | Rust | 22,412 | 4,095 |
| 5 | [open-webui/open-webui](https://github.com/open-webui/open-webui) | Python | 155,127 | 157 |
| 6 | [cathrynlavery/diagram-design](https://github.com/cathrynlavery/diagram-design) | HTML | 52,791 | 2,081 |
| 7 | [lyogavin/airllm](https://github.com/lyogavin/airllm) | Jupyter Notebook | 37,618 | 879 |
| 8 | [microsoft/BitNet](https://github.com/microsoft/BitNet) | C++ | 40,944 | 97 |
| 9 | [Alishahryar1/free-claude-code](https://github.com/Alishahryar1/free-claude-code) | Python | 59,247 | 626 |

第10项：官方本次返回未提供。顺序显然不按stars today降序，例如第3的246低于第4的4,095，因此不能自行按数字重排。

## 1. [morluto/rea](https://github.com/morluto/rea)

### ① 元信息与固定版本
- 本轮官方日榜：第1，TypeScript，163,731 stars，页面显示今日增加45,327。仅沿用本轮同一榜单快照，未混入之后仓库API的计数
- REA（Reverse Engineer Anything），npm包 rea-agents，MIT，默认分支 main。固定完整SHA：[a2d8b94dd50dab8d966239dd63ab84718aa8b4b4](https://github.com/morluto/rea/commit/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4)，提交于2026-10-13 02:51:14 UTC
- [依赖清单](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/package.json)仍为6.4.0；最新正式发布仍是10月11日03:58 UTC的 [rea-agents-6.4.0](https://github.com/morluto/rea/releases/tag/rea-agents-6.4.0)。下述10月13日 main 新功能不能直接等同于npm已发布功能
- 相对昨日固定SHA 2ff850de68dc9b05c6faf2bbfd26d56bc2d5d27c，[compare](https://github.com/morluto/rea/compare/2ff850de68dc9b05c6faf2bbfd26d56bc2d5d27c...a2d8b94dd50dab8d966239dd63ab84718aa8b4b4)显示 ahead 160、behind 0；两页取得全部160条提交元数据，文件列表达到300项上限。因此能确认版本前进160次提交，不能宣称审完全部差异

### ② 它解决谁的问题
REA面向需要调查应用行为、打包后JavaScript/Electron程序、移动应用和原生二进制的开发者与编码Agent。它把引擎调用、静态分析和运行观察统一为CLI/MCP操作，并把结果与来源、身份和限制一起交给模型。对“已有软件的这个功能究竟如何工作”尤其有用，但应只分析有权研究的目标；底层引擎和平台支持决定实际能力。[项目定位](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/README.md)

### ③ 架构与真实数据流
1. **请求、记录、交付分层。** main先快照环境、解析配置、创建BinarySession，再启动stdio MCP；通用handler把MCP取消信号传入operation，成功结果先记录Evidence再交付，失败时也会保留带evidence_id的部分观察。交付层检查序列化预算，过大时返回可恢复错误及已确认保留的Evidence引用，而非悄悄把结果截成“完整答案”。[启动链](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/main.ts#L50-L89)；[执行与记录](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/server/contractToolHandler.ts#L59-L90)；[预算与恢复](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/server/toolResult.ts#L155-L204)
2. **今日新增SAZ是一条离线证据管线。** HistoricalCaptureDecoder先读取稳定文件快照并记录SHA-256，在私有目录写请求，启动受限解码进程，校验输出schema和解码器身份；WebNetworkCaptureService再验证文件/格式/原始序号未被适配器改变，最后进行记录选择和显式敏感值处理。SazCapture直接读ZIP中的 raw/<id>_c.txt、_s.txt、_m.xml 等成员，不启动Fiddler、不转HAR；重复成员、加密归档、链接和超出展开预算的输入会被拒绝。[快照、进程与输出校验](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/browser/history/HistoricalCaptureDecoder.ts#L71-L217)；[来源约束与选择](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/application/WebNetworkCaptureService.ts#L69-L124)；[SAZ解码](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/browser/history/SazCapture.ts#L16-L173)
3. **今日新增Android摘要保留原始事实。** detail=summary先检查是否有保留能力，再照常向分析服务提交完整path请求；成功后才创建摘要。投影只移除manifest长文本，保留声明、partial/null及父Evidence身份；后续manifest页面按UTF-16 code unit读取已保留文本，明确“页面耗尽”不能证明原始manifest完整，也不能拿引擎JAR的hash冒充APK身份。[摘要入口](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/application/android/AndroidPackageInspection.ts#L15-L42)；[摘要与分页](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/domain/analysisView/androidPackageView.ts#L69-L134)

### ④ 亮点、已确认增量与边界
- 与昨日比较，本轮实际核读了 [SAZ提交](https://github.com/morluto/rea/commit/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4)和 [Android摘要提交](https://github.com/morluto/rea/commit/f254f5ac2b804b353a711264bb178f43fdf07867)的关键diff及当前实现，二者均是今日新加入的实现，不是重复介绍昨日功能
- SAZ保留“记录原样”这一点值得借鉴：HTTP body不自动解压或去chunk；缺失成员为null，与空body分开；WebSocket/gRPC成员保留不透明字节，不冒称已经理解协议。序号按ZIP中首个session成员出现顺序生成，并非时间顺序。[明确支持边界](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/browser/history/NodeCaptureAdapter.ts#L16-L41)；[HTTP字节处理](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/browser/history/SazHttp.ts#L3-L70)
- 资源限制是真实分支：输入32 MiB、回复96 MiB、嵌套64层、单次owned command 30秒；SAZ在没有可强制执行的解码器内存限制时拒绝运行。所有记录先解码再选择，不能靠“只选第0条”忽略后面的坏数据。上述行为可从源码和拒绝坏HTTP/XML、DTD、CRC错误等测试用例核对；本轮未运行这些测试。[预算与限制](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/browser/history/HistoricalCaptureDecoder.ts#L201-L215)；[异常输入测试](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/tests/boundary/browser/sazWebCapture.test.ts#L427-L497)
- 提交说明报告验证356个真实录制session，并明确当前Fiddler Everywhere GUI及非Linux生产流程未验证；Android提交报告某组回复从119,527缩至8,659字节，同时明确未证明模型token或时间收益。它们都是作者实验记录，不是本轮复现成绩
- 近期原始 [issue #2454](https://github.com/morluto/rea/issues/2454)仍开放，报告Harmony opener/status的MCP输出契约与实际格式不一致、native summary引导不符等12项问题。本轮未逐项复现，不把“有统一MCP”写成所有入口已完全一致
- 主干为Node/TypeScript，Node要求 ^22.19.0、^24.11.0 或 >=26；固定依赖含MCP server/client 2.3.1、Zod 4.4.3、Babel 8.0.4、Playwright-core 1.58.2、zip.js与xmldom。桥接层还有Python/Java/原生实现，不能仅凭TS语言标签判断安装成本。[运行与依赖](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/package.json)

### ⑤ 今日热度：事实与推测分开
**已确认事实：** 官方快照第1、今日增星45,327；默认分支短期活跃，且本轮读取到SAZ、Android摘要等新提交。6.4.0发布于10月11日，不是今天刚发布的新版本。

**解释性推测：** 用一个MCP把应用观察、逆向分析和可追溯证据交给编码Agent，可能契合开发者当前兴趣；可读抓包和更小的按需结果也可能增加实用性。但没有传播链、流量来源或star归因证据，不能认定这些提交造成今日暴涨。未找到足够的直接证据解释今天为何上榜。

### ⑥ 对AI、RAG与全栈项目的具体复用建议
- **Agent/MCP：** 优先借鉴“先记录完整结果，再按预算交付可恢复引用”的协议。把取消、部分观察、保留失败和传输失败拆开，有助于避免Agent把没读完当作不存在
- **RAG：** 可把Evidence作为有版本、有来源、带unknown的文档单元；摘要只做检索入口，正文仍可按父引用回读。它提供的是证据建模思路，本轮未见通用向量检索能力的验证
- **React/Next.js/Node：** 调查打包后JS、Electron和HTTP交互时可评估CLI/MCP；自己做分析台时可借鉴summary→detail分页，但没有可直接搬来的React组件。抓包记录中的URL不要自动请求，否则会把历史分析变成真实网络动作
- **Python/Django：** 在Django后台导入抓包/分析结果，可借鉴稳定快照、摘要hash、解码子进程、资源上限和结果schema；不要把REA整个Node依赖树当作Python库直接嵌入
- **读取覆盖：** 获取完整递归目录3531项（truncated=false），实读README定位/能力、package依赖、入口/handler/交付实现；深读SAZ快照服务、ZIP/HTTP/XML解析、内存门禁及Android摘要/投影；EvidenceLedger选读记录与原子导入段，测试选读异常输入和partial/Unicode/保留能力段。另读最近5个commit、3个release记录、相关commit关键diff、compare两页元数据（非逐条完整diff）、issue #2454。未全仓审计、安装、执行仓库代码或复现性能

## 2. [bilawalsidhu/gods-eye-view](https://github.com/bilawalsidhu/gods-eye-view)

### ① 元信息与固定版本

- 官方榜单快照：第 2，53,849 stars，今日 +1,895，语言 JavaScript；默认分支 main
- 本轮固定 SHA：[8b8ccc9a81379e8b40d4be67610570ee5b159512](https://github.com/bilawalsidhu/gods-eye-view/commit/8b8ccc9a81379e8b40d4be67610570ee5b159512)，提交时间 2026-10-12 14:15:32 UTC
- 与昨日 591f299d… 的真实 compare 是 ahead 6，但这包含分支同步/合并；净变化仅 4 文件：TLE parser、回归测试、两份说明。不能写成六项新功能。[完整比较](https://github.com/bilawalsidhu/gods-eye-view/compare/591f299d11f38a612629a274463196d57ae3862e...8b8ccc9a81379e8b40d4be67610570ee5b159512)
- package 仍为 0.2.1，最近 GitHub Release 仍是 10 月 3 日的 [v0.2.1](https://github.com/bilawalsidhu/gods-eye-view/releases/tag/v0.2.1)。源码 MIT，但内置/在线第三方数据和 3D 模型另有许可，部分海缆、事件影像和衍生坐标不允许直接按 MIT 商用。[实际 LICENSE](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/LICENSE)

### ② 它解决什么问题、给谁用

它把飞机、船舶、卫星、地震、天气与公开摄像头等分散数据放进同一个三维地球，允许使用者从全球态势下钻到单个目标，并让 Agent 查询数据、定位和改变视图。适合公开数据分析、地理可视化、教学演示，以及想做空间上下文界面的开发者。产品的“间谍卫星”是视觉比喻：README 明示车流是沿真实道路的模拟，摄像头姿态和火箭轨迹有估计成分，FLIR 等风格也不意味着真实热成像观测。[产品范围](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/README.md)

### ③ 真实架构与数据、控制流

依赖是原生 JavaScript ES modules、Vite、Cesium、Node，以及 satellite.js、hls.js、Mapillary 等；package 没有 React。运行要求 Node >=24.14 且 <25，或 >=26 且 <27。[依赖与导出边界](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/package.json)

1. 卫星链路是 source.readGroup → 文本 TLE 解析 → satellite.js 的 twoline2satrec → NORAD 去重 → 轨道推算 → Cesium PointPrimitive。多个星群并发读；全部失败时保留旧目录、不刷新 lastUpdate，部分失败则重建可用部分并保留降级提示。AbortController 和更新 epoch 负责撤销、跟踪恢复及过期结果管理。[ingestion.js](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/layers/satellites/ingestion.js#L13-L190)
2. 本次真正新增的是解析器恢复能力：原先每次固定跨三行，某个卫星少一行会令后续分组全部错位；现在失败时只前进一行，遇到相邻的 `1 ` / `2 ` 轨道行才接受该组并再前进两行。新增测试分别删掉第二组的 line 1、line 2，要求其余七组仍被保留；图层 orbits 和 Agent 的 space queries 共用这个 parser，所以不是只修显示层。[解析器](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/sources/tle.js#L1-L22) · [回归用例](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/tools/queries/space.test.mjs#L35-L56) · [图层共用入口](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/layers/satellites/orbits.js#L1-L44)
3. MCP 是已有可执行服务：composeCatalog 按依赖筛选工具、校验参数，经统一拦截器执行；本地 server 把服务的相对 `/api` 请求接到运行中的应用。`next_satellite_pass` 再从目录匹配名称/NORAD，计算升起、最高点、落下和可见性，同时把 stale 与建议 view 带回。协议层将结果同时写入摘要、JSON 文本和 structuredContent，并把已知 ToolError 与隐藏内部细节的未知错误分开。[工具目录](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/tools/catalog.js#L150-L227) · [过境查询](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/tools/queries/space.js#L190-L254) · [MCP 实现](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/tools/mcp/protocol.js#L65-L153)

### ④ 技术亮点与实际边界

- 本次改动小而具体：恢复坏记录之后的同步，而非整份数据有一条坏行就丢掉尾部。它仍是带名称的三行 TLE parser，靠轨道行前缀识别，不是完整 checksum、两行 catalog number 一致性或轨道数据真实性验证器；后续卫星库解析和卫星图层的 satrec.error 检查仍有自己的职责
- 数据状态值得借鉴：卫星数据保留 stale；船舶的“权威空覆盖”必须同时满足 rawRowCount=0、complete=true、freshness=current、传输健康、有有效 lastMessageAt。空数组、请求失败、旧缓存不是同一件事。这套船舶机制是昨日已存在的代码，并非本次新功能。[空覆盖条件](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/layers/vessels/queries.js#L115-L148)
- MCP 面板 key 不能充当用户认证：server 源码明确能读取面板页的客户端也能拿到 key。直接用于企业多租户产品仍需要独立身份、权限与数据许可设计。[实际边界说明](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/server/mcp/server.js#L24-L54)
- **更新昨日未复现的风险提示：** 分享链接 360° 导致卡住的 issue #1068 已被报告者撤回。他确认是隐藏测试浏览器被限帧造成的假象，并在可见 Chrome、未修改的昨日 SHA 上验证链接正常；不能继续把它列为应用缺陷，也不能说今日代码修好了它。[作者撤回原评](https://github.com/bilawalsidhu/gods-eye-view/issues/1068#issuecomment-6117033123)

### ⑤ 今日热度：事实与猜测分开

事实：官方榜第 2、今日 +1,895；10 月 12 日合入 [PR #936](https://github.com/bilawalsidhu/gods-eye-view/pull/936) 的 TLE 恢复修复，PR 作者记录了单测、构建和浏览器跟踪验证，但本轮没有重跑。README 继续展示实时地球、视觉演示和 Agent 接入，这些大多早已存在；本次没有新 Release。

推测：直观的三维演示和自然语言操控可能有助于传播。但没有流量来源、推广活动或作者直接归因证据，无法证明今日 star 增长是这次 parser 修复或某一项功能带来的。

### ⑥ 对 AI / Agents / RAG / MCP 与全栈的具体复用建议

- Agent/MCP：优先精读“查询结果同时包含结构化事实、数据状态与可显示 view”的接口；将查询和视图操作分开，使文本客户端和可视化客户端复用一个目录。已有 MCP 实现可研究，不必凭空再造协议层
- RAG：可把卫星坏记录重同步与船舶空覆盖规则迁移到抓取/切片/检索流水线；为“源不可用、解析失败、截断、过时、确认零命中”定义独立状态，避免把不完整检索包装成否定事实
- React/Next.js：可借鉴 source、layer、rendering 的分层，再由 React 管页面而让 Cesium 控制高频渲染；项目本身不是 React/Next SDK，迁移时需要处理浏览器专用初始化及销毁
- Node/Python/Django：Node 可复用/参考其纯工具与服务适配层；Python/Django 侧更适合迁移响应契约、超时/撤销和供应商隔离思路，而非照搬 WebGL。商业集成先逐源核对地图、海缆和影像许可

读取覆盖与限制：固定 SHA 的递归树 1,913 项、未截断；取得 15 个文件，核读 README/package/LICENSE、TLE 解析与测试、卫星 source/ingestion/orbits/rendering、space 查询、船舶空覆盖、MCP server/services/protocol 和 catalog，长文件重点读相关路径。另读最近 5 commits、3 releases、最新讨论列表、真实 compare、PR #936、issue #1068 与撤回评论。未运行仓库脚本、测试、浏览器或任何外部代码；PR 测试数字属于作者报告。

## 3. [mksglu/context-mode](https://github.com/mksglu/context-mode)

### ① 元信息与固定版本
- 本轮官方日榜：第3，TypeScript，27,380 stars，页面显示今日增加246
- 默认分支 main；固定完整SHA：[1a1bed139906ecc048233583bb2fd29290603b7a](https://github.com/mksglu/context-mode/commit/1a1bed139906ecc048233583bb2fd29290603b7a)，提交于2026-10-12 18:05:17 UTC，内容是安装统计更新
- [package.json](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/package.json)版本1.0.169，Node >=22.5.0；主要依赖MCP SDK ^1.26.0、better-sqlite3 ^12.6.2、Zod ^3.25.0和HTML→Markdown转换组件
- 许可证为 [Elastic License 2.0](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/LICENSE)，并非MIT/Apache式宽松许可；条款明确限制向第三方提供可访问实质功能的托管/管理服务。昨天可见8项中没有它，不能据此断言它首次上榜

### ② 它解决谁的问题
它面向持续读取日志、测试输出、文档和MCP工具结果的编码Agent：原始数据很大，直接塞进对话既挤占窗口，压缩后又容易丢掉工作状态。它让代码先在子进程里计算、筛选，再把完整输出索引到本地SQLite，只向模型返回小块结果与后续检索入口；另用hook记录会话事件以支持恢复。适合长任务和大量工具输出，但效果依赖客户端hook支持、路由是否真的生效以及查询是否命中。[定位与接入](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/README.md)

### ③ 架构与真实数据流
1. **执行后按需检索。** ctx_execute先做deny-policy检查，再通过PolyglotExecutor启动相应语言子进程；普通成功输出在携带intent且超过5,000字节时进入intentSearch，先持久索引再返回匹配标题/120字符预览；没有intent但超过102,400字节也转为索引引用。它没有在这一步用另一个LLM概括全部原文。异常与超时有不同分支，超时的部分输出会直接带说明返回，不能把所有返回都假设成同样的压缩路径。[执行与输出分流](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/server.ts#L1743-L1949)；[检索入口生成](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/server.ts#L1979-L2035)
2. **检索是本地词法混合。** ContentStore建porter/unicode61与trigram两套FTS5索引，各做BM25检索，再以K=60的RRF融合；随后按标题、词距和短语邻接重排，没有结果才走拼写模糊纠正。文件来源记录SHA-256并在搜索前检查过期。这里的“混合”指两类词法索引，所读链路未调用embedding服务。[索引表](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/store.ts#L475-L497)；[融合、重排和fallback](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/store.ts#L1242-L1404)
3. **会话恢复是索引和引用，不只是一段摘要。** PreCompact读取SessionDB事件并保存resume snapshot；Claude Code的SessionStart在compact时写可索引事件文件、注入检索指引及部分行为状态，在resume时优先当前session事件，缺失才领取未消费snapshot。统一搜索默认只查ContentStore；timeline模式才加入SessionDB和auto-memory并按时间合并。[压缩前持久化](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/hooks/precompact.mjs#L34-L54)；[恢复实际分支](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/hooks/sessionstart.mjs#L186-L295)；[多来源检索](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/search/unified.ts#L91-L175)

### ④ 真实亮点与必须知道的边界
- **今天最重要的源码发现是“sandbox”措辞与真实写入行为不一致。** 普通执行分支实际使用 cwdOverride ?? projectRoot，JS/Python等代码可在项目工作目录运行；只有Rust提前进入临时目录compile-and-run分支。清理的是每次创建的临时目录，并不回滚项目目录写入。可是当前工具参数仍声称非shell在临时目录，路由提示甚至声称这些子进程写入不会持久到宿主文件系统。[真实工作目录与清理](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/executor.ts#L282-L318)；[过时cwd描述](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/server.ts#L1728-L1731)；[过时写入描述](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/hooks/routing-block.mjs#L42-L51)
- 这不是仅凭注释猜测：6月21日 [89f4e736](https://github.com/mksglu/context-mode/commit/89f4e7363080ed2d72ff530c577cdd872dfbfe1b)已改变普通运行分支cwd；[issue #788在10月12日的跟进](https://github.com/mksglu/context-mode/issues/788#issuecomment-6127025076)报告macOS/Claude Code的JS相对写入在宿主持续存在，并限定自己的实测范围。当前测试源码也明确要求Python看到项目根并尊重cwd override。作者/用户实测与本轮静态验证分开，不能说我们重现了写入。[cwd回归测试](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/tests/executor/win-sandbox-782-788.test.ts#L79-L133)
- 子进程会继承大部分父环境，仅过滤一组危险变量；有stdout+stderr默认100 MiB上限以及显式timeout，但未传timeout时不设置自有计时器。文件入口有路径/符号链接约束，项目根未知时边界检查明确fail-open。这些有用防护不能替代操作系统级隔离，也不适合直接执行不可信外来代码。[进程、计时和输出上限](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/executor.ts#L409-L568)；[环境继承](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/executor.ts#L573-L694)；[路径边界](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/security.ts#L662-L783)
- README的“98% reduction”是项目给出的情景结果；它不能保证所有任务都有相同token/费用收益。最新 [v1.0.169 release](https://github.com/mksglu/context-mode/releases/tag/v1.0.169)还专门修正了多会话节省展示、retrieval bytes与累计任务计费口径。统计指标本身需要验证
- 文本与实现还存在维护漂移：PreCompact头注释称snapshot小于2KB，而实际builder保留maxBytes参数却忽略它，并组装所有非空分类。若复用恢复机制，应按实际代码另设可测的上下文预算，不能照注释宣传。[旧注释](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/hooks/precompact.mjs#L1-L7)；[实际配置与构造](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/session/snapshot.ts#L29-L33)；[组装逻辑](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/session/snapshot.ts#L463-L576)

### ⑤ 今日热度：事实与推测分开
**已确认事实：** 官方快照第3、今日增星246；最新5个commit都是安装统计更新；最近release为6月29日的v1.0.169，并没有读取到10月13日新发版。issue #788昨日的新评论属于使用反馈，不能把“issue近日更新”误写为近日完成修复。

**解释性推测：** 本地全文检索、减少重复工具输出和会话恢复，可能满足AI编码的持续痛点；多客户端接入也可能扩大受众。这不构成今天增星的因果证据，历史HN徽章与README用户品牌墙也不能证明今日传播。未找到足够的直接证据解释今天为何上榜。

### ⑥ 对AI、RAG与全栈项目的具体复用建议
- **Agent/MCP：** 借鉴“计算结果小回传、原始输出可回查”的工具契约。接入前校对真实cwd、网络/文件写权限以及hook文字，让模型获知真实副作用；不要把sandbox一词当作隔离承诺
- **RAG：** 可以独立借鉴FTS5双索引、RRF、代码标题加权、检索后按项目/session过滤的思路，适合日志/源码/任务事件等精确词匹配。要评测同义改写、中文切词、召回遗漏与跨项目隔离，不能从英语示例外推
- **React/Next.js/Node：** Node侧可参考“先索引、后返回引用”接口，React/Next.js侧做来源、摘要和全文展开。没有现成React UI复用结论；若计划托管成SaaS，先核对ELv2限制
- **Python/Django：** 在后台任务里做筛选/聚合，再让Django返回分页片段和来源ID；可用SQLite FTS5移植检索设计。执行器应使用独立受限环境，明确挂载和写入策略，而非直接复制此子进程封装用于不可信代码
- **读取覆盖：** 目录714项完整（truncated=false）；README读定位/接入段，完整读依赖与许可证；核心大文件按执行器、输出分流、FTS5/RRF/模糊检索、路径边界、会话恢复函数选读，完整读统一搜索及对应cwd测试。另读最近5次commit、executor最近5次路径提交、3个release、issue #788与全部2条评论。未逐个验证17类客户端、未测节省率、未运行仓库代码

## 4. [storytold/artcraft](https://github.com/storytold/artcraft)

### ① 元信息与固定版本

- 官方榜单快照：第 4，22,412 stars，今日 +4,095，语言 Rust；默认分支 main
- 固定 SHA：[d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373](https://github.com/storytold/artcraft/commit/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373)，2026-10-11 13:47:59 UTC；与昨日相同。实际 compare 返回 identical、ahead 0、0 个变更文件，**没有本次代码增量**。[比较结果](https://github.com/storytold/artcraft/compare/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373...d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373)
- 源码为 MIT OR Apache-2.0 双许可；GitHub API 单项显示 Apache-2.0 不能覆盖 README/NOTICE 的双许可声明。商标和一批第三方声音、图像、天空盒、动作素材被 NOTICE 明确排除，整仓资产不能一概按双许可分发。[NOTICE](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/NOTICE)
- 最近 Release 仍是 9 月 26 日 [artcraft-v0.41.0](https://github.com/storytold/artcraft/releases/tag/artcraft-v0.41.0)；它早于 10 月的 native 客户端与 provider 提交，不能把 main 的能力直接写成该安装包已具备的能力

### ② 它解决什么问题、给谁用

ArtCraft 面向需要控制构图、参考素材、角色、镜头和生成结果的艺术家、设计师与视频创作者，把编辑界面、模型选择、多供应商提交及素材库连接起来。它缓解的是在多个模型网站间反复上传、下载、整理素材的工作流碎片化。它是生成服务的客户端与创作工具集合，不是基础模型或本地推理引擎；新 native 客户端也没有把旧产品的所有编辑工具完整迁移。[产品范围](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/README.md) · [native 范围](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/README.md)

### ③ 真实架构与数据、控制流

这是两条并行 UI：旧 frontend 是 React 18.3.1、Three.js、Konva、Zustand/Signals 的 Nx/Vite 工作区，加 Rust/Tauri；新 artcraft-native 是 egui/eframe 0.36、Tokio、reqwest、rodio。根 Cargo 的 default-members 仍指向旧 Tauri 应用。native 主 UI 不依赖 JS/Tauri，但 Cargo 仍引入 wry 处理 Midjourney 登录，不能宣传整个程序绝无 WebView。[前端依赖](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/frontend/package.json) · [native 依赖](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/Cargo.toml)

1. 图片页按模型维护 provider 选择，Provider::resolve 过滤不支持的组合，adapt 再调整可选参数。当前 native picker 的 fal 入口只覆盖 Flux 1 Dev/Schnell、Nano Banana 2/Pro；直接 Midjourney 固定四张、无参考图/分辨率/质量选项。页面验证后，ArtCraft 走 omni_gen API，其他 provider 走独立提交器，后台事件返回 UI。[页面分流](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/pages/create_image.rs#L206-L251) · [能力适配](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/mod.rs#L42-L84)
2. submit 将页面 fields 转为共享 router 的 GenerateImageRequestBuilder，再向用户的 Midjourney 账号或 fal key 提交。Midjourney 的 ArtCraft prompt 记录必须先创建成功；fal 建 prompt 失败只告警、仍允许生成，这是实际一致性差别。返回 provider job id 后才创建/保存本地任务，附带 batch token、逐结果 upload token 和已入库 media token。[提交路径](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/submit.rs#L55-L145) · [后端保存入口](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/mod.rs#L446-L465)
3. Worker 通过 fal status/response URL，或 Midjourney websocket + 15 秒 feed 兜底发现完成；每轮处理完再睡两秒，不是保证两秒轮询完所有任务。结果按序下载、上传 ArtCraft 素材库；上传前保存该结果的幂等 token，上传后记录 media token，全部成功才删除任务并通知 UI。重启后从本地 JSON 恢复进度。[任务存储](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/jobs.rs) · [完成与归档](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/worker.rs#L94-L228)

### ④ 技术亮点与实际边界

- 值得研究的不是供应商菜单长度，而是“供应商完成”和“本方入库完成”分成两个阶段；每个结果独立 checkpoint，并用 websocket 降低等待、轮询补偿漏事件。这些都是昨日同一 SHA 已存在的机制
- **本次进一步核读的边界，不是今日新增 bug：** JobStore 用临时文件 persist 减少截断风险，但 mutate 的存盘错误只 warn，并不返回失败；submit 请求先发生，任务随后才存盘。故磁盘写失败或特定崩溃窗口仍可能丢恢复记录，不能把这套方案称为无条件 exactly-once。源码也未给直接 provider 的 request_builder 设置 idempotency_token。[存储错误分支](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/jobs.rs#L78-L99) · [直接 provider 请求字段](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/submit.rs#L130-L141)
- “使用自己的 provider 账号”不代表素材只在该 provider：worker 最终会下载结果、上传 ArtCraft library，且没有 ArtCraft 登录时不继续完成入库。产品化时需要把这个数据流与费用边界说清楚。[worker 登录与上传分支](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/worker.rs#L101-L228)
- 近期 [issue #2199](https://github.com/storytold/artcraft/issues/2199) 反映 Windows 安装目录/手动改路径后的使用问题；当前是用户报告与讨论，本轮没有重现，也没有把评论中的 UAC 推测当作维护者设计说明。新原生客户端、旧安装包、操作系统部署体验需要分别验证

### ⑤ 今日热度：事实与猜测分开

事实：榜单第 4、今日 +4,095，星数增长很快但当前 SHA 与昨日完全相同。可确认的近期事件是 10 月 10 日重新许可、加入原生 Rust UI 与音频/视频体验，10 月 11 日加入直接 provider 选择；这些是前几天的开发活动，不是今天又新增了一遍。[固定版本提交历史](https://github.com/storytold/artcraft/commits/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373)

推测：视觉演示、宽松源码许可、跨模型创作需求可能继续吸引关注，但本轮没有核到明确的当日推广来源或作者归因，不能证明增长由原生化或重许可单独驱动。

### ⑥ 对 AI / Agents / RAG / MCP 与全栈的具体复用建议

- Agent、多模态产品：将 generate、poll、archive 三步设成明确状态，给每张结果固定幂等 key；进一步用数据库事务/可靠 outbox 解决“远端已接受，本地没记下”的窗口。这里是改进建议，不能写成 ArtCraft 现已保证
- React/Next.js：旧 React 前端与 Rust API 客户端可用来学习复杂生成 UI 的能力表、参考素材状态和事件边界；Web 产品可保留这些契约，把 Tauri/egui 部分替换为浏览器与服务端队列
- Node/Python/Django：适合将 provider adapter、持久任务、超时/重试、逐文件归档迁移到 Node worker 或 Django/Celery。处理生成服务计费前，应区分业务失败、重试安全性和真实供应商价格，不把 UI 的零额外 ArtCraft credits 当成外部服务免费
- RAG/MCP：不是检索引擎，本轮未验证到可直接使用的 MCP server。可围绕素材库检索、生成任务状态与归档做 MCP 工具，或把 prompt、provider、model、素材来源存为多模态 RAG provenance；这些是二次集成方向

读取覆盖与限制：固定 SHA 的完整递归树 7,307 项、未截断；取得 12 个文件，核读 README、NOTICE、根 Cargo、frontend package、native README/Cargo、图片页、backend 生成入口、providers 的 mod/submit/jobs/worker。另读最近 5 commits、3 releases、最新讨论列表、同 SHA compare、issue #2199 与评论。长文件只对相关链路重点阅读，没有审计全仓；没有编译、运行测试、登录账号、上传素材或付费生成。

## 5. [open-webui/open-webui](https://github.com/open-webui/open-webui)

### ① 元信息与固定版本

- 官方日榜第5；语言 Python；累计 **155,127 stars**；页面显示 **157 stars today**。这些值只取本期同一张官方榜单
- 默认分支 main；本轮固定 [f8ae8a6c328946dc62cd0712961a0632574581bf](https://github.com/open-webui/open-webui/commit/f8ae8a6c328946dc62cd0712961a0632574581bf)，提交于2026-10-10 21:10:07 UTC。最新正式 [v0.12.0](https://github.com/open-webui/open-webui/releases/tag/v0.12.0) 发布于10月10日21:13:24 UTC；不是今天发布
- 前端实际为 Svelte 5 / SvelteKit 2 / Vite，后端为 Python FastAPI；依赖指定 Python >=3.11、<3.13，FastAPI 0.136.3、MCP SDK 1.27.2、LangChain、SQLAlchemy、Chroma及多种向量库客户端。不是React/Next.js或Django工程：[package.json](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/package.json)、[pyproject.toml](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/pyproject.toml)
- 许可是仓库的 **Open WebUI License**，API标记NOASSERTION。当前许可包含品牌保留条件及有限例外，不能概括为MIT；做白标分发前应逐条核对，不在本报告作法律判断：[LICENSE](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/LICENSE)

### ② 它解决谁的问题

Open WebUI为个人、团队和自托管运维者提供统一的模型聊天、知识库、工具与协作界面，连接Ollama及OpenAI兼容端点。它的价值是把“模型请求”与权限、文件、检索、对话持久化、工具调用和交互状态接起来，减少自行搭建整套应用的工作。离线运行需要模型、依赖和数据源也满足离线条件；接入云模型或外部工具后，不能仅凭自托管就声称数据从不出网。[README](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/README.md)

### ③ 实际架构、数据流与控制流

1. **请求不是简单反向代理。** FastAPI的chat_completion先解析模型与可能的fallback，检查原模型及fallback访问权，再合并全局、模型、请求参数。内部process_chat调用process_chat_payload，允许工具审批导致paused状态，随后路由模型、处理流式/非流式响应，最后清理MCP会话及活动任务。chat.py再按direct/pipe/Ollama/OpenAI兼容路径分派；arena选择子模型后也有访问检查。[入口与权限](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/main.py#L1138-L1260)、[处理/清理](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/main.py#L1639-L1770)、[模型分派](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/chat.py#L148-L317)
2. **RAG从入库到召回保留元信息与权限边界。** save_docs_to_vector_db先按内容hash查重，可先按Markdown标题分组，再用字符/token/Transformers长度切块；每块记录embedding engine/model，批量生成向量后写入统一vector client。查询先尝试向量库原生hybrid，无法使用时退回BM25 + vector的加权集成，再rerank；用原文本hash去重，避免BM25增强文本与原文被当成两块。集合入口校验文件权限、用户memory归属、临时web-search所有者和知识库权限，非受管集合默认拒绝。[切分入库](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/routers/retrieval.py#L1366-L1557)、[hybrid与rerank](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/retrieval/utils.py#L414-L598)、[集合授权](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/retrieval/utils.py#L1281-L1349)
3. **MCP与长工具循环有自己的生命周期。** connect_mcp_server检查连接启用状态、用户权限和OAuth，再建立Streamable HTTP会话、分页读取tools并按配置过滤名称。MCPClient把structuredContent在必要时补进文本结果，序列化比较避免Python把true与1当作相同；elicitation校验schema/URL和答案，不解析远程schema引用。工具轮次间还会检查上下文压缩阈值，按assistant tool-call批次切边界，保留call/result和随后图像；普通聊天则以user轮次为边界。[工具连接](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/tools.py#L197-L262)、[MCP client](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/mcp/client.py)、[压缩边界与摘要](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/context_compaction.py#L335-L423)、[工具循环压缩](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/middleware.py#L6240-L6340)

### ④ 技术亮点、近期变化与边界

- 最有迁移价值的是“协议与任务状态一起管理”：MCP的AnyIO资源要在创建它的同一个async task中退出。源码专门避免用wait_for/shield包裹disconnect，因为这会新建task、破坏cancel-scope所有权；逐客户端清理避免一个失败阻断其余。它是实际异步资源约束，不是换个SDK名称就自然可靠
- v0.12.0的工具轮次压缩已在固定源码中存在，保留工具名和参数进入摘要。代价也明确：估算fallback是字符数/4、图片固定估算；生成摘要为空时使用截短文本fallback，异常则保持原上下文继续。因此它不能保证每次一定缩到模型窗口以内，中文、多模态和超大单批工具结果仍要测量：[context_compaction.py](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/context_compaction.py#L44-L130)
- 近期已合入的[67ff390c](https://github.com/open-webui/open-webui/commit/67ff390c1cfcb0b2137792e6bf94a923a8b77bd7)修复浏览器重启后OAuth转发/退出失联：OAuth session和ID-token cookie跟随登录有效期，MFA结束路径也设max_age。已读实际两文件diff；这是10月10日的修复，不是今日新增
- 原始[issue #32314](https://github.com/open-webui/open-webui/issues/32314)今日仍open，用户报告URL导入Skill后预览弹窗无法关闭，版本字段为dev。此报告能提示交互回归风险，不能直接当作本轮main已经复现的错误，更不能把尚在dev的修复算进已发布版本
- 原生hybrid失败会返回None并退回legacy；后者需要拉取集合文档构造BM25，大知识库的内存与延迟成本值得单独测。授权过滤设计可读，不等于完成全系统安全审计

### ⑤ 今日热度：事实与推测

事实：本期第5、页面今日+157；10月10日有v0.12.0发布，发行说明含Realtime语音、共享聊天回复、多文件Skill和工具循环压缩，且原始issue/PR活跃。主线最新提交仍是10月10日，不能说“今天刚发布新版本所以爆火”。

推测：自托管、多模型、RAG和Agent工作台合一可能持续吸引开发者；本轮没有流量来源或传播链证据，**暂无足够公开证据确认今天上榜的直接原因**。[发行说明](https://github.com/open-webui/open-webui/releases/tag/v0.12.0)

### ⑥ 对你的AI / Agent / RAG / 全栈开发价值

- **AI Agent / MCP：**优先学习MCP连接权限、令牌轮转、工具批次保留和异步清理；摘要压缩不应破坏tool_call_id配对，也不能悄悄把失败变成成功
- **RAG / Python / Django：**可迁移入库元信息、受管集合授权与hybrid fallback设计。Django接入时应复用契约思路、独立适配ORM/async边界，不直接搬FastAPI request.app全局状态
- **React / Next.js / Node：**它的UI是Svelte，适合参考对话状态、流式事件、审批暂停/恢复与知识引用接口；复用“整个前端组件”会有框架迁移成本。Node BFF应保留上游错误、取消和用户身份，不只透传文本
- **选型建议：**作为自托管完整应用候选，也作为大型Python Agent应用教材；先核对许可证、外部数据流、工具权限和自己的检索集合规模，再决定二次开发范围

读取覆盖：取得5402项完整递归树（truncated=false）、README/许可/两个依赖清单；完整取得main.py、chat.py、middleware.py、tools.py、MCP client、context_compaction.py、retrieval utils/router、vector factory/async client及oauth.py，重点逐段核读上文函数和流程。另读最近5commit、最近3release、最近8issue/PR、#32314和OAuth完整diff。不是逐行审计全部大文件；未运行服务、导入数据、连模型/MCP或执行测试。

## 6. [cathrynlavery/diagram-design](https://github.com/cathrynlavery/diagram-design)

### ① 元信息与固定版本

- 官方榜单快照：第 6，52,791 stars，今日 +2,081，语言 HTML；默认分支 main，MIT
- 本轮固定 SHA：[41765070ace63009f23c741cedb0c81429710b4f](https://github.com/cathrynlavery/diagram-design/commit/41765070ace63009f23c741cedb0c81429710b4f)，2026-10-13 02:48:44 UTC
- 相比昨日 7a2e2217…，真实 compare 是 ahead 34、77 个净变更文件，包含多次版本号提交、导入/导出与验证修复，以及新增 service blueprint；不能把 34 commits 当成 34 项新能力。[完整比较](https://github.com/cathrynlavery/diagram-design/compare/7a2e22170ee838e859d8142ba825d83f8b6375e6...41765070ace63009f23c741cedb0c81429710b4f)
- plugin manifest 从 2.6.74 升到 2.6.90，Skill frontmatter 仍是 2.6；releases API 仍返回空列表，**没有对应 GitHub Release**。[manifest](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/.claude-plugin/plugin.json)
- 当前 README 和 SKILL 已写 **45 种**图，包含新增 service blueprint；仓库 description 仍写 44，README 一处画廊编号说明也未同步。本文按固定源码的 45 种范围说明，不沿用旧宣传计数。[README](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/README.md#L1-L10) · [类型表](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/SKILL.md#L83-L134)

### ② 它解决什么问题、给谁用

它让现有编码 Agent 按编辑设计规范把系统、流程和数据画成单文件 HTML+SVG，面向开发者、技术作者、顾问和需要交付成图的人。核心价值是稳定图型选择、视觉层次、可访问性和交付校验，而不是另造一个拖拽画布。Skill 文档决定 Agent 应如何理解和排版，Python 脚本负责结构提取、部分可机械检验的约束与导出；这两部分不能混称为自动布局引擎。[Skill 工作流](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/SKILL.md)

### ③ 真实架构与数据、控制流

基本路径是导入器提取结构 → 宿主 Agent 按规范选择图型和重排 → HTML 内嵌 SVG → self-check/仓库验证器 → SVG 或浏览器光栅化导出。静态 HTML 不要求 Node/React 构建；核心 self_check 使用 Python 标准库，PNG 示例另依赖 Playwright/Chromium，默认字体也可能访问 Google Fonts。[真实模板](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/assets/template.html) · [导出依赖与流程](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/references/export.md)

1. 新 service blueprint 不止多一张模板。SVG 用 data-layer、data-stage、data-name、data-role 声明层、阶段、动作与可见性分界线；独立验证器再读取实际 rect/line/text，验证层序、等宽等间距列、每阶段 customer/frontstage/backstage 完整性、文字与声明一致、最多一个 focal、最多六阶段，以及可见性线位置和至少 3:1 对比度。测试通过移动单元格、删 backstage 单元、交换层、隐藏分界线等反例防止“能画出来却说错关系”。[实际验证器](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/scripts/verify-service-blueprint.py#L630-L831) · [反例测试](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/scripts/test-verify-service-blueprint.py#L46-L143)
2. 最新 self_check 为 viewBox 增加几何边界检查。它提取 rect/line/circle/ellipse/polygon/polyline 的极值点，以及 text 的锚点，累计纯 translate 偏移；超出边缘 2 个 viewBox 单位才报告。原有无障碍、重复 ID、远程引用/CSS loader 和允许的规范动画脚本检查仍保留。这是随 Skill 一起安装的可执行检查器，不只是文档里的待办清单。[新增边界实现](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/scripts/self_check.py#L252-L407) · [越界判定](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/scripts/self_check.py#L541-L567)
3. 导出脚本选择实际 SVG，携带并限定页面 CSS 到新的 root ID，隔离 defs 引用，修正 HTML/XML 差异、RGBA/opacity，再做 XML well-formed 检查；当前处理了嵌套 SVG 图标、含双连字符注释等增量。Mermaid 导入先有界读取，再以 utf-8-sig 解码，今天加入 BOM 接受能力。PNG 则在浏览器把视口和 SVG 尺寸对齐、释放祖先裁剪，并对字体加载超时保留告警。[SVG 导出流水线](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/scripts/export_svg.py#L939-L968) · [BOM 解码](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/scripts/mermaid_extract.py#L243-L258) · [PNG 示例](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/references/export.md#L311-L365)

### ④ 技术亮点、昨日结论更新与边界

- 设计主张开始拥有独立数据契约和反例，而不是只检查“文件能打开”。service blueprint 的声明、实际位置和可见性分界应一致，这类机制适合 Agent 生成的解释性产物
- **昨日两个具体缺口已修复：** draw.io 的 --out 写入已包在 OSError 捕获中，并以 cannot write/exit 2 失败；PNG 示例已把 int 改成 float，验证有限值及 1–4 范围。PR #398 自身 closed 且未直接 merge，不能据此推断修复未落地，当前源码和 compare 才是依据。[draw.io 输出分支](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/scripts/drawio_extract.py#L943-L948) · [当前 scale 处理](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/references/export.md#L315-L322)
- 新 viewBox 检查仍是保守静态近似：会跳过隐藏/裁剪、CSS 移动及复杂变换元素；没有把任意 path 曲线、文字字形完整包围盒、stroke/marker 外扩都求解出来。self_check 通过不等于任何 SVG 都没有裁切，也不是不可信 HTML 的安全沙箱。完整像素检查与无障碍/语义人工检查不能删掉
- **新的已知风险有源码支撑但未在本轮运行复现：** 10 月 13 日 02:52 的 [issue #420](https://github.com/cathrynlavery/diagram-design/issues/420) 报告属性选择器引号中的逗号/连续空白在 standalone SVG 导出后改变匹配。固定 SHA 的 scope_selector 仍直接 split(',')，CSS 提取仍用空白 split/join 规范化，静态核读支持这一风险；因此 XML 合法、CLI exit 0 不等于样式语义保持。[真实 CSS 处理](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/skills/diagram-design/scripts/export_svg.py#L461-L568)

### ⑤ 今日热度：事实与猜测分开

事实：官方榜第 6、今日 +2,081；相较昨日确实有 34 个提交和 77 个变更文件，新 service blueprint、导入/导出可靠性、viewBox 检测都有可核代码证据，不能沿用昨日“没有代码增量”的结论。最新 manifest 为 2.6.90，而非一个已发布的同名 GitHub Release。[固定提交历史](https://github.com/cathrynlavery/diagram-design/commits/41765070ace63009f23c741cedb0c81429710b4f)

推测：跨 Agent 使用、直观图形样例和即拿即用的 HTML/SVG 可能促进传播。但没有取得当日传播渠道或增长归因数据，本次大量修复与热度同时出现不构成因果证据。

### ⑥ 对 AI / Agents / RAG / MCP 与全栈的具体复用建议

- Agent 输出：值得采用“模型负责编辑判断、脚本负责机械不变量”的分工，并用能正常渲染但语义错误的反例测试检查器，避免只验证正例
- RAG：适合在答案后生成可追溯的架构/流程图；保留来源 ID、边方向与合并删减清单，分别验证信息真实性、拓扑保真和视觉约束。验证器不能替代检索证据，也不能让漂亮图形掩盖遗漏
- React/Next.js：单文件产物可以作为静态附件或受限预览；若转 React 组件，保留 title/desc、ID 隔离、主题与打印行为。不要在主应用里直接信任生成的任意脚本，尤其不要把静态检查器当正式隔离边界
- Node/Python/Django/MCP：可让 Python worker 做有界提取和校验，Web 后端保存产物及验证结果，MCP 暴露提取/验证/导出三个明确工具。该仓是 Agent Skill 加脚本，本轮未发现已实现 MCP server；新增协议封装、沙箱和队列是你自己的集成工作

读取覆盖与限制：固定 SHA 完整树 710 项、未截断；取得 16 个文件，重点核读 README、SKILL、manifest、CI、真实模板、Mermaid/draw.io 导入、self_check、export_svg、export 规范、service-blueprint 规范/验证器/反例，以及 self-check/export/doc-sync 测试相关段落。另读最近 5 commits、空 releases 列表、完整 compare、issues #401/#420 和 PR #398 等当前讨论。没有运行外部脚本或 Playwright，没有逐个渲染 45 种图，也没有把 CI 配置或作者声明当成本轮测试通过。

## 7. [lyogavin/airllm](https://github.com/lyogavin/airllm)

### ① 元信息与固定版本

- 官方第7；Jupyter Notebook；累计 **37,618 stars**；**879 stars today**
- main固定 [7bb8a8600937ff15b81016f286142bcdac7ee2d2](https://github.com/lyogavin/airllm/commit/7bb8a8600937ff15b81016f286142bcdac7ee2d2)，2026-10-12 06:31:49 UTC，提交内容为刷新star-history图片。相对昨日报告1c8d2630的[compare](https://github.com/lyogavin/airllm/compare/1c8d2630c9373a6d345febe8ef93e05c58bdfb21...7bb8a8600937ff15b81016f286142bcdac7ee2d2)为ahead 1、behind 0，只变更两张图片；**没有已确认算法或接口增量**
- 包和最新正式release仍为[4.0.0，9月5日](https://github.com/lyogavin/airllm/releases/tag/v4.0.0)；Apache-2.0。运行实现是Python/PyTorch，Notebook只是榜单语言标签；包在air_llm/airllm，setup依赖torch>=2.4、transformers>=4.49,<6、accelerate、safetensors等，模型特定依赖另有约束：[setup.py](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/setup.py)

### ② 它解决谁的问题

AirLLM让模型权重不必一次全部驻留GPU，适合显存小、磁盘和主存较充裕、能接受较长等待的本地实验者与研究者。它把磁盘→CPU→GPU权重流动嵌入模型执行，4.0还支持指定模型路径的流式LoRA训练。它解决容量限制，不自动解决响应速度、长上下文KV占用或多用户吞吐；“4GB运行大模型”不能直接等同于“4GB提供可交互生产服务”。[README](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/README.md)

### ③ 实际架构与数据流

1. **分派与切层。** AutoModel按config.architectures选特殊子类，其余使用通用AirLLMBaseModel；macOS有提前分支直接返回MLX Llama实现。utils根据checkpoint weight_map确定每个模块属于哪些分片，以最长模块前缀处理嵌套CPU常驻表；已有一模块一safetensors分片时可链接，减少重复磁盘副本。基类在meta device上创建真实Transformers模型，再组装embedding、decoder layers、norm、lm_head序列。[分派](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/auto_model.py)、[切分](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/utils.py#L528-L782)、[meta初始化](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/airllm_base.py#L335-L402)
2. **一次层执行的生命周期。** pre-hook取已预取的state_dict或同步加载当前层，将对应参数物化到运行设备，并由单线程executor预取下一层；post-hook把本层已搬入的tensor放回meta。若有expert streaming、量化器或CPU常驻参数，它只回收记录的参数，避免误删另一类生命周期。generate/forward委托底层Transformers；逐token解码仍反复经过权重搬运，并非模型永久留卡。[权重加载](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/airllm_base.py#L429-L457)、[hooks与委托](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/airllm_base.py#L850-L921)
3. **训练以重算换显存。** _StreamedModule.forward在no_grad下执行，保存CPU hidden；backward重新加载冻结层并带梯度重算，再驱逐权重，adapter参与优化。最终loss按词表块计算log-sum-exp/目标logit，反向再计算各块得到hidden梯度，避免完整token×vocab矩阵；测试源码有与常驻小模型loss/gradient对照，但不是本轮测试结果。[流式autograd](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/airllm_lora.py#L35-L76)、[train_step](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/airllm_lora.py#L329-L368)、[分块CE](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/chunked_ce.py)、[小张量测试](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/tests/test_streamed_lora.py)

### ④ 技术亮点、今天新发现与边界

- 亮点在于把“空模型、按层物化、下一层预取、选择性驱逐、常驻例外”做成明确状态。压缩与prefetch不能简单叠加：compression不为空时源码会关闭prefetch；所谓一层占显存仍不包含KV、激活和常驻模块等其他资源。[配置行为](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/airllm_base.py#L183-L212)
- **今日新增研究发现，不是今日引入回归：**load_records用utf-8读JSON/JSONL/TXT，没有剥离BOM。今日[PR #382](https://github.com/lyogavin/airllm/pull/382)提出改为utf-8-sig；已核实它仍open、merged=false，作者自报三格式回归验证，而本轮没有执行。固定main仍保留旧读取方式，不能写成“已修复Windows导出数据集”。[实际读取器](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/lora_data.py#L78-L118)
- 切分也有今天值得注意的工程边界：固定utils中的_last_shard_of对带连字符的第二段直接int转换；单文件checkpoint路径在layer循环中重新load_file/torch.load。[PR #380](https://github.com/lyogavin/airllm/pull/380)正提议一次预读和非数字文件名处理。这里只报告当前代码与提案的对应关系，未证明所有模型都受影响，也不把PR当作main已有功能
- [issue #374](https://github.com/lyogavin/airllm/issues/374)用户报告GPT-OSS 20B生成约120 tokens需30分钟，但硬件信息只有“1x GPU”；这是交互风险信号，不是通用benchmark。4.0的训练显存数字是作者自报、带特定模型/序列长度/显卡条件；本轮没有验证性能
- 模型配置读取含trust_remote_code=True，运行前需独立审核模型代码与revision。macOS先走MLX Llama分支、共享实例预取状态和autograd辅助类的暂存状态，也提醒部署者先验证模型匹配和并发假设；不要从示例推导多请求线程安全

### ⑤ 今日热度：事实与推测

事实：第7、今日+879，连续两份报告可见；最新5条默认分支提交均为星图更新，最新release仍9月5日。最近讨论集中在慢推理、模型/平台适配、切分恢复与训练数据格式，不是确认了一次今日新推理突破。

推测：低显存运行大模型的产品主张具有传播力，但本轮没有直接传播证据。**暂无足够公开证据确认今天增星的直接原因**。

### ⑥ 对AI / Agent / RAG / 全栈开发的价值

- **Python / 模型系统：**值得精读hooks和chunked CE，学习资源生命周期、重算及checkpoint结构；适合受控离线实验，不应先承诺在线延迟
- **Agent / RAG：**多轮调用会放大逐层搬运的成本。若作为离线总结/批处理后端，先固定模型、测首token/全程/质量/磁盘；它本身没有检索、向量库或工具权限层
- **React / Next.js / Node / Django：**另设Python worker和作业队列，UI展示下载、切分、推理阶段及取消状态。不要在Django请求线程或Node同步请求中等待长时生成；并发、恢复、磁盘清理应是应用自己的显式契约
- **MCP：**可在经过验证的受控本地服务上提供窄工具，但仓库不是MCP server，需自己处理超时、单模型并发与失败结果。最适合先学习内存分层，再决定是否集成

读取覆盖：完整117项目录树；当前SHA的README、setup.py、auto_model.py、airllm_base.py、utils.py、airllm_lora.py、chunked_ce.py、lora_data.py和test_streamed_lora.py；逐段核读分派、meta、权重hooks、切层、LoRA重算、CE和数据读取，测试只读相关断言。另读5commit、3release、8条近期issue/PR、#382完整PR元数据及昨日compare。未逐个模型子类/MLX审计，未下载权重、运行代码或复现训练/推理。

## 8. [microsoft/BitNet](https://github.com/microsoft/BitNet)

### ① 元信息与固定版本

- 官方第8；C++；累计 **40,944 stars**；**97 stars today**
- main固定 [0b341e582afbf9e1011f24744b554c96a3477eb5](https://github.com/microsoft/BitNet/commit/0b341e582afbf9e1011f24744b554c96a3477eb5)，最近提交是2026-07-27 05:52:05 UTC，把VibeASR.cpp消息加入README。GitHub releases接口返回空列表；README里的“1.0”和模型新闻不能当作本次读取发现了GitHub release
- MIT；核心C/C++、Python构建/转换脚本、可选CUDA目录。根CMake最低3.14；requirements覆盖Transformers、torch、NumPy等模型转换依赖。默认CPU入口run_inference.py调用llama-cli并传-ngl 0，GPU目录是另一条未在本轮深读的路径：[CMakeLists](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/CMakeLists.txt)、[依赖](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/requirements.txt)
- 必須同时固定子模块：3rdparty/llama.cpp指向isHuangXin/llama.cpp的[390c307752ab78fd8189f359d6954c9ba1be74af](https://github.com/isHuangXin/llama.cpp/tree/390c307752ab78fd8189f359d6954c9ba1be74af)。不是随便一份最新upstream llama.cpp：[.gitmodules](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/.gitmodules)

### ② 它解决谁的问题

BitNet为使用原生三值权重模型的边缘推理和模型系统开发者提供CPU低比特执行栈，把权重编码、GGUF转换、SIMD内核和模型计算图配套起来。它既有生成模型路径，也有0.6B/270M embedding模型转换与推理支持，后者直接贴近RAG。所谓1-bit/b1.58描述三值权重方案，实际I2_S存储使用2-bit编码并附尺度等信息；它不是把任意FP16模型无损压成1-bit的通用按钮。[README](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/README.md)、[embedding指南](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/docs/bitnet-embeddings-i2s-guide.md)

### ③ 实际架构与数据流

1. **入口→构建→模型文件→native推理。** setup_env.py的main按setup_gguf、gen_code、compile、prepare_model执行；可下载指定模型，生成/拷贝kernel配置，构建llama工具，再将HF权重转成GGUF。run_inference/server脚本只是参数适配层，真实执行交给llama-cli/llama-server。默认CMake关闭TL1/TL2选项，不能把所有默认执行都统称LUT查表路径。[setup](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/setup_env.py)、[CLI](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/run_inference.py)、[server入口](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/run_inference_server.py)
2. **embedding转换必须保留模型语义。** 专用converter建立HF→GGUF tensor映射，保留每个q/k/v/o/gate/up/down投影前的norm。I2_S路径用abs-mean缩放、round/clamp成{-1,0,1}，映射{0,1,2}，128权重打包成32字节并写尺度尾部；embedding和norm保留浮点。Gemma3原生RMSNorm需要w+1，BitLinear的*_norm_in不能做同样偏移。固定子模块qwen3.cpp确实在各投影前读取可选norm_in并插入RMSNorm，证明这不只是转换文档中的名字。[转换与打包](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/utils/convert-bitnet-embedding-to-gguf.py#L428-L635)、[真实计算图](https://github.com/isHuangXin/llama.cpp/blob/390c307752ab78fd8189f359d6954c9ba1be74af/src/models/qwen3.cpp#L86-L212)
3. **低比特内核与shape/硬件分支。** 根源码提供I2_S packing及向量点积、TL LUT适配，子模块ggml-cpu-i2s.c提供GEMV/GEMM。其AVX2 GEMM按4×4块计算，从2-bit权重解包并与I8激活累加；支持时使用VNNI，否则走maddubs/madd组合，余下行列另行处理。根gemm-config按x86/ARM及DOTPROD设置并行块大小；“低比特”仍是具体layout、内核和CPU指令集共同作用。[I2_S内核](https://github.com/isHuangXin/llama.cpp/blob/390c307752ab78fd8189f359d6954c9ba1be74af/ggml/src/ggml-cpu/ggml-cpu-i2s.c#L25-L185)、[根packing/点积](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/src/ggml-bitnet-mad.cpp#L51-L196)、[配置](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/include/gemm-config.h)

### ④ 技术亮点、今天新发现与边界

- 真正亮点是把模型的norm、tensor命名、量化尺度、packed layout和计算图配套，避免只保存更小的权重却执行了另一个模型。embedding converter专门区分Gemma原生norm和新增BitLinear norm，这比“参数位宽低”更值得RAG开发者读
- **今日源码核对发现一条安装路径不一致：**SUPPORTED_HF_MODELS列出了两个embedding模型，但main无条件先gen_code，而gen_code只接受几类生成模型名，其他走NotImplementedError；prepare_model的I2_S分支也仍调用通用convert-hf-to-gguf-bitnet.py，而不是已存在的embedding专用converter。今日[PR #673](https://github.com/microsoft/BitNet/pull/673)和[#677](https://github.com/microsoft/BitNet/pull/677)分别修这些入口问题，本轮确认均open、merged=false。可准确报告“固定源码中存在不一致、提案尚未合入”，不能声称已经修好或本轮安装失败复现
- 上述PR作者只声称小fixture/tokenizer测试，没有完整模型/CUDA验证，本轮同样未执行。选embedding路径应细读专用指南、固定子模块并做端到端数值验证，不能把SUPPORTED列表视为所有快捷安装路径都成功
- README模型性能数字属于作者测量，不是本报告复跑。CPU平台、线程数、batch、prefill/decode、量化和基线都影响结果；embedding指南中的last-token pooling/L2 normalization是模型使用约定，接到向量库前要验证query/document预处理一致
- 根树有96项，但llama子模块包含大量真正运行时代码；本轮进一步固定并读了Qwen3图、I2_S内核及构建链接，仍未覆盖完整llama tokenizer、采样器、所有架构、ARM分支或GPU代码，不能声称全引擎审计

### ⑤ 今日热度：事实与推测

事实：第8、今日+97；主线最新提交在7月27日，7月的embedding/VibeASR新闻仍在README。今日有一批修复PR，但尚未合入本轮main，没有今天新release的证据。

推测：CPU低比特推理和低成本embedding会持续吸引本地AI/RAG开发者；本期没有外部传播链或新增star来源可验证。**暂无足够公开证据解释今天上榜的直接原因**。

### ⑥ 对AI / Agent / RAG / 全栈开发的价值

- **RAG：**比只看生成速度更应关注embedding路径。可用固定语料比较检索召回、向量维度、归一化、吞吐和持久化体积；更换模型或预处理后需要重建/版本化索引，不能混在旧embedding空间
- **Agent / MCP：**适合研究低资源本地模型服务，但推理栈不等于Agent编排或权限系统。MCP包装应提供明确模型版本、任务类型和资源限制；不能把任意模型的function-calling能力归给引擎
- **Python / Django / Node：**Python脚本负责转换与调用，native server作为独立进程服务；业务API应固定模型与子模块SHA，管理进程、健康检查和取消。embedding API与文本生成API应分清，不能把小模型推理直接写进每个Web请求的启动流程
- **React / Next.js：**UI复用价值主要在可观测性：显示模型/量化/索引版本和测量结果；仓库不是组件库。建议先精读专用converter与子模块计算图，再做离线RAG实验

读取覆盖：完整根目录树和子模块递归树；README、两个构建文件、requirements、.gitmodules、setup、两个运行入口、LUT/MAD源码、两个头文件、embedding指南与converter、TL2生成器；重点核读前述入口/转换/打包/内核及源码边界。子模块实读qwen3.cpp、ggml-cpu-i2s.c和CMakeLists；另读5commit、空release列表、8条近期issue/PR及#673/#677完整PR状态。TL2生成器只读结构、未逐行验证生成的全部SIMD代码；未构建或跑模型、benchmark、CUDA与测试。

## 9. [Alishahryar1/free-claude-code](https://github.com/Alishahryar1/free-claude-code)

### ① 元信息与固定版本
- 本轮官方日榜：第9，Python，59,247 stars，页面显示今日增加626
- 默认分支 main；固定完整SHA：[4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b](https://github.com/Alishahryar1/free-claude-code/commit/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b)，提交于2026-10-12 17:09:36 UTC
- 最新release [v6.16.0](https://github.com/Alishahryar1/free-claude-code/releases/tag/v6.16.0)发布于10月12日17:10:02 UTC，新增fallback模型的API key编号选择；同日还有v6.15.0多key配置及v6.14.1推理策略修复
- GitHub仓库API许可证识别为NOASSERTION，但实际 [pyproject](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/pyproject.toml)写明AGPL-3.0-only，[LICENSE](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/LICENSE)为AGPL v3文本。Python要求精确为==3.14.7，不能只写“Python 3”；昨天可见8项没有它，不能判断是否首次上榜

### ② 它解决谁的问题
它是让现有编码客户端使用不同模型供应商的本地推理网关，适合希望统一模型选择、保留流式工具调用并配置故障切换的开发者。客户端访问本地Anthropic Messages或OpenAI Responses接口，再由它映射到实际provider/model，管理页面负责路由和凭据配置。所谓free主要来自可接入的免费额度或本地模型，实际可用性和成本由供应商决定；项目名称不保证免费获得官方Claude模型。[项目定位与额度说明](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/README.md)

### ③ 架构与真实数据流
1. **HTTP适配器与请求所用配置代际分开。** FastAPI工厂注入services，注册Admin、Code与推理router；/v1/messages和/v1/responses接到各自handler。每个请求先获取runtime lease，ModelRouter在这份settings快照上解析provider/model，provider resolver也绑定同一lease，流结束后才释放，避免管理界面改配置时进行中的请求突然切换客户端。原生Messages provider走专用透传契约，非原生路径才用标准化请求模型。[应用组合](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/api/app.py#L45-L56)；[请求代际和双入口](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/api/routes.py#L53-L207)；[租约](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/runtime/provider_manager.py#L86-L153)
2. **fallback的身份包含provider、model与key编号。** ModelRouter把每个fallback变成带独立reasoning preference的候选；ProviderRuntime以(provider_id, api_key_number)缓存客户端和构造任务，避免并发共享时误用别的key。AdmissionRegistry按provider共享rate/concurrency容量，又用实际key摘要区分恢复状态，所以调换key顺序不应把凭据故障状态错误继承给另一把key。当前这一设计可从最新提交diff与实际实现交叉核对。[目标与fallback构造](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/application/routing.py#L44-L69)；[按key缓存](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/providers/runtime/runtime.py#L62-L114)；[共享容量、独立恢复](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/providers/admission_registry.py#L14-L52)
3. **流式恢复不是见错就重放整个请求。** ProviderExecutor按顺序消费候选，带进度截止时间并关闭每个旧stream；失败后询问已交付内容与provider恢复快照。没有交付可restart，已交付可携带的文本/推理前缀才continue；正常结束、结构化输出或不安全前缀可stop；已经释放的工具调用走严格的handoff/stop分支，避免把任意半截工具调用当成可继续文本。[候选生命周期](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/application/execution.py#L435-L570)；[恢复状态机](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/core/stream_recovery.py#L62-L105)

### ④ 亮点、近期变化与边界
- 真正值得复用的是“协议语义与资源生命周期”而非简单换base_url：原生Messages只保留支持该契约的fallback，reasoning从原请求/策略解析，客户端配置更新通过代际租约隔离；退役代际在仍有active lease时不会清理。[原生契约筛选](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/application/routing.py#L271-L294)；[代际清理门槛](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/runtime/provider_manager.py#L686-L703)
- 最新 [#2058提交](https://github.com/Alishahryar1/free-claude-code/pull/2058)的变化已在路由、client cache和admission源码核实。所读回归测试用MockTransport检查两种公开API、三类自定义endpoint格式及403/429场景，验证请求头按Key 1→2→3流转且不会回显key；这是测试设计证据，不是本轮现场调用真实供应商。[请求头回归测试](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/tests/api/test_fallback_key_requests.py#L20-L150)
- Admin安全边界是本地设计：同时检查连接来源、Host及Origin的loopback条件。把它原样放到公网并不能据此获得生产级多租户鉴权、配额隔离或密钥托管能力。[本地Admin边界](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/api/admin_security.py#L58-L67)
- 运行栈包括FastAPI/Uvicorn、Pydantic、httpx/httpx2、OpenAI SDK、tiktoken及可选语音依赖；前端目录是静态HTML/CSS/JS管理界面，本轮没有React/Next.js实现可供评价。精确Python版本和较大的集成面意味着环境升级成本不可忽略。[依赖与可选项](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/pyproject.toml)
- 今日仍有真实使用阻力：[issue #2066](https://github.com/Alishahryar1/free-claude-code/issues/2066)报告Windows上的ConnectTimeout，用户报告版本为6.10.7；维护者建议把HTTP_CONNECT_TIMEOUT提高到30秒，用户最后回复将尝试，尚无成功确认。它不能被当作已修复，也不能直接判定为当前6.16.0的回归。[免费额度由provider控制](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/README.md)中的供应商数、免费token总量和“up to 90%”节省属于项目宣传，本轮未逐个验证

### ⑤ 今日热度：事实与推测分开
**已确认事实：** 官方快照第9、今日增星626；最近一天有多key列表、fallback key选择与reasoning策略相关发布，最新5次commit具有实际功能/修复内容，issue仍在收到反馈。

**解释性推测：** 在不更换熟悉的编码客户端的情况下选择本地/免费/付费模型，并在供应商故障时继续工作，可能具有较低试用门槛和传播吸引力；最近多key和fallback改进也可能提升留存。但release与增星同时出现不证明因果，免费额度宣传更不能直接当作今天上榜原因。未找到足够的直接证据解释今天为何上榜。

### ⑥ 对AI、RAG与全栈项目的具体复用建议
- **Agent：** 优先精读stream_recovery的交付边界：重试依据应是用户/工具究竟收到了什么，不只是HTTP错误码。特别为“工具调用已交付、JSON只到一半、纯文本可续写”建立不同测试
- **MCP：** 本轮核心是HTTP模型网关，不是MCP server；它更适合作为MCP Agent所用的模型后端。可借鉴provider capability过滤，避免把不兼容工具/推理协议的模型硬塞进统一fallback
- **RAG：** 可放在检索后的生成层实现模型路由，但检索、embedding、向量存储不在本轮验证能力内。评估时固定提示与检索片段，另测跨provider工具调用、引用保真及成本
- **React/Next.js/Node：** 可以通过兼容HTTP接口接本地网关，前端只显示模型/流状态；凭据与供应商请求留在服务端。现有静态Admin不能直接当作React组件库
- **Python/Django：** 值得移植的是不可变配置快照、租约、惰性客户端构造去重、credential恢复状态与provider容量分离。不要在Django模块级全局变量里原地替换正被SSE流使用的client；复制源码或提供网络服务前核对AGPL条款适用性
- **读取覆盖：** 完整递归目录1116项（truncated=false）；实读README定位/接入说明、pyproject与许可证头及相关条款；逐段核读API入口、routing、候选执行/流恢复、runtime client cache、admission registry和Admin边界，provider manager选读lease/关闭段，Messages handler选读原生及常规分流。另读最近5次commit、3个release、最新commit关键diff、fallback请求头测试、issue #2066及全部4条评论。未安装、运行、调用外部模型、验证供应商额度或执行测试

## A. 今天最值得深入的3个项目

### A1. REA：读“完整证据保留→小结果交付”的契约

从 [contractToolHandler.ts](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/server/contractToolHandler.ts) → [toolResult.ts](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/server/toolResult.ts) → [AndroidPackageInspection.ts](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/application/android/AndroidPackageInspection.ts)及[摘要投影](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/domain/analysisView/androidPackageView.ts)读下去。它最贴近Agent/MCP和代码RAG：在上下文预算小、原始结果大时，不把“摘要完了”当成“证据读完了”。今日新SAZ通路还提供了历史网络资料的稳定快照、资源门禁与来源校验实例。建议先学协议，不急于安装完整逆向工具链。

### A2. Open WebUI：读一个完整Agent产品怎样连接RAG、权限和工具循环

以 [main.py的chat_completion](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/main.py#L1138-L1260)为入口，分三支看 [retrieval/utils.py](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/retrieval/utils.py)、[MCP client](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/mcp/client.py)、[context_compaction.py](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/context_compaction.py)。对React/Next前端配Python/Django后端，最可迁移的是集合授权、模型fallback授权、tool-call批次不拆散和async资源关闭。它不是可直接搬进React的组件包；选型时先核对许可与真实外部数据流。

### A3. context-mode：同时学检索策略和审查安全边界

按 [server.ts输出分流](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/server.ts#L1743-L1949) → [store.ts融合检索](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/store.ts#L1242-L1404) → [executor.ts实际cwd](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/executor.ts#L282-L318)阅读。前两者是可复用的日志/源码RAG思路，后者提醒：工具描述可能落后于代码，模型若相信“写入不持久”就可能误判副作用。借鉴本地FTS5与按需回查即可；不要照搬其子进程包装去执行不可信代码，托管复用还需核对ELv2。

## B. 当天样本支持的5个趋势

1. **上下文治理正在从“截短”转向“可回查与合法压缩边界”。** REA保留完整Evidence再交摘要；context-mode先索引原始输出后给片段；Open WebUI按工具调用批次压缩。共同点是保留恢复路径及协议关系，而不是只统计省了多少token。三者都存在自己的预算、召回或摘要边界，不能等同于无损记忆。[REA投影](https://github.com/morluto/rea/blob/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4/src/domain/analysisView/androidPackageView.ts) · [context索引](https://github.com/mksglu/context-mode/blob/1a1bed139906ecc048233583bb2fd29290603b7a/src/store.ts) · [压缩边界](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/context_compaction.py#L335-L349)
2. **Agent基础设施的难点在已经发生的副作用。** ArtCraft把供应商完成与素材归档分开，FCC按已经交付的文本/工具调用决定是否能重试，Open WebUI关心MCP会话由哪个task关闭。长期任务的正确性依赖提交、交付、持久化和清理的明确状态，而不只是“支持更多provider”。[ArtCraft任务](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/jobs.rs) · [FCC恢复](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/core/stream_recovery.py) · [MCP清理](https://github.com/open-webui/open-webui/blob/f8ae8a6c328946dc62cd0712961a0632574581bf/backend/open_webui/utils/mcp/client.py)
3. **模型输出和数据可视化需要检查语义，不能只看格式成功。** diagram-design用service-blueprint语义标签、几何关系与反例校验；God’s Eye View修复坏TLE之后的分组同步，并保留stale/权威空覆盖；BitNet在转换和计算图中保留投影norm。XML合法、数据数组非空或GGUF文件生成成功，都不足以证明原义保持。[图形验证](https://github.com/cathrynlavery/diagram-design/blob/41765070ace63009f23c741cedb0c81429710b4f/scripts/verify-service-blueprint.py) · [TLE恢复](https://github.com/bilawalsidhu/gods-eye-view/blob/8b8ccc9a81379e8b40d4be67610570ee5b159512/src/sources/tle.js) · [embedding转换](https://github.com/microsoft/BitNet/blob/0b341e582afbf9e1011f24744b554c96a3477eb5/utils/convert-bitnet-embedding-to-gguf.py)
4. **低成本AI有多条路径，资源账本必须分开。** AirLLM用磁盘/主存流动换显存，BitNet用模型与低比特内核配套减小存储/计算开销，FCC调度不同供应商和key。三者分别关乎容量、特定模型执行效率和请求供给，不能一概归为“免费、更快”。磁盘、延迟、检索质量、服务费用与协议兼容仍要各自测量。[AirLLM hooks](https://github.com/lyogavin/airllm/blob/7bb8a8600937ff15b81016f286142bcdac7ee2d2/air_llm/airllm/airllm_base.py#L850-L921) · [BitNet内核](https://github.com/isHuangXin/llama.cpp/blob/390c307752ab78fd8189f359d6954c9ba1be74af/ggml/src/ggml-cpu/ggml-cpu-i2s.c) · [FCC路由](https://github.com/Alishahryar1/free-claude-code/blob/4e99ddaa5cf453d4ef22fae7c17f7f3aacc3c52b/src/free_claude_code/application/routing.py)
5. **热度、主线、发行与问题状态是四条不同时间线。** ArtCraft今日增星高但SHA未变；AirLLM只有图片增量；BitNet有今日PR但主线仍停在7月；REA主线新增不能自动算入6.4.0。GEV撤回误报又说明原始讨论会改变昨日风险结论。日报必须按固定版本说话，不能用活跃评论替代已发布实现。[ArtCraft比较](https://github.com/storytold/artcraft/compare/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373...d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373) · [AirLLM比较](https://github.com/lyogavin/airllm/compare/1c8d2630c9373a6d345febe8ef93e05c58bdfb21...7bb8a8600937ff15b81016f286142bcdac7ee2d2) · [GEV撤回](https://github.com/bilawalsidhu/gods-eye-view/issues/1068#issuecomment-6117033123)

以上是今天9个可见样本的工程归纳，不能外推为已经量化的全GitHub或全行业趋势。

## C. 与10月12日已交付报告比较

### C1. 连续可见的5项与真实顺位变化

| 项目 | 昨日 → 今日顺位 | 变化 | 昨日 → 今日累计stars | 两快照差 | 今日stars today |
|---|---:|---|---:|---:|---:|
| morluto/rea | 1 → 1 | 持平 | 108,037 → 163,731 | +55,694 | 45,327 |
| bilawalsidhu/gods-eye-view | 5 → 2 | 上升3位 | 51,788 → 53,849 | +2,061 | 1,895 |
| storytold/artcraft | 3 → 4 | 下降1位 | 18,135 → 22,412 | +4,277 | 4,095 |
| cathrynlavery/diagram-design | 4 → 6 | 下降2位 | 50,463 → 52,791 | +2,328 | 2,081 |
| lyogavin/airllm | 7 → 7 | 持平 | 36,541 → 37,618 | +1,077 | 879 |

比较使用[昨天固定存档正文](https://github.com/DanielMax937/daily-research-reports/blob/e5df9a6eb13b042913d86b4283eb8c098d5ef464/2026-10-12/github-trending.md)与今天官方HTML。累计差值只是两个读取版本的数字差，不是官方日增、更不是严格24小时净增。ArtCraft/diagram顺位下降同时仍在增星，也不能简单翻译为“项目开始衰退”。

### C2. 今天可见样本中新增的4个项目

mksglu/context-mode（第3）、open-webui/open-webui（第5）、microsoft/BitNet（第8）、Alishahryar1/free-claude-code（第9）未出现在昨天可见8项里。准确表述是“相对已交付报告的新面孔”；因为昨天缺第9/10项，**不能确认这四项都是今天才进入官方前10，也不能声称首次上榜**。它们没有昨天报告内的源码SHA基线，不能编造逐日commit差异。

### C3. 昨天出现、今天9项中未见的3个项目

boykopovar/AnyPS5（昨日第2）、pytorch/pytorch（第6）、chrislgarry/Apollo-11（第8）未出现在今天返回的9项中。今天第10项未取得，所以不能逐一断言全部跌出完整前10，更不能推断停止维护。

### C4. 固定源码和原始讨论带来的更新

- **REA：** [2ff850de](https://github.com/morluto/rea/commit/2ff850de68dc9b05c6faf2bbfd26d56bc2d5d27c) → [a2d8b94d](https://github.com/morluto/rea/commit/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4)，ahead 160/behind 0；compare两页取得全部160条提交元数据，文件列表达300项上限，未逐条审计全量diff。今天确认SAZ原生离线导入及Android保留式summary/manifest续读；正式release仍6.4.0，不能把这两项主线新能力自动归给npm发行版
- **God’s Eye View：** [591f299d](https://github.com/bilawalsidhu/gods-eye-view/commit/591f299d11f38a612629a274463196d57ae3862e) → [8b8ccc9a](https://github.com/bilawalsidhu/gods-eye-view/commit/8b8ccc9a81379e8b40d4be67610570ee5b159512)，ahead 6/behind 0、净4文件。已确认TLE缺行后的重同步修复，版本仍0.2.1；另外[issue #1068撤回](https://github.com/bilawalsidhu/gods-eye-view/issues/1068#issuecomment-6117033123)澄清昨天尚未复现的分享链接360°卡住报告，是测试条件澄清，不是代码修复
- **ArtCraft：** 昨日和今天都是[d4e4ac69](https://github.com/storytold/artcraft/commit/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373)，compare identical，**无代码增量**。今天补读确认JobStore持久化失败只告警、外部提交早于本地保存；这是同一版本的新增理解，不是今天才出现的问题
- **diagram-design：** [7a2e2217](https://github.com/cathrynlavery/diagram-design/commit/7a2e22170ee838e859d8142ba825d83f8b6375e6) → [41765070](https://github.com/cathrynlavery/diagram-design/commit/41765070ace63009f23c741cedb0c81429710b4f)，ahead 34/behind 0、净77文件，manifest 2.6.74→2.6.90，类型44→45。昨天draw.io输出异常和PNG小数scale缺口均已在当前源码修正；新增service-blueprint验证与viewBox静态检查。今日CSS选择器问题仍有原始issue及源码支撑，未独立运行复现
- **AirLLM：** [1c8d2630](https://github.com/lyogavin/airllm/commit/1c8d2630c9373a6d345febe8ef93e05c58bdfb21) → [7bb8a860](https://github.com/lyogavin/airllm/commit/7bb8a8600937ff15b81016f286142bcdac7ee2d2)，ahead 1/behind 0，只改assets/star-history.png与dark版，**无已确认执行代码增量**。BOM读取、单文件切分等修复提案不能当已合入；训练仍为9月4.0范围

最需要更新昨天风险提示的是GEV报告者撤回误报和diagram-design两个旧缺口已经修正；最值得今天新增学习的是Open WebUI的工具循环/权限边界，以及context-mode实际执行行为与文字承诺的差异。对没有代码变化的项目，不用星数增长制造技术增量。
