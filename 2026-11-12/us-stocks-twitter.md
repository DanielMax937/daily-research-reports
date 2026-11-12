# 美股 Twitter 观点日报 · 2026-11-12

周四现货还没开。抓取结束时美东大约 5:03。这个窗口的主线是周三现货把周二的 CPI 抛售收成一次科技反弹，CoreWeave 走出今年 4 月以来最好的一天；收盘后《纽约时报》写出黄仁勋和第二位公司高管的关系，《华尔街日报》写出董事会准备换掉他，盘后百分比和白天的涨幅是两套。环比、点位、英伟达的盘中和盘后、WTI 和布伦特，各自留在原来的帖上。这是公开帖文的整理，不是投资建议。

下面每一条归纳都附有帖文链接。

## 抓取口径

- 报告日期按北京时间 **2026-11-12**。触发时刻约 10:00 UTC，时间线补抓到 **约 10:03 UTC（北京时间 18:03，美东 5:03）**。美国夏令时已经结束。美股现货 9:30 才开。周二的 CPI、周二收盘 7,521.50，以及英伟达周二的会话低点 -7.06%，不在这份报告里重算。
- 观察窗口从 **2026-11-11 10:17 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周三大约 5:17 以后的盘前、周三现货全天、收盘、盘后，以及美东周四凌晨到大约 5:03。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。全站搜索返回了结果，用来核对“当前讨论”的范围。正文里的价格和立场仍以账号时间线为准。抓取开始时，未加地区的趋势和美国地区是同一组：Ayesha、`#sptwt`、Charles Bassey、Damian Lillard、POR ACNE STUDIOS MOMENT、`#AcneStudiosxPor`。结束时未加地区的趋势换成 Ayesha、`#sptwt`、POR ACNE STUDIOS MOMENT、`#AcneStudiosxPor`、Good Thursday、Rings of Power。两边都没有美股代码。
- 不存在官方的“美股 Top 100”。这次沿用上一份已经排过的金融候选，并补了紧贴截止线的账号，成功读到粉丝数之后重新排序。用来排序的账号截止在 Eric Balchunas（625,971）。前 100 的账号集合和 11 月 11 日那份相同。名次动了三处：彭博主号（1,359,395）到彼得·布兰特（1,359,363）前面；Stocktwits（1,194,991）到 Squawk Box（1,194,712）前面；fundstrat（672,573）到 amit（672,486）前面。Morning Brew（594,083）第 101。Bloomberg Opinion 的 `@opinion`（586,152）第 102。Gary Black（585,245）第 103。Barchart（579,754）第 104，到 Cboe（579,366）前面。First Squawk（578,107）第 106。排序不代表预测准确度。
- 100 个账号里，**72 个**在窗口内有按帖文链接去重后、且接口没有标成回复或转发的原创帖。路透读穿窗口，271 条。彭博商业账号 312 条。FinancialJuice 298 条。零对冲 117 条。《华尔街日报》62 条。《经济学人》90 条。CNBC 75 条。DeItaone 66 条，可见最新帖停在周四 00:45 UTC。《金融时报》64 条。线外的 First Squawk 原创 324 条，读穿到窗口起点。LiveSquawk 69 条。德意志银行、美国银行、CNBC Now、芝商所的时间线是失败，表里的 0 不是确认沉默。沃伦·巴菲特和 Downtown 的时间线是空页。Charlie Bilello 有 7 条，全部被接口标成转发。彭博主号、markets、BBC Business、CNN Business、美联储、高盛、美国财政部、Lyn Alden、纽约时报商业、摩根大通、花旗、Hindenburg、economics、摩根士丹利、Nouriel、fundstrat、Carl Icahn、Cathie Wood、保罗·克鲁格曼、安德鲁·罗斯·索尔金，窗口内没有计为原创的新帖。

## 周三开盘、盘中和收盘是三张，收盘高于开盘

