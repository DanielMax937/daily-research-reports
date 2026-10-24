# 美股 Twitter 观点日报 · 2026-10-24

周六美股现货不开市。到北京时间 10 月 24 日 23:15 为止，时间线上还在消化周五那根 K 线：道指大跌，标普和纳指跌幅小得多，油价把伊朗风险和通胀预期重新推回前台，AI 交易的争论从“还能涨多少”转到“谁在借钱、CDS 有没有裂开”。指数底下，等权股票和能源明显强于被融资担忧压住的大型科技。周末能执行的计划取决于下一则伊朗头条：升级就继续把能源放在股票前面；出现可以结束冲突的说法，帖文里的多头准备的是股票挤空，而不是去追已经把供给中断定到极端的近月原油。

下面每一条归纳都附有帖文链接。收盘点位来自通讯社当日稿，并用通讯社自己的推文核对方向；盘中喊出的油价高点单独标明，不拿来代替收盘价。这是公开帖文的整理，不是投资建议，也不是对任何账户历史业绩的背书。

## 抓取口径

- 报告日期按北京时间 **2026-10-24**。触发时刻约 15:03 UTC，时间线补抓到 **15:15 UTC（北京时间 23:15）**。观察窗口是 **美东 2026-10-23 00:00 至抓取结束**，也就是周五全天加上周六上午到中午。周五收盘是美东 16:00，对应北京时间周六 04:00。
- X 的官方连接器在这次运行里没有可用的搜索和时间线工具。帖文用公开时间线接口读取，链接都是 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果，所以“当前讨论”指的是这 100 个账号窗口内的帖，不是全站每一条提及。
- 不存在官方的“美股 Top 100”。样本是 229 个候选金融媒体、宏观、投资者、交易员、交易所和投行账号，成功读到粉丝数的有 151 个，再按抓取当时的粉丝数取前 100。粉丝数是公开资料读数，会变。排序不代表预测准确度。
- 100 个账号里，**70 个**在窗口内有原创帖，**3 个**只有转发（Bill Ackman、Ben Carlson、Mohnish Pabrai）。路透、经济学人、彭博主号、FinancialJuice 的原创计数停在分页上限附近（约 120 条），是下限。First Squawk、Seeking Alpha 后页读取失败，条数也是下限。德意志银行、富国银行、Jesse Felder 的时间线这次返回失败，表里的 0 是没读到，不能当成确认沉默。
- 窗口内确认没有市场原创的包括 Jim Cramer、Nick Timiraos、Jim Bianco、Lyn Alden、Alf、Carl Icahn、Nouriel Roubini、Gavin Baker。Ray Dalio 发的是一条原则短帖，不是行情判断。Cramer 最近一条可见帖停在 10 月 20 日。

## 周五收盘，帖文在围着什么转

