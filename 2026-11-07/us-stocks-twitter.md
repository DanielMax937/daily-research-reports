# 美股 Twitter 观点日报 · 2026-11-07

周五现货已经走完，周六现货不开。抓取结束时美东大约 5:30。开盘有点位，收盘帖只有百分比。非农是大超，但“预期是多少”有好几套，不能并成一个数。油价结算几乎走平，和本周大跌的句子不是同一张。这是公开帖文的整理，不是投资建议。

下面每一条归纳都附有帖文链接。

## 抓取口径

- 报告日期按北京时间 **2026-11-07**。触发时刻约 10:02 UTC，时间线补抓到 **约 10:30 UTC（北京时间 18:30，美东 5:30）**。美国夏令时已经结束。美股现货周六不开。股指期货要到周日美东 18:00 才重新开，这个窗口里没有周日晚间期货。
- 观察窗口从 **2026-11-06 10:19 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周五凌晨的盘前、8:30 的就业报告、周五现货全天、收盘和盘后，以及美东周六凌晨到大约 5:30。上一份日报里的周四收盘不在这里重算。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。抓取开始时，未加地区、美国地区和全球趋势都是 Usher、Schumer、Stephen Miller、Susie Wiles、Chief of Staff，另有 `#RTXON`。抓取结束时 `#RTXON` 不在名单里，出现过 Arizona。里面没有被这些账号解释过的美股代码。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。
- 不存在官方的“美股 Top 100”。这次试了 **739** 个候选，成功读到粉丝数的有 **620** 个。排序时拿掉加密货币账号、综合新闻主号、科技风投和创始人、大型科技公司首席执行官、竞选和政治账号、公司产品品牌、大学和智库，以及简介对不上的错人号。`@DanielNewman` 仍是漫威演员，`@SEC` 仍是东南联盟，`@goldman` 仍不是高盛，`@robinbrooks` 只有十几个粉丝。拉加德和格奥尔基耶娃的个人号这次也拿掉，因为欧洲央行和国际货币基金组织的机构号已经在名单里。福布斯科技号、两个讽刺号，以及和经济学家罗森伯格无关的 `@Rosie`，同样不拿来抬高截止线。用来排序的账号是 **513** 个，截止在 Eric Balchunas（626,660）。Morning Brew（593,712）落到第 101。Bloomberg Opinion 第 102。Gary Black 第 103。Cboe 第 104。Barchart 第 105。First Squawk（576,802）第 106。dampedspring、Gundlach、Earnings Whispers、LiveSquawk、瑞银、Nick Timiraos、日经亚洲、Keith McCullough、Fxhedgers、MacroAlf、Traderstewie、The Stalwart、Hedgeye、巴伦、Javier Blas、Robin Brooks、Bespoke、SpotGamma、The Transcript、firstadopter、Ryan Detrick、Yardeni、RenMac、RedDog、Benzinga、Seeking Alpha、Newsquawk 落在线外，引用时会写明。排序不代表预测准确度。前 100 的账号集合和 11 月 6 日那份相同。名次变了的是：彭博主号到了 Peter Brandt 前面，StockMKTNewz 到了美国财政部和塔勒布前面，Liz Ann Sonders 到了摩根大通前面，amit 到了 Tom Lee 前面。
- 100 个账号里，**77 个**在窗口内有按帖文链接去重后、且接口没有标成回复的原创帖。路透读穿窗口，212 条。彭博商业账号读穿窗口，293 条。《金融时报》64 条。《华尔街日报》76 条。《经济学人》94 条。零对冲 96 条。FinancialJuice 读穿窗口，230 条。CNBC 61 条。《The Street》72 条。DeItaone 69 条。StockMKTNewz 35 条。unusual_whales 40 条。线外的 First Squawk 读穿窗口，原创 157 条。LiveSquawk 读穿窗口，原创 72 条。德意志银行的时间线返回错误，表里的 0 不是确认沉默。保罗·克鲁格曼、BBC Business、彭博 markets、沃伦·巴菲特、CNN Business、彭博主号、Peter Brandt、Andrew Ross Sorkin、塔勒布、Lyn Alden、Downtown、美国银行、TradingView、纽约时报商业、花旗、Hindenburg、美国证交会、Bloomberg Economics、Jim Bianco、CNBC Now、Nouriel Roubini、Carl Icahn 的 0，是可见时间线在窗口内没有计为原创的新帖。Gundlach 和 David Rosenberg 的主号这次也是 0。

## 周五开盘有点位，收盘只有百分比

