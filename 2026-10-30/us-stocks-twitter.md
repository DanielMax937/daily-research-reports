# 美股 Twitter 观点日报 · 2026-10-30

周四的现货收盘是跌的，跌幅集中在纳斯达克。周五早上的期货跌得更深。First Squawk 的非官方收盘：纳斯达克收 26177.91，跌 371.94 点，跌 1.40%；标普收 7718.38，跌 25.60 点，跌 0.33%；道指收 52330.24，跌 144.86 点，跌 0.28%：[三行收盘](https://x.com/FirstSquawk/status/2115897119752249506)。同一账号的收盘综述把纳斯达克 100 也写成跌 1.4%，原因放在 Alphabet 因销售不及大跌 12%；人工智能投资回报的担心触发了向更广股票的轮动，标普里有 400 多只上涨，国债因避险上涨：[综述](https://x.com/FirstSquawk/status/2115909358873903319)。综合指数的 1.40% 和纳斯达克 100 的 1.4% 是两行字。点位以那三行非官方收盘为准。

到美东周五早上约 8:20，现货还没开盘。盘后期货先是纳斯达克期货跌 1.4%、标普期货跌 0.6%：[帖](https://x.com/FirstSquawk/status/2115930325486543142)。Investing.com 随后写纳斯达克 100 期货跌 1.7%：[帖](https://x.com/Investingcom/status/2115943212124668240)。04:01 UTC，First Squawk 写纳斯达克 100 跌 2%、标普跌近 1%：[帖](https://x.com/FirstSquawk/status/2116017609921704151)。Gary Black 在 10:40 UTC 的盘前快照是标普跌 1.0%、纳斯达克 100 跌 2.2%：[帖](https://x.com/garyblack00/status/2116118139582697581)。《华尔街日报》11:41 UTC 写纳斯达克期货跌超 2%：[帖](https://x.com/WSJ/status/2116133504480120855)。线外的 RedDogT3 在 11:56 UTC 写标普期货跌 75 点，7612 是要看的位置：[帖](https://x.com/RedDogT3/status/2116137281262059553)。这几张都不是周五收盘。

下面每一条归纳都附有帖文链接。结算价、盘后期货和早盘口号按发帖时间分开。不同账号的预期基数不合成一个数。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-10-30**。触发时刻约 12:05 UTC，时间线补抓到 **约 12:17 UTC（北京时间 20:17，美东 8:17）**。观察窗口是 **2026-10-29 16:00 UTC 至抓取结束**，也就是北京时间周五零点到晚上 8 点 17 分。这覆盖美东周四中午以后的现货、周四收盘、周四盘后财报，以及周五开盘前。美股现货 9:30 才开盘。美东 8:30 的就业成本指数和 9:45 的芝加哥 PMI，抓取结束时还没有结果帖。Bespoke 把这两项写在周五的日历上：[帖](https://x.com/bespokeinvest/status/2116120553371451872)。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。公开趋势读到的是 The Next Generation、Patrick Stewart、Peltola、Josh Jacobs、Star Trek、Halloween。里面没有标普、纳指或个股话题。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。
- 不存在官方的“美股 Top 100”。这次试了 **402** 个候选，成功读到粉丝数的有 **358** 个。排序时拿掉加密货币账号、综合新闻主号、公司品牌号和竞选主号，也拿掉科技风投和创业者主号（Marc Andreessen、Paul Graham、Naval、Jason、David Sacks、a16z、Ben Horowitz、David Friedberg）、加密快讯号 tier10k，以及 Noah Smith 和 OECD。用来排序的账号是 **347** 个，截止在 Earnings Whispers（约 57.2 万粉）。Mad Money、Aswath Damodaran、Carl Quintanilla、美银新闻、LiveSquawk、瑞银、Nick Timiraos、日经亚洲、Keith McCullough、MacroAlf、traderstewie、The Stalwart、Hedgeye、巴伦、Javier Blas、Robin Brooks、Bespoke、SpotGamma、The Transcript、firstadopter、Lisa Abramowicz、RedDogT3 落在线外，引用时会写明。排序不代表预测准确度。
- 100 个账号里，**74 个**在窗口内有按帖文链接去重后、且接口没有标成回复或转发的原创帖。路透读穿窗口，79 条。First Squawk 343 条，FinancialJuice 290 条，彭博商业账号 249 条。德意志银行的时间线返回服务器错误，表里的 0 不是确认沉默。彭博主号、彭博 markets、BBC Business、CNN Business、纽约时报商业、TradingView 的可见首页已经早于窗口起点，这几家的 0 同样不能当成确认沉默。Charlie Bilello 有 4 条市场帖被接口标成回复，所以表里是 0；正文引用的仍是他的状态页。

## 周四收盘和周五早上，讲的不是同一根 K 线

收盘价以 First Squawk 那三行为准。Investing.com 把 Alphabet 的收盘写成跌 12.6%，市值抹掉 4800 亿美元：[帖](https://x.com/Investingcom/status/2115896860783345762)。First Squawk 综述里的“大跌 12%”和 12.6% 是两行字。巴伦的标题是 Alphabet 的大跌把道指、标普和纳斯达克拉下来，但表面之下大多数股票当天是扎实的：[帖](https://x.com/barronsonline/status/2115956082258391458)。这和“400 多只标普成分上涨”是同一张宽度图的两种说法。

盘后立刻换了一张图。Bespoke：QQQ 盘后已经跌超 1%，来自英特尔和亚马逊的急跌；半导体 ETF SOXX 盘后跌 4%：[QQQ](https://x.com/bespokeinvest/status/2115897995971678353)、[SOXX](https://x.com/bespokeinvest/status/2115898684390961186)。Investing.com 的纳斯达克 100 期货跌 1.7%，发在周四 23:05 UTC。周五 04:01 UTC 的口号已经是纳斯达克 100 跌 2%、标普跌近 1%。Gary 的 10:40 UTC 是标普跌 1.0%、纳斯达克 100 跌 2.2%，10 年期收益率降到 4.93%，布伦特涨 1.6% 到 117 美元。零对冲 12:07 UTC 的盘前异动是七巨头一起跌：亚马逊跌 7.3%，英伟达跌 2.8%，特斯拉跌 2.4%，Meta 跌 1.8%，苹果跌 1.1%，Alphabet 跌 0.7%，微软跌 0.6%：[帖](https://x.com/zerohedge/status/2116139928174182778)。亚马逊这一只，盘后先被写成跌 6%、跌 7% 和跌 10%，周五盘前停在零对冲的 7.3%。英特尔从盘后跌 17%、18%、20%、21%，写到 Kobeissi 周五 09:44 UTC 的跌 27%。这些百分比按原帖留着，不合成一个收盘跌幅。

线外的 Ryan Detrick 写，标普过去两个周五都是跌的，连续三个周五下跌要回到 3 月和 4 月那一串六个周五；期货看着会走出第三个：[帖](https://x.com/RyanDetrick/status/2116018269975121953)。

## 观点分成四组

### 1. 指数跌得少，纳指跌得多，宽度和科技是两张图

周四现货的分裂已经写在收盘帖里。标普跌 0.33%，纳斯达克跌 1.40%，同时 400 多只标普成分上涨。FinancialJuice 的收盘竞价失衡是标普 44.833 亿美元、纳斯达克 100 29.624 亿美元、道指 9.736 亿美元、七巨头 10.513 亿美元：[帖](https://x.com/financialjuice/status/2115894164860649473)。单位按帖文的 “MLN” 理解成百万美元。

Bespoke 把财报反应拆开：这个财报季里，已经公布的股票平均下来，公布当日是涨的；被砸的是科技，平均跌 1.2%；可选消费是反弹最大的一组：[帖](https://x.com/bespokeinvest/status/2115926325139804438)。Jim Cramer 周五早上写，周四有一笔很大的程序，几十亿美元从科技挪到消费品、医疗和银行；极端反应来自对冲基金急着买可口可乐这种包装消费品、卖掉四个字母的代码。他用强生和第一资本在没有新闻时上涨，来说明这种挪仓：[挪仓](https://x.com/jimcramer/status/2115975905202024860)、[包装消费品](https://x.com/jimcramer/status/2116107189962129477)、[强生](https://x.com/jimcramer/status/2116107768675610636)。他另写，选举被交易成会关掉数据中心建设，他认为这不会发生，但心理损伤已经在，对冲基金想出去：[帖](https://x.com/jimcramer/status/2116107574647149008)。中期选举日是 11 月 3 日。

线外的 Keith McCullough 把同一天写成过程日：从科技出来，进必需消费，医疗继续拿着。Hedgeye 的美股行业配置第一名医疗保健 ETF 创了历史新高。高收益 OAS 利差昨天再走阔 11 个基点。10 年期 BBB 利差打到这轮周期新高。他把七巨头里超过三分之一的利润写成纸面利润，并且利润正从周期高点放缓。Alphabet 和 Meta 的隐含波动率在他那里仍然“ complacent”。高贝塔动量正在经历他写成的、被广泛持有的因子里最快的一段下跌之一：[行业](https://x.com/KeithMcCullough/status/2116102485064528022)、[医疗](https://x.com/KeithMcCullough/status/2115881852787638392)、[利差](https://x.com/KeithMcCullough/status/2116103849773822273)、[BBB](https://x.com/KeithMcCullough/status/2116104121849716955)、[纸面利润](https://x.com/KeithMcCullough/status/2116103417420779593)、[波动率](https://x.com/KeithMcCullough/status/2116104845413527603)、[动量](https://x.com/KeithMcCullough/status/2116105471337869578)。

Kobeissi 的宽度用的是高点回撤，不是周四涨跌幅：标普成分里超过 60% 已经处在熊市区间，较纪录高点跌了 20% 或更多；七巨头里有四只处在熊市区间，七个名字合计从高点抹掉 4 万亿美元。他们把这写成隐蔽熊市，并写成巨大的机会：[帖](https://x.com/KobeissiLetter/status/2115944476292104688)。

Mark Minervini 在周四收盘前写，前一天他在 IBD Live 上公开了做空 SPY 和 DIA；如果周四收盘不好，他可能会把空头加到超配。他当时唯一的个股多头是梯瓦，唯一的 ETF 多头是生物科技 IBB，两条都还拿着：[帖](https://x.com/markminervini/status/2115877761835241654)。周四收盘三个指数都是跌的。窗口里没有他确认已经加到超配的后续帖。

### 2. 亚马逊和英特尔把周四晚上切成两边，现金流叙事还在

亚马逊是双不及，经营利润和云是超的。Gary：盘后跌 6%。收入 2019 亿美元，预期 2023 亿美元；每股收益 1.89 美元，预期 1.97 美元；经营利润 281 亿美元，预期 261 亿美元；资本开支 773 亿美元，预期 588 亿美元；AWS 460 亿美元，预期 457 亿美元；线上商店 685 亿美元，预期 696 亿美元；广告 196 亿美元，预期 209 亿美元。同一条帖的开头把 2026 财年资本开支指引写成 2.2 亿美元，后面又写成维持此前 2200 亿美元的指引。两行都留在这条帖里：[帖](https://x.com/garyblack00/status/2115910608818425934)。

雅虎财经的预期基数不同：收入 2019 亿美元对 2022.5 亿美元，调整后每股收益 1.89 美元对 1.97 美元，四季净销售指引 2400 亿到 2470 亿美元对 2445 亿美元，AWS 459 亿美元对 456.8 亿美元：[帖](https://x.com/YahooFinance/status/2115900985692356777)。Investing.com 的每股收益预期是 1.96 美元，销售预期是 2021 亿美元，并写盘后跌 7%：[每股收益](https://x.com/Investingcom/status/2115897783567749581)、[跌 7%](https://x.com/Investingcom/status/2115902647253262747)。TrendSpider 的销售预期是 2023.08 亿美元，标题是双不及、跌 10%：[帖](https://x.com/TrendSpider/status/2115897499022135578)。1.96、1.97，以及 2021 亿、2022.5 亿、2023 亿、2023.08 亿，都按原帖留着。

线外的 The Transcript 给了分部：净销售同比增 12.1% 到 2019 亿美元；经营利润增 61.2% 到 281 亿美元，利润率 13.9%，一年前 9.7%；净利润降 2.4% 到 207 亿美元。AWS 增 39.3% 到 460 亿美元，经营利润增 55.4% 到 178 亿美元，利润率 38.7%。北美增 6.2% 到 1129 亿美元。国际增 5.4% 到 431 亿美元。AWS 贡献了大约 63.3% 的经营利润和 59.6% 的收入增量。净利润下降，是因为营业外从一年前的 107 亿美元收益变成 12 亿美元亏损：[分部](https://x.com/TheTranscript_/status/2115901875073737189)、[营业外](https://x.com/TheTranscript_/status/2115902066602500453)。CEO 的指引句是 2026 年现金资本开支仍看到约 2200 亿美元，大部分给 AWS，2027 年还会明显更多：[帖](https://x.com/TheTranscript_/status/2115918171756699824)。同一账号写 AWS 积压 5780 亿美元，同比三位数增长；亚马逊认为 AWS 在 2027 和 2028 年都可以增速超过 40%，并在 5 到 10 年里成为 1 万亿美元收入的业务：[积压](https://x.com/TheTranscript_/status/2116125739024261526)、[40%](https://x.com/TheTranscript_/status/2116127291281719364)。The Stalwart 的 AWS 是剔除汇率增 39%，预期增 38%：[帖](https://x.com/TheStalwart/status/2115897271250211056)。Bespoke：这是 2022 年 4 月以来第一次收入和利润同时不及预期：[帖](https://x.com/bespokeinvest/status/2115908665404170738)。TrendSpider 另写，财报之后亚马逊的市盈率落到十多年来最低：[帖](https://x.com/TrendSpider/status/2115987050927464612)。周五盘前的 7.3% 是零对冲的快照，理由被写成 AWS 增长不够看，不是盘后的 10%。

Andy Constan 盘后问亚马逊会用哪种发行：股票承销加强制可转、ATM 股票、或者一笔 250 亿美元的基准债，或者几样一起。他没有给出已经宣布的方案：[帖](https://x.com/dampedspring/status/2115900162732404834)。

英特尔是季度超预期、指引把股价砸下去。TrendSpider：调整后每股收益 0.52 美元对 0.40 美元，销售 165.13 亿美元对 164.67 亿美元；四季调整后每股收益指引 0.25 美元对 0.43 美元；四季销售指引 155 亿美元对 170 亿美元；标题是跌超 20%：[帖](https://x.com/TrendSpider/status/2115898166574723532)。雅虎财经：收入 165.1 亿美元对 165.4 亿美元，调整后每股收益 0.52 美元对 0.41 美元，数据中心与人工智能收入 73.2 亿美元对 66.7 亿美元，四季收入指引 150 亿到 160 亿美元对 170.5 亿美元：[帖](https://x.com/YahooFinance/status/2115897174617989276)。Investing.com 的季度预期是每股收益 0.40 美元、收入 164.8 亿美元，并另写股价跌 20%：[季度](https://x.com/Investingcom/status/2115897910860861881)、[跌 20%](https://x.com/Investingcom/status/2115904135266451943)。《金融时报》的标题是跌 17%：[帖](https://x.com/FT/status/2115902351198302531)。The Stalwart 写跌 21%：[帖](https://x.com/TheStalwart/status/2115898013420060678)。Kobeissi 周五早上写跌幅延伸到 27%，有望成为 1974 年以来最大单日跌幅，较 6 月 30 日的纪录高点跌 53%，市值抹掉 4000 亿美元：[帖](https://x.com/KobeissiLetter/status/2116103832702693474)。27% 发在美东凌晨，还不是收盘。CNBC 的盘前标题是跌 25%：[帖](https://x.com/CNBC/status/2116085417782972662)。零对冲的盘前也是跌 25%，理由包括个人电脑疲弱。Gary 把个人电脑需求疲弱的展望写到 2027 年中。

线外的 The Transcript 引了电话会。CFO：收入、毛利率和每股收益都超过指引，数据中心收入增速是 15 年来最强；盘后当时的股价注记是跌 18%。CEO：客户过去几周开始按内存价格和供给发出个人电脑放缓的信号，终端价格上升挤压本来就有限的 IT 预算，OEM 在按更弱的动销管库存；他失望于本季满足不了强的客户需求，近端是制造供给短缺、前所未有的内存紧张，以及由此而来的个人电脑需求转弱。CFO：2027 年是投资年，预计下一年自由现金流不会转正；个人电脑库存修正在四季会感觉到很多，至少延续到一季度。数据中心客户的需求信号继续变强，行业供给约束预计贯穿 2027 年、进入 2028 年：[超指引](https://x.com/TheTranscript_/status/2115905398859563492)、[个人电脑](https://x.com/TheTranscript_/status/2115917105849934306)、[自由现金流](https://x.com/TheTranscript_/status/2115921971057934438)、[库存](https://x.com/TheTranscript_/status/2115922224951730449)、[数据中心](https://x.com/TheTranscript_/status/2115921171669819439)。First Squawk 另有 CEO 的一句：先进有机基板短缺也在影响 EMIB 封装的产出：[帖](https://x.com/FirstSquawk/status/2115916466847687140)。

线外的 SpotGamma 在财报前写，期权定价大约上下 9.3%，100 美元附近是负伽马：[帖](https://x.com/spotgamma/status/2115888721769771161)。盘后的 17% 到 21% 已经大于这个 9.3%。Keith 转述：英特尔只占标普大约 0.70%，但是半导体 ETF SOXX 的第二大持仓、大约 8.3%，这个跌幅会拖半导体指数，并可能在三倍做多 SOXL 上造成显著的收盘竞价失衡：[帖](https://x.com/KeithMcCullough/status/2116107027315302711)。他维持英特尔、Sandisk、泰瑞达的看空交易和看空趋势。

Sandisk 在同一小时里被写成双超。TrendSpider：调整后每股收益 49.51 美元对 46.22 美元，销售 110.31 亿美元对 106.39 亿美元；宣布 8 比 1 拆股；盘后一度翻绿：[财报](https://x.com/TrendSpider/status/2115898712593441027)、[拆股](https://x.com/TrendSpider/status/2115901075396169802)、[翻绿](https://x.com/TrendSpider/status/2115901330401222862)。The Transcript 引 CFO：数据中心收入环比增 61% 到 48 亿美元。CEO 把 NAND 需求写成结构性上升，客户信号延伸到 2030 财年以后。同一条帖开头的盘后注记曾是跌 2%，和后来翻绿是两个时点：[48 亿](https://x.com/TheTranscript_/status/2115908340652105989)、[2030](https://x.com/TheTranscript_/status/2115908593593823526)。

软件和流量是被罚的另一组。TrendSpider：Reddit 每股收益 1.40 美元对 1.36 美元，销售 8.95 亿美元对 8.78 亿美元，随后盘后跌 20%。Pinterest 调整后每股收益 0.46 美元对 0.48 美元，销售不及，并下调四季销售指引。Twilio 双超并上调全年销售指引，盘后仍跌 12.92%。Roblox 双超。零对冲周五盘前把 Reddit 写成跌 20%，Roblox 跌 18%，Twilio 跌 18%，Pinterest 跌 8%：[Reddit](https://x.com/TrendSpider/status/2115901665085702636)、[Twilio](https://x.com/TrendSpider/status/2115902854162518355)、[盘前](https://x.com/zerohedge/status/2116139928174182778)。12.92% 和 18% 是两个时点。线外的 The Transcript 引 Reddit CEO：10 月搜索推荐平均每周少了 100 万以上；若这个下降速度持续，四季日活可能从目前 1.3 亿的基数掉一个低两位数百分比。Kobeissi 引同一场电话会：人工智能模式不再带来流量，以前会，现在不会。他们把这句话和前一天谷歌因同一问题抹掉 4800 亿美元放在一起：[日活](https://x.com/TheTranscript_/status/2115910883335614861)、[流量](https://x.com/KobeissiLetter/status/2116139805516210579)。

Andreas Steno 的问题是：可以惩罚超大规模云的资本开支，同时惩罚供应商在他看来讲不通。他另写，对冲基金深仓七巨头，是为了躲开人工智能；拿这个仓位去读一份本来扎实的季报，反应会被放大：[供应商](https://x.com/AndreasSteno/status/2115907667810287745)、[对冲基金](https://x.com/AndreasSteno/status/2116113823631573161)。《金融时报》的标题是，三季度支出再大幅上升之后，大型科技公司市值合计掉了近 9000 亿美元：[帖](https://x.com/FT/status/2116115427570987506)。微软发债仍在窗口里。CNBC：微软计划借 250 亿美元，用于人工智能建设：[帖](https://x.com/CNBC/status/2115967568695455893)。MarketWatch 的标题是最多 250 亿美元：[帖](https://x.com/MarketWatch/status/2115944824134127618)。两行都留着。

线外的 firstadopter 把内存涨价写到苹果和手机。美银把 2027 财年 iPhone 出货量预期下调 900 万部到 2.47 亿部，街边预期 2.60 亿部。内存对 iPhone 毛利率的毛影响大约 900 个基点，经过价格、结构和成本动作之后净影响大约 500 个基点，对公司整体毛利率大约 250 个基点。他另写全球智能手机芯片出货量三季度同比降 21%，高通受的伤害最大：[苹果](https://x.com/firstadopter/status/2116107298397356503)、[手机](https://x.com/firstadopter/status/2116090277077164413)。

### 3. 3.4% 的 GDP 和 0.5% 的 PCE 已经是周四的数字，周五 8:30 还没响

美国财政部的账号把三季度 GDP 写成再次超预期，增速 3.4%；家庭需求仍然强，设备投资是 2010 年以来最快的前三季度节奏：[帖](https://x.com/USTreasury/status/2115883180926414989)。First Squawk 转述特朗普的 Truth Social：经济以 3.4%“蓬勃增长”，设备投资增 21%：[帖](https://x.com/FirstSquawk/status/2115880805650313658)。El-Erian 引用《纽约时报》的图，把三季度增速写成一年里最高的 3.4%：[帖](https://x.com/elerianm/status/2115977595724660945)。这三处都是 3.4%。First Squawk 的收盘综述另写，9 月 PCE 通胀环比升 0.5%，是六个月里最大的单月升幅：[帖](https://x.com/FirstSquawk/status/2115909370433417266)。DeItaone 的达拉斯联储截尾均值 PCE 是另一条序列：9 月年化升 2.8%，8 月是升 2.0%：[帖](https://x.com/DeItaone/status/2115861373758669266)。0.5% 的环比和 2.8% 的年化截尾均值不要写成同一个通胀数字。

Charlie Bilello 的帖被接口标成回复，内容仍在他的状态页上：初请失业金落到 1969 年以来最低；1969 年美国人口 2.03 亿，现在 3.49 亿，按人口调整之后，初请从未低于现在：[帖](https://x.com/charliebilello/status/2115896355751108784)。帖文没有给初请的绝对人数。同一串里，Alphabet 三季度收入同比增 25% 到 1280 亿美元的纪录，经营利润增 30% 到 410 亿美元，净利润降 25% 到 260 亿美元，因为权益证券未实现亏损 80 亿美元；云收入增 103% 到 310 亿美元。自由现金流负 90 亿美元，资本开支同比增 114% 到 510 亿美元：[利润](https://x.com/charliebilello/status/2115842367924449731)、[现金流](https://x.com/charliebilello/status/2115843152326348870)。这是周四白天对周三财报的复盘，跌 12.6% 是周四的收盘。

利率的句子分成已经发生的和还没发生的。欧洲央行自己的帖：管委会决定维持利率不变，拉加德说致力于让通胀在中期稳定在 2%：[帖](https://x.com/ecb/status/2115849208494178428)。周五早上的委员讲话更紧。LiveSquawk 引 Panetta：价格前景在变差，通胀预计会有几个季度高于 2%；进一步加息可能是必要的；核心通胀的上升可能在明年初变得更明显：[帖](https://x.com/LiveSquawk/status/2116112162582089822)。First Squawk 引 Kocher：通胀风险已经上升；如果情况不很快改善，就有“采取行动的需要”；过早行动和干等都不能保证物价稳定：[风险](https://x.com/FirstSquawk/status/2116124044852691245)、[行动](https://x.com/FirstSquawk/status/2116124576589766853)。FinancialJuice 引 Makhlouf：按住利率并不表示欧洲央行已经结束；当前通胀局面让人不舒服：[帖](https://x.com/financialjuice/status/2116133066368315733)。

日本央行按住 1.25%。CNBC：日本央行说通胀“大体上符合”2% 的目标，这是 2013 年采用该目标以来第一次这样评估；利率仍在 1995 年以来的高位：[帖](https://x.com/CNBC/status/2116009860462522795)。First Squawk：决定以 8 比 1 通过。El-Erian 把日本央行、欧洲央行和美联储写成这一周都按住了：[帖](https://x.com/elerianm/status/2116043305557586352)。

美债收益率在周四收盘后是往下的。First Squawk：10 年期收益率降 8.5 个基点，延伸到七周低点；两年期延伸到 4.5648%，也是七周低点：[10 年](https://x.com/FirstSquawk/status/2115971438503141781)、[两年](https://x.com/FirstSquawk/status/2115971402759315474)。The Stalwart 写两年期当天降 10 个基点到 4.6%：[帖](https://x.com/TheStalwart/status/2115901144451219833)。4.5648% 和 4.6% 是两个时点。Gary 周五 10:40 UTC 的 10 年期是 4.93%。7 年期拍卖在窗口内：高收益率 4.894%，和发行前的预发行收益率打平，前一次是 5.085%，投标倍数 2.46，发行 440 亿美元：[帖](https://x.com/financialjuice/status/2115852105911259515)。Freddie Mac 的 30 年期固定按揭利率降到 7.24%，上周 7.32%，两周前 7.40%：[帖](https://x.com/DeItaone/status/2115836416961691996)。

线外的 Robin Brooks 把 12 月加息写成远非确定。9 月加息是对 8 月长端收益率急升的反应；欧元区债务的发酵正在把美国收益率往下压，所以没有加息的需要。他把“沃什是鹰还是鸽”写成问错了问题：沃什和贝森特一样，首要是把长端收益率按住，所以杰克逊霍尔偏鹰，这一周偏鸽：[12 月](https://x.com/robin_j_brooks/status/2116067839065125375)、[鹰鸽](https://x.com/robin_j_brooks/status/2116066108629229842)。Lyn Alden 的一句是，更高的利率并不能在所有成因下修好通胀：[帖](https://x.com/LynAldenContact/status/2115935054392418569)。线外的 Lisa Abramowicz 转述德意志银行的 George Saravelos：过去两周出现过科技股和美元同时急跌；美元在人工智能驱动的市场修正里，不能再被当成当然的避险：[帖](https://x.com/lisaabramowicz1/status/2116103451235020957)。

Liz Ann Sonders 的亚特兰大联储 GDPNow 是四季度的即时预测，不是三季度的 3.4%：初值升 3.2%：[帖](https://x.com/LizAnnSonders/status/2115877957914722329)。她周五 12:11 UTC 写 9 月个人储蓄率降到 3.8%，是 2022 年以来第一次落到 3 字头：[帖](https://x.com/LizAnnSonders/status/2116141159797940684)。AAII 的看多比例升到 37.8%，前值 36.9%，略高于 37.5% 的历史平均；同一条帖里另一个“看多比例”降到 41.4%，前值 45.8%。两个比例都留在原帖里：[帖](https://x.com/LizAnnSonders/status/2115877759767453890)。她另写 10 年期收益率和标普的滚动相关性继续冲高：[帖](https://x.com/LizAnnSonders/status/2116134161958256945)。Bob Elliott 的标题是名义 GDP 增速已经过了高点，下半年市场一直押注的名义增长热潮，被最新的增长数据和人工智能公司的财报打上问号：[帖](https://x.com/BobEUnlimited/status/2116126720507957724)。

欧洲早上的 GDP 是另一组。欧元区三季度环比升 0.4%，预期 0.2%，前值 0.6%；同比升 1.3%，预期 1.1%：[LiveSquawk](https://x.com/LiveSquawk/status/2116108338555695125)。德国环比升 0.2%，预期 0.1%。法国环比降 0.1%，预期升 0.1%；法国 10 月 CPI 同比升 3.4%，预期 3.3%。这些是欧洲的初步数，不是美国的 3.4%。

### 4. 油的结算价在跌，周五的口号在涨；黑客和霍尔木兹是两条线

周四的结算先写。FinancialJuice：NYMEX WTI 12 月原油期货结算 102.00 美元，跌 0.78 美元，跌 0.76%：[帖](https://x.com/financialjuice/status/2115874170328244447)。First Squawk：布伦特原油期货结算跌 0.38% 到 114.88 美元，跌 0.44 美元：[帖](https://x.com/FirstSquawk/status/2115879143279845644)。23:21 UTC 的综述用了同一个 114.88 美元和大约 102 美元，理由写成美伊外交接触缓和了进一步军事升级的担心；德黑兰对外交表示开放，但 11 月 3 日中期选举之后美国和以色列会不会动武仍不确定：[帖](https://x.com/FirstSquawk/status/2115947035769896992)。

周五的口号是往上的。01:40 UTC，First Squawk：布伦特和 WTI 因美伊地缘风险各涨 2 美元：[帖](https://x.com/FirstSquawk/status/2115982261099381031)。Gary 10:40 UTC 的布伦特是涨 1.6% 到 117 美元。114.88、涨 2 美元之后的价格、117，不要写成一个油价。路透调查的 2026 年平均布伦特是 92.88 美元，9 月的调查是 89.05 美元。那是年度平均预测，不是现货：[帖](https://x.com/LiveSquawk/status/2116102695639498836)。

战和谈的帖还是两套。First Squawk：特朗普说不知道该和谁谈，很多伊朗领导人已经不在了，伊朗必须做交易；福克斯称特朗普周四听取了伊朗军事选项的简报：[交易](https://x.com/FirstSquawk/status/2116133821980827747)、[简报](https://x.com/FirstSquawk/status/2116134084313497822)。伊朗国家媒体称，伊朗海军在霍尔木兹海峡东部摧毁了一艘美国无人艇，没有美方确认：[帖](https://x.com/FirstSquawk/status/2116134413281161298)。FinancialJuice：伊斯兰革命卫队海军称，两艘关闭导航系统的油轮在霍尔木兹以南被拦下：[帖](https://x.com/financialjuice/status/2116118224802869555)。CNBC 的标题是伊朗称四艘油轮在霍尔木兹触雷，中期选举后的打击担心在上升：[帖](https://x.com/CNBC/status/2116057942742962442)。线外的 Javier Blas 转述参议员 Chris Murphy：有人已经听过战争计划的简报，他不能披露细节，但可以说计划是疯狂的。他另写美国通过交换，从战略石油储备放出 4060 万桶原油的合同。他的必读链接是《华尔街日报》写乔治·华盛顿号上的战斗机在夜间起飞、拦截伊朗巡航导弹：[计划](https://x.com/JavierBlas/status/2115887134725079394)、[储备](https://x.com/JavierBlas/status/2115927707062075833)、[航母](https://x.com/JavierBlas/status/2116093172304708018)。Brooks 的文章标题里有 117 美元。正文写的是现货 Dated Brent 昨天重新收到近月期货，这是 9 月 10 日东西管道遇袭以来第一次；市场担心热战重启，这件事一旦过去，价格会掉下来：[帖](https://x.com/robin_j_brooks/status/2116064295645549053)。

黄金和白银在这些帖里是跌的。First Squawk 06:49 UTC：现货金回到 3983.79 美元，跌近 1%：[帖](https://x.com/FirstSquawk/status/2116059975151956060)。Keith 周五早上写黄金再跌 1% 到周期新低，离历史高点的跌幅 26.5%；白银再跌 3%，离周期高点的跌幅 57%。他维持做空白银，并维持做空金矿股。油在他那里周五早上再涨 2.2%，他把它当成多头，用来不听政客谈通胀：[黄金](https://x.com/KeithMcCullough/status/2116117174234595775)、[白银](https://x.com/KeithMcCullough/status/2116117868635148662)、[油](https://x.com/KeithMcCullough/status/2116115736808820768)。Barchart 写白银跌到 200 日均线下方，偏离是新冠以来最大：[帖](https://x.com/Barchart/status/2115871964653089040)。彭博写金价在 4000 美元附近企稳，并走向第二个月下跌，因为能源推动的通胀提高了年内加息的可能性：[帖](https://x.com/business/status/2115985823279550488)。3983.79、跌 1%、4000 附近，是三张快照。

币安的数字按时间留着。Kobeissi 先写 Tether 冻结了 9.71 亿美元与疑似黑客有关的 USDT，五个链上流出 28 亿美元；随后写钱包流出 57 亿美元；CZ 先说损失可能超过 10 亿美元、公司会覆盖，后来的公司口径是影响大约 63 亿美元，大约 30 亿美元已经在链上冻结，还剩 33 亿美元：[28 亿](https://x.com/KobeissiLetter/status/2115915162259460108)、[57 亿](https://x.com/KobeissiLetter/status/2115926246916038921)、[63 亿](https://x.com/KobeissiLetter/status/2116001196226003032)。TrendSpider 曾写最多 58 亿美元。63 亿美元是后来的公司口径。CNBC 写比特币跌破 7.8 万美元：[帖](https://x.com/CNBC/status/2115967016414699866)。Kobeissi 写比特币跌破 7.7 万美元、以太坊跌破 2200 美元。Gary 写比特币跌 1.5% 到 7.56 万美元。Keith 把比特币的趋势信号切回看空，目标价砍到 7.5 万美元：[帖](https://x.com/KeithMcCullough/status/2116120022623912120)。7.8 万、7.7 万、7.56 万、7.5 万的目标，是四个句子。

周五早上已经出来的公司数字是另一组。雪佛龙调整后每股收益 5.28 美元。First Squawk 的预期是 4.93 美元，收入及其他 678.0 亿美元对 625.5 亿美元：[帖](https://x.com/FirstSquawk/status/2116112978257006899)。TrendSpider 的销售预期是 616.23 亿美元，调整后每股收益预期是 4.88 美元：[帖](https://x.com/TrendSpider/status/2116135167102488835)。埃克森调整后每股收益 4.23 美元。First Squawk 的预期是 4.13 美元，收入 1131.6 亿美元对 1053.6 亿美元，季度股息从 1.03 美元提到 1.07 美元：[帖](https://x.com/FirstSquawk/status/2116116911100735781)。TrendSpider 的每股收益预期是 4.08 美元，销售预期是 1030.9 亿美元。艾伯维调整后每股收益 3.82 美元对 3.74 美元，净收入 174.0 亿美元对 173.4 亿美元，全年调整后每股收益看到 13.95 到 13.99 美元，之前是 13.76 到 13.96 美元：[帖](https://x.com/FirstSquawk/status/2116135157384310926)。FinancialJuice 的艾伯维预期是每股 3.74 美元、收入 173.4 亿美元。TrendSpider 写成 3.75 美元和 173.1 亿美元。通用动力收入 145.7 亿美元对 137.1 亿美元，每股收益 4.49 美元对 4.13 美元：[帖](https://x.com/FirstSquawk/status/2116123287369781269)。Javier Blas 写雪佛龙和埃克森的主题是炼油利润率极高；雪佛龙用多出来的现金继续减债，没有加大回购；埃克森引导投资者预期明年的回购和 2026 年差不多：[雪佛龙](https://x.com/JavierBlas/status/2116138431478976552)、[埃克森](https://x.com/JavierBlas/status/2116140412754932224)。BP 在他那里是 18 年来最高利润，一个季度减债近 100 亿美元：[帖](https://x.com/JavierBlas/status/2116073351034937399)。

## 要盯住的五件事

1. **周五开盘时，7718.38 和 26177.91 还在不在。** 盘后先是纳斯达克期货跌 1.4%、标普期货跌 0.6%，后是纳斯达克 100 期货跌 1.7%，再后是跌 2% 和标普跌近 1%，Gary 写成标普跌 1.0%、纳斯达克 100 跌 2.2%。线外的 RedDog 写标普期货跌 75 点，7612 是位置；QQQ 已经在上周低点，701 一带重要，200 日均线在 684 附近。零对冲的七巨头是一起跌。
2. **英特尔的跌 25% 或 27% 有没有变成收盘。** 财报前的期权定价大约上下 9.3%。盘后的帖从跌 17% 写到跌 21%，周五凌晨写到跌 27%，并写成有望成为 1974 年以来最大单日跌幅。SOXX 盘后跌 4%。Keith 写英特尔占 SOXX 大约 8.3%。四季销售指引在不同帖里是 155 亿美元一个点，或者 150 亿到 160 亿美元一个区间。
3. **亚马逊的跌 7.3% 和 AWS 增 39% 不要写成同一个故事。** 收入和每股收益不及，经营利润和 AWS 超。2027 和 2028 年增速超过 40% 是 CEO 的句子。资本开支 773 亿美元对 588 亿美元。2026 年资本开支，Gary 的帖开头写成 2.2 亿美元，同一条后面写成 2200 亿美元；The Transcript 的引文是约 2200 亿美元。微软借债是 250 亿美元，MarketWatch 写成最多 250 亿美元。
4. **114.88 美元和 117 美元不要写成同一个油价。** WTI 周四结算 102.00 美元。布伦特结算 114.88 美元。周五曾各涨 2 美元，Gary 写 117 美元。和谈帖、军事选项简报、以及没有美方确认的无人艇帖同时在。Brooks 认为热战一旦过去，价格会掉。Keith 维持黄金和白银看空。
5. **8:30 的就业成本指数还没有结果帖。** 三季度 GDP 的 3.4% 和 9 月 PCE 环比 0.5% 是周四已经进入综述的数字。达拉斯联储截尾均值是年化 2.8%。Brooks 把 12 月加息写成远非确定，Panetta 把进一步加息写成可能必要。两年期在 First Squawk 那里是 4.5648%，10 年期在 Gary 那里是 4.93%。芝加哥 PMI 在 9:45。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 周四收盘 | 道指、标普、纳斯达克 | 道指收 52330.24，跌 0.28%。标普收 7718.38，跌 0.33%。纳斯达克收 26177.91，跌 1.40%。综述另写纳斯达克 100 跌 1.4%，400 多只标普成分上涨 | [收盘](https://x.com/FirstSquawk/status/2115897119752249506)、[宽度](https://x.com/FirstSquawk/status/2115909358873903319) |
| 周五盘前 | 标普期货、纳斯达克期货、七巨头 | 盘后纳斯达克期货跌 1.4%，标普期货跌 0.6%。随后纳斯达克 100 期货跌 1.7%，再写到跌 2%。Gary：标普跌 1.0%，纳斯达克 100 跌 2.2%，10 年期 4.93%。零对冲：七巨头全跌，亚马逊跌 7.3% | [1.4%](https://x.com/FirstSquawk/status/2115930325486543142)、[Gary](https://x.com/garyblack00/status/2116118139582697581)、[七巨头](https://x.com/zerohedge/status/2116139928174182778) |
| 周四收盘被罚 | GOOGL | 收盘跌 12.6%，市值抹掉 4800 亿美元。综述写成大跌 12%。自由现金流负 90 亿美元。云增 103% | [12.6%](https://x.com/Investingcom/status/2115896860783345762)、[现金流](https://x.com/charliebilello/status/2115843152326348870) |
| 双不及、云超预期 | AMZN | 每股收益 1.89 美元。收入 2019 亿美元。经营利润 281 亿美元，超预期。AWS 增 39.3% 到 460 亿美元。盘后跌幅帖从 6% 到 10%，盘前 7.3%。2027–2028 年增速超过 40% 是 CEO 的句子 | [Gary](https://x.com/garyblack00/status/2115910608818425934)、[分部](https://x.com/TheTranscript_/status/2115901875073737189)、[7.3%](https://x.com/zerohedge/status/2116139928174182778) |
| 指引被罚 | INTC | 季度调整后每股收益 0.52 美元，超预期。四季销售指引在 155 亿美元或 150–160 亿美元，预期大约 170 亿美元。盘后从跌 17% 写到跌 21%，周五凌晨写到跌 27%。期权在财报前定价大约上下 9.3% | [指引](https://x.com/TrendSpider/status/2115898166574723532)、[27%](https://x.com/KobeissiLetter/status/2116103832702693474) |
| 双超后翻绿 | SNDK | 调整后每股收益 49.51 美元对 46.22 美元。数据中心收入环比增 61% 到 48 亿美元。8 比 1 拆股。盘后一度翻绿。Keith 维持看空 | [财报](https://x.com/TrendSpider/status/2115898712593441027)、[48 亿](https://x.com/TheTranscript_/status/2115908340652105989) |
| 超预期后仍被卖 | RDDT、TWLO、RBLX、PINS | Reddit 季度超预期，盘后跌 20%，搜索推荐每周少 100 万以上。Twilio 双超，盘后跌 12.92% 或盘前跌 18%。Roblox 双超，盘前跌 18% | [Reddit](https://x.com/TrendSpider/status/2115901665085702636)、[日活](https://x.com/TheTranscript_/status/2115910883335614861) |
| 周五早上已有数字 | CVX、XOM、ABBV、GD | 雪佛龙调整后每股收益 5.28 美元。埃克森 4.23 美元，股息提到 1.07 美元。艾伯维上调全年利润。通用动力每股收益 4.49 美元对 4.13 美元。炼油利润率是 Javier Blas 的主题 | [雪佛龙](https://x.com/FirstSquawk/status/2116112978257006899)、[埃克森](https://x.com/FirstSquawk/status/2116116911100735781) |
| 发债仍在 | MSFT | CNBC 写计划借 250 亿美元。MarketWatch 写最多 250 亿美元。Azure 下一季指引 49%–50% 在 The Transcript 的引文里 | [250 亿](https://x.com/CNBC/status/2115967568695455893)、[Azure](https://x.com/TheTranscript_/status/2116127291281719364) |
| 内存外溢 | AAPL、QCOM | firstadopter：美银把 2027 财年 iPhone 下调 900 万部到 2.47 亿部。手机芯片出货量同比降 21%，高通受伤害最大 | [苹果](https://x.com/firstadopter/status/2116107298397356503) |
| 位置 | QQQ、SPX 期货 | RedDog：QQQ 在上周低点，701 重要，200 日在 684 附近。标普期货跌 75 点，7612。Barchart：QQQ 回到 100 日均线下方 | [QQQ](https://x.com/RedDogT3/status/2116097034222522865)、[7612](https://x.com/RedDogT3/status/2116137281262059553) |
| 亚洲和行业空头 | EWY、DRAM、SOXX、XLV、XLP | Keith：韩国隔夜再跌 3.5%，6 月以来跌 37.1%，继续做空 EWY 和 DRAM。日经隔夜跌 2.1%。中国再跌 1.4%，离周期高点跌 15.1%。医疗 ETF 创历史新高。必需消费是过去两天重新加的多头 | [韩国](https://x.com/KeithMcCullough/status/2116110621410574667)、[医疗](https://x.com/KeithMcCullough/status/2115881852787638392) |
| 油、金、银 | WTI、布伦特、黄金、白银 | WTI 结算 102.00 美元。布伦特结算 114.88 美元，周五口号到 117 美元。现货金 3983.79 美元。Keith 写黄金离高点跌 26.5%，白银离周期高点跌 57% | [WTI](https://x.com/financialjuice/status/2115874170328244447)、[布伦特](https://x.com/FirstSquawk/status/2115879143279845644)、[117](https://x.com/garyblack00/status/2116118139582697581) |

## 后续走势：三套可以证伪的剧本

帖文没有给周五的收盘点位。周四写下来的现货收盘是标普 7718.38、纳斯达克 26177.91、道指 52330.24。下面三套的顺序，以开盘前纳斯达克期货仍跌大约 2%、英特尔仍在跌 25% 上下、8:30 的就业成本指数还没落地为前提。

**轮动把指数接住，英特尔和亚马逊留在单个公司的事件里。** 触发器是标普守住 7718 一带，或者守住 RedDog 写的 7612，纳斯达克期货从跌 2.2% 收到跌 1% 以内，医疗和必需消费继续是上涨的一组，雪佛龙和埃克森的炼油利润被当成油价受益而不是周期高点。这条路径上，市场交易的是 400 多只标普成分上涨、AWS 增 39%、Sandisk 数据中心环比增 61%。Bespoke 的“平均一只股票公布当日是涨的”站在这一侧。若开盘后七巨头维持零对冲那张全跌的表，并且 SOXX 的盘后跌 4% 扩散到已经双超的 Sandisk 以外，这条路径失败。

**资本开支和供应商一起被罚，7612 先被打穿。** 触发器已经写在盘后和盘前：Alphabet 收盘跌 12.6% 且自由现金流为负，亚马逊资本开支 773 亿美元高于预期，微软开始一笔 250 亿美元的债，Reddit 和 Twilio 在成绩单之后下跌，英特尔的个人电脑指引下修。Keith 维持半导体、韩国和一只内存篮子的空头，并把高收益利差再走阔 11 个基点写成事实。Kobeissi 的高点回撤名单里，七巨头有四只已经在熊市区间。这条路径失败的条件，是就业成本指数没有强化 0.5% 的 PCE，英特尔的跌幅收到 9.3% 的期权定价以内，并且标普期货从跌 75 点回到 7718 之上。

**117 美元的油价口号留在结算价之上，12 月加息被重新定价。** 触发器是布伦特从 114.88 美元的结算留在 Gary 的 117 美元，同时 Panetta 那句“进一步加息可能必要”压过 Brooks 的“12 月远非确定”。霍尔木兹的油轮和无人艇帖是这条路径的地缘句子，无人艇目前没有美方确认。它失败的条件，是油价回到 114.88 美元以下，两年期留在 4.56% 一带，而且欧洲央行委员的周五讲话没有被交易成加息。黄金在这条路径上不会自动上涨：Keith 在金价仍被写成跌 1% 时维持看空，白银他维持做空。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照美东 9:30 的开盘。它不决定仓位大小。

**开盘前只核对五样东西。** 期货还在不在 04:01 UTC 的纳斯达克 100 跌 2%、标普跌近 1%，还是 Gary 的标普跌 1.0%、纳斯达克 100 跌 2.2%，还是 RedDog 的标普期货跌 75 点、7612；英特尔的盘前跌 25% 或 27% 是维持，还是收到财报前 9.3% 的期权定价以内；布伦特是停在 117 美元，还是回到 114.88 美元的结算；10 年期还在不在 4.93%，两年期还在不在 4.5648%；雪佛龙和礼来这一侧是跟着利润走，还是跟着“超预期仍被卖”走。五样里油价留在结算价以上、英特尔的跌幅守住 25%、已经超预期的软件继续被卖，这些帖给出的默认顺序是融资敏感的人工智能信用和已经在跌的半导体，低于炼油、医疗和 Keith 放在多头上的必需消费。油价回到 114.88 美元、英特尔的缺口收到 9.3% 以内、标普守住 7718，默认顺序掉过头来：云和 Sandisk 的数据中心高于去追从高点已经跌了 20% 以上的那张名单。

**已经公开的方向，按账号而不是按共识。**

- Gary Black：盘前标普跌 1.0%，纳斯达克 100 跌 2.2%。英特尔跌 25%，个人电脑展望疲弱到 2027 年中。亚马逊收入不及、AWS 超、资本开支高于预期。英伟达跌 2.9%，博通跌 4.0%，美光跌 5.2%，戴尔跌 10%。布伦特 117 美元，10 年期 4.93%，比特币 7.56 万美元。标普 2026 年每股收益预测仍是 369 美元，同比增 33%。他维持对特斯拉谨慎。
- Keith McCullough，线外：从科技出来，进必需消费，医疗继续多头。做空韩国、DRAM、金矿股、白银。英特尔、Sandisk、泰瑞达维持看空。礼来和奥驰亚维持看多。高收益利差再走阔 11 个基点。比特币目标价砍到 7.5 万美元。油是多头。黄金看成从高点跌了 26.5% 的下跌趋势。
- Robin Brooks，线外：12 月加息远非确定。沃什这一周偏鸽，是为了按住长端。布伦特的文章标题有 117 美元，正文写热战一旦过去价格会掉。现货和近月的缺口昨天回到遇袭前。
- Nick Timiraos，线外：窗口里只有一条，问的是经济强、通胀没有回到 2%、金融条件不紧的时候，为什么美联储按住。没有新的概率。
- Peter Schiff、Bianco、Cathie Wood、Gundlach、Guy Adami、MacroAlf、Tavi Costa：窗口内没有可引用的新指数或个股方向。
- El-Erian：三季度 GDP 3.4%，一年里最高。日本央行、欧洲央行、美联储这一周都按住。
- Liz Ann Sonders：GDPNow 的四季度即时预测是升 3.2%，这不是三季度公布值。储蓄率 3.8%。10 年期和标普的相关性继续冲高。AAII 看多 37.8%。
- Kobeissi：隐蔽熊市，超过 60% 的标普成分较高点跌了 20% 以上，七巨头里四只在熊市区间，合计抹掉 4 万亿美元。英特尔盘前延伸到跌 27%。币安影响大约 63 亿美元。Reddit 的人工智能模式不再带来流量。他们没有给周五的标普目标。
- Jim Cramer：对英特尔失望。亚马逊和星巴克在他那里是很好的季报。科技里的钱在挪到包装消费品、医疗和银行。他认为选举不会关掉数据中心建设。
- Bespoke，线外：QQQ 盘后跌超 1%，SOXX 盘后跌 4%。亚马逊是 2022 年 4 月以来第一次双不及。已公布股票的平均反应是涨，科技平均跌 1.2%。卡特彼勒上半年涨 86%，下半年跌 39%，年内仍涨 13%。8:30 是就业成本指数，9:45 是芝加哥 PMI。
- SpotGamma，线外：Alphabet 跌了 12% 之后隐含波动率被打下来，买反弹可以看期权而不是股票。英特尔财报前定价大约上下 9.3%。没有新的指数目标价。
- The Transcript，线外：AWS 增 39.3%，2026 年现金资本开支约 2200 亿美元，2027 和 2028 年增速可以超过 40%。英特尔下一年自由现金流预计不会转正。Reddit 搜索推荐每周少 100 万以上。
- Lisa Abramowicz，线外：转述德意志银行，科技股和美元可以同时跌，美元的避险属性不能再当成当然。
- firstadopter，线外：看苹果要看内存对毛利率的 250 个基点。高通在手机芯片下滑里受伤最大。
- Andy Constan：盘后卖掉了短端利率期货的多头。亚马逊的发行方式还是一个问题，不是一个已经宣布的方案。债券是他当晚的偏好。
- Javier Blas，线外：炼油利润率极高。雪佛龙减债，埃克森的回购引导和 2026 年差不多。战争计划的帖是参议员的原话，他没有给新的油价目标。
- Mark Minervini：收盘前的条件是，周四如果收得不好，空头可能加到超配。窗口内没有确认已经加仓的后续帖。多头只写了梯瓦和 IBB。
- Andreas Steno：不要同时惩罚云和供应商。对冲基金的七巨头仓位会放大财报反应。
- Luke Gromen：窗口内没有新的点位。一条是宏观访谈预告。
- Eric Balchunas：币安事件之后，他把比特币 ETF 写成托管和费用上的替代，没有指数点位。
- Bill Ackman：窗口内没有新的指数方向。帖是墨西哥城的访谈和一桩学术争议。
- Raoul Pal：新书预告。他转发的对谈把人工智能热潮写成还没破裂、交易正在变化。
- Michael Burry：一条 Build-A-Bear 的报告链接，没有指数方向。
- Ray Dalio、Taleb、Chamath、Damodaran、Cathie Wood：没有可引用的新指数或个股方向。Taleb 的一条不是市场判断。ARK 官方账号窗口内的一条没有正文。

**财报的顺序。** 先看已经写进价格的文件：Alphabet 的负自由现金流和跌 12.6% 的收盘，亚马逊的双不及和 2200 亿美元资本开支，英特尔的四季指引，微软的 250 亿美元债。再看周五早上已经出来的雪佛龙、埃克森、艾伯维、通用动力。然后才是 Bespoke 点名的 8:30 就业成本指数和 9:45 芝加哥 PMI。抓取结束时这两项还没有公布值。

**明确留在观察、不放进计划的东西。** 周五现货还没开盘，不用期货倒推收盘。就业成本指数还没有结果帖。三季度 GDP 的 3.4% 和 9 月 PCE 的 0.5% 是周四的综述，不是周五 8:30 的新数。德意志银行的时间线没有读到。彭博主号、markets、BBC Business、CNN Business、纽约时报商业、TradingView 的时间线对不上这个窗口。Gundlach、Damodaran、Cathie Wood、Chamath、Krugman、Nouriel、Hindenburg、Icahn、Peter Schiff、Bianco 这次没有可引用的新判断。Kobeissi 的高点回撤百分比不要和周四的涨跌幅相加。币安的 28 亿、57 亿、58 亿和 63 亿按发帖顺序留着，公司后来的口径是 63 亿。

## 帖文索引

周四收盘与周五盘前：[纳斯达克 26177.91、标普 7718.38、道指 52330.24](https://x.com/FirstSquawk/status/2115897119752249506)、[宽度和纳斯达克 100](https://x.com/FirstSquawk/status/2115909358873903319)、[期货跌 1.4%](https://x.com/FirstSquawk/status/2115930325486543142)、[跌 2%](https://x.com/FirstSquawk/status/2116017609921704151)、[Gary 的盘前](https://x.com/garyblack00/status/2116118139582697581)、[七巨头](https://x.com/zerohedge/status/2116139928174182778)。

增长、通胀与利率：[GDP 3.4%](https://x.com/USTreasury/status/2115883180926414989)、[PCE 0.5%](https://x.com/FirstSquawk/status/2115909370433417266)、[截尾均值](https://x.com/DeItaone/status/2115861373758669266)、[欧洲央行按住](https://x.com/ecb/status/2115849208494178428)、[Panetta](https://x.com/LiveSquawk/status/2116112162582089822)、[12 月](https://x.com/robin_j_brooks/status/2116067839065125375)、[两年期 4.5648%](https://x.com/FirstSquawk/status/2115971402759315474)。

财报：[Alphabet 收盘](https://x.com/Investingcom/status/2115896860783345762)、[亚马逊](https://x.com/garyblack00/status/2115910608818425934)、[AWS 分部](https://x.com/TheTranscript_/status/2115901875073737189)、[英特尔](https://x.com/TrendSpider/status/2115898166574723532)、[跌 27%](https://x.com/KobeissiLetter/status/2116103832702693474)、[Sandisk](https://x.com/TrendSpider/status/2115898712593441027)、[微软发债](https://x.com/CNBC/status/2115967568695455893)。

油、黄金与日历：[WTI 结算](https://x.com/financialjuice/status/2115874170328244447)、[布伦特结算](https://x.com/FirstSquawk/status/2115879143279845644)、[涨 2 美元](https://x.com/FirstSquawk/status/2115982261099381031)、[117](https://x.com/garyblack00/status/2116118139582697581)、[军事选项](https://x.com/FirstSquawk/status/2116134084313497822)、[现货金](https://x.com/FirstSquawk/status/2116059975151956060)、[就业成本指数日历](https://x.com/bespokeinvest/status/2116120553371451872)、[币安 63 亿](https://x.com/KobeissiLetter/status/2116001196226003032)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-10-30 抓取时的公开读数。原创条数是北京时间当天窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 79 条、First Squawk 343 条、FinancialJuice 290 条、彭博商业账号 249 条是读穿窗口后的计数。德意志银行的 0 是读取失败。彭博主号、markets、BBC Business、CNN Business、纽约时报商业、TradingView 的 0 来自对不上这个窗口的时间线。Charlie Bilello 的 4 条市场帖被接口标成回复，所以表里是 0。Earnings Whispers 的周五日历帖被接口标成回复，表里的 5 是其余原创。


| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,439,426 | 79 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,323,704 | 105 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,277,500 | 87 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,322,926 | 39 |
| 5 | [@business](https://x.com/business) | 10,487,828 | 249 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,563,451 | 0 |
| 7 | [@FT](https://x.com/FT) | 7,106,134 | 51 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,256,819 | 73 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,400,474 | 13 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,646,626 | 39 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,578,186 | 0 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,424,303 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,359,037 | 35 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,431,350 | 43 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,421,869 | 41 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,038,601 | 3 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 2,997,418 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,707,103 | 24 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,558,654 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,511,569 | 9 |
| 21 | [@chamath](https://x.com/chamath) | 2,478,986 | 2 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,436,937 | 4 |
| 23 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,567 | 18 |
| 24 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,158,075 | 0 |
| 25 | [@michaeljburry](https://x.com/michaeljburry) | 2,131,004 | 1 |
| 26 | [@YahooFinance](https://x.com/YahooFinance) | 2,075,335 | 23 |
| 27 | [@markets](https://x.com/markets) | 2,046,741 | 0 |
| 28 | [@DeItaone](https://x.com/DeItaone) | 1,968,161 | 43 |
| 29 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,772,371 | 0 |
| 30 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,417 | 37 |
| 31 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,717,523 | 5 |
| 32 | [@NYSE](https://x.com/NYSE) | 1,700,260 | 6 |
| 33 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,693,176 | 0 |
| 34 | [@theinformation](https://x.com/theinformation) | 1,610,333 | 11 |
| 35 | [@federalreserve](https://x.com/federalreserve) | 1,601,141 | 3 |
| 36 | [@Investingcom](https://x.com/Investingcom) | 1,533,633 | 48 |
| 37 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,508,301 | 1 |
| 38 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,469,935 | 14 |
| 39 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,789 | 2 |
| 40 | [@Bloomberg](https://x.com/Bloomberg) | 1,352,561 | 0 |
| 41 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,351,540 | 2 |
| 42 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,246,900 | 1 |
| 43 | [@TheStreet](https://x.com/TheStreet) | 1,226,813 | 64 |
| 44 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,193,615 | 4 |
| 45 | [@Stocktwits](https://x.com/Stocktwits) | 1,192,993 | 3 |
| 46 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,185,601 | 6 |
| 47 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,185,383 | 0 |
| 48 | [@USTreasury](https://x.com/USTreasury) | 1,165,268 | 1 |
| 49 | [@nntaleb](https://x.com/nntaleb) | 1,164,796 | 1 |
| 50 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,160,500 | 32 |
| 51 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,156,678 | 2 |
| 52 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,152,688 | 11 |
| 53 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,141,777 | 3 |
| 54 | [@elerianm](https://x.com/elerianm) | 1,116,711 | 2 |
| 55 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,110,510 | 24 |
| 56 | [@Scaramucci](https://x.com/Scaramucci) | 1,096,191 | 5 |
| 57 | [@BlackRock](https://x.com/BlackRock) | 1,081,422 | 3 |
| 58 | [@Downtown](https://x.com/Downtown) | 1,043,588 | 0 |
| 59 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,344 | 16 |
| 60 | [@financialjuice](https://x.com/financialjuice) | 954,546 | 290 |
| 61 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,512 | 1 |
| 62 | [@Teslarati](https://x.com/Teslarati) | 935,110 | 12 |
| 63 | [@tradingview](https://x.com/tradingview) | 906,677 | 0 |
| 64 | [@BloombergTV](https://x.com/BloombergTV) | 893,775 | 11 |
| 65 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 890,005 | 0 |
| 66 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,732 | 10 |
| 67 | [@charliebilello](https://x.com/charliebilello) | 873,610 | 0 |
| 68 | [@axios](https://x.com/axios) | 861,740 | 32 |
| 69 | [@jpmorgan](https://x.com/jpmorgan) | 859,862 | 1 |
| 70 | [@Citi](https://x.com/Citi) | 853,381 | 1 |
| 71 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 851,986 | 13 |
| 72 | [@HindenburgRes](https://x.com/HindenburgRes) | 848,419 | 0 |
| 73 | [@themotleyfool](https://x.com/themotleyfool) | 840,845 | 1 |
| 74 | [@ecb](https://x.com/ecb) | 830,057 | 5 |
| 75 | [@ARKInvest](https://x.com/ARKInvest) | 822,511 | 1 |
| 76 | [@bgurley](https://x.com/bgurley) | 812,040 | 0 |
| 77 | [@SECGov](https://x.com/SECGov) | 810,445 | 0 |
| 78 | [@biancoresearch](https://x.com/biancoresearch) | 790,443 | 0 |
| 79 | [@leadlagreport](https://x.com/leadlagreport) | 770,147 | 13 |
| 80 | [@markminervini](https://x.com/markminervini) | 767,369 | 1 |
| 81 | [@MorganStanley](https://x.com/MorganStanley) | 758,064 | 2 |
| 82 | [@CNBCnow](https://x.com/CNBCnow) | 752,136 | 0 |
| 83 | [@morganhousel](https://x.com/morganhousel) | 729,445 | 0 |
| 84 | [@TrendSpider](https://x.com/TrendSpider) | 718,812 | 33 |
| 85 | [@CMEGroup](https://x.com/CMEGroup) | 712,093 | 2 |
| 86 | [@Nouriel](https://x.com/Nouriel) | 704,439 | 0 |
| 87 | [@DanielNewman](https://x.com/DanielNewman) | 695,608 | 0 |
| 88 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 673,817 | 5 |
| 89 | [@fundstrat](https://x.com/fundstrat) | 673,323 | 1 |
| 90 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,046 | 0 |
| 91 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,792 | 0 |
| 92 | [@LukeGromen](https://x.com/LukeGromen) | 637,583 | 3 |
| 93 | [@EricBalchunas](https://x.com/EricBalchunas) | 628,016 | 5 |
| 94 | [@garyblack00](https://x.com/garyblack00) | 584,540 | 2 |
| 95 | [@Cboe](https://x.com/Cboe) | 578,821 | 0 |
| 96 | [@Barchart](https://x.com/Barchart) | 578,255 | 10 |
| 97 | [@dampedspring](https://x.com/dampedspring) | 576,914 | 13 |
| 98 | [@FirstSquawk](https://x.com/FirstSquawk) | 575,002 | 343 |
| 99 | [@TruthGundlach](https://x.com/TruthGundlach) | 573,196 | 0 |
| 100 | [@eWhispers](https://x.com/eWhispers) | 572,438 | 5 |
