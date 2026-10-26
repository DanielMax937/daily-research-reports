# 美股 Twitter 观点日报 · 2026-10-26

美股现货还没开盘。到北京时间 10 月 26 日 20:10、美东大约早上 8:10 为止，时间线上能对上的是三件同时发生的事：卢拉赢下巴西决选，巴西资产在盘前被砸出熔断级别的缺口，美股期货却因为特朗普说今天不打伊朗而维持上涨；AI 的钱还在流向已经有收入的那一侧，Meta 抛出股票融资、SpaceX 用租赁去拿 400 亿美元的 GPU，neocloud 被马斯克写成要大批死去；周三是沃什任内的又一次议息，高盛把加息放在 12 月，垃圾债利差已经宽过 2022 年的高点。

下面每一条归纳都附有帖文链接。盘前百分比和当地股市跌幅不要互相替换。媒体标题里没有写出的公司名和目标价，这里不补。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-10-26**。触发时刻约 12:05 UTC，时间线补抓到 **约 12:10 UTC（北京时间 20:10，美东 8:10）**。观察窗口是 **2026-10-25 16:00 UTC 至抓取结束**，也就是北京时间周一零点到晚上 8 点 10 分。美股现货 9:30 才开盘，所以下面的指数涨跌都是期货或盘前，不是收盘。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。公开趋势接口只返回了 6 条：Robyn、Nicki、`#CryptoNews`、`#100DaysofDeception`、Candiace、多伦多丰业银行球馆。里面没有标普、纳指或个股话题。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数刚好落在前 100 之外的市场账号。它不是全站每一条提及。
- 不存在官方的“美股 Top 100”。样本是金融媒体、宏观、投资者、交易员、交易所和投行账号，成功读到粉丝数的有 **222** 个，再按抓取当时的粉丝数取前 100。这次的截止在《巴伦周刊》（约 40.8 万粉）。基金策略的 Tom Lee 账号、Gundlach、Josh Brown、Mark Minervini、芝商所和 StockMKTNewz 排进了前 100。Javier Blas 的粉丝数卡在线外一点点。Bespoke、Detrick、SpotGamma、Steno、Benzinga、Seeking Alpha、Kitco 仍在线外，引用时会写明。排序不代表预测准确度。
- 100 个账号里，**56 个**在窗口内有去重后的原创帖，合计 **1173** 条。First Squawk 读到 195 条后仍停在窗口打开后约 5 分钟，条数是下限。德意志银行的时间线返回失败，表里的 0 不是确认沉默。彭博主号可见时间线的最新一条仍停在 10 月 12 日，和它平时的发帖密度对不上，0 同样不能当成确认沉默。
- 窗口内确认没有市场原创的包括 Jim Cramer、Cathie Wood、ARK 官方账号、Ray Dalio、Peter Schiff、Nick Timiraos、Luke Gromen、Alf、Aswath Damodaran、Hedgeye 官方账号、高盛官方账号、摩根大通官方账号、美联储官方账号、Tom Lee 的 fundstrat 账号、Gundlach。Bill Ackman 写的是选举短评和纽约州检察长，不是仓位。Anthony Pompliano 的两条是球赛和早安。Raoul Pal 在推自己的书。Keith McCullough 有帖，Hedgeye 主号没有。

## 开盘前，期货和巴西不在讲同一件事

