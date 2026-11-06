# 美股 Twitter 观点日报 · 2026-11-06

周四现货已经走完，周五现货还没开。抓取结束时美东大约 5:19。指数收盘是大跌，芯片和数据中心是主线，油价结算是上涨。开盘、盘中、收盘、盘后和周五凌晨的期货，按发帖原文分开。非农还在美东 8:30。这是公开帖文的整理，不是投资建议。

下面每一条归纳都附有帖文链接。

## 抓取口径

- 报告日期按北京时间 **2026-11-06**。触发时刻约 10:02 UTC，时间线补抓到 **约 10:19 UTC（北京时间 18:19，美东 5:19）**。美国夏令时已经结束。美股现货 9:30 才开。10 月就业报告还在美东 8:30。
- 观察窗口从 **2026-11-05 10:22 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周四白天的现货全天、收盘、盘后，以及美东周五凌晨到大约 5:19。上一份日报里的周三收盘不在这里重算。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。抓取开始时未加地区的趋势是 Wizkid、Jags、Jaguars、Atiku、South Africans、Elysium。同一时刻美国地区趋势是 Schumer、Nick Fuentes、Ted Cruz、Thune、DeSantis、Dems。抓取结束时，未加地区和美国地区都是 Thune、Schumer、DeSantis、Dems、Hegseth、Massie。里面没有美股代码。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。
- 不存在官方的“美股 Top 100”。这次试了 **348** 个候选，成功读到粉丝数的有 **335** 个，去重后 **335** 个。排序时拿掉加密货币账号、综合新闻主号、科技风投和创始人、大型科技公司首席执行官、竞选和政治账号、公司产品品牌、大学和智库，以及简介对不上的错人号。`@DanielNewman` 仍是漫威演员，`@SEC` 仍是东南联盟，`@goldman` 仍不是高盛，`@robinbrooks` 仍不是 Robin Brooks。这四个号的粉丝都高于今天的截止线，排除之后截止才停在 Eric Balchunas。用来排序的账号是 **276** 个，截止在 Eric Balchunas（627,209）。Morning Brew（593,567）落到第 101。Gary Black（584,671）第 102。Cboe 第 103。Barchart 第 104。First Squawk（576,701）第 105。dampedspring、Gundlach、Earnings Whispers、LiveSquawk、瑞银、Nick Timiraos、日经亚洲、Keith McCullough、Fxhedgers、MacroAlf、Traderstewie、The Stalwart、Hedgeye、巴伦、Javier Blas、Robin Brooks、Bespoke、SpotGamma、The Transcript、firstadopter、Ryan Detrick、Yardeni、RenMac、RedDog、Benzinga、Newsquawk 落在线外，引用时会写明。排序不代表预测准确度。前 100 的账号集合和 11 月 5 日那份相同，名次在 Mark Minervini 与 Michael Gayed、Tom Lee 与 amit 这两对上对调。
- 100 个账号里，**77 个**在窗口内有按帖文链接去重后、且接口没有标成回复的原创帖。路透读穿窗口，295 条。彭博商业账号读穿窗口，322 条。《金融时报》70 条。《华尔街日报》67 条。《经济学人》132 条。零对冲 160 条。FinancialJuice 读穿窗口，302 条。CNBC 90 条。《The Street》75 条。DeItaone 74 条。StockMKTNewz 50 条。unusual_whales 45 条。Axios 42 条。《福布斯》42 条。线外的 First Squawk 读穿窗口，原创 278 条。LiveSquawk 读穿窗口，原创 126 条。德意志银行的时间线返回错误，表里的 0 不是确认沉默。保罗·克鲁格曼、Cathie Wood、BBC Business、彭博 markets、沃伦·巴菲特、CNN Business、彭博主号、Andrew Ross Sorkin、美国财政部、高盛、Downtown、美国银行、TradingView、纽约时报商业、摩根大通、花旗、Hindenburg、Bloomberg Economics、CNBC Now、Nouriel Roubini、Carl Icahn、马克·库班的 0，是可见时间线在窗口内没有计为原创的新帖。世界银行的资料接口显示账号已停用。

## 周四收盘是指数大跌，开盘那张已经过期

