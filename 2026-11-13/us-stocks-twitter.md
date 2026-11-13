# 美股 Twitter 观点日报 · 2026-11-13

周五现货还没开。抓取结束时美东大约 5:08。这个窗口的主线是周四现货：黄仁勋辞去英伟达总裁、首席执行官和董事，立即生效；Colette Kress 任临时首席执行官，Harvey C. Jones 成为董事会第一任主席。指数开盘跌得更深，盘中一度转绿，收盘仍是小跌。英伟达的收盘百分比有 4.3%、4% 和将近 7% 三句，不能并成一个收盘。油价结算是上涨。这是公开帖文的整理，不是投资建议。

下面每一条归纳都附有帖文链接。

## 抓取口径

- 报告日期按北京时间 **2026-11-13**。触发时刻约 10:00 UTC，时间线补抓到 **约 10:08 UTC（北京时间 18:08，美东 5:08）**。美国夏令时已经结束。美股现货 9:30 才开。周三收盘 7,619.22、25,465.38、52,465.11，以及英伟达周三盘后那一串百分比，不在这份报告里重算。
- 观察窗口从 **2026-11-12 10:03 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周四大约 5:03 以后的盘前、周四现货全天、收盘、盘后，以及美东周五凌晨到大约 5:08。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。全站搜索返回了结果，用来核对“当前讨论”的范围。正文里的价格和立场仍以账号时间线为准。抓取开始时，未加地区的趋势是 Outlook、Electoral College、Microsoft、NAMTANFILM GLAM NIGHT、Happy Friday the 13th、Blue Beetle；美国地区把 Blue Beetle 换成 Blough，并多了 `#SLOMWOC`。结束时两边都是 Outlook、Electoral College、Microsoft，另有 Gmail、wooyoung、Happy Friday the 13th。没有美股代码。Outlook、Microsoft、Gmail 对得上微软服务中断，时间线里没有微软股价的百分比。
- 不存在官方的“美股 Top 100”。这次沿用上一份已经排过的金融候选，并补了紧贴截止线的账号，成功读到粉丝数之后重新排序。用来排序的账号截止在 Eric Balchunas（625,861）。前 100 的账号集合和 11 月 12 日那份相同。名次只对调了一处：塔勒布（1,167,739）到美国财政部（1,166,527）前面。Morning Brew（594,160）第 101。Bloomberg Opinion 的 `@opinion`（586,247）第 102。Gary Black（585,635）第 103。Barchart（579,838）第 104。Cboe（579,360）第 105。First Squawk（578,939）第 106。排序不代表预测准确度。
- 100 个账号里，**72 个**在窗口内有按帖文链接去重后、且接口没有标成回复或转发的原创帖。路透读穿窗口，278 条。彭博商业账号 329 条。FinancialJuice 389 条。零对冲 139 条。《经济学人》124 条。DeItaone 77 条，可见最新帖停在周四 23:33 UTC。《金融时报》71 条。CNBC 75 条。《华尔街日报》41 条。线外的 First Squawk 原创 361 条，读穿到窗口起点。LiveSquawk 83 条。德意志银行的时间线是 404，表里的 0 不是确认沉默。沃伦·巴菲特和 Downtown 的时间线停在更早的年份。达利欧有 1 条原则帖，下一页是 404。彭博主号、markets、BBC Business、CNN Business、Cathie Wood、保罗·克鲁格曼、Bill Ackman、安德鲁·罗斯·索尔金、Lyn Alden、纽约时报商业、花旗、Hindenburg、摩根士丹利、CNBC Now、economics、Nouriel、Carl Icahn、美国银行、TradingView、美国财政部、Charlie Bilello、SEC、Bill Gurley、摩根·豪泽尔，窗口内没有计为原创的新帖。美联储账号有 7 条，其中一条是 2027 年 FOMC 日程修订的公告链接，没有在帖文里写出新的日期。

## 辞职已经公告，开盘的 -13% 和收盘的 4.3% 不是同一张

