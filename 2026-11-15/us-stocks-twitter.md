# 美股 Twitter 观点日报 · 2026-11-15

周日现货不开。抓取结束时美东大约 5:15。这个窗口没有新的现货收盘点位，股指期货要到周日美东 18:00 才开，所以也没有周日晚间期货。周末真正在交易的是比特币和以太坊：价格从跌破 66,000 美元写到 63,000 美元附近，清算数字按发帖顺序往上加。英伟达这边，请愿从超过 10 万写到超过 12 万，供应链却是两句相反的话。油价没有新的结算价。航班数字有很多张，原因也没有收成一种。这是公开帖文的整理，不是投资建议。

下面每一条归纳都附有帖文链接。

## 抓取口径

- 报告日期按北京时间 **2026-11-15**。触发时刻约 10:00 UTC，时间线补抓到 **约 10:15 UTC（北京时间 18:15，美东周日 5:15）**。美国夏令时已经结束。周日现货不开。股指期货周日美东 18:00 才开，这个窗口里没有周日晚间期货。上一份写下的周四收盘不在这里重算，周五收盘点位上一份也没有写出来，这份同样不补。
- 观察窗口从 **2026-11-14 10:16 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周六大约 5:16 以后、周六白天和晚上，以及美东周日凌晨到大约 5:15。
- X 的官方连接器这次仍然没有搜索和时间线工具。粉丝数用 `https://api.fxtwitter.com/{handle}`。时间线用 `/2/profile/{handle}/statuses`，空 404 要原请求重试。全站搜索这次仍是空 404，不能当成全站讨论。抓取结束时趋势是 AO3 IS BACK、Hokit、`#UFC334`、Gane、Jeremy culhane，美国地区多了一条 beamer。没有美股代码。
- 不存在官方的“美股 Top 100”。这次沿用上一份已经排过的金融候选，并补了紧贴截止线的账号，成功读到粉丝数之后重新排序。用来排序的账号截止在 Eric Balchunas（625,614）。前 100 的账号集合和名次都和 11 月 14 日那份相同，没有对调。Morning Brew（594,173）第 101。Bloomberg Opinion 的 `@opinion`（586,434）第 102。Gary Black（586,102）第 103。Barchart（580,174）第 104。Cboe（579,344）第 105。First Squawk（579,215）第 106。排序不代表预测准确度。
- 100 个账号里，**63 个**在窗口内有按帖文链接去重后、且接口没有标成回复或转发的原创帖。路透读穿窗口，123 条。彭博商业账号 76 条。《经济学人》77 条。《华尔街日报》51 条。The Street 48 条。零对冲 43 条。FinancialJuice 40 条，可见时间线最新一条停在周日 00:27 UTC，读穿到了窗口起点之前，所以 40 不是分页中途停住。CNBC 28 条。《金融时报》19 条。unusual_whales 第一次整页 404，慢速重试后读穿，17 条。线外的 First Squawk 原创 168 条，读穿窗口。德意志银行的时间线仍是读取失败，表里的 0 不是确认沉默。LiveSquawk 的可见时间线最新帖仍早于窗口，停在 11 月 13 日。彭博主号、markets、BBC Business、CNN Business、Cathie Wood、克拉默、美联储、Nick Timiraos、Liz Ann、美国银行、欧洲央行、沃伦·巴菲特，窗口内没有计为原创的新帖；这些号读到的页面都早于窗口，不是这次的读取失败。

## 现货不开，周末行情代码不是收盘