开盘是 First Squawk 14:31 UTC 的一张帖。道指涨 330.63 点，或 0.62%，到 53,686.75。纳斯达克跌 198.95 点，或 0.77%，到 25,537.57。标普 500 跌 12.86 点，或 0.17%，到 7,675.76：[开盘三条写在同一帖](https://x.com/FirstSquawk/status/2118350563197005886)。开盘这一侧，高通被写成下跌 14%，准备创 2020 年以来最差的一天：[LiveSquawk](https://x.com/LiveSquawk/status/2118350636898979878)、[First Squawk](https://x.com/FirstSquawk/status/2118351160440652094)。零对冲同一分钟把特斯拉写成 -3.9%，SpaceX 写成 -4.3%：[帖](https://x.com/zerohedge/status/2118350533258011114)。

盘中的百分比一路加深，不要拿去替换收盘。First Squawk 14:47 UTC：纳斯达克 100 跌幅扩到 3%，标普跌 1.3%：[帖](https://x.com/FirstSquawk/status/2118354533500031044)。15:29 UTC：纳斯达克 100 跌到 5.1%，标普跌 2.8%：[帖](https://x.com/FirstSquawk/status/2118365186071650405)。15:54 UTC：纳斯达克 100 跌超 6%，标普跌 3.7%：[帖](https://x.com/FirstSquawk/status/2118371323131085160)。DeItaone 15:12 UTC：道指跌 1.00%：[帖](https://x.com/DeItaone/status/2118360741329916295)。15:46 UTC：罗素 2000 跌 2.5%，写成准备创 6 月 5 日以来最大单日跌幅：[帖](https://x.com/DeItaone/status/2118369319654773196)。18:00 UTC：标普跌幅扩到 4.00%：[帖](https://x.com/DeItaone/status/2118403121353220177)。18:05 UTC：标普跌 4.1%，纳斯达克跌 5.4%，道指跌 3.2%：[帖](https://x.com/DeItaone/status/2118404453737115984)。Kobeissi 15:17 UTC 把开盘后 40 分钟写成标普抹掉 2 万亿美元，中期选举之后的反弹在几分钟里被擦掉：[帖](https://x.com/KobeissiLetter/status/2118362154558779411)。15:30 UTC 他把 55 分钟写成抹掉 2.2 万亿美元，并写当天跌幅已经是前一天选举反弹的两倍，纳斯达克 100 距离熊市大约还有 6%：[帖](https://x.com/KobeissiLetter/status/2118365320968634757)。15:50 UTC：纳斯达克 100 跌到 -5.5%，准备创 2025 年 4 月以来最大单日跌幅，距离熊市大约还有 5%：[帖](https://x.com/KobeissiLetter/status/2118370442276643091)。-5.5% 是这一条的盘中句子。下面的 -6.4% 是收盘句子。

收盘点位是 First Squawk 21:05 UTC 的一张帖。纳斯达克跌 5.56%，到 24,305.70，跌 1,430.82 点。标普 500 跌 4.33%，到 7,355.81，跌 332.81 点。道指跌 3.45%，到 51,515.81，跌 1,840.31 点：[帖](https://x.com/FirstSquawk/status/2118449557944307879)。Morning Brew 21:04 UTC 是另一张百分比，没有点位：纳斯达克 100 -6.4%，纳斯达克 -5.5%，罗素 2000 -4.5%，标普 500 -4.4%，道指 -3.4%：[帖](https://x.com/MorningBrew/status/2118449382303695034)。5.56% 和 5.5%、4.33% 和 4.4%、3.45% 和 3.4%、1,840.31 点和“下跌 1,800 点”，并列。MarketWatch 的标题是道指收盘下跌 1,800 点，纳斯达克下跌 5.5% 并进入修正：[帖](https://x.com/MarketWatch/status/2118450691177927141)。Investing.com 的标题是道指收盘下跌 1,800 点，波动率因为人工智能科技股重挫而飙升：[帖](https://x.com/Investingcom/status/2118449533994865139)。另一条把标普写成下跌 4.3%，是 2025 年 4 月以来最差的抛售：[帖](https://x.com/Investingcom/status/2118453607519424591)。CNBC 的标题是道指下跌 1,800 点，纳斯达克跌进修正：[帖](https://x.com/CNBC/status/2118451159132491991)。路透的收盘标题没有点位：纳斯达克综合指数收盘大跌，创 19 个月最深的单日跌幅，并确认进入修正，芯片股因为民主党拿下国会之后对人工智能监管收紧的担心而下跌：[帖](https://x.com/Reuters/status/2118451823183015968)。19 个月是路透的句子。2025 年 4 月是 Investing.com 和下面 Gary Black 的句子。

“最差的一天从什么时候算起”有两句，不要并成一句。线外的 Gary Black：纳斯达克 100 跌 6.4%，标普跌 4.4%，是 2025 年 4 月以来最差的一天：[帖](https://x.com/garyblack00/status/2118467071960834122)。Charlie Bilello：标普跌 4.4%，是 2025 年 4 月关税动荡以来最大的下跌日，也是 1989 年以来第 37 大的下跌日：[帖](https://x.com/charliebilello/status/2118478453708312730)。Kobeissi 收盘后的线程把纳斯达克 100 写成 2020 年疫情以来最大的单日跌幅，并把标普当天抹掉的市值写成 3 万亿美元；24 小时前道指在民主党横扫之后涨了 1,600 点：[帖](https://x.com/KobeissiLetter/status/2118455887413285205)。彭博周五的直播标题用的是“2020 年以来最差的美股暴跌”：[帖](https://x.com/business/status/2118500850528051418)。6.4% 是纳斯达克 100。5.56% 和 5.5% 是综合指数。3 万亿美元是 Kobeissi 的标普句子。

市值还有另外两张，不要换成 3 万亿。DeItaone 21:12 UTC：纳斯达克 100 下跌 6.4%，抹掉 2.3 万亿美元：[帖](https://x.com/DeItaone/status/2118451528981753938)。00:20 UTC 他又写成抹掉 2.5 万亿美元，综合指数跌 5.5%，进入修正，距离 10 月高点将近 12%；半导体跌 12%，英伟达跌 9%：[帖](https://x.com/DeItaone/status/2118498750826004588)。First Squawk 的收盘综述是纳斯达克 100 跌 6.4%、抹掉 2.3 万亿美元，标普跌 4.4%，芯片指数跌 12%：[帖](https://x.com/FirstSquawk/status/2118457236985160060)。2.3 万亿和 2.5 万亿并列。12% 在综述里是芯片指数，在 Gary 的帖里是半导体 ETF SOXX，并被写成 2020 年 3 月新冠开始以来最大的单日百分比跌幅。

熔断没有被写成已经触发。DeItaone 在标普盘中跌 3.8% 的时候列出规则：7% 的位置在 7,150.41，会停 15 分钟；13% 是下一档：[帖](https://x.com/DeItaone/status/2118374553789268091)。线外的 SpotGamma 提醒，标普现货的全市场熔断大约在 -7%，纳斯达克 100 期货有自己的大约 7%、13%、20% 限制，期货停了现货不一定停：[帖](https://x.com/spotgamma/status/2118371930168565852)。收盘点位 7,355.81 高于他帖里的 7,150.41。7,150.41 是规则位置，不是收盘。

波动率的句子从盘中到收盘换了好几张。零对冲 15:42 UTC：VIX 24，大约涨了 50%：[帖](https://x.com/zerohedge/status/2118368444156411934)。Kobeissi 15:59 UTC：VIX 当天涨超 70%，准备创 2018 年 2 月以来最大单日涨幅，并写 2020 年 3 月也没有过这样的单日跳升：[帖](https://x.com/KobeissiLetter/status/2118372705917603963)。DeItaone：VIX 最多涨 48%，是 2025 年 4 月 4 日解放日以来最大的百分比飙升：[帖](https://x.com/DeItaone/status/2118372582781001771)。CNBC：盘中高点 28.09，是 3 月 31 日高点 29.64 以来最高：[帖](https://x.com/CNBC/status/2118383454001811495)。线外的 Keith McCullough：VIX 当天 +55%，共识在选举前拆掉了对冲：[帖](https://x.com/KeithMcCullough/status/2118423810940498365)。Gary 的收盘帖把 VIX 写成两年里最大的上涨，从 17 到 28。线外的 SpotGamma 在收盘后改口点数和百分比：今天收盘对收盘涨 11.57 点，按点数在 1990 年以来排第 17，最大的一次是 2020 年 3 月 16 日的 +24.86 点；按百分比排第三，是因为起点的 VIX 更低：[帖](https://x.com/spotgamma/status/2118474418649174017)。24、28.09、28、从 17 到 28、+48%、+50%、+55%、+70%、+11.57 点，按账号和时间留着。+70% 是 15:59 UTC 的“准备创”句子。+11.57 点是收盘对收盘。

## 油、黄金和收益率沿途有多句，就业数字的符号也不一样

周四油价结算是上涨，和指数的方向相反。FinancialJuice、LiveSquawk、First Squawk：WTI 12 月期货结算每桶 90.52 美元，上涨 2.40 美元，涨幅 2.72%：[FinancialJuice](https://x.com/financialjuice/status/2118425923037155519)、[LiveSquawk](https://x.com/LiveSquawk/status/2118426054976995418)、[First Squawk](https://x.com/FirstSquawk/status/2118426223894548805)。布伦特结算每桶 98.29 美元，上涨 3.67 美元，涨幅 3.88%：[FinancialJuice](https://x.com/financialjuice/status/2118428871012020226)、[First Squawk](https://x.com/FirstSquawk/status/2118429232443580776)、[LiveSquawk](https://x.com/LiveSquawk/status/2118429247555371123)。First Squawk 的收盘综述把油写成上涨 2.7%、到 90.54 美元：[帖](https://x.com/FirstSquawk/status/2118457252244058175)。Gary 的收盘帖把布伦特写成 +4%。90.52 和 90.54、3.88% 和 4%、2.72% 和 2.7%，并列。上一份日报里的周三结算不在这里重算。

盘前和周五凌晨是另外几张。线外的 Gary Black 10:29 UTC，也就是暴跌之前：标普期货 -0.1%，纳斯达克期货 -0.7%，布伦特在前一天跌 8% 之后涨 1.3% 到 96 美元，10 年期落到 4.87%：[帖](https://x.com/garyblack00/status/2118289614355963954)。First Squawk 周五 03:28 UTC：美国原油期货上涨 1 美元，到 91.52：[帖](https://x.com/FirstSquawk/status/2118546106741395539)。03:40 UTC：布伦特期货上涨超过 2 美元，站上 100 美元：[帖](https://x.com/FirstSquawk/status/2118549168029659226)。08:57 UTC 的标题改成油价下跌、中东降温的希望增加：布伦特在前一交易日涨近 4% 之后落到 98 美元下方，美国基准 WTI 在 90 美元附近：[帖](https://x.com/FirstSquawk/status/2118628880743620763)。96、90.52、90.54、91.52、站上 100、98 下方、90 附近，按时间留着。

黄金也是几张，而且有一张是从历史高点算的回撤。First Squawk 00:28 UTC：现货黄金上涨 0.9%，到每盎司 4,099.15 美元，从更早的上涨 2.1% 回落，美元偏强限制了上行：[帖](https://x.com/FirstSquawk/status/2118500808153248048)。03:13 UTC：黄金下跌接近 1%，到 4,049.88：[帖](https://x.com/FirstSquawk/status/2118542211759653023)。06:22 UTC 的 FXStreet 标题是在美元偏强、美国就业数据之前，黄金进一步落到 4,050 下方：[帖](https://x.com/FirstSquawk/status/2118589730619281513)。线外的 Hedgeye 另写黄金较历史高点下跌 24.5%：[帖](https://x.com/Hedgeye/status/2118339641946628323)。4,099.15、4,049.88、4,050 下方是当天和周五凌晨的价格。24.5% 是距高点的回撤。

收益率没有和油价结算写在同一句里的唯一收盘。DeItaone 13:35 UTC，数据出来之后、现货暴跌之前：10 年期最后上涨 1.04 个基点，到 4.902%；2 年期上涨 3.31 个基点，到 4.614%：[帖](https://x.com/DeItaone/status/2118336286927020429)。Kobeissi 16:08 UTC：波动率大涨、当天市值损失 2.5 万亿美元的时候，10 年期只跌了 7 个基点：[帖](https://x.com/KobeissiLetter/status/2118374902596059374)。First Squawk 的收盘综述是收益率下跌 6 个基点，到 4.83%。Gary 的收盘帖是下跌 5.5 个基点，到 4.85%。周五 08:56 UTC，First Squawk 引述国债交易员在就业报告前押注债券上涨，10 年期写成 4.82%，是 9 月初以来最低：[帖](https://x.com/FirstSquawk/status/2118628634110173204)。4.902%、下跌 7 个基点、4.83%、4.85%、4.82%，并列。4.87% 是 Gary 暴跌前的那一张。

初请和生产率已经出来，预期和符号不要并。First Squawk：初请 189,000，前值 194,000，估计 196,000：[帖](https://x.com/FirstSquawk/status/2118335096117936195)。FinancialJuice 的初请是 189,000，预期 196,000，前值 194,000：[帖](https://x.com/financialjuice/status/2118335139566489636)。DeItaone：初请减少 6,000，到 189,000，调查 197,000；10 月 24 日当周续请增加 23,000，到 1,718,000；10 月 24 日当周初请修正到 195,000：[帖](https://x.com/DeItaone/status/2118335144255721967)。零对冲：初请 189,000，预期 196,000；续请 1,718,000，预期 1,710,000：[帖](https://x.com/zerohedge/status/2118335159816921231)。LiveSquawk：初请 189,000，估计 196,000，前值 194,000，修正前值 195,000；续请 171.8 万，估计 171.0 万，前值 170.1 万，修正前值 169.5 万：[帖](https://x.com/LiveSquawk/status/2118335344626356333)。Liz Ann Sonders：初请 189,000，对估计 196,000、前值 195,000；续请 171.8 万，对估计 171.0 万、前值 169.5 万：[帖](https://x.com/LizAnnSonders/status/2118340726878540111)。线外的 Hedgeye：189,000，估计 197,000，前值 195,000：[帖](https://x.com/Hedgeye/status/2118338333990621656)。196,000 和 197,000 并列。前值 194,000、修正 195,000、Liz Ann 直接用的 195,000，并列。续请的前值 170.1 万和修正 169.5 万，并列。路透的标题是初请处在 57 年低点：[帖](https://x.com/Reuters/status/2118428204184584474)。Charlie Bilello 写成 1969 年夏天以来最低：[帖](https://x.com/charliebilello/status/2118358028915540276)。

生产率的方向一致，单位劳动力成本的符号不一致。FinancialJuice：初值 3.6%，预期 2.7%，前值 1.4%：[帖](https://x.com/financialjuice/status/2118335174207582415)。LiveSquawk：非农生产率 3.6%，估计 2.7%，前值 1.4%，修正前值 2.1%；单位劳动力成本 0.7%，估计 0.4%，前值 1.2%，修正前值 1.9%：[帖](https://x.com/LiveSquawk/status/2118335379103461811)。零对冲把单位劳动力成本写成 -0.7%，预期 0.4%，前值 1.9%；生产率 3.6%，预期 2.7%，前值 2.1%：[帖](https://x.com/zerohedge/status/2118335533005046252)。Liz Ann：单位劳动力成本 -0.7%，前值 +1.9%（从 +1.2% 上修）；生产率 +3.6%，前值 +2.1%（从 +1.4% 下修）：[帖](https://x.com/LizAnnSonders/status/2118337643977265541)。DeItaone 把生产率写成 3.6%，并写成远超“收缩 0.7%”的预期；单位劳动力成本下降 0.7%，预期是上升 1.8%：[帖](https://x.com/DeItaone/status/2118348197177274576)。3.6% 是生产率。预期有 2.7%，也有 DeItaone 的“收缩 0.7%”。单位劳动力成本在 LiveSquawk 是 +0.7%，在零对冲、Liz Ann 和 DeItaone 是 -0.7%。

Challenger 是另一张已经公布的裁员数。First Squawk：裁员总数 43,994，前值 43,281：[帖](https://x.com/FirstSquawk/status/2118290195368079518)。LiveSquawk 的同比是 -71.3%，前值 -19.9%：[帖](https://x.com/LiveSquawk/status/2118289902592729213)。Liz Ann：裁员公告同比 -71.3%；截至 10 月累计 617,189，比 2025 年前 10 个月宣布的 110 万少 44%：[帖](https://x.com/LizAnnSonders/status/2118325288962867394)。

非农本身还没有结果。Gary 把华尔街对 10 月非农的共识写成增加 65,000；他写如果太强（超过 130,000）或者太弱（如果是负数），周五的下跌可能延续。同一帖把 12 月加息的押注写成从昨天的 82% 降到 66%。路透的预览是另一句：10 月非农可能回升，但全年工资增速预计降到 3.0% 以下，会是将近五年半以来第一次，用来说明劳动力市场不是通胀来源：[帖](https://x.com/Reuters/status/2118586687651565995)。65,000、超过 130,000、负数、工资低于 3.0%，都是公布前的句子。

英国央行已经决定，和美国的非农分开。First Squawk：利率 4.0%，前值 3.75%，估计 4.0%：[帖](https://x.com/FirstSquawk/status/2118312417721774473)。FinancialJuice：加息票数 9，预期 7，前值 3；不变票数 0，预期 2：[加息 9 票](https://x.com/financialjuice/status/2118312548294353392)、[不变 0 票](https://x.com/financialjuice/status/2118312535615262889)。First Squawk：Mann 反对，主张加 50 个基点：[帖](https://x.com/FirstSquawk/status/2118312935080775839)。LiveSquawk 的标题是加 25 个基点，到 4.00%，符合预期：[帖](https://x.com/LiveSquawk/status/2118312671636570449)。Mohamed El-Erian 把投票写成 8 比 1，一位异议者要加 50 个基点，并写通胀明年可能见顶在 4.9%：[帖](https://x.com/elerianm/status/2118313989662810211)。9 票对 0 票，和 8 比 1，并列。4.9% 是 El-Erian 的句子。

## 观点分成四组

### 1. 选举被写成已经定价，新的句子是人工智能监管和数据中心

Kobeissi 16:26 UTC：过去 24 小时基本面变了什么；选举结果不能单独解释，因为市场大体已经定价；他写最可能的催化剂是对“禁止人工智能”、至少是严厉监管的担心，包括民主党议员公开呼吁限制先进人工智能、以及“禁止人工超级智能”；他接着写彻底的禁令不会发生，否则等于把位置让给中国；下跌更多是技术性的，情绪碰到了过高的杠杆，可能触发几家大型机构的强制平仓；价格看起来既不 orderly 也不理性；把时间拉长，保持冷静：[帖](https://x.com/KobeissiLetter/status/2118379488971043055)。Tom Lee 把当天写成蓝色浪潮的余震式强制平仓，对上 2025 年的关税冲击、DeepSeek、以及 2026 年 6 月的情境；他写先前每一次冲击都在几天里见底，而且是买入机会；需求仍强，没有新的竞争者来打破瓶颈，速度上可能有一个减速带，减速带等于机会：[帖](https://x.com/fundstrat/status/2118432421813129491)。同一小时他又写 9 月的加息开始看起来没有必要：[帖](https://x.com/fundstrat/status/2118437431196409968)。

监管和数据中心是另一组已经点名的句子。Kobeissi 周五 01:01 UTC：得州候任州长 Gina Hinojosa 呼吁在新法律出台之前暂停人工智能数据中心，引自 CNN；原话是先停掉现在对数据中心所做的事，直到有那些保护；她会是 1995 年以来得州第一位民主党州长：[帖](https://x.com/KobeissiLetter/status/2118509115806818423)。DeItaone 有同一句：[帖](https://x.com/DeItaone/status/2118507047016620230)。线外的 Ed Yardeni：标普刚经历 4 月关税冲击以来最差的一天；触发器是 76% 的选民现在反对自己社区里的新数据中心；正文在会员墙后面：[帖](https://x.com/yardeni/status/2118565616671916033)。The Transcript 引 Arm 首席执行官：如果美国在数据中心建设上有任何犹豫，世界其他地方已经准备好、也愿意接过去：[帖](https://x.com/TheTranscript_/status/2118401082141401299)。

线外的 Robin Brooks 把两天并成另一张，不要换成周四的收盘跌幅。他写市场交易的不是中期选举；昨天标普的上涨来自万斯把战争和共和党失利连在一起的帖，以及随之而来的油价大跌；把昨天和今天轧差之后，标普是 -2%，和 2022 年 11 月 9 日、上一次中期选举次日一样：[帖](https://x.com/robin_j_brooks/status/2118382360961900782)。-2% 是他的两日轧差。4.33% 和 4.4% 是周四单日。他早上另写，万斯那条帖之后布伦特几乎跌了 7%；未来几天可能还有一轮轰炸，但那会是表演性的，战争实际上已经结束：[帖](https://x.com/robin_j_brooks/status/2118323907753046244)。几乎 -7% 是他写的前一天。周四结算是上涨。他又写，今年偏鹰的联邦公开市场委员会成员会重新找回内在的鸽派：[帖](https://x.com/robin_j_brooks/status/2118327295022711242)。

Jim Cramer 把 Anthropic 写成得打折才能做成，并写成恐惧的主要源头，而这种恐惧是美国人所感觉到的：[帖](https://x.com/jimcramer/status/2118359783497495002)。CNBC 的标题是 Cramer 说人工智能抛售还没结束，但不是又一次互联网泡沫崩溃：[帖](https://x.com/CNBC/status/2118483689550024916)。DeItaone：Anthropic 2026 年上市的 Kalshi 概率跌到 60% 以下，选举前接近 90%；投资者把估值目标写成 1.5 万亿到 1.6 万亿美元：[帖](https://x.com/DeItaone/status/2118391560811278770)。Kobeissi 另写 Anthropic 已经披露创纪录的 8,950 亿美元未来人工智能基础设施承诺，其中 4,480 亿、也就是 50% 预计在 2030 年底前发生，未来 12 个月大约 700 亿；最大一笔是博通 1,610 亿，其次是谷歌 1,210 亿，另外最多还有 1,500 亿：[帖](https://x.com/KobeissiLetter/status/2118397431729586495)。60% 以下是上市概率。1.5 万亿到 1.6 万亿是估值目标。8,950 亿是支出承诺。

### 2. 指数里面，芯片、存储和与马斯克相关的名字跌得更深

开盘后的名单和收盘百分比不是同一张。Kobeissi 14:59 UTC 把科技股 30 分钟抹掉的市值写成 1.3 万亿美元，并列出两位数跌幅：SanDisk -15%，西部数据 -13%，Nebius -13%，AMD -12%，希捷 -12%，高通 -10%，美光 -10%，特斯拉 -10%，戴尔 -10%，Arm -10%，Marvell -10%，CrowdStrike 也在名单里：[帖](https://x.com/KobeissiLetter/status/2118357540299735378)。他 14:43 UTC 单独把 AMD 写成跌超 11%，较 10 月 6 日高点 -35%，过去一个月市值抹掉 3,800 亿美元：[帖](https://x.com/KobeissiLetter/status/2118353456255955415)。线外的 Hedgeye 把 AMD 写成 -12.2%，到 7 月以来最低：[帖](https://x.com/Hedgeye/status/2118356071660057084)。-11%、-12%、-12.2% 并列。-35% 和 3,800 亿是从 10 月 6 日算的，不是周四单日。

高通的盘中百分比有三句。开盘 -14% 见上。CNBC 15:22 UTC 的标题是财报之后下跌 9%，领着选举之后的芯片抛售：[帖](https://x.com/CNBC/status/2118363265335996654)。16:14 UTC：下跌 13%；四季度略超预期，当季指引偏弱：[帖](https://x.com/CNBC/status/2118376531957297373)。-14%、-9%、-13% 按时间留着。没有一张高通的收盘专帖。Arm 的目标价是另一句。FinancialJuice：瑞银把目标价从 320 美元砍到 270 美元：[帖](https://x.com/financialjuice/status/2118357091605987344)。

英伟达的收盘百分比有两句。DeItaone 16:08 UTC：大约下跌 8%，今年至今大约 -2%，2026 年的涨幅被抹掉：[帖](https://x.com/DeItaone/status/2118374995793527184)。Gary 的收盘帖是 -9.3%，今年至今 -3%。Cramer 在开盘时写英伟达终于低开：[帖](https://x.com/jimcramer/status/2118318993261863071)。他后来写英伟达有 2,350 亿美元回购：[帖](https://x.com/jimcramer/status/2118360971605385348)。中午之前又写已经成交 1.44 亿股：[帖](https://x.com/jimcramer/status/2118386315435618729)。大约 -8% 和 -9.3%、大约 -2% 和 -3%，并列。2,350 亿是回购。1.44 亿股是中午之前的成交。

Gary 的收盘帖还把特斯拉写成 -11%，SpaceX 写成 -9%，并把特斯拉与 SpaceX 合并的赔率写成下降。开盘那张是 -3.9% 和 -4.3%。两日市值有三句。MarketWatch 先写成特斯拉和 SpaceX 两天合计抹掉 4,500 亿美元：[帖](https://x.com/MarketWatch/status/2118428523278798998)。后来写成 4,560 亿美元：[帖](https://x.com/MarketWatch/status/2118472769297858967)。Investing.com 写成 5,000 亿美元：[帖](https://x.com/Investingcom/status/2118464680280670701)。4,500 亿、4,560 亿、5,000 亿并列。周五另有一句和股价百分比无关：马斯克说特斯拉将在 2027 年中停止得州 Cybertruck 的生产：[帖](https://x.com/financialjuice/status/2118592324783722643)。

七巨头的市值也有两句。DeItaone 盘中：七巨头准备在一个交易日抹掉 1.1 万亿美元，会是这组最大的单日市值损失；当时纳斯达克正在进入修正：[帖](https://x.com/DeItaone/status/2118372358746440149)。CNBC 收盘后的标题是七巨头损失 1 万亿美元：[帖](https://x.com/CNBC/status/2118467318942515378)。1.1 万亿是盘中的“准备”。1 万亿是收盘后的标题。

债券和股价分开的名字还有 CoreWeave 和 DraftKings。Cramer：CoreWeave 2032 年 7 月 15 日到期、票息 8.5% 的债券交易在 73：[帖](https://x.com/jimcramer/status/2118369179854082135)。彭博：DraftKings 2027 年盈利预测低于平均估计，并下调 2026 财年展望，三季度收入也不及预期，盘后股价跌 19%：[帖](https://x.com/business/status/2118462120266207421)。The Street：SanDisk 在业绩强劲的情况下，随着人工智能抛售加深下跌 20%：[帖](https://x.com/TheStreet/status/2118458390598877204)。-15% 是 Kobeissi 的开盘后名单。-20% 是 The Street 的句子。

Charlie Bilello 给了一张距离各自高点的表，不是周四单日：苹果 -3%，微软 -4%，标普 -6%，亚马逊 -9%，Meta -24%，英伟达 -26%，Palantir -27%，黄金 -27%，谷歌 -31%，特斯拉 -31%，AMD -39%，比特币 -40%，SpaceX -45%，奈飞 -51%：[帖](https://x.com/charliebilello/status/2118497988024971738)。他另写，价值股今年至今 +24%，成长股 -6%，差距超过 30 个百分点；如果保持到年底，会是比 2000 年互联网泡沫破裂那年更宽的纪录差距：[帖](https://x.com/charliebilello/status/2118527226790736036)。半导体自 6 月底下跌 37%：[帖](https://x.com/charliebilello/status/2118546188148600847)。6 月 25 日半导体相对七巨头的今年至今超额是 115 个百分点，当天收成 29 个百分点：[帖](https://x.com/charliebilello/status/2118545288923435068)。+24%、-6%、-37%、115 个百分点和 29 个百分点，都不是周四的单日收盘。市盈率是另一张：开市客 51，沃尔玛 46，英伟达 23：[帖](https://x.com/charliebilello/status/2118548764101091699)。

等权指数被写成在崩跌之前已经创新高，不要写成周四收盘。线外的 Bespoke 13:13 UTC：人工智能交易崩了的同时，标普等权指数昨天创出历史新高：[帖](https://x.com/bespokeinvest/status/2118330795396059321)。线外的 Sentimentrader 15:08 UTC：等权指数刚刚收在三年高点；从高点经过 5% 以上的回撤再回来，用了 57 个交易日；类似恢复之后，三个月后更高的比例是 83% 到 93%，相对标普 500 的领先往往会在之后一年里消退：[帖](https://x.com/sentimentrader/status/2118359682939314654)。“昨天”是 Bespoke 的句子。15:08 UTC 的“刚刚收在”发生在周四现货暴跌的上午。三年高点和历史新高并列，都不是 First Squawk 的周四收盘点位。

### 3. 亚洲跟着跌，美股期货在周五凌晨被买回去一截

收盘之后，期货先被写成继续跌。Kobeissi 23:12 UTC：纳斯达克 100 期货过去 12 小时的亏损扩到 -7.1%，抛售延续到盘后；标普较 10 月 6 日高点抹掉 5 万亿美元：[帖](https://x.com/KobeissiLetter/status/2118481733460930830)。-7.1% 是这 12 小时的期货句子。-6.4% 是现货收盘。5 万亿是从 10 月 6 日算的。CNBC 23:10 UTC 的标题仍是股指期货下跌、交易员等待就业报告：[帖](https://x.com/CNBC/status/2118481228588261883)。

亚洲开盘是另一张。First Squawk 23:52 UTC：日本基准 10 年期国债期货上涨 0.9 点，日经平均期货下跌 7%：[帖](https://x.com/FirstSquawk/status/2118491721982193942)。DeItaone：日经平均期货早盘 -7%：[帖](https://x.com/DeItaone/status/2118492133443108904)。随后日经平均指数 -5%：[帖](https://x.com/DeItaone/status/2118497422200508731)。再写成 -6.2%：[帖](https://x.com/DeItaone/status/2118499608078737511)。Kobeissi 00:06 UTC：韩国 KOSPI 暴跌 9%，触发交易暂停，是美国下跌之后第一次开盘；指数较纪录高点 -47%：[帖](https://x.com/KobeissiLetter/status/2118495095901315560)。First Squawk 00:37 UTC 写的是另一档：韩国交易所对 KOSPI 200 期货下跌 5% 启动 sidecar，程序化交易暂停五分钟：[帖](https://x.com/FirstSquawk/status/2118502886456058000)。-9% 是 KOSPI 现货并带有交易暂停。-5% 是 KOSPI 200 期货的 sidecar。-47% 是距纪录高点。零对冲：日经较 6 月高点低 20%：[帖](https://x.com/zerohedge/status/2118497622512062480)。彭博：日经 225 跌破 60,000：[帖](https://x.com/business/status/2118550213203726527)。CNBC：SK 海力士跌超 8%，三星电子跌 7%，台积电跌 9.6%，软银下跌：[帖](https://x.com/CNBC/status/2118553981383246055)。日本首相高市早苗说，市场动荡不只在日本，人工智能和半导体股票大幅下跌，正在密切关注：[帖](https://x.com/DeItaone/status/2118506572620157258)。台湾财政部次长：国安基金密切跟踪股市，如果市场失序或信心崩溃，可能召开紧急会议：[跟踪](https://x.com/financialjuice/status/2118517132736774493)、[紧急会议](https://x.com/financialjuice/status/2118517316111441937)。

美股期货随后被写成收复。First Squawk 01:47 UTC：标普 500 电子迷你期货抹掉跌幅后持平，纳斯达克期货上涨 0.6%：[帖](https://x.com/FirstSquawk/status/2118520508522307884)。02:28 UTC：纳斯达克期货涨超 1%：[帖](https://x.com/FirstSquawk/status/2118530901479153686)。LiveSquawk 02:30 UTC：纳斯达克期货 +1.3%，日经 -5.3%：[帖](https://x.com/LiveSquawk/status/2118531477105410289)。线外的 Newsquawk 06:53 UTC：纳斯达克下跌超过 6% 的那个交易日之后，亚太全线更低，KOSPI 最差并触发多次 sidecar；美国股指期货找到了底，欧洲股指期货指向更低的开盘：[帖](https://x.com/Newsquawk/status/2118597670876926267)。-7.1%、持平、+0.6%、涨超 1%、+1.3%、“找到了底”，按时间留着。抓取结束时没有比 +1.3% 更新的期货百分比，也没有周五现货点位。日经的 -7%、-6.2%、-5.3%、-5%，以及跌破 60,000、较 6 月高点 -20%，并列。

### 4. 海峡和谈的句子同时存在，黄金没有跟着油价的结算上涨

DeItaone 16:37 UTC：伊朗拒绝重开霍尔木兹海峡，称结束战争是 Rezaei 与普京会谈的主要焦点；海峡会一直关闭，直到七项条件满足：[帖](https://x.com/DeItaone/status/2118382097182167165)。16:40 UTC 的另一句是伊朗正在审阅核计划的新方案，可能有助于结束对美国的战争，引自《纽约时报》、五名官员；卡塔尔的调解在推进：[帖](https://x.com/DeItaone/status/2118382892250214858)。拒绝重开和正在审阅方案，按发帖顺序留着。LiveSquawk：伊斯兰革命卫队称在格什姆岛上空打下第六架美国 MQM-170 无人机：[帖](https://x.com/LiveSquawk/status/2118427509003817438)。

周五的外交句子转向降温。线外的 Javier Blas：特朗普致电卡塔尔埃米尔，讨论与伊朗正在进行的外交；多哈现在是德黑兰和华盛顿之间的主要中间人：[帖](https://x.com/JavierBlas/status/2118614609255141765)。油价落到 98 美元下方的那条 First Squawk，把降温希望和卡塔尔埃米尔的讨论写在一起。特朗普还有两句和油价不是同一张。FinancialJuice：被问到是否见了俄罗斯的德米特里耶夫，他说见了，而且非常接近解决俄乌战争：[帖](https://x.com/financialjuice/status/2118456906243088780)。Kobeissi：特朗普就当天的股市暴跌发表声明，称之为市场“历史上最差的日子之一”：[帖](https://x.com/KobeissiLetter/status/2118483781778551225)。彭博：特朗普把美国人 401(k) 的损失怪到民主党头上：[帖](https://x.com/business/status/2118546458412515828)。

库存是 Kobeissi 周五 02:49 UTC 的一张，原油减少 86.5 万桶这个数字和上一份日报里的周三句子相同，柴油和战略储备是这一帖多出来的句子。柴油库存上周减少 360 万桶，到 9,930 万桶，是 2003 年 5 月以来最低；2026 年 1 月以来馏分油库存减少 3,370 万桶，或 25%。战略储备上周减少 39.9 万桶，到 2.822 亿桶，是 1982 年 10 月以来最低；3 月以来减少 1.332 亿桶，或 32%。不含战略储备的商业原油减少 86.5 万桶，到 4.098 亿桶，是 7 月 31 日以来最低：[帖](https://x.com/KobeissiLetter/status/2118536096623571052)。86.5 万桶不要写成周五新的一周。360 万桶是柴油。39.9 万桶是战略储备的一周变化。

Peter Schiff 把黄金没有大涨写成市场还没看懂。他写昨天面对民主党压倒性胜利的上涨说不通，今天的抛售说得通，这样的日子还会有：[帖](https://x.com/PeterSchiff/status/2118375401143562716)。金银矿股不该跟着大盘跌；民主党的压倒性胜利、以及它对 2028 年的意味，是贵金属能遇到的最有利的发展：[帖](https://x.com/PeterSchiff/status/2118385685367332919)。如果交易员看懂了，黄金今天应该大涨；美国经济正在走向衰退，股票和房价会崩，美联储将被迫中止：[帖](https://x.com/PeterSchiff/status/2118453083063669167)。比特币被他写成没有价值，选举是最后一根针，现在就卖：[帖](https://x.com/PeterSchiff/status/2118401574653534499)。房利美和房地美的私有化被他写成已经不可能：[帖](https://x.com/PeterSchiff/status/2118394052785951039)。比特币在收盘综述里是下跌 5.4%、到 75,810：[帖](https://x.com/FirstSquawk/status/2118457252244058175)。DeItaone 盘中写成最多跌 5.8%、跌破 76,000、七周低点：[帖](https://x.com/DeItaone/status/2118383418618634505)。Gary 的收盘帖是 -6%。5.8%、5.4% 到 75,810、-6%，并列。

## 要盯住的五件事

1. **周四收盘有点位，也有四舍五入的百分比。** First Squawk：纳斯达克 24,305.70，跌 5.56%，跌 1,430.82 点；标普 7,355.81，跌 4.33%，跌 332.81 点；道指 51,515.81，跌 3.45%，跌 1,840.31 点。Morning Brew：纳斯达克 100 -6.4%，纳斯达克 -5.5%，罗素 2000 -4.5%，标普 -4.4%，道指 -3.4%。开盘是道指 53,686.75、涨 0.62%，纳斯达克 25,537.57、跌 0.77%，标普 7,675.76、跌 0.17%。“2025 年 4 月以来最差”和“2020 年以来最大”是两句。2.3 万亿、2.5 万亿和 3 万亿是三句。
2. **周五盘前期货没有一张新的收盘。** 盘后 Kobeissi 的纳斯达克 100 期货是过去 12 小时 -7.1%。凌晨先抹平，纳斯达克期货到过 +0.6%、涨超 1%、+1.3%。Newsquawk 06:53 UTC 写成期货找到了底，欧洲期货更低。抓取结束时现货没开。RedDog 要看的 680 美元，QQQ 在盘中已经被写成跌破：[先看 680](https://x.com/RedDogT3/status/2118319001151615186)、[跌破](https://x.com/RedDogT3/status/2118356860151673123)。
3. **WTI 结算是 90.52，布伦特结算是 98.29。** 沿途还有盘前的 96、综述里的 90.54、凌晨的 91.52、布伦特站上 100，以及周五标题里的布伦特 98 下方、WTI 在 90 附近。黄金是 4,099.15，然后 4,049.88，再是 4,050 下方。10 年期有 4.902%、4.87%、下跌 7 个基点、4.83%、4.85% 和 4.82%。
4. **初请是 189,000，生产率是 3.6%，单位劳动力成本的符号有两套。** 估计有 196,000 和 197,000。前值有 194,000 和修正后的 195,000。LiveSquawk 的单位劳动力成本是 +0.7%。零对冲、Liz Ann 和 DeItaone 是 -0.7%。非农还没公布。Gary 的共识是增加 65,000；他写超过 130,000 或负数会把抛售延长。12 月加息被他写成从 82% 降到 66%。
5. **VIX 的收盘句子不要用盘中的 +70%。** 盘中有 24、大约 +50%、+70%、+48%、高点 28.09。收盘帖有从 17 到 28，也有 +11.57 点。+11.57 点按点数被 SpotGamma 写成 1990 年以来第 17，按百分比排第三。熔断的 7% 位置 7,150.41 没有被写成已经触及。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 收盘点位 | 道指、标普、纳斯达克 | 纳斯达克 24,305.70，-5.56%。标普 7,355.81，-4.33%。道指 51,515.81，-3.45%。另一张百分比是纳斯达克 100 -6.4%、综合指数 -5.5%、标普 -4.4%、道指 -3.4%、罗素 -4.5% | [点位](https://x.com/FirstSquawk/status/2118449557944307879)、[百分比](https://x.com/MorningBrew/status/2118449382303695034) |
| 开盘 | 道指、标普、纳斯达克 | 道指 53,686.75，+0.62%。纳斯达克 25,537.57，-0.77%。标普 7,675.76，-0.17% | [开盘](https://x.com/FirstSquawk/status/2118350563197005886) |
| 盘中已经过期 | 纳斯达克 100、标普 | 先到 -3% 和 -1.3%，再到 -5.1% 和 -2.8%，再到超过 -6% 和 -3.7%。标普盘中到过 -4.1%，道指到过 -3.2% | [-6%](https://x.com/FirstSquawk/status/2118371323131085160)、[-4.1%](https://x.com/DeItaone/status/2118404453737115984) |
| 两句“最差” | 纳斯达克 100、标普 | Gary 和 Bilello：4.4% 是 2025 年 4 月以来最差。Kobeissi 的线程：纳斯达克 100 是 2020 年以来最大单日跌幅，标普抹掉 3 万亿。另有 2.3 万亿和 2.5 万亿 | [4.4%](https://x.com/garyblack00/status/2118467071960834122)、[2020](https://x.com/KobeissiLetter/status/2118455887413285205)、[2.3 万亿](https://x.com/DeItaone/status/2118451528981753938) |
| 波动率 | VIX | 盘中 24、+70%、+48%、高点 28.09。收盘从 17 到 28。收盘对收盘 +11.57 点 | [28.09](https://x.com/CNBC/status/2118383454001811495)、[+11.57](https://x.com/spotgamma/status/2118474418649174017) |
| 规则位置 | 标普熔断 | 跌 7% 的位置写成 7,150.41。收盘点位在这之上 | [7,150.41](https://x.com/DeItaone/status/2118374553789268091) |
| 跌破的位置 | QQQ | 680 美元被写成主要区域，随后被写成很快跌破 | [680](https://x.com/RedDogT3/status/2118319001151615186)、[跌破](https://x.com/RedDogT3/status/2118356860151673123) |
| 单日最深的一档 | SOXX、芯片指数 | SOXX -12%，被写成 2020 年 3 月以来最大单日百分比跌幅。综述里的芯片指数也是 -12% | [SOXX](https://x.com/garyblack00/status/2118467071960834122)、[芯片指数](https://x.com/FirstSquawk/status/2118457236985160060) |
| 三句百分比 | QCOM | 开盘 -14%。标题里 -9%。盘中 -13%，四季度略超、指引偏弱 | [-14%](https://x.com/LiveSquawk/status/2118350636898979878)、[-13%](https://x.com/CNBC/status/2118376531957297373) |
| 目标价 | ARM | 瑞银目标价 270 美元，原先 320。首席执行官说美国若犹豫，别处会接过数据中心 | [270](https://x.com/financialjuice/status/2118357091605987344)、[数据中心](https://x.com/TheTranscript_/status/2118401082141401299) |
| 两句收盘 | NVDA | 大约 -8%，今年至今大约 -2%。另一帖 -9.3%，今年至今 -3%。回购被写成 2,350 亿美元 | [大约 -8%](https://x.com/DeItaone/status/2118374995793527184)、[-9.3%](https://x.com/garyblack00/status/2118467071960834122) |
| 从高点算 | AMD | 盘中超过 -11%，也有 -12% 和 -12.2%。较 10 月 6 日 -35%，市值 3,800 亿美元 | [-11%](https://x.com/KobeissiLetter/status/2118353456255955415)、[-12.2%](https://x.com/Hedgeye/status/2118356071660057084) |
| 开盘和收盘 | TSLA、SPCX | 开盘 -3.9% 和 -4.3%。收盘帖 -11% 和 -9%。两日市值 4,500 亿、4,560 亿、5,000 亿 | [开盘](https://x.com/zerohedge/status/2118350533258011114)、[收盘帖](https://x.com/garyblack00/status/2118467071960834122) |
| 债券 | CRWV | 2032 年 7 月 15 日、票息 8.5% 的债券交易在 73 | [73](https://x.com/jimcramer/status/2118369179854082135) |
| 盘后 | DKNG | 2027 年预测不及，2026 财年展望下调，盘后 -19% | [-19%](https://x.com/business/status/2118462120266207421) |
| 两句跌幅 | SNDK | 开盘后名单 -15%。The Street 写成下跌 20%，尽管业绩强 | [-20%](https://x.com/TheStreet/status/2118458390598877204) |
| 市值标题 | 七巨头 | 盘中准备抹掉 1.1 万亿。收盘后标题是损失 1 万亿 | [1.1 万亿](https://x.com/DeItaone/status/2118372358746440149)、[1 万亿](https://x.com/CNBC/status/2118467318942515378) |
| 概率和承诺 | Anthropic | 上市概率 60% 以下，估值目标 1.5 万亿到 1.6 万亿。支出承诺 8,950 亿美元 | [概率](https://x.com/DeItaone/status/2118391560811278770)、[8950 亿](https://x.com/KobeissiLetter/status/2118397431729586495) |
| 州一级的暂停 | 数据中心 | 得州候任州长要在新法律之前停掉数据中心。Yardeni 写 76% 的选民反对社区里的新数据中心 | [暂停](https://x.com/KobeissiLetter/status/2118509115806818423)、[76%](https://x.com/yardeni/status/2118565616671916033) |
| 油的结算和夜里 | 原油、布伦特 | WTI 结算 90.52，+2.72%。布伦特结算 98.29，+3.88%。夜里到过 91.52，布伦特站上 100，周五标题落到 98 下方 | [90.52](https://x.com/FirstSquawk/status/2118426223894548805)、[98.29](https://x.com/FirstSquawk/status/2118429232443580776)、[100](https://x.com/FirstSquawk/status/2118549168029659226) |
| 贵金属 | 黄金 | 4,099.15，然后 4,049.88，再落到 4,050 下方。较历史高点 -24.5% 是另一句 | [4099](https://x.com/FirstSquawk/status/2118500808153248048)、[4049](https://x.com/FirstSquawk/status/2118542211759653023) |
| 已经公布 | 初请、生产率 | 初请 189,000。生产率 3.6%。单位劳动力成本有 +0.7% 和 -0.7% | [初请](https://x.com/FirstSquawk/status/2118335096117936195)、[+0.7%](https://x.com/LiveSquawk/status/2118335379103461811)、[-0.7%](https://x.com/zerohedge/status/2118335533005046252) |
| 还没公布 | 非农 | 共识被写成 +65,000。超过 130,000 或负数被写成会延长抛售。工资增速低于 3.0% 是路透的预览 | [65,000](https://x.com/garyblack00/status/2118467071960834122)、[工资](https://x.com/Reuters/status/2118586687651565995) |
| 亚洲 | 日经、KOSPI、海力士、三星、台积电 | 日经期货 -7%，现货有 -6.2% 和 -5.3%，并跌破 60,000。KOSPI -9% 并暂停交易。KOSPI 200 期货 sidecar 是 -5%。SK 海力士超过 -8%，三星 -7%，台积电 -9.6% | [-9%](https://x.com/KobeissiLetter/status/2118495095901315560)、[台积电](https://x.com/CNBC/status/2118553981383246055) |
| 已经公开的方向 | XLV、GS、SPY、DIA | Keith：6 月以来医疗是第一配置，XLV +26%，仍在做空高盛。Minervini 仍空着 SPY 和 DIA | [XLV](https://x.com/KeithMcCullough/status/2118384835463151763)、[仍空着](https://x.com/markminervini/status/2118449372421849324) |

## 后续走势：三套可以证伪的剧本

帖文没有给周五的收盘点位。抓取结束时现货没开。周四已经写下来的收盘，First Squawk 是纳斯达克 24,305.70、标普 7,355.81、道指 51,515.81。Morning Brew 的百分比是纳斯达克 100 -6.4%、综合指数 -5.5%、标普 -4.4%、道指 -3.4%。下面三套的顺序，以这张收盘、WTI 结算 90.52、布伦特结算 98.29、纳斯达克期货凌晨一度到 +1.3%、非农还没公布为前提。

**强制平仓在几天里止住，期货的反弹留到现货。** 触发器是 Tom Lee 把先前的关税冲击和 DeepSeek 都写成几天里见底的买入机会，Kobeissi 把当天写成技术性的、彻底的禁令不会发生。期货从过去 12 小时的 -7.1%，走到持平、+0.6%、涨超 1% 和 +1.3%，Newsquawk 写成找到了底。这条路径失败的条件，是现货不接受 7,355.81，重新走向 DeItaone 列出的 7,150.41，或者纳斯达克期货把凌晨的涨幅还回去、重新交易那张 -7.1%；就业报告落在 Gary 写的超过 130,000 或负数，而不是他写的共识 65,000 附近，也会把这条路径打断。

**数据中心和半导体的跌幅盖过指数期货的反弹。** 触发器是 SOXX -12%、芯片指数 -12%、高通盘中仍有 -13% 和 -14% 的句子、得州的数据中心暂停、Yardeni 的 76%，以及韩国 -9%、台积电 -9.6%。RenMac 把当天唯一上涨的一组写成饮料，人工智能的拥挤多头在别处找不到安慰：[帖](https://x.com/RenMacLLC/status/2118486712594928111)。这条路径失败的条件，是高通和 SOXX 的跌幅在现货里被买回去，QQQ 重新站上 RedDog 的 680，而且 Keith 做多的医疗不再强于他仍在做空的高盛和半导体。

**油价决定黄金是跟着海峡走，还是跟着抛售变现走。** 触发器是周四股票大跌的同时，WTI 结算涨 2.72%、布伦特结算涨 3.88%，和前一天油价大跌、股票上涨的方向对调。伊朗拒绝重开海峡的句子和正在审阅核方案的句子同一天都在。周五布伦特从站上 100 回到 98 下方，黄金从 4,099.15 落到 4,049.88。Schiff 写如果看懂了，黄金应该大涨。它失败的条件，是布伦特留在 100 上方、黄金却继续掉到 4,049.88 之下，那就是变现盖过了海峡；或者布伦特留在 98 下方、黄金重新站上 4,099.15，那就是降温和更低的收益率盖过了库存和无人机。

另有一张就业报告，不并进上面三套。初请 189,000 和生产率 3.6% 已经出来。单位劳动力成本的 +0.7% 和 -0.7% 还并列着。10 月非农抓取结束时没有数字。共识句子是增加 65,000。工资增速低于 3.0% 是预览，不是已经公布的数。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周五开盘和 8:30 的就业报告。它不决定仓位大小。现货还没开。

**开盘前只核对五样东西。** 期货是停在“找到了底”、纳斯达克期货一度 +1.3% 的那一侧，还是回到过去 12 小时 -7.1%；油价交易的是布伦特结算 98.29、夜里站上 100，还是周五标题里的 98 下方，90.52 是 WTI 结算，91.52 是凌晨的句子；黄金是停在 4,050 下方，还是回到 4,099.15；科技是继续 SOXX 的 -12% 和高通的 -13% 或 -14%，还是把凌晨期货的反弹留在现货里，680 是 QQQ 已经被写成跌破的位置；美国 10 年期是留在 4.82% 或 4.83%，还是回到暴跌前的 4.902%。五样里期货留住反弹、布伦特留在 100 下方、就业人数靠近 65,000 而不是超过 130,000 或变成负数，这些帖给出的默认顺序是强制平仓的技术性下跌，高于去追已经在数据中心标题里下跌的半导体。海峡被交易成重新关闭、布伦特留在 100 上方、标普期货重新掉向 7,150，默认顺序掉过头来：原油和黄金的反向映射，高于去抄纳斯达克 100 那 6.4%。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：下跌更多是技术性的，彻底的禁令不会发生，把时间拉长：[帖](https://x.com/KobeissiLetter/status/2118379488971043055)。收盘线程把纳斯达克 100 写成 2020 年以来最大单日跌幅，标普抹掉 3 万亿美元：[帖](https://x.com/KobeissiLetter/status/2118455887413285205)。盘后期货过去 12 小时 -7.1%：[帖](https://x.com/KobeissiLetter/status/2118481733460930830)。KOSPI -9% 并暂停交易，较高点 -47%：[帖](https://x.com/KobeissiLetter/status/2118495095901315560)。他们没有给周五的收盘点位。
- Gary Black，线外：收盘是纳斯达克 100 -6.4%、标普 -4.4%、VIX 从 17 到 28、SOXX -12%、英伟达 -9.3%、特斯拉 -11%、SpaceX -9%、12 月加息从 82% 到 66%、非农共识 +65,000。暴跌之前他写想买被打下来的高质量媒体和科技股，点名 Alphabet、Meta、亚马逊，估值低于 1.0 倍企业价值/EBITDA 相对 2027 到 2031 年收入增长：[帖](https://x.com/garyblack00/status/2118423360690635237)。
- Tom Lee：强制平仓，先前的冲击是几天里的买入机会，人工智能的故事没变；9 月加息开始看起来没有必要。
- Mark Minervini：仍空着 SPY 和 DIA，多头里有 Teva 和 IBB，收盘时还没平掉空头：[仍空着](https://x.com/markminervini/status/2118377687550996772)、[收盘后仍没平](https://x.com/markminervini/status/2118449372421849324)。他猜不是 1987 年那种百分比的崩盘，但可能走出一两周的下跌；标普自高点 10% 到 15%，最差 20%；纳斯达克可能跌 20% 到 25%；有可能是 1998 年那种周期熊市：[帖](https://x.com/markminervini/status/2118452116339531878)。
- Liz Ann Sonders：初请 189,000，续请 171.8 万，生产率 +3.6%，单位劳动力成本 -0.7%。她的单位劳动力成本符号和 LiveSquawk 的 +0.7% 不同。
- Peter Schiff：这样的下跌日还会有；金银矿股不该跟着跌；黄金应该大涨；比特币现在就卖。
- Charlie Bilello：标普 4.4% 是 1989 年以来第 37 大的下跌日，大跌日和大涨日常常挨在一起。价值股今年至今 +24%，成长股 -6%。半导体自 6 月底 -37%。
- Steve Hanke 这个窗口没有新的海峡通航艘数。他的帖在战争和通胀的政治句子上，没有新的指数点位。
- Michael Gayed：JOJO 指数目前持有的是做多国债，自 10 月 23 日那一周起已经连续三周信用关掉：[帖](https://x.com/leadlagreport/status/2118353959299563926)。
- Jim Cramer：纳斯达克 100 先在他写的情境低点反弹，随后跌破：[反弹](https://x.com/jimcramer/status/2118361493523829142)、[跌破](https://x.com/jimcramer/status/2118369268475605306)。CoreWeave 那只 2032 年债券在 73。Anthropic 得打折。CNBC 的标题是抛售还没结束，但不是又一次互联网泡沫。
- Keith McCullough，线外：医疗是 6 月以来的第一配置，XLV +26%；仍做空高盛：[XLV](https://x.com/KeithMcCullough/status/2118384835463151763)、[高盛](https://x.com/KeithMcCullough/status/2118441090303090741)。VIX 当天 +55%。
- Robin Brooks，线外：两日轧差标普 -2%，不要换成周四的 -4.4% 或 -4.33%。战争被他写成实际上已经结束，表演性的轰炸仍可能发生。偏鹰的委员会重新偏鸽。
- Ole Hansen，线外：这个窗口没有新的布伦特结算或标普点位。他的帖在运价和别的题目上。
- SpotGamma，线外：熔断规则，以及 VIX +11.57 点的排名。VVIX 当天超过 120；他写 VVIX 高于 125 之后，标普指数基金往后 10 天和 20 天的收益偏强：[帖](https://x.com/spotgamma/status/2118398021067219230)。
- RedDog，线外：QQQ 的 680 已经跌破。
- Bespoke，线外：等权指数昨天创出历史新高。这是暴跌当天上午写的“昨天”。
- Ryan Detrick，线外：今天的大跌是 2026 年第二次 5% 的温和修正，波动是投资要付的过路费：[帖](https://x.com/RyanDetrick/status/2118456149607641464)。
- Yardeni，线外：最差的一天对上 76% 反对新数据中心，正文在会员墙后面。
- First Squawk，线外：开盘和收盘点位、WTI 90.52、布伦特 98.29、凌晨的期货百分比，见上。
- 美联储的 Williams：关税的影响大体已经过去：[帖](https://x.com/FirstSquawk/status/2118641080791171359)。这是一句官员评论，不是利率决定。

**财报和数据的顺序。** 先看已经写进标题的高通、Arm、AMD、英伟达、特斯拉、SpaceX、CoreWeave 的债券、DraftKings 的盘后 -19%，以及 SanDisk 的 -15% 和 -20%。然后才是还没公布的 10 月就业报告。初请和生产率已经出来。单位劳动力成本先把 +0.7% 和 -0.7% 看成两套，再决定要不要用。英国央行的 4.00% 已经决定。抓取结束时，美国的非农还没有数字。

**明确留在观察、不放进计划的东西。** 不用还没开出的周五现货去倒推收盘，也不把开盘的 -0.17% 写成收盘。7,675.76 是开盘。7,355.81 是收盘点位。4.33% 和 4.4% 并列。纳斯达克 100 的 -6.4% 和综合指数的 -5.56%、-5.5% 并列。WTI 结算 90.52 和 90.54、91.52、90 附近并列。布伦特结算 98.29 和 +4%、站上 100、98 下方并列。黄金的 4,099.15、4,049.88 和较高点 -24.5% 并列。VIX 的盘中百分比和 +11.57 点并列。高通的 -14%、-9%、-13% 并列。英伟达的大约 -8% 和 -9.3% 并列。特斯拉的 -3.9% 和 -11% 并列。Robin Brooks 的两日 -2% 不是周四单日。Kobeissi 的原油减少 86.5 万桶和上一份日报里的周三数字相同，不当成新的一周。德意志银行的时间线没有读到。Cathie Wood、Ray Dalio 的主号这个窗口没有新的指数点位。Ray Dalio 有一条关于跌倒后再走钢丝的帖，没有目标价。Bill Ackman 有一条帖，没有目标价。Michael Burry 的帖是订阅墙链接，没有写出点位。Paul Krugman、Nouriel Roubini、Warren Buffett 这次没有可引用的新点位。Nick Timiraos 窗口内没有新帖。

## 帖文索引

收盘和开盘：[纳斯达克 24,305.70、标普 7,355.81、道指 51,515.81](https://x.com/FirstSquawk/status/2118449557944307879)、[百分比另一张](https://x.com/MorningBrew/status/2118449382303695034)、[开盘](https://x.com/FirstSquawk/status/2118350563197005886)。

油、金和收益率：[WTI 结算 90.52](https://x.com/FirstSquawk/status/2118426223894548805)、[布伦特结算 98.29](https://x.com/FirstSquawk/status/2118429232443580776)、[布伦特站上 100](https://x.com/FirstSquawk/status/2118549168029659226)、[黄金 4,049.88](https://x.com/FirstSquawk/status/2118542211759653023)、[10 年期 4.82%](https://x.com/FirstSquawk/status/2118628634110173204)。

抛售和就业：[纳斯达克 100 自 2020 年以来](https://x.com/KobeissiLetter/status/2118455887413285205)、[技术性下跌](https://x.com/KobeissiLetter/status/2118379488971043055)、[非农共识 65,000](https://x.com/garyblack00/status/2118467071960834122)、[初请 189,000](https://x.com/FirstSquawk/status/2118335096117936195)、[单位劳动力成本两套](https://x.com/LiveSquawk/status/2118335379103461811)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-06 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 295 条、彭博商业账号 322 条、《金融时报》70 条、《华尔街日报》67 条、《经济学人》132 条、零对冲 160 条、FinancialJuice 302 条、CNBC 90 条、《The Street》75 条、DeItaone 74 条、StockMKTNewz 50 条，是读穿窗口后的计数。德意志银行的 0 是读取失败。保罗·克鲁格曼、Cathie Wood、BBC Business、markets、沃伦·巴菲特、CNN Business、彭博主号、Andrew Ross Sorkin、美国财政部、高盛、Downtown、美国银行、TradingView、纽约时报商业、摩根大通、花旗、Hindenburg、Bloomberg Economics、CNBC Now、Nouriel、Carl Icahn、马克·库班的 0，是窗口内没有计为原创的新帖。线外的 First Squawk 是 278 条，LiveSquawk 是 126 条，不在这张表里。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,441,449 | 295 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,326,382 | 132 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,276,779 | 67 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,314,312 | 42 |
| 5 | [@business](https://x.com/business) | 10,490,602 | 322 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,568,417 | 0 |
| 7 | [@FT](https://x.com/FT) | 7,113,088 | 70 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,256,835 | 90 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,384,323 | 45 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,648,366 | 50 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,600,245 | 1 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,429,790 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,355,137 | 42 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,431,430 | 160 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,425,423 | 24 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,046,611 | 1 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,004,656 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,733,871 | 27 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,566,839 | 2 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,526,916 | 11 |
| 21 | [@chamath](https://x.com/chamath) | 2,486,566 | 4 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,439,473 | 8 |
| 23 | [@BW](https://x.com/BW) | 2,288,379 | 5 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,356 | 24 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,157,405 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,130,130 | 1 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,078,344 | 18 |
| 28 | [@markets](https://x.com/markets) | 2,048,555 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,971,083 | 74 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,795,241 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,776,478 | 12 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,884 | 34 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,710,113 | 10 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,700,748 | 8 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,648 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,615,862 | 23 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,602,932 | 2 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,536,802 | 73 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,512,403 | 1 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,471,292 | 20 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,673 | 3 |
| 42 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,356,181 | 5 |
| 43 | [@Bloomberg](https://x.com/Bloomberg) | 1,356,051 | 0 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,251,512 | 2 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,226,395 | 75 |
| 46 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,194,427 | 8 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,193,952 | 5 |
| 48 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,191,094 | 0 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,185,074 | 9 |
| 50 | [@USTreasury](https://x.com/USTreasury) | 1,165,907 | 0 |
| 51 | [@nntaleb](https://x.com/nntaleb) | 1,164,908 | 2 |
| 52 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,161,729 | 50 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,157,331 | 0 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,153,506 | 14 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,141,140 | 5 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,118,225 | 7 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,109,796 | 27 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,097,218 | 12 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,081,715 | 2 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,065,964 | 6 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,413 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,635 | 25 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,003,892 | 1 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 956,503 | 302 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,072 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 934,887 | 9 |
| 67 | [@tradingview](https://x.com/tradingview) | 907,006 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 894,213 | 17 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 890,771 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,502 | 17 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 874,220 | 10 |
| 72 | [@axios](https://x.com/axios) | 863,111 | 42 |
| 73 | [@steve_hanke](https://x.com/steve_hanke) | 862,087 | 29 |
| 74 | [@jpmorgan](https://x.com/jpmorgan) | 860,570 | 0 |
| 75 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 860,382 | 20 |
| 76 | [@Citi](https://x.com/Citi) | 853,171 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 847,879 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,628 | 2 |
| 79 | [@ecb](https://x.com/ecb) | 830,780 | 3 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,336 | 1 |
| 81 | [@bgurley](https://x.com/bgurley) | 812,405 | 1 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,328 | 1 |
| 83 | [@economics](https://x.com/economics) | 806,417 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 790,583 | 2 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,312 | 10 |
| 86 | [@markminervini](https://x.com/markminervini) | 769,520 | 6 |
| 87 | [@leadlagreport](https://x.com/leadlagreport) | 769,380 | 33 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 759,297 | 2 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,685 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 736,161 | 2 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 719,039 | 37 |
| 92 | [@CMEGroup](https://x.com/CMEGroup) | 712,187 | 4 |
| 93 | [@Nouriel](https://x.com/Nouriel) | 709,038 | 0 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 674,261 | 9 |
| 95 | [@fundstrat](https://x.com/fundstrat) | 673,417 | 6 |
| 96 | [@amitisinvesting](https://x.com/amitisinvesting) | 673,344 | 5 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 647,065 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,622 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 637,273 | 1 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 627,209 | 5 |
