# 美股 Twitter 观点日报 · 2026-11-24

美东周一的现货在这个窗口里走完了。主线是英伟达董事会把黄仁勋请回来：纳斯达克 100 期货在上涨 7% 之后短暂停牌，非官方收盘是道指 49,662.07（+3.15%）、标普 7,243.61（+4.82%）、纳斯达克综合指数 24,101.62（+6.56%）。同一天还有标普 +4.7% 和 +4.73% 两套收盘，不取平均。抓取结束时是美东周二清晨，现货还没开。最新一张通讯社期货帖把标普电子迷你改成下跌 0.4%、纳斯达克 100 期货下跌 0.9%、道指期货下跌 0.1%，英伟达盘前先写 -4%，随后写 -3.5%。这是公开帖文的整理，不是投资建议。

下面每一条归纳都附有帖文链接。

## 抓取口径

- 报告日期按北京时间 **2026-11-24**。触发时刻约 10:00 UTC，时间线补抓到 **约 10:09 UTC（北京时间 18:09，美东周二 5:09）**。美国夏令时已经结束。周一现货全天、收盘和盘后在这个窗口里。周二现货未开。戴尔的财报、PCE 和 GDP 都还没有结果。
- 观察窗口从 **2026-11-23 10:06 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周一大约 5:06 以后的盘前、现货、收盘，以及美东周二凌晨到大约 5:09。
- X 的官方连接器这次仍然没有搜索和时间线工具。粉丝数和时间线用 `https://api.fxtwitter.com/2/profile/{handle}` 与 `/statuses`，必须带浏览器 User-Agent，并加 `?_={ns}`。结果键是 `results`。空 404 要原请求重试。分页参数是 URL 编码的 `cursor`。时间线不是严格倒序，连续两页的最新帖都早于窗口再停。全站搜索这次返回 503，不能当成全站讨论。抓取开始时的趋势是 #iskadiyebiri、Jensen Huang、Commanders、Thanksgiving、Sanofi、Jags。结束时 Thanksgiving 和 Sanofi 不在了，换成 Monday Night Football 和 Tom Jackson。Jensen Huang 还在，上下文是商业和金融。没有美股代码。
- 不存在官方的“美股 Top 100”。这次沿用上一份已经排过的金融候选，并补了紧贴截止线的账号，成功读到粉丝数之后重新排序。三处对调：IMF（4,652,901）到 MarketWatch 前面；Squawk Box（1,196,037）到 Stocktwits 前面；Mark Minervini（793,852）到 Bianco Research 前面。截止仍是 Eric Balchunas（624,876）。Morning Brew（594,831）第 101。Bloomberg Opinion 的 `@opinion`（586,944）第 102。投资人 Gary Black 仍是 [@garyblack00](https://x.com/garyblack00)（586,401），第 103，这个窗口 5 条。Barchart（582,257）第 104。First Squawk（580,520）第 105，仍在 Cboe（577,805）前面。排序不代表预测准确度。
- 100 个账号里，**75 个**在窗口内有按帖文链接去重后、且接口没有标成回复或转发的原创帖。路透读穿窗口，原创 264 条。彭博商业账号原创 304 条。零对冲原创 142 条。DeItaone 原创 106 条。FinancialJuice 原创 201 条。《华尔街日报》原创 91 条。CNBC 原创 90 条。《经济学人》原创 89 条。The Street 原创 70 条。《金融时报》原创 61 条。线外的 First Squawk 原创 247 条，读穿到窗口起点之前。德意志银行的时间线仍是 500，表里的 0 不是确认沉默。fundstrat 的 0，是可见帖被接口标成转发或回复。Cathie Wood、美联储、彭博主号、markets 的 0，是可见时间线早于窗口。Warren Buffett 和 Downtown 是空页。

## 复职之前是一条盘前，熔断之后才是周一的现货

黄仁勋的董事会决定大约在周一 13:57 UTC 才进时间线。在那之前，盘前是上一份期货反弹的延续，不是后来的 +7%。

线外 Gary Black 10:29 UTC：标普 +2.7%，纳斯达克 +3.5%，英伟达 +8.5% 到 136 美元。布伦特 92 美元，他写成 11 月大约 -23%。10 年期 4.96%。12 月加息概率写成大于 100%：[136 美元](https://x.com/garyblack00/status/2124812678522675561)。Kobeissi 11:15 UTC：纳斯达克 100 期货盘前将近 +4%，有望成为 2025 年 5 月以来最大的单日涨幅：[将近 +4%](https://x.com/KobeissiLetter/status/2124824171628863961)。+2.7%、+3.5% 和将近 +4% 都早于复职标题，不并进开盘后的 +5% 和 +7%。

复职标题出来之后，期货百分数换了一档。线外 First Squawk 14:00 UTC：标普 500 期货涨幅扩到 3.8%，纳斯达克 100 期货跳升 6%：[3.8%](https://x.com/FirstSquawk/status/2124865637969518603)。DeItaone 14:02 UTC：标普电子迷你 +3.9%，纳斯达克 100 期货 +6.2%，道指期货 +2.4%：[3.9%](https://x.com/DeItaone/status/2124866291890610566)。随后是停牌，不是这三张百分数的平均值。DeItaone：纳斯达克在黄仁勋复职后触及涨停并暂停：[涨停](https://x.com/DeItaone/status/2124870414962962700)。同一分钟他又写，纳斯达克 100 期货在跳升 7% 之后短暂波动性停牌：[7%](https://x.com/DeItaone/status/2124871293023535410)。First Squawk 的用词是 “HALTER”，纳斯达克 100 期货在飙升 7% 之后停牌：[HALTER](https://x.com/FirstSquawk/status/2124871809451671594)。Kobeissi：纳斯达克 100 期货因英伟达请回黄仁勋、上涨 7% 之后停牌：[停牌](https://x.com/KobeissiLetter/status/2124871861804654908)。StockMKTNewz 写成 7% 的熔断：[熔断](https://x.com/StockMKTNewz/status/2124871028438643144)。停的是期货。没有人把现货写成触发了 7% 的市场熔断。

开盘点位只引用 First Squawk。道指 49,487.64，上涨 1,340.31 点，或 2.78%：[开盘道指](https://x.com/FirstSquawk/status/2124873679243010388)。标普 7,251.32，上涨 340.93 点，或 4.93%：[开盘标普](https://x.com/FirstSquawk/status/2124873708691239325)。另一张帖是标普指数开盘跳升 5.1%，纳斯达克 100 上涨 7.4%：[5.1%](https://x.com/FirstSquawk/status/2124874403993596204)。7,251.32 对 +4.93%，和“指数跳升 5.1%”，是两张开盘帖。

盘中继续分着写。First Squawk：纳斯达克 100 升到当日新高，上涨 7.6%：[7.6%](https://x.com/FirstSquawk/status/2124886173764268318)。标普涨幅扩到 5.5%：[5.5%](https://x.com/FirstSquawk/status/2124889370180366712)。Kobeissi：标普涨幅扩到 +5.3%，有望成为 2025 年 4 月以来最大的一天，美股市值当天增加 3.5 万亿美元：[3.5 万亿](https://x.com/KobeissiLetter/status/2124895247121654238)。DeItaone：纳斯达克综合指数涨幅扩到最后上涨 7.4%：[综合指数 7.4%](https://x.com/DeItaone/status/2124886200368484791)。纳斯达克 100 有望增加超过 2 万亿美元市值，最后上涨超过 6%：[2 万亿](https://x.com/DeItaone/status/2124881478672658547)。后来 First Squawk 写纳斯达克 100 涨幅收到 6.5%：[收到 6.5%](https://x.com/FirstSquawk/status/2124906131206414427)。7.6%、7.4%、超过 6%、6.5% 不收成一个盘中高点。3.5 万亿是这张盘中帖，不是收盘。

收盘至少三套，外加一张综述。First Squawk 的非官方收盘：道指 49,662.07，+3.15%，上涨 1,514.74 点：[道指](https://x.com/FirstSquawk/status/2124972028721770792)。标普 7,243.61，+4.82%，上涨 333.22 点：[标普](https://x.com/FirstSquawk/status/2124972142613950551)。纳斯达克综合指数 24,101.62，+6.56%，上涨 1,483.89 点：[纳指](https://x.com/FirstSquawk/status/2124972344641020229)。同一账号稍后的综述是另一句：英伟达上涨 31%，纳斯达克 100 跳升 6.9%，标普上涨 4.7%，2025 年 4 月以来最大的一天：[31% / 6.9% / 4.7%](https://x.com/FirstSquawk/status/2124976863508660657)。6.9% 是纳斯达克 100。6.56% 是综合指数。4.82% 和 4.7% 并列。

Kobeissi 的收盘句是标普 +4.7%，正式成为 2025 年 4 月以来最好的一天，美股当天增加超过 3 万亿美元：[超过 3 万亿](https://x.com/KobeissiLetter/status/2124971344043622642)。3 万亿不替换盘中的 3.5 万亿。线外 Nick Timiraos 把标普和纳斯达克写成 +4.7% 和 +6.5%，并且写成自 2025 年 4 月 9 日“解放日”关税暂缓以来最好的一天。道指和纳斯达克今年至今都超过 +3%，标普今年至今将近 +6%：[4 月 9 日](https://x.com/NickTimiraos/status/2124991158111842802)。帖文写的是 Nasdaq indices，这里不把它改判成综合指数或纳斯达克 100。+6.5% 不替换 First Squawk 的综合指数 +6.56%，也不替换综述里的纳斯达克 100 +6.9%。

线外 RedDog 的收盘铃是第四套：标普 7,237.17，+4.73%，他写成结束了七连跌。纳斯达克 24,089.56，+6.51%。道指 49,595.31，+3.01%，+1,448 点：[收盘铃](https://x.com/RedDogT3/status/2124990286254276794)。7,237.17 不是 7,243.61。24,089.56 不是 24,101.62。49,595.31 不是 49,662.07。+4.73% 也是线外 Bespoke 用来排名的数字：过去 25 年标普第二十四好的一天：[第二十四](https://x.com/bespokeinvest/status/2124973223351627842)。线外 Ryan 用的是 +4.7%：过去 20 年 25 个最好的交易日里排第 21。这些日子之后，下一个交易日和下一周上涨的次数都只有 29%。一年之后 24 次里 23 次上涨，平均 +29.8%，普通日子是 +10.2%。唯一没涨的是 2008 年 9 月 30 日：[29%](https://x.com/RyanDetrick/status/2125010173911498925)。+29.8% 是历史平均，不是这次的目标。

点数不要自行轧差。7,243.61 减去 333.22 等于 6,910.39，对得上上一份里 RedDog 周末简报的周五标普，对不上上一份 First Squawk 的周五 6,902.03。24,101.62 减去 1,483.89 等于 22,617.73，对得上那份简报里的纳斯达克，对不上 22,620.17。49,662.07 减去 1,514.74 等于 48,147.33，对得上那份简报里的道指。这里不改任何一张周五帖。

## 英伟达：董事会请回了人，涨幅从盘前 +8.5% 走到收盘附近的三套

董事会的句子和调查的句子同时在。DeItaone：董事会一致投票，立即恢复黄仁勋的总裁、首席执行官和董事身份。帖文写董事会认为复职没有国家安全风险。Colette Kress 继续当首席财务官，Harvey Jones 继续当董事长。公司还要成立委员会，调查一项指控：[一致投票](https://x.com/DeItaone/status/2124864807429968103)。FinancialJuice 的标题是调查在复职之后继续：[调查继续](https://x.com/financialjuice/status/2124864923809529897)。“没有国家安全风险”不覆盖“调查继续”。

StockMKTNewz 引了公司声明的开头：立即生效，董事会在和黄仁勋以及高级政府官员讨论之后一致投票：[声明](https://x.com/StockMKTNewz/status/2124865588778447051)。零对冲贴了同一份新闻稿：[新闻稿](https://x.com/zerohedge/status/2124865663214698990)。Kobeissi 引了黄仁勋的声明，他感谢董事会和董事长 Harvey Jones，也感谢 Colette Kress 和经营班子在他离开期间带队：[声明](https://x.com/KobeissiLetter/status/2124871560028725383)。线外 LiveSquawk 把委员会写成调查针对黄仁勋的外国情报行动，Harvey Jones 留任董事长：[委员会](https://x.com/LiveSquawk/status/2124867529482928149)。

过程不要写成董事会主动、平静的决定。DeItaone 引彭博：特朗普施压，董事会在周日几小时内作了决定，没有咨询临时首席执行官 Colette Kress 和其他高管，他们到最后一刻才知道：[没有咨询](https://x.com/DeItaone/status/2124925801376161947)。unusual_whales 是同一句，并写一些替代人选已经退出搜寻：[最后一刻](https://x.com/unusual_whales/status/2124963446537981994)。线外 Gary 据此写，如果高管确实没被咨询，高层还会再波动：[再波动](https://x.com/garyblack00/status/2125016235679388023)。

复职之前的概率已经过期。DeItaone 在董事会标题之前写：Arm 的 Rene Haas 把任期延到 2033 年，12 月 1 日起兼任软银副董事长。当时预测市场是黄仁勋 17%，Haas 14%，Ian Buck 13%。黄仁勋刚超过 Haas，成为预测市场里的热门，首席执行官仍不确定：[17%](https://x.com/DeItaone/status/2124836301778116808)。17% 是决定公布前的帖，不是复职之后的概率。Kobeissi 同一时段写 Haas 表态长期留下，英伟达当时的涨幅是超过 +8%：[超过 +8%](https://x.com/KobeissiLetter/status/2124838190666199095)。超过 +8% 对得上 Gary 的 +8.5%，不是后来的 +30%。Haas 留下和黄仁勋回来是前后两张帖，不并成“两个人选还在竞争”。

盘前路径按时间留着。Gary 的 +8.5% 到 136 美元最早。DeItaone：盘前一度 +25%，打到当时的高点：[+25%](https://x.com/DeItaone/status/2124865047247667390)。随后涨幅扩到 +27%：[+27%](https://x.com/DeItaone/status/2124865950306705469)。First Squawk：盘前涨幅超过 30%：[超过 30%](https://x.com/FirstSquawk/status/2124866780611194965)。DeItaone 的清单是 +31.19%，旁边 CoreWeave +33.52%、Nebius +32.21%、IREN +24.02%、超微 +19.66%、美光 +17.61%：[+31.19%](https://x.com/DeItaone/status/2124867095389159800)。136 美元不换成这些百分比。

盘中和收盘也不并。Kobeissi 14:30 UTC：涨幅超过 +35%，当天市值增加 1 万亿美元；如果收在当时的位置，将是历史上第一家单日增加 1 万亿美元的公司：[如果收在](https://x.com/KobeissiLetter/status/2124873304464904473)。“如果”没有变成收盘句。他 19:04 UTC 的科技清单把英伟达写成 +32%，戴尔 +22%，Nebius 和 CoreWeave 各 +21%，美光 +19%，Arm 和台积电各 +16%：[+32%](https://x.com/KobeissiLetter/status/2124942055952482332)。收盘帖是另一张：+31.6%，市值增加 9,550 亿美元，他写成史上任何一只股票最大的单日市值增幅，这个增幅超过全球除 15 家以外所有公司的总市值：[9,550 亿](https://x.com/KobeissiLetter/status/2124974519567737034)。

线外的数字并列，不覆盖 9,550 亿。Ryan 开盘两小时：市值增加将近 1 万亿美元，微软的纪录是 4,500 亿美元：[两小时](https://x.com/RyanDetrick/status/2124905134731723005)。收盘附近他写成增加 9,540 亿美元：[9,540 亿](https://x.com/RyanDetrick/status/2124973974366966185)。RedDog 午盘大约 +33%，到大约 166 美元，市值回到 4 万亿美元上方：[午盘](https://x.com/RedDogT3/status/2124909363164786692)。收盘铃是 +31.5%，大约 9,520 亿美元，2003 年以来最好的一天：[收盘铃](https://x.com/RedDogT3/status/2124990286254276794)。Bespoke 的 167 美元是条件句：如果在 167 美元，当天市值增加就是 1 万亿美元：[167 美元](https://x.com/bespokeinvest/status/2124870508512755765)。166、167 和 136 不取一个收盘价。9,550 亿、9,540 亿、9,520 亿和“将近 1 万亿”并列。+31.6%、+31.5%、综述里的 31%、清单里的 +32%、盘中的 +35% 和 +31.19% 并列。

Bespoke 还写了三句不能并进涨幅的位置。英伟达六个月仍跌 23%。两倍做空的 $NVD 当天跌 62%，六个月仍跌 15.9%：[62%](https://x.com/bespokeinvest/status/2124929751139655746)。距历史高点仍有 30%：[30%](https://x.com/bespokeinvest/status/2124890279861768442)。标普仍在 200 日均线下方 2%，纳斯达克 100 仍在下方 5%：[200 日](https://x.com/bespokeinvest/status/2124883352041710022)。英伟达大约贡献了标普 326 点里的 110 点：[110 点](https://x.com/bespokeinvest/status/2125045488382550079)。326 点不是 First Squawk 的 333.22 点。另一张帖把英伟达写回市值第二，排到微软和字母表前面，用的是 +31.5%。原句是 “Jensen's back as #1, NVIDIA back at #2”，这里不把 #1 改写成某一家公司：[第二](https://x.com/bespokeinvest/status/2124984164986622038)。Business Insider 是另一套市值：被赶下台之后抹掉超过 1 万亿美元，回来之后 9,000 亿美元也回来了：[9,000 亿](https://x.com/BusinessInsider/status/2124918920461087106)。9,000 亿不是 9,550 亿。

杠杆产品是第三条路径。线外 Hedgeye：三倍做空英伟达的 ETF 在下跌 91.4% 之后停牌：[91.4%](https://x.com/Hedgeye/status/2124894484056228115)。线外 Jesse Cohen 自己写了同一句 -91.4%：[RIP](https://x.com/JesseCohenInv/status/2124963014004572222)。Eric Balchunas 写的是欧洲的一只 -3 倍英伟达 ETP，几秒内下跌 91%，并拿已清盘的 $XIV 单日 -92% 作对照：[欧洲](https://x.com/EricBalchunas/status/2124887432940401139)。91.4%、91% 和 $NVD 的 62% 是三只产品。成交额是另一句：英伟达当天成交超过 1,000 亿美元，这是它第三次，特斯拉有过一次，标普 ETF 接近十次：[1,000 亿](https://x.com/EricBalchunas/status/2124959800530440358)。

立场按人留下。线外 Gary：他承认自己说错了，黄仁勋不会被请回来；英伟达仍是他最重的多头之一。另一张帖写，危机最高的 11 月 17 日，被问什么时候回来买，他的一个词是“现在”。2027 年 EV/EBITDA 8.3 倍，收入和 EBITDA 在可见的将来每年增长 25%，他写成当时自己股票池里最便宜的科技股：[现在](https://x.com/garyblack00/status/2124977241499054580)、[说错了](https://x.com/garyblack00/status/2124955218680942637)。Minervini：早盘看起来很猛，正是他平掉空头的原因。超卖足以走出撕脸的反弹。下跌这边大约拿到 7 倍初始风险。10% 到 30% 的反弹在图上大多仍是向下趋势里的逆向波动。标普从 10 月 6 日高点跌了 11.6%，这是 2025 年 2 月到 4 月那轮抛售以来的第一次 10% 修正。他还没走出树林：[平空](https://x.com/markminervini/status/2124875682576531796)。稍后只有两个词：他回来了：[回来了](https://x.com/markminervini/status/2124950425996501347)。

Peter Brandt：即便 NQ、ES、M2K、YM 今天上涨，趋势仍是向下。V 型延伸底有可能，但举证责任在价格：[趋势仍向下](https://x.com/PeterLBrandt/status/2125035697396736135)。Burry：英伟达比他想的更软弱。他要司法部继续反垄断，证券交易委员会继续查账：[继续查](https://x.com/michaeljburry/status/2124876426486681864)。Kevin O'Leary：公司会在他重新当首席执行官的情况下接受调查，证券交易委员会已经让所有人知道他们在查，这是前所未有的反转：[调查](https://x.com/kevinolearytv/status/2124942994495132112)。Cramer：先是仓促调查，然后是一场绞刑，现在欢迎回来。他预计从“他不会回来”到“他在这儿”会有一大堆余波：[余波](https://x.com/jimcramer/status/2124995015713931598)。Chamath：总统进了董事会电话，说“这里没什么可看的”，这是能从美国政府拿到的最能放在台面上的一句。他另写过去几周是一次演习，紧急状态还会回来，开源要踩油门：[台面上](https://x.com/chamath/status/2124890007651660011)。Ackman 只有一句：群众的智慧占了上风：[群众](https://x.com/BillAckman/status/2124872767309050160)。

线外 Hedgeye 不把反弹写成解套。最大的反弹出现在他定义的 Quad 4 熊市里，因为跌得最多、波动也升得最多。反弹不是全面解除警报，是打扫日子：卖掉本该在更高的地方卖掉的东西：[打扫](https://x.com/Hedgeye/status/2124889278345814151)。Keith McCullough 经他们转述：他不知道这是不是底，只知道告诉你这是底的人，正是一开始没让你出来的人：[不是底](https://x.com/Hedgeye/status/2124911952107360352)。纳斯达克 100 被他们写成抹掉了今年的亏损，2026 年至今 +5.5%：[+5.5%](https://x.com/Hedgeye/status/2124878340725055755)。+5.5% 是纳斯达克 100 的今年至今。Nick Timiraos 的“纳斯达克今年至今超过 +3%、标普将近 +6%”是另一套，不互相改。

线外 SpotGamma 的交易日记录和收盘涨幅分开。开盘设置：卖出 6,460 万美元英伟达看涨期权，另外是 12 月的 SOXX 看跌价差 3,780 万美元、QQQ 看跌价差 2,370 万美元。标普 gamma 仍是负的，所以两边的波动都可能还大：[开盘设置](https://x.com/spotgamma/status/2124869357373157846)。盘中一张是标普 ETF +5%、QQQ +8%、英伟达 +36%、Anthropic -0.8%：[盘中](https://x.com/spotgamma/status/2124889171001008134)。负 gamma 一直堆到 200 美元，穿过圣诞节：[200 美元](https://x.com/spotgamma/status/2124889075933200863)。收盘后：周五是期权到期的恐慌，周一是爆炸式反转。负 gamma 会把已实现波动往两个方向放大。他的 HIRO 在标普个股被买的时候继续上升，先是 10 亿美元，随后 14 亿美元，工具显示的是不要做空：[不要做空](https://x.com/spotgamma/status/2125031789320085698)。+36% 和 -0.8% 是这张盘中帖，不是收盘。200 美元是 gamma 位置，不是目标价。

Ryan 还补了两个位置。标普相对 50 日均线曾经在 -4.1 个标准差，当时写成历史级，现在收到 -2.3 个：[标准差](https://x.com/RyanDetrick/status/2124879062157906271)。收盘前一小时，标普里 428 只在上涨：[428](https://x.com/RyanDetrick/status/2124960901807894572)。他另写标普当天的市值增幅是史上第二大：[第二大](https://x.com/RyanDetrick/status/2124987794971922633)。第二大是标普。英伟达那张是单只股票。不要并。

## Anthropic 没有收盘价，两倍产品的代码仍是三套

正股全天和芯片的方向相反，但没有一张通讯社美元收盘价。盘前先是 DeItaone 的抹掉涨幅、最后 -0.3%，然后打到盘前低点 -1.5%。零对冲写转负，此前最多上涨 5.6%，帖文里的单词拼成了 “NAEGATIVE”：[转负](https://x.com/zerohedge/status/2124847173515014519)。复职之后 DeItaone 写成最后盘前 +4.5%，再写成最后 -3%：[-3%](https://x.com/DeItaone/status/2124874313295593808)。Hedgeye：科技在反弹，Anthropic 继续更低。彭博商业的标题是周一下跌，没有跟上黄仁勋带来的板块反弹：[周一下跌](https://x.com/business/status/2124982455320904025)。-0.3%、-1.5%、+5.6%、+4.5%、-3%、SpotGamma 的 -0.8% 和“周一下跌”并列。

两倍产品周一开了，代码不要并。unusual_whales：Tradr 的 $ANTT 是两倍做多，$ANTZ 是两倍做空，已经在交易：[ANTT](https://x.com/unusual_whales/status/2124870177619865838)。同一账号后来有一张帖把 $ANTZ 叫成两倍做多，并写开盘 30 分钟成交 5 万股。StockMKTNewz 把 $ANTZ 写成两倍做空，30 分钟 9 万股，90 分钟那张是 17 万股。5 万、9 万、17 万不相加，多空方向以各自的帖为准。DeItaone 的 Leverage Shares 仍是 $ANUU 做多、$ANDD 做空。unusual_whales 的 GraniteShares $AIL / $ANS 仍写成即将。Eric Balchunas 数了 14 只杠杆 Anthropic ETF 同一天上市：[14 只](https://x.com/EricBalchunas/status/2124858968476463477)。

83 美元不是周一的成交价。First Squawk：Anthropic 首席执行官 Daniela Amodei 大约卖出 340 万股 A 类股，每股 83 美元：[Daniela](https://x.com/FirstSquawk/status/2124999375592284412)。FinancialJuice：首席执行官 Dario Amodei 在 11 月 20 日卖出 338 万股，每股 83 美元，依据是 SEC 文件：[Dario](https://x.com/financialjuice/status/2124999383707967607)。Daniela 和 Dario、340 万和 338 万，不并成一个人。11 月 20 日是周五的申报，不是周一收盘。线外 Barchart 的“较首日交易价跌 20%”是跨日句子，不写成周一的跌幅。

El-Erian：到目前为止，而且还早，Anthropic 的走势像 SpaceX 上市之后的路径，只是快进：[快进](https://x.com/elerianm/status/2124955847000535482)。unusual_whales 引《华尔街日报》：公司亏损，成立不到六年，华尔街不确信它应付得了长期义务，债市预期评级会是垃圾级：[垃圾级](https://x.com/unusual_whales/status/2124824531395067947)。CNBC 的 Faber 经 DeItaone：黄仁勋回来对 Anthropic 可能是负面的，理由是他支持开源：[开源](https://x.com/DeItaone/status/2124876977077473740)。

## 采购经理人指数偏软，威廉姆斯要“随着时间”行动，油价却在下跌

美国标普全球初值 PMI 已经出来，预期有两套。FinancialJuice：综合 54.6（预期 55.6，前值 55.9），制造业 54.5（预期 54.5，前值 54.9），服务业 54.7（预期 55.5，前值 56.1）：[综合](https://x.com/financialjuice/status/2124876980671725888)、[制造业](https://x.com/financialjuice/status/2124876995326836963)、[服务业](https://x.com/financialjuice/status/2124877007536165340)。LiveSquawk 和 Liz Ann 的预期与这套相同：[Liz Ann](https://x.com/LizAnnSonders/status/2124893566853894290)。DeItaone 的服务业预期写成 55.7，不是 55.5：[55.7](https://x.com/DeItaone/status/2124877138289721495)。54.6、54.5、54.7 是实际数。55.5 和 55.7 是两套预期。RedDog 的午报把服务业预期写成 55.8，市场没理会这份偏软的 PMI。

威廉姆斯的原句按通讯社留着，不收成一次已经宣布的加息。FinancialJuice 和 First Squawk：还必须把通胀拉回 2%。通胀在 2026 年结束时应该是 3.5%，2028 年回到 2%。失业率明年回到 4%。经济 2026 和 2027 年都增长 2.75%。通胀仍然太高，风险偏向上行，但他看不到通胀压力明显扩散。人工智能的影响不确定，就业市场稳定，能源价格前景不确定：[3.5%](https://x.com/FirstSquawk/status/2124972399364092060)。稍后：2027 年会是通胀更低的一年，最近把通胀推高的是不寻常的因素。强增长的底座仍有挑战：[2027](https://x.com/FirstSquawk/status/2124981452794405358)。再稍后：科技板块的波动没有推翻正的经济前景。如果通胀压力不缓解，美联储会回应，必要的话连续会议加息。他没有把一条利率路径写进铅笔稿，也不排除任何节奏：[连续会议](https://x.com/FirstSquawk/status/2125006629355827561)。

Nick Timiraos 的读法是：还会再收紧，但他不主张过度跟着最近偏热的通胀数据走。10 月 28 日开会以来，经济“仍然强”，通胀“继续太高”。“还有工作要做”，“必须随着时间采取行动”。他的提醒是，政策要一到两年才完全起作用，所以要向前看：[随着时间](https://x.com/NickTimiraos/status/2124989372630184215)。CNBC 的标题是更高的利率很可能“随着时间”用来对付通胀。彭博的标题是官员必须“随着时间”对通胀采取行动。三张标题都没有写出 25 还是 50。

概率因此仍是几套。El-Erian 14:02 UTC：不管看市场定价还是 Kalshi，加息概率仍在 90% 上方：[90% 上方](https://x.com/elerianm/status/2124866266578268560)。19:06 UTC：12 月 9 日不加息会非常难。市场和预测市场对 25 个基点的预期都在 90% 上方。50 个基点在他看来对经济和金融都是不明智的：[不要 50](https://x.com/elerianm/status/2124942766862131397)。Liz Ann：或许部分因为人回来了，CME FedWatch 的加息概率接近 100%，周五是 88%：[接近 100%](https://x.com/LizAnnSonders/status/2124872576056832045)。Gary 早上的“大于 100%”早于演讲，也早于复职。接近 100%、90% 上方、大于 100%、周五的 88%，不收成一个数。没有人在这个窗口写出新的联邦基金利率区间。

原油结算和股市的方向相反。FinancialJuice：NYMEX WTI 1 月期货结算 80.17 美元，下跌 3.24 美元，3.88%：[80.17](https://x.com/financialjuice/status/2124948970367496643)。First Squawk 用了同一组数字：[同一组](https://x.com/FirstSquawk/status/2124949006036214245)。布伦特结算 89.37 美元，下跌 3.20 美元，3.46%：[89.37](https://x.com/financialjuice/status/2124951846737658015)。Hedgeye 的盘中是布伦特 -3.2%，跌到 90 美元下方。Gary 早上的 92 美元早于这张结算。80.17 对 3.88%，89.37 对 3.46%，按帖保留，不跟上一份的周五 83.98 和 92.57 自行轧差。布伦特的 3.20 美元刚好等于 92.57 减 89.37，这里只当作算术，不把两天收成一张结算。

黄金是一条路径，不是一个收盘。复职之前 DeItaone 引瑞银：黄金靠近 3,500 美元，期货未平仓减少相当于超过 600 万盎司，ETF 持仓大体稳定，但在更高价位积累的 166 吨流入可能面临卖压：[3,500](https://x.com/DeItaone/status/2124846138851307820)。停牌那一刻，DeItaone 和 First Squawk 都写现货黄金涨幅接近 4%，到 3,673.36 美元：[3,673.36](https://x.com/DeItaone/status/2124871204645613915)。收盘后的综述是另一句：最多反弹 4.3%，到大约 3,690 美元；现货上涨 3.3%，到 3,656.82 美元：[3,656.82](https://x.com/FirstSquawk/status/2124976410062467472)。周二 First Squawk：黄金上涨将近 1%，到 3,666.01 美元：[3,666.01](https://x.com/FirstSquawk/status/2125042777230917926)。3,500、3,673.36、3,690、3,656.82、3,666.01 并列。Bespoke 的盘中是黄金 ETF +4.5%、白银 ETF +6.5%，不换算成美元现货。

10 年期没有新的收盘点位。Gary 早上是 4.96%。Hanke 在复职之后写，各期限收益率上升，10 年期重新靠近 5.0%：[靠近 5.0%](https://x.com/steve_hanke/status/2124934505849065529)。4.96% 和“靠近 5.0%”并列。路透的亚洲综述只写，收紧的押注推高了美债收益率和美元，没有新的百分比。

比特币和 ETF 流出也不并。Kobeissi 周二：比特币跌破 60,000 美元，24 小时杠杆清算升到 8.5 亿美元：[6 万](https://x.com/KobeissiLetter/status/2125064305372520946)。同一账号写 $IBIT 11 月至今流出 30 亿美元，有望成为纪录上第二大的单月流出，连续四个月流入中断。上周流出 8.29 亿美元。周四流出 5.45 亿美元，写成该基金最大的单日流出：[30 亿](https://x.com/KobeissiLetter/status/2124956652185309373)。另一张帖写周四是 5.41 亿美元，而且将近 40 亿美元是全部美国现货比特币 ETF，不是单只 $IBIT。5.45 亿和 5.41 亿并列。30 亿和将近 40 亿不是同一个口径。Brandt：比特币暂时守住了它必须守住的位置，也许不止是暂时。

## 财报、并购和这一周还没发生的事

CrowdStrike 的季报和并购绑在一起，价格不要合成。LiveSquawk：第三财季收入 15.83419 亿美元，预期 15.29 亿美元。第四财季收入指引 16.381 亿到 16.441 亿美元，预期 16.23 亿美元。全年收入指引 60.781 亿到 60.841 亿美元，预期 60.07 亿美元：[季报](https://x.com/LiveSquawk/status/2124813825798971743)。并购有 439 亿美元和大约 440 亿美元两套。StockMKTNewz：全股票，1.135 股换 1 股，大约 260.41 美元，相对周五收盘溢价 34%，股东占比 84.1% 对 15.9%：[1.135](https://x.com/StockMKTNewz/status/2124819530929029260)。unusual_whales 写成大约 440 亿美元、史上最大的网络安全收购，溢价基准写成 11 月 20 日收盘，占比大约 84% 对 16%：[440 亿](https://x.com/unusual_whales/status/2124829510092898349)。34% 的基准是“周五”还是“11 月 20 日”，两张帖各写各的。线外 WOLF 写盘前 Zscaler +8.1%：[8.1%](https://x.com/WOLF_Financial/status/2124815319109685372)。RedDog 收盘铃把 CrowdStrike 写成标普里最差，-11%，挂在大约 440 亿美元的交易上。-11% 只在这张收盘铃里。盘前 +8.1% 是 Zscaler，不是 CrowdStrike。

慧与的数字超了预期，标题却说不够乐观。LiveSquawk：第四财季净收入 145.5 亿美元，预期 142.5 亿美元。调整后每股收益 1.43 美元，预期 1.28 美元。第一财季净收入指引 140 亿到 146 亿美元，预期 128.4 亿美元。第一财季调整后每股收益 1.30 到 1.40 美元，预期 1.08 美元。2027 财年净收入 594 亿到 631 亿美元，预期 550 亿美元。调整后每股收益 5.05 到 5.35 美元，预期 4.74 美元。自由现金流至少 55 亿美元，此前至少 50 亿美元，预期 53.4 亿美元。另外授权 50 亿美元回购：[慧与](https://x.com/LiveSquawk/status/2124973248827822100)。彭博商业的标题是，当季收入预测达不到最乐观的估计，一些想要更大人工智能增量的投资者失望了：[最乐观](https://x.com/business/status/2124976337962111375)。“高于预期”和“达不到最乐观”是两张帖，不互相删。这个窗口没有慧与的收盘涨跌。

Zoom 只有定性句。彭博商业：当季收入指引的中点略低于分析师预期：[中点](https://x.com/business/status/2125002739767722225)。没有收入数字，也没有涨跌百分比，这里不补。

赛诺菲买 Insmed 是周二早上的句子，也是抓取开始时的美国趋势。彭博商业和《华尔街日报》商业账号都写 410 亿美元：[410 亿](https://x.com/business/status/2125118502574940173)。CNBC：Insmed 股价上涨 14%，写成三年来制药业最大的一笔交易：[14%](https://x.com/CNBC/status/2125168948891050399)。欧洲央行的 Simkus 是另一条：把利率加到开始约束经济的水平是审慎的，因为价格压力已经扩散到石油以外。他另写欧元最近走弱是另一个通胀因素，应该提前行动，宜早不宜迟：[审慎](https://x.com/business/status/2125148704818508041)。FinancialJuice 在英伟达新闻之后写，交易员增加了欧洲央行和英国央行的加息押注。这是押注，不是决定。

指数调整在 12 月 2 日。First Squawk 引标普道琼斯指数：SharkNinja 加入标普 500，替换 AES。Paycom 加入标普中盘 400，替换 SharkNinja。Guardian Pharmacy Services 加入标普小盘 600，替换 Paycom。Transocean 加入中盘 400，替换 Valaris：[12 月 2 日](https://x.com/FirstSquawk/status/2124991601114288232)。

亚洲的新收盘只有少数几张。窗口开头 Investing.com 还有一张 KOSPI 下跌 3.3% 到 4,708.54：[4,708.54](https://x.com/Investingcom/status/2124808736858419411)。上一份已经有周一 -3.31% 的收盘标题，4,708.54 是这张帖的点位，不是周二的新收盘。周二的韩国句子是 First Squawk：KOSPI 200 期货上涨 5%，交易所启动 sidecar，程序化交易暂停五分钟：[sidecar](https://x.com/FirstSquawk/status/2125018539761484218)。没有周二现货收盘百分比。台湾有两句。Ryan 周一盘中：正在大涨 20%：[20%](https://x.com/RyanDetrick/status/2124915488144703830)。First Squawk 周二：台湾股市收盘大涨 9%：[9%](https://x.com/FirstSquawk/status/2125100835495661939)。20% 不是 9%。日经期货早盘上涨 2%，只是期货。日本初值 PMI：综合 51.5，前值 52.1。制造业 53.7，前值 53.3。服务业 50.5，前值 51.7：[日本](https://x.com/LiveSquawk/status/2125024460218449941)。

这一周还没落地的日历，沿用这个窗口里重新出现的句子。StockMKTNewz：周四美股休市，周五半天。戴尔在感恩节当周的财报名单上，结果还没出。PCE 仍被外汇帖写成尚未公布。威廉姆斯的演讲已经发生，不需要再和上一份“周一下午 4 点”对“这一周没有讲话”互相删除。

## 要盯住的五件事

1. **周二现货还没开，周一收盘有三套点位。** First Squawk 非官方是道指 49,662.07（+3.15%）、标普 7,243.61（+4.82%）、纳斯达克综合指数 24,101.62（+6.56%）。综述是英伟达 +31%、纳斯达克 100 +6.9%、标普 +4.7%。RedDog 是 7,237.17、24,089.56、49,595.31。开盘的 7,251.32 高于非官方收盘 7,243.61，两张都留着。
2. **盘前期货已经在回吐，英伟达没有守住盘前的 +30%。** 09:10 UTC 的修正帖是标普期货 -0.4%、纳斯达克 100 期货 -0.9%、道指期货 -0.1%。英伟达盘前先 -4%，后 -3.5%。CNBC 的标题是超过 -3%。RedDog 大约美东 4:30 的快照是标普 -0.4%、道指 -0.2%、纳斯达克 100 超过 -1%，QQQ 644.22 美元，相对周一收盘 651.03 美元是 -1.05%。
3. **黄仁勋回来了，调查句子没有撤。** 一致投票、没有国家安全风险、Colette Kress 留任财务官、Harvey Jones 留任董事长，和“调查继续”“高管最后一刻才知道”“证券交易委员会仍在查”并列。17% 是复职标题之前的概率。
4. **Anthropic 没有美元收盘，两倍 ETF 的方向帖互相打架。** 盘前从 -1.5% 到 +4.5% 再到 -3%。$ANTT / $ANTZ、$ANUU / $ANDD 已写开张，$AIL / $ANS 仍是即将。83 美元是 11 月 20 日的减持价。
5. **宏观没有被反弹改写。** PMI 综合 54.6、制造业 54.5、服务业 54.7。威廉姆斯的 3.5%、2028 年回到 2%、必要时连续加息，没有写成 12 月已经决定 25 还是 50。加息概率有大于 100%、接近 100%、90% 上方。WTI 结算 80.17，布伦特 89.37。黄金 3,673.36、3,656.82 和周二的 3,666.01 并列。

## 尤其值得看的名字

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。周二现货未开。期货和盘前不是收盘。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 复职前的盘前，线外 | 标普、纳指、英伟达 | +2.7%、+3.5%，英伟达 +8.5% 到 136 美元。布伦特 92，10 年期 4.96% | [136](https://x.com/garyblack00/status/2124812678522675561) |
| 期货停牌 | 纳斯达克 100 | 上涨 7% 后短暂停牌。停的是期货 | [7%](https://x.com/DeItaone/status/2124871293023535410) |
| 开盘 | 道指、标普 | 49,487.64（+2.78%），7,251.32（+4.93%）。另一张是标普 +5.1%、纳斯达克 100 +7.4% | [开盘](https://x.com/FirstSquawk/status/2124873708691239325) |
| 非官方收盘 | 道指、标普、纳指 | 49,662.07（+3.15%），7,243.61（+4.82%），24,101.62（+6.56%） | [标普](https://x.com/FirstSquawk/status/2124972142613950551) |
| 综述，不是点位 | 英伟达、纳指 100、标普 | +31%、+6.9%、+4.7% | [综述](https://x.com/FirstSquawk/status/2124976863508660657) |
| 收盘句 | 标普、英伟达 | 标普 +4.7%，市值增加超过 3 万亿。英伟达 +31.6%，增加 9,550 亿 | [9,550 亿](https://x.com/KobeissiLetter/status/2124974519567737034) |
| 另一套收盘，线外 | 三大指数 | 7,237.17（+4.73%），24,089.56（+6.51%），49,595.31（+3.01%） | [收盘铃](https://x.com/RedDogT3/status/2124990286254276794) |
| 次日历史，不是承诺 | 标普 | +4.7% 排过去 20 年最好的 25 天里第 21。次日和下一周上涨的次数都是 29%。一年后平均 +29.8% | [29%](https://x.com/RyanDetrick/status/2125010173911498925) |
| 盘前路径 | NVDA | +25%，+27%，超过 30%，清单上的 +31.19%。盘中超过 +35%。收盘帖 +31.6% | [+31.19%](https://x.com/DeItaone/status/2124867095389159800) |
| 周二盘前 | 期货、NVDA | 标普期货 -0.4%，纳指期货 -0.9%，道指期货 -0.1%。英伟达 -4%，随后 -3.5% | [修正](https://x.com/FirstSquawk/status/2125155144836972827)、[-3.5%](https://x.com/FirstSquawk/status/2125158243802743242) |
| 仍是多头，线外 | NVDA | 承认看错复职。仍是最重的多头。8.3 倍 2027 年 EV/EBITDA，回答是“现在” | [现在](https://x.com/garyblack00/status/2124977241499054580) |
| 平了空头 | 标普 | 大约 7 倍初始风险之后平空。11.6% 的修正还没走出树林。反弹多是逆向 | [平空](https://x.com/markminervini/status/2124875682576531796) |
| 趋势仍向下 | 股指期货 | NQ、ES、M2K、YM 上涨之后，趋势仍向下。V 型底要价格自己证明 | [趋势](https://x.com/PeterLBrandt/status/2125035697396736135) |
| 调查不撤 | NVDA | 司法部和证监会继续查。凯文：人回来了，调查也在 | [继续查](https://x.com/michaeljburry/status/2124876426486681864) |
| 负 gamma，线外 | NVDA、标普 | 负 gamma 堆到 200 美元。HIRO 显示周一不要做空。盘中帖是英伟达 +36%、Anthropic -0.8% | [200](https://x.com/spotgamma/status/2124889075933200863) |
| 杠杆清掉 | 三倍做空 | 下跌 91.4% 后停牌。欧洲一只 -3 倍产品几秒 -91%。$NVD 当天 -62% | [91.4%](https://x.com/Hedgeye/status/2124894484056228115) |
| 没有收盘价 | ANT | 盘前 -1.5%、+4.5%、-3%。彭博标题是周一下跌。83 美元是 11 月 20 日减持 | [-3%](https://x.com/DeItaone/status/2124874313295593808) |
| 代码不要并 | ANTT、ANUU、AIL | $ANTT / $ANTZ 已交易。$ANUU / $ANDD 周一。$AIL / $ANS 即将。14 只杠杆产品同一天 | [ANTT](https://x.com/unusual_whales/status/2124870177619865838) |
| 垃圾级，不是股价 | ANT 债券 | 《华尔街日报》经 unusual_whales：债市预期评级是垃圾级 | [垃圾级](https://x.com/unusual_whales/status/2124824531395067947) |
| 实际数 | 美国 PMI | 综合 54.6，制造业 54.5，服务业 54.7。服务业预期有 55.5 和 55.7 | [54.6](https://x.com/financialjuice/status/2124876980671725888) |
| 没有写下路径 | 威廉姆斯 | 2026 年底通胀 3.5%，2028 年回 2%。必要时连续加息。没有写进铅笔稿 | [连续](https://x.com/FirstSquawk/status/2125006629355827561) |
| 25，不是 50 | 12 月 9 日 | 概率仍在 90% 上方。50 个基点被写成不明智 | [不要 50](https://x.com/elerianm/status/2124942766862131397) |
| 接近 100% | 加息概率 | FedWatch 接近 100%，周五 88%。早上另有大于 100% | [接近 100%](https://x.com/LizAnnSonders/status/2124872576056832045) |
| 结算 | WTI、布伦特 | 80.17 美元，-3.24 美元，-3.88%。布伦特 89.37，-3.20 美元，-3.46% | [80.17](https://x.com/financialjuice/status/2124948970367496643) |
| 现货路径 | 黄金 | 3,673.36，综述 3,656.82，最多大约 3,690。周二 3,666.01 | [3,656.82](https://x.com/FirstSquawk/status/2124976410062467472) |
| 跌破 | 比特币 | 跌破 60,000。24 小时清算 8.5 亿美元。$IBIT 11 月流出 30 亿 | [6 万](https://x.com/KobeissiLetter/status/2125064305372520946) |
| 全股票 | CRWD、ZS | 439 亿或大约 440 亿。1.135 股，260.41 美元，溢价 34%。收盘铃里 CRWD -11% | [1.135](https://x.com/StockMKTNewz/status/2124819530929029260) |
| 高于预期，标题仍失望 | HPE | 收入 145.5 亿对 142.5 亿，调整后每股 1.43 对 1.28。彭博写达不到最乐观估计 | [慧与](https://x.com/LiveSquawk/status/2124973248827822100) |
| 只有定性 | ZM | 当季收入指引中点略低于预期。没有数字 | [中点](https://x.com/business/status/2125002739767722225) |
| 周二，410 亿 | SNY、INSM | 赛诺菲收购 Insmed。CNBC 写 Insmed +14% | [14%](https://x.com/CNBC/status/2125168948891050399) |
| 12 月 2 日 | SN | SharkNinja 加入标普 500，替换 AES | [指数](https://x.com/FirstSquawk/status/2124991601114288232) |
| 12 个月，不是周一 | 标普 | 加皇 8,050，自周五收盘 +16.5%。2027 年末市盈率压到 18.8 倍 | [8,050](https://x.com/DeItaone/status/2124830744069484727) |
| 2027，不是目标现价 | 标普 | 德意志银行看到 9,000。斯托克 600 到 2027 年四季度 750。主号时间线没读到 | [9,000](https://x.com/DeItaone/status/2124850351098478755) |
| 买修正，不是抄底令 | 标普 | 亚德尼：前瞻市盈率 16.4 倍，2022 年以来最低。2028 年每股收益共识 498.44 美元。咆哮的 2020 年代概率 70% | [16.4](https://x.com/DeItaone/status/2124845772688462311) |
| 反弹未必持续 | 标普 | 摩根大通交易台从战术看多改成谨慎。想看到更低的波动和更强的周期股 | [谨慎](https://x.com/DeItaone/status/2124834788783661146) |
| 2018 的剧本 | 标普 | 城堡证券：更强的美元、更弱的周期股、更高的收益率。周一的反弹未必反映完风险 | [2018](https://x.com/DeItaone/status/2124943492732330294) |
| 卖出挤压，只是标题 | 高盛交易台 | 零对冲：Privorotsky 在问要不要卖出这次挤压。另一条是 Pasquariello 在画战术底部的路标 | [挤压](https://x.com/zerohedge/status/2124873216237682747) |
| 信用，11 月 19 日 | 高收益 | OAS 352 个基点，12 个月最宽，仍低于十年均值 382。高收益比投资级 3.74 | [352](https://x.com/leadlagreport/status/2124876920076529800) |
| 周二收盘，不是周一 | 台湾、韩国期货 | 台湾 +9%。周一盘中另有 +20%。KOSPI 200 期货 +5% 触发 sidecar | [9%](https://x.com/FirstSquawk/status/2125100835495661939) |

## 后续走势：三套可以证伪的剧本

抓取结束时是美东周二清晨。现货未开。已经写下来的锚是：周一非官方收盘标普 7,243.61（+4.82%），另有 +4.7% 和 7,237.17；英伟达收盘帖 +31.6% 和 9,550 亿美元，盘前已经到 -4% 和 -3.5%；期货修正帖是 -0.4% / -0.9% / -0.1%；威廉姆斯没有写下 12 月的基点；WTI 结算 80.17，布伦特 89.37。

**周一的涨幅在周二开盘还留不留得住。** 触发器是非官方收盘 7,243.61、24,101.62、49,662.07 还被当成周一的收盘，同时 09:10 UTC 的期货 -0.4% / -0.9% / -0.1% 没有再被写成涨。它失败的条件，是现货被写成重新跌回 7,243.61 和 7,237.17 两套周一收盘的下沿之外，七连跌被 RedDog 写成结束后又被写回去，同时 Minervini 的“还没走出树林”和 Brandt 的“趋势仍向下”还对得上。Ryan 的次日只有 29% 的历史次数上涨，不是这次的承诺。开盘的 7,251.32 高于收盘 7,243.61，不能用来证明收盘更高。

**黄仁勋的复职是反转，还是调查还在的一天大涨。** 触发器是盘前 -3.5% 到 -4% 守住，收盘帖的 +31.6% 和 9,550 亿不被改写成 +35% 或 1 万亿，董事会的“没有国家安全风险”还在。它失败的条件，是 Burry 的反垄断和会计调查、FinancialJuice 的“调查继续”、或者凯文的“证券交易委员会仍在查”被写成已经结案，同时 Colette Kress 不再被写成留任财务官。Gary 的“现在”和 8.3 倍是他的仓位理由。Hedgeye 的打扫日子和摩根大通“反弹未必持续”是对立的句子，不收成一个共识。

**油价、黄金和 12 月的基点仍然各走各的。** 触发器是 WTI 还停在 80.17、布伦特还停在 89.37，黄金的下一张现货仍能对上 3,666.01、3,656.82 或 3,673.36 中的一张，威廉姆斯的“随着时间”和“没有写进铅笔稿”还在。它失败的条件，是有人把 80.17 和 89.37 收成一个油价，把加息概率收成既不是接近 100%、也不是 90% 上方、也不是大于 100% 的一个数，或者把 50 个基点写成 El-Erian 已经接受。赛诺菲的 410 亿美元和 Insmed 的 +14% 不是指数。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周二开盘。它不决定仓位大小。抓取结束时，现货还没开。周一的三套收盘都在。这个窗口新增加的是复职、期货停牌、PMI、威廉姆斯和原油结算。

**开盘前只核对五样东西。** 指数是停在 First Squawk 的 7,243.61 / 24,101.62 / 49,662.07，停在 RedDog 的 7,237.17 / 24,089.56 / 49,595.31，还是只剩下综述里的 +4.7% 和 +6.9%。英伟达是停在盘前 -3.5%，回到 -4%，还是重新被写成周一的 +31.6%。Anthropic 有没有新的美元价；如果没有，就只核对 $ANTT 和 $ANTZ 谁被写成做多、谁被写成做空。原油是停在 80.17 和 89.37，还是出现一张新价。利率是停在“接近 100% 的 25 个基点、50 个基点被写成不明智”，还是威廉姆斯的连续会议被写成已经排期。五样里，+31.6% 不代表周二还在涨，7% 的停牌不代表现货熔断，9,000 点不代表德意志银行的帖出现在它自己的时间线上。

**已经公开的方向，按账号而不是按共识。**

- First Squawk，线外：非官方收盘 49,662.07、7,243.61、24,101.62。综述另写 +31%、+6.9%、+4.7%。周二期货修正为 -0.4%、-0.9%、-0.1%。英伟达盘前 -4%，然后 -3.5%。布伦特结算 89.37。黄金 3,673.36，综述 3,656.82，周二 3,666.01。台湾收盘 +9%。
- Kobeissi：期货在 +7% 停牌。盘中标普 +5.3%、市值 +3.5 万亿。收盘标普 +4.7%、超过 3 万亿。英伟达收盘 +31.6%、9,550 亿。盘中曾经超过 +35%，并写成如果收在那里就是 1 万亿。比特币跌破 60,000。$IBIT 11 月流出 30 亿。
- DeItaone：董事会一致复职，Kress 留任财务官，同时引彭博写高管没被咨询。加皇 12 个月 8,050。亚德尼前瞻市盈率 16.4 倍。德意志银行 2027 年标普 9,000。摩根大通交易台改成谨慎。城堡证券用 2018 年作对照。
- Gary Black，线外：复职前 +8.5% 到 136 美元。承认看错人事，仓位仍是最重的多头之一，8.3 倍 2027 年 EV/EBITDA，答案是“现在”。如果高管没被咨询，高层还会再波动。
- RedDog，线外：收盘铃 7,237.17、24,089.56、49,595.31，七连跌被他写成结束。周五买了 QQQ 11 月 27 日到期、行权价 635 美元的看涨期权，振荡指标当时 -65。周二大约 4:30 的期货是标普 -0.4%、道指 -0.2%、纳斯达克 100 超过 -1%。QQQ 盘前 644.22 美元。CrowdStrike -11% 只在他的收盘铃里。
- El-Erian：12 月 9 日很难不加。25 个基点的概率在 90% 上方，50 个基点不明智。Anthropic 像 SpaceX 上市路径的快进。
- Liz Ann：PMI 54.5 / 54.7 / 54.6。加息概率接近 100%，周五 88%。
- Nick Timiraos，线外：还会收紧，但不要过度跟着最近的通胀走。政策要一到两年才完全起作用。标普和纳斯达克 +4.7% 和 +6.5%，对的是 2025 年 4 月 9 日。今年至今是另一句：道指和纳斯达克超过 +3%，标普将近 +6%。
- Minervini：空头已平，大约 7 倍初始风险。还没走出树林。人回来了。
- Brandt：趋势仍向下。
- Burry：继续查反垄断和会计。Kevin O'Leary：调查会在他重新掌舵时进行。Cramer：预计人事反转还有余波。
- Hedgeye，线外：反弹是打扫，不是全面解除。纳斯达克 100 今年至今 +5.5%。三倍做空下跌 91.4% 后停牌。
- SpotGamma，线外：标普 gamma 仍为负。200 美元是英伟达的负 gamma。HIRO 说周一不要做空。
- Ryan，线外：次日和下一周的历史胜率都是 29%。50 日均线从 -4.1 个标准差收到 -2.3。英伟达 9,540 亿和“将近 1 万亿”是两张帖。
- Bespoke，线外：+4.73% 是 25 年里第二十四好。英伟达约占 326 点里的 110 点。距高点仍 30%，六个月仍 -23%。标普和纳斯达克 100 仍在 200 日均线下方 2% 和 5%。
- 零对冲：期货停牌之后，Privorotsky 在问要不要卖出挤压。Pasquariello 在画战术底部的路标。两则都是标题，正文没有把路标展开。
- 高盛主号这个窗口没有新的标普点位。德意志银行的时间线没有读到，9,000 只出现在通讯社。Cathie Wood、fundstrat、美联储账号没有新的指数或利率决定。

**数据和交易日的顺序。** 先看周二开盘时 7,243.61 和 7,237.17 哪一套还在标题上，再看英伟达是 -3.5%、-4% 还是被写回 +31%。然后才是 $ANTT 和 $ANTZ 的方向有没有被写清楚。戴尔若出财报，对的是感恩节当周的日历，不是慧与已经公布的 1.43 美元。PCE 和 GDP 仍在后面。周四休市，周五半天。原油若没有新结算，就不要用黄金的 3,666.01 去改 80.17。

**明确留在观察、不放进计划的东西。** 不把 7,243.61、7,237.17、+4.82%、+4.7% 和 +4.73% 收成一个标普收盘。不把 24,101.62、24,089.56、+6.56%、+6.51%、+6.9% 和 +6.5% 收成一个纳指。不把 49,662.07、49,595.31、+3.15% 和 +3.01% 收成一个道指。不把开盘的 7,251.32 写成高于收盘所以收盘应该更高。不把点数减回去改上一份的周五 6,902.03 或 22,620.17。不把期货的 +7% 停牌写成现货熔断。不把复职前的 +2.7%、+3.5%、+8.5% 和 136 美元并进收盘。不把 +25%、+27%、超过 30%、+31.19%、+32%、+35%、+31.6%、+31.5% 和综述的 31% 收成一个英伟达涨幅。不把 9,550 亿、9,540 亿、9,520 亿、将近 1 万亿、1 万亿的“如果”，和 Business Insider 的 9,000 亿收成一个市值。不把 166、167 和 136 收成一个股价。不把 91.4%、欧洲的 91% 和 $NVD 的 62% 收成一只产品。不把 17% 写成复职之后的概率。不把“没有国家安全风险”写成调查已经结束。不把 Anthropic 的 -1.5%、+5.6%、+4.5%、-3%、-0.8% 和“周一下跌”收成一个跌幅。不把 $ANTZ 同时写成唯一的做多和唯一的做空。不把 83 美元写成周一收盘。不把 PMI 预期 55.5 和 55.7 收成一个预期。不把接近 100%、90% 上方和大于 100% 收成一个加息概率。不把 25 个基点和“连续会议、没有铅笔稿”收成已经公布的决定。不把 80.17 和 89.37 收成一个油价。不把 3,673.36、3,690、3,656.82 和 3,666.01 收成一个金价。不把 4.96% 和“靠近 5.0%”收成一个收益率。不把台湾的 +20% 和 +9% 收成一个收盘。不把慧与“高于一致预期”和“达不到最乐观估计”互相删掉。不把 CrowdStrike 的 -11% 写成 Zscaler 的盘前 +8.1%。不把搜索当成全站讨论，这次搜索接口是 503。

## 搜索这次没有结果，趋势里有黄仁勋

`/2/search` 这次返回 503。不能用它核对全站在讨论什么，也不能用它里面的价格替换时间线。讨论范围就是上面这些账号在窗口里写下的帖。

抓取开始时的趋势是 #iskadiyebiri、Jensen Huang、Commanders、Thanksgiving、Sanofi、Jags。Jensen Huang 的上下文是商业和金融。Sanofi 的上下文是美国趋势，对得上 410 亿美元收购 Insmed 的帖，不是一只美股代码。结束时 Thanksgiving 和 Sanofi 不在了，换成 Monday Night Football 和 Tom Jackson。Jensen Huang 还在。没有美股代码。

## 帖文索引

复职和收盘：[一致投票](https://x.com/DeItaone/status/2124864807429968103)、[期货停牌](https://x.com/KobeissiLetter/status/2124871861804654908)、[非官方标普](https://x.com/FirstSquawk/status/2124972142613950551)、[英伟达 +31.6%](https://x.com/KobeissiLetter/status/2124974519567737034)。

周二盘前和宏观：[期货转跌](https://x.com/FirstSquawk/status/2125155144836972827)、[英伟达 -3.5%](https://x.com/FirstSquawk/status/2125158243802743242)、[PMI](https://x.com/financialjuice/status/2124876980671725888)、[连续加息](https://x.com/FirstSquawk/status/2125006629355827561)、[WTI 80.17](https://x.com/financialjuice/status/2124948970367496643)。

交易计划里的两套方向：[平空，但还没出树林](https://x.com/markminervini/status/2124875682576531796)、[趋势仍向下](https://x.com/PeterLBrandt/status/2125035697396736135)、[现在仍然做多](https://x.com/garyblack00/status/2124977241499054580)、[次日历史胜率 29%](https://x.com/RyanDetrick/status/2125010173911498925)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-24 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 264 条、彭博商业账号 304 条、零对冲 142 条、DeItaone 106 条、FinancialJuice 201 条，是读穿窗口后的原创计数。德意志银行的 0 是读取失败。fundstrat 的 0，是可见帖被标成转发或回复。Cathie Wood、美联储、彭博主号、markets、摩根大通、花旗、美国银行的 0，是可见时间线早于窗口，或空页。Warren Buffett 和 Downtown 是空页。线外的 First Squawk 是 247 条。

| 1 | [@Reuters](https://x.com/Reuters) | 26,446,871 | 264 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,346,297 | 89 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,280,835 | 91 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,293,364 | 44 |
| 5 | [@business](https://x.com/business) | 10,499,697 | 304 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,580,647 | 0 |
| 7 | [@FT](https://x.com/FT) | 7,130,845 | 61 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,263,974 | 90 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,369,014 | 58 |
| 10 | [@IMFNews](https://x.com/IMFNews) | 4,652,901 | 0 |
| 11 | [@MarketWatch](https://x.com/MarketWatch) | 4,651,215 | 46 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,441,795 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,353,379 | 47 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,438,921 | 142 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,433,758 | 40 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,082,073 | 3 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,021,566 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,797,760 | 31 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,589,131 | 2 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,550,829 | 6 |
| 21 | [@chamath](https://x.com/chamath) | 2,506,110 | 3 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,438,917 | 18 |
| 23 | [@BW](https://x.com/BW) | 2,288,358 | 4 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,242,935 | 42 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,154,757 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,137,675 | 3 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,086,572 | 29 |
| 28 | [@markets](https://x.com/markets) | 2,047,488 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,980,906 | 106 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,802,000 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,791,921 | 5 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,772,684 | 20 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,714,219 | 8 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,700,951 | 6 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,690,705 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,631,951 | 17 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,608,167 | 0 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,545,120 | 47 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,516,184 | 3 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,474,781 | 13 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,392,993 | 4 |
| 42 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,369,343 | 5 |
| 43 | [@Bloomberg](https://x.com/Bloomberg) | 1,365,397 | 0 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,268,573 | 4 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,227,747 | 70 |
| 46 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,210,269 | 0 |
| 47 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,196,037 | 9 |
| 48 | [@Stocktwits](https://x.com/Stocktwits) | 1,195,875 | 4 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,184,090 | 5 |
| 50 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,174,316 | 47 |
| 51 | [@nntaleb](https://x.com/nntaleb) | 1,170,631 | 4 |
| 52 | [@USTreasury](https://x.com/USTreasury) | 1,168,367 | 2 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,160,836 | 2 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,160,600 | 10 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,140,284 | 4 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,119,576 | 11 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,105,639 | 47 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,098,547 | 6 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,083,128 | 1 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,070,595 | 4 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,042,570 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,881 | 39 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,007,723 | 2 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 959,978 | 201 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 945,462 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 934,326 | 16 |
| 67 | [@tradingview](https://x.com/tradingview) | 914,122 | 1 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 896,893 | 22 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 892,962 | 0 |
| 70 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 883,001 | 16 |
| 71 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,808 | 23 |
| 72 | [@charliebilello](https://x.com/charliebilello) | 876,586 | 2 |
| 73 | [@axios](https://x.com/axios) | 866,410 | 35 |
| 74 | [@jpmorgan](https://x.com/jpmorgan) | 862,817 | 0 |
| 75 | [@steve_hanke](https://x.com/steve_hanke) | 862,799 | 33 |
| 76 | [@Citi](https://x.com/Citi) | 852,649 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 846,590 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 839,788 | 1 |
| 79 | [@ecb](https://x.com/ecb) | 832,134 | 3 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,278 | 1 |
| 81 | [@bgurley](https://x.com/bgurley) | 812,748 | 1 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,059 | 0 |
| 83 | [@economics](https://x.com/economics) | 805,146 | 0 |
| 84 | [@markminervini](https://x.com/markminervini) | 793,852 | 4 |
| 85 | [@biancoresearch](https://x.com/biancoresearch) | 789,729 | 2 |
| 86 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,806 | 1 |
| 87 | [@leadlagreport](https://x.com/leadlagreport) | 768,164 | 26 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 760,984 | 4 |
| 89 | [@morganhousel](https://x.com/morganhousel) | 756,322 | 0 |
| 90 | [@CNBCnow](https://x.com/CNBCnow) | 750,584 | 0 |
| 91 | [@Nouriel](https://x.com/Nouriel) | 723,581 | 0 |
| 92 | [@TrendSpider](https://x.com/TrendSpider) | 719,013 | 30 |
| 93 | [@CMEGroup](https://x.com/CMEGroup) | 710,938 | 2 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 675,518 | 9 |
| 95 | [@fundstrat](https://x.com/fundstrat) | 672,970 | 0 |
| 96 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,115 | 7 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 647,364 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,102 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 636,035 | 3 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 624,876 | 12 |

