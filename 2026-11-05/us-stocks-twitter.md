# 美股 Twitter 观点日报 · 2026-11-05

周三现货已经走完，周四现货还没开。抓取结束时美东大约 5:22。指数收盘是大涨，芯片和数据中心是另一张图。油价沿途经过盘前的 103、盘中的 93.25 和“接近 90”，结算写成 88.12 和 94.62，夜里又到 87.07 和 93.61。黄金从 ADP 之后的 4,035.85 写到收盘综述的 4,063，周四凌晨到过 4,134.67，后来的句子是从两周高点回落、仍守在 4,100 上方。

下面每一条归纳都附有帖文链接。开盘、盘中、收盘、盘后和期货，按发帖原文分开。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-11-05**。触发时刻约 10:01 UTC，时间线补抓到 **约 10:22 UTC（北京时间 18:22，美东 5:22）**。美国夏令时已经结束。美股现货 9:30 才开。非农还在周五。周四开盘前的那一批财报，抓取结束时还没有结果帖。
- 观察窗口从 **2026-11-04 10:12 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周三白天的现货全天、收盘、高通和 Arm 的盘后，以及美东周四凌晨到大约 5:22。上一份日报里的周二收盘不在这里重算。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。抓取开始时美国趋势是 Kyrie、Mississippi、Thune、Jeffries、DeSantis、The GOP。抓取结束时还是这六条，顺序换成 Kyrie、Thune、Mississippi、Jeffries、DeSantis、The GOP。里面没有美股代码。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。
- 不存在官方的“美股 Top 100”。这次试了 **961** 个候选，成功读到粉丝数的有 **822** 个。排序时拿掉加密货币账号、综合新闻主号、科技风投和创始人、大型科技公司首席执行官、竞选和政治账号、公司产品品牌、大学和智库，以及简介对不上的错人号。`@DanielNewman` 这次的简介是漫威和《行尸走肉》演员，不是市场分析师，按错人号拿掉，Eric Balchunas 因此进入前 100。`@SEC` 是东南联盟体育号，`@goldman` 是另一位同姓用户，都没有拿来代替美国证交会和高盛。用来排序的账号是 **669** 个，截止在 Eric Balchunas（627,108）。Morning Brew（593,131）落到第 101。Bloomberg Opinion（585,714）第 102。First Squawk、Gary Black、Cboe、Barchart、dampedspring、Gundlach、Earnings Whispers、LiveSquawk、瑞银、Nick Timiraos、日经亚洲、Keith McCullough、Fxhedgers、MacroAlf、Traderstewie、The Stalwart、Hedgeye、Javier Blas、Robin Brooks、Bespoke、SpotGamma、The Transcript、firstadopter、Ryan Detrick、Yardeni、RenMac、RedDog、Benzinga、Newsquawk、OpenOutcrier 落在线外，引用时会写明。排序不代表预测准确度。
- 100 个账号里，**74 个**在窗口内有按帖文链接去重后、且接口没有标成回复的原创帖。路透读穿窗口，290 条。彭博商业账号补抓后读穿窗口，326 条。《金融时报》49 条。《华尔街日报》补抓后读穿窗口，38 条。《经济学人》90 条。零对冲 48 条。FinancialJuice 读穿窗口，217 条。CNBC 86 条。《The Street》72 条。DeItaone 50 条。StockMKTNewz 47 条。Axios 补抓后读穿窗口，45 条。路透商业账号补抓后 14 条。线外的 First Squawk 补抓后读穿窗口，原创 269 条。LiveSquawk 读穿窗口，原创 83 条。德意志银行的时间线返回错误，表里的 0 不是确认沉默。保罗·克鲁格曼、Cathie Wood、BBC Business、彭博 markets、沃伦·巴菲特、CNN Business、彭博主号、Andrew Ross Sorkin、高盛、Lyn Alden、贝莱德、Downtown、美国银行、TradingView、纽约时报商业、摩根大通、花旗、Hindenburg、美国证交会、Bloomberg Economics、Jim Bianco、CNBC Now、Morgan Housel、Nouriel Roubini、Carl Icahn 的 0，是可见时间线早于窗口。

## 周三收盘是指数大涨，半导体和数据中心没有一起涨

