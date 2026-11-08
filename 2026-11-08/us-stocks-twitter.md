# 美股 Twitter 观点日报 · 2026-11-08

周日现货不开，抓取结束时美东大约 5:17，股指期货要到周日 18:00 才重新开。这个窗口里没有新的指数点位，也没有周日晚间期货。周末帖文的主线是伯克希尔三季报、人工智能资本开支还在不在、以及霍尔木兹又多出来的几张不能并成一句的军事帖。这是公开帖文的整理，不是投资建议。

下面每一条归纳都附有帖文链接。

## 抓取口径

- 报告日期按北京时间 **2026-11-08**。触发时刻约 10:01 UTC，时间线补抓到 **约 10:17 UTC（北京时间 18:17，美东 5:17）**。美国夏令时已经结束。美股现货周六、周日都不开。股指期货要到周日美东 18:00（23:00 UTC）才重新开，这个窗口里没有那一档。
- 观察窗口从 **2026-11-07 10:30 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周六上午 6:30 以后、周六全天和周日凌晨到大约 5:17。上一份日报里的周五开盘点位、非农 165,000 和 WTI 结算 90.83，不在这里重算。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。抓取开始时，美国趋势是 lubbock、utah state、Emma Stone、`#EmborgxEngLot`、`#NINGNING`、Dave Chappelle。抓取结束时是 Bama、Emma Stone、Georgia、`#shortdrama`、utah state、`#MoboReels`。两边都没有美股代码。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。
- 不存在官方的“美股 Top 100”。这次试了 **500** 个候选，成功读到粉丝数的有 **468** 个。排序时拿掉加密货币账号、综合新闻主号、科技风投和创始人、大型科技公司首席执行官、竞选和政治账号、公司产品品牌、大学和智库，以及简介对不上的错人号。`@DanielNewman` 仍是漫威演员，`@SEC` 仍是东南联盟，`@goldman` 仍不是高盛，`@robinbrooks` 只有十几个粉丝。这次如果把国会账号留在排序里，Alexandria Ocasio-Cortez、Bernie Sanders、Elizabeth Warren、Chuck Schumer 和 Mike Johnson 会把截止线抬高，把 Eric Balchunas 挤出前 100。他们按以往口径拿掉。用来排序的账号是 **345** 个，截止在 Eric Balchunas（626,589）。前 100 的账号集合和 11 月 7 日那份相同。名次只对调了一对：Liz Ann Sonders（862,296）到了第 73，Steve Hanke（862,056）到了第 74。Morning Brew（593,690）第 101。Gary Black 第 102。Barchart 第 103。First Squawk（576,964）第 104。dampedspring 第 105。Gundlach 第 106。Earnings Whispers 第 107。排序不代表预测准确度。
- 100 个账号里，**62 个**在窗口内有按帖文链接去重后、且接口没有标成回复的原创帖。路透读穿窗口，88 条。彭博商业账号 75 条。《华尔街日报》75 条。《经济学人》76 条。《金融时报》18 条。CNBC 29 条。零对冲 48 条。FinancialJuice 补抓后读穿窗口，59 条。《The Street》48 条。Investing.com 24 条。线外的 First Squawk 读穿窗口，原创 189 条。Seeking Alpha 50 条。《The Information》第一次是空结果，重试后 19 条。德意志银行的时间线仍是服务器错误，表里的 0 不是确认沉默。LiveSquawk 可见时间线最新一条停在 11 月 6 日 21:07 UTC，窗口内 0 也不是确认沉默。吉姆·克拉默第一次读取失败，重试后窗口内有 1 条原创。

## 伯克希尔的回购各家都写成大约 96 亿美元，现金有两套

