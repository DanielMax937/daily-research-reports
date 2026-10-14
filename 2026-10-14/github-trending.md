# GitHub Trending 源码深读日报

## 2026年10月14日 · 北京时间

今天需要分开的三件事：主线真的改了什么、工具文字承诺是否符合实现、一个操作从提交到真正交付经过哪些状态。最值得跟进的实质增量包括REA的证据/查询契约、God’s Eye View的街景provider与GBFS名称修复，以及diagram-design的CSS导出修正。context-mode只更新统计、AirLLM只更新星图、ArtCraft主线完全未动，不能用热度增长制造代码进展。

研究目标是官方Daily、All languages的前10。**本次官方页面实际呈现9个仓库，下文完整研究这9项；第10项未取得，不补榜、不用搜索或总stars排序替代，也不声称已覆盖完整前10。**

## 范围、时间与证据口径

- 唯一排名来源：[GitHub Trending当前官方页面](https://github.com/trending)。在dot云浏览器中直接打开并读到页尾，筛选明确为Repositories、Spoken Language: Any、Language: Any、Date range: Today。采用**2026-10-14 02:53 UTC，即北京时间10:53**读取的同一页面快照；时间精度为分钟
- 页面正文只有9个仓库article，之后即页尾。网页文本读取也返回相同9项和顺序，但累计stars略旧，**没有把它的计数混进下面的浏览器快照**。本轮没有HTTP响应Date或GitHub内部榜单计算时间，不能声称数据恰好在10:53刷新；能确认的是当时浏览器实际呈现内容
- 累计stars、stars today、顺位及榜单语言均来自同一快照。stars today是GitHub展示字段，时间窗未获证实，不能等同北京时间自然日或两个日报累计stars的差。排名没有按stars today自行重排
- 昨日基线是已完整读回且核对内容一致的[2026-10-13固定归档](https://github.com/DanielMax937/daily-research-reports/blob/c153427620f4316c779ffa7419381f76fbd81be4/2026-10-13/github-trending.md)。昨日也只有9个可见项目；“新增”“未见”均指两份报告的可见样本，不能推断完整前10的首次进入或退出
- 源码读取稍后完成，每仓固定完整commit SHA。README、设计文档、Skill指令、可执行源码、测试源码、PR作者测试报告分别对待；长文件明确选读，未全仓审计。没有安装依赖、执行第三方仓库代码、下载模型、调用付费供应商或复现benchmark
- 研究仓库保持只读。唯一获授权的外部写入是本报告的公开Markdown归档；不修改这些项目、不star、不发issue或PR、不使用用户电脑。正文只使用本轮公开资料，不含私密会话、账户凭证或内部工作记录
- “未找到足够直接证据解释今日热度”是实质结论。近期功能合并、release或讨论与增星同时出现，不代表已经证明因果；维护者关闭问题也不等于本轮独立复现修复

### 同一快照的实际顺序

| 顺位 | 项目 | 页面语言 | 累计stars | stars today |
|---:|---|---|---:|---:|
| 1 | [morluto/rea](https://github.com/morluto/rea) | TypeScript | 211,533 | 54,679 |
| 2 | [bilawalsidhu/gods-eye-view](https://github.com/bilawalsidhu/gods-eye-view) | JavaScript | 55,558 | 1,961 |
| 3 | [debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio) | Python | 63,623 | 1,748 |
| 4 | [mksglu/context-mode](https://github.com/mksglu/context-mode) | TypeScript | 28,336 | 969 |
| 5 | [cathrynlavery/diagram-design](https://github.com/cathrynlavery/diagram-design) | HTML | 54,313 | 1,815 |
| 6 | [vercel-labs/skills](https://github.com/vercel-labs/skills) | TypeScript | 34,590 | 190 |
| 7 | [lyogavin/airllm](https://github.com/lyogavin/airllm) | Jupyter Notebook | 38,392 | 1,001 |
| 8 | [storytold/artcraft](https://github.com/storytold/artcraft) | Rust | 25,935 | 4,081 |
| 9 | [xtool-org/xtool](https://github.com/xtool-org/xtool) | Swift | 9,521 | 1,198 |

第10项：未取得。下面顺序严格沿用官方页面，不按技术价值或日增重排。

## 1. [morluto/rea](https://github.com/morluto/rea)

### ① 元信息与固定版本

- 官方同一日榜快照：第1，TypeScript，211,533 stars，stars today 54,679；默认分支 main，MIT。热度数字沿用2026-10-14 02:53 UTC官方页面，不以稍后仓库API替换
- 本轮固定完整SHA：[d901561640121272bf1498d85e38e1ac8b3f5793](https://github.com/morluto/rea/commit/d901561640121272bf1498d85e38e1ac8b3f5793)，2026-10-14 02:37:10 UTC
- [package.json](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/package.json)仍为 rea-agents 6.4.0；最新正式Release仍是10月11日03:58 UTC的 [rea-agents-6.4.0](https://github.com/morluto/rea/releases/tag/rea-agents-6.4.0)。本节主干增量不能直接写成npm已发布能力
- 对昨日固定 a2d8b94dd50dab8d966239dd63ab84718aa8b4b4 的[真实compare](https://github.com/morluto/rea/compare/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4...d901561640121272bf1498d85e38e1ac8b3f5793)：ahead 383、behind 0；返回文件列表达到300上限，不能将它当完整变更清单。本轮读取最近100条提交元数据后，选取证据投影、输入边界及效率实验深入核读，未逐条审计383次提交

### ② 它解决什么问题、给谁用

REA把本地二进制、JavaScript/Electron应用、移动应用、数据库与录制网络数据的分析能力接到CLI和MCP，让编码Agent根据可追溯观察继续调查、解释和重建功能。不同分析器的支持平台和依赖各异；静态读取与会启动或交互目标的运行观察是不同操作。它适合有权分析目标的开发者和Agent工具作者，价值在于保留来源、身份和未知项，而非保证把任何应用完整还原。[README定位与能力表](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/README.md#L59-L220)

### ③ 架构、依赖与真实控制／数据流

主干是Node/TypeScript，要求Node ^22.19.0、^24.11.0或>=26；固定依赖包括MCP client/server 2.3.1、Zod 4.4.3、Babel 8.0.4、Playwright-core 1.58.2、zip.js、xmldom及saxes；Frida为可选依赖。底层原生、Java及Python工具按分析目标另行需要，不能把“TS项目”理解为所有功能只装一个JS包便可工作。[依赖清单](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/package.json)

1. **工具调用有会话归属，产物有留存与交付两个阶段。** main快照环境、解析配置、建立BinarySession，再启动stdio transport并注册清理；通用handler把取消信号交给operation，在session admission范围内执行、记录完整或部分Evidence，再按契约交付。超出MCP预算时返回明确的可恢复资源错误，只有真正保留了源证据时才提供相应恢复建议，不把截断结果伪装成完整成功。[入口](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/main.ts#L50-L89) · [handler](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/server/contractToolHandler.ts#L59-L93) · [admission包装](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/server/admittedToolOperation.ts) · [预算与恢复](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/server/toolResult.ts#L155-L206)
2. **分析视图不是再跑一次目标。** retained-evidence按精确ID从当前会话取回，拒绝缺失或身份不符；inline Evidence先验数据形态再解析。投影继续携带parent ID、操作、subject digest及limitations，摘要前必须具备完整源的留存能力；有路径模板推断时，整套API-surface的分页都标为inferred，而不会把某一页“看着普通”的分组标成纯观察。[引用解析](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/EvidenceInputResolver.ts#L12-L43) · [投影与留存](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/analysisView/AnalysisViewService.ts#L52-L158) · [派生Evidence](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/analysisView/AnalysisViewService.ts#L250-L294)
3. **今日深入核读的HAR→API-surface链路。** 先检查parent operation、HAR格式、敏感值声明，再按method→origin→path template→segment rule分组；数字、UUID、长hex、合法ISO日期可变成推断占位符，并记录实际值、源record ordinals、状态/MIME及排除理由。路径直接保留录制字符串，避免WHATWG的dot-segment规范化把不同原始路径折叠；查询参数名另按URLSearchParams语义解码。聚合完成后排序和分页，group coverage与源records coverage分开。[视图契约与HAR门禁](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/webNetworkApiSurfaceView.ts#L14-L158) · [聚合器](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/WebNetworkApiSurfaceAccumulator.ts#L254-L512) · [保留原始路径](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/recordedTransportUrl.ts)

### ④ 实际新变化、技术价值与边界

- **新增“观察到的参数名”，不是自动生成完整API schema。** [合入提交dd36b4a](https://github.com/morluto/rea/commit/dd36b4a8a0c2c93216961f351856d54dd23e7156)增加可选include_query_parameter_names；默认不输出该字段，开启后只保留去重名称及各自原始序号，不复制查询值或fragment。空名称、Unicode、加号与百分号解码的区别被测试覆盖；记录顺序不会被数值排序重写。字段不宣称必填、类型、完整性或handler身份。[契约及源码](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/webNetworkApiSurfaceView.ts#L14-L51) · [反例／兼容测试](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/webNetworkApiSurfaceView.test.ts#L37-L128)
- **新增输入行为边界。** [278d7fb提交](https://github.com/morluto/rea/commit/278d7fb284124438eed1da3d248ea2a764dc67bf)在summary、capture和api-surface共用解析路径中先检查对象原型、循环与property descriptor，拒绝getter/setter而不读取其值。测试要求恶意getter从未触发，同时普通Evidence仍可进入三类视图。这是进程内调用者对象的防御，不是“所有不可信JS都有安全沙箱”的证明，也不意味着普通网络JSON能携带getter。[实际门禁](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/analysisView/AnalysisViewService.ts#L159-L247) · [测试](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/analysisView/AnalysisViewService.test.ts#L432-L468)
- **资源预算同时算暂存与留存。** accumulator在schema clone、hash、URL/query解析和组变更之前预留表示层成本；临时与留存数据合计限96 MiB，超限不返回局部视图。代码明确这只是保守的表示预算，不是V8 heap/RSS硬限制。api-surface目前仅接受HAR，SAZ／mitmproxy／qlog不支持；敏感声明没有保留到可重新校验程度时直接拒绝，不能因为昨日新增SAZ读取就推断这条派生视图也支持SAZ。[预算实现](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/WebNetworkApiSurfaceAccumulator.ts#L86-L226) · [明确边界](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/docs/web-network-captures.md#L272-L301)
- **值得保留的负结果：分页不一定省token。** 今日合入的[小PCAP实验](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/experiments/analysis-efficiency/pcap-small-captures.md#L1-L119)记录两份25,803／47,804字节录制、固定问题和8次SDK工作流：summary+URI page总JSON约17.2–17.5KB，complete约7.5–7.6KB。4次实际模型任务的两个配对中，summary/page总输入分别增加50.92%和50.54%，耗时一快一慢，未证明通用速度收益。因此保留complete默认，不新增生产优化。这是仓库作者已记录、运行于旧固定测量SHA的实验，本轮只读未复现；不能宣称本轮d901实测，也不能推广到大录制或其他问题。[新增实验提交](https://github.com/morluto/rea/commit/c7105d9723c835b5e0122f5fc6cfbea86265c349)
- **更新昨日风险状态。** [issue #2454](https://github.com/morluto/rea/issues/2454)已于10月13日04:06 UTC关闭，12项清单全部勾选。不能再照抄“该12项仍开放”；本轮未逐项重跑公共CLI/MCP来独立证明修复。另有[按family裁剪MCP工具目录的PR #3026](https://github.com/morluto/rea/pull/3026)仍开放，不能作为这个固定SHA已经具备的能力

### ⑤ 今日热度：事实与推测分开

**事实：** 官方日榜第1、今日54,679 stars；相邻固定版本间383次提交，主干同时出现功能、契约、文档和测试修正。仓库还出现庆祝200,000 stars的提交，这只能证明维护者记录了增长，不能解释增长来源；6.4.0不是今天刚发布。

**推测：** 将多类软件分析入口接到Agent并保持可追溯证据，可能符合编码Agent用户的兴趣；但本轮没有当日传播渠道、流量来源或star归因数据，无法证明某个提交、文章或账号造成热度。**未找到足够直接证据解释今天为何上榜。**

### ⑥ 对AI、Agents、RAG、MCP与全栈／数据工程的具体价值

- **Agent／MCP：** 可复用Evidence父子引用、取消与session admission、超预算后的可恢复交付；优先优化完成一次真实任务的总成本，再决定summary、分页和工具目录策略
- **RAG／数据工程：** HAR→参数名/路由候选适合作为可检索的观测索引；保留ordinal、原始URL、未知/排除原因和源digest。不要把一次录制的候选自动升级为OpenAPI真值、全站路由全集或接口必填参数
- **React／Next.js／Node：** 有权调查自己的打包JS/Electron应用时可评估；搭建分析UI可借鉴summary→detail和父引用回读。这里研究的是后端分析与协议，不是一个可直接安装的React组件库
- **Python／Django：** 可借鉴“先承认输入规模、再clone和聚合”的worker边界，以及保留完整证据后再生成摘要；Node进程和底层引擎仍需单独部署。历史URL只应作为数据处理，不应因为构建索引而自动访问

读取覆盖：完整目录4076项，truncated=false；取得17个固定SHA文件，README定位／依赖、main、handler、delivery、admission包装与所有权选择、EvidenceInputResolver、AnalysisViewService及其测试、API-surface schema／accumulator／测试、recordedTransportUrl、抓包文档、效率实验README与小PCAP报告。短模块完整阅读，大文件按上述函数、契约、预算及反例范围深入选读；另读最近100条commit元数据、3条release、compare、两个重点commit diff、#2454及近期issue/PR状态。未安装、执行仓库代码、运行测试或全仓审计。

## 2. [bilawalsidhu/gods-eye-view](https://github.com/bilawalsidhu/gods-eye-view)

### ① 元信息与固定版本

- 官方日榜第2；JavaScript；55,558 stars；1,961 stars today。相对昨日报告仍第2
- 固定完整SHA：[132b9e96dc1491e5db8bf949b1560f4561c925c3](https://github.com/bilawalsidhu/gods-eye-view/commit/132b9e96dc1491e5db8bf949b1560f4561c925c3)，2026-10-13 22:39:26 UTC；与昨日8b8ccc9a…比较，ahead 18、behind 0、62个净变更文件。[版本比较](https://github.com/bilawalsidhu/gods-eye-view/compare/8b8ccc9a81379e8b40d4be67610570ee5b159512...132b9e96dc1491e5db8bf949b1560f4561c925c3)
- package仍0.2.1，最近GitHub Release仍是10月3日的[v0.2.1](https://github.com/bilawalsidhu/gods-eye-view/releases/tag/v0.2.1)；本次新增在main，不能等同于旧发行包。运行依赖原生ES modules、Cesium、Vite、Node，Node范围为>=24.14且<25或>=26且<27；不是React项目。[package.json](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/package.json)

### ② 它解决谁的问题

它把飞机、船舶、卫星、天气、公开摄像头等数据放到同一个可探索的三维地球，并为语音Agent和MCP提供查询及视图控制。适合公开地理数据分析、可视化教学和空间信息产品原型。车辆流动有模拟成分，摄像头姿态和火箭轨迹存在估计，视觉上的“情报台”不代表每个像素都是实时观测。[定位与数据边界](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/README.md#L41-L53)

### ③ 实际架构与控制、数据流

1. **启动与供应商注入。** main调用createStandaloneApplication；Street Level应用组合层把Mapillary和新增Google provider交给createStreetLevelLayer，并注入拾取、输入归属、渲染和地表服务。共享registry校验provider ID、pick前缀不冲突、必需字段及分享链接长度；核心拥有选择状态和viewer host，provider拥有图像查询及播放器。因此新增一家图片服务不必复制整个图层状态机。[启动](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/main.js) · [应用装配](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/app/layers/streetLevel.js) · [provider契约](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/registry.js)
2. **今日新增Google Street View有可执行的能力门槛。** provider声明默认关闭、需要Google Maps key、只在指定Google 3D地图栈可用、无coverage和日期过滤；不是给所有地图塞一个iframe。最近全景查询按需加载Maps JavaScript API，使用Google户外影像；ZERO_RESULTS返回null，认证失败、取消与10秒无响应分别终止。页面级Promise复用脚本加载；取消后即使脚本迟到，也不会继续发起已经过期的查询。[provider](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/index.js#L23-L181) · [延迟加载](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/mapsLoader.js)
3. **显示完成与数据到达分开。** viewer以pendingOpen和generation排除“关闭/卸载之后才完成”的异步结果；open等待全景状态或位置事件，20秒未回答会结束等待。日期、作者、地址另走可重试的元信息查询；日期精度标为month，而不是把月份补成某一天后冒充日级观测。核心在新操作时abort最近查询，切换provider会卸载旧viewer。[viewer完整实现](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/viewer.js) · [核心取消与切换](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/index.js#L283-L351)
4. **另一个已合入增量是GBFS名称规范化。** stationName同时接受旧字符串和v3的Localized String数组，优先非空英文（含en-*），其次首个可用翻译，再尝试short_name；无名称仍保留有效站点。修改的是共用parser，MCP的get_bike_share也导入它，避免地图显示修好、Agent仍回答“[object Object]”。没有把这次小修写成完整GBFS v3支持。[名称处理](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/sources/gbfsStations.js#L54-L102) · [工具调用同一parser](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/tools/queries/mobility.js#L1-L7) · [反例测试](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/sources/gbfsStations.test.mjs)

### ④ 技术亮点、已确认增量与边界

- 两个变化分别由已合并[PR #966](https://github.com/bilawalsidhu/gods-eye-view/pull/966)和[PR #1120](https://github.com/bilawalsidhu/gods-eye-view/pull/1120)支撑，并与固定源码核对。#1120的测试覆盖坏名称、缺版本、区域语言标签、不修改原输入等情况；PR报告12项parser回归以及浏览器QA通过，本轮没有运行这些测试
- Street View的费用与展示范围被落实成defaultOn、requiresMapStack和首次使用才加载脚本。这里确认的是项目实现的供应商约束，不能据此保证其他产品复用后自动符合供应商条款；地图、数据及第三方素材也不随源码MIT许可一起放开。[约束字段](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/index.js#L65-L83) · [数据与素材许可说明](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/LICENSE#L25-L62)
- **“show me X on Street View”尚未合入。** [PR #1113](https://github.com/bilawalsidhu/gods-eye-view/pull/1113)提出语音/文本复合动作及携带地点的分享链接，读取时open、merged=false。不能把PR正文中的演示和测试写成当前main已有能力；Energy Atlas也是新issue提案，不是本轮可用功能
- MCP已有的协议包装会把结果分别交给summary、JSON文本及structuredContent；未知异常不直接暴露内部细节。这种“结果给模型和UI各自可消费的表示”适合移植，但本轮没有验证完整部署的多租户鉴权。[协议输出和错误分支](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/tools/mcp/protocol.js#L107-L155)

### ⑤ 今日热度：事实与推测

**事实：** 当前官方快照第2、今日+1,961；昨天快照之后合入Street View和站名修复；正式release未更新。README存在历史视频传播和8月Trending说明，它们不能直接解释10月14日的增星。

**推测：** 三维地球与真实数据、可切换街景及Agent交互容易形成可演示的作品，可能持续吸引开发者。未取得本日传播来源、访问转化或star归因证据，不能认定两次合并造成今天上榜。

### ⑥ 与你的项目的具体关系、建议读哪里

- **Agent/MCP与数据工程：** 先读gbfsStations.js，再读mobility.js和mcp/protocol.js。把脏数据清洗放在图层与工具共用的源边界，并给结果保留缺失、过期、来源和精度，避免自然语言把未知改写成确定
- **React/Next.js/Node：** 借鉴registry→provider→viewer的协议分层和取消机制，把React仅作为状态投影；地图SDK实例和异步生命周期单独管理。Google key是浏览器可见配置，需要提供商侧限制和预算，不能当服务端秘密藏在前端环境变量
- **Python/Django与RAG：** 后端可用同样schema组织实时观测，RAG引用观测时间、来源与精度；街景照片日期不能变成“当前路况”。本仓不是向量数据库，也不能替代检索权限与更新策略
- **本轮实读范围：** 完整目录1926项；README定位/Street Level/架构段、package、LICENSE、CHANGELOG近期段；main与Street Level装配/registry、Google四模块完整读取，图层index选读组合/取消/切换，GBFS parser及测试、mobility工具和MCP protocol关键段。读取最近5个commit、3个release及上述3个PR；没有启动地球、使用供应商key、运行测试或复现PR声称的性能

## 3. [debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio)

### ① 元信息与固定版本
- 本期同一官方日榜快照（2026-10-14 02:53 UTC）：第3，Python，累计63,623 stars，stars today为1,748
- 默认分支main；本轮固定完整commit：[fdeeec5b0bcbefc9f3f576bb3689686feed8e569](https://github.com/debpalash/VoiceStudio/commit/fdeeec5b0bcbefc9f3f576bb3689686feed8e569)，2026-10-13 21:02:46 UTC，合并桌面商店发行基础工作
- 应用许可证AGPL-3.0；[主干清单](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/pyproject.toml#L5-L15)写0.5.7，而最新正式发布仍是2026-09-23的[v0.5.6](https://github.com/debpalash/VoiceStudio/releases/tag/v0.5.6)。本文不会把主干实现全算作该安装包已有功能
- 昨日报告未出现本项目；“新面孔”仅指进入本轮报告，不等于今天创建，也没有可作逐行增量对比的昨日固定版本

### ② 解决什么问题
VoiceStudio把声音克隆、声音设计、视频配音、转写、听写和长篇有声内容制作放进一个本地优先工作台，并用API和MCP向Agent开放。价值是将模型选择、声音档案、硬件适配、任务执行和音频资产放到同一流程，而不是让用户分别拼接多个模型脚本。README宣称覆盖646种语言，但这是项目层面的覆盖口径，各引擎有自己的语言、设备与参考音频能力；本轮未验证646种语言的质量。远程服务属于可选路径，“本地优先”不能被理解为所有配置都不会联网。[README.md](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/README.md)

### ③ 源码结构与真实控制／数据流
先读取固定SHA的完整递归目录，再对照[结构文档](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/STRUCTURE.md)：Python端为backend/api、core、services、engines；Electron＋React是当前唯一桌面和浏览器UI，frontend/dist只是网页构建产物；omnivoice是底层模型包，不能把这个Python语言标签当成一个纯Python小服务。

1. **桌面启动分工。** [主进程](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/electron/src/main/index.ts#L232-L319)创建BackendSupervisor、协议和IPC入口，再打开窗口并启动后端。[前端依赖](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/electron/package.json#L37-L115)包含React 19、TanStack Router/Query、Zustand、Vite和Electron；不是Next.js应用。[Python依赖](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/pyproject.toml#L36-L182)包括PyTorch、Transformers、WhisperX/faster-whisper、FastAPI、MCP、FFmpeg相关包，Apple Silicon另有MLX条件依赖；安装成本明显高于一个轻量HTTP包装器
2. **MCP复用业务API。** [FastAPI注册入口](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/main.py#L771-L799)挂载路由、音频目录和MCP。[MCP客户端](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/mcp_server.py#L434-L516)在内嵌模式用httpx ASGITransport以loopback身份调用同一应用，独立模式才经HTTP。generate_speech先按显式profile／客户端绑定解析声音，再提交/generate；最终用响应头中的audio_id、耗时、时长构造JSON。[声音绑定与API调用](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/mcp_server.py#L577-L625)
3. **生成不是直接model.generate。** [/generate入口](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/generation.py#L1675-L1865)先NFC正规化文本，解析引擎、检查已有的引擎许可接受开关与声音条件能力，驱逐其他驻留TTS实例，再做设备路由和预热。随后经gpu_gateway分发本地计算；普通完成路径进入统一finalize，依次处理可选水印、保存WAV、写SQLite历史、保留策略清理、事件通知。[调度与响应](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/generation.py#L2414-L2508)；[持久化尾部](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/generation.py#L1492-L1637)
4. **硬件和运行时契约明确。** [路由判定](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/services/engine_routing.py#L146-L237)区分accelerated、cpu_only、cpu_fallback、unavailable；缺少支持的加速器且没有CPU路径会拒绝。[TTSBackend契约](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/services/tts_backend.py#L215-L387)声明采样率、语言、可用性、声音设计和预热接口；[GPU任务管理](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/services/model_manager.py#L768-L1023)把排队计时与实际执行计时分开，并用有上限的进度心跳延长执行预算
5. **MCP二进制结果有边界。** 默认resources模式仍将WAV以base64放入JSON；files模式返回音频URL及可选共享目录路径，both兼有两者。文件输入需配置BASE_PATH，源码先realpath判断，再以no-follow／目录描述符打开，并复核已打开对象仍位于边界内。跨容器时路径必须真的共享；URL返回成功也不代表Agent主机拥有同一路径。[路径读取边界](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/mcp_server.py#L127-L206)；[输出契约](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/mcp_server.py#L379-L405)；[docs/mcp.md](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/mcp.md)

本轮文件实读范围（共15项，长文件是选读，不是全仓审计）：README全文；docs/STRUCTURE全文；docs/mcp全文；docs/benchmarks全文；docs/licensing/model-inventory全文；pyproject.toml 1–185；electron/package.json全文；electron/src/main/index.ts 1–70、127–190、232–345；backend/main.py 771–807；backend/mcp_server.py 127–209、379–626、921–954并检索工具定义；generation.py 1492–1639、1675–1865、2410–2510并检索主请求调用点；openai_compat.py 629–726、802–866；model_manager.py 768–1023；engine_routing.py 146–240；tts_backend.py 215–387、4374–4439。其余仅目录或函数轮廓扫描，不据此声称完整实现已核验。

### ④ 技术价值、近期变化与真实边界
- **值得借鉴的是资源与状态管理。** 冷启动模型加载和热生成分开预算，排队超时不会被误报为“机器太慢”；生成成功后历史表失败会自修复重试，仍失败则尽量保留音频交付。这个设计比单纯支持多少模型更能说明产品工程投入。对应实现见上面的任务管理与finalize
- **超时并不等于强制终止GPU工作。** 线程池超时路径明确记录：旧工作线程可能继续运行、继续持有设备，pool reset只是更换执行器；不可把它写成硬隔离。仍开放的[issue #2700](https://github.com/debpalash/VoiceStudio/issues/2700)于10月10日报告M2／OuteTTS内部Whisper下载锁死，10月14日仍有更新。这里是用户日志与源码边界相互印证，本轮未复现该故障。[超时后的实际动作](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/services/model_manager.py#L988-L1015)
- **“流式”要分入口。** 原生/generate的stream是按文本块生成预览；OpenAI兼容接口的SSE／chunked audio则先完成整段推理和编码，再切分已完成音频，不能据此宣称token级流式合成或低首包延迟。[原生预览说明](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/generation.py#L1709-L1716)；[SSE实际实现](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/openai_compat.py#L629-L643)；[先推理后传输](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/openai_compat.py#L816-L858)
- **评测与许可都必须降到证据口径。** 固定版本的[benchmark页](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/benchmarks.md)明确尚无已验证结果行；本轮没有运行模型、音质测试或性能测量。[模型许可清单](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/licensing/model-inventory.md)覆盖56个配置仓库和7类尚未解析的资产族，明确目前没有任何记录完成商业使用clearance；false既可能是已知非商用，也可能是未完成审查。证据revision不钉住运行时下载，普通下载并未被可选“reviewed-file”流程全局约束。应用开源许可、模型权重条款、输出使用权和声音授权是不同层面
- **近期活动是集成与发行。** v0.5.6发布说明列出MCP路径修复、OpenAI SDK适配、Twilio接入和长篇任务可靠性，也披露Electron安装包未签名或仅ad-hoc签名、未Apple notarize。最新主干合并的[commit](https://github.com/debpalash/VoiceStudio/commit/fdeeec5b0bcbefc9f3f576bb3689686feed8e569)新增Mac App Store、Microsoft Store、Snap相关工作流及打包验证文件；本轮读了提交说明和变更清单，没有验证商店审核或上架，所以只能称“发行基础工作”

### ⑤ 今日热度：事实与推测分开
**事实：** 同快照第3、stars today 1,748；主干昨晚有发行基础提交，正式版仍为9月23日发布。README把声音克隆、桌面工作台和Agent接口组合在一起。

**推测：** 本地声音生产工具加MCP／OpenAI兼容层，可能同时吸引创作者和Agent开发者；多模型、可见桌面流程也降低了理解门槛。没有star来源、传播链或活动归因证据，无法确认哪一个更新推动今天上榜，也不能把今日增长归因于尚未核验的商店上线。

### ⑥ 对你的技术方向有什么具体用处
- **Agent／MCP：** 可以作为“文本任务结果转为音频资产”的独立后端；最值得研究的是MCP输出模式、文件边界、声音绑定以及错误如何保持可操作。适合先用经过授权的声音和明确引擎做小范围验证；files模式避免把大段WAV base64塞回Agent上下文，但需要处理URL认证与共享存储
- **RAG／数据工程：** 适合补在语音输入转写和答案朗读两端，不承担检索正确性、来源引用或回答事实验证。长任务的排队／执行两时钟、产物先落盘后记录索引、历史保留和事件通知可迁移到文档摄取、批处理与GPU作业
- **Python／Django／Node：** 对现有Web系统更合适的结合点是独立语音服务与任务队列，而非把重模型塞进Web请求进程。重点读model_manager的预算与遗弃清理、generation的统一finalize和openai_compat的真实协议语义；兼容请求格式并不保证延迟、声音含义和云API相同
- **React前端：** 能借鉴桌面壳／后端监管分离、模型可用性与CPU fallback反馈，但本轮未深读renderer组件。若目标是Next.js产品，应借用API契约与任务状态模式，不能把Electron界面直接当Next.js模板

## 4. [mksglu/context-mode](https://github.com/mksglu/context-mode)

### ① 元信息与固定版本

- 官方第4；TypeScript；28,336 stars；969 stars today；昨日第3，下降1位
- 固定SHA：[dbec9809d83172a2fa3edd69cc9b95000c3b9859](https://github.com/mksglu/context-mode/commit/dbec9809d83172a2fa3edd69cc9b95000c3b9859)，2026-10-14 00:11:32 UTC。对昨日1a1bed13…的[compare](https://github.com/mksglu/context-mode/compare/1a1bed139906ecc048233583bb2fd29290603b7a...dbec9809d83172a2fa3edd69cc9b95000c3b9859)为ahead 2、behind 0，**唯一净变更是stats.json，没有执行代码增量**
- package仍1.0.169，Node>=22.5.0；最近正式[v1.0.169](https://github.com/mksglu/context-mode/releases/tag/v1.0.169)仍是6月29日。依赖MCP SDK、better-sqlite3、Zod、HTML→Markdown转换组件。许可为[Elastic License 2.0](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/LICENSE)，其中限制把实质功能作为第三方托管/管理服务提供，不能当MIT样例直接搬进SaaS。[依赖](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/package.json)

### ② 它解决谁的问题

面向长时间读取源码、日志、文档和工具输出的编码Agent，把大输出留在本地索引，只将相关片段返回模型，同时用会话事件帮助压缩后续接任务。它主要解决上下文拥挤及回查问题，而非训练一个更长窗口模型。今天背景沿用昨日，下面重点复核检索与执行边界是否变化。[README定位](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/README.md#L32-L51)

### ③ 实际架构与控制、数据流

1. ctx_execute先检查deny规则，再由PolyglotExecutor启动语言子进程。普通输出在给定intent且超过5,000字节时先存入ContentStore，返回标题和120字符预览；无intent但超过102,400字节返回索引引用。超时的部分输出走另外分支，不能假定每条路径都经过同一种压缩。[handler与门槛](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/server.ts#L1743-L2035)
2. ContentStore用porter与trigram两路FTS5检索，RRF合并后按标题、词距/短语邻近重排，完全无结果时再做模糊纠正。它是两种词法索引的融合，所读链路没有调用embedding服务。搜索前刷新过期文件来源，带session allow-set时先扩大候选池再过滤。[融合和重排](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/store.ts#L1242-L1404)
3. PreCompact把SessionDB事件制成resume snapshot；SessionStart在compact时写入可索引事件并注入回查指引，resume时优先指定session，缺失再领取此前未消费的快照。统一搜索只有timeline模式才把SessionDB与auto-memory并入，普通搜索不是“搜遍全部历史”。[压缩前记录](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/hooks/precompact.mjs#L34-L89) · [恢复分支](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/hooks/sessionstart.mjs#L186-L295) · [统一搜索](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/search/unified.ts#L91-L175)

### ④ 技术亮点、今日变化与风险边界

- **没有新代码修复。** 今日两次commit只刷新安装统计；stats.json中的users/npm/marketplace是项目自报展示字段，不等于独立用户数，更不能拿它解释本日增星。[实际统计文件](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/stats.json)
- **昨日指出的sandbox文字与实现差异仍存在。** 普通语言执行分支使用cwdOverride或projectRoot，脚本文件放在临时目录；删除临时目录不回滚项目目录写入。可是工具cwd描述仍称非shell在sandbox临时目录，routing文案仍称子进程写入不会持久到宿主。Rust有单独编译分支，不能一概套用普通语言路径。[真实cwd](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/executor.ts#L282-L318) · [工具参数说明](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/server.ts#L1728-L1738) · [路由提示](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/hooks/routing-block.mjs#L39-L50)
- 源码确有file-path containment、realpath及deny规则检查，不应写成“毫无安全措施”；但server侧evaluateCommandDenyOnly只执行deny、不会替宿主发ask确认，未知projectRoot的containment路径也明确fail-open。这些是应用层检查，不能等同OS隔离或任意代码的安全执行环境。[deny-only](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/security.ts#L566-L588) · [边界条件](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/security.ts#L744-L782) · [边界测试源码](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/tests/security/project-boundary-852.test.ts)
- 本次近期issues列表返回空数组，没有足够新的原始讨论可补充；不据此宣布所有问题已解决。release关于成本归因修正是6月的事实，不能写成今天刚修。README的“98%”是项目特定示例，未在你的任务上测量召回、速度或质量

### ⑤ 今日热度：事实与推测

**事实：** 第4、今日+969，主线仅统计文件变化，package及正式发行不变。**推测：** 编码Agent的大工具输出和恢复需求可能解释持续关注，但没有足够的直接证据说明今日增星来自哪个发布或传播事件；不能用“今天新优化了98%”制造因果。

### ⑥ 与你的项目的具体关系、建议读哪里

- **代码RAG/数据工程：** 优先读store.ts的RRF和来源刷新，再读server.ts的indexStdout/intentSearch。日志和源码可先试FTS5与可回查片段，不必一开始就建设向量平台；同时评估符号查询、同名段落、中文分词和漏检
- **Agent/MCP：** 给“已索引”“已返回”“已执行”各自状态，别让小摘要掩盖未读完。接入前校验宿主hook真的拦截了目标工具，也别让工具内的deny-only替代你的动作授权
- **React/Next/Node与Python/Django：** Node可复用异步索引/检索思想；Django后台可做文件hash→分块→检索的服务，但多租户需要独立权限与索引隔离。不要直接把此executor挂到公网执行用户代码，且源码托管复用须先核许可
- **本轮实读范围：** 完整目录714项；README定位/接入相关段、package、LICENSE条款、stats；server执行/索引分流、store检索/过滤、executor实际cwd、unified搜索、两个恢复hook、安全策略和边界测试相关段，共13个固定版本文件。读取最近5次commit、现有两条release和空的近期issues响应；未安装、启动MCP或运行测试

## 5. [cathrynlavery/diagram-design](https://github.com/cathrynlavery/diagram-design)

### ① 元信息与固定版本

- 官方同一日榜快照：第5，HTML，54,313 stars，stars today 1,815；默认分支main，MIT
- 本轮固定SHA：[11b08eade8049c441ed3df1895e3b527c26c0fbe](https://github.com/cathrynlavery/diagram-design/commit/11b08eade8049c441ed3df1895e3b527c26c0fbe)，2026-10-13 21:34:16 UTC，即北京时间10月14日05:34
- 对昨日41765070ace63009f23c741cedb0c81429710b4f的[compare](https://github.com/cathrynlavery/diagram-design/compare/41765070ace63009f23c741cedb0c81429710b4f...11b08eade8049c441ed3df1895e3b527c26c0fbe)：ahead 16、behind 0、39个净变更文件。16次提交包含8次manifest自动升版，不能写成16项新能力
- [plugin manifest](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.claude-plugin/plugin.json)从2.6.90升到2.6.98；releases接口仍为空，没有对应GitHub Release。README仍为45种图，新增containment是Architecture变体，不是第46种图。[README](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/README.md#L10-L16) · [变体定义](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/references/type-architecture.md#L76-L117)

### ② 它解决什么问题、给谁用

这是给现有编码Agent使用的图形设计Skill：将系统、流程、数据关系整理成可交付的单文件HTML+SVG，服务技术文档、架构沟通和演示材料。宿主模型承担图型选择、信息取舍和布局，Python脚本承担结构提取、机械校验与SVG导出。它不是独立拖拽编辑器，也不能靠验证器证明一张图中的业务事实正确。[产品定位](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/README.md#L38-L45) · [工作流](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/SKILL.md#L330-L352)

### ③ 架构、依赖与真实控制／数据流

1. **提取结构→Agent重绘→约束校验→独立导出。** Mermaid脚本有界读入UTF-8/BOM文本，先识别Markdown中的真实代码块，再按选择解析，输出nodes、edges、containers、fragments、discarded等IR或摘要；Agent依Skill保留关系、报告删并清单，产物为HTML内嵌SVG。脚本不依赖Mermaid渲染器或React/Node构建。[导入入口](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/mermaid_extract.py#L245-L303) · [选择与IR输出入口](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/mermaid_extract.py#L1445-L1505) · [重绘及fidelity约定](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/SKILL.md#L341-L377)
2. **SVG不是直接截出一个字符串。** export_svg_document先找到真实首个SVG、修正HTML/XML实体与属性、检查viewBox和namespace，设置独立root ID，携带并限制页面CSS，隔离defs ID及引用，处理注释/RGBA，再做export gate和XML解析；只有之后才写文件。Google Fonts可能带来外部请求，--system-fonts可省略字体import；“单文件”不自动等于完全离线。[执行流水线](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/export_svg.py#L1065-L1144) · [导出规范](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/references/export.md#L1-L58)
3. **新增containment把“画在里面”变成可检查的语义。** SVG声明admin／traffic scope、compute／endpoint／managed node、最内层parent及endpoint target；验证器读取bounds rect实际坐标，检查ID、父循环、几何包含、节点归属、兄弟区域轴向／重叠和peering声明。仅有data-parent正确但图形位置错误也会失败。[真实示例](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/assets/example-architecture-containment.html#L60-L185) · [实际语义验证](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/verify-architecture-containment.py#L520-L774)

核心导入、SVG导出及containment验证使用Python标准库；PNG／浏览器渲染校验另外依赖Playwright/Chromium。本次新增的CI依赖项目固定Python 3.12、Playwright 1.62.0、Pillow 12.1.1，以及Node校验用Claude Code 2.1.229；这些是CI依赖，不是打开每张静态HTML都必须安装的应用依赖。[Python CI清单](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/ci/python/pyproject.toml) · [Node CI清单](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/ci/node/package.json)

### ④ 实际新变化、昨日风险更新与边界

- **昨日CSS literal风险已落地修复。** [PR #423](https://github.com/cathrynlavery/diagram-design/pull/423)已merge，对应compare内e794452d；[issue #420](https://github.com/cathrynlavery/diagram-design/issues/420)已closed。当前selector_list_parts跟踪引号、escape及括号深度，只在顶层逗号分割，并不再把selector中的连续空白全部压缩；测试包含Revenue, net、连续空白、escaped逗号及:is/:where嵌套。它修的是选择器语义保持，不只是让XML可以解析。[源码](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/export_svg.py#L427-L458) · [scoping和空白处理](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/export_svg.py#L544-L656) · [新回归](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/test-export-svg-standalone.py#L69-L92)
- **另外两类导出改动也是真增量。** SVG style中的CDATA在带出规则前解包，HTML stylesheet里的同形文字仍保留为文字；扫描器跟踪SVG与foreignObject／desc／title等上下文。defs重命名区分live与commented定义，避免注释中同名可选定义把真实元素引用改向不存在ID。[上下文扫描](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/export_svg.py#L133-L188) · [defs引用](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/export_svg.py#L747-L863)
- **Mermaid新修复保留“语义层”和“展示层”区别。** 外层普通Markdown fence里的Mermaid教学样例不再被误当真实图；sequence的rect视觉高亮块用空标记入栈，其end不会提前关闭alt／loop等语义fragment，semantic_depth单独计数。测试明确区分外层代码样例、真正的混合大小写／tilde fence及选中图索引。[新fence状态机](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/mermaid_extract.py#L261-L303) · [sequence栈](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/mermaid_extract.py#L853-L932) · [回归](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/verify-mermaid-import.py#L582-L631)
- **containment有具体适用边界。** 限2个admin、4个traffic、8个node；父ID必须指向最内层实际包围区域，managed节点依这个绘图契约归admin、private endpoint归traffic并指向managed。它拒绝移动检查对象的transform、CSS、嵌套SVG和动画，因为坐标校验不是浏览器布局引擎；无data-grammar标记的普通Architecture文件被跳过，外部CSS和脚本不执行。该领域约定要对照真实部署采用，不能把验证器通过当成云网络安全审计。[预算／父链／放置](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/verify-architecture-containment.py#L641-L756) · [移动几何拒绝](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/verify-architecture-containment.py#L777-L828) · [错误父级与错误放置测试](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/test-verify-architecture-containment.py#L136-L155)
- **CI硬化已经进入代码，不能由此宣称测试本轮通过。** [d23f9ef提交](https://github.com/cathrynlavery/diagram-design/commit/d23f9ef113b64c152a80658b6dbcae37d6c6af95)固定Actions SHA及依赖锁；当前CI用npm ci和uv --locked，containment检查和反例进入常规门禁；Pages写入与id-token权限仅在deploy job。[CI配置](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/workflows/ci.yml#L425-L500) · [Pages权限](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/workflows/pages.yml)
- **仍有未合入边界。** [PR #432](https://github.com/cathrynlavery/diagram-design/pull/432)仍open，报告CSS-escaped local paint引用和inline style字符引用空白在导出后的保真问题；[PR #433](https://github.com/cathrynlavery/diagram-design/pull/433)仍open，涉及若干验证器把quoted CSS数据误判成几何声明。它们是作者报告与候选修复，本轮未运行复现，不能把开放PR的验证声明写成固定主干已经修好，也不能因#420关闭就声称所有CSS保真问题已解决

### ⑤ 今日热度：事实与推测分开

**事实：** 官方日榜从昨日第6到本次第5，stars today 1,815；16次提交确有CSS、Mermaid、containment和CI方面的净变化，2.6.98是manifest版本而非正式GitHub Release。

**推测：** 直观样例、跨Agent工作流和可直接交付的HTML/SVG可能容易传播；但本轮未取得当日访问、转载或star归因数据。没有足够直接证据认定本次修复或containment功能导致上榜。

### ⑥ 对AI、Agents、RAG、MCP与全栈／数据工程的具体价值

- **Agent生成物：** 适合借鉴“模型负责信息表达，机器检查可声明的不变量”。给节点/边/区域稳定ID，既检查metadata也检查实际几何；反例应包含看起来能渲染、实际上关系错误的产物
- **RAG／数据工程：** 将检索到的架构、数据流和血缘关系转成图时，保留来源ID与删并清单。Mermaid的新fence修复说明，索引文档中的真实结构和讲解样例必须分开；containment可以验证表达一致性，不能验证来源事实
- **React／Next.js／Node：** 单文件产物可作为静态附件或受限预览；嵌入时保留root/defs隔离、title/desc和可访问性。没有必要为了使用Python提取器另加React构建链；任意生成HTML仍需独立的隔离／内容安全设计
- **Python／Django／MCP：** Python worker可做提取、验证、导出，Django保存原文、产物和验证记录；若封装MCP，宜拆成有界提取、类型校验、导出三个明确工具。当前研究范围是Skill和脚本，本轮未见原生MCP server实现，服务层、队列、资源隔离仍是集成方的工作

读取覆盖：完整目录731项，truncated=false；取得16个固定SHA文件，README／SKILL／manifest、Mermaid提取及回归、SVG导出及回归、导出规范、Architecture规范／containment验证器／反例／真实HTML，以及CI、Pages、Python／Node CI清单。大文件重点读上述入口、状态机、scoping、几何检查和反例；另读完整16提交compare、最近5提交、空release列表、#420与#423及近期开放PR。未安装、执行外部脚本或启动浏览器渲染，未逐张检查45种图。

## 6. [vercel-labs/skills](https://github.com/vercel-labs/skills)

### ① 元信息与固定版本
- 本期同一官方日榜快照（2026-10-14 02:53 UTC）：第6，TypeScript，累计34,590 stars，stars today为190
- 默认分支main；固定完整commit：[13e4063a1cf913f5606d57d42ab83a86f5001e04](https://github.com/vercel-labs/skills/commit/13e4063a1cf913f5606d57d42ab83a86f5001e04)，2026-10-09 17:54:46 UTC
- [包清单](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/package.json)为skills 1.7.2，MIT，Node要求>=22.20.0；最新正式发布[v1.7.2](https://github.com/vercel-labs/skills/releases/tag/v1.7.2)发表于10月9日16:46:55 UTC。固定主干稍晚于该版本，包含fx共享技能目录调整
- 昨日报告没有本项目；本次为首次纳入深读，不能把下面所有功能当成今天新增

### ② 解决什么问题
这是一套Agent技能发现、安装、使用和更新CLI。它面对的是同一团队在Codex、Claude Code、Cursor等工具之间共享SKILL.md及配套脚本／参考材料时的来源、路径和版本管理问题。技能在这里主要是有名称和描述的可复用指令包；CLI负责把包放到Agent会发现的位置，并不保证Agent一定按指令执行，也不是MCP服务器或Agent运行时。[来源与使用方式](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/README.md#L17-L81)；[技能定义](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/README.md#L266-L277)

### ③ 源码结构与真实控制／数据流
已先读取固定SHA的完整目录：bin为发布入口，src包含命令、来源解析、安装器、锁文件与provider，tests为测试，skills为仓库自身发布的技能。包使用ESM／TypeScript，依赖yaml、tar；开发构建依赖包括simple-git、Clack、obuild、Vitest及Vercel的Agent检测工具。[package.json](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/package.json)

1. **CLI入口并不复杂，副作用边界在分派后。** [bin入口](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/bin/cli.mjs)启用可用的Node编译缓存并加载dist；[命令路由](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/cli.ts#L310-L426)先让子命令help短路，再进入add、use、update、remove等处理器。源码中的依赖同步命令叫experimental_sync，锁文件恢复叫experimental_install，不能把发布说明里的sync措辞读成已经有稳定的“skills sync”命令
2. **来源解析与获取分开。** [parseSource](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/source-parser.ts#L352-L422)识别本地路径、Git托管地址、ref与下载类来源；subpath拒绝包含上跳段。[resolveSkills](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/add.ts#L1137-L1223)从本地发现，或下载归档，或克隆仓库；特定GitHub owner／repo有blob快路径，失败会退回git clone。因此“npx安装一个技能”背后可能包含完整克隆和多次网络请求，不应假设永远是单文件下载
3. **发现是文件系统规则。** [frontmatter解析](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/frontmatter.ts)只接受YAML；[discoverSkills](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/skills.ts#L75-L329)校验name／description、过滤internal、识别标准技能目录和plugin manifest引用，目录最多按配置深度扫描，去重并避免把本仓已安装的镜像重新当源。根目录本身是技能时默认提前返回；full-depth和没有匹配时另有递归分支
4. **安装形成一份规范副本和多个入口。** [installSkillForAgent](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/installer.ts#L300-L468)清洗名字，验证目标路径，避免源／目标目录重叠导致自删。常规symlink模式把资源复制到.agents/skills，再链接到各Agent目录；copy模式独立复制，link模式让规范路径直接指向源，链接失败会回退复制。配套脚本／assets也会被递归复制，不只是SKILL.md
5. **锁文件记录来源与内容变化，但要读清其能力。** [本地锁](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/local-lock.ts)保存source、sourceUrl、ref、skillPath和整个技能目录的computedHash；排序输出、没有时间戳，利于Git合并。[恢复入口](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/install.ts)按来源分组恢复，[更新来源重建](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/update-source.ts)遇到旧的通用Git／GitLab记录丢失原始host时拒绝猜成GitHub。这里保存的ref可为分支或tag，恢复路径也没有把computedHash当不可变安装强制条件；所以不能把它简单等同于完整的包管理器内容寻址锁
6. **npm／工作区同步是这版的重要方向。** [发现阶段](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/sync.ts#L184-L310)读取当前项目和可选workspace的直接依赖，处理package.json的skills声明及npm／Git来源；[执行阶段](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/sync.ts#L695-L838)默认链接node_modules里的技能、记录包版本和via来源，再安装远程声明。由Agent环境触发时会自动转为非交互选择；这是CLI自身行为，不是用户对任意来源内容的授权。[Agent环境分支](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/sync.ts#L550-L579)

本轮实读15项：README全文；package.json、bin/cli.mjs、frontmatter.ts、skills.ts、install.ts、local-lock.ts、update-source.ts、telemetry.ts全文；cli.ts 310–427；add.ts 1137–1388、1769–1811；installer.ts 300–480、513–566；sync.ts 184–312、550–581、695–879；source-parser.ts 84–127、352–422；agents.ts 870–917及最新commit中的fx配置diff。另读最新commit的README／agents／fx测试补丁；其他src文件只查看目录和函数轮廓，不冒称全量安全审计。

### ④ 技术价值、近期变化与真实边界
- **它把技能变成可维护工程资产。** 单一规范路径减少多工具复制漂移；skillPath减少更新时装错同名镜像的可能；排序锁文件使团队协作易审查。这里的收益是组织与来源一致性，而不是模型推理质量已提升
- **v1.7.2的实际变化**包括workspace递归同步、optional／peer依赖、package.json skills声明、node_modules链接、更新保留锁定路径及Codex全局目录调整。最新主干[fx提交](https://github.com/vercel-labs/skills/commit/13e4063a1cf913f5606d57d42ab83a86f5001e04)进一步把fx纳入.agents/skills共享目录，并有针对该目录分类的测试补丁。发布清单是作者记录，本轮未运行Vitest、安装或恢复流程
- **有防护，不等于内容可信。** frontmatter实现刻意避免支持可执行JavaScript frontmatter；子路径和安装名有检查。这些针对解析／路径风险，不负责证明SKILL.md里的指令或附带脚本安全，也不能代替Agent的工具权限、凭证边界和人工审查。[src/frontmatter.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/frontmatter.ts)；[subpath检查](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/source-parser.ts#L101-L121)
- **审计信息不是阻断式准入。** [fetchAuditData](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/telemetry.ts#L110-L141)默认3秒超时，出错返回null且不阻止安装。安装入口只有GitHub明确确认公开后才请求其审计，private或unknown不发仓库／技能名；README也承认其他远程来源不能通过GitHub确认可见性，安装遥测可能带来源及技能标识。DISABLE_TELEMETRY或DO_NOT_TRACK可同时关闭遥测和审计请求。[公开性门槛](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/add.ts#L1792-L1805)；[遥测说明](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/README.md#L548-L552)
- **现有讨论提醒关注审计时效。** 10月14日01:36 UTC新开的[issue #2485](https://github.com/vercel-labs/skills/issues/2485)仍开放，报告修复后仍显示旧commit的多家审计结果，要求重新索引／扫描。这是报告者的情况，本轮未验证该第三方技能是否已修好；它说明“页面有审计结果”本身不足以确认结果针对当前下载内容
- **跨Agent兼容仍有差异。** README兼容表区分基础技能、allowed-tools、fork和hooks支持；安装成功只说明文件到位。Node>=22.20.0也是实际门槛，Python仓库不会因此自动获得Python依赖安装与隔离。[兼容性边界](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/README.md#L505-L515)；[package.json](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/package.json)

### ⑤ 今日热度：事实与推测分开
**事实：** 本快照stars today为190；最新正式版本及主干提交均来自10月9日，没有今天刚发布版本的证据。README明确服务多种编码Agent，最近发行聚焦技能与项目依赖／工作区的结合。

**推测：** 编码Agent增多后，团队会需要一套跨工具复用和更新工作规范的办法；把技能随npm包带入工程也可能吸引前端／Node生态。但未检索到可以直接解释今天上榜的传播来源，不能把该工具的存在推导为整个技能生态已经解决安全和可复现问题。

### ⑥ 对你的技术方向有什么具体用处
- **React／Next.js／Node：** 最贴近的是将某个库的用法、项目约定和迁移手册随对应依赖版本交给编码Agent。优先读sync的发现／冲突处理及锁文件结构，关注“库升级后提示材料是否同步”“卸载依赖后谁清理旧技能”；experimental_sync目前仍是实验入口，先在可审查项目范围试验
- **Python／Django／数据工程：** 可把迁移审查、测试命令、ETL数据质量检查等团队步骤打包给多个编码工具，但Python环境、数据库权限、生产变更审批仍需独立建立。技能资源应和真正执行的工具版本一起审查，不能让一份说明文档偷偷扩大权限
- **Agent／RAG／MCP：** 可以复用“来源→发现→筛选→分发→锁记录”这个管理面；它不会替你建立向量索引、实现MCP transport或隔离每个Agent的执行。RAG检索流程的操作手册能作为技能，检索结果本身仍应保留来源与时效
- **优先读的代码：** add.ts的resolveSkills／installFromSource，installer.ts的canonical／agent目录处理，local-lock.ts的哈希与来源语义，update-source.ts对丢失host的拒绝分支，以及telemetry.ts的默认网络行为。对于你做编码工具链，后两者比“支持多少Agent”更值得纳入设计检查

## 7. [lyogavin/airllm](https://github.com/lyogavin/airllm)

### ① 元信息与固定版本

- 官方第7；页面语言Jupyter Notebook；38,392 stars；1,001 stars today；昨日也是第7
- main固定SHA：[cb807515f640f9489f267adc0c66afb249e90a17](https://github.com/lyogavin/airllm/commit/cb807515f640f9489f267adc0c66afb249e90a17)，2026-10-13 06:24:33 UTC。[与昨天7bb8a860…比较](https://github.com/lyogavin/airllm/compare/7bb8a8600937ff15b81016f286142bcdac7ee2d2...cb807515f640f9489f267adc0c66afb249e90a17)只有1个commit、两张star-history图片，**没有新的算法或执行代码**
- 实际包是Python/PyTorch，setup版本4.0.0，torch>=2.4、transformers>=4.49且<6、accelerate及safetensors等；latest release仍是9月5日的[v4.0.0](https://github.com/lyogavin/airllm/releases/tag/v4.0.0)。特定模型另需特定Transformers/量化后端，宽泛依赖范围不代表所有组合都受测。[包依赖](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/setup.py)

### ② 它解决谁的问题

它让冻结模型权重按层在磁盘、主存和GPU间流动，降低“一次装下全部权重”的显存门槛，适合显存小但磁盘/主存较充裕的离线实验。4.0还提供特定Qwen路径的流式LoRA训练。它解决容量问题，不自动保证低延迟、多用户吞吐或任意长上下文可用；宣传的显存数字应连同模型、硬件、序列长度和磁盘需求一起看。[项目说明与条件](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/README.md#L9-L38)

### ③ 实际架构与数据流

1. AutoModel在非macOS路径读取config.architectures，有专用布局就选子类，否则走AirLLMBaseModel；macOS提前直接分派MLX Llama。utils从weight_map或单文件checkpoint建立参数→文件映射，再按层拆为safetensors，兼容常驻模块；符合现成分片布局时尝试链接/复制，降低重复存储。[实际分派](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/auto_model.py) · [切分入口](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/utils.py#L528-L594) · [分片复用](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/utils.py#L661-L700)
2. 基类构造meta模型；pre-hook取得预取结果或同步载入当前层，物化到设备，再预取下一层；post-hook释放本次搬入参数。expert streaming或CPU常驻表有自己的生命周期，不能简单把整层一刀移到meta。generate/forward仍委托底层Transformers，逐token生成仍受重复I/O影响。[层生命周期](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/airllm_base.py#L850-L920)
3. LoRA的_StreamedModule前向no_grad并保存CPU hidden，反向重载冻结层再计算梯度，然后驱逐权重；adapter和优化器状态留在GPU。chunked CE分块遍历词表累计log-sum-exp，反向重算每块求hidden梯度，避免完整token×vocab logits常驻。测试源码把小张量loss/梯度与普通cross_entropy比较，但本轮没有执行。[流式autograd](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/airllm_lora.py#L35-L76) · [训练步骤](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/airllm_lora.py#L329-L368) · [分块CE](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/chunked_ce.py) · [小张量对照](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/tests/test_streamed_lora.py#L75-L96)

### ④ 技术亮点、今日变化与边界

- 减显存来自权重生命周期和重计算的调度，不只是“用了Python/PyTorch”。它把存储、CPU RAM、GPU VRAM和时间换算成可检查的路径；README宣称4GB/6GB等结果仍为作者条件下的记录，本轮没有复现。Flash-Next训练类注释本身也明确一层MoE约5GB，**不是4GB方案**。[训练类边界](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/airllm_lora.py#L381-L386)
- **新讨论并非新修复：** 今天新开[PR #384](https://github.com/lyogavin/airllm/pull/384)报告macOS将不兼容架构送入Llama MLX后迟至生成才失败，提出下载前检查；读取时open、merged=false。当前固定源码的macOS直接返回分支仍在，因此不能说今日已解决。作者M4 Pro复现和tiny-Mistral对照是作者报告，不是本轮成绩
- 昨日已提的BOM加载[PR #382](https://github.com/lyogavin/airllm/pull/382)仍open；当前lora_data.py仍以utf-8而非utf-8-sig读取。新[issue #383](https://github.com/lyogavin/airllm/issues/383)列出旧training/qlora.py的兼容性问题，本轮未逐项复现，尤其不能把它们直接归到新air_llm/airllm/airllm_lora.py路径。[当前数据读取](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/lora_data.py#L76-L109)
- AutoConfig使用trust_remote_code=True；运行前应审核模型来源。把模型名填进去就可能加载模型仓库代码，不能将“离线推理工具”理解为任意模型文件天然安全。[真实加载参数](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/auto_model.py#L37-L43)

### ⑤ 今日热度：事实与推测

**事实：** 第7、今日+1,001；主线只更新星图，最近正式版本距今一个多月。**推测：** 小显存运行大模型与LoRA的叙事可能继续吸引实验者，但没有直接证据说明10月14日上榜由哪次传播触发；不能把今日新增PR描述成已发布性能突破。

### ⑥ 与你的项目的具体关系、建议读哪里

- **AI/Agent：** 可作为离线批量实验候选；对需要频繁交互的coding agent，先测首token、每token、工具轮次和磁盘吞吐，别仅比较峰值显存
- **RAG/数据工程：** 适合学习分片、预取、常驻参数与容量估算。用于RAG生成端时须先测真实检索上下文长度；它不提供检索器、索引或引用真实性保证
- **Python/Django：** 核心阅读顺序auto_model→airllm_base hooks→chunked_ce。GPU任务应放独立worker与任务队列，避免在Web请求进程反复切层或并发共享未经评估的训练实例
- **React/Next.js/Node/MCP：** 没有现成React组件或已验证MCP入口；可以自己包任务状态API，但不要把长推理阻塞直接暴露成无限等待的HTTP请求。前端应显示排队、载入、生成和失败状态
- **本轮实读范围：** 完整目录117项；README硬件/依赖/平台说明、setup与许可证、auto_model；utils切分/复用、airllm_base初始化及hooks、LoRA前后向、chunked CE完整实现、数据loader及相关测试选段。最近5个commit、3个release、#384完整PR与diff、#383原issue、#382近期状态；未下载模型、安装依赖或跑GPU/测试

## 8. [storytold/artcraft](https://github.com/storytold/artcraft)

### ① 元信息与固定版本

- 官方第8；Rust；25,935 stars；4,081 stars today；昨日第4，下降4位，仍有显著日增
- 固定SHA仍为[d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373](https://github.com/storytold/artcraft/commit/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373)，2026-10-11 13:47:59 UTC。[与昨天比较](https://github.com/storytold/artcraft/compare/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373...d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373)identical、ahead 0、0文件，**今天没有主线代码增量**
- 最新GitHub Release仍是9月26日[artcraft-v0.41.0](https://github.com/storytold/artcraft/releases/tag/artcraft-v0.41.0)，早于10月native改造。源码MIT或Apache-2.0双许可；商标和NOTICE列出的第三方素材不自动获得同样许可。[范围](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/NOTICE)

### ② 它解决谁的问题

它为艺术家、设计师和影视创作者组合素材、prompt、参考图、模型选择、生成任务和结果库，减少在不同供应商网站之间来回传文件。既有React/Tauri前端，也在建设纯Rust主要UI的native客户端。它是创作工作流与服务接入工具，不是本地基础模型；native尚未迁完全部工具。[README](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/README.md) · [native范围](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/README.md#L1-L12)

### ③ 实际架构与控制、数据流

1. native main通过eframe启动ArtcraftApp，后台Tokio处理API调用，Event回传UI；旧前端仍是React/Nx/Vite路线。native使用egui/eframe 0.36、reqwest、rodio，且仍用wry打开Midjourney登录窗口，所以“主UI不依赖WebView”不能扩大成“全程序绝无WebView”。[入口](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/main.rs) · [实际依赖](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/Cargo.toml) · [旧前端依赖](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/frontend/package.json)
2. 图片页按模型选择provider，Provider::resolve过滤不支持组合，adapt删除不支持参数。直接Midjourney固定4图、不接受参考图；fal在native picker只开放四个模型。submit将界面fields变成共享router请求，供应商返回job ID之后才生成本地ProviderJob并存储。[能力映射](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/mod.rs#L48-L79) · [提交实现](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/submit.rs#L53-L129) · [提交后存储](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/mod.rs#L440-L454)
3. Worker轮询fal，Midjourney以websocket加15秒feed补查。供应商完成不直接意味着用户素材库完成：finish先复用/生成每张结果的upload token并保存，再下载、上传，记录uploaded进度；重启后继续剩余结果，全部完成才移除job并发成功事件。JobStore用临时文件替换避免截断，但保存失败仅warn，不向调用方返回失败，所以“跨崩溃绝不重复/丢任务”不是无条件保证。[持久化](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/jobs.rs) · [交付与幂等边界](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/worker.rs#L180-L221)

### ④ 技术亮点、今日新证据与边界

- 把“提交”“供应商完成”“素材库持久化”建成不同状态，对生成Agent和长耗时任务有直接价值。外部提交先于本地持久化，以及本地保存best-effort，是昨日已有、今天仍成立的边界，不是今天新引入的bug
- **同SHA的新核读发现：音频/视频router会丢掉批次中次要job ID。** API response明确提供all_job_tokens数组，但两个request_common把all_inference_job_tokens重新构成只有primary的一元素数组。当前源码能够直接确认这一数据收缩；[PR #2275](https://github.com/storytold/artcraft/pull/2275)正在修复并报告本地HTTP回归测试，读取时仍open、merged=false，不能称已修复。[音频API schema](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_api_defs/src/omni_gen/generate_response/omni_gen_audio_generate_response.rs) · [音频适配器](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_router/src/generate/generate_audio/providers/artcraft/request_common.rs#L25-L28) · [视频API schema](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_api_defs/src/omni_gen/generate_response/omni_gen_video_generate_response.rs) · [视频适配器](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_router/src/generate/generate_video/providers/artcraft/request_common.rs#L25-L28)
- 新[issue #2291](https://github.com/storytold/artcraft/issues/2291)报告线上3D生成失败仍扣credits、未退款；读取时open且无评论。这是未经本轮复现的用户报告，发生在线上3D路径，**不能据此断言上述native图片worker或批次ID问题造成扣款**
- #2275中测试通过、live tests忽略、旧lint/格式化失败及Netlify旧文档检查跳过都只是该PR作者报告，不是本轮运行结果；“检查绿了”也不自动等于功能已进入main

### ⑤ 今日热度：事实与推测

**事实：** 今日+4,081，但主线和正式发布都没变化。**推测：** 跨模型创作工作流、10月新增native界面及许可变化可能仍有传播惯性；没有10月14日star归因证据。顺位下降也不能等同于绝对热度下降，更不能制造“今日发布新客户端”的故事。

### ⑥ 与你的项目的具体关系、建议读哪里

- **Agent与数据工程：** 重点读ProviderJob、Worker::finish和两个request_common。多结果任务应持久保存完整job集合、稳定顺序和每个产物的幂等key；不要把primary当作全批成功凭据
- **React/Next/Node：** 老frontend提供真实创作交互参考；新native则展示将UI能力约束与provider路由分开。自己的前端应显示每个job/产物状态，不让一个成功卡片隐藏整个批次中仍在运行或丢失的任务
- **Python/Django：** 可借鉴任务账本与分阶段完成，将“外部提交”和“本地记录”设计成可恢复过程；数据库保存失败应可观测且能阻止错误的成功确认。供应商完成、上传完成和计费补偿是三个不同问题
- **RAG/MCP：** 本轮链路不是检索或MCP框架；若给创作Agent包装工具，返回任务ID、已交付产物清单与下一次查询入口，不将大素材直接塞进模型上下文，也不把下单权限藏进通用生成按钮
- **本轮实读范围：** 完整目录7307项；README、native README、两套依赖、NOTICE；native main、图片页/provider能力、submit/jobs/worker、后台提交段，以及两份API schema和两份audio/video适配器。读取最近5个commit、3个release、#2275正文与diff、#2291及空评论；未运行UI、付费生成、安装或测试

## 9. [xtool-org/xtool](https://github.com/xtool-org/xtool)

### ① 元信息与固定版本
- 本期同一官方日榜快照（2026-10-14 02:53 UTC）：第9，Swift，累计9,521 stars，stars today为1,198
- 默认分支main，MIT；固定完整commit：[65bf3cc5a1240fea53ac0748d29a01878222a6ce](https://github.com/xtool-org/xtool/commit/65bf3cc5a1240fea53ac0748d29a01878222a6ce)，2026-10-14 00:11:18 UTC，提交主题是补充较新的Apple根证书
- 最新正式版[1.22.2](https://github.com/xtool-org/xtool/releases/tag/1.22.2)于今天00:30:10 UTC发布，明确提示Apple ID认证用户升级后需要重新登录。上一版1.21.0发表于10月5日
- 昨日报告未纳入，不能声称今日代码相较昨日报告增加多少。以下为本轮固定主干阅读和有日期的近期发布，不是历史榜位推算

### ② 解决什么问题
xtool尝试把SwiftPM项目构建、打包成iOS应用，并处理签名与真机安装，让开发者可在Linux、Windows的WSL和macOS上使用命令行工作流。它的价值是让构建／设备操作接口更可脚本化，并把Apple Developer Services与设备通信抽成可复用XKit库。README称其为跨平台Xcode替代，但Linux安装文档仍要求取得Xcode.xip来提取Apple SDK，Windows也依赖WSL与设备透传；它不是无需Apple工具资产、无需账号或覆盖整个Xcode功能集的保证。[README.md](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/README.md)；[Documentation/xtool.docc/Installation-Linux.md](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Documentation/xtool.docc/Installation-Linux.md)

### ③ 源码结构与真实控制／数据流
已先读完整递归目录。Sources/xtool是极薄的可执行入口，XToolSupport处理CLI、SDK安装和开发命令，PackLib处理规划／构建／组包，XKit承担认证、Developer Services、签名、设备连接与安装；XcodeProjects另管Xcode工程格式。[依赖与目标](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Package.swift)可见Swift ArgumentParser、swift-subprocess、NIO、OpenAPI runtime、X509／Crypto，以及SwiftyMobileDevice、zsign、xadi等依赖，说明这不只是调用一次swift build。

1. **命令控制。** [程序入口](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/xtool/XTool.swift)进入[命令注册](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/XTool.swift)，提供setup、auth、sdk、dev和设备命令，SIGINT会取消任务。[PackOperation](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/DevCommand.swift)确认当前目录有Package.swift，确保SDK、读取xtool.yml、配置LSP，然后构造BuildSettings、Planner和Packer；dev默认进入run，build子命令可选择签名或生成IPA
2. **先规划应用结构。** [Planner](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/PackLib/Planner.swift#L27-L218)读取依赖图，遍历产品／target及资源，形成应用和扩展的Plan；会跳过在宿主运行的macro target，收集SwiftPM bundle、动态库和binary target，并合并Info.plist。xtool.yml控制bundle ID、图标、资源、entitlements和扩展，而不是把所有这些隐式交给IDE
3. **再用生成的包驱动构建。** [Packer](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/PackLib/Packer.swift#L14-L127)生成临时SwiftPM builder package，将原项目产品作为依赖，用executable target连接；构建时禁用自动重新解析，避免改坏已解析的根依赖。之后将二进制、bundle、动态framework、图标和Info.plist组装为.app；静态archive不会当动态framework嵌入。[资源组包](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/PackLib/Packer.swift#L129-L211)
4. **SDK是实际资产流水线。** [SDKBuilder](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/SDKBuilder.swift#L99-L233)依次装宏、工具链和从Xcode抽取的Developer内容，写出Swift SDK与toolset元数据；iOS目标使用Apple SDK路径，Linux链接器指向ld64.lld。[BuildSettings](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/PackLib/BuildSettings.swift#L32-L72)根据SwiftPM／swift-build选择SDK参数，并清除会干扰目标SDK的SDKROOT。构建配置与工具资产的来源应独立追踪
5. **打包成功还要经过签名和设备链。** [IntegratedInstaller](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XKit/Integration/IntegratedInstaller.swift#L195-L322)将IPA解包或复制.app到staging，和设备握手，调用signInPlace，重新压缩再交给AppInstaller。[AutoSigner](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XKit/Signer/AutoSigner.swift#L45-L96)先向Developer Services做provisioning，再改bundle ID、写embedded.mobileprovision、应用entitlements并签名。签名证书撤销需要通过delegate询问，而不是把证书不足静默处理掉
6. **认证有两种不同依赖。** [AuthCommand](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/AuthCommand.swift#L7-L129)区分付费开发者可用的App Store Connect API key和走Apple私有接口的Apple ID密码模式。后者在登录前披露设备模拟，并建议谨慎使用次级Apple ID；这属于项目的风险提示，本轮没有登录或传输任何凭证

本轮实读16项：README、Package.swift、Installation-Linux.md、Control.md、Sources/xtool/XTool.swift、XToolSupport/XTool.swift、DevCommand.swift、AutoSigner.swift、Tests/XToolTests/PackerTests.swift全文；Planner.swift 1–222；Packer.swift全文；BuildSettings.swift 32–88、116–162；IntegratedInstaller.swift 195–328；AuthCommand.swift 1–133；AsyncHTTPClient+HTTP.swift 24–61及根证书列表定位；SDKBuilder.swift 99–237。另读认证修复commit的ADIDataProvider、DeviceInfo和AuthCommand完整小补丁，未据此声称已审计整个认证实现。

### ④ 技术价值、近期变化与真实边界
- **可借鉴的是“计划→构建→产物→provision→签名→设备”的明确分层。** .app生成与签名／安装失败可区分，资源及Info.plist处理可以定位到具体代码；XKit也作为SwiftPM库公开。对需要自动化工具链的人，比泛称“取代IDE”更有实际意义
- **今天的1.22.2确有可核验发布事件。** [认证修复commit](https://github.com/xtool-org/xtool/commit/fae19812754f115be4f96b48e2eae8ec1f821ef9)把客户端指纹从macOS风格改为Pixel 7／Android 14，provider ID改为2；说明称此前Android Anisette数据与自报Mac身份不匹配，修复-80045。原[issue #329](https://github.com/xtool-org/xtool/issues/329)已于今天00:31 UTC关闭。作者勾选了重新认证验证，这不是本轮执行结果
- **TLS修复仍保留正常验证默认值。** 固定主干在Linux HTTP client的additionalTrustRoots加入Apple Root CA、G2、G3，原[issue #339](https://github.com/xtool-org/xtool/issues/339)已随补丁关闭。源码另有显式关闭TLS验证的环境分支，但本轮未设置，也不应把关闭验证当成登录修复方案。[TLS配置](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XKit/HTTPClientProtocol/AsyncHTTPClient%2BHTTP.swift#L37-L48)
- **发布不代表认证端到端无障碍。** 今天02:49 UTC刚创建、仍开放的[issue #345](https://github.com/xtool-org/xtool/issues/345)在1.22.2／WSL2上报告短信二次验证HTTP 403；另有[issue #341](https://github.com/xtool-org/xtool/issues/341)报告已完成构建和签名后设备连接超时。这些是用户报告，未本轮复现；不能把之前-80045与证书问题关闭等同于所有Apple ID／USB链路都稳定
- **平台边界要讲清。** Linux指南要求Swift 6.4、usbmuxd和Xcode 27.xip，Windows需要WSL及USB透传。macOS的simulator运行入口在DevCommand中用条件编译保护，不能从SDK里有simulator triple就推导Linux能运行iOS模拟器。Control文档也说明部分entitlement需要付费账号、Apple特批或尚缺对应capability映射。[Documentation/xtool.docc/Installation-Linux.md](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Documentation/xtool.docc/Installation-Linux.md)；[平台条件分支](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/DevCommand.swift)；[entitlement边界](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Documentation/xtool.docc/Control.md)
- **测试范围仍需区分。** 已读的[Packer测试](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Tests/XToolTests/PackerTests.swift)只证明仓库有按target triple检查CFBundleSupportedPlatforms的断言，不证明本轮跨平台构建、真机安装或签名通过。本轮没有安装Swift／SDK、运行仓库代码、接入iOS设备或进行性能测试；issue日志中的0.92秒构建也只是报告者环境的一次结果，不能拿作benchmark

### ⑤ 今日热度：事实与推测分开
**事实：** 本快照第9、stars today为1,198；今天确实发布1.22.2，紧接认证与Apple根证书修复。项目当前仍有登录和设备通信问题讨论。

**推测：** “在Linux／Windows开发并装到iPhone”的门槛突破和脚本化工作流很有吸引力，新版本解决此前登录阻断也可能增加关注。但没有传播链或star归因证据，不能确认此次发布导致全部今日增长，更不能把热度当成其已全面替代Xcode的证据。

### ⑥ 对你的技术方向有什么具体用处
- **编码Agent／自动化：** 如果以后做Swift原生iOS客户端，可将规划、编译、产物检查纳入Agent工具；优先读DevCommand→Planner→Packer，保留各阶段日志和明确失败类别。账号认证、证书撤销、签名与真机安装应是单独权限边界，不能因为CLI支持就默认交给Agent无限执行
- **React／Next.js／Node：** 对纯Web产品没有直接运行时收益，也不能自动把React或Next.js项目转成iOS应用。它更适合原生Swift客户端或工具链研究；可借鉴的是显式产物计划、构建配置和设备部署分层
- **Python／Django／RAG／数据工程：** 没有直接替换现有后端、向量检索或ETL的能力；如果你的产品需要独立iOS前端，它可作为构建／部署外围工具。数据管线可借鉴其输入资源→Plan→物化产物的结构，而不是引入整个Apple认证与签名栈
- **优先读的代码：** Planner的依赖／资源闭包、Packer的临时builder包和动态／静态资源判别、IntegratedInstaller与AutoSigner的阶段边界，以及SDKBuilder的元数据生成。若真评估采用，先验证所需SwiftPM依赖、entitlements和目标设备路径，再判断是否覆盖你的实际项目

## 逐仓源码来源与读取范围索引

以下列出本轮涉及的136个固定版本文件，含全文阅读、明确选段和少量轮廓扫描；它们不是136个文件全部逐行审计。各节对哪些实现支撑了结论已作说明；仅查看目录不计入此表。链接均指向本文固定SHA，作者提交/发布/讨论链接另在正文。

### 1. morluto/rea：17个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [src/server/contractToolHandler.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/server/contractToolHandler.ts) | 完整 |
| [src/main.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/main.ts) | 完整 |
| [src/server/toolResult.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/server/toolResult.ts) | 交付预算、恢复建议与成功输出，140-245 |
| [package.json](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/package.json) | package版本、engines、dependencies、optionalDependencies；未逐项审查脚本 |
| [README.md](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/README.md) | 定位、工作流、能力和运行限制，1-220 |
| [src/server/admittedToolOperation.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/server/admittedToolOperation.ts) | 完整 |
| [src/application/EvidenceInputResolver.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/EvidenceInputResolver.ts) | 完整 |
| [src/domain/analysisView/webNetworkApiSurfaceView.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/webNetworkApiSurfaceView.ts) | 完整 |
| [src/application/analysisView/AnalysisViewService.test.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/analysisView/AnalysisViewService.test.ts) | 预算、digest及getter拒绝回归，390-490；另读278d7fb diff |
| [src/application/analysisView/AnalysisViewService.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/analysisView/AnalysisViewService.ts) | 完整 |
| [src/domain/analysisView/WebNetworkApiSurfaceAccumulator.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/WebNetworkApiSurfaceAccumulator.ts) | 输入承认、表示预算、分组、query names和分页，1-520 |
| [src/server/analysisAdmission.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/server/analysisAdmission.ts) | 完整 |
| [src/domain/recordedTransportUrl.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/recordedTransportUrl.ts) | 完整 |
| [experiments/analysis-efficiency/README.md](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/experiments/analysis-efficiency/README.md) | 指标语义、限制及复现说明，1-190选读 |
| [experiments/analysis-efficiency/pcap-small-captures.md](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/experiments/analysis-efficiency/pcap-small-captures.md) | 完整：实验设定、原始表格、方法限制、grading增量及结论 |
| [docs/web-network-captures.md](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/docs/web-network-captures.md) | 派生API surface及资源限制209-321；扫描SAZ/敏感边界 |
| [src/domain/analysisView/webNetworkApiSurfaceView.test.ts](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/webNetworkApiSurfaceView.test.ts) | query名、默认兼容、unicode、ordinal与敏感父拒绝1-130；扫描其他测试名称 |

### 2. bilawalsidhu/gods-eye-view：16个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [README.md](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/README.md) | 1–110、320–400；定位/街景/架构 |
| [package.json](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/package.json) | 版本、engines、依赖和exports |
| [CHANGELOG.md](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/CHANGELOG.md) | 1–42及本次变更位置 |
| [src/sources/gbfsStations.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/sources/gbfsStations.js) | 完整 |
| [src/sources/gbfsStations.test.mjs](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/sources/gbfsStations.test.mjs) | 名称解析和坏输入回归选读 |
| [src/layers/streetLevel/providers/google/index.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/index.js) | 完整 |
| [src/layers/streetLevel/providers/google/policy.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/policy.js) | 完整 |
| [src/layers/streetLevel/providers/google/mapsLoader.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/mapsLoader.js) | 完整 |
| [src/layers/streetLevel/providers/google/viewer.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/viewer.js) | 完整 |
| [src/layers/streetLevel/registry.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/registry.js) | 完整 |
| [src/layers/streetLevel/index.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/index.js) | 1–80、225–440 |
| [src/tools/queries/mobility.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/tools/queries/mobility.js) | 导入/工具结构及260–410；没有完整审计所有查询 |
| [src/tools/mcp/protocol.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/tools/mcp/protocol.js) | 60–155 |
| [LICENSE](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/LICENSE) | 完整 |
| [src/main.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/main.js) | 完整 |
| [src/app/layers/streetLevel.js](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/app/layers/streetLevel.js) | 完整 |

### 3. debpalash/VoiceStudio：15个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [README.md](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/README.md) | 全文 |
| [docs/STRUCTURE.md](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/STRUCTURE.md) | 全文 |
| [docs/benchmarks.md](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/benchmarks.md) | 全文 |
| [pyproject.toml](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/pyproject.toml) | 1–185 |
| [docs/mcp.md](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/mcp.md) | 全文 |
| [backend/main.py](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/main.py) | 771–807 |
| [backend/mcp_server.py](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/mcp_server.py) | 127–209、379–626、921–954 |
| [backend/api/routers/generation.py](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/generation.py) | 1492–1639、1675–1865、2410–2510 |
| [backend/api/routers/openai_compat.py](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/openai_compat.py) | 629–726、802–866 |
| [backend/services/model_manager.py](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/services/model_manager.py) | 768–1023 |
| [backend/services/engine_routing.py](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/services/engine_routing.py) | 146–240 |
| [backend/services/tts_backend.py](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/services/tts_backend.py) | 215–387、4374–4439 |
| [electron/package.json](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/electron/package.json) | 全文 |
| [electron/src/main/index.ts](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/electron/src/main/index.ts) | 1–70、127–190、232–345 |
| [docs/licensing/model-inventory.md](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/licensing/model-inventory.md) | 全文 |

### 4. mksglu/context-mode：13个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [README.md](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/README.md) | 定位与平台接入说明选读 |
| [package.json](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/package.json) | 完整依赖/脚本/版本范围 |
| [LICENSE](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/LICENSE) | 1–55条款选读 |
| [stats.json](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/stats.json) | 完整 |
| [src/server.ts](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/server.ts) | 1710–1788、1850–2035 |
| [src/store.ts](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/store.ts) | 1242–1405；索引定义定位 |
| [src/executor.ts](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/executor.ts) | 232–335 |
| [src/search/unified.ts](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/search/unified.ts) | 80–177 |
| [hooks/precompact.mjs](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/hooks/precompact.mjs) | 20–100 |
| [hooks/sessionstart.mjs](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/hooks/sessionstart.mjs) | 186–295 |
| [src/security.ts](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/security.ts) | 策略函数扫描及566–588、744–782 |
| [hooks/routing-block.mjs](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/hooks/routing-block.mjs) | 相关路由/写入承诺39–50 |
| [tests/security/project-boundary-852.test.ts](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/tests/security/project-boundary-852.test.ts) | 用例名称和边界断言轮廓扫描，未运行 |

### 5. cathrynlavery/diagram-design：16个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [skills/diagram-design/scripts/mermaid_extract.py](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/mermaid_extract.py) | 完整compare diff；有界读取与fence245-303、sequence853-945、输出入口1430-1505 |
| [skills/diagram-design/SKILL.md](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/SKILL.md) | 定位、语义类型、工作流、导入及输出1-84/135-212/330-394选读 |
| [.claude-plugin/plugin.json](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.claude-plugin/plugin.json) | 完整 |
| [skills/diagram-design/scripts/export_svg.py](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/scripts/export_svg.py) | 完整compare diff；HTML/SVG扫描133-188、CSS427-656、defs747-863、执行入口1065-1158重点 |
| [README.md](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/README.md) | 定位安装1-135；导入输出400-460 |
| [scripts/test-verify-architecture-containment.py](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/test-verify-architecture-containment.py) | 测试目录；错误放置、endpoint/peering136-166；最内父级316-343 |
| [skills/diagram-design/references/type-architecture.md](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/references/type-architecture.md) | 完整 |
| [scripts/test-export-svg-standalone.py](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/test-export-svg-standalone.py) | 选择器字面量69-92及相关测试名称；compare中CDATA和defs增量 |
| [.github/ci/node/package.json](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/ci/node/package.json) | 完整 |
| [.github/workflows/ci.yml](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/workflows/ci.yml) | 头部权限依赖1-145、containment425-445和locked Playwright约490-500 |
| [skills/diagram-design/references/export.md](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/references/export.md) | SVG流水线与字体依赖1-78，未全读PNG示例 |
| [.github/ci/python/pyproject.toml](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/ci/python/pyproject.toml) | 完整 |
| [scripts/verify-mermaid-import.py](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/verify-mermaid-import.py) | 外层fence582-631；grammars、选中块相关测试选读 |
| [scripts/verify-architecture-containment.py](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/verify-architecture-containment.py) | 完整结构扫描；核心520-828；开头限制声明 |
| [.github/workflows/pages.yml](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/workflows/pages.yml) | 完整 |
| [skills/diagram-design/assets/example-architecture-containment.html](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/skills/diagram-design/assets/example-architecture-containment.html) | 结构及data-grammar/scope/node/parent/target/peering的60-185 |

### 6. vercel-labs/skills：15个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [README.md](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/README.md) | 全文 |
| [package.json](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/package.json) | 全文 |
| [bin/cli.mjs](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/bin/cli.mjs) | 全文 |
| [src/frontmatter.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/frontmatter.ts) | 全文 |
| [src/skills.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/skills.ts) | 全文 |
| [src/install.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/install.ts) | 全文 |
| [src/local-lock.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/local-lock.ts) | 全文 |
| [src/update-source.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/update-source.ts) | 全文 |
| [src/cli.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/cli.ts) | 310–427 |
| [src/add.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/add.ts) | 1137–1388、1769–1811 |
| [src/installer.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/installer.ts) | 300–480、513–566 |
| [src/sync.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/sync.ts) | 184–312、550–581、695–879 |
| [src/telemetry.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/telemetry.ts) | 全文 |
| [src/source-parser.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/source-parser.ts) | 84–127、352–422 |
| [src/agents.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/agents.ts) | 870–917 |

### 7. lyogavin/airllm：11个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [README.md](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/README.md) | 1–100、175–191；模型条件与平台说明 |
| [air_llm/setup.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/setup.py) | 完整 |
| [air_llm/airllm/auto_model.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/auto_model.py) | 完整 |
| [air_llm/airllm/airllm_base.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/airllm_base.py) | 340–402、850–921 |
| [air_llm/airllm/airllm_lora.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/airllm_lora.py) | 1–90、329–390 |
| [air_llm/airllm/chunked_ce.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/chunked_ce.py) | 完整 |
| [air_llm/airllm/utils.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/utils.py) | 528–594、660–702 |
| [air_llm/airllm/lora_data.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/airllm/lora_data.py) | 1–110 |
| [air_llm/tests/test_streamed_lora.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/tests/test_streamed_lora.py) | 1–98 |
| [air_llm/tests/test_automodel.py](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/air_llm/tests/test_automodel.py) | 完整 |
| [LICENSE](https://github.com/lyogavin/airllm/blob/cb807515f640f9489f267adc0c66afb249e90a17/LICENSE) | 许可证标题与定义段 |

### 8. storytold/artcraft：17个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [README.md](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/README.md) | 1–50、133–146 |
| [NOTICE](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/NOTICE) | 完整 |
| [Cargo.toml](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/Cargo.toml) | workspace/default-members及依赖定位 |
| [frontend/package.json](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/frontend/package.json) | React/Nx/Vite依赖定位 |
| [artcraft-native/README.md](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/README.md) | 完整 |
| [artcraft-native/Cargo.toml](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/Cargo.toml) | 完整 |
| [artcraft-native/src/main.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/main.rs) | 完整 |
| [artcraft-native/src/backend/providers/mod.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/mod.rs) | 1–90 |
| [artcraft-native/src/backend/providers/jobs.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/jobs.rs) | 完整 |
| [artcraft-native/src/pages/create_image.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/pages/create_image.rs) | 199–253 |
| [artcraft-native/src/backend/providers/submit.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/submit.rs) | 完整 |
| [artcraft-native/src/backend/providers/worker.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/providers/worker.rs) | 完整 |
| [crates/api_clients/artcraft/artcraft_router/src/generate/generate_audio/providers/artcraft/request_common.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_router/src/generate/generate_audio/providers/artcraft/request_common.rs) | 完整 |
| [crates/api_clients/artcraft/artcraft_router/src/generate/generate_video/providers/artcraft/request_common.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_router/src/generate/generate_video/providers/artcraft/request_common.rs) | 完整 |
| [crates/api_clients/artcraft/artcraft_api_defs/src/omni_gen/generate_response/omni_gen_audio_generate_response.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_api_defs/src/omni_gen/generate_response/omni_gen_audio_generate_response.rs) | 完整 |
| [crates/api_clients/artcraft/artcraft_api_defs/src/omni_gen/generate_response/omni_gen_video_generate_response.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_api_defs/src/omni_gen/generate_response/omni_gen_video_generate_response.rs) | 完整 |
| [artcraft-native/src/backend/mod.rs](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/artcraft-native/src/backend/mod.rs) | provider导入/启动定位及440–455 |

### 9. xtool-org/xtool：16个文件

| 固定版本文件 | 实际读取范围 |
|---|---|
| [README.md](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/README.md) | 全文 |
| [Package.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Package.swift) | 全文 |
| [Documentation/xtool.docc/Installation-Linux.md](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Documentation/xtool.docc/Installation-Linux.md) | 全文 |
| [Documentation/xtool.docc/Control.md](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Documentation/xtool.docc/Control.md) | 全文 |
| [Sources/xtool/XTool.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/xtool/XTool.swift) | 全文 |
| [Sources/XToolSupport/XTool.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/XTool.swift) | 全文 |
| [Sources/XToolSupport/DevCommand.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/DevCommand.swift) | 全文 |
| [Sources/PackLib/Planner.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/PackLib/Planner.swift) | 1–222 |
| [Sources/PackLib/Packer.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/PackLib/Packer.swift) | 全文 |
| [Sources/PackLib/BuildSettings.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/PackLib/BuildSettings.swift) | 32–88、116–162 |
| [Sources/XKit/Integration/IntegratedInstaller.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XKit/Integration/IntegratedInstaller.swift) | 195–328 |
| [Sources/XKit/Signer/AutoSigner.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XKit/Signer/AutoSigner.swift) | 全文 |
| [Sources/XToolSupport/AuthCommand.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/AuthCommand.swift) | 1–133 |
| [Sources/XKit/HTTPClientProtocol/AsyncHTTPClient+HTTP.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XKit/HTTPClientProtocol/AsyncHTTPClient%2BHTTP.swift) | 24–61、141–151 |
| [Tests/XToolTests/PackerTests.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Tests/XToolTests/PackerTests.swift) | 全文 |
| [Sources/XToolSupport/SDKBuilder.swift](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/SDKBuilder.swift) | 99–237 |

## A. 今天最值得深入的3个项目

### A1. REA：用完整任务成本检验“少给上下文”的设计

建议按[EvidenceInputResolver](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/EvidenceInputResolver.ts) → [AnalysisViewService](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/application/analysisView/AnalysisViewService.ts) → [API-surface accumulator](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/WebNetworkApiSurfaceAccumulator.ts)阅读，再回看[小PCAP实验](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/experiments/analysis-efficiency/pcap-small-captures.md)。它同时展示如何保留原始证据、为派生推断标注来源、在clone前预算，以及为什么更多分页调用可能抵消单次返回变小。对Agent/MCP与代码RAG，最值得移植的是可恢复证据协议和任务级测量方法；不必为学习它先装完整逆向工具链。

### A2. vercel-labs/skills：把技能分发当作供应链和版本管理问题

按[add.ts来源解析](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/add.ts#L1137-L1223) → [installer.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/installer.ts#L300-L468) → [local-lock.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/local-lock.ts) → [update-source.ts](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/update-source.ts)阅读，最后补[telemetry.ts审计分支](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/telemetry.ts#L110-L141)。它最贴近React/Next/Node项目与编码Agent协作：同一依赖版本如何找到正确技能，技能如何落到多个Agent可见目录，来源缺失时是否拒绝猜测。重点反问“锁记录是否真的约束安装字节”“审计失败是否阻断”“审计针对哪个commit”，不要把文件复制成功等同于技能可信。

### A3. God’s Eye View：学习真实外部数据如何进入Agent与交互界面

阅读[GBFS共用parser](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/sources/gbfsStations.js)和[对应反例](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/sources/gbfsStations.test.mjs)，再看[provider契约](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/registry.js)、[Google provider](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/index.js)和[viewer](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/viewer.js)。这些小而完整的链路适合迁移到前端分析台、Django数据服务和MCP：一个清洗函数供UI与工具共用；无数据、错误和缺key分开；旧异步响应不能覆盖新的用户意图；日期精度与供应商限制需要进入schema而非只写在README。

## B. 当天具体项目支持的5个趋势

1. **上下文治理开始需要端到端账本，而非单次压缩比。** REA保留了小PCAP中分页反而增加约51%模型输入的负结果；context-mode通过本地FTS5回查完整输出；VoiceStudio可返回音频URL/文件而非base64。这三者共同说明：应测完成问题所需的全部调用、返回字节和正确性，不能把“小结果”自动当成省成本。[REA实验](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/experiments/analysis-efficiency/pcap-small-captures.md) · [context-mode分流](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/server.ts#L1958-L2035) · [音频交付契约](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/mcp_server.py#L379-L405)
2. **“兼容”“sandbox”“替代”必须拆到实际行为层。** VoiceStudio的OpenAI兼容SSE先完成生成再传输；context-mode普通子进程在项目cwd运行；xtool仍依赖Apple SDK和认证/设备链。它们可以有用，但词语本身不证明低延迟、文件隔离或完整替代IDE。工程选型应把每个承诺变成独立验收条件。[SSE实现](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/api/routers/openai_compat.py#L629-L643) · [实际cwd](https://github.com/mksglu/context-mode/blob/dbec9809d83172a2fa3edd69cc9b95000c3b9859/src/executor.ts#L282-L318) · [xtool SDK流程](https://github.com/xtool-org/xtool/blob/65bf3cc5a1240fea53ac0748d29a01878222a6ce/Sources/XToolSupport/SDKBuilder.swift#L99-L233)
3. **数据与生成物要保留语义，不能只证明格式有效。** GEV修复Localized String而非把对象强制变成字串；diagram-design同时检查containment声明与实际几何，修CSS selector中的逗号和空白；REA把观察到的查询参数名与推断的路径模板分开。对RAG、可视化和代码Agent，schema合法只是一层，来源、精度、真实关系是另一层。[GBFS](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/sources/gbfsStations.js#L54-L102) · [containment](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/scripts/verify-architecture-containment.py#L520-L774) · [API-surface](https://github.com/morluto/rea/blob/d901561640121272bf1498d85e38e1ac8b3f5793/src/domain/analysisView/webNetworkApiSurfaceView.ts#L14-L51)
4. **长任务可靠性取决于已经产生的外部效果。** ArtCraft要分别追踪供应商job和每张上传结果，却在另一条音频/视频适配器上丢失次要job ID；VoiceStudio线程超时不保证GPU执行停止；GEV用generation与pendingOpen处理卸载后的迟到响应。“请求结束”“工作结束”“产物交付”应各有状态和测试。[批次适配器](https://github.com/storytold/artcraft/blob/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373/crates/api_clients/artcraft/artcraft_router/src/generate/generate_video/providers/artcraft/request_common.rs#L25-L28) · [超时边界](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/backend/services/model_manager.py#L988-L1015) · [viewer生命周期](https://github.com/bilawalsidhu/gods-eye-view/blob/132b9e96dc1491e5db8bf949b1560f4561c925c3/src/layers/streetLevel/providers/google/viewer.js#L149-L265)
5. **Agent工具链的可复现性需要来源、内容和执行环境共同固定。** skills保存source/ref/hash却不把hash全面变成恢复安装的强制条件；diagram-design开始固定CI Actions和依赖；VoiceStudio记录模型许可证据revision但不自动固定运行时下载。锁文件、审计页面和许可清单各自解决一部分问题，不能相互替代。[技能锁语义](https://github.com/vercel-labs/skills/blob/13e4063a1cf913f5606d57d42ab83a86f5001e04/src/local-lock.ts) · [CI依赖与执行](https://github.com/cathrynlavery/diagram-design/blob/11b08eade8049c441ed3df1895e3b527c26c0fbe/.github/workflows/ci.yml) · [模型清单边界](https://github.com/debpalash/VoiceStudio/blob/fdeeec5b0bcbefc9f3f576bb3689686feed8e569/docs/licensing/model-inventory.md)

这些是今天9个可见样本支持的工程观察，不是对整个GitHub、开源生态或行业趋势的定量证明。

## C. 与10月13日实际报告的比较

### C1. 连续出现的6项及实际顺位

| 项目 | 昨日→今日顺位 | 变化 | 昨日→今日累计stars | 两快照差 | 今日stars today |
|---|---:|---|---:|---:|---:|
| morluto/rea | 1→1 | 持平 | 163,731→211,533 | +47,802 | 54,679 |
| bilawalsidhu/gods-eye-view | 2→2 | 持平 | 53,849→55,558 | +1,709 | 1,961 |
| mksglu/context-mode | 3→4 | 下降1位 | 27,380→28,336 | +956 | 969 |
| cathrynlavery/diagram-design | 6→5 | 上升1位 | 52,791→54,313 | +1,522 | 1,815 |
| lyogavin/airllm | 7→7 | 持平 | 37,618→38,392 | +774 | 1,001 |
| storytold/artcraft | 4→8 | 下降4位 | 22,412→25,935 | +3,523 | 4,081 |

昨日采用其10:56:59北京时间官方HTML快照，今天采用10:53浏览器快照，间隔并非严格24小时。累计差只是两份已读报告数字相减；上表刻意把它与官方stars today分列。不能把ArtCraft顺位下降翻译为不再增长，也不能把REA累计差与今日增星的差异补成“缺失stars”。[昨日固定正文](https://github.com/DanielMax937/daily-research-reports/blob/c153427620f4316c779ffa7419381f76fbd81be4/2026-10-13/github-trending.md)

### C2. 报告样本的新面孔与未见项目

- 今天可见、昨天报告未出现：VoiceStudio（第3）、vercel-labs/skills（第6）、xtool（第9）。这三项是**相对昨天报告的新面孔**，不是已证实首次上榜。昨天未知第10项，不能排除其中一个当时也在完整前10
- 昨天可见、今天9项中未见：Open WebUI（昨天第5）、BitNet（第8）、free-claude-code（第9）。今天未知第10项，不能逐一断言全部跌出完整前10，更不能推断维护停滞
- 样本主题从昨日的WebUI/模型网关/低比特推理，增加了本地语音生产、Agent技能分发、跨平台iOS工具链。上下文治理、公开数据可视化和生成工作流仍连续出现；这是样本构成变化，不是全行业份额统计

### C3. 固定源码逐日变化

| 项目 | 昨日完整SHA | 今日完整SHA | 经核验的变化 |
|---|---|---|---|
| REA | a2d8b94dd50dab8d966239dd63ab84718aa8b4b4 | d901561640121272bf1498d85e38e1ac8b3f5793 | ahead 383、behind 0；compare文件列表300项上限，不能当完整diff审计；本文只确认明确选读的证据契约、查询来源、安全边界及实验 |
| God’s Eye View | 8b8ccc9a81379e8b40d4be67610570ee5b159512 | 132b9e96dc1491e5db8bf949b1560f4561c925c3 | ahead 18、behind 0、62净文件；Street View第二provider及GBFS多语名称修复已合入 |
| context-mode | 1a1bed139906ecc048233583bb2fd29290603b7a | dbec9809d83172a2fa3edd69cc9b95000c3b9859 | ahead 2、仅stats.json；执行代码未变，昨日sandbox文字与cwd差异仍在 |
| diagram-design | 41765070ace63009f23c741cedb0c81429710b4f | 11b08eade8049c441ed3df1895e3b527c26c0fbe | ahead 16、39净文件；plugin 2.6.90→2.6.98，CSS导出、containment验证及CI改进，仍无GitHub Release |
| AirLLM | 7bb8a8600937ff15b81016f286142bcdac7ee2d2 | cb807515f640f9489f267adc0c66afb249e90a17 | ahead 1、只改2张star-history图片；没有已确认执行代码增量 |
| ArtCraft | d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373 | d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373 | identical、0变更；批次job ID收缩是同一版本的新核读发现，修复PR仍未合入 |

逐仓比较来源：[REA](https://github.com/morluto/rea/compare/a2d8b94dd50dab8d966239dd63ab84718aa8b4b4...d901561640121272bf1498d85e38e1ac8b3f5793) · [God’s Eye View](https://github.com/bilawalsidhu/gods-eye-view/compare/8b8ccc9a81379e8b40d4be67610570ee5b159512...132b9e96dc1491e5db8bf949b1560f4561c925c3) · [context-mode](https://github.com/mksglu/context-mode/compare/1a1bed139906ecc048233583bb2fd29290603b7a...dbec9809d83172a2fa3edd69cc9b95000c3b9859) · [diagram-design](https://github.com/cathrynlavery/diagram-design/compare/41765070ace63009f23c741cedb0c81429710b4f...11b08eade8049c441ed3df1895e3b527c26c0fbe) · [AirLLM](https://github.com/lyogavin/airllm/compare/7bb8a8600937ff15b81016f286142bcdac7ee2d2...cb807515f640f9489f267adc0c66afb249e90a17) · [ArtCraft](https://github.com/storytold/artcraft/compare/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373...d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373)

### C4. 应更新的昨日结论

REA的[#2454](https://github.com/morluto/rea/issues/2454)已经由维护者关闭并完成清单，不能继续照抄昨日“仍开放”的状态；本轮没有逐一独立复现那12项。diagram-design昨日的CSS selector问题[#420](https://github.com/cathrynlavery/diagram-design/issues/420)已关闭且能从当前实现确认修正，但新[#432](https://github.com/cathrynlavery/diagram-design/pull/432)说明escape paint引用仍有边界，不能把一个修复扩大成导出全面可靠。GEV真正新增街景与GBFS修复，而语音打开地点的[#1113](https://github.com/bilawalsidhu/gods-eye-view/pull/1113)仍未合入。AirLLM的macOS提前验证[#384](https://github.com/lyogavin/airllm/pull/384)以及ArtCraft批次ID保留[#2275](https://github.com/storytold/artcraft/pull/2275)也仍是提案/修复分支，不能提前计算为main进展。

今天最重要的学习方式变化是：保留昨日结构，但把篇幅用在可验证的增量、被修正的风险和仍未合入的边界上；没有代码变化的项目，不靠重新描述README凑“新发现”。
