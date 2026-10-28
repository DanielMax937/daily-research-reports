# 美股 Twitter 观点日报 · 2026-10-28

周二的收盘价只写到了两条指数。First Squawk 的纳斯达克收盘是涨 1.21% 到 26484.86，道指涨 0.07% 到 52399.09：[纳斯达克](https://x.com/FirstSquawk/status/2115175570632053046)、[道指](https://x.com/FirstSquawk/status/2115175594132640132)。同一账号的盘后综述把纳斯达克 100 写成涨 1.3%、半导体指数涨 3.6%，原因是大型科技财报和美联储决议之前的科技股上涨，Meta 250 亿美元股票发售获 5 倍超额认购，甲骨文用 Cerebras 芯片扩大与 OpenAI 的人工智能合作：[帖](https://x.com/FirstSquawk/status/2115187615028916646)。这次抓到的帖里没有标普现货收盘点位。Investing.com 的收盘标题是美股收高、VIX 下跌、科技股连续第二天上涨：[帖](https://x.com/Investingcom/status/2115175284320215251)。到美东周三早上约 8:17，现货还没开盘。盘前是另一组数字：Gary Black 写下盘前标普涨 0.1%、盘前纳斯达克 100 涨 0.3%，布伦特站上 115 美元；更晚一点，The Stalwart 写下纳斯达克期货涨 0.46%。下午 2 点是沃什的决议，Alphabet 和微软在收盘后。

下面每一条归纳都附有帖文链接。结算价、盘前期货和早盘口号按发帖时间分开。媒体标题里没有写出的目标价和公司名，这里不补。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-10-28**。触发时刻约 12:04 UTC，时间线补抓到 **约 12:17 UTC（北京时间 20:17，美东 8:17）**。观察窗口是 **2026-10-27 16:00 UTC 至抓取结束**，也就是北京时间周三零点到晚上 8 点 17 分。这覆盖美东周二中午以后的现货交易、周二收盘，以及周三开盘前。美股现货 9:30 才开盘，所以周三的指数涨跌都是期货或盘前。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。公开趋势读到的是 Cuba、`#dwts`、Shirley、`#VisionQuest`、Iryo，以及 Julio y Fer。里面没有标普、纳指或个股话题。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。
- 不存在官方的“美股 Top 100”。这次试了 **352** 个候选，成功读到粉丝数的有 **323** 个。排序时拿掉加密货币账号（Michael Saylor、Watcher.Guru、Bitcoin Magazine、Coin Bureau、Documenting Bitcoin、Mike Novogratz、Scott Melker、Forbes Crypto、Preston Pysh）、两个不是美股市场账号的账号（Noah Smith、OECD），以及综合新闻账号（CNN、纽约时报主号、BBC World、Fox News、华盛顿邮报、TIME、美联社、卫报、Politico、The Hill、日经主号、Newsweek、大西洋月刊、路透世界）。这些综合新闻账号粉丝数很高，放进排序会把交易员和通讯社挤出去。用来排序的账号是 **298** 个，截止在日经亚洲（约 48.9 万粉）。Keith McCullough、Hedgeye、The Stalwart、巴伦、Javier Blas、Robin Brooks、Gold Telegraph、Bespoke、Ryan Detrick、SpotGamma、Kitco、The Transcript 落在线外，引用时会写明。SpotGamma 的资料接口这次没有读到粉丝数，不进这张表；它的帖仍在。排序不代表预测准确度。
- 100 个账号里，**68 个**在窗口内有按帖文链接去重后的原创帖。路透补抓后读穿了窗口，242 条。First Squawk 读穿了窗口，272 条。彭博商业账号 255 条，分页在窗口内结束。德意志银行、Mark Minervini 和 TradingView 的时间线读取失败，表里的 0 不是确认沉默。彭博主号可见时间线最新帖仍停在 10 月 12 日，BBC Business 停在 2024 年，CNN Business 停在 2021 年，这三家的 0 同样不能当成确认沉默。Nick Timiraos 的可见时间线最新帖在周二 10:41 UTC，早于窗口起点，窗口内没有新帖。

## 周二收盘和周三早上，讲的不是同一根 K 线

收盘价以 First Squawk 那两行为准：纳斯达克 26484.86，涨 1.21%，涨 315.48 点；道指 52399.09，涨 0.07%，涨 37.51 点。纳斯达克 100 的 1.3% 和半导体指数的 3.6% 写在另一条综述里。标普现货收盘点位这次没有出现在已读到的收盘帖里，不用周一的 7677.10 去推。Investing.com 只确认方向：美股收高，VIX 下跌，科技股连涨第二天。《华尔街日报》市场账号的标题是美股在财报和美联储声明前继续上涨：[帖](https://x.com/WSJmarkets/status/2115178876099789280)。纽交所的节目提要写成芯片股延续涨势、为期两天的会议开场：[帖](https://x.com/NYSE/status/2115172269286740328)。

收盘前的买卖失衡仍是卖盘。FinancialJuice 记下的收盘失衡是标普 -1050.1、纳斯达克 100 -2059.8、道指 -136.7、七巨头 -504.0，单位是百万美元：[帖](https://x.com/financialjuice/status/2115169388991242595)。指数收涨，和这笔失衡的方向相反。

周三盘前至少有两张快照，中间隔了大约 40 分钟。Gary Black 在 10:24 UTC 写下：美股盘前小幅走高，标普涨 0.1%，纳斯达克 100 涨 0.3%；油价上涨抵消了人工智能的涨幅；布伦特站上每桶 115 美元，因为有报道称美国可能在中期选举后打击伊朗；他等待的是偏鹰的按兵不动，以及今天 Alphabet、微软和明天亚马逊的财报。他写下的估值是标普 2026 年每股收益 369 美元，对应 20.9 倍市盈率、收益率 4.8%，和 5.01% 的 10 年期收益率倒挂；他预计这组收益率会在伊朗紧张缓和后回落。个股上，SK 海力士大超预期、并说长期内存需求至少到 2030 年都会超过供给，三星和美光跟着涨；多数科技股上涨，特斯拉和 SpaceX 在合并猜测里更高，Robinhood 因三季度业绩偏弱下跌。他对特斯拉保持谨慎，理由是估值已经拉高、盈利预测在下修，以及自动驾驶技术会变成普通商品：[帖](https://x.com/garyblack00/status/2115389356307341625)。The Stalwart 在 11:00 UTC 另写期货再次转绿，纳斯达克期货涨 0.46%：[帖](https://x.com/TheStalwart/status/2115398342985265289)。CNBC 更早的一条只说期货变动不大，交易员在等美联储和大型科技财报：[帖](https://x.com/CNBC/status/2115204458791551123)。这几条都是盘前，都不能写成周三收盘。

零对冲在抓取结束前的盘前异动是：七巨头里 Alphabet 领涨，因为有人说 OpenAI 打算买谷歌的人工智能芯片；英伟达 +0.8%，Meta +0.2%，特斯拉 +0.2%，亚马逊 +0.2%，苹果 -0.4%，微软 -0.3%。Axogen 涨 13%。波士顿科学跌 6%，因为全年调整后每股收益指引低于平均预期。Enphase 跌 18%：[帖](https://x.com/zerohedge/status/2115415265957560615)。

## 观点分成四组

### 1. 按住是基准，鹰不鹰分成四句话

决定还没出来。已经写下来的基准是维持利率不变，分歧在措辞和 12 月。

彭博的标题是，即便 9 月通胀数据比预期热，美联储仍预计周三维持利率，并对 12 月的决定点头：[帖](https://x.com/business/status/2115295021930856683)。福克斯商业频道写 9 月 CPI 同比 3.7%，高于 2% 的目标，市场给维持不变的概率是 90.6%：[帖](https://x.com/FoxBusiness/status/2115146012000203261)。路透的早间播客写成：政策制定者预计维持利率，同时暗示后面仍可能加息：[帖](https://x.com/Reuters/status/2115394417758540250)。CNBC 的直播标题是不预计加息，眼睛在沃什接下来怎么说：[帖](https://x.com/CNBC/status/2115409193528177061)。零对冲的预览标题是，加息现在已经“难以想象”，问题变成沃什如何解释在偏热的 CPI 之后跳过这一次：[帖](https://x.com/zerohedge/status/2115294770947916155)。

线外的 Robin Brooks 在周二晚上写的是另一条曲线：法国的危机把美国收益率曲线压平了，沃什明天没有必要偏鹰。他把沃什在杰克逊霍尔转鹰、以及 9 月 16 日那次一致加息，写成更早的事：[帖](https://x.com/robin_j_brooks/status/2115179994825822222)。这句写在《华尔街日报》那条“中期选举后可能打击伊朗”之前。周三早上他没有改这句，改写的是美元和油。线外的 Keith McCullough 周三早上仍把美元多头信号写成加速的通胀和偏鹰的美联储：[帖](https://x.com/KeithMcCullough/status/2115377512117346632)。线外的 Kitco 转述 Natixis：周三不太可能用加息制造意外，但 7 月那组异议者可能回来，新闻发布会可能给出 2026 年剩余时间的线索：[帖](https://x.com/KitcoNewsNOW/status/2115414789564326216)。线外的 SpotGamma 写，美联储可能已经被定价成暂停，期权市场却没有把这一周定成安静的一周；标普的事件波动率偏高，仓位偏防御，更大的问题不是美联储做什么，而是市场会走多远：[帖](https://x.com/spotgamma/status/2115126483450478791)。

线外的 Bob Elliott 把发达经济体 3%–4% 的通胀和央行的慢动作放在一起，称作冰川式的加息周期：[帖](https://x.com/BobEUnlimited/status/2115401943397044498)。新西兰是这场会旁边的对照。储备银行把官方现金利率维持在 2.75%，预期是 3%。会议记录写四人支持不动，三人支持加息。行长 Breman 说接下来的会议很可能进一步加息：[维持](https://x.com/FirstSquawk/status/2115247512739324048)、[分歧](https://x.com/FirstSquawk/status/2115250252630687907)、[后续加息](https://x.com/financialjuice/status/2115265221476454768)。彭博写新西兰元在意外按住之后下跌：[帖](https://x.com/business/status/2115297538425094385)。

美债的买方结构被 El-Erian 单独写了一句。他引用彭博的标题“对美国友好的国家把美债购买砍了 60%，亚洲打头”，说历史上可靠的买家在后退，买方正在变成更战术、更短期的投资者和交易员：[帖](https://x.com/elerianm/status/2115394735862898829)。Barchart 用了同一组 60%：[帖](https://x.com/Barchart/status/2115297711671103591)。周二的 5 年期拍卖是另一行数字：高收益率 4.845%，尾部 0.4 个基点，投标倍数 2.33，发行 700 亿美元，间接投标 60.0%：[帖](https://x.com/financialjuice/status/2115127238555312507)。财政部接受了 60 亿美元买回，达到上限，收到的报价是 107.46 亿美元，对象是 2046–2056 年到期的息票债：[帖](https://x.com/FirstSquawk/status/2115166763692507594)。Andy Constan 把这个节奏写成每年 1920 亿美元，相当于计划新发行量的 43%，并写贝森特在压低长期利率：[帖](https://x.com/dampedspring/status/2115142764782305477)。

Kobeissi 写的是相关性，不是点位。10 年期收益率和纳斯达克 100 的 20 日相关性升到 +0.51，为 3 月回调以来最高，9 月最后一周还是 -0.68；在那之前连续 6 个月为负。他们把这写成国债再次在科技股下跌时充当对冲，和 3 月以及 2025 年 3–4 月那次一样：[帖](https://x.com/KobeissiLetter/status/2115413042200535298)。Liz Ann Sonders 写 10 年期收益率和标普的滚动相关性继续走高：[帖](https://x.com/LizAnnSonders/status/2115401213340471356)。Ryan Detrick 在线外写，CCC 级利差今年明显走阔，但高收益利差只是回到 3 月底的水平；如果这是第一块多米诺，它还没有碰倒别的：[帖](https://x.com/RyanDetrick/status/2115236647281250560)。Keith 写高收益公司债利差昨天只收了 3 个基点，趋势没有变：[帖](https://x.com/KeithMcCullough/status/2115369567400898910)。

### 2. 超预期和盘后下跌写在同一批财报里

内存是周三早上还在涨的那一组。SK 海力士三季度营业利润 83.3 万亿韩元，高于 LSEG 聪明预期的 76.7 万亿；收入 104.6 万亿，高于 98.3 万亿；净利润 39.5 万亿，低于 55.4 万亿：[帖](https://x.com/FirstSquawk/status/2115224735219102114)。股东回报被写成 2026 年大约 100 万亿韩元，其中现金分红超过 30 万亿，回购并注销超过 60 万亿：[帖](https://x.com/FirstSquawk/status/2115224851522986339)。三季度股息每股 2 万韩元，含来自铠侠投资的 1 万韩元特别股息，另决定回购 20 万亿韩元：[帖](https://x.com/FirstSquawk/status/2115225237587726728)。公司说四季度 DRAM 出货比三季度增两成出头，NAND 增中个位数；HBM4 预计在四季度的 HBM 出货和收入份额上超过 HBM3E；2027 年 HBM 谈判已经定下来：[帖](https://x.com/FirstSquawk/status/2115226832614388002)。The Transcript 补了营业利润率 80%、DRAM 平均售价环比大约 +20%、NAND 平均售价环比升到两成出头、长期协议锁住 2027–28 年产能的一半以上：[利润率](https://x.com/TheTranscript_/status/2115335800414163087)。韩国综合指数收盘涨 6.63%，为 7 月 31 日以来最强的单日：[帖](https://x.com/FirstSquawk/status/2115331589593079928)。Investing.com 把同一天写成芯片股带动指数跳涨 6.6%：[帖](https://x.com/Investingcom/status/2115361669073244181)。Cramer 写海力士兑现了，存储交易还能再打；如果海力士能靠 2028 年的可见度涨这么多，美光应该是今天最大的赢家：[兑现](https://x.com/jimcramer/status/2115245989774668239)、[美光](https://x.com/jimcramer/status/2115364643552293194)。TrendSpider 写周三早上存储股在海力士财报后走高，点名 SNDK、美光、西部数据和希捷：[帖](https://x.com/TrendSpider/status/2115413685598601361)。线外的 Andreas Steno 只写了一句：海力士再次大超所有预期：[帖](https://x.com/AndreasSteno/status/2115367666781225358)。

超预期之后下跌的名单和这组存储股分开。

Robinhood 的数字在不同账号里对不上，按原帖保留。First Squawk：收入 14.00 亿美元，低于 IBES 的 14.22 亿；每股收益 0.51 美元；调整后每股收益 0.60 美元，高于预期 0.56 美元；净利润 4.76 亿美元；调整后 EBITDA 8.08 亿美元，高于 7.655 亿；净存款 160 亿美元；黄金订阅用户纪录 520 万；交易收入同比增 19% 到 8.67 亿美元：[收入](https://x.com/FirstSquawk/status/2115174211186741539)、[EBITDA](https://x.com/FirstSquawk/status/2115174238114259078)。Gary Black 用的收入预期是 14.4 亿美元，净存款预期 174 亿美元、实际 157 亿美元，月活 1300 万对预期 1410 万，盘后跌 5%。他记下的指引是全年调整后运营费用收到 26.8–27.5 亿美元，以及 10 月净存款月初至今已经超过 130 亿美元，其中 60 亿美元来自戴尔家族对特朗普账户的供款：[帖](https://x.com/garyblack00/status/2115179102420271306)。TrendSpider 把调整后每股收益 0.60 对 0.56、销售额 14.24 亿对 14.22 亿写成双超，同时写股票在跌：[帖](https://x.com/TrendSpider/status/2115174530029072673)。The Transcript 写成双双不及预期，盘后跌 4%，并引用首席执行官说四季度带着强劲势头进入：[帖](https://x.com/TheTranscript_/status/2115173805740224961)。Stocktwits 的三个字是双双不及预期：[帖](https://x.com/Stocktwits/status/2115176202461720990)。

希捷同样有两套动词。TrendSpider：调整后每股收益 7.68 美元对 7.42 美元，销售额 42.33 亿对 41.38 亿，上调二季度每股收益和销售指引，季度股息提高 3%，股价 -7.38%：[帖](https://x.com/TrendSpider/status/2115173947427967421)。The Transcript 引首席执行官说又一个纪录盈利季度、9 月季度自由现金流为历史最高，盘后跌 8%：[帖](https://x.com/TheTranscript_/status/2115174323925487805)。Earnings Whispers 问，花旗的 Asiya Merchant 早上说希捷不及预期，为什么别人都在报超预期：[帖](https://x.com/eWhispers/status/2115388230552207448)。

其余已经落地的反应：恩智浦收入 37.8 亿美元对 37.5 亿，调整后每股收益 4.20 美元对 4.12 美元，每股收益 3.48 美元、一年前 2.48 美元：[帖](https://x.com/FirstSquawk/status/2115176145809547345)。The Transcript 写盘后跌 8%：[帖](https://x.com/TheTranscript_/status/2115176271873470542)。Visa 调整后每股收益 3.48 美元对 3.44 美元，净收入 121.0 亿美元、大致持平于 120.9 亿美元，跨境量按固定汇率增 14%，股息提高 16% 到每股 78 美分：[每股](https://x.com/FirstSquawk/status/2115174570579882137)、[股息](https://x.com/FirstSquawk/status/2115174586677645549)。The Transcript 写盘后跌 1%，并引首席执行官：全年净收入纪录 460 亿美元，增 15%，是除疫情后复苏和收购以外 15 年多来最强的增长；美国支出有韧性，支出较低的客户没有看到变弱：[里程碑](https://x.com/TheTranscript_/status/2115175207707304371)、[美国消费者](https://x.com/TheTranscript_/status/2115195215179055583)。Enphase 被 TrendSpider 写成双双不及预期，调整后每股收益 0.41 美元对 0.51 美元，销售额 2.39 亿对 3.04 亿，盘后一度延伸到跌 13%：[初值](https://x.com/TrendSpider/status/2115175126216192456)、[-13%](https://x.com/TrendSpider/status/2115182625023217760)。零对冲盘前写到跌 18%。Teradyne 双超后盘后跌 8.24%，调整后每股收益 2.29 美元对 2.04 美元，销售额 13.06 亿对 12.64 亿：[帖](https://x.com/TrendSpider/status/2115180334811857057)。Waste Management 运营收入 68.5 亿美元对 68.2 亿，调整后每股收益 2.15 美元、略低于 2.18 美元，全年调整后经营 EBITDA 仍看 81.5–82.5 亿美元，全年收入仍看 262.8–264.8 亿美元：[收入](https://x.com/FirstSquawk/status/2115180330227552318)、[指引](https://x.com/FirstSquawk/status/2115180360946631121)。

周三早上已经出来、而且数字完整的一组是电力和医疗器械。GE Vernova 收入 126.4 亿美元对 119.9 亿，调整后 EBITDA 19.4 亿对 16.8 亿，净利润 12.9 亿对 10.8 亿，每股收益 4.81 美元、一年前 1.64 美元，订单有机增长 96% 到 293 亿美元，全年收入看到 465–475 亿美元、之前是 455 亿到一个更高的区间：[帖](https://x.com/FirstSquawk/status/2115391061778636987)。TrendSpider 用的每股收益预期是 4.01 美元。Cramer 写他想钻进卖掉 GE Vernova 的人的脑子里，但不确定他们有没有脑子：[帖](https://x.com/jimcramer/status/2115390150851055683)。Vertiv 调整后每股收益 2.21 美元对 1.83 美元，销售额 43.13 亿对 37.60 亿，上调全年每股收益和销售指引：[帖](https://x.com/TrendSpider/status/2115410497323348091)。Amphenol 销售额 102 亿美元对 95 亿，有机销售增 37%、预期 30.3%，调整后每股收益 80 美分，四季度看到 81–83 美分，全年销售看到 369–371 亿美元、预期 356.8 亿，并宣布新的 3 年、40 亿美元回购：[帖](https://x.com/FirstSquawk/status/2115414002654384152)。波士顿科学销售额 51.4 亿美元对 50.5 亿，调整后每股收益 73 美分、持平于预期，全年调整后每股收益看到 3.16–3.18 美元、预期 3.23 美元：[帖](https://x.com/FirstSquawk/status/2115411155887984866)。TrendSpider 写它下调了四季度调整后每股收益和销售指引：[帖](https://x.com/TrendSpider/status/2115412035580444953)。百健调整后每股收益 2.62 美元对 2.06 美元，收入 28.0 亿对 26.4 亿：[帖](https://x.com/FirstSquawk/status/2115384403308511404)。Phillips 66 调整后每股收益 14.08 美元对 12.08 美元：[帖](https://x.com/FirstSquawk/status/2115397143968284976)。GE HealthCare 调整后每股收益 1.34 美元对 1.21 美元，收入 55 亿对 53.5 亿：[帖](https://x.com/FirstSquawk/status/2115390947429433455)。ADP 收入 55 亿对 54.7 亿，调整后每股收益 2.82 美元对 2.76 美元，并上调全年收入和调整后每股收益增长指引：[帖](https://x.com/FirstSquawk/status/2115399117270839651)。

今晚的名字已经排好。线外的 Bespoke：收盘后是 Alphabet、微软、Chipotle、Carvana、福特和联邦快递；开盘前还有百健、C.H. Robinson 和 Phillips 66：[帖](https://x.com/bespokeinvest/status/2115194451110814173)。The Transcript 的收盘后名单还包括 T-Mobile、ServiceNow、Fortinet、eBay 和 KLA：[帖](https://x.com/TheTranscript_/status/2115383133394944499)。Dan Ives 写，超大规模云厂商这周的财报需要成为企业支出、战略人工智能交易、云增长以及 2027 年资本开支的验证时刻；微软、Alphabet 和亚马逊应该是科技板块的牛市试纸：[帖](https://x.com/DivesTech/status/2115392942118404172)。彭博的标题是，微软和 Alphabet 的股票自上次财报以来走了不同的方向，这次财报把焦点放在人工智能对现金流的消耗上：[帖](https://x.com/business/status/2115403242230182171)。

融资的句子和财报叠在一起。零对冲写，博通支持的那笔 630 亿美元特殊目的载体里，第一留置权大约 435 亿美元，占 69%；这笔纪录规模的人工智能债务交易里，超过三分之二实际上由供应商担保：[帖](https://x.com/zerohedge/status/2115279214798925915)。同一账号把周一的人工智能筹资加成大约 2000 亿美元：博通这笔交易、Anthropic 交 S-1、Meta 启动 950 亿美元发行（上沿 975 亿美元），再加上 SpaceX 与 Apollo 敲定的 400 亿美元英伟达芯片租赁：[帖](https://x.com/zerohedge/status/2115279522438258743)。250 亿美元和 950 亿美元是两条帖，不合成一次发行。Anthropic 把给政府的 Claude 折扣扩大成 40%，并扩到州、地方、部落和领地政府：[帖](https://x.com/FirstSquawk/status/2115214006051115433)。线外的 Hedgeye 标题是 Anthropic 在大型 IPO 前有一个重大的中国问题，正文没有写出问题是什么：[帖](https://x.com/Hedgeye/status/2115171834622771292)。Steno 写 Anthropic 把看空叙事完全戳破了，没有数字：[帖](https://x.com/AndreasSteno/status/2115391454969266541)。Burry 写他对 Anthropic S-1 的看法在一条子栈链接里，帖文正文没有写出结论：[帖](https://x.com/michaeljburry/status/2115174435242058121)。

OpenAI 买谷歌芯片是另一笔没有金额的交易。DeItaone 转述 The Information：OpenAI 计划向谷歌购买人工智能芯片，金额和规模都没有披露，路透没有独立核实：[帖](https://x.com/DeItaone/status/2115236965318578581)。这和甲骨文用 Cerebras 芯片扩大合作是两件事。

Kobeissi 的结构数据和“人工智能还在涨”放在一起。10 月迄今，剔除人工智能股票的标普跑赢标普 6.4 个百分点，有望成为纪录上最好的相对月度表现；前一个月是跑输 5.1 个百分点，为纪录上第二差。过去三周的相对跑赢是 7.4 个百分点，为这个长度的最宽纪录。2026 年迄今，剔除人工智能的标普有 4 个月跑赢、标普有 6 个月跑赢。他们把这写成投资者在兑现人工智能交易里的大额利润：[帖](https://x.com/KobeissiLetter/status/2115165670136496363)。等权指数 10 月迄今跑赢标普 4.0 个百分点，有望成为 2009 年 4 月以来第二强的相对月；等权指数涨 4.3%，标普涨 0.3%；年初至今回报分别是 13.4% 和 12.1%。这是月内口径，发帖时周二收盘还没到：[帖](https://x.com/KobeissiLetter/status/2115135372095328336)。线外的 Bespoke 在当天下午写的是另一根 K 线：今天是人工智能上涨的一天，等权的 RSP 仍在跌：[帖](https://x.com/bespokeinvest/status/2115129649839960201)。苹果被 Kobeissi 单独拆开：苹果和纳斯达克 100 的 3 个月相关性降到 -0.12，为 1980 年代初以来的数据里第一次转负，并且已经连续两个月为负；这段时间苹果涨 9.7%，纳斯达克 100 只涨 0.2%；2006 年到 2025 年这段相关性从未低于 +0.30：[帖](https://x.com/KobeissiLetter/status/2115214294610591793)。

Unusual Whales 转述美国银行的调查：37% 的全球基金经理现在超配科技股，9 月是 30%，为 2020 年 8 月以来最高：[帖](https://x.com/unusual_whales/status/2115407731922206834)。fundstrat 只写了透过噪音往下看、底下的东西看起来不错：[帖](https://x.com/fundstrat/status/2115158162399711340)。Keith 的早评标题是人工智能（半导体）泡沫对 Quad 2 的美联储。他写反弹不是信号，是反射；机器生成它，零售追逐它，流动性蒸发，拥挤崩掉：[帖](https://x.com/KeithMcCullough/status/2115401859640754407)。他另写周二标普上涨那天 11 个板块里有 6 个下跌，反弹第二天的成交量在减速，三倍做多半导体的 SOXL 出现今年初夏以来最大的正收盘失衡之一，买单将近 55 亿美元：[广度](https://x.com/KeithMcCullough/status/2115368686131540363)、[成交量](https://x.com/KeithMcCullough/status/2115368304458035709)、[SOXL](https://x.com/KeithMcCullough/status/2115371234473214224)。

### 3. 周二油是结算下来的，周三早上又被写成供应风险

结算价先写。FinancialJuice：NYMEX WTI 原油期货结算 99.90 美元，跌 1.86 美元，跌 1.83%；布伦特结算 113.88 美元，跌 1.93 美元，跌 1.67%：[WTI](https://x.com/financialjuice/status/2115149506660515961)、[布伦特](https://x.com/financialjuice/status/2115153247422075048)。First Squawk 用了同一组结算。汽油 11 月期货结算每加仑 3.1376 美元，柴油结算 4.7752 美元：[汽油](https://x.com/financialjuice/status/2115149376134013037)、[柴油](https://x.com/financialjuice/status/2115149409767788912)。

周三亚洲时段的期货又涨了回去。First Squawk：布伦特期货涨 1.48 美元到 115.36 美元，美国原油期货涨 1.22 美元到 101.12 美元：[布伦特](https://x.com/FirstSquawk/status/2115250849358463121)、[WTI](https://x.com/FirstSquawk/status/2115251054531256517)。零对冲在接近的时点写布伦特涨 1.3%、站上 115 美元，眼睛在以色列选举：[帖](https://x.com/zerohedge/status/2115260392284819742)。再晚一点，First Squawk 写布伦特和美国原油期货都涨超 2 美元，因为供应风险重新点燃：[帖](https://x.com/FirstSquawk/status/2115340421622898827)。115.36 美元、站上 115 美元、涨超 2 美元，是三张不同时间的快照。

供应风险的原文是中期选举之后，不是今晚。Kobeissi 转述《华尔街日报》：美国已经告诉几个海湾阿拉伯国家，为中期选举后一场“短而激烈的军事行动”做准备；有越来越多的迹象显示美国和以色列在准备对伊朗的新一轮重型作战；美国在向以色列再送一套爱国者；地区里的美军在补充弹药，飞机在为打击做准备；特朗普这周说“我们也许再来一小场 Epic Fury”。油价在这条消息上上涨：[帖](https://x.com/KobeissiLetter/status/2115277626948354146)。DeItaone 写特朗普还没有做最后决定，外交谈判仍是替代方案：[帖](https://x.com/DeItaone/status/2115401710583624123)。同一窗口里还有相反的外交句子。Unusual Whales 转述《卫报》：海湾国家避免美伊再次开战的计划核心，是制裁解除后四天内重开霍尔木兹的多路和平协议，以及胡塞从也门境内实质撤军；美国知道谈话的进展，但仍在等一个让步，欧洲方面暗示可能是伊朗允许联合国武器核查人员回去：[帖](https://x.com/unusual_whales/status/2115382565842354688)。LiveSquawk 转述一位伊朗高级官员对路透说：卡塔尔没有提出结束敌对的新方案，卡塔尔提过的想法伊朗不能接受，德黑兰在核问题上不灵活的政策没有变：[帖](https://x.com/LiveSquawk/status/2115385275392344349)。零对冲的隔夜要闻把这三句放在一起：华尔街日报的战备、路透信源说卡塔尔周日给了一份新草案、伊朗官员说没有新方案：[帖](https://x.com/zerohedge/status/2115412585893732696)。

线外的 Javier Blas 把油市的未来写成市场眼里的二元：要么几天内达成协议，要么再开战、也许就在 11 月初。他补了第三条路：眼下的僵局变成新常态：[帖](https://x.com/JavierBlas/status/2115359681313218621)。Brooks 写布伦特在 115 美元定价的是波斯湾每天 600 万桶的流出，而实际流出是每天 2000 万桶；3 月和 4 月最差的时候也曾落到每天 800 万桶，所以 600 万桶比那场更差，油价高得太多：[帖](https://x.com/robin_j_brooks/status/2115378493487743420)。他另写美元这轮上涨始于 9 月 10 日沙特东西管道遇袭，所以这轮美元是油；油一跌，美元就会跌。欧元的下跌他也写成同一天开始，不是法国：[美元](https://x.com/robin_j_brooks/status/2115373040380825812)、[欧元](https://x.com/robin_j_brooks/status/2115411670252024176)。他又写伊朗在中期选举前不到一周的时间里要给特朗普造成最大伤害，油却在以战前的水平离开海湾：[帖](https://x.com/robin_j_brooks/status/2115381919298761021)。Keith 维持布伦特多头，并写布伦特一个月里为他们涨了 20%，欧洲天然气涨了大约两倍：[布伦特](https://x.com/KeithMcCullough/status/2115374782825042370)、[能源通胀](https://x.com/KeithMcCullough/status/2115375198216089903)。

实物和库存仍是另一列。美国石油学会原油库存降 203.1 万桶，预期是增加 80 万桶，前值是下降 493 万桶，库欣降 45.3 万桶：[帖](https://x.com/FirstSquawk/status/2115183836548210802)。《金融时报》经由 First Squawk：美国和俄罗斯在考虑战后于萨哈林近海做石油合资，白宫和克里姆林宫表示战争结束后、包括美国和俄罗斯石油公司的合资可能恢复；报道还说双方在讨论把美国大公司纳进恢复经德鲁日巴管道向欧洲输送俄罗斯石油的计划。美国领导人说这些项目在冲突结束前不会开始：[合资](https://x.com/FirstSquawk/status/2115168074974585166)、[管道](https://x.com/FirstSquawk/status/2115168084206215525)。特朗普称汽油和柴油价格很快会暴跌，并称油在从霍尔木兹流出、委内瑞拉可能成为美国的一个州：[油价](https://x.com/DeItaone/status/2115132377831768420)、[霍尔木兹](https://x.com/FirstSquawk/status/2115169759402860816)。沙特阿美在向欧洲提供本月和下月的现货原油，彭博的人说这是在补一条关键出口管道停摆后失去的供应：[帖](https://x.com/business/status/2115167946100158915)。Blas 写北海市场仍受高运费抬升的 Dated Brent 好处；哈萨克斯坦旗舰出口品种 CPC 今天被报在对布伦特近 10 美元的纪录折扣：[帖](https://x.com/JavierBlas/status/2115136082056520041)。高盛研究的 Daan Struyven 讨论中东石油流量已经反弹、价格却在近期上涨：[帖](https://x.com/GoldmanSachs/status/2115132258549903544)。

黄金在 4000 美元上下，方向仍分裂。Kitco 写消费者信心升到 91.7 之后，金价冲到盘中高点每盎司 4048 美元。会议委员会的 10 月消费者信心 91.7，预期 81，9 月上修后是 84.2：[帖](https://x.com/KitcoNewsNOW/status/2115114675583033767)。同一账号转述渣打的 Suki Cooper：金价需要在这里筑底，否则面对更深的回调；全球黄金 ETP 上周晚些时候重新流出：[帖](https://x.com/KitcoNewsNOW/status/2115165854996611179)。《华尔街日报》市场账号的标题是金价守在 4000 美元上方的涨幅、市场等美联储：[帖](https://x.com/WSJmarkets/status/2115238860883972135)。彭博写金价在决议前稳住在 4000 美元之上，逢低买盘进场：[帖](https://x.com/business/status/2115266082348941397)。路透的标题随后是油价更高、金价回落：[帖](https://x.com/Reuters/status/2115385627013267708)。彭博另转述摩根大通私人银行的 Tang：抛售后黄金仍有下行风险，流动性薄，利率还有上升空间：[帖](https://x.com/business/status/2115373039206506920)。Keith 写黄金和白银在会议前再次下跌，两者维持看空趋势：[帖](https://x.com/KeithMcCullough/status/2115375737561563635)。线外的 Gold Telegraph 写上海黄金交易所一个热门合约上周成交升到 4300 万手、大约 430 吨，为 4 月以来最高，并写中国家庭经银行积存计划在 2026 年前 9 个月买的黄金已经超过 2025 年全年：[成交](https://x.com/GoldTelegraph/status/2115146327118225681)、[家庭](https://x.com/GoldTelegraph/status/2115181591840555038)。线外的 Tavi Costa 写，如果把金矿股当成一个板块，它们会有市场上最干净的资产负债表、最强的利润率和最有吸引力的估值：[帖](https://x.com/TaviCosta/status/2115286795026124988)。

铜被彭博写成靠近两周最高收盘，交易员在等美联储：[帖](https://x.com/business/status/2115339059505557954)。伦敦金属交易所因技术问题推迟部分合约结算：[帖](https://x.com/LiveSquawk/status/2115384729704763544)。

### 4. 巴西的缺口还在被交易，选举人已经到了迈阿密

周一的跌幅没有被重写成一个新的收盘。Kobeissi 把 10 月 26 日 EWZ 跌 19.8% 写成 8.4 个标准差；过去 20 年日均变动 +0.04%，标准差 2.36%；正态分布下这种跌幅的概率大约是 58 千万亿分之一：[帖](https://x.com/KobeissiLetter/status/2115117452644221274)。线外的 Sentimentrader 用了同一个 19.8%：IBOV 12 周新低占比从 1.3% 跳到 67.1%，巴西 Optix 从 68.1 塌到 2.1：[帖](https://x.com/sentimentrader/status/2115136695498924428)。线外的 SpotGamma 写，选举之后 EWZ 跌了 20%，波动率却在被压扁：[帖](https://x.com/spotgamma/status/2115144986690019715)。

人的位置更新了。Kobeissi 写弗拉维奥·博索纳罗已经离开巴西、据报在前往美国：[帖](https://x.com/KobeissiLetter/status/2115148308792655895)。零对冲写他在逃离巴西后抵达迈阿密：[抵达](https://x.com/zerohedge/status/2115269867540492685)、[落地](https://x.com/zerohedge/status/2115414311996641690)。线外的 The Stalwart 先写他的名字可能出现在巴西飞美国的诱饵舱单上，人其实先进了阿根廷：[帖](https://x.com/TheStalwart/status/2115130581373624714)。阿根廷政府随后确认他周二入境又离境：[帖](https://x.com/TheStalwart/status/2115404507563626940)。同一账号写，如果在投票后的底部买巴西，已经可以赚到 16%，帖文没有写出工具和底部价位：[帖](https://x.com/TheStalwart/status/2115398668274507835)。Unusual Whales 转述《华盛顿邮报》：一位巴西最高法院大法官下令调查，对象是副总统万斯共同创立的一个捐赠网络与博索纳罗竞选之间被指控的联系：[帖](https://x.com/unusual_whales/status/2115285636672577944)。同一账号转述《经济学人》：如果巴西总统认为现在该加倍押注让他连任的政策，他会造成财政危机和深度衰退：[帖](https://x.com/unusual_whales/status/2115397413582012576)。

Andy Constan 把巴西的选举意外和美国中期选举放在一个问句里：这是不是在让市场打折“共和党不会丢掉众议院”。他写自己并不知道：[帖](https://x.com/dampedspring/status/2115120220138328454)。Robinhood 写距离选举日还有一周：[帖](https://x.com/RobinhoodApp/status/2115162533187248426)。

以色列选举是油价帖旁边的另一场未完成计票。Kobeissi 写内塔尼亚胡在一半选票点完后超过艾森科特，几天前他的胜选赔率还低到 20%：[帖](https://x.com/KobeissiLetter/status/2115384142720594263)。彭博写出口民调曾经让反对派领先，一半选票点完后两边都没有清楚的组阁路径：[帖](https://x.com/business/status/2115358464385909162)。The Stalwart 写反对派领袖理论上有足够席位把内塔尼亚胡换掉，问题是他需要阿拉伯政党的支持，而那些政党一进政府，非阿拉伯政党就不再支持他；谢克尔是表现最差的货币：[帖](https://x.com/TheStalwart/status/2115404183826583865)。

## 要盯住的五件事

1. **周三开盘时，周二的 26484.86 和 52399.09 还在不在。** 标普现货收盘点位这次没有帖。盘前先是 Gary 的标普涨 0.1%、纳斯达克 100 涨 0.3%，后是 The Stalwart 的纳斯达克期货涨 0.46%。线外的 Ryan Detrick 写 10 月 28 日历史上是标普一年里最好的一天，同一天又是美联储日，而美联储日最近很差：[帖](https://x.com/RyanDetrick/status/2115163492605120757)。线外的 Sentimentrader 写的季节性从今天收盘算起：1949 年以来，10 月最后两个交易日加 11 月前三个交易日，标普平均涨 1.23%，全部五日区间平均是 0.18%，77 年里涨了 56 年。今年这段从 10 月 28 日收盘算到 11 月 4 日收盘：[帖](https://x.com/sentimentrader/status/2115258661832712449)。
2. **下午 2 点的措辞，而不是这次会议加不加息。** 彭博、福克斯、CNBC 和零对冲的基准都是按住。福克斯写下的概率是 90.6%，CPI 是 3.7%。路透的播客把“后面仍可能加息”留在信号里。Brooks 周二晚上写法国已经把曲线压平、沃什不必偏鹰。Keith 周三早上仍把美元看成偏鹰。Kitco 转述的 Natixis 把异议和 12 月的线索放在发布会上。SpotGamma 写期权没有把这一周定成安静。
3. **超预期之后是续涨还是继续被卖。** 海力士、韩国指数、美光、Vertiv、GE Vernova 和 Amphenol 在涨的那一侧。Robinhood、希捷、恩智浦、Enphase 和 Teradyne 在超预期或纪录利润之后下跌的那一侧。Enphase 在 The Transcript 那里盘后跌 10%，TrendSpider 写盘后延伸到跌 13%，零对冲盘前写跌 18%。今晚是 Alphabet 和微软，明天是亚马逊。Dan Ives 把这三家写成验证时刻。
4. **113.88 美元和 115 美元以上不要写成同一个油价。** WTI 周二结算 99.90 美元，布伦特结算 113.88 美元。周三有布伦特期货 115.36 美元、美国原油 101.12 美元，以及后来涨超 2 美元的一条。战备写的是中期选举之后。卡塔尔草案和“没有新方案”同时在帖里。Brooks 认为 115 美元定价的流出远低于实际每天 2000 万桶。Keith 维持布伦特多头。
5. **巴西用缺口还是用 16% 的反弹交易。** EWZ 周一跌 19.8% 仍是 Kobeissi 的标准差句子。博索纳罗一侧已经写到迈阿密，中间经过阿根廷。The Stalwart 写从底部买已经能赚 16%，没有写出价格。波动率在 SpotGamma 那里是被压扁的。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 周二收盘 | 纳斯达克、道指、纳斯达克 100、半导体指数 | 纳斯达克收 26484.86，涨 1.21%。道指收 52399.09，涨 0.07%。另一条综述写纳斯达克 100 涨 1.3%、半导体指数涨 3.6%。标普点位没有出现在已读收盘帖里。Investing.com：美股收高，VIX 下跌 | [纳斯达克](https://x.com/FirstSquawk/status/2115175570632053046)、[道指](https://x.com/FirstSquawk/status/2115175594132640132)、[纳指 100 与半导体](https://x.com/FirstSquawk/status/2115187615028916646)、[方向](https://x.com/Investingcom/status/2115175284320215251) |
| 周三盘前 | 标普、纳斯达克 100、纳斯达克期货、七巨头 | Gary：盘前标普 +0.1%，盘前纳斯达克 100 +0.3%，10 年期 5.01%。The Stalwart：纳斯达克期货 +0.46%。零对冲：Alphabet 领涨七巨头，英伟达 +0.8%，苹果 -0.4%，微软 -0.3% | [Gary](https://x.com/garyblack00/status/2115389356307341625)、[期货](https://x.com/TheStalwart/status/2115398342985265289)、[盘前](https://x.com/zerohedge/status/2115415265957560615) |
| 还在涨的内存 | SK 海力士、美光、三星、希捷、西部数据、SNDK、韩国指数 | 营业利润 83.3 万亿韩元对 76.7 万亿，收入 104.6 万亿对 98.3 万亿，净利润低于预期。2026 年股东回报约 100 万亿韩元。KOSPI 收盘 +6.63%。Cramer 点美光。TrendSpider 点名周三早上走高的存储股 | [利润](https://x.com/FirstSquawk/status/2115224735219102114)、[回报](https://x.com/FirstSquawk/status/2115224851522986339)、[KOSPI](https://x.com/FirstSquawk/status/2115331589593079928)、[美光](https://x.com/jimcramer/status/2115364643552293194)、[存储](https://x.com/TrendSpider/status/2115413685598601361) |
| 超预期后被卖 | HOOD、STX、NXPI、ENPH、TER、V | Robinhood 的收入在 First Squawk 和 Gary 那里不及预期，调整后每股收益 0.60 美元高于 0.56 美元；The Transcript 写盘后跌 4%，Gary 写盘后跌 5%。希捷在 TrendSpider 那里双超后跌 7.38%，The Transcript 写盘后跌 8%，花旗被写成说不及预期。恩智浦双超后，The Transcript 写盘后跌 8%，TrendSpider 写跌 7.46%。Enphase 双双不及预期，零对冲盘前写到跌 18%。Teradyne 双超后 TrendSpider 写盘后跌 8.24%。Visa 调整后每股收益 3.48 美元对 3.44 美元，股息提到 78 美分；The Transcript 写盘后跌 1% | [HOOD 收入](https://x.com/FirstSquawk/status/2115174211186741539)、[Gary](https://x.com/garyblack00/status/2115179102420271306)、[希捷](https://x.com/TrendSpider/status/2115173947427967421)、[花旗口径](https://x.com/eWhispers/status/2115388230552207448)、[Enphase](https://x.com/TrendSpider/status/2115175126216192456)、[Visa](https://x.com/FirstSquawk/status/2115174570579882137) |
| 周三早上已有数字 | GEV、VRT、APH、BSX、BIIB、PSX、GEHC、ADP、STLA | GE Vernova 收入和利润超预期，订单有机增 96%。Vertiv 调整后每股收益 2.21 美元对 1.83 美元并上调全年。Amphenol 有机销售 +37%，40 亿美元回购。波士顿科学季度持平、全年调整后每股收益指引 3.16–3.18 美元低于预期，盘前跌 6%。Stellantis 调整后经营利润 2.56 亿欧元对 2.105 亿欧元，工业自由现金流 -40.1 亿欧元 | [GEV](https://x.com/FirstSquawk/status/2115391061778636987)、[VRT](https://x.com/TrendSpider/status/2115410497323348091)、[APH](https://x.com/FirstSquawk/status/2115414002654384152)、[BSX](https://x.com/FirstSquawk/status/2115411155887984866)、[STLA](https://x.com/FirstSquawk/status/2115339196869337222) |
| 今晚和明天 | GOOGL、MSFT、AMZN、META、NVDA、ORCL、TSLA、SPCX | 今晚 Alphabet、微软，明天亚马逊。OpenAI 计划买谷歌芯片，金额未披露。甲骨文用 Cerebras 扩大与 OpenAI 的合作。Meta 250 亿美元发售获 5 倍超额认购；零对冲另写 950 亿美元发行。Gary 对特斯拉谨慎，同时写它和 SpaceX 在合并猜测里盘前更高。Bespoke：特斯拉高于 50 日均线 11.3%，Meta 和 Alphabet 低于 50 日均线最多 | [日程](https://x.com/bespokeinvest/status/2115194451110814173)、[谷歌芯片](https://x.com/DeItaone/status/2115236965318578581)、[250 亿](https://x.com/FirstSquawk/status/2115187615028916646)、[950 亿](https://x.com/zerohedge/status/2115279522438258743)、[均线](https://x.com/bespokeinvest/status/2115414091153965547) |
| 信用里被点名的载体 | AVGO、META、SPCX | 630 亿美元载体里第一留置权约 435 亿美元。零对冲把周一的人工智能筹资加成大约 2000 亿美元。Keith 周二又做空一只人工智能泡沫信用 ETF，并说黑石下跌是一个信号 | [留置权](https://x.com/zerohedge/status/2115279214798925915)、[2000 亿](https://x.com/zerohedge/status/2115279522438258743)、[BX](https://x.com/KeithMcCullough/status/2115161173641592853) |
| 巴西 | EWZ、巴西股市 | 周一 EWZ 跌 19.8%，8.4 个标准差。波动率在下跌后被压扁。The Stalwart：从投票后的底部买已经能赚 16%，没有价格 | [19.8%](https://x.com/KobeissiLetter/status/2115117452644221274)、[波动率](https://x.com/spotgamma/status/2115144986690019715)、[16%](https://x.com/TheStalwart/status/2115398668274507835) |
| 油和黄金的价格 | WTI、布伦特、黄金 | WTI 结算 99.90 美元。布伦特结算 113.88 美元。周三期货曾到布伦特 115.36 美元、WTI 101.12 美元，后有涨超 2 美元的一条。黄金盘中高点 4048 美元，后来的标题是守在 4000 美元上方、再后来是随油价回落。Keith 维持黄金看空、布伦特看多 | [结算](https://x.com/financialjuice/status/2115149506660515961)、[115.36](https://x.com/FirstSquawk/status/2115250849358463121)、[4048](https://x.com/KitcoNewsNOW/status/2115114675583033767)、[回落](https://x.com/Reuters/status/2115385627013267708) |
| 已经点名的图表和空头 | AAPL、INTC、GM、IDX、XLV、BUG | 苹果与纳斯达克 100 的 3 个月相关性 -0.12。英特尔仍低于首席执行官买入超过 10 万股、约 1000 万美元时的价位；周二盘中曾涨 4.9% 到时段高点。Keith 把通用汽车放在做空一侧，做空印尼，做多医疗和软件 | [苹果](https://x.com/KobeissiLetter/status/2115214294610591793)、[英特尔](https://x.com/TrendSpider/status/2115113258495705439)、[通用](https://x.com/KeithMcCullough/status/2115161929832710321)、[软件](https://x.com/KeithMcCullough/status/2115153114487746721) |
| 一笔现金收购 | WEN | 零对冲：Trian 提出以每股 7.35 美元现金收购 Wendy's，并问“又来？” | [帖](https://x.com/zerohedge/status/2115414226638618925) |

Earnings Whispers 的周二收盘后名单还包括 SK 海力士、希捷、Visa、Enphase、恩智浦、Teradyne、Waste Management、Baker Hughes；周三开盘前还包括 Amphenol、Vertiv、GE Vernova、波士顿科学、Phillips 66、ADP、百健：[周二](https://x.com/eWhispers/status/2115121062421647405)、[周三](https://x.com/eWhispers/status/2115146014143492118)。

## 后续走势：三套可以证伪的剧本

帖文没有给周三的收盘点位。周二写下来的现货收盘是纳斯达克 26484.86、道指 52399.09。下面三套的顺序，以开盘前油价仍在 115 美元一带、期货仍小幅为正为前提。

**内存和电力设备把风险偏好接过去，决议按住，巴西留在反弹里。** 触发器是纳斯达克守住 26484 一带，半导体维持 First Squawk 写下的那种跳升，EWZ 不再扩大周一大约 20% 的缺口，布伦特不把“涨超 2 美元”续写成趋势。这条路径上，市场交易的是海力士 80% 的营业利润率、2027 年已经谈完的 HBM、Vertiv 和 GE Vernova 的订单，以及等权指数 10 月迄今仍跑赢的那组月内数字。Dan Ives 的验证时刻和 fundstrat 的“底下看起来不错”站在这一侧。若 Alphabet 或微软今晚把微软的现金流消耗交易成稀释而不是云增长，或者 Enphase 那种盘前 -18% 扩散到已经双超的恩智浦和希捷以外的半导体，这条路径失败。

**超预期被当成卖出，信用先于指数。** 触发器已经写在周二盘后：Robinhood、希捷、恩智浦、Enphase、Teradyne 在成绩单出来后下跌，收盘失衡是卖盘，Keith 把反弹写成机器的反射，并把一只人工智能信用 ETF 放在做空一侧。博通那笔 630 亿美元里大约 69% 是供应商担保的第一留置权。零对冲的标题是加息难以想象，所以问题变成如何解释跳过偏热的 CPI。这条路径失败的条件，是海力士的 100 万亿韩元回报和 Amphenol 的 40 亿美元回购被当成融资已经找到买家，而 Meta 的超额认购把 950 亿美元里还没定价的部分一起接住。

**油价口号盖过结算价，按住被说成还不够。** 触发器是布伦特从 113.88 美元的结算重新站上并守住 115 美元，同时沃什的措辞比 Brooks 周二晚上写的“不必偏鹰”更接近路透那句“后面仍可能加息”，或者 Keith 的美元多头被盘中交易承认。战备写的是中期选举之后，不是周三下午。它失败的条件，是卡塔尔那份“制裁解除后四天重开霍尔木兹”被后续帖文写成有文本，而且伊朗官员那句“没有新方案”被替换掉，油价回到结算价。黄金在这条路径上不会自动上涨：摩根大通私人银行把进一步下跌的条件写成流动性薄和利率还有上升空间，Keith 在金价仍被写成 4000 美元附近时维持看空。

Peter Brandt 发了一张电子迷你标普年底涨势的图表问句，帖文正文没有写出价位：[帖](https://x.com/PeterLBrandt/status/2115183311618441602)。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照美东 9:30 的开盘。它不决定仓位大小。

**开盘前只核对五样东西。** 盘前还在不在 Gary 写下的标普涨 0.1%、纳斯达克 100 涨 0.3%，还是 The Stalwart 那条纳斯达克期货涨 0.46%；布伦特是停在 113.88 美元的结算附近，还是守住 115 美元以上；Robinhood 盘后跌 4% 到 Gary 写下的跌 5%，以及 Enphase 盘前跌 18% 的缺口，是收敛，还是把“成绩单出来就被卖”带进周三；存储股里的美光、希捷、西部数据是跟着海力士和韩国指数，还是跟着希捷自己盘后的下跌；高收益利差有没有离开 Detrick 写下的“只回到 3 月底”和 Keith 写下的“3 个基点、趋势没变”。五样里油价重新上涨、信用变宽、超预期的股票继续被卖，这些帖给出的默认顺序是融资敏感的人工智能信用和已经在跌的个股，低于已经涨了 3.6% 的半导体指数和仍被写成有订单的 GE Vernova、Vertiv。油价停在结算价、缺口收敛、S-1 和超额认购被当成风险偏好，默认顺序掉过头来：半导体和存储高于去追 EWZ 的缺口。

**已经公开的方向，按账号而不是按共识。**

- Gary Black：盘前标普涨 0.1%，盘前纳斯达克 100 涨 0.3%，布伦特站上 115 美元，10 年期 5.01%，标普 2026 年每股收益 369 美元、20.9 倍。他等待偏鹰的按兵不动。个股句子是海力士带动美光、Robinhood 因三季度偏弱下跌、特斯拉在合并猜测里上涨但他对特斯拉谨慎。
- Keith McCullough，线外：布伦特维持多头，一个月涨 20% 是他的口径。黄金和白银维持看空。美元维持多头，并写成偏鹰的美联储。软件 BUG 在创新高，医疗维持多头。做空印尼、做空一只人工智能信用 ETF，通用汽车放在做空一侧，黑石下跌被他当成信号。反弹是反射，不是信号。标普上涨那天 11 个板块有 6 个下跌。
- Robin Brooks，线外：周二晚上，法国把美国曲线压平，沃什不必偏鹰。周三早上，美元和欧元的这轮方向是 9 月 10 日以来的油，不是法国。布伦特 115 美元定价的海湾流出是每天 600 万桶，实际是 2000 万桶，所以油价高得太多。
- El-Erian：对美国友好的买家在减少美债购买，买方更战术、更短期。他没有写这次会议加息或降息。
- Nick Timiraos：窗口内没有新帖。他的可见时间线停在周二早上那条关于沃什少说的帖之前的时点，那条不在这个窗口里。
- Kobeissi：EWZ 周一跌 19.8% 是 8.4 个标准差。剔除人工智能的标普 10 月迄今跑赢 6.4 个百分点。苹果和纳斯达克 100 的相关性第一次转负。10 年期和纳斯达克 100 的 20 日相关性转到 +0.51。战备帖把油价上涨和中期选举后的军事行动放在一起。他们没有给周三的标普目标。
- Jim Cramer：企业库藏不要做 ATM。波音今天被倒进了厨房水槽，人们没看见。海力士兑现，美光应是今天最大的赢家。他不理解 GE Vernova 的卖方。
- Eric Balchunas：写了 BTAL，把它当成人工智能泡沫破裂或广度回归时的 ETF 对冲，做空高贝塔、做多低贝塔。日本的 ETF 讨论不是美股点位。
- Barchart：韩国股票在涨。美国友好国家今年把美债购买砍了 60%。原油此前因伊朗最高领袖重申协议条款而回落，那是结算之前的标题。
- TrendSpider：希捷、Robinhood、Visa、恩智浦、Enphase、Teradyne 的盘后反应按上面的数字。Vertiv 和 GE Vernova 周三早上是另一侧。英特尔仍低于首席执行官买入价。SOXL 在离开超卖、MACD 金叉在眼前，这是图表句子。
- 线外的 Hedgeye：医疗 ETF 维持多头。Anthropic 的中国问题只有标题。国际机票价格升到 1000 美元以上、五个月高位。
- 线外的 Ryan Detrick：10 月 28 日历史上最好，又是美联储日。资本开支图仍热。高收益利差还没有把 CCC 的走阔传开。
- 线外的 Bespoke：周二下午人工智能涨、等权仍跌。今晚 Alphabet 和微软。特斯拉高于 50 日均线 11.3%，Meta 和 Alphabet 低于 50 日均线最多。熊市名单里写了中国、韩国、印尼和沙特，这张表发在韩国指数涨 6.63% 的收盘之前。
- 线外的 SpotGamma：暂停已经被定价，这一周的期权没有定成安静。EWZ 跌 20% 之后波动率被压扁。没有新的目标价。
- 线外的 Javier Blas：油市的第三条路是僵局变成常态。CPC 对布伦特近 10 美元的纪录折扣是实物，不是目标价。
- 线外的 The Stalwart：纳斯达克期货涨 0.46%。巴西从底部买已经能赚 16%。博索纳罗的行程经阿根廷确认。以色列组阁卡在阿拉伯政党。
- Dan Ives：微软、Alphabet、亚马逊是这周的验证。没有目标价。
- Charlie Bilello：窗口内是一条图表视频和一句“死亡、税收和印钞”。没有新的六行数字。
- Chamath：只有“好文”和一个链接，正文没有观点。
- Bill Ackman、Cathie Wood、Dalio、Cuban、Pompliano：没有可引用的指数或个股方向。Dalio 是一条原则。Pompliano 是早安。Ackman 的链接不是美股。ARK 官方账号窗口内没有原创。
- Burry：Anthropic 的看法在链接里，帖文没有写出结论。
- Peter Schiff：窗口内的长帖是他的银行托管，不是美股点位。另一条是印钞从解药变成疾病的标题。
- Yardeni，线外：工业股从今年第二落到第六，这个板块的远期盈利刚创纪录。正文没有目标价。

**财报的顺序。** 先看已经写进价格的发行和文件：Meta 的 250 亿美元超额认购和零对冲的 950 亿美元、博通 630 亿美元里的 435 亿美元第一留置权、OpenAI 买谷歌芯片但没有金额。再看今天已经出来的海力士、GE Vernova、Vertiv、Amphenol、波士顿科学、Robinhood 和 Enphase 的缺口。然后才是 Bespoke 和 The Transcript 点名的周三收盘后：Alphabet、微软、Carvana、福特、联邦快递、ServiceNow、KLA。亚马逊仍是 Gary 和 Dan Ives 写在明天的名字。

**明确留在观察、不放进计划的东西。** 标普现货收盘点位这次没有帖，不用其他指数倒推。Nick Timiraos、Gundlach、Damodaran、Cathie Wood、Cuban、Hindenburg、Nouriel 和多家银行官方账号这次没有可引用的新判断。Gundlach 的可见时间线停在 10 月 19 日。德意志银行的时间线没有读到。彭博主号、BBC Business、CNN Business 的时间线陈旧。SpotGamma 没有粉丝数，偏度帖只有 EWZ。Kobeissi 另有一条写特朗普说要禁用“Artificial Intelligence”和“AI”这两个词，帖文没有给出场合，这里不把它写成已经落地的政策：[帖](https://x.com/KobeissiLetter/status/2115120589320900964)。

## 帖文索引

周二收盘与盘前：[纳斯达克 26484.86](https://x.com/FirstSquawk/status/2115175570632053046)、[道指 52399.09](https://x.com/FirstSquawk/status/2115175594132640132)、[纳指 100 与半导体](https://x.com/FirstSquawk/status/2115187615028916646)、[收盘方向](https://x.com/Investingcom/status/2115175284320215251)、[收盘失衡](https://x.com/financialjuice/status/2115169388991242595)、[Gary 的盘前](https://x.com/garyblack00/status/2115389356307341625)、[纳指期货 +0.46%](https://x.com/TheStalwart/status/2115398342985265289)。

美联储与利率：[按住并对 12 月点头](https://x.com/business/status/2115295021930856683)、[90.6%](https://x.com/FoxBusiness/status/2115146012000203261)、[仍可能加息](https://x.com/Reuters/status/2115394417758540250)、[不必偏鹰](https://x.com/robin_j_brooks/status/2115179994825822222)、[美元与偏鹰](https://x.com/KeithMcCullough/status/2115377512117346632)、[期权没有定成安静](https://x.com/spotgamma/status/2115126483450478791)、[美债买家](https://x.com/elerianm/status/2115394735862898829)、[5 年期拍卖](https://x.com/financialjuice/status/2115127238555312507)。

财报与人工智能：[海力士](https://x.com/FirstSquawk/status/2115224735219102114)、[KOSPI](https://x.com/FirstSquawk/status/2115331589593079928)、[Robinhood](https://x.com/garyblack00/status/2115179102420271306)、[Vertiv](https://x.com/TrendSpider/status/2115410497323348091)、[Amphenol](https://x.com/FirstSquawk/status/2115414002654384152)、[博通留置权](https://x.com/zerohedge/status/2115279214798925915)、[谷歌芯片](https://x.com/DeItaone/status/2115236965318578581)、[剔除人工智能](https://x.com/KobeissiLetter/status/2115165670136496363)、[Dan Ives](https://x.com/DivesTech/status/2115392942118404172)。

油、黄金与巴西：[WTI 结算](https://x.com/financialjuice/status/2115149506660515961)、[布伦特 115.36](https://x.com/FirstSquawk/status/2115250849358463121)、[选举后战备](https://x.com/KobeissiLetter/status/2115277626948354146)、[没有新方案](https://x.com/LiveSquawk/status/2115385275392344349)、[115 美元定价 600 万桶](https://x.com/robin_j_brooks/status/2115378493487743420)、[第三条路](https://x.com/JavierBlas/status/2115359681313218621)、[EWZ 19.8%](https://x.com/KobeissiLetter/status/2115117452644221274)、[迈阿密](https://x.com/zerohedge/status/2115414311996641690)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-10-28 抓取时的公开读数。原创条数是北京时间当天窗口内、按帖文链接去重后的原创帖，回复不计入。路透 242 条和 First Squawk 272 条是补抓后读穿窗口的计数。德意志银行、Mark Minervini 和 TradingView 的 0 是读取失败。彭博主号、BBC Business、CNN Business 的 0 来自对不上近期发帖的时间线。Nick Timiraos 的 0 是窗口内没有新帖，可见时间线最新一条在周二 10:41 UTC。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,438,094 | 242 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,321,553 | 74 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,280,068 | 39 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,323,068 | 26 |
| 5 | [@business](https://x.com/business) | 10,486,760 | 255 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,562,218 | 0 |
| 7 | [@FT](https://x.com/FT) | 7,104,434 | 63 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,259,831 | 74 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,422,771 | 12 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,646,269 | 28 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,573,909 | 0 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,424,769 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,362,646 | 35 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,434,476 | 34 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,421,780 | 26 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,039,711 | 2 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,000,825 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,701,068 | 12 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,559,193 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,509,213 | 7 |
| 21 | [@chamath](https://x.com/chamath) | 2,480,105 | 1 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,439,687 | 1 |
| 23 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,670 | 27 |
| 24 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,158,206 | 0 |
| 25 | [@michaeljburry](https://x.com/michaeljburry) | 2,133,208 | 1 |
| 26 | [@YahooFinance](https://x.com/YahooFinance) | 2,074,398 | 15 |
| 27 | [@markets](https://x.com/markets) | 2,046,192 | 0 |
| 28 | [@DeItaone](https://x.com/DeItaone) | 1,968,367 | 26 |
| 29 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,772,576 | 3 |
| 30 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,280 | 35 |
| 31 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,735,740 | 1 |
| 32 | [@NYSE](https://x.com/NYSE) | 1,699,264 | 5 |
| 33 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,693,299 | 0 |
| 34 | [@theinformation](https://x.com/theinformation) | 1,609,348 | 16 |
| 35 | [@federalreserve](https://x.com/federalreserve) | 1,600,131 | 0 |
| 36 | [@Investingcom](https://x.com/Investingcom) | 1,532,953 | 32 |
| 37 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,508,984 | 2 |
| 38 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,469,917 | 14 |
| 39 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,794 | 4 |
| 40 | [@Bloomberg](https://x.com/Bloomberg) | 1,352,054 | 0 |
| 41 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,351,727 | 1 |
| 42 | [@TheStreet](https://x.com/TheStreet) | 1,228,905 | 53 |
| 43 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,195,135 | 3 |
| 44 | [@Stocktwits](https://x.com/Stocktwits) | 1,193,067 | 3 |
| 45 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,184,805 | 0 |
| 46 | [@nntaleb](https://x.com/nntaleb) | 1,164,931 | 1 |
| 47 | [@USTreasury](https://x.com/USTreasury) | 1,163,642 | 0 |
| 48 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,160,675 | 30 |
| 49 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,156,439 | 1 |
| 50 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,152,372 | 5 |
| 51 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,143,105 | 1 |
| 52 | [@elerianm](https://x.com/elerianm) | 1,117,996 | 1 |
| 53 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,112,654 | 21 |
| 54 | [@BlackRock](https://x.com/BlackRock) | 1,081,218 | 1 |
| 55 | [@Downtown](https://x.com/Downtown) | 1,043,625 | 0 |
| 56 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,308 | 29 |
| 57 | [@financialjuice](https://x.com/financialjuice) | 955,291 | 232 |
| 58 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,604 | 0 |
| 59 | [@tradingview](https://x.com/tradingview) | 906,586 | 0 |
| 60 | [@BloombergTV](https://x.com/BloombergTV) | 893,292 | 16 |
| 61 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 889,896 | 0 |
| 62 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,725 | 12 |
| 63 | [@charliebilello](https://x.com/charliebilello) | 874,193 | 2 |
| 64 | [@axios](https://x.com/axios) | 861,504 | 30 |
| 65 | [@jpmorgan](https://x.com/jpmorgan) | 859,640 | 0 |
| 66 | [@Citi](https://x.com/Citi) | 853,420 | 1 |
| 67 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 850,981 | 15 |
| 68 | [@HindenburgRes](https://x.com/HindenburgRes) | 848,528 | 0 |
| 69 | [@themotleyfool](https://x.com/themotleyfool) | 840,863 | 1 |
| 70 | [@ecb](https://x.com/ecb) | 828,686 | 0 |
| 71 | [@ARKInvest](https://x.com/ARKInvest) | 822,470 | 0 |
| 72 | [@SECGov](https://x.com/SECGov) | 810,453 | 1 |
| 73 | [@leadlagreport](https://x.com/leadlagreport) | 770,249 | 10 |
| 74 | [@markminervini](https://x.com/markminervini) | 767,231 | 0 |
| 75 | [@MorganStanley](https://x.com/MorganStanley) | 757,939 | 1 |
| 76 | [@CNBCnow](https://x.com/CNBCnow) | 752,242 | 0 |
| 77 | [@morganhousel](https://x.com/morganhousel) | 727,933 | 0 |
| 78 | [@TrendSpider](https://x.com/TrendSpider) | 719,291 | 26 |
| 79 | [@CMEGroup](https://x.com/CMEGroup) | 712,039 | 0 |
| 80 | [@Nouriel](https://x.com/Nouriel) | 703,851 | 0 |
| 81 | [@fundstrat](https://x.com/fundstrat) | 674,312 | 1 |
| 82 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 673,694 | 11 |
| 83 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 647,011 | 0 |
| 84 | [@LukeGromen](https://x.com/LukeGromen) | 638,877 | 0 |
| 85 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,831 | 0 |
| 86 | [@EricBalchunas](https://x.com/EricBalchunas) | 629,504 | 3 |
| 87 | [@garyblack00](https://x.com/garyblack00) | 584,452 | 2 |
| 88 | [@dampedspring](https://x.com/dampedspring) | 579,084 | 6 |
| 89 | [@Cboe](https://x.com/Cboe) | 578,813 | 2 |
| 90 | [@Barchart](https://x.com/Barchart) | 577,950 | 6 |
| 91 | [@FirstSquawk](https://x.com/FirstSquawk) | 575,049 | 272 |
| 92 | [@eWhispers](https://x.com/eWhispers) | 572,256 | 5 |
| 93 | [@MadMoneyOnCNBC](https://x.com/MadMoneyOnCNBC) | 543,444 | 0 |
| 94 | [@AswathDamodaran](https://x.com/AswathDamodaran) | 521,128 | 0 |
| 95 | [@BofA_News](https://x.com/BofA_News) | 518,236 | 0 |
| 96 | [@carlquintanilla](https://x.com/carlquintanilla) | 517,764 | 1 |
| 97 | [@LiveSquawk](https://x.com/LiveSquawk) | 506,244 | 27 |
| 98 | [@UBS](https://x.com/UBS) | 499,460 | 0 |
| 99 | [@NickTimiraos](https://x.com/NickTimiraos) | 494,098 | 0 |
| 100 | [@NikkeiAsia](https://x.com/NikkeiAsia) | 489,469 | 53 |
