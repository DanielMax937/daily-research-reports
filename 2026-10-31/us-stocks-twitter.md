# 美股 Twitter 观点日报 · 2026-10-31

周五现货是跌的，跌幅集中在纳斯达克，英特尔和人工智能资本开支是帖文里的两根主线，油价结算往上，黄金往下。First Squawk 的非官方收盘：纳斯达克收 25438.40，跌 746.33 点，跌 2.85%；道指收 51763.41，跌 579.15 点，跌 1.11%；标普收 7578.14，跌 142.25 点，跌 1.84%：[三行收盘](https://x.com/FirstSquawk/status/2116259225370493248)。同一分钟 Investing.com 的标题是纳斯达克跌 3%：[帖](https://x.com/Investingcom/status/2116259289203642645)。Bespoke 稍后把标普收盘写成 7580.07，并写成和 5 月最后一个交易日的 7580.06 只差一美分：[帖](https://x.com/bespokeinvest/status/2116264164482322693)。7578.14 和 7580.07 是两张收盘帖。2.85% 和 3% 也是两张。点位和点数不拿去跟周四那份非官方收盘轧差。

纳斯达克 100 的盘中路径是另一条线。Kobeissi 先写跌 3.6%、抹掉 1.3 万亿美元，再写跌 4.2%、抹掉 1.7 万亿美元，然后在美东下午 3 点写已经进入技术性调整、较 10 月 6 日高点跌 10%，英特尔当时“有望”跌 31%：[3.6%](https://x.com/KobeissiLetter/status/2116218071153295381)、[4.2%](https://x.com/KobeissiLetter/status/2116235618984538493)、[10%](https://x.com/KobeissiLetter/status/2116243866718523645)。Gary Black 在 17:25 UTC 的快照是纳斯达克 100 跌 3.7%：[帖](https://x.com/garyblack00/status/2116220018018955433)。Bespoke 在 18:00 UTC 写 QQQ 较高点跌 9.55%，离 10% 的调整还差几档，今年前两次调整停在大约 11.5%：[帖](https://x.com/bespokeinvest/status/2116228872887001308)。彭博 19:35 UTC 的句子是“正走向”今年第三次技术性调整，还没有写成已经收在调整里：[帖](https://x.com/business/status/2116251348156993790)。收盘后 TrendSpider 只写 QQQ 是 6 月以来最差的一天，没有给收盘百分比：[帖](https://x.com/TrendSpider/status/2116266469499777285)。综合指数的 2.85% 不要换成这些盘中百分比。

下面每一条归纳都附有帖文链接。盘中百分比、非官方收盘和另一家的收盘点位按发帖时间分开。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-10-31**。触发时刻约 12:00 UTC，时间线补抓到 **约 12:18 UTC（北京时间 20:18，美东 8:18）**。周六现货不开市。观察窗口从 **2026-10-30 12:17 UTC** 到抓取结束，也就是上一份日报写明“现货还没开盘”之后，覆盖美东周五现货全天、周五收盘、周五盘后和周六上午。美东零点到 8:17 的盘前已经写在 10 月 30 日那份日报里。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。美国趋势读到的是 Happy Halloween、Intel、Haley Stevens、Christian Watson、Tusk、Patrick Stewart。里面和美股直接有关的是 **Intel**。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号，再加上趋势里的 Intel。
- 不存在官方的“美股 Top 100”。这次试了 **704** 个候选，成功读到粉丝数的有 **618** 个。排序时拿掉加密货币账号、综合新闻主号、科技风投和创始人、大型科技公司首席执行官、竞选和政治账号、公司产品品牌，以及金融时报的重复账号。用来排序的账号是 **547** 个，截止在 Eric Balchunas（约 62.8 万粉）。《商业周刊》、彭博经济、纳斯达克交易所账号、财政部长 Scott Bessent 的账号按粉丝数排进了前 100。Gary Black、Cboe、Barchart、First Squawk、Jeffrey Gundlach、Earnings Whispers、Mad Money、Aswath Damodaran、Carl Quintanilla、美银新闻、LiveSquawk、瑞银、Nick Timiraos、日经亚洲、Keith McCullough、Hedgeye、巴伦、Javier Blas、Robin Brooks、Bespoke、SpotGamma、The Transcript、firstadopter、Lisa Abramowicz、RedDogT3、Ryan Detrick、The Stalwart、MacroAlf 落在线外，引用时会写明。Andy Constan 的资料接口这次没有读到粉丝数，时间线仍有帖。排序不代表预测准确度。
- 100 个账号里，**76 个**在窗口内有按帖文链接去重后、且接口没有标成回复或转发的原创帖。路透读穿窗口，175 条。彭博商业账号 212 条。FinancialJuice 177 条。零对冲 96 条。线外的 First Squawk 读穿窗口，206 条，窗口内最早一条早于窗口起点。德意志银行和 Daniel Newman 的时间线返回失败，表里的 0 不是确认沉默。沃伦·巴菲特的可见时间线停在 2016 年，彭博经济停在 2026 年 7 月，彭博主号停在 10 月 12 日，彭博 markets 停在 9 月 11 日，BBC Business 停在 2024 年，CNN Business 停在 2021 年，TradingView 停在 2026 年 6 月。这几家的 0 同样不能当成确认沉默。

## 周五的现货，指数、纳指和等权是三张图

收盘价先以 First Squawk 那三行为准。标普跌 1.84%，纳斯达克跌 2.85%，道指跌 1.11%。Bespoke 的 7580.07 用来说明五个月走了一个来回：5 月最后一个交易日是 7580.06。Ryan Detrick 在收盘前写，这一天有可能成为 2009 年以来最差的 10 月最后一个交易日，2009 年那天跌了 2.81%，也是周五：[帖](https://x.com/RyanDetrick/status/2116242207900680458)。非官方收盘是跌 1.84%，小于 2.81%。他收盘后另写，标普连续两周跌了半个百分点，体感更差：[帖](https://x.com/RyanDetrick/status/2116265354016215261)。半个百分点是周线句子，1.84% 是周五当天。

线外的 SpotGamma 在中午写，标普已经 101 天没有单日跌 2%，7600 附近有支撑，收在 7566 以下才是跌 2%：[帖](https://x.com/spotgamma/status/2116209307335438844)。7578.14 和 7580.07 都在 7566 上面。同一账号开盘前后写，标普期货跌 80 点，0DTE 跨式大约 40 点；风险是科技传染，纳斯达克 100 的波动率升得比标普快，因为有资金从科技转到其他行业、把标普托住：[期货](https://x.com/spotgamma/status/2116150457462853793)、[传染](https://x.com/spotgamma/status/2116143508881117590)。

宽度和等权是十月的另一张图，不要和周五这一天的跌幅相加。Bespoke：成长跌 5.5%，价值涨 5% 并创历史新高；能源和必需消费涨超过 10%，科技和通信服务跌超过 8%。标普等权相对市值加权，是 2009 年 4 月以来最强的一个月，也是 1990 年以来第二强：[十月](https://x.com/bespokeinvest/status/2116301443632398814)、[等权](https://x.com/bespokeinvest/status/2116286212340342990)。Detrick 在开盘后写，超过 75% 的标普成分在 20 日均线之上，是 4 月以来最多；涨跌线在前一天突破阻力。他同时写，10 月只剩一天的时候，11 个行业里 9 个是涨的，但科技跌 3%、通信服务跌 14%，指数就很难看出涨：[20 日](https://x.com/RyanDetrick/status/2116161420882858489)、[行业](https://x.com/RyanDetrick/status/2116150604137742599)。Bespoke 另写，周四是 1990 年以来、标普下跌日里涨跌家数最正的一天，净上涨 309 家：[帖](https://x.com/bespokeinvest/status/2116190500151492831)。Kobeissi 的 30 日热力图句子是：情绪像大熊市，科技股三周跌了 5 万亿美元，但标普多数成分过去一个月是绿的，指数离纪录高点还有 3%。这条发在 16:35 UTC，还不是收盘：[帖](https://x.com/KobeissiLetter/status/2116207249987383572)。

El-Erian 把周五写成难看的一天，尤其是科技。相对小的财报瑕疵就引发大跌，说明投资者已经转去审人工智能的资本开支、融资、变现和回报。他补了一句：这种紧张到当时为止，还没有变成对科技拉动的增长前景的重估：[帖](https://x.com/elerianm/status/2116241450912592010)。周六他引《华尔街日报》：贷款人和投资人开始挑项目、要更硬的条款，人工智能建设进入新阶段：[帖](https://x.com/elerianm/status/2116485855594377465)。

## 观点分成四组

### 1. 英特尔的收盘帖停在 28.5% 和 29%，盘中到过 30% 和 31%

开盘前后的句子是跌 26%。First Squawk 13:34 UTC：跌 26%，2024 年以来最大单日跌幅：[帖](https://x.com/FirstSquawk/status/2116161810433011867)。Hedgeye 同时写跌 26.2%，到 2026 年 4 月以来最低：[帖](https://x.com/Hedgeye/status/2116158540888887346)。随后 Kobeissi 写成延伸到跌 30%，并写成有望成为纪录上最大单日跌幅，互联网泡沫和 1970 年代都没有这样的跌幅：[帖](https://x.com/KobeissiLetter/status/2116166412024868892)。美东下午 3 点他写“有望”跌 31%。收盘时段换成另外三个数。零对冲 20:10 UTC：跌 29%，至少四十年来最差的一天：[帖](https://x.com/zerohedge/status/2116261599195341028)。Detrick 20:18 UTC：纪录性的跌 28.5%，年内仍涨 67.0%：[帖](https://x.com/RyanDetrick/status/2116263422342160385)。CNBC：跌 29%，1970 年代以来最差的一天；指引不及，原因写成以色列一座工厂停工，以及个人电脑仍然疲弱：[帖](https://x.com/CNBC/status/2116274978400133507)。雅虎财经的标题是 1974 年以来最差的一天：[帖](https://x.com/YahooFinance/status/2116265992401645878)。28.5%、29%、1970 年代、1974 年、四十年，都按原帖留着。26%、30%、31% 是更早的盘中帖。

美银把英特尔从买入降到中性，目标价从 145 美元降到 100 美元：[帖](https://x.com/StockMKTNewz/status/2116154088945860934)。DeItaone：5 年期信用违约互换扩到纪录的 123.5 个基点，有望成为 2022 年 10 月以来最大的单日走阔：[帖](https://x.com/DeItaone/status/2116173199377408042)。123.5 发在 14:19 UTC，句子里是“有望”，不是收盘利差。Guy Adami 写，政府持有 4.33 亿股，成本大约 20.47 美元；仓位已经涨了两倍，但较 6 月 142.35 美元的历史高点跌了超过 50%：[帖](https://x.com/GuyAdami/status/2116318806762996140)。线外的 Keith 在收盘前说，只跌 30% 也好，CNBC 那类散户没有拿着它：[帖](https://x.com/KeithMcCullough/status/2116253906913181914)。Mark Minervini 贴了自己的 50/80 规则，并写空头有效、多头还撑着：[空头](https://x.com/markminervini/status/2116236435674042691)、[规则](https://x.com/markminervini/status/2116164348854854089)。

半导体是被拖着走的一组，百分比仍是盘中。Bespoke 17:57 UTC：半导体 ETF SOXX 当天跌近 10%，跌破 7 月 29 日的收盘低点：[帖](https://x.com/bespokeinvest/status/2116228098798887000)。Andy Constan 17:33 UTC：三倍做多半导体的 SOXL 跌 28%，收盘前还有股票要卖：[帖](https://x.com/dampedspring/status/2116221960665309601)。这两条都早于 20:01 UTC 的指数收盘。TrendSpider 在周五晚写，Sandisk 第一次跌到 200 日均线下方：[帖](https://x.com/TrendSpider/status/2116334348337315988)。线外的 RedDog 在早上把 1225 美元写成 Sandisk 当天要看的位置，并把 QQQ 的 200 日写成 684 到 685 一带：[Sandisk](https://x.com/RedDogT3/status/2116149829969875245)、[200 日](https://x.com/RedDogT3/status/2116237017638117557)。

### 2. 亚马逊盘中到过跌 3%，融资帖是最多 800 亿美元

Gary 14:18 UTC 的亚马逊是跌 3%。两条理由：线上增速降到同比 2%，2023 年一季度以来最慢；资本开支 773 亿美元，预期 588 亿美元，2026 财年资本开支指引维持 2200 亿美元。他把买下跌的障碍写成，资本开支竞赛要到 2027 年早到中才能看到回报。估值在他那里是 2027 年市盈率 22.1 倍、EV/EBITDA 9.2 倍，对照长期收入增速 14%、每股收益增速 16%：[帖](https://x.com/garyblack00/status/2116172920271552719)。线外的 Stephanie Link 把反应写成过重：AWS 增 39%，连续第六个季度加速，是 2021 年四季度以来最好，积压翻了三倍，未来两年指引是 40% 的增速和 40% 的经营利润率；她另写 15 倍市盈率：[帖](https://x.com/Stephanie_Link/status/2116146031696167378)。22.1 倍和 15 倍是两个估值句子。线外的 firstadopter 写，绝对数字很好，未来两年 AWS 增 40% 的展望很强，亚马逊已经离开恐慌低点：[帖](https://x.com/firstadopter/status/2116188507144339754)。Cramer 在 19:34 UTC 写亚马逊跑赢纳斯达克 100：[帖](https://x.com/jimcramer/status/2116252405784617023)。窗口里没有一张把亚马逊收盘跌幅写成一个百分比的帖。Bespoke 只统计了开盘：这是 101 份财报里第 40 次开盘跌 4% 以上，此前只有 2008 年两次开盘大跌后收阳：[帖](https://x.com/bespokeinvest/status/2116183401631781193)。

融资是收盘前已经写出来的事实。彭博：亚马逊安排了以所购硬件为抵押的供应商融资，规模最多 800 亿美元：[帖](https://x.com/business/status/2116257611507020056)。StockMKTNewz 引《华尔街日报》：可以从 2027 年初用到 2028 年三季度；此前主要靠自有现金和债券：[帖](https://x.com/StockMKTNewz/status/2116211136416669926)。最多 800 亿美元、2027 年到 2028 年三季度，是这两条帖的口径。同一账号另写，摩根士丹利把目标价从 350 美元降到 335 美元，维持超配；美银从 320 美元降到 317 美元，维持买入：[帖](https://x.com/StockMKTNewz/status/2116189468151455835)。335 和 317 是两条券商目标价，和 800 亿美元的融资额度不是同一个数。

云的积压是 The Transcript 的一条引文。微软商业剩余履约义务增 73% 到 6770 亿美元，大约 30% 会在未来 12 个月确认。谷歌云积压 5610 亿美元，略多于 55% 预计在未来 24 个月确认。亚马逊积压 5780 亿美元，同比三位数增长。三条加总被写成大约 1.8 万亿美元：[帖](https://x.com/TheTranscript_/status/2116319301452075213)。

Meta 的信用句子在收盘后。Kobeissi 引标普全球：展望调到负面，杠杆可能超过 1.0 倍，自由经营现金流为负的时间可能长于预期：[帖](https://x.com/KobeissiLetter/status/2116280985612636573)。CNBC 的标题相同：[帖](https://x.com/CNBC/status/2116287262056948178)。First Squawk 另有一条：Meta 和解社交媒体成瘾诉讼、避免开庭。那是诉讼，不是评级：[帖](https://x.com/FirstSquawk/status/2116198912893829413)。

OpenAI 和 Anthropic 是周五夜里的融资帖。Kobeissi 引《金融时报》：融资目标砍 100 亿美元，估值砍 1500 亿美元；现在寻求以 1.25 万亿美元估值筹集 200 亿美元，之前是 1.4 万亿美元估值筹集 300 亿美元。部分投资者降低了分配，第一次关闭预计不到 200 亿美元。帖子发在美东周五 22:33，里面的“今天”是美东周五。他并写这发生在预期中的 Anthropic 上市前几周：[帖](https://x.com/KobeissiLetter/status/2116357848464601125)。更早一条：黑石告诉投资人，Anthropic 上市后很可能拿不到投资级；公司称从现在到 2045 年计算基础设施支出超过 8000 亿美元：[帖](https://x.com/KobeissiLetter/status/2116228648978055455)。firstadopter 问的是另一句：SpaceX 被当成投资级、Anthropic 不是，评级机构是否合理。他的答案是护城河在 Anthropic：[评级](https://x.com/firstadopter/status/2116225039465099539)、[护城河](https://x.com/firstadopter/status/2116230997423567170)。

线外的 Earnings Whispers 把本周公布的三只超大盘写成全部不及预期，点名微软、Alphabet、亚马逊：[帖](https://x.com/eWhispers/status/2116235943006863378)。这是他的归类。Gary 和 Stephanie 对亚马逊的拆分仍然是收入和资本开支一条线、AWS 增速另一条线。

Kobeissi 的个股回撤名单用的是高点，不是周五涨跌幅。AppLovin 跌 68%，Coinbase 跌 62%，CoreWeave 跌 60%，Arm 跌 55%，西部数据跌 54%，英特尔跌 54%，甲骨文跌 51%，Sandisk 跌 49%，Circle 跌 48%，ServiceNow 跌 44%，Robinhood 跌 44%，希捷跌 42%，迈威尔跌 39%，超微跌 39%，博通跌 34%，Alphabet 跌 31%，Adobe 跌 29%，美光跌 29%，IBM 跌 23%，Meta 跌 21%，亚马逊跌 21%。纳斯达克 100 自 10 月 6 日跌去近 5 万亿美元：[帖](https://x.com/KobeissiLetter/status/2116179386030342497)。这份名单上的 21% 和 Gary 盘中的跌 3% 是两个窗口。Reddit 被他写成 8 个交易日跌 42%：[帖](https://x.com/KobeissiLetter/status/2116191185677246814)。Investing.com 在 18:14 UTC 写 Reddit 把纪录盘中跌幅延伸到超过 30%：[帖](https://x.com/Investingcom/status/2116232193169056027)。30% 是当天盘中，42% 是 8 天。

苹果在彭博的收盘叙事里换成了避风港：周五重新成为全球市值最高的公司，从英伟达手里拿回这个位置：[帖](https://x.com/business/status/2116268642522316913)。礼来自 4 月下旬涨 66%，创历史新高：[帖](https://x.com/bespokeinvest/status/2116258759014248709)。伯克希尔 B 股 10 月涨 9%，刚创历史新高：[帖](https://x.com/bespokeinvest/status/2116259323328475526)。Hedgeye 写医疗板块 ETF 创历史新高，他们继续拿着多头：[帖](https://x.com/Hedgeye/status/2116173709191045161)。

### 3. 就业成本指数打平，收盘后的加息概率是 75%

8:30 的就业成本指数已经出来。LiveSquawk：三季度升 0.8%，预期 0.8%，前值 0.9%：[帖](https://x.com/LiveSquawk/status/2116145812757704958)。Nick Timiraos：剔除激励性职业之后，私营部门薪酬同比升 3.1%，一年前 3.4%，是 2021 年一季度以来最低：[帖](https://x.com/NickTimiraos/status/2116150942093410559)。他另写工资增速 3.1%，福利成本升 3.9%，福利增速现在略高于工资：[帖](https://x.com/NickTimiraos/status/2116197607701672196)。Liz Ann Sonders：劳动力成本同比升 3.4%，低于 9 月标题 CPI 的 3.7%：[帖](https://x.com/LizAnnSonders/status/2116276357579882842)。线外的 Bob Elliott 把基准就业成本指数的工资写成周期低点，和平均时薪一致，说明劳动力市场没有多紧：[帖](https://x.com/BobEUnlimited/status/2116156150282354983)。0.8% 的季度数、3.1% 的工资、3.9% 的福利、3.4% 的劳动力成本，是四条序列。

芝加哥 PMI 在 9:45。LiveSquawk：10 月 55.3，预期 56.0，前值 58.8：[帖](https://x.com/LiveSquawk/status/2116164542191341608)。Bespoke 把两项放在一起：就业成本指数 0.8% 符合预期，芝加哥 PMI 不及预期：[帖](https://x.com/bespokeinvest/status/2116175990225510896)。

收益率的早晨快照早于股市的下跌。DeItaone 12:37 UTC：10 年期收益率降 6.22 个基点到 4.927%，两年期降 7.05 个基点到 4.586%，发生在美国数据之后：[帖](https://x.com/DeItaone/status/2116147497999773727)。Gary 17:25 UTC 的 10 年期是 4.94%，并写成从 9 月 30 日的 5.3% 降下来，股票相对债券更有吸引力。Kobeissi 在 18:45 UTC 写，科技大跌的同时美债收益率几乎没有得到缓解。收盘后 20:12 UTC，他把 12 月再次加息的概率写成 75%，理由是 CPI、PPI 和 PCE 都重新抬头；12 个月前市场看到的是 2026 年至少降息 3 次：[帖](https://x.com/KobeissiLetter/status/2116261977559544282)。4.927%、4.94% 和 75% 按时间留着。

委员讲话分成“还要加”和“慢慢加”。Nick 引达拉斯联储的 Logan：跳过一次会议不改变目的地，她仍然认为还要加息两次；渐进调整可以帮助家庭和企业适应更高的利率：[帖](https://x.com/NickTimiraos/status/2116222283954168289)。同一作者引圣路易斯联储的 Musalem：进一步收紧是必要的，而且要快。他更可能的情景是，不再加息的话通胀会维持太高；更不可能但说得通的情景是能源价格下跌、人工智能支出急刹车，或者金融条件突然收紧：[帖](https://x.com/NickTimiraos/status/2116206415534563715)。里士满联储的 Barkin 对 SiriusXM 说，方向清楚，问题是节奏，9 月说过渐进，渐进仍然合适：[帖](https://x.com/NickTimiraos/status/2116171320341713253)。LiveSquawk 另引 Barkin：人工智能投资推高了供应链压力，也带来需求侧通胀，这是美联储可以去压的那种：[帖](https://x.com/LiveSquawk/status/2116163176903651784)。

德国 10 月 CPI 是另一组。LiveSquawk：同比升 2.8%，预期 3.0%，前值 3.3%；环比降 0.2%，预期升 0.1%：[帖](https://x.com/LiveSquawk/status/2116153309618946492)。DeItaone 的读法是，低于预期的德国通胀可能减轻欧洲央行进一步加息的压力：[帖](https://x.com/DeItaone/status/2116153643720167727)。这是欧洲的初步数，不是美国的 0.8%。

周六已经落地的是中国官方 PMI。First Squawk：10 月制造业 49.3，9 月 50.1；非制造业 49.7，9 月 50.2：[制造业](https://x.com/FirstSquawk/status/2116342068817838446)、[非制造业](https://x.com/FirstSquawk/status/2116342164137619482)。

Kobeissi 另有一条消费者情绪：41% 的美国人预期未来 12 个月财务状况变差，是纪录，自 2024 年二季度以来增加两倍有余；2008 年这个数的峰值是 23%。31% 认为 5 年后更差：[帖](https://x.com/KobeissiLetter/status/2116313518911668301)。Hedgeye 用了同一个 41%：[帖](https://x.com/Hedgeye/status/2116211024915230822)。

### 4. 油的结算价往上，黄金往下，霍尔木兹是好几条没有合成的帖

结算先写。First Squawk：WTI 原油期货结算 104.12 美元，涨 2.12 美元，涨 2.08%：[帖](https://x.com/FirstSquawk/status/2116236578456809803)。布伦特结算 117.64 美元，涨 2.76 美元，涨 2.4%：[帖](https://x.com/FirstSquawk/status/2116241855419703583)。FinancialJuice 的 NYMEX 12 月 WTI 和布伦特是同样的 104.12 和 117.64：[WTI](https://x.com/financialjuice/status/2116236543983538573)、[布伦特](https://x.com/financialjuice/status/2116240802016084256)。周四结算是 102.00 和 114.88，这次的涨幅和那两个基数对得上，所以结算价可以连着写。银行调查不是现货。DeItaone 引《华尔街日报》调查：2026 年布伦特预测 90.40 美元，之前 88.13；WTI 84.38，之前 82.98。2027 年布伦特 76.74，WTI 70.52：[帖](https://x.com/DeItaone/status/2116172297706860847)。90.40 是年度预测，117.64 是周五结算。Hedgeye 写原油这个月涨了 12.5%：[帖](https://x.com/Hedgeye/status/2116171247910522895)。

霍尔木兹的说法按账号留着。零对冲的早盘标题是期货下跌，人工智能清算打到亚马逊和英特尔，油价因为霍尔木兹油轮遇袭而跳升：[帖](https://x.com/zerohedge/status/2116143691538604324)。First Squawk 20:10 UTC 引伊斯兰革命卫队和 IRIB：第四艘油轮在海峡触雷后爆炸：[帖](https://x.com/FirstSquawk/status/2116261433398989144)。《金融时报》的标题是伊朗用吸附水雷打中霍尔木兹的油轮，打法出现变化：[帖](https://x.com/FT/status/2116145508582322364)。线外的 Rory Johnston 引《金融时报》的正文：快艇把水雷贴到船体，是 2019 年以来第一次；船上的人在水线以上装了两枚爆炸装置：[帖](https://x.com/Rory_Johnston/status/2116211734075621644)。彭博写的是快艇上的人把爆炸物贴到油轮、打坏引擎，并写成当前冲突里第一次这种打法：[帖](https://x.com/business/status/2116195959843479655)。路透的标题是安全消息人士称油轮遭吸附水雷击中：[帖](https://x.com/Reuters/status/2116255103082467635)。FinancialJuice 引 UKMTO：收到一条迟到报告，原油轮在过海峡时遭抛射物击中：[帖](https://x.com/financialjuice/status/2116263478772253152)。First Squawk 周六另有 UKMTO 确认未知抛射物击中原油轮：[帖](https://x.com/FirstSquawk/status/2116396989814620312)。第四艘、两枚装置、一次抛射物，不要加成一个总数。CNBC 的标题是油轮仍在把原油运过海峡：[帖](https://x.com/CNBC/status/2116221578572620027)。

线外的 Javier Blas 引埃克森首席执行官：清洁油品短缺大约三分之一直接来自波斯湾，三分之一来自和中东连着的中国，三分之一来自俄乌，后者他认为还要很久：[帖](https://x.com/JavierBlas/status/2116171411052011880)。他另写美国 8 月原油、凝析油和天然气液合计产量第一次超过每天 2200 万桶：[帖](https://x.com/JavierBlas/status/2116201620921102460)。周六他引伊朗最高领袖穆杰塔巴·哈梅内伊：任何级别的威胁都要立刻、有效、不受地理限制地回应：[帖](https://x.com/JavierBlas/status/2116488582206525568)。Brooks 周六的框架是，市场在给美国恢复空袭伊朗定价。对油价的 30 日滚动相关里，热战回归的对冲是做多美元、尤其对新兴市场货币；标普、黄金、白银是脆弱的一方。布伦特若到 130 美元，法国利差可能走向 200 个基点。黄金周六在他那里已经稳稳低于 4000 美元，是 2026 年第一次；轰炸焦虑过去之后，金价会弹回来：[美元](https://x.com/robin_j_brooks/status/2116460592567349483)、[4000](https://x.com/robin_j_brooks/status/2116445187127812472)、[法国](https://x.com/robin_j_brooks/status/2116458921489797464)。

黄金和白银的盘中数字比收盘句子小。Schiff 13:16 UTC：黄金跌超过 80 美元，交易在 3940 美元下方，跌破 6 月低点；白银跌超过 2.50 美元，就在 49.50 上方，2026 年第一次低于 50。他当时就写买：[帖](https://x.com/PeterSchiff/status/2116157358925885733)。Kobeissi 13:20 UTC：现货金跌破 3950，现货银跌破 50，白银是 2025 年 11 月以来第一次低于 50：[帖](https://x.com/KobeissiLetter/status/2116158382881038840)。Hedgeye：黄金跌 2.2%，到 4000 下方：[帖](https://x.com/Hedgeye/status/2116162005140938816)。Bespoke：黄金 ETF 较 1 月高点回撤 27.4%：[帖](https://x.com/bespokeinvest/status/2116165599038742696)。Schiff 收盘后把当天写成黄金跌近 150 美元、白银跌超过 3 美元，归因于短期流动性，并写成下周可能出现在更广的市场里，同时仍是买入：[帖](https://x.com/PeterSchiff/status/2116273530505482435)。80 美元、150 美元、跌破 3940、跌破 3950、低于 4000，按时间分开。Andy Constan 收盘后写，债券是当天最好的，黄金反而是最差的：[帖](https://x.com/dampedspring/status/2116263508396695657)。

比特币是另一条。Anthony Pompliano：币安被黑客攻击 60 亿美元，比特币只跌了不到 5%，他写成看多：[帖](https://x.com/APompliano/status/2116148361707589805)。Kobeissi 写，即便发生了加密历史上最大的黑客事件，比特币这周跌幅仍小于 5%：[帖](https://x.com/KobeissiLetter/status/2116251100517216634)。60 亿美元是周五这条帖的数字。不到 5% 和“小于 5%”是两句。

## 要盯住的五件事

1. **7580 和 7566 是两条已经写出来的线。** First Squawk 的非官方标普是 7578.14，跌 1.84%。Bespoke 的收盘是 7580.07。SpotGamma 把收在 7566 以下写成单日跌 2%。纳斯达克综合指数的非官方收盘是 25438.40，跌 2.85%。纳斯达克 100 的盘中到过跌 4.2%，也到过较 10 月 6 日高点跌 10% 的说法。QQQ 的 200 日在 RedDog 那里是 684 到 685。
2. **英特尔的收盘帖是 28.5% 和 29%，不是盘中的 31%。** 美银目标价 100 美元，中性。5 年期信用违约互换盘中到过 123.5 个基点。政府持仓成本大约 20.47 美元，6 月高点 142.35 美元。SOXX 盘中跌近 10%，SOXL 盘中跌 28%，都还不是收盘百分比。
3. **亚马逊没有一张收盘跌幅帖。** 盘中 Gary 写跌 3%，开盘统计是跌 4% 以上。资本开支 773 亿美元对 588 亿美元，2026 年维持 2200 亿美元。供应商融资最多 800 亿美元，使用窗口是 2027 年到 2028 年三季度。AWS 增 39% 和未来两年增 40% 是 Stephanie 和 firstadopter 的句子。积压 5780 亿美元是电话会引文。
4. **117.64 美元和 90.40 美元不要写成同一个油价。** WTI 结算 104.12 美元。布伦特结算 117.64 美元。90.40 美元是银行对 2026 年均价的调查。霍尔木兹同时有水雷、吸附水雷、抛射物和“第四艘”几种说法。Brooks 把布伦特 130 美元写成法国利差走向 200 个基点的条件。黄金在他那里低于 4000；Schiff 收盘后写成跌近 150 美元。
5. **12 月加息的 75% 是收盘后的句子。** 早晨 10 年期是 4.927%，Gary 下午是 4.94%。就业成本指数 0.8%，符合预期。芝加哥 PMI 55.3，不及预期。Logan 仍要两次加息，Musalem 说要快，Barkin 说方向清楚、节奏渐进。中国官方制造业 PMI 已经是 49.3。中期选举在下一周：[Bespoke](https://x.com/bespokeinvest/status/2116304186841211303)。RedDog 点名的下一周还有就业报告，以及苹果、Palantir、AMD、Arm、高通的财报：[帖](https://x.com/RedDogT3/status/2116271110849474986)。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 周五收盘 | 道指、标普、纳斯达克 | 道指收 51763.41，跌 1.11%。标普非官方收 7578.14，跌 1.84%。纳斯达克收 25438.40，跌 2.85%。Bespoke 的标普是 7580.07。Investing.com 的标题是纳斯达克跌 3% | [收盘](https://x.com/FirstSquawk/status/2116259225370493248)、[7580.07](https://x.com/bespokeinvest/status/2116264164482322693) |
| 盘中路径 | 纳斯达克 100、QQQ | 盘中跌 3.6%、3.7%、4.2%，一度写成较 10 月 6 日高点跌 10%。Bespoke 写 9.55%，离调整还差几档。收盘后只确认是 6 月以来最差的一天 | [4.2%](https://x.com/KobeissiLetter/status/2116235618984538493)、[9.55%](https://x.com/bespokeinvest/status/2116228872887001308) |
| 位置 | SPX、QQQ | 收在 7566 以下才是单日跌 2%。QQQ 200 日在 684–685。开盘前 QQQ 要看 700 美元支撑 | [7566](https://x.com/spotgamma/status/2116209307335438844)、[200 日](https://x.com/RedDogT3/status/2116237017638117557) |
| 收盘被罚 | INTC | 收盘帖是跌 28.5% 或 29%。盘中到过 30% 和 31%。美银中性，目标价 100 美元。CDS 盘中 123.5 个基点。年内仍涨 67% | [28.5%](https://x.com/RyanDetrick/status/2116263422342160385)、[29%](https://x.com/CNBC/status/2116274978400133507) |
| 盘中、云仍强 | AMZN | 盘中跌 3%。资本开支 773 亿美元对 588 亿美元。2026 年资本开支 2200 亿美元。供应商融资最多 800 亿美元。AWS 增 39%。积压 5780 亿美元 | [Gary](https://x.com/garyblack00/status/2116172920271552719)、[800 亿](https://x.com/business/status/2116257611507020056)、[积压](https://x.com/TheTranscript_/status/2116319301452075213) |
| 信用展望 | META | 标普把展望调到负面。杠杆可能超过 1.0 倍。自由经营现金流为负的时间可能更长。诉讼和解是另一条帖 | [展望](https://x.com/KobeissiLetter/status/2116280985612636573) |
| 融资被砍 | OpenAI、Anthropic | 200 亿美元、估值 1.25 万亿美元，之前是 300 亿美元和 1.4 万亿美元。Anthropic 被写成上市后很可能不是投资级，到 2045 年算力支出超过 8000 亿美元 | [OpenAI](https://x.com/KobeissiLetter/status/2116357848464601125)、[Anthropic](https://x.com/KobeissiLetter/status/2116228648978055455) |
| 空头名单 | QQQ、SPY | QQQ 空头约 8200 万股，2023 年 3 月以来最高，近几周增 28%。SPY 空头较 3 月减少 3000 万股，到约 9200 万股 | [空头](https://x.com/KobeissiLetter/status/2116271956987154764) |
| 半导体盘中 | SOXX、SOXL、SNDK | SOXX 盘中跌近 10%。SOXL 盘中跌 28%。Sandisk 跌到 200 日下方。1225 美元是早盘要看的位置 | [SOXX](https://x.com/bespokeinvest/status/2116228098798887000)、[200 日](https://x.com/TrendSpider/status/2116334348337315988) |
| 十月的另一侧 | XLV、LLY、BRK.B、能源、必需消费 | 医疗 ETF 创历史新高。礼来自 4 月下旬涨 66%。伯克希尔 10 月涨 9%。能源和必需消费 10 月涨超过 10% | [医疗](https://x.com/Hedgeye/status/2116173709191045161)、[十月](https://x.com/bespokeinvest/status/2116301443632398814) |
| 市值换位 | AAPL、NVDA | 苹果周五重新成为全球市值最高的公司，从英伟达手里拿回位置 | [苹果](https://x.com/business/status/2116268642522316913) |
| 油、金、银 | WTI、布伦特、黄金、白银 | WTI 结算 104.12 美元。布伦特结算 117.64 美元。黄金盘中跌破 3940 和 3950，周六被写成 2026 年第一次稳在 4000 下方。白银跌破 50 | [WTI](https://x.com/FirstSquawk/status/2116236578456809803)、[布伦特](https://x.com/FirstSquawk/status/2116241855419703583)、[4000](https://x.com/robin_j_brooks/status/2116445187127812472) |

## 后续走势：三套可以证伪的剧本

帖文没有给下周一的收盘点位。周五写下来的现货收盘是标普 7578.14 或 7580.07、纳斯达克 25438.40、道指 51763.41。下面三套的顺序，以英特尔收盘帖仍在跌大约 29%、布伦特结算留在 117.64 美元、12 月加息概率被写成 75% 为前提。

**等权把指数接在 5 月的位置上，英特尔留在单个公司的事件里。** 触发器是标普留在 7580 一带，并且留在 7566 之上，医疗、能源和必需消费继续是 10 月上涨的那一组，苹果继续被当成人工智能开支担忧里的避风港。这条路径上，市场交易的是等权创下 2009 年以来相对市值加权最强的一个月、礼来和伯克希尔创历史新高、AWS 增 39%。Bespoke 的“标普五个月走回原地”站在这一侧。若 QQQ 收破 684–685 的 200 日，并且 SOXX 盘中接近 10% 的跌幅在周一扩散到已经双超的名字以外，这条路径失败。

**资本开支、融资和供应商一起被罚，7566 先被打穿。** 触发器已经写在收盘后：OpenAI 把融资从 300 亿美元砍到 200 亿美元，Anthropic 被写成拿不到投资级，Meta 展望负面，亚马逊安排最多 800 亿美元供应商融资，英特尔信用违约互换盘中扩到 123.5 个基点。Kobeissi 把 12 月加息写成 75%。Keith 的实盘警报多头名单是空的：[帖](https://x.com/Hedgeye/status/2116195160476283377)。VIX 升过 19 之后他把标普的风险区间信号写成已经爆掉：[帖](https://x.com/KeithMcCullough/status/2116244688852177158)。这条路径失败的条件，是就业成本指数 0.8% 的符合预期压过 75% 的口号，10 年期留在 4.94% 附近而不是回到 9 月 30 日的 5.3%，并且亚马逊按 Stephanie 的 15 倍和 AWS 增 39% 被买回去。

**117.64 美元的布伦特留在结算价上，热战定价压过黄金。** 触发器是布伦特守住 117.64 美元，同时 Brooks 写热战回归在未来几天是可能的：[帖](https://x.com/robin_j_brooks/status/2116460592567349483)。这条压过德国 CPI 2.8% 带来的欧洲央行加息压力减轻。他的对冲是做多美元对新兴市场，标普、黄金、白银在热战回归时是脆弱的。布伦特到 130 美元，是法国利差走向 200 个基点的条件。它失败的条件，是油价回到周四结算 114.88 美元以下，霍尔木兹的几种说法没有被交易成新的战役，而且黄金按 Brooks 自己的后半句、在轰炸焦虑过去之后反弹。Schiff 的买入点更早：他在黄金还被写成跌近 150 美元时就叫买。两个人的黄金句子不是同一个时点。

另有一条季节统计，不并进上面三套。Sentimentrader 周六写，从 10 月 28 日收盘到 11 月 4 日这个窗口，77 年里涨幅至少 3% 的次数对跌幅至少 3% 的次数是 15 比 2；2022 年同一个窗口收跌 2.3%。他写成倾向，不是承诺：[帖](https://x.com/sentimentrader/status/2116485346733305876)。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照下周一的开盘。它不决定仓位大小。周六现货不开市。

**开盘前只核对五样东西。** 标普期货还在不在 7580 之上、还是已经到 SpotGamma 的 7566；英特尔的跌 28.5% 或 29% 是维持，还是继续走向盘中那张 31% 的帖；布伦特是停在 117.64 美元，还是回到 114.88 美元；10 年期还在不在 4.94%，12 月加息概率还在不在 75%；医疗和必需消费是跟着 10 月的涨幅走，还是跟着纳斯达克的单日跌幅走。五样里油价留在结算价以上、英特尔守住大约 29% 的跌幅、QQQ 空头维持在大约 8200 万股，这些帖给出的默认顺序是融资敏感的人工智能信用和已经在跌的半导体，低于炼油、医疗和 Keith 仍放在多头上的油与航运。油价回到 114.88 美元、标普守住 7580、亚马逊按 AWS 增速被买，默认顺序掉过头来：云的积压高于去追从高点已经跌了 20% 以上的那张名单。

**已经公开的方向，按账号而不是按共识。**

- Gary Black，线外：盘中纳斯达克 100 跌 3.7%。英特尔跌 30% 是当时的快照，四季收入指引弱，个人电脑出货疲弱。亚马逊跌 3%，线上同比只增 2%，资本开支 773 亿美元对 588 亿美元。10 年期 4.94%，从 9 月 30 日的 5.3% 降下来：[帖](https://x.com/garyblack00/status/2116220018018955433)、[亚马逊](https://x.com/garyblack00/status/2116172920271552719)。
- Keith McCullough，线外：周六的标题是人工智能泡沫在干净利落地破裂：[帖](https://x.com/KeithMcCullough/status/2116471604624413131)。实盘警报的多头名单是零：[帖](https://x.com/Hedgeye/status/2116195160476283377)。宏观前十里两个多头是航运和油，其余是空头：[帖](https://x.com/KeithMcCullough/status/2116249131865854324)。VIX 升过 19 之后标普风险区间被写成爆掉：[帖](https://x.com/KeithMcCullough/status/2116244688852177158)。医疗 ETF 继续多头：[帖](https://x.com/Hedgeye/status/2116173709191045161)。黄金早盘跌 2.2% 到 4000 下方：[帖](https://x.com/Hedgeye/status/2116162005140938816)。原油这个月涨 12.5%：[帖](https://x.com/Hedgeye/status/2116171247910522895)。
- Robin Brooks，线外：热战回归的对冲是做多美元对新兴市场。标普、黄金、白银脆弱：[帖](https://x.com/robin_j_brooks/status/2116460592567349483)。布伦特 130 美元对应法国利差可能到 200 个基点：[帖](https://x.com/robin_j_brooks/status/2116458921489797464)。黄金低于 4000 是 2026 年第一次；焦虑过去之后金价会反弹：[帖](https://x.com/robin_j_brooks/status/2116445187127812472)。他没有给周一的标普点位。
- Nick Timiraos，线外：Logan 仍要两次加息，跳过一次会议不改变目的地：[帖](https://x.com/NickTimiraos/status/2116222283954168289)。Musalem 说进一步收紧有必要而且要快：[帖](https://x.com/NickTimiraos/status/2116206415534563715)。Barkin 说方向清楚、节奏渐进：[帖](https://x.com/NickTimiraos/status/2116171320341713253)。就业成本指数的工资同比 3.1%：[帖](https://x.com/NickTimiraos/status/2116150942093410559)。没有新的概率表。
- Kobeissi：收盘后把 12 月加息写成 75%：[帖](https://x.com/KobeissiLetter/status/2116261977559544282)。纳斯达克 100 盘中进入较 10 月 6 日高点跌 10% 的调整，这条是下午 3 点的句子：[帖](https://x.com/KobeissiLetter/status/2116243866718523645)。QQQ 空头约 8200 万股：[帖](https://x.com/KobeissiLetter/status/2116271956987154764)。三季度标普混合盈利增速 30.2%，纳斯达克 100 年内仍涨 11%、较 2025 年 4 月低点涨近 70%：[帖](https://x.com/KobeissiLetter/status/2116251100517216634)。OpenAI 融资降到 200 亿美元：[帖](https://x.com/KobeissiLetter/status/2116357848464601125)。他们没有给周一的标普目标。
- Jim Cramer：周五是股票末日：[帖](https://x.com/jimcramer/status/2116242687993188690)。月末平仓，或者有人说到选举后再见：[帖](https://x.com/jimcramer/status/2116243921126686966)。亚马逊在下午跑赢纳斯达克 100：[帖](https://x.com/jimcramer/status/2116252405784617023)。他发过“buy”和“tech”两张图，正文没有把股票代码写出来：[buy](https://x.com/jimcramer/status/2116177685546189163)、[tech](https://x.com/jimcramer/status/2116165009898135567)。
- Bespoke，线外：标普收 7580.07，和 5 月收盘差一美分：[帖](https://x.com/bespokeinvest/status/2116264164482322693)。等权是 2009 年 4 月以来相对市值加权最强的一个月：[帖](https://x.com/bespokeinvest/status/2116286212340342990)。QQQ 较高点跌 9.55%：[帖](https://x.com/bespokeinvest/status/2116228872887001308)。SOXX 盘中跌近 10%：[帖](https://x.com/bespokeinvest/status/2116228098798887000)。亚马逊是第 40 次财报后开盘跌 4% 以上：[帖](https://x.com/bespokeinvest/status/2116183401631781193)。中期选举下一周，他的历史句子是不要用政治决定仓位：[帖](https://x.com/bespokeinvest/status/2116304186841211303)。
- SpotGamma，线外：7566 是跌 2% 的收盘线：[帖](https://x.com/spotgamma/status/2116209307335438844)。开盘时期货跌 80 点：[帖](https://x.com/spotgamma/status/2116150457462853793)。科技传染是风险，因为轮动把标普托住了：[帖](https://x.com/spotgamma/status/2116143508881117590)。没有新的指数目标价。
- The Transcript，线外：三家云积压大约 1.8 万亿美元。亚马逊积压 5780 亿美元：[帖](https://x.com/TheTranscript_/status/2116319301452075213)。
- Stephanie Link，线外：亚马逊反应过重，AWS 增 39%，她写 15 倍市盈率：[帖](https://x.com/Stephanie_Link/status/2116146031696167378)。盈利季节到目前每股收益增 25.6%，总收入增 12%：[帖](https://x.com/Stephanie_Link/status/2116282985834225961)。联合健康是她点名的医疗交易：[帖](https://x.com/Stephanie_Link/status/2116254752820347142)。
- Peter Schiff：黄金跌近 150 美元时叫买，并把这写成短期流动性，下周可能蔓延：[帖](https://x.com/PeterSchiff/status/2116273530505482435)。民主党拿下参议院的概率在他那里是 71%。若周一股市崩盘，这个概率还会上升：[帖](https://x.com/PeterSchiff/status/2116301965563220461)。这是参议院 71%，和 Kobeissi 盘中把民主党横扫写成从 65% 到 72% 不是同一条帖：[帖](https://x.com/KobeissiLetter/status/2116240066142154894)。
- Andy Constan，线外：仍是做多债券、做空股票。债券可能已经完成了大部分任务：[帖](https://x.com/dampedspring/status/2116165912390938690)。黄金是当天最差的：[帖](https://x.com/dampedspring/status/2116263508396695657)。10 日实现波动率年化 14%。买 15 到 20 的指数隐含波动率是过去六个月的痛点：[帖](https://x.com/dampedspring/status/2116278011393724502)。
- Javier Blas，线外：炼油和柴油仍是主题，短缺被埃克森分成波斯湾、中国和俄乌三块：[帖](https://x.com/JavierBlas/status/2116171411052011880)。美国 8 月液体产量第一次超过每天 2200 万桶：[帖](https://x.com/JavierBlas/status/2116201620921102460)。周六的伊朗引文是不受地理限制的回应：[帖](https://x.com/JavierBlas/status/2116488582206525568)。他没有给新的油价目标。
- Mark Minervini：空头有效，多头还撑着：[帖](https://x.com/markminervini/status/2116236435674042691)。英特尔用的是他的 50/80 规则：[帖](https://x.com/markminervini/status/2116164348854854089)。窗口内没有新的指数点位。
- Ryan Detrick，线外：英特尔跌 28.5%，年内仍涨 67%：[帖](https://x.com/RyanDetrick/status/2116263422342160385)。标普连续两周各跌约半个百分点：[帖](https://x.com/RyanDetrick/status/2116265354016215261)。2.81% 是 2009 年 10 月最后一个交易日的参照，周五非官方收盘是 1.84%：[帖](https://x.com/RyanDetrick/status/2116242207900680458)。
- Andreas Steno，线外：把当天写成像是真正的投降：[帖](https://x.com/AndreasSteno/status/2116249418361876846)。也写成十多年来最大的去杠杆之一：[帖](https://x.com/AndreasSteno/status/2116250977406009734)。另一条是人工智能收入增速在历史上没有可比的东西：[帖](https://x.com/AndreasSteno/status/2116267057297973705)。他没有给点位。
- El-Erian：审的是资本开支、融资、变现和回报。到周五为止，这还没有变成对科技增长前景的重估：[帖](https://x.com/elerianm/status/2116241450912592010)。周六引文是贷款人开始挑项目：[帖](https://x.com/elerianm/status/2116485855594377465)。
- Luke Gromen：美国实际利率到正 2% 时，风险资产和贵金属会跌，这次又发生了：[帖](https://x.com/LukeGromen/status/2116214172379971814)。把联邦债务调进去之后的巴菲特指标在 130%，黄金低于 4000 被他写成有东西要来：[帖](https://x.com/LukeGromen/status/2116179965011951804)。
- Tavi Costa，线外：硬资产的抛售在他看来卖家快没了。沃什是不是只会说，要等东西坏了才知道：[帖](https://x.com/TaviCosta/status/2116272072641187969)。
- firstadopter，线外：亚马逊的 AWS 两年 40% 展望很强：[帖](https://x.com/firstadopter/status/2116188507144339754)。Anthropic 对 SpaceX 的评级比较，他站在 Anthropic：[帖](https://x.com/firstadopter/status/2116230997423567170)。
- Eric Balchunas：窗口内没有指数点位。一条是韩国财经账号在用三倍做多半导体 SOXL，也用 VOO 和 QQQ：[帖](https://x.com/EricBalchunas/status/2116347125621473285)。
- Michael Burry：10 月 6 日的标普纪录收盘，在他上周的文章里更像 2000 年 3 月，而不是 1980 年以来的其他纪录高点：[帖](https://x.com/michaeljburry/status/2116249765226680751)。周六是一条关于护城河的视频：[帖](https://x.com/michaeljburry/status/2116497128218632428)。没有新的点位。
- Bill Ackman、Raoul Pal、Cathie Wood、Gundlach、Taleb、Chamath、Dalio、Nouriel、Bianco：窗口内没有可引用的新指数或个股方向。Ackman 只有一个词。Raoul 是新书。Cathie Wood 的可见时间线早于窗口。
- 财政部长 Scott Bessent：窗口内的两条是明尼苏达州欺诈调查和租金，不是指数方向。
- 美联储官方账号：窗口内是数据发布和教育日历，没有新的利率句子。利率句子在 Nick 引的委员讲话里。

**财报和数据的顺序。** 先看已经写进价格的文件：英特尔的四季指引和大约 29% 的收盘跌幅，亚马逊的 2200 亿美元资本开支和最多 800 亿美元供应商融资，OpenAI 的 200 亿美元，Meta 的负面展望。再看已经公布的就业成本指数 0.8% 和芝加哥 PMI 55.3。然后才是 Earnings Whispers 列在周一开盘前的那张日历：[帖](https://x.com/eWhispers/status/2116210262160048434)。以及 RedDog 点名的下一周就业报告和苹果、Palantir、AMD、Arm、高通：[帖](https://x.com/RedDogT3/status/2116271110849474986)。抓取结束时这些都还没有新的公布值。

**明确留在观察、不放进计划的东西。** 周六现货不开市，不用期货倒推周一收盘。纳斯达克 100 的跌 4.2% 和较 10 月 6 日高点跌 10% 是盘中帖，综合指数收盘是跌 2.85%。英特尔的 26%、28.5%、29%、30%、31% 按时间留着。亚马逊没有收盘跌幅帖。德意志银行和 Daniel Newman 的时间线没有读到。彭博主号、markets、BBC Business、CNN Business、TradingView、巴菲特账号的时间线对不上这个窗口。Gundlach、Damodaran、Cathie Wood、Chamath、Krugman、Nouriel、Hindenburg、Icahn、Bianco 这次没有可引用的新判断。Kobeissi 的高点回撤百分比不要和周五的涨跌幅相加。币安的 60 亿美元是 Pompliano 周五的数字。中国 PMI 的 49.3 和 49.7 已经公布，不是下周的预测。

## 帖文索引

周五收盘与盘中路径：[纳斯达克 25438.40、标普 7578.14、道指 51763.41](https://x.com/FirstSquawk/status/2116259225370493248)、[标普 7580.07](https://x.com/bespokeinvest/status/2116264164482322693)、[纳斯达克 100 跌 4.2%](https://x.com/KobeissiLetter/status/2116235618984538493)、[较 10 月 6 日高点跌 10%](https://x.com/KobeissiLetter/status/2116243866718523645)、[9.55%](https://x.com/bespokeinvest/status/2116228872887001308)、[7566](https://x.com/spotgamma/status/2116209307335438844)。

英特尔、亚马逊与融资：[跌 28.5%](https://x.com/RyanDetrick/status/2116263422342160385)、[跌 29%](https://x.com/CNBC/status/2116274978400133507)、[目标价 100 美元](https://x.com/StockMKTNewz/status/2116154088945860934)、[CDS 123.5](https://x.com/DeItaone/status/2116173199377408042)、[亚马逊盘中](https://x.com/garyblack00/status/2116172920271552719)、[800 亿美元](https://x.com/business/status/2116257611507020056)、[云积压](https://x.com/TheTranscript_/status/2116319301452075213)、[OpenAI](https://x.com/KobeissiLetter/status/2116357848464601125)、[Meta 展望](https://x.com/KobeissiLetter/status/2116280985612636573)。

利率、油价与日历：[就业成本指数 0.8%](https://x.com/LiveSquawk/status/2116145812757704958)、[10 年期 4.927%](https://x.com/DeItaone/status/2116147497999773727)、[12 月 75%](https://x.com/KobeissiLetter/status/2116261977559544282)、[Logan](https://x.com/NickTimiraos/status/2116222283954168289)、[WTI 104.12](https://x.com/FirstSquawk/status/2116236578456809803)、[布伦特 117.64](https://x.com/FirstSquawk/status/2116241855419703583)、[黄金低于 4000](https://x.com/robin_j_brooks/status/2116445187127812472)、[中国制造业 PMI 49.3](https://x.com/FirstSquawk/status/2116342068817838446)、[QQQ 空头](https://x.com/KobeissiLetter/status/2116271956987154764)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-10-31 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 175 条、彭博商业账号 212 条、FinancialJuice 177 条、零对冲 96 条是读穿窗口后的计数。德意志银行和 Daniel Newman 的 0 是读取失败。沃伦·巴菲特的可见时间线停在 2016 年。彭博经济停在 2026 年 7 月。彭博主号、markets、BBC Business、CNN Business、纽约时报商业、TradingView 的 0 来自对不上这个窗口的时间线。线外的 First Squawk 是 206 条，不在这张表里。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,440,457 | 175 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,324,996 | 97 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,275,660 | 79 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,322,659 | 31 |
| 5 | [@business](https://x.com/business) | 10,488,044 | 212 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,564,205 | 2 |
| 7 | [@FT](https://x.com/FT) | 7,107,053 | 55 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,255,276 | 52 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,391,866 | 9 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,646,909 | 28 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,581,335 | 1 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,424,581 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,356,884 | 30 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,430,802 | 96 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,422,248 | 14 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,039,032 | 1 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 2,997,365 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,710,150 | 16 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,559,194 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,516,100 | 6 |
| 21 | [@chamath](https://x.com/chamath) | 2,479,666 | 3 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,436,887 | 5 |
| 23 | [@BW](https://x.com/BW) | 2,288,255 | 6 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,538 | 24 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,158,034 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,130,568 | 3 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,075,817 | 27 |
| 28 | [@markets](https://x.com/markets) | 2,047,037 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,968,193 | 54 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,793,023 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,773,093 | 10 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,520 | 12 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,709,349 | 1 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,700,809 | 5 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,693,126 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,610,902 | 19 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,601,194 | 3 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,534,009 | 25 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,508,471 | 1 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,470,075 | 6 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,790 | 3 |
| 42 | [@Bloomberg](https://x.com/Bloomberg) | 1,352,900 | 0 |
| 43 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,351,855 | 11 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,247,317 | 3 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,226,363 | 70 |
| 46 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,193,232 | 4 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,193,108 | 4 |
| 48 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,186,066 | 0 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,185,533 | 7 |
| 50 | [@USTreasury](https://x.com/USTreasury) | 1,165,461 | 1 |
| 51 | [@nntaleb](https://x.com/nntaleb) | 1,164,809 | 3 |
| 52 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,160,355 | 40 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,156,857 | 1 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,152,912 | 10 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,141,576 | 2 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,116,652 | 4 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,110,018 | 26 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,096,589 | 4 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,081,495 | 1 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,064,699 | 1 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,606 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,383 | 24 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,003,810 | 2 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 954,429 | 177 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,480 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 935,150 | 14 |
| 67 | [@tradingview](https://x.com/tradingview) | 906,737 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 893,902 | 18 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 890,030 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,729 | 16 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 873,472 | 0 |
| 72 | [@axios](https://x.com/axios) | 861,982 | 24 |
| 73 | [@jpmorgan](https://x.com/jpmorgan) | 859,995 | 0 |
| 74 | [@Citi](https://x.com/Citi) | 853,367 | 0 |
| 75 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 852,903 | 3 |
| 76 | [@HindenburgRes](https://x.com/HindenburgRes) | 848,377 | 0 |
| 77 | [@themotleyfool](https://x.com/themotleyfool) | 840,832 | 1 |
| 78 | [@ecb](https://x.com/ecb) | 830,230 | 2 |
| 79 | [@ARKInvest](https://x.com/ARKInvest) | 822,556 | 1 |
| 80 | [@bgurley](https://x.com/bgurley) | 812,025 | 1 |
| 81 | [@SECGov](https://x.com/SECGov) | 810,463 | 0 |
| 82 | [@economics](https://x.com/economics) | 806,781 | 0 |
| 83 | [@biancoresearch](https://x.com/biancoresearch) | 790,174 | 0 |
| 84 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,227 | 7 |
| 85 | [@leadlagreport](https://x.com/leadlagreport) | 770,100 | 27 |
| 86 | [@markminervini](https://x.com/markminervini) | 767,491 | 2 |
| 87 | [@MorganStanley](https://x.com/MorganStanley) | 758,139 | 2 |
| 88 | [@CNBCnow](https://x.com/CNBCnow) | 752,078 | 0 |
| 89 | [@morganhousel](https://x.com/morganhousel) | 730,253 | 1 |
| 90 | [@TrendSpider](https://x.com/TrendSpider) | 718,800 | 14 |
| 91 | [@CMEGroup](https://x.com/CMEGroup) | 712,149 | 1 |
| 92 | [@Nouriel](https://x.com/Nouriel) | 704,927 | 0 |
| 93 | [@DanielNewman](https://x.com/DanielNewman) | 695,587 | 0 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 673,895 | 7 |
| 95 | [@fundstrat](https://x.com/fundstrat) | 673,254 | 1 |
| 96 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,912 | 1 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 645,957 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,776 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 637,260 | 4 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 627,597 | 2 |