开盘点位是 First Squawk 14:31 UTC：纳斯达克上涨 382.90 点，或 1.53%，到 25,448.77；标普 500 上涨 71.69 点，或 0.95%，到 7,592.62；道指上涨 96.92 点，或 0.19%，到 52,328.81：[帖](https://x.com/FirstSquawk/status/2120524934007202168)。

盘前的期货更早，而且不是这张开盘。First Squawk 11:15 UTC：标普 500 电子迷你期货上涨 0.77%，纳斯达克 100 期货上涨 1.77%，道指期货持平：[帖](https://x.com/FirstSquawk/status/2120475409976590491)。12:40 UTC 和 12:47 UTC 都写成纳斯达克 100 期货涨幅扩到 2%：[12:40](https://x.com/FirstSquawk/status/2120496779733164502)、[12:47](https://x.com/FirstSquawk/status/2120498553449755059)。13:21 UTC：标普 500 指数期货涨幅扩到 1%：[帖](https://x.com/FirstSquawk/status/2120507322846060880)。线外的 Gary Black 在 10:44 UTC 写成标普 +0.7%、纳斯达克 100 +1.7%，那是现货开盘之前：[帖](https://x.com/garyblack00/status/2120467581123391639)。0.77%、1.77%、2%、1%、0.7% 都早于 14:31 的开盘点位。

盘中还有两句指数，都早于收盘。Kobeissi 14:32 UTC：标普 500 冲上 7,600，距离新高还有 3%：[帖](https://x.com/KobeissiLetter/status/2120525198776754351)。18:41 UTC：纳斯达克 100 当天涨超 3%，从 6 天前的低点上涨 9%：[帖](https://x.com/KobeissiLetter/status/2120580607860154422)。7,600 和 +3% 是盘中。+9% 是 6 天的跨度。

收盘点位也是 First Squawk。21:01 UTC：道指收高 0.45%，在 52,465.11，上涨 233.22 点。同一分钟：标普收高 1.31%，在 7,619.22，上涨 98.29 点。纳斯达克收高 1.59%，在 25,465.38，上涨 399.51 点：[道指](https://x.com/FirstSquawk/status/2120622927242756224)、[标普](https://x.com/FirstSquawk/status/2120623000294977744)、[纳斯达克](https://x.com/FirstSquawk/status/2120623082771726482)。7,619.22 高于他写的开盘 7,592.62，25,465.38 高于开盘 25,448.77，52,465.11 高于开盘 52,328.81。路透的收盘句没有点位：标普和纳斯达克各自上涨超过 1%，CoreWeave 的业绩让市场对人工智能交易耐久性的担心降温，英伟达在连续两个交易日大跌之后稳住：[帖](https://x.com/Reuters/status/2120684028588384430)。“超过 1%”是路透的收盘句。1.31% 和 1.59% 是 First Squawk 的点位。

纳斯达克 100 的 2.3% 是另一句。First Squawk 21:33 UTC：纳斯达克 100 飙升 2.3%，有望创 5 月以来最强的一周，标普上涨 1.3%，英伟达上涨，CoreWeave 在正面前景之后跳涨 25%：[帖](https://x.com/FirstSquawk/status/2120630993518539190)。2.3% 是纳斯达克 100。1.59% 是纳斯达克综合指数的收盘。1.3% 和他 21:01 的标普 1.31% 是同一段收盘的两种写法。Kobeissi 盘中的 +3% 不拿来替换 2.3%。

线外的 Ryan Detrick 在周四 02:37 UTC 写，自 10 月 6 日标普最后一次历史高点以来，科技跌了将近 14%，指数离新高只剩 2.5%；12 个板块里有 7 个上涨超过 5%，两个是两位数：[帖](https://x.com/RyanDetrick/status/2120707627109826860)。2.5% 是他周四凌晨的距离。3% 是 Kobeissi 周三 14:32 的距离。将近 14% 是科技板块的跨度，不是周三当天。

## 英伟达白天在涨，盘后换成另一串百分比，没有收盘百分比

盘前按发帖的人留着。线外的 Gary 10:44 UTC：英伟达 +4.5%，到 176 美元；博通 +3.9%；他把 2027 年日历年市盈率写成 12 倍：[帖](https://x.com/garyblack00/status/2120467581123391639)。零对冲 13:16 UTC 的盘前 movers 里，七巨头那一行是英伟达 +5.1%、特斯拉 +2%、字母表 +1.2%、Meta +0.8%、微软 0%、亚马逊 -0.1%、苹果 -0.7%；同一帖后文又写英伟达上涨 3.7%，即便 Baird 把它降到中性：[帖](https://x.com/zerohedge/status/2120505854164144197)。+5.1% 和 +3.7% 在同一张盘前帖里。线外的 RedDog 把盘前写成大约 174 美元、上涨将近超过 3%，近端阻力 179 美元，然后是 185 美元：[帖](https://x.com/RedDogT3/status/2120524535501885672)。174、176、+3%、+3.7%、+4.5%、+5.1% 都是盘前。

现货开盘之后的百分比仍不是收盘。Kobeissi 11:08 UTC：上涨超过 6%，买盘把昨天的跌幅抹掉：[帖](https://x.com/KobeissiLetter/status/2120473795899126012)。11:08 早于 14:31 的指数开盘，这句 +6% 和他后来的盘后 -10% 不是同一时段。DeItaone 14:35 UTC 的芯片快照：Marvell +8.5%，美光 +6.6%，英特尔 +6.3%，博通 +6.2%，AMD +3.2%，英伟达 +2.6%，高通 +2.6%，半导体 ETF +4.8%：[帖](https://x.com/DeItaone/status/2120525754442076339)。+2.6% 是 14:35。StockMKTNewz 18:31 UTC：当天到那时上涨 5%：[帖](https://x.com/StockMKTNewz/status/2120585284119347331)。unusual_whales 18:44 UTC：当天反弹 5%，到 177 美元；风险逆转偏度到了今年最高，而这只股票一个月跌了 25%：[帖](https://x.com/unusual_whales/status/2120588369801695497)。5% 和 177 美元是 18:44。这批时间线里没有英伟达的周三收盘百分比。路透只写“稳住”。

盘后按时间留着，不取一个收盘。DeItaone 22:12 UTC：下跌最多 3.1%，同一帖写《纽约时报》说黄仁勋和一位副总裁有关系：[帖](https://x.com/DeItaone/status/2120640833930309661)。零对冲 22:22 UTC：盘后跌幅扩到 4%：[帖](https://x.com/zerohedge/status/2120643404048580957)。Gary 22:29 UTC 的标题是盘后 -4.4%：[帖](https://x.com/garyblack00/status/2120645026565009560)。DeItaone 22:27 UTC：盘后扩到 5%。22:30 UTC：扩到 8.5%：[5%](https://x.com/DeItaone/status/2120644714521399296)、[8.5%](https://x.com/DeItaone/status/2120645268265660667)。线外的 The Stalwart 22:34 UTC：盘后下跌将近 8%：[帖](https://x.com/TheStalwart/status/2120646308805382331)。Kobeissi 22:34 UTC：暴跌超过 10%：[帖](https://x.com/KobeissiLetter/status/2120646315503985114)。3.1%、4%、4.4%、5%、将近 8%、8.5%、超过 10% 是七个时刻。都不是一张收盘。

跨度更长的百分比也不收成一天。零对冲 20:24 UTC 引高盛：费城半导体指数靠近 200 日均线 10,865；英伟达自周一下跌 540 个基点，同期费城半导体上涨 14%：[帖](https://x.com/zerohedge/status/2120613548111897002)。540 个基点是自周一。14% 是指数，不是英伟达。Kobeissi 23:38 UTC：两段关系的报道之间，市值抹掉 7000 亿美元；自 10 月 6 日在 26 个交易日里抹掉 2.1 万亿美元，相当于每天 810 亿美元：[帖](https://x.com/KobeissiLetter/status/2120662526320890187)。他 22:57 UTC 的另一句是，自第一段关系的新闻以来抹掉 6500 亿美元：[帖](https://x.com/KobeissiLetter/status/2120652042167517274)。周四 01:53 UTC 那条被接口标成转发的长帖写成 26 个交易日下跌 35%，其中将近一半来自这次风波，换人大约 80% 已经被定价：[帖](https://x.com/KobeissiLetter/status/2120696537458114929)。线外的 Bianco 周四 03:46 UTC：过去一个月下跌 31%，市值大约少 1.8 万亿美元，大约是澳大利亚的 GDP：[帖](https://x.com/biancoresearch/status/2120724792365961370)。6500 亿、7000 亿、2.1 万亿、1.8 万亿、35%、31%、25% 是不同账号、不同跨度。10,865 是费城半导体的 200 日均线，不是英伟达的价格。

## 换帅的句子按来源留着，概率也不并成一个

报道的顺序是：先是第二段关系，再是准备换人，再是外部公司在找人。DeItaone 21:59 UTC：《纽约时报》说黄仁勋和一位英伟达高管有过关系。22:00 UTC：和一位副总裁有关系：[高管](https://x.com/DeItaone/status/2120637644636135622)、[副总裁](https://x.com/DeItaone/status/2120637736327786862)。零对冲点出名字：医疗健康副总裁 Kimberly Powell；黄仁勋挂断了《纽约时报》的询问，公司拒绝置评：[帖](https://x.com/zerohedge/status/2120638451439538379)。Kobeissi 补了安保扣人、提供保密协议的说法：[帖](https://x.com/KobeissiLetter/status/2120638848086733130)。

换人的标题随后出现，而且没有一张写成已经公告。DeItaone 22:28 UTC：《华尔街日报》说英伟达准备撤掉黄仁勋。22:29 UTC：董事会最早当天开会决定他的去留，没有最终决定，也没有官方宣布：[准备撤掉](https://x.com/DeItaone/status/2120644924299203039)、[最早当天](https://x.com/DeItaone/status/2120645108337197284)。Kobeissi用的是“准备解雇”，董事会最早当天开会：[帖](https://x.com/KobeissiLetter/status/2120645818587951491)。23:22 UTC 的 DeItaone 改成“董事会周三开会，决定是否撤掉”，来源是一位消息人士：[帖](https://x.com/DeItaone/status/2120658539546882079)。23:39 UTC 又是另一句：英伟达在和一家外部公司合作，寻找可能的新首席执行官，并考虑先任命临时首席执行官，再做更广的搜寻：[外部公司](https://x.com/DeItaone/status/2120662640972144887)、[临时](https://x.com/DeItaone/status/2120662714980933653)。Kobeissi把这句收成彭博：[帖](https://x.com/KobeissiLetter/status/2120663608065704205)。“准备撤掉”“是否撤掉”“外部公司在找人”是三句，时间挨着，内容并不相同。

白宫的两句也不相同。DeItaone 23:31 UTC：CBS 记者在 X 上说，特朗普政府知道董事会很快就要撤掉黄仁勋：[帖](https://x.com/DeItaone/status/2120660828001124769)。周四 00:45 UTC：《华盛顿邮报》说白宫不介入董事会的决定：[帖](https://x.com/DeItaone/status/2120679435972022678)。“知道”和“不介入”是两张帖。

人选只写已经点名的句子。零对冲 02:09 UTC 引 Semafor：部分董事倾向于让首席财务官 Kress 做临时首席执行官：[帖](https://x.com/zerohedge/status/2120700484034105534)。线外的 Gary 在一条回复里把 Ian Buck 写成最可能的内部候选人，并称他是 CUDA 的发明者：[帖](https://x.com/garyblack00/status/2120653998554313169)。线外的 firstadopter 写自己几年前的书把公司说成没有黄仁勋就会完全迷路，这个看法已经变了；他认为内部有一位强候选人，外部还有一位员工愿意跟着干的人；通常的路径是先任命临时首席执行官：[内部](https://x.com/firstadopter/status/2120648383044129216)、[外部](https://x.com/firstadopter/status/2120658109471330596)、[临时路径](https://x.com/firstadopter/status/2120664950611775759)。Kress、Ian Buck、以及 firstadopter 没有写出名字的两位，不要收成一张候选名单。彭博商业引 Bernstein 的 Stacy Rasgon：英伟达增长的很大一部分来自黄仁勋是远见者，而不只是每天把公司运转起来：[帖](https://x.com/business/status/2120740027567046855)。CNBC：马斯克说雇黄仁勋会是一种荣幸；零对冲先写了“Elon 请雇 Jensen”，马斯克回复了那句：[帖](https://x.com/CNBC/status/2120773683862024528)。

概率按时刻留着。DeItaone 22:07 UTC：预测市场给黄仁勋在 2027 年 7 月之前离开的概率是 57%，2033 年之前是 71%：[帖](https://x.com/DeItaone/status/2120639522354389286)。22:34 UTC：2027 年 7 月之前 80%，1 月之前 70%：[帖](https://x.com/DeItaone/status/2120646256728981727)。Kobeissi 22:45 UTC：如果他不否认《纽约时报》刚刚报道的第二段关系，自己的展望改成将近确定、超过 90% 会把他从首席执行官的位置上拿掉：[帖](https://x.com/KobeissiLetter/status/2120649072344445378)。22:57 UTC：市场对卸任或辞职的预期升到创纪录的 85%：[帖](https://x.com/KobeissiLetter/status/2120652042167517274)。01:53 UTC 的长帖把“换人大约 80% 已经被定价”写成留任的理由，并建议董事会召开特别股东大会做顾问投票；他引用一项 187 位标普 1500 被迫离职首席执行官的研究，称撤掉跑赢的首席执行官会带来负的长期回报；2019 年亚马逊在贝索斯的婚外情公开后留任他，到 2021 年股价上涨 108%：[帖](https://x.com/KobeissiLetter/status/2120696537458114929)。57%、71%、80%、70%、超过 90%、85%、大约 80% 已定价，是七个不同的句子。超过 90% 以“如果不否认”为条件。85% 是市场预期。80% 已定价是定价，不是概率合约。

目标价也分开。DeItaone：Baird 把目标价从 500 美元砍到 200 美元，评级从跑赢降到中性；分析师 Tristan Gerra 警告 2027 年数据中心预测面临延迟，超大规模云的人工智能支出增长在 2027 年可能放到 40% 或更低，渠道订单里 10% 到 30% 可能被提前削减：[帖](https://x.com/DeItaone/status/2120481933515772150)。FinancialJuice 的降级句是同一组 200 美元和中性：[帖](https://x.com/financialjuice/status/2120483701872291951)。另一条：摩根士丹利把它从首选名单拿掉，超配还在：[帖](https://x.com/financialjuice/status/2120489150596182061)。First Squawk 周四 03:43 UTC：Oppenheimer 把评级降到 Perform，这则标题没有目标价：[帖](https://x.com/FirstSquawk/status/2120724029531414765)。StockMKTNewz 引 Dan Ives：有黄仁勋在，价值是每股 300 美元；没有他，是 225 美元：[帖](https://x.com/StockMKTNewz/status/2120688205179580646)。500 到 200、300 和 225、Perform、超配还在，是四句。200 美元是 Baird 的新目标价。225 美元是 Ives 写的“没有黄仁勋”。300 美元是“有他”。

调查和出口管制是旁边的一串，不改上面的价格。FinancialJuice 14:21 UTC：众议院中国问题小组主席 Moolenaar 说，给英伟达首席执行官的期限到当天收盘；线外的 LiveSquawk 补了一句，不回应的话传票有可能：[期限](https://x.com/financialjuice/status/2120522205587210664)、[传票](https://x.com/LiveSquawk/status/2120522427168161810)。DeItaone：贝森特质问卢特尼克，为什么被指控把芯片转往中国的客户 Megaspeed 不在实体清单上；卢特尼克的回答是“我不知道，我会去看”；消息源称他担心升级美中贸易战：[帖](https://x.com/DeItaone/status/2120536364928127373)。Axios 经 DeItaone：特朗普三次批准收紧之后，卢特尼克一再拖延；椭圆形办公室里马斯克、鲁比奥、贝森特和赫格塞思站在收紧一边，卢特尼克说这会开启对华贸易战，特朗普说“那就去做”，限制仍然没有落地：[帖](https://x.com/DeItaone/status/2120623497680769169)。First Squawk 周四把同一件事收成“对英伟达芯片转运中国的打击被卢特尼克推迟”：[帖](https://x.com/FirstSquawk/status/2120701853935759833)。沃伦和库恩斯要求卢特尼克、鲁比奥和米勒保留与对华芯片出口有关的文件：[Warren 办公室](https://x.com/financialjuice/status/2120710474564063324)。中国外交部的句子是：美国应该停止编造中国间谍叙事：[帖](https://x.com/FirstSquawk/status/2120776096971104298)。Alice Huang 被写成已经回到北京：[彭博商业](https://x.com/business/status/2120691813279306176)、[The Stalwart](https://x.com/TheStalwart/status/2120697075801428162)。FinancialJuice：中国人工智能公司在海外数据中心抢英伟达算力；担心华盛顿限制远程使用先进芯片；灰色市场交易商在囤受限芯片：[抢算力](https://x.com/financialjuice/status/2120750299640119617)、[远程](https://x.com/financialjuice/status/2120750313116512528)、[囤货](https://x.com/financialjuice/status/2120750325900444072)。西门子首席执行官说和英伟达的合作照常，不需要额外护栏，公司太聚焦在一个人身上，公司无论如何会继续：[照常](https://x.com/financialjuice/status/2120772799988191661)、[一个人](https://x.com/FirstSquawk/status/2120786758820597914)。

## CoreWeave 的白天涨幅有四句，盘后是 -6%

盘前和盘中按时间留着。零对冲的盘前是上涨 15%：[帖](https://x.com/zerohedge/status/2120505854164144197)。StockMKTNewz：有望以将近上涨 14% 开盘：[帖](https://x.com/StockMKTNewz/status/2120470455203360870)。RedDog 在开盘前的长帖里写成当天飙升超过 13%，并把阻力看在 58 美元附近，提示不要追开盘缺口：[帖](https://x.com/RedDogT3/status/2120524535501885672)。CNBC 15:27 UTC：周三上涨 20%，业绩超预期并上调全年指引：[帖](https://x.com/CNBC/status/2120538963878547782)。DeItaone 15:31 UTC：涨幅扩到 20.8%，触及两周高点：[帖](https://x.com/DeItaone/status/2120539922620936374)。First Squawk 的收盘综述是跳涨 25%。CNBC 23:26 UTC：周三上涨 24.71%，是 2025 年 4 月以来最好的一天：[帖](https://x.com/CNBC/status/2120659582506684560)。15%、将近 14%、超过 13%、20%、20.8%、25%、24.71% 是七个时刻。24.71% 是 CNBC 对全天的写法。25% 是 First Squawk 综述里的整数。

盘后是另一张。DeItaone 22:44 UTC：CoreWeave 跟随英伟达下跌 6%：[帖](https://x.com/DeItaone/status/2120648847718552043)。6% 的下跌晚于 24.71% 的白天。

贷款的句子被改过。DeItaone 先写至少 40 亿美元的投资级贷款出售：[帖](https://x.com/DeItaone/status/2120648976588591471)。零对冲随后更正：Jenxit 之后，那句话应该是高收益贷款出售：[帖](https://x.com/zerohedge/status/2120656506420904135)。投资级和高收益是先后两句，后一句标明是更正。

电话会的原话按账号留着。FinancialJuice 引首席执行官 Intrator：在美国交付数据中心的能力没有受到影响；英伟达不是一个人，他们仍会是很好的伙伴；建设计划没有被推迟，也没有被改形：[交付](https://x.com/financialjuice/status/2120528883476799544)、[不是一个人](https://x.com/financialjuice/status/2120529688628212148)、[计划](https://x.com/financialjuice/status/2120530322198532572)。零对冲：当被问到为什么不回购收益率 15% 的深度承压债券时，他说资本可以投到更高的回报率上；克拉默追问能不能做出高于 16% 的回报：[帖](https://x.com/zerohedge/status/2120529942031348057)。线外的 firstadopter 补了两句：他取消了 10b5-1；调整后经营回报的轨迹会远高于 16%；他想买那些债券，但公司里有更好的资本用途：[帖](https://x.com/firstadopter/status/2120531763835342972)。15% 是债券收益率。16% 是克拉默的问题和 Intrator 被引用的回报。10b5-1 是内部人出售计划被取消。花旗把目标价从 128 美元升到 149 美元：[帖](https://x.com/FirstSquawk/status/2120470186616848467)。149 美元是目标价，不是现价。58 美元是 RedDog 写的阻力。

RedDog 在同一帖里复述了上一份已经写过的利润表：三季度收入同比增长 168%，到 36.6 亿美元；2026 年收入展望抬到 130 亿到 133 亿美元；积压 1325 亿美元；净亏损扩到 7.09 亿美元；资本开支 370 亿到 390 亿美元。他另写债务义务接近 470 亿美元。470 亿美元是他这张帖的债务句子。上一份里，有追索权债务是 91.8 亿美元，流动负债是 243.9 亿美元，470 亿美元当时出现在零对冲的标题里。这里不把三列债务收成一个资产负债表。

线外的 Keith 没有把空头加回去。他写 CoreWeave 自周期高点下跌 74% 的图仍然挂着；基本面上他会在周三早上把空头重新加上，但资金流很清楚，一批惊慌的对冲基金要回补很多股票：[74%](https://x.com/KeithMcCullough/status/2120530607952351649)、[回补](https://x.com/KeithMcCullough/status/2120613706144837727)。74% 是自周期高点，不是周三的涨幅。

## 油价结算上涨，周四早上先跌 1 美元，再写成 92.44 美元

结算价有明确的 settle。FinancialJuice：NYMEX WTI 12 月期货结算 86.53 美元，上涨 49 美分，0.57%；布伦特期货结算 92.76 美元，上涨 1.27 美元，1.39%：[WTI](https://x.com/financialjuice/status/2120600232870519044)、[布伦特](https://x.com/financialjuice/status/2120603744941318555)。First Squawk 是同一组：[WTI](https://x.com/FirstSquawk/status/2120600758467117176)、[布伦特](https://x.com/FirstSquawk/status/2120604102904488068)。汽油期货结算 2.6075 美元/加仑，柴油期货结算 4.2113 美元/加仑，天然气期货结算 3.2150 美元/百万英热：[汽油](https://x.com/financialjuice/status/2120600268098384184)、[柴油](https://x.com/financialjuice/status/2120600303091482781)、[天然气](https://x.com/financialjuice/status/2120600444838052165)。86.53 美元是 WTI 结算。92.76 美元是布伦特结算。

盘中的口号对不上这组结算。DeItaone 15:19 UTC：布伦特因为伊朗和乌克兰谈判的不确定性上涨 2 美元。15:36 UTC 他和 First Squawk 都写成上涨 3 美元：[2 美元](https://x.com/DeItaone/status/2120536888415326649)、[3 美元](https://x.com/FirstSquawk/status/2120541202135359955)。线外的 Gary 在 10:44 UTC 写成布伦特守在 93 美元。线外的 Brooks 同一天写，93 美元的布伦特定价合理，但最近的下跌并没有把冲突结束定价进去，布伦特较年初仍高 55%：[帖](https://x.com/robin_j_brooks/status/2120510725017776541)。+2 美元、+3 美元、93 美元都早于结算。结算是 92.76 和 86.53。

周四早上又是另一组。First Squawk 01:37 UTC：油价因为中东和平的乐观而下跌，布伦特和 WTI 各跌 1 美元：[帖](https://x.com/FirstSquawk/status/2120692422418301221)。09:41 UTC：布伦特期货下跌 0.3%，到 92.44 美元，价格在摇摆：[帖](https://x.com/FirstSquawk/status/2120814310456963146)。跌 1 美元是 01:37。92.44 美元是 09:41。92.76 美元是周三结算。线外的 Ole Hansen 周四上午：布伦特本月跌了 18%，中东供应在恢复，柴油和液化天然气仍然紧；能源期货今年至今的回报很好，市场在学着和“没有战争、也没有和平”相处，升级的风险还在：[帖](https://x.com/Ole_S_Hansen/status/2120818410003013989)。18% 是本月，不是周三的 1.39%，也不是周四的 0.3%。

海峡的句子不要合成。窗口刚开始，FinancialJuice 10:18 UTC：伊斯兰革命卫队称两艘油轮夜里在霍尔木兹触雷：[帖](https://x.com/financialjuice/status/2120461261963927689)。周四 06:51 UTC，First Squawk：革命卫队海军称昨夜两艘超级油轮在海峡爆炸。06:59 UTC：两艘油轮在“未经授权的航线”上发生爆炸，伊朗媒体说的是周三夜里：[超级油轮](https://x.com/FirstSquawk/status/2120771399547789419)、[未经授权](https://x.com/financialjuice/status/2120773451673993371)。触雷和爆炸是两张帖，时间隔了一夜。政治句子是另外四张。FinancialJuice：伊朗准将 Heydari 说海峡已经关闭，除非革命领袖下令否则不会打开：[帖](https://x.com/financialjuice/status/2120607898237620720)。议长 Ghalibaf：要重开海峡并恢复谈判，美国必须完全落实伊朗的 7 个条件；同一天他又说已经和阿曼就航道和分道通航达成谅解：[7 个条件](https://x.com/financialjuice/status/2120553195000787194)、[阿曼](https://x.com/financialjuice/status/2120557708893921578)。CENTCOM：美军继续行动，保持海峡开放，执行对伊朗的海上封锁：[帖](https://x.com/financialjuice/status/2120579267230875694)。DeItaone：万斯在考虑和伊朗安全负责人 Mohsen Rezaei 面对面谈，特朗普支持，多哈是可能的地点：[帖](https://x.com/DeItaone/status/2120600061700702292)。关闭、7 个条件、谅解、继续开放、面对面谈，按原帖留着。

流量和运费是另一列。线外的 Javier Blas：沙特告诉欧佩克，10 月产量回到战前水平，达到每天 1060 万桶；官方井口产量是每天 1056.3 万桶，扣除入库之后的市场供应是每天 920.3 万桶；配额大约每天 1050 万桶：[1060 万](https://x.com/JavierBlas/status/2120503237568844205)、[1056.3 万和 920.3 万](https://x.com/JavierBlas/status/2120508120195633610)。First Squawk 写成 10 月增产 26%，到每天 1056 万桶：[帖](https://x.com/FirstSquawk/status/2120502772399473007)。1056.3 万是井口。920.3 万是市场供应。26% 只在 First Squawk 的帖里。美国汽油全国零售价单日下跌大约 3.6 美分，到每加仑 3.94 美元，是 18 年来最大的单日跌幅：[帖](https://x.com/JavierBlas/status/2120490146004894004)。3.94 美元是零售价。2.6075 美元是汽油期货结算。苏伊士以西多条航线的油运费过去几天下跌 50% 到 75%；阿曼湾到东北亚的关键航线自 10 月 15 日下跌大约 60%；波斯湾里出发的油轮运费守得更好。他用问号写“危机结束了？”：[帖](https://x.com/JavierBlas/status/2120802801173381217)。50% 到 75% 是运费，不是油价。Hanke 另写乌克兰无人机打了俄罗斯在乌斯季卢加的石油出口终端：[帖](https://x.com/steve_hanke/status/2120671666883678343)。

## 国债、黄金和 12 月加息仍是几套句子

退伍军人节的现券和周四凌晨的收益率分开。线外的 Gary 在周三 10:44 UTC 写，债券因为退伍军人节休市，10 年期收益率守在 4.99%，12 月加息的赔率超过 85%，布伦特守在 93 美元。4.99% 是他写的休市日报价。超过 85% 没有拆开 25 个基点和 50 个基点。First Squawk 周四 01:18 UTC：基准 10 年期国债收益率稳定在 4.99%。01:19 UTC：2 年期收益率上涨将近 5 个基点，到两周高点 4.7756%：[10 年](https://x.com/FirstSquawk/status/2120687756624142471)、[2 年](https://x.com/FirstSquawk/status/2120687798751801839)。4.99% 在两张帖里相同。4.7756% 是周四凌晨的 2 年期。将近 5 个基点是这一夜的升幅，不是上一份里周二全天的 0.18 个百分点。

黄金有三句。线外的 Brooks 周三中午写的是前一天：黄金只跌了 2.6%，他认为在沃勒、热的 CPI 和 Logan 这三重压力下，这是一个好迹象；到周三收盘，市场已经为 2027 年中之前多定价了一次加息：[2.6%](https://x.com/robin_j_brooks/status/2120505153862123845)。2.6% 是他对周二的复述。Peter Schiff 20:16 UTC：黄金下跌 50 美元，回到 4,000 美元下方，理由是市场相信美联储可能加息 50 个基点；等到真的加的时候，通胀会再高 200 个基点以上；他的结论是买黄金：[帖](https://x.com/PeterSchiff/status/2120611597076893857)。下跌 50 美元、回到 4,000 下方，是他的周三晚上。First Squawk 周四 00:10 UTC：黄金下跌 0.8%，到 4,002.54 美元；随后一帖写 Goolsbee 把通胀报告称为“接近令人不安”，央行买盘把黄金支撑在 4,000 美元附近，白银上涨 1.2% 到 52.14 美元，美元指数上涨 0.4%：[4002.54](https://x.com/FirstSquawk/status/2120670651250094183)、[白银](https://x.com/FirstSquawk/status/2120670662264258638)。4,002.54 美元和“4,000 下方”差在 4,000 这一线的哪一侧，按原帖留着。-0.8% 不是 -2.6%，也不是下跌 50 美元。

加息路径按人留着。线外的 Nick Timiraos：现在几乎没有疑问，美联储 12 月会加息；第三次扎实的通胀报告之后，问题是多快：一次会议 25 个基点，还是先上 50，还是放出一串更快的 25；这种战术选择通常由主席拍板，他举了格林斯潘 1994 年 8 月和 2000 年 5 月，以及鲍威尔 2022 年 6 月走到 75 个基点：[帖](https://x.com/NickTimiraos/status/2120495446179131412)。Brooks：通过 2027 年 6 月，市场现在定价 76 个基点的加息；昨天收在 72 个基点；加这么多会是一个可怕的错误；他仍然认为加 50 个基点是错的，因为 10 月 CPI 的热来自 9 月和 10 月的油价，扩散指数会再掉下来：[76 个基点](https://x.com/robin_j_brooks/status/2120616483726229667)、[不要 50](https://x.com/robin_j_brooks/status/2120508894577410069)。76 对 72 是他写的累计路径，不是 12 月单次会议的概率。超过 85% 是 Gary 的 12 月加息赔率。Nick 没有给一个概率数字。Liz Ann：CPI 分项里，月环比年化快于 2% 的比例跳到 76.3%，快于 3% 的升到 54.5%，高于 5 年均值的升到 32.2%：[帖](https://x.com/LizAnnSonders/status/2120488907775398095)。NFIB：计划在未来三个月涨价的小企业占 37%，和 2022 年 7 月相同；最近一笔贷款利率更高的老板占 13%，是 2024 年 8 月以来最高：[37%](https://x.com/LizAnnSonders/status/2120489631934292054)、[13%](https://x.com/LizAnnSonders/status/2120489534727340069)。Hanke 的数量方程是另一套：2026 年美国家庭和企业支出增长 7.6%，实际增长大约 3%，剩下的 4.6% 是通胀；Divisia M4 增长 7.4%，高于他写的 6.3% 黄金增长率；他引用 Roth Capital 的 Michael Darda“美联储迷路了”，并表示同意：[4.6%](https://x.com/steve_hanke/status/2120639958100652363)、[7.4%](https://x.com/steve_hanke/status/2120494252438548539)。4.6% 是他的余数。76.3% 是 Liz Ann 的分项广度。

线外的 Bespoke 写下周四的日程，抓取结束时这些都还没有发生：六位美联储官员讲话，从 Hammack 美东 9:00 开始，到 Williams 18:30 结束；能源库存在中午；ATI、卡夫亨氏、Moderna 有分析师日：[帖](https://x.com/bespokeinvest/status/2120646627085914298)。

## 周四盘前：期货在跌，现货还没开，电线没有写出百分比

彭博商业 09:55 UTC：美股股指期货下跌，因为英伟达在考虑替换黄仁勋；这只芯片股的下跌占了纳斯达克 100 合约跌幅的一半以上：[帖](https://x.com/business/status/2120817637114474669)。《华尔街日报》市场号 09:18 UTC 的标题是领导层风波拖累美股期货、压制人工智能交易，没有百分比：[帖](https://x.com/WSJmarkets/status/2120808374690332900)。CNBC 在周三 23:25 UTC 已经用“纳斯达克 100 期货下滑”做了标题，同样没有百分比：[帖](https://x.com/CNBC/status/2120659186681880825)。FinancialJuice 23:13 UTC：美股期货在《华尔街日报》报道准备替换首席执行官之后下跌：[帖](https://x.com/financialjuice/status/2120656074621464745)。这四句都是方向，没有一个点数。一半以上是英伟达在纳斯达克 100 期货跌幅里的占比，不是指数的百分比。

芯片股的盘前也没有个股百分比。First Squawk 09:25 UTC：美国芯片股盘前跟随英伟达下跌：[帖](https://x.com/FirstSquawk/status/2120810089867300908)。亚洲有点数。台湾加权收盘下跌 2.6%：[帖](https://x.com/FirstSquawk/status/2120752181452394601)。首尔结束两天的上涨，Yonhap 的标题没有百分比：[帖](https://x.com/FirstSquawk/status/2120770580878422286)。First Squawk 01:00 UTC 的区域句是，亚太股市下跌，因为盘后关于黄仁勋的报道压过了华尔街科技股的反弹：[帖](https://x.com/FirstSquawk/status/2120683157288861833)。礼来盘前上涨 2%，因为公司成为第一家 GLP-1 减肥药在中国获批的药厂：[帖](https://x.com/FirstSquawk/status/2120809806105886985)。2% 是礼来，不是芯片股。

已经排进周四、但抓取结束时还没有结果的名字按日历留着。线外的 Bespoke：盘后是应用材料和分析师日之外的思科；开盘前是 National Vision、Spectrum Brands、Wolverine 和 YETI：[帖](https://x.com/bespokeinvest/status/2120645368819970551)。线外的 Earnings Whispers 把 Nebius 放在周四开盘前那一长串的第一个：[帖](https://x.com/eWhispers/status/2120570691606974517)。unusual_whales：Nebius 当天已经上涨 19%，期权定价大约 20% 的波动；华尔街预期收入大约 9.01 亿美元，上一季是 5.82 亿美元：[帖](https://x.com/unusual_whales/status/2120590129685299389)。19% 是周三的股票。20% 是期权定价的波动，不是已经发生的涨跌。9.01 亿是预期。线外的 The Transcript 把英伟达的电话会写成“周二越早到越好”，是今年最受关注的一场：[帖](https://x.com/TheTranscript_/status/2120642707244843221)。线外的 Ryan Detrick 在播客摘要里写，英伟达财报在 17 日，黄仁勋被邀请在 18 日作证：[帖](https://x.com/RyanDetrick/status/2120583714468159503)。17 日是下周二。18 日是作证，不是财报。

## 要盯住的五件事

1. **现货 9:30 还没开，周三收盘已经写下来了。** 标普 7,619.22，+1.31%。纳斯达克综合指数 25,465.38，+1.59%。道指 52,465.11，+0.45%。开盘是 7,592.62、25,448.77、52,328.81。纳斯达克 100 的盘中有过超过 +3%，收盘综述是 +2.3%。
2. **英伟达没有收盘百分比，盘后有一串。** 盘前有 174 美元、176 美元、+3%、+3.7%、+4.5%、+5.1%。盘中有过超过 +6%、+2.6%、+5% 到 177 美元。盘后有 -3.1%、-4%、-4.4%、-5%、将近 -8%、-8.5%、超过 -10%。Baird 的目标价是 200 美元。Ives 写有黄仁勋 300 美元、没有他 225 美元。Kress 是 Semafor 经零对冲的临时人选。
3. **换人还不是公告。** 《华尔街日报》的句子是准备撤掉，董事会最早周三开会。彭博的句子是外部公司在找人，并考虑临时首席执行官。《华盛顿邮报》的句子是白宫不介入。CBS 记者的句子是政府知道很快要撤。Kobeissi 的超过 90% 以不否认为条件，85% 是市场预期，80% 是他后来写的已经定价。
4. **油价结算和周四早上的口号分开。** WTI 结算 86.53 美元，涨 0.57%。布伦特结算 92.76 美元，涨 1.39%。周四 01:37 的口号是布伦特和 WTI 各跌 1 美元。09:41 的布伦特期货是 92.44 美元，-0.3%。沙特井口是每天 1056.3 万桶，市场供应是 920.3 万桶。
5. **周四的日历还没有结果。** 股指期货在跌，电线没有写出百分比，只写了英伟达占纳斯达克 100 期货跌幅的一半以上。开盘前有 Nebius，盘后有应用材料和思科。六位美联储官员从美东 9:00 的 Hammack 讲到 18:30 的 Williams。英伟达财报被写成 17 日，作证是 18 日。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。盘前和盘中不是收盘。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 收盘 | 标普、纳斯达克、道指 | 标普 7,619.22，+1.31%，+98.29 点。纳斯达克 25,465.38，+1.59%，+399.51 点。道指 52,465.11，+0.45%，+233.22 点 | [标普](https://x.com/FirstSquawk/status/2120623000294977744)、[纳斯达克](https://x.com/FirstSquawk/status/2120623082771726482)、[道指](https://x.com/FirstSquawk/status/2120622927242756224) |
| 开盘 | 标普、纳斯达克、道指 | 7,592.62，+0.95%；25,448.77，+1.53%；52,328.81，+0.19% | [开盘](https://x.com/FirstSquawk/status/2120524934007202168) |
| 盘中 | 标普、纳斯达克 100 | 标普冲上 7,600，离新高 3%。纳斯达克 100 当天超过 +3%，6 天 +9%。收盘综述里纳斯达克 100 是 +2.3% | [7600](https://x.com/KobeissiLetter/status/2120525198776754351)、[+3%](https://x.com/KobeissiLetter/status/2120580607860154422)、[2.3%](https://x.com/FirstSquawk/status/2120630993518539190) |
| 周四盘前 | 股指期货 | 下跌。英伟达的下跌占纳斯达克 100 合约跌幅的一半以上。没有百分比 | [期货](https://x.com/business/status/2120817637114474669) |
| 盘前 | NVDA | Gary：+4.5% 到 176 美元，2027 年市盈率 12 倍。零对冲同一帖里有 +5.1% 和 +3.7%。线外的 RedDog：大约 174 美元，将近超过 +3%，阻力 179 然后 185 | [176](https://x.com/garyblack00/status/2120467581123391639)、[5.1 和 3.7](https://x.com/zerohedge/status/2120505854164144197)、[174](https://x.com/RedDogT3/status/2120524535501885672) |
| 盘中 | NVDA | 超过 +6% 的那句在指数开盘前。14:35 的快照是 +2.6%。18:31 当天 +5%。18:44 反弹 5% 到 177 美元。没有收盘百分比 | [+6%](https://x.com/KobeissiLetter/status/2120473795899126012)、[177](https://x.com/unusual_whales/status/2120588369801695497) |
| 盘后 | NVDA | -3.1%、-4%、-4.4%、-5%、将近 -8%、-8.5%、超过 -10% | [-8.5%](https://x.com/DeItaone/status/2120645268265660667)、[超过 -10%](https://x.com/KobeissiLetter/status/2120646315503985114) |
| 目标价 | NVDA | Baird 从 500 美元降到 200 美元，中性。摩根士丹利移出首选，超配还在。Oppenheimer 降到 Perform，无目标价。Ives：有黄仁勋 300 美元，没有他 225 美元 | [200](https://x.com/DeItaone/status/2120481933515772150)、[300/225](https://x.com/StockMKTNewz/status/2120688205179580646) |
| 人选 | NVDA | Semafor：部分董事倾向首席财务官 Kress 做临时首席执行官。Gary 的回复把 Ian Buck 写成最可能的内部候选人 | [Kress](https://x.com/zerohedge/status/2120700484034105534)、[Buck](https://x.com/garyblack00/status/2120653998554313169) |
| 全天 | CRWV | 盘前 +15%、将近 +14%、超过 +13%。盘中 +20% 和 +20.8%。综述 +25%。CNBC 全天 +24.71%，2025 年 4 月以来最好的一天。盘后 -6% | [24.71%](https://x.com/CNBC/status/2120659582506684560)、[-6%](https://x.com/DeItaone/status/2120648847718552043) |
| 目标价和阻力 | CRWV | 花旗目标价 149 美元，从 128。线外的 RedDog 把阻力看在 58 美元附近 | [149](https://x.com/FirstSquawk/status/2120470186616848467)、[58](https://x.com/RedDogT3/status/2120524535501885672) |
| 贷款 | CRWV | 先写成至少 40 亿美元投资级贷款。零对冲更正为高收益贷款出售 | [更正](https://x.com/zerohedge/status/2120656506420904135) |
| 盘中快照 | MRVL、MU、INTC、AVGO、AMD、QCOM、SOXX | +8.5%、+6.6%、+6.3%、+6.2%、+3.2%、+2.6%、ETF +4.8%。这是 14:35，不是收盘 | [快照](https://x.com/DeItaone/status/2120525754442076339) |
| 位置 | 费城半导体 | 高盛经零对冲：靠近 200 日均线 10,865。英伟达自周一 -540 个基点，同期指数 +14% | [10865](https://x.com/zerohedge/status/2120613548111897002) |
| 结算 | WTI、布伦特 | WTI 86.53 美元，+0.57%。布伦特 92.76 美元，+1.39% | [WTI](https://x.com/financialjuice/status/2120600232870519044)、[布伦特](https://x.com/financialjuice/status/2120603744941318555) |
| 周四盘前 | 布伦特 | 01:37 布伦特和 WTI 各跌 1 美元。09:41 布伦特期货 92.44 美元，-0.3% | [跌 1 美元](https://x.com/FirstSquawk/status/2120692422418301221)、[92.44](https://x.com/FirstSquawk/status/2120814310456963146) |
| 供给 | 沙特原油 | 井口每天 1056.3 万桶。市场供应每天 920.3 万桶。First Squawk 的增产是 26% | [井口](https://x.com/JavierBlas/status/2120508120195633610)、[26%](https://x.com/FirstSquawk/status/2120502772399473007) |
| 零售 | 美国汽油 | 单日大约 -3.6 美分，到 3.94 美元/加仑。期货结算是 2.6075 美元 | [3.94](https://x.com/JavierBlas/status/2120490146004894004) |
| 现货 | 黄金、白银 | Schiff：下跌 50 美元，回到 4,000 下方。First Squawk：-0.8% 到 4,002.54 美元。白银 +1.2% 到 52.14 美元 | [50 美元](https://x.com/PeterSchiff/status/2120611597076893857)、[4002.54](https://x.com/FirstSquawk/status/2120670651250094183) |
| 收益率 | 10 年、2 年 | 10 年期稳定在 4.99%。2 年期将近 +5 个基点，到 4.7756%。Gary 写现券因为退伍军人节休市 | [4.99%](https://x.com/FirstSquawk/status/2120687756624142471)、[4.7756%](https://x.com/FirstSquawk/status/2120687798751801839) |
| 周四盘前 | LLY | 上涨 2%。GLP-1 减肥药在中国获批 | [2%](https://x.com/FirstSquawk/status/2120809806105886985) |
| 周三已经上涨 | NBIS | 当天 +19%。期权定价大约 20% 的波动。收入预期大约 9.01 亿美元。业绩在周四开盘前，抓取结束时还没有结果 | [19%](https://x.com/unusual_whales/status/2120590129685299389) |
| 周四日历 | AMAT、CSCO、EYE、SPB、WWW、YETI | 线外的 Bespoke：应用材料和思科在盘后。四只消费股在开盘前 | [日历](https://x.com/bespokeinvest/status/2120645368819970551) |
| 位置 | TSLA | 线外的 RedDog：枢纽 382 美元，守住则看 396 美元。线外的 Gary：估值拉伸、前瞻下修、自动驾驶商品化，他保持谨慎 | [382](https://x.com/RedDogT3/status/2120524535501885672)、[谨慎](https://x.com/garyblack00/status/2120467581123391639) |
| 相对表现 | RSP、QQQ、UUP | 线外的 Keith：做多等权已经一个月，正在碾压 QQQ。他又做空了 QQQ。美元是多头 | [RSP](https://x.com/KeithMcCullough/status/2120605003941568572)、[QQQ](https://x.com/KeithMcCullough/status/2120675524838101328) |
| 亚洲 | 台湾加权 | 收盘 -2.6% | [-2.6%](https://x.com/FirstSquawk/status/2120752181452394601) |

## 后续走势：三套可以证伪的剧本

抓取结束时现货未开。已经写下来的锚是：标普收在 7,619.22，涨 1.31%；周四股指期货在跌，但没有百分比；英伟达盘后最深的一句是超过 -10%，没有收盘百分比；WTI 结算 86.53 美元，布伦特周四 09:41 是 92.44 美元。

**周三的反弹被当成超卖之后的延续，周四期货的下跌只是盘后新闻的回吐。** 触发器是收盘点位高于开盘，Kobeissi 把标普冲上 7,600 写成离新高 3%，Detrick 写指数离 10 月 6 日高点只剩 2.5%、11 月转正，以及他的节目摘要里那句中期选举后六个月 19 次里 19 次更高、平均上涨 14.1%：[2.5%](https://x.com/RyanDetrick/status/2120707627109826860)、[19 次](https://x.com/RyanDetrick/status/2120583714468159503)。它失败的条件，是期货把 7,619.22 送回开盘的 7,592.62，或者线外的 RedDog 写的 7,577 和标普 ETF 758 美元失守，同时纳斯达克 100 期货把周三综述里的 +2.3% 全部吐回。

**英伟达的换人被当成已经定价，白天的抄底还会再出现一次。** 触发器是 Kobeissi 后来那条长帖：26 个交易日 -35%，换人大约 80% 已经被定价，历史上下掉跑赢的首席执行官代价很高，董事会应该先问股东。旁边是 Ives 的 300 美元对 225 美元，以及周三盘中一度超过 +6%、反弹到 177 美元。它失败的条件，是开盘之后股价离开盘后那一串、走向 Baird 的 200 美元，或者不否认第二段关系、使他自己 22:45 UTC 的超过 90% 变成基准，同时 Semafor 的 Kress 从“部分董事倾向”变成已经任命。

**油价和换帅各走各的，直到现货开盘才知道哪一张盖过另一张。** 触发器是结算 WTI 86.53 美元、布伦特 92.76 美元，周四早上 92.44 美元，Brooks 写 93 美元定价合理、加 50 个基点是错的，Blas 写运费大跌并用问号结束危机。对面是两艘触雷和两艘爆炸的两张帖，Heydari 说海峡仍然关闭，2 年期到了 4.7756%。它失败的条件，是布伦特离开 92.44 美元、回到周三盘中上涨 3 美元的那一侧，同时 Nick 的 12 月问题只剩下 50 个基点；或者油价留在 92 美元附近、期货却因为换帅继续下跌，那就是首席执行官的句子盖过了油。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周四开盘。它不决定仓位大小。抓取结束时，现货还没有开。

**开盘前只核对五样东西。** 期货是继续落在彭博商业“下跌、英伟达占纳斯达克 100 合约跌幅一半以上”这一侧，还是回到周三收盘的 7,619.22。英伟达是离开盘后超过 -10% 的那一句，还是开盘后靠近 RedDog 的 179 美元和 185 美元；200 美元仍是 Baird 的目标价，300 和 225 是 Ives 的两列，都不是现价。CoreWeave 用的是全天 +24.71% 还是盘后 -6%，贷款句子用的是更正后的高收益，而不是更正前的投资级。油是继续交易结算 86.53 美元和 92.76 美元，还是把 92.44 美元、跌 1 美元和两艘爆炸收成一张新的供给冲击。加息句子是停在 Brooks 的“不要 50、累计 76 个基点”，还是走到 Nick 的“12 月会加，快慢由主席定”。五样里，期货跌幅没有写成一个百分比、英伟达不把 200 美元当成已经交易的价格、油价留在 92 美元这一侧、50 个基点仍是 Nick 的三个问题之一，这些帖给出的默认顺序是：先看换帅有没有从“准备”变成公告，再决定 7,619.22 是不是还站得住。期货把周三涨幅吐回、英伟达走向 200 美元、或者 50 个基点变成唯一被交易的句子，默认顺序掉过头来：先处理首席执行官和 12 月的速度，再决定 CoreWeave 的 +24.71% 还剩多少。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：周三早段英伟达超过 +6%，抹掉昨天的跌幅。标普冲上 7,600 时，他在一条回复里写自己在 7,370 做多、目标 7,600，这套已经走完，点数是 +230：[帖](https://x.com/KobeissiLetter/status/2120525278443196485)。盘后超过 -10%。若不否认，超过 90% 会换人。市场预期后来写成 85%。再后来的长帖是不要解雇，大约 80% 已经定价，建议顾问投票。
- First Squawk，线外：开盘标普 7,592.62。收盘标普 7,619.22、纳斯达克 25,465.38、道指 52,465.11。纳斯达克 100 综述 +2.3%，CoreWeave 综述 +25%。WTI 结算 86.53 美元，布伦特结算 92.76 美元。周四布伦特期货 92.44 美元。Oppenheimer 降到 Perform。
- Nick Timiraos，线外：12 月会加息。速度是 25、50，或一串更快的 25。主席拍板。
- Brooks，线外：不要加 50。通过 2027 年 6 月定价 76 个基点，昨天是 72。布伦特 93 美元定价合理，较年初仍高 55%。黄金周二只跌 2.6%，他当成扛住了鹰派。
- Gary，线外：盘前英伟达 +4.5% 到 176 美元，12 倍 2027 年市盈率。盘后标题 -4.4%。董事会会换人，对 AMD 和博通是正面的。特斯拉保持谨慎。10 年期在休市日守着 4.99%，12 月加息赔率超过 85%。
- Baird，经 DeItaone：目标价 200 美元，中性。2027 年资本开支增速可能放到 40% 或更低。
- Dan Ives，经 StockMKTNewz：300 美元对 225 美元。
- 摩根士丹利，经 FinancialJuice：移出首选，超配还在。克拉默把这句写成“跳船”，并写英伟达只有在多数分析师砍掉之后才会见底；盘后他改口说板凳在，关键人物被抹掉之后值多少，他还要再想：[跳船](https://x.com/jimcramer/status/2120488652010586598)、[见底](https://x.com/jimcramer/status/2120489029493834093)、[板凳](https://x.com/jimcramer/status/2120662411028140195)。
- RedDog，线外：标普期货 +70 点时，阻力 7,577 和 7,635，逢强减仓。标普 ETF 当时大约 756 美元，下一关 758。纳斯达克 100 ETF 收回 682，200 日均线大约 685，阻力 687.70。英伟达盘前大约 174 美元，阻力 179 和 185。CoreWeave 阻力大约 58 美元。特斯拉枢纽 382 美元，上看 396。他在上一周四、标普 ETF 大约较低点低 6% 时投了第一笔 25%，计划拿到指数回到历史高点；若再跌 15% 到 20% 才加档。
- 米内尔维尼：10 月 15 日的标普 ETF 空头还在叙述里。从他的进场价算，纳斯达克 100 ETF 跌了 11%，标普 ETF 跌了 5%，多头只剩梯瓦，空头从对冲变成净空头。这 11% 和 5% 不是周三的涨幅：[帖](https://x.com/markminervini/status/2120499249733423221)。
- Keith，线外：又做空纳斯达克 100 ETF。等权做多一个月，正在碾压纳斯达克 100 ETF。做多美元。现金 19%，还要降，因为要加固定收益、并把 Quad 4 的股票铺开。当天重新做空了两只没有写出名字的大盘科技。CoreWeave 的空头没有加回去，因为对冲基金在回补。英伟达 177.5 美元的零日期权成交超过 39.5 万张，当天成交大约 3.39 亿股：[期权](https://x.com/KeithMcCullough/status/2120693270749893031)、[股数](https://x.com/KeithMcCullough/status/2120694545939927040)。
- Detrick，线外：标普还守着向上的 200 日均线、夏季低点和趋势线。截至上周五今年大约 +8%，他预期今年剩下的时间往上。11 月已经转正。科技自 10 月 6 日将近 -14%，指数离新高 2.5%。
- Sentimentrader，线外：11 月 10 日的读数是聪明钱 0.65，非常乐观；笨钱 0.5，中性。风险偏好掉到 30 以下、标普仍在 200 日均线之上的类似情形，一年后更高的次数是 94%，中位数上涨 17.43%；只在第一声信号买入，中位数降到 6%。类似翻转之后三周，10 次里只有 4 次更高，平均跌 3.1%：[一年](https://x.com/sentimentrader/status/2120516910353883537)、[三周](https://x.com/sentimentrader/status/2120532248672031023)。
- Eric Balchunas：标普 ETF 成交超过 600 亿美元的日子，之后一个月上涨的次数是三分之二，平均 1.8%：[帖](https://x.com/EricBalchunas/status/2120495536864157958)。
- Hanke：支出增长 7.6%，他算出的通胀是 4.6%。Divisia M4 增长 7.4%。美联储在他看来已经迷路。
- El-Erian：市场对第一轮风波的反应是首席执行官扛得住；董事会调查挑战了这个假设；这不是普通的首席执行官、普通的公司、普通的行业、普通的时间，影响很难只留在公司里面：[帖](https://x.com/elerianm/status/2120655409488789804)。日元弱到将近 160，他写成干预区：[帖](https://x.com/elerianm/status/2120577133424554390)。
- Bilello 的两条被标成转发：标普远期 12 个月市盈率降到 17.7，是 2023 年 11 月以来最低，5 年均值 19.8、10 年 19.1、15 年 17.6；2026 年盈利预测 +34%，价格 +7%，数据截至 11 月 5 日：[市盈率](https://x.com/charliebilello/status/2120526731128046062)。信用卡 90 天以上逾期 12.9%，学生贷款 10.9%，汽车贷款 5.7% 是纪录：[逾期](https://x.com/charliebilello/status/2120514825864573108)。
- 方舟和 Cathie Wood 的账号这个窗口没有新的指数点位。高盛主号没有新帖。德意志银行的时间线没有读到。

**财报和数据的顺序。** 先看周四期货有没有写出百分比，再看英伟达是离开超过 -10% 还是靠近 179 美元。然后才是开盘前的 Nebius，以及 Bespoke 点名的 National Vision、Spectrum Brands、Wolverine、YETI。盘后是应用材料和思科。能源库存在美东中午。美联储讲话从 9:00 的 Hammack 排到 18:30 的 Williams。英伟达自己的财报被写成 17 日，不在今天。

**明确留在观察、不放进计划的东西。** 不把开盘的 7,592.62 和收盘的 7,619.22 取一个价格。不把纳斯达克综合指数的 +1.59% 写成纳斯达克 100 的 +2.3% 或盘中的 +3%。不给英伟达补一个没有写出的收盘百分比，也不把 +6%、+5%、177 美元和盘后的 -10% 收成一天。不把 174、176、179、185、200、225、300 放进同一个目标。不把 57%、71%、80%、70%、85%、超过 90% 和“80% 已定价”收成一个概率。不把 Kress 和 Ian Buck 收成已经公布的继任者。不把白宫“不介入”写成“已经同意撤掉”。不把 CoreWeave 的 +24.71%、+25%、+20.8% 和盘后 -6% 取一个涨幅。不把投资级贷款和更正后的高收益贷款并成一种评级。不把 470 亿美元、91.8 亿美元和 243.9 亿美元收成一项债务。不把 WTI 的 86.53 美元和布伦特的 92.76 美元对调，也不把 92.44 美元、跌 1 美元和盘中的上涨 3 美元写成结算。不把井口的 1056.3 万桶写成市场供应的 920.3 万桶。不把零售汽油 3.94 美元写成期货的 2.6075 美元。不把黄金的 4,002.54 美元和“4,000 下方”合成一个收盘。不把 4.99% 的 10 年期和 4.7756% 的 2 年期对调。不把 Gary 的超过 85% 和 Brooks 的 76 个基点收成同一个 12 月概率。不把礼来的盘前 +2% 写成芯片股的盘前跌幅。德意志银行的时间线没有读到。Cathie Wood 的账号没有新帖。美联储账号没有单独重述 50 个基点。

## 全站搜索里、排在这 100 个账号之外的讨论

搜索结果用来看讨论范围，不拿来改上面的收盘数字。讨论集中在要不要把黄仁勋换掉，而不是周三的点位。DHH（约 95 万粉，不在这 100 个账号里）写，因为婚外情解雇黄仁勋是错的，那是他、他的妻子和董事会 reprimand 之间的事，要有比例感：[帖](https://x.com/dhh/status/2120801995615604849)。这句和 Kobeissi 写给董事会的长帖方向相同，粉丝数在截止线外。另一条高互动帖把 Semafor 的临时人选写成 Colette Kress，并称这一串新闻闻起来不对：[帖](https://x.com/Pirat_Nation/status/2120788166323900856)。零对冲的时间线只写了“首席财务官 Kress”，没有写 Colette。搜索里还有把英伟达写成“正在找新首席执行官”的新闻转述，以及和 DLSS 竞品有关的显卡帖。代币喊单和德语段子出现在同一批搜索里，不进入价格表。搜索没有给出一张与 First Squawk 不同的周三收盘点位，所以 7,619.22、25,465.38 和 52,465.11 仍以他的收盘帖为准。

## 帖文索引

收盘和开盘：[开盘 7,592.62](https://x.com/FirstSquawk/status/2120524934007202168)、[标普收盘 7,619.22](https://x.com/FirstSquawk/status/2120623000294977744)、[纳斯达克收盘 25,465.38](https://x.com/FirstSquawk/status/2120623082771726482)、[道指收盘 52,465.11](https://x.com/FirstSquawk/status/2120622927242756224)。

英伟达和利率：[盘后超过 -10%](https://x.com/KobeissiLetter/status/2120646315503985114)、[不要解雇](https://x.com/KobeissiLetter/status/2120696537458114929)、[12 月会加息](https://x.com/NickTimiraos/status/2120495446179131412)、[76 个基点](https://x.com/robin_j_brooks/status/2120616483726229667)、[Baird 200 美元](https://x.com/DeItaone/status/2120481933515772150)。

油、黄金和 CoreWeave：[WTI 86.53](https://x.com/financialjuice/status/2120600232870519044)、[布伦特 92.76](https://x.com/financialjuice/status/2120603744941318555)、[布伦特 92.44](https://x.com/FirstSquawk/status/2120814310456963146)、[黄金 4,002.54](https://x.com/FirstSquawk/status/2120670651250094183)、[CoreWeave 24.71%](https://x.com/CNBC/status/2120659582506684560)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-12 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 271 条、彭博商业账号 312 条、FinancialJuice 298 条、零对冲 117 条，是读穿窗口后的计数。德意志银行、美国银行、CNBC Now、芝商所的 0 是读取失败。沃伦·巴菲特和 Downtown 的 0 是空页。Charlie Bilello 的 0 是 7 条都被标成转发。线外的 First Squawk 是 324 条。保罗·克鲁格曼、Cathie Wood、BBC Business、markets、CNN Business、美联储、高盛、美国财政部、Lyn Alden、纽约时报商业、摩根大通、花旗、Hindenburg、economics、摩根士丹利、Nouriel、fundstrat、Carl Icahn、彭博主号、安德鲁·罗斯·索尔金的 0，是窗口内没有计为原创的新帖。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,446,989 | 271 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,330,193 | 90 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,282,163 | 62 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,312,036 | 39 |
| 5 | [@business](https://x.com/business) | 10,495,309 | 312 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,574,577 | 1 |
| 7 | [@FT](https://x.com/FT) | 7,119,184 | 64 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,259,416 | 75 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,378,950 | 54 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,650,389 | 34 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,617,899 | 2 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,434,348 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,354,644 | 43 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,433,047 | 117 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,428,847 | 19 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,052,469 | 1 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,009,010 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,741,383 | 17 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,574,102 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,535,498 | 16 |
| 21 | [@chamath](https://x.com/chamath) | 2,492,985 | 1 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,440,141 | 11 |
| 23 | [@BW](https://x.com/BW) | 2,288,599 | 5 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,368 | 31 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,157,052 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,128,503 | 2 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,080,965 | 26 |
| 28 | [@markets](https://x.com/markets) | 2,049,642 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,974,151 | 66 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,797,612 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,779,635 | 7 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,772,027 | 26 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,711,921 | 7 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,701,670 | 10 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,362 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,620,299 | 26 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,604,296 | 0 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,540,212 | 53 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,513,649 | 3 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,472,874 | 17 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,472 | 5 |
| 42 | [@Bloomberg](https://x.com/Bloomberg) | 1,359,395 | 0 |
| 43 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,359,363 | 5 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,256,855 | 3 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,225,058 | 66 |
| 46 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,196,476 | 0 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,194,991 | 5 |
| 48 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,194,712 | 5 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,184,813 | 5 |
| 50 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,172,325 | 23 |
| 51 | [@USTreasury](https://x.com/USTreasury) | 1,166,498 | 0 |
| 52 | [@nntaleb](https://x.com/nntaleb) | 1,165,841 | 3 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,158,210 | 0 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,155,755 | 12 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,140,073 | 0 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,118,295 | 3 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,107,594 | 16 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,097,809 | 5 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,082,316 | 3 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,069,350 | 10 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,309 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,988 | 34 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,004,787 | 1 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 957,353 | 298 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 945,915 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 934,821 | 16 |
| 67 | [@tradingview](https://x.com/tradingview) | 909,182 | 1 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 895,015 | 18 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 891,812 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,557 | 20 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 874,699 | 0 |
| 72 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 867,966 | 12 |
| 73 | [@axios](https://x.com/axios) | 865,033 | 12 |
| 74 | [@steve_hanke](https://x.com/steve_hanke) | 862,175 | 34 |
| 75 | [@jpmorgan](https://x.com/jpmorgan) | 861,071 | 0 |
| 76 | [@Citi](https://x.com/Citi) | 853,121 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 847,580 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,594 | 1 |
| 79 | [@ecb](https://x.com/ecb) | 831,317 | 4 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,678 | 1 |
| 81 | [@bgurley](https://x.com/bgurley) | 812,094 | 3 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,231 | 1 |
| 83 | [@economics](https://x.com/economics) | 806,110 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 789,749 | 2 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,727 | 5 |
| 86 | [@markminervini](https://x.com/markminervini) | 776,892 | 9 |
| 87 | [@leadlagreport](https://x.com/leadlagreport) | 769,117 | 22 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 760,025 | 0 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,445 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 742,802 | 0 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 719,012 | 18 |
| 92 | [@Nouriel](https://x.com/Nouriel) | 714,132 | 0 |
| 93 | [@CMEGroup](https://x.com/CMEGroup) | 712,407 | 0 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 674,647 | 9 |
| 95 | [@fundstrat](https://x.com/fundstrat) | 672,573 | 0 |
| 96 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,486 | 7 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 647,285 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,525 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 636,193 | 3 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 625,971 | 4 |