开盘有两张点位，不要并成一句。First Squawk 14:31 UTC：标普 500 涨 86.51 点，或 1.14%，到 7,655.43；道指涨 997.76 点，或 1.93%，到 52,784.48；纳斯达克涨 271.36 点，或 1.07%，到 25,643.36：[开盘三条写在同一帖](https://x.com/FirstSquawk/status/2117988101599764889)。线外的 SpotGamma 把开盘写成 7,636，并写波动率压缩在美东下午 2:30 把指数抬到 7,700，当时涨 1.75%；他的风险枢轴在 7,600，上方目标是 7,700。同一帖把前一天收盘写成 7,569：[帖](https://x.com/spotgamma/status/2118066449868533918)。7,655.43 是 First Squawk 的开盘句子。7,636 和 7,700 是 SpotGamma 的句子。7,569 是他写的周二收盘，不是这张周三收盘。

开盘前的期货路径是先跌后被买回去，抓取开始时已经在涨的一侧。线外的 Gary Black 10:59 UTC：标普期货 +0.7%，纳斯达克期货 +0.6%，布伦特到每桶 103 美元，10 年期到 4.92%：[帖](https://x.com/garyblack00/status/2117934874145198508)。Kobeissi 13:11 UTC：道指有望开盘高出将近 1,000 点，并把隔夜的下跌写成教科书式的空头陷阱：[帖](https://x.com/KobeissiLetter/status/2117968023474872708)。线外的 Newsquawk 13:46 UTC 的盘前表是标普期货 +1.1%、纳斯达克期货 +0.4%、罗素期货 +1.7%：[帖](https://x.com/Newsquawk/status/2117976659500429547)。线外的 RedDog：隔夜标普期货一度跌近 100 点，到早上期货大幅反转，SPY 指示高出约 8 美元，QQQ 高出约 3 美元：[帖](https://x.com/RedDogT3/status/2117982085294018841)。MarketWatch 14:34 UTC 的标题是道指开盘高出 1,000 点：[帖](https://x.com/MarketWatch/status/2117988952283992382)。Kobeissi 14:35 UTC：道指涨超 1,100 点，开盘时美股市值增加超过 1 万亿美元：[帖](https://x.com/KobeissiLetter/status/2117989202151576061)。将近 1,000 点、1,000 点、超过 1,100 点、997.76 点，按发帖顺序留着。

盘中还有更高的一组，不要拿去替换收盘。Kobeissi 14:53 UTC 把当时的反应写成标普 +1.7%、道指 +2.4%、纳斯达克 100 +2.0%，白银 +5.0%，黄金 +3.0%，比特币 +3.0%，WTI -3.5%，美股市值当天增加 1.3 万亿美元：[帖](https://x.com/KobeissiLetter/status/2117993673174532144)。1.7% 是这一条的标普。1.61% 是下面的收盘帖。2.0% 是纳斯达克 100。开盘那张 1.07% 是综合指数。

收盘点位是 First Squawk 21:10 UTC 起的三张帖。纳斯达克涨 1.42%，到 25,732.53，涨 360.52 点：[帖](https://x.com/FirstSquawk/status/2118088576135241870)。标普 500 涨 1.61%，到 7,690.79，涨 121.87 点：[帖](https://x.com/FirstSquawk/status/2118088643097366638)。道指涨 3.03%，到 53,357.52，涨 1,570.80 点：[帖](https://x.com/FirstSquawk/status/2118088661451649064)。MarketWatch 21:35 UTC 是另一张：道指涨 1,569.40 点，或 3.03%，到 53,356.12，点和百分比都是 2025 年 4 月 9 日以来最大；标普涨 119.70 点，或 1.58%，到 7,688.62，是 2026 年 8 月 4 日以来最好的一天；纳斯达克涨 364.50 点，或 1.44%，到 25,736.51：[帖](https://x.com/MarketWatch/status/2118094828055711913)。7,690.79 和 7,688.62、25,732.53 和 25,736.51、53,357.52 和 53,356.12、1,570.80 和 1,569.40，并列。Investing.com 的标题是道指收盘涨了将近 1,600 点，是 2026 年最好的一天，没有写出点位：[帖](https://x.com/Investingcom/status/2118090067927511091)。Morning Brew 的收盘亮点又是一组百分比：道指 +3.0%，2025 年 4 月 9 日以来最好，并自 9 月以来第一次站上 53,000；标普 +1.6%，2026 年 4 月 8 日以来最好；纳斯达克 +1.4%；罗素 2000 +1.5%：[帖](https://x.com/MorningBrew/status/2118090165340033173)。“4 月 8 日”是这一条。“8 月 4 日”是 MarketWatch 的句子。First Squawk 的收盘综述把标普写成跳涨 1.6%、道指涨 3%，国债收益率跌 7 个基点，布伦特跌破每桶 100 美元：[帖](https://x.com/FirstSquawk/status/2118095074332680613)。路透的收盘标题没有点位：华尔街收盘大涨，数据中心股票因为担心人工智能监管收紧而下跌：[帖](https://x.com/Reuters/status/2118135451924181236)。

指数里面已经拆开。线外的 Bespoke 14:56 UTC：纳斯达克涨 2%，费城半导体指数 30 只成分里有 25 只在跌：[帖](https://x.com/bespokeinvest/status/2117994495857856884)。16:29 UTC 他把费城半导体写成下跌超过 4.0%，并说纳斯达克涨 1% 以上、同时费城半导体跌得比当天更深的日子，之前只有 2001 年 3 月 30 日的 -4.4% 和 2008 年 7 月 22 日的 -4.5%：[帖](https://x.com/bespokeinvest/status/2118017754251006456)。2% 和 25 只是下午早些时候。-4.0% 是 16:29 UTC 的句子，不是收盘点位。线外的 Ryan Detrick 在收盘之后写，纽约证券交易所有 150 只创出新高，是 8 月初以来最多；标普有 67 只创出新高，是 2 月以来最多：[150 只](https://x.com/RyanDetrick/status/2118173285515223427)、[67 只](https://x.com/RyanDetrick/status/2118173925691822271)。同一小时他又写成 67 只新高对 3 只新低：[帖](https://x.com/RyanDetrick/status/2118175302144737573)。10 月初标普里站上 50 日均线的比例是 20%，当时接近 72%：[帖](https://x.com/RyanDetrick/status/2118174649900990960)。线外的 Ole Hansen 周四早上把标普等权指数写成创出新高，今年至今 +16.5%，标普 500 今年至今 +12.3%：[帖](https://x.com/Ole_S_Hansen/status/2118252615016353898)。16.5% 和 12.3% 是今年至今，不是周三的单日涨幅。

## 油、黄金和收益率沿途有多句

油价一天里换了好几张绝对价格。Gary 盘前的布伦特是 103。First Squawk 14:04 UTC：WTI 下跌 3%，到每桶 93.25 美元：[帖](https://x.com/FirstSquawk/status/2117981370354172333)。15:57 UTC：布伦特跌破 100 美元，是 10 月 7 日以来第一次：[帖](https://x.com/FirstSquawk/status/2118009682140995912)。DeItaone 16:06 UTC：布伦特和美国原油期货下跌超过 4 美元：[帖](https://x.com/DeItaone/status/2118012006972158184)。16:17 UTC：布伦特下跌超过 5 美元：[帖](https://x.com/DeItaone/status/2118014757974511892)。16:37 UTC：美国原油下跌超过 5 美元，布伦特下跌超过 7 美元：[帖](https://x.com/DeItaone/status/2118019926015312377)。First Squawk 16:39 UTC：美国原油接近每桶 90 美元：[帖](https://x.com/FirstSquawk/status/2118020407290900972)。17:52 UTC：布伦特下跌 10%，接近 93 美元，两个月低点：[帖](https://x.com/FirstSquawk/status/2118038570770600061)。

结算是另一张。FinancialJuice、LiveSquawk、First Squawk：WTI 12 月期货结算每桶 88.12 美元，下跌 7.97 美元，跌幅 8.29%：[FinancialJuice](https://x.com/financialjuice/status/2118063524534735267)、[LiveSquawk](https://x.com/LiveSquawk/status/2118063634337198083)、[First Squawk](https://x.com/FirstSquawk/status/2118063632257036562)。布伦特结算每桶 94.62 美元，下跌 8.98 美元，跌幅 8.67%：[FinancialJuice](https://x.com/financialjuice/status/2118066891197677797)、[LiveSquawk](https://x.com/LiveSquawk/status/2118067154499064029)。Morning Brew 的收盘亮点写成美国原油 88.56、跌 7.8%，布伦特 95.12、跌 8.2%：[帖](https://x.com/MorningBrew/status/2118090165340033173)。88.12、88.56、93.25、接近 90、94.62、95.12、接近 93、103，并列。上一份日报里的周二结算不在这里重算。

夜里又低了一截。First Squawk 01:43 UTC：美国原油期货滑到 87.07，下跌 1.05 美元：[帖](https://x.com/FirstSquawk/status/2118157253987737955)。01:44 UTC：布伦特下跌 1.01 美元，到 93.61：[帖](https://x.com/FirstSquawk/status/2118157397659435260)。线外的 Ole Hansen 09:44 UTC：布伦特在 200 日均线 93.40 找到支撑，24 小时里试了两次都被拒绝：[帖](https://x.com/Ole_S_Hansen/status/2118278162631024792)。93.61、93.40 和结算 94.62 并列。93.40 是均线位置。

黄金也是几张。First Squawk 在 ADP 之后：现货黄金最后上涨 2.74%，到每盎司 4,035.85 美元：[帖](https://x.com/FirstSquawk/status/2117969787867578711)。14:47 UTC：现货白银涨幅扩到将近 5%，到 52.26 美元：[帖](https://x.com/FirstSquawk/status/2117992060544524371)。收盘综述：黄金上涨 3.4%，到 4,063 美元；比特币站上 80,000：[帖](https://x.com/FirstSquawk/status/2118095096226938929)。周四 01:12 UTC：黄金上涨将近 1%，到 4,098.29：[帖](https://x.com/FirstSquawk/status/2118149419472404594)。02:13 UTC：黄金上涨将近 2%，到 4,134.67：[帖](https://x.com/FirstSquawk/status/2118164702194970668)。05:30 UTC：黄金从两周高点回落，在美元偏弱的语气里仍守在 4,100 上方：[帖](https://x.com/FirstSquawk/status/2118214343926128671)。Peter Schiff：周三白天涨了超过 130 美元之后，夜里又涨 55 美元，交易在 4,100 上方；白银再涨 40 美分，交易在 52.50 上方：[帖](https://x.com/PeterSchiff/status/2118155528786579941)。4,035.85、4,063、4,098.29、4,134.67、4,100 上方，按时间留着。52.26 和 52.50 并列。

收益率没有一张和油价结算写在同一句里的美国 10 年期收盘点位。Gary 盘前是 4.92%。First Squawk 的收盘综述是收益率下跌 7 个基点，没有写出收盘绝对水平。周四 00:36 UTC 他把美国 10 年期写成 4.88%：[帖](https://x.com/FirstSquawk/status/2118140486049480749)。彭博引 Ed Yardeni：通胀预计降温的前提下，10 年期在大约 5% 看起来很有吸引力：[帖](https://x.com/business/status/2118262057648689546)。4.92%、下跌 7 个基点、4.88%、大约 5%，并列。法国 10 年期下跌 12.5 个基点到 4.80%，是 DeItaone 的另一句，不是美国国债：[帖](https://x.com/DeItaone/status/2118010921356259532)。英国 10 年期曾到 5.21%，后来到 5.143%，也不是美国国债：[5.21%](https://x.com/FirstSquawk/status/2117925360067383433)、[5.143%](https://x.com/FirstSquawk/status/2118017620385665211)。

## 观点分成四组

### 1. 选举被交易成更低的油价，周四早上海峡又有新句子

盘前的映射是蓝色浪潮对上伊朗战争。线外的 Robin Brooks 12:45 UTC：一切取决于和伊朗的战争以及油价；大规模蓝色浪潮会让特朗普降温撤出，还是加倍恢复轰炸；布伦特在 102 美元，从上周结束时的 118 掉下来，市场在赌前者：[帖](https://x.com/robin_j_brooks/status/2117961396583280975)。17:03 UTC 他又把布伦特写成 95 美元、较周五下跌 10%，并说高油价是风险溢价，不是供给、运费或中国：[帖](https://x.com/robin_j_brooks/status/2118026446656708801)。102 和 95 是两句。他 13:49 UTC 另列了三个问题：对伊朗的战争是不是结束了，长端收益率会不会因为超大规模云少发债而下降，以及贬值交易会不会再起来：[帖](https://x.com/robin_j_brooks/status/2117977648773394880)。Kobeissi 把隔夜先跌后涨写成空头陷阱，见上。

收盘之后，降温和备战同时出现。路透：特朗普说共和党受到伊朗战争的伤害：[帖](https://x.com/Reuters/status/2118142529921015972)。Kobeissi 03:11 UTC 引 Axios：特朗普政府和美军正在完成准备，以便可能恢复对伊朗的“重大”作战；细节包括向中东增派资产，以及副总统万斯私下指责内塔尼亚胡在伊朗问题上“什么都错了”：[帖](https://x.com/KobeissiLetter/status/2118179324050260254)。FinancialJuice 04:07 UTC：伊朗伊斯兰革命卫队称，两艘油轮和一艘拖船在霍尔木兹海峡起火：[帖](https://x.com/financialjuice/status/2118193363706888462)。First Squawk 转发同一句：[帖](https://x.com/FirstSquawk/status/2118193748928778539)。随后革命卫队的句子改成油轮在未经授权的航线上触雷：[帖](https://x.com/financialjuice/status/2118193850321961411)。周四 10:15 UTC，伊朗海军称油轮周四早上在霍尔木兹触雷：[FinancialJuice](https://x.com/financialjuice/status/2118285987566530876)、[First Squawk](https://x.com/FirstSquawk/status/2118285995158413447)。“起火”和“触雷”按发帖顺序留着。

阿曼和伊朗的外长周四早上通电话。First Squawk 07:17 UTC：两人讨论了地区局势和争取和平的外交：[帖](https://x.com/FirstSquawk/status/2118241202739024026)。10:11 UTC 起又是另一组：讨论保障海路的安排，强调从降温转向持久协议，并讨论维持贸易和能源流动的措施：[海路](https://x.com/FirstSquawk/status/2118285177818673603)、[持久协议](https://x.com/FirstSquawk/status/2118285212224541017)、[贸易和能源](https://x.com/FirstSquawk/status/2118285257065820200)。Steve Hanke 仍把海峡写成实际上关闭：去年 11 月 3 日有 37 艘油轮通过，今年 11 月 3 日是 1 艘：[帖](https://x.com/steve_hanke/status/2118121110902604055)。1 艘和“起火或触雷”是两件被写下来的事。阿联酋在考虑第三条绕开霍尔木兹的原油管道，是 First Squawk 周三盘中的句子：[帖](https://x.com/FirstSquawk/status/2117987172540367306)。

线外的 Ole Hansen 把周三原油下跌 8% 和近月布伦特本周下跌超过 16% 写在一起，并说大约一半跌幅发生在中期选举结果之后；特朗普承认共和党失利在很大程度上和伊朗冲突、燃料价格有关，同时没有发出立刻升级军事打击的信号：[帖](https://x.com/Ole_S_Hansen/status/2118237934146994233)。8% 是他的周三句子。结算帖的 WTI 是 -8.29%，布伦特是 -8.67%。超过 16% 是他的本周句子。他周四另写，能源下跌的同时贵金属成为选举之后的赢家，因为能源价格、通胀和利率担忧、国债收益率和美元一起往下，逼最近建立的投机空头回补：[帖](https://x.com/Ole_S_Hansen/status/2118232756085731673)。

线外的 Andreas Steno 把选举写成同时定价了两件事：油价战争的结束，和数据中心斗争的开始：[帖](https://x.com/RenMacLLC/status/2118134144009924870)。这句是 RenMac 的，不是 Steno。Steno 周四早上的句子是半导体：见下一节。RenMac 在投票日尘埃落定后仍把劳动力市场写成在变好、金融条件仍然宽松、通胀远高于目标，并写民主党不是唯一要来的东西，加息也是：[帖](https://x.com/RenMacLLC/status/2118011217012817940)。

### 2. 指数在涨的时候，数据中心和部分芯片在跌

盘前表已经把两边分开。Newsquawk：可再生能源上涨，First Solar +7.5%，清洁能源 ETF ICLN +4.8%；neocloud 承压，CoreWeave -6.2%，IREN -5.4%，NBIS -3.2%，neocloud ETF -7%；超大规模云上涨，亚马逊 +3.8%，微软 +2.7%，Alphabet +1.2%；英伟达 -1.5%：[帖](https://x.com/Newsquawk/status/2117976659500429547)。DeItaone 14:42 UTC 的早盘句是亚马逊 +7%、微软 +5.7%、Alphabet +2.9%、Meta +1.7%：[帖](https://x.com/DeItaone/status/2117990861027881222)。盘前的 +3.8% 和早盘的 +7% 是亚马逊的两句。

下午的数据中心标题更重。彭博：CoreWeave 的债券周三下跌，有的落到新低，触发器是支持放慢数据中心建设的民主党人赢下多场州长选举，包括得克萨斯：[帖](https://x.com/business/status/2118043131576783020)。First Squawk 用了同一句：[帖](https://x.com/FirstSquawk/status/2118043572100637139)。Investing.com：人工智能数据中心股票因民主党大胜下跌，点名 CoreWeave、NBIS、IREN：[帖](https://x.com/Investingcom/status/2118048854843220299)。线外的 The Stalwart：CoreWeave 当天下跌将近 10%：[帖](https://x.com/TheStalwart/status/2118178229940851114)。零对冲：CoreWeave 债券到 78，股权价值之前债权人已经减值 22 美分：[帖](https://x.com/zerohedge/status/2118179141690483154)。将近 -10% 是股价句子。78 是债券句子。线外的 SpotGamma：31 个非财报名字里有 28 个的 30 天平值隐含波动率较周二下午下降；QQQ 掉 4.5 个波动率点，IWM 掉 3.0，标普掉 2.7，时间是美东下午 2 点。跌得最差的那几只波动率在升：Marvell、CoreWeave、阿里巴巴。Marvell 和 CoreWeave 较周二收盘下跌 9% 到 11%：[帖](https://x.com/spotgamma/status/2118077662912823415)。9% 到 11% 是这一条。将近 10% 是 The Stalwart。

英特尔被零对冲写成已经低于卖方最低目标价，56 位分析师里有 1 个卖出、其余是买入或持有：[帖](https://x.com/zerohedge/status/2118193722399825928)。Keith McCullough 把当天全市场最活跃的两个代码写成还在爆的人工智能泡沫，点名半导体杠杆 ETF SOXL 和英特尔：[帖](https://x.com/KeithMcCullough/status/2118138923331252443)。美光在 aleabitoreddit 的对照里是 -4.41%，多邻国是 +34.86%，他写成从风险资产转向安全、优质资产：[帖](https://x.com/aleabitoreddit/status/2118004727053218010)。-4.41% 是这一条的盘中或当日句子，不是收盘专帖。

线外的 Steno 周四 08:00 UTC：半导体被定价成芯片销售到 2027 年中腰斩；韩国出货 +200%，内存售罄而且预付，每家研究机构现在都发誓自己从没喜欢过这笔交易：[帖](https://x.com/AndreasSteno/status/2118251986105565212)。腰斩是他的定价句子。+200% 是他的韩国出货句子。彭博周四的亚洲标题是，民主党内阁式的横扫推动了轮动，芯片股因为人工智能建设的担忧下跌，汽车和消费品上涨：[帖](https://x.com/business/status/2118194120590012863)。First Squawk 00:36 UTC：MSCI 亚太指数 +0.3%，日本东证指数 +2.1%，澳洲标普/ASX 200 +1.3%，韩国 KOSPI 因为芯片股弱势下跌 2.7%：[帖](https://x.com/FirstSquawk/status/2118140460703342768)。Newsquawk 更早一张是 KOSPI -1.9%、日经 +0.5%、ASX +1.5%：[帖](https://x.com/Newsquawk/status/2118137275280154802)。-1.9% 和 -2.7% 并列。

### 3. 财报的预期不要并成一套，盘后百分比按账号留着

Uber 的调整后每股收益都写成 0.88 美元，估计值不是同一个数。FinancialJuice：调整后每股收益 0.88 对 0.87，收入 147.7 亿对 146.5 亿，总预订 598.2 亿对 597.9 亿，出行预订 295.1 亿对 298.8 亿，配送预订 285.4 亿对 284.1 亿，调整后 EBITDA 29.6 亿对 29.3 亿；同一帖还有一行每股收益 0.25 美元。四季度总预订展望 632.5 亿到 652.5 亿，估计 642.9 亿：[帖](https://x.com/financialjuice/status/2117949334478115259)。Yahoo Finance：收入 147.7 亿对 146.5 亿，每股收益 0.88 对 0.87，总预订 598 亿对 598 亿，四季度总预订展望对的是 644 亿：[帖](https://x.com/YahooFinance/status/2118083055025877460)。StockMKTNewz：每股收益 0.88 对 0.86，收入 148 亿对 146.9 亿：[帖](https://x.com/StockMKTNewz/status/2117949648975569226)。TrendSpider：调整后每股收益 0.88 对 0.96，写成不及；销售额 147.6 亿对 147.0 亿；四季度调整后每股收益指引被写成下调：[帖](https://x.com/TrendSpider/status/2117957180989304903)。0.87、0.86、0.96 并列。0.25 是 FinancialJuice 同一帖里的另一行，不换成 0.88。线外的 Gary Black 引彭博：结果好于被下调之后的预期，盘前一度写成 +0.7%；他帖子的开头是 +7%：[帖](https://x.com/garyblack00/status/2118001531572093261)。First Squawk 15:21 UTC：Lyft 涨幅扩到 11%，Uber 上涨 7%：[帖](https://x.com/FirstSquawk/status/2118000769916129433)。+0.7%、+7%、上涨 7% 按账号留着。没有一张 Uber 的收盘百分比帖。

麦当劳的估计也有两套。StockMKTNewz：每股收益 3.57 对 3.38，收入 71.6 亿对 72.8 亿，盘前最初上涨 1.7%：[帖](https://x.com/StockMKTNewz/status/2117951427213455727)。First Squawk：调整后每股收益 3.57 对 3.40，收入 71.6 亿对 72.9 亿，同店销售 +1.5% 对 +1.35%，美国同店 -0.2% 对 -0.47%：[帖](https://x.com/FirstSquawk/status/2117951438844539134)。3.38 和 3.40、72.8 亿和 72.9 亿并列。CVS 是 First Squawk 的一张：调整后每股收益 2.09 对 1.66，调整后经营利润 41.9 亿对 36.2 亿，净收入 1,084 亿对 1,046.2 亿；全年调整后每股收益至少 8.20，原先是 7.90 到 8.10，估计 8.05；全年收入至少 4,200 亿，原先至少 4,140 亿：[帖](https://x.com/FirstSquawk/status/2117943594418090409)。卡夫亨氏：调整后每股收益 0.53 对 0.42，净销售 61 亿对 60.9 亿，有机收入 -1.1% 对 -1.9%；全年调整后每股收益 2.07 到 2.13，原先 2.03 到 2.09：[帖](https://x.com/FirstSquawk/status/2117951473116209187)。

高通的收入有两套，盘后百分比有一句。FinancialJuice 和 LiveSquawk、Yahoo Finance、First Squawk：调整后每股收益 2.17 对 2.16，调整后收入 104.4 亿对 101.2 亿；一季度调整后每股收益展望 2.15 到 2.35，估计 2.32；一季度收入 104 亿到 112 亿，估计 105.5 亿：[FinancialJuice](https://x.com/financialjuice/status/2118086103567565126)、[LiveSquawk](https://x.com/LiveSquawk/status/2118086576681152726)、[Yahoo](https://x.com/YahooFinance/status/2118089045519810976)、[First Squawk](https://x.com/FirstSquawk/status/2118089490032197967)。StockMKTNewz：每股收益 2.17 对 2.16，收入 103.2 亿对 101.1 亿：[帖](https://x.com/StockMKTNewz/status/2118086920429568397)。TrendSpider：销售额 103.3 亿对 101.1 亿，并写成下调了一季度公认会计准则每股收益指引，盘后 -6%：[帖](https://x.com/TrendSpider/status/2118087264588705810)。线外的 The Transcript 也写成盘后 -6%，并引首席执行官：四季度非公认会计准则收入在指引高端，汽车和物联网合计收入同比 +36%：[帖](https://x.com/TheTranscript_/status/2118090897577619840)。104.4 亿、103.2 亿、103.3 亿并列。Investing.com 把季度写成三季度，估计写成每股收益 2.17 对 2.17、收入 104.4 亿对 101.4 亿：[帖](https://x.com/Investingcom/status/2118092781751251270)。“三季度”和“四季度”按账号留着。数据中心是另一组。The Transcript：一季度数据中心收入超过 6.5 亿美元，之后每个季度增加，2027 财年末尾的年化运行率是 70 亿美元：[帖](https://x.com/TheTranscript_/status/2118091298276348251)。First Squawk 引首席财务官：一季度指引反映开始向两家超大规模云客户出货定制芯片，QCT 手机收入一季度环比将下降中个位数：[帖](https://x.com/FirstSquawk/status/2118104872247857650)。线外的 firstadopter：高通收入同比 -7%，盈利同比 -28%：[帖](https://x.com/firstadopter/status/2118090897900364236)。-7% 和 -28% 是同比，不是盘后的 -6%。

Arm 是 First Squawk 的一张：二季度调整后每股收益 0.52 对 0.47，收入 14.4 亿对 13.8 亿，调整后经营利润 6.38 亿对 5.757 亿：[帖](https://x.com/FirstSquawk/status/2118089462836351373)。The Transcript 引首席执行官：连续第五个季度收入增长超过 20%：[帖](https://x.com/TheTranscript_/status/2118090166242070637)。AppLovin 盘后涨幅扩到 +16%，是 TrendSpider 的句子：[帖](https://x.com/TrendSpider/status/2118090040328978612)。Snap 盘后 -10%，每股收益 0.03 对 0.00，销售额 17.2 亿对 17.3 亿：[帖](https://x.com/TrendSpider/status/2118089551969403312)。CAVA 盘后下跌超过 10%，是 StockMKTNewz 的句子，没有随帖写出每股收益：[帖](https://x.com/StockMKTNewz/status/2118132670710333556)。

苹果和微软的涨幅沿途在变，收盘百分比不是同一张。StockMKTNewz 14:39 UTC：苹果早盘上涨超过 5%：[帖](https://x.com/StockMKTNewz/status/2117990162890416339)。15:05 UTC：创出历史新高：[帖](https://x.com/StockMKTNewz/status/2117996677671837853)。Kobeissi 16:31 UTC：涨幅扩到 +7%，市值超过 5.1 万亿美元，写成全球市值最大：[帖](https://x.com/KobeissiLetter/status/2118018182598504854)。Morning Brew 盘中的七巨头表：亚马逊 +7.1%，微软 +6.9% 并创历史新高，苹果 +6.5% 并创历史新高，Alphabet +4.5%，Meta +2.4%，英伟达 -1.2%，特斯拉 -3.3%：[帖](https://x.com/MorningBrew/status/2118024873507197330)。他后来的市值表：苹果增加 3,110 亿美元、+6.2%；微软增加 2,650 亿美元、+7.2%；亚马逊增加 1,870 亿美元、+6.9%；Alphabet 增加 1,470 亿美元、+3.8%；Meta 增加 370 亿美元、+1.6%：[帖](https://x.com/MorningBrew/status/2118077895834832959)。收盘亮点里的苹果是 +5.3% 并创历史新高，微软是 +6.7% 并创历史新高：[帖](https://x.com/MorningBrew/status/2118090165340033173)。超过 5%、+7%、+6.5%、+6.2%、+5.3% 是苹果的五句。微软另有 Kobeissi 15:37 UTC 的 +7%、市值 4.1 万亿美元、全球第三：[帖](https://x.com/KobeissiLetter/status/2118004815829872890)。TrendSpider：亚马逊开盘大涨 +8%，到 8 月中以来最高：[帖](https://x.com/TrendSpider/status/2117997156028293380)。+8%、+7.1%、+7%、+6.9% 是亚马逊的四句。英伟达盘前 -1.5%，七巨头表上 -1.2%。没有一张英伟达的收盘百分比帖。

苹果还有一张和股价无关的内部预算。FinancialJuice 和 LiveSquawk、Investing.com：把部分工程师的每日人工智能额度从 300 美元降到 200 美元，并计划进一步削减：[FinancialJuice](https://x.com/financialjuice/status/2118067182022140249)、[LiveSquawk](https://x.com/LiveSquawk/status/2118067765739200696)。微软另有一张债券：First Squawk 写筹集 250 亿美元、分 10 档：[帖](https://x.com/FirstSquawk/status/2118089508973609401)。周四标题是微软拒绝了英国 Nscale 的一项大型人工智能合作，消息来自《金融时报》：[帖](https://x.com/FirstSquawk/status/2118207485106672052)。250 亿美元是债券。拒绝 Nscale 是另一句。

AMD 没有一张周三收盘百分比。First Squawk：公司 8 月达成协议，以 29 亿美元收购 Taalas，其中约 14 亿美元是或有对价：[帖](https://x.com/FirstSquawk/status/2117938590240141406)。同一账号：美银把目标价从 720 美元砍到 650 美元：[帖](https://x.com/FirstSquawk/status/2117990272722452928)。Benzinga 复述的仍是周二那份业绩：收入同比 +45% 到 134 亿美元，数据中心同比 +97% 到 85.5 亿美元，Lisa Su 预计服务器 CPU 收入 2027 年翻倍：[帖](https://x.com/Benzinga/status/2118106766281990473)。134 亿和 85.5 亿是上一份业绩的复述，不是周三新的收盘价。

### 4. ADP 和服务业指数已经出来，加息的句子还在

ADP 的结果都是增加 86,000，估计和前值不要并。FinancialJuice：86,000，预期 67,000，前值 90,000：[帖](https://x.com/financialjuice/status/2117968956841419075)。DeItaone：服务业 +82,000，商品生产 +4,000，贸易和运输 +39,000，专业和商业服务 -27,000：[帖](https://x.com/DeItaone/status/2117969214665347453)。线外的 Hedgeye：86,000，估计 69,000，前值 86,000；换工作的人总薪资同比 +7.6%，是 2024 年 3 月以来最快：[人数](https://x.com/Hedgeye/status/2117969376305697087)、[薪资](https://x.com/Hedgeye/status/2117969557612806280)。Liz Ann Sonders：+86,000 对估计 +67,000、前值 +86,000，是 6 月以来最强的连续增长：[帖](https://x.com/LizAnnSonders/status/2117974766594253252)。67,000 和 69,000 并列。前值 90,000 和 86,000 并列。

服务业指数是两套调查。FinancialJuice 和 LiveSquawk：ISM 服务业 54.5，预期 54.8，前值 54.9；价格指数 73.0，预期 74.6，前值 74.0；新订单 55.9，预期 58.5，前值 59.8；就业 51.4，预期 50.0，前值 50.1：[FinancialJuice](https://x.com/financialjuice/status/2117995419099890139)、[LiveSquawk](https://x.com/LiveSquawk/status/2117995442831016174)。Liz Ann 的价格指数前值写成 74.0，没有写 74.6 的预期：[帖](https://x.com/LizAnnSonders/status/2117999867943420228)。标普全球服务业终值是另一张：56.1，预期 57.9，前值 57.9；综合指数 55.9，预期 57.3，前值 57.6：[LiveSquawk](https://x.com/LiveSquawk/status/2117991602597630210)、[First Squawk](https://x.com/FirstSquawk/status/2117991916545679629)。54.5 是 ISM。56.1 是标普全球。

库存是周三 10:30 的那张，和周四的物价指数分开。First Squawk：美国原油库存实际减少 86.5 万桶，前值减少 189.2 万桶，预期减少 37.75 万桶：[帖](https://x.com/FirstSquawk/status/2118002882477949339)。Ole Hansen 周四复述 EIA：原油和汽油小幅去库，馏分油减少 360 万桶，总量降到 1 亿桶以下，是 2003 年以来第一次；原油产量回到纪录的每天 1,400 万桶以上；战略储备提取放慢到每天 40 万桶：[帖](https://x.com/Ole_S_Hansen/status/2118242319803564105)。减少 86.5 万桶是 First Squawk 的原油句子。360 万桶是馏分油。欧元区 9 月生产者价格指数同比 11.1%，预期 10.6%，前值 8.2%；环比 2.5%，符合预期：[LiveSquawk](https://x.com/LiveSquawk/status/2118282296881225943)。11.1% 是欧元区出厂价格，不是美国 CPI。

加息预期没有被周三的上涨收掉。RenMac 的句子见上。Charlie Bilello：全球通胀在升，美联储、欧洲央行、日本央行和英国央行都落在曲线后面，年底前这几家都会继续加息：[帖](https://x.com/charliebilello/status/2118163522731298958)。挪威央行周四把存款利率维持在 4.50%，符合预期，并写如果需要就准备加息，通胀仍明显高于目标：[维持](https://x.com/LiveSquawk/status/2118267173575721255)、[准备加息](https://x.com/LiveSquawk/status/2118267873671983107)。英国央行还没有决定。彭博的标题是，英国央行看起来准备 25 个基点、把利率加到 4%，会是三年多来第一次加息：[帖](https://x.com/business/status/2118270861656363479)。这是决定之前的句子。瑞典 10 月 CPI 同比 0.9%，预期 1.2%，前值 1.1%；CPIF 同比 1.1%，预期 1.4%：[帖](https://x.com/FirstSquawk/status/2118237780073648426)。德国 9 月工厂订单环比 +4.4%，预期 +4.5%，前值 -10.6%，修正后的前值是 -10.1%：[帖](https://x.com/LiveSquawk/status/2118238776279343508)。

国债供给是另一张。First Squawk：美国财政部修改了关于未来拍卖规模变化的指引：[帖](https://x.com/FirstSquawk/status/2117974930570747952)。彭博：华尔街策略师在财政部放出信号、票据和债券的拍卖规模变化已经在眼前之后，正在重写明年的美国借款预测：[帖](https://x.com/business/status/2118136247755440202)。线外的 Jeffrey Gundlach：新的民主党多数接到的任务好像是“可负担性”；要么找到很快把价格打下来的魔杖，要么再次给人民发钱，那只会制造更多通胀：[帖](https://x.com/TruthGundlach/status/2118172592427405328)。线外的 Cem Karsan：蓝色浪潮很可能把特朗普和美联储的看跌期权调低了；印钞和推高资产价格的剧本还在，但动用它的政治门槛升高了，下一次流动性可能要等更深的市场危机；左尾更肥了：[帖](https://x.com/jam_croissant/status/2118176904670830766)。

## 要盯住的五件事

1. **周三收盘有两张点位，开盘那张已经过期。** First Squawk 的收盘是纳斯达克 25,732.53、涨 1.42%，标普 7,690.79、涨 1.61%，道指 53,357.52、涨 3.03%。MarketWatch 是纳斯达克 25,736.51、涨 1.44%，标普 7,688.62、涨 1.58%，道指 53,356.12、涨 3.03%。开盘是标普 7,655.43、涨 1.14%，道指 52,784.48、涨 1.93%，纳斯达克 25,643.36、涨 1.07%。SpotGamma 的开盘是 7,636，盘中到过 7,700。
2. **周四盘前期货没有一张新的收盘。** 周三夜里 CNBC 的标题是大涨之后期货变动不大。周四 06:31 UTC 的 Newsquawk 写成美国股指期货涨跌互现，纳斯达克期货落后。这些都不是周四收盘。RedDog 要看的是 SPY 能不能在 762 上方消化，再清除 769 和 774。
3. **WTI 结算是 88.12，布伦特结算是 94.62。** 沿途还有 103、93.25、接近 90、下跌 10% 到接近 93、Morning Brew 的 88.56 和 95.12，以及夜里的 87.07 和 93.61。Ole 的 200 日均线是 93.40。黄金是 4,035.85、4,063、4,098.29、4,134.67，以及“守在 4,100 上方”。10 年期盘前 4.92%，综述是下跌 7 个基点，周四亚洲时段写成 4.88%，Yardeni 说大约 5% 有吸引力。
4. **海峡的句子在结算之后又增加了。** 革命卫队写两艘油轮和一艘拖船起火，后来写成触雷。阿曼和伊朗外长在谈海路、贸易和能源。Kobeissi 引 Axios，写可能恢复重大作战的准备还在做。Hanke 仍写 11 月 3 日只有 1 艘油轮通过。非农在周五。周四开盘前的财报日历已经列出来，抓取结束时还没有新的公布值。
5. **高通盘后 -6% 只有 TrendSpider 和 The Transcript 两句。** 调整后收入 104.4 亿对 101.2 亿，另有 103.2 亿和 103.3 亿的句子。一季度数据中心收入被写成超过 6.5 亿美元，2027 财年末尾年化运行率 70 亿美元。Uber 的估计有 0.87、0.86 和 0.96 三句。苹果的当日涨幅有超过 5%、+7%、+6.5%、+6.2% 和 +5.3%。CoreWeave 有将近 -10%，也有 9% 到 11%。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 收盘两张 | 道指、标普、纳斯达克 | First Squawk：道指 53,357.52，+3.03%。标普 7,690.79，+1.61%。纳斯达克 25,732.53，+1.42%。MarketWatch：53,356.12、7,688.62、25,736.51 | [道指](https://x.com/FirstSquawk/status/2118088661451649064)、[标普](https://x.com/FirstSquawk/status/2118088643097366638)、[纳斯达克](https://x.com/FirstSquawk/status/2118088576135241870)、[另一张](https://x.com/MarketWatch/status/2118094828055711913) |
| 开盘 | 道指、标普、纳斯达克 | 开盘后标普 7,655.43，+1.14%。道指 52,784.48，+1.93%。纳斯达克 25,643.36，+1.07%。另有开盘 7,636、盘中 7,700 | [开盘](https://x.com/FirstSquawk/status/2117988101599764889)、[7636](https://x.com/spotgamma/status/2118066449868533918) |
| 周四开盘前的位置 | SPY | 看能不能在 762 上方消化，再清除 769 和 774。隔夜期货曾跌近 100 点，早上指示 SPY 高出约 8 美元 | [762](https://x.com/RedDogT3/status/2118285139834966156)、[隔夜](https://x.com/RedDogT3/status/2117982085294018841) |
| 内部已经拆开 | 费城半导体、标普广度 | 纳斯达克涨 2% 时，30 只里有 25 只在跌。16:29 UTC 费城半导体超过 -4.0%。标普 67 只新高对 3 只新低。等权指数今年至今 +16.5%，标普 +12.3% | [25 只](https://x.com/bespokeinvest/status/2117994495857856884)、[-4%](https://x.com/bespokeinvest/status/2118017754251006456)、[67 对 3](https://x.com/RyanDetrick/status/2118175302144737573)、[等权](https://x.com/Ole_S_Hansen/status/2118252615016353898) |
| 涨幅沿途在变 | AAPL、MSFT、AMZN | 苹果有超过 +5%、+7%、+6.5%、+6.2%、+5.3%。微软有 +5.7%、+7%、+6.9%、+7.2%、+6.7%。亚马逊开盘有 +8%，另有 +7.1% 和 +6.9%。英伟达盘前 -1.5%，表上 -1.2% | [苹果 +7%](https://x.com/KobeissiLetter/status/2118018182598504854)、[七巨头](https://x.com/MorningBrew/status/2118024873507197330)、[收盘亮点](https://x.com/MorningBrew/status/2118090165340033173) |
| 内部预算和债券 | AAPL、MSFT | 苹果把部分工程师的每日人工智能额度从 300 美元降到 200 美元。微软筹集 250 亿美元、10 档。周四标题是拒绝英国 Nscale 的合作 | [额度](https://x.com/financialjuice/status/2118067182022140249)、[250 亿](https://x.com/FirstSquawk/status/2118089508973609401)、[Nscale](https://x.com/FirstSquawk/status/2118207485106672052) |
| 盘后 -6% | QCOM | 调整后每股收益 2.17 对 2.16。调整后收入 104.4 亿，另有 103.2 亿和 103.3 亿。盘后 -6%。数据中心一季度超过 6.5 亿美元，2027 财年末尾年化 70 亿美元 | [业绩](https://x.com/financialjuice/status/2118086103567565126)、[-6%](https://x.com/TrendSpider/status/2118087264588705810)、[70 亿](https://x.com/TheTranscript_/status/2118091298276348251) |
| 预期三套 | UBER | 调整后每股收益 0.88。估计有 0.87、0.86 和 0.96。0.96 那张写成不及。盘中上涨 7%，盘前还有 +0.7% 的句子。没有收盘百分比 | [0.87](https://x.com/financialjuice/status/2117949334478115259)、[0.86](https://x.com/StockMKTNewz/status/2117949648975569226)、[0.96](https://x.com/TrendSpider/status/2117957180989304903) |
| 美国同店为负 | MCD | 调整后每股收益 3.57。估计有 3.38 和 3.40。收入 71.6 亿，估计有 72.8 亿和 72.9 亿。美国同店 -0.2% | [3.40](https://x.com/FirstSquawk/status/2117951438844539134) |
| 上调全年 | CVS、KHC | CVS 调整后每股收益 2.09 对 1.66，全年至少 8.20。卡夫亨氏调整后每股收益 0.53 对 0.42，全年 2.07 到 2.13 | [CVS](https://x.com/FirstSquawk/status/2117943594418090409)、[KHC](https://x.com/FirstSquawk/status/2117951473116209187) |
| 盘后两边 | APP、SNAP、ARM | AppLovin 盘后涨幅扩到 +16%。Snap 盘后 -10%。Arm 调整后每股收益 0.52 对 0.47，收入 14.4 亿对 13.8 亿 | [+16%](https://x.com/TrendSpider/status/2118090040328978612)、[-10%](https://x.com/TrendSpider/status/2118089551969403312)、[Arm](https://x.com/FirstSquawk/status/2118089462836351373) |
| 目标价下修 | AMD | 美银目标价 650 美元，原先 720。另有 29 亿美元收购 Taalas，其中约 14 亿美元是或有对价。没有周三收盘百分比 | [650](https://x.com/FirstSquawk/status/2117990272722452928)、[Taalas](https://x.com/FirstSquawk/status/2117938590240141406) |
| 债券和股价分开 | CRWV、MRVL | 债券有的落到新低，零对冲写成 78。股价将近 -10%，SpotGamma 写成较周二收盘 -9% 到 -11%。盘前表是 -6.2% | [债券](https://x.com/business/status/2118043131576783020)、[78](https://x.com/zerohedge/status/2118179141690483154)、[-10%](https://x.com/TheStalwart/status/2118178229940851114) |
| 低于最低目标价 | INTC | 零对冲写成已经低于卖方最低目标价。Keith 把它和 SOXL 写成当天最活跃的两个代码 | [目标价](https://x.com/zerohedge/status/2118193722399825928) |
| 两个不同的交易 | SPCX、QCOM | SpaceX 股价跌幅一度扩到超过 8%。高通给 Starlink 地面 5G 供货是另一张。高盛和 Apollo 在为 400 亿美元的 SpaceX 人工智能芯片交易找买家，又是一张 | [超过 8%](https://x.com/FirstSquawk/status/2117967483785400396)、[5G](https://x.com/StockMKTNewz/status/2117975850553323596)、[400 亿](https://x.com/Reuters/status/2118171494471651428) |
| 油的结算和夜里 | 原油、布伦特 | WTI 结算 88.12，跌 8.29%。布伦特结算 94.62，跌 8.67%。夜里 87.07 和 93.61。200 日均线 93.40 | [88.12](https://x.com/FirstSquawk/status/2118063632257036562)、[94.62](https://x.com/financialjuice/status/2118066891197677797)、[93.61](https://x.com/FirstSquawk/status/2118157397659435260)、[93.40](https://x.com/Ole_S_Hansen/status/2118278162631024792) |
| 贵金属 | 黄金、白银 | 4,035.85，收盘综述 4,063、+3.4%。夜里 4,098.29 和 4,134.67，后来守在 4,100 上方。白银 52.26，Schiff 写 52.50 上方 | [4063](https://x.com/FirstSquawk/status/2118095096226938929)、[4134](https://x.com/FirstSquawk/status/2118164702194970668)、[4100](https://x.com/FirstSquawk/status/2118214343926128671) |
| 已经公开的方向 | XLV、XLP、XLI、XLK、QQQ | Keith：做多医疗和必需消费这些在创新高的板块，做空工业，离开科技。QQQ 隐含波动率掉到 18% 之后，他做空了一部分 | [板块](https://x.com/KeithMcCullough/status/2118283615666901219)、[QQQ](https://x.com/KeithMcCullough/status/2118284965062594653) |
| 周四还没公布 | 开盘前财报 | Earnings Whispers 的周四开盘前名单里有 Conoco、Cardinal Health、Kimberly-Clark、Sony、Molson Coors、Tapestry 等。抓取结束时没有新的结果帖 | [日历](https://x.com/eWhispers/status/2118050440197644547) |

## 后续走势：三套可以证伪的剧本

帖文没有给周四的收盘点位。抓取结束时现货没开。周三已经写下来的收盘，First Squawk 是标普 7,690.79、纳斯达克 25,732.53、道指 53,357.52，MarketWatch 是 7,688.62、25,736.51、53,356.12。下面三套的顺序，以指数收盘大涨、WTI 结算 88.12、布伦特结算 94.62、黄金标题仍在 4,100 上方、高通盘后 -6%、CoreWeave 被写成下跌将近 10% 为前提。

**网格锁和油价回落留到周四的现货。** 触发器已经写在周三收盘：道指涨约 3%，标普涨约 1.6%，收益率综述下跌 7 个基点，布伦特结算 94.62，夜里 93.61，并在 93.40 被拒绝了两次。Kobeissi 把隔夜先跌写成空头陷阱。华尔街交易台的标题是选举前仓位下降之后，有空间做年底上涨。这条路径失败的条件，是现货不接受这张收盘，SPY 掉回 RedDog 的 762 下方并走向 SpotGamma 的 7,600 风险枢轴，或者布伦特从 93.61 回到盘前的 103、或重新站上 100，同时 10 年期从 4.88% 回到 Gary 盘前的 4.92% 之上、并靠近 Yardeni 说的大约 5%。

**指数的涨幅盖不住数据中心和半导体。** 触发器是费城半导体在纳斯达克上涨时有 25 只成分下跌、16:29 UTC 超过 -4%，CoreWeave 将近 -10% 且债券到 78，英特尔被写成低于最低卖方目标价，Steno 说半导体被定价成 2027 年中芯片销售腰斩，高通盘后 -6%。RenMac 把选举写成油价战争结束和数据中心斗争开始是同一件事。这条路径失败的条件，是高通 -6% 的盘后跌幅在现货里被买回去，费城半导体不再延续那张超过 -4% 的句子，而且 Keith 做空的 QQQ、做空的工业和已经离开的科技，在开盘后不再弱于他做多的医疗和必需消费。

**霍尔木兹决定黄金是跟着选举走，还是跟着油轮走。** 触发器是结算已经把战争溢价拿掉一大截，但周四早上革命卫队和伊朗海军写下起火和触雷，Kobeissi 引 Axios 写重大作战的准备还在做，Hanke 仍写海峡实际上关闭。Ole 把贵金属写成选举和更低收益率的赢家，同时把布伦特的 93.40 写成支撑。它失败的条件，是布伦特从 93.61 回到 100 上方，同时黄金从 4,100 上方退回 4,063 甚至 4,035.85；或者反过来，布伦特留在 93.40 下方、黄金继续站在 4,134.67 那一侧，那就是选举和收益率盖过了海峡的新句子。

另有一张 ADP，不并进上面三套。10 月私人就业增加 86,000。估计有 67,000 和 69,000 两句，前值有 90,000 和 86,000 两句。ISM 服务业是 54.5，标普全球服务业终值是 56.1。周五的就业报告才是下一张劳动市场的帖，抓取结束时还没有数字。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周四开盘、周四开盘前那一批财报，以及周五的就业报告。它不决定仓位大小。现货还没开。

**开盘前只核对五样东西。** 期货是停在“大涨之后变动不大”、纳斯达克期货落后的那一侧，还是重新去交易隔夜曾经有过的下跌近 100 点；油价交易的是布伦特结算 94.62、夜里的 93.61 和 93.40，还是回到 100 或 103，87.07 是 WTI 夜里的句子，88.12 是结算；黄金是停在 4,100 上方，还是退回 4,063 和 4,035.85，以及它是否还按 Ole 的映射跟更低的收益率走；科技是继续费城半导体超过 -4% 和高通盘后 -6%，还是把苹果收盘亮点里的 +5.3%、微软的 +6.7% 留在现货里；美国 10 年期是留在 4.88%，还是回到 4.92%，或者走到 Yardeni 说的大约 5%。五样里油价留在 94.62 下方、黄金守住 4,100、SPY 留在 762 上方，这些帖给出的默认顺序是选举之后的收益率回落，高于去追已经在数据中心标题里下跌的 neocloud。海峡被交易成破裂、布伦特回到 100 上方、标普期货重新掉向 7,600，默认顺序掉过头来：原油和黄金的反向映射，高于追涨那 3% 的道指。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：隔夜下跌是空头陷阱，道指开盘涨超 1,100 点：[陷阱](https://x.com/KobeissiLetter/status/2117968023474872708)、[开盘](https://x.com/KobeissiLetter/status/2117989202151576061)。盘中另有标普 +1.7%、道指 +2.4%、纳斯达克 100 +2.0%：[帖](https://x.com/KobeissiLetter/status/2117993673174532144)。周四凌晨引 Axios，写可能恢复对伊朗的重大作战准备：[帖](https://x.com/KobeissiLetter/status/2118179324050260254)。他们没有给周四的收盘点位。
- Liz Ann Sonders：ADP +86,000 对估计 +67,000、前值 +86,000：[帖](https://x.com/LizAnnSonders/status/2117974766594253252)。ISM 服务业 54.5：[帖](https://x.com/LizAnnSonders/status/2117999867943420228)。
- Peter Schiff：黄金夜里再涨 55 美元、站上 4,100，白银站上 52.50，并写现在就买：[帖](https://x.com/PeterSchiff/status/2118155528786579941)。
- Steve Hanke：11 月 3 日霍尔木兹是 1 艘对去年的 37 艘，海峡实际上关闭：[帖](https://x.com/steve_hanke/status/2118121110902604055)。
- Charlie Bilello：美联储、欧洲央行、日本央行、英国央行年底前还会加息：[帖](https://x.com/charliebilello/status/2118163522731298958)。
- Mark Minervini：民主党的胜面超出市场此前的预期，赢到了传统上稳固的共和党州和选区：[帖](https://x.com/markminervini/status/2117997414422335667)。没有新的指数点位。
- Keith McCullough：做多医疗和必需消费，做空工业，离开科技；QQQ 隐含波动率 18% 之后做空一部分：[板块](https://x.com/KeithMcCullough/status/2118283615666901219)、[空 QQQ](https://x.com/KeithMcCullough/status/2118284965062594653)。黄金只在上涨的时候持有，不在下跌里抄底：[帖](https://x.com/KeithMcCullough/status/2118149864622321756)。
- Michael Gayed：高收益 OAS 截至 11 月 2 日是 343 个基点，12 个月低点 260，十年均值 383：[帖](https://x.com/leadlagreport/status/2117991630233886962)。这是周一的读数，不是周三收盘。
- First Squawk，线外：开盘和收盘点位、WTI 88.12、布伦特 94.62、夜里的 87.07 和 93.61、黄金 4,063 和 4,134.67，见上。
- Ole Hansen，线外：贵金属是选举之后的赢家；布伦特 200 日均线 93.40 被拒绝两次；等权标普创出新高：[贵金属](https://x.com/Ole_S_Hansen/status/2118232756085731673)、[93.40](https://x.com/Ole_S_Hansen/status/2118278162631024792)、[等权](https://x.com/Ole_S_Hansen/status/2118252615016353898)。
- Robin Brooks，线外：布伦特 12:45 UTC 写成 102，从 118 下来：[帖](https://x.com/robin_j_brooks/status/2117961396583280975)。17:03 UTC 写成 95、较周五 -10%，高油价是风险溢价：[帖](https://x.com/robin_j_brooks/status/2118026446656708801)。
- Andreas Steno，线外：半导体被定价成 2027 年中芯片销售腰斩，韩国出货 +200%：[帖](https://x.com/AndreasSteno/status/2118251986105565212)。
- Ryan Detrick，线外：67 只新高对 3 只新低；站上 50 日均线的比例从 20% 到将近 72%；远期每股收益从年初的 308 美元到 411 美元，+33.2%：[新高](https://x.com/RyanDetrick/status/2118175302144737573)、[72%](https://x.com/RyanDetrick/status/2118174649900990960)、[411](https://x.com/RyanDetrick/status/2118182885899313375)。
- Bespoke，线外：纳斯达克涨的时候费城半导体在跌，16:29 UTC 超过 -4.0%。
- SpotGamma，线外：风险枢轴 7,600，上方 7,700；CoreWeave 和 Marvell 较周二收盘 -9% 到 -11%，QQQ 波动率掉 4.5 个点。
- RedDog，线外：762、769、774。隔夜跌近 100 点之后，早上的指示是 SPY 高出约 8 美元。
- Gary Black，线外：盘前标普期货 +0.7%、纳斯达克期货 +0.6%、布伦特 103、10 年期 4.92%。Uber 的 +7% 和彭博摘录里的盘前 +0.7% 写在同一帖。
- Yardeni，线外：道指创出 40 年来最好的中期选举之后涨幅，正文在会员墙后面：[帖](https://x.com/yardeni/status/2118207182160224422)。10 年期大约 5% 有吸引力，是彭博的转述：[帖](https://x.com/business/status/2118262057648689546)。
- RenMac，线外：劳动力市场在变好，加息仍在眼前；选举同时定价了油价战争的结束和数据中心斗争的开始。
- Gundlach，线外：可负担性如果变成再发钱，会制造更多通胀。
- Cem Karsan，线外：特朗普和美联储的看跌期权被调低，左尾更肥。

**财报和数据的顺序。** 先看已经写进标题的高通、Arm、AppLovin、Snap，以及苹果、微软、亚马逊沿途的涨幅。高通要同时对上 104.4 亿和 103.2 亿、103.3 亿，以及盘后 -6%。然后才是还没公布的周四开盘前名单，以及周五的就业报告。ADP 的 86,000 已经出来。ISM 的 54.5 和标普全球的 56.1 已经出来。抓取结束时，非农还没有数字，英国央行加到 4% 也还是一篇决定之前的报道。

**明确留在观察、不放进计划的东西。** 不用还没开出的周四现货去倒推收盘，也不把开盘的 +1.14% 写成收盘。7,655.43 是开盘。7,690.79 和 7,688.62 是两张收盘。WTI 结算 88.12 和 93.25、88.56、87.07 并列。布伦特结算 94.62 和 103、95.12、93.61、93.40 并列。黄金的 4,035.85、4,063、4,098.29、4,134.67 并列。苹果的五句涨幅并列。Uber 的三种估计并列。高通的三种收入并列。ADP 的两种预期、两种前值并列。法国国债 4.80% 和英国国债 5.143% 不是美国 10 年期。欧元区生产者价格 11.1% 不是美国 CPI。德意志银行的时间线没有读到。Cathie Wood、Ray Dalio 的主号、Bill Ackman 的主号这个窗口没有新的指数点位。Bill Ackman 窗口里有帖，但没有目标价。Paul Krugman、Nouriel Roubini、Warren Buffett 这次没有可引用的新点位。

## 帖文索引

收盘和开盘：[道指 53,357.52](https://x.com/FirstSquawk/status/2118088661451649064)、[标普 7,690.79](https://x.com/FirstSquawk/status/2118088643097366638)、[纳斯达克 25,732.53](https://x.com/FirstSquawk/status/2118088576135241870)、[另一张收盘](https://x.com/MarketWatch/status/2118094828055711913)、[开盘 7,655.43](https://x.com/FirstSquawk/status/2117988101599764889)。

油、金和收益率：[WTI 结算 88.12](https://x.com/FirstSquawk/status/2118063632257036562)、[布伦特结算 94.62](https://x.com/financialjuice/status/2118066891197677797)、[布伦特 93.61](https://x.com/FirstSquawk/status/2118157397659435260)、[黄金 4,063](https://x.com/FirstSquawk/status/2118095096226938929)、[黄金 4,134.67](https://x.com/FirstSquawk/status/2118164702194970668)、[10 年期 4.88%](https://x.com/FirstSquawk/status/2118140486049480749)。

海峡和高通：[可能恢复作战](https://x.com/KobeissiLetter/status/2118179324050260254)、[油轮起火](https://x.com/financialjuice/status/2118193363706888462)、[触雷](https://x.com/FirstSquawk/status/2118285995158413447)、[高通业绩](https://x.com/financialjuice/status/2118086103567565126)、[盘后 -6%](https://x.com/TrendSpider/status/2118087264588705810)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-05 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 290 条、彭博商业账号 326 条、《金融时报》49 条、《华尔街日报》38 条、《经济学人》90 条、零对冲 48 条、FinancialJuice 217 条、CNBC 86 条、《The Street》72 条、DeItaone 50 条、StockMKTNewz 47 条、Axios 45 条，是读穿窗口后的计数。德意志银行的 0 是读取失败。保罗·克鲁格曼、Cathie Wood、BBC Business、markets、沃伦·巴菲特、CNN Business、彭博主号、Andrew Ross Sorkin、高盛、Lyn Alden、贝莱德、Downtown、美国银行、TradingView、纽约时报商业、摩根大通、花旗、Hindenburg、美国证交会、Bloomberg Economics、Jim Bianco、CNBC Now、Morgan Housel、Nouriel、Carl Icahn 的 0，是窗口内没有新帖。线外的 First Squawk 是 269 条，不在这张表里。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,448,907 | 290 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,324,371 | 90 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,276,230 | 38 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,314,235 | 37 |
| 5 | [@business](https://x.com/business) | 10,489,856 | 326 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,567,391 | 7 |
| 7 | [@FT](https://x.com/FT) | 7,112,160 | 49 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,256,322 | 86 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,385,943 | 6 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,648,016 | 48 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,596,719 | 3 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,428,227 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,355,314 | 51 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,431,313 | 48 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,424,821 | 14 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,044,560 | 3 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,002,511 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,713,863 | 20 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,564,901 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,524,819 | 6 |
| 21 | [@chamath](https://x.com/chamath) | 2,484,908 | 2 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,437,676 | 7 |
| 23 | [@BW](https://x.com/BW) | 2,288,327 | 5 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,392 | 28 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,157,513 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,129,458 | 1 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,077,850 | 24 |
| 28 | [@markets](https://x.com/markets) | 2,048,171 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,969,851 | 50 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,794,865 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,775,694 | 18 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,796 | 43 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,709,796 | 6 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,700,758 | 8 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,715 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,615,026 | 24 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,602,214 | 1 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,536,302 | 14 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,512,130 | 3 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,470,971 | 15 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,638 | 2 |
| 42 | [@Bloomberg](https://x.com/Bloomberg) | 1,355,464 | 0 |
| 43 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,355,181 | 5 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,250,222 | 5 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,226,070 | 72 |
| 46 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,194,004 | 10 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,193,733 | 4 |
| 48 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,189,920 | 0 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,185,135 | 7 |
| 50 | [@USTreasury](https://x.com/USTreasury) | 1,165,819 | 1 |
| 51 | [@nntaleb](https://x.com/nntaleb) | 1,164,876 | 2 |
| 52 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,160,217 | 47 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,157,215 | 0 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,153,430 | 3 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,140,755 | 0 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,117,268 | 5 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,109,595 | 24 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,097,069 | 5 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,081,659 | 0 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,065,659 | 9 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,420 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,597 | 35 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,003,825 | 1 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 955,714 | 217 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,087 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 934,908 | 11 |
| 67 | [@tradingview](https://x.com/tradingview) | 906,881 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 894,088 | 15 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 890,676 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,508 | 16 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 873,625 | 4 |
| 72 | [@axios](https://x.com/axios) | 862,844 | 45 |
| 73 | [@steve_hanke](https://x.com/steve_hanke) | 862,120 | 36 |
| 74 | [@jpmorgan](https://x.com/jpmorgan) | 860,474 | 0 |
| 75 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 858,547 | 19 |
| 76 | [@Citi](https://x.com/Citi) | 853,177 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 847,941 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,639 | 2 |
| 79 | [@ecb](https://x.com/ecb) | 830,655 | 6 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,344 | 1 |
| 81 | [@bgurley](https://x.com/bgurley) | 812,013 | 1 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,324 | 0 |
| 83 | [@economics](https://x.com/economics) | 806,469 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 790,317 | 0 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,254 | 4 |
| 86 | [@leadlagreport](https://x.com/leadlagreport) | 769,428 | 13 |
| 87 | [@markminervini](https://x.com/markminervini) | 767,798 | 4 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 758,742 | 1 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,743 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 734,690 | 0 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 718,719 | 38 |
| 92 | [@CMEGroup](https://x.com/CMEGroup) | 712,171 | 1 |
| 93 | [@Nouriel](https://x.com/Nouriel) | 708,264 | 0 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 674,004 | 7 |
| 95 | [@amitisinvesting](https://x.com/amitisinvesting) | 673,109 | 5 |
| 96 | [@fundstrat](https://x.com/fundstrat) | 672,953 | 12 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,527 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,645 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 637,096 | 3 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 627,108 | 3 |
