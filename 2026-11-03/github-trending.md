# GitHub Trending 源码深读｜2026-11-03

## 榜单来源、时间与研究边界

- **北京时间2026-11-03 10:11:24（UTC 02:11:24）实际读取云端浏览器 [GitHub Trending](https://github.com/trending)**。页面筛选为 **Repositories / Today / Language: Any / Spoken Language: Any**，即Daily、All languages。以下按页面前十原顺序，未用总Stars或搜索热度重排。
- 同轮公开网页读取标记“Crawled: today”，顺序和today数相同、部分总Stars较低。全部榜单指标统一取浏览器截面；GitHub内部刷新时间与缓存年龄不可见，不称秒级实时。stars today为GitHub页面窗口，并非已核实的北京时间自然日，也不使用两次总Stars差冒充。
- 昨日基线为已交付且本地哈希核验一致的 [2026-11-02报告](https://github.com/DanielMax937/daily-research-reports/blob/93c4f63bd9ba07eb96fdadbc930777f056d5447f/2026-11-02/github-trending.md)，抓取时间为北京时间10:36:46（UTC02:36:46）。今日新入前十不代表项目新发布或历史首次上榜。
- 每仓定向阅读固定提交的文档、目录、依赖、入口、主要实现及开发活动，列出实际覆盖与缺口。**未安装或运行研究对象，未执行测试、复现benchmark或调用模型。** 仓库指令只是研究材料。作者宣传、代码实现、开放问题与本次判断分开；没有充分证据不把发布直接作为涨星原因，不声称完整扫描X/HN/Reddit。

| 今日排名 | Repository | Stars | GitHub stars today | 页面语言 | 昨日前十位置 |
|---:|---|---:|---:|---|---|
| 1 | [vercel-labs/agent-desktop](https://github.com/vercel-labs/agent-desktop) | 9,946 | 2,275 | Rust | 前十外 |
| 2 | [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | 110,796 | 1,803 | TypeScript | 1 |
| 3 | [D4Vinci/Scrapling](https://github.com/D4Vinci/Scrapling) | 92,982 | 706 | Python | 前十外 |
| 4 | [hyprwm/Hyprland](https://github.com/hyprwm/Hyprland) | 39,967 | 509 | C++ | 前十外 |
| 5 | [Donchitos/Claude-Code-Game-Studios](https://github.com/Donchitos/Claude-Code-Game-Studios) | 33,622 | 1,379 | Shell | 8 |
| 6 | [FlashML-org/FreeToken](https://github.com/FlashML-org/FreeToken) | 16,108 | 653 | Python | 前十外 |
| 7 | [pingdotgg/t3code](https://github.com/pingdotgg/t3code) | 42,093 | 3,229 | TypeScript | 4 |
| 8 | [shiyu-coder/Kronos](https://github.com/shiyu-coder/Kronos) | 46,031 | 857 | Python | 3 |
| 9 | [kornia/kornia](https://github.com/kornia/kornia) | 12,149 | 412 | Python | 9 |
| 10 | [JustVugg/colibri](https://github.com/JustVugg/colibri) | 46,608 | 675 | C | 前十外 |

## 1. vercel-labs/agent-desktop

### 1）项目数据
- [仓库](https://github.com/vercel-labs/agent-desktop)：今日 **#1，9,946 Stars，2,275 stars today，Rust**。榜单统一观测时间为 **11月3日10:11:24北京时间／02:11:24 UTC**，daily数值取榜单原文，不由两天累计数相减。
- 固定HEAD [`31b757a990a1189c9df8128df10e8df2ee5e15e1`](https://github.com/vercel-labs/agent-desktop/commit/31b757a990a1189c9df8128df10e8df2ee5e15e1)，提交于 **11月3日09:32:57北京／01:32:57 UTC**。它不在昨日交付前十中，因此只能称本次进入所比较的前十，不声称历史首次上榜，也没有可核的昨日同仓源码基线。

### 2）它解决什么问题
这是让外部AI Agent读取和操作桌面软件的Rust CLI与C库：读取操作系统无障碍树，为元素分配ref，执行动作后再次观察。它不内置模型推理循环，不是React桌面聊天壳，也不是仅靠截图坐标匹配的视觉Agent。真正难点是两次调用之间UI会重排、元素会销毁、进程会更换，旧ref不能“看起来像”就点下去；今日源码最值得读的是这条身份验证链，而非命令数量。

### 3）实际实现与控制流
1. **平台适配与进程边界。** [Cargo workspace](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/Cargo.toml)含core、macOS、Windows、Linux、ffi及CLI六块，Rust edition 2024、最低1.89；[CLI manifest](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/src/Cargo.toml)按target选择原生adapter。[main.rs](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/src/main.rs)解析clap命令、构造session/agent/deadline上下文、做权限与headed策略preflight，再dispatch；每个CLI调用独立进程。macOS入口还停止旧版command host，不应沿用旧文章将当前版本描述为常驻执行daemon。
2. **观察与展示深度分开。** [snapshot入口](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/commands/snapshot.rs)校验surface、root与wait组合，skeleton把展示深度压到最多3层，再走普通快照、root drill或selector wait。[window_capture.rs](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/snapshot/window_capture.rs)对不保留元素token的adapter先尝试完整窗口观察，再从同一份树投影浅层展示；整窗无法读完时仍可返回浅树，但标记identity_unproven，不能据局部视野宣布元素唯一。完整树本身也有深度/预算边界，“完整”按内部exhaustive条件判断。
3. **快照名空间落盘，ref不是短号全局通行证。** [RefStore](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/refs/refs_store.rs)按session存快照，ref解析同时指定snapshot和local id；更新旧快照前在写锁下核对expected entry，读取有大小限制及schema校验。保存量上限128，裁到96的低水位，避免每次保存都反复排序裁剪。这是本地持久状态，不是远端Agent记忆数据库。
4. **无原生token时，用同一谓词证明两次身份。** [CaptureProof](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/refs/ref_capture_proof.rs)要求完整whole-window读、同一条记录在该观察中恰好匹配一次，且没有未知字段留下潜在同胞；按字段mask缓存计数，避免每个ref重新扫树。[FullPredicate](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/refs/ref_full_predicate.rs)比较role及已记录的native identifier、稳定name、description，区分Match／NoMatch／Unknown，mutable value与bounds不作为这一规则的身份。[resolve_saved_ref](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/refs/resolve_saved_ref.rs)再要求当下完整证据中唯一匹配，定位后重读落点确认；同名双胞胎、缺字段和已消失对象分别拒绝，不能将路径位置或Windows runtime id直接当永久身份。
5. **macOS走另一条有边界的原生身份路径。** [retained.rs](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/macos/src/tree/resolve/retained.rs)动态查找私有AX remote-token符号，将对象地址证据编码为axtok1；缺失符号或无法取token时返回无token，而非假造成功。[retained_resolve.rs](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/macos/src/tree/resolve/retained_resolve.rs)解析后检查PID、role和已记录native identifier；token死亡或不匹配返回STALE_REF，不搜索一个相似替代品。使用私有符号意味着跨OS版本可用性必须独立验证，不能把本次静态阅读写成Apple长期兼容保证。
6. **身份通过才进入动作。** [ref_action](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/ref_action/mod.rs)在持有interaction lease时resolve、检查可操作性，必要时滚动后重新resolve，再调用execute_verified_action。[Unix lease](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/session/interaction_lease.rs)组合进程内guard与用户专属目录中的文件锁，沿deadline计入等待；这串行化协作调用，不会冻结外部应用或阻止真人同时改变UI，不能推导成OS事务或exactly-once保证。

### 4）技术亮点与边界
- **拒绝有歧义的动作优先于“尽量点中”。** capture和resolve共用谓词、未知信息不当作匹配，可迁移到Agent执行前校验与引用撤销。
- **浅层输出不意味着浅层身份判断。** skeleton减少模型读入量，后台仍可能扫描整窗才能证明唯一；token开销、原生调用成本和正确性不能混为一谈。本轮没有实测速度或token节省。
- **无窗口后台应用有显式owner。** [app_lookup](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/system/app_lookup.rs)只让background app无窗口时回退process owner；process-owned ref重验进程身份。snapshot输出此时省略window字段，消费JSON的客户端不能强制假定每次都有window.id。今日HEAD对应Dock、菜单栏extras及Control Center等macOS面板修复，不代表Linux／Windows获得相同surface。
- 默认headless不是“无权限或无副作用”：它限制抢焦点/合成输入，仍可经无障碍接口修改应用。快照、剪贴板和调试产物可能含私人内容；外接模型与日志留存须由harness另设权限边界。

### 5）今日热度：已证事实与缺证
公开[v1.0.2](https://github.com/vercel-labs/agent-desktop/releases/tag/v1.0.2)发布于 **10月31日05:17:30北京／10月30日21:17:30 UTC**，公告包含迁入vercel-labs后的链接修订、Labs标识及文档站。近5个主线提交显示 **11月3日06:08:02北京／11月2日22:08:02 UTC**集中合入移除macOS host、macOS token、Linux/Windows capture rule，随后为Discussions调整和今日系统面板修复。manifest仍标1.0.2，**当前main新实现不能等同已发布1.0.2二进制**。

已读开放[PR #505](https://github.com/vercel-labs/agent-desktop/pull/505)与[#506](https://github.com/vercel-labs/agent-desktop/pull/506)，创建于 **11月3日09:44:03／09:44:08北京，01:44:03／01:44:08 UTC**，提出install/sandbox命令及macOS VM sandbox；两者未合并，不能宣称项目现在已经提供开箱即用VM隔离。[PR #504](https://github.com/vercel-labs/agent-desktop/pull/504)创建于 **09:33:08北京／01:33:08 UTC**，拟扩展AX窗口发现并强化native ID校验，作者明确实机E2E和性能A/B尚待完成。本轮没有执行其单测，也不把作者报告变成本期测试结果。**暂无足够公开证据解释今日热度。** 迁移组织和集中合并是同期事实，不能据此断言造成2,275 stars today。

### 6）对用户AI／React／Node／Python工程的价值
做Agent工具层，优先借鉴“观察证据→有作用域的引用→执行前重新验证→可解释拒绝”的接口，而不是在LLM提示里仅写“不要点错”。Node可调用CLI读取结构化JSON，Python可研究C FFI接入，但真正运行前仍需评估平台权限、FFI生命周期与当前ABI版本。做React/Electron应用时，无障碍role/name/id是否稳定会直接影响Agent可操作性；重复按钮需要可区分的语义。它不是RAG或模型训练库，价值在电脑操作控制层；VM sandbox尚为PR，不能用它替代现有执行隔离。

**实际覆盖与限制**：完整递归树4,035项、README、两份Cargo manifest、CLI入口、core导出、snapshot/refs store/capture proof/full与live predicate/saved-ref resolution/lease/ref-action相关模块、macOS retained token与验证、surface read、process owner和部分相关测试源码；最近5提交、3 release及3开放PR正文。大型helpers与部分平台文件仅定位阅读，未逐行审计所有adapter／FFI／输入实现；没有昨日固定基线。未安装、运行、测试、benchmark、操作桌面或修改仓库。

## 2. thedotmack/claude-mem

### 1）项目数据
- [仓库](https://github.com/thedotmack/claude-mem)：今日 **#2，110,796 Stars，1,803 stars today，TypeScript**；昨日#1→今日#2。统一榜单时点 **11月3日10:11:24北京／02:11:24 UTC**。
- 固定[`02584c4ac9d92fea45adf5c61e22c546b5738621`](https://github.com/thedotmack/claude-mem/commit/02584c4ac9d92fea45adf5c61e22c546b5738621)，提交于 **11月3日04:37:31北京／11月2日20:37:31 UTC**。与昨日交付固定c239a048[比较](https://github.com/thedotmack/claude-mem/compare/c239a048a8a07607148f4c1f26b258ccfb28b80d...02584c4ac9d92fea45adf5c61e22c546b5738621)前进 **76 commits、270个变更文件**，文件清单未到300上限；并非每个文件都经逐行审计。

### 2）它解决什么问题
基础产品仍将编码Agent的工具观察、对话摘要和项目状态整理为可检索记忆，再通过本地viewer/My Work和可选云端功能使用。今天最重要的增量不是“支持更多Agent”，而是安装引导读历史之后，怎样把**本地导入**与**把原文交给云端AI整理**隔开。昨日报告集中云viewer与分享投影；今日可确认新增了setup上传同意状态机，并发布明确隐私修复，必须与“所有内容始终本地”这种过度概括区分。

### 3）实际实现：从React选择到云端POST
1. **入口与本地数据准备。** 根[package.json](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/package.json)为15.9.0；[worker-service](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/worker-service.ts)把SessionStore、SetupScan和WorkViewRoutes接在同一个worker。[SetupScan](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/prompt-import/setup-scan.ts)扫描近30天用户输入，匹配hook已有记录、去重写本地数据库，并整理仅存在记忆中的输入；这发生在上传选择之前。因此“拒绝上传”并不等于“不读取本地历史或不落本地库”。
2. **同意是可等待状态，不只是checkbox文案。** 有待传prompts时，扫描结束将数据留在pendingUpload内存中，状态停在awaiting-consent并return；start在等待或上传期间复用当前状态，避免重复扫描带出第二次上传。confirmUpload只能从等待态进入，先清空pending句柄，再按所选agents过滤；拒绝或空选择给extractor传空数组并完成。失败后用户重新start会再次等待同意，测试源码也专门覆盖“不沿用上次yes”。
3. **React真实接线及默认选择要说清。** [scan-screen.tsx](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/ui/my-work/src/setup/screens/scan-screen.tsx)展示有prompts的工具及条数，**工具默认勾选**，用户可取消；improveProduct单独控制且初始false。页面明确写选中消息会送cmem.ai与AI provider，details列完整消息、session IDs、项目名、路径和时间。[setup-page](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/ui/my-work/src/setup/setup-page.tsx)防双击，并把当前分析共享选择与同意一起提交；[setup-data](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/ui/my-work/src/setup/setup-data.ts)实际POST到/api/setup/scan/consent。HEAD的拒绝按钮现为“Skip this step”，不能把15.8.3公告旧文案“Keep everything local”当今日界面截图。
4. **服务端验证不能由UI替代。** [WorkViewRoutes](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/worker/http/routes/WorkViewRoutes.ts#L654-L676)将consent POST串接loopback客户端、loopback Host、拒绝forwarded headers、Origin／Sec-Fetch-Site、JSON body和strict schema检查，随后才调用confirmUpload。它允许API省略agents，此时上传所有pending工具；本次React客户端显式传chosen。不能把这层origin防护称为对本机恶意程序的通用认证屏障。
5. **云端调用及恢复语义。** 同一routes构造[HostedIntent](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/work-view/hosted-intent.ts)，把其run绑定为SetupScan extractor。空数组直接结束，不调用云；已有完成结果直接复用，已有pending-save先重放保存，防成功响应后本地中断导致重复付费。真正POST前检查不同平台session ID冲突、未压缩与gzip各2MiB上限，再向/api/pro/intent发送所选ownerPrompts、improveProduct及时区偏移；不自动retry，因为丢回包也可能已经消费服务端额度。成功响应经Zod校验，先存pending，再保存goals、rules及group关系，完成标记最后写。这是可恢复保存，不是客户端与云端间的分布式exactly-once保证。
6. **避免同步SQLite读堵住HTTP。** 新[WorkViewReadWorkerClient](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/work-view/WorkViewReadWorkerClient.ts)以node:worker_threads把projection读移出HTTP事件循环，request id映射pending promise，后台[worker](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/work-view/work-view-read-worker.ts)同步逐条读WorkStateSource并回送结果。退出时拒绝未完成请求，下次读可重建；队列刻意不另设cap，因此事件循环隔离不等于负载背压或无限扩容。

### 4）技术亮点与限制
- 隐私选择贯穿UI、路由、状态机和实际网络函数，且分析共享与执行云整理分开；关闭improveProduct**不会阻止已明确同意的云端整理**。反过来，拒绝这一步也不意味着关闭产品所有其他可选云同步或遥测。
- [worker-url.ts](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/shared/worker-url.ts)新增显式remote worker URL校验：仅http(s)，非loopback必须https，拒绝内嵌凭据/query/fragment，坏值抛InvalidWorkerUrlError而非偷偷回退本地。它是传输配置校验，不负责证明远端运营者可信或配置数据不外泄。
- 昨日尚开放的[#5267](https://github.com/thedotmack/claude-mem/pull/5267)已于 **11月2日16:51:46北京／08:51:46 UTC**合并；当前[OpenRouterProvider](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/worker/OpenRouterProvider.ts#L1061-L1086)对特定“禁止关闭reasoning”的拒绝去掉reasoning字段仅重发一次，已开始输出或强制关闭reasoning的耗尽重试不走此分支，不按URL永久记住偏好。不能再沿用昨日“仍为开放提案”的状态，也不能概括为所有400自动重试。

### 5）今日热度：发布与问题事实
[v15.8.3](https://github.com/thedotmack/claude-mem/releases/tag/v15.8.3)发布于 **11月2日14:26:25北京／06:26:25 UTC**，晚于昨日榜单截面 **10:36:46北京／02:36:46 UTC**。维护者公告明确承认，自15.2.0起浏览器setup曾不询问就上传近30天完整prompts及上述元数据；本版新增同意门槛，**不会删除此前已上传的数据，cmem.ai服务端处理及隐私政策也不在该修复范围**。这是维护者发布声明与当前客户端源码共同支持的结论，不等于本轮取证了所有历史用户或云端记录。

[v15.9.0](https://github.com/thedotmack/claude-mem/releases/tag/v15.9.0)于 **11月3日02:03:43北京／11月2日18:03:43 UTC**发布，公告列Devin接入、remote worker、更多secret redaction、错误报告撤销和多项可靠性修复；本期实际深入同意链、read worker、URL校验及OpenRouter，不把其余公告全部视为已逐项代码验证。

开放[issue #5307](https://github.com/thedotmack/claude-mem/issues/5307)创建于 **11月3日09:38:43北京／01:38:43 UTC**，报告15.8.3→15.9.0升级时SIGKILL与OAuth refresh竞态可能导致登录失效；作者明确未观察到被杀child内部刷新，只是结合日志推断，不能将其根因当已证定论。开放[PR #5308](https://github.com/thedotmack/claude-mem/pull/5308)创建于 **09:49:09北京／01:49:09 UTC**，拟在上传前检查云端容量、持久化429/503冷却，且依赖服务端配套协议；**当前HEAD的HostedIntent仍直接POST，不能预报为已上线能力**。**暂无足够公开证据解释今日热度。** 隐私修复和发布密集与1,803 stars today同时发生，不证明正面传播或争议导致涨星。

### 6）对用户AI／React／Node／Python工程的价值
Node/Python/Django的RAG导入器应把“本地发现→本地保存→选择范围→发送第三方→保存结果”做成显式状态机，失败重试重新核对同意，而不是一个通用loading按钮。React同意面板值得学习请求与最新偏好一起提交、防双击及列出每类数据量，但默认勾选全部工具与折叠数据说明仍是需要独立评估的产品选择。后台读取可迁出HTTP线程，却仍需针对队列、取消和数据库快照一致性设计容量策略。把HostedIntent的pending-save模式迁入Agent总结任务时，也要补齐云端幂等键与留存/撤销协议，而非以“已脱敏”替代明确告知。

**实际覆盖与限制**：已读昨日完整对应章节与证据摘要；今日完整递归树3,326项，根manifest、SetupScan、HostedIntent、React scan/page/setup-data、worker接线与WorkViewRoutes同意路由/guard段、read worker三模块、worker URL、OpenRouter指定重试段及相关setup测试。另抓取redaction、telemetry等全文但不声称全面审计；大型worker/routes仅定向阅读。核近5提交、76提交compare统计/完整270文件清单、3 release、最新issue/PR正文与#5267合并状态。未审计私有云服务、复现上传、调用模型、安装、跑测试或修改任何研究对象。

## 3. D4Vinci/Scrapling

### 1）项目数据
- Repository：[D4Vinci/Scrapling](https://github.com/D4Vinci/Scrapling)；今日排名 **3**；**92,982 Stars，706 stars today，Python**。统一采用 **2026-11-03 02:11:24 UTC／10:11:24 北京**的浏览器榜单截面；昨日已交付报告前十未收录它，不等于首次上榜或刚发布。
- 本轮固定源码为 [95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0](https://github.com/D4Vinci/Scrapling/commit/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0)，HEAD 时间为 **11 月 1 日 17:59:59 UTC／11 月 2 日 01:59:59 北京**，提交题目是新增赞助商，不是抓取引擎升级。稍后 API 返回的总 Stars 不替换上述统一截面。

### 2）它解决什么问题
Scrapling 把网页解析、HTTP 获取、浏览器会话和整站爬取接到同一组 Python 对象上，减少从单页脚本扩展到有重试、去重、并发控制的数据管道时重复搭框架的工作。面向 AI，它提供 MCP 浏览器工具和网页转 Markdown 模板，适合充当 Agent 或 RAG 的数据获取层。它并不是靠 LLM 自动理解任何网站的万能抓取器，网页变化后的“自适应”主要是结构相似度匹配，网站授权、访问政策和内容可信度仍需调用方处理。[README](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/README.md)

### 3）实际架构与核心实现
1. **依赖和入口明确分层。** [pyproject.toml](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/pyproject.toml) 为 0.5，要求 Python ≥3.10；基础依赖是 lxml、cssselect、orjson、tld、w3lib。fetchers extra 才加入 curl_cffi、Playwright、Patchright、指纹及异步组件，ai extra 再加入 MCP、Markdown 转换。CLI 指向 scrapling.cli:main，MCP 指向 scrapling.cli:mcp，所以只安装解析核心不能假定浏览器和爬虫依赖已齐全。
2. **自适应不是模型推理。** [parser.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/parser.py) 正常先跑 XPath/CSS；启用 adaptive 并保存过元素时，选择器失效才取旧元素特征，对新 DOM 所有候选计算标签、文本、属性、路径、父节点及兄弟关系的相似分数。返回达到阈值的最高分候选，最高分并列可以有多个；默认不是全局自动开启。其“百分比”是启发式分数，不能当正确概率。配套 [storage.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/core/storage.py) 用 SQLite、WAL、RLock 保存元素特征，以基域和 identifier 区分记录；这是可替换的存储接口，不是向量数据库。
3. **爬虫的数据流是 Request → Scheduler → Session → callback → 新请求或 item。** [engine.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/spiders/engine.py) 统一 session ID，进行域名过滤、可选 robots 判断、域级限流、缓存读取及抓取；callback 产出 Request 就重新入队，产出 dict 就交给 on_scraped_item，再存入结果或流式发送。主动任务数在创建时受上限约束，避免先创建成千上万个等待任务。被判定 blocked 的响应不进入后面的开发缓存写入路径；重试降低优先级、计数并绕过去重，且有上限。
4. **调度次序和完成次序不同。** [scheduler.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/spiders/scheduler.py) 用 asyncio.PriorityQueue 的“负 priority＋递增／递减序号”实现优先级优先、同优先级 BFS／DFS。pending 镜像直到 complete 才移除，因此 checkpoint 包含队列中和执行中的请求；恢复仍可能重新执行尚未记完的任务，不宜把它理解为外部副作用的 exactly-once。去重由 [request.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/spiders/request.py) 组合 session、规范化 URL、method、body，可选 header／kwargs 后计算 SHA-1，明确用于非安全用途。
5. **MCP 是能力封装，不是多租户授权系统。** [server.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/core/ai/server.py) 用进程内字典管理 session，检查类型、存活状态和页面忙碌状态；一次性请求与持久会话分开，持久页面可用于提取、截图、执行 JS、表单和网络检查。HTTP 传输默认要求共享 bearer token，恒时比较，除非显式 no-auth；[CLI](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/cli.py) 默认绑定 127.0.0.1。一个 token 能使用该服务的全部工具，不能据此推导每用户或每站点隔离。
6. **面向 Agent 的动作和证据有实际边界。** [_browser_actions.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/core/ai/_browser_actions.py) 先校验目标，再按顺序执行；遇首个错误停止，已经产生的效果保留，不自动重试，也不回滚。[_network.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/engines/_browsers/_network.py) 只在 requestfinished 捕获完成请求，默认至多 1,000 条，响应体单条上限 1 MiB、总量 20 MiB，超出按最旧记录淘汰；generation 和监听器身份检查防止清空／卸载后迟到回调重新写入。没有记录不等于没有发起过请求。

### 4）技术亮点与限制
最值得借鉴的是把解析、获取、调度和 Agent 工具分开，以及让调度恢复、浏览器动作部分成功、网络记录淘汰都有显式状态。对 RAG，[ContentSpider](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/spiders/templates/site_to_markdown.py) 强制配置 allowed_domains，输出 url／title／markdown；max_pages 限制的是转换数量，已排队请求仍可能获取，所以它不是严格 HTTP 请求预算。

另一个必须看到的边界是 URL 协议。固定版本的 [links.py](https://github.com/D4Vinci/Scrapling/blob/95cf9019ab5a5d6f3e9654b7ef1c6a26e29dc5c0/scrapling/spiders/links.py) 的 valid_schemas 确实含 file；开放 [PR #542](https://github.com/D4Vinci/Scrapling/pull/542) 报告本地文件读取风险，并建议分层限制 http/https。该 PR **未合并**，本轮未运行复现；不能写成风险已修复，也不能因为有 bearer token 就认为任意 URL 已安全。若把能力开放给不可信网页或模型，应在应用层额外限制协议、目标地址、重定向和进程可访问资源。自适应选错元素、内容包含恶意指令也都不是“转换为 Markdown”自然解决的问题。

### 5）今日热度：发布事实与因果缺证
可核对的最新发布是 [v0.5](https://github.com/D4Vinci/Scrapling/releases/tag/v0.5)，发布于 **10 月 17 日 21:43:59 UTC／10 月 18 日 05:43:59 北京**，包括更完整的 MCP 浏览器动作、网络历史、会话状态、Shadow DOM 和 BFS／DFS 等，并明示破坏性迁移；不是今日发布。最近四个 main 提交均是赞助相关文档。11 月 2 日 **21:14:23 UTC／11 月 3 日 05:14:23 北京**新开的 [PR #545](https://github.com/D4Vinci/Scrapling/pull/545) 处理代理 URL 凭据百分号解码；[PR #521](https://github.com/D4Vinci/Scrapling/pull/521) 则报告 form 序列值的指纹与实际请求体不一致，最近更新于 **11 月 2 日 20:53:19 UTC／11 月 3 日 04:53:19 北京**。这些是维护活动和工程问题的证据，不是已合并修复或涨星归因。**暂无足够公开证据解释今日热度。**

### 6）对 AI／React／Node／Python／Agent 工程的价值
Python 侧适合学习如何把单页获取演进为有恢复能力的数据入口；Node Agent 可以通过 MCP 调用，React 只呈现进度、内容预览与审核结果，不必承载抓取进程。优先借鉴 session 类型校验、有限队列、partial-effects 报告和有上限的观测历史；若用于自动填表或提交操作，必须由上层权限系统明确授权，失败后先判断是否已生效，不能盲目重复整串动作。自适应可以降低 DOM 小改动的维护成本，但关键字段仍要以 schema、数量、页面身份和业务约束复核。

**实际覆盖／限制**：完整递归 tree（835 条，未截断）；README 功能与安装段、pyproject、CLI 的 MCP 配置；parser 的 XPath／adaptive／相似度路径、storage；engine、scheduler、request、links、ContentSpider；MCP server 的会话／动作／认证部分、动作执行、NetworkRecorder。另读最近 4 commits、2 releases、3 条开放 PR 正文并单独确认 #542 未合并。大型 parser/server 采取相关函数定向阅读，未逐行审计全仓；未安装、启动浏览器、执行脚本／测试、复现漏洞或测量性能。

## 4. hyprwm/Hyprland

### 1）项目数据
- Repository：[hyprwm/Hyprland](https://github.com/hyprwm/Hyprland)；今日排名 **4**；**39,967 Stars，509 stars today，C++**，截面为 **2026-11-03 02:11:24 UTC／10:11:24 北京**。昨日已交付前十没有它；本次是进入本轮前十，不是新建项目。
- 固定 HEAD：[e93501dd1bfeabf6206cdaebd853008d47a7dcc1](https://github.com/hyprwm/Hyprland/commit/e93501dd1bfeabf6206cdaebd853008d47a7dcc1)，提交于 **11 月 2 日 17:57:19 UTC／11 月 3 日 01:57:19 北京**，修正组合键解析中的输入消费例外。

### 2）它解决什么问题
Hyprland 是动态平铺 Wayland compositor，管理应用窗口、输入、工作区、显示输出以及动画和合成效果。它服务的是 Linux 桌面的交互与图形管线，不是 React 组件库，也不是浏览器或 Agent 编排框架。当前源码和 README 均表明其后端与合成系统已独立演进，不能继续套用“基于 wlroots 的窗口管理器”这一历史描述。[README](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/README.md)

### 3）实际架构与核心实现
1. **构建揭示真实技术栈。** [CMakeLists.txt](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/CMakeLists.txt) 指定 C++26，链接 Aquamarine、Wayland server、xkbcommon、pixman、Hypr 系列库及 EGL／OpenGL ES，查找 Lua 5.5，并用 hyprwayland-scanner 生成协议绑定。主程序与 hyprland_lib、hyprctl、插件管理组件分开；这不是单纯用脚本给现有桌面换皮。
2. **进程入口 → compositor → 后端与管理器 → 事件循环。** [main.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/main.cpp) 解析配置、socket 接管、safe mode 等参数，检查 XDG_RUNTIME_DIR 与 root 使用条件，创建 CCompositor。其 [initServer](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/Compositor.cpp) 建立 Wayland display／event loop，再让 Aquamarine 按 mandatory headless、可用时 DRM、fallback Wayland 的策略创建后端；注册输出和输入设备事件，并按阶段初始化配置、渲染、协议、seat、输入、XWayland、IPC 等管理器。不能仅看到 headless 后端选项就推断所有无 GPU 的运行环境都受支持，代码仍有相关 TODO 与失败路径。
3. **事件循环把设备、配置和计时器放进同一个调度域。** [EventLoopManager.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/managers/eventLoop/EventLoopManager.cpp) 向 Wayland loop 注册 timerfd、配置 inotify 和 Aquamarine poll FD；后端 FD 集合变化时补加／移除监听。计时器触发后将重算安排为 idle 工作，避免遍历 timer 集合时递归修改；doLater 先移动出本轮函数列表，再执行回调，新的任务进入下一轮。这比“所有回调马上执行”更容易维持集合和生命周期不变量。
4. **窗口协议状态不是 UI 树里的一个布尔值。** [XDGShell.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/protocols/XDGShell.cpp) 区分 pending／current、surface 映射与卸载、configure 序号和 ack；toplevel 请求移动或调整大小时验证对应 seat 的 pointer-button serial。状态变化可通过 doLaterLock 合并 configure，再发给客户端。理解这一来一回，有助于避免把“发出窗口尺寸请求”误当“客户端已经按新尺寸呈现”。
5. **渲染先判定是否该做，再组织 scene，最后提交。** [Renderer.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/render/Renderer.cpp) 的 renderMonitor 有防重入守卫；检查显示尺寸、session、pending damage 和 commit coordinator，符合条件先尝试 direct scanout，否则建立渲染上下文与 damage transaction。绘制后将损伤区域转换到输出坐标，再进入 commitPendingAndDoExplicitSync；未能开始新帧时保留 pendingFrame。独立 [MonitorScene.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/render/scene/MonitorScene.cpp) 负责镜像或工作区场景，再画锁屏和位于锁屏上方的输入法，说明 scene 排序本身就有可用性和边界含义。
6. **组合键是有延迟决策的状态机。** [Manager.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/keybinds/Manager.cpp) 收集候选，处理捕获、释放、拖动阈值等状态，交给 [MatchResolver.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/keybinds/MatchResolver.cpp) 分为 partial／deferred／immediate；较长的完整组合压过短组合，仍可延长的前缀延后触发。最新补丁不是重写整个解析器，而是去掉 release 标志在按下阶段“不消费事件”的错误特例；non_consuming、auto_consuming 仍单独保留。

### 4）技术亮点与限制
它的阅读价值在于把“收到事件”“决定谁拥有事件”“完成渲染”“输出已提交”区分开。最新提交新增的 keyboard_input 回归测试检查普通 release bind 与 non_consuming／auto_consuming 的转发差异；[MatchResolver 测试](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/tests/keybinds/MatchResolver.cpp) 则覆盖完整长组合抑制短组合、前缀延后及不同按键顺序。这些是测试设计证据，本轮没有跑过。

配置也应看当前版本：[ConfigManager.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/config/ConfigManager.cpp) 实例化的是 Lua 配置管理器，不能拿旧教程当当前 API。权限层 [DynamicPermissionManager.cpp](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/managers/permissions/DynamicPermissionManager.cpp) 有截屏、插件、键盘、光标位置、输入捕获等分类，按客户端／二进制规则决定允许、拒绝或等待；enforce_permissions 为 0 时直接允许，不能仅因为“采用 Wayland”就宣称任何安装都天然提供同样的权限隔离。本文不判断用户具体发行版的配置、驱动兼容性或安全状态。

### 5）今日热度：发布事实与因果缺证
[v0.57.0](https://github.com/hyprwm/Hyprland/releases/tag/v0.57.0) 发布于 **10 月 28 日 10:42:35 UTC／18:42:35 北京**，公告列出 scene composition、window wobble、可替换 blur、Lua 配置事件等，并有大量输入与显示修复；不是今日新版本。最新 [PR #16806](https://github.com/hyprwm/Hyprland/pull/16806) 已于上述 HEAD 时间合并；此前最近提交还有按配置位深设置 max_bpc、鼠标输入 shadowing 和设备 sysname 暴露。它们说明主干持续维护，不能证明其中任何一项带来 509 stars today。

开放 [issue #16783](https://github.com/hyprwm/Hyprland/issues/16783) 于 **11 月 1 日 17:42:00 UTC／11 月 2 日 01:42:00 北京**报告窗口布局变化但光标不动时，客户端 surface 的光标位置没有更新；正文很短，不足以量化影响范围。开放 [PR #16812](https://github.com/hyprwm/Hyprland/pull/16812) 提议为不支持协议的窗口强制 shortcuts inhibition，创建于 **11 月 2 日 19:59:41 UTC／11 月 3 日 03:59:41 北京**，仍不能作为已支持功能。**暂无足够公开证据解释今日热度**；桌面定制吸引力和近期版本只能列为可能关注背景，不能代替传播因果数据。

### 6）对 AI／React／Node／Python／Agent 工程的价值
若主要做 Web 全栈，不必为了上榜就切换桌面；更有用的是抽取状态机思路。React 复杂快捷键、编辑器命令系统可借鉴“前缀暂存、长组合优先、事件消费与回调触发分离”，Node/Python 异步服务可借鉴 doLater 防重入和资源监听生命周期。桌面 Agent 则必须分清截图权限、输入捕获、键盘映射、输出缩放和实际呈现状态，不能把远程发送操作当成功证据。对图形方向，damage transaction、direct-scanout fallback 与 scene 分层比简单的动画截图更值得读，但性能与兼容性需要在自己的硬件和显示组合上验证。

另一个可迁移细节是延迟任务的撤销：EventLoopManager 的 doLaterLock 返回生命周期对象，析构时删除尚未执行的回调。对异步界面或 Agent 任务面板，这对应“页面、窗口或任务已经消失，迟到回调就不应继续修改旧状态”。应把取消条件绑定到资源生命周期，而不是只在正常完成时清理。[实现](https://github.com/hyprwm/Hyprland/blob/e93501dd1bfeabf6206cdaebd853008d47a7dcc1/src/managers/eventLoop/EventLoopManager.cpp)

**实际覆盖／限制**：完整递归 tree（1,528 条，未截断）；README、CMakeLists、main、ConfigManager；Compositor 初始化／manager／启动段，EventLoopManager，XDGShell 的 toplevel／commit／configure 段；Renderer 的 renderMonitor／damage／提交路径，MonitorScene；keybind Manager 的 processEvent、MatchResolver、Resolver、对应测试；DynamicPermissionManager。读最近 4 commits、2 releases、当前 HEAD 完整 diff、3 条开放 PR 正文、#16806 合并状态和 #16783 issue。#11468 的单独读取未获得有效 issue 正文，不用其推论；没有编译、运行 compositor、测试显示器／驱动、验证权限或复现问题。

## 5. Donchitos/Claude-Code-Game-Studios

### 1）项目数据
- Repository：[Donchitos/Claude-Code-Game-Studios](https://github.com/Donchitos/Claude-Code-Game-Studios)；今日排名 **5**；**33,622 Stars，1,379 stars today，Shell**，截面为 **2026-11-03 02:11:24 UTC／10:11:24 北京**。
- 昨日第 8、32,403 Stars、967 stars today；两次总 Stars 截面差 **1,219**，不等同于今天页面的 1,379，也不冒充北京时间自然日新增。
- 固定 SHA 仍为 [05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418](https://github.com/Donchitos/Claude-Code-Game-Studios/commit/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418)，提交时间 **10 月 19 日 02:09:09 UTC／10:09:09 北京**。[与昨日固定 SHA 比较](https://github.com/Donchitos/Claude-Code-Game-Studios/compare/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418...05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418)为 identical、0 commits、0 变更文件。**本期没有确认到主干源码新增**；阅读重点转为现有实现中公开讨论的新问题。

### 2）它解决什么问题
这是为 Claude Code 游戏开发会话准备的角色、技能、规则、文档模板与 Shell 检查资源，目的是让需求、架构、实现、验收和项目状态有一致路径。执行主体仍是 Claude Code 及其工具与用户的游戏引擎，不应把它包装成仓库自带的通用多 Agent 服务端、消息总线或调度器。它的实际价值在于把重复判断交给小脚本，把需要判断的部分留在有输入和产出约束的技能流程里。[README](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/README.md)

### 3）实际架构与核心实现
1. **配置与事件钩子是宿主接入层。** [project.yaml](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/project.yaml) 记录 schema、框架版本；模板刻意不预填会遮蔽 rigor 展开的六个底层开关。真正的工具接入在 [.claude/settings.json](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/settings.json)：SessionStart 跑会话／缺口检查，PreToolUse 对 Bash／PowerShell 检查 commit 和 push，对 Read／Write／Edit 做读取、写入和 registry 检查，SubagentStop 检查返回产物。这里描述的是 Claude Code 调用 hook 的配置，不是独立常驻进程。
2. **故事实现流程靠 Markdown 技能驱动。** [dev-story/SKILL.md](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/skills/dev-story/SKILL.md) 先用 helper 获取故事事实与配置，再检查 ADR、依赖、manifest 和 tier；随后按故事类型选择程序员角色，并把引擎版本核查交给 specialist。返回后要求核对文件是否真实存在，解析是否执行、截图是否留存；“模型说完成”不直接变成 story complete。无引擎时明确 NOT VERIFIED，静态阅读不能代替 parse 成功；截图也不能验证手感、节奏等动态体验。
3. **证据与状态分别落盘。** [.claude/scripts/session-state.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/scripts/session-state.sh) 维护 active.md 中 STATUS／CHECKPOINT 标记，先构造新内容再写回，保留换行风格；标记缺一半或次序错误时拒绝写入。它只是保存技能给出的状态，不判断状态是否真实。[review-receipts.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/scripts/review-receipts.sh) 则用文件内容 hash 判断相对上次审查的变化，可按二级标题做分段 hash；输出 CHANGED、NEW、GONE、UNRESOLVED 等事实，由调用技能决定是否重新审查。内容 hash 比 mtime 更适合对抗同步和恢复导致的假新鲜，但它只证明字节关系，不能证明审查质量。
4. **进度统计是解析器，不是自然语言理解。** [plan-math.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/scripts/plan-math.sh) 用 awk 读取 sprint-status.yaml 的日期、stories、status、priority，计算时间消耗比例与完成比例差，并输出 On Track／At Risk／Behind。相邻 [story-facts.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/scripts/story-facts.sh) 从 sprint 条目得到故事文件，再读取实际 Markdown。当前实现对 stories 下任意缩进的“- ”递增或切换条目，对嵌套-looking 的 file／status 也匹配，这正是后述新 PR 的依据，不是完整 YAML 语法树。
5. **测试执行与业务判定分离。** [test-run.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/scripts/test-run.sh) 按 Godot／Unity／Unreal 选择命令、前置 import／build、超时方式与结果读取，输出命令、exit、timed_out、rule 等字段；Unreal build 失败时不继续跑可能过期的测试二进制。script 存在不代表环境有引擎，也不代表每次用户流程会运行它；dev-story 明确说 story-done 的文件证据检查本身不运行测试。
6. **commit 检查关注将被提交的版本。** [validate-commit.sh](https://github.com/Donchitos/Claude-Code-Game-Studios/blob/05ad7c8a5b8aa2aa86bbd3439ae7cf7295cac418/.claude/hooks/validate-commit.sh) 区分 index、工作区、git add／commit -a／pathspec 等来源，对数据文件 JSON 检查失败或无法执行检查时可 exit 2 阻止工具调用。它避免了“工作区没坏但 index 已坏”的错判，却仍是特定宿主下的命令解析与 hook，不等于不可绕过的系统沙箱。

### 4）技术亮点与限制
新阅读的两个开放 PR 提醒：**证据系统也需要验证证据定位和解析本身**。[PR #167](https://github.com/Donchitos/Claude-Code-Game-Studios/pull/167) 指出 review-receipts 的 grep 固定字符串仍是前缀匹配，design.md 与 design.md notes.md 可能取错最后一条 hash；固定 main 的 compare_stamp 确实仍用这种匹配，所以“hash 可靠”不代表“选择了正确 hash”。[PR #168](https://github.com/Donchitos/Claude-Code-Game-Studios/pull/168) 则指出 multiline blocker 里的项目符号和 file／status 文本会混进故事统计，影响完成比例和选择范围。两者均未合并，本轮只是将报告与当前代码对照，**没有执行作者复现，也不声称修复已生效**。

这比重复介绍角色数量更有工程意义：将自然语言流程脚本化可以提高一致性，但若 parser 的结构边界不精确，只会把误判稳定地自动化。收据格式、文件名、CRLF、嵌套文本、缺失产物及“从未验证”都应进入测试集。权限 allow／deny 列表和文档里的审批约定也不能替代 Claude Code 本身及实际运行环境的安全边界。

### 5）今日热度：发布事实与因果缺证
最新 [v1.2.0](https://github.com/Donchitos/Claude-Code-Game-Studios/releases/tag/v1.2.0) 仍发布于 **10 月 19 日 02:44:23 UTC／10:44:23 北京**，内容是主流程重构、共享 helpers、读取 guard、证据 hash、引擎参考更新及收窄 shell 预批准；没有今日新发布。#167 创建于 **11 月 2 日 17:59:19 UTC／11 月 3 日 01:59:19 北京**，#168 创建于 **11 月 2 日 19:06:42 UTC／11 月 3 日 03:06:42 北京**；作者给出测试结果，但属于 PR 作者报告，不是本轮执行记录。

新 [issue #169](https://github.com/Donchitos/Claude-Code-Game-Studios/issues/169) 于 **11 月 3 日 01:37:05 UTC／09:37:05 北京**请求增加 Bevy，描述了 fork 中的工作并询问维护者是否接受。当前 main 不能据此称已有第四种引擎支持；issue 内的测试与版本描述也未在本轮独立验证。排名上升、Stars 增长与主干不变可以同时成立。**暂无足够公开证据解释今日热度。**

### 6）对 AI／React／Node／Python／Agent 工程的价值
可直接迁移的不是“49 个角色就是完整团队”，而是任务输入、文件范围、验收证据、状态和人类决定分开记录。做 React／Node／Python 编码 Agent，可用机器可解析状态取代从总结文字猜进度，用精确路径和内容签名判定证据新鲜度，把真实测试命令与“文件存在”分别展示；不要把截图或模型报告当通过验收。若复制这种模式到自己的平台，建议使用成熟 YAML／JSON parser、结构化收据、明确 schema 和权限中间层，避免用一段 grep／awk 同时承担观察、授权和完成判定。

**实际覆盖／限制**：完整递归 tree（782 条，未截断）；README、project.yaml、settings；dev-story、sprint-status；session-state、review-receipts 的文件／分段签名与检查、plan-math 的 progress、story-facts 的 sprint reader、test-run 的命令／超时／结果、validate-commit 的命令与提交版本识别／失败分支。核对昨日报告及 evidence-summary，重新比较同 SHA；读最近 4 commits、2 releases、#167／#168／#169 正文，并单独确认两 PR 未合并。没有运行任何仓库脚本、Claude Code 工作流、游戏引擎或测试；未审计全部角色、技能和 hook。

## 6. FlashML-org/FreeToken

### 1）项目数据
Repository：[FlashML-org/FreeToken](https://github.com/FlashML-org/FreeToken)；今日排名 **6**；**16,108 Stars；653 stars today；Python**。榜单采样：**2026-11-03 02:11:24 UTC／10:11:24 北京**。源码固定为 [3d23551c5b43b61ef26e24cb86a22ff550e502a3](https://github.com/FlashML-org/FreeToken/commit/3d23551c5b43b61ef26e24cb86a22ff550e502a3)，默认分支 main；提交时间 **2026-11-02 23:05:17 UTC／2026-11-03 07:05:17 北京**。相对 11 月 2 日已交付报告，它是本次前十新进入项目，不代表首次上榜或刚开源。

### 2）解决什么问题
FreeToken 针对大规模 MoE 模型在本地显存装不下、专家权重搬运代价高，以及现有 Agent 客户端需要统一服务接口的问题。它把 CPU、主存、GPU 专家缓存、量化内核和请求调度组合起来，提供本地生成与兼容式 HTTP 接口。定位是推理运行时，不是新训练的通用模型；能否跑得快取决于模型格式、路由命中率、PCIe／内存带宽和所用硬件。[项目定位与入口](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/README.md)

### 3）实际架构与核心实现
从 [pyproject.toml](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/pyproject.toml) 可确认这是 Python 3.10+ 包，命令 ft 指向 [cli.main](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/cli.py)，serve、daemon、launch、checkpoint、bench 分开分发。依赖包含 PyTorch、Triton、FastAPI、uvicorn、pyzmq、safetensors；原生加速包是额外选项，不能把“Python 项目”理解成仅靠 Python 循环计算。

HTTP 路径不是把外部请求直接塞给模型。[openai_api.py](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/server/openai_api.py) 先校验能力和参数，转成协议中立的 GenSpec；[generation.py](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/server/generation.py) 解析图像引用、分配 uid，发送 TokenizeMsg，再把回包拆成 reasoning、content、tool-call delta 和 GenDone。最后由协议适配层输出 JSON 或 SSE。这种分层允许多个协议共用生成流程，同时保留各自字段和错误语义。

[Scheduler](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/scheduler/scheduler.py) 创建 Engine、页表、缓存管理器、PrefillManager 和 DecodeManager。当前策略先尝试 prefill，再安排 decode；重叠循环使本轮计算与上轮结果处理并行，同时专门处理“请求已取消但上一批计算尚未返回”的资源回收。离线 [LLM.generate](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/llm/llm.py) 继承同一 Scheduler，通过 pending_requests 和 status_map 汇总输出，并不是另一套独立推理核心。

关键数据通路在 [OffloadMoELayer](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/layers/moe.py)：router 产生 top-k 专家及权重；decode 阶段把专家编号映射为 GPU 缓存槽，缺失项按需拷贝。hybrid 分支让 GPU 计算命中项及有限数量的新取专家，CPU worker pool 计算其余 miss，再合并部分结果；prefill 则按整层流式搬运，并可双缓冲。对应 [offload_cache.py](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/moe/offload_cache.py) 使用受上限约束的 LRU 取数，将路由切分与缓存复用设计成固定形状的设备端路径，以适配 CUDA Graph。

### 4）技术亮点与工程边界
新进入主分支的 MTP 不是“多猜几个 token 就直接输出”。[SpecRunner](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/spec/runner.py) 负责 draft 后的目标模型 verify；[rejection.py](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/spec/rejection.py) 按目标采样结果与草稿的连续前缀一致性计算可接受长度。[MTPProposer](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/spec/mtp/proposer.py) 默认 3 步、最多 8 步，设置 radix_lookahead；草稿专家必须是独立、GPU 常驻的层，不能误复用目标的 offload 专家。它明确拒绝 dummy weights、尚不能读取的 FTW 草稿及不存在的本地草稿路径。这些检查比只列支持模型名更能说明集成边界。

HEAD 的 [NVFP4 CPU 内核](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/kernel/csrc/cpu_moe/kernels/nvfp4.cpp) 重排 int8 激活、拆分 packed nibble，并使用带偏移的查找表及累加补偿配合 VNNI 点积；ISA 选择会检查 AVX-512 VNNI／AVX-VNNI，不具备路径时回到浮点累加方案。改动目的为减少每权重指令数，作者报告的吞吐提升不等于本次独立测试结果。

API 兼容性也有明确上限：源码拒绝 n≠1、logit_bias、旧 function_call，以及需要 constrained decoding 的 json_object／json_schema response_format。Agent 若要求严格 JSON Schema，不能仅改 base URL 就假设契约完全等价。当前依赖约束没有 lockfile；GPU、量化与第三方内核组合仍需单独验证。[API 校验实现](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/server/openai_api.py#L152-L189)

还值得关注内存预算与提交顺序两个容易被速度宣传遮住的细节。[Engine](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/engine/engine.py#L1673-L1780) 在自动选择 CPU 专家执行前检查已编译扩展、激活函数与权重格式；自动选择不可行时与用户明确强制 CPU／hybrid 的行为不同，后者应显式报错。在已知 pinned host memory 预算下，会先估算专家库，再决定是否拒绝启动或把部分首尾层留在 CPU，避免完整加载之后才发现主存锁页限制。

投机验证的结果也不能只截断文本。[Scheduler._drain_verify](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/scheduler/scheduler.py#L423-L450) 先按结束符与输出上限提交接受 token，归还被拒绝行的缓存，再提交目标模型状态，最后释放完成请求的循环状态槽。[对应测试](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/tests/scheduler/test_spec_drain.py) 用记录器检查先提交后释放的顺序。这类不变量关系到多请求共享状态是否串线，与单次回答看起来正常是不同层次的正确性。

### 5）今日热度：事实与推测
**已确认事实**：最近三个主分支提交依次为 CPU NVFP4 W4A8 优化、[MTP 支持 #844](https://github.com/FlashML-org/FreeToken/commit/dacac5f5fa543247bcda47599d15d9f7470fe135) 和 [gpt-oss GGUF #838](https://github.com/FlashML-org/FreeToken/commit/ea2916d31cf17f13c3d74edcc3683a73fca9ce39)。后两项分别提交于 **11 月 2 日 19:37:09 UTC／11 月 3 日 03:37:09 北京**、**11 月 2 日 16:58:07 UTC／11 月 3 日 00:58:07 北京**。这些是真实近期代码进展，但不能自动认定为 653 today 的传播原因。

最新稳定版 [v0.2.1](https://github.com/FlashML-org/FreeToken/releases/tag/v0.2.1) 发布时间为 **10 月 26 日 03:24:21 UTC／11:24:21 北京**，包含 GGUF 图像输入等功能。另有滚动 [nightly](https://github.com/FlashML-org/FreeToken/releases/tag/nightly)，页面明确说 tag 会移动；此次读到的 wheel 对应 ee43b2a11、构建时间 **10 月 30 日 11:19 UTC／19:19 北京**，不是本次 HEAD，因此不能把 nightly 标签当不可变版本。

开放 [PR #764](https://github.com/FlashML-org/FreeToken/pull/764) 最近更新于 **11 月 3 日 00:23:20 UTC／08:23:20 北京**，讨论 ROCm CPU 专家输入发布与通知之间的可见性，属于正确性边界；[PR #814](https://github.com/FlashML-org/FreeToken/pull/814) 更新于 **00:01:28 UTC／08:01:28 北京**，提议在响应中加入逐请求 timings。两者仍开放，不能把补丁和作者验证描述写成当前 main 已具备。**推测**：本地大模型、Agent 接入和近期推理优化可能吸引关注；暂无足够公开证据解释今日热度。

### 6）对 AI／React／Node／Python／Agent 工程的价值
Python 侧最值得借鉴的是协议适配层、语义事件层和执行调度层的分离；React／Node 产品可借此设计 reasoning／正文／tool-call 的独立流式状态，而非只拼接一段字符串。Agent 工程应额外测取消请求、缓存重建、结构化输出拒绝、MTP 接受／拒绝和模型格式的交叉组合。本项目价值在于研究内存受限服务的完整系统权衡，不能以某张卡上的作者数字保证用户机器的速度。

**实际覆盖／限制**：读取未截断递归 tree、README、pyproject、CLI、离线 LLM、OpenAI 适配、生成层、Scheduler、Engine 的 CPU 可用性／锁页预算路径、MoE layer／cache／pool policy、MTP proposer／runner／rejection、NVFP4 CPU 源码，以及 rejection 与 scheduler drain 测试文件；取得最近 6 commits、HEAD diff、3 个 release 条目和最近 5 条 issue／PR 正文。大文件为完整取回后定点阅读，未逐行审计全部模型与原生后端；测试文件体现作者预期覆盖，未运行测试、安装依赖或下载权重。

## 7. pingdotgg/t3code

### 1）项目数据
- [仓库](https://github.com/pingdotgg/t3code)：今日 **#7，42,093 Stars，3,229 stars today，TypeScript**；昨日#4→今日#7。榜单时点为 **11月3日10:11:24北京／02:11:24 UTC**，累计Stars变化不等于rolling daily涨星。
- 固定[`e0f69e9ea4cb550cb8a395ccc8096d387783b577`](https://github.com/pingdotgg/t3code/commit/e0f69e9ea4cb550cb8a395ccc8096d387783b577)，提交于 **11月3日10:03:56北京／02:03:56 UTC**。[相较昨日dd6c05e](https://github.com/pingdotgg/t3code/compare/dd6c05ec313c6c870c7a7688e87143da5084031d...e0f69e9ea4cb550cb8a395ccc8096d387783b577)前进 **117 commits**，compare文件列表达到 **300项上限**，不能当完整文件审计。

### 2）它解决什么问题
T3 Code让Web、桌面和手机共同控制拥有工作区的Agent服务器，统一provider、Git、文件和会话状态。昨日深入管理员managed policy，今天沿控制面继续看**源码托管token从secret provider按需解析**，以及运行恢复/空闲压缩只读取所需历史。它仍不是单个模型或RAG库；将凭据引用、真正凭据、客户端设置和执行期配置分开，是多provider全栈Agent产品比聊天界面更困难的部分。

### 3）实际实现与数据流
1. **入口与monorepo。** 当前根目录及apps/packages目录包括React Web、mobile、Electron desktop、Node server、contracts、client-runtime、多个provider及secret-provider包。根/server[manifest](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/package.json)的server版本仍是0.1.6，不能据此把main能力等同stable。实际[bin.ts](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/src/bin.ts)优先dispatch document、managed-token及ACP MCP快路径，普通命令动态加载[binCli](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/src/binCli.ts)，后者以Effect CLI/Layer组合运行。这一层不应因读取一个secret就把所有provider都启动。
2. **schema声明秘密位置，而非按字段名猜。** [SettingsSecretValue](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/packages/contracts/src/settingsSecretValue.ts)为literal或SecretReference union，通过annotation识别秘密字段。本次扩展到“单字段”与“按host键索引的record”；secretReferencesInSettings返回field/key slot，withSettingsSecrets只替换目标slot并保留其他host条目。GitHub.com与企业host可各有引用，不应把整张tokens字典覆盖掉。读取schema AST的能力有明确范围，不是任意深层JSON自动识别秘密。
3. **保存字面token和保存引用不是同一条路径。** [settingsSecrets](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/src/settingsSecrets.ts)对literal走secret store/客户端遮罩，对引用保留对象；[sourceControlHostSecrets](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/src/sourceControl/sourceControlHostSecrets.ts)按kind/field/标准化host构造稳定存储名，扫描时不会把引用误当plaintext token。[serverSettings](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/src/serverSettings.ts#L998-L1048)计算新增、删除和保留的secret集合，修改成引用后旧字面secret会进入清理路径。引用本身可在设置中展示，**它仍可能泄露vault、item或host名称，不等于没有任何元数据隐私风险**。
4. **真实consumer按需取值。** [ServerSourceControlHost](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/src/sourceControl/ServerSourceControlHost.ts)分别暴露普通settings.get与getWithSecrets(kind)，后者只解析对应host kind，并把结果供源码托管driver使用；[settingsSecretValue resolver](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/src/secrets/settingsSecretValue.ts)批量读取引用，无法读取时填空串按unset处理，不把错误对象混进credential。没有secret的普通设置读取无需触发解锁。
5. **secret resolver是缓存与用户交互调度器。** [SecretResolver](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/packages/secret-provider-core/src/server/SecretResolver.ts)按provider+reference及配置fingerprint缓存，成功和失败都保留到服务器生命周期结束或显式invalidate；配置变化重新读取。命中不抢semaphore，miss串行化、按provider聚合并去重，以免每次重建反复弹解锁。代价是vault里旋转了token、或先前拒绝解锁后，不能期待自动TTL刷新，需现有refresh/invalidate路径或重启；这正是需要写进运维体验的边界。
6. **1Password批量读取也要防错位与无限等待。** [driver.ts](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/packages/secret-provider-onepassword/src/server/driver.ts)调用op且设cache=false避免后台daemon卡住；多个引用用临时模板和随机separator进行一次inject，校验结果数量与尾部，再按输入顺序映射。每次读上限45秒；批量超时不再逐个等待45秒，普通失败才尝试逐条read。秘密保留原始空白，日志仅写阶段/退出码等信息。模板写的是引用，读取后秘密仍进入服务端内存及下游认证，不是“token永不离开密码库”。

### 4）技术亮点与昨日问题跟进
- **schema到存储到consumer使用同一slot模型**，解决单token扩展为多host map时，UI、secret清理和运行期替换容易不一致的问题。当前实际新提交是[源码托管secret-provider接线](https://github.com/pingdotgg/t3code/commit/84537c4dd976a89b6ec094f43ae3ef7bee12cb1a)，不是今日首次发明整个secret provider框架。
- **缓存失败也有用户体验意义和代价。** 它防止后台任务反复唤起解锁窗口，但会保留失败与旧值；“减少弹窗”与“及时轮换凭据”需要可见刷新协议，不宜盲目复制永久缓存。
- [IdleCompactionService](https://github.com/pingdotgg/t3code/blob/e0f69e9ea4cb550cb8a395ccc8096d387783b577/apps/server/src/orchestration-v2/IdleCompactionService.ts)相较昨日已有实质变化：先取thread，只请求当前run的messages、latest/active/rolled-back runs、活跃turn items、pending requests/transfers及最新usage，减少全历史读取；旧run的迟到completed事件如果覆盖timer，会在循环中改为最新completed run。它仍用thread-keyed FiberMap内存timer，源码明确重启会跳过等待中的compaction；旧[#28490](https://github.com/pingdotgg/t3code/pull/28490)仍closed且未merged。不能把本次读优化或迟到事件修复写成“已恢复重启后timer”。

### 5）今日热度：发布与开放问题
最新已读nightly [v0.1.7-nightly.20261102.4093](https://github.com/pingdotgg/t3code/releases/tag/v0.1.7-nightly.20261102.4093)于 **11月3日03:48:59北京／11月2日19:48:59 UTC**发布，列14项变化，含源码托管secret引用、Cursor compact与Tailscale发现不阻塞启动；前一[4080](https://github.com/pingdotgg/t3code/releases/tag/v0.1.7-nightly.20261102.4080)于 **11月2日21:24:45北京／13:24:45 UTC**发布。正式latest查询仍为[v0.1.6](https://github.com/pingdotgg/t3code/releases/tag/v0.1.6)，发布于 **10月31日18:52:24北京／10:52:24 UTC**。nightly、最新main及stable是三种不同状态。

近5提交分别涉及聊天图片重写后刷新、checkpoint skip-worktree/assume-unchanged处理、过长goal拒绝、project分组恢复和stream时间戳解析；只读了标题/元数据，不把五项全部宣传成已深入验证。开放[PR #29845](https://github.com/pingdotgg/t3code/pull/29845)于 **11月3日10:04:23北京／02:04:23 UTC**提出修复默认分支dirty tree时Push对话框仍提供服务端拒绝的feature-branch操作；[#29846](https://github.com/pingdotgg/t3code/pull/29846)于 **10:07:36北京／02:07:36 UTC**拟让新thread picker遵守手动项目排序，均未计入固定HEAD。作者提供的红绿测试数字不是本轮执行结果。**暂无足够公开证据解释今日热度。** 117 commits、nightly与3,229 stars today是同期事实，不能直接归因给某项feature或作者传播。

### 6）对用户AI／React／Node／Python工程的价值
做多租户Agent或Django/Node后台，值得拆开“设置引用”“存储secret”“解锁和读取”“提供给具体consumer”四层，尤其要定义配置变化、vault轮换、失败缓存与刷新按钮的关系。React表单可从同一schema识别secret slot，防止每个provider自己发明password输入框及遮罩回传规则；本期未审计完整React表单实现，以上是从契约设计推导的可迁移建议。长任务系统则可学习按thread/run ownership限制恢复读取与处理迟到事件，但需另做持久timer恢复，不能靠读取更快来补足重启一致性。

**实际覆盖与限制**：核昨日章节与证据摘要、根/apps/packages/server目录及packages递归树；全仓递归tree两次返回Transport closed，未声称获得完整树。读根/server manifests、bin/binCli、contracts秘密slot、secret resolver与1Password driver、secret映射与source-control接线、IdleCompactionService全文；serverSettings仅存储/清理相关段，另抓取若干外围模块。核117提交compare统计及受300项限制文件表、最近100提交标题/元数据、secret接线commit diff、3 nightly、stable和开放PR正文、#28490状态。未安装、运行、测试、读取真实密码库、连接provider、操作本机或修改仓库。

## 8. shiyu-coder/Kronos

### 1）项目数据
Repository：[shiyu-coder/Kronos](https://github.com/shiyu-coder/Kronos)；今日排名 **8**；**46,031 Stars；857 stars today；Python**。榜单采样：**2026-11-03 02:11:24 UTC／10:11:24 北京**。固定 [67b630e67f6a18c9e9be918d9b4337c960db1e9a](https://github.com/shiyu-coder/Kronos/commit/67b630e67f6a18c9e9be918d9b4337c960db1e9a)，HEAD 时间 **2026-04-13 12:38:49 UTC／20:38:49 北京**。与 11 月 2 日报告的源码 SHA 完全一致，GitHub compare 返回 identical、ahead 0、behind 0、文件变化 0。

排名 **3→8**，Stars **45,452→46,031，快照差 +579**，today **630→857**。这两种增量口径不同，不能把 +579 解释成对 857 的校验失败，也不能把榜单位置下降解释成项目停止增长。本次未发现可确认的新主分支变更或新 GitHub release。

### 2）解决什么问题
Kronos 把金融 OHLCV／成交额等连续序列编码为离散 token，再用预训练自回归模型生成未来序列，试图把基础模型式表示学习用于时间序列预测。公开包提供 tokenizer、预测模型和方便 pandas 输入的 Predictor，也包含微调与 Web UI 示例。它输出的是模型生成路径，不是交易执行系统；本文不据此判断盈利能力，也不将 README 或 issue 内的回测数字当作独立验证。[模型说明](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/README.md)

### 3）实际架构与核心实现
[requirements.txt](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/requirements.txt) 指向 PyTorch、pandas、einops、safetensors，并固定 huggingface_hub 0.33.1；[model/__init__.py](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/model/__init__.py) 直接导出 KronosTokenizer、Kronos 和 KronosPredictor。主数据流可沿 [model/kronos.py](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/model/kronos.py) 追踪：数值特征先经 Linear 与 Transformer encoder 映射到潜变量；BSQuantizer 量化后拆为 s1、s2 两组索引，decoder 再把两组离散码还原成连续特征。

[module.py](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/model/module.py) 中的 BinarySphericalQuantizer、层次 embedding、RMSNorm、RoPE attention、DependencyAwareLayer 和 DualHead 组成核心。模型把分钟、小时、星期、日、月 embedding 加到序列 embedding，先计算 s1 分布，再让依赖感知层以 s1 的 embedding 为条件生成 s2。训练路径既支持 teacher forcing，也支持从第一头分布采样 sibling token；它不是对六个价格／量字段分别做独立回归。

Predictor 要求 OHLC 列，复制 DataFrame 后补缺失 volume／amount，拒绝 NaN；若只有 volume，则用 OHLC 均价乘 volume 估算 amount。历史每列按均值和标准差归一化、clip，再复制 sample_count 份进入生成。auto_regressive_inference 每一步先 decode_s1、采样，再 decode_s2、采样；超过 max_context 后滚动 token buffer。最后 tokenizer decode、对样本路径求均值并反归一化，返回以调用方未来时间戳为索引的 DataFrame。因此未来交易日／时间间隔仍是 API 输入契约的一部分，且默认返回均值路径而非保留所有样本的概率分布。[预测与生成实现](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/model/kronos.py#L389-L560)

### 4）技术亮点与工程边界
本次较昨日新增的是检查深度，不是项目新功能。最需要进一步区分的是两条训练数据路径：[finetune/dataset.py](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/finetune/dataset.py#L95-L130) 已用 lookback 部分计算统计量；但 [finetune_csv/finetune_base_model.py](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/finetune_csv/finetune_base_model.py#L107-L132) 仍对完整 window_data 计算均值和标准差。不能把前一路径的修复推广为“整个仓库已解决归一化泄漏”。同时 [train_predictor.py](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/finetune/train_predictor.py#L95-L110) 的 next-token loss 覆盖移位后的序列，这使归一化统计量与被评分位置的时间关系仍值得单独审查；公开代码不能直接证明未公开预训练过程如何处理这些边界。

第二个问题是推理状态。Predictor.__init__ 只将 tokenizer／model 移至设备，没有显式 eval；no_grad 也不会关闭 dropout。[Issue #415](https://github.com/shiyu-coder/Kronos/issues/415) 报告固定旧版 huggingface_hub 下可能保留训练状态。源码进一步可见 cross-attention 的 is_causal_flag 取 self.training，因此这不只是随机性问题，训练／推理模式还会改变注意力掩码。我们确认了这些源码条件，未重新运行权重来量化其影响。

第三个边界是 [开放 PR #425](https://github.com/shiyu-coder/Kronos/pull/425) 的 RoPE 修复：当前实现按 query 长度建立同一组 cos／sin 给 q 和 k；decode_s2 的单 query 对整段 context 与训练等长输入不同。补丁拟分别对齐 query 末尾位置与 key 全序列，目前仍未合并。另 top_k_top_p_filtering 在 top_k>0 后直接返回，故 top_p 不会与 top_k 叠加生效；多参数 API 需要明说这种优先级，而非沿用其他模型服务的直觉。

[回归测试](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/tests/test_kronos_regression.py) 固定模型／tokenizer revision、CPU seed，明确调用 eval，并比较 256／512 上下文的 CSV 与 MSE。它是可重复输出的有用基线，但既不能替代入口状态测试，也不是对投资效用、样本外稳健性或概率校准的证明。

批量接口还有一个实际限制：[predict_batch](https://github.com/shiyu-coder/Kronos/blob/67b630e67f6a18c9e9be918d9b4337c960db1e9a/model/kronos.py#L562-L680) 要求各序列历史长度一致，逐项检查未来时间戳长度等于预测步数，然后逐条保存归一化统计再堆叠批次。这不是任意变长、多频率序列的通用批调度器。服务端若要动态合批，需要自己按长度与频率分组，并保持结果和输入顺序对应，不能靠填充零值掩盖数据差异。

### 5）今日热度：事实与推测
**已确认事实**：最近三个 merge 都在 **4 月 13 日**：HEAD batch 维度修复为 **12:38:49 UTC／20:38:49 北京**，归一化相关 #234 为 **12:36:38 UTC／20:36:38 北京**，top-k 相关 #232 为 **12:36:00 UTC／20:36:00 北京**。本次 release 列表仍为空，不存在可据此宣称的“今日新版本”。

[Issue #426](https://github.com/shiyu-coder/Kronos/issues/426) 在 **11 月 2 日 00:03:41 UTC／08:03:41 北京** 申请 large 权重研究访问；[PR #425](https://github.com/shiyu-coder/Kronos/pull/425) 更新于 **11 月 1 日 16:06:16 UTC／11 月 2 日 00:06:16 北京**。已实读的 [#422](https://github.com/shiyu-coder/Kronos/issues/422) 与 [#415](https://github.com/shiyu-coder/Kronos/issues/415) 分别更新于 **10 月 29 日 14:56:51 UTC／22:56:51 北京**、**07:53:41 UTC／15:53:41 北京**，讨论预测受归一化统计影响和 eval 状态；这些都是报告者的实验与问题，不等同于维护者已确认所有因果，也不是今日新出现事件。

**推测**：金融基础模型及开源权重可能继续吸引试验者，但目前没有可核验的当日传播来源将其与 857 today 连接起来。**暂无足够公开证据解释今日热度。** 与昨日的差异应写成“榜单快照变化＋补充已存在的源码边界”，不能包装成新发布或已修复。

### 6）对 AI／React／Node／Python／Agent 工程的价值
它适合学习连续数值如何离散化、如何设计层次 token 生成，以及预测服务怎样暴露版本、采样参数、时间戳和归一化规则。Python 服务包装时应将 eval、模型 revision、随机种子、输入频率、缺失值策略和输出是否保留样本写入契约。React 图表或 Node BFF 应清楚标识历史、模型输出及独立评估结果；Agent 只能把模型输出视为待验证研究材料，不能把生成的一条平滑曲线当确定性未来。实际应用还需独立时间外评估、简单基线、泄漏审查及成本约束，本报告不作盈利结论。

**实际覆盖／限制**：重新读取当前完整文件与未截断 tree，包括 README、requirements、导出入口、kronos.py、module.py、两条微调 dataset 路径、train_predictor、回归测试与 Web UI 模型加载入口；读取最近 6 commits、HEAD diff、空 releases、5 条 issue／PR 正文，并与昨日固定 SHA 比较。大文件定点审读，不声称通读全部 examples／训练流程；未下载模型、运行预测、训练或回测。

## 9. kornia/kornia

### 1）项目数据
- Repository：[kornia/kornia](https://github.com/kornia/kornia)；今日排名 **9**；**12,149 Stars，412 stars today，Python**，截面为 **2026-11-03 02:11:24 UTC／10:11:24 北京**。昨日同为第 9，11,832 Stars、101 stars today；总 Stars 截面差 317 不替代 GitHub 的 412。
- 固定 HEAD：[a733fe3b6248652b0a509d002cf452b2167965f0](https://github.com/kornia/kornia/commit/a733fe3b6248652b0a509d002cf452b2167965f0)，时间 **11 月 2 日 21:00:50 UTC／11 月 3 日 05:00:50 北京**。与昨日 ff6774d332d98a7ba78a09d058bb40998d9774d4 的 [compare](https://github.com/kornia/kornia/compare/ff6774d332d98a7ba78a09d058bb40998d9774d4...a733fe3b6248652b0a509d002cf452b2167965f0) 返回 **领先 7 commits、落后 0、81 个变更文件**；既有文档重写，也有具体运行时修复，不把 81 个文件都说成功能新增。

### 2）它解决什么问题
Kornia 把视觉变换、几何、特征检测／匹配、增强与损失函数接到 PyTorch tensor 上，让批处理、设备和梯度能够留在同一条计算管线里。适用场景包括需要每个样本不同变换参数的训练、可微相机几何，以及图像匹配前后处理；单张 CPU 图像的一次固定 resize 并不天然需要它。本期不重复昨天的 crop3d 与 float16 sigmoid 增强概览，而检查形状约定、编译器行为及接口兼容这三类真实增量。[项目入口](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/kornia/__init__.py)

### 3）实际架构与核心实现
1. **它首先是 Python 库，不是视觉 SaaS 或 LLM Agent。** [pyproject.toml](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/pyproject.toml) 要求 Python ≥3.11、torch ≥2.5.1、kornia_rs ≥0.2.0 和 numpy；ONNX、图像、扩散模型另设 extras。当前包入口标记 0.9.1.dev，先导入 filters／geometry，再组织 augmentation、feature、models、onnx 等模块以控制依赖顺序。不能把 main 的修复直接归给已发布的 0.9.0 安装包。
2. **translate／shear 修的是输入语义，不是新算法。** [affwarp.py](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/kornia/geometry/transform/affwarp.py) 现在先将一维的 (2,) 平移或 shear 参数升为 (1,2)，再构造矩阵并交给 affine／warp_affine。此前分量数 2 被当成 batch 数，单张输入可能静默返回两张，三张输入反而 expand 失败；两张输入偶然正常。新实现把“一个共享参数”和“多组逐图参数”区分开，函数及 Translate／Shear 模块一同受益。
3. **对应测试验证形状及等价关系。** [test_affine.py](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/tests/geometry/transform/test_affine.py) 新回归覆盖空 batch、单图、无 batch 维、两图、三图，将 (2,) 输出和显式加 batch 维的参考相比较，并核对输出 shape 与模块结果。它防的不是立即崩溃，而是下游可能仍能继续运行的重复样本错误。这类测试比只测常见 batch=2 更有辨识力。
4. **LightGlue 的早退检查必须数特征，不能数 batch。** [integrated.py](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/kornia/feature/integrated.py) 的 LightGlueMatcher 现在用 desc.shape[-2] 判断是否少于两个特征，支持 (N,D) 或 batch-of-one 的 (1,N,D)；随后补齐必要 batch 维，从 LAF 提取 keypoint／尺度／方向，构建 image0／image1 输入，最后过滤无匹配索引并返回分数和配对。旧检查 shape[0] 遇 (1,N,D) 总是得到 1，静默返回无匹配。此改动并不宣称任意多图 batch 都已支持。
5. **回归测试隔离了适配器和模型权重。** [test_integrated.py](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/tests/feature/test_integrated.py) 用 recording stub 替代会下载权重的 LightGlue 构造器，按描述子行配对，验证两种布局是否到达 matcher 并得到相同结果。它能准确证明 wrapper 的形状处理契约，却不是 LightGlue 匹配精度评测；报告时需要保留这种测试范围。
6. **十次迭代的写法影响编译后的执行。** [distortion_kannala_brandt.py](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/kornia/geometry/camera/distortion_kannala_brandt.py) 先除去内参得到归一化点，再用十步 Gauss-Newton 求角度、tan 映射回无畸变半径，并保留光轴附近和 dtype 处理。此次将常数次数 for 改为计数 while，避免 TorchScript 展开后 CUDA fuser 将重复表达式膨胀；算法仍是十步，不是改用新求解器。[test_distortion.py](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/tests/geometry/camera/test_distortion.py) 连续调用两次，比较 eager 输出并检查优化图中的算子数量，针对的是“第一遍正常、第二遍优化才失败”。
7. **SOLD2 的变化是兼容承诺纠正。** [sold2_detector.py](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/kornia/feature/sold2/sold2_detector.py) 继续接受 dict，转换成 DetectorCfg 后构造 SOLD2Net 和线段后处理；网络输出 junction／line heatmap，再逐图提取交点和线段。最新 HEAD 去掉了将来不会兑现的 dict 弃用告警，并非替换网络或提高检测精度；其坐标输出是 row／col，接 Web 画布的 x／y 时仍需转换。

### 4）技术亮点与限制
本期最突出的主题是**把 convention 变成可执行契约**：轴的意义、共享参数、调用次数、坐标顺序都比 API 名称更影响结果。新 [CONTRIBUTING](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/CONTRIBUTING.md) 明确输入以浮点 tensor 为主，图像通常在 [0,1]，并不追求为所有函数增加整数输入。translate 与 shear 的 align_corners 默认值并不一致；shear 的原始因子也不等同于 Affine 中的 shear 角度，不能只看同名参数就替换调用。

新增 [image_matching 指南](https://github.com/kornia/kornia/blob/a733fe3b6248652b0a509d002cf452b2167965f0/docs/source/applications/image_matching.rst) 公开不同设备和 reference 的选择，包含 eager ALIKED CUDA、CPU SIFT、ratio-test matching 等不占优的情况，并解释硬件、特征预算与计时口径。这里的数字是项目作者测量，本轮没有复测；“PyTorch／GPU”不能推导所有负载更快。README 还明确 CPU half precision 的已知失败，以及 CUDA／MPS half-precision CI 覆盖缺口，不能用 CPU 通过代替 GPU 正确性。

### 5）今日热度：发布事实与因果缺证
最新稳定 [v0.9.0](https://github.com/kornia/kornia/releases/tag/v0.9.0) 仍发布于 **10 月 23 日 18:26:01 UTC／10 月 24 日 02:26:01 北京**，不是今天新发。七个增量提交中，[相机修复](https://github.com/kornia/kornia/commit/64e2ca9918083642641042920099e43bce65766f) 合并于 **11 月 2 日 17:08:49 UTC／11 月 3 日 01:08:49 北京**，[平移／shear](https://github.com/kornia/kornia/commit/532a4bf75a13b2adcf66272cee2722cd6ff9a2ad) 于 **19:51:15 UTC／次日 03:51:15 北京**，[LightGlue](https://github.com/kornia/kornia/commit/507be3d51744460153f696bdb184ad813f1470fe) 于 **19:56:56 UTC／次日 03:56:56 北京**。这是相对昨日真正可确认的运行时更新。

已关闭 [issue #6257](https://github.com/kornia/kornia/issues/6257) 报告第二次 scripted CUDA 调用卡住、主机内存增长；具体内存和耗时来自报告者，不是普遍发生率。已关闭 [#6521](https://github.com/kornia/kornia/issues/6521) 提供了单图重复的形状复现，与当前修复相对应。另有开放 [PR #6542](https://github.com/kornia/kornia/pull/6542)，创建于 **11 月 2 日 21:45:10 UTC／11 月 3 日 05:45:10 北京**，讨论 CUDA float64 下 8-bit 量化边界，不在固定 HEAD 中，不能说已解决；开放 [#6544](https://github.com/kornia/kornia/issues/6544) 的 fuzzy RCC-8 是功能提议，不是现有模块。近期维护与涨星同时发生，但**暂无足够公开证据解释今日热度**。

### 6）对 AI／React／Node／Python／Agent 工程的价值
做视觉 AI 的 Python 后端，可以借鉴“真实业务输入形状＋参考等价关系＋跨执行模式”测试，而不是只跑 smoke test。React／Node 前端与 Python 服务交接时应明确 H/W、x/y、row/col、batch 维、dtype、像素范围和匹配分数方向，把这些写进 API schema；否则一处静默 batch 扩张就可能让队列、标注与结果错位。对 Agent 自动修代码，本期尤其适合训练审查标准：修 wrapper 应测试 wrapper，改编译路径要测第二次调用，作者 benchmark 要保留环境条件，开放 PR 和已发布版本必须分开。实际采用仍应固定版本，并按自己的 CPU／CUDA／MPS 与导出路径验证。

**实际覆盖／限制**：完整递归 tree（1,653 条，未截断）；README、pyproject、顶层入口；integrated 的 LightGlueMatcher、affwarp 的 affine／translate／shear、Kannala-Brandt undistort、SOLD2_detector 构造及 forward，三份对应测试的相关新回归段；image_matching 指南、CONTRIBUTING 更新。读取最近 4 commits、2 releases、昨日 compare 的 7 commits／81 文件清单及相关 patch；#6257／#6521 issue、#6542／#6543 PR、#6544 功能请求正文。未完整阅读每个视觉算子、未下载模型权重、未运行测试／GPU／ONNX／benchmark；没有把作者验证结果记作本轮验证。

## 10. JustVugg/colibri

### 1）项目数据
Repository：[JustVugg/colibri](https://github.com/JustVugg/colibri)；今日排名 **10**；**46,608 Stars；675 stars today；C**。榜单采样：**2026-11-03 02:11:24 UTC／10:11:24 北京**。固定 main 的 [0a5504a1dc64f86fcd0fe7db298b0448c730e7e6](https://github.com/JustVugg/colibri/commit/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6)，HEAD 时间 **10 月 31 日 21:29:12 UTC／11 月 1 日 05:29:12 北京**。相对昨日已交付前十新进入；不能把开发分支中的讨论当作 main 内容。

### 2）解决什么问题
colibri 试图让远大于显存、甚至大于内存的大型 MoE 模型在现有电脑上推理：只有当前路由专家需要被计算，权重可以分布在 VRAM、RAM 和磁盘。它同时提供 C 模型引擎、资源规划、命令行、HTTP 网关和聊天界面，把“权重能加载”延伸到“可被现有客户端调用”。“模型能运行”和“有交互级速度”是不同结论；模型大小、活跃专家数、磁盘与带宽都会影响实际体验。[项目说明](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/README.md)

### 3）实际架构与核心实现
[pyproject.toml](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/pyproject.toml) 提供 colibri-engine 包和 coli 入口；[colibri/cli.py](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/colibri/cli.py) 只是经 runpy 转入 [c/coli](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/coli) 的包装。根 Makefile 转交 c/Makefile，模型家族各自具有 C 引擎与共享头文件，CUDA／Vulkan／Metal 后端也是独立代码。Python 承担启动、模型解析、资源计划和网关，不是热路径矩阵计算主体。

以 serve 为例，cmd_serve 先解析模型 family、检查 gateway adapter 和 KV slot 上限，再把环境与队列参数交给 [openai_server.py](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/openai_server.py)。Engine 类通过 Popen 启动匹配的原生可执行文件，使用 stdin／stdout 帧协议；启动需读到 READY／CAPS，后台 dispatcher 按请求 id 分发 DATA、完成和错误事件。HTTP 层不是无限塞请求：GenerationScheduler 用有界 FIFO 和独立 KV slots 做 admission，满队列／超时返回 429，关闭返回 503，取消与 finally 路径归还 slot，并记录不带 prompt 标签的 Prometheus 指标。

在实际查看的 [c/colibri.c](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/colibri.c) GLM 路径中，一层依次做 norm、attention、残差、post norm 与 sparse MoE／dense MLP。路由选择专家后，命中常驻表或 LRU 缓存便直接使用，miss 则经 expert_load 读取；相邻 gate／up／down 权重可合并为一次读，非相邻布局分别读取，也有 mmap、预取和 GPU 路径。缓存索引验证实际 eid，失效索引退化为 miss，而不是返回错误专家；被后台预读占用的槽也有独立状态。这里分析的是已读 GLM 引擎，不把它的每个细节套用到所有模型家族。

[resource_plan.py](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/resource_plan.py) 从模型 tensor／GGUF 信息、上下文与设备状况估算放置，Linux 可用 RAM 取宿主 MemAvailable 与 cgroup 剩余额度的较小者。它区分“测不到”“确实为零”“格式错误”，不会把容器配置读取失败都当成无限内存。这说明资源计划不仅是 GUI 显示数字，而是启动前的约束输入。

### 4）技术亮点与工程边界
专家缓存有很具体的抖动控制：[tier.h](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/tier.h) 要求热度超过冷项约 25% 再加固定余量才替换，并先扩宽计数再加阈值，避免饱和整数回绕。LFRU 让频次为主、近期访问打破接近的比较。另 [expert_store.h](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/expert_store.h) 定义 lookup／release 成对 lease，不允许复制活跃 view，prefetch 不得驱逐仍被借用的槽；[registry](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/expert_store_registry.c) 的默认实现接到 DeepSeek V4 存储路径。这是可扩展接口，不表示所有旧引擎都已统一到同一种存储实现。

Agent 多轮性能还取决于状态复用。[pin_pool.h](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/pin_pool.h) 保留多个嵌套前缀快照，选最深的严格前缀，token id 与末端 logits 一起保存；恢复者仍须确认对应 KV 行存活。它与短请求插入时的 conversation parking 配合，避免标题／摘要调用覆盖长对话状态。[test_pin_pool.c](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/tests/test_pin_pool.c) 和 [test_glm_park.py](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/c/tests/test_glm_park.py) 分别覆盖前缀匹配／存活性与短请求后恢复对话的预期，不等于本次已经运行它们。

前端必须区分两套目录：[web/package.json](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/web/package.json) 确认旧 dashboard 使用 React／Vite；新 [ui/server.py](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/ui/server.py) 则服务单页 index.html，并用 Python 标准库代理 HTTP／SSE，另将 Responses 请求转给 shim。不能仅见 package.json 就说新 UI 也必须 Node 构建。UI 中模型切换又涉及真实进程生命周期，属于需要特别测试的控制面，不只是前端按钮。当前代理代码会过滤逐跳头，并把响应按 chunk 透传，但阻塞读取、断开时机与连接清理仍要组合验证；下面的开放修复正说明单看“支持流式”标签无法判断取消语义是否完整。

### 5）今日热度：事实与推测
**已确认事实**：稳定版 [v2.1.0](https://github.com/JustVugg/colibri/releases/tag/v2.1.0) 于 **10 月 31 日 12:50:50 UTC／20:50:50 北京** 发布，列出 GGUF 扩展、CUDA chains、新聊天 UI 和长上下文／Agent 状态复用。release 的速度表有明确硬件和请求条件，部分取两次运行较好值；本文只把它当作者披露，不把其中数字移植成通用性能保证。HEAD merge 在该 release 后，包含站点更新及 Qwen3.6 MTP 文案纠正：需要 Q36_MTP=1，不能写成所有场景默认开启。[HEAD 差异](https://github.com/JustVugg/colibri/commit/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6)

近期开放 [PR #2559](https://github.com/JustVugg/colibri/pull/2559) 在 **11 月 2 日 21:02:58 UTC／11 月 3 日 05:02:58 北京** 提议把 Qwen3.8 CUDA MTP 更多计算留在卡上，标题有加速数字，但仍未合并。控制面还有 [#2560](https://github.com/JustVugg/colibri/pull/2560)，**11 月 2 日 21:18:41 UTC／11 月 3 日 05:18:41 北京**，针对毫秒时间戳 job id 冲突；当前 [ui/models.py](https://github.com/JustVugg/colibri/blob/0a5504a1dc64f86fcd0fe7db298b0448c730e7e6/ui/models.py#L1037-L1043) 确实仍以毫秒生成 id。另 [#2562](https://github.com/JustVugg/colibri/pull/2562) 于 **11 月 3 日 01:42:52 UTC／09:42:52 北京** 更新，提议回收已退出的子网关，避免 Linux 僵尸进程使 /proc 存在检查等满停止期限。我们已对照当前停止循环，但未复现或认定补丁已生效。

[PR #2558](https://github.com/JustVugg/colibri/pull/2558) 更新于 **11 月 2 日 22:48:34 UTC／11 月 3 日 06:48:34 北京**，还区分了 TCP reset 与仅关闭写半边的合法客户端，提醒“浏览器停止”等同“所有上游阻塞立即释放”并非理所当然。**推测**：近期发布与本地大模型定位可能有助传播；但目前未找到将这些事件与 675 today 建立因果的证据。**暂无足够公开证据解释今日热度。**

### 6）对 AI／React／Node／Python／Agent 工程的价值
对 AI 系统开发，最有价值的是“内存分层＋专家生命周期＋状态复用”如何进入真实服务，而不是单独比较一个 GEMV 数字。React／Node 团队可学习能力握手、流式事件、有限队列和 job id 的可靠性要求；Python 团队可研究轻量网关与原生子进程间的帧协议、取消和重启。Agent 客户端尤其应验证主对话与标题／摘要／工具请求交错时的 KV 所有权，以及不同模型对 tools、vision、Responses 的实际能力，不能根据一个统一 API 名称推断完全兼容。

**实际覆盖／限制**：读取未截断 tree、README、两个 Python 包入口、两层 Makefile、c/coli、openai_server、resource_plan、GLM colibri.c 的缓存／expert I/O／forward 片段、tier／pin_pool／expert_store／registry、三个相关测试文件、新 UI server／models／Responses shim 与旧 web manifest；取得最近 6 commits、HEAD diff、3 个 releases 和最近 5 条 PR 正文。大源码完整取回后定点读，未全面审计各模型或 GPU kernel；未编译、安装、下载权重、运行测试或独立复核性能。

## A. 今天最值得深入看的3个项目

1. **claude-mem：先看导入与上传的同意链。** 建议连读 [SetupScan](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/prompt-import/setup-scan.ts)、[React scan-screen](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/ui/my-work/src/setup/screens/scan-screen.tsx)、[HostedIntent](https://github.com/thedotmack/claude-mem/blob/02584c4ac9d92fea45adf5c61e22c546b5738621/src/services/work-view/hosted-intent.ts)。它把真实隐私修复映射到数据范围选择、状态迁移和网络调用，适合RAG导入、Agent记忆及批量文档处理产品。如果使用过受公告描述影响的旧版browser setup，应先核自己的版本与操作记录，再判断既往数据如何处理；更新客户端本身不会删除此前上传。本报告未核查用户是否安装或受影响。
2. **vercel-labs/agent-desktop：学习执行前如何证明引用仍有效。** 重点看 [ref_capture_proof](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/refs/ref_capture_proof.rs)、[resolve_saved_ref](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/refs/resolve_saved_ref.rs) 与 [interaction_lease](https://github.com/vercel-labs/agent-desktop/blob/31b757a990a1189c9df8128df10e8df2ee5e15e1/crates/core/src/session/interaction_lease.rs)。对电脑操作Agent，拒绝歧义、保留观察范围并在动作前重验身份，比单纯追求更多工具更有学习价值。当前VM sandbox仍为开放提案，不应把它当既有隔离保证。
3. **FreeToken：学习受内存约束的推理服务怎样串起协议与执行。** 重点看 [generation.py](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/server/generation.py)、[scheduler.py](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/scheduler/scheduler.py)、[moe.py](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/layers/moe.py) 和 [spec/runner.py](https://github.com/FlashML-org/FreeToken/blob/3d23551c5b43b61ef26e24cb86a22ff550e502a3/python/freetoken/spec/runner.py)。先理解取消、资源回收、专家缓存与草稿验证，再评估本机速度；需要严格JSON Schema的Agent尤其应先看API明确拒绝的参数。

## B. 今天的技术趋势

仅概括本次前十实际阅读样本，不由单日榜单推断长期行业走向。

- **Agent执行越来越依赖可检查的状态与身份。** agent-desktop把快照引用与当前UI身份分开验证；T3 Code把secret引用、解锁缓存、消费端取值分层；claude-mem把本地扫描与云上传拆成状态机。共同值得借鉴的是每一步都有明确输入范围和失败语义。
- **本地大模型的重点是系统资源调度。** FreeToken的CPU/GPU专家切分、缓存与投机验证，colibri的VRAM/RAM/磁盘分层、lease和KV前缀保存，都说明“放得下权重”只是第一步。不同模型、缓存命中和硬件条件不能被一个通用速度数字替代。
- **兼容性需要落实到具体契约。** FreeToken兼容接口仍拒绝某些结构化输出参数；colibri区分模型能力与网关支持；Kornia的单样本形状修复显示张量维度也是契约。对全栈Agent接入，除了成功返回文本，还要测shape、取消、错误和恢复。
- **文档、界面与保护机制需要对照实际接线。** claude-mem默认勾选工具与独立analytics选择影响用户理解；Game Studios仍有未合并的校验修复；colibri旧React目录不等于当前UI实现。资源清单或配置文件可提供线索，不能替代对真正执行路径的阅读。

## C. 与昨天相比

昨日基线为实际交付的11月2日报告，抓取北京时间10:36:46（UTC02:36:46）；今日为11月3日10:11:24（UTC02:11:24），相隔23小时34分38秒。不能把两个总Stars截面相减当作GitHub today指标。

| Repository | 昨日→今日 | 变化 |
|---|---|---|
| vercel-labs/agent-desktop | 前十外 → 1 | 新进入本报告前十 |
| thedotmack/claude-mem | 1 → 2 | 下降1位 |
| D4Vinci/Scrapling | 前十外 → 3 | 新进入本报告前十 |
| hyprwm/Hyprland | 前十外 → 4 | 新进入本报告前十 |
| Donchitos/Claude-Code-Game-Studios | 8 → 5 | 上升3位 |
| FlashML-org/FreeToken | 前十外 → 6 | 新进入本报告前十 |
| pingdotgg/t3code | 4 → 7 | 下降3位 |
| shiyu-coder/Kronos | 3 → 8 | 下降5位 |
| kornia/kornia | 9 → 9 | 位置不变 |
| JustVugg/colibri | 前十外 → 10 | 新进入本报告前十 |

- **5项新进入**：agent-desktop、Scrapling、Hyprland、FreeToken、colibri。这仅是相对于昨日观察前十，不等于今日首次发布或历史第一次上榜。
- **5项连续**：claude-mem、Claude-Code-Game-Studios、t3code、Kronos、Kornia。至少连续两个有证据的观察日上榜；不凭印象虚构更长连续天数。
- **5项离开本次前十**：Lightpanda、OpenMausBot、public-apis、Handy、AiSOC。未据本次前十去判断它们更低名次、质量、是否停更或整体降温。

### 连续项目中真正发生了什么

- **claude-mem：76个新增提交、270个变更文件。** 昨日报告后发布v15.8.3隐私修复及v15.9.0；今日重点核对了同意面板到网络发送的完整接线、read worker与remote URL校验。昨日开放的OpenRouter #5267已合并且存在一次特定重试实现。这是可更新的旧判断；既往上传不会被客户端升级删除，仍是明确限制。
- **T3 Code：117个新增提交，返回文件表达到300项上限。** 重点新接线为按host索引的secret引用及实际消费端解析。IdleCompactionService已有读取范围和迟到事件处理变化，但内存timer重启丢失的限制仍在，不能说恢复问题已解决。nightly更新不等于stable更新。
- **Kornia：7个新增提交、81个变更文件。** (2,)共享变换参数、LightGlue batch-of-one描述子和scripted相机迭代有实际修复；SOLD2更正弃用提示。昨天关注的单图重复问题已能与当前代码对应，稳定release仍是v0.9.0。
- **Claude-Code-Game-Studios：同一SHA，0提交／0文件变化。** 新出现的review-receipts路径前缀碰撞和多行blocker解析问题仍是开放PR；本期增加源码对照，不冒充主干修复或新发布。
- **Kronos：同一SHA，0提交／0文件变化。** 本轮进一步区分Qlib与CSV微调归一化路径、训练／推理状态及采样参数优先级。这是对已有实现的认识补充，不是今日代码改变；没有新增release。

各项固定SHA、compare、发布和问题链接已放在对应项目中。未获得昨日已读SHA的新入榜项目不制造代码日差。相对昨天样本，本次新增桌面无障碍操作、Python网页采集、Wayland合成器与两种内存分层推理系统；“本地推理”成为本次前十更集中的主题，但不能据一天榜单推导行业长期迁移。