回购的整数是 96 亿美元。Kobeissi：三季度回购 96 亿美元，2026 年累计 144 亿美元，将近 22 个月没回购之后重新开始；2026 年已经是股票的净买入方，净买入 112 亿美元，2025 年同期是净卖出 106 亿美元：[回购和净买入](https://x.com/KobeissiLetter/status/2119079789751414924)。《金融时报》的标题是把 96 亿美元投进股票回购：[帖](https://x.com/FT/status/2119069592660156912)。彭博商业：三季度把回购提高到 96 亿美元，保险承保拖累经营利润：[帖](https://x.com/business/status/2119105118096224300)。First Squawk：三季度回购约 96 亿美元：[帖](https://x.com/FirstSquawk/status/2119051700078338224)。Morning Brew 把 2024 年下半年和 2025 年四个季度都写成 0，2026 年一季度 2.35 亿美元、二季度 45 亿美元、三季度 96 亿美元，并写成公司纪录：[帖](https://x.com/MorningBrew/status/2119092654755414350)。StockMKTNewz 的季度标题是大约 96.5 亿美元，月度拆开是 7 月 33.9 亿、8 月 8.47 亿、9 月 54.1 亿：[月度](https://x.com/StockMKTNewz/status/2119071034921853233)。96 亿和大约 96.5 亿并列。2.35 亿、45 亿、96 亿是 Morning Brew 的三个季度。144 亿是 Kobeissi 的 2026 年累计。112 亿是净买入，不是回购。

现金不能并成一个数。StockMKTNewz：现金和短期国债大约 3770 亿美元：[帖](https://x.com/StockMKTNewz/status/2119072966369525918)。Seeking Alpha 的标题是现金 3774 亿美元，经营利润同比 -6%：[帖](https://x.com/SeekingAlpha/status/2119115168005411284)。The Transcript：现金和短期国债环比 -1.9%，到大约 3523 亿美元；经营利润同比 -5.8%，到 127 亿美元；保险浮存金环比增加 10 亿美元，到大约 1785 亿美元；回购大约 96 亿美元，2026 年累计大约 144 亿美元：[帖](https://x.com/TheTranscript_/status/2119090964526760119)。彭博商业的经营利润是 127 亿美元、同比 -5.8%：[帖](https://x.com/business/status/2119057306755149942)。First Squawk 写成 127.1 亿美元、同比 -5.8%：[帖](https://x.com/FirstSquawk/status/2119051683254976521)。3770 亿、3774 亿和 3523 亿并列。-5.8% 和 -6% 并列。127 亿和 127.1 亿并列。巴伦只写经营利润被更弱的承保和投资收入压住，没有给另一个金额：[帖](https://x.com/barronsonline/status/2119057702110310662)。

股票组合是另一张。StockMKTNewz：组合市值 3355 亿美元，今年 +12.7%。前五名是苹果 2.279 亿股、660 亿美元；美国运通 1.516 亿股、513 亿美元；谷歌 1.06 亿股、378 亿美元；可口可乐 4 亿股、325 亿美元；美国银行 4.834 亿股、275 亿美元：[帖](https://x.com/StockMKTNewz/status/2119079362360193101)。吉姆·克拉默问的是：伯克希尔为什么在 Alphabet 上拿了这么大、而且他认为不明智的仓位：[帖](https://x.com/jimcramer/status/2119185730358669402)。“不明智”是他的形容词。1.06 亿股和 378 亿美元是 StockMKTNewz 的持仓句，不是克拉默写的。零对冲的标题是后巴菲特时代开局不稳，人工智能押注绊倒：[帖](https://x.com/zerohedge/status/2119095138303488027)。TrendSpider 的图评是市场在沟里、伯克希尔在创新高：[帖](https://x.com/TrendSpider/status/2119203243808960732)。这是图上的句子，不是收盘点位。

苹果自己的资本政策是另一句。The Transcript 引苹果首席财务官：公司放弃了净现金中性的目标，资本配置原则还在，去掉这个目标是为了更灵活地做对公司合适的投资：[帖](https://x.com/TheTranscript_/status/2119074901265203504)。

## 观点分成四组

### 1. 周五的反弹被写成底，也被写成华尔街不会自己想

迈克尔·伯里：华尔街用糟糕的一天就把它叫成底部；在他看来，华尔街现在就是人工智能，拿不出一个自己的想法：[帖](https://x.com/michaeljburry/status/2119092664612090018)。Steve Hanke 把裂缝写成已经出现：[帖](https://x.com/steve_hanke/status/2119021543737135208)。他又写，信息处理设备和软件支出占 GDP 到了纪录的 5.35%，互联网泡沫顶点是 4.46%：[帖](https://x.com/steve_hanke/status/2119262129102733641)。费城半导体指数他写成从今年早些时候的高点大约跌了 40%：[帖](https://x.com/steve_hanke/status/2119286036526174222)。5.35% 和 4.46% 是支出占 GDP。大约 40% 是 SOX 从高点算的，不是周五单日。他引达摩达兰：大科技在花，是因为别人都在花，怕被甩下；又引他另一句，过去四十年实际 GDP 增长比个人电脑出现之前更低，那些号称提高生产率的东西只是重新分配了财富：[怕被甩下](https://x.com/steve_hanke/status/2119174300670321006)、[四十年](https://x.com/steve_hanke/status/2119242751501914403)。Chris Wood 经他转述：美国预算赤字已经是 GDP 的 6.2%，而且没有衰退；典型衰退里赤字还会再扩大约 6 个百分点：[帖](https://x.com/steve_hanke/status/2119052749849706889)。6.2% 是赤字占 GDP。5.35% 是信息处理设备。两句不要对调。

另一边把同一周写成减速带，而且给了两个年底目标。Carl Quintanilla 引 Yardeni：估值在掉、盈利在涨，人工智能反弹被看成又一个减速带，不是路障；年底标普目标仍是 7900：[帖](https://x.com/carlquintanilla/status/2119146701168807940)。同一账号引摩根大通：股票倍数从 1 月高点以来压缩了大约 4 倍，是衰退之外现代历史上最极端的压缩之一；如果 2027 年盈利下修、进入周期末端，投降还有空间，但他们看成人工智能超级周期里的周期中重置，标普目标维持 8000：[压缩](https://x.com/carlquintanilla/status/2119044039987343371)、[8000](https://x.com/carlquintanilla/status/2119047699085643938)。7900 和 8000 并列。大约 4 倍是倍数压缩的句子，不是指数跌了 4 倍。Yardeni 自己的帖没有重写 7900。他写标普从 2022 年 10 月以来涨了 106%，估值倍数已经不再上升，之后的上涨来自盈利；市场连续第四周绊倒，强就业触发了周五的反弹，这周有通胀数据和一连串美联储讲话：[106%](https://x.com/yardeni/status/2119122706759090582)、[第四周](https://x.com/yardeni/status/2119215657199731138)。106% 是从 2022 年 10 月算的。第四周是他的周数。DataTrek 只发了视频标题“10 月是不是标普 2026 年的高点”，帖文里没有给出是或否：[帖](https://x.com/DataTrekMB/status/2119144121311088991)。

宽度和“是不是熊市”也有两套。线外的 Ryan Detrick：上周多数股票其实还行，Duality Research 的平均股票只跌了略多于 1%，351 只跑赢标普；科技和通信现在占标普 46%，1999 年是 37%；前十大占 39%，1999 年是 25%，而且前十里有 8 只在科技这一侧：[平均股票](https://x.com/RyanDetrick/status/2119099383098544435)、[46%](https://x.com/RyanDetrick/status/2119092552099844211)、[39%](https://x.com/RyanDetrick/status/2119096774610591860)。他又写，从 10 月 6 日历史高点跌到 -5% 用了 23 个交易日；Sam Stovall 的历史是，多数熊市跌到 -5% 更快，只有 1960 年代末到 1970 年代初那次 34% 的熊市用了更久；熊市当然可能发生，但他现在不这么预期：[23 天](https://x.com/RyanDetrick/status/2119160875193889133)。另一张是，像周四那样发生在 200 日均线上方的 4% 暴跌，很少在近期继续大跌：[帖](https://x.com/RyanDetrick/status/2119090440070717920)。23 天、-5%、4%、200 日均线，都是这几张帖的句子。46%、39%、37%、25% 是权重，不是跌幅。线外的 Stephanie Link 把这一周写成标普 -2.7%、纳斯达克综合指数 -3.4%，表面之下通信服务 +5.4%、可选消费 +3.3%，医疗、房地产、必需消费和金融 +1% 到 +2%；她把这写成补涨，不只是防守，可选消费里她点了 Dick's：[帖](https://x.com/Stephanie_Link/status/2119155752116138331)。线外的 Michael Gayed：截至 11 月 6 日那一周，标普 -2.7%，高收益债 -0.26%，长久期国债 +0.1%；高收益债期权调整利差 11 月 5 日收到 348 个基点，是 12 个月高点，比 8 月 28 日 260 个基点的低点高 88 个基点：[帖](https://x.com/leadlagreport/status/2119078750939693253)。-2.7% 在 Stephanie 和 Gayed 两张帖里都是标普的一周。-3.4% 只在 Stephanie 的综合指数。348 个基点是信用利差，不是指数。

El-Erian 把这一周收成：剧烈的美国政治重组、人工智能紧张和强数据叠在一起；科技股和油价是猛烈的重新定价，更广的信用和经济学家对经济前景的信心还在；接下来一周数据很多，包括美国通胀：[一周](https://x.com/elerianm/status/2119169460783169620)。他另写，能源板块的亏损比科技更大，图是《华尔街日报》的：[帖](https://x.com/elerianm/status/2119198809544630523)。标普成分股电话会上，“通胀”或“通胀性”的提及 10 月升到 820 次，是 2024 年 2 月以来最高的月份：[帖](https://x.com/elerianm/status/2119204117952233795)。820 次是提及次数。The Stalwart 用的是同一件事实的另一句：提及升到两年多来的最高：[帖](https://x.com/TheStalwart/status/2119204160415633601)。

Cathie Wood：这次选举掀不翻人工智能革命；建数据中心的公司会更在意当地社区，并拿出更低的房产税、更高的工资、商业开发和学校；生产率的提高会变成更高的薪酬、更厚的利润率、更多投资和更低的价格；经济比多数投资者以为的更强：[帖](https://x.com/CathieDWood/status/2119103890339590569)。ARK 的机构号把中期选举后一年的标普写成自 1958 年以来通常上涨，连 1987 年那种单日跌 22% 的年份最后也收高：[帖](https://x.com/ARKInvest/status/2119063570918875285)。通常上涨是历史句。22% 是 1987 年的单日，不是这周。Anthony Pompliano 引 Jordi Visser：标普 500 里 492 只是债券、8 只是看涨期权；人工智能的负面今年才开始，后面还会更差；做不了人工智能输家的市场，可以二十年跑不赢通胀：[帖](https://x.com/APompliano/status/2119136685019549752)。492 和 8 是这句比喻。不是持仓建议。

Keith McCullough 的市场句夹在和 Ryan Detrick 的争吵里。能单独拿出来的是：选举之后他做了卖出 QQQ 的决定，之后 CNBC 一系的人一直在骂 Hedgeye；宏观节目的标题是市场、中期选举和通往 Quad 4 的路；另一条标题是，2008 年以来喊出每一次美国市场崩溃的团队正在对 2027 年示警；Signal Strength 里他写成正在帮社区管理 44 个多头和 56 个空头：[卖出 QQQ](https://x.com/KeithMcCullough/status/2119221963684007986)、[Quad 4](https://x.com/KeithMcCullough/status/2119227184393150529)、[2027](https://x.com/KeithMcCullough/status/2119123343873859728)、[44 和 56](https://x.com/KeithMcCullough/status/2119104148998414413)。44 和 56 是那套产品里的个数，不是指数涨跌。线外的 Andreas Steno 把空头的庆祝写成：人工智能空头在第一次落后 4 到 6 个月之后就绕场，即便他们连续多年看错：[帖](https://x.com/AndreasSteno/status/2119119553976467502)。RedDog 的规则仍是：个股跌破并留在 8 日和 21 日均线之下就卖掉；SPY、QQQ、SMH 在 8 日和 21 日之下就该做交易，而不是做组合：[帖](https://x.com/RedDogT3/status/2119207583403962700)。

### 2. 数据中心被写成已经禁了，也被写成信还在谈、开支还在创纪录

“得州已经禁止数据中心”只出现在 Hanke 的帖里。他写中期选举三天之后，得州已经对数据中心下了禁令：[帖](https://x.com/steve_hanke/status/2119037157759414498)。其他账号没有用“已经禁止”这四个字。The Information：地方性的数据中心禁令从年初大约 40 个增加到 8 月的 500 多个，新州长还可能加上全州暂停：[帖](https://x.com/theinformation/status/2119067394060464199)。这个窗口里的彭博句是 CoreWeave 给当选州长 Gina Hinojosa 写了信，希望和她的新政府谈现在和将来的州内项目：[帖](https://x.com/business/status/2119169304109142096)。StockMKTNewz 也发了这封信：[帖](https://x.com/StockMKTNewz/status/2119242335058104812)。线外的 firstadopter 把信读成：人工智能公司会接受她的条件和保护要求，得州的建设会继续，不会被挡住：[帖](https://x.com/firstadopter/status/2119171365081342460)。“已经禁止”、大约 40 个到 500 多个、一封还在谈的信、建设会继续，四句并列。

资本开支的硬数字在另一张。Kobeissi：9 月非国防资本品出货、剔除飞机，同比 +11.6%，到纪录的 860 亿美元，是 2021 年 7 月以来最快；三个月年化 +16.5%，是除了疫情复苏之外 2011 年以来最强；2024 年 10 月以来增加 120 亿美元，也是 +16.5%；计算机、服务器、存储和相关设备订单同比 +27%，是 1997 年 1 月以来最大：[帖](https://x.com/KobeissiLetter/status/2119249539873886436)。+11.6% 是同比。两个 +16.5% 一个是三个月年化，一个是 2024 年 10 月以来的累计。860 亿是出货金额。+27% 是订单，不是出货。生产率是他的另一条：三季度非农劳动生产率年化 +3.5%，是 2025 年三季度以来最大，也是连续第三个季度改善；非农企业产出年化 +3.7%；时薪年化 +2.9%；单位劳动力成本 -0.7%，是 2025 年二季度以来第一次季度下降；他把这写成人工智能、软件和设备投资的结果：[帖](https://x.com/KobeissiLetter/status/2119116014478565476)。+3.5% 是这一帖的生产率。上一份日报里有过 3.6% 的句子，不在这里改写，也不把 -0.7% 的单位劳动力成本换成别的符号。

线外的 Bob Elliott 把近端风险写成资本开支被卡住，这比“最终需求不够”更伤整个市场，因为资本开支打的是现在：[帖](https://x.com/BobEUnlimited/status/2119116419145343456)。Stephanie Link 的方向相反：数据中心建设的增速会慢，但未来几年的支出更高，建设 3 到 4 万亿美元、电网 1 万亿美元、电力 1 万亿美元；需求强，两党都需要就业，相对中国有两年优势，美联储也支持；护栏是需要的，她对超大规模公司的融资狂热仍看多：[帖](https://x.com/Stephanie_Link/status/2119157118284538212)。3 到 4 万亿、1 万亿、1 万亿是她的三笔。860 亿美元是 Kobeissi 的单月出货。不要换算。The Information 引 Paul Kedrosky：建设推迟对数据中心供应商是坏事，队列里相当一部分至少会被推后，英伟达在这条供应链上：[帖](https://x.com/theinformation/status/2119210846828007631)。亚马逊云首席执行官 Matt Garman 经 The Information：选举之后亚马逊在数据中心扩张上“位置不错”，其他人可能还有更多工作要做：[帖](https://x.com/theinformation/status/2119112729176805848)。“位置不错”是 Garman 说亚马逊。被推后的是 Kedrosky 说的供应商队列。

涡轮机和长约也是两套。零对冲的标题是马斯克称软银在涡轮订单上违约：[帖](https://x.com/zerohedge/status/2119067457717412198)。Benzinga 用了同一句标题：[帖](https://x.com/Benzinga/status/2119082446285107467)。unusual_whales 的一条被接口标成回复，也是这句：[帖](https://x.com/unusual_whales/status/2119260115832586384)。aleabitoreddit 把摩根士丹利问 GE Vernova 首席执行官的回答写成：没有看到客户融资中断、退出涡轮预留的请求，或者放缓；他同时引美光，战略客户协议不能单方取消，是照付不议，客户不论提不提货都要为承诺的量付钱，和以前那种没有约束力的长约不是一种：[帖](https://x.com/aleabitoreddit/status/2119023086502805730)。“违约”是马斯克的标题。GE Vernova 的“没有”是 aleabitoreddit 对那场问答的转述。照付不议是他引的美光，不是涡轮。台积电 3D DRAM 也有了否认。他写，Tom's Hardware 报道台积电发言人否认正在探索 3D DRAM；前一天 The Information 写过这是英伟达的要求。他把这种来回的标题，连同英伟达首席执行官的那则私人关系指控，看成会制造波动，尤其如果最后不实：[帖](https://x.com/aleabitoreddit/status/2119097842363211968)。否认是这一帖。零对冲的标题是报道称黄仁勋和一名被指的中国间谍有过浪漫关系：[帖](https://x.com/zerohedge/status/2119088846985969739)。标题不是已经查实的事实。

新云和信用是第三张。aleabitoreddit 在估值砸过之后把 Nebius 这类新云看成有吸引力，理由包括和英伟达的分配关系、已经签约的产能、超大规模公司这种对手方，以及融资方式；他明确不喜欢 CoreWeave 那种高利息债务，除非再融资。他又写 IREN 用五年合同、90% 的 GPU 资本开支预付款适应了紧市场，旧的 H100 重新签约价格是以前的两倍：[帖](https://x.com/aleabitoreddit/status/2119077473107472729)。他后来把基础设施和“人工智能泡沫”拆开：存储有 1 到 3 倍的远期市盈率，还有超大规模公司的多年价格下限；有的光模块公司市值比净现金还低；该谨慎的是某些私募估值、没有好好融资的杠杆新云，以及实验室的承诺。他写成 2026 年的人工智能去杠杆，不是需求消失：[帖](https://x.com/aleabitoreddit/status/2119363124147191823)。1 到 3 倍是他的市盈率句子。90% 是预付款。两倍是 H100 重签。零对冲把在建和已宣布未开工的数据中心写成 2028 年是悬崖，并点名甲骨文在新墨西哥因不可抗力停过的 Project Jupiter：[帖](https://x.com/zerohedge/status/2119116536023511154)。另一条标题是超大规模公司的发债已经超过全年预测，人工智能债券的让价在飙，信用紧缩就在眼前：[帖](https://x.com/zerohedge/status/2119127353360085176)。还有一条标题是股票慌了、信用打了个哈欠：[帖](https://x.com/zerohedge/status/2119124080104214847)。“2028 是悬崖”“信用紧缩就在眼前”“信用打了个哈欠”三句都在，不要只留一句。The Transcript 引 Blue Owl 首席财务官：买数据中心不是在押人工智能，而是给投资级租户盖楼、签长约，承担的是微软、亚马逊、Meta 的信用：[帖](https://x.com/TheTranscript_/status/2119142847291285584)。unusual_whales 一条被标成回复的帖引彭博：Samlyn Capital 几乎卖掉了金融以外的一切，并在裁高级分析师：[帖](https://x.com/unusual_whales/status/2119271440747016225)。这是回复里的标题，不是 Samlyn 自己的帖。

Anthropic 的估值沿途又短了一截。Bob Elliott 引彭博：上市买家把估值看到低至 1.1 万亿美元，并问 2 万亿去哪了：[帖](https://x.com/BobEUnlimited/status/2119071159731794336)。Sonali Basak：如果上市估值掉到 1 万亿美元以下，她认为大概不该上市；买盘被打疼了，还可能继续去杠杆；最近的就业和增长支持宏观，从而再给加息让路；蓝色浪潮仍可能带来明年的债务上限争论，压着长端；股票和债券市场仍开着，私募干火药她写成 450 亿美元，VIX 也还没到她认为警报的水平，公司更该等：[帖](https://x.com/sonalibasak/status/2119076207144665153)。1.1 万亿是买家看到的低点。1 万亿以下是她的“不该上市”。2 万亿是 Elliott 问的上一档。450 亿美元是她写的干火药。unusual_whales 两条被标成回复的帖把买家写成在嫌 1.5 万亿太贵，连 1 万亿都要争：[1.5 万亿](https://x.com/unusual_whales/status/2119203493479403685)、[连 1 万亿](https://x.com/unusual_whales/status/2119214817428857337)。1.5 万亿是回复标题。Investing.com 的标题是高盛看到“蓝色浪潮”对人工智能和数据中心政策有重大含义，这条里没有新的目标价：[帖](https://x.com/Investingcom/status/2119156093154902154)。

估值倍数有一张周末新句。Morning Brew：科技股预期市盈率大约 17 倍，标普大约 18 倍，是 2017 年以来第一次科技比标普便宜；作为对照，2025 年 10 月科技大约 32 倍：[帖](https://x.com/MorningBrew/status/2119135399440441773)。17、18、32 都是大约。Charlie Bilello 的回撤表锚定的是 11 月 5 日修正低点，不是周日的现价：标普 -6%，纳斯达克 100 -15%，英伟达 -26%，台积电 -28%，SK 海力士 -39%，AMD -39%，博通 -41%，美光 -48%，应用材料 -57%，泛林 -58%，英特尔 -64%，Sandisk -66%：[帖](https://x.com/charliebilello/status/2119083483855470768)。这些是距历史高点、打在 11 月 5 日那个低点上的百分比。Carl Quintanilla 引的另一套是从高点算的回撤：科技在养伤 15%，杠杆科技 55%，SOXL 84%：[帖](https://x.com/carlquintanilla/status/2119140138798457325)。15%、55%、84% 不是 Bilello 那张表。Hanke 的 SOX 大约 -40% 也不是这张表。TrendSpider 把 Nebius、英特尔、Sandisk、谷歌画进了第 4 阶段：[帖](https://x.com/TrendSpider/status/2119259864195055901)。台积电被他写成双顶、18 个月上升趋势出去了：[帖](https://x.com/TrendSpider/status/2119071120737628174)。甲骨文被写成这种恐惧见过：[帖](https://x.com/TrendSpider/status/2119146618071163038)。Sandisk 被单独写成正式进入第 4 阶段：[帖](https://x.com/TrendSpider/status/2119165494355787963)。这些是图评。

今年至今的涨跌是 StockMKTNewz 周六夜里的一张，不是新收盘。标普今年至今 +7.83%：[帖](https://x.com/StockMKTNewz/status/2119180536958820388)。纳斯达克 100 +6.8%，标普跑赢了它：[帖](https://x.com/StockMKTNewz/status/2119190078316478535)。大票今年至今：苹果 +25.94%，英伟达 +0.08%，微软 +9.72%，谷歌 -9.02%，亚马逊 +12.34%，Meta -7.57%，特斯拉 -20.35%，博通 -15.14%，礼来 +25.99%，伯克希尔 +13.58%，沃尔玛 +12.66%，摩根大通 +3.81%，Visa +20.51%，美光 +141.76%，AMD +109.68%，埃克森 +37.83%，强生 +33.47%，万事达 +14.33%，艾伯维 +27.49%：[帖](https://x.com/StockMKTNewz/status/2119159247649099999)。+0.08% 是英伟达的今年至今。-26% 是 Bilello 打在 11 月 5 日低点上的距高点。两句不要替换。全球前十大股票的合计市值他写成 28.15 万亿美元，上周是 28.62 万亿：[帖](https://x.com/StockMKTNewz/status/2119061570831384966)。

### 3. 霍尔木兹这个周末又多了几张不能合成的帖

水雷、爆炸、有限打击、大楼和无人机，按发帖时间留着。

First Squawk 在窗口开头：伊朗陆军海军称，一艘不服从的油轮今天早上在霍尔木兹海峡以东触雷后起火：[帖](https://x.com/FirstSquawk/status/2119021074662965642)。同一分钟，伊朗通讯社称军队防空在格什姆岛上空打下美国 MQ-9：[帖](https://x.com/FirstSquawk/status/2119021120359920082)。上一份日报里 FinancialJuice 已经有过一句格什姆岛的 MQ-9。这是一条新帖，不是新的独立核实。

FinancialJuice 15:34 UTC：也门胡塞称打了利雅得和 Khurais 的阿美设施，没有沙特方面的即时确认：[帖](https://x.com/financialjuice/status/2119091105841258930)。First Squawk 后来把胡塞的宣布又发了一遍：[帖](https://x.com/FirstSquawk/status/2119261028173447217)。没有确认，就还是宣布。

爆炸从周六晚上开始换说法。FinancialJuice 19:33 UTC：ISNA 称格什姆有爆炸：[帖](https://x.com/financialjuice/status/2119151182144852079)。19:39 UTC：IRNA 更正了消息来源：[帖](https://x.com/financialjuice/status/2119152797090529458)。DeItaone 20:14 UTC：伊朗国家电视台称贾斯克、锡里克、阿巴斯港和格什姆听到爆炸，原因不明：[帖](https://x.com/DeItaone/status/2119161693674549308)。20:33 UTC：塔斯尼姆引消息源，格什姆的爆炸和导弹打击无关：[帖](https://x.com/DeItaone/status/2119166379102216599)。FinancialJuice 20:23 UTC：国家电视台记者称爆炸可能和伊朗在海峡的军事行动有关：[帖](https://x.com/financialjuice/status/2119163939091292161)。“和导弹无关”和“可能和海峡军事行动有关”并列。

水雷的第二句在 21:11 UTC。DeItaone 和 FinancialJuice：伊朗伊斯兰革命卫队海军称，两艘油轮在霍尔木兹附近触雷：[DeItaone](https://x.com/DeItaone/status/2119175971752587615)、[FinancialJuice](https://x.com/financialjuice/status/2119175930291839093)。这是两艘。窗口开头那艘是“一艘不服从的油轮”。不要并成同一艘。

有限打击是美国这一侧的句子。零对冲的标题：特朗普下令选举后的第一轮“小规模打击”：[帖](https://x.com/zerohedge/status/2119082563415285890)。Investing.com：美军在最新一轮有限打击里打了伊朗的防御系统：[帖](https://x.com/Investingcom/status/2119161745100902612)。Hanke 写特朗普确认对格什姆岛做了“小规模打击”：[帖](https://x.com/steve_hanke/status/2119196194782257341)。他又写美国打击了一艘试图绕过港口封锁的伊朗货船：[帖](https://x.com/steve_hanke/status/2119219095937896509)。小规模打击、防御系统、货船，三句并列。

周日早上才是利雅得的楼。Javier Blas 09:11 UTC：利雅得金融区的沙特阿美大楼今早遇袭；沙特当局把损坏说成“轻微”，社交媒体视频显示外立面有一个两层楼高的洞，利雅得称没有人受伤：[帖](https://x.com/JavierBlas/status/2119357203933180348)。FinancialJuice 09:43 UTC 的口径是沙特能源部：有人试图打击利雅得的阿美大楼，来源是国家电视台：[帖](https://x.com/financialjuice/status/2119365076843127187)。“遇袭、轻微、两层楼的洞”是 Blas。“试图打击”是能源部经 FinancialJuice。周六胡塞那句没有被确认的设施袭击，不要改写成周日早上这栋楼。First Squawk 周日另有联军发言人称，胡塞射向南部地区的一架无人机已被拦截摧毁：[帖](https://x.com/FirstSquawk/status/2119372323224428798)。无人机拦截和大楼不是同一句。

交易员把战争溢价写成已经掉下去了，尽管这些帖还在增加。Robin Brooks：布伦特已经完全回吐东向西管道遇袭之后那一波长达数月的上涨，现货 Dated Brent 掉到了近月期货下面；油价从未到过 150 或 200 美元，那些数字是恐吓；价格行为说明那一波不是供给、运费或中国，是风险溢价，战争结束之后会很快回到 60 美元；美元被高油价撑着，油价下来之后美元会明显走弱：[现货低于期货](https://x.com/robin_j_brooks/status/2119058028632687009)、[回到 60](https://x.com/robin_j_brooks/status/2119060294865391686)、[美元](https://x.com/robin_j_brooks/status/2119062078111600644)。60 美元是他的战后路径，不是这个窗口里的现货报价。这个窗口没有新的 WTI 或布伦特结算价。上一份的周五结算 90.83 和 98.32 不在这里重算。零对冲的标题是对冲基金在布伦特上吐出 66 亿美元多头，中期选举把油价里的战争溢价掏空了：[帖](https://x.com/zerohedge/status/2119188257908904235)。66 亿美元是这张标题里的平仓金额。Rory Johnston：可以有地区性的暂时过剩，即便全球背景仍然偏紧；6 月、7 月谅解备忘录之后的“小过剩”就是例子；市场如果重新转紧，期限结构会确认：[帖](https://x.com/Rory_Johnston/status/2119088186932490319)。他又写封锁见效不够快，对方也不像下定决心走大规模升级，所以走到了“封锁加”的策略；伊朗的陆地边界会难得多：[帖](https://x.com/Rory_Johnston/status/2119089386952245541)。线外的 firstadopter 仍把战争收场写成更可能了：没有公众支持，国会已经看到反对的规模；一旦收场，能源价格下跌，通胀和美联储加息压力缓解，金融条件放松，对人工智能的融资和股票是正的：[帖](https://x.com/firstadopter/status/2119047773764850088)。“会很快回到 60 美元”和“收场对人工智能融资是正的”是两个人的条件。水雷和大楼是已经发出的帖，不是这个条件已经实现。

### 4. 利率、房贷和黄金各有一张新的周末数字，期货没有

房贷有两个利率，指的不是同一件事。Kobeissi：购房抵押贷款申请指数上周 -2%，到 131，是 2025 年 1 月以来第二低，也是 1995 年以来第六低的一周，比 1 月低 32%，比 2019 年疫情前低 50%；30 年固定利率自 2 月以来上升 120 个基点，到 7.18%，接近 2023 年 11 月以来最高，并且连续 7 周在 7% 上方：[帖](https://x.com/KobeissiLetter/status/2119201719099822544)。unusual_whales 引《经济学人》：按今天的利率把尚未还清的余额再融资，平均每月多付大约 335 美元；例子里的新利率是 7.4%：[帖](https://x.com/unusual_whales/status/2119112896127082634)。7.18% 是购房申请那张里的 30 年利率。7.4% 是再融资例子。131 是指数点位。

美联储资产负债表是 Kobeissi 的一张，不是利率决定。截至 11 月 4 日那一周扩大 30 亿美元，到 6.75 万亿美元，是 2025 年 3 月中以来第三高；从 2025 年 12 月的低点以来增加 2120 亿美元；国债持有增加 3900 亿美元，到 4.58 万亿美元，是 2024 年 3 月以来最高；抵押贷款支持证券减少 1700 亿美元，到 1.88 万亿美元，是 2020 年 6 月以来最低；比疫情前高 2.99 万亿美元，或 80%：[帖](https://x.com/KobeissiLetter/status/2119181497529684135)。30 亿是一周。2120 亿是从 12 月低点算的。3900 亿和 -1700 亿是资产结构。Gayed 的另一句是：就业强不能修好债券市场仍在定价的赤字；美联储想加息就加，长端决定钱的价格：[强就业](https://x.com/leadlagreport/status/2119120227556368572)、[长端](https://x.com/leadlagreport/status/2119049733633179923)。Brooks：人工智能抛售像一场自然实验，10 年期的 10 年远期利率还是稳的，更短的收益率在掉，所以把长端抬起来的是财政，不是人工智能：[帖](https://x.com/robin_j_brooks/status/2119053070110019839)。“短端在掉”是这一帖。“10 年远期是稳的”也是这一帖。

期权是周四的纪录，周六才写成帖。Kobeissi：周四芝商所看跌期权成交放到纪录的 1123 万张，超过 2025 年 4 月 4 日的 1022 万张；20 日均值大约 700 万张，2022 年在大约 400 万张附近；成交最高的 10 天里有 8 天在 2026 年：[帖](https://x.com/KobeissiLetter/status/2119160893950828791)。1123 万是周四，不是周日。

黄金没有新的现货价，但有新的目标和购买量，两边都不要补数字。零对冲的标题：高盛再次下调黄金目标，Warsh 暂时杀掉了“货币贬值”交易，长期仍建设性，只是不是今天：[帖](https://x.com/zerohedge/status/2119226001657930207)。标题里没有新的目标价。上一份日报里的 4150 和 4800 不在这里改写，也不要猜这次砍到了多少。Gold Telegraph：中国央行连续第 24 个月买金，10 月再买 25.8 吨，今年累计 129 吨：[帖](https://x.com/GoldTelegraph/status/2119195693512610283)。peruvian_bull 把 10 月写成这 24 个月里买得最多的一个月，而且发生在金价下跌的时候：[帖](https://x.com/peruvian_bull/status/2119099060078739878)。25.8 吨和 129 吨是 Gold Telegraph。上一份的 7830 万盎司和 3064.1 亿美元不在这里重算。Tavi Costa：白银比 200 日均线低了将近 30%，上一次类似的位置是 2020 年 3 月：[帖](https://x.com/TaviCosta/status/2119186131980099967)。将近 30% 是距均线。Charlie Bilello：比特币 -13% 和黄金 -6% 是 2026 年到目前表现最差的两类大类资产，这是以前任何一个日历年没见过的组合：[帖](https://x.com/charliebilello/status/2119067482153779367)。-6% 是黄金的今年至今。将近 -30% 是白银距 200 日均线。

高盛自己的账号这个窗口没有黄金目标。Lou Miller 谈的是传统防守股在当前价格上价值有限，没有给指数点位：[帖](https://x.com/GoldmanSachs/status/2119067348241879312)。欧元区通胀是 Hanke 的另一国：10 月 4%，目标 2%，已经连续八个月高于目标：[帖](https://x.com/steve_hanke/status/2119361534019461579)。4% 不是美国的 CPI。美国的通胀数字，Yardeni 和 El-Erian 都写成这周才会来。

日经是 RenMac 的一张。东京被低估报道，日经现在处于熊市，较低点 -20.6%，软银的信用违约互换走到四年最宽：[帖](https://x.com/RenMacLLC/status/2119064795110576602)。-20.6% 是日经从 6 月高点。四年最宽是软银的互换，不是股价。

## 要盯住的五件事

1. **周一开盘前，这个窗口没有指数期货。** 现货周六、周日都不开。抓取结束是美东周日大约 5:17。期货要到美东 18:00 才开。周五的开盘点位和收盘百分比都在上一份日报里，不在这里重算，也不要拿今年至今的 +7.83% 和 +6.8% 去倒推收盘点位。
2. **伯克希尔的回购大约是 96 亿美元，现金不是一个数。** 96 亿是 Kobeissi、金融时报、彭博、First Squawk 和 Morning Brew。大约 96.5 亿和 7 月 33.9 亿、8 月 8.47 亿、9 月 54.1 亿是 StockMKTNewz。现金是大约 3770 亿、3774 亿，以及 The Transcript 的大约 3523 亿。经营利润是 127 亿或 127.1 亿、同比 -5.8%，Seeking Alpha 写成 -6%。谷歌持仓 1.06 亿股、378 亿美元是持仓帖。克拉默的“不明智”是另一句。
3. **霍尔木兹的帖不能收成一次袭击。** 一艘触雷的油轮、两艘触雷的油轮、格什姆爆炸的两种解释、美军的有限打击、一艘货船、利雅得大楼的“遇袭”和“试图打击”、胡塞未被确认的设施宣布、一架被拦截的无人机，按上面的链接分开。Brooks 的 60 美元是战后路径。66 亿美元是零对冲标题里的布伦特平仓。这个窗口没有新的油价结算。
4. **数据中心同时存在禁令句、信和创纪录的出货。** Hanke 的“得州已经禁止”没有第二家用同样的句子。地方禁令是大约 40 个到 500 多个。CoreWeave 的信还在谈。firstadopter 写成建设会继续。非国防资本品出货同比 +11.6%，到 860 亿美元。生产率 +3.5%。单位劳动力成本 -0.7%。
5. **这周会改写利率句子的是通胀数据，不是周末这几张。** Yardeni 和 El-Erian 都把通胀数据放在这周。房贷是 7.18% 和 7.4% 两张。高盛黄金目标的标题说又砍了，但没有新数字。中国 10 月买金 25.8 吨。白银距 200 日均线将近 30%。看跌期权 1123 万张是周四。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。11 月 5 日的距高点不是周日的现价。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 回购 | BRK.B | 三季度 96 亿美元，也有大约 96.5 亿美元。2026 年累计 144 亿美元。月度是 33.9 亿、8.47 亿、54.1 亿。2025 年四个季度被写成 0 | [96 亿](https://x.com/KobeissiLetter/status/2119079789751414924)、[96.5 亿](https://x.com/StockMKTNewz/status/2119071034921853233)、[纪录](https://x.com/MorningBrew/status/2119092654755414350) |
| 现金两套 | BRK.B | 大约 3770 亿美元，Seeking Alpha 写成 3774 亿。The Transcript 是大约 3523 亿，环比 -1.9% | [3770 亿](https://x.com/StockMKTNewz/status/2119072966369525918)、[3774 亿](https://x.com/SeekingAlpha/status/2119115168005411284)、[3523 亿](https://x.com/TheTranscript_/status/2119090964526760119) |
| 经营利润 | BRK.B | 127 亿美元、同比 -5.8%。First Squawk 是 127.1 亿。Seeking Alpha 写成 -6% | [127 亿](https://x.com/business/status/2119057306755149942)、[127.1 亿](https://x.com/FirstSquawk/status/2119051683254976521) |
| 持仓和提问 | AAPL、AXP、GOOGL、KO、BAC | 组合 3355 亿美元，今年 +12.7%。谷歌 1.06 亿股、378 亿美元。克拉默问这笔 Alphabet 为何不明智 | [前五](https://x.com/StockMKTNewz/status/2119079362360193101)、[不明智](https://x.com/jimcramer/status/2119185730358669402) |
| 资本政策 | AAPL | 首席财务官说放弃净现金中性目标 | [净现金](https://x.com/TheTranscript_/status/2119074901265203504) |
| 今年至今，不是收盘 | 标普、纳斯达克 100 | 标普 +7.83%。纳斯达克 100 +6.8% | [7.83%](https://x.com/StockMKTNewz/status/2119180536958820388)、[6.8%](https://x.com/StockMKTNewz/status/2119190078316478535) |
| 今年至今的大票 | NVDA、TSLA、AVGO、MU、AMD | 英伟达 +0.08%，特斯拉 -20.35%，博通 -15.14%，美光 +141.76%，AMD +109.68%。苹果 +25.94%，微软 +9.72% | [大票](https://x.com/StockMKTNewz/status/2119159247649099999) |
| 11 月 5 日低点上的距高点 | NVDA、TSM、AMD、AVGO、MU、INTC、SNDK | 英伟达 -26%，台积电 -28%，AMD -39%，博通 -41%，美光 -48%，英特尔 -64%，Sandisk -66%。标普 -6%，纳斯达克 100 -15% | [低点](https://x.com/charliebilello/status/2119083483855470768) |
| 从高点算的另一套 | 科技、SOXL | 科技 15%，杠杆科技 55%，SOXL 84%。SOX 另有大约 -40% | [15%](https://x.com/carlquintanilla/status/2119140138798457325)、[40%](https://x.com/steve_hanke/status/2119286036526174222) |
| 年底目标 | 标普 | Yardeni 仍是 7900。摩根大通仍是 8000。倍数从 1 月高点压缩大约 4 倍 | [7900](https://x.com/carlquintanilla/status/2119146701168807940)、[8000](https://x.com/carlquintanilla/status/2119047699085643938) |
| 预期市盈率 | 科技、标普 | 科技大约 17 倍，标普大约 18 倍，2017 年以来第一次科技更便宜。2025 年 10 月科技大约 32 倍 | [17 倍](https://x.com/MorningBrew/status/2119135399440441773) |
| 一周 | 标普、纳指、XLC、XLY | 标普 -2.7%。综合指数 -3.4%。通信 +5.4%，可选消费 +3.3%。平均股票略超 -1%，351 只跑赢标普 | [一周](https://x.com/Stephanie_Link/status/2119155752116138331)、[351](https://x.com/RyanDetrick/status/2119099383098544435) |
| 图上的阶段 | NBIS、INTC、SNDK、GOOG、TSM、ORCL | 四只被画进第 4 阶段。台积电被写成双顶。甲骨文被写成这种恐惧见过 | [第 4 阶段](https://x.com/TrendSpider/status/2119259864195055901)、[台积电](https://x.com/TrendSpider/status/2119071120737628174) |
| 规则 | SPY、QQQ、SMH | 留在 8 日和 21 日均线之下就该做交易，不是做组合 | [8 日和 21 日](https://x.com/RedDogT3/status/2119207583403962700) |
| 出货和生产率 | 资本品、芯片设备 | 剔除飞机的非国防资本品出货同比 +11.6%，到 860 亿美元。相关订单同比 +27%。生产率 +3.5%，单位劳动力成本 -0.7% | [出货](https://x.com/KobeissiLetter/status/2119249539873886436)、[生产率](https://x.com/KobeissiLetter/status/2119116014478565476) |
| 得州 | CRWV | 给 Gina Hinojosa 的信还在谈项目。另有“已经禁止”和“地方禁令从大约 40 个到 500 多个” | [信](https://x.com/business/status/2119169304109142096)、[禁止](https://x.com/steve_hanke/status/2119037157759414498)、[500 多个](https://x.com/theinformation/status/2119067394060464199) |
| 涡轮和长约 | 软银、GEV、MU | 马斯克称软银涡轮订单违约。GE Vernova 的回答被转述成没有看到退出。美光的协议被引成不能单方取消 | [违约](https://x.com/zerohedge/status/2119067457717412198)、[没有](https://x.com/aleabitoreddit/status/2119023086502805730) |
| 否认 | TSM | 发言人被报道否认探索 3D DRAM | [否认](https://x.com/aleabitoreddit/status/2119097842363211968) |
| 新云 | NBIS、CRWV、IREN | 估值砸过之后 Nebius 被看成有吸引力。CoreWeave 的高利息被单独点名。IREN 有 90% 预付款和 H100 价格翻倍 | [新云](https://x.com/aleabitoreddit/status/2119077473107472729) |
| 信用句子 | 超大规模公司、OWL | 发债超过全年预测是标题。Blue Owl 说自己承担的是微软、亚马逊、Meta 的租约信用 | [发债](https://x.com/zerohedge/status/2119127353360085176)、[租约](https://x.com/TheTranscript_/status/2119142847291285584) |
| 平仓标题 | 布伦特 | 对冲基金吐出 66 亿美元布伦特多头。Brooks 的战后路径是 60 美元。没有新结算价 | [66 亿](https://x.com/zerohedge/status/2119188257908904235)、[60 美元](https://x.com/robin_j_brooks/status/2119060294865391686) |
| 周日早上 | 阿美大楼 | Blas：遇袭，损坏被说成轻微，外立面有两层楼的洞，无人受伤。能源部的句子是“试图打击” | [遇袭](https://x.com/JavierBlas/status/2119357203933180348)、[试图](https://x.com/financialjuice/status/2119365076843127187) |
| 目标被砍但没有新数字 | 黄金 | 高盛再次下调目标的标题没有写出新价格。中国 10 月再买 25.8 吨，今年 129 吨。白银距 200 日均线将近 30% | [标题](https://x.com/zerohedge/status/2119226001657930207)、[25.8 吨](https://x.com/GoldTelegraph/status/2119195693512610283)、[白银](https://x.com/TaviCosta/status/2119186131980099967) |
| 房贷 | 30 年利率 | 7.18% 连着购房申请指数 131。7.4% 是再融资例子，每月大约多 335 美元 | [7.18%](https://x.com/KobeissiLetter/status/2119201719099822544)、[7.4%](https://x.com/unusual_whales/status/2119112896127082634) |
| 内部人 | MGM | Keith Meister 经公司大约买了 5200 万美元，仓位增加将近 33%，股票处在 2025 年 4 月以来最差的回撤 | [5200 万](https://x.com/TrendSpider/status/2119108869599457660) |
| 目标价下调 | IONQ | 杰富瑞 65 美元，从 80，维持买入。瑞穗 42，从 52，维持跑赢。摩根士丹利 40，从 43，维持标配 | [三家](https://x.com/StockMKTNewz/status/2119023876420084049) |
| 政府股权 | GFS | 首席执行官估计各项协议完成后，美国政府大约持有 7% | [7%](https://x.com/TheTranscript_/status/2119223099577241856) |
| 流量 | SHOP | 人工智能流量同比 2.6 倍，订单 3.3 倍，转化率高 64% | [2.6 倍](https://x.com/TheTranscript_/status/2119248021309317419) |
| 熊市句 | 日经、软银 | 日经从 6 月高点 -20.6%。软银信用违约互换四年最宽 | [日经](https://x.com/RenMacLLC/status/2119064795110576602) |

## 后续走势：三套可以证伪的剧本

这个窗口没有新的指数点位，也没有周日晚间期货。已经写下来的锚是：伯克希尔回购大约 96 亿美元、现金至少有 3770 亿和 3523 亿两套、标普今年至今 +7.83%、纳斯达克 100 +6.8%、科技预期市盈率大约 17 倍对标普大约 18 倍、11 月 5 日低点上的距高点、以及一串还不能并成一次袭击的霍尔木兹帖。下面三套的顺序，以抓取结束时现货仍休市、期货尚未重开为前提。

**战争溢价继续掉，周一不给周末的军事帖重新定价，人工智能仍被当成减速带。** 触发器是 Brooks 把油价写成会在战争结束之后很快回到 60 美元、美元随之走弱，firstadopter 把收场写成会放松加息压力并帮到人工智能融资，Yardeni 把反弹维持在年底 7900，摩根大通维持 8000，Cathie Wood 认为选举掀不翻数据中心。这条路径失败的条件，是周日晚间期货把水雷、有限打击或利雅得大楼当成新的供给冲击，布伦特离开“已经掉到近月期货下面”的那张图，而不是走向 60 美元；或者 10 年远期利率不再是 Brooks 写的那种稳定，财政把长端再抬起来。

**周五不是底，资本开支和信用会在周一继续计价。** 触发器是伯里拒绝把糟糕的一天叫成底部，Hanke 把信息处理设备占 GDP 的 5.35% 放在互联网泡沫 4.46% 之上、并把 SOX 写成大约 -40%，Bob Elliott 把近端风险放在资本开支而不是最终需求，Keith 维持选举后卖出 QQQ、通往 Quad 4、并对 2027 年示警，零对冲同时写着 2028 年的数据中心悬崖和超大规模发债超过全年预测。TrendSpider 已经把 Nebius、英特尔、Sandisk 和谷歌画在第 4 阶段。这条路径失败的条件，是 Detrick 那张“200 日均线上方的 4% 暴跌很少继续大跌”在周一成立，351 只股票跑赢标普的宽度还在，而且科技停在大约 17 倍、没有回到他没有写过的新高。

**油价决定黄金和美元是跟着溢价消失走，还是跟着周末的袭击帖走。** 触发器是同一段窗口里，Brooks 写溢价已经回吐、现货油低于近月期货，零对冲写对冲基金吐出 66 亿美元布伦特，而水雷、爆炸、有限打击和利雅得大楼的帖还在增加。高盛黄金目标的标题说又砍了，但没有新价格；中国仍在买，10 月 25.8 吨；白银距 200 日均线将近 30%。它失败的条件，是布伦特留在“低于近月期货”的那一侧、大楼和两艘油轮都没有把价格打回 100 美元以上，同时黄金目标价却从标题里的“再次下调”继续下移，那就是加息和 Warsh 盖过了海峡；或者布伦特因为这些帖重新站上周五结算已经离开的位置、白银把将近 30% 的均线差距收掉，那就是供给冲击盖过了 Brooks 的 60 美元。

另有一张还没公布的通胀数据，不并进上面三套。Yardeni 写这周有通胀报告和一连串美联储讲话。El-Erian 写这周的数据包括美国通胀，电话会上的通胀提及已经到 820 次。欧元区 10 月的 4% 是另一国，已经公布。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周日晚间期货和周一开盘。它不决定仓位大小。周日现货不开。抓取结束时，周日晚间的股指期货还没开。

**周一开盘前只核对五样东西。** 期货是把周末的霍尔木兹帖当成新的供给冲击，还是沿用 Brooks 已经回吐的战争溢价、走向他写的战后 60 美元。指数是停在“减速带”这一侧，Yardeni 的 7900 和摩根大通的 8000 还都在，科技大约 17 倍仍低于标普大约 18 倍，还是重新交易伯里拒绝承认的底部、以及 11 月 5 日低点上那些距高点。伯克希尔是交易大约 96 亿美元的回购和谷歌那 378 亿美元的持仓，还是把 3770 亿和 3523 亿的现金并成一个数。后者这些帖没有授权。利率是房贷停在 7.18% 的购房申请，还是去交易 7.4% 的再融资例子；长端是 Brooks 写的财政，不是人工智能。黄金是交易高盛标题里那次没有写出数字的下调，还是交易中国的 25.8 吨和白银距 200 日均线将近 30%。五样里，期货不给水雷和大楼重新定价、科技倍数留在 17 倍附近、回购按 96 亿美元而不是按两套现金交易，这些帖给出的默认顺序是把周末当成减速带的消化，高于去追已经在第 4 阶段图里的半导体。期货把布伦特打回 100 美元上方、或者标普期货掉回 Detrick 写成很少继续的那种 200 日均线上方的暴跌，默认顺序掉过头来：海峡和信用的映射，高于去抄周五那次被伯里拒绝叫成底部的反弹。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：回购 96 亿美元，2026 年累计 144 亿美元，净买入股票 112 亿美元。生产率 +3.5%，单位劳动力成本 -0.7%。资本品出货同比 +11.6%，到 860 亿美元。资产负债表一周 +30 亿美元，到 6.75 万亿美元。购房申请指数 131，30 年利率 7.18%。看跌期权周四 1123 万张。
- 伯里：糟糕的一天不够叫成底部。
- 克拉默：问伯克希尔的 Alphabet 仓位为什么又大又不明智。没有给新的指数点位。
- Cathie Wood：选举掀不翻人工智能。生产率会变成薪酬、利润率和更低的价格。ARK 的机构号补了一句，中期选举后一年标普通常上涨。
- Yardeni：年底目标经 Quintanilla 仍是 7900。自己的帖写倍数不再上升，这周看通胀和美联储讲话。连续第四周绊倒。
- 摩根大通，经 Quintanilla：周期中重置，目标 8000。倍数压缩大约 4 倍。
- Steve Hanke：信息处理设备占 GDP 5.35%，对照互联网泡沫 4.46%。SOX 大约 -40%。得州禁令是他的句子。赤字 6.2%。格什姆的小规模打击和货船是他的另外两句。
- Gary Black，线外：两座的 Cybercab 机会有限，因为超过两名乘客的单子被排除。他早就改口，不再把 Cybertruck 看成最初报价那种机会。没有新的指数点位。
- Sawyer Merritt：特斯拉在 2027 年中停产之前又加了一个 Cybertruck 班次。马斯克把人和产线让给 Cybercab。座位数之争里，他用联邦公路管理局的出行研究：约 85% 的网约车只有 1 到 2 名乘客，其中 1 名占 64.2%，2 名占 21.5%，3 名及以上占 13%。
- Michael Gayed，线外：一周标普 -2.7%，高收益利差 348 个基点。强就业修不好赤字。长端决定资金价格。
- Ryan Detrick，线外：平均股票略超 -1%，351 只跑赢。从 10 月 6 日高点到 -5% 用了 23 个交易日，他目前不把这看成熊市的标准起手。200 日均线上方的 4% 暴跌很少马上延续。2026 年每个月大约 8.6 万个岗位，他仍把劳动力看成下半年的亮点。
- Robin Brooks，线外：战争溢价已经回吐，战后油价很快回到 60 美元，美元会跟着掉。10 年远期利率稳定，短端在掉，长端是财政。
- Ole Hansen 这个窗口没有新的结算价。Javier Blas 的新帖是利雅得的楼，不是油价。
- firstadopter，线外：战争收场会压低能源价格、减轻加息压力，对人工智能融资是正的。CoreWeave 的信被他读成得州建设会继续。
- Bob Elliott，线外：近端最大的风险是资本开支被卡住。Anthropic 买家看到的估值低至 1.1 万亿。
- Keith McCullough，线外：选举后卖出 QQQ 的决定还在。节目标题是通往 Quad 4。44 个多头、56 个空头是那套信号产品里的个数。
- RedDog，线外：8 日和 21 日均线之下，SPY、QQQ、SMH 用交易而不是组合。
- aleabitoreddit：美光的照付不议和 GE Vernova 的“没有看到退出”用来对冲马斯克的涡轮违约标题。Nebius 在砸估值之后被他看成有吸引力。3D DRAM 有了发言人否认的报道。
- 零对冲：66 亿美元的布伦特平仓是标题。黄金目标再次下调是标题，没有新价格。数据中心的悬崖被写成 2028。信用有“紧缩就在眼前”和“打了个哈欠”两句。
- First Squawk，线外：经营利润 127.1 亿美元、同比 -5.8%，回购约 96 亿美元。霍尔木兹的水雷、无人机和爆炸见上。没有指数期货。
- 美联储的账号这个窗口没有新帖。高盛账号只让 Lou Miller 说传统防守股价值有限。

**财报和数据的顺序。** 先看已经写进标题的伯克希尔回购、两套现金、生产率、资本品出货、房贷申请和霍尔木兹的分句。然后才是这周还没公布的美国通胀。Yardeni 没有在这张帖里写出公布日。Earnings Whispers 这个窗口的日历帖是一张图，正文没有列出新的代码：[图](https://x.com/eWhispers/status/2119071709168861388)。IonQ 的三家目标价已经下调，那是周六的评级帖，不是下周一的财报。

**明确留在观察、不放进计划的东西。** 不用今年至今的 +7.83% 倒推收盘点位。不把 11 月 5 日低点上的距高点写成周日现价。不把 96 亿美元和大约 96.5 亿美元轧成第三个数，也不把 3770 亿和 3523 亿取平均。不把 -5.8% 改成 -6%，也不把 -6% 改成 -5.8%。不把 Hanke 的得州禁令写成 CoreWeave 的信，也不把信写成禁令。不把马斯克的涡轮违约标题写成 GE Vernova 已经确认。不把一艘触雷、两艘触雷、货船、有限打击和利雅得大楼收成一次事件。不给高盛的黄金目标补一个标题里没有的价格。60 美元是战后路径。7.18% 和 7.4% 不是同一个利率。1123 万张看跌期权是周四。德意志银行的时间线没有读到。LiveSquawk 的可见时间线停在窗口开始之前。Liz Ann Sonders、Gundlach、SpotGamma、美国银行、花旗、摩根大通、摩根士丹利、黑石、美国财政部和美联储的账号这个窗口没有新的指数点位。Mark Minervini 的帖是研讨会通知。Bill Ackman 的帖在阅读推荐和播客赞助商。Ray Dalio 的帖是会议原则。Peter Lynch 式的语录和 Wordle 不进计划。

## 帖文索引

回购和现金：[96 亿美元、净买入 112 亿](https://x.com/KobeissiLetter/status/2119079789751414924)、[大约 3770 亿](https://x.com/StockMKTNewz/status/2119072966369525918)、[大约 3523 亿](https://x.com/TheTranscript_/status/2119090964526760119)、[经营利润 127 亿](https://x.com/business/status/2119057306755149942)。

估值和路径：[科技大约 17 倍](https://x.com/MorningBrew/status/2119135399440441773)、[年底 7900](https://x.com/carlquintanilla/status/2119146701168807940)、[目标 8000](https://x.com/carlquintanilla/status/2119047699085643938)、[11 月 5 日距高点](https://x.com/charliebilello/status/2119083483855470768)、[不是底部](https://x.com/michaeljburry/status/2119092664612090018)。

海峡、油和黄金：[两艘油轮触雷](https://x.com/DeItaone/status/2119175971752587615)、[利雅得的楼](https://x.com/JavierBlas/status/2119357203933180348)、[战后 60 美元](https://x.com/robin_j_brooks/status/2119060294865391686)、[黄金目标再次下调，没有新价格](https://x.com/zerohedge/status/2119226001657930207)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-08 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 88 条、彭博商业账号 75 条、《华尔街日报》75 条、《经济学人》76 条、零对冲 48 条、FinancialJuice 59 条、《The Street》48 条、Investing.com 24 条，是读穿窗口后的计数。德意志银行的 0 是读取失败。Downtown 的时间线返回空页，0 也不是确认沉默。LiveSquawk 不在表里，可见时间线停在窗口开始之前。线外的 First Squawk 是 189 条。保罗·克鲁格曼、BBC Business、雅虎财经、markets、沃伦·巴菲特、CNN Business、美联储、彭博主号、Squawk Box、Andrew Ross Sorkin、Bloomberg Originals、美国财政部、Lyn Alden、黑石、美国银行、Teslarati、TradingView、Bloomberg TV、纽约时报商业、摩根大通、花旗、Hindenburg、Bill Gurley、美国证交会、Bloomberg Economics、纳斯达克交易所、摩根士丹利、CNBC Now、Morgan Housel、芝商所、Nouriel、amit、Carl Icahn 的 0，是窗口内没有计为原创的新帖。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,443,750 | 88 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,329,321 | 76 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,278,209 | 75 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,312,807 | 20 |
| 5 | [@business](https://x.com/business) | 10,491,582 | 75 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,570,265 | 2 |
| 7 | [@FT](https://x.com/FT) | 7,114,946 | 18 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,257,402 | 29 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,381,779 | 12 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,648,964 | 4 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,605,636 | 1 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,430,357 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,354,977 | 18 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,430,902 | 48 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,426,453 | 1 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,047,364 | 3 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,004,834 | 1 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,735,584 | 8 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,568,304 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,529,536 | 1 |
| 21 | [@chamath](https://x.com/chamath) | 2,487,641 | 2 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,440,015 | 6 |
| 23 | [@BW](https://x.com/BW) | 2,288,451 | 1 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,329 | 16 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,157,328 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,129,391 | 1 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,079,188 | 0 |
| 28 | [@markets](https://x.com/markets) | 2,049,078 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,971,370 | 7 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,796,061 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,777,412 | 4 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,771,107 | 2 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,710,165 | 1 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,700,699 | 0 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,595 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,617,242 | 19 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,603,119 | 0 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,537,786 | 24 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,512,492 | 1 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,471,703 | 1 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,629 | 2 |
| 42 | [@Bloomberg](https://x.com/Bloomberg) | 1,357,062 | 0 |
| 43 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,356,750 | 1 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,253,364 | 2 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,225,733 | 48 |
| 46 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,194,229 | 0 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,194,136 | 1 |
| 48 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,192,383 | 0 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,184,968 | 0 |
| 50 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,169,750 | 17 |
| 51 | [@USTreasury](https://x.com/USTreasury) | 1,166,266 | 0 |
| 52 | [@nntaleb](https://x.com/nntaleb) | 1,165,187 | 1 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,157,661 | 1 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,154,246 | 10 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,140,309 | 0 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,117,510 | 4 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,108,916 | 25 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,097,684 | 2 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,081,942 | 0 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,067,681 | 6 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,377 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,702 | 22 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,004,489 | 0 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 956,055 | 59 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,065 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 934,872 | 0 |
| 67 | [@tradingview](https://x.com/tradingview) | 907,500 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 894,409 | 0 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 891,107 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,564 | 5 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 874,189 | 6 |
| 72 | [@axios](https://x.com/axios) | 863,469 | 7 |
| 73 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 862,296 | 0 |
| 74 | [@steve_hanke](https://x.com/steve_hanke) | 862,056 | 27 |
| 75 | [@jpmorgan](https://x.com/jpmorgan) | 860,773 | 0 |
| 76 | [@Citi](https://x.com/Citi) | 853,158 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 847,759 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,623 | 1 |
| 79 | [@ecb](https://x.com/ecb) | 830,921 | 2 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,596 | 1 |
| 81 | [@bgurley](https://x.com/bgurley) | 811,908 | 0 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,311 | 0 |
| 83 | [@economics](https://x.com/economics) | 806,299 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 790,127 | 1 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,597 | 0 |
| 86 | [@markminervini](https://x.com/markminervini) | 773,870 | 1 |
| 87 | [@leadlagreport](https://x.com/leadlagreport) | 769,278 | 10 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 759,580 | 0 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,592 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 738,373 | 0 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 718,794 | 12 |
| 92 | [@CMEGroup](https://x.com/CMEGroup) | 712,307 | 0 |
| 93 | [@Nouriel](https://x.com/Nouriel) | 710,536 | 0 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 674,495 | 9 |
| 95 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,846 | 0 |
| 96 | [@fundstrat](https://x.com/fundstrat) | 672,722 | 1 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,662 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,586 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 636,748 | 3 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 626,589 | 1 |