开盘是 First Squawk 14:32 UTC 的一张帖。道指跌 486.37 点，或 0.94%，到 51,036.69。标普 500 涨 19.44 点，或 0.26%，到 7,373.17。纳斯达克涨 299.54 点，或 1.23%，到 24,614.53：[开盘三条写在同一帖](https://x.com/FirstSquawk/status/2118713036857102433)。这张是开盘，不是收盘。上一份日报里的周四收盘，纳斯达克 24,305.70、标普 7,355.81、道指 51,515.81，不在这里重算，也不拿来和这张开盘轧差。

盘前已经是反弹，而且各账号的百分比不一样。线外的 Gary Black 10:26 UTC：标普 +0.2%，纳斯达克 +1.2%，布伦特在他写的 -1.4% 之后到 97 美元，10 年期 4.84%：[帖](https://x.com/garyblack00/status/2118651214636220583)。DeItaone 11:01 UTC：半导体 ETF 盘前接近 +5%，纳斯达克 100 期货 +1.3%；Lam Research +9%，美光 +7.5%，Marvell +7%，AMD 和 Applied Materials +6%，CoreWeave 反弹 6.3%：[帖](https://x.com/DeItaone/status/2118660143885783134)。11:57 UTC 他又换成另一张：美光 +9.2%，AMD +8.3%，Arm +7.4%，英特尔 +6.2%，英伟达 +5.0%，博通 +4.9%，高通 +3.4%，SOXX +5.9%：[帖](https://x.com/DeItaone/status/2118674223438709214)。Kobeissi 12:49 UTC 的盘前名单又是一张，并写成芯片当天已经收回 5,000 亿美元市值：SanDisk +12%，Marvell +10%，美光 +9%，AMD +8%，Arm +7%，英特尔 +6%，超微 +6%，英伟达 +5%，博通 +5%，高通 +3%：[帖](https://x.com/KobeissiLetter/status/2118687090435137597)。零对冲 12:47 UTC 同一篇里写了两套：七巨头里英伟达 +4%、特斯拉 +1.7%、Alphabet -0.1%、Meta 大约持平、苹果 -1.2%、亚马逊 -0.8%、微软 -0.7%；后面美光先写 +8% 再写 +7.8%，AMD 先写 +8% 再写 +7.1%，英特尔先写 +6% 再写 +4.7%，博通 +4.4%：[帖](https://x.com/zerohedge/status/2118686600410329595)。这些都是盘前，不要拿去替换开盘点位，也不要合成一张“芯片涨了多少”。

盘中的指数百分比继续换。First Squawk 14:43 UTC：纳斯达克 100 涨 2%，标普涨 0.8%：[帖](https://x.com/FirstSquawk/status/2118715986295890369)。Kobeissi 14:48 UTC：纳斯达克 100 涨幅扩到 +2.4%，开盘时芯片又写成接近多收回 6,000 亿美元：[帖](https://x.com/KobeissiLetter/status/2118717121354232120)。+1.23% 是开盘那张里的纳斯达克。+1.2% 是 Gary 的盘前期货。+1.3% 是 DeItaone 的纳斯达克 100 期货。+2% 和 +2.4% 是盘中的纳斯达克 100。5,000 亿和 6,000 亿是两句。

收盘没有一张带点位的帖。CNBC 21:03 UTC 的一条被接口标成回复：纳斯达克综合指数反弹 1.09%，标普涨 0.3%，道指跌 237 点，或 0.5%：[帖](https://x.com/CNBC/status/2118811613352337911)。线外的 Keith McCullough 21:15 UTC 把 SPY 当天的反弹写成 +0.3%：[帖](https://x.com/KeithMcCullough/status/2118814613378601093)。Seeking Alpha 的标题是纳斯达克上涨 1%，指数本周损失很大：[帖](https://x.com/SeekingAlpha/status/2118849666154737685)。Investing.com：美股收盘多数上涨，但在周四大跌之后记下周线损失：[帖](https://x.com/Investingcom/status/2118818529591857359)。MarketWatch 的标题是美股收盘多数上涨，周四深跌之后记下周线损失：[帖](https://x.com/MarketWatch/status/2118812045135012152)。路透周六的标题是纳斯达克反弹，但连续第四周下跌：[帖](https://x.com/Reuters/status/2118939026593915087)。StockMKTNewz：标普刚经历 2025 年 4 月以来最大的周线跌幅，纳斯达克连续第四周下跌：[帖](https://x.com/StockMKTNewz/status/2118817733194440861)。1.09%、1%、0.3%、道指 -237 点或 -0.5%，按账号留着。没有人在这个窗口里写出周五的收盘点位。开盘的 24,614.53、7,373.17、51,036.69 不能改写成收盘。

“本周”和“周四”也不要并。线外的 SpotGamma 把周四标普写成 -4.36%，并写成 2011 年以来、除去新冠和 2025 年 4 月关税冲击之外最差的一天：[帖](https://x.com/spotgamma/status/2118832058436825171)。上一份日报里的周四句子是 4.33% 和 4.4%。4.36% 是他这一帖的句子。

## 非农是 165,000，预期有四套，加息概率有三套

就业报告在 13:30 UTC 前后出来。人数本身各家都写成 165,000，失业率都写成 4.1%。预期和修正的口径不要并。

First Squawk：非农 165,000，前值 29,000，估计 70,000；失业率 4.1%，前值 4.2%，估计 4.2%：[非农](https://x.com/FirstSquawk/status/2118697999228702850)、[失业率](https://x.com/FirstSquawk/status/2118697938553811089)。FinancialJuice 同一套：非农 165,000，预期 70,000，前值 29,000；失业率 4.1%，预期 4.2%，前值 4.2%；私人非农 159,000，预期 65,000，前值 46,000；制造业就业 19,000，预期 7,000，前值 9,000：[非农](https://x.com/financialjuice/status/2118697639390962092)、[失业率](https://x.com/financialjuice/status/2118697651885547897)、[私人](https://x.com/financialjuice/status/2118697690645045719)、[制造业](https://x.com/financialjuice/status/2118697717668909142)。LiveSquawk 的结果帖把前值修过：非农 165,000，估计 70,000，前值 29,000，修正前值 60,000；失业率 4.1%，估计 4.2%，前值 4.2%；时薪环比 0.4%，估计 0.3%，前值 0.1%，修正前值 0.3%；时薪同比 3.1%，估计 2.9%，前值 3.0%，修正前值 3.2%：[帖](https://x.com/LiveSquawk/status/2118698626524627191)。同一分钟的明细还有：制造业就业 19,000，估计 7,000，前值 9,000，修正前值 13,000；私人非农 159,000，估计 65,000，前值 46,000，修正前值 78,000；政府就业 6,000，前值 -17,000；参与率 61.9%，估计 61.8%，前值 61.8%；不完全就业率 7.9%，估计 7.6%，前值 7.6%；三个月平均新增 137,000，前值 51,000，修正前值 79,000；两个月净修正 +84,000，前值 -60,000：[帖](https://x.com/LiveSquawk/status/2118698049627177050)。零对冲：非农 165,000，预期 70,000，上月从 29,000 上修到 60,000；失业率 4.1%，预期 4.2%，9 月 4.2%：[非农](https://x.com/zerohedge/status/2118697522353045622)、[失业率](https://x.com/zerohedge/status/2118697969474310358)。他又写成 5 个标准差的超预期：[帖](https://x.com/zerohedge/status/2118700399863476392)。

Liz Ann Sonders 和 El-Erian 用的估计也是 70,000。Liz Ann：失业率 4.1%，估计 4.2%，前月 4.2%；非农 +165,000，估计 +70,000，前月 +60,000，从 29,000 上修；时薪环比 +0.4%，估计 +0.3%，前值从 +0.1% 上修到 +0.3%；同比 +3.1%，估计 +2.9%，前月 3.2%；工时 34.4 不变；两个月净修正 +84,000；参与率升到 61.9%：[失业率](https://x.com/LizAnnSonders/status/2118698026151608511)、[非农](https://x.com/LizAnnSonders/status/2118698591745397032)、[时薪环比](https://x.com/LizAnnSonders/status/2118698691708289170)、[时薪同比](https://x.com/LizAnnSonders/status/2118698771349442674)、[工时](https://x.com/LizAnnSonders/status/2118699053189853512)、[两个月](https://x.com/LizAnnSonders/status/2118699449950347312)、[参与率](https://x.com/LizAnnSonders/status/2118700264333128060)。她另写，失业超过 27 周的比例 27.6%，前值 27.1%；临时裁员的失业人数 766,000，永久性失业 1,733,000：[长期失业](https://x.com/LizAnnSonders/status/2118699347156389942)、[裁员结构](https://x.com/LizAnnSonders/status/2118699232135991551)。El-Erian 在数据出来之前把共识写成非农 70,000、失业率维持 4.2%、参与率 61.8%、时薪环比 +0.3%、同比 +2.9%：[共识](https://x.com/elerianm/status/2118681696547606631)。出来之后他写成全面偏强，两个月净上修 +84,000，失业率 4.1%，时薪环比 +0.4%，参与率 61.9%：[结果](https://x.com/elerianm/status/2118701008746410301)。

另外三套预期不要改成 70,000。DeItaone 的叙述帖把预期写成 59,000，并写成将近三倍：非农 +165,000 对 +59,000，失业率 4.1% 对 4.2%，私人 +159,000，时薪在这一帖里是月环比 +0.37%、年率 +3.12%，9 月非农上修到 +60,000：[59,000](https://x.com/DeItaone/status/2118697658403467340)。他下一分钟的通讯社格式又写成估计 +70,000，两个月净修正 +84,000：[70,000](https://x.com/DeItaone/status/2118697834530967845)。59,000 和 70,000 都是他的帖。更完整的一帖把时薪写成月环比 +0.4%、年率 +3.1%，政府就业 +6,000，参与率 61.9%，工时 34.4，并写因经济原因做兼职的人增加 339,000，到 480 万：[明细](https://x.com/DeItaone/status/2118698896855593031)。0.37% 和 0.4%、3.12% 和 3.1%，并列。Kobeissi 把预期写成 +64,000，并写比预期多 100,000；9 月他写成上修 31,000；12 月加息预期在这条里是上升：[64,000](https://x.com/KobeissiLetter/status/2118698893210763689)、[多 10 万](https://x.com/KobeissiLetter/status/2118705205864988781)。31,000 和“从 29,000 上修到 60,000”是同一件 9 月的事。+84,000 是两个月，不是 9 月单月。Gary 盘前写的预期是 +65,000，那是数据出来之前。StockMKTNewz 把 165,000 写成低于 +65,000 的预期：[帖](https://x.com/StockMKTNewz/status/2118697591713960044)。这句话和他前后其他账号的“大超”方向相反，按原文留着，不改成超预期。

Nick Timiraos 的失业率精度是另一句。他写 10 月非农 +165,000，8 月和 9 月合计上修 +84,000，失业率下降 0.03 个百分点，到 4.14%：[帖](https://x.com/NickTimiraos/status/2118697935596646759)。4.14% 是他的句子。4.1% 是通讯社标题。他又写，怎么切，非农都是在夏天接近停滞后重新加快：[帖](https://x.com/NickTimiraos/status/2118700625932198024)。

12 月加息概率有三套，都是数据出来之后的句子。DeItaone：预测市场把 12 月加息写成 79%，前一天 67%，按住的概率退到 22%：[帖](https://x.com/DeItaone/status/2118699348485685271)。Kobeissi：再加 25 个基点的预期升到 80% 的新高：[帖](https://x.com/KobeissiLetter/status/2118705205864988781)。Liz Ann：芝商所 FedWatch 从 67% 升到 77%，升了 10 个百分点：[帖](https://x.com/LizAnnSonders/status/2118789205052846511)。79%、80%、77% 并列。67% 是升之前的句子。22% 只出现在 DeItaone 的“按住”。

官员和经济学家对这份报告的读法也不一样。First Squawk 引旧金山联储的 Daly：就业报告对美国工人是好消息：[帖](https://x.com/FirstSquawk/status/2118766619694596398)。DeItaone 把她写成欢迎强就业，但工资增长并不猛、实际工资在下降，通胀已经高得太久：[帖](https://x.com/DeItaone/status/2118766805418123390)。StockMKTNewz 引路透，把她写成还可能继续收紧，通胀是第一优先，9 月的加息是对的，上次按住也是对的，就业是好消息，但人工智能抛售到目前为止是有序的：[帖](https://x.com/StockMKTNewz/status/2118779730027786331)。“好消息”“实际工资在下降”“还要收紧”三句都在，不要只留一句。白宫经济顾问委员会的 Phelan 是另一个人。LiveSquawk：不要预期强就业会让美联储加息，要看下一份 CPI：[帖](https://x.com/LiveSquawk/status/2118772327903117678)。高盛自己的账号引 Jan Hatzius：强于预期的就业说明劳动力市场稳定，没有在这条里给加息概率：[帖](https://x.com/GoldmanSachs/status/2118840998583230659)。线外的 Keith 在数据之前引 Williams：通胀太高，必须及时拉回 2%：[帖](https://x.com/KeithMcCullough/status/2118652343143030895)。财政部长 Bessent 的句子是另一张时间尺度：过去三个月私人部门创造了将近 40 万个岗位，2026 年制造业就业已经增加超过 10 万：[帖](https://x.com/SecScottBessent/status/2118744781769658655)。将近 40 万是三个月。159,000 是 10 月私人非农。19,000 是 10 月制造业。超过 10 万是他写的 2026 年累计。

密歇根大学和加拿大是另外两张已经公布的数。LiveSquawk：11 月密歇根情绪初值 51.0，估计 48.0，前值 48.0；现状 51.0，估计 47.0，前值 46.7；预期 50.9，估计 49.0，前值 48.8；一年通胀预期 4.3%，估计 4.6%，前值 4.7%；五到十年 3.4%，估计 3.5%，前值 3.5%：[帖](https://x.com/LiveSquawk/status/2118720327849005519)。零对冲和 Liz Ann 是同一套数：[零对冲](https://x.com/zerohedge/status/2118720500494897489)、[Liz Ann 情绪](https://x.com/LizAnnSonders/status/2118739039801282616)、[Liz Ann 通胀预期](https://x.com/LizAnnSonders/status/2118739175457583280)。加拿大：就业 -4,700，估计 +15,000，前值 -68,300；失业率 6.7%，估计 6.5%，前值 6.5%；全职 -18,100；兼职 +13,400；永久雇员时薪 2.0%，估计 2.1%，前值 2.3%：[帖](https://x.com/LiveSquawk/status/2118698074323243282)。First Squawk 周六又引 CNBC，失业率升到 6.7%、失去 4,700 个岗位：[帖](https://x.com/FirstSquawk/status/2118924519008313835)。这是加拿大，不是美国的 4.1%。

美联储自己的账号没有利率决定。它公布的是消费者信贷：三季度环比年率 +4.2%，循环信贷 +4.1%，非循环 +4.2%，9 月消费者信贷 +6.4%：[帖](https://x.com/federalreserve/status/2118796957158126043)。线外的 Hedgeye 用的是另一套单位：9 月消费者信贷增加 278 亿美元，大约是 120 亿美元预期的两倍多；同一帖把实际可支配收入写成 -0.3%，储蓄率 3.8%，单月 PCE +0.5%，CPI 同比 3.7%，信用卡平均利率 22.36%：[帖](https://x.com/Hedgeye/status/2118799122425639047)。6.4% 是美联储的年率。278 亿美元是 Hedgeye 的金额。不把两句换算成彼此。

Kobeissi 还有一张 9 月职位空缺，窗口里的通讯社帖没有另一张同样的数字。他写职位空缺增加 333,000，到 752 万，专业和商业服务 +106,000，州和地方政府（不含教育）+104,000，空缺与失业人数之比 1.06，空缺比失业多 414,000：[帖](https://x.com/KobeissiLetter/status/2118786224202584387)。这是他的帖，不当成已经有第二来源的官方标题。

## 观点分成四组

### 1. 强就业把 12 月加息拉回来，但“会不会加”仍是两套

数据出来之后，利率的方向在交易员的帖里是向上。DeItaone：10 年期收益率上涨 6.3 个基点，到 4.898%：[帖](https://x.com/DeItaone/status/2118698045030420941)。线外的 Robin Brooks：2 年期上涨 4 个基点，他把这写成对非农超预期的正常反应，并写市场正在看穿正在展开的人工智能泡沫破裂；美国经济很大，人工智能只是其中一小块：[帖](https://x.com/robin_j_brooks/status/2118700067083129013)。4.898% 是 10 年期。4 个基点是 2 年期。Gary 盘前的 4.84%，和收盘后他写的 4.88%，都不是这张 4.898%。他 20:01 UTC 把 2026 年标普每股收益写成 369 美元、同比 +33%，对应 19.9 倍市盈率和 5.0% 的盈利收益率，高于当时他写的 4.88% 的 10 年期；盘前那张是 368 美元和 4.84%：[收盘后](https://x.com/garyblack00/status/2118795998214680917)、[盘前](https://x.com/garyblack00/status/2118651214636220583)。368 和 369、4.84%、4.88%、4.898% 并列。

“加息”和“先看 CPI”同时存在。Daly 被 StockMKTNewz 写成还可能收紧。Phelan 被 LiveSquawk 写成不要因为这份就业就加息。Nick 把张力写成：就业数据没有理由改掉美联储对增长和通胀的解读，但人工智能抛售会不会改掉对金融条件的看法，是 12 月之前的问题；他写 Warsh 更愿意读前瞻的市场，而不是滞后的数据：[帖](https://x.com/NickTimiraos/status/2118716534260388066)。线外的 RenMac：过去三个月总周薪指数按年率飙了 6.2%，岗位、工时和时薪都在增加，美联储得盯着劳动力市场；未来几个月的主要风险是失业率下降，通胀还比目标高 1 个百分点的时候，美联储没法为市场托底：[6.2%](https://x.com/RenMacLLC/status/2118698395325866152)、[失业率](https://x.com/RenMacLLC/status/2118813250318176467)。amit 把同一份报告写成很好，但也可能让美联储觉得劳动力市场这么好只会让通胀黏着，从而加息：[帖](https://x.com/amitisinvesting/status/2118699940637466676)。

线外的 Michael Gayed 在数据出来之前写，修正会比当天的标题非农更重要：[帖](https://x.com/leadlagreport/status/2118687364109242717)。出来之后他写，2 年期已经说出了美联储不会说的增长；又写他们大概会砸股票来救债券：[2 年期](https://x.com/leadlagreport/status/2118758022570737793)、[砸股票](https://x.com/leadlagreport/status/2118763356106772760)。Brooks 在非农之前的另一句不要和“2 年期涨 4 个基点”合成。他 12:58 UTC 写 10 年期的 10 年远期利率是平的，短端收益率在掉，长期利率高是因为赤字，不是人工智能举债：[帖](https://x.com/robin_j_brooks/status/2118689368105755082)。“短端在掉”是数据前。“2 年期涨 4 个基点”是数据后。

### 2. 芯片的反弹被写成修复，也被写成死猫

多头这边，Gary 把周四纳斯达克 100 的 -6% 写成短视，理由是民主党会拖慢数据中心，而这个论点拿不出数字；他预期下周就不会再听到这句。英伟达在盘前那张里被写成 2027 年市盈率 20 倍，对 2027 到 2031 年收入增长 +20%、每股收益增长 +25%。Tom Lee 的回复把人工智能和科技公司写成挨过了新冠、2022 年最快的加息、2025 年解放日、2026 年的美伊战争和这次蓝色浪潮，每一次都还是找到办法增长：[帖](https://x.com/fundstrat/status/2118759776465109347)。线外的 Yardeni 在收盘后的 Closing Bell 上说，小心的那段已经过去，市场上出现了买点：[帖](https://x.com/yardeni/status/2118820166620307733)。DeItaone 在数据前引 Yardeni Research：周四的抛售过度了，标普 -4.4%，纳斯达克 -5.5% 并进入修正，高盛称 45% 的计划中美国数据中心产能可能面临州一级限制；Yardeni 把这些障碍写成只是减速带：[帖](https://x.com/DeItaone/status/2118696360287318144)。零对冲的另一条标题把高盛写成相反方向的建设预测：蓝色浪潮之下，高盛上调数据中心建设预测，并看到支出延续到 2030 年：[帖](https://x.com/zerohedge/status/2118835933147488686)。45% 可能受限，和上调建设预测，按标题留着，不合成。

空头和交易员把同一天的反弹写成不够。Mark Minervini：只看今天，超卖之后的科技反弹很强；把早上的跳空放回图里，只是一个小波动：[帖](https://x.com/markminervini/status/2118713950179369304)。他写 VIX 到了 28.5，这是他的熊市警告位，也是很多中期修正曾经见底的区域；如果不能从这里走出像样的跟随日，波动还会继续。收盘前他又写成，到目前为止当天的上涨感觉像死猫反弹：[VIX](https://x.com/markminervini/status/2118715580840644669)、[死猫](https://x.com/markminervini/status/2118744812836819276)。28.5 是 14:42 UTC 的句子，不是收盘。线外的 Hedgeye：熊市会反弹，人群在区间下沿卖、在反弹里追；他们的过程是在低位回补一部分空头，再在反弹向上沿时重新做空：[帖](https://x.com/Hedgeye/status/2118725090829328743)。Keith 收盘后把 SPY 的 +0.3% 写成“惊人的”反弹，并写 Quad 4 才刚开始。线外的 UBS 经由 DeItaone：Gerry Fowler 警告纳斯达克期货的反弹可能是误导，趋势跟踪的量化基金股票敞口仍重，可能还要减仓；反弹反映的是稀薄期货市场里的试探性买入：[帖](https://x.com/DeItaone/status/2118682108075855989)。DeItaone 另有一张技术位，不是收盘：标普 E-mini 跌破 7,386，下行目标 7,317、7,240 和 7,176，初始阻力 7,675；超卖，但反弹被写成修正性的：[帖](https://x.com/DeItaone/status/2118663147233890561)。7,386 以下是这张期货帖。7,373.17 是现货开盘。两者不要互换。

芯片从高点算的跌幅仍在。Kobeissi：半导体指数 SOX 过去 5 个交易日 -21.8%，是 2001 年 9 月 21 日以来最大的 5 日跌幅，也是纪录上第三大；周四单日 -12.3%，是 2020 年 3 月 16 日以来最大的单日跌幅，那天是 -15.9%。三倍做多半导体的 SOXL 5 日 -60%，较高点 -86%：[帖](https://x.com/KobeissiLetter/status/2118729368977518626)。线外的 Bespoke 把 SOX 写成过去五天跌了 20% 以上，历史上只有另外五次：[帖](https://x.com/bespokeinvest/status/2118703318709252382)。-21.8% 和“20% 以上”并列。-12.3% 是 Kobeissi 的周四句子。Hedgeye 把 SOXX 的单日跌幅写成纪录上第二大，-12.5%：[帖](https://x.com/Hedgeye/status/2118761407235661959)。-12.5% 是 SOXX。-12.3% 是 SOX。上一份日报里的 -12% 不在这里改写。动量也有两句。Kobeissi：MTUM 周四 -8.2%，5 日 -16%，6 月高点以来 -27%：[帖](https://x.com/KobeissiLetter/status/2118741448422002779)。Hedgeye：高盛的高贝塔动量篮子从 6 月高点下跌超过 50%：[帖](https://x.com/Hedgeye/status/2118788007960740059)。-27% 是 MTUM。超过 50% 是高盛那只篮子。Keith 另写高贝塔动量从 +69% 到 -18%：[帖](https://x.com/KeithMcCullough/status/2118658421293744195)。+69% 到 -18% 是他的句子。

Jim Cramer 的计划是把资本从科技挪到非科技、风险更低的股票；论点被新事实打乱的时候，减仓从来减不够；如果继续下跌，他不会一直这么谨慎，尤其是非科技；如果大型的 Anthropic 交易公开、让人看到算力有多值钱，他会没那么悲观：[挪出科技](https://x.com/jimcramer/status/2118731844677943359)、[减仓](https://x.com/jimcramer/status/2118733354682208279)、[Anthropic](https://x.com/jimcramer/status/2118738823412842518)。他在年会上说自己点了一个现在会买的名字，帖文里没有写出代码。El-Erian 把周四纳斯达克写成 2020 年 3 月以来最大的抛售，并写有人急着下调 2027 年增长预测；他看成的是中枢情景的风险平衡变了，不是中枢本身被划掉：[帖](https://x.com/elerianm/status/2118679341290717459)。

### 3. 甲骨文、OpenAI 和数据中心是同一天的三件不同的事

微软和甲骨文是已经发生的公司新闻，百分比却有两句。DeItaone：微软正在结束向甲骨文租用人工智能云产能的协议，甲骨文股价跌 4%：[结束](https://x.com/DeItaone/status/2118759939720237133)、[-4%](https://x.com/DeItaone/status/2118760159162053104)。Kobeissi：甲骨文 -5%，较高点 -68%：[帖](https://x.com/KobeissiLetter/status/2118761153866482032)。-4% 和 -5% 并列。-68% 是从纪录高点算的。FinancialJuice 的解释是：租来的产能用的是较老一代英伟达芯片，不再符合微软的规格，所以近月关掉；甲骨文称人工智能基础设施的需求仍然强，9 月还说过一些四年前的 GPU 合同在以原价加 20% 续约：[帖](https://x.com/financialjuice/status/2118760114131710144)。线外的 firstadopter 把这条写成旧闻：可能是商业内幕 6 月已经写过的、给必应搜索用的 30 亿美元 A100 合同；他后来说彭博补上了商业内幕的出处：[30 亿](https://x.com/firstadopter/status/2118765086114259192)、[补出处](https://x.com/firstadopter/status/2118771176340402351)。30 亿美元是他的句子。-4% 和 -5% 是股价帖。20% 的溢价续约是 FinancialJuice 引甲骨文 9 月的话。Hedgeye 把信用违约互换写成当天早上创纪录：CoreWeave 大约 66% 的五年违约概率，甲骨文大约 22%：[帖](https://x.com/Hedgeye/status/2118775422141743423)。66% 和 22% 是互换隐含的概率，不是股价跌幅。

OpenAI 的融资在窗口里从“正在谈”变成“已经进来一部分”。First Squawk 17:08 UTC：首席财务官确认正在融资谈判，估值比 3 月那轮收高将近 50%：[帖](https://x.com/FirstSquawk/status/2118752374118547526)。20:59 UTC，FinancialJuice、LiveSquawk 和零对冲：新一轮里的 110 亿美元已经按 1.25 万亿美元估值到账：[FinancialJuice](https://x.com/financialjuice/status/2118810514210046085)、[LiveSquawk](https://x.com/LiveSquawk/status/2118810635798487463)、[零对冲](https://x.com/zerohedge/status/2118810953559241202)。StockMKTNewz 把 110 亿写成这一轮的第一笔，这一轮最多可能到 200 亿；原先要募 300 亿或更多、估值 1.4 万亿，后来缩到 200 亿、估值 1.25 万亿；剩下的 90 亿预计未来几周完成；相对 3 月那次 1,220 亿美元、估值 8,520 亿美元，新估值大约高 47%。首席财务官当天早些时候还在 CNBC 上说公司在融新的资本，并反驳缩减融资的说法：[帖](https://x.com/StockMKTNewz/status/2118812938161258659)。unusual_whales 的过程句是：一开始要超过 300 亿、估值 1.4 万亿，后来缩到 200 亿、估值 1.25 万亿，剩下 90 亿预计未来几周完成：[帖](https://x.com/unusual_whales/status/2118823339959751010)。110 亿是已经到账的。200 亿是这一轮的上限句子。300 亿或“超过 300 亿”是更早的目标。1.25 万亿是这次的估值。8,520 亿是 StockMKTNewz 写的 3 月估值。将近 50% 和大约 47% 并列。The Transcript 引首席财务官：业务环比增长 70%，企业业务翻倍，每周 12 亿人使用，其中 3 亿人用于健康，2 亿人用于个人财务，三季度的大客户包括摩根大通：[帖](https://x.com/TheTranscript_/status/2118782036643074445)。70% 是业务环比，不是融资额。

Anthropic 是另一家。unusual_whales 引彭博：潜在的上市买家现在把估值看到低至 1.1 万亿，正式路演前讨论的区间是 1.2 万亿到 1.3 万亿，周四之前是 1.4 万亿到 1.5 万亿；同一帖把周四纳斯达克 100 写成 -6.4%、抹掉创纪录的 2.3 万亿美元：[帖](https://x.com/unusual_whales/status/2118760070888796583)。1.1 万亿到 1.5 万亿是估值区间的沿途，不是已经成交的价格。-6.4% 和 2.3 万亿是他写的周四，不是周五收盘。线外的 firstadopter 把 10 月经常性收入写成 800 亿美元，并写成这会让上市继续推进：[帖](https://x.com/firstadopter/status/2118694978465501418)。800 亿美元是他的句子。Cramer 说的是交易如果公开会让人看到算力的价值，没有写 800 亿。

数据中心的政治句子也有好几张。特朗普被 FinancialJuice、LiveSquawk 和 DeItaone 写成 100% 支持超级智能，并会和想靠它变富的州合作：[FinancialJuice](https://x.com/financialjuice/status/2118675472892539141)、[LiveSquawk](https://x.com/LiveSquawk/status/2118675588143575220)、[DeItaone](https://x.com/DeItaone/status/2118675843924799641)。这和上一份日报里“暂停数据中心”的州级句子不是同一张。彭博：几十个针对人工智能基础设施的地方公投里，只有一个站在数据中心开发商一边：[帖](https://x.com/business/status/2118819475994649052)。巴伦：选举结果指向数据中心支出放慢，而这可能有助于压通胀：[帖](https://x.com/barronsonline/status/2118828002263880140)。线外的 Andreas Steno 把得州的要求写成可以谈的条件，不是结束人工智能：[帖](https://x.com/AndreasSteno/status/2118741149124804655)。阿姆斯特丹的微软工地被写成有抗议者进入。DeItaone：大约 100 人，反对人工智能基础设施扩张：[帖](https://x.com/DeItaone/status/2118663940737478699)。零对冲的标题写成气候抗议者冲进工地：[帖](https://x.com/zerohedge/status/2118760435067355246)。大约 100 人是 DeItaone 的句子。谷歌买下 Crusoe 在怀俄明的数据中心用地，LiveSquawk 写没有条款：[谷歌](https://x.com/FirstSquawk/status/2118777839466184951)、[没有条款](https://x.com/LiveSquawk/status/2118777801255829543)。台积电在为英伟达考虑 3D DRAM，FinancialJuice 引 The Information：[帖](https://x.com/financialjuice/status/2118705926953906615)。

### 4. 油价周五结算几乎没动，本周的跌幅是另一句

周五的结算是小涨。FinancialJuice、LiveSquawk、First Squawk：WTI 12 月期货每桶 90.83 美元，上涨 31 美分，涨幅 0.34%：[FinancialJuice](https://x.com/financialjuice/status/2118788382243672404)、[LiveSquawk](https://x.com/LiveSquawk/status/2118788424865849500)、[First Squawk](https://x.com/FirstSquawk/status/2118788445976113225)。布伦特结算每桶 98.32 美元，上涨 3 美分，涨幅 0.03%：[帖](https://x.com/financialjuice/status/2118790930283294899)。上一份日报的周四结算是 WTI 90.52、布伦特 98.29，不在这里重算。Gary 盘前的布伦特 97 美元、跌 1.4%，是结算前的句子。

本周的跌幅不要换成周五的 +0.34% 和 +0.03%。线外的 Ole Hansen：选举冲击之后油价因为伊朗和平的希望跌了 13%，铜受到人工智能摇摆和关税预期消退的拖累，黄金和白银上涨：[帖](https://x.com/Ole_S_Hansen/status/2118682112165302452)。零对冲的标题是布伦特创新冠崩盘以来最大的周线跌幅，特朗普和卡塔尔埃米尔在谈伊朗和平：[帖](https://x.com/zerohedge/status/2118679903503601777)。-13% 是 Ole 的周线句子。0.34% 和 0.03% 是周五结算。最大周线跌幅是标题，没有在这条里写出周线百分比。

实物和在途库存是第三张。线外的 Rory Johnston：尽管布伦特价格稳定、期货仍深度升水，现货 Dated Brent 已经低于近月期货，布伦特 CFD 曲线前半段进入贴水；实物市场目前是平衡到略微过剩：[帖](https://x.com/Rory_Johnston/status/2118774686876369111)。投机盘在截至周二的一周净卖出 7,800 万桶纸原油，是 6 月中以来最大的平仓：[帖](https://x.com/Rory_Johnston/status/2118806543856767146)。Kobeissi：全球在途原油升到 12.8 亿桶的历史新高，过去几周增加 1.8 亿桶；霍尔木兹和替代航线的中东流量在恢复，但船对船转运和更长的航程把油留在海上，近端供应因此更紧：[帖](https://x.com/KobeissiLetter/status/2118818571111612486)。“略微过剩”是实物曲线。“在途创新高、交付变紧”是 Kobeissi。7,800 万桶是一周的纸原油净卖出。彭博另写，对冲基金把看多原油的仓位削减了 6 月以来最多，赶在选举日的下跌之前：[帖](https://x.com/business/status/2118845904169861600)。7,800 万桶和“6 月以来最多”不要合成成同一个数字。

伊朗的政策句子是结束战争，不是新的通航艘数。Brooks：中期选举对伊朗是胜利，封锁的效力在消退；没有必要为了重开海峡先签和平协议，海湾国家自己能处理，美国应该走开：[封锁](https://x.com/robin_j_brooks/status/2118686350211707179)、[走开](https://x.com/robin_j_brooks/status/2118836059165561189)。FinancialJuice 周六仍有一句军事帖：伊朗军方称在格什姆岛上空打下美国 MQ-9 无人机：[帖](https://x.com/financialjuice/status/2118841718120321107)。结束战争的建议，和打下无人机，按原文并列。

黄金没有跟着油价的周五结算走成同一句。中国央行的美元金额下降、盎司上升。First Squawk 和 FinancialJuice：黄金储备 3,064.1 亿美元，9 月底是 3,235.2 亿美元；持有量 7,830 万金衡盎司，FinancialJuice 写 9 月是 7,747 万：[金额](https://x.com/FirstSquawk/status/2118886517682905491)、[盎司](https://x.com/financialjuice/status/2118886485575516335)。彭博的标题是中国把购金延续到两年，金价这个月下跌将近 7%，月底落到每盎司 4,000 美元的支撑下方：[帖](https://x.com/business/status/2118908851030249727)。将近 -7% 和 4,000 美元下方是彭博写的 10 月金价，不是周五的现货报价。这个窗口里没有一张新的现货黄金收盘价。DeItaone 引高盛把目标价砍掉：2026 年底 4,150 美元，原先 4,650；2027 年底 4,800，原先 5,400；高盛预期 12 月加息，降息可能要到 2027 年末；每月央行购买 60 吨，支撑到 2027 年底大约 15% 的上涨：[帖](https://x.com/DeItaone/status/2118676041149370655)。4,150 和 4,800 是目标价，不是现货。Peter Schiff：主要股指本周都更低，突出的赢家是贵金属矿股，GDX 涨 9.6%：[帖](https://x.com/PeterSchiff/status/2118813467042005073)。9.6% 是他写的一周，不是周五单日。线外的 SentimenTrader：GLD 从 1 月高点下跌超过 28%，情绪刚到熊市极端；过去信号之后，已完成的 8 次里 GLD 一年后更高的是 8 次：[帖](https://x.com/sentimentrader/status/2118722573957742724)。超过 28% 是从 1 月高点算的。Luke Gromen：ChatGPT 发布以来的四年里，纳斯达克 100 和黄金的表现一样；人工智能如果成功、造成消费信贷危机，对黄金有利，如果破裂、造成更广的债务危机，也对黄金有利：[四年](https://x.com/LukeGromen/status/2118817509407437231)、[两种都有利](https://x.com/LukeGromen/status/2118853626689122809)。

## 要盯住的五件事

1. **周五开盘有点位，收盘没有。** First Squawk：道指 51,036.69，跌 0.94%；标普 7,373.17，涨 0.26%；纳斯达克 24,614.53，涨 1.23%。收盘百分比是 CNBC 回复里的纳斯达克综合指数 +1.09%、标普 +0.3%、道指 -237 点或 -0.5%。Keith 的 SPY 是 +0.3%。Seeking Alpha 的纳斯达克是 1%。盘中的纳斯达克 100 到过 +2% 和 +2.4%。
2. **非农是 165,000，失业率标题是 4.1%，Nick 写成 4.14%。** 估计有 DeItaone 叙述里的 59,000、Kobeissi 的 64,000、Gary 盘前和 StockMKTNewz 那句里的 65,000、通讯社和 El-Erian、Liz Ann 的 70,000。9 月从 29,000 上修到 60,000。两个月净修正是 +84,000。时薪环比是 0.4% 对 0.3%，另有 DeItaone 的 0.37%。12 月加息是 79%、80% 和 77%。
3. **WTI 结算 90.83，布伦特结算 98.32。** 这是周五的小涨。Ole 的 -13% 和零对冲的“新冠以来最大周线跌幅”是本周。Gary 盘前的 97 美元是结算前。实物曲线被 Rory 写成平衡到略微过剩。在途原油被 Kobeissi 写成 12.8 亿桶的新高。
4. **下一份会改写利率句子的数据还没来。** SpotGamma 把下一档写成 11 月 10 日的 CPI 和 11 月 13 日的 PPI，负伽马还绑在 11 月 20 日的期权到期上：[帖](https://x.com/spotgamma/status/2118832058436825171)。Phelan 说要看下一份 CPI 才知道美联储做什么。Daly 被写成还可能收紧。两句都留着。
5. **周四的波动率句子不要写成周五收盘。** Minervini 的 VIX 28.5 是周五上午。SpotGamma 写，进入周四时交易商在下跌一侧是负伽马，这种负伽马还在，所以两个方向的大波动都还有。Record SPX 看跌期权成交里，58% 是 0DTE、10% 是 1DTE，那是他 14:18 UTC 的句子：[帖](https://x.com/spotgamma/status/2118709710358782084)。SMH 的看跌偏斜在反弹里仍在变宽：[帖](https://x.com/spotgamma/status/2118749732797358265)。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 开盘点位 | 道指、标普、纳斯达克 | 道指 51,036.69，-0.94%。标普 7,373.17，+0.26%。纳斯达克 24,614.53，+1.23% | [开盘](https://x.com/FirstSquawk/status/2118713036857102433) |
| 收盘只有百分比 | 道指、标普、纳斯达克 | 综合指数 +1.09%，标普 +0.3%，道指 -237 点或 -0.5%。另有 SPY +0.3%，以及纳斯达克上涨 1% | [1.09%](https://x.com/CNBC/status/2118811613352337911)、[SPY](https://x.com/KeithMcCullough/status/2118814613378601093)、[1%](https://x.com/SeekingAlpha/status/2118849666154737685) |
| 盘中已经过期 | 纳斯达克 100 | 盘前期货有 +1.2% 和 +1.3%。盘中到过 +2% 和 +2.4% | [+2%](https://x.com/FirstSquawk/status/2118715986295890369)、[+2.4%](https://x.com/KobeissiLetter/status/2118717121354232120) |
| 盘前名单不要合成 | 芯片 | DeItaone、Kobeissi、零对冲各有一张百分比。SOXX 有接近 +5% 和 +5.9%。市值收回有 5,000 亿和 6,000 亿 | [+5.9%](https://x.com/DeItaone/status/2118674223438709214)、[名单](https://x.com/KobeissiLetter/status/2118687090435137597) |
| 盘中高点 | NVDA | 最多上涨 7.3%，周四跌了 9.3%。盘前另有 +5% 和 +4% | [7.3%](https://x.com/FirstSquawk/status/2118718633442717977) |
| 五天和单日 | SOX、SOXX、SOXL | SOX 五天 -21.8%，周四 -12.3%。Bespoke 写五天跌 20% 以上。SOXX 单日被写成 -12.5%。SOXL 五天 -60%，较高点 -86% | [SOX](https://x.com/KobeissiLetter/status/2118729368977518626)、[SOXX](https://x.com/Hedgeye/status/2118761407235661959) |
| 规则 | SMH、QQQ、AMD、SNDK | RenMac：在 200 日均线上方才算还能做，下方就是脆弱 | [200 日](https://x.com/RenMacLLC/status/2118726672870441226) |
| 距均线 | NVDA、AVGO、SPCX、GOOGL、ORCL | 这五只被写成极度超卖，都比 50 日均线低 14% 以上。苹果、亚马逊、微软在 50 日均线上方 | [五只](https://x.com/bespokeinvest/status/2118704370984669206)、[三只在上方](https://x.com/bespokeinvest/status/2118704524848435592) |
| 平均回撤 | 数据中心“镐和铲” | 罗素 3000 里这组平均较高点 -48.3%，过去一个月 -33.3%，今年至今仍 +21% | [48.3%](https://x.com/bespokeinvest/status/2118793021550432602) |
| 周线 | XLE | 能源板块五天都跌，一周 -12%。板块内股票全部落在 50 日均线下方 | [XLE](https://x.com/bespokeinvest/status/2118829747102789915) |
| 两句跌幅 | ORCL | 微软结束租用之后 -4%，也有 -5%。较高点 -68%。CDS 隐含大约 22% 的五年违约概率 | [-4%](https://x.com/DeItaone/status/2118760159162053104)、[-5%](https://x.com/KobeissiLetter/status/2118761153866482032)、[CDS](https://x.com/Hedgeye/status/2118775422141743423) |
| 信用 | CRWV | CDS 创纪录，隐含大约 66% 的五年违约概率。下周财报名单里也有它 | [66%](https://x.com/Hedgeye/status/2118775422141743423) |
| 盘中高点 | SPCX | 盘中高点 +8.3%。马斯克看到四季度收入环比大约 +70%。年化收入有 12 月 1,000 亿美元和 2027 年 12 月超过 5,000 亿美元两句 | [+8.3%](https://x.com/FirstSquawk/status/2118775202020745368)、[1,000 亿](https://x.com/LiveSquawk/status/2118775674353721799)、[5,000 亿](https://x.com/LiveSquawk/status/2118776684417536205) |
| 估值谨慎 | TSLA | Gary：2026 年市盈率 200 倍，对长期每股收益增长 +45%，PEG 4.4 倍。Cybertruck 被写成 2027 年中附近在得州停产，给 Cybercab 腾地方 | [估值](https://x.com/garyblack00/status/2118651214636220583)、[停产](https://x.com/DeItaone/status/2118674943445532941) |
| 已经到账和还没到 | OpenAI | 1,100 亿美元按 1.25 万亿估值到账。这一轮还有 200 亿和剩下 90 亿的句子。早先的目标是 300 亿或超过 300 亿、估值 1.4 万亿 | [110 亿](https://x.com/financialjuice/status/2118810514210046085)、[过程](https://x.com/StockMKTNewz/status/2118812938161258659) |
| 区间 | Anthropic | 买家看到的估值低至 1.1 万亿，讨论区间 1.2 到 1.3 万亿，周四前是 1.4 到 1.5 万亿。另有 10 月经常性收入 800 亿美元的句子 | [估值](https://x.com/unusual_whales/status/2118760070888796583)、[800 亿](https://x.com/firstadopter/status/2118694978465501418) |
| 持仓 | GOOGL | 三季度末股票组合里 SpaceX 被写成 837.3 亿美元，并新建高通仓位 5.479 亿美元 | [组合](https://x.com/StockMKTNewz/status/2118665638260470192) |
| 请求 | TSM、NVDA | 台积电在英伟达要求下考虑 3D DRAM | [3D DRAM](https://x.com/financialjuice/status/2118705926953906615) |
| 用地 | GOOGL | 买下 Crusoe 的怀俄明数据中心用地，帖文写没有条款 | [没有条款](https://x.com/LiveSquawk/status/2118777801255829543) |
| 当天曾创新低 | AVGO、ORCL、DKNG | StockMKTNewz 把博通、甲骨文、DraftKings 写进当天曾碰到 52 周低点的名单。这是盘中碰到，不是收盘跌幅 | [52 周](https://x.com/StockMKTNewz/status/2118792735654384030) |
| 期权 | MU | unusual_whales：有人在买 2027 年 1 月到期、行权价 600 美元的看涨期权，股价当时 690 美元；周四美光大约跌了 13% | [600](https://x.com/unusual_whales/status/2118796309968904538) |
| 结算 | 原油、布伦特 | WTI 90.83，+0.34%。布伦特 98.32，+0.03%。周线另有 -13% | [90.83](https://x.com/FirstSquawk/status/2118788445976113225)、[98.32](https://x.com/financialjuice/status/2118790930283294899)、[-13%](https://x.com/Ole_S_Hansen/status/2118682112165302452) |
| 目标价 | 黄金 | 高盛把 2026 年底砍到 4,150 美元，2027 年底砍到 4,800 美元。中国持金盎司增加、美元金额下降。GDX 一周 +9.6% | [目标](https://x.com/DeItaone/status/2118676041149370655)、[盎司](https://x.com/financialjuice/status/2118886485575516335)、[GDX](https://x.com/PeterSchiff/status/2118813467042005073) |
| 下周 | CSCO、AMAT、CRWV、NBIS、CBRS | RedDog 和 The Transcript 都把这些名字放进下周。CPI 是 11 月 10 日，PPI 是 11 月 13 日 | [名单](https://x.com/RedDogT3/status/2118806212510613749)、[财报](https://x.com/TheTranscript_/status/2118850472635453811)、[CPI](https://x.com/spotgamma/status/2118832058436825171) |

## 后续走势：三套可以证伪的剧本

帖文没有给周五的收盘点位。已经写下来的开盘是纳斯达克 24,614.53、标普 7,373.17、道指 51,036.69。收盘百分比里，纳斯达克综合指数有 +1.09% 和 1%，标普和 SPY 有 +0.3%，道指有 -237 点或 -0.5%。下面三套的顺序，以这张开盘、这些收盘百分比、非农 165,000、WTI 结算 90.83、布伦特结算 98.32，以及抓取结束时现货已经休市为前提。

**芯片的反弹留到下周，强就业被当成增长而不是立刻加息。** 触发器是 Gary 把数据中心监管写成拿不出数字、因而短命，Tom Lee 把蓝色浪潮写成又一次挨过去的冲击，Yardeni 说买点出现，Phelan 说先看 CPI。期货和现货已经把盘前的芯片涨幅留进了周五：开盘纳斯达克 +1.23%，收盘标题仍是上涨。这条路径失败的条件，是现货下周不接受这张收盘百分比，重新走向 DeItaone 列出的 7,386 下方，目标 7,317、7,240、7,176；或者 10 年期留在 4.898% 之上、12 月加息概率停在 77%、79% 或 80% 的高位，而不是回到 Gary 盘前的 4.84%。

**反弹是死猫，半导体的五天跌幅还没走完。** 触发器是 Minervini 的死猫和 VIX 28.5，Hedgeye 在反弹里重新做空，Keith 把 SPY 的 +0.3% 写成不够，SOX 五天仍有 -21.8% 和“20% 以上”两句，SOXX 的周四单日仍被写成 -12.5%。RenMac 的规则是 200 日均线下方的 SMH、QQQ、AMD、SanDisk 就是脆弱。这条路径失败的条件，是这些名字站回 200 日均线，SMH 的看跌偏斜不再变宽，而且 Keith 仍在做的美元多头、医疗和空头不再强于他写成刚开始的 Quad 4。

**油价决定黄金是跟着海峡缓和走，还是跟着加息走。** 触发器是周五股票反弹的同一天，WTI 只结算在 +0.34%、布伦特只结算在 +0.03%，而 Ole 的周线是 -13%。实物被写成略微过剩，在途原油被写成历史新高。高盛的黄金目标价被砍到 4,150 和 4,800，中国的盎司在增加、美元金额在下降，GDX 的一周是 +9.6%。它失败的条件，是布伦特重新站上 Gary 盘前已经离开的 100 美元、黄金目标价却继续从 4,150 下移，那就是加息盖过了海峡；或者布伦特留在 98.32 附近、GDX 把 9.6% 的一周涨幅还回去，那就是风险偏好盖过了 Schiff 和 Gromen 的黄金句子。

另有一张还没公布的通胀数据，不并进上面三套。密歇根大学的一年通胀预期已经降到 4.3%，五到十年是 3.4%。CPI 被写成 11 月 10 日，PPI 是 11 月 13 日。Phelan 要等 CPI。Daly 被写成通胀仍是第一优先。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周一开盘、11 月 10 日的 CPI，以及下周财报。它不决定仓位大小。周六现货不开。抓取结束时，周日晚间的股指期货还没开。

**周一开盘前只核对五样东西。** 指数是停在收盘百分比这一侧，纳斯达克综合指数 +1.09% 或 1%、标普和 SPY +0.3%、道指 -0.5%，还是回到开盘那张 24,614.53、7,373.17、51,036.69 再往 DeItaone 的 7,386 下方掉。利率是 10 年期留在 4.898%，还是回到 4.88% 或盘前的 4.84%；12 月加息是 77%、79% 还是 80%。油价交易的是结算 90.83 和 98.32，还是 Ole 的周线 -13%，或者重新交易 Gary 盘前的 97 美元。芯片是把盘前的 SOXX +5.9% 和纳斯达克 100 的 +2.4% 留住，还是重新交易五天的 -21.8% 和周四的 -12.3%、-12.5%。黄金是交易高盛的 4,150 美元目标、中国盎司增加，还是交易 GDX 一周 +9.6% 和 GLD 从 1 月高点超过 -28%。五样里，收盘百分比留住、10 年期不站上 4.898%、布伦特留在 98 美元附近，这些帖给出的默认顺序是把强就业当成增长，高于去追已经在五天跌幅里的半导体。Daly 的“还要收紧”压过 Phelan 的“先看 CPI”、布伦特离开 98.32 再向上、标普期货掉回 7,386 下方，默认顺序掉过头来：利率和原油的映射，高于去抄纳斯达克当天那 1% 左右的反弹。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：非农比他写的 +64,000 预期多出大约 10 万，12 月再加 25 个基点的预期到 80%。纳斯达克 100 盘中 +2.4%。SOX 五天 -21.8%，周四 -12.3%。甲骨文 -5%，较高点 -68%。在途原油 12.8 亿桶。他们没有给周五的收盘点位。
- Gary Black，线外：盘前标普 +0.2%、纳斯达克 +1.2%、布伦特 97 美元、10 年期 4.84%、非农预期 +65,000。收盘后他仍把数据中心监管写成短命，2026 年每股收益写成 369 美元，10 年期写成 4.88%。英伟达的估值在盘前那张里是 2027 年 20 倍。特斯拉他仍然谨慎，200 倍对 +45%。
- Tom Lee：蓝色浪潮是又一次宏观冲击，人工智能和科技公司以前也挨过来了。
- Mark Minervini：早盘的科技反弹放到图里只是小波。VIX 28.5。到收盘前，他把当天写成死猫。没有写下新的指数点位。
- Liz Ann Sonders：非农 +165,000 对 +70,000，失业率 4.1%，时薪环比 +0.4%，两个月 +84,000，参与率 61.9%。12 月加息概率从 67% 到 77%。标普远期市盈率 17.8 倍，年初高点是 22.4 倍：[市盈率](https://x.com/LizAnnSonders/status/2118708138086203723)。她写周四只有科技跑输标普，另外 10 个板块跑赢：[板块](https://x.com/LizAnnSonders/status/2118685644876640597)。
- Peter Schiff：本周指数更低，GDX +9.6%。比特币的价格低于微策略的平均成本，他仍把黄金或标普写成更好的去处。
- Charlie Bilello：高贝塔、高动量和迷因股较高点分别 -21%、-27% 和 -57%，今年已经跑输标普：[帖](https://x.com/charliebilello/status/2118692258732265702)。
- Steve Hanke 这个窗口没有新的海峡通航艘数。他写美国货币供应仍然热，9 月 Divisia M4 年率 7.4%，他的黄金增长率是 6.3%。他又引 Chris Wood：中国人工智能芯片股从 6 月下旬高点跌了 50%，而更广的中国市场只跌 1%；人工智能相关投资过去一年占美国经济增长的 67%，2024 年是 13%：[50%](https://x.com/steve_hanke/status/2118957119173263727)、[67%](https://x.com/steve_hanke/status/2118992855247028267)。67% 是他引的增长占比。50% 是中国芯片股。
- Michael Gayed：修正比标题非农重要；2 年期已经定价增长；他写下了“砸股票来救债券”。
- Jim Cramer：把资本从科技挪到更不冒险的非科技。减仓要减够。继续下跌的话，非科技他不会一直这么谨慎。Anthropic 的交易如果公开，他会没那么悲观。帖文里没有写出那个“现在会买”的代码。
- Keith McCullough，线外：Quad 4 刚开始，美元仍是大头配置，SPY 当天只反弹 0.3%。黄金被他写成从周期高点 -25%，而且美元弱的时候才是黄金的时候，现在他做多美元：[黄金](https://x.com/KeithMcCullough/status/2118670526914699766)。日本 10 年期他写成一个月 -46 个基点，Hedgeye 写成 -44 个基点：[Keith](https://x.com/KeithMcCullough/status/2118671638673944578)、[Hedgeye](https://x.com/Hedgeye/status/2118796089134616941)。-46 和 -44 并列。
- Robin Brooks，线外：2 年期涨 4 个基点是正常反应。战争带来的避险会压过美国增长优势，所以美元还是会跌。海峡不必等和平协议。数据前的“短端在掉”不要换成数据后的 4 个基点。
- Ole Hansen，线外：这一周油价 -13%，铜跟着人工智能和关税预期，黄金和白银上涨。没有新的周五结算点位，结算以 90.83 和 98.32 为准。
- SpotGamma，线外：周四标普 -4.36% 是他的句子。负伽马绑到 11 月 20 日。CPI 11 月 10 日，PPI 11 月 13 日。SMH 的看跌偏斜在反弹当天仍变宽。
- RedDog，线外：这一天是破碎图表上的反弹，阻力位在图里，帖文没有写出新的指数点位。下周要看 CPI、PPI，以及 Rocket Lab、CoreWeave、Cerebras、思科、应用材料、Nebius。
- Bespoke，线外：SOX 五天跌 20% 以上。五只巨型股比 50 日均线低 14% 以上。数据中心镐和铲平均较高点 -48.3%。能源板块一周 -12%。
- Ryan Detrick，线外：选举以来中国接近 +5%，标普接近 -3%。标普今年至今 +8%。他仍超配股票，但强调分散。没有写下周五的收盘点位。
- Yardeni，线外：小心的那段已经过去，买点出现。目标价的数字在 DeItaone 引的那张高盛帖里，不在 Yardeni 自己的这两条里。
- First Squawk，线外：开盘点位、非农 165,000 对 70,000、WTI 90.83，见上。没有周五收盘点位。
- 美联储的账号：9 月消费者信贷 +6.4%，不是利率决定。高盛账号只让 Hatzius 说劳动力市场稳定。

**财报和数据的顺序。** 先看已经写进标题的非农、时薪、密歇根大学、WTI、布伦特、甲骨文的 -4% 和 -5%、SpaceX 的盘中 +8.3%、英伟达的盘中 +7.3%。然后才是还没公布的 11 月 10 日 CPI 和 11 月 13 日 PPI。下周名字按 RedDog 和 The Transcript 的帖是思科、应用材料、CoreWeave、Nebius、Cerebras、Sea。线外的 Earnings Whispers 把 11 月 9 日开盘前的日历单独放了一张，里面有 KKR 和 CNH，不并进上面那张科技名单：[日历](https://x.com/eWhispers/status/2118785641236365753)。

**明确留在观察、不放进计划的东西。** 不用开盘点位倒推收盘，也不把盘中的纳斯达克 100 +2.4% 写成综合指数收盘。24,614.53 是开盘。1.09% 和 1% 是收盘标题。0.3% 是标普和 SPY。道指的 -0.94% 是开盘，-0.5% 是收盘标题。非农预期的 59,000、64,000、65,000、70,000 并列。StockMKTNewz 那句“低于 65,000 的预期”不改成超预期。加息概率的 77%、79%、80% 并列。WTI 的 90.83 和周四的 90.52 并列在两天里，周五只引用 90.83。布伦特的 98.32、盘前的 97、周线的 -13% 并列。黄金没有新的周五现货价。高盛的 4,150 和 4,800 是目标。中国的 7,830 万盎司和 3,064.1 亿美元方向相反，盎司是增加。VIX 的 28.5 是上午。SOX 的 -21.8% 和 SOXX 的 -12.5% 不是同一指数。甲骨文的 -4% 和 -5% 并列。SpaceX 的 1,000 亿美元年化是“12 月”，5,000 亿美元是“2027 年 12 月”。OpenAI 的 110 亿是已到账，200 亿和 300 亿是目标沿途。德意志银行的时间线没有读到。Cathie Wood、Ray Dalio 的主号这个窗口没有新的指数点位。Bill Ackman 的帖在大学治理上，没有目标价。Michael Burry 的帖是市场结构的订阅链接，没有写出点位。Paul Krugman、Nouriel Roubini、Warren Buffett、Peter Brandt、Lyn Alden、Jim Bianco、Gundlach、David Rosenberg 这次没有可引用的新点位。

## 帖文索引

开盘和收盘百分比：[道指 51,036.69、标普 7,373.17、纳斯达克 24,614.53](https://x.com/FirstSquawk/status/2118713036857102433)、[综合指数 +1.09%、标普 +0.3%、道指 -0.5%](https://x.com/CNBC/status/2118811613352337911)、[SPY +0.3%](https://x.com/KeithMcCullough/status/2118814613378601093)。

就业和利率：[非农 165,000 对 70,000](https://x.com/FirstSquawk/status/2118697999228702850)、[失业率 4.14%](https://x.com/NickTimiraos/status/2118697935596646759)、[10 年期 4.898%](https://x.com/DeItaone/status/2118698045030420941)、[加息 79%](https://x.com/DeItaone/status/2118699348485685271)、[加息 77%](https://x.com/LizAnnSonders/status/2118789205052846511)。

油、芯片和融资：[WTI 90.83](https://x.com/FirstSquawk/status/2118788445976113225)、[布伦特 98.32](https://x.com/financialjuice/status/2118790930283294899)、[SOX 五天 -21.8%](https://x.com/KobeissiLetter/status/2118729368977518626)、[OpenAI 110 亿美元](https://x.com/financialjuice/status/2118810514210046085)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-07 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 212 条、彭博商业账号 293 条、《金融时报》64 条、《华尔街日报》76 条、《经济学人》94 条、零对冲 96 条、FinancialJuice 230 条、CNBC 61 条、《The Street》72 条、DeItaone 69 条、StockMKTNewz 35 条，是读穿窗口后的计数。德意志银行的 0 是读取失败。保罗·克鲁格曼、BBC Business、markets、沃伦·巴菲特、CNN Business、彭博主号、Peter Brandt、Andrew Ross Sorkin、塔勒布、Lyn Alden、Downtown、美国银行、TradingView、纽约时报商业、花旗、Hindenburg、美国证交会、Bloomberg Economics、Jim Bianco、CNBC Now、Nouriel、Carl Icahn 的 0，是窗口内没有计为原创的新帖。线外的 First Squawk 是 157 条，LiveSquawk 是 72 条，不在这张表里。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,442,683 | 212 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,330,214 | 94 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,277,489 | 76 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,314,093 | 33 |
| 5 | [@business](https://x.com/business) | 10,491,079 | 293 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,569,411 | 4 |
| 7 | [@FT](https://x.com/FT) | 7,114,024 | 64 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,257,144 | 61 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,382,681 | 40 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,648,658 | 32 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,602,521 | 1 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,429,591 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,355,072 | 39 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,431,156 | 96 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,425,853 | 23 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,046,471 | 1 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,003,969 | 2 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,735,063 | 16 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,567,097 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,528,318 | 15 |
| 21 | [@chamath](https://x.com/chamath) | 2,486,627 | 2 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,439,820 | 6 |
| 23 | [@BW](https://x.com/BW) | 2,288,396 | 4 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,336 | 31 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,157,375 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,129,677 | 1 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,078,780 | 16 |
| 28 | [@markets](https://x.com/markets) | 2,048,865 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,970,937 | 69 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,795,620 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,776,914 | 2 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,992 | 19 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,709,890 | 2 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,700,717 | 8 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,619 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,616,437 | 20 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,602,886 | 4 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,537,310 | 27 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,512,346 | 3 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,471,430 | 6 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,638 | 2 |
| 42 | [@Bloomberg](https://x.com/Bloomberg) | 1,356,487 | 0 |
| 43 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,356,409 | 0 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,252,659 | 2 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,225,963 | 72 |
| 46 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,194,056 | 8 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,194,044 | 5 |
| 48 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,191,590 | 0 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,185,013 | 6 |
| 50 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,166,977 | 35 |
| 51 | [@USTreasury](https://x.com/USTreasury) | 1,166,051 | 1 |
| 52 | [@nntaleb](https://x.com/nntaleb) | 1,164,906 | 0 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,157,475 | 2 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,154,028 | 19 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,140,456 | 0 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,117,378 | 3 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,109,261 | 27 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,097,567 | 7 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,081,820 | 4 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,066,083 | 2 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,399 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,665 | 28 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,004,354 | 3 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 956,003 | 230 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,053 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 934,884 | 13 |
| 67 | [@tradingview](https://x.com/tradingview) | 907,243 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 894,310 | 21 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 890,945 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,549 | 16 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 873,948 | 1 |
| 72 | [@axios](https://x.com/axios) | 863,357 | 28 |
| 73 | [@steve_hanke](https://x.com/steve_hanke) | 862,075 | 34 |
| 74 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 861,087 | 29 |
| 75 | [@jpmorgan](https://x.com/jpmorgan) | 860,662 | 1 |
| 76 | [@Citi](https://x.com/Citi) | 853,149 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 847,816 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,609 | 1 |
| 79 | [@ecb](https://x.com/ecb) | 830,845 | 2 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,376 | 2 |
| 81 | [@bgurley](https://x.com/bgurley) | 811,930 | 1 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,317 | 0 |
| 83 | [@economics](https://x.com/economics) | 806,362 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 790,176 | 0 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,506 | 7 |
| 86 | [@markminervini](https://x.com/markminervini) | 771,998 | 5 |
| 87 | [@leadlagreport](https://x.com/leadlagreport) | 769,319 | 12 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 759,455 | 2 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,636 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 737,446 | 1 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 718,722 | 13 |
| 92 | [@CMEGroup](https://x.com/CMEGroup) | 712,236 | 1 |
| 93 | [@Nouriel](https://x.com/Nouriel) | 709,846 | 0 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 674,422 | 9 |
| 95 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,843 | 1 |
| 96 | [@fundstrat](https://x.com/fundstrat) | 672,794 | 2 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,535 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,599 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 636,814 | 6 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 626,660 | 4 |
