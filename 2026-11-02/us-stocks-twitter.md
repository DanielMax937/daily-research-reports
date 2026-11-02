# 美股 Twitter 观点日报 · 2026-11-02

周一现货还没开。抓取结束时美东大约 5:17，现货 9:30 才开，10:00 的 ISM 制造业也还没有数。这个窗口里的新价格是周日晚场以后的期货、原油和黄金，不是收盘。帖文在交易三件事：油价因为“选举后再谈”往下掉，但霍尔木兹的条件并没有合成一句；人工智能的杠杆在被减，同时等权和“去掉人工智能的标普”仍被写成已经走在指数前面；苹果今晚财报、周二中期选举、周五非农挤在同一周。

下面每一条归纳都附有帖文链接。周日晚的百分比、周一凌晨的油价、高盛的预测价，按发帖原文分开。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-11-02**。触发时刻约 10:01 UTC，时间线补抓到 **约 10:17 UTC（北京时间 18:17，美东 5:17）**。美国夏令时已结束，这个 5:17 是东部标准时间。美股现货未开盘。
- 观察窗口从 **2026-11-01 10:17 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周日白天、周日 18:00 开出的股指期货晚场，以及美东周一凌晨到大约 5:17。上一份日报里的周五非官方收盘不在这里重算。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。抓取结束时美国趋势是 Halloween、Schumer、Andy Reid、Haley Stevens、Abdul、AIPAC。里面没有美股代码。Schumer、Haley Stevens、AIPAC 是选举话题，不是行情。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。
- 不存在官方的“美股 Top 100”。这次试了 **890** 个候选，成功读到粉丝数的有 **726** 个。排序时拿掉加密货币账号、综合新闻主号、科技风投和创始人、大型科技公司首席执行官、竞选和政治账号、公司产品品牌，以及《哈佛商业评论》、Inc.、Entrepreneur、Fast Company、Ezra Klein、Matthew Yglesias 这类不按美股讨论的账号。用来排序的账号是 **641** 个，截止在 Luke Gromen（637,224）。Eric Balchunas（627,453）落到第 101。First Squawk、Gary Black、Cboe、Barchart、Andy Constan、Jeffrey Gundlach、Earnings Whispers、Mad Money、Aswath Damodaran、Carl Quintanilla、美银新闻、LiveSquawk、瑞银、Nick Timiraos、日经亚洲、Keith McCullough、Fxhedgers、MacroAlf、Traderstewie、The Stalwart、Hedgeye、Javier Blas、Robin Brooks、Bespoke、SpotGamma、The Transcript、firstadopter、Ryan Detrick、Yardeni、RenMac 落在线外，引用时会写明。排序不代表预测准确度。
- 100 个账号里，**59 个**在窗口内有按帖文链接去重后、且接口没有标成回复的原创帖。路透读穿窗口，159 条。彭博商业账号 152 条。《金融时报》48 条。《华尔街日报》36 条。《经济学人》83 条。零对冲 45 条。FinancialJuice 112 条。Investing.com 31 条。《The Street》48 条。CNBC 23 条。unusual_whales 12 条。线外的 First Squawk 读穿窗口，262 条。德意志银行和 Daniel Newman 的时间线返回空结果，表里的 0 不是确认沉默。沃伦·巴菲特、彭博主号、彭博 markets、彭博经济、BBC Business、CNN Business、纽约时报商业、TradingView、CNBC Now、美联储官方账号这次窗口内仍是 0，沿用上一份日报已经写明的停更时间线，这次没有新帖推翻那条观察。

## 现货没开，期货、油和黄金是三张报价

周五的非官方收盘仍是上一份日报里的那一组：纳斯达克综合指数 25438.40、标普 7578.14、道指 51763.41。这个窗口没有新的现货收盘帖去替换它们。