公司公告按通讯社的句子留着。First Squawk 13:51 UTC：英伟达宣布首席执行官交接。同一分钟：黄仁勋辞去首席执行官。13:52 UTC：任命 Kress 为临时首席执行官，并保留首席财务官职务；公司将考虑内部和外部候选人：[交接](https://x.com/FirstSquawk/status/2120877163381772557)、[辞职](https://x.com/FirstSquawk/status/2120877233443340526)、[Kress](https://x.com/FirstSquawk/status/2120877271980589430)、[内外部](https://x.com/FirstSquawk/status/2120877370869723462)。零对冲写成“Jensen 出局”，并补了 Harvey Jones 成为董事会第一任主席：[出局](https://x.com/zerohedge/status/2120876454367953005)、[主席](https://x.com/zerohedge/status/2120876646748090804)。FinancialJuice：Kress 任临时首席执行官，董事会启动永久首席执行官的搜寻，三季度财年 2027 的业绩仍定在 11 月 17 日：[Kress](https://x.com/financialjuice/status/2120876539067969948)、[搜寻](https://x.com/financialjuice/status/2120876701907616169)、[11 月 17 日](https://x.com/financialjuice/status/2120876971324580002)。Kobeissi 把辞职写成总裁、首席执行官和董事立即生效，33 年职业生涯结束：[辞职](https://x.com/KobeissiLetter/status/2120877226459820170)、[Kress](https://x.com/KobeissiLetter/status/2120878535497916576)。这和上一份里“准备撤掉、还没有公告”已经不是同一句。

“今后在公司没有任何角色”是稍后的另一句。First Squawk 15:27 UTC 和零对冲 15:21 UTC 都这么写：[First Squawk](https://x.com/FirstSquawk/status/2120901331598860626)、[零对冲](https://x.com/zerohedge/status/2120899907834065154)。全员会的钟点有两种写法。FinancialJuice 引备忘录：11 月 18 日太平洋时间上午 9 点：[帖](https://x.com/financialjuice/status/2120885961005384086)。DeItaone 写成 11 月 18 日美东中午 12 点，财报次日早上：[帖](https://x.com/DeItaone/status/2120954810832687132)。两张帖写的是同一个钟点的两个时区，不是两场会。

盘前的百分比早于开盘，而且彼此不同。Kobeissi 10:41 UTC：从低点反弹 6%，仍比前一天收盘低 5%。那是辞职公告之前：[帖](https://x.com/KobeissiLetter/status/2120829226718724535)。零对冲 13:03 UTC 的盘前 movers：英伟达 -7%。同一帖里 AMD +1%，博通将近 +1%：[帖](https://x.com/zerohedge/status/2120865088101896514)。DeItaone 12:37 UTC：盘前跌幅扩到 8%：[帖](https://x.com/DeItaone/status/2120858604890657161)。他更早一帖写 Saxo 客户周一到周三将近 90% 的英伟达成交是买入，而这只股票盘前又跌了 8.4%：[帖](https://x.com/DeItaone/status/2120855841100189933)。辞职之后，First Squawk 先写跌幅扩到 10%，再写盘前低点 -11%，14:22 UTC 写成盘前 -13%：[10%](https://x.com/FirstSquawk/status/2120877398778605579)、[-11%](https://x.com/FirstSquawk/status/2120878155640742350)、[-13%](https://x.com/FirstSquawk/status/2120885026162377149)。StockMKTNewz 写成盘前几乎 -12%：[帖](https://x.com/StockMKTNewz/status/2120883300201844753)。-5%、-7%、-8%、-8.4%、-10%、-11%、-12%、-13% 都是盘前的不同时刻。

开盘和盘中又是另一串。金融时报：开盘暴跌 13%，市值抹掉超过 5000 亿美元：[帖](https://x.com/FT/status/2120890502404874652)。FinancialJuice：暴跌 14%，市值跌破 4 万亿美元，这一下要抹掉 5930 亿美元：[帖](https://x.com/financialjuice/status/2120887371202015394)。DeItaone：市值自 2025 年 7 月以来第一次跌破 4 万亿美元，下跌 13%，并写成有望成为 2025 年 1 月以来最大的单日跌幅：[帖](https://x.com/DeItaone/status/2120886996990034312)。“有望成为”是 14:30 UTC，不是收盘。Kobeissi：暴跌超过 10%，自风波开始抹掉 7500 亿美元市值：[帖](https://x.com/KobeissiLetter/status/2120877770247221444)。7500 亿是自风波开始，不是开盘这一下的 5930 亿。

买盘把跌幅收回来的句子，也还不是收盘。Kobeissi 15:21 UTC：重新站上 163 美元，抹掉当天跌幅的一半：[帖](https://x.com/KobeissiLetter/status/2120899669341446242)。15:56 UTC：标普抹掉全部跌幅并转绿，英伟达抹掉超过一半的当天跌幅：[帖](https://x.com/KobeissiLetter/status/2120908498804293843)。线外的 SpotGamma：从 148.80 美元的低点反弹大约 9%，低点靠近他周三写的 150 美元看跌墙；30 天 25-delta 看跌隐含波动率在美东 9:40 到 9:50 是 68.1%，比周三收盘的 57.9% 高 10.2 个波动点：[9%](https://x.com/SpotGamma/status/2120905831096926450)、[150](https://x.com/SpotGamma/status/2120867060318449986)。unusual_whales：隔夜在 Liquid 上跌到 151 美元，随后反弹 9.3% 到 165 美元，市值仍在 4 万亿美元下方：[帖](https://x.com/unusual_whales/status/2120927033383608655)。另一帖是当天 -5.4%、现价 164 美元，较 10 月高点约 240 美元下跌 32%；风险逆转偏度仍是 +0.05：[帖](https://x.com/unusual_whales/status/2120931881654837704)。再一帖：187 美元是最大的正 gamma 墙，170 到 176 美元是重的负 gamma：[帖](https://x.com/unusual_whales/status/2120934901578879352)。线外的 RedDog：有人在周线上看的 148 到 152 美元买到了：[帖](https://x.com/RedDogT3/status/2120919871034982755)。线外的 firstadopter：从日内低点上涨 12%：[帖](https://x.com/firstadopter/status/2120912924965572770)。148.80、151、163、164、165、170 到 176、187 是不同账号的价位。9%、9.3%、12%、一半，是四句反弹。

收盘百分比有三套，不要取中间值。金融时报：周四收盘下跌 4.3%：[帖](https://x.com/FT/status/2120989286644224158)。First Squawk 的收盘综述也是 4.3%，并写大多数标普公司下跌：[帖](https://x.com/FirstSquawk/status/2120991070276530643)。MarketWatch：削掉早段跌幅后，收盘下跌 4%：[帖](https://x.com/MarketWatch/status/2120991036507922462)。Investing.com 的标题是下跌 4%：[帖](https://x.com/Investingcom/status/2120989385252315595)。The Information：辞职之后下跌将近 7%，这是过去两周超过 25% 跌幅的一部分：[帖](https://x.com/theinformation/status/2121022759371157543)。4.3%、4%、将近 7% 是三句收盘或收盘后的写法。25% 是两周。Hanke 15:11 UTC 写的暴跌 8%，早于这些收盘帖：[帖](https://x.com/steve_hanke/status/2120897372309844041)。线外的 Detrick 19:22 UTC：英伟达当周到那时下跌 12%，半导体 ETF 上涨 8%，英伟达占这只 ETF 的 20%：[帖](https://x.com/RyanDetrick/status/2120960467753394353)。12% 是周，8% 是 ETF，都不是周四收盘。线外的 Earnings Whispers 在 18:46 UTC 问了一句“标普 ETF 收红、英伟达收绿？”这是问题，不是收盘：[帖](https://x.com/eWhispers/status/2120951438625116643)。

## 指数开盘低于收盘，盘中的转绿没有留到收盘

开盘点位是 First Squawk 14:31 UTC：纳斯达克下跌 378.46 点，或 1.49%，到 25,087.73；道指上涨 69.03 点，或 0.13%，到 52,555.52；标普 500 下跌 59.51 点，或 0.78%，到 7,559.87：[帖](https://x.com/FirstSquawk/status/2120887132659323356)。

开盘前的期货更低，而且不是这张开盘。线外的 Gary 11:20 UTC：标普 -0.3%，纳斯达克 100 -0.7%：[帖](https://x.com/garyblack00/status/2120839259468796146)。DeItaone 12:49 UTC：纳斯达克 100 期货跌幅扩到 1%：[帖](https://x.com/DeItaone/status/2120861580162167087)。First Squawk 13:17 UTC：纳斯达克 100 期货跌幅扩到 1.4%。13:18 UTC：标普 500 指数期货跌幅扩到 0.7%：[1.4%](https://x.com/FirstSquawk/status/2120868664799047904)、[0.7%](https://x.com/FirstSquawk/status/2120868799042007261)。线外的 The Stalwart：纳斯达克 100 期货 -1.2%：[帖](https://x.com/TheStalwart/status/2120877976615018640)。Kobeissi 在新云那条里写成纳斯达克 100 期货当天 -1.5%：[帖](https://x.com/KobeissiLetter/status/2120886129813553412)。-0.3%、-0.7%、-1%、-1.2%、-1.4%、-1.5%、-0.7% 都早于 14:31 的开盘点位。

盘中转绿有三句，都早于收盘。Investing.com 16:23 UTC：股市转正，交易员消化首席执行官离任，AMD 上涨：[帖](https://x.com/Investingcom/status/2120915508748771338)。El-Erian 16:29 UTC：早段由英伟达带动的抛售之后，三大指数都在反弹，并且当时当天是上涨的：[帖](https://x.com/elerianm/status/2120916971893969284)。Kobeissi 15:56 UTC 的那句是标普抹掉全部跌幅并转绿。转绿是盘中。

收盘点位也是 First Squawk 21:04 UTC：纳斯达克收低 0.41%，在 25,362.36，下跌 103.83 点。标普收低 0.34%，在 7,593.63，下跌 25.75 点。道指收低 0.35%，在 52,303.93，下跌 182.56 点：[帖](https://x.com/FirstSquawk/status/2120985997983043681)。25,362.36 高于他写的开盘 25,087.73，7,593.63 高于开盘 7,559.87，52,303.93 低于开盘 52,555.52。路透的收盘句没有点位：美股收低，英伟达的下跌盖过了能源股的上涨：[帖](https://x.com/Reuters/status/2121052929008287966)。Investing.com 只写 VIX 跳升，没有点位：[帖](https://x.com/Investingcom/status/2120986732325753002)。不要拿周三的 7,619.22 去轧这 25.75 点。

## 目标价、继任概率和“该不该走”按账号留着

降级和目标价在 DeItaone 的一张盘前帖里，时间是辞职公告之前。Bernstein SocGen 降到 Market Perform，目标价从 400 美元砍到 200 美元。Oppenheimer 降到 Perform，撤回目标价。William Blair 降到 Market Perform。Evercore ISI 降到 In Line，目标价降到 186 美元。Stifel 从 315 美元降到 205 美元。花旗从 285 美元降到 225 美元。RBC 从 330 美元降到 230 美元。美银从 350 美元降到 280 美元。Yorkville Ives 从 300 美元降到 225 美元。维持的有：瑞穗 Outperform、目标价 250 美元；瑞银 Buy、300 美元；Raymond James Strong Buy、515 美元；Piper Sandler Overweight、300 美元：[帖](https://x.com/DeItaone/status/2120848638142226876)。另一条是 Melius 从 Buy 降到 Hold，目标价 185 美元：[帖](https://x.com/DeItaone/status/2120851588399173810)。200、186、205、225、230、280、185、250、300、515 是这张单子上的不同目标价。零对冲另写 Dan Ives 说没有黄仁勋，英伟达的价值少 25%。那是 13:13 UTC，也在正式辞职之前，而且不是一个美元目标价：[帖](https://x.com/zerohedge/status/2120867606563537186)。25% 不要换算成 225 或 200。

英特尔是另一只股票。First Squawk：美银全球研究把英特尔目标价从 100 美元降到 80 美元：[帖](https://x.com/FirstSquawk/status/2120838452203966954)。AMD 的方向相反，但没有收盘百分比。StockMKTNewz：William Blair 把 AMD 从 Market Perform 升到 Outperform：[帖](https://x.com/StockMKTNewz/status/2120863109048856826)。线外的 Earnings Whispers 只写 AMD 和博通在盘前上涨：[帖](https://x.com/eWhispers/status/2120878036056760465)。零对冲的 +1% 和将近 +1% 是盘前。

继任概率只有一张。DeItaone：预测市场把 Ian Buck 放在 34%，Kress 25%，AMD 的 Lisa Su 6%，并写临时首席执行官不是领先者：[帖](https://x.com/DeItaone/status/2120889004732059951)。特朗普的人选是另一句。First Squawk 引他的话：黄仁勋已经辞职，只有一个人能接，苹果的 Tim Cook：[帖](https://x.com/FirstSquawk/status/2120902063299428523)。34%、25%、6% 和 Tim Cook 不是同一张名单。

该不该辞职，账号之间是反的。线外的 Gary：他看了 30 年的公司剧，都是不确定性拖到不可避免的结果；黄仁勋辞职当天、不确定性最大的那天，应该买英伟达：[帖](https://x.com/garyblack00/status/2120881953394073711)。fundstrat：明天抄底；英伟达仍会是世界上最重要的公司；芯片设计、供应链和 CUDA 不会因为换人消失；如果黄仁勋是芯片的总设计师，风险会大得多：[抄底](https://x.com/fundstrat/status/2120918290650268041)、[CUDA](https://x.com/fundstrat/status/2120910321741119956)。线外的 firstadopter：七位华尔街分析师今天慌了、降级了，而这只股票是十五年来最便宜的；离开不意味着公司马上归零；未来两年已经订好了，下一任要为三到五年后做对决定：[帖](https://x.com/firstadopter/status/2121037830889566479)。Kobeissi 的判断相反：董事会犯了大错，他不该辞职，应该先调查、问股东：[帖](https://x.com/KobeissiLetter/status/2120888131314717128)。周五他又写，情报界的材料还不能证明 Alice Huang 是在为中国当间谍，中情局“还没有被说服”，联邦调查局查这件事至少一年；他维持“分手太早、需要完整调查”：[帖](https://x.com/KobeissiLetter/status/2121124218133725538)。aleabitoreddit：对未来没有信心，路演和收入能撑过接下来几年，长期看不到和 AMD、博通拉开距离的远见：[帖](https://x.com/aleabitoreddit/status/2120943109505008055)。克拉默收盘后改口：和投资人、技术人士谈了一天，对英伟达的变化感觉比早上好，但仍然难受：[帖](https://x.com/jimcramer/status/2121025275718783390)。周五早上他又写，现在听到首席财务官因为想拦住首席执行官过于激进的背书而被贬低，故事还有下文：[帖](https://x.com/jimcramer/status/2121163441297560048)。“应该买”“不该辞职”“没有信心”“感觉比早上好”是四句。

员工和散户的数字也不并。unusual_whales：匿名职场应用 Blind 上 232 名经过验证的员工里，88% 希望他留下：[帖](https://x.com/unusual_whales/status/2120913762198712429)。Kobeissi 引 WIRED：一份要求董事会让他复职的内部帖有超过 1600 条评论，多数是“完全支持”：[帖](https://x.com/KobeissiLetter/status/2121141764568314058)。aleabitoreddit 的投票是 22,965 人里 19,750 人支持留下、1,840 人反对，在表态的人里是 91.5% 对 8.5%：[帖](https://x.com/aleabitoreddit/status/2121148384555995136)。232 人、1600 条评论、22,965 人是三张调查。

零售买盘有两套美元数。DeItaone 引 Vanda：开盘头 30 分钟净买入 1.11 亿美元，是这只股票有记录以来最大的开盘半小时：[帖](https://x.com/DeItaone/status/2120936638461165973)。零对冲的标题是正常开盘的 41 倍：[帖](https://x.com/zerohedge/status/2120933505819357244)。Kobeissi 周五把同一笔拆开：头 30 分钟买入 4.55 亿美元、卖出 3.45 亿美元，净买入 1.11 亿美元。他又写周二买入 7.3 亿美元，是 3 月以来最大的单日；周一 5.9 亿，周三 3 亿；截止周三的三个交易日一共 16 亿美元，至少是 12 个月里最大的三日买入。两倍做多 ETF NVDL 流入 4.01 亿美元，NVDU 流入 6400 万美元：[帖](https://x.com/KobeissiLetter/status/2121171229210005816)。1.11 亿是净额。4.55 亿和 3.45 亿是同一窗口的买卖。16 亿是周一到周三，不含周四这 1.11 亿。

持股和表外承诺按帖留着。路透：他是第四大股东，持股大约 3.61%，也会离开董事会：[帖](https://x.com/Reuters/status/2120957222192832692)。CNBC：大约 1400 亿美元的持股大部分在和妻子 Lori 共同持有的信托里：[帖](https://x.com/CNBC/status/2121000143440765415)。unusual_whales：两人通过信托和有限责任公司共同持有大约 8 亿股、大约 1350 亿美元；他直接持有大约 7000 万股、大约 120 亿美元：[帖](https://x.com/unusual_whales/status/2120903695865196792)。彭博商业：未归属股份要损失 1.08 亿美元：[帖](https://x.com/business/status/2121017710448410969)。1400 亿、1350 亿、120 亿、1.08 亿、3.61% 不要收成一张资产负债表。unusual_whales 另写表外：给新云的贷款背书 360 亿美元，另有 200 亿美元是签了约、打算转租的数据中心租约：[帖](https://x.com/unusual_whales/status/2120950252513759625)。

调查和白宫是旁边的一串。FinancialJuice 引 Semafor：司法部反垄断调查；没有迹象要对黄仁勋提刑事指控；同时还在查 Megaspeed 和超微：[反垄断](https://x.com/financialjuice/status/2120915995191542171)、[不刑事](https://x.com/financialjuice/status/2120916345617514723)。First Squawk 写成多项司法部调查：[帖](https://x.com/FirstSquawk/status/2120918969578320308)。司法部长 Blanche：还没有得出 Alice Huang 是中国间谍的结论：[帖](https://x.com/FirstSquawk/status/2120981182599077949)。Kobeissi 把超微当天的跌幅写成扩到 14%，理由是在查她是否参与把超微产品走私到中国：[帖](https://x.com/KobeissiLetter/status/2120931469954596891)。DeItaone：黄仁勋聘了 Paul Weiss：[帖](https://x.com/DeItaone/status/2120935913693827273)。第二段关系和第三段关系是两张帖。First Squawk 引消息源：和另一名员工有亲密关系：[帖](https://x.com/FirstSquawk/status/2120964024821326268)。DeItaone 引路透：又一段，算第三段：[帖](https://x.com/DeItaone/status/2120970488008609934)。沃伦：辞职不能免除他的责任：[帖](https://x.com/DeItaone/status/2120888190277939307)。作证：First Squawk 写他同意向议员作证；FinancialJuice 写参议院银行委员会主席要求他和卢特尼克都来：[同意](https://x.com/FirstSquawk/status/2120909591685054793)、[召唤](https://x.com/financialjuice/status/2121030970522718215)。新加坡：DeItaone 写证据不足以起诉，但禁止再入境；The Stalwart 补了她向调查人员提供了不准确的信息：[DeItaone](https://x.com/DeItaone/status/2120871049940087122)、[The Stalwart](https://x.com/TheStalwart/status/2120883955826380962)。The Information 经 FinancialJuice：她的公司投资了 DeepSeek，并承诺提供 Blackwell：[帖](https://x.com/financialjuice/status/2120895316685918242)。公司会继续调查前首席执行官和所谓的中国间谍：[帖](https://x.com/FirstSquawk/status/2120983753774547205)。

特朗普的几句不要合成。除了 Tim Cook，周五 00:12 UTC 他称黄仁勋会“自己站起来”，才华很大，他还不知道那位女性有没有被认定是间谍：[帖](https://x.com/FirstSquawk/status/2121033379890246085)。《纽约时报》的句子是他曾施压，要黄仁勋为自己的职位争：[帖](https://x.com/FirstSquawk/status/2121035164847571419)。另一张是鼓励他坚守：[帖](https://x.com/FirstSquawk/status/2121037448398696909)。amit 引的是另一段：特朗普说周三和他通过话，他在受罪，最难受的是妻子和家人：[帖](https://x.com/amitisinvesting/status/2121038760817369254)。“让 Tim Cook 来”“会站起来”“曾要他争”“最难受的是家人”是四句。卢特尼克也是两句。DeItaone：白宫高级官员在讨论是否换掉商务部长：[帖](https://x.com/DeItaone/status/2120956721405575305)。FinancialJuice 引 CNN：特朗普仍然支持卢特尼克：[帖](https://x.com/financialjuice/status/2120889755999084768)。

马斯克和合并是旁边的价格。DeItaone：SpaceX 股份周四上涨大约 4%，因为市场在猜黄仁勋会不会和马斯克一起干；马斯克的回复是“那会是一种荣幸”：[帖](https://x.com/DeItaone/status/2120895754109628842)。FinancialJuice：SpaceX 和特斯拉的合并讨论在推进，最早 12 月宣布，也可能滑到 2027 年：[帖](https://x.com/financialjuice/status/2120972445020508224)。线外的 Gary：用 SpaceX 股票做合并，对特斯拉股东几乎没有意外之财，稀释很大，从宣布到完成要 12 到 18 个月：[帖](https://x.com/garyblack00/status/2120983275040539044)。4% 是 SpaceX。12 到 18 个月是 Gary 写的时间，不是已经宣布的交易。FinancialJuice 另有一张：SpaceX 计划在亚利桑那做大约 500 亿美元的超算园区、6500 个岗位：[帖](https://x.com/financialjuice/status/2120910738629771641)。500 亿是园区，不是合并对价。

## 新云按时刻留跌幅，思科和应用材料是盘后的另一张成绩单

辞职之后的盘前跌幅不要收成收盘。DeItaone：Nebius -20.1%，CoreWeave -13.6%，Roundhill 新云 ETF -12.5%，IREN -8.1%：[帖](https://x.com/DeItaone/status/2120880061985243640)。Kobeissi 的名单更长，数字也略有不同：Nebius -21%，CoreWeave -14%，Roundhill 的 NEO -13%，IREN -9%，Cipher -9%，Applied Digital -8%，TeraWulf -7%，Core Scientific -5%：[帖](https://x.com/KobeissiLetter/status/2120886129813553412)。-20.1% 和 -21%、-13.6% 和 -14%、-8.1% 和 -9% 按原帖留着。

Nebius 自己的业绩是更早的一套。零对冲的盘前 movers：因为 2027 年资本开支看到 400 亿到 450 亿美元，彭博一致预期是 287.6 亿美元，盘前 -8%：[帖](https://x.com/zerohedge/status/2120865088101896514)。StockMKTNewz 把资本开支写成 400 亿到 450 亿美元：[帖](https://x.com/StockMKTNewz/status/2120864890676191531)。The Transcript：公司更新 2026 年指引，一部分原定今年上线的第三方产能改到 2027 年上半年，盘前 -15%：[帖](https://x.com/TheTranscript_/status/2120876119113322644)。首席执行官仍说需求极强：[帖](https://x.com/TheTranscript_/status/2120876292921069899)。开盘之后，CNBC 写成周四下跌 10%，收入超预期、指引令人失望：[帖](https://x.com/CNBC/status/2120887852024160578)。彭博商业写成早盘大约 -10%：[帖](https://x.com/business/status/2120902019594465294)。unusual_whales：开盘缺口 -17%，盘中从 120 美元回到 128 美元，看涨权利金中午后占了上风：[帖](https://x.com/unusual_whales/status/2120933697218359601)。-8%、-15%、-20.1%、-21%、-10%、大约 -10%、-17% 是七个时刻。120 和 128 是缺口之后的价格。aleabitoreddit 的利润表不要和跌幅合成：收入从 5.823 亿美元到 9.808 亿美元，环比 +68%；调整后 EBITDA 从 2.362 亿到 4.658 亿，环比 +97%；人工智能云的调整后 EBITDA 利润率从 49.7% 到 53.2%；净亏损从 1.904 亿收到 3750 万；9 月末年化经常性收入 64 亿美元；三季度开始以来新签超过 120 亿美元；GPU 价格环比上涨超过 20%：[帖](https://x.com/aleabitoreddit/status/2120866647930187882)。

CoreWeave 周四的百分比只有盘前那两句。米内尔维尼写的是周三：大涨 24.7%，收在 60.77 美元，52 周高点 138.2 美元，仍比高点低大约 56%。IREN 周三涨 5.6%，收在 20.84 美元，高点 70.71 美元，仍低大约 71%。他把这些叫做下跌趋势里的反弹：[帖](https://x.com/markminervini/status/2120883843221573909)。24.7% 和 5.6% 是周三，不是周四的 -13.6% 或 -14%。

思科是盘后的超预期，而且股价有一句。First Squawk：调整后每股收益 1.40 美元，高于预期 1.32 美元；收入 185 亿美元，高于 181.3 亿美元。下一帖：二季度调整后每股收益看到 1.34 到 1.36 美元，收入 180 亿到 182 亿美元，全年调整后每股收益从 5.05 到 5.11 美元上修到 5.47 到 5.53 美元：[一季度](https://x.com/FirstSquawk/status/2120986818917347676)、[指引](https://x.com/FirstSquawk/status/2120986828782363116)。FinancialJuice 多了几行：调整后毛利率 65.6%，符合预期；产品收入 146.7 亿美元，预期 142.9 亿美元；服务收入 38.5 亿美元，预期 38.3 亿美元；剩余履约义务 461.7 亿美元，预期 451.6 亿美元；全年人工智能超大规模云收入目标抬到 90 亿美元；二季度收入预期在他这张帖上是 178.5 亿美元，调整后每股收益预期 1.23 美元；全年收入从 722 亿到 734 亿美元上修到 748 亿到 758 亿美元：[帖](https://x.com/financialjuice/status/2120986922126376970)。LiveSquawk 的二季度收入预期写成 178.5 亿美元，和 FinancialJuice 相同，和 First Squawk“高于预期”那句没有写出的预期数字不必轧差：[帖](https://x.com/LiveSquawk/status/2120987892205932603)。CNBC：股价上涨 5%：[帖](https://x.com/CNBC/status/2120990002418971037)。The Transcript 引首席执行官：一季度收入和非公认会计准则每股收益的增速是十多年来最强：[帖](https://x.com/TheTranscript_/status/2120992658894242054)。5% 是 CNBC 的盘后股价。1.40 美元对 1.32 美元是每股收益。90 亿美元只在 FinancialJuice 的人工智能目标那一行。

应用材料也是双超，没有盘后股价。FinancialJuice：调整后每股收益 4.16 美元，预期 4.06 美元；销售额 104.1 亿美元，预期 102.7 亿美元；半导体系统 80 亿美元，预期 79.4 亿美元；一季度销售额看到 106 亿到 116 亿美元，预期 108.7 亿美元：[帖](https://x.com/financialjuice/status/2120987109632917754)。First Squawk 把区间中点写成高于 108.7 亿美元的预期：[销售额](https://x.com/FirstSquawk/status/2120988077426610424)、[区间](https://x.com/FirstSquawk/status/2120988088205979830)。The Transcript 引首席执行官：财季收入同比 +53%，非公认会计准则每股收益同比 +92%，自由现金流 26 亿美元，向股东分配超过 24 亿美元：[帖](https://x.com/TheTranscript_/status/2120991803570893141)。线外的 SpotGamma 在业绩前写，期权定价大约 7.1% 的波动：[帖](https://x.com/SpotGamma/status/2120968953879007259)。7.1% 是期权定价，不是已经发生的涨跌。线外的 Earnings Whispers 引 KLA：把 2027 年晶圆厂设备市场看到 2000 亿美元以上：[帖](https://x.com/eWhispers/status/2120946012651209078)。2000 亿是 KLA 的行业句子，不是应用材料的销售额。克拉默把 Cerebras 和思科放在一起：人工智能在英伟达以外仍然强：[帖](https://x.com/jimcramer/status/2120989394995646546)。零对冲的 Cerebras 是四季度核心收入 3.1 亿到 3.3 亿美元，预期 2.712 亿美元：[帖](https://x.com/zerohedge/status/2120986358227345452)。

## 油价结算上涨，黄金和收益率是另一套

结算价有明确的 settle。FinancialJuice：NYMEX WTI 12 月期货结算 88.74 美元，上涨 2.21 美元，2.55%。布伦特结算 95.82 美元，上涨 3.06 美元，3.3%：[WTI](https://x.com/financialjuice/status/2120962717188297098)、[布伦特](https://x.com/financialjuice/status/2120966210317947064)。First Squawk 的布伦特是同一组 95.82 美元、+3.3%、+3.06 美元：[帖](https://x.com/FirstSquawk/status/2120966476840739226)。汽油期货结算 2.6708 美元/加仑，柴油 4.2865 美元/加仑，天然气 3.3400 美元/百万英热：[汽油](https://x.com/financialjuice/status/2120962896142246330)、[柴油](https://x.com/financialjuice/status/2120962975641272326)、[天然气](https://x.com/financialjuice/status/2120962837434527786)。88.74 美元是 WTI 结算。95.82 美元是布伦特结算。

盘中的口号对不上这组结算。线外的 Gary 11:20 UTC：布伦特下跌 1%，到 92 美元。First Squawk 13:13 UTC：布伦特涨幅扩到 1%，在特朗普的伊朗评论之后：[帖](https://x.com/FirstSquawk/status/2120867685835915555)。13:17 UTC：特朗普说美国不需要和伊朗做交易之后，油价抹掉跌幅：[帖](https://x.com/FirstSquawk/status/2120868592048828417)。线外的 Blas 引的原话是：不需要交易，那些日子过去了，钱在我们手里，海峡也在我们手里：[帖](https://x.com/JavierBlas/status/2120877211687309361)。DeItaone 19:15 UTC：伊朗通讯社称遭袭击之后，WTI 当时 +2.36%，布伦特 +3%：[帖](https://x.com/DeItaone/status/2120958766644609049)。-1% 到 92 美元、+1%、抹掉跌幅、+2.36%、+3% 都早于结算。结算是 88.74 和 95.82。

库存和月报不要合成。FinancialJuice 的能源信息署：原油库存 +465.7 万桶，预期 -148.3 万桶，前值 -86.5 万桶：[帖](https://x.com/financialjuice/status/2120924713417650409)。First Squawk 的预期写成 -85.26 万桶：[帖](https://x.com/FirstSquawk/status/2120924629879619882)。-148.3 万和 -85.26 万是两套预期，实际数都是增加。LiveSquawk 把分项写成：馏分油 +407.1 万桶，预期 -200 万桶；库欣 +10.6 万桶；汽油 +179.9 万桶，预期 -35 万桶：[帖](https://x.com/LiveSquawk/status/2120925216255656103)。零对冲的标题是全面累库、战略储备大降、美国产量创纪录，帖文里没有写出战略储备的桶数：[帖](https://x.com/zerohedge/status/2120926711730585927)。周五的国际能源署是另一份报告。First Squawk：10 月观察到的库存增加 5200 万桶，是 6 月以来第一次增加；11 月的平衡改成 2026 年四季度过剩每天 170 万桶，先前的预测是短缺；成员国计划到 2027 年 2 月底再释放 7100 万桶紧急原油和成品油库存：[5200 万](https://x.com/FirstSquawk/status/2121168836338823177)、[170 万桶](https://x.com/FirstSquawk/status/2121169625753006510)、[7100 万](https://x.com/FirstSquawk/status/2121168937975201812)。FinancialJuice：10 月霍尔木兹石油流量环比增加每天 44 万桶，到 1180 万桶：[帖](https://x.com/financialjuice/status/2121166804559294949)。Blas 的句子是：10 月因为海湾高出口转入过剩，但柴油供应的严重紧张仍是压倒性的问题：[帖](https://x.com/JavierBlas/status/2121167841583825181)。他另写，把基准油价、实货贴水和运费加在一起，炼厂门口的“落地”油价自 9 月 15 日前后的高点下跌 35% 到 40%：[帖](https://x.com/JavierBlas/status/2120920859095306729)。35% 到 40% 是自 9 月中，不是周四的 +3.3%。美国零售汽油他写成连续第二天大跌，周四是有记录以来第二大的单日跌幅；如果批发价守住，感恩节周末零售价会到 8 个月低点：[帖](https://x.com/JavierBlas/status/2120848679309553987)。这张帖没有写出周四的零售美分。Hanke 的船数是 11 月 11 日：去年当天 67 艘，今年 1 艘：[帖](https://x.com/steve_hanke/status/2120964345320583325)。1 艘对 67 艘是他的 11 月 11 日。1180 万桶是国际能源署的 10 月日流量。不要并成“海峡开了”或“海峡关了”。

袭击是另外几张。First Squawk：胡塞称袭击沙特延布的石油设施：[帖](https://x.com/FirstSquawk/status/2120924038092738699)。周五又写袭击东西管道的泵站：[帖](https://x.com/FirstSquawk/status/2121065711909191728)。零对冲：伊朗打击引导油轮走霍尔木兹“未经授权”南线的阿曼岛屿：[帖](https://x.com/zerohedge/status/2120883674811945147)。另一帖：法尔斯称锡里克听到爆炸：[帖](https://x.com/zerohedge/status/2120952368963399795)。延布、泵站、阿曼岛、锡里克按原帖留着。

黄金没有结算价。DeItaone 13:27 UTC：现货金跌幅将近 2%，到 3,908.03 美元。14:59 UTC 他和 First Squawk 都写成下跌 3%，到 3,866.08 美元：[3908](https://x.com/DeItaone/status/2120871190088798224)、[3866](https://x.com/DeItaone/status/2120894164967862607)、[First Squawk](https://x.com/FirstSquawk/status/2120894318261223669)。线外的 Ole Hansen 13:53 UTC：黄金跌向上个月低点附近的 3,870 美元：[帖](https://x.com/Ole_S_Hansen/status/2120877569440448640)。3,908.03、3,866.08、3,870 附近是三个时刻，都不是结算。Peter Schiff：黄金把中期选举之后的涨幅全部吐掉，理由是更高的通胀带来更多加息谈话，而那些加息小到影响不了通胀；他的结论是买跌：[帖](https://x.com/PeterSchiff/status/2120876066269171908)。线外的 Bespoke 只写黄金 ETF 创出新低，没有价格：[帖](https://x.com/bespokeinvest/status/2120930186875060430)。Luke Gromen：黄金的价格行为应该把投资者吓醒，他引了一句“如果你不害怕，就是没在看”：[帖](https://x.com/LukeGromen/status/2120993413034340686)。线外的 Keith 早上把黄金写成美元相关性里最差的大类资产，他做多美元：[帖](https://x.com/KeithMcCullough/status/2120820694208430403)。Ole 周五早上的周线是另一句：彭博商品总回报指数本周小跌，今年至今还剩 +26%；贵金属本周 -4%：[帖](https://x.com/Ole_S_Hansen/status/2121145011848847691)。-4% 是本周的贵金属，不是周四现货的 -3%。

收益率有三套 10 年期，不要收成一个收盘。El-Erian 17:31 UTC：10 年期国债收益率交易在 5.10%：[帖](https://x.com/elerianm/status/2120932564814770512)。零对冲 18:34 UTC：回到 5.11%，三天上涨 25 个基点，离几十年高点还差 20 个基点：[帖](https://x.com/zerohedge/status/2120948425000685914)。Bianco 周五：本周四个交易日上涨超过 25 个基点：[帖](https://x.com/biancoresearch/status/2121078591731777540)。5.10%、5.11%、超过 25 个基点、25 个基点、四个交易日对三天，按原帖留着。2 年期是另一列。First Squawk 周五 00:13 UTC：上升到一个月高点 4.8920%：[帖](https://x.com/FirstSquawk/status/2121033667615363521)。周四 15:01 UTC 他写 2 年到 5 年的收益率当天至少上升 10 个基点：[帖](https://x.com/FirstSquawk/status/2120894691990519919)。Ole 13:53 UTC：2 年期从上周低点上升 35 个基点，当时纳斯达克曾跌 1800 点。35 个基点是从上周低点，不是周四当天的 10 个基点，也不是 4.8920% 这个点位。

30 年拍卖有尾部。FinancialJuice：招标前预发行收益率 5.437%；最高收益率 5.441%，尾部 0.4 个基点，投标倍数 2.36，间接标 68.11%，前一次最高收益率 5.618%：[预发行](https://x.com/financialjuice/status/2120940266764796013)、[结果](https://x.com/financialjuice/status/2120940410637783150)。零对冲：0.4 个基点的尾部是 6 月以来最大：[帖](https://x.com/zerohedge/status/2120940753266541007)。5.441% 是拍卖。5.10% 和 5.11% 是 10 年期。4.8920% 是 2 年期。

美元是 El-Erian 的收盘后句子：美元指数到了 2025 年 4 月初的水平，欧元 1.1057，日元 159.89：[帖](https://x.com/elerianm/status/2120984427241046386)。他早上只写美国仍在把全球国债收益率往上带，没有点位：[帖](https://x.com/elerianm/status/2120870944566567286)。

## 加息的句子互相矛盾，数据日已经有结果

有效联邦基金利率是 3.88%，11 月 10 日对 11 月 9 日没有变化：[帖](https://x.com/financialjuice/status/2120879334554796193)。

官员按人留着。First Squawk 引 Hammack：要把利率抬到限制性；她不认为现在落后于曲线，如果落后才会考虑更猛的动作：[限制性](https://x.com/FirstSquawk/status/2120880186409537984)、[不落后](https://x.com/FirstSquawk/status/2120880209356571024)。FinancialJuice 补了她更想看到更小、更稳的步骤：[帖](https://x.com/financialjuice/status/2120879347103850618)。Daly 在 First Squawk 的三张帖里：通胀压力是向上的，企业在说要转嫁成本，她对 9 月的加息放心，倾向是还要再收；具体收多少、什么时候，现在不必决定，更紧的金融条件给了时间：[向上](https://x.com/FirstSquawk/status/2120950644903383249)、[再收](https://x.com/FirstSquawk/status/2120950669016551912)、[不必现在决定](https://x.com/FirstSquawk/status/2120950681456800240)。FinancialJuice 把“对 9 月加息放心、还要再收”收成一句：[帖](https://x.com/financialjuice/status/2120948696812532138)。Goolsbee：美联储在通胀这一侧的使命上是失败的：[帖](https://x.com/financialjuice/status/2120920510276284696)。Schmid：还没打败通胀这个敌人；必须把通胀打回 2% 的目标：[敌人](https://x.com/financialjuice/status/2120951340746809503)、[2%](https://x.com/financialjuice/status/2120957217545535862)。国际货币基金组织：为了反通胀，美联储需要维持限制性立场：[帖](https://x.com/financialjuice/status/2120917184168047093)。

市场定价和交易员的句子是反的。线外的 Ole：市场已经完全定价下个月加 25 个基点，其后六个月再加两次：[帖](https://x.com/Ole_S_Hansen/status/2120877569440448640)。周五他又写 SOFR 期货把明年 9 月的峰值利率定在 4.8%，本周上移 40 个基点：[帖](https://x.com/Ole_S_Hansen/status/2121151516245438484)。线外的 Gary 在早盘长帖里写，市场已经完全定价下个月加息。线外的 Brooks 写的是不需要加息：疫情后那次更大的核心 PCE 冲击，在同样紧的劳动力市场里自己掉了回来；油价跌了，但美联储定价更鹰、美元升、黄金跌，这种相关性破裂维持不了多久：[不加息](https://x.com/robin_j_brooks/status/2120897446616461347)、[相关性](https://x.com/robin_j_brooks/status/2120871757011980549)。“油价跌了”是他 13:30 UTC 的句子，早于布伦特结算上涨 3.3%。线外的 RedDog 12:31 UTC 写成市场在定价 12 月降息：[帖](https://x.com/RedDogT3/status/2120857027828203835)。25 个基点再加两次、完全定价加息、不需要加息、12 月降息，是四句。4.8% 是 Ole 写的明年 9 月峰值，不是有效联邦基金利率的 3.88%。

2027 年日历不要听错。美联储账号只写修订了 2027 年 FOMC 的暂定日程，帖文里没有日期：[帖](https://x.com/federalreserve/status/2120936375390540151)。线外的 Nick Timiraos 把日期写出来了：10 月 26 到 27 日的会还在，但是战略会，没有政策行动；原来 12 月 7 到 8 日的会提前到 11 月 16 到 17 日：[帖](https://x.com/NickTimiraos/status/2120936270004371890)。First Squawk、FinancialJuice 和零对冲的标题是“拿掉 10 月的议息会”：[First Squawk](https://x.com/FirstSquawk/status/2120924318913995188)、[FinancialJuice](https://x.com/financialjuice/status/2120924438023503878)、[零对冲](https://x.com/zerohedge/status/2120924398832046228)。“拿掉议息”是标题。“会还在、但没有政策行动，12 月的会提前到 11 月”是 Nick 的句子。

已经出来的数据按账号留着。Liz Ann：初请 20 万，预期 19.4 万，前值 19.1 万；续请 169.7 万，预期 171 万，前值 171.7 万：[帖](https://x.com/LizAnnSonders/status/2120873577540984864)。零对冲的初请和续请是同一组 20 万和 169.7 万，预期也是 19.4 万和 171 万：[帖](https://x.com/zerohedge/status/2120871795968573658)。他的标题把初请写成 57 年低位：[帖](https://x.com/zerohedge/status/2120873355427365250)。成屋销售：Liz Ann 写成 10 月环比 -5.5%，预期 -3.5%，前值从 +1.5% 下修到 +1.0%；中位价同比 +0.4%，到 416,700 美元：[帖](https://x.com/LizAnnSonders/status/2120897176150933527)。零对冲的年化套数是 375 万，预期 385 万，前值 397 万：[帖](https://x.com/zerohedge/status/2120894512239177750)。El-Erian 写成 16 年最低：[帖](https://x.com/elerianm/status/2120896220885303489)。Schiff 多了同比 -8.76%，并写成 2010 年 8 月以来最低、崩溃还在前面：[帖](https://x.com/PeterSchiff/status/2120904813202288758)。-5.5%、375 万、16 年、-8.76%、2010 年 8 月，按原帖留着。

预算是 10 月的财政月报。LiveSquawk：赤字 4041 亿美元，预期 3175 亿，前值 2843 亿：[帖](https://x.com/LiveSquawk/status/2120954901471900016)。DeItaone：4040 亿美元，比一年前的 2840 亿高 42%；支出创纪录 7730 亿美元，一年前 6890 亿：[帖](https://x.com/DeItaone/status/2120955090525720997)。零对冲把收入写成同比 -8.8%、到 3690 亿美元，支出 7730 亿美元、同比 +12%，国防开支一个月里涨了将近 50%、到 1290 亿美元，利息 1155 亿美元；每一美元税收里有 28 美分付利息；他写债务会在四到六周里碰到 41 万亿美元：[收入](https://x.com/zerohedge/status/2121062936437244034)、[利息](https://x.com/zerohedge/status/2121065172827848739)、[28 美分](https://x.com/zerohedge/status/2121065882927411696)。4041 亿和 4040 亿是两种四舍五入。42% 只在 DeItaone 的帖里。

## 周五盘前：期货几乎持平，现货还没开

First Squawk 09:57 UTC：标普 500 电子迷你期货上涨 0.07%，纳斯达克 100 期货下跌 0.16%，道指期货上涨 0.11%：[帖](https://x.com/FirstSquawk/status/2121180640272154984)。这是抓取结束前最后一条股指期货。0.07%、-0.16%、0.11% 不是收盘，也不是周四的 -0.34%、-0.41%、-0.35%。

欧洲和澳洲有点数，韩国没有。First Squawk 05:18 UTC：欧元区斯托克 50 和德国 DAX 的期货下跌 0.4%：[帖](https://x.com/FirstSquawk/status/2121110523479801874)。08:01 UTC：富时 100 -0.16%，法国 CAC -0.2%，西班牙 IBEX -0.17%。08:04 UTC：DAX 现货 -0.2%：[富时](https://x.com/FirstSquawk/status/2121151512697340252)、[DAX](https://x.com/FirstSquawk/status/2121152330657865733)。澳洲标普/ASX 200 收盘 -0.7%，到 9,082.20：[帖](https://x.com/FirstSquawk/status/2121111897890250794)。韩国股份在开盘时因为英伟达的人事变化上涨，这则标题没有百分比：[帖](https://x.com/FirstSquawk/status/2121045232649474552)。00:27 UTC 的区域句是亚太涨跌互现：[帖](https://x.com/FirstSquawk/status/2121037096072917194)。

油价的隔夜标题和结算相反方向。First Squawk 02:29 UTC 引《华尔街日报》：原油进一步下滑，市场在权衡外交突破的可能性：[帖](https://x.com/FirstSquawk/status/2121068010177958260)。“进一步下滑”没有百分比。95.82 美元和 88.74 美元仍是周四结算。

比特币有三句。Kobeissi 01:19 UTC：跌破 71,000 美元，是 8 月 20 日以来第一次，自 10 月 2 日下跌超过 19%：[帖](https://x.com/KobeissiLetter/status/2121050160784400606)。LiveSquawk 03:38 UTC 引彭博：跌破 70,000 美元：[帖](https://x.com/LiveSquawk/status/2121085352966590710)。StockMKTNewz 05:57 UTC：回到 68,000 美元：[帖](https://x.com/StockMKTNewz/status/2121120317016006855)。Schiff 写成交易价格低于 2021 年 11 月，长期熊市：[帖](https://x.com/PeterSchiff/status/2121081741804765691)。71,000、70,000、68,000 按时间留着。

微软的服务中断是趋势里的 Outlook、Microsoft 和 Gmail，不是一个股价。First Squawk 18:06 UTC：Downdetector 显示 Outlook 在美国超过 39,000 名用户报告故障，Microsoft 365、Copilot 和商店也有数千人：[帖](https://x.com/FirstSquawk/status/2120941336258040026)。CNBC：Outlook 中断，亚马逊云和谷歌的用户也有报告：[帖](https://x.com/CNBC/status/2120985126284730480)。周五 09:23 UTC，微软称看到初步企稳迹象，并把邮件超时窗口延到 48 小时：[企稳](https://x.com/FirstSquawk/status/2121172123377131617)、[48 小时](https://x.com/FirstSquawk/status/2121172192046289187)。时间线里没有微软股价的百分比。

已经排进周五、抓取结束时还没有结果的名字按日历留着。线外的 Bespoke：美联储讲话是 Collins、Logan、Bowman、Daly、Jefferson。天然气库存美东 10:30。贝克休斯钻机数下午 1 点：[帖](https://x.com/bespokeinvest/status/2121007634979397737)。零对冲把下周写成 11 月 17 日英伟达财报，11 月 18 到 19 日特朗普飞深圳参加 APEC：[帖](https://x.com/zerohedge/status/2121072324162019722)。线外的 The Stalwart：下周是英伟达财报，以及大概率的 Anthropic IPO：[帖](https://x.com/TheStalwart/status/2121020573522313630)。17 日是下周二。18 日同时是全员会和 APEC 的第一天。

Anthropic 的认购是周四晚上的句子，不是已经定价。DeItaone 引彭博：大约 6 倍超额认购；IPO 要募 644 亿美元，另加 260 亿美元私募，他写成合计可能 904 亿美元；英伟达承诺了大约 100 亿美元的私募，尽管股价在跌；10 月年化收入跑到 810 亿美元，9 月是 710 亿，7 月是 650 亿；估值目标 1.4 万亿美元：[帖](https://x.com/DeItaone/status/2120987833888370826)。零对冲另写 OpenAI 以 1.25 万亿美元估值筹集 150 亿美元，来源是 CNBC：[帖](https://x.com/zerohedge/status/2120892048404341156)。6 倍、644 亿、260 亿、904 亿、100 亿、810 亿、1.4 万亿是 Anthropic。150 亿和 1.25 万亿是 OpenAI。Bianco 用 6 倍认购写成“人工智能泡沫也许没在破”：[帖](https://x.com/biancoresearch/status/2120985585200582753)。

## 要盯住的五件事

1. **现货 9:30 还没开，周四收盘已经写下来了。** 标普 7,593.63，-0.34%。纳斯达克 25,362.36，-0.41%。道指 52,303.93，-0.35%。开盘是 7,559.87、25,087.73、52,555.52。盘中标普曾被写成转绿。周五 09:57 的期货是标普 +0.07%、纳斯达克 100 -0.16%、道指 +0.11%。
2. **英伟达的收盘不要取一个百分比。** 金融时报和 First Squawk 的综述是 -4.3%。MarketWatch 和 Investing.com 是 -4%。The Information 是将近 -7%，外加两周超过 -25%。开盘有 -13% 和 -14%，盘前还有 -7% 到 -13%。163、164、165、148.80、151、187 是不同时刻的价格。Bernstein 的目标价是 200 美元。Melius 是 185 美元。Raymond James 维持 515 美元。
3. **辞职已经生效，继任还没有。** Kress 是临时首席执行官，仍是首席财务官。Harvey Jones 是第一任主席。Ian Buck 34%、Kress 25%、Lisa Su 6% 是预测市场。Tim Cook 是特朗普的句子。司法部还没有把 Alice Huang 定成间谍，也没有迹象要刑事起诉黄仁勋。
4. **油价结算和周五早上的“下滑”标题分开。** WTI 结算 88.74 美元，涨 2.55%。布伦特结算 95.82 美元，涨 3.3%。周五标题只写原油进一步下滑，没有百分比。国际能源署把四季度改成每天过剩 170 万桶。Hanke 的 11 月 11 日是 1 艘对 67 艘。
5. **周五的日历还没有结果。** 美联储讲话从 Collins、Logan、Bowman、Daly 到 Jefferson。天然气库存在美东 10:30。钻机数在下午 1 点。英伟达财报是 17 日，全员会是 18 日。Anthropic 是 6 倍认购，还没有定价。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。盘前和盘中不是收盘。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 收盘 | 标普、纳斯达克、道指 | 标普 7,593.63，-0.34%，-25.75 点。纳斯达克 25,362.36，-0.41%，-103.83 点。道指 52,303.93，-0.35%，-182.56 点 | [收盘](https://x.com/FirstSquawk/status/2120985997983043681) |
| 开盘 | 标普、纳斯达克、道指 | 7,559.87，-0.78%；25,087.73，-1.49%；52,555.52，+0.13% | [开盘](https://x.com/FirstSquawk/status/2120887132659323356) |
| 盘中 | 标普 | Kobeissi：抹掉全部跌幅并转绿。El-Erian：三大指数当时都在上涨。收盘仍是下跌 | [转绿](https://x.com/KobeissiLetter/status/2120908498804293843)、[当时上涨](https://x.com/elerianm/status/2120916971893969284) |
| 周五盘前 | 股指期货 | 标普电子迷你 +0.07%，纳斯达克 100 -0.16%，道指 +0.11% | [期货](https://x.com/FirstSquawk/status/2121180640272154984) |
| 收盘 | NVDA | 金融时报和 First Squawk 综述 -4.3%。MarketWatch 和 Investing.com -4%。The Information 将近 -7%，两周超过 -25% | [-4.3%](https://x.com/FT/status/2120989286644224158)、[将近 -7%](https://x.com/theinformation/status/2121022759371157543) |
| 开盘和盘前 | NVDA | 盘前有 -7%、-8%、-8.4%、-10%、-11%、几乎 -12%、-13%。开盘金融时报 -13%、超过 5000 亿美元。FinancialJuice -14%、5930 亿美元、跌破 4 万亿美元 | [-13% 盘前](https://x.com/FirstSquawk/status/2120885026162377149)、[-14%](https://x.com/financialjuice/status/2120887371202015394) |
| 盘中价位 | NVDA | 重新站上 163 美元。164 美元、当天 -5.4%。隔夜 151 美元后到 165 美元。低点 148.80 美元后大约 +9%。正 gamma 在 187，负 gamma 在 170 到 176 | [163](https://x.com/KobeissiLetter/status/2120899669341446242)、[187](https://x.com/unusual_whales/status/2120934901578879352) |
| 目标价 | NVDA | Bernstein 200 美元，从 400。Melius 185。Evercore 186。Stifel 205。花旗和 Yorkville Ives 225。RBC 230。美银 280。瑞穗 250。瑞银、Piper 300。Raymond James 515。Oppenheimer 撤回目标价 | [清单](https://x.com/DeItaone/status/2120848638142226876)、[185](https://x.com/DeItaone/status/2120851588399173810) |
| 概率 | NVDA | Ian Buck 34%，Kress 25%，Lisa Su 6%。特朗普点名 Tim Cook | [34%](https://x.com/DeItaone/status/2120889004732059951)、[Cook](https://x.com/FirstSquawk/status/2120902063299428523) |
| 零售 | NVDA | 头 30 分钟净买入 1.11 亿美元。Kobeissi 拆成买入 4.55 亿、卖出 3.45 亿。周一到周三合计 16 亿美元 | [1.11 亿](https://x.com/DeItaone/status/2120936638461165973)、[16 亿](https://x.com/KobeissiLetter/status/2121171229210005816) |
| 盘前 | NBIS、CRWV、IREN | DeItaone：-20.1%、-13.6%、-8.1%。Kobeissi：-21%、-14%、-9%。Nebius 另有盘前 -8%、-15%，以及开盘后 -10% 和 -17% 后回到 128 美元 | [DeItaone](https://x.com/DeItaone/status/2120880061985243640)、[128](https://x.com/unusual_whales/status/2120933697218359601) |
| 资本开支 | NBIS | 2027 年 400 亿到 450 亿美元。零对冲写的彭博预期是 287.6 亿美元 | [400 到 450](https://x.com/StockMKTNewz/status/2120864890676191531) |
| 盘后 | CSCO | 调整后每股收益 1.40 对 1.32，收入 185 亿对 181.3 亿。全年调整后每股收益上修到 5.47 到 5.53。CNBC 写股价 +5% | [业绩](https://x.com/FirstSquawk/status/2120986818917347676)、[+5%](https://x.com/CNBC/status/2120990002418971037) |
| 盘后 | AMAT | 调整后每股收益 4.16 对 4.06，销售额 104.1 亿对 102.7 亿。一季度看到 106 到 116 亿美元。没有盘后股价。期权定价过 7.1% 的波动 | [业绩](https://x.com/financialjuice/status/2120987109632917754)、[7.1%](https://x.com/SpotGamma/status/2120968953879007259) |
| 盘前 | AMD、AVGO | 零对冲：AMD +1%，博通将近 +1%。William Blair 把 AMD 升到 Outperform。没有收盘百分比 | [盘前](https://x.com/zerohedge/status/2120865088101896514)、[升级](https://x.com/StockMKTNewz/status/2120863109048856826) |
| 目标价 | INTC | 美银从 100 美元降到 80 美元 | [80](https://x.com/FirstSquawk/status/2120838452203966954) |
| 盘中 | SMCI | Kobeissi：跌幅扩到 14%，司法部在查是否经她走私超微产品 | [14%](https://x.com/KobeissiLetter/status/2120931469954596891) |
| 周四大约 +4% | SPCX | DeItaone：因为和马斯克合作的猜测上涨大约 4%。合并讨论最早 12 月，也可能到 2027 年 | [4%](https://x.com/DeItaone/status/2120895754109628842)、[合并](https://x.com/financialjuice/status/2120972445020508224) |
| 结算 | WTI、布伦特 | WTI 88.74 美元，+2.55%。布伦特 95.82 美元，+3.3% | [WTI](https://x.com/financialjuice/status/2120962717188297098)、[布伦特](https://x.com/financialjuice/status/2120966210317947064) |
| 现货 | 黄金 | 将近 -2% 到 3,908.03 美元，再 -3% 到 3,866.08 美元。Ole 写成跌向 3,870 附近。没有结算价 | [3866](https://x.com/FirstSquawk/status/2120894318261223669) |
| 收益率 | 10 年、2 年、30 年 | El-Erian 的 10 年期 5.10%。零对冲 5.11%。2 年期 4.8920%。30 年拍卖 5.441%，尾部 0.4 个基点 | [5.10%](https://x.com/elerianm/status/2120932564814770512)、[4.8920%](https://x.com/FirstSquawk/status/2121033667615363521)、[5.441%](https://x.com/financialjuice/status/2120940410637783150) |
| 周内 | SMH | 线外的 Detrick：英伟达当周 -12%，SMH +8% | [SMH](https://x.com/RyanDetrick/status/2120960467753394353) |
| 52 周 | 一批个股 | StockMKTNewz：当天曾创 52 周高的包括礼来、苹果、可口可乐、Costco、伯克希尔 B、强生。曾创 52 周低的包括英伟达、Corteva、蔚来、Stellantis | [高点](https://x.com/StockMKTNewz/status/2120970793198985613)、[低点](https://x.com/StockMKTNewz/status/2120980070206521580) |
| 盘前 | CTVA、EYE、YETI、LLY | 零对冲：Corteva -9%，National Vision -16%，YETI -7%，礼来 +2%。都是盘前 movers，不是收盘 | [盘前](https://x.com/zerohedge/status/2120865088101896514) |
| 位置 | 标普 gamma | 线外的 SpotGamma：gamma 在 7,600 下方翻转，负 gamma 建到 7,350。收盘前 7,625 到 7,605 有正 charm | [7600](https://x.com/SpotGamma/status/2120840474206343371)、[charm](https://x.com/SpotGamma/status/2120979361490747824) |

## 后续走势：三套可以证伪的剧本

抓取结束时现货未开。已经写下来的锚是：标普收在 7,593.63，跌 0.34%；周五期货是标普 +0.07%、纳斯达克 100 -0.16%；英伟达收盘帖有 -4.3%、-4% 和将近 -7%，没有一个盘后新价格；WTI 结算 88.74 美元，布伦特结算 95.82 美元。

**辞职被当成不确定性的顶点，周四从 25,087.73 收回来的买盘还会在周五开盘后留住。** 触发器是 Gary 写的“辞职当天该买”，fundstrat 的“明天抄底、CUDA 还在”，Kobeissi 记下的散户三日 16 亿美元和周四头 30 分钟净买入 1.11 亿美元，以及收盘点位高于纳斯达克和标普的开盘点位。它失败的条件，是期货把 7,593.63 送回开盘的 7,559.87，同时英伟达离开 -4.3% 那一句、重新走向开盘的 -13% 或 -14%，或者价格走向 Bernstein 的 200 美元和 Melius 的 185 美元，而不是 unusual_whales 写的 187 美元正 gamma。

**周四的反弹被当成要卖掉的礼物，空头还在。** 触发器是线外的 Keith 在午盘告诉一家对冲基金：要淡化这波日内反弹；收盘时他仍把英伟达放在下跌趋势里，并写风险区间的下沿低得多。米内尔维尼早上把已经盈利的标普空头加了一倍。零对冲引 BTIG 的 Krinsky：英伟达的反弹是卖出的礼物，美元在突破：[淡化](https://x.com/KeithMcCullough/status/2120975048232288351)、[下跌趋势](https://x.com/KeithMcCullough/status/2120985091669447056)、[加空](https://x.com/markminervini/status/2120883843221573909)、[礼物](https://x.com/zerohedge/status/2121015293526802451)。它失败的条件，是标普站上 SpotGamma 写的 7,600 翻转线，并进入他收盘前标出的 7,625 到 7,605，同时英伟达守住 RedDog 写的 148 到 152 美元买盘、不再回到 148.80。

**油价和换帅各走各的，直到现货开盘才知道哪一张盖过另一张。** 触发器是结算 WTI 88.74 美元、布伦特 95.82 美元，特朗普说不需要协议，国际能源署却把四季度改成过剩。对面是 10 年期 5.10% 和 5.11%，以及 Ole 完全定价的 12 月加 25 个基点。Brooks 写的是不加息，而且他中午看到的“油价在跌”没有活到结算。它失败的条件，是布伦特离开 95.82 美元、回到 Gary 早上的 92 美元，同时指数期货仍停在 +0.07% 和 -0.16%；或者油价留在结算这一侧、英伟达却把 -4.3% 走成开盘的 -13%，那就是首席执行官的句子盖过了油。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周五开盘。它不决定仓位大小。抓取结束时，现货还没有开。

**开盘前只核对五样东西。** 期货是继续落在 First Squawk 09:57 的标普 +0.07%、纳斯达克 100 -0.16%，还是回到周四收盘的 7,593.63，或开盘的 7,559.87。英伟达是离开 -4.3% 和 -4% 的收盘帖，还是重新靠近 148.80 到 152 美元；200 美元和 185 美元仍是目标价，163 到 165 是盘中价，都不是同一个收盘。新云用的是盘前的 -20.1% 和 -13.6%，还是 Nebius 从 120 美元回到 128 美元的那一截。油是继续交易结算 88.74 美元和 95.82 美元，还是把《华尔街日报》那句“进一步下滑”收成一张新的供给标题。加息句子是停在 Ole 的“下个月 25 个基点、其后再两次”，还是 Brooks 的“不需要加息”，还是 RedDog 早上那句“12 月降息”。五样里，期货仍贴着平盘、英伟达不把 200 美元当成已经交易的价格、油价留在 95.82 这一侧、25 个基点仍只是 Ole 的句子而不是 Hammack 已经宣布的步骤，这些帖给出的默认顺序是：先看辞职有没有从“Kress 临时”变成新的永久人选或司法部结论，再决定 7,593.63 是不是还站得住。期货跌回 7,559.87、英伟达走向 185 到 200 美元、或者 5.11% 的 10 年期再往上走，默认顺序掉过头来：先处理首席执行官和收益率，再决定思科的 +5% 还剩多少。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：辞职是董事会的错误。盘中标普转绿时，英伟达抹掉超过一半跌幅并站上 163 美元。散户周一到周三买了 16 亿美元，周四头 30 分钟净买 1.11 亿美元。周五他仍写分手太早。
- First Squawk，线外：开盘标普 7,559.87、纳斯达克 25,087.73、道指 52,555.52。收盘标普 7,593.63、纳斯达克 25,362.36、道指 52,303.93。综述里英伟达 -4.3%。WTI 他没有单独再写一遍结算，布伦特结算 95.82 美元。周五期货标普 +0.07%、纳斯达克 100 -0.16%、道指 +0.11%。
- Gary，线外：辞职当天、不确定性最大的时候买英伟达。早盘标普 -0.3%、纳斯达克 100 -0.7%，布伦特 -1% 到 92 美元。他认为市场已经完全定价下个月加息。标普 2026 年每股收益他写成 369 美元、同比 +33%，20.6 倍市盈率，盈利收益率 4.8%，低于 10 年期国债。SpaceX 换股合并对特斯拉股东几乎没有意外之财。
- fundstrat：坏消息上见底，形容的是这一周。明天抄底。英伟达仍是最重要的公司。
- Nick Timiraos，线外：2027 年 10 月的会还在，但是没有政策行动；12 月的会提前到 11 月 16 到 17 日。
- Brooks，线外：不需要加息。油价冲击不是全面通胀。相关性破裂维持不久。他写“油价在跌”的时候，布伦特还没结算在 95.82 美元。
- Ole Hansen，线外：完全定价下个月加 25 个基点，其后六个月再加两次。SOFR 把明年 9 月的峰值定在 4.8%。黄金跌向 3,870 美元。商品指数今年至今 +26%，贵金属本周 -4%。
- RedDog，线外：早盘标普期货 -24 点时，标普 ETF 要守住 755 美元一带，枢轴阻力 762.50 美元。标普从 7346 反弹到 7635 之后，7571 是要守的位置。他当时写成市场在定价 12 月降息。稍后写反弹不等于修复，标普 ETF 看 755 美元，纳斯达克 100 ETF 看 683 美元，特斯拉必须守住 386 美元。英伟达 148 到 152 美元有人买到。
- 米内尔维尼：把已经盈利的标普空头加了一倍。纳斯达克出现跟随日，他还要看后面有没有派发。投资者情报多头从 42.6% 降到 37.0%，空头从 18.5% 升到 24.1%。他不认为这是投降。CoreWeave 周三收在 60.77 美元，仍比高点低大约 56%。
- Keith，线外：淡化日内反弹。英伟达维持下跌趋势。做空罗素 ETF、内存、他的宏观空头 PBD。做多低波 LVHI、反贝塔 BTAL 和美元。MEME ETF 他写成 -5.5%。超微维持下跌趋势。债券一个月前是空头，周四在选择性买固定收益。黄金仍是最差的大类资产。油在他早上的趋势系统里仍是空头，那是结算上涨之前。
- Detrick，线外：大多数股票在涨，像牛市。股票看跌/看涨比在他看来像上一次的买点。英伟达当周 -12%、SMH +8%，他写成轮动是牛市的生命线。
- SpotGamma，线外：标普 gamma 在 7,600 下方翻转，负 gamma 到 7,350。英伟达支撑仍只在 150 美元，低点 148.80。收盘前 7,625 到 7,605 有正 charm，那是问题不是预测。应用材料的期权定价过 7.1%。
- Sentimentrader，线外：11 月 11 日的读数是聪明钱 0.64，乐观；笨钱 0.51，中性。半导体 ETF 四个交易日反弹 17.8%，83% 的成分股在 10 日均线之上，只有 37% 在 200 日均线之上。纳斯达克 100 ETF 四个交易日涨 6.7%，仍比年内高点低 9% 以上；类似反弹之后一个月更高的次数是 33 次里 13 次：[聪明钱](https://x.com/sentimentrader/status/2120867988643684836)、[SOXX](https://x.com/sentimentrader/status/2120879315747520700)、[QQQ](https://x.com/sentimentrader/status/2121047569996603408)。
- Baird 不在这张单子里。今天写下目标价的是 Bernstein 的 200 美元、Melius 的 185 美元，以及其他券商从 186 到 515 的那一列。
- Dan Ives，经零对冲：没有黄仁勋，价值少 25%。这不是美元目标价。
- 克拉默：盘后说感觉比早上好。周五早上又说首席财务官曾想拦住过于激进的背书。Cerebras 和思科超预期，人工智能在英伟达以外仍然强。
- firstadopter，线外：十五年来最便宜。七位分析师降级是慌了。从日内低点上涨 12% 是他 16:13 的句子。
- Hanke：辞职后已经暴跌 8%，那是 15:11。11 月 11 日海峡是 1 艘对 67 艘。
- El-Erian：辞职只是更大问题的一章。16:29 的三大指数上涨没有留到收盘。10 年期 5.10%。欧元 1.1057，日元 159.89。英国三季度 GDP 环比 0.7%，是两年半最好，前值 0.5%，年率 1.9%：[GDP](https://x.com/elerianm/status/2120865579032576324)。
- Schiff：买黄金的跌。成屋销售是崩溃前的低点。比特币低于 2021 年 11 月。
- Bianco：10 年期四个交易日超过 25 个基点。Anthropic 6 倍认购让他问泡沫是不是没在破。
- 高盛的指数目标在 FinancialJuice，不在高盛主号：未来 12 个月标普看到 8700。全球人工智能投资从 2026 年的 1.1 万亿美元到 2027 年的 1.8 万亿美元。2027 年美国 GDP 2.4%，全球 2.8%：[8700](https://x.com/financialjuice/status/2120919557330157694)、[人工智能投资](https://x.com/financialjuice/status/2120918906097610850)、[2.4%](https://x.com/financialjuice/status/2120917756417552746)。First Squawk 把高盛的斯托克 600 十二个月目标从 695 改到 700，并把欧洲能源降到低配：[700](https://x.com/FirstSquawk/status/2121132408997351850)、[能源](https://x.com/FirstSquawk/status/2121132374218129885)。高盛主号这个窗口没有新的指数点位。
- Burry 的交易帖标题是“够了，$NVDA，SMH 对 SOXX”，正文在订阅通讯里，时间线没有给出点位：[帖](https://x.com/michaeljburry/status/2121031795676242379)。
- 彼得·布兰特：白银还没有见底的图形，杠杆期货没有理由持有：[帖](https://x.com/PeterLBrandt/status/2120957087924797906)。
- 方舟和 Cathie Wood 的账号这个窗口没有新的指数点位。德意志银行的时间线没有读到。

**财报和数据的顺序。** 先看周五期货有没有离开 +0.07% 和 -0.16%，再看英伟达是离开 -4.3% 还是靠近 148.80。然后才是美联储讲话和上午 10:30 的天然气库存。思科的 +5% 和应用材料的业绩已经在盘后。英伟达自己的财报是 17 日，不在今天。Anthropic 的 6 倍认购还没有定价。

**明确留在观察、不放进计划的东西。** 不把开盘的 7,559.87 和收盘的 7,593.63 取一个价格。不把纳斯达克综合指数的 -0.41% 写成纳斯达克 100 期货的 -1.4% 或 -0.16%。不把英伟达的 -4.3%、-4% 和将近 -7% 收成一个收盘，也不把 -13%、-14%、163 美元和 148.80 美元收成一天。不把 185、186、200、205、225、230、250、280、300、515 放进同一个目标。不把 25% 换成这些美元。不把 34%、25%、6% 和 Tim Cook 收成一张继任名单。不把 Kress 写成已经任命的永久首席执行官。不把“还没认定是间谍”写成“已经认定”或“已经洗清”。不把 Nebius 的 -8%、-10%、-15%、-17%、-20.1%、-21% 取一个跌幅。不把 120 美元和 128 美元写成收盘。不把思科的 +5% 写成应用材料的涨跌。不把 WTI 的 88.74 美元和布伦特的 95.82 美元对调，也不把早盘的 92 美元写成结算。不把 1 艘对 67 艘写成 10 月每天 1180 万桶。不把黄金的 3,866.08 美元写成结算。不把 5.10%、5.11%、4.8920% 和 5.441% 收成一个收益率。不把 25 个基点、两次追加、不需要加息和 12 月降息收成同一个会议。不把比特币的 71,000、70,000 和 68,000 取一个价。德意志银行的时间线没有读到。Cathie Wood 的账号没有新帖。美联储账号没有在帖文里写出 12 月的步长。

## 全站搜索里、排在这 100 个账号之外的讨论

搜索结果用来看讨论范围，不拿来改上面的收盘数字。讨论集中在黄仁勋该不该复职、董事会是不是在损害股东，而不是周四的点位。搜索“Nvidia CEO resign”和“Jensen Huang”时，靠前的帖是小账号的复述、复职猜测和招聘广告式的预测市场。一个大约 8.5 万粉的账号把现价写成大约 164 美元，并警告跌幅可能比看到的更大：[帖](https://x.com/0x_Discover/status/2121183753611493747)。164 美元和 unusual_whales 盘中的 164 美元是同一量级，但它不是收盘帖，不替换金融时报的 -4.3%。搜索里还有员工联名要求复职的转述，和 Kobeissi 引的 WIRED 内部帖是同一方向，粉丝数在截止线外。代币群和多语言段子出现在同一批搜索里，不进入价格表。搜索没有给出一张与 First Squawk 不同的周四收盘点位，所以 7,593.63、25,362.36 和 52,303.93 仍以他的收盘帖为准。

## 帖文索引

收盘和开盘：[开盘 7,559.87](https://x.com/FirstSquawk/status/2120887132659323356)、[标普收盘 7,593.63](https://x.com/FirstSquawk/status/2120985997983043681)、[周五期货 +0.07%](https://x.com/FirstSquawk/status/2121180640272154984)。

英伟达和利率：[辞职](https://x.com/FirstSquawk/status/2120877233443340526)、[收盘 -4.3%](https://x.com/FT/status/2120989286644224158)、[200 美元](https://x.com/DeItaone/status/2120848638142226876)、[10 年期 5.10%](https://x.com/elerianm/status/2120932564814770512)、[不加息](https://x.com/robin_j_brooks/status/2120897446616461347)。

油、黄金和思科：[WTI 88.74](https://x.com/financialjuice/status/2120962717188297098)、[布伦特 95.82](https://x.com/financialjuice/status/2120966210317947064)、[黄金 3,866.08](https://x.com/FirstSquawk/status/2120894318261223669)、[思科 +5%](https://x.com/CNBC/status/2120990002418971037)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-13 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 278 条、彭博商业账号 329 条、FinancialJuice 389 条、零对冲 139 条，是读穿窗口后的计数。德意志银行的 0 是读取失败。沃伦·巴菲特和 Downtown 的 0 是时间线早于窗口。达利欧的 1 条是原则帖，下一页没有读到。Charlie Bilello、Bill Ackman、Lyn Alden、美国财政部、马克·库班、摩根士丹利的 0，是窗口内帖文被接口标成回复或转发，或者没有新帖。线外的 First Squawk 是 361 条。保罗·克鲁格曼、Cathie Wood、BBC Business、markets、CNN Business、彭博主号、安德鲁·罗斯·索尔金、美国银行、TradingView、纽约时报商业、花旗、Hindenburg、Bill Gurley、SEC、economics、CNBC Now、摩根·豪泽尔、Nouriel、Carl Icahn 的 0，是窗口内没有计为原创的新帖。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,449,031 | 278 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,331,194 | 124 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,284,540 | 41 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,312,999 | 38 |
| 5 | [@business](https://x.com/business) | 10,497,620 | 329 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,575,432 | 0 |
| 7 | [@FT](https://x.com/FT) | 7,120,537 | 71 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,260,698 | 75 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,378,620 | 55 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,650,888 | 38 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,621,151 | 3 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,435,223 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,354,571 | 49 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,436,026 | 139 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,429,520 | 24 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,053,359 | 0 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 3,009,680 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,743,853 | 24 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,575,306 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,536,845 | 5 |
| 21 | [@chamath](https://x.com/chamath) | 2,494,112 | 5 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,439,807 | 11 |
| 23 | [@BW](https://x.com/BW) | 2,288,737 | 5 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,389 | 33 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,156,999 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,128,412 | 4 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,082,143 | 46 |
| 28 | [@markets](https://x.com/markets) | 2,049,965 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,975,902 | 77 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,798,016 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,780,056 | 8 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,772,202 | 24 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,712,224 | 9 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,701,711 | 11 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,305 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,621,376 | 30 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,604,585 | 7 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,540,696 | 46 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,513,887 | 2 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,473,201 | 19 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,454 | 4 |
| 42 | [@Bloomberg](https://x.com/Bloomberg) | 1,360,091 | 0 |
| 43 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,359,810 | 3 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,257,628 | 5 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,224,940 | 74 |
| 46 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,197,423 | 0 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,195,109 | 3 |
| 48 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,194,848 | 3 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,184,833 | 9 |
| 50 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,172,539 | 25 |
| 51 | [@nntaleb](https://x.com/nntaleb) | 1,167,739 | 1 |
| 52 | [@USTreasury](https://x.com/USTreasury) | 1,166,527 | 0 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,158,404 | 1 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,156,096 | 13 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,140,014 | 0 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,118,441 | 7 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,107,138 | 35 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,097,808 | 1 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,082,421 | 3 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,070,074 | 9 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,304 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,995 | 32 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,005,025 | 1 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 957,940 | 389 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 945,892 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 934,848 | 12 |
| 67 | [@tradingview](https://x.com/tradingview) | 909,375 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 895,342 | 19 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 891,962 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,587 | 17 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 874,763 | 0 |
| 72 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 869,478 | 14 |
| 73 | [@axios](https://x.com/axios) | 865,485 | 37 |
| 74 | [@steve_hanke](https://x.com/steve_hanke) | 862,135 | 22 |
| 75 | [@jpmorgan](https://x.com/jpmorgan) | 861,194 | 1 |
| 76 | [@Citi](https://x.com/Citi) | 853,114 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 847,521 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,589 | 2 |
| 79 | [@ecb](https://x.com/ecb) | 831,427 | 3 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,666 | 2 |
| 81 | [@bgurley](https://x.com/bgurley) | 812,179 | 0 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,209 | 0 |
| 83 | [@economics](https://x.com/economics) | 806,062 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 790,034 | 2 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,780 | 5 |
| 86 | [@markminervini](https://x.com/markminervini) | 777,262 | 5 |
| 87 | [@leadlagreport](https://x.com/leadlagreport) | 769,078 | 20 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 760,114 | 0 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,402 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 743,866 | 0 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 719,090 | 27 |
| 92 | [@Nouriel](https://x.com/Nouriel) | 714,909 | 0 |
| 93 | [@CMEGroup](https://x.com/CMEGroup) | 712,415 | 4 |
| 94 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 674,683 | 8 |
| 95 | [@fundstrat](https://x.com/fundstrat) | 672,549 | 6 |
| 96 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,436 | 4 |
| 97 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 647,204 | 0 |
| 98 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,509 | 0 |
| 99 | [@LukeGromen](https://x.com/LukeGromen) | 636,202 | 4 |
| 100 | [@EricBalchunas](https://x.com/EricBalchunas) | 625,861 | 1 |