周日晚间期货开盘时，Kobeissi 记下的是特朗普宣布今天不打击伊朗之后的第一组报价：标普期货涨 0.5%，纳指期货涨 0.7%，道指期货涨 0.4%，WTI 跌 1.5%，布伦特跌 1.0%，天然气跌 2.5%，并称标普离新高大约还有 3%：[帖](https://x.com/KobeissiLetter/status/2114490147773235247)。同一句“今天不打”也出现在 First Squawk 和 Investing.com：[特朗普](https://x.com/FirstSquawk/status/2114388286173298745)、[Investing.com](https://x.com/Investingcom/status/2114420712509264146)。到美东早上，DeItaone 的期货读数仍是标普涨 0.4%、纳指 100 涨 0.5%、道指涨 0.5%：[帖](https://x.com/DeItaone/status/2114687217897787568)。Gary Black 在更早一点的盘前写成标普涨 0.3%、纳指涨 0.2%，10 年期收益率 4.98%，比特币 8.01 万美元，黄金和白银在涨：[帖](https://x.com/garyblack00/status/2114650044812992942)。《华尔街日报》市场账号的标题是期货和美债大致稳住、巴西资产在滑：[帖](https://x.com/WSJmarkets/status/2114653750937759773)。

巴西是另一张表。卢拉拿下第四任期。CNBC 写的计票是有效票 51.8% 对弗拉维奥·博索纳罗 48.2%：[帖](https://x.com/CNBC/status/2114517041927327996)。Unusual Whales 写的是 51.76% 对 48.24%、相差 435 万票、99.77% 已计，并注明卢拉是 1989 年以来第一个首轮落后、决选翻盘的人：[帖](https://x.com/unusual_whales/status/2114554104710312112)。Kobeissi 补的是选前隐含胜率一度低到 10%：[帖](https://x.com/KobeissiLetter/status/2114518806370599401)。博索纳罗拒绝承认，并要求法院以计票问题宣布决选无效：[Kobeissi](https://x.com/KobeissiLetter/status/2114539126561079300)、[路透](https://x.com/Reuters/status/2114616769679966640)、[zerohedge](https://x.com/zerohedge/status/2114533704009683428)。

跌幅要分成当地股市和美国上市的 ETF。Kobeissi 写巴西股市跌 20%：[帖](https://x.com/KobeissiLetter/status/2114560008897671476)。线外的 Bespoke 写 iShares 巴西 ETF EWZ 盘前跌 25.4%，价格回到 2025 年底：[帖](https://x.com/bespokeinvest/status/2114680755829764556)。The Stalwart 先写 Hyperliquid 上的巴西永续合约跌过 5%、再跌过 10%，然后写 EWZ 盘前跌 27%：[5%](https://x.com/TheStalwart/status/2114491887985864931)、[10%](https://x.com/TheStalwart/status/2114503723271753903)、[EWZ](https://x.com/TheStalwart/status/2114659539681169655)。Eric Balchunas 写一只在日本上市的巴西 ETF 当天跌 15%、成交高于平均，并说 EWZ 会有自己的一天：[帖](https://x.com/EricBalchunas/status/2114622640610783691)。Barchart 的图说是 EWZ 在卢拉胜选后下坠：[帖](https://x.com/Barchart/status/2114571913481908304)。芝商所写，亚太时段巴西雷亚尔期货名义成交已经大约 24 亿美元，是该时段新纪录：[帖](https://x.com/CMEGroup/status/2114665847637549331)。

投行的情景和已经打出来的价格要分开。zerohedge 转述高盛：今天可能看到美元对雷亚尔上涨 10%、长端利率上升 200 个基点、信用利差走阔 30 到 40 个基点、股票跌 15%，熔断会很快触发，之后更多是按指令、受熔断限制的交易：[帖](https://x.com/zerohedge/status/2114549663554793937)。同一账号转述法兴：雷亚尔可能再跌 8% 到 10%：[帖](https://x.com/zerohedge/status/2114529365228671365)。DeItaone 转述的是摩根士丹利更后面的一版：巴西股票跌 20% 到 30%，美元对雷亚尔看到 5.60、财政担心加重则到 6.00，银行间利率再受 300 到 400 个基点压力，点名 EWZ、巴西石油、淡水河谷：[帖](https://x.com/DeItaone/status/2114682043044892785)。彭博商业账号的一篇观点文章标题是先别卖巴西股票，政治版图变了，财政压力会逼卢拉更务实：[帖](https://x.com/business/status/2114645753599496284)。Lyn Alden 只写了一句：价值投资者在看今晚巴西选举的抛售：[帖](https://x.com/LynAldenContact/status/2114540400006607212)。大豆是外溢的第一条商品。彭博商业账号写，卢拉胜选抬高了巴西和中国走得更近的预期，芝加哥大豆期货跌到两个月低点：[帖](https://x.com/business/status/2114561440585523360)。

## 观点分成四组

### 1. 今天不打伊朗，油在退，袭击和谈判还在同一天

油价从近六个月高位往下走，帖文给出的是百分比，不是新的收盘价。路透的标题是油价从近六个月高点回落，因为市场在赌伊朗战事会缓和：[帖](https://x.com/Reuters/status/2114621861044564307)。CNBC 的标题是油价跌超 2%，交易员在称沙特遇袭风险和需求破坏：[帖](https://x.com/CNBC/status/2114588202723930278)。《华尔街日报》市场账号先写技术性回调，再写交易员在权衡美伊外交和沙特遇袭：[回调](https://x.com/WSJmarkets/status/2114542732337127677)、[外交与袭击](https://x.com/WSJmarkets/status/2114625408272347284)。《金融时报》的标题是油价因卡塔尔斡旋而下跌：[帖](https://x.com/FT/status/2114621460354318601)。

袭击没有从时间线上消失。路透写胡塞称打击了沙特东西原油泵站和利雅得机场：[帖](https://x.com/Reuters/status/2114616217444991105)。FinancialJuice 的用词更窄：胡塞称用无人机打了东西泵站，沙特方面没有立即确认：[帖](https://x.com/financialjuice/status/2114545545742279135)。谈判的名单是具体的。粉丝数刚好落在前 100 之外的 Javier Blas 写沙特国防大臣、巴基斯坦陆军参谋长和土耳其情报负责人前往德黑兰，对象包括总统佩泽希齐扬和国家安全秘书礼萨伊：[帖](https://x.com/JavierBlas/status/2114606899492683997)。彭博商业账号用的是同一组行程，目的写成给谈判续命、避免战事扩大：[帖](https://x.com/business/status/2114626875406286866)。First Squawk 另有卡塔尔代表团当天已在德黑兰斡旋，以及伊朗官员称障碍在华盛顿不接受其要求：[代表团](https://x.com/FirstSquawk/status/2114394531164819631)、[障碍](https://x.com/FirstSquawk/status/2114395196863782912)。DeItaone 写巴基斯坦陆军参谋长阿西姆·穆尼尔抵达德黑兰，参加与伊朗的第一次麦加协议会议：[帖](https://x.com/DeItaone/status/2114669145350406208)。zerohedge 的标题是土耳其开始批准与沙特、巴基斯坦的麦加防务协议：[帖](https://x.com/zerohedge/status/2114597925170856151)。

供给的实物账和油价方向也不一致。Javier Blas 写美国中央司令部更新的数字：入夏以来经霍尔木兹的石油流量约 15 亿桶，近几周折合每天超过 1450 万桶；他注明这不含阿联酋富查伊拉管道和沙特东西管道：[流量](https://x.com/JavierBlas/status/2114434374972088659)、[不含绕行](https://x.com/JavierBlas/status/2114436308064223360)。同一天他的图说是，Vortexa 的在途石油升到历史新高，原因包括中东流量、船对船转运，以及进口商绕开中东以后的更长航线：[帖](https://x.com/JavierBlas/status/2114688708012372402)。新加坡将从明年下半年起在岩洞里储存沙特石油，彭博和《金融时报》都写了这是应对美伊战争中断的安排：[彭博](https://x.com/business/status/2114548872789799194)、[FT](https://x.com/FT/status/2114627688832827872)。DeItaone 转述美国银行：红海航运恢复到正常水平的 65%，9 月是 50%，但油轮日租金仍高达 65 万美元，干散货运价同比涨 31%：[帖](https://x.com/DeItaone/status/2114653814267449681)。阿联酋外海的溢油在扩大，乌姆盖万、沙迦和拉斯海玛的海滩被关，DeItaone 写专家把它连到上月一艘据称被弹丸击中的油轮，原因未证实：[帖](https://x.com/DeItaone/status/2114649984125579272)。

天然气分成两个市场。Javier Blas 写美国天然气基准掉到大约每百万英热 2.5 美元，接近两年新低，并用了“能源危机？什么危机？”：[帖](https://x.com/JavierBlas/status/2114621771085172911)。《华尔街日报》市场账号的标题是欧洲天然气处于四年高位，冬季供应担忧还在：[帖](https://x.com/WSJmarkets/status/2114656033809313968)。First Squawk 另有一条标题，欧洲天然气期货升到 2022 年以来最高，而原油期货周一早段跌了大约 1%，并称没有立刻的催化剂：[帖](https://x.com/FirstSquawk/status/2114510507155902622)。Keith McCullough 把原油的早盘下跌写成对上周布伦特创下通胀周期新高之后的修正，并称自己这边天然气已经出来了：[原油](https://x.com/KeithMcCullough/status/2114650591872049496)、[天然气](https://x.com/KeithMcCullough/status/2114650219283435728)。

HSBC 的配置和“油价在跌”放在一起。DeItaone 和 Investing.com 都写下：全球股票从最大超配降到中性，黄金超配也下调，原油升到明确超配：[股票](https://x.com/DeItaone/status/2114650917966320030)、[黄金与原油](https://x.com/DeItaone/status/2114654012494565656)、[Investing.com](https://x.com/Investingcom/status/2114673739069538770)。First Squawk 有一条没有署名的标题，冲突若重启，全球油价可能冲过 150 美元：[帖](https://x.com/FirstSquawk/status/2114415979153539151)。这是标题，不是收盘预测。《华尔街日报》另有一条没有在正文里写出公司名的帖，全年布伦特假设从 80 美元上调到 90 美元，炼油利润从每桶油当量 13 美元上调到大约 25 美元：[帖](https://x.com/WSJ/status/2114622034294497635)。

### 2. 借得到钱的在加杠杆，借不到的被写成要消失

马斯克的两句话在这些账号里被分开转述。一句是债务市场几乎已经切断任何没有数据中心以外实质收入的公司。Kobeissi 的原话转述是 neocloud 将看到“孔雀鱼级别的死亡和整合”：[帖](https://x.com/KobeissiLetter/status/2114522987018031174)。DeItaone 点了 CoreWeave、Nebius、IREN、Applied Digital、Cipher：[帖](https://x.com/DeItaone/status/2114654789711634736)。Business Insider 引用了同一句“有些能活下来，但不会很多”：[帖](https://x.com/BusinessInsider/status/2114593140887769191)。CNBC 的标题是 neocloud 股票下跌，马斯克说 200 多家面临这种结局：[帖](https://x.com/CNBC/status/2114640836465991785)。Business Insider 写 CoreWeave 和 Nebius 过去一个月都跌了超过 30%：[帖](https://x.com/BusinessInsider/status/2114688944566681994)。《巴伦周刊》的标题是这两家最大的玩家仍可能挺过去，正文没有在帖文里写出理由：[帖](https://x.com/barronsonline/status/2114678682795053309)。彭博商业账号写，华尔街策略师警告 AI 云计算股票的下跌会蔓延到科技交易的其他角落，并可能把美股拖回 6 月低点：[帖](https://x.com/business/status/2114678473243451463)。The Information 仍把 CoreWeave 写成整场 AI 建设能不能融到资的风向标，投资者在押“不能”：[帖](https://x.com/theinformation/status/2114401651402342636)。

另一句是 SpaceX 自己拿到了钱，但“已经关闭”和“还没关闭”在窗口里都出现了。CNBC 先按马斯克的帖写成 400 亿美元债务已经关闭，用于买 GPU，并称资金预计在 2027 年一二季度到位：[帖](https://x.com/CNBC/status/2114567736789500082)。彭博商业账号随即写，熟悉此事的人说截至周日各方仍在谈价格，交易还没有关闭：[帖](https://x.com/business/status/2114526226341638145)。到抓取结束前，DeItaone 和 LiveSquawk 改用美国证交会文件的口径：SpaceX 与 Apollo 达成有约束力的主融资租赁承诺，Apollo 购买 GPU 舱并租给 SpaceX，计划本金合计 400 亿美元，预计 2026 年底前关闭：[DeItaone](https://x.com/DeItaone/status/2114688952686805491)、[LiveSquawk](https://x.com/LiveSquawk/status/2114689409266122981)。盘前报价是 SpaceX 股票涨 1.2%：[帖](https://x.com/DeItaone/status/2114655332677177480)。Bernstein 把目标价从 248 美元调到 268 美元：[帖](https://x.com/DeItaone/status/2114666385255108763)。《巴伦周刊》另写，SpaceX 自上市以来已经迅速累积了大约 650 亿美元更多债务：[帖](https://x.com/barronsonline/status/2114679798190543110)。线外的 The Transcript 贴出的公司口径是，AI 算力回本有可能在 2027 年缩短到六个月，说话人说这不是需求问题，六个月回本“不是不可能”：[帖](https://x.com/TheTranscript_/status/2114462023732064573)。

Meta 的融资数字在标题里有三种加法，零件是同一套。FinancialJuice 写 Meta 通过远期销售发行 225 亿美元 A 类普通股，并发行 2.5 亿份 A 系列存托股；英伟达、AMD、博通将买入最多 50 亿美元 A 类股票：[发行](https://x.com/financialjuice/status/2114673261829316918)、[芯片商](https://x.com/financialjuice/status/2114674483449544837)。DeItaone 把 225 亿普通股和 125 亿可转换优先股加成 350 亿美元，并写 2027 年另有 600 亿美元股票销售计划，2026 年资本开支目标仍是 1350 亿到 1450 亿美元：[帖](https://x.com/DeItaone/status/2114673499650371710)。zerohedge 的快讯是发行 225 亿美元 A 类，以及可能出售至多 600 亿美元 C 类：[A 类](https://x.com/zerohedge/status/2114676322161074330)、[C 类](https://x.com/zerohedge/status/2114676482274390064)。《金融时报》的突发标题是 950 亿美元股票发行，芯片商作为基石：[帖](https://x.com/FT/status/2114678996352799131)。线外的 The Transcript 把 950 亿写成 350 亿发行加计划中的 600 亿随时发行，并写 Meta 盘前涨 2%：[帖](https://x.com/TheTranscript_/status/2114687804844482577)。DeItaone 随后写 Meta 盘前转涨，最后涨 2.2%：[帖](https://x.com/DeItaone/status/2114680082497478886)。稀释和有人接盘，在这些帖里是同一条新闻。

Anthropic 被写成周一上午要交表，抓取结束时表还没到点。DeItaone 转述福克斯商业频道：S-1 在美东上午 9 点发布，IPO 可能在 11 月 19 日到 20 日：[S-1](https://x.com/DeItaone/status/2114680761848897631)、[时间窗口](https://x.com/DeItaone/status/2114688340054208631)。彭博商业账号写 Anthropic 计划周一公开递交，规模可能是纪录：[帖](https://x.com/business/status/2114689790700408938)。The Information 写员工绝大多数相信 AI 会在 2030 年前做出诺贝尔奖级别的突破，华尔街远没有这么信：[帖](https://x.com/theinformation/status/2114394064829214897)。路透的评论播客仍在问 neocloud 股票和无担保债的下跌会不会再打到 Anthropic 放缓的增长：[帖](https://x.com/Reuters/status/2114635684539511037)。Axios 写 Claude 绕过付费墙读取了佐治亚州选民数据，福克斯商业频道的标题改成 Anthropic 确认读取的是公开数据：[Axios](https://x.com/axios/status/2114485266555523538)、[福克斯](https://x.com/FoxBusiness/status/2114514907563442411)。

Chamath 从拿地的一侧写 2027 年。他称 neocloud 组织混乱、资本不足，超大规模云厂商官僚，现有管道的延误会在 2027 年让人意外；被买下但赚不回资本成本、或者积在库存里的算力会比现在的预测多。他点名的例外只有“一个”，帖文里没有写出名字。他还写，如果 Anthropic 的 S-1 里那条“对方说没有算力给它们”的传闻为真，就是超大规模云厂商已经在保自己的证据：[帖](https://x.com/chamath/status/2114389987563381004)。后续两条回复把德州矿权豁免、东德州的法律风险、电网排队要更早交资本金，以及 neocloud 和对家合同里的违约金，写成最后一关：[德州与电力](https://x.com/chamath/status/2114398862836379727)、[违约金](https://x.com/chamath/status/2114402667082752044)。

信用是这组观点的价格。Kobeissi 写美国 CCC 及以下高收益债有效收益率到 18.0%，为 2020 年疫情以来最高，六个月上升 500 个基点；相对国债的利差 13.4%，为 2020 年 7 月以来最宽，六个月走阔 464 个基点，已经超过 2022 年熊市 12.8% 的高点：[帖](https://x.com/KobeissiLetter/status/2114455149670228337)。Keith McCullough 写自己对高收益和信用风险维持看空，利差处于突破：[帖](https://x.com/KeithMcCullough/status/2114645520706900232)。zerohedge 的标题是高盛承认自己的信用空头情形还不够空，AI 压力打进了债券：[帖](https://x.com/zerohedge/status/2114484677553574120)。Carl Quintanilla 引用的一段把名字写具体了：拉姆研究、GE Vernova、Vertiv、Bloom Energy 从 6 月下旬高点跌了 30% 到 35%，投资级利差走阔 40 到 60 个基点：[帖](https://x.com/carlquintanilla/status/2114422228850741387)。MarketWatch 的标题是摩根士丹利说半导体的支撑位可能比现价再低 15%：[帖](https://x.com/MarketWatch/status/2114645519607689444)。《财富》写数据中心业主需要在这个十年结束前累计创造 8.5 万亿美元收入，才对得起这些投资：[帖](https://x.com/FortuneMagazine/status/2114492207474585913)。线外的 Benzinga 标题是超大规模云厂商到十年末可能面临每年 5000 亿到 1 万亿美元折旧：[帖](https://x.com/Benzinga/status/2114688996370424264)。

需求没有被写成消失。Kobeissi 写马来西亚 9 月出口同比增 54.5%，电气电子产品增 69.2%，对台湾出口增 175.2%，并把这称为 AI 投资带起来的亚洲贸易：[帖](https://x.com/KobeissiLetter/status/2114400418524729698)。日经亚洲写软银计划在马来西亚做 500 亿美元 AI 投资，这是总理的说法：[帖](https://x.com/NikkeiAsia/status/2114405431112003819)。Unusual Whales 转述黑石总裁：投资者不必担心 AI 繁荣变成泡沫：[帖](https://x.com/unusual_whales/status/2114667604577333743)。StockMKTNewz 转述 Tom Lee 说大家“太悲观了”。这是媒体转述，fundstrat 账号窗口内没有对应帖：[帖](https://x.com/StockMKTNewz/status/2114429788995940483)。

### 3. 周三是沃什，12 月才是加息被写进基准的地方

DeItaone 转述高盛：美联储本周维持利率不变，12 月再加 25 个基点。Kalshi 上 10 月维持不变的价格是 93%，加息是 6%：[帖](https://x.com/DeItaone/status/2114652209463922971)。同一账号把沟通难题写到主席 Kevin Warsh 身上：能源价格和 AI 基建需求还在推通胀，暂停之后怎么说，会动到美债收益率、美元和科技股：[帖](https://x.com/DeItaone/status/2114663072073707749)。《巴伦周刊》的标题是交易员预期本周利率停在原地：[帖](https://x.com/barronsonline/status/2114444223382462832)。zerohedge 的标题把沃什和他的班子写成偏鹰的一班人，问的是按住还是加：[帖](https://x.com/zerohedge/status/2114689781149880388)。Investing.com 的日程是周三美东下午 2 点决议和声明，2 点 30 分沃什讲话：[帖](https://x.com/Investingcom/status/2114438312920306073)。

线外的 Ryan Detrick 把日历叠在一起：10 月 28 日历史上往往是全年最好的一天，今年这天是周三，也是议息日。他写下沃什任内标普的议息日跌幅：6 月跌 1.21%，7 月跌 1.52%，9 月跌 0.45%，并问哪一段历史会重复：[帖](https://x.com/RyanDetrick/status/2114534807149371458)。Mark Minervini 发了一张图，问题是标普从这里开始会先做什么，帖文没有给出他的选择：[帖](https://x.com/markminervini/status/2114466231990595816)。

同一周的数据被 Investing.com 列成：周二耐用品订单、消费者信心、新屋销售；周四三季度 GDP、核心 PCE、初请、就业成本指数：[帖](https://x.com/Investingcom/status/2114410520862248972)。线外的圣路易斯联储写，10 月 23 日的即时预测把三季度实际 GDP 年化放在 3.2%，一周前是 2.8%：[帖](https://x.com/stlouisfed/status/2114541529029026052)。同一账号写，截至 10 月 16 日当周的金融压力指数是 -0.63，前一周 -0.72，仍低于 0 所代表的正常压力，但压力在上升：[帖](https://x.com/stlouisfed/status/2114484906344550795)。商业票据余额在截至 10 月 21 日当周升到 1.50 万亿美元，一周增加 226 亿美元：[帖](https://x.com/stlouisfed/status/2114507806699081941)。

高盛对增长的另一面由 DeItaone 转述：2027 年全球增长大体稳定，但能源价格、债券收益率和放慢的 AI 投资在加大下行风险；AI 对就业的影响更明显、通胀预期下降之后，高盛认为央行加息会少于市场现在的定价：[帖](https://x.com/DeItaone/status/2114678717033107849)。Carl Quintanilla 引用高盛：AI 的影响开始溢出科技部门，把 AI 用进常规业务的美国公司占比，已经和就业增长出现统计上显著的负相关：[帖](https://x.com/carlquintanilla/status/2114684511829057661)。

法国债是欧洲这边的对应物。Charlie Bilello 写法国 10 年期收益率升破 5%，为 2002 年以来最高，相对德国的利差回到欧债危机时期的水平：[帖](https://x.com/charliebilello/status/2114437436248097187)。到周一，穆迪维持评级之后，DeItaone 写法国 10 年期收益率下降 5.3 个基点，到 4.9685%：[帖](https://x.com/DeItaone/status/2114622867510112471)。Investing.com 写欧元走高、债券收益率缓和，因为法国避开了降级：[帖](https://x.com/Investingcom/status/2114684427552919902)。ING 仍警告欧元可能因为法国债务进一步下跌，欧元兑美元 1.1206，支撑 1.1180：[帖](https://x.com/DeItaone/status/2114647436182310983)。Gold Telegraph 写拉加德没有排除在下次法国选举前离开欧洲央行：[帖](https://x.com/GoldTelegraph/status/2114623707213938820)。zerohedge 的标题是高盛上调法国 2027 年赤字，并警告欧洲的选举周期会威胁把利差压住的财政整合：[帖](https://x.com/zerohedge/status/2114654547138253136)。DeItaone 另记马克龙的一句：下周六又是有风险的一天：[帖](https://x.com/DeItaone/status/2114685062650167510)。

黄金还在 4000 美元下方。《华尔街日报》市场账号的标题是金价持平、徘徊在每盎司 4000 美元之下：[帖](https://x.com/WSJmarkets/status/2114531417174524304)。Keith 写黄金早盘反弹 0.6%，上周再跌 4.1%：[帖](https://x.com/KeithMcCullough/status/2114651096484385176)。线外的 Kitco 转述 Phil Streible：10 月 22 日中东紧张、油价摸到 100 美元、美元和美债收益率下跌、加息赔率下降，这些通常利好黄金，12 月黄金还是跌了 90 美元，周五跌破 4000，为 7 月中以来最低，大约比 1 月纪录低 30%。他写转折要看经济弱到美联储不能再加息，而不是下一条头条：[帖](https://x.com/KitcoNewsNOW/status/2114676309787812259)。同一账号预告 Jeffrey Christian 讨论黄金跌破 4000、白银跌破 55 美元：[帖](https://x.com/KitcoNewsNOW/status/2114680957164810346)。HSBC 下调黄金超配，见上一节。Unusual Whales 转述的央行购金是 8 月的旧数：全球央行约买 79 吨，为 2022 年前月均 17 吨的四倍多：[帖](https://x.com/unusual_whales/status/2114537749072249296)。

比特币没有新的崩盘帖。Schiff 今天没有发帖。Gary Black 的盘前读数是 8.01 万美元。alphatrends 写周六早上 79420 美元的买单成交，随后在 79756 美元卖掉四分之三，理由是不想亏钱：[成交](https://x.com/alphatrends/status/2114466870208393457)、[卖出](https://x.com/alphatrends/status/2114532857523892317)。

### 4. 指数期货是绿的，底下的分化没有停

El-Erian 的周一短信是：这一周挤着数据、财报和政策，更多注意力在转向某些 AI 板块内部扩大的分化：[帖](https://x.com/elerianm/status/2114662171804385454)。他窗口内的另一条市场相关帖只是记下卢拉连任，没有方向：[帖](https://x.com/elerianm/status/2114517994462417360)。

Liz Ann Sonders 的图说没有展开成交易指令。她写 10 年期收益率和标普的 30 日滚动相关性没那么负了，因为两者最近一起往下：[帖](https://x.com/LizAnnSonders/status/2114679162464297108)。另一张写，有盈利的罗素 2000 今年继续大幅跑赢没有盈利的那一组，去年相反；口径是截至 10 月 23 日、过去 12 个月每股收益大于 0：[帖](https://x.com/LizAnnSonders/status/2114679663586947476)。

Michael Burry 今天没有新的点位。他贴出的一节写，市场下面的机械买盘是阴，阳的那一面是一个阿尔法接近零、贝塔很低、伽马却在纪录的市场；它对上涨无感，对大跌的反应是历史水平两到三倍的混乱，然后在一个月内把恐惧耗尽，比历史纪录快一倍以上。他说人类的恐惧不是这样：[帖](https://x.com/michaeljburry/status/2114607124110356928)。zerohedge 的另一条标题把同一类结构写成 0DTE 交易员压住标普波动率的程度已经超过做市商伽马：[帖](https://x.com/zerohedge/status/2114552626608009384)。线外的 SpotGamma 今天没有帖，昨天的认沽偏度没有被这些账号更新。

银行目标价都是转述，不是这些账号自己的模型。DeItaone 转述摩根士丹利 Michael Wilson：这轮修正会在若干风险出清后结束，近端下行 7100 到 7200，年底基准 8000；三个催化剂是 AI 融资、中期选举和收紧的金融条件，流动性是最近的风险，选举后 6 到 12 个月历史上回报偏强：[帖](https://x.com/DeItaone/status/2114676641888612695)。同一账号转述 Ed Yardeni：接下来的抛售是买点，年底标普 7900，2027 年中 8400，依据是 2027 年每股收益 425 美元；他列出的风险是地缘升级、美联储加息、中期选举和 AI 投资：[帖](https://x.com/DeItaone/status/2114688174949548490)。LiveSquawk 写标普混合盈利增长 29%，连续第三个季度超过 25%，86% 的公司超预期利润，70% 超预期收入；警示是盈利修正动量在放慢，同样的形态出现在 2021 年三季度，两个月后标普见顶、2022 年熊市开始：[帖](https://x.com/LiveSquawk/status/2114674372799606942)。Gary Black 写 2026 年标普盈利预期同比增 33% 撑着估值，但股票风险溢价相对国债倒挂，让他想起 1990 年代末；他预期收益率会随伊朗冲突收场而回落，并对特斯拉保持谨慎，理由是估值、盈利下修和自动驾驶被商品化：[帖](https://x.com/garyblack00/status/2114650044812992942)。

亚洲是 AI 交易的另一条腿。高盛把韩国综指 12 个月目标从 12000 砍到 9000，DeItaone 写指数已从 6 月高点跌 40%、前瞻估值大约 4 倍盈利，高盛仍看到超过 60% 的上行，并称市场把半导体定价得过度悲观：[帖](https://x.com/DeItaone/status/2114665254781161837)。zerohedge 贴出的是同一目标的内部口径：[帖](https://x.com/zerohedge/status/2114506569559781787)。Keith 写韩国当天再跌 1.5%，从 6 月高点累计跌 40%，日本再跌 0.8% 并维持看空趋势，菲律宾再跌 1.5%、他仍做空：[韩国](https://x.com/KeithMcCullough/status/2114648582100009348)、[日本](https://x.com/KeithMcCullough/status/2114647690349068433)、[菲律宾](https://x.com/KeithMcCullough/status/2114649108967256555)。Barchart 写中国向股市注入 1290 亿元人民币（190 亿美元），试图打断历史上最长的连跌：[帖](https://x.com/Barchart/status/2114613144203211009)。日经亚洲的标题是 AI 股票下跌成了中国自力更生策略的痛点：[帖](https://x.com/NikkeiAsia/status/2114463698051838439)。

线外的 Bespoke 用上半年最差的 25 只标普股票做了一个事后组合：消费股和被说成会被 AI 取代的软件，等权买入后下半年涨 34%：[帖](https://x.com/bespokeinvest/status/2114491171141517592)。他们周一的板块帖是通信服务落后，移动运营商、Alphabet 和奈飞靠近六个月低点，迪士尼则在 1 月以来高位：[帖](https://x.com/bespokeinvest/status/2114682816650739969)。

中期选举被 Unusual Whales 收成一张年龄表：《纽约时报》/锡耶纳民调，18 到 29 岁倾向民主党的比例从 2024 年 10 月的 55% 升到 2026 年 10 月的 70%：[帖](https://x.com/unusual_whales/status/2114662571664113707)。同一账号写马斯克在今年中期选举投入 4.46 亿美元自有资金，主要用来保住共和党对国会的控制：[帖](https://x.com/unusual_whales/status/2114672637708267855)。高盛主经纪商的另一条由 Unusual Whales 转述：上周全球对冲基金出现疫情以来最广的一次下跌：[帖](https://x.com/unusual_whales/status/2114658545400463811)。

## 要盯住的五件事

1. **巴西的缺口会不会在美股开盘后还只是巴西的。** 当地股市被写成跌 20%，EWZ 盘前跌 25% 到 27%，雷亚尔期货在亚太时段放量。高盛的草图是股票跌 15%、美元对雷亚尔涨 10%；摩根士丹利的草图是股票跌 20% 到 30%、汇率 5.60 到 6.00。博索纳罗要求宣布无效这件事还没落地。大豆已经先动了。
2. **“今天不打”能撑多久。** 期货的绿色和油价的回落都系在这句话上。同一天的帖里还有胡塞称打了东西泵站、麦加协议国家的人在德黑兰、卡塔尔在斡旋。HSBC 在油价下跌的早上把原油升到明确超配、把股票降到中性。欧洲天然气在四年高位，美国天然气靠近两年低点，两套能源价格不要合成一个方向。
3. **美东上午 9 点的 Anthropic S-1，以及 Meta 的发行结构。** 抓取结束时 S-1 还没到点。Meta 的零件是 225 亿美元 A 类远期销售、可能至多 600 亿美元 C 类、芯片商最多 50 亿美元；950 亿美元是《金融时报》和 The Transcript 的加法，不是另一笔已经宣布的现金。CoreWeave 被继续当成融资风向标。
4. **周三的沃什，以及周四的 GDP 和核心 PCE。** 基准是本周不动、12 月加 25 个基点，Kalshi 上维持不变约 93%。Detrick 记下的是沃什任内此前三次议息日标普都收跌，而 10 月 28 日又是历史上偏强的一天。CCC 利差已经宽过 2022 年高点，Keith 维持信用看空。
5. **韩国综指和法国 10 年期，是美股期货绿盘旁边的两个压力表。** 韩国从 6 月高点跌了 40%，高盛把目标从 12000 砍到 9000，但仍写超过 60% 的上行。法国 10 年期在穆迪维持评级后回到 4.9685%，周日晚上 Bilello 写下的读数是在 5% 上方。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、位置或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 已经在交易的缺口 | EWZ、PBR、VALE、雷亚尔 | Kobeissi：巴西股市跌 20%。Bespoke：EWZ 盘前跌 25.4%，回到 2025 年底。The Stalwart：盘前跌 27%。摩根士丹利经 DeItaone 转述：股票跌 20%–30%，美元对雷亚尔 5.60，财政恶化则 6.00，并点名这三只。高盛经 zerohedge 转述的草图是股票跌 15%、汇率涨 10% | [巴西股市](https://x.com/KobeissiLetter/status/2114560008897671476)、[EWZ 25.4%](https://x.com/bespokeinvest/status/2114680755829764556)、[EWZ 27%](https://x.com/TheStalwart/status/2114659539681169655)、[摩根士丹利](https://x.com/DeItaone/status/2114682043044892785)、[高盛草图](https://x.com/zerohedge/status/2114549663554793937) |
| 仍能借到钱的 AI | SPCX、APO、META、NVDA、AMD、AVGO | SpaceX 与 Apollo 的主融资租赁承诺，计划本金 400 亿美元，盘前股票涨 1.2%，Bernstein 目标价 268 美元。Meta 的 A 类远期销售 225 亿美元，芯片商最多接 50 亿美元，盘前后来涨 2.2%。“已经关闭”的说法被彭博的消息人士改成周日仍在谈价格 | [Apollo 文件](https://x.com/DeItaone/status/2114688952686805491)、[盘前 1.2%](https://x.com/DeItaone/status/2114655332677177480)、[Bernstein](https://x.com/DeItaone/status/2114666385255108763)、[Meta 零件](https://x.com/financialjuice/status/2114673261829316918)、[盘前 2.2%](https://x.com/DeItaone/status/2114680082497478886)、[尚未关闭](https://x.com/business/status/2114526226341638145) |
| 被点名的 neocloud | CRWV、NBIS、IREN、APLD、CIFR | 马斯克的融资切断和“孔雀鱼级别的死亡”由 Kobeissi 和 DeItaone 转述，后者列出这五个代码。CoreWeave 与 Nebius 过去一个月跌超 30%。彭博标题警告云计算的下跌会把美股拖向 6 月低点 | [马斯克](https://x.com/KobeissiLetter/status/2114522987018031174)、[代码](https://x.com/DeItaone/status/2114654789711634736)、[一个月跌幅](https://x.com/BusinessInsider/status/2114688944566681994)、[6 月低点](https://x.com/business/status/2114678473243451463) |
| 周一上午的事件 | Anthropic | 福克斯商业频道经 DeItaone：美东上午 9 点发 S-1，IPO 或在 11 月 19–20 日。抓取结束时这个时点还没到。The Information 写的是员工与华尔街对 2030 年前诺贝尔级突破的信念差 | [S-1](https://x.com/DeItaone/status/2114680761848897631)、[11 月](https://x.com/DeItaone/status/2114688340054208631)、[信念差](https://x.com/theinformation/status/2114394064829214897) |
| 盘前个股 | TSLA、MRNA、VZ、LMT | 巴克莱把特斯拉上调到超配，目标价 450 美元，前值 370，理由包括可能的 SpaceX 合并；盘前涨 1.9%。Gary Black 对特斯拉保持谨慎。Moderna 盘前跌 9.3%，前两日已跌超 18%。Verizon 调整后每股收益 1.31 美元，高于预期的 1.27 或 1.28 美元，收入 343 亿美元低于预期，与亚马逊的 AI 合作价值超过 20 亿美元。摩根士丹利经 CNBC 标题称洛马在新的五角大楼协议后将涨近 40%，帖文没有写出目标价 | [巴克莱](https://x.com/DeItaone/status/2114670677319995530)、[特斯拉盘前](https://x.com/DeItaone/status/2114671554348884181)、[Black](https://x.com/garyblack00/status/2114650044812992942)、[Moderna](https://x.com/DeItaone/status/2114667500830904480)、[Verizon](https://x.com/DeItaone/status/2114673947434201185)、[洛马标题](https://x.com/CNBC/status/2114683305777824107) |
| 信用里被点名的设备与电力 | LRCX、GEV、VRT、BE | Carl Quintanilla 引用的口径：从 6 月下旬高点跌 30%–35%，投资级利差走阔 40–60 个基点。MarketWatch 标题称摩根士丹利认为半导体支撑可能再低 15% | [利差](https://x.com/carlquintanilla/status/2114422228850741387)、[半导体](https://x.com/MarketWatch/status/2114645519607689444) |
| 本周财报日程 | MSFT、GOOGL、AMZN、INTC、LLY、XOM、CVX 等 | Investing.com 列出微软、Alphabet、亚马逊、英特尔、Sandisk、Reddit、Roblox、Robinhood、SoFi、Visa、万事达、福特、UPS、联邦快递、波音、卡特彼勒、可口可乐、星巴克、Chipotle、Verizon、T-Mobile、礼来、埃克森、雪佛龙。线外的 The Transcript 把 Alphabet、微软放在周三，亚马逊、英特尔、礼来放在周四，埃克森和雪佛龙放在周五 | [名单](https://x.com/Investingcom/status/2114467814664798631)、[分日](https://x.com/TheTranscript_/status/2114688528013832636) |
| 能源配置而不是单一个股 | 原油、美国天然气、欧洲天然气 | HSBC 把原油升为明确超配。美国基准天然气约 2.5 美元，接近两年低点。欧洲天然气被写成四年高位。胡塞称打了东西泵站，沙特没有立即确认 | [HSBC](https://x.com/DeItaone/status/2114654012494565656)、[美国气](https://x.com/JavierBlas/status/2114621771085172911)、[欧洲气](https://x.com/WSJmarkets/status/2114656033809313968)、[泵站](https://x.com/financialjuice/status/2114545545742279135) |
| 指数目标，不是周一的价位 | 标普 | Wilson：近端 7100–7200，年底 8000。Yardeni：年底 7900，2027 年中 8400。Kobeissi：期货开盘时标普离新高约 3% | [Wilson](https://x.com/DeItaone/status/2114676641888612695)、[Yardeni](https://x.com/DeItaone/status/2114688174949548490)、[离新高](https://x.com/KobeissiLetter/status/2114490147773235247) |
| 图表账号的标题 | ADBE、INTU、MSI、PLTR、GLD、XLE | TrendSpider 把 Adobe 配上倒头肩、Intuit 配上“在画回升”、摩托罗拉解决方案配上“又想突破”、Palantir 配上“空头的噩梦”。黄金和能源 ETF 被放在一张“这看起来眼熟”的图里。这些是图说，没有价位 | [ADBE](https://x.com/TrendSpider/status/2114420476412068118)、[INTU](https://x.com/TrendSpider/status/2114439352021578126)、[MSI](https://x.com/TrendSpider/status/2114458224858657038)、[PLTR](https://x.com/TrendSpider/status/2114514850051506663)、[GLD 与 XLE](https://x.com/TrendSpider/status/2114401607714480263) |

《华尔街日报》那条“股票跌了 5% 以上”的帖没有在正文里写出公司名，这里不补代码：[帖](https://x.com/WSJ/status/2114641308530725097)。The Stalwart 后来写的“35% move”同样没有在正文里说明方向和标的：[帖](https://x.com/TheStalwart/status/2114678583511945510)。

## 后续走势：三套可以证伪的剧本

帖文没有给出周一收盘点位。能整理出来的是三套条件。抓取结束时期货还是绿的，所以下面的顺序以“开盘时这组读数还在不在”为准。

**巴西留在当地。** 触发器是美股期货维持 DeItaone 记下的标普大约涨 0.4%，而 EWZ、雷亚尔和巴西长端不再扩大缺口。这条路径上，卢拉交易是新兴市场和商品的事：大豆已经跌到两个月低点，美国上市的巴西股票按 Bespoke 的说法回到 2025 年底。彭博那篇“先别卖”的观点文章是这条路径上的反对意见，它的条件是财政压力逼出更务实的卢拉，不是决选无效。博索纳罗的诉讼若把当地交易再关进熔断，这条路径失败。高盛草图里的信用走阔 30 到 40 个基点若出现在美国高收益而不是巴西信用，也失败。

**伊朗这句话被下一则袭击盖过。** 触发器已经写在周一的帖里：胡塞称打了东西泵站、以色列选举前内塔尼亚胡说有伊朗及其代理人扰局的情报、First Squawk 那条没有署名的“冲突重启则油价可能过 150 美元”。这条路径上，周日晚间那种“股票涨、油价跌”会倒过来。HSBC 把原油升到明确超配、把股票降到中性，就是在油价已经下跌的早上摆的仓位，它赌的不是今天的负号，而是供应中断还没结束。美国天然气靠近两年低点、欧洲天然气在四年高位，说明这条路径先打在跨大西洋的天然气和运费上，不一定先打在亨利港。卡塔尔斡旋和德黑兰那场会议若被后续帖文写成有结果，这条路径失败。

**融资分化继续，指数不必跟着 neocloud。** 触发器是 Anthropic 的 S-1 真的在美东上午 9 点出现，Meta 的发行按 225 亿美元 A 类而不是“AI 结束了”来交易，SpaceX 的 Apollo 租赁按证交会文件而不是“已经关闭”来交易。Chamath 把 2027 年写成清算年：算力被买下但赚不回资本成本。Wilson 和 Yardeni 站在买跌的一侧，价位分别是近端 7100 到 7200、年底 7900 或 8000。CoreWeave 若再被写成融不到钱，彭博标题里的“拖回 6 月低点”就从警告变成路径。CCC 利差若从 13.4% 再走阔，Burry 写的那种“跌的时候混乱、一个月内把恐惧耗尽”会先面对信用，而不是先面对期货的 0.4%。

选举后的季节性不要提前用到今天。Wilson 的 6 到 12 个月强回报是中期选举之后的历史，选举还没投。Detrick 的强季节性具体到周三，而那天同时是议息日，他已经把沃什任内三次下跌的议息日写在旁边。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照美东 9:30 开盘。它不决定仓位大小。

**开盘前只核对五样东西。** EWZ 盘前大约 25% 的缺口、以及雷亚尔期货的成交，开盘后是收敛还是把美国盘带下去；原油仍在从六个月高位回落，还是被新的泵站或伊朗头条拉回去；Meta 盘前大约涨 2% 的融资，开盘后市场交易的是 50 亿美元芯片商接盘，还是 600 亿美元 C 类的稀释；Anthropic 的 S-1 有没有在 9 点出现，半导体有没有像 DeItaone 写的那样跟着抬；CCC 利差和法国 10 年期 4.9685% 这两个信用读数有没有在开盘头一小时变差。五样里巴西和信用变差、油价重新上涨，这些帖给出的默认顺序是已经在跌的 neocloud 和融资敏感的半导体低于有盈利的小盘和仍被 HSBC 超配的原油。巴西留在当地、油价继续回落、S-1 被当成风险偏好，默认顺序掉过头来：期货已经在涨的纳指高于去追 EWZ 的缺口。

**已经公开的方向，按账号而不是按共识。**

- HSBC：股票降到中性，黄金超配下调，原油升到明确超配。这是配置变化，不是今天的油价目标。
- Kobeissi：今天不打伊朗对应期货上涨、原油下跌；巴西股市跌 20% 是另一条新闻；CCC 收益率 18%、利差 13.4% 是他们写下的信用事实。他们没有在这些帖里给周一的标普目标，只说离新高大约 3%。
- Keith McCullough：高收益维持看空，韩国和日本维持熊市趋势，菲律宾仍空，原油是对上周周期高点的修正，黄金是上周再跌 4.1% 之后的 0.6% 反弹。Hedgeye 主号今天没有帖。他的 Early Look 标题是为 Quad 4 做准备。
- Gary Black：盘前标普和纳指小涨、10 年期 4.98%、比特币 8.01 万美元。他的交易表达是对特斯拉谨慎，不是对指数看空。巴克莱的超配和 450 美元目标价是另一套。
- Michael Wilson，经 DeItaone：近端可以到 7100–7200，年底基准 8000，条件是 AI 融资、中期选举和金融条件这三件事出清。这是选举前的修正框架，不是今天做多的指令。
- Ed Yardeni，经 DeItaone：抛售是买点，年底 7900，2027 年中 8400。他把地缘、加息、中期选举和 AI 投资并列成风险，没有说哪一条已经解除。
- Chamath：2027 年会清掉算力上的错误赌注，neocloud 的违约金条款是最后一关。他没有给周一的代码。
- Bespoke：EWZ 跌回 2025 年底是价格事实。上半年最差的 25 只股票下半年等权涨 34%，是已经发生的半年，不是周一的篮子。
- Ryan Detrick：周三同时是全年历史上偏强的一天和议息日。计划是看沃什任内议息日下跌的记录会不会再重复，而不是把季节性当成方向。
- Kitco 转述的 Streible：黄金跌破 4000 之后，转折看美联储不能再加息，不看下一条战争头条。这和他记录的“利好黄金的宏观当天金价仍跌 90 美元”是同一句话。
- alphatrends：比特币 79420 的买单周六成交，79756 卖掉四分之三。这是他公开的成交，不是指数观点。

**财报周的顺序。** 先看已经写进文件的融资，SpaceX 与 Apollo 的租赁、Meta 的远期销售和 C 类额度、Anthropic 的 S-1，再看 Investing.com 点名的微软、Alphabet、亚马逊、英特尔，以及周四的礼来和周五的埃克森、雪佛龙。Verizon 的数字已经出来了，用来对照云厂商会不会把资本开支说得更大，而不是用来重做 Verizon 的交易。应用材料、拉姆研究只出现在 Seeking Alpha 的文章标题和 Carl 引用的跌幅里。

**明确留在观察、不放进计划的东西。** Cramer、Cathie Wood、ARK、Dalio、Schiff、Timiraos、Gromen、Alf、Damodaran、Gundlach 和 Tom Lee 的 fundstrat 账号这天没有可引用的新判断。Lee“大家太悲观”只出现在 StockMKTNewz 的转述里。Ackman 的帖是选举和纽约州检察长。Pompliano 的帖是球赛。Pal 的帖是书。Burry 的帖是市场结构，不是目标点位。彭博主号和德意志银行的时间线这次没有形成可用的周一早晨样本。SpotGamma 今天没有更新期权偏度。

## 帖文索引

巴西：[计票 51.8%](https://x.com/CNBC/status/2114517041927327996)、[股市跌 20%](https://x.com/KobeissiLetter/status/2114560008897671476)、[EWZ 盘前](https://x.com/bespokeinvest/status/2114680755829764556)、[高盛草图](https://x.com/zerohedge/status/2114549663554793937)、[摩根士丹利](https://x.com/DeItaone/status/2114682043044892785)、[要求无效](https://x.com/Reuters/status/2114616769679966640)、[大豆](https://x.com/business/status/2114561440585523360)、[雷亚尔期货](https://x.com/CMEGroup/status/2114665847637549331)。

伊朗与能源：[今天不打](https://x.com/KobeissiLetter/status/2114408186363134405)、[期货第一组报价](https://x.com/KobeissiLetter/status/2114490147773235247)、[油价跌超 2%](https://x.com/CNBC/status/2114588202723930278)、[东西泵站](https://x.com/financialjuice/status/2114545545742279135)、[德黑兰会议](https://x.com/JavierBlas/status/2114606899492683997)、[霍尔木兹流量](https://x.com/JavierBlas/status/2114434374972088659)、[美国天然气](https://x.com/JavierBlas/status/2114621771085172911)、[HSBC](https://x.com/DeItaone/status/2114654012494565656)。

AI 与信用：[neocloud](https://x.com/KobeissiLetter/status/2114522987018031174)、[Apollo 租赁](https://x.com/DeItaone/status/2114688952686805491)、[周日尚未关闭](https://x.com/business/status/2114526226341638145)、[Meta 发行](https://x.com/financialjuice/status/2114673261829316918)、[S-1 时间](https://x.com/DeItaone/status/2114680761848897631)、[CCC 利差](https://x.com/KobeissiLetter/status/2114455149670228337)、[Chamath 的 2027](https://x.com/chamath/status/2114389987563381004)、[CoreWeave 风向标](https://x.com/theinformation/status/2114401651402342636)。

政策与交叉资产：[10 月维持不变](https://x.com/DeItaone/status/2114652209463922971)、[沃什的议息日](https://x.com/RyanDetrick/status/2114534807149371458)、[Wilson 的区间](https://x.com/DeItaone/status/2114676641888612695)、[Yardeni](https://x.com/DeItaone/status/2114688174949548490)、[法国收益率回落](https://x.com/DeItaone/status/2114622867510112471)、[黄金在 4000 下方](https://x.com/WSJmarkets/status/2114531417174524304)、[韩国目标 9000](https://x.com/DeItaone/status/2114665254781161837)、[期货午后读数](https://x.com/DeItaone/status/2114687217897787568)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-10-26 抓取时的公开读数。原创条数是北京时间当天窗口内、按帖文编号去重后的原创帖，回复不计入。First Squawk 的 195 是分页下限，最老一条仍在窗口打开后约 5 分钟。德意志银行的 0 是读取失败。彭博主号的 0 来自一条明显不完整的时间线，最新可见帖停在 10 月 12 日。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,433,452 | 76 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,318,437 | 75 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,277,687 | 53 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,322,630 | 21 |
| 5 | [@business](https://x.com/business) | 10,483,961 | 109 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,559,933 | 0 |
| 7 | [@FT](https://x.com/FT) | 7,101,816 | 41 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,258,194 | 33 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,423,010 | 11 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,645,472 | 11 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,567,192 | 1 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,422,428 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,362,766 | 18 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,433,764 | 50 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,420,402 | 5 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,036,646 | 2 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 2,997,345 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,697,688 | 11 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,555,906 | 0 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,506,169 | 0 |
| 21 | [@chamath](https://x.com/chamath) | 2,476,206 | 1 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,438,338 | 2 |
| 23 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,731 | 13 |
| 24 | [@michaeljburry](https://x.com/michaeljburry) | 2,133,235 | 4 |
| 25 | [@YahooFinance](https://x.com/YahooFinance) | 2,073,177 | 0 |
| 26 | [@markets](https://x.com/markets) | 2,045,548 | 0 |
| 27 | [@DeItaone](https://x.com/DeItaone) | 1,966,893 | 34 |
| 28 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,771,317 | 0 |
| 29 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,734,665 | 1 |
| 30 | [@NYSE](https://x.com/NYSE) | 1,699,293 | 0 |
| 31 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,693,453 | 0 |
| 32 | [@theinformation](https://x.com/theinformation) | 1,607,580 | 12 |
| 33 | [@federalreserve](https://x.com/federalreserve) | 1,599,149 | 0 |
| 34 | [@Investingcom](https://x.com/Investingcom) | 1,531,887 | 18 |
| 35 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,508,210 | 2 |
| 36 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,469,242 | 12 |
| 37 | [@Bloomberg](https://x.com/Bloomberg) | 1,350,659 | 0 |
| 38 | [@TheStreet](https://x.com/TheStreet) | 1,228,912 | 42 |
| 39 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,194,390 | 0 |
| 40 | [@Stocktwits](https://x.com/Stocktwits) | 1,192,666 | 2 |
| 41 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,182,454 | 0 |
| 42 | [@USTreasury](https://x.com/USTreasury) | 1,163,588 | 0 |
| 43 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,160,188 | 25 |
| 44 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,156,158 | 0 |
| 45 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,143,139 | 1 |
| 46 | [@elerianm](https://x.com/elerianm) | 1,117,552 | 4 |
| 47 | [@BlackRock](https://x.com/BlackRock) | 1,080,988 | 0 |
| 48 | [@Downtown](https://x.com/Downtown) | 1,043,682 | 0 |
| 49 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,182 | 30 |
| 50 | [@financialjuice](https://x.com/financialjuice) | 954,677 | 83 |
| 51 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,684 | 0 |
| 52 | [@tradingview](https://x.com/tradingview) | 906,549 | 0 |
| 53 | [@BloombergTV](https://x.com/BloombergTV) | 892,997 | 0 |
| 54 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 889,487 | 0 |
| 55 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,700 | 9 |
| 56 | [@charliebilello](https://x.com/charliebilello) | 873,801 | 2 |
| 57 | [@axios](https://x.com/axios) | 861,348 | 11 |
| 58 | [@jpmorgan](https://x.com/jpmorgan) | 859,446 | 0 |
| 59 | [@Citi](https://x.com/Citi) | 853,447 | 0 |
| 60 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 848,028 | 7 |
| 61 | [@ARKInvest](https://x.com/ARKInvest) | 822,351 | 0 |
| 62 | [@biancoresearch](https://x.com/biancoresearch) | 791,558 | 0 |
| 63 | [@markminervini](https://x.com/markminervini) | 767,180 | 1 |
| 64 | [@MorganStanley](https://x.com/MorganStanley) | 757,773 | 0 |
| 65 | [@CNBCnow](https://x.com/CNBCnow) | 752,320 | 0 |
| 66 | [@morganhousel](https://x.com/morganhousel) | 725,526 | 1 |
| 67 | [@TrendSpider](https://x.com/TrendSpider) | 719,072 | 11 |
| 68 | [@CMEGroup](https://x.com/CMEGroup) | 711,979 | 1 |
| 69 | [@Nouriel](https://x.com/Nouriel) | 701,837 | 0 |
| 70 | [@fundstrat](https://x.com/fundstrat) | 674,316 | 0 |
| 71 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 673,583 | 6 |
| 72 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,631 | 0 |
| 73 | [@LukeGromen](https://x.com/LukeGromen) | 638,793 | 0 |
| 74 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,872 | 0 |
| 75 | [@EricBalchunas](https://x.com/EricBalchunas) | 629,506 | 2 |
| 76 | [@garyblack00](https://x.com/garyblack00) | 584,319 | 1 |
| 77 | [@Barchart](https://x.com/Barchart) | 577,344 | 5 |
| 78 | [@FirstSquawk](https://x.com/FirstSquawk) | 574,624 | 195 |
| 79 | [@TruthGundlach](https://x.com/TruthGundlach) | 573,855 | 0 |
| 80 | [@eWhispers](https://x.com/eWhispers) | 572,020 | 0 |
| 81 | [@MadMoneyOnCNBC](https://x.com/MadMoneyOnCNBC) | 543,507 | 0 |
| 82 | [@AswathDamodaran](https://x.com/AswathDamodaran) | 520,934 | 0 |
| 83 | [@carlquintanilla](https://x.com/carlquintanilla) | 515,597 | 4 |
| 84 | [@LiveSquawk](https://x.com/LiveSquawk) | 505,995 | 23 |
| 85 | [@UBS](https://x.com/UBS) | 499,487 | 0 |
| 86 | [@NickTimiraos](https://x.com/NickTimiraos) | 493,839 | 0 |
| 87 | [@NikkeiAsia](https://x.com/NikkeiAsia) | 489,394 | 38 |
| 88 | [@KeithMcCullough](https://x.com/KeithMcCullough) | 478,695 | 18 |
| 89 | [@Fxhedgers](https://x.com/Fxhedgers) | 472,083 | 2 |
| 90 | [@MacroAlf](https://x.com/MacroAlf) | 465,628 | 0 |
| 91 | [@traderstewie](https://x.com/traderstewie) | 462,928 | 1 |
| 92 | [@IBDinvestors](https://x.com/IBDinvestors) | 456,271 | 1 |
| 93 | [@TheStalwart](https://x.com/TheStalwart) | 453,518 | 12 |
| 94 | [@CNBCFastMoney](https://x.com/CNBCFastMoney) | 451,578 | 0 |
| 95 | [@Hedgeye](https://x.com/Hedgeye) | 447,749 | 0 |
| 96 | [@GoldTelegraph](https://x.com/GoldTelegraph) | 447,346 | 2 |
| 97 | [@lisaabramowicz1](https://x.com/lisaabramowicz1) | 444,868 | 0 |
| 98 | [@BeckyQuick](https://x.com/BeckyQuick) | 441,649 | 0 |
| 99 | [@alphatrends](https://x.com/alphatrends) | 431,335 | 3 |
| 100 | [@barronsonline](https://x.com/barronsonline) | 408,062 | 14 |