线外的 First Squawk 在周日 08:07 UTC 发了一行周末行情：`#DAX 26710 -0.24%`，`#DOW 52120 -0.27%`，`#NASDAQ 27603 -0.82%`，`#FTSE 10880 -0.16%`，`#HANGSENG 23673 -0.21%`，`#EURUSD 11025 +0.03%`，`#GOLD 3840 -1.16%`，`#SILVER 4780 -2.14%`，`#USOIL 8830 +0.50%`：[帖](https://x.com/FirstSquawk/status/2121877675774271698)。这是他的代码行，不是现货收盘。`#NASDAQ 27603` 不能写成纳斯达克综合指数。`#GOLD 3840` 配上 -1.16%，也不换算成黄金现货 3,840 美元。`#USOIL 8830` 不换算成新的原油结算价。上一份的 WTI 结算 88.56 美元和布伦特结算 95.84 美元不在这行里重写。

同一分钟稍早，他的加密代码是另一行。`#Bitcoin 63970.00 -0.68%`，`#Ether 1782.40 +0.52%`：[帖](https://x.com/FirstSquawk/status/2121877267202908410)。63,970 美元是这行代码里的比特币，下面还有更早和更晚的价，不取中间值。

这个窗口里没有人写出周五或周六的美股现货收盘点位。周日晚间期货还没开。

## 英伟达：请愿在加，供应链是两句

请愿按时间留着，不并成一个总数。Kobeissi 周六 17:00 UTC：超过 100,000 个签名，其中超过 53,000 个股东、6,200 名现任和前任员工；请愿开始后的头 24 小时里，将近 15% 的员工签了；董事会还没有评论：[帖](https://x.com/KobeissiLetter/status/2121649553287864472)。unusual_whales 17:09 UTC 写成超过 100,000，超过 53,000 个签名者称自己是股东，6,200 人称自己是现任或前任员工：[帖](https://x.com/unusual_whales/status/2121651845173039406)。线外的 First Squawk 周日 00:02 UTC 引 TSI：请愿超过 120,000：[帖](https://x.com/FirstSquawk/status/2121755567928864844)。线外的 Barchart 周日写成超过 100,000，包括马斯克：[帖](https://x.com/Barchart/status/2121830393632493872)。100,000 和 120,000 是两个时刻。15% 只在 Kobeissi 这句里。

Kobeissi 更早的立场是董事会还能改。辞职满 48 小时，职务是首席执行官、总裁和董事。他说司法部长、中情局、国家情报总监和众议院情报委员会的成员都表示，现有证据还不能确定黄仁勋是否卷入了和一名中国间谍的关系。董事会有义务公开承认，调查做完之前他可以回来。个人生活不自动决定职务，除非调查确立了国家安全方面的不当行为：[帖](https://x.com/KobeissiLetter/status/2121582019138171310)。稍后他引《华盛顿邮报》：这一串事情是国务卿鲁比奥“启动”的。备忘录来自一份中情局报告，被他用自己的措辞重写，然后泄露。辞职发生在泄露之后 6 天。鲁比奥拒绝对自己的角色回答记者：[帖](https://x.com/KobeissiLetter/status/2121739849388425605)。零对冲的标题是中情局并没有被说服，所以鲁比奥改写了他们的备忘录：[帖](https://x.com/zerohedge/status/2121626821502320731)。另一条标题引萨克斯：把黄仁勋拿下，是因为开源；Anthropic 的“安全派”盟友想让政府对模型和芯片有完全的控制：[帖](https://x.com/zerohedge/status/2121755174871900235)。线外的 Jesse Cohen 把这写成传闻：政府里的对华鹰派，主要是鲁比奥以及国家安全委员会和商务部的官员，用间谍指控当掩护，因为黄仁勋被视为过于亲华、游说放松对北京的出口管制，也支持开源模型。他的推论是，最大的辩护者走了之后，对华芯片限制会更快收紧：[帖](https://x.com/JesseCohenInv/status/2121703426367324163)。“证据还不能确定”“中情局没被说服”“用指控当掩护”是三句，不要收成已经认定或已经洗清。

CNBC：两位大投资者敦促董事会考虑“黄仁勋可能回来”：[帖](https://x.com/CNBC/status/2121660005782851823)。《金融时报》：黄仁勋倒台之后，英伟达可能面临诉讼：[帖](https://x.com/FT/status/2121565390526402623)。路透经线外的 firstadopter：黄仁勋向包括总法律顾问 Tim Teter 和首席营销官 Alison Wagonfeld 在内的几位公司领导，误述了和中国商人 Alice Huang 的关系性质。10 月的两条信息说这些往来是和客户的通常业务。另一些信息说和 Megaspeed 的往来是例行的。他还讨论过对《纽约时报》采取法律行动：[帖](https://x.com/firstadopter/status/2121586714091089940)。《华盛顿邮报》经同一账号：黄仁勋仍在参与这个过程，并至少给一位潜在候选人打过电话。Tae Kim 说他在公司里戴太多顶帽子，很难替换；能不能留下 Ian Buck、Jonah Alben 和临时首席执行官 Colette Kress，会决定一部分前景。“董事会现在就得把他们锁定”：[帖](https://x.com/firstadopter/status/2121649412552134723)。路透周日：Megaspeed 说 Alice Huang 在 2025 年 8 月已经离开公司：[帖](https://x.com/Reuters/status/2121896007763931533)。CNBC 的标题是同一句，并写公司对相关报道启动了内部调查：[帖](https://x.com/CNBC/status/2121882300199674268)。unusual_whales：新加坡当局 2025 年 6 月扣下了当时的 Megaspeed 首席执行官 Alice Huang 的护照，扣了八个月：[帖](https://x.com/unusual_whales/status/2121611048230785063)。

供应链不要收成一句。线外的 firstadopter：未来两年的供应链基本上已经锁死，多名高管层在亚洲建了几十年的关系，没有黄仁勋供应链也会没事：[帖](https://x.com/firstadopter/status/2121659688030806436)。DeItaone 引马斯克，方向相反：黄仁勋把供应链运转得很漂亮，但那些关键协议里有很多是和他本人的握手，不是书面合同；没有他，至少有一部分关键协议会丢：[握手](https://x.com/DeItaone/status/2121614295695757475)、[会丢](https://x.com/DeItaone/status/2121614381436051636)。“会没事”和“至少丢掉一部分”并列。

周线和连跌也不并。线外的 Bespoke 写的是周五下午交易时已经跌了 14%，处在去年夏天以来的最低；从 10 月初到谷底大约 40%，其中大部分发生在他上周末承认那些关系之前。这是连续第六周下跌，和他的记录里另外三段并列第二长。最长的一段是七周，结束于 2008 年 7 月。标普这一周上涨刚刚超过 2%，英伟达当时看上去会跑输指数超过 16 个百分点，是 2018 年 11 月以来最弱的相对表现。员工大约 42,000 人。他引用的一篇 5 月雅虎文章写，大约 50% 的员工净资产超过 2,500 万美元，并写这个比例现在显然更低了。离职率 3.7%，科技行业平均 21.9%。他说下周财报时，投资者会看销售和指引，往后几个季度更该看的是有多少员工决定留下：[帖](https://x.com/bespokeinvest/status/2121716161079292200)。14% 是他写的“这一周”，时间点是“周五下午”。40% 是 10 月初以来的峰谷。16 个百分点是相对标普。线外的 Barchart 把连续六周写成 2012 年以来最长：[帖](https://x.com/Barchart/status/2121712006545674612)。“并列第二长、最长是 2008 年 7 月的七周”是 Bespoke。“2012 年以来最长”是 Barchart。两句都留着。Barchart 另有一条，经零对冲：估值掉到 13 年来最便宜：[帖](https://x.com/Barchart/status/2121864451821383827)。The Street 的正文写，芯片巨头的业绩应该会让人惊叹，但问题是刚看到股价从 10 月以来跌了 33% 的投资者，能不能忘掉首席执行官的离开：[帖](https://x.com/TheStreet/status/2121838144211325194)。33% 是 The Street。14% 是 Bespoke 的这一周。40% 是峰谷。不要收成一个回撤。

线外的 Keith：周五有人在追 165 美元的当日到期期权，收盘时期权在价外，正股在 162 美元：[帖](https://x.com/KeithMcCullough/status/2121582695822057604)。162 美元是他写的那张期权收在价外时的正股，不是交易所的官方收盘稿。他把请愿写成为了让股票涨回去，钱压过了道德：[帖](https://x.com/KeithMcCullough/status/2121662692985565431)。线外的 The Market Ear：信用市场拒绝为这些事定罪，英伟达五年期 CDS 过去两周停在原地：[帖](https://x.com/themarketear/status/2121603305222602885)。

《福布斯》：扎克伯格、迈克尔·戴尔和埃文·斯皮格尔有多数投票权，黄仁勋没有，所以他更容易失去对公司的控制：[帖](https://x.com/Forbes/status/2121596517954031892)。同一天的另一篇写，几天前英伟达还像打不破的堡垒，现在 AMD 和 Cerebras 准备挤进来：[帖](https://x.com/Forbes/status/2121702216772030552)。The Street 的链接路径写 Cathie Wood 买入下跌的半导体股 1,530 万美元、另一只人工智能股票 1,500 万美元、Alphabet 1,720 万美元。帖文正文只说这是她的最新动作，没有把金额写进句子里：[英伟达](https://x.com/TheStreet/status/2121581447093924170)、[人工智能股票](https://x.com/TheStreet/status/2121589067913596947)、[Alphabet](https://x.com/TheStreet/status/2121619234207736299)。Cathie Wood 自己的账号这个窗口没有新帖。另一条 The Street 的链接路径是 `nvidia-stacy-rasgon-200-target`，正文只写“一个意外的决定改变了整个前景”，没有写出 200 美元：[帖](https://x.com/TheStreet/status/2121898531753468189)。

## 比特币按时间往下写，清算数字是先后两张

价格按发帖时间留着。StockMKTNewz 15:17 UTC：回到 66,000 美元下方：[帖](https://x.com/StockMKTNewz/status/2121623671689376032)。Kobeissi 15:37 UTC：跌破 66,000 美元，以太坊跌破 1,850 美元，60 分钟里杠杆头寸清算 2.15 亿美元：[帖](https://x.com/KobeissiLetter/status/2121628482019229844)。FinancialJuice 20:57 UTC：下跌 5.3%，到 64,733.68 美元：[帖](https://x.com/financialjuice/status/2121709041756041726)。Kobeissi 21:27 UTC：跌破 65,000 美元，以太坊跌破 1,750 美元，24 小时清算 18 亿美元，加密货币市值这一周抹掉 3,300 亿美元：[帖](https://x.com/KobeissiLetter/status/2121716781534314731)。22:19 UTC：今天跌了 5,000 美元，三天跌了 11,000 美元；24 小时清算正式跨过 20 亿美元；过去 4 小时超过 9 亿美元；10 月 6 日以来市值抹掉 8,000 亿美元；自 2025 年 10 月的纪录高点以来，加密货币总市值已经抹掉一半以上：[帖](https://x.com/KobeissiLetter/status/2121729777891496181)。2.15 亿、18 亿、20 亿、4 小时的 9 亿是四个时点，后面的数包含更长的窗口，不要相加。TrendSpider 22:31 UTC：跌破 64,000 美元，自 10 月初以来下跌超过 25%：[帖](https://x.com/TrendSpider/status/2121732859073577131)。APompliano 23:02 UTC：极端恐惧出现在 63,000 美元一枚的时候：[帖](https://x.com/APompliano/status/2121740704850624586)。StockMKTNewz 周日 01:10 UTC：回到 63,000 美元下方：[帖](https://x.com/StockMKTNewz/status/2121772800776253830)。First Squawk 08:05 UTC 的代码是 63,970.00 美元，-0.68%。66,000、65,000、64,733.68、64,000、63,970、63,000 按账号和时间留着。

回撤的分母也不并。Bianco：自 9 月 21 日高点 87,381 美元下跌超过 25%，回吐了 7 月 1 日低点 57,742 美元以来涨幅的 70% 以上。那个低点是 2024 年 10 月以来的最低：[帖](https://x.com/biancoresearch/status/2121634244359270883)。线外的 Bespoke：9 月 21 日见顶之后一路向下，回撤接近 20%：[帖](https://x.com/bespokeinvest/status/2121590643889983717)。超过 25% 和接近 20% 是两套。TrendSpider 的超过 25% 是“自 10 月初”，不是自 9 月 21 日。Bilello：2026 年至今比特币 -22%、黄金 -10%，是主要资产里最差的两个，以前任何一个日历年都没同时出现过：[帖](https://x.com/charliebilello/status/2121664864259350975)。Schiff：黄金自中期选举以来只跌 1%，2026 年至今 -10%，2025 年涨了 65%；比特币自中期选举以来 -15%，2026 年至今 -25%，2025 年是 -6.5%：[帖](https://x.com/PeterSchiff/status/2121649198873420191)。-22% 和 -25% 都是年初至今，不要取一个。-10% 的黄金在 Bilello 和 Schiff 两张帖里是同一方向。

仓位按 Bianco 的线程留着。他的主帖写，现货比特币 ETF 加上 Strategy 合计持有大约 10% 的流通比特币，而且再次处在亏损里：[帖](https://x.com/biancoresearch/status/2121646195571294612)。线程回复写 Strategy 持有 850,364 枚，大约 601.2 亿美元；平均买入价 75,820 美元，按当时价格每枚大约亏 10,000 美元：[持仓](https://x.com/biancoresearch/status/2121646208464900494)、[亏损](https://x.com/biancoresearch/status/2121646213313474674)。10,000 美元是每枚，不是总亏损。601.2 亿美元是持仓金额。

周一的句子互相矛盾，而且都还在。Schiff：周一我们会得知 Strategy 回购了大量 STRC，否则股价会低得多；周一抛压还会更大；现金很快会用完，到时只能在抛 MicroStrategy 和抛比特币之间选：[帖](https://x.com/PeterSchiff/status/2121729715534717373)。自托管的人现在就能卖，ETF 持有人要等到周一早上：[帖](https://x.com/PeterSchiff/status/2121771273214914799)。以太坊如果这个周末跌破 1,600 美元，周一可能到 1,000 美元，那对以太坊 ETF 和 BMNR 会是黑色星期一。他写自己 12 小时前的警告之后，以太坊已经又低了 8% 以上：[周一](https://x.com/PeterSchiff/status/2121783906966094222)、[1600](https://x.com/PeterSchiff/status/2121596606617182528)。1,600 美元和 1,000 美元是他的路径，不是现价。现价附近的以太坊是 Kobeissi 的跌破 1,850、跌破 1,750，以及 First Squawk 的 1,782.40。APompliano 的清单是另一套：价格还可以更低；大多数人定额定投好过交易；恐惧与贪婪指数低于 20 的时候买入，历史上算有吸引力；不要把所有的钱放进单一资产；政府不会停止印钞：[帖](https://x.com/APompliano/status/2121790383789052254)。他同一天的播客简介把比特币写成卖到了 69,000 美元，那是节目介绍，不是 23:02 UTC 的 63,000 美元：[简介](https://x.com/APompliano/status/2121618323850858619)。布兰特：如果这是一个成立的头肩顶，他可以搭出一套技术叙事，历史高点已经出现，至少在他有生之年不会再被越过。对数坐标才能给出下跌测量目标，线性坐标会给出一个很大的负数：[头肩](https://x.com/PeterLBrandt/status/2121786054873337951)、[对数](https://x.com/PeterLBrandt/status/2121797865135906830)。他没有在帖文里写出那个目标价。线外的 Barchart：跌破 200 周均线：[帖](https://x.com/Barchart/status/2121691094970704339)。Hanke 把比特币写成没有基本面价值的高度投机资产，并引用了 Kobeissi 的价格帖：[帖](https://x.com/steve_hanke/status/2121660180379447473)。

fundstrat 把最近几周的加密抛售归到几件并列的事：人工智能和半导体、英伟达的下跌触发了保证金追缴，尤其是亚洲散户；即将到来的 Anthropic IPO 是股票的供给冲击，投资者提前卖出好拿钱认购；ANT 在 Robinhood 的零售配售会很重；最近 63 亿美元黑客事件的资金放回了账户，持有人换成现金或稳定币。次要因素是路演在讲人工智能会“打破”一切，以及司法部在审查对亚洲和中国的芯片销售。他的结论仍是加密货币是金融的未来，逆风会过去，以太坊是金融的未来：[帖](https://x.com/fundstrat/status/2121647654614519841)。63 亿美元是这笔黑客资金，不是比特币价格。路透：币安的目标是下周完全恢复提款：[帖](https://x.com/Reuters/status/2121589024133456339)。《金融时报》：特朗普媒体集团面对 10 亿美元的债务压力，比特币押注在褪色：[帖](https://x.com/FT/status/2121594294708371957)。

## 收益率有 5.14% 和 5.15%，流入有 980 亿和 983 亿

El-Erian 把这一周写成：英伟达的领导层动荡、偏鹰的美联储讲话、10 年期收益率触及 5.14%、日元触及 160。股票仍然上涨，经济仍然有韧性：[帖](https://x.com/elerianm/status/2121602528378806364)。5.14% 是他的句子。Brooks 转发的另一张帖写，布伦特这一周结算低了 2.52%，在 95.84 美元，10 年期国债收益率仍跳升 29 个基点，到 5.15%。更便宜的油本该帮到债券。发帖的人把很大一部分归到供给，因为 10 月赤字创了 4,040 亿美元的纪录：[转发](https://x.com/capitaledgenote/status/2121598566368006452)。5.15% 和 +29 个基点是这张转发。5.14% 是 El-Erian。不要收成 5.145%。2.52% 是这一周，不是一张新的周五单日结算。95.84 美元和上一份的周五布伦特结算是同一个价，这张帖给它配的是周涨跌。

Brooks 自己的会议句子是：12 月 9 日议息之前的未知数是收益率曲线的长端。长端收益率的一次跳升，曾让沃什在杰克逊霍尔转鹰，并铺开了现在这条加息路径。只有长端大跌，才会走到 50 个基点：[帖](https://x.com/robin_j_brooks/status/2121594830765912267)。他的订阅者圆桌：预期战争在 2027 年一季度结束，油价落在 75 美元附近；绝大多数看多美元，认为美国在过热，并担心黄金的交易方式：[帖](https://x.com/robin_j_brooks/status/2121663116262174732)。75 美元是 2027 年一季度的结算想象，不是周一的现货。另一帖写共识是 2027 年初结束，而且油价不会一路回到战前：[帖](https://x.com/robin_j_brooks/status/2121591115774312456)。美元最近的走强完全是对 G10，对新兴市场是平的，所以这段对 G10 的跳升会褪掉：[帖](https://x.com/robin_j_brooks/status/2121588422938697869)。这一周是相关性断裂：美元本该跟着油下跌，黄金和白银本该反弹。大致还跟着油走的，是法国 10 年期相对德国国债的利差：[帖](https://x.com/robin_j_brooks/status/2121597136823316893)。

Collins 是另一句。StockMKTNewz 引彭博：柯林斯说，为了把通胀降下来，渐进的加息路径是合适的。她看到价格压力在变广，而且已经高了很久。她此刻觉得稳定、渐进的路径合适，但保持开放：[帖](https://x.com/StockMKTNewz/status/2121674181334974561)。“渐进”是柯林斯。“只有长端大跌才到 50 个基点”是 Brooks。高盛自己的账号没有写出步长。它说这一周的通胀报告高于预测，并让利率产品的联席主管去解释对利率的影响：[帖](https://x.com/GoldmanSachs/status/2121604062571298891)。另一帖是 2027 年展望：在更低的能源价格和持续的人工智能投资之下，预期全球经济稳定增长：[帖](https://x.com/GoldmanSachs/status/2121678077642063918)。彭博商业的标题是，最新的美国通胀报告支持美联储加息，链接路径写的是通胀报告：[帖](https://x.com/business/status/2121556260285751585)。帖文里没有新的 CPI 数字。Kobeissi 的累计 CPI 是另一张：自 2020 年 1 月以来 +30.2%，年化 +4.0%；如果一直按 2% 走，累计只应是 +14.3%，实际高出 15.9 个百分点。CPI 连续 67 个月高于 2%，连续 7 个月高于 3%：[帖](https://x.com/KobeissiLetter/status/2121607597211926983)。30.2% 是六年多的累计，不是这一周的新 CPI。

赤字有两个写法。Bilello：10 月政府支出比收入多 4,040 亿美元，把 12 个月赤字推到 -2.1 万亿美元，是 20 个月来最大：[帖](https://x.com/charliebilello/status/2121669014422491578)。Schiff：10 月联邦赤字 4,041 亿美元。同一句里先写“纪录上最大的 10 月赤字”，又写“现在是纪录上第二大的 10 月赤字”，并写比 2025 年 10 月高 42.1%：[帖](https://x.com/PeterSchiff/status/2121623066652692527)。4,040 亿和 4,041 亿按原帖留着。“最大”和“第二大”是他同一句里的两个短语，这里不替他选一个。

流入也不并。Kobeissi：截至 11 月 11 日的那一周，全球股票基金流入 980 亿美元，是纪录上第二大的单周流入；连续第五周流入，五周合计大约 3,500 亿美元；四周移动平均大约 750 亿美元，是纪录最大。2021 年 meme 股时期的四周平均峰值大约是 450 亿美元。全球股票科技基金那一周流入 26 亿美元，三周合计 91 亿美元。他的结论是投资者在 aggressively 买跌：[帖](https://x.com/KobeissiLetter/status/2121564824760902115)。线外的 Barchart：上周全球股票流入 983 亿美元，是 6 月以来最大：[帖](https://x.com/Barchart/status/2121900567664500901)。980 亿且“纪录第二大”是 Kobeissi。983 亿且“6 月以来最大”是 Barchart。26 亿是科技基金，不是总流入。

零对冲这几条是标题，正文在链接里，这里不补文章。高盛 2027 年剧本：买债券、做空欧元、对冲人工智能的宿醉：[帖](https://x.com/zerohedge/status/2121634373548060793)。美元现在无论好坏都是一笔人工智能交易，2027 年转向之前还有最后一推：[帖](https://x.com/zerohedge/status/2121694769675981236)。对冲基金在 4 月以来最好的芯片反弹里卖出，高盛的科技多空比创纪录低位：[帖](https://x.com/zerohedge/status/2121724974536786283)。Hartnett 维持风险规避，强美元变成“破坏球”：[帖](https://x.com/zerohedge/status/2121824624845414592)。leadlagreport：股票最终得和债券市场达成一致。他的信用轮动已经 credit-off、做多国债，进入第四周：[一致](https://x.com/leadlagreport/status/2121657022827450579)、[第四周](https://x.com/leadlagreport/status/2121615430045348143)。截至 11 月 12 日的记分牌是 JOJO 指数一周 -2.7%、一月 -0.55%、年初至今 -2.0%。标普自该指数 2021 年 6 月启动以来 +91.59%，JOJO 是 -9.25%。这张牌他自己标明了，启动前的结果是回测。

## 能源在创新高的速度，海峡和航班是另外的账

Kobeissi：标普 500 能源板块用 196 个交易日把年初至今的涨幅做到 +50%，是 1990 年以来第五快。2022 年用了 94 天，那是 36 年里最快。科技板块在 1996 年和 1997 年分别用了 133 天和 160 天。可选消费、必需消费、工业、材料和房地产自 1990 年以来从没做过 +50% 的年度涨幅：[帖](https://x.com/KobeissiLetter/status/2121781479910883578)。196 天是能源。133 和 160 是历史上的科技，不是这一周的科技板块。线外的 Keith 站在能源和防守的另一侧表述：做多必需消费和住房，做空高贝塔的 TMT 动量。他写人们还会拿标普 ETF 的“这一周上涨”和“年初至今上涨”来说事，但 2026 年真正的故事是他们追过的那只泡沫；他们还拿着的东西，从 5 月末的峰值到现在年初至今 -16.7%：[做多](https://x.com/KeithMcCullough/status/2121580321263231317)、[-16.7%](https://x.com/KeithMcCullough/status/2121579708139630906)。-16.7% 是“他们还拿着的东西”，不是标普指数本身。线外的 Detrick 指向芯片股这一周一次少见的、可能相当看涨的走势，并把轮动说成牛市里健康的事：[帖](https://x.com/RyanDetrick/status/2121593521710751889)。“做空高贝塔 TMT”和“芯片股这次走势可能看涨”并列。线外的 Sentimentrader：比特币 RSI 模型 11 月 10 日给出离场，趋势分数模型接近跟上。能源跌了 13%，纳斯达克综合指数滑进修正，标普的流动性读数指向未来两到三周回报更弱。长期上升趋势没有破：[帖](https://x.com/sentimentrader/status/2121558775274598766)。13% 是他写的能源跌幅，不是 Kobeissi 的 +50%。

StockMKTNewz 的 2026 年至今翻倍名单有 11 只：Moderna +657.44%，SanDisk +272.82%，戴尔 +173.70%，美光 +172.70%，Marathon Petroleum +154.97%，AMD +149.37%，Valero +133.33%，Bloom Energy +120.96%，Okta +111.48%，Phillips 66 +105.29%，HPE +101.04%：[帖](https://x.com/StockMKTNewz/status/2121657629735096563)。全球前十大股票合计市值 28.43 万亿美元，上周是 28.15 万亿：[帖](https://x.com/StockMKTNewz/status/2121653662808146066)。28.43 和 28.15 是前十大合计，不是标普点位。

油和成品油按帖留着，没有新的原油结算。FinancialJuice 周日 00:27 UTC 引 GasBuddy 的 Patrick De Haan：美国柴油跌到每加仑 6 美元下方，是 9 月以来第一次：[帖](https://x.com/financialjuice/status/2121761916163113330)。路透的标题是美国柴油低于 6 美元，两个月低点，原因写成紧张缓和、需求转弱：[帖](https://x.com/Reuters/status/2121777801292374329)。CNBC：取暖油价格比上个冬天高 59%：[帖](https://x.com/CNBC/status/2121614837335663019)。“低于 6 美元”是柴油现货的标题。+59% 是取暖油相对上个冬天。不要并成同一张价格。线外的 Bespoke：2026 年已经有 192 天全国普通无铅汽油在每加仑 4 美元以上，超过 2022 年的 158 天。2008 年是此前唯一年份有过 4 美元以上的日子。中期选举以来，AAA 全国均价下跌 6.1%，是 2008 年以来选举后最大的跌幅：[192 天](https://x.com/bespokeinvest/status/2121601607217405978)、[6.1%](https://x.com/bespokeinvest/status/2121602166322565510)。6.1% 是选举后的汽油均价跌幅，不是柴油。

海峡的句子按天分开。窗口刚开始，线外的 First Squawk：伊朗海军说一艘油轮在霍尔木兹东部触雷起火。两分钟后：伊朗陆军海军说这是当天第二艘，在限制区触雷起火：[第一艘](https://x.com/FirstSquawk/status/2121547752526278778)、[第二艘](https://x.com/FirstSquawk/status/2121548375019733250)。路透的标题用的是单数：伊朗海军说油轮触雷起火：[帖](https://x.com/Reuters/status/2121630532228293091)。周日 00:24 UTC 和 01:20 UTC，First Squawk 又写成两艘在秘密通过时触雷、两艘都起火：[00:24](https://x.com/FirstSquawk/status/2121761267866361930)、[01:20](https://x.com/FirstSquawk/status/2121775206255804811)。“当天第二艘”是周六上午。“两艘秘密通过”是周日凌晨的另一张。不要和上一份窗口里周五的触雷帖收成同一次。美军中央司令部：海湾伙伴经霍尔木兹运输的石油超过 17 亿桶：[帖](https://x.com/FirstSquawk/status/2121660617140650075)。17 亿桶是这句里的累计运输量，不是一天的流量。线外的 Blas：伊拉克 10 月产量到大约每天 460 万桶，七年高点，低于 2019 年 8 月大约每天 480 万桶的历史高点。出口走霍尔木兹，也走经土耳其的管道和经叙利亚的卡车：[帖](https://x.com/JavierBlas/status/2121586696483676562)。460 万桶是伊拉克产量。周日他又写，巴林说防空系统拦截并摧毁了伊朗周日的多起空中袭击，这是本周第二次：[帖](https://x.com/JavierBlas/status/2121874916551401932)。First Squawk 周日：得到国际承认的也门政府一方说，他们正从曼德海峡一带撤出，伊朗支持的胡塞会控制俯瞰这条航道的地盘：[帖](https://x.com/FirstSquawk/status/2121897213714653459)。Hanke：乌克兰军队打击了俄罗斯萨马拉的一座石油泵站：[帖](https://x.com/steve_hanke/status/2121680061665321141)。曼德海峡、巴林、萨马拉和霍尔木兹是四个地点。

线外的 Ole：美国 CFTC 的持仓报告覆盖到 11 月 10 日，周一美东 15:30 发布，因为上周的联邦假日推迟了。洲际交易所欧洲周五的报告里，布伦特投机净多头下降 26%，到四个月低点的 13.4 万张；柴油净多头降到 5.4 万张，是 6 月以来最低：[帖](https://x.com/Ole_S_Hansen/status/2121897683249930395)。13.4 万张是投机净多头，不是油价。Brooks 写油价已经回到袭击沙特东西管道之前的水平，运价也在降，但还没有完全正常：[帖](https://x.com/robin_j_brooks/status/2121593689109651827)。帖文里没有写出那个管道袭击前的美元价格。印度尼西亚、泰国、菲律宾要建立共享石油储备，日经写这是伊朗战争造成东盟能源短缺之后、由日本牵头的项目：[帖](https://x.com/FirstSquawk/status/2121552305179050207)。

## 航班的数字很多，原因没有收成一种

取消和延误按账号留着。窗口开始后不久，First Squawk：美国当天取消 3,000 班：[帖](https://x.com/FirstSquawk/status/2121554814601666624)。《华尔街日报》14:08 UTC：周五取消超过 9,000 班，周六到发帖时已经取消超过 3,500 班：[帖](https://x.com/WSJ/status/2121606092429918216)。15:53 UTC：周六早些时候将近 3,900 班被取消：[帖](https://x.com/WSJ/status/2121632739816247772)。First Squawk 15:11 UTC 引 FlightAware：当天大约 4,000 班国内和国际航班取消；达美取消预定航班的 20%，美联航 18%，美国航空 15%：[大约 4000](https://x.com/FirstSquawk/status/2121621976032956716)、[三家航司](https://x.com/FirstSquawk/status/2121622022937833865)。路透引达菲：地面停止大约四小时，取消超过 6,600 班；他呼吁国会拿出 500 亿美元紧急资金，更换更老的模拟技术：[帖](https://x.com/Reuters/status/2121616643633947009)。DeItaone：取消或延误超过 22,000 班。周五将近五小时的地面停止带来大约 10,000 班取消和 7,000 班延误。周六另有 3,700 班取消、2,000 班延误：[帖](https://x.com/DeItaone/status/2121642097086193738)。First Squawk 引法新社：周五和周六合计取消超过 16,000 班：[帖](https://x.com/FirstSquawk/status/2121651285913117020)。DeItaone 20:11 UTC 引 FlightAware：周六延误或取消超过 10,000 班：[帖](https://x.com/DeItaone/status/2121697468954153329)。周日凌晨，福克斯经 First Squawk：周六取消班次升到 7,000。FlightAware 经他：周六延误和取消超过 10,000：[7000](https://x.com/FirstSquawk/status/2121818310241374540)、[10000](https://x.com/FirstSquawk/status/2121832692308488633)。3,000、3,500、3,900、4,000、6,600、7,000、9,000、10,000、16,000、22,000 是不同时刻、不同口径。有的只算取消，有的把延误和取消加在一起，有的把周五和周六加在一起。

原因同样分开。达菲经 First Squawk：空中导航系统的关闭不是网络攻击。DeItaone 引他：对系统造成冲击的根因不是外国行为体：[不是网络攻击](https://x.com/FirstSquawk/status/2121640764275089415)、[不是外国行为体](https://x.com/DeItaone/status/2121657411383726261)。CNBC：联邦航空局说全国地面停止的根因未知：[帖](https://x.com/CNBC/status/2121743207025275017)。First Squawk 引 CNBC：调查还没有找出原因：[帖](https://x.com/FirstSquawk/status/2121759257188254205)。路透：达菲说联邦航空局的承包商 L3Harris 在一个远程地点把电信线路从铜缆换成光纤，这次是 2001 年 9 月 11 日以来最长的全国停飞。稍后的标题写成归咎于 L3Harris 安装的路由器：[换光纤](https://x.com/Reuters/status/2121669491969110405)、[路由器](https://x.com/Reuters/status/2121699720749797761)。《华尔街日报》：数据过载发生在一套过时的联邦航空局网络上；另一篇写的是老化的电缆和通信设备：[过载](https://x.com/WSJ/status/2121789416855241075)、[电缆](https://x.com/FirstSquawk/status/2121772073777610949)。“不是网络攻击”“根因未知”“铜缆换光纤”“安装的路由器”“数据过载”是五句。达菲周六上午说航班运行在慢慢恢复正常，旅客仍会看到延误和取消：[帖](https://x.com/FirstSquawk/status/2121602524205711584)。unusual_whales 引美联社：联邦航空局局长说，美国航班时刻表应在周日完全恢复：[帖](https://x.com/unusual_whales/status/2121647623593394182)。“慢慢恢复”和“周日完全恢复”是两句，这个窗口结束时还没有一张帖写出已经完全恢复。

微软服务是旁边的一句。First Squawk：微软说扰乱全球的中断之后，服务已经完全恢复：[帖](https://x.com/FirstSquawk/status/2121569817308418304)。Bill Gurley 把这次软件导致的停飞，和欧盟 12 月 9 日生效的产品责任指令放在一起：软件将第一次承担和实物产品一样的产品责任。他认为美国也应该这么做：[帖](https://x.com/bgurley/status/2121766826631999489)。12 月 9 日在这张帖里是欧盟指令的日期。Brooks 的 12 月 9 日是美联储会议。两个 12 月 9 日不要合成。

## 要盯住的五件事

1. **周日晚间期货还没开，周末代码不是收盘。** First Squawk 08:07 UTC 的 `#DOW 52120`、`#NASDAQ 27603`、`#GOLD 3840`、`#USOIL 8830` 按代码留着。纳斯达克综合指数不在这行里。原油没有新的结算价。柴油标题是跌到 6 美元下方。取暖油是比上个冬天高 59%。
2. **英伟达的供应链是两句。** firstadopter 写未来两年锁死、没有黄仁勋也会没事。马斯克经 DeItaone 写很多关键协议是握手，没有他至少丢掉一部分。请愿在 17:00 UTC 超过 10 万，周日标题超过 12 万。两位大投资者要求董事会考虑他回来。董事会在 Kobeissi 的帖里还没有评论。Kress 仍是临时首席执行官。
3. **比特币的周一卖盘是 Schiff 的句子，不是已经发生的开盘。** ETF 持有人要等到周一。他预期 Strategy 回购了大量 STRC，否则股价会更低，周一抛压更大。以太坊的路径是 1,600 美元然后 1,000 美元。APompliano 写价格还可以更低，同时把恐惧指数低于 20 写成历史上有吸引力的买点。布兰特的头肩顶没有写出目标价。
4. **加息的句子仍是反的。** 柯林斯是渐进。Brooks 是只有长端大跌才到 50 个基点，会议日写成 12 月 9 日。El-Erian 的 10 年期是 5.14%。Brooks 转发的是 5.15%、一周 +29 个基点。高盛自己的帖没有写出 12 月的步长。
5. **这一周被点名的财报还没有结果。** Jesse Cohen 列出的名字是英伟达、Palo Alto Networks、沃尔玛、家得宝、Target、TJX、迪士尼、阿里巴巴、百度、拼多多、京东：[帖](https://x.com/JesseCohenInv/status/2121671130024985054)。这张帖没有写星期几。The Street 把英伟达财报放在下一周，并写股价从 10 月以来跌了 33%。Ole 的持仓报告是周一美东 15:30。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。周末代码不是收盘。周日晚间期货还没开。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 代码，不是收盘 | 道指、纳斯达克、黄金、原油 | 周日 08:07 UTC：`#DOW 52120 -0.27%`，`#NASDAQ 27603 -0.82%`，`#GOLD 3840 -1.16%`，`#USOIL 8830 +0.50%`。不换算成现货收盘 | [代码](https://x.com/FirstSquawk/status/2121877675774271698) |
| 周末价格 | 比特币、以太坊 | 15:17 回到 66,000 下方。15:37 跌破 66,000，以太坊跌破 1,850。20:57 为 64,733.68，-5.3%。21:27 跌破 65,000。22:31 跌破 64,000。23:02 极端恐惧出现在 63,000。周日 01:10 回到 63,000 下方。08:05 代码 63,970.00，以太坊 1,782.40 | [64733](https://x.com/financialjuice/status/2121709041756041726)、[63000](https://x.com/APompliano/status/2121740704850624586)、[63970](https://x.com/FirstSquawk/status/2121877267202908410) |
| 周一路径 | MSTR、STRC、比特币 ETF、ETH、BMNR | Schiff：周一会看到大量 STRC 回购，否则股价会更低；周一抛压更大。ETF 要等到周一才能卖。以太坊若跌破 1,600，周一可能到 1,000 | [STRC](https://x.com/PeterSchiff/status/2121729715534717373)、[1600](https://x.com/PeterSchiff/status/2121783906966094222) |
| 图形 | 比特币 | 布兰特：如果头肩顶成立，历史高点至少在他有生之年不再被越过。没有写出测量目标。Barchart：跌破 200 周均线 | [头肩](https://x.com/PeterLBrandt/status/2121786054873337951)、[200 周](https://x.com/Barchart/status/2121691094970704339) |
| 持仓 | Strategy、比特币 ETF | 850,364 枚，大约 601.2 亿美元，平均买入价 75,820 美元，每枚大约亏 10,000 美元。ETF 加 Strategy 大约占流通量 10% | [10%](https://x.com/biancoresearch/status/2121646195571294612)、[850364](https://x.com/biancoresearch/status/2121646208464900494) |
| 请愿 | NVDA | 17:00 超过 10 万，股东超过 5.3 万，员工 6,200，头 24 小时将近 15% 的员工。周日标题超过 12 万。董事会尚未评论 | [10 万](https://x.com/KobeissiLetter/status/2121649553287864472)、[12 万](https://x.com/FirstSquawk/status/2121755567928864844) |
| 供应链 | NVDA | firstadopter：未来两年锁死，没有黄仁勋也会没事。马斯克：很多是握手，没有他至少丢掉一部分 | [没事](https://x.com/firstadopter/status/2121659688030806436)、[握手](https://x.com/DeItaone/status/2121614381436051636) |
| 周线和峰谷 | NVDA | Bespoke：周五下午这一周 -14%，10 月初以来大约 -40%，连续第六周，并列第二长。Barchart：六周是 2012 年以来最长。The Street：10 月以来 -33%。Keith：165 美元当日期权收在价外，正股 162 美元 | [14%](https://x.com/bespokeinvest/status/2121716161079292200)、[2012](https://x.com/Barchart/status/2121712006545674612)、[162](https://x.com/KeithMcCullough/status/2121582695822057604) |
| 信用 | NVDA | 线外的 The Market Ear：五年期 CDS 过去两周停在原地 | [CDS](https://x.com/themarketear/status/2121603305222602885) |
| 对手 | AMD、Cerebras | 《福布斯》：黄仁勋没有多数投票权。AMD 和 Cerebras 准备挤进来 | [投票权](https://x.com/Forbes/status/2121596517954031892)、[对手](https://x.com/Forbes/status/2121702216772030552) |
| 多空相反 | 能源、必需消费、住房、TMT、芯片 | 能源板块 196 个交易日 +50%。Keith 做多必需消费和住房，做空高贝塔 TMT。Detrick 说芯片这一周的走势可能相当看涨。Sentimentrader：能源 -13%，纳斯达克综合指数进入修正 | [+50%](https://x.com/KobeissiLetter/status/2121781479910883578)、[做空 TMT](https://x.com/KeithMcCullough/status/2121580321263231317)、[芯片](https://x.com/RyanDetrick/status/2121593521710751889) |
| 翻倍 | MRNA、SNDK、DELL、MU、MPC、AMD、VLO、BE、OKTA、PSX、HPE | 2026 年至今都翻倍。美光另有 TrendSpider 的杯形旗形说法，那是产品帖 | [名单](https://x.com/StockMKTNewz/status/2121657629735096563)、[美光](https://x.com/TrendSpider/status/2121654194331648401) |
| 内部人 | COHR | TrendSpider：首席执行官在一年多来最深的回撤里用自己的钱买了大约 100 万美元 | [100 万](https://x.com/TrendSpider/status/2121785258593190062) |
| 市值 | 前十大股票 | 合计 28.43 万亿美元，上周 28.15 万亿 | [28.43](https://x.com/StockMKTNewz/status/2121653662808146066) |
| 标题 | 数据中心建设股 | 《金融时报》：人工智能交易解体，市值损失 4.2 万亿美元。这是标题，不是一张成分股清单 | [4.2 万亿](https://x.com/FT/status/2121834199325737421) |
| 现金流 | GOOGL | unusual_whales 引《华尔街日报》的图：自由现金流二十年来第一次转负，最近两个季度大约 -60 亿美元，然后大约 -90 亿美元 | [转负](https://x.com/unusual_whales/status/2121740208131686571) |
| 支出和收入 | 超大规模云 | Hanke 引达摩达兰：所有人工智能产品一年收入大约 2,500 亿美元。今年四家最大的超大规模云厂商在人工智能数据中心上花费大约 7,250 亿美元 | [2500 亿](https://x.com/steve_hanke/status/2121565053761814888) |
| 增长归因 | 标普里的人工智能 | Hanke：三季度年化增长 3.4%，其中 96% 由人工智能解释，其余经济是平的。3.4% 不是这个窗口的新 GDP 发布 | [96%](https://x.com/steve_hanke/status/2121777705800658952) |
| 需求 | 人工智能本身 | Raoul Pal：这不是 2000 年。买智能的是智能本身，需求是无限的 | [无限](https://x.com/RaoulGMI/status/2121747874782347490) |
| 乐观差 | 用人工智能的小企业 | 美联储银行的小企业信贷调查：预期收入增加减去预期下降，使用人工智能的公司领先 48.2 个百分点，不用的领先 20.6 个百分点 | [48.2](https://x.com/KobeissiLetter/status/2121796579644555475) |
| 就业 | 年轻软件开发者 | 22 到 25 岁自 2022 年 11 月以来 -20%。41 到 49 岁 +20%。ARK 的帖是另一句：预期劳动力短缺，失业率走向 3% 区间，人工智能密集的公司招人更快 | [-20%](https://x.com/KobeissiLetter/status/2121689817301819425)、[短缺](https://x.com/ARKInvest/status/2121601581972107532) |
| 住房 | 成屋、房贷 | 10 月成屋销售环比 -5.5%，年化 375 万套。同比 -8.8%。30 年房贷上个月 7.6%。首次购房者占比 29%，一年前 32% | [375 万](https://x.com/KobeissiLetter/status/2121672047117914373)、[29%](https://x.com/TheStreet/status/2121634366094708907) |
| 这一周的名字 | NVDA、PANW、WMT、HD、TGT、TJX、DIS、BABA、BIDU、PDD、JD | Jesse 只列了代码，没有写星期几 | [名单](https://x.com/JesseCohenInv/status/2121671130024985054) |
| 标题，没有百分比 | LLY、TSLA | 礼来说肥胖药物在临床研究里展示了减重结果。路透：特斯拉邀请部分客户购买 Cybercab 自用。《华尔街日报》的标题是放弃 Cybertruck、押注 Cybercab | [礼来](https://x.com/FirstSquawk/status/2121824760854425813)、[Cybercab](https://x.com/Reuters/status/2121600306739851419) |
| 航司取消比例 | DAL、UAL、AAL | 周六当天：达美 20%，美联航 18%，美国航空 15%。这是 FlightAware 经 First Squawk 的“今天”，不是一周 | [20%](https://x.com/FirstSquawk/status/2121622022937833865) |
| 事件 | SPCX | 星舰被发射塔的机械臂接住。不是股价 | [接住](https://x.com/DeItaone/status/2121719599964225571) |

## 后续走势：三套可以证伪的剧本

抓取结束时是周日清晨，现货不开，周日晚间期货还没开。已经写下来的锚是：没有新的股指现货收盘；First Squawk 的周末代码不能换成综合指数和结算价；比特币从跌破 66,000 美元写到 63,000 美元附近，08:05 UTC 的代码是 63,970 美元；英伟达在 Keith 的句子里，165 美元当日期权收在价外、正股 162 美元；10 年期有 5.14% 和 5.15% 两句；柴油标题在 6 美元下方；原油没有新结算。

**请愿和两位大投资者把英伟达托过周一开盘，芯片的轮动被当成看涨。** 触发器是 Kobeissi 的超过 10 万个签名、CNBC 的两位大投资者、firstadopter 写黄仁勋仍在给潜在候选人打电话而且供应链会没事，以及 Detrick 说芯片这一周的走势可能相当看涨。Kobeissi 同时写全球股票基金一周流入 980 亿美元，投资者在买跌。它失败的条件，是周日晚间期货开盘之后英伟达留在 Keith 写的 162 美元下方，同时马斯克那句“至少丢掉一部分握手协议”变成一张新的客户或供应商标题。

**周末的比特币下跌在周一变成 ETF 和 Strategy 的卖盘，科技股跟着保证金压力走。** 触发器是 Schiff 的周一抛压、ETF 要等到周一才能卖、以太坊 1,600 然后 1,000 的路径，fundstrat 写的亚洲散户保证金追缴，以及 Sentimentrader 写的未来两到三周标普回报更弱。布兰特的头肩顶如果成立，历史高点不再被越过。它失败的条件，是周一比特币重新站上 Kobeissi 21:27 UTC 的 65,000 美元，而不是停在 63,000 美元那一侧，同时英伟达站上 162 美元。APompliano 的“恐惧指数低于 20 历史上有吸引力”是同一套事实的反方向，不并进这套剧本的胜率。

**指数跟着长端收益率和债券市场走，不跟着请愿走。** 触发器是 El-Erian 的 5.14%、转发帖里的 5.15% 和一周 +29 个基点、柯林斯的渐进加息、Brooks 的“只有长端大跌才到 50 个基点”、leadlagreport 的“股票最终得同意债券”，以及零对冲标题里 Hartnett 继续风险规避。油价没有一张新的结算来盖住这个方向。它失败的条件，是 10 年期现货写出一个低于 5.14% 和 5.15% 这两句的数字，同时柯林斯的“渐进”从帖文里消失。75 美元油价和 2027 年一季度结束战争是 Brooks 的订阅者预期，不能用来证伪周一开盘。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周日晚间期货和周一开盘。它不决定仓位大小。抓取结束时，现货不开，周日晚间期货也还没开。

**开盘前只核对五样东西。** 期货是在交易 First Squawk 的周末代码，还是在交易一张还没有出现的现货收盘。英伟达是离开 Keith 写的 162 美元，还是停在那里；165 美元是周五的当日期权行权价，不是目标价。请愿是停在超过 10 万、董事会尚未评论，还是停在超过 12 万，还是停在“黄仁勋打过电话”和“握手协议会丢”这两句里的一句。比特币是重新站上 65,000 美元，还是留在 63,000 到 63,970 这一侧；以太坊的 1,600 美元仍只是 Schiff 的路径。收益率是停在 5.14%，还是停在 5.15%，还是柯林斯的渐进已经变成一张新的概率。五样里，英伟达不把 162 美元当成已经发布的官方收盘、比特币的几个价不取平均、50 个基点仍只是“长端大跌才会走到”的句子，这些帖给出的默认顺序是：先看周一有没有新的永久首席执行官、客户丢掉协议，或者 ETF 的开盘卖盘，再决定这一周的财报名单还值不值得排在前面。期货和比特币一起掉到这些价的下沿，默认顺序掉过头来：先处理 162 美元和 63,000 美元，再决定请愿还剩多少。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：全球股票基金一周流入 980 亿美元，他写成在买跌。请愿超过 10 万，董事会该承认黄仁勋可以回来。比特币从跌破 66,000 写到跌破 65,000，清算从 2.15 亿写到 24 小时跨过 20 亿。能源板块 196 个交易日 +50%。成屋销售年化 375 万套，30 年房贷 7.6%。
- First Squawk，线外：周末代码 `#DOW 52120`、`#NASDAQ 27603`、`#GOLD 3840`、`#USOIL 8830`。比特币代码 63,970.00。请愿标题超过 12 万。周六触雷是“当天第二艘”，周日凌晨是两艘秘密通过。曼德海峡一带在撤出。
- FinancialJuice：比特币 64,733.68 美元，-5.3%。柴油跌到 6 美元下方。可见时间线停在周日 00:27 UTC。
- 零对冲：标题是买债券、做空欧元、对冲人工智能宿醉；对冲基金在芯片反弹里卖出；Hartnett 继续风险规避。这些是标题，不是他自己算出的点位。
- Brooks，线外：12 月 9 日之前看长端。只有大跌才到 50 个基点。订阅者把战争结束放在 2027 年一季度，油价 75 美元附近，看多美元。转发帖里的 10 年期是 5.15%，布伦特周线 -2.52% 到 95.84 美元。
- El-Erian：10 年期触及 5.14%，日元 160，股票仍涨。
- StockMKTNewz：柯林斯要渐进加息。翻倍名单里有美光、AMD、三家炼油和 SanDisk。前十大股票合计 28.43 万亿美元。
- Schiff：黄金 2026 年至今 -10%，比特币 -25%。周一抛压在 Strategy 和比特币 ETF。以太坊路径 1,600 然后 1,000。10 月赤字他写成 4,041 亿美元。
- Bilello：比特币 -22%，黄金 -10%，是 2026 年至今最差的两个主要资产。10 月多支出 4,040 亿美元，12 个月赤字 -2.1 万亿美元。
- Hanke：达摩达兰的人工智能收入大约 2,500 亿美元，对上大约 7,250 亿美元的数据中心支出。三季度增长的 96% 来自人工智能。比特币没有基本面价值。萨马拉泵站被打击。
- Keith，线外：做多必需消费和住房，做空高贝塔 TMT。165 美元期权收在价外，正股 162 美元。他们还拿着的东西年初至今 -16.7%。请愿是为了让股票涨回去。
- Detrick，线外：芯片这一周的走势少见，而且可能相当看涨。轮动是健康的。
- Bespoke，线外：英伟达周五下午这一周 -14%，峰谷大约 -40%，六周连跌并列第二长。比特币回撤接近 20%。汽油 4 美元以上已经 192 天，选举后均价 -6.1%。
- Barchart，线外：六周连跌是 2012 年以来最长。估值 13 年来最便宜。比特币跌破 200 周均线。全球股票流入 983 亿美元。
- firstadopter，线外：供应链会没事。黄仁勋误述了关系，也还在给候选人打电话。要锁定 Buck、Alben 和 Kress。
- Bianco：自 87,381 美元下跌超过 25%。Strategy 850,364 枚，平均价 75,820 美元。
- fundstrat：加密抛售有保证金、Anthropic 认购和 63 亿美元黑客资金这几条。他仍把以太坊写成金融的未来。这个窗口他自己的帖没有写标普年底 8,200。8,200 出现在 Keith 转发的 Doug Kass 帖里，是 Kass 对 Tom Lee 的转述，不是 fundstrat 这个账号的新目标：[转发](https://x.com/DougKass/status/2121578320261152942)。
- Raoul Pal：买智能的是智能本身，不是 2000 年。
- leadlagreport：股票最终得同意债券。信用轮动做多国债，进入第四周。
- Sentimentrader，线外：未来两到三周标普回报更弱，长期上升趋势没破。能源 -13%。
- Ole，线外：布伦特投机净多头 13.4 万张，下降 26%。持仓报告周一美东 15:30。
- Blas，线外：伊拉克大约每天 460 万桶。巴林说周日拦截了伊朗的空中袭击。
- APompliano：63,000 美元处在极端恐惧。价格还可以更低。恐惧指数低于 20 时买入，他写成历史上有吸引力。
- 布兰特：头肩顶如果成立，高点已过。没有目标价。
- Gurley：大型公司董事和高管责任险可以自保。12 月 9 日还有欧盟的软件产品责任，和美联储的 12 月 9 日不是同一件事。
- 高盛主号：通胀报告高于预测，但没有写出数字。2027 年是更低的能源价格加上人工智能投资、全球稳定增长。没有新的指数点位。
- 美联储账号没有新帖，也没有写出 12 月的步长。Cathie Wood 的账号没有新帖。克拉默的账号没有新帖。The Street 有一篇指向他谈英伟达下一章和 Kress 的链接，正文没有引用他的原句：[链接](https://x.com/TheStreet/status/2121679657565041028)。Burry 的账号这个窗口是一篇慈善帖，不是新的空仓说明。The Street 的标题写他在黄仁勋离开之后加空半导体，但不是每一家英伟达的对手都在他的目标里：[标题](https://x.com/TheStreet/status/2121807952986149299)。德意志银行的时间线没有读到。

**财报和数据的顺序。** 先看周日晚间期货落在哪，再看英伟达是离开 162 美元还是留在下面，然后看比特币开盘是靠近 65,000 还是靠近 63,000。Jesse 点名的那张财报名单没有写星期几。Ole 的持仓报告在周一美东 15:30。12 月 9 日的议息不在周一开盘。

**明确留在观察、不放进计划的东西。** 不把 `#NASDAQ 27603` 写成纳斯达克综合指数，也不把 `#GOLD 3840`、`#USOIL 8830` 换算成新的现货价。不把 66,000、65,000、64,733.68、64,000、63,970 和 63,000 收成一个比特币价格。不把清算的 2.15 亿、18 亿、20 亿和 4 小时的 9 亿加总。不把请愿的 10 万和 12 万收成一个数，也不把 15% 的员工写成已经复职。不把“供应链会没事”写成“握手协议会丢”。不把周线 14%、峰谷 40%、10 月以来 33% 收成一个跌幅。不把“2012 年以来最长”写成“并列第二长”。不把 5.14% 和 5.15% 取平均。不把 980 亿和 983 亿收成一个流入。不把 4,040 亿和 4,041 亿合成一个赤字，也不替 Schiff 选“最大”还是“第二大”。不把柴油的 6 美元下方写成取暖油的 +59%。不把航班的 3,000、4,000、7,000、10,000、16,000 和 22,000 收成一个取消数。不把“不是网络攻击”写成已经找到的路由器或铜缆。不把伊拉克的每天 460 万桶写成霍尔木兹的 17 亿桶。不把 75 美元写成周一的油价。不把 8,200 写成 fundstrat 这个周末的新目标。

## 全站搜索没有打开，讨论范围只以这些时间线为准

`/2/search` 这次仍是空 404，不能用来改上面的价格。抓取结束时的趋势里没有美股代码，也没有英伟达或比特币的标签。能在这些账号里看见的讨论，集中在三件事：黄仁勋回不回得去、比特币这个周末还要不要在周一开盘被卖掉、停飞的原因到底是哪一种。小账号的复盘没有进入上面的价格表。

## 帖文索引

英伟达和利率：[请愿 10 万](https://x.com/KobeissiLetter/status/2121649553287864472)、[握手协议](https://x.com/DeItaone/status/2121614381436051636)、[供应链会没事](https://x.com/firstadopter/status/2121659688030806436)、[5.14%](https://x.com/elerianm/status/2121602528378806364)、[渐进加息](https://x.com/StockMKTNewz/status/2121674181334974561)。

比特币、油和航班：[64,733.68](https://x.com/financialjuice/status/2121709041756041726)、[周一抛压](https://x.com/PeterSchiff/status/2121729715534717373)、[柴油低于 6 美元](https://x.com/financialjuice/status/2121761916163113330)、[根因未知](https://x.com/CNBC/status/2121743207025275017)、[周末代码](https://x.com/FirstSquawk/status/2121877675774271698)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-15 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 123 条、彭博商业账号 76 条、FinancialJuice 40 条、零对冲 43 条，是读穿窗口后的计数。FinancialJuice 的最新可见帖在周日 00:27 UTC。德意志银行的 0 是读取失败。彭博主号、markets、BBC Business、CNN Business、Cathie Wood、克拉默、美联储、Liz Ann、美国银行、欧洲央行、沃伦·巴菲特的 0，是可见时间线早于窗口。Bianco 的持仓线程后半、Eric Balchunas 的部分黄金帖、Bill Ackman 的多数帖，被接口标成回复或转发，不在表内的原创计数里，正文在引用时单独标明。线外的 First Squawk 是 168 条。Nick Timiraos 不在前 100，可见时间线也早于窗口。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,454,951 | 123 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,335,246 | 77 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,288,732 | 51 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,313,959 | 22 |
| 5 | [@business](https://x.com/business) | 10,500,544 | 76 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,578,703 | 1 |
| 7 | [@FT](https://x.com/FT) | 7,123,772 | 19 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,262,712 | 28 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,378,687 | 17 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,652,004 | 9 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,627,526 | 0 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,437,152 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,354,827 | 20 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,437,172 | 43 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,431,000 | 0 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,057,262 | 1 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,012,428 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,745,775 | 13 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,578,388 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,540,440 | 0 |
| 21 | [@chamath](https://x.com/chamath) | 2,497,217 | 0 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,438,974 | 5 |
| 23 | [@BW](https://x.com/BW) | 2,288,910 | 1 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,451 | 16 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,156,924 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,128,767 | 1 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,083,421 | 1 |
| 28 | [@markets](https://x.com/markets) | 2,049,998 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,976,409 | 6 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,799,042 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,782,465 | 15 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,772,512 | 5 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,714,275 | 3 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,701,841 | 0 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,272 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,623,596 | 17 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,605,176 | 0 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,541,674 | 13 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,514,491 | 2 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,473,873 | 1 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,546 | 2 |
| 42 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,362,197 | 3 |
| 43 | [@Bloomberg](https://x.com/Bloomberg) | 1,361,494 | 0 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,260,048 | 1 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,225,007 | 48 |
| 46 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,200,343 | 1 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,195,611 | 2 |
| 48 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,195,133 | 0 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,184,898 | 6 |
| 50 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,172,921 | 7 |
| 51 | [@nntaleb](https://x.com/nntaleb) | 1,168,623 | 1 |
| 52 | [@USTreasury](https://x.com/USTreasury) | 1,166,983 | 0 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,158,850 | 2 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,157,540 | 10 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,139,487 | 0 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,118,202 | 1 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,106,959 | 33 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,097,898 | 8 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,082,629 | 0 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,070,618 | 1 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,317 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,039,107 | 24 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,005,780 | 0 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 958,325 | 40 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 945,882 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 934,967 | 10 |
| 67 | [@tradingview](https://x.com/tradingview) | 909,843 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 895,877 | 0 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 892,375 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,762 | 7 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 874,748 | 2 |
| 72 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 872,729 | 0 |
| 73 | [@axios](https://x.com/axios) | 866,055 | 7 |
| 74 | [@steve_hanke](https://x.com/steve_hanke) | 862,232 | 36 |
| 75 | [@jpmorgan](https://x.com/jpmorgan) | 861,436 | 0 |
| 76 | [@Citi](https://x.com/Citi) | 853,109 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 847,439 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,585 | 2 |
| 79 | [@ecb](https://x.com/ecb) | 831,607 | 0 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,705 | 1 |
| 81 | [@bgurley](https://x.com/bgurley) | 811,962 | 2 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,222 | 0 |
| 83 | [@economics](https://x.com/economics) | 806,070 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 789,973 | 3 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,835 | 1 |
| 86 | [@markminervini](https://x.com/markminervini) | 778,132 | 4 |
| 87 | [@leadlagreport](https://x.com/leadlagreport) | 769,129 | 16 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 760,258 | 0 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,369 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 746,994 | 0 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 719,077 | 13 |
| 92 | [@Nouriel](https://x.com/Nouriel) | 717,256 | 0 |
| 93 | [@CMEGroup](https://x.com/CMEGroup) | 712,457 | 0 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 675,158 | 9 |
| 95 | [@fundstrat](https://x.com/fundstrat) | 672,599 | 2 |
| 96 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,149 | 2 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 647,235 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,481 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 636,097 | 1 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 625,614 | 4 |