通讯社收盘稿和它们自己的推文一致：道指跌 652.82 点（1.23%）至 52,215.16，标普 500 跌 0.52% 至 7,623.68，纳指跌 0.21% 至 25,955.34。WTI 收 103.27 美元，涨 3.8%；布伦特收 116.72 美元，涨 3.1%，为 4 月以来收盘高点。10 年期美债收益率收在 5% 下方、约 4.999%，当天上升约 4 个基点。全周标普跌 0.5%，纳指跌 0.7%，道指涨 0.4%。依据是 [CNBC 周五盘后稿](https://www.cnbc.com/2026/10/22/stock-market-today-live-update.html) 和 [路透收盘稿](https://www.investing.com/news/stock-market-news/wall-street-futures-dip-after-ai-rout-telecoms-slide-4968816)。推文核对：[Investing.com 写道指收盘跌 650 点](https://x.com/Investingcom/status/2113723918510924145)，[MarketWatch 写道指跌 650 点、油价到 6 个月高位](https://x.com/MarketWatch/status/2113724454077346204)，[路透写科技股稳住、全周仍以 AI 交易动荡收场](https://x.com/Reuters/status/2113785039196414297)，[Investing.com 周六再确认油价和 AI 开支担忧压住全周](https://x.com/Investingcom/status/2113936519035543855)。

周四已经先砸过一波。Benzinga 记录纳指周四跌 2.60% 至 26,008.86，标普跌 1.21% 至 7,663.43，道指几乎走平，CNN 恐惧贪婪指数进了“极度恐惧”。[这条 Benzinga 帖](https://x.com/Benzinga/status/2113643621320638555) 和 [FinancialJuice 的 20/100 极度恐惧读数](https://x.com/financialjuice/status/2113636405670785244) 说的是同一件事。周五尾盘 FinancialJuice 的收盘不平衡单是标普 **-12.56 亿美元**、纳指 100 **-7.96 亿美元**，道指为正的 1.21 亿美元。[帖在这里](https://x.com/financialjuice/status/2113719845485482125)。

油是周五的价格主线，但盘中口号和收盘价要分开看。Kobeissi 盘中依次写下布伦特站上 114、115、117 美元，并称有新高的 34% 概率在本月内看到 WTI 高于 110 美元：[114](https://x.com/KobeissiLetter/status/2113576677397913993)、[115](https://x.com/KobeissiLetter/status/2113616486774473180)、[117](https://x.com/KobeissiLetter/status/2113658171315126666)、[110 美元概率](https://x.com/KobeissiLetter/status/2113668947467984906)。Hedgeye 盘中写布伦特涨 3.2%、高于 118 美元，并称自己仍以 BNO 做多原油：[帖](https://x.com/Hedgeye/status/2113669859292897533)。收盘稿里的布伦特是 116.72 美元。DeItaone 早盘写 WTI 涨过 2 美元、到 101.62 美元，那是上涨过程中的报价，不是收盘：[帖](https://x.com/DeItaone/status/2113604983060897917)。

地缘头条到周六还没停。Unusual Whales 转述特朗普称美国没有在和伊朗谈判、很快会有动作：[帖](https://x.com/unusual_whales/status/2113850722030932114)。First Squawk 转述《华尔街日报》：航母乔治·华盛顿号在接收大量弹药和导弹，为可能的升级做准备：[帖](https://x.com/FirstSquawk/status/2113993956312879132)。《华尔街日报》自己的帖是水兵在该打击群为前线可能升级做准备：[帖](https://x.com/WSJ/status/2113927208402108616)。zerohedge 周五晚间贴出特朗普“可能再做一次行动，否则就坐下来谈”的说法：[帖](https://x.com/zerohedge/status/2113720853603246160)。

## 观点分成四组

### 1. 指数很贵，个股已经在自己的熊市里

Kobeissi 把眼下叫做“隐形熊市”：标普成分股里近 60% 已经处在熊市，指数离纪录高点大约还有 3%，他们把这看成历史性机会：[帖](https://x.com/KobeissiLetter/status/2113593587258560734)。同一天他们又写下美股市值达到 M2 的 350%，为 2000 年互联网泡沫以来最高，2022 年熊市以来标普涨 118%、M2 只涨 9%：[帖](https://x.com/KobeissiLetter/status/2113702478088749307)。两句话放在一起，是“指数贵、大多数股票已经跌出熊市”。

Ryan Detrick 用 10 月的数字把同一件事说得更具体：标普 10 月持平，等权指数月内涨超 4%：[帖](https://x.com/RyanDetrick/status/2113676462591222005)。SentimenTrader 补的是周四的极端分化：10 月 22 日标普跌 1.21%，等权 RSP 涨 0.73%；2008 年以来标普跌超 1% 的 601 天里，这种组合只出现过 3 次：[帖](https://x.com/sentimentrader/status/2113649143986163934)。Stephanie Link 用自己的一周口径写标普微跌、等权 SPW 上涨 195 个基点，同时 10 年期收益率一周下降 41 个基点，已公布盈利增长 38%，估值倍数今年下降 17%，她把年底季节性当作朋友：[帖](https://x.com/Stephanie_Link/status/2113733605725720905)。她的“标普微跌”是她自己的一周表述，和路透全周标普跌 0.5% 的收盘统计并列，不互相替换。

Bespoke 描述周五盘中的质地：周四是“广度好、价格差”，周五是“广度很差、纳指 100 走平”，来回抽打还在继续：[帖](https://x.com/bespokeinvest/status/2113635093340381530)。

### 2. AI 是泡沫、融资问题，还是杠杆平仓

看空融资的一侧有具体价格。Citadel 的 Ken Griffin 被 Unusual Whales 和 Barchart 同时引述为“几乎可以确定处在 AI 泡沫”，Barchart 还写他把它比作互联网泡沫时期的光纤过度建设：[Unusual Whales](https://x.com/unusual_whales/status/2113745025632784710)、[Barchart](https://x.com/Barchart/status/2113544411887944107)。Hedgeye 写 Oracle 5 年期 CDS 高于 300 个基点，AI 相关 CDS 交易自 7 月以来放大到 4 倍，Meta 和英伟达的利差创纪录：[Oracle](https://x.com/Hedgeye/status/2113690918910108084)、[META 与 NVDA](https://x.com/Hedgeye/status/2113707528618168658)。ARK 写超大规模云厂商正在动用它们过去不碰的债市，投资级和高收益 CDS 都在抬升；Cathie Wood 不把这叫做系统性风险，银行 CDS 仍近低位，但她把这张图当作那期节目的结尾：[帖](https://x.com/ARKInvest/status/2113615580041220418)。zerohedge 贴出亚马逊放弃 Loudoun 县数据中心的报道，并问“数据中心走廊变暗对美国其他地方意味着什么”：[报道帖](https://x.com/zerohedge/status/2113742292842357082)、[追问](https://x.com/zerohedge/status/2113743514546626940)。周六 zerohedge 再转高盛图表，标题是动量来回打到零、资本不再便宜：[帖](https://x.com/zerohedge/status/2113975069172990378)，以及 McElligott 称 AI 交易变成“有毒的二选一”、出现 5 个标准差的止损：[帖](https://x.com/zerohedge/status/2113790100446302306)。

看多基本面的一侧认为这是仓位出清。Andreas Steno 写，不要把杠杆事件误认为基本面改变，这是他职业生涯里宏观对冲基金遭受的最重打击之一，它也会过去：[帖](https://x.com/AndreasSteno/status/2113651945122443273)。他同时写，若特朗普“可以很快结束伊朗战争”的说法属实，配置会像 4 月那样走出一轮很陡的反弹：[帖](https://x.com/AndreasSteno/status/2113700746843795721)。对 CDS 图表，他的原话是：看到有人拿微软和亚马逊的 CDS 做图就会取关，不认为这两家会因为 AI 把自己做成破产：[帖](https://x.com/AndreasSteno/status/2113734811730710605)。周六他补了一句：算力若真的过剩，眼下这些事不会发生，互联网类比“差得离谱”：[帖](https://x.com/AndreasSteno/status/2114008196222214587)。Seeking Alpha 转述黑石总裁 Jon Gray 拒绝泡沫说法，称 AI 基础设施需求“近乎抛物线”，并写黑石参与了 CoreWeave 85 亿美元融资、还和谷歌在定制芯片上合作：[帖](https://x.com/SeekingAlpha/status/2113742206464823667)。这是媒体转述，不是 Gray 本人的帖。

Kobeissi 提供了需求侧的一个冷数字：9 月 AI token 支出环比只增 0.2%，为 2025 年 11 月以来最慢；7 月以来 token 价格下降 48%，到每百万 token 0.65 美元。他们把降价解读成可能打开下一轮采用，而不是需求消失：[帖](https://x.com/KobeissiLetter/status/2113734106546573722)。另一条是半导体生产者价格 9 月同比涨 26%，为有记录以来第四大，2021 年之前这个指数几乎年年下降：[帖](https://x.com/KobeissiLetter/status/2113999526142915022)。价格在涨、使用单价在跌，两条可以同时为真。

Jurrien Timmer 把两边收成一个时钟：盈利很强，AI 建设若因此多一点纪律，长期更可持续；同时实际利率已经高到会在高负债世界里惹麻烦，法国 CDS 是他的例证。他把眼下放在“盈利增长、金融条件收紧”的象限，并提醒实际利率相对潜在增长偏高、估值也偏高，散点图的两个尾部历史上都不好：[时钟](https://x.com/TimmerFidelity/status/2113704256918163752)、[估值散点](https://x.com/TimmerFidelity/status/2113620958254964880)。

Gary Black 周五开盘前写标普 2026 年 EPS 预期 368 美元、对应 20.8 倍市盈率、盈利收益率 4.8%，低于国债收益率，这种倒挂上次持续出现在 1990 年代末。他预期伊朗战争结束会让国债收益率回落，同时对特斯拉保持谨慎（他给出的 2026 年市盈率 220 倍、PEG 5 倍）：[帖](https://x.com/garyblack00/status/2113550966121169305)。他还转述高盛主经纪商：周四全球基本面多空基金跌 1.4%，为 7 月以来最差，而且疫情以来第一次三类股票策略同一天跌超 1%：[帖](https://x.com/garyblack00/status/2113600600424272205)。Ryan Detrick 另引高盛主经纪商，全球股票净卖出接近 3 月末的水平：[帖](https://x.com/RyanDetrick/status/2113667694566555863)。

### 3. 油价里有一大块风险溢价，黄金和法国债是连带伤害

Robin Brooks 周六的系列帖把布伦特 117 美元拆开：这个价格对应的波斯湾出口大约是每天 600 万桶，而实际流量大约是每天 1800 万桶；2027 年 12 月合约稳定在 87 美元附近，所以近月的跳涨是短期风险溢价，形态像 3 月和 4 月。亚洲原油进口已经回到战前，中国仍少大约每天 200 万桶，那是对伊朗的封锁，不是恐慌性补库。黄金跌破 4000 美元，在他看来是这轮油价恐惧的函数：[117 美元定价了什么](https://x.com/robin_j_brooks/status/2113963543070466495)、[远月仍在 87 附近](https://x.com/robin_j_brooks/status/2113968676122816813)、[黄金与 3 月的恐惧](https://x.com/robin_j_brooks/status/2113965319114924144)。他同时把法国债叫做油价的代理交易：6 月油价下跌时资金涌入法国债，9 月 10 日沙特东西管道遇袭之后交易反噬：[帖](https://x.com/robin_j_brooks/status/2113589996745789598)。

Holger Zschäpitz 给出法国债的市场价格：10 年期相对德国利差扩到 175 个基点，为 2011 年以来最宽，离欧债危机峰值还差 15 个基点：[帖](https://x.com/Schuldensuehner/status/2113542692307443776)。穆迪维持法国 Aa3、负面展望，5 年期违约保险成本升到 103 个基点，为十多年来高位：[帖](https://x.com/Schuldensuehner/status/2113769167501295635)。

Peter Schiff 的交易结论相反：黄金随股票跌到 4000 美元下方，他称之为买入黄金的时机，白银则看 54 美元下方，并写“对股票利空的东西对黄金利多”：[帖](https://x.com/PeterSchiff/status/2113655049666589124)。这是他的贵金属销售立场，和 Brooks“恐惧会过去”的判断对着放。Kobeissi 则披露他们在黄金反弹到 4200 美元时做空、周五在 4000 美元附近平掉空单：[帖](https://x.com/KobeissiLetter/status/2113638248740487559)。Luke Gromen 贴出另一张长周期图：中国人买的黄金自 1998 年以来跑赢标普全收益，用来反驳“中国股市不行所以黄金只是避险”的口头共识：[帖](https://x.com/LukeGromen/status/2113700314834702681)。

### 4. 季节性、保证金和回购：还没到用杠杆指标宣布见顶的时候

SentimenTrader 写，纽约证交所保证金债务仍比 12 个月均值高 11.9%（数据截止 9 月底）；历史上这个比例还在均值之上时，股票多处于有利区间，跌到均值之下才更常对应熊市。他们因此还不用“这就是顶部”来回答当周的提问，同周材料里还包括必需消费的广度冲刺、金矿股超卖反弹，以及比特币趋势信号转多：[帖](https://x.com/sentimentrader/status/2113733450213867688)。周六他们把权重证据概括为“建设性、有选择”：[帖](https://x.com/sentimentrader/status/2113948619300864402)。

Ryan Detrick 写 10 月的这一段历史上往往是全年较差的时段，而 10 月下旬的低点很常见；情绪走到极端时，又会变成 10 月下旬的买入窗口：[帖](https://x.com/RyanDetrick/status/2113683965617766630)。Kobeissi 预期后面有一大波回购：2026 年以来回购授权同比增 13%，到纪录的 1.305 万亿美元；已执行回购二季度同比增 20%：[帖](https://x.com/KobeissiLetter/status/2113717650119663799)。

利率路径没有统一口径。Bespoke 写，市场对“今年不再加息”的定价从一个月前的 6% 升到 26%：[帖](https://x.com/bespokeinvest/status/2113747414477848719)。Squawk Box 引述摩根士丹利 Andrew Slimmon：存在一种清楚的可能，通胀下来、不会进入一大轮加息，市场回到盈利本身：[帖](https://x.com/SquawkCNBC/status/2113614979416859061)。Stocktwits 预告周二的节目时仍把背景写成“100 美元油价，加上还在谈论加息的美联储”：[帖](https://x.com/Stocktwits/status/2113677603655610627)。美联储账号只贴了下周日程链接，没有在这条帖里预告决定：[帖](https://x.com/federalreserve/status/2113618335065645386)。Liz Ann Sonders 描述的是避险：10 年期收益率和标普的滚动相关性没那么负了，因为收益率这轮更在交易增长而不是通胀：[帖](https://x.com/LizAnnSonders/status/2113593200401400135)。Kobeissi 写国债期权从 9 月底偏爱认沽，转到认购相对认沽溢价约 50 个基点，为 2025 年 3 月以来最高；有一笔约 6.5 万张、权利金约 700 万美元的交易，目标是一个月内 10 年期收益率落到约 4.60%：[帖](https://x.com/KobeissiLetter/status/2113685382961213460)。

增长数据没有一起塌。Liz Ann 写 10 月标普全球美国综合 PMI 初值 56，销售价格仍高、需求和就业都稳，仍指向扎实的 GDP：[帖](https://x.com/LizAnnSonders/status/2113661863082758520)。Hedgeye 写 10 月制造业 PMI 初值 56，为 53 个月高点：[帖](https://x.com/Hedgeye/status/2113628230322172326)。密歇根大学消费者信心终值 48，高于共识 46.3，一年通胀预期 4.7%（[CNBC 稿](https://www.cnbc.com/2026/10/22/stock-market-today-live-update.html)）。Jason Furman 把信心放在疫情前分布的最底部，通胀预期在第 80 到 88 百分位：[帖](https://x.com/jasonfurman/status/2113711426070024502)。他跟踪的三季度 GDP 综合预测是年化 3.2%，私人需求更强，数据在周四公布：[帖](https://x.com/jasonfurman/status/2113743316105752832)。圣路易斯联储 10 月 23 日的现在预测也是三季度实际 GDP 年化 3.2%，一周前是 2.8%：[帖](https://x.com/stlouisfed/status/2113756118115586507)。堪萨斯城联储制造业里，支付价格升到 2022 年中以来最高，收取价格明显回落，价差在扩大：[帖](https://x.com/LizAnnSonders/status/2113585767196869076)。

## 要盯住的五件事

1. **近月原油和远月原油的裂口。** Brooks 用 117 对 87 说明近月挤的是恐惧。裂口收敛，能源股的超额收益和股票的风险溢价会一起重新定价。裂口再扩大，周五那种“防御股也跌、道指领跌”会重复。Hedgeye 已经宣布仍做多 BNO，能源指数 XLE 当天创纪录高点：[XLE](https://x.com/Hedgeye/status/2113632713521410414)。
2. **AI 信用而不是 AI 叙事。** Oracle CDS 300 个基点以上、Meta 与英伟达 CDS 创新高、超大规模厂商发债，是这组账号里能量化的风险。Steno 认为微软、亚马逊的 CDS 图不能推出破产。两条都要留着，触发器是 CDS 和融资头条，不是聊天室里的“泡沫”两个字。
3. **广度是否还在，指数是否还在失血。** 等权强、指数平，是 10 月的主线。Bespoke 已经看到周五广度转差。若下周等权也跟着纳指破位，隐形熊市的“机会”说法就少了一个支柱。
4. **美联储会议前的增长和通胀组合。** PMI 和 GDP 现在预测仍强，密歇根信心极差、短期通胀预期 4.7%，油价在 100 美元以上。Slimmon 的路径是通胀回落、不加息、看盈利；另一侧是 Stocktwits 仍放在“加息言论”的背景里。周四 GDP 是 Furman 点名的下一份硬数据。
5. **周末风险资产的读数。** Kobeissi 周六下午写比特币和以太坊急跌，60 分钟内约 2 亿美元杠杆仓被强平，比特币回到 8 万美元下方：[帖](https://x.com/KobeissiLetter/status/2114006499248816421)。这不是美股收盘，但它是周一开盘前最新的风险偏好读数。

劳动和市场结构还有两条独立的帖。Kobeissi 汇总 2026 年裁员，美国运通被写成约 3840 人，科技行业今年已有约 13.5 万人、330 家公司：[帖](https://x.com/KobeissiLetter/status/2113651913350639989)。运通当天宣布再裁约 5%、约 3500 人，CEO 的用词是更敏捷、更有效率：[Kobeissi](https://x.com/KobeissiLetter/status/2113631530065305785)、[CNBC](https://x.com/CNBC/status/2113623328153837907)。快讯对运通 EPS 的口径不一致：Investing.com 写三季度 EPS 5.42 美元、预期 4.58 美元，收入 201 亿美元、预期 201.2 亿美元：[帖](https://x.com/Investingcom/status/2113596202432266519)；FinancialJuice 写调整后 EPS 4.68 美元，全年调整后 EPS 指引 17.60 至 17.90 美元。两套数字都只当作快讯原文，本报告不把其中一个收成“公司盈利已确认”。股价反应在收盘稿里是下跌约 3% 至 3.7%。

FXHedge 写财政部提出规则，拟从 2027 年 1 月 7 日起禁止机构投资者购买单户住宅，除非属于例外：[帖](https://x.com/Fxhedgers/status/2113736044025942056)。这是住房股周一要单独看的政策标题，和周四因收益率下跌而上涨的房屋建筑商不是同一条逻辑。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向或位置的名字。媒体标题若没有展开具体公司，就不补名单。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 能源多头正在持有 | BNO、XLE、XOM、CVX、SHEL、COP | Hedgeye 称仍做多 BNO；XLE 创纪录高。TrendSpider 周六把 XOM、CVX、SHEL、COP 放在“油价疼痛、图表受益”。CNBC 稿写埃克森、雪佛龙、康菲周五交易在历史高位 | [BNO](https://x.com/Hedgeye/status/2113669859292897533)、[XLE](https://x.com/Hedgeye/status/2113632713521410414)、[大油](https://x.com/TrendSpider/status/2114003570617934121) |
| 半导体站在均线上 | SOXX、SOXL、MU、AMAT、SNDK | 3 倍做多半导体 SOXL 自 10 月 5 日以来跌 50%。SOXX 停在 200 日均线上方，2025 年初以来没跌破过。TrendSpider 把美光放在上升的 30 周均线、存储收入上升的位置，把应用材料描述成自 2025 年关税回撤以来第一次投降式下跌 | [SOXL](https://x.com/bespokeinvest/status/2113578996109545669)、[SOXX](https://x.com/bespokeinvest/status/2113599250755879172)、[MU](https://x.com/TrendSpider/status/2113669278239007088)、[AMAT](https://x.com/TrendSpider/status/2113714575094714680)、[SNDK](https://x.com/TrendSpider/status/2113654178518028710) |
| AI 信用和大型云 | ORCL、META、NVDA、AMZN、MSFT | CDS 与发债见上一节。Meta 的突破正在接受测试。亚马逊数据中心报道被 zerohedge 放大。Benzinga 写微软 10 月 28 日财报，市场预期 EPS 4.72 美元、收入 906.9 亿美元，这是 Benzinga 的预期转述 | [META 图表](https://x.com/TrendSpider/status/2113810205167247644)、[MSFT 日期](https://x.com/Benzinga/status/2113797873921933369)、[AMZN](https://x.com/zerohedge/status/2113742292842357082) |
| 财报周的平台型公司 | GOOGL、AAPL、PLTR、SNOW | Benzinga 写谷歌云加速、市场在看 TPU。CNBC 标题是苹果有可能在财报前从英伟达手里拿回市值第一，正文名单以原标题为准，这里不外推数字。Benzinga 转述 Dan Ives：Palantir 和 Snowflake 接近“开支到变现”的尾声，并称华尔街未来 12 到 18 个月可能低估科技盈利 15% 到 25%。这是转述，不是 Ives 本人帖 | [GOOGL](https://x.com/Benzinga/status/2113677581325357221)、[AAPL](https://x.com/CNBC/status/2113710079207751989)、[Ives](https://x.com/Benzinga/status/2113671541221466268) |
| 期权账本里的杠铃 | META、XLE、NBIS、SPCX | SpotGamma 记录的头寸变化：META 1 月看涨价差约 400 万美元，XLE 2027 年 6 月看涨价差约 700 万美元，NBIS 3 月看涨约 900 万美元，另有 SPCX 12 月看跌的空头约 1000 万美元。这是持仓观察，不是号召 | [帖](https://x.com/spotgamma/status/2113619551128629567) |
| 图表账号单独点名 | NOW、NET、CART、MCD、WDC | ServiceNow 被 TrendSpider 写成突破箱体；Cloudflare 被放在网络攻击的一周；Instacart 在 AI 股票下跌时创历史新高；麦当劳配上“别人恐惧时贪婪”。Seeking Alpha 转述“华尔街认为西部数据的下跌过头”，并给出超过 650 美元的平均目标价，这是媒体汇总 | [NOW](https://x.com/TrendSpider/status/2113628037925535768)、[NET](https://x.com/TrendSpider/status/2113700510574453073)、[CART](https://x.com/TrendSpider/status/2113759874912080209)、[MCD](https://x.com/TrendSpider/status/2113774975656304762)、[WDC](https://x.com/SeekingAlpha/status/2113741642167718162) |
| 特斯拉和 SpaceX | TSLA、SPCX | Gary Black 继续把沟通和估值当作特斯拉的短板，并对比苹果过去 1、3、5 年大幅跑赢特斯拉。ARK 发布 2031 年特斯拉股价模型，窗口内帖文没有写出目标价数字。Unusual Whales 转述彭博：马斯克想在特朗普卸任前把特斯拉和 SpaceX 合成约 3.7 万亿美元的交易。CNBC 用的词是财报之后的合并讨论。TrendSpider 周六用“升空”描述 SPCX | [Black](https://x.com/garyblack00/status/2113693747804278876)、[ARK](https://x.com/ARKInvest/status/2113644362303422651)、[合并传闻](https://x.com/unusual_whales/status/2113782019243303125)、[SPCX](https://x.com/TrendSpider/status/2113827822368137621) |
| 指数技术位 | QQQ、SPY | TrendSpider 写 QQQ 在看跌动量下失掉云层，50 周指数均线在下方；另一条是“小心下面，SPY”。CNBC 标题称标普正在走出看跌形态。这些是形态描述，帖文没有给出可执行的价位 | [QQQ](https://x.com/TrendSpider/status/2113729675843567834)、[SPY](https://x.com/TrendSpider/status/2113684378144690649)、[CNBC](https://x.com/CNBC/status/2113664248505127190) |
| 宽度和医疗 | 等权、XLV、BUG、EWZ、XLI | Hedgeye 的 Keith McCullough 写周五做多网络安全 BUG 和巴西 EWZ 是对的，医疗 XLV 仍是他的长期板块赢家、也是当天亏损来源；工业 XLI 被他称为跌到新的周期低点。零售投资者自周期高点回撤 25% 是他转发的 Hedgeye 图 | [BUG 与 EWZ](https://x.com/KeithMcCullough/status/2113713054882119868)、[XLV](https://x.com/KeithMcCullough/status/2113714521411825784)、[XLI](https://x.com/KeithMcCullough/status/2113639198267969859) |
| 尚未上市、但在占用风险预算 | Anthropic | Unusual Whales 写其上市可能成为历史上最大的股票发行之一。Damodaran 提醒这类公司会用 ARR 一类不熟悉的指标定价，风险投资估值反映的是对 IPO 定价的预期再加下行保护，信息量有限 | [发行](https://x.com/unusual_whales/status/2113760125156577468)、[定价](https://x.com/AswathDamodaran/status/2113652867567657027) |

Bespoke 在周五美东傍晚列出的下一档财报名字是：开盘前阿斯利康、Verizon；收盘后 Cadence、纽柯、Public Storage、Welltower、惠而浦。帖子用了“明天”，而第二天是周六、美股不开市，所以这里只记录名单，不把它们写成周六公布：[帖](https://x.com/bespokeinvest/status/2113744774486265959)。

## 后续走势：两套可以证伪的剧本

帖文没有给出周一的点位预测。能从原文整理出来的是两套条件，以及一套不依赖头条的结构判断。

**升级剧本。** 触发器已经写在周六的帖里：没有谈判、很快有动作、航母补弹、革命卫队称回应会加倍（First Squawk 周六另有一条革命卫队发言人的转述：[帖](https://x.com/FirstSquawk/status/2113993818483892447)）。这条路径上，近月油价维持或扩大相对远月的溢价，能源股保持领先，高融资 AI 和纳指继续承受 CDS 与利率的压力，黄金继续被油价压制，法国债利差继续充当油价代理。Kobeissi 的 34%“本月 WTI 高于 110 美元”是这条路径在预测市场里的一个报价，不是基线。

**缓和剧本。** 触发器是 Steno 引用的那句“战争可以很快结束”，以及 Gary Black“战争结束则收益率回落”。Brooks 的远月油价停在 87 美元附近，说明缓和若被相信，近月可以从风险溢价里退出一大截。Steno 把随后的股票反应类比 4 月的陡峭反弹，并强调那是杠杆回补，不是基本面突然变了。这条路径上追近月原油的赔率差，半导体和被 CDS 叙事打过的大型云更有弹性。SOXX 的 200 日均线、美光的 30 周均线是这组技术帖给出的位置。

**不依赖头条的结构判断。** 指数贵、等权强、回购授权在纪录高位、保证金债务仍高于 12 个月均值、10 月下旬历史上常常先差后出现低点。Detrick、Kobeissi、SentimenTrader、Stephanie Link 站在这一侧。Timmer 的约束是：盈利向上和金融条件收紧可以并存，实际利率已经落在他散点图里历史上回报差的区域。Hedgeye 的指数估值帖是美股市值达到 GDP 的 200%，为最高：[帖](https://x.com/Hedgeye/status/2113619045446725825)。这和 Kobeissi 的市值/M2 是同一类“贵”的证据，不能单独推出下周方向。

周末情绪帖本身不是预测。Stocktwits 周五收盘写“周末把股市关上”，周六写“下跌还在跌”：[周五](https://x.com/Stocktwits/status/2113626781991235614)、[周六](https://x.com/Stocktwits/status/2113972778298679336)。TrendSpider 则把“你说过下次回调就买”直接对着当前的位置：[帖](https://x.com/TrendSpider/status/2113616441547034728)。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和仓位，方便对照周一开盘。它不决定任何人的仓位大小，也不把付费会员的历史平仓当成可以跟着做的指令。RealVision 周六转述的清单更接近可执行的顺序：先看宏观变化率，再看市场是不是已经挤在同一笔交易里，最后才是技术形态；别人的风险承受不是你的风险承受：[宏观三步](https://x.com/RealVision/status/2113798433030935003)、[风险](https://x.com/RealVision/status/2113708130152386754)。

**开盘前只核对三样东西。** 近月布伦特相对 2027 年 12 月合约还在不在 Brooks 说的极端裂口里；Oracle、Meta、英伟达的 CDS 有没有继续走阔；比特币周日晚上是否还停在 Kobeissi 周六写下的 8 万美元下方。三样都变差，周一的默认敞口是能源高于高融资科技。三样都缓和，默认敞口是等权和被砸过的半导体高于近月原油。

**已经公开的方向，按账号而不是按共识。**

- Hedgeye / Keith McCullough：做多原油（BNO），能源指数在纪录高位；工业放在周期低点；医疗是长期多头、周五却在亏；网络安全和巴西是当天的分散化仓位；他并写过去两天买罗素 2000 的短线看跌是“容易的一球”：[IWM 看跌](https://x.com/KeithMcCullough/status/2113637365533057134)。小盘若延续周五的广度恶化，这张看跌期权的逻辑还在；等权若重新转强，这张期权就是对冲而不是方向。
- SpotGamma 看到的期权增量是杠铃：科技看涨价差和能源看涨价差同时出现，并有人卖出 SpaceX 的 12 月看跌。这和“要么全仓 AI、要么全仓逃命”不同，是两边都留位置。
- Kobeissi：黄金空单已在 4000 美元附近了结；公开的前瞻是回购潮和“隐形熊市等于机会”。他们没有在这些帖里给出标普的目标点位。
- Schiff：股票下跌时买黄金和白银。这是单边商品结论，和 Brooks、Kobeissi 的黄金处理都不同。
- Gary Black：收益率回落的条件是战争结束；特斯拉不在他的舒适区。特斯拉的交易如果要做，窗口内更接近事件（合并传闻、FSD 沟通）而不是他的估值框架。
- Detrick / SentimenTrader / Stephanie Link：10 月下旬的弱、情绪极端、等权强、保证金未跌破均值，被他们用作“还不是用见顶框架全仓撤离”的理由。对应的计划是分批而不是一次买完，位置参照 Bespoke 的 SOXX 200 日均线，而不是参照已经跌掉 50% 的 SOXL。Bespoke 把 SOXL 的跌幅写成事实，没有写成买入理由。
- 债券：Kobeissi 记录的期权在赌 10 年期往 4.60% 走；Bob Elliott 在周三的电视采访里把债券说成眼下可以买的东西，帖文是周六补发的链接：[帖](https://x.com/BobEUnlimited/status/2113937910747574284)。BlackRock 的官方账号在卖主动债券产品 BINC，理由是利率和信用条件在变：[帖](https://x.com/BlackRock/status/2113725151711797741)。三条都指向“利率有交易”，没有一条给出周一的具体久期。

**财报周的顺序。** 先看已经在 CDS 里的名字（Oracle、Meta、英伟达）和 10 月 28 日的微软，再看谷歌云和 TPU 的资本开支口径，然后才是苹果与英伟达的市值叙事。运通的裁员说明 AI 节约成本的故事已经进了金融股的业绩会，道指对这种“准备迎接 AI”的反应是下跌。折扣零售对柴油的敏感写在 CNBC 稿里：富国银行估计柴油价格上升会把经营利润率的拖累从 18 个基点提高到约 27 个基点，Dollar Tree、Dollar General 盘中跌约 5%。这是油价进消费股的传导，推文讨论明显少于能源和半导体。

**明确留在观察、不放进计划的东西。** Ackman 窗口内没有原创市场帖；他转发的一条中文帖转述他近期仍把房利美、房地美说成不对称仓位，那是转发对象的文字，不是他这天写的：[转发](https://x.com/casualstudy023/status/2113693203413319859)。Cathie Wood 周六只确认了别人对 Meta 三季度的正面评价，并附和马斯克，没有新的仓位说明：[Meta](https://x.com/CathieDWood/status/2113842475194327100)。Cramer、Timiraos、Bianco 这天没有可引用的新判断。

## 帖文索引

收盘与全周：[Investing.com 650 点](https://x.com/Investingcom/status/2113723918510924145)、[MarketWatch](https://x.com/MarketWatch/status/2113724454077346204)、[路透](https://x.com/Reuters/status/2113785039196414297)、[全周油价与 AI](https://x.com/Investingcom/status/2113936519035543855)、[CNBC 盘后稿](https://www.cnbc.com/2026/10/22/stock-market-today-live-update.html)。

地缘与油：[布伦特 117](https://x.com/KobeissiLetter/status/2113658171315126666)、[WTI 高于 110 的概率](https://x.com/KobeissiLetter/status/2113668947467984906)、[Hedgeye 做多 BNO](https://x.com/Hedgeye/status/2113669859292897533)、[Brooks 解释 117 美元](https://x.com/robin_j_brooks/status/2113963543070466495)、[远月 87 美元](https://x.com/robin_j_brooks/status/2113968676122816813)、[特朗普称未在谈判](https://x.com/unusual_whales/status/2113850722030932114)、[航母补弹](https://x.com/FirstSquawk/status/2113993956312879132)。

指数结构：[隐形熊市](https://x.com/KobeissiLetter/status/2113593587258560734)、[市值相对 M2](https://x.com/KobeissiLetter/status/2113702478088749307)、[等权 10 月](https://x.com/RyanDetrick/status/2113676462591222005)、[10 月下旬](https://x.com/RyanDetrick/status/2113683965617766630)、[保证金](https://x.com/sentimentrader/status/2113733450213867688)、[回购](https://x.com/KobeissiLetter/status/2113717650119663799)、[Stephanie Link 的一周](https://x.com/Stephanie_Link/status/2113733605725720905)。

AI 与信用：[Griffin / Barchart](https://x.com/Barchart/status/2113544411887944107)、[Oracle CDS](https://x.com/Hedgeye/status/2113690918910108084)、[ARK 论发债](https://x.com/ARKInvest/status/2113615580041220418)、[Steno 论杠杆事件](https://x.com/AndreasSteno/status/2113651945122443273)、[Steno 论微软和亚马逊 CDS](https://x.com/AndreasSteno/status/2113734811730710605)、[token 支出](https://x.com/KobeissiLetter/status/2113734106546573722)、[Timmer 时钟](https://x.com/TimmerFidelity/status/2113704256918163752)、[Gary Black 的估值](https://x.com/garyblack00/status/2113550966121169305)。

交叉资产：[法国利差](https://x.com/Schuldensuehner/status/2113542692307443776)、[Schiff 买黄金](https://x.com/PeterSchiff/status/2113655049666589124)、[国债期权](https://x.com/KobeissiLetter/status/2113685382961213460)、[比特币强平](https://x.com/KobeissiLetter/status/2114006499248816421)、[Slimmon 论加息与盈利](https://x.com/SquawkCNBC/status/2113614979416859061)、[今年不再加息的定价](https://x.com/bespokeinvest/status/2113747414477848719)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-10-24 抓取时的公开读数。原创条数是观察窗口内的原创帖。标成 120 左右的通讯社账号触到了分页上限。德意志银行、富国银行、Jesse Felder 的 0 是读取失败。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,430,305 | 120 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,316,183 | 120 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,277,341 | 98 |
| 4 | [@business](https://x.com/business) | 10,482,723 | 119 |
| 5 | [@mcuban](https://x.com/mcuban) | 8,558,122 | 1 |
| 6 | [@CNBC](https://x.com/CNBC) | 6,257,336 | 73 |
| 7 | [@unusual_whales](https://x.com/unusual_whales) | 5,424,029 | 20 |
| 8 | [@MarketWatch](https://x.com/MarketWatch) | 4,645,006 | 41 |
| 9 | [@paulkrugman](https://x.com/paulkrugman) | 4,420,032 | 0 |
| 10 | [@zerohedge](https://x.com/zerohedge) | 3,433,160 | 79 |
| 11 | [@BillAckman](https://x.com/BillAckman) | 3,033,533 | 0 |
| 12 | [@CathieDWood](https://x.com/CathieDWood) | 2,994,092 | 2 |
| 13 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,696,397 | 15 |
| 14 | [@RayDalio](https://x.com/RayDalio) | 2,552,835 | 1 |
| 15 | [@jimcramer](https://x.com/jimcramer) | 2,503,125 | 0 |
| 16 | [@markets](https://x.com/markets) | 2,045,197 | 0 |
| 17 | [@DeItaone](https://x.com/DeItaone) | 1,966,138 | 42 |
| 18 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,770,074 | 4 |
| 19 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,734,397 | 2 |
| 20 | [@NYSE](https://x.com/NYSE) | 1,699,367 | 11 |
| 21 | [@federalreserve](https://x.com/federalreserve) | 1,598,402 | 2 |
| 22 | [@Investingcom](https://x.com/Investingcom) | 1,530,999 | 28 |
| 23 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,507,395 | 7 |
| 24 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,468,801 | 11 |
| 25 | [@Bloomberg](https://x.com/Bloomberg) | 1,349,553 | 0 |
| 26 | [@TheStreet](https://x.com/TheStreet) | 1,228,873 | 100 |
| 27 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,193,833 | 10 |
| 28 | [@Stocktwits](https://x.com/Stocktwits) | 1,192,308 | 5 |
| 29 | [@USTreasury](https://x.com/USTreasury) | 1,163,685 | 1 |
| 30 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,143,084 | 0 |
| 31 | [@BlackRock](https://x.com/BlackRock) | 1,080,944 | 1 |
| 32 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,088 | 35 |
| 33 | [@financialjuice](https://x.com/financialjuice) | 954,094 | 120 |
| 34 | [@tradingview](https://x.com/tradingview) | 906,497 | 0 |
| 35 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 889,139 | 0 |
| 36 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,770 | 20 |
| 37 | [@charliebilello](https://x.com/charliebilello) | 873,462 | 1 |
| 38 | [@Citi](https://x.com/Citi) | 853,487 | 0 |
| 39 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 845,132 | 14 |
| 40 | [@ARKInvest](https://x.com/ARKInvest) | 822,370 | 2 |
| 41 | [@biancoresearch](https://x.com/biancoresearch) | 791,503 | 0 |
| 42 | [@MorganStanley](https://x.com/MorganStanley) | 757,711 | 0 |
| 43 | [@CNBCnow](https://x.com/CNBCnow) | 752,513 | 0 |
| 44 | [@TrendSpider](https://x.com/TrendSpider) | 718,717 | 18 |
| 45 | [@Nouriel](https://x.com/Nouriel) | 699,987 | 0 |
| 46 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,179 | 0 |
| 47 | [@LukeGromen](https://x.com/LukeGromen) | 638,770 | 3 |
| 48 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,912 | 0 |
| 49 | [@EricBalchunas](https://x.com/EricBalchunas) | 629,559 | 4 |
| 50 | [@garyblack00](https://x.com/garyblack00) | 584,167 | 5 |
| 51 | [@Barchart](https://x.com/Barchart) | 577,163 | 19 |
| 52 | [@FirstSquawk](https://x.com/FirstSquawk) | 574,315 | 60 |
| 53 | [@eWhispers](https://x.com/eWhispers) | 571,923 | 1 |
| 54 | [@MadMoneyOnCNBC](https://x.com/MadMoneyOnCNBC) | 543,589 | 0 |
| 55 | [@AswathDamodaran](https://x.com/AswathDamodaran) | 520,653 | 3 |
| 56 | [@carlquintanilla](https://x.com/carlquintanilla) | 513,776 | 1 |
| 57 | [@LiveSquawk](https://x.com/LiveSquawk) | 505,806 | 60 |
| 58 | [@UBS](https://x.com/UBS) | 499,496 | 0 |
| 59 | [@NickTimiraos](https://x.com/NickTimiraos) | 493,727 | 0 |
| 60 | [@NikkeiAsia](https://x.com/NikkeiAsia) | 489,272 | 72 |
| 61 | [@KeithMcCullough](https://x.com/KeithMcCullough) | 478,465 | 18 |
| 62 | [@Fxhedgers](https://x.com/Fxhedgers) | 472,113 | 4 |
| 63 | [@MacroAlf](https://x.com/MacroAlf) | 465,577 | 0 |
| 64 | [@TheStalwart](https://x.com/TheStalwart) | 453,244 | 18 |
| 65 | [@CNBCFastMoney](https://x.com/CNBCFastMoney) | 451,642 | 0 |
| 66 | [@Hedgeye](https://x.com/Hedgeye) | 447,605 | 12 |
| 67 | [@robin_j_brooks](https://x.com/robin_j_brooks) | 398,359 | 13 |
| 68 | [@awealthofcs](https://x.com/awealthofcs) | 394,751 | 0 |
| 69 | [@RealVision](https://x.com/RealVision) | 392,267 | 11 |
| 70 | [@Schuldensuehner](https://x.com/Schuldensuehner) | 385,443 | 4 |
| 71 | [@GuyAdami](https://x.com/GuyAdami) | 382,222 | 3 |
| 72 | [@LHSummers](https://x.com/LHSummers) | 366,570 | 0 |
| 73 | [@GavinSBaker](https://x.com/GavinSBaker) | 356,968 | 0 |
| 74 | [@SantiagoAuFund](https://x.com/SantiagoAuFund) | 346,188 | 5 |
| 75 | [@Benzinga](https://x.com/Benzinga) | 345,288 | 58 |
| 76 | [@SeekingAlpha](https://x.com/SeekingAlpha) | 343,920 | 60 |
| 77 | [@jasonfurman](https://x.com/jasonfurman) | 340,417 | 14 |
| 78 | [@stlouisfed](https://x.com/stlouisfed) | 337,386 | 6 |
| 79 | [@WellsFargo](https://x.com/WellsFargo) | 335,116 | 0 |
| 80 | [@BobEUnlimited](https://x.com/BobEUnlimited) | 306,477 | 3 |
| 81 | [@AndreasSteno](https://x.com/AndreasSteno) | 298,990 | 12 |
| 82 | [@Barclays](https://x.com/Barclays) | 296,460 | 0 |
| 83 | [@iancassel](https://x.com/iancassel) | 295,030 | 3 |
| 84 | [@jam_croissant](https://x.com/jam_croissant) | 282,694 | 3 |
| 85 | [@howardlindzon](https://x.com/howardlindzon) | 278,289 | 3 |
| 86 | [@sentimentrader](https://x.com/sentimentrader) | 270,111 | 5 |
| 87 | [@MohnishPabrai](https://x.com/MohnishPabrai) | 269,655 | 0 |
| 88 | [@bespokeinvest](https://x.com/bespokeinvest) | 267,972 | 16 |
| 89 | [@NewYorkFed](https://x.com/NewYorkFed) | 256,869 | 0 |
| 90 | [@MorningstarInc](https://x.com/MorningstarInc) | 240,329 | 7 |
| 91 | [@Nasdaq](https://x.com/Nasdaq) | 238,946 | 5 |
| 92 | [@altcap](https://x.com/altcap) | 235,203 | 4 |
| 93 | [@TimmerFidelity](https://x.com/TimmerFidelity) | 231,224 | 6 |
| 94 | [@RyanDetrick](https://x.com/RyanDetrick) | 226,205 | 10 |
| 95 | [@Stephanie_Link](https://x.com/Stephanie_Link) | 213,846 | 1 |
| 96 | [@petenajarian](https://x.com/petenajarian) | 212,658 | 1 |
| 97 | [@InvescoUS](https://x.com/InvescoUS) | 212,158 | 0 |
| 98 | [@Qullamaggie](https://x.com/Qullamaggie) | 188,142 | 0 |
| 99 | [@jessefelder](https://x.com/jessefelder) | 170,550 | 0 |
| 100 | [@spotgamma](https://x.com/spotgamma) | 153,008 | 3 |

