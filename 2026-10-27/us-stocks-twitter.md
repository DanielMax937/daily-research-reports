# 美股 Twitter 观点日报 · 2026-10-27

周一的收盘已经写进快讯。First Squawk 的收盘价是标普 500 涨 0.70% 到 7677.10，道指涨 0.28% 到 52362.78，纳斯达克综合指数涨 0.83% 到 26169.72：[标普](https://x.com/FirstSquawk/status/2114809922248646785)、[道指](https://x.com/FirstSquawk/status/2114809961608073418)、[纳指](https://x.com/FirstSquawk/status/2114810008760361208)。同一条盘后综述把纳斯达克 100 写成涨 1.1%、半导体指标涨 2.8%，原因是 Anthropic 交表，后面还有 Alphabet、微软和亚马逊的财报：[帖](https://x.com/FirstSquawk/status/2114818707809878271)。巴西和这份收盘不在一张表上。到美东周二早上约 8:10，期货先绿、再红、再回到绿，油的周一结算价和早盘口号也各写各的。周三下午 2 点是沃什的决议。

下面每一条归纳都附有帖文链接。当地股指、EWZ 和盘中口号不要互相替换。媒体标题里没有写出的公司名和目标价，这里不补。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-10-27**。触发时刻约 12:02 UTC，时间线补抓到 **约 12:10 UTC（北京时间 20:10，美东 8:10）**。观察窗口是 **2026-10-26 16:00 UTC 至抓取结束**，也就是北京时间周二零点到晚上 8 点 10 分。这覆盖美东周一中午以后的现货交易、周一收盘，以及周二开盘前。美股现货 9:30 才开盘，所以周二的指数涨跌都是期货或盘前。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。公开趋势接口读到的是 Nicki Minaj、Cheesecake Factory、`#BallonDor`、Riq Woolen、Chiefs，以及政治标签 Flavio。里面没有标普、纳指或个股话题。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。它不是全站每一条提及。
- 不存在官方的“美股 Top 100”。这次试了 **358** 个候选，成功读到粉丝数的有 **324** 个。排序时拿掉 6 个加密货币原生账号（Michael Saylor、Watcher.Guru、Bitcoin Magazine、Coin Bureau、Documenting Bitcoin、Mike Novogratz）和 2 个不是美股市场账号的账号（Noah Smith、OECD），避免它们把交易员和通讯社挤出去。Nick Timiraos 的资料接口第一次返回 404，时间线里的作者字段是 **493,936** 粉，补进排序。用来排序的账号是 **317** 个，截止在 Alf（约 46.6 万粉）。《巴伦周刊》、Hedgeye、Bespoke、Javier Blas、Robin Brooks、The Stalwart、Ryan Detrick、SpotGamma、Kitco、The Transcript 落在线外，引用时会写明。Earnings Whispers 的资料接口这次没有稳定读到粉丝数，不进这张表；它的日历帖链接仍然可用。排序不代表预测准确度。
- 100 个账号里，**69 个**在窗口内有去重后的原创帖，合计 **至少 1825** 条。彭博商业账号读到 197 条后分页中断，最老一条仍在 10 月 26 日 21:15 UTC，条数是下限。《经济学人》读到 80 条后停在窗口起点附近。德意志银行的时间线返回 500，表里的 0 不是确认沉默。彭博主号可见时间线仍对不上它平时的发帖密度，0 同样不能当成确认沉默。路透补抓后读穿了窗口，223 条是完整计数。
- 窗口内确认没有市场原创的包括 Mark Cuban、Paul Krugman、Cathie Wood、Ray Dalio、Andrew Ross Sorkin、Josh Brown、高盛以外的多家银行官方账号、Tom Lee 的 fundstrat 账号、Gundlach、Damodaran、Hindenburg、SEC 官方账号。Dalio 写的是一条原则短帖。Anthony Pompliano 写的是早安，以及一条把周三下午 2 点的决议交给读者自己去问组合影响的帖，没有方向：[帖](https://x.com/APompliano/status/2114878745794490649)。Bill Ackman 只有一句“This is bad”，帖文没有写出对象。ARK 官方账号写的是 Cathie Wood 认为特斯拉和 SpaceX 可能把实际 GDP 增速从 3% 抬到 7%–9%，不是仓位：[帖](https://x.com/ARKInvest/status/2114870074263671023)。

## 周一收盘和周二早上，讲的不是同一根 K 线

收盘价以 First Squawk 那三行为准：标普 7677.10，涨 0.70%；道指 52362.78，涨 0.28%；纳斯达克综合指数 26169.72，涨 0.83%。纳斯达克 100 的 1.1% 和半导体指标的 2.8% 是另一条综述里的口径，不要和综合指数的 0.83% 合成一个涨幅。Investing.com 的收盘标题是美股周一开始收高、VIX 下跌，Anthropic 的 IPO 文件抬了 AI 股票：[帖](https://x.com/Investingcom/status/2114815577370001521)。路透的标题是股票收高，标普和纳指结束了连续周线下跌：[帖](https://x.com/Reuters/status/2114881010701897732)。《华尔街日报》市场账号的标题是美股在科技财报前上涨：[帖](https://x.com/WSJmarkets/status/2114814520921067848)。纽交所的节目提要写成标普上涨、芯片股带动、美联储决议周开场：[帖](https://x.com/NYSE/status/2114808533078376704)。MarketWatch 的标题是股票全线收高，Anthropic 的交表抬了科技和 AI：[帖](https://x.com/MarketWatch/status/2114810977535263125)。同一账号后来写 Lumentum 领涨标普：[帖](https://x.com/MarketWatch/status/2114835302208385451)。

收盘前的买卖失衡是卖盘。FinancialJuice 记下的收盘失衡是标普 -17.185 亿美元、纳斯达克 100 -14.927 亿美元、道指 -3.572 亿美元、七巨头 -3.992 亿美元：[帖](https://x.com/financialjuice/status/2114807008469688576)。指数收涨，和这笔失衡的方向相反。

周二盘前期货换过三次方向。First Squawk 先写标普期货涨 0.2%、纳指期货涨 0.43%：[帖](https://x.com/FirstSquawk/status/2114879224028999952)。随后改成标普电子迷你期货跌 0.2%、纳斯达克 100 期货跌 0.5%、道指期货持平，同时富时 100 跌 0.87%、法国 CAC 跌 0.34%：[美股期货](https://x.com/FirstSquawk/status/2114990884836286559)、[欧洲](https://x.com/FirstSquawk/status/2114990841790120035)。DeItaone 在美东清晨的读数又回到标普电子迷你期货涨 0.3%、纳斯达克 100 期货涨 0.5%、道指期货涨 0.4%：[帖](https://x.com/DeItaone/status/2115032523910623495)。MarketWatch 的标题是期货升到盘前高位、油价下跌：[帖](https://x.com/MarketWatch/status/2115034420893614234)。彭博商业账号的标题是人工智能的乐观在美联储前减弱、美国期货摇摆：[帖](https://x.com/business/status/2115035894256115734)。《华尔街日报》市场账号的标题是期货稳住，Anthropic 的涨势停住，以色列选举进入视线：[帖](https://x.com/WSJmarkets/status/2115017074342854716)。这五条都是盘前，都不能写成周二收盘。

Gary Black 在这组摆动中间写下的盘前快照是：股票小幅走高，市场对已经宣布的人工智能股票发行耸耸肩，其中包括他写成“可能 1000 亿美元”的 Anthropic IPO、OpenAI 预期中的发行，以及 Meta 1000 亿美元的二次发行。他等待的是明天偏鹰的按兵不动，以及本周 Alphabet、微软、亚马逊的财报。他写下的价格是布伦特 117 美元、10 年期收益率 4.98%、比特币 7.97 万美元，黄金和白银下跌，科技股普遍更高，特斯拉在 SpaceX 合并猜测里上涨：[帖](https://x.com/garyblack00/status/2115016452516270335)。1000 亿美元是他的取整，不是文件里的发行额。

## 观点分成四组

### 1. 巴西有四组跌幅，美股周一没收进这张表

跌幅按发帖时间分开，不取平均。

Kobeissi 在美东中午写，巴西股票跌 30%，巴西波动率指数下跌 40%，当天市值少了 2000 亿美元：[帖](https://x.com/KobeissiLetter/status/2114762014354714958)。同一账号随后写巴西 10 年期国债收益率推向 16%，一天上升 300 个基点：[帖](https://x.com/KobeissiLetter/status/2114785608312967621)。雅虎财经在 20:46 UTC 写巴西股票跌超 18%，并说这逆转了博索纳罗首轮领先之后的涨势：[帖](https://x.com/YahooFinance/status/2114821109870653557)。Investing.com 在收盘后写巴西股票跌 13.9%，为 2020 年以来最差的一天：[帖](https://x.com/Investingcom/status/2114842673622200789)。

美国上市的 ETF 是另一列。Barchart 写 EWZ 跌近 20%，跌幅超过全球金融危机，是史上第二大单日跌幅：[帖](https://x.com/Barchart/status/2114894352116052233)。Eric Balchunas 写 EWZ 成交大约 100 亿美元，打破纪录，超过微软当天的成交，ETF 跌 20%：[帖](https://x.com/EricBalchunas/status/2114827178311602642)。线外的 Bespoke 写，这是 EWZ 第 16 次单日下跌超过 10%，在国家 ETF 里是新纪录：[帖](https://x.com/bespokeinvest/status/2114832698061517286)。

《金融时报》写的是雷亚尔和圣保罗股指一起滑，卢拉胜选加重了财政担心：[股汇](https://x.com/FT/status/2114760072207241280)、[财政](https://x.com/FT/status/2114948931754885429)。Investing.com 转述摩根大通把巴西雷亚尔和利率降到市场权重：[帖](https://x.com/Investingcom/status/2114770314882146795)。El-Erian 把跌幅的量级写成共识错了：市场对博索纳罗获胜太有把握，抛售说明的是这个错误，不是巴西本身的前景：[帖](https://x.com/elerianm/status/2114771487924367576)。线外的 The Stalwart 补了一句，按年初至今算，巴西雷亚尔仍是表现最好的主要货币之一：[帖](https://x.com/TheStalwart/status/2114853473561059481)。彭博商业账号转述 John Authers：巴西的黑色星期一可能又是一个买点：[帖](https://x.com/business/status/2114956545649754431)。

政治上的更新比周一早上的“宣布无效”更靠后。彭博商业账号写，落败的弗拉维奥·博索纳罗放弃寻求宣布选举无效，改为控告卢拉滥用权力：[帖](https://x.com/business/status/2114885775934267868)。《金融时报》写博索纳罗的自由党承认败选，特朗普称结果被操纵：[帖](https://x.com/FT/status/2114887552935076111)。路透用了同一组话：[帖](https://x.com/Reuters/status/2114912478438043945)。Keith McCullough 的交易结果只写了一句：家里人当天亏钱，主要是因为被巴西打到：[帖](https://x.com/KeithMcCullough/status/2114879510734663996)。TheStreet 点名 Nubank 在卢拉胜选后的巴西抛售里下跌，正文没有写出百分比：[帖](https://x.com/TheStreet/status/2114967869607834000)。

### 2. 调整后盈利和 GAAP 巨亏写在同一份 S-1 里

Charlie Bilello 把 Anthropic 上半年的数字列成：收入 163 亿美元，同比增 1300%；营业费用 170 亿美元，同比增 415%；净利润 -808 亿美元，一年前是 -130 亿美元，他注明大部分来自可转换票据和融资协议的非现金会计；调整后净利润 27 亿美元，一年前上半年是 -17 亿美元；现金及等价物 1124 亿美元；短期投资 193 亿美元。代码是 `$ANT`：[帖](https://x.com/charliebilello/status/2114879002053693669)。Investing.com 的标题把亏损写成 807 亿美元，并写公司在纳斯达克申请上市：[帖](https://x.com/Investingcom/status/2114763002360520758)。《华尔街日报》Heard 栏目写，807 亿美元净亏损的另一面，是亚马逊和 Alphabet 在许多同一批融资交易上记了大额账面收益：[帖](https://x.com/WSJmarkets/status/2115013645591609445)。Business Insider 另有一条把 2025 年净亏损写成约 420 亿美元、收入 46 亿美元，那是另一年的句子，不要和上半年的 808 亿放进同一个格子：[帖](https://x.com/BusinessInsider/status/2114759501735674237)。

文件里的风险条款被快讯拆开了。Investing.com 写收入增长可能不可持续、可能比目前预期更早再融资、IPO 后有早期股份出售、人工智能可能带来比以往技术更大的经济扰乱，并警告灾难性和生存性风险：[增长](https://x.com/Investingcom/status/2114752543351771245)、[再融资](https://x.com/Investingcom/status/2114768074406613385)、[生存风险](https://x.com/Investingcom/status/2114772172317073745)。同一账号写，公司到 2033 年可能向谷歌支出至多约 1145 亿美元；Class F 普通股没有经济权利，投票权占 50.1%；截至 9 月 30 日，年收入超过 100 万美元的客户超过 1900 个：[谷歌](https://x.com/Investingcom/status/2114784543282786508)、[Class F](https://x.com/Investingcom/status/2114787637437378929)、[客户](https://x.com/Investingcom/status/2114803735646134411)。《巴伦周刊》在线外，它写上半年调整后净利润 27 亿美元，并写七位联合创始人通过 Class F 保持多数控制：[利润](https://x.com/barronsonline/status/2114761857734959364)、[控制权](https://x.com/barronsonline/status/2114816230993334578)。高盛和摩根士丹利将牵头这次 IPO：[巴伦](https://x.com/barronsonline/status/2114837732107133296)。彭博商业账号写，这两家拿到的位置和它们在 6 月 SpaceX 那次 862 亿美元上市里的位置一样：[帖](https://x.com/business/status/2114838273285669358)。

The Information 写的承诺和估值是另一组：云计算承诺大约 6570 亿美元，IPO 估值可能到 1.5 万亿美元或更高，并披露二季度营业利润 9.74 亿美元；过去 12 个月收入 197 亿美元：[承诺与利润](https://x.com/theinformation/status/2114794705435189750)、[12 个月收入](https://x.com/theinformation/status/2114847104447193564)。路透写公司披露了长达一个月的训练暂停和人工智能安全事件：[帖](https://x.com/Reuters/status/2114863435196268987)。彭博商业账号写，文件警告可能比预期更早再融资，而且几乎没有写投资级信用评级的路径：[帖](https://x.com/business/status/2114873509914509472)。

融资的现金侧被写成博通的芯片。路透的标题是华尔街银行和黑石排起 630 亿美元，为 Anthropic 的博通人工智能芯片融资：[帖](https://x.com/Reuters/status/2114897412586168771)。彭博商业账号把参与方写成美国银行、黑石、花旗和摩根士丹利：[帖](https://x.com/business/status/2114857153919914124)。《华尔街日报》写博通首席执行官在周末和银行做了最后关头的谈话，要他们落实对一笔 Anthropic 债务交易的承诺：[帖](https://x.com/WSJ/status/2115005351196004393)。彭博另一条只说，周一早上三笔巨型人工智能融资有一个共同的名字，高盛；正文没有写出金额：[帖](https://x.com/business/status/2114870987732799898)。Chamath 的市场原话只有一句：Ant 是一门了不起的生意：[帖](https://x.com/chamath/status/2114757891609788831)。

信用和“调整后已经赚钱”放在一起。zerohedge 写，如果 Anthropic 在贷款上违约，没有东西能保护银行：[帖](https://x.com/zerohedge/status/2114927610690232321)。同一账号的标题是 Citadel Securities 认为人工智能交易在拆开，容错空间已经很小：[帖](https://x.com/zerohedge/status/2115047147817029760)。Carl Quintanilla 引用的判断是，人工智能泡沫若破裂，很可能从信用事件开始，neocloud 和有风险的人工智能债务违约，再传到估值和增长；他点了 CoreWeave：[帖](https://x.com/carlquintanilla/status/2114766698318303342)。线外的 Hedgeye 引 Felix Wang：在他覆盖的范围里，neocloud 会第一个炸，因为杠杆太高：[帖](https://x.com/Hedgeye/status/2114773892354941143)。线外的 SpotGamma 写，HYG 的认沽偏度周五收在过去一年的第 82 百分位；CoreWeave 在上周跌了 11.7%、马斯克谈过债务市场之后，认沽偏度仍在第 39 百分位，一个月隐含波动率 108%，下行认沽相对认购几乎没有溢价（+0.46 个波动率点）：[帖](https://x.com/spotgamma/status/2114750018204688834)。

Raoul Pal 站在相反的资产负债表上。他写超大规模云厂商是史上最大的现金产生者，把现金流再投进史上最大的资本开支，债务大约只占市值的 3.5%：[帖](https://x.com/RaoulGMI/status/2114945696725885028)。《财富》转述 Apollo 的 Torsten Slok：尽管有巨大投资和宣传，人工智能对科技业以外的美国公司财务回报是零：[帖](https://x.com/FortuneMagazine/status/2114854629666091067)。Unusual Whales 转述 Dan Ives 的赌注：人工智能牛市走了不到 15%：[帖](https://x.com/unusual_whales/status/2115029992547774897)。Keith 转发的 Hedgeye 标题是人工智能交易到了中局：[帖](https://x.com/KeithMcCullough/status/2115015599676174484)。

Meta 的发行和英伟达的 30 亿美元是周二早上的价格。路透商业账号写 Meta 计划筹集至多 950 亿美元，是它最大的一次股权融资：[帖](https://x.com/ReutersBiz/status/2114805513171214798)。线外的《巴伦周刊》把其中 125 亿美元可转换股票写成 950 亿美元融资的一部分：[帖](https://x.com/barronsonline/status/2114804884402835790)。StockMKTNewz 写普通股发行从 225 亿美元提高到 250 亿美元，定价每股 625 美元，英伟达将投入 30 亿美元，两家扩大合作，Meta 会更多使用英伟达硬件，包括 Vera Rubin，用来跑 Muse：[帖](https://x.com/StockMKTNewz/status/2115046396252312011)。First Squawk 写 Meta 在宣布发行定价后盘前跌 0.5%：[帖](https://x.com/FirstSquawk/status/2114994414154371526)。Axios 用的是同一笔 30 亿美元和 Muse：[帖](https://x.com/axios/status/2115012094202466604)。

投资级债券的发行纪录和这些股票发行是同一天的信用事实。DeItaone 写美国高评级债券销售将创纪录，达到 1.76 万亿美元：[帖](https://x.com/DeItaone/status/2114795884269428871)。彭博商业账号写，周一就将超过 2020 年疫情借款潮的 1.75 万亿美元：[帖](https://x.com/business/status/2114849612628361586)。StockMKTNewz 转述黑石的 Rick Rieder：人工智能驱动的债务繁荣带来了他职业生涯里没见过的融资规模，他等了很久的 7% 收益率：[帖](https://x.com/StockMKTNewz/status/2114905585443278949)。彭博商业账号转述摩根大通资产管理的 Bob Michele：美国债券市场未来 12 个月回报可能在 7% 到 8%：[帖](https://x.com/business/status/2114947734247522534)。Business Insider 转述 Mark Zandi：利率若不尽快回落，会造成真正的损害，债券投资者已经在替美联储干活：[帖](https://x.com/BusinessInsider/status/2114777070358122861)。

Kobeissi 写的是杠杆的需求，不是目标价。全球股票基金在截至 10 月 21 日的一周流入 282 亿美元，连续第五周，这段时间合计流入 1386 亿美元；亚洲股票基金上周流入 115 亿美元，至少是 2022 年 12 月以来最大的一周，欧洲和美国分别流入 91 亿和 51 亿美元：[帖](https://x.com/KobeissiLetter/status/2114809543918071925)。美国 10 只最大的杠杆股票 ETF 过去一个月流入 120 亿美元，同一时期这些基金的市值少了 200 亿美元；三倍做多半导体的 SOXL 两周流入 90 亿美元，为该长度的纪录；三倍做多纳斯达克 100 的 TQQQ 流入 13 亿美元：[帖](https://x.com/KobeissiLetter/status/2114827351850639388)。零售期权占 Citadel 平台成交量的 61%，接近纪录，12 个月上升 16 个百分点，比 2020 年的高点还高 10 个百分点；指数和 ETF 期权相对个股是 1.7 比 1，SPY 和 QQQ 合计占零售期权成交的 47%：[帖](https://x.com/KobeissiLetter/status/2114881746621575597)。

### 3. 周一油是结算下来的，周二早上又被写成周期新高

结算价先写。FinancialJuice：NYMEX WTI 12 月期货结算 101.76 美元，跌 1.51 美元，跌 1.46%；布伦特结算 115.81 美元，跌 91 美分，跌 0.78%：[WTI](https://x.com/financialjuice/status/2114786993620365496)、[布伦特](https://x.com/financialjuice/status/2114790431225757996)。First Squawk 用了同一组结算，并在更晚的一条写布伦特期货再跌 1% 到 114.62 美元：[结算](https://x.com/FirstSquawk/status/2114788027398770806)、[114.62](https://x.com/FirstSquawk/status/2114893483064631334)。《华尔街日报》市场账号的标题先是外交努力让油价下跌，后是交易员在伊朗外交和沙特遇袭之间权衡、油价下跌：[外交](https://x.com/WSJmarkets/status/2114892631444525434)、[遇袭](https://x.com/WSJmarkets/status/2114984269281951854)。

早盘口号比结算更高。线外的 Hedgeye 在周一下午写布伦特涨破每桶 116 美元，为四年高位：[帖](https://x.com/Hedgeye/status/2114774627251568835)。Keith 在周二早上写布伦特再次涨到 116 美元，是这轮通胀周期的新高，并问“没有通胀问题”还能否相信：[116](https://x.com/KeithMcCullough/status/2115012383827492953)、[通胀](https://x.com/KeithMcCullough/status/2115012695988785228)。Gary Black 写的是 117 美元。三组数字按各自的发帖时间保留，不合成一根结算价。

期权和库存仍在定价供应风险。DeItaone 写 WTI 看涨期权偏斜升到 +7.2%，为 9 月 10 日以来最高；1 到 2 个月价差从每桶 5.40 美元收到 2.30 美元，近端现货升水变弱：[帖](https://x.com/DeItaone/status/2114779813953060983)。Investing.com 写美国战略石油储备降到 2.826 亿桶，为 1982 年以来最低：[帖](https://x.com/Investingcom/status/2114760664774312071)。LiveSquawk 写胡塞称袭击了沙特拉斯塔努拉炼厂：[帖](https://x.com/LiveSquawk/status/2115035862107037909)。同一账号转述路透信源：欧佩克+周日的会议准备维持产量目标不变：[帖](https://x.com/LiveSquawk/status/2115011343334228434)。

霍尔木兹和柴油是谈判侧。DeItaone 写伊朗称若条件满足，可以在 4 到 5 天而不是提议的 7 天内重开霍尔木兹，对象包括沙特、土耳其和巴基斯坦：[帖](https://x.com/DeItaone/status/2114808748380246193)。Investing.com 转述伊朗官员：与麦加协议国家的谈话不包括核问题，美国满足要求之前不讨论核计划：[帖](https://x.com/Investingcom/status/2114756683050197359)。周二早上，DeItaone 和 LiveSquawk 都写最高领袖要求满足条件才能结束战争：[DeItaone](https://x.com/DeItaone/status/2115030405124440541)、[LiveSquawk](https://x.com/LiveSquawk/status/2115032902278996044)。卡塔尔的话是伊朗需要拿出诚意、停止对邻国的威胁：[帖](https://x.com/DeItaone/status/2115035943161786749)。俄罗斯柴油继续往美国走。DeItaone 转述诺瓦克：第四艘油轮 10 月 28 日出发，另有三艘在途：[帖](https://x.com/DeItaone/status/2115035884504436901)。普京称俄方对天然气合作开放，并在探索与美国伙伴的合作：[帖](https://x.com/DeItaone/status/2115046518596243747)。

线外的 Javier Blas 写的是实物出口。沙特本月前 22 天原油出口折合每天超过 700 万桶，回到战前水平，走波斯湾也走红海；他把产量写成朝每天 900 万到 1000 万桶靠拢。加上成品油，10 月 1 日到 22 日的出口大约每天 850 万桶，略低于战前每天超过 900 万桶的水平：[帖](https://x.com/JavierBlas/status/2115041611461632085)。日经亚洲写印度分析师认为，即便有新的美国法律，印度也停不了俄罗斯石油：[帖](https://x.com/NikkeiAsia/status/2114987361951945095)。路透写印度石油部长称，美国没有施压要求削减俄罗斯石油进口：[帖](https://x.com/Reuters/status/2114999325256270199)。

天然气要和原油分开。FinancialJuice 的 NYMEX 天然气 11 月期货结算是每百万英热 2.6020 美元：[帖](https://x.com/financialjuice/status/2114787221543034965)。zerohedge 的标题是欧洲面对提前到来的冬季考验，天然气价格靠近三位数：[帖](https://x.com/zerohedge/status/2115050919159099836)。同一账号转述国际能源署的比罗尔：2027 年没有可信的路径回到战前的能源市场：[帖](https://x.com/zerohedge/status/2115034561444708681)。

黄金在 4000 美元上方，方向仍分裂。彭博商业账号写金价守在每盎司 4000 美元之上，交易员在等预计维持利率不变的美联储：[帖](https://x.com/business/status/2114899993593008606)。Keith 写黄金和白银继续下跌，他仍看空：[帖](https://x.com/KeithMcCullough/status/2115013016760754599)。线外的 Kitco 转述 BCA 的 Ibrahim：金价在 4000 美元下方超卖，但近端反弹仍可能够不着；10 年期收益率本周从 5% 下方开出，对黄金的缓解有限：[帖](https://x.com/KitcoNewsNOW/status/2114802339056124021)。同一账号转述 UBWM 的 Haworth：黄金要有机会上涨，伊朗战争得结束；他写下年初纪录高点在每盎司 5600 美元之上：[帖](https://x.com/KitcoNewsNOW/status/2115035602982744267)。

### 4. 周三是按住，市场只给这次会议定价了大约 3 个基点

El-Erian 写，美联储今天开始为期两天的会议，市场压倒性预期明天维持利率不变；鉴于最近一串通胀数据，会后措辞应相对偏鹰，异议可能出现，但这点没那么清楚：[帖](https://x.com/elerianm/status/2115049021177745820)。线外的 Robin Brooks 把同一件事写成两边都有限：不会加息，所以沃什能说出的鹰派有上限；他又想把 12 月的加息留在桌面上，所以也不能真的偏鸽。新闻发布会对市场应大致中性。他写下的定价是这次会议大约 3 个基点，并说市场在中期选举前的这场会里显得温顺：[中性](https://x.com/robin_j_brooks/status/2115010283655803090)、[3 个基点](https://x.com/robin_j_brooks/status/2115012697787887934)。

Nick Timiraos 写的是另一场辩论：利率定在哪里，以及官员该把对未来的看法说到什么程度。沃什强调少说，同事们说话的量和一年前至少一样多。一位前美联储经济学家把这个结果称为“所有可能结果里最差的”：没有人能逼他代表委员会说话，他也没法逼其他委员闭嘴：[帖](https://x.com/NickTimiraos/status/2115031082403844333)。Squawk Box 引前副主席 Roger Ferguson：周三按住，但下次得动得相当猛：[帖](https://x.com/SquawkCNBC/status/2114767521542783247)。Jason Furman 写，美联储去年预测今年降息一次，结果会是加息一到两次，低于他心目中的反应函数所要求的幅度；若把大约 0.5 个百分点的通胀写成暂时的，他们就刚好在目标上：[帖](https://x.com/jasonfurman/status/2114905286657921442)。《华尔街日报》观点版的标题把沃什、前瞻指引和诺贝尔奖放在一起，写获奖经济学家在为这位主席不喜欢的那种预测做辩护：[帖](https://x.com/WSJ/status/2114789796824461814)。

Keith 的利率表达是曲线，不是点位。他写债券波动率信号等于没有变化；曲线进一步走平，短端 2 年期随通胀上升，长端 30 年期下降，因为人工智能泡沫的增长预期在破裂；美元仍是核心配置，趋势看多：[波动率](https://x.com/KeithMcCullough/status/2115007101760151869)、[曲线](https://x.com/KeithMcCullough/status/2115014048920301590)、[美元](https://x.com/KeithMcCullough/status/2115014791764885666)。他的 Early Look 标题是 Quad 2 的石油通胀对 Quad 4 的人工智能泡沫破裂：[帖](https://x.com/KeithMcCullough/status/2115040306403914154)。他问标普 ETF 这周会不会重新掉进震荡区间：[帖](https://x.com/KeithMcCullough/status/2115007332036009998)。他另写，一种被他称为“CNBC 式零售投资者”的篮子在市场上涨的周一又跌了 1.2%，年初至今跌 11.2%：[帖](https://x.com/KeithMcCullough/status/2115008465143808059)。

法国和住房是这条利率故事旁边的两张表。LiveSquawk 写法国 10 月消费者信心 80，预期 85，前值修正后 85：[帖](https://x.com/LiveSquawk/status/2114987008531530056)。El-Erian 把这个读数写成 2013 年以来最低：[帖](https://x.com/elerianm/status/2115050631119458574)。线外的 Robin Brooks 写法国收益率和利差在稳住，上周被停掉的是 6 月油价下跌时建上的套息，清洗已经结束：[帖](https://x.com/robin_j_brooks/status/2115017728595513854)。Charlie Bilello 写美国成屋销售待完成降到纪录最低，低于 2020 年 4 月；房屋建筑商信心降到 2012 年以来最低，纪录的 43% 在降价，65% 在提供激励，并且这是连续第 19 个月高于 60%：[销售](https://x.com/charliebilello/status/2114800650710053142)、[建筑商](https://x.com/charliebilello/status/2114806739971326192)。他另写，美国物价自 2023 年以来第一次涨得比工资快：[帖](https://x.com/charliebilello/status/2114826693546287514)。Peter Schiff 用 9 月出口价格上升 2.2% 做同一件事，说这超过了美联储全年 2% 的目标，年化是 30%，并把眼下写成住房的 2008 加上通胀的 2021：[帖](https://x.com/PeterSchiff/status/2114791326042452091)。

Michael Burry 周一的新帖仍是市场结构。他写画面是市场下面有一股越来越强的机械买盘：它不做评估，不把上涨读成有用的信息，下跌时出现的规模和速度没有先例：[帖](https://x.com/michaeljburry/status/2114777677760774611)。

## 要盯住的五件事

1. **周二开盘时，周一的 7677.10 还在不在。** 盘前期货在涨 0.2%、跌 0.2% 和涨 0.3% 之间换过手。DeItaone 抓取结束前的最后一组是标普期货涨 0.3%、纳指期货涨 0.5%。Meta 盘前跌 0.5% 是发行定价之后的反应。耐久品订单、消费者信心、里士满联储和新屋销售按 Bespoke 的日程在美东 8:30 和 10:00，抓取结束时还没到点：[帖](https://x.com/bespokeinvest/status/2115033389782729072)。
2. **巴西用哪一个收盘数字交易。** 帖文里同时有跌 30%、跌超 18%、收盘跌 13.9%，以及 EWZ 跌约 20%、成交约 100 亿美元。10 年期收益率被写成推向 16%。博索纳罗一侧已经从“宣布无效”改成放弃寻求宣布选举无效，改为控告滥用权力。Authers 把这一天写成可能的买点，El-Erian 把量级写成共识错误。
3. **Anthropic 的文件今天交易的是 27 亿美元调整后利润，还是 808 亿美元净亏损和“可能更早再融资”。** 630 亿美元的博通芯片融资已经有银行名单。Meta 的普通股定价在每股 625 美元，英伟达认 30 亿美元，盘前股票先跌了 0.5%。CoreWeave 的认沽在线外的 SpotGamma 那里仍几乎没有溢价。
4. **116 美元和 101.76 美元不要写成同一个油价。** WTI 周一结算 101.76 美元，布伦特结算 115.81 美元，随后有一条布伦特期货 114.62 美元。Keith 和 Gary 周二早上分别写 116 和 117。胡塞称打了拉斯塔努拉，欧佩克+被写成周日维持产量。美国战略储备在 1982 年以来的低位。欧洲天然气和美国 2.60 美元的结算是两个市场。
5. **周三下午 2 点的措辞，而不是这次会议的加息。** El-Erian 的基准是按住、措辞偏鹰、异议可能有。Brooks 写新闻发布会大致中性，定价大约 3 个基点，12 月的加息被留在桌面上。Timiraos 写的裂缝是沃什少说、同事照说。Furman 写的全年路径是加息一到两次，不是这次会议。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 周一收盘 | 标普、道指、纳斯达克综合指数、纳斯达克 100 | 标普收 7677.10，涨 0.70%。道指收 52362.78，涨 0.28%。纳斯达克综合指数收 26169.72，涨 0.83%。另一条综述写纳斯达克 100 涨 1.1%、半导体指标涨 2.8% | [标普](https://x.com/FirstSquawk/status/2114809922248646785)、[道指](https://x.com/FirstSquawk/status/2114809961608073418)、[综合指数](https://x.com/FirstSquawk/status/2114810008760361208)、[纳指 100 与半导体](https://x.com/FirstSquawk/status/2114818707809878271) |
| 已经打出来的缺口 | 巴西股市、EWZ、雷亚尔、Nubank | Kobeissi：股票跌 30%，10 年期收益率推向 16%。雅虎：股票跌超 18%。Investing.com：收盘跌 13.9%。Balchunas：EWZ 跌 20%，成交约 100 亿美元。Bespoke：EWZ 第 16 次跌超 10%。TheStreet：Nubank 在抛售中下跌 | [30%](https://x.com/KobeissiLetter/status/2114762014354714958)、[18%](https://x.com/YahooFinance/status/2114821109870653557)、[13.9%](https://x.com/Investingcom/status/2114842673622200789)、[EWZ](https://x.com/EricBalchunas/status/2114827178311602642)、[Nubank](https://x.com/TheStreet/status/2114967869607834000) |
| 文件而不是行情 | ANT、AMZN、GOOGL、AVGO、GS、MS、BX | 上半年收入 163 亿美元，净利润 -808 亿美元，调整后净利润 27 亿美元。博通芯片融资 630 亿美元，银行名单含美国银行、黑石、花旗、摩根士丹利。高盛和摩根士丹利牵头 IPO。Heard：亚马逊和 Alphabet 在相关融资上有账面收益 | [上半年](https://x.com/charliebilello/status/2114879002053693669)、[630 亿](https://x.com/Reuters/status/2114897412586168771)、[银行名单](https://x.com/business/status/2114857153919914124)、[账面收益](https://x.com/WSJmarkets/status/2115013645591609445) |
| 周二盘前已有价格 | META、NVDA | 普通股发行提高到 250 亿美元，每股 625 美元，英伟达投入 30 亿美元。盘前 Meta 跌 0.5%。路透商业账号的总额是至多 950 亿美元 | [625 美元](https://x.com/StockMKTNewz/status/2115046396252312011)、[盘前](https://x.com/FirstSquawk/status/2114994414154371526)、[950 亿](https://x.com/ReutersBiz/status/2114805513171214798) |
| 合并猜测里的汽车股 | TSLA、SPCX | 线外《巴伦周刊》没有写目标价的那条之外，StockMKTNewz 转述巴克莱把特斯拉上调到超配，目标价 450 美元，前值 370 美元。彭博写分析师因更接近的 SpaceX 合并而更快转多。TrendSpider：特斯拉创 7 月以来最高收盘。线外 The Transcript 引 SpaceX 首席执行官：算力大约一半自用、一半外租，按现货价而不是长期合同 | [巴克莱](https://x.com/StockMKTNewz/status/2114891578812879319)、[合并](https://x.com/business/status/2114833238703100412)、[收盘](https://x.com/TrendSpider/status/2114836242420625835)、[算力](https://x.com/TheTranscript_/status/2114869695748964814) |
| 信用里被单独点名 | CRWV、HYG | Carl：泡沫若破裂，可能从 neocloud 的信用事件开始，点名 CoreWeave。线外 SpotGamma：CRWV 认沽几乎没有溢价。Cramer 问 CoreWeave 是不是在试图反弹 | [Carl](https://x.com/carlquintanilla/status/2114766698318303342)、[偏度](https://x.com/spotgamma/status/2114750018204688834)、[Cramer](https://x.com/jimcramer/status/2114822284762321053) |
| 周一领涨和图表 | LITE、SOXX、GOOGL、IGV、MU | MarketWatch：Lumentum 领涨标普。TheStreet：StoneX 以买入覆盖 Lumentum，理由是人工智能需求延伸到 2029 年。Barchart：半导体从 200 日均线反弹；Alphabet 低于 200 日均线的幅度是 17 个月最大。线外《巴伦周刊》：Alphabet 较高点回落 22%。线外 Detrick 转发的图问软件能否再涨 31%，代码是 IGV。TheStreet 标题：美光在跌 6% 的情况下出现 3000 美元的看涨说法 | [Lumentum](https://x.com/MarketWatch/status/2114835302208385451)、[StoneX](https://x.com/TheStreet/status/2114899952388264179)、[均线](https://x.com/Barchart/status/2114913666982408552)、[Alphabet 均线](https://x.com/Barchart/status/2114924310334939239)、[22%](https://x.com/barronsonline/status/2114779965065503122)、[IGV](https://x.com/RyanDetrick/status/2114762677339742711)、[美光](https://x.com/TheStreet/status/2114998069381013555) |
| 已经公布的财报 | KO、BA、UPS、PYPL、GLW、SOFI、FCX、CLS、SPGI、RCL | 可口可乐收入 134 亿美元、调整后每股收益 0.91 美元，上调全年。波音收入 241.9 亿美元、核心每股亏损 0.34 美元。UPS 调整后每股收益 1.69 美元，全年收入看到 926 亿美元。PayPal 收入低于预期、每股收益高于预期，全年调整后每股收益大约 5.60 美元。康宁双超。SoFi 盘前一度涨超 10%。自由港调整后每股收益 0.88 美元，铜产量同比降 8.8%。Celestica 盘后涨超 10% 并上调。标普全球双超并上调。皇家加勒比上调全年，四季度每股收益指引 3.48 到 3.58 美元，低于帖文里的预期 | [可口可乐](https://x.com/DeItaone/status/2115035752878731560)、[波音](https://x.com/LiveSquawk/status/2115043870010437992)、[UPS](https://x.com/LiveSquawk/status/2115022122636501355)、[PayPal](https://x.com/LiveSquawk/status/2115036792848076821)、[SoFi](https://x.com/StockMKTNewz/status/2115050080139133174)、[自由港](https://x.com/LiveSquawk/status/2115052109477425357)、[Celestica](https://x.com/TrendSpider/status/2114815158430171544)、[标普全球](https://x.com/TrendSpider/status/2115047640786161688)、[皇家加勒比](https://x.com/LiveSquawk/status/2115029059872919713) |
| 可能本周落地的并购 | DASH、CART | 雅虎财经写 DoorDash 收购 Instacart 的谈判可能本周完成，估值大约 170 亿美元，报道前大约 130 亿美元。福克斯商业频道用了 170 亿美元这个数字 | [雅虎](https://x.com/YahooFinance/status/2114825620815270228)、[福克斯](https://x.com/FoxBusiness/status/2114899949380899170) |
| 能源和黄金的价格，不是目标价 | WTI、布伦特、黄金 | WTI 结算 101.76 美元。布伦特结算 115.81 美元，另有期货 114.62 美元，以及早盘口号 116 和 117 美元。黄金守在 4000 美元上方，Keith 仍看空 | [WTI](https://x.com/financialjuice/status/2114786993620365496)、[布伦特结算](https://x.com/financialjuice/status/2114790431225757996)、[114.62](https://x.com/FirstSquawk/status/2114893483064631334)、[黄金](https://x.com/business/status/2114899993593008606) |
| 开支和上市地点 | MSFT、GM | 微软向大约 6 万名员工提供自愿离职。通用汽车 11 月 17 日从纽交所转到纳斯达克。美加正在谈减轻加拿大钢铁和汽车关税，DeItaone 点名通用、福特、Stellantis 和克利夫兰克利夫斯 | [微软](https://x.com/Reuters/status/2114898155699314735)、[通用汽车](https://x.com/CNBC/status/2115029206883082732)、[关税](https://x.com/DeItaone/status/2114801784833335515) |

周一盘后还有一组没有放进方向、但日历已经点名的名字。Earnings Whispers 的资料接口这次没读到粉丝数，日历帖仍在：周一收盘后包括 Celestica、Cadence、Nucor、Rambus、Amkor、Welltower、Whirlpool；周二开盘前包括 SoFi、可口可乐、UPS、康宁、自由港、PayPal、波音、标普全球：[周一](https://x.com/eWhispers/status/2114751595896574055)、[周二](https://x.com/eWhispers/status/2114771384333140448)。线外的 Bespoke 把周二收盘后写成 Visa、恩智浦和希捷：[帖](https://x.com/bespokeinvest/status/2114831941560136139)。StockMKTNewz 的收盘后名单还包括 Robinhood、Waste Management、Teradyne、Baker Hughes：[帖](https://x.com/StockMKTNewz/status/2114843466421432376)。

## 后续走势：三套可以证伪的剧本

帖文没有给周二的收盘点位。周一的现货收盘是 7677.10。下面三套的顺序，以开盘时期货还停在 DeItaone 那组涨 0.3% 附近为前提。

**Anthropic 的文件继续被当成风险偏好，巴西留在当地。** 触发器是标普守住 7677 一带，半导体维持 First Squawk 写下的那种跳升，EWZ 不再扩大大约 20% 的缺口。这条路径上，市场交易的是调整后 27 亿美元、1900 个百万美元客户，以及亚洲芯片股已经先涨这一事实。彭博写亚洲半导体股票在交表后跳升：[帖](https://x.com/business/status/2114918817008582777)。日经亚洲写韩国三季度经济增长 1.0%，靠的是芯片：[帖](https://x.com/NikkeiAsia/status/2114855837919228053)。Dan Ives 的“不到 15%”和 Raoul 的“债务只占市值 3.5%”站在这一侧。若 Meta 的 625 美元发行在开盘后被交易成稀释而不是英伟达的 30 亿美元接盘，或者 CoreWeave 的认沽溢价从 SpotGamma 写下的接近于零明显走阔，这条路径失败。

**信用先于指数。** 触发器已经写在周一的帖里：Citadel Securities 的容错很小，Carl 把破裂的起点放在 neocloud 债务，Anthropic 自己写可能更早再融资，投资级发行越过 1.75 万亿美元。Keith 的标题把人工智能放在 Quad 4 的破裂里，并把 30 年期收益率的下降说成增长预期在破。Wilson 和 Yardeni 的点位这次没有被这些账号更新。这条路径失败的条件，是调整后利润和博通的 630 亿美元被当成融资已经找到，而不是债务还要再加。

**油价口号盖过结算价，周三的“按住”被说成还不够鹰。** 触发器是布伦特从 115.81 美元的结算重新站上 Keith 的 116 或 Gary 的 117，同时沃什的措辞比 Brooks 写的“大致中性”更鹰，12 月加息从“留在桌面上”变成基准。胡塞的拉斯塔努拉和战略储备的 1982 年低位是这条路径已经印出来的供给句子。它失败的条件，是卡塔尔和霍尔木兹那组“4 到 5 天”被后续帖文写成有结果，而且欧佩克+周日真的按 LiveSquawk 转述的那样维持产量、油价继续收。黄金在这条路径上不会自动上涨：Kitco 转述的 Haworth 把金价反弹的条件写成战争结束，Keith 在金价仍高于 4000 美元时维持看空。

中期选举还没投。DeItaone 写美加钢和汽车关税的谈判想赶在 11 月 3 日之前，这是日历，不是周二的方向：[帖](https://x.com/DeItaone/status/2114801784833335515)。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照美东 9:30 的开盘。它不决定仓位大小。

**开盘前只核对五样东西。** 期货还在不在 DeItaone 写下的标普大约涨 0.3%、纳指大约涨 0.5%，还是回到 First Squawk 那次跌 0.2% 和跌 0.5%；EWZ 大约 20% 的缺口是收敛，还是把周一没收进美股的跌幅带进周二；Meta 盘前大约跌 0.5% 的发行，开盘后交易的是 625 美元和英伟达的 30 亿美元，还是 950 亿美元总额里还没定价的部分；布伦特是停在 115.81 美元的结算附近，还是重新报价到 116 以上；HYG 和 CoreWeave 的认沽有没有偏离 SpotGamma 周五的读数。五样里巴西和信用变差、油价重新上涨，这些帖给出的默认顺序是融资敏感的 neocloud 和已经在跌的软件，低于周一领涨的半导体和仍被写成有收入的可口可乐、UPS。巴西留在当地、油价停在结算价、S-1 被当成风险偏好，默认顺序掉过头来：周一已经涨了 2.8% 的半导体指标高于去追 EWZ 的缺口。

**已经公开的方向，按账号而不是按共识。**

- Gary Black：盘前股票小幅走高，10 年期 4.98%，比特币 7.97 万美元，布伦特 117 美元，黄金和白银下跌。他等待明天偏鹰的按兵不动。他的个股句子是特斯拉在 SpaceX 合并猜测里上涨，不是指数目标。
- Keith McCullough：巴西是周一亏损的来源。布伦特 116 美元被他写成通胀周期新高。黄金和白银维持看空，美元维持看多。曲线走平，债券波动率没有变化。人工智能放在 Quad 4，石油放在 Quad 2。零售投资者篮子年初至今跌 11.2%。Hedgeye 主号在前 100 之外，Felix 关于 neocloud 杠杆的话在那边。
- El-Erian：巴西跌幅的量级是共识错误。明天按住，措辞偏鹰，异议可能有。法国信心是 2013 年以来最低。韩国和中国的数据被他用来提醒电子和半导体仍在拉动增长。
- Robin Brooks，线外：这次会议大约 3 个基点，发布会大致中性，12 月加息留在桌面上。法国利差的套息清洗已经结束。
- Nick Timiraos：这场会的裂缝是谁替委员会说话。他没有写加息或降息。
- Kobeissi：巴西 10 年期推向 16%，波动率指数却在跌；杠杆 ETF 和零售期权的流入是他们写下的事实。他们没有给周二的标普目标。
- Charlie Bilello：Anthropic 上半年的六行数字是这份日报里最完整的一页。住房是纪录低的待完成销售和 2012 年以来最差的建筑商信心。工资跑输物价是 2023 年以来第一次。
- Eric Balchunas：EWZ 跌 20%、成交约 100 亿美元是价格和成交事实。持有 Anthropic 的 ETF 出现流入，他把它写成 SpaceX 之后的又一次。
- Bespoke，线外：EWZ 的 10% 跌幅次数是纪录。标普成分股里站上 50 日均线的比例回到 60%。半导体 ETF 仍在 200 日均线上方。今早的“三击”名单里有康宁、可口可乐、Polaris 和 SoFi。
- Javier Blas，线外：沙特原油出口在 10 月前 22 天回到战前的每天 700 万桶以上。这是实物，不是油价目标。
- SpotGamma，线外：CoreWeave 的下行没有按信用泄漏来定价。这是周五收盘的偏度，窗口内没有更新。
- Chamath：Ant 是一门了不起的生意。没有目标价。
- Cramer：计算力里除了马斯克还没有人按该有的方式变现，希望亚马逊有好消息；博通的交易因为他眼里的 Hock Tan 才成立。StockMKTNewz 另外转述他警告大规模 IPO 和增发会从股市抽走资金。那是转述，不是他本账号的原帖：[转述](https://x.com/StockMKTNewz/status/2114846078772170923)。
- Peter Schiff：出口价格和住房的句子是通胀和冻结的需求同时存在。他没有给周二的金价。
- Burry：机械买盘对上涨无感，对下跌的反应没有先例。这是结构，不是点位。

**财报的顺序。** 先看已经写进价格的发行和文件：Meta 的 625 美元、英伟达的 30 亿美元、Anthropic 的上半年调整后利润和净亏损、博通的 630 亿美元。再看今天已经出来的可口可乐、UPS、PayPal、波音、康宁、SoFi、自由港。然后才是 Bespoke 和 StockMKTNewz 点名的周二收盘后：Visa、恩智浦、希捷、Robinhood。Alphabet、微软、亚马逊仍是 First Squawk 和 Gary Black 写在本周后面的名字，抓取结束时还没到点。

**明确留在观察、不放进计划的东西。** fundstrat、Gundlach、Damodaran、Cathie Wood 本人、Dalio、Cuban、Hindenburg 和多家银行官方账号这次没有可引用的新判断。Ackman 的那句没有对象。Pompliano 没有方向。Deutsche Bank 的时间线没有读到。彭博主号的时间线仍不完整，商业账号的 197 条是下限。SpotGamma 的偏度停在周五。Tavi Costa 发了一篇巴西笔记的链接，帖文正文没有写出结论，这里不替他总结：[帖](https://x.com/TaviCosta/status/2114804860684321209)。

## 帖文索引

周一收盘与盘前：[标普 7677.10](https://x.com/FirstSquawk/status/2114809922248646785)、[纳指 100 与半导体](https://x.com/FirstSquawk/status/2114818707809878271)、[期货涨 0.3%](https://x.com/DeItaone/status/2115032523910623495)、[期货曾跌 0.2%](https://x.com/FirstSquawk/status/2114990884836286559)、[Gary 的盘前](https://x.com/garyblack00/status/2115016452516270335)、[收盘失衡](https://x.com/financialjuice/status/2114807008469688576)。

巴西：[跌 30%](https://x.com/KobeissiLetter/status/2114762014354714958)、[收益率 16%](https://x.com/KobeissiLetter/status/2114785608312967621)、[跌超 18%](https://x.com/YahooFinance/status/2114821109870653557)、[收盘 13.9%](https://x.com/Investingcom/status/2114842673622200789)、[EWZ](https://x.com/EricBalchunas/status/2114827178311602642)、[共识错误](https://x.com/elerianm/status/2114771487924367576)、[放弃宣布无效](https://x.com/business/status/2114885775934267868)。

Anthropic 与信用：[上半年六行](https://x.com/charliebilello/status/2114879002053693669)、[807 亿标题](https://x.com/Investingcom/status/2114763002360520758)、[630 亿](https://x.com/Reuters/status/2114897412586168771)、[Meta 625 美元](https://x.com/StockMKTNewz/status/2115046396252312011)、[投资级纪录](https://x.com/business/status/2114849612628361586)、[CoreWeave](https://x.com/carlquintanilla/status/2114766698318303342)、[零售期权](https://x.com/KobeissiLetter/status/2114881746621575597)。

油、黄金与美联储：[WTI 结算](https://x.com/financialjuice/status/2114786993620365496)、[布伦特 116](https://x.com/KeithMcCullough/status/2115012383827492953)、[沙特出口](https://x.com/JavierBlas/status/2115041611461632085)、[按住且偏鹰](https://x.com/elerianm/status/2115049021177745820)、[3 个基点](https://x.com/robin_j_brooks/status/2115012697787887934)、[沃什少说](https://x.com/NickTimiraos/status/2115031082403844333)、[黄金在 4000 上方](https://x.com/business/status/2114899993593008606)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-10-27 抓取时的公开读数。原创条数是北京时间当天窗口内、按帖文编号去重后的原创帖，回复不计入。彭博商业账号的 197 是分页下限，最老一条仍在 10 月 26 日 21:15 UTC。《经济学人》的 80 停在窗口起点附近。德意志银行的 0 是读取失败。彭博主号的 0 来自一条对不上发帖密度的时间线。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,434,450 | 223 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,319,432 | 80 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,278,755 | 52 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,323,117 | 34 |
| 5 | [@business](https://x.com/business) | 10,485,531 | 197 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,561,054 | 0 |
| 7 | [@FT](https://x.com/FT) | 7,102,927 | 55 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,259,040 | 66 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,423,401 | 5 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,645,852 | 32 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,570,724 | 2 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,423,964 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,362,659 | 35 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,434,486 | 14 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,421,084 | 24 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,038,670 | 1 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 2,999,923 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,700,113 | 6 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,558,020 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,507,743 | 9 |
| 21 | [@chamath](https://x.com/chamath) | 2,478,782 | 1 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,439,354 | 3 |
| 23 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,677 | 24 |
| 24 | [@michaeljburry](https://x.com/michaeljburry) | 2,133,396 | 1 |
| 25 | [@YahooFinance](https://x.com/YahooFinance) | 2,073,715 | 17 |
| 26 | [@markets](https://x.com/markets) | 2,045,843 | 0 |
| 27 | [@DeItaone](https://x.com/DeItaone) | 1,968,099 | 33 |
| 28 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,771,979 | 2 |
| 29 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,146 | 25 |
| 30 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,735,300 | 2 |
| 31 | [@NYSE](https://x.com/NYSE) | 1,699,282 | 5 |
| 32 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,693,368 | 0 |
| 33 | [@theinformation](https://x.com/theinformation) | 1,608,585 | 18 |
| 34 | [@federalreserve](https://x.com/federalreserve) | 1,599,666 | 1 |
| 35 | [@Investingcom](https://x.com/Investingcom) | 1,532,504 | 29 |
| 36 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,508,743 | 3 |
| 37 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,469,574 | 13 |
| 38 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,065 | 3 |
| 39 | [@Bloomberg](https://x.com/Bloomberg) | 1,351,395 | 0 |
| 40 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,350,875 | 2 |
| 41 | [@TheStreet](https://x.com/TheStreet) | 1,229,111 | 57 |
| 42 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,194,949 | 6 |
| 43 | [@Stocktwits](https://x.com/Stocktwits) | 1,192,891 | 4 |
| 44 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,183,863 | 0 |
| 45 | [@USTreasury](https://x.com/USTreasury) | 1,163,601 | 1 |
| 46 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,160,427 | 15 |
| 47 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,156,298 | 1 |
| 48 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,143,347 | 1 |
| 49 | [@elerianm](https://x.com/elerianm) | 1,118,161 | 5 |
| 50 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,112,834 | 21 |
| 51 | [@BlackRock](https://x.com/BlackRock) | 1,081,079 | 0 |
| 52 | [@Downtown](https://x.com/Downtown) | 1,043,651 | 0 |
| 53 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,224 | 28 |
| 54 | [@financialjuice](https://x.com/financialjuice) | 955,348 | 170 |
| 55 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,643 | 0 |
| 56 | [@tradingview](https://x.com/tradingview) | 906,580 | 0 |
| 57 | [@BloombergTV](https://x.com/BloombergTV) | 893,103 | 9 |
| 58 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 889,724 | 0 |
| 59 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,720 | 8 |
| 60 | [@charliebilello](https://x.com/charliebilello) | 874,191 | 5 |
| 61 | [@axios](https://x.com/axios) | 861,438 | 28 |
| 62 | [@jpmorgan](https://x.com/jpmorgan) | 859,528 | 0 |
| 63 | [@Citi](https://x.com/Citi) | 853,428 | 0 |
| 64 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 849,767 | 11 |
| 65 | [@HindenburgRes](https://x.com/HindenburgRes) | 848,581 | 0 |
| 66 | [@themotleyfool](https://x.com/themotleyfool) | 840,878 | 1 |
| 67 | [@ecb](https://x.com/ecb) | 828,575 | 2 |
| 68 | [@ARKInvest](https://x.com/ARKInvest) | 822,427 | 2 |
| 69 | [@SECGov](https://x.com/SECGov) | 810,467 | 0 |
| 70 | [@biancoresearch](https://x.com/biancoresearch) | 791,777 | 0 |
| 71 | [@markminervini](https://x.com/markminervini) | 767,173 | 0 |
| 72 | [@MorganStanley](https://x.com/MorganStanley) | 757,842 | 0 |
| 73 | [@CNBCnow](https://x.com/CNBCnow) | 752,268 | 0 |
| 74 | [@morganhousel](https://x.com/morganhousel) | 726,800 | 0 |
| 75 | [@TrendSpider](https://x.com/TrendSpider) | 719,356 | 23 |
| 76 | [@CMEGroup](https://x.com/CMEGroup) | 712,033 | 1 |
| 77 | [@Nouriel](https://x.com/Nouriel) | 702,910 | 0 |
| 78 | [@fundstrat](https://x.com/fundstrat) | 674,596 | 0 |
| 79 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 673,639 | 6 |
| 80 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 647,104 | 0 |
| 81 | [@LukeGromen](https://x.com/LukeGromen) | 638,935 | 3 |
| 82 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,847 | 0 |
| 83 | [@EricBalchunas](https://x.com/EricBalchunas) | 629,665 | 6 |
| 84 | [@garyblack00](https://x.com/garyblack00) | 584,398 | 1 |
| 85 | [@dampedspring](https://x.com/dampedspring) | 579,317 | 4 |
| 86 | [@Cboe](https://x.com/Cboe) | 578,823 | 3 |
| 87 | [@Barchart](https://x.com/Barchart) | 577,686 | 5 |
| 88 | [@FirstSquawk](https://x.com/FirstSquawk) | 574,906 | 242 |
| 89 | [@TruthGundlach](https://x.com/TruthGundlach) | 574,170 | 0 |
| 90 | [@MadMoneyOnCNBC](https://x.com/MadMoneyOnCNBC) | 543,478 | 0 |
| 91 | [@AswathDamodaran](https://x.com/AswathDamodaran) | 521,035 | 0 |
| 92 | [@BofA_News](https://x.com/BofA_News) | 518,256 | 0 |
| 93 | [@carlquintanilla](https://x.com/carlquintanilla) | 516,762 | 3 |
| 94 | [@LiveSquawk](https://x.com/LiveSquawk) | 506,442 | 50 |
| 95 | [@UBS](https://x.com/UBS) | 499,471 | 0 |
| 96 | [@NickTimiraos](https://x.com/NickTimiraos) | 493,936 | 1 |
| 97 | [@NikkeiAsia](https://x.com/NikkeiAsia) | 489,423 | 53 |
| 98 | [@KeithMcCullough](https://x.com/KeithMcCullough) | 479,046 | 30 |
| 99 | [@Fxhedgers](https://x.com/Fxhedgers) | 472,064 | 1 |
| 100 | [@MacroAlf](https://x.com/MacroAlf) | 465,689 | 0 |