周日晚场开出来的第一组期货百分比是上涨，而且只有这一组带数字。First Squawk 23:05 UTC：标普 500 期货涨 0.3%，纳斯达克期货涨 0.4%：[帖](https://x.com/FirstSquawk/status/2117030271182901627)。Investing.com 同一时段的标题是周日晚盘期货上涨、VIX 下跌，没有另给一个百分比：[帖](https://x.com/Investingcom/status/2117031144222756870)。周一 09:41 UTC，《华尔街日报》市场账号的标题是“期货更高、油更低，投资者回到风险资产”，标题里没有新的期货百分比：[帖](https://x.com/WSJmarkets/status/2117190297184579616)。0.3% 和 0.4% 停在周日 23:05。后面的“更高”不要改写成一个新的点数。

同一条亚洲综述把周五写成另一张图。First Squawk 00:50 UTC：纳斯达克 100 周五跌 3.5%，费城半导体指数跌 7.2%；美股期货至少反弹 0.3%；布伦特跌 1.6% 到每桶 111.60 美元；黄金升到 3900 美元附近：[帖](https://x.com/FirstSquawk/status/2117056756904067404)。3.5% 是纳斯达克 100。25438.40 是上一份日报的综合指数收盘。7.2% 是半导体指数。不要互相替换。

油价在这条 111.60 之后又有三张帖，都不要并成一个结算价。First Squawk 00:58 UTC：布伦特和 WTI 再跌 2 美元，没有新的绝对价格：[帖](https://x.com/FirstSquawk/status/2117058726171709919)。02:32 UTC：美国原油价格跌破前一交易时段，原油跌超过 3 美元，到每桶 101.11 美元：[帖](https://x.com/FirstSquawk/status/2117082453722710306)。02:33 UTC：布伦特跌超过 3 美元，到每桶 110.37 美元，接近一周多以来的低位：[帖](https://x.com/FirstSquawk/status/2117082763337826733)。09:17 UTC 的标题是布伦特跌 4%，因为美国和伊朗的战争有望得到解决，标题里没有新的绝对价格：[帖](https://x.com/FirstSquawk/status/2117184206765969679)。111.60、再跌 2 美元、101.11、110.37、跌 4%，是五句。

线外的 Ole Hansen 06:39 UTC 用的是 1 月合约：布伦特跌 3%，1 月合约 110 美元，周五曾交易在 114 美元上方。他把下跌写成特朗普希望在周二中期选举之后、可能恢复打击之前，先给和伊朗的外交更多时间。卡塔尔和伊朗官员还在谈，海峡附近仍有船只遇袭。欧佩克+把产量目标维持到 12 月。高盛把布伦特预测提高到 12 月 105 美元、2027 年平均 88 美元：[帖](https://x.com/Ole_S_Hansen/status/2117144450090549297)。110 美元、跌 3%、114 上方，是这张 1 月合约。110.37 是 First Squawk 的另一句。105 和 88 是高盛预测，不是现货。

合约换月被单独写出来。线外的 Rory Johnston 周日 23:46 UTC：2027 年 1 月布伦特本周开局只是滑了一点（“还没开战”）；但周五是 2026 年 12 月合约的最后交易日，所以滚动近月看起来像被砸得很惨。左边是滚动近月，右边是新的近月 2027 年 1 月：[帖](https://x.com/Rory_Johnston/status/2117040683282210848)。“滑了一点”和“跌 4%”的标题不要合成。

高盛的油价预测还有两张通讯社帖，和 Ole 的 105 / 88 并列，不覆盖。First Squawk 周日 22:48 UTC：高盛把 2026 年 12 月布伦特预测从 90 美元上调到 105 美元：[帖](https://x.com/FirstSquawk/status/2117026119530713153)。线外的 LiveSquawk 周一 07:57 UTC 的标题是，高盛上调油价预测，并警告布伦特 2027 年可能到 140 美元：[帖](https://x.com/LiveSquawk/status/2117164145556467872)。90 到 105、2027 年平均 88、2027 年可能 140，是三句。

黄金也有两套百分比。First Squawk 00:20 UTC：黄金最多反弹 0.7%，到接近每盎司 3900 美元；周五跌了 3.7%，是 2008 年以来最差的 10 月；油价下来减轻了通胀担忧，抄底盘回来了；现货黄金涨 0.6% 到 3899.39 美元，白银涨 1.3% 到 49.76 美元：[帖](https://x.com/FirstSquawk/status/2117049268758548721)。Ole Hansen 周日上午的复盘是另一套：周五跌破 3970 美元的关键支撑，收在 3900 下方、一年低点，10 月跌 12.7%，是全球金融危机以来最差的 10 月；对冲基金黄金期货净多已降到 10.7 万张，只比今年低点高 1.5 万张；金银比升到近 79，是 11 个月高点；收在 2025 年 10 月修正低点 3886 下方会进一步走弱，回到 4000 上方才开始修复短期图形。加息预期在他那里已经从三次收成两次：[帖](https://x.com/Ole_S_Hansen/status/2116838096633200933)。他周一 06:39 UTC 又写，黄金反弹 1% 到 3915 美元，10 月跌幅写成 6.8%；白银反弹 2.3% 到 50.20 美元：[帖](https://x.com/Ole_S_Hansen/status/2117144450090549297)。3899.39、3915、0.6%、0.7%、1%、周五 3.7%、10 月 12.7%、10 月 6.8%，按原帖留着，不取平均。

## 观点分成四组

### 1. 等权已经跑赢，科技的自由现金流被写成转负

Kobeissi 把 10 月写成领导权在换。等权标普跑赢标普 5.7 个百分点，是 2009 年 4 月以来最大的月度超额，也是 1990 年代以来第二大。等权 10 月涨 4.8%，标普跌 0.9%。年初至今等权涨 13.9%，标普涨 10.7%。“不含人工智能的标普”年初至今涨 14.2%，周五创历史新高：[帖](https://x.com/KobeissiLetter/status/2116916423138132362)。4.8%、跌 0.9%、5.7 个百分点、13.9%、10.7%、14.2%，都是这一条。

线外的 Ryan Detrick 用的是另一张 10 月差：等权跑赢市值加权 5.9%，史上第二大，只有 2009 年 4 月更大：[帖](https://x.com/RyanDetrick/status/2117026847871381507)。5.9% 不要改成 Kobeissi 的 5.7 个百分点。他另写，价值股 10 月跑赢成长股超过 10 个百分点，是 2000 年末到 2001 年初以来最多：[帖](https://x.com/RyanDetrick/status/2116939914629570642)。Magnificent 7 的三季度同比每股收益只有 22.6%，而且只有五家已经公布，苹果和英伟达还没有；其余 493 家是 32.6%。他写成这有可能是 2022 年四季度以来第一次 493 家更好：[帖](https://x.com/RyanDetrick/status/2116918400832393530)。22.6% 和 32.6% 是这组，不是指数涨跌。

线外的 Stephanie Link 的 10 月句子又是一套：标普跌 93 个基点，但 11 个行业里 9 个上涨，500 只里 327 只涨了 2% 或更多，站上 50 日均线的比例从 20% 升到 61%。摩根士丹利大宗经纪看到史上最大的一次去杠杆。她的结论是年底的设置看起来相当好：[帖](https://x.com/Stephanie_Link/status/2116918384180809867)。93 个基点和 Kobeissi 的跌 0.9% 都是 10 月，不合并成一个新数字。

自由现金流是 Kobeissi 的另一条。亚马逊、Alphabet、Meta、微软四家三季度资本开支合计增加 369 亿美元，到纪录的 2019 亿美元。这个数字 12 个月里翻了一倍多，相对 2024 年一季度涨 356%。过去三年资本开支合计 1.6 万亿美元。四家合计自由现金流上季度减少 331 亿美元，到负 264 亿美元，是纪录低位；过去一年减少 882 亿美元。三季度只有微软的自由现金流为正。向前看，这四家计划四季度再花 2320 亿美元资本开支，2026 年合计有可能到纪录的 7400 亿美元：[帖](https://x.com/KobeissiLetter/status/2116900354717589597)。2019 亿、负 264 亿、2320 亿、7400 亿，都是这四家的句子。

他把私人部门的信息处理设备和软件投资写成占 GDP 的 5.4%，高于 2000 年四季度的前高 4.5%。三季度年化增长 7.3%，是 1983 年四季度以来最大的季度增幅；2000 年互联网泡沫高点是 6.2%。2022 年四季度以来这项投资增了 61%，即 6710 亿美元，到纪录的 1.77 万亿美元：[帖](https://x.com/KobeissiLetter/status/2116996835621621916)。5.4% 和 4.5% 是占 GDP。7.3% 和 6.2% 是增速。

线外的 Sonali Basak 引的高盛资本开支观察是另一张表：人工智能基础设施的盈利扩张，预计从同比跳升 80%，到明年晚些时候接近 40%。明年预计支出 1.2 万亿美元，支出本身还在，但是在见顶。她把这写成市场在按一个新现实修正：[帖](https://x.com/sonalibasak/status/2116968836612456623)。1.2 万亿是这条“明年”的句子，不要加进 Kobeissi 的 7400 亿。她的利率句子是：利率更高、更久的路径上，更 exuberant 的股票在被重新定价；主要人工智能公司的筹资会慢下来，尤其是经营利润率更薄、杠杆更明显的那些，这不必是灾难性的放缓。她的团队今年仍看到再加一次息的可能，油价是变数，高油价可能开始破坏需求，但宏观里还没看到。超配科技的日子很难过，但资金流向质量、交易变宽仍有机会，部分科技已经在腾进场位置：[帖](https://x.com/sonalibasak/status/2116889296661594241)。

零对冲引的摩根士丹利大宗经纪把仓位写成已经转空。对冲基金对更宽的人工智能交易转为低配，是 2023 年初以来第一次。夏天加上 10 月的去杠杆，是 15 年以上多空基金持续降风险最长的一段，总敞口在两段之间没有完全恢复。累计总资金流较 6 月高点下降 8%，是纪录上最长的一段持续去杠杆。这一周的买入主要来自空头回补，美国多空净杠杆因此上升 5 个百分点到 51%，总杠杆降 1 个百分点到 207%：[帖](https://x.com/zerohedge/status/2117082767590650199)。“史上最大的一次去杠杆”是 Stephanie 的句子。下降 8%、净杠杆 51%、总杠杆 207%，是零对冲这条摩根士丹利帖。

Jim Bianco 把周五之后的人工智能写成近两年第七大抛售，ChatGPT 2022 年 11 月发布以来涨过 500%，历史高点在 10 月 6 日，不到一个月前：[帖](https://x.com/biancoresearch/status/2116934214335520777)。线外的 peruvian_bull 用的是瑞银人工智能赢家篮子：较高点 10 月 6 日回撤 13.5%，是 ChatGPT 发布以来第七大回撤，图来自 Bianco：[帖](https://x.com/peruvian_bull/status/2117133884555219185)。第七大抛售和 13.5% 的篮子回撤是两句。他另写，中国 STAR 50 科技指数自 6 月 30 日高点跌了 47%：[帖](https://x.com/peruvian_bull/status/2116950874690072936)。

Charlie Bilello 把周五标普跌 1.8% 写成今年第 22 次单日跌超 1%，1928 年以来平均一年有 29 次：[帖](https://x.com/charliebilello/status/2117000719001588157)。1.8% 是他的周五句子。他的年内利润句子是，标普利润今年有望增 35%，2027 年再增 15%，两年 55%：[帖](https://x.com/charliebilello/status/2117028806469058667)。线外的 SpotGamma 把周五写成 6 月以来最大的抛售，VIX 相对标普跌 1.8% 的反应偏轻；收盘时期权、尤其是认沽看起来贵，需要更陡的已实现下跌才配得上这个价格：[VIX](https://x.com/spotgamma/status/2116967245796487441)、[认沽](https://x.com/spotgamma/status/2116991918546784473)。

### 2. 选举之后打还是谈，霍尔木兹的条件还在

外交和打击被写成同时准备着。CNBC 的标题是，鲁比奥说特朗普希望“和平地”结束伊朗战争，与此同时双方都在为打击做准备：[帖](https://x.com/CNBC/status/2117084613340266866)。Kobeissi 引 Axios：内塔尼亚胡在“推动”特朗普于周二中期选举之后立刻打击伊朗；以方消息把通话写成 tough，美方消息写成 direct。帖里写特朗普说美国仍要“处理”伊朗一到两处核设施：[帖](https://x.com/KobeissiLetter/status/2116975383077904829)。线外的 Javier Blas 引的是同一通通话的另一半：内塔尼亚胡要选举之后立刻打，特朗普目前想让谈判走下去，内塔尼亚胡担心这个策略：[帖](https://x.com/JavierBlas/status/2116971468630507657)。“立刻打”和“先让谈判走”是这一通通话里的两句。

伊朗方面的条件按时间留着，不并成“谈判已经成了”。DeItaone 引阿拉格齐：和卡塔尔调解人的谈判还在进行、有进展，但还没有定论：[帖](https://x.com/DeItaone/status/2116881976581927337)。周一上午 First Squawk 引巴加埃：和美国的外交基础是伊朗的七步方案，未来几天有落实的机会：[帖](https://x.com/FirstSquawk/status/2117156814466978224)。同一小时又写，霍尔木兹在美国制裁解除之前不能重开：[帖](https://x.com/FirstSquawk/status/2117160364546957716)。万斯的信没有提供新基础，要求没变：[帖](https://x.com/FirstSquawk/status/2117166356147913183)。还没到和美国谈核问题的阶段：[帖](https://x.com/FirstSquawk/status/2117170557364167010)。谈判能否开始，取决于海上封锁是否结束：[帖](https://x.com/FirstSquawk/status/2117163157202538708)。德黑兰不预期中期选举之后会出现一个“新的美国”：[帖](https://x.com/FirstSquawk/status/2117166233221300338)。七步方案、制裁不解除就不重开、封锁不结束就不谈，是三句。

现场仍有遇袭。DeItaone 引伊朗国营媒体：两艘油轮在霍尔木兹“未经许可的航线”上触雷：[帖](https://x.com/DeItaone/status/2116985225024504163)。路透的标题是，伊斯兰革命卫队海军说两艘油轮触雷后爆炸：[帖](https://x.com/Reuters/status/2117051608190144626)。“两艘”是这两条。不要和上一份日报里的船次计数加总。

中国的句子是另一边。线外的 Javier Blas：中国对霍尔木兹的立场在变硬，而且是对着伊朗。中国和阿曼周一的联合公报写，双方认为海峡应当恢复正常、安全开放通航：[帖](https://x.com/JavierBlas/status/2117196115443646643)。他的专栏把美国天然气写成页岩革命让美国消费者躲开了这场冲突的经济后果，并引特朗普说“我们在赚一大笔”：[帖](https://x.com/JavierBlas/status/2117190842297557189)。阿布扎比国家石油公司首席执行官的句子是，能源安全现在不只量在生产端，也量在交付端：[帖](https://x.com/JavierBlas/status/2117156124839551473)。

Steve Hanke 周日仍把海峡写成实际上危险、功能上关闭：[帖](https://x.com/steve_hanke/status/2116908873818800442)。他 21:55 UTC 回财政部长的上一句：世界离得开伊朗的油是真的，但价格会高得多；他问贝森特知不知道布伦特刚刚到了每桶 117.70 美元：[帖](https://x.com/steve_hanke/status/2117012556011192463)。117.70 是他周日晚的这句，早于上面 111.60 和 110.37 的周一报价。他另写，沙特经济三季度同比收缩 3.8%，连续第二个季度；石油活动骤降 20.4%。他把这写成对伊朗的战争在拖累王国：[帖](https://x.com/steve_hanke/status/2117105921201430534)。

Scott Bessent 这条窗口里的能源帖不是油价，是产量。美国原油和天然气产量相对拜登政府最后一年增加每天 310 万桶油当量。他的句子是“生产带来繁荣”：[帖](https://x.com/SecScottBessent/status/2116953954311676032)。310 万桶油当量不要换成 117.70 或 110。

线外的 Robin Brooks 周日上午仍按热战回来做映射：布伦特再涨 10%，对应黄金跌 4%、白银跌 8%：[帖](https://x.com/robin_j_brooks/status/2116846273575657650)。这是“如果回到热战”的映射。周一上午的磁带是油价往下、黄金从周五低点往上，和这张映射的方向相反。映射本身没有被他撤回。

Cramer 周一 09:28 UTC 把开盘前写成良性：油更低，利率更低，除了科技之外没有超卖。他又写，特朗普再次放出消息，中期选举之后海湾地区可能什么也不会发生：[帖](https://x.com/jimcramer/status/2117187066907836687)。09:56 UTC 他补了一句，SK 海力士在涨，是好迹象，并问上周是不是有对冲基金爆仓，要看卖盘会不会回来：[帖](https://x.com/jimcramer/status/2117194153532731881)。“可能什么也不会发生”是 Cramer 转述的特朗普消息。Kobeissi 帖里的“仍要处理一到两处核设施”是另一句。

Raoul Pal 的框架发在周日 11:19 UTC，早于油价下滑：美元、利率和油价一起往上，三者都在收紧金融条件，流动性跟着紧，市场跟着紧。加密需要这三者散掉。他写特朗普到中期选举想把油价、利率和美元打下来，油价大概要靠一个伊朗解决方案。那才会重新打开冒险、把资本带回市场：[帖](https://x.com/RaoulGMI/status/2116852542638264735)。这是他周日中午的条件。周一凌晨油价已经往下，美元和美国 10 年期在这个窗口里没有一张带数字的新报价可以拿来核对后半句。

### 3. 这周的日历比昨天的收盘更密，债券账户在看收益率

Kobeissi 的一周清单是：周一 10 月 ISM 制造业；周一苹果和 Palantir 财报；周二美国中期选举；周二 9 月 JOLTS；周二 AMD 和超微电脑财报；周三 10 月 ADP；周三 ISM 非制造业；周五就业报告；周五密歇根通胀预期和消费者情绪；本周大约 20% 的标普公司公布财报；本周 5 场美联储讲话：[帖](https://x.com/KobeissiLetter/status/2116885664780231025)。抓取结束时，ISM、苹果和 Palantir 的结果都还没有帖。

线外的 Earnings Whispers 把本周最受关注的公布写成苹果、Palantir、AMD、1stDibs、AppLovin、Aehr、高通、AMC、Shopify、Moderna：[帖](https://x.com/eWhispers/status/2117039745305858171)。超微电脑的共识每股收益 1.16 美元被他写成没有意义、应当忽略：[帖](https://x.com/eWhispers/status/2116914435918872758)。1.16 是他要求忽略的共识，不是结果。

线外的 Bespoke：苹果和 Palantir 在周一收盘后。雅诗兰黛、福克斯、万豪在开盘前。古尔斯比周一 11:15 与国际清算银行对谈，爱德华生命科学同一天有投资者日：[财报](https://x.com/bespokeinvest/status/2117021489773826439)、[古尔斯比](https://x.com/bespokeinvest/status/2117022748421869909)。11:15 的讲话在抓取结束之后。

Mike Wilson 的路径经由 StockMKTNewz，不是摩根士丹利官方账号。他看到标普先跌到 7100，再涨到 8000。几件“出清事件”可能把标普从最近的纪录打下大约 9%：中期选举、对人工智能开支的压力、更紧的流动性。之后他预期回抽。摩根士丹利的数据是，1950 年以来每次中期选举之后 6 个月和 12 个月标普都更高：[帖](https://x.com/StockMKTNewz/status/2116948821192171527)。7100、8000、大约 9%，是这一条。Seeking Alpha 的标题是“跌 9% 然后涨到 8000”，没有写出 7100：[帖](https://x.com/SeekingAlpha/status/2116960979011739783)。线外的 Barchart 用的是更长的历史句子：过去 75 年，中期选举之后 6 个月和 12 个月标普都更高：[帖](https://x.com/Barchart/status/2116944547762569391)。1950 年以来和过去 75 年是两句。

线外的 Ryan Detrick 把季节性写成一串可以核对的比例，不是点位。11 月是 1950 年以来平均最好的月份，过去 20 年第二好，过去 10 年最好，中期选举年里第二好：[帖](https://x.com/RyanDetrick/status/2116929853266034855)。中期选举年里，没有哪个月比 11 月更经常收涨，概率 78.9%：[帖](https://x.com/RyanDetrick/status/2117030459175546970)。中期选举年里，10 月和 11 月从未同时下跌；五次 10 月下跌之后，11 月都涨回来。12 月只跌过一次，就是特朗普上次在任时那次 9.2%：[帖](https://x.com/RyanDetrick/status/2117031590438359067)。未来六个月历史上是最好的半年，中期选举年里 11 月到 4 月 19 次里 19 次上涨：[半年](https://x.com/RyanDetrick/status/2117040274064933126)、[19 次](https://x.com/RyanDetrick/status/2117040770217853295)。78.9%、五次、9.2%、19 次，都是他的历史句子，不是本周的预测点位。

利率没有一张美国 10 年期的新点位。《华尔街日报》市场账号的标题是，亚洲交易时段美债收益率基本持平，市场在等中期选举和本周的关键数据：[帖](https://x.com/WSJmarkets/status/2117152952259342534)。CNBC 的标题是，油价大跌、中期选举之前，美债收益率涨跌互现：[帖](https://x.com/CNBC/status/2117187639455470070)。“基本持平”和“涨跌互现”是两张标题。英国国债有数字，不能当成美国国债。First Squawk：英国 10 年期跌 5 个基点到 5.23%，是 2023 年 9 月以来最低：[帖](https://x.com/FirstSquawk/status/2117182603845632261)。30 年期当天跌超过 7 个基点，到 5.648%，是 8 月 7 日以来最低：[帖](https://x.com/FirstSquawk/status/2117193438622081295)。

线外的 DataTrek 给了一个基金兴趣的门槛，不是今天的收益率：美国基金投资者最近几周对利率非常敏感，10 年期超过 5.2% 会引起他们对这个资产类别的兴趣，低于这个水平兴趣很快消退：[帖](https://x.com/DataTrekMB/status/2117003111676174381)。5.2% 是这道门槛。他的就业句子是，最近四周初请平均刚刚创下回到 2022 年初的新低，而 2022 年初那个低点又是回到 1960 年代末的低点。美国企业仍然很不愿意裁员，尽管油价和利率都高：[帖](https://x.com/DataTrekMB/status/2116995595676373163)。帖里没有写出那个初请的绝对数字。

加息的句子按账号留着。Bilello：核心 PCE 已经连续 67 个月高于美联储 2% 的目标，货币政策仍然太松，还会有更多加息：[帖](https://x.com/charliebilello/status/2117012211369738547)。Peter Schiff：问到以当前经济和通胀展望、为什么 10 月没加息，沃什没有回答这个问题。他回应了，但那个回应并不构成答案，因为不想说实话：[帖](https://x.com/PeterSchiff/status/2116900672969064477)。Michael Gayed：劳动力市场这么软，吸收不了加息；他认为美联储在往放缓里加息，债券市场知道：[软](https://x.com/leadlagreport/status/2116874154393612362)、[放缓](https://x.com/leadlagreport/status/2116945971812716852)。线外的 RenMac 标题是通胀风险在上升、美联储可能再加息，正文是视频链接，没有新的概率：[帖](https://x.com/RenMacLLC/status/2116946675025490050)。Ole Hansen 写的是市场已经把进一步加息从三次收到两次。67 个月、再加一次、从三次收到两次，是三套。

选举定价也有两套。Bilello 引 Polymarket：民主党横扫（同时拿回众议院和参议院）的概率 71%，是到目前最高，他写成“是通胀，笨蛋”：[帖](https://x.com/charliebilello/status/2117031004225556904)。Schiff 写的是民主党拿下参议院的赔率升到 72%，新高。他把共和党表现差写成经济比特朗普上台时更差、但共和党仍说经济在繁荣：[帖](https://x.com/PeterSchiff/status/2116929600957939871)。71% 的横扫和 72% 的参议院不是同一个合约。

国债供给有两个写法。线外的 Barchart：美国财政部上周借入纪录的 8390 亿美元：[帖](https://x.com/Barchart/status/2117085608522686568)。unusual_whales：财政部刚完成纪录最大的拍卖周，8390 亿美元里大部分是滚动到期债务：[帖](https://x.com/unusual_whales/status/2117148703060537511)。“借入”和“大部分是滚到期”是两种说法，数字都是 8390 亿。线外的 Gold Telegraph 另写，2026 年要再融资的到期债务是 9.7 万亿美元，并把大型科技被抹掉的市值写成将近 1 万亿美元：[9.7 万亿](https://x.com/GoldTelegraph/status/2117099522715496535)、[将近 1 万亿](https://x.com/GoldTelegraph/status/2117012427137220713)。9.7 万亿是全年到期再融资，8390 亿是上一周。

线外的 Keith McCullough 周一开盘前的风险条目是：周五之后纳斯达克处于 8% 的回撤；周五卖盘放量；高收益债期权调整利差周五扩了 17 个基点；他所说的 CNBC 那类散户周五又跌了 5.6%：[回撤](https://x.com/KeithMcCullough/status/2117196228031397997)、[利差](https://x.com/KeithMcCullough/status/2117197500255797729)、[5.6%](https://x.com/KeithMcCullough/status/2117198762137510302)。8%、17 个基点、5.6% 都是周五的句子，不是周一期货。

### 4. 苹果今晚考试，OpenAI 的新融资标题是 200 亿美元

苹果被写成今年 Magnificent 7 里唯一跑赢标普的一只。Bilello 的理由是，它的自由现金流比其他六家都多，同时又大体避开了正在抽干超大规模云厂商的人工智能开支：[帖](https://x.com/charliebilello/status/2116995004883255763)。他的距高点表：苹果跌 2%，标普跌 3%，微软跌 6%，Palantir 跌 14%，英伟达跌 16%，亚马逊跌 17%，特斯拉跌 20%，Meta 跌 23%，AMD 跌 24%，黄金跌 31%，谷歌跌 32%，比特币跌 39%，SpaceX 跌 41%，奈飞跌 54%：[帖](https://x.com/charliebilello/status/2117004450137289143)。这些百分比是距各自高点，不是周五或 10 月。

线外的 Barchart：苹果超过英伟达，成为全球市值最大的公司：[帖](https://x.com/Barchart/status/2117053477428048110)。线外的 Bespoke：超大盘最近的走势很乱，苹果和微软是仅有的两个上升趋势，Alphabet 已经掉下悬崖：[帖](https://x.com/bespokeinvest/status/2116878138139402307)。彭博周一的标题是，苹果股价近几个月涨出来的这 1 万亿美元，让今晚财报没有犯错的余地：[帖](https://x.com/business/status/2117197550692237607)。路透的标题是，新任首席执行官特努斯面对第一次财报考试，内存成本在飙：[帖](https://x.com/Reuters/status/2117169879648178610)。StockMKTNewz 的首席执行官年表把库克写成 2011 年到 2026 年，特努斯从 2026 年起：[帖](https://x.com/StockMKTNewz/status/2117069637896835436)。1 万亿美元是涨幅句子。距高点跌 2% 是另一张表。

OpenAI 的融资标题在周一早上更新了。First Squawk 引 CNBC：OpenAI 寻求 200 亿美元新融资：[帖](https://x.com/FirstSquawk/status/2117196993231786126)。下一条：这笔新融资达不到此前 300 亿美元的目标：[帖](https://x.com/FirstSquawk/status/2117197262992613570)。200 亿和 300 亿是这一对。上一份日报里的“最多 200 亿美元、估值 1.25 万亿美元、经常性收入 500 亿美元”没有在这个窗口被一张新帖改写，这里不重复成新事实。Axios 的新句子是选举之后的公关：中期选举一过，OpenAI 会放出政策和公关攻势，包括把数据中心重新叫成“人工智能计算园区”：[帖](https://x.com/axios/status/2116889969432150442)。CNBC 另写，阿尔特曼突然访问韩国，OpenAI 在芯片合作上加码：[帖](https://x.com/CNBC/status/2117089789283344777)。

存储链在分化。零对冲：铠侠股价跌 14%，利润预测不及估计：[帖](https://x.com/zerohedge/status/2117052258516947439)。彭博的标题没有 14% 这个数字，只写展望谨慎、投资者担心人工智能带来的爆发式增长可能在走平：[帖](https://x.com/business/status/2117052853017539001)。14% 只挂在零对冲这条。Cramer 的 SK 海力士是上涨。Kobeissi 的韩国宏观是另一条：三季度经济环比增 1.0%，预期 0.8%，连续第三个季度扩张；出口增 2.3%，设备投资增 4.1%；同比增 3.4%，预期 3.0%。韩国有望在 2026 年第一次让年出口超过 1 万亿美元：[帖](https://x.com/KobeissiLetter/status/2117024379481509961)。1.0%、3.4%、1 万亿美元出口，都不是铠侠的股价。

Anthropic 有三句，都不是估值更新。Jeffrey Gundlach：Anthropic 希望拿到投资级债券评级，简直荒谬；任何可能给出这种评级的评级机构都该被调查、立刻关掉：[帖](https://x.com/TruthGundlach/status/2117118928963133625)。Michael Burry 发了一篇题为 “Short thoughts: Anthropic's S-1” 的笔记链接，窗口里的正文没有摘出论点：[帖](https://x.com/michaeljburry/status/2117048379469406713)。Cramer：外面那些空头的目标是搅黄 Anthropic 的上市，那会是最后一根稻草：[帖](https://x.com/jimcramer/status/2116989356082954676)。彭博电视引 Howard Marks：最近和人工智能有关的市场踉跄，多少戳破了这个行业不会出错的泡沫：[帖](https://x.com/BloombergTV/status/2117153036166459868)。

电力仍被写成硬约束。Chamath：现在能不成比例地塑造人工智能的，是那个把电力、数据中心、芯片和模型收成一个在经济上说得通的终点的人。电力是绑定约束，而且是今天的电力，不是 2028 年的预测：[帖](https://x.com/chamath/status/2116926625657024819)。零对冲列的摩根士丹利电力账：2024 年 12 月估计到 2028 年需要 57 吉瓦、缺口 36 吉瓦；2025 年 11 月是 69 吉瓦、缺口 44 吉瓦；现在总需求估计翻倍到 116 吉瓦、缺口 70 吉瓦：[帖](https://x.com/zerohedge/status/2117004944566022465)。就算加上燃气轮机、燃料电池和亚洲需求外溢，净缺口仍有 38 吉瓦，是 2025 年的 3 倍：[帖](https://x.com/zerohedge/status/2117005726682153337)。公用事业口径是 2028 年需求 180 吉瓦、供给 137 吉瓦、缺口 43 吉瓦，今年这个缺口是 15 吉瓦：[帖](https://x.com/zerohedge/status/2117005812698665420)。116、70、38、180、137、43、15，都在这三帖里，不要相加。Kevin O'Leary 写自己把超过 20% 的投资组合放在电力和计算基础设施上：[帖](https://x.com/kevinolearytv/status/2116969723418255784)。

铜被写成实物紧、不是股票代码。Kobeissi：中国铜进口溢价超过伦铜每吨 200 美元，是纪录；洋山溢价三个月里翻了一倍多，2026 年以来涨了 700%；伦铜现货相对三个月期货的溢价扩到每吨 217 美元，是 8 月中以来最大。他同时写，对美国精炼铜关税的预期把几十万吨铜改道到了美国：[帖](https://x.com/KobeissiLetter/status/2117049594194378850)。Ole Hansen 的铜价是 6.52 美元，两日回调之后回升，中国进口溢价到了纪录：[帖](https://x.com/Ole_S_Hansen/status/2117144450090549297)。每吨 200 美元、217 美元、6.52 美元，单位不同，并列不换算。

## 要盯住的五件事

1. **0.3% 和 0.4% 是周日 23:05 的期货，不是收盘。** 标普期货涨 0.3%，纳斯达克期货涨 0.4%。周一 09:41 的标题只说期货更高、油更低。周五纳斯达克 100 跌 3.5%、费城半导体跌 7.2%，是亚洲综述里的句子。综合指数收盘仍是上一份日报的 25438.40 和 7578.14。Bilello 的周五标普是跌 1.8%。
2. **油价有换月，也有四张不同的报价。** Hanke 周日晚的布伦特是 117.70。First Squawk 随后写 111.60（跌 1.6%）、再跌 2 美元、原油 101.11、布伦特 110.37、标题跌 4%。Ole 的 1 月合约是 110 美元、跌 3%、周五在 114 上方。Rory 提醒 12 月合约周五到期，滚动近月看起来更惨。高盛是 12 月 105（从 90 上调）、Ole 写的 2027 年平均 88、LiveSquawk 标题里的 2027 年可能 140。欧佩克+产量目标维持到 12 月。
3. **黄金 3899.39 和 3915 不要合成。** First Squawk 是涨 0.6% 到 3899.39，最多反弹 0.7%，周五跌 3.7%。Ole 周一是反弹 1% 到 3915，并把 10 月写成跌 6.8%；他周日的复盘把 10 月写成跌 12.7%、收破 3900。Brooks 的“布伦特涨 10%、黄金跌 4%”是热战回来的映射。周一上午的方向是油向下、金向上。
4. **今晚是苹果和 Palantir，周二是选举，周五才是非农。** ISM 制造业在美东 10:00，抓取结束时没有结果。古尔斯比 11:15 也还没讲。Wilson 的路径是先 7100 再 8000，大约从纪录打下 9%。Detrick 的 11 月历史概率是 78.9%，中期选举年 11 月到 4 月是 19 次里 19 次上涨。美国 10 年期没有新点位；英国 10 年期是 5.23%。DataTrek 的基金兴趣门槛是 5.2%。
5. **四家超大规模云厂商的三季度自由现金流被写成负 264 亿美元，只有微软为正。** 2026 年资本开支有可能到 7400 亿美元。高盛那条是明年人工智能基础设施支出 1.2 万亿美元、增速从 80% 收到接近 40%。摩根士丹利大宗经纪：人工智能交易转为低配，是 2023 年初以来第一次，总资金流较 6 月高点下降 8%。OpenAI 的新标题是寻求 200 亿美元，达不到此前 300 亿。铠侠跌 14% 和 SK 海力士上涨是两家公司。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 期货只这一组有数字 | 标普期货、纳斯达克期货 | 周日 23:05，标普期货涨 0.3%，纳斯达克期货涨 0.4%。周一标题是期货更高、油更低，没有新百分比 | [0.3% 与 0.4%](https://x.com/FirstSquawk/status/2117030271182901627)、[更高](https://x.com/WSJmarkets/status/2117190297184579616) |
| 先下后上的路径 | 标普 | Wilson：先到 7100，再到 8000，出清事件包括选举、人工智能开支和更紧的流动性，大约从纪录打下 9%。1950 年以来选举后 6 个月和 12 个月都更高 | [7100](https://x.com/StockMKTNewz/status/2116948821192171527) |
| 10 月已经分化 | 等权、价值、493 | 等权超额 5.7 个百分点或 5.9%，两帖不要合并。价值跑赢成长超过 10 个百分点。Magnificent 7 已公布的同比每股收益 22.6%，493 家是 32.6%。标普 10 月跌 93 个基点，但 327 只涨了 2% 以上 | [5.7 个点](https://x.com/KobeissiLetter/status/2116916423138132362)、[5.9%](https://x.com/RyanDetrick/status/2117026847871381507)、[22.6%](https://x.com/RyanDetrick/status/2116918400832393530)、[93 个基点](https://x.com/Stephanie_Link/status/2116918384180809867) |
| 今晚 | AAPL、PLTR | 苹果是今年唯一跑赢标普的 Magnificent 7，距高点跌 2%，刚超过英伟达成为市值最大。1 万亿美元的涨幅让财报没有犯错余地。特努斯第一次考试，内存成本在飙。Palantir 同一天收盘后 | [唯一跑赢](https://x.com/charliebilello/status/2116995004883255763)、[市值](https://x.com/Barchart/status/2117053477428048110)、[1 万亿](https://x.com/business/status/2117197550692237607)、[特努斯](https://x.com/Reuters/status/2117169879648178610) |
| 上升趋势只剩两家 | AAPL、MSFT、GOOG | 苹果和微软是超大盘里仅有的上升趋势，Alphabet 掉下悬崖。距高点：微软跌 6%，谷歌跌 32% | [趋势](https://x.com/bespokeinvest/status/2116878138139402307)、[距高点](https://x.com/charliebilello/status/2117004450137289143) |
| 图表位 | QQQ | 第一次碰到 200 日，683 到 684 被守住。上面要看 701 一带的阻力，还是补上面的缺口。这是开盘前的句子 | [200 日](https://x.com/RedDogT3/status/2117195639628915108) |
| 期权换仓 | NVDA、INTC、MU、META、GOOGL、AMZN、TSLA、AAPL、PLTR | 买方持仓变化的净方向是多头，前 50 名大约正 270 亿美元 delta。新的净下行仓在特斯拉、苹果、MicroStrategy、Palantir、DRAM、SK 海力士、亚马逊、IBIT。被写成偏多的一边包括英伟达、SPCX、Meta、Robinhood、英特尔、美光、谷歌 | [持仓](https://x.com/spotgamma/status/2116943703969239496) |
| 自由现金流为负 | AMZN、GOOGL、META、MSFT | 四家三季度资本开支 2019 亿美元，自由现金流合计负 264 亿美元，只有微软为正。四季度再计划 2320 亿美元 | [资本开支](https://x.com/KobeissiLetter/status/2116900354717589597) |
| 仍在装机 | AMZN、GOOGL、V、MA、SCHW | AWS 大约每 14 秒装一颗加速芯片，仍供给受限。谷歌第一方模型接口每分钟将近 320 亿 token，是一年前的 4 倍多。Visa 和万事达把代理商务看成长期机会，未来四个季度的量仍然很小。嘉信说人工智能用得越多，客户现金持有越多 | [14 秒](https://x.com/TheTranscript_/status/2116877990386950314)、[320 亿](https://x.com/TheTranscript_/status/2116926994692895116)、[代理商务](https://x.com/TheTranscript_/status/2116900573899616713)、[现金](https://x.com/TheTranscript_/status/2117044018282713340) |
| 融资还在发生 | GOOGL、OpenAI | Alphabet 今年第二次发行欧元债，帖里没有金额。OpenAI 寻求 200 亿美元，达不到此前 300 亿。选举后的公关包括把数据中心改叫计算园区 | [欧元债](https://x.com/business/status/2117158546533941503)、[200 亿](https://x.com/FirstSquawk/status/2117196993231786126)、[园区](https://x.com/axios/status/2116889969432150442) |
| 存储链拆开 | 铠侠、SK 海力士、AMD、SMCI | 铠侠跌 14%，展望被写成可能走平。Cramer 写 SK 海力士在涨。AMD 和超微电脑周二财报。超微的 1.16 美元共识被要求忽略 | [14%](https://x.com/zerohedge/status/2117052258516947439)、[海力士](https://x.com/jimcramer/status/2117194153532731881)、[1.16](https://x.com/eWhispers/status/2116914435918872758) |
| 债券评级这句话 | Anthropic | 投资级评级被写成荒谬。Burry 只发了 S-1 笔记的链接。Cramer 认为空头想搅黄上市 | [评级](https://x.com/TruthGundlach/status/2117118928963133625)、[笔记](https://x.com/michaeljburry/status/2117048379469406713)、[上市](https://x.com/jimcramer/status/2116989356082954676) |
| 电力和空头名单 | CRWV、电力 | 电力是今天的绑定约束。数据中心电力缺口被写成 70 吉瓦，修补之后仍有 38 吉瓦。Coreweave 被点名为原来那批空头。O'Leary 说组合里超过 20% 在电力和计算 | [电力](https://x.com/chamath/status/2116926625657024819)、[70 吉瓦](https://x.com/zerohedge/status/2117004944566022465)、[Coreweave](https://x.com/KeithMcCullough/status/2116966272726376782) |
| 油和气 | 布伦特、原油、天然气 | 1 月布伦特 110 美元。原油报价 101.11。对冲基金的天然气空头被写成史上最大。美国天然气消费者被写成躲开了冲突的账单。美国油气产量增加每天 310 万桶油当量 | [110](https://x.com/Ole_S_Hansen/status/2117144450090549297)、[101.11](https://x.com/FirstSquawk/status/2117082453722710306)、[天然气空头](https://x.com/Barchart/status/2117064778094940551)、[产量](https://x.com/SecScottBessent/status/2116953954311676032) |
| 贵金属 | 黄金、白银、GLD、SLV | 现货 3899.39 或 3915，两帖并列。GLD 10 月流出 18 亿美元。白银信托被写成失守地板 | [3899.39](https://x.com/FirstSquawk/status/2117049268758548721)、[3915](https://x.com/Ole_S_Hansen/status/2117144450090549297)、[GLD](https://x.com/KobeissiLetter/status/2116930768136245591)、[SLV](https://x.com/TrendSpider/status/2116991166746857622) |
| 防御和图表 | MCD、WMT、V、MA、NKE、AMZN、IREN | 麦当劳被写成从芯片换到薯条。沃尔玛是日子难过时还在的名字。Visa 和万事达是在花别人的钱。耐克月线第一次在 46 年历史里超卖。亚马逊在测历史趋势线，前三次是 2001、2008、2022。IREN 被写成往下看 | [麦当劳](https://x.com/TrendSpider/status/2116896793644654909)、[沃尔玛](https://x.com/TrendSpider/status/2116934542074528074)、[耐克](https://x.com/TrendSpider/status/2117047788244758909)、[亚马逊](https://x.com/TrendSpider/status/2116915670281605388) |
| 消费股的 10 月 | AXP、COST、HD、LOW、MCD、PEP、TJX、WMT | 和美国消费者绑在一起的股票 10 月有一个月的反弹，在那之前是走低的 | [消费](https://x.com/bespokeinvest/status/2116887755842326620) |
| 油轮 | ECO | Okeanis Eco Tankers 年初至今涨 217%，油轮运价推着收入同比三位数增长 | [217%](https://x.com/TrendSpider/status/2116972290772701583) |

## 后续走势：三套可以证伪的剧本

帖文没有给周一的收盘点位。抓取结束时现货没开，ISM 没有数，苹果和 Palantir 的财报没有结果。周五写下来的现货收盘仍是上一份日报里的标普 7578.14、纳斯达克综合指数 25438.40、道指 51763.41。下面三套的顺序，以周日晚期货还是涨的、1 月布伦特已经落到 110 美元附近、四家云厂商自由现金流被写成合计为负为前提。

**外交时间换来油价回落，指数只做周五跌深之后的修复。** 触发器已经写在周一凌晨：Cramer 转述选举之后海湾可能什么也不发生，Ole 写特朗普想先给外交时间，期货在周日晚是涨的，英国国债收益率在掉，黄金从周五低点往上。这条路径上，市场交易的是 1 月布伦特留在 110 美元这一带、而不是回到 Hanke 周日写的 117.70，同时等权和 Detrick 的 11 月季节性继续盖过纳斯达克 100 周五那张跌 3.5%。它失败的条件，是巴加埃写的“制裁不解除、海峡不重开”被交易成通航谈判破裂，或者 Kobeissi 帖里那句“仍要处理一到两处核设施”盖过“先谈”，布伦特回到周五 114 美元上方，Brooks 那张“油涨 10%、金跌 4%”重新变成当天的方向。

**人工智能的减仓还没完，7100 是出清，不是开盘目标。** 触发器是摩根士丹利大宗经纪把人工智能交易写成 2023 年初以来第一次低配，总资金流较 6 月高点下降 8%，四家自由现金流合计为负，只有微软为正，铠侠跌 14%，Bianco 把周五写成近两年第七大人工智能抛售。Wilson 的 7100 是这些出清事件走完之前的路径，8000 在那之后。这条路径失败的条件，是 Cramer 看到的 SK 海力士上涨扩散成卖盘不再回来，QQQ 守住 RedDog 写的 683 到 684 并走向 701，苹果今晚把“没有犯错余地”的 1 万亿美元涨幅消化掉，并且 Detrick 的 493 家盈利 32.6% 继续盖过已经公布的 Magnificent 7 的 22.6%。

**选举和数据周把利率从“油价下跌的缓和”里拉回来。** 触发器是美国 10 年期在这个窗口里没有新点位，亚洲时段被写成基本持平，CNBC 写成涨跌互现，而 Bilello 仍要更多加息，Gayed 认为这是在往放缓里加息，DataTrek 的基金兴趣门槛在 5.2%。周五高收益利差扩了 17 个基点。它失败的条件，是油价停留在下跌的那一组报价里，收益率按 Cramer 的“利率更低”走，而不是按 5.2% 的门槛重新吸引或吓退债券账户；或者周五的就业和本周的 ISM 让 Ole 已经写过的“加息从三次收到两次”继续往下收，而不是回到 Bilello 的更紧。古尔斯比 11:15 的讲话、美东 10:00 的 ISM，抓取结束时都还不能用来判定这一套。

另有一张铜的纪录溢价，不并进上面三套。洋山和伦铜的每吨 200 美元、217 美元是 Kobeissi 的实物句子，6.52 美元是 Ole 的价格，两者都还没有被写成某一只矿业股票的目标价。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周一开盘、周一晚上的苹果和 Palantir、周二选举。它不决定仓位大小。现货还没开。ISM 还没有数。

**开盘前只核对五样东西。** 期货是停在周日那组涨 0.3% 和涨 0.4%，还是《华尔街日报》那句“更高”已经配上了一个新的百分比；油价交易的是 Ole 的 1 月合约 110 美元，还是回到 Hanke 的 117.70，换月造成的滚动近月跌幅不要单独当成新的供给冲击；黄金是停在 3899.39 附近，还是 Ole 的 3915，以及它是否还在按 Brooks 的热战映射跟油价反向走；科技是继续四家自由现金流为负、大宗经纪低配人工智能，还是按 SK 海力士和 QQQ 的 200 日被买回去；美国 10 年期是继续没有方向（持平或涨跌互现），还是开始反映 5.2% 那道门槛和周五已经扩出的 17 个基点高收益利差。五样里油价留在 110 美元附近、等权继续强于市值加权、苹果没有在财报前被砸，这些帖给出的默认顺序是等权、价值、消费和电力，高于去追周五已经跌深的半导体。海峡谈判被交易成破裂、布伦特回到 114 上方、QQQ 失守 683，默认顺序掉过头来：原油和 Brooks 的黄金下行映射，高于追涨周日那 0.4% 的纳斯达克期货。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：等权 10 月超额 5.7 个百分点，标普跌 0.9%，不含人工智能的标普年初至今涨 14.2% 并在周五创新高：[帖](https://x.com/KobeissiLetter/status/2116916423138132362)。四家资本开支 2019 亿美元，自由现金流合计负 264 亿美元，只有微软为正：[帖](https://x.com/KobeissiLetter/status/2116900354717589597)。信息处理投资占 GDP 5.4%，高于 2000 年的 4.5%：[帖](https://x.com/KobeissiLetter/status/2116996835621621916)。内塔尼亚胡推动选举之后立刻打击，特朗普说仍要处理一到两处核设施：[帖](https://x.com/KobeissiLetter/status/2116975383077904829)。铜溢价每吨超过 200 美元：[帖](https://x.com/KobeissiLetter/status/2117049594194378850)。韩国三季度环比增 1.0%：[帖](https://x.com/KobeissiLetter/status/2117024379481509961)。他们没有给周一的标普点位。同一账号有一条回复写，伊朗战争据报会在中期选举之后恢复：[帖](https://x.com/KobeissiLetter/status/2116885828400005379)。
- Jim Cramer：油更低，利率更低，除了科技没有超卖；选举之后海湾可能什么也不会发生：[帖](https://x.com/jimcramer/status/2117187066907836687)。SK 海力士在涨：[帖](https://x.com/jimcramer/status/2117194153532731881)。空头想搅黄 Anthropic 上市：[帖](https://x.com/jimcramer/status/2116989356082954676)。没有期货百分比。
- Ole Hansen，线外：1 月布伦特 110 美元，跌 3%，周五在 114 上方。欧佩克+产量目标维持到 12 月。高盛 12 月布伦特 105 美元、2027 年平均 88 美元：[帖](https://x.com/Ole_S_Hansen/status/2117144450090549297)。黄金周一反弹 1% 到 3915，10 月在这张帖里是跌 6.8%。他周日另写 10 月跌 12.7%、收破 3900：[12.7%](https://x.com/Ole_S_Hansen/status/2116838096633200933)。加息预期从三次收到两次写在周日那篇。没有标普点位。
- Steve Hanke：海峡功能上关闭：[帖](https://x.com/steve_hanke/status/2116908873818800442)。布伦特 117.70 是他周日晚用来反驳“世界离得开伊朗的油”的价格：[帖](https://x.com/steve_hanke/status/2117012556011192463)。沙特 GDP 收缩 3.8%，石油活动降 20.4%：[帖](https://x.com/steve_hanke/status/2117105921201430534)。没有周一的期货点位。
- Scott Bessent：油气产量增加每天 310 万桶油当量：[帖](https://x.com/SecScottBessent/status/2116953954311676032)。没有指数点位。
- Javier Blas，线外：特朗普目前想让谈判走下去：[帖](https://x.com/JavierBlas/status/2116971468630507657)。中国和阿曼写海峡应当恢复正常通航：[帖](https://x.com/JavierBlas/status/2117196115443646643)。美国天然气消费者躲开了冲突账单：[帖](https://x.com/JavierBlas/status/2117190842297557189)。没有新的油价目标。
- Robin Brooks，线外：若回到热战，布伦特涨 10% 对应黄金跌 4%、白银跌 8%：[帖](https://x.com/robin_j_brooks/status/2116846273575657650)。这是映射，不是周一的报价。
- Rory Johnston，线外：2027 年 1 月只是滑了一点；滚动近月看起来更惨，是因为 12 月合约周五到期：[帖](https://x.com/Rory_Johnston/status/2117040683282210848)。
- Ryan Detrick，线外：等权超额 5.9%：[帖](https://x.com/RyanDetrick/status/2117026847871381507)。493 家每股收益增速 32.6%，已公布的 Magnificent 7 是 22.6%：[帖](https://x.com/RyanDetrick/status/2116918400832393530)。11 月在中期选举年有 78.9% 的时间上涨，11 月到 4 月 19 次全涨：[78.9%](https://x.com/RyanDetrick/status/2117030459175546970)、[19 次](https://x.com/RyanDetrick/status/2117040770217853295)。没有周一的点位。
- Stephanie Link，线外：10 月标普跌 93 个基点，但广度是正的，大宗经纪有史上最大的去杠杆，年底设置看起来相当好：[帖](https://x.com/Stephanie_Link/status/2116918384180809867)。
- Mike Wilson，经由 StockMKTNewz：7100，然后 8000：[帖](https://x.com/StockMKTNewz/status/2116948821192171527)。摩根士丹利官方账号这个窗口没有帖。
- Charlie Bilello：周五标普跌 1.8%：[帖](https://x.com/charliebilello/status/2117000719001588157)。苹果是唯一跑赢标普的 Magnificent 7，距高点跌 2%：[帖](https://x.com/charliebilello/status/2116995004883255763)。核心 PCE 高于目标已 67 个月，还会加息：[帖](https://x.com/charliebilello/status/2117012211369738547)。民主党横扫概率 71%：[帖](https://x.com/charliebilello/status/2117031004225556904)。
- Keith McCullough，线外：纳斯达克回撤 8%，高收益利差周五扩 17 个基点，散户再跌 5.6%：[回撤](https://x.com/KeithMcCullough/status/2117196228031397997)、[利差](https://x.com/KeithMcCullough/status/2117197500255797729)。Coreweave 仍在原来的空头名单上：[帖](https://x.com/KeithMcCullough/status/2116966272726376782)。Hedgeye 官方账号这个窗口没有新帖。
- SpotGamma，线外：周五是 6 月以来最大抛售，VIX 偏轻，认沽偏贵：[帖](https://x.com/spotgamma/status/2116967245796487441)。买方持仓净多，下行仓和偏多仓的名单见上表：[帖](https://x.com/spotgamma/status/2116943703969239496)。
- RedDog，线外：QQQ 的 200 日在 683 到 684，阻力看 701：[帖](https://x.com/RedDogT3/status/2117195639628915108)。
- Bespoke，线外：苹果和微软是仅有的上升趋势：[帖](https://x.com/bespokeinvest/status/2116878138139402307)。今晚苹果和 Palantir：[帖](https://x.com/bespokeinvest/status/2117021489773826439)。
- Sonali Basak，线外：明年人工智能基础设施支出 1.2 万亿美元，增速从 80% 收到接近 40%：[帖](https://x.com/sonalibasak/status/2116968836612456623)。筹资会变慢，她的团队今年仍看到再加一次息：[帖](https://x.com/sonalibasak/status/2116889296661594241)。
- 零对冲转述的摩根士丹利大宗经纪：人工智能低配，总资金流下降 8%，净杠杆 51%：[帖](https://x.com/zerohedge/status/2117082767590650199)。电力缺口 70 吉瓦、修补后 38 吉瓦、2028 年 180 对 137：[70](https://x.com/zerohedge/status/2117004944566022465)、[38](https://x.com/zerohedge/status/2117005726682153337)、[180](https://x.com/zerohedge/status/2117005812698665420)。Hartnett 的标题是，一年前说做空超大规模云厂商的债，现在说买：[帖](https://x.com/zerohedge/status/2117034057951289397)。铠侠跌 14%：[帖](https://x.com/zerohedge/status/2117052258516947439)。
- Jeffrey Gundlach，线外：Anthropic 的投资级评级荒谬：[帖](https://x.com/TruthGundlach/status/2117118928963133625)。
- Chamath：电力是今天的绑定约束：[帖](https://x.com/chamath/status/2116926625657024819)。
- Raoul Pal：美元、利率、油价一起往上才会收紧条件；选举前他想看到三者往下，油价要靠伊朗方案：[帖](https://x.com/RaoulGMI/status/2116852542638264735)。这是周日中午的框架。
- DataTrek，线外：10 年期 5.2% 是基金兴趣的门槛：[帖](https://x.com/DataTrekMB/status/2117003111676174381)。四周初请平均在他那里是多年新低，帖里没有绝对数字：[帖](https://x.com/DataTrekMB/status/2116995595676373163)。
- Peter Schiff：沃什没有回答为什么 10 月不加息：[帖](https://x.com/PeterSchiff/status/2116900672969064477)。民主党拿下参议院的赔率 72%：[帖](https://x.com/PeterSchiff/status/2116929600957939871)。
- Michael Gayed：软的劳动力市场吸收不了加息：[帖](https://x.com/leadlagreport/status/2116874154393612362)。
- Yardeni，线外：美国 19 倍市盈率，新兴市场 9 倍：[帖](https://x.com/yardeni/status/2116936439686435123)。半导体盈利预期翻倍，但芯片股相对大盘折价 27%：[帖](https://x.com/yardeni/status/2117100211273084989)。两条都写着会员内容，窗口里没有更多数字。
- RenMac，线外：77% 的股票在指数下跌时上涨，标题如此：[帖](https://x.com/RenMacLLC/status/2116881413999845783)。债券终于有收益，股票还没注意到：[帖](https://x.com/RenMacLLC/status/2117028995032031658)。
- The Transcript，线外：每 14 秒一颗芯片、每分钟 320 亿 token、代理商务量仍小、嘉信客户现金持有上升：[14 秒](https://x.com/TheTranscript_/status/2116877990386950314)、[token](https://x.com/TheTranscript_/status/2116926994692895116)、[现金](https://x.com/TheTranscript_/status/2117044018282713340)。黑石说计算基础设施的融资会逐渐不完全看交易对手信用：[帖](https://x.com/TheTranscript_/status/2116953427918156276)。
- TrendSpider：亚马逊的历史趋势线、麦当劳、沃尔玛、白银失守、耐克月线超卖、IREN 往下：[亚马逊](https://x.com/TrendSpider/status/2116915670281605388)、[耐克](https://x.com/TrendSpider/status/2117047788244758909)、[IREN](https://x.com/TrendSpider/status/2117066664978043206)。
- Gavin Baker：他从图表里看到人工智能的投资回报，不同意《金融时报》那篇的结论；美国占 Anthropic 收入的 72%；采用最深的三个行业，生产率增速从 2.2% 到 5%：[帖](https://x.com/GavinSBaker/status/2116973459519709591)。
- Bob Elliott：人工智能投资热是对未来几万亿现金的承诺，任何迹象显示现金不会来，房子就倒：[帖](https://x.com/BobEUnlimited/status/2116866595163406840)。生产率在他那里仍沿长期趋势，不是从人工智能开始才恢复：[帖](https://x.com/BobEUnlimited/status/2116896793841578413)。
- Andreas Steno：不要把一次杠杆事件误当成基本面变了：[帖](https://x.com/AndreasSteno/status/2116985513382982136)。杰文斯悖论才刚开始：[帖](https://x.com/AndreasSteno/status/2116996701516939765)。他周一写对这次波动的幅度感到意外，并且怀疑它会被证明是对的，帖子没有点名资产：[帖](https://x.com/AndreasSteno/status/2117158767729217757)。
- firstadopter，线外：搜索和广告仍是谷歌 75% 以上的收入、90% 以上的利润，云和 TPU 补不上：[帖](https://x.com/firstadopter/status/2116940466612564231)。
- Sawyer Merritt：算力的每瓦成本会在高位停留得比很多人预期更久；SpaceX 的收入预测被他复述为 2027 年底年化 5000 亿到 1 万亿美元，即使打五折也还有 2500 亿：[算力](https://x.com/SawyerMerritt/status/2117061732250042826)、[收入](https://x.com/SawyerMerritt/status/2116926072176472091)。特斯拉无人监督的 Robotaxi 周一早上扩到沃思堡，七个城市的运营围栏合计大约覆盖美国人口的 1%：[帖](https://x.com/SawyerMerritt/status/2117139487083933972)。
- Luke Gromen：窗口内只有一句“很好的清单，我家在按这 10 点做”，帖文没有把那 10 点写进正文：[帖](https://x.com/LukeGromen/status/2116922118495760729)。
- Anthony Pompliano：政府未来十年会印很多钱：[帖](https://x.com/APompliano/status/2117053397602058425)。微软向大约 6 万名员工、约 25% 的人手提供买断，这句话他归给另一位作者：[帖](https://x.com/APompliano/status/2116893471386579068)。
- Kevin O'Leary：两场战争、能源价格超过 100 美元，衰退却没有发生，消费者还在；自己的组合里超过 20% 在电力和计算：[消费者](https://x.com/kevinolearytv/status/2117010365066420577)、[20%](https://x.com/kevinolearytv/status/2116969723418255784)。
- El-Erian：10 月的特征是分化，纳斯达克明显弱于道指和欧洲股票，油价跳升，黄金和比特币下跌的同时美国国债大涨，10 年期收益率下降 36 个基点，是 2023 年以来最大的月度降幅：[帖](https://x.com/elerianm/status/2116949137744683343)。36 个基点是他的 10 月句子，不是周一的新点位。欧洲和美国高收益债里，CCC 和 BB 的利差在拉开：[帖](https://x.com/elerianm/status/2116970296523547108)。
- 美联储官方账号、高盛、摩根大通、花旗、美国银行、SEC、欧洲央行：窗口内没有新的利率决定。高盛的油价数字出现在通讯社和 Ole 的帖里，不在高盛主号。欧洲央行的帖是能源冲击对食品价格的追踪，动量弱于 2022 年：[帖](https://x.com/ecb/status/2117196443052372164)。
- Gary Black、Hedgeye、Liz Ann Sonders、基金策略的 Tom Lee、Aswath Damodaran、Bill Ackman、Ray Dalio、Cathie Wood：窗口内没有新的指数或个股方向。Ackman 的两条是选举和一架私人飞机。Dalio 是一条原则。Wood 没有新帖。

**财报和数据的顺序。** 先看已经写进标题、但还没有结果的两场：周一收盘后的苹果和 Palantir，周二的 AMD 和超微电脑。苹果要同时对上“距高点只跌 2%”“1 万亿美元的涨幅没有犯错余地”和“内存成本”。然后才是还没公布的 ISM、古尔斯比、周二选举、周二 JOLTS、周三 ADP、周五非农。线外的 Earnings Whispers 把本周名单写全了，超微的 1.16 美元共识是他明确说不要用的数字。抓取结束时这些日历项都没有新的公布值。

**明确留在观察、不放进计划的东西。** 不用还没开出的现货去倒推收盘，也不把周日 0.3% 和 0.4% 写成已经实现的涨幅。111.60、110.37、110、101.11、117.70 并列。3899.39 和 3915 并列。10 月黄金跌 12.7% 和跌 6.8% 是 Ole 的两张帖。高盛的 105、88 和标题里的 140 并列。200 亿美元的新融资和上一份日报里的经常性收入不是同一个数。铠侠的 14% 不套到 SK 海力士上。英国国债 5.23% 不是美国 10 年期。德意志银行和 Daniel Newman 的时间线没有读到。彭博主号、markets、BBC Business、CNN Business、纽约时报商业、TradingView、巴菲特账号、美联储官方账号这个窗口没有新帖。Gary Black、Hedgeye、Liz Ann、Tom Lee、Damodaran 这次没有可引用的新点位。

## 帖文索引

期货、油和黄金：[期货涨 0.3% 和 0.4%](https://x.com/FirstSquawk/status/2117030271182901627)、[期货更高、油更低](https://x.com/WSJmarkets/status/2117190297184579616)、[布伦特 111.60、纳指 100 跌 3.5%](https://x.com/FirstSquawk/status/2117056756904067404)、[原油 101.11](https://x.com/FirstSquawk/status/2117082453722710306)、[布伦特 110.37](https://x.com/FirstSquawk/status/2117082763337826733)、[跌 4%](https://x.com/FirstSquawk/status/2117184206765969679)、[1 月合约 110 美元](https://x.com/Ole_S_Hansen/status/2117144450090549297)、[换月](https://x.com/Rory_Johnston/status/2117040683282210848)、[现货黄金 3899.39](https://x.com/FirstSquawk/status/2117049268758548721)、[黄金 3915](https://x.com/Ole_S_Hansen/status/2117144450090549297)。

分化和资本开支：[等权超额 5.7 个百分点](https://x.com/KobeissiLetter/status/2116916423138132362)、[自由现金流负 264 亿美元](https://x.com/KobeissiLetter/status/2116900354717589597)、[493 家盈利 32.6%](https://x.com/RyanDetrick/status/2116918400832393530)、[10 月跌 93 个基点](https://x.com/Stephanie_Link/status/2116918384180809867)、[人工智能低配](https://x.com/zerohedge/status/2117082767590650199)、[明年支出 1.2 万亿美元](https://x.com/sonalibasak/status/2116968836612456623)。

选举、海峡和日历：[先让谈判走](https://x.com/JavierBlas/status/2116971468630507657)、[仍要处理核设施](https://x.com/KobeissiLetter/status/2116975383077904829)、[制裁不解除就不重开](https://x.com/FirstSquawk/status/2117160364546957716)、[海湾可能什么也不发生](https://x.com/jimcramer/status/2117187066907836687)、[7100 然后 8000](https://x.com/StockMKTNewz/status/2116948821192171527)、[11 月 19 次全涨](https://x.com/RyanDetrick/status/2117040770217853295)。

个股和融资：[苹果距高点跌 2%](https://x.com/charliebilello/status/2116995004883255763)、[1 万亿美元的涨幅](https://x.com/business/status/2117197550692237607)、[OpenAI 200 亿美元](https://x.com/FirstSquawk/status/2117196993231786126)、[达不到 300 亿](https://x.com/FirstSquawk/status/2117197262992613570)、[铠侠跌 14%](https://x.com/zerohedge/status/2117052258516947439)、[QQQ 200 日](https://x.com/RedDogT3/status/2117195639628915108)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-02 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 159 条、彭博商业账号 152 条、《金融时报》48 条、《华尔街日报》36 条、《经济学人》83 条、零对冲 45 条、FinancialJuice 112 条、Investing.com 31 条、《The Street》48 条、CNBC 23 条、unusual_whales 12 条是读穿窗口后的计数。德意志银行和 Daniel Newman 的 0 是读取失败。沃伦·巴菲特、彭博主号、markets、彭博经济、BBC Business、CNN Business、纽约时报商业、TradingView、CNBC Now、美联储官方账号的 0，是窗口内没有新帖。线外的 First Squawk 是 262 条，不在这张表里。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,442,472 | 159 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,327,754 | 83 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,276,204 | 36 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,321,579 | 23 |
| 5 | [@business](https://x.com/business) | 10,488,624 | 152 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,565,218 | 10 |
| 7 | [@FT](https://x.com/FT) | 7,108,508 | 48 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,255,978 | 23 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,390,393 | 12 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,647,278 | 7 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,587,449 | 2 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,426,395 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,356,455 | 24 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,430,796 | 45 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,423,200 | 8 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,041,884 | 2 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,000,173 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,711,832 | 12 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,561,998 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,519,924 | 3 |
| 21 | [@chamath](https://x.com/chamath) | 2,482,372 | 2 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,437,635 | 5 |
| 23 | [@BW](https://x.com/BW) | 2,288,194 | 2 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,447 | 11 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,157,785 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,130,228 | 2 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,076,451 | 2 |
| 28 | [@markets](https://x.com/markets) | 2,047,341 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,968,439 | 4 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,793,677 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,774,075 | 2 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,612 | 2 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,710,200 | 0 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,700,862 | 0 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,933 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,612,565 | 18 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,601,664 | 0 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,535,129 | 31 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,509,679 | 3 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,470,392 | 11 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,724 | 3 |
| 42 | [@Bloomberg](https://x.com/Bloomberg) | 1,353,935 | 0 |
| 43 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,353,761 | 0 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,248,873 | 4 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,226,289 | 48 |
| 46 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,193,648 | 0 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,193,277 | 2 |
| 48 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,188,113 | 0 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,185,274 | 5 |
| 50 | [@USTreasury](https://x.com/USTreasury) | 1,165,483 | 0 |
| 51 | [@nntaleb](https://x.com/nntaleb) | 1,164,758 | 1 |
| 52 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,160,387 | 13 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,156,927 | 1 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,153,004 | 8 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,141,339 | 7 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,117,068 | 4 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,109,978 | 32 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,096,572 | 0 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,081,521 | 0 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,064,713 | 0 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,522 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,410 | 22 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,004,215 | 1 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 954,636 | 112 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,266 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 935,059 | 3 |
| 67 | [@tradingview](https://x.com/tradingview) | 906,764 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 893,892 | 1 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 890,271 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,645 | 6 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 873,685 | 9 |
| 72 | [@axios](https://x.com/axios) | 862,331 | 16 |
| 73 | [@steve_hanke](https://x.com/steve_hanke) | 862,205 | 28 |
| 74 | [@jpmorgan](https://x.com/jpmorgan) | 860,077 | 0 |
| 75 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 855,640 | 0 |
| 76 | [@Citi](https://x.com/Citi) | 853,263 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 848,183 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,756 | 1 |
| 79 | [@ecb](https://x.com/ecb) | 830,335 | 2 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,462 | 0 |
| 81 | [@bgurley](https://x.com/bgurley) | 812,075 | 0 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,372 | 0 |
| 83 | [@economics](https://x.com/economics) | 806,639 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 790,312 | 2 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,191 | 0 |
| 86 | [@leadlagreport](https://x.com/leadlagreport) | 769,975 | 9 |
| 87 | [@markminervini](https://x.com/markminervini) | 767,548 | 0 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 758,202 | 0 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,917 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 732,443 | 0 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 718,865 | 13 |
| 92 | [@CMEGroup](https://x.com/CMEGroup) | 712,115 | 0 |
| 93 | [@Nouriel](https://x.com/Nouriel) | 706,605 | 0 |
| 94 | [@DanielNewman](https://x.com/DanielNewman) | 695,411 | 0 |
| 95 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 673,920 | 9 |
| 96 | [@fundstrat](https://x.com/fundstrat) | 673,133 | 0 |
| 97 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,720 | 0 |
| 98 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,285 | 0 |
| 99 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,721 | 0 |
| 100 | [@LukeGromen](https://x.com/LukeGromen) | 637,224 | 1 |
