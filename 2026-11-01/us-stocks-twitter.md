# 美股 Twitter 观点日报 · 2026-11-01

周日现货不开市，到抓取结束时美股期货的周日晚场也还没开。这个窗口里没有新的现货收盘。帖文在交易三件事：人工智能股票和“去掉人工智能的标普”已经分成两张图；霍尔木兹的通航口径互相打架，热战被写到中期选举之后；投资级发债和垃圾债到期墙在变大，债券账户在躲选举、把目光放在本周的再融资日程。

下面每一条归纳都附有帖文链接。周六的周末报价、年内涨跌和十月的行业差按发帖原文分开。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-11-01**。触发时刻约 10:01 UTC，时间线补抓到 **约 10:17 UTC（北京时间 18:17，美东 5:17）**。美国夏令时已在周日凌晨结束，这个 5:17 是东部标准时间。美股现货周日不开。股指期货的周日晚场要到美东 18:00 才开，抓取结束时还没开，所以下文没有周日晚间的期货新价。
- 观察窗口从 **2026-10-31 12:18 UTC** 接到抓取结束，也就是上一份日报写明的截止之后。它覆盖美东周六白天、周六夜间和美东周日清晨。美东周五的现货收盘已经写在 10 月 31 日那份日报里。
- X 的官方连接器这次仍然没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是帖文自带的 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。抓取结束时美国趋势是 MANIAC FINAL MOMENT、#MLBS7Spoilers、Good Sunday、#BornToBeNuNewConcertD2、#Bharat_BulletTrain、Joe Lacob。里面没有美股话题。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数落在前 100 之外的市场账号。
- 不存在官方的“美股 Top 100”。这次试了 **496** 个候选，成功读到粉丝数的有 **427** 个。排序时拿掉加密货币账号、综合新闻主号、世界经济论坛、科技战略通讯、科技风投和创始人、大型科技公司首席执行官、竞选和政治账号、公司产品品牌，以及金融时报的重复账号。用来排序的账号是 **362** 个，截止在 Luke Gromen（约 63.7 万粉）。Steve Hanke 这次按粉丝数排进前 100，Eric Balchunas 落到第 101。First Squawk、Gary Black、Cboe、Barchart、Jeffrey Gundlach、Earnings Whispers、Mad Money、Aswath Damodaran、Carl Quintanilla、美银新闻、LiveSquawk、瑞银、Nick Timiraos、日经亚洲、Keith McCullough、Hedgeye、The Stalwart、MacroAlf、Robin Brooks、Javier Blas、Bespoke、SpotGamma、The Transcript、firstadopter、Ryan Detrick、Andy Constan、Yardeni、RenMac 落在线外，引用时会写明。排序不代表预测准确度。
- 100 个账号里，**54 个**在窗口内有按帖文链接去重后、且接口没有标成回复或转发的原创帖。路透读穿窗口，126 条。彭博商业账号 67 条。《华尔街日报》69 条。《金融时报》24 条。FinancialJuice 52 条。零对冲 39 条。unusual_whales 23 条。线外的 First Squawk 读穿窗口，138 条。德意志银行和 Daniel Newman 的时间线返回失败，表里的 0 不是确认沉默。沃伦·巴菲特的可见时间线停在 2016 年，彭博经济停在 2026 年 7 月，彭博主号停在 10 月 12 日，彭博 markets 停在 2026 年 7 月，BBC Business 停在 2024 年，CNN Business 停在 2021 年，纽约时报商业停在 2024 年，TradingView 停在 2026 年 6 月，CNBC Now 停在 2024 年。这几家的 0 同样不能当成确认沉默。

## 周末没有新的现货收盘

周五的非官方收盘仍是上一份日报里的那一组：纳斯达克综合指数 25438.40、标普 7578.14、道指 51763.41。这个窗口没有新的收盘帖去替换它们。

周六下午有一张周末报价，不是收盘。First Squawk 15:05 UTC 写：DAX 25806，涨 0.10%；道指 51821，涨 0.06%；纳斯达克 28447，涨 0.16%；富时 10721，跌 0.01%；恒生 23398，涨 0.02%；欧元美元 11150，跌 0.08%；黄金 3885，涨 0.25%；美油 10258，涨 0.22%：[帖](https://x.com/FirstSquawk/status/2116547100666384737)。28447 是这张报价上的“纳斯达克”。25438.40 是上一份日报里的综合指数收盘。10258 按帖面保留，不换算成周五的原油结算价。3885 是这张报价上的黄金，和后文“低于 4000”是两句。

同一窗口里的年内成绩是另一张表。Investing.com 周六晚：道指年内涨 7.6%，标普涨 10.2%，纳斯达克涨 8.3%，罗素 2000 涨 12.8%，VIX 涨 29.9%：[帖](https://x.com/Investingcom/status/2116650231014338846)。这是 2026 年以来，不是周六这一天。

Investing.com 周六中午的标题仍是“全球股市跌着结束这一周”，点名英特尔和亚马逊的财报加深了对人工智能交易的怀疑：[帖](https://x.com/Investingcom/status/2116509589365575813)。CNBC 周六重发英特尔跌 29%、分析师提醒不要抄底：[帖](https://x.com/CNBC/status/2116517464141856872)。29% 是这条周六标题里的数字。上一份日报里还有 28.5% 的另一张收盘帖，这里不合并。

## 观点分成四组

### 1. 去掉人工智能的标普创新高，科技财报日仍在拖后腿

Kobeissi 周六把行情写成“隐蔽熊市”已经完全展开：纳斯达克 100 在 25 天里抹掉 4 万亿美元，周五“不含人工智能的标普 500”创下纪录高点；10 月人工智能股票跌超过 13%，不含人工智能的标普涨 8%：[帖](https://x.com/KobeissiLetter/status/2116567209367445876)。同一串帖的下一条写，若没有这场全球能源危机，标普会在 8500 点上方；他预期 11 月会多事：[帖](https://x.com/KobeissiLetter/status/2116567243245121613)。4 万亿美元、跌 13%、涨 8%、8500，都是这一串帖里的句子。

财报次日的行业差是另一条。信息科技股 10 月在财报后第一个交易日平均跌 1.2%，11 个行业里最弱；能源平均跌 0.3%，必需消费跌 0.2%。8 个行业为正。可选消费平均涨 1.9%，医疗涨 1.5%，工业涨 1.2%。个股平均涨 0.6%。他的结论是科技在偏离市场的其余部分：[帖](https://x.com/KobeissiLetter/status/2116542276738355535)。

线外的 Yardeni 用的是从 10 月高点算起的另一段：等权标普涨 4.9%，市值加权指数跌 3.1%，拖累来自此前领涨的人工智能股票：[帖](https://x.com/yardeni/status/2116605997837881478)。4.9% 和 3.1% 不要换成 Kobeissi 的 8% 和 13%。

线外的 Ryan Detrick 写，科技一旦感冒，主要指数就会吃力，表面之下仍有机会：[帖](https://x.com/RyanDetrick/status/2116559730806059230)。他另写，7 月底配置一些低波动当时很少有人当回事；Todd Sohn 的做法是把它和动量配在一起，他们的模型全年都留着这对：[帖](https://x.com/RyanDetrick/status/2116540295185621156)。

S. Joseph Burns 把周五写成他见过最差的科技日之一，他经历过互联网泡沫和 2008 年秋天：[帖](https://x.com/SJosephBurns/status/2116676810922766400)。同一小时他写周五从股市抹掉 1.8 万亿美元市值：[帖](https://x.com/SJosephBurns/status/2116675992853123097)。1.8 万亿是他的周五全市场句子。4 万亿是 Kobeissi 的纳斯达克 100、25 天句子。

Anthony Pompliano 的方向相反：股市在跌，同时全球最大的那些公司在报出更多收入和更好的利润率，市场最终会追上基本面：[帖](https://x.com/APompliano/status/2116677583878422805)。El-Erian 把周六的悲观报道写成跟着价格走，并问这种突然转向会不会做过了头：[帖](https://x.com/elerianm/status/2116563633216122955)。他的周报把过去五天写成科技财报、分化和央行，美国有韧性的增长数据是底下的缓冲；向前看是中期选举、就业和其他数据，以及央行官员的讲话：[帖](https://x.com/elerianm/status/2116626131906334784)。

Charlie Bilello 的年内资产表是另一组：2026 年到周六为止，比特币跌 11.7%，黄金跌 10.2%，是主要资产里最差的两个，他写成以前任何一个日历年都没同时见过：[帖](https://x.com/charliebilello/status/2116594862942568958)。美国本轮扩张已经 77 个月，1949 年以来平均 67 个月，最长 128 个月，最短 12 个月：[帖](https://x.com/charliebilello/status/2116597357215433093)。

线外的 Barchart 周日凌晨写，中国股市跑输标普的幅度是历史上最大的：[帖](https://x.com/Barchart/status/2116739505671852135)。帖里没有给出那个幅度的数字。

### 2. 霍尔木兹同时有“已经恢复”“基本关闭”和“选举后再打”

财政部长 Scott Bessent 周六写，霍尔木兹的通行量已经回到冲突前的水平，只是少了伊朗的桶；世界离得开伊朗的油，伊朗离不了石油出口：[帖](https://x.com/SecScottBessent/status/2116581781562368057)。

线外的 Javier Blas 用的是 10 月 1 日到 26 日的中东原油出口，不含伊朗：10 月有望高于 9 月，月均已经非常接近战前，在战前的 90% 以上。油轮和设施被打了几周，伊朗及其代理没有截住这股流量。他接着写，若 11 月 3 日之后战争重启，这些恢复可能全部消失。成品油和燃料油仍低迷，环比几乎没变，大约停在战前的 60% 以上：[帖](https://x.com/JavierBlas/status/2116571020857581818)。他的另一张图是美国汽油：除了 2020 年疫情，今年夏天（7 月和 8 月平均）的消费是大约 25 年来最弱的：[帖](https://x.com/JavierBlas/status/2116602101434642915)。

Steve Hanke 的计数是单日船次。他写去年 10 月 30 日有 46 艘油轮过海峡，今年 10 月 30 日是 1 艘，并写成海峡实际上仍然关闭：[帖](https://x.com/steve_hanke/status/2116619969119297578)。更早一条引伊斯兰革命卫队：四艘油轮在“未经许可的航线”上触雷起火，海峡仍然危险、功能上关闭：[帖](https://x.com/steve_hanke/status/2116559571552469349)。90% 以上的月均出口、回到冲突前的通行量、10 月 30 日的 1 艘，是三套口径。

现场消息按时间留着。First Squawk 引阿拉格齐对半岛电视台：调解方提出了核问题方案，德黑兰在研究；重新开放霍尔木兹，桌上只有伊朗自己的方案：[帖](https://x.com/FirstSquawk/status/2116519354431050231)。他的条件包括取消伊斯兰堡谅解备忘录之后加的制裁、减少美国在该地区的兵力，并要求承认和阿曼商定的新航道、关掉其他航道：[帖](https://x.com/FirstSquawk/status/2116519868967330076)。按德黑兰的条件重开海峡，会被写成给恢复对华盛顿的谈判开门：[帖](https://x.com/DeItaone/status/2116520181929275549)。伊朗安全负责人 Rezaei 的句子是，在德黑兰的条件满足之前，海峡保持关闭：[帖](https://x.com/FirstSquawk/status/2116707170008150156)。伊朗海军经国家媒体说，一艘油轮在海峡东部禁区内触雷起火：[帖](https://x.com/FirstSquawk/status/2116596708981494217)。周日另有伊朗议员呼吁把退出《不扩散核武器条约》当成认真的优先事项：[帖](https://x.com/FirstSquawk/status/2116806878496002352)。

热战的时间被放在选举之后。Kobeissi 引《华尔街日报》：特朗普周六与内塔尼亚胡通话，美国准备恢复轰炸伊朗；政府已警告海湾国家，为 11 月 3 日中期选举之后一场“短而激烈”的军事行动做准备。帖里写伊朗战争已经第 245 天：[帖](https://x.com/KobeissiLetter/status/2116687632826605694)。路透的标题是伊朗特使会见卡塔尔调解人，中期选举之后美国打击的威胁仍在：[帖](https://x.com/Reuters/status/2116555858762965093)。

线外的 Robin Brooks 把市场写成已经在给热战回归定价。过去几周的一个结构断裂是，油价上涨的同时美国 10 年期收益率下降；他归因于欧洲的债务麻烦，避险资金流向美债：[帖](https://x.com/robin_j_brooks/status/2116507185387561305)。周六他写，这就是白银周五跌了将近 6% 的原因：[帖](https://x.com/robin_j_brooks/status/2116548358021992558)。周日清晨他写，黄金周五陡跌、回到 4000 美元下方；开战以来黄金和油价负相关，布伦特涨 10% 对应黄金跌 4%；热战回归会再压一压黄金，但下行有限：[帖](https://x.com/robin_j_brooks/status/2116778807499821175)。3885 是 First Squawk 周六那张报价。4000 下方是 Brooks 周日的框架。白银将近 6% 是他写的周五跌幅。

Hanke 的油价句子来自国际货币基金组织：由于对伊朗的战争，油价可能从 2026 年末到 2027 年初到每桶 130 美元，亚洲和欧洲的天然气价格 2027 年可能比基金组织的基准高 26%。他的结论是继续做多石油和天然气：[帖](https://x.com/steve_hanke/status/2116705533117776145)。130 美元是这条基金组织路径，不是周六报价上的 10258。他另引《华尔街日报》，关税加上对伊朗的战争给美国新建住房增加了大约 8200 美元成本：[帖](https://x.com/steve_hanke/status/2116686658808762408)。CNBC 的周六标题是，特朗普承诺过削减能源成本，汽油、柴油和航空煤油反而都涨了：[帖](https://x.com/CNBC/status/2116513557407822037)。

线外的 firstadopter 把 110 美元以上的油价写成跑道的尽头：金融条件在变紧，信用和股权融资可能干涸，即便回报期本身还说得通；他要求一个可信的伊朗战争解决方案，否则就是一次自己造成的衰退：[帖](https://x.com/firstadopter/status/2116520245741355336)。他周六贴了 10 月 28 日主席 Kevin Warsh 的话：利率会钻进缝里，几乎影响一切；9 月初以来，科技内部和外部的信用利差有的走阔、有的裂开，金融条件有所收紧，但不是全面大幅收紧；利率对这轮人工智能投资是起作用的：[帖](https://x.com/firstadopter/status/2116552705887932561)。

线外的 Keith McCullough 把因子篮子写成：做多石油和能源股是好的，离开人工智能泡沫股、比特币以及相关股票更好：[帖](https://x.com/KeithMcCullough/status/2116533627156902043)。他另写，CNBC 那类散户周五只跌了 5.6%：[帖](https://x.com/KeithMcCullough/status/2116533103565193353)。5.6% 是他的散户句子，不是指数收盘。

### 3. 11 月要发的投资级债是纪录，垃圾债收益率写成 8%

Kobeissi 引的 11 月供给还是预期。美国投资级公司债销售预计同比增加 370 亿美元，增 27%，到 1750 亿美元，是有纪录以来最高的 11 月；相对 2024 年 11 月增加 770 亿美元，增 77%；2025 年之前的五年均值是 1040 亿美元。10 月大约 1000 亿美元。年初至今投资级发行到了纪录的 1.76 万亿美元，已经超过 2025 年全年的 1.75 万亿美元。全球投资级市场里和人工智能有关的公司债 2026 年已经超过 3000 亿美元，几乎是 2025 年全年的 3 倍：[帖](https://x.com/KobeissiLetter/status/2116614948071539134)。

到期墙是另一条。未来 5 年大约 1.9 万亿美元的美国投机级公司债和贷款到期，其中 4380 亿美元在 2028 年底之前。2020、2021、2022 年这个五年数字在 1.4 万亿到 1.5 万亿美元。两年内到期的垃圾级债务同比增 31%。到 2031 年还有 1.6 万亿美元投资级公司债到期。公开交易的美国垃圾债有效收益率过去 12 个月上升 150 个基点，到 8.0%：[帖](https://x.com/KobeissiLetter/status/2116647408465563761)。

储蓄率被他写成已经下来了。9 月个人储蓄率降 0.2 个百分点到 4.2%，2022 年 10 月以来最低；2024 年 1 月以来降了 3.4 个百分点，低于疫情前五年均值 6.2%。个人收入同比增 4.1%，个人消费支出同比增 6.3%：[帖](https://x.com/KobeissiLetter/status/2116630555135517067)。4.2%、4.1%、6.3% 是这三条序列。

信用分化有三张帖。El-Erian 写科技信用的利差在拉开，自由现金流差的名字和其余名字被区别定价，相对价值交易因此出现：[帖](https://x.com/elerianm/status/2116526579232702587)。线外的 Carl Quintanilla 引 FedWatch：自由现金流差的公司信用违约互换飙升，现金多的资产负债表相对还被护着，流动性成了市场最贵的资产：[帖](https://x.com/carlquintanilla/status/2116572580349972957)。线外的 Danielle DiMartino Booth 写信用永远在核心；Arini Capital Management 这个月亏损之后，PIMCO 和橡树给它的一些高收益债持仓出了价：[帖](https://x.com/DiMartinoBooth/status/2116514754542121024)。

利率日程被放在选举旁边，而不是被选举取代。《金融时报》周日的标题是，债券投资者在旁观“多年来最关键”的美国中期选举：[帖](https://x.com/FT/status/2116766641308524667)。线外的 Andy Constan 写，本周的再融资日程（QRA）比选举更重要：[帖](https://x.com/dampedspring/status/2116584846084730984)。线外的 RenMac 写，障碍利率回来了，TINA 死了，权益这边几乎还没注意到：[帖](https://x.com/RenMacLLC/status/2116591155399868703)。他们的通胀保值债句子是：相对过去五年，在这个原油价位上 TIPS 处于第 6 百分位的低位；反过来说很弱，因为 2.34% 的盈亏平衡通胀曾经和 59 美元到 112 美元的原油共存：[帖](https://x.com/RenMacLLC/status/2116508777784742337)。2.34% 是这条盈亏平衡句子，8.0% 是垃圾债有效收益率。

线外的 Yardeni 把下一周写成就业、美联储讲话和中期选举挤在一起，他们在等强于共识的非农：[帖](https://x.com/yardeni/status/2116618678007431343)。帖里没有写出那个共识数字。

unusual_whales 有一条和储蓄率无关的利率：11 月 1 日到明年 4 月 30 日，新买的 I 系列储蓄债年利率 5.51%，此前到 10 月 31 日的购买利率是 4.26%：[帖](https://x.com/unusual_whales/status/2116610657856393527)。

Michael Gayed 写股票估值被拉到此前只见过两次的水平，股票被定价在完美情景时，信用的风险很大：[帖](https://x.com/leadlagreport/status/2116546610729451993)。这是他的估值句子。同一账号窗口里大量帖在推销自己的信用轮动基金，那些句子不放进下面的计划。

### 4. OpenAI 的年内经常性收入被写成 500 亿美元，币安开始恢复提现

融资数字按账号留着。unusual_whales：这一轮把 OpenAI 估在 1.25 万亿美元，低于此前瞄准的 1.4 万亿美元；公司此前想按那个更高估值筹集 300 亿美元。帖里同时写，OpenAI 称经常性收入已经到 500 亿美元，年底目标 700 亿美元：[帖](https://x.com/unusual_whales/status/2116595662779462054)。CNBC 的标题是筹集目标下调，现在这一轮最多寻求 200 亿美元：[帖](https://x.com/CNBC/status/2116621770811674986)。零对冲的标题是目标砍掉 100 亿美元，几乎算一轮降价融资：[帖](https://x.com/zerohedge/status/2116552135089242282)。现在这一轮的“最多 200 亿美元”和“1.25 万亿美元”不要写成还在寻求 300 亿美元。500 亿和 700 亿是经常性收入，不是融资额。

Anthropic 没有一张公司公告写上市日。StockMKTNewz 写，11 月 20 日目前是上市最可能的一天，11 月 19 日和“11 月不上市”并列第二：[帖](https://x.com/StockMKTNewz/status/2116609121281790212)。这是他的排序。《华尔街日报》写 Anthropic 和其他热门科技公司一样，用把创始人控制权留住的股权结构上市：[帖](https://x.com/WSJ/status/2116682250385326250)。零对冲的标题是 Steve Eisman 认为 Anthropic 在藏东西：[帖](https://x.com/zerohedge/status/2116606239308128391)。彭博周日写 DeepSeek 放出更自主的编程代理原型，要对着 Anthropic 的 Claude Code：[帖](https://x.com/business/status/2116754642222616835)。

币安的金额有两个写法。Kobeissi：联邦调查局宣布朝鲜是 63 亿美元币安被盗案的幕后，这是史上最大黑客案；朝鲜此前还被归到去年 Bybit 的 15 亿美元和 2022 年的 6.2 亿美元：[帖](https://x.com/KobeissiLetter/status/2116669713430282667)。路透的标题是联邦调查局把超过 60 亿美元的盗窃联系到朝鲜：[帖](https://x.com/Reuters/status/2116648956197220612)。63 亿和“超过 60 亿”按原帖留着。

补偿和提现按时间留着。DeItaone 周六：被盗资产已补上 90%：[帖](https://x.com/DeItaone/status/2116540319122518312)。公司称将自己吸收损失，并仍按原来说法在周日 2026-11-01 重开提现：[帖](https://x.com/DeItaone/status/2116540825853472908)。彭博周日 05:10 UTC 写成将在周日分阶段恢复提现：[帖](https://x.com/business/status/2116759670010302467)。路透 07:00 UTC 的标题是，补上 63 亿美元被盗资金的大部分之后，比特币提现已经恢复：[帖](https://x.com/Reuters/status/2116787463465074766)。《金融时报》09:58 UTC 的标题是，63 亿美元被盗之后客户提现重新开始：[帖](https://x.com/FT/status/2116832325598150761)。“将在周日恢复”“比特币提现已经恢复”“客户提现重新开始”是三张先后发出的标题。

## 要盯住的五件事

1. **25438.40 仍是上一份日报的综合指数收盘。** 这个窗口没有新的现货收盘。周六报价上的纳斯达克是 28447，涨 0.16%；道指是 51821，涨 0.06%。年内标普涨 10.2%，纳斯达克涨 8.3%。Kobeissi 的 25 天抹掉 4 万亿美元、10 月人工智能股票跌超过 13%、不含人工智能的标普涨 8% 并在周五创高，是第三张图。Yardeni 从 10 月高点算，等权涨 4.9%，市值加权跌 3.1%。
2. **霍尔木兹有三套流量口径。** Bessent 写通行量回到冲突前、只是少了伊朗的桶。Blas 写 10 月 1 日到 26 日不含伊朗的原油出口高于 9 月、月均超过战前的 90%，成品油大约停在战前的 60% 以上，并写 11 月 3 日之后若重启战争，这些恢复可能消失。Hanke 写 10 月 30 日只有 1 艘油轮，相对去年同日 46 艘。阿拉格齐要求按伊朗方案重开，Rezaei 写条件满足前保持关闭。Kobeissi 引的战役时间是 11 月 3 日中期选举之后。
3. **黄金 3885 和“4000 下方”不要合成一个新价。** 3885、涨 0.25% 是周六报价。Brooks 周日写黄金回到 4000 下方，布伦特涨 10% 对应黄金跌 4%，下行有限。白银将近 6% 是他写的周五跌幅。Bilello 的黄金跌 10.2% 是 2026 年以来。Hanke 的 130 美元是基金组织路径上的油价。周六报价上的美油是 10258。firstadopter 把 110 美元以上写成跑道尽头。
4. **11 月投资级发行预期是 1750 亿美元。** 年初至今 1.76 万亿美元。人工智能相关投资级债超过 3000 亿美元。垃圾债有效收益率 8.0%。未来五年投机级到期大约 1.9 万亿美元。9 月储蓄率 4.2%。I 债新利率 5.51%，旧的购买利率 4.26%。债券投资者被《金融时报》写成在旁观选举。Constan 把本周再融资日程写成比选举更重要。
5. **OpenAI 这一轮是最多 200 亿美元、估值 1.25 万亿美元。** 经常性收入 500 亿美元、年底目标 700 亿美元是另一句。Anthropic 的 11 月 20 日是 StockMKTNewz 的可能性排序。《华尔街日报》写的是创始人控制权还在的上市结构。币安是 63 亿美元或“超过 60 亿美元”，周日早上的标题已经写到提现恢复。抓取结束时，El-Erian 和 Yardeni 点名的就业数据、美联储讲话都还没有新的公布值。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、价格或事件的名字。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 两张指数 | 标普、纳斯达克 100 | 不含人工智能的标普周五创纪录高点，10 月涨 8%。人工智能股票 10 月跌超过 13%。纳斯达克 100 在 25 天里抹掉 4 万亿美元。没有能源危机的话标普会在 8500 上方 | [8% 与 13%](https://x.com/KobeissiLetter/status/2116567209367445876)、[8500](https://x.com/KobeissiLetter/status/2116567243245121613) |
| 等权和低波动 | 等权标普、低波动 | 从 10 月高点算，等权涨 4.9%，市值加权跌 3.1%。低波动和动量的配对被写成全年留在模型里。科技感冒时指数吃力，表面之下另有机会 | [等权](https://x.com/yardeni/status/2116605997837881478)、[低波动](https://x.com/RyanDetrick/status/2116540295185621156) |
| 财报次日 | 科技、可选消费、医疗 | 科技财报后第一天平均跌 1.2%。可选消费涨 1.9%，医疗涨 1.5%，工业涨 1.2%。个股平均涨 0.6% | [行业](https://x.com/KobeissiLetter/status/2116542276738355535) |
| 仍在被罚的标题 | INTC | 周六标题仍是跌 29%，并提醒不要抄底。芯片短缺被一条对冲基金引文写成可能是幻觉 | [29%](https://x.com/CNBC/status/2116517464141856872)、[短缺](https://x.com/carlquintanilla/status/2116617869723340948) |
| 云和模型 | AMZN | 过去 12 个月 AWS 收入 1610 亿美元，高于标普里 476 家公司的收入。首席执行官说未来两到三年可能有六到八个模型足以覆盖 95% 以上的企业负载 | [1610 亿](https://x.com/charliebilello/status/2116601170055549390)、[模型](https://x.com/TheTranscript_/status/2116564605367709847) |
| 估值句子没有倍数 | NVDA | 被写成人工智能浪潮开始以来最便宜的估值，帖里没有给出倍数。SpaceX 两个新集群大约再上 350 亿美元以上的 GPU、约 42 万颗 GB300，时间是 11 月末和 12 月。另一条播客观点是英伟达比礼来更容易被颠覆 | [估值](https://x.com/TrendSpider/status/2116595179117326744)、[GPU](https://x.com/SawyerMerritt/status/2116592175823642670)、[礼来](https://x.com/APompliano/status/2116608090401542213) |
| 图表位 | AAPL、TSLA、NFLX | 苹果被写成盯着 400 美元，并且刚结束“一年多来第一次”作为全球市值最大公司的一周。特斯拉被写成摆脱 2026 年的下降趋势。奈飞较高点跌了超过 50%，并出现看涨背离 | [400](https://x.com/TrendSpider/status/2116613680037081449)、[市值](https://x.com/StockMKTNewz/status/2116580873550389377)、[奈飞](https://x.com/TrendSpider/status/2116557055519502591) |
| 资本开支还在 | GOOGL、META | 谷歌云说把 TPU 放到第三方和客户机房，可以少预建自己的设施。首席财务官说基础设施和 TPU 库存会挤压自由现金流，同时投入资本回报率仍高于资本成本。若 Alphabet、亚马逊或 Meta 再跌 50%，帖中的问题是人工智能开支还会不会维持。Meta 的人形机器人原型是另一条。标普负面展望周六仍有通讯社标题 | [TPU](https://x.com/TheTranscript_/status/2116636345426903102)、[自由现金流](https://x.com/TheTranscript_/status/2116681635651522734)、[再跌 50%](https://x.com/carlquintanilla/status/2116628358444490913) |
| 卖铲的人 | GNRC、三星 HBM、BX | Generac 数据中心发电机积压约 45 亿美元，和亚马逊的长期协议里 2027 与 2028 年合计交付 24 亿美元，90 天里积压将近变成三倍。三星 2027 年 HBM 产量按约定目标价已经售罄。黑石 1.4 万亿美元资产里大约 7% 和人工智能有关 | [发电机](https://x.com/TheTranscript_/status/2116720122878362096)、[HBM](https://x.com/TheTranscript_/status/2116579261494735135)、[黑石](https://x.com/TheTranscript_/status/2116591034297983444) |
| 支付网络 | V、MA | Visa 预计全年调整后净收入低双位数增长，二季度是增速低点。万事达预计 2026 年净收入增速留在低双位数区间的高端 | [两家](https://x.com/TheTranscript_/status/2116538195307552942) |
| 能源多头 | XOM、CVX、SHEL、COP、原油 | 大型石油公司股东被写成是高油价里唯一在笑的人。Keith 的多头是石油和能源股。Hanke 写继续做多石油和天然气。韩国 10 月出口被写成维持强增长，芯片景气还在推动 | [石油股](https://x.com/TrendSpider/status/2116539432912220448)、[因子](https://x.com/KeithMcCullough/status/2116533627156902043)、[韩国](https://x.com/business/status/2116698016862048385) |
| 贵金属 | 黄金、白银 | 周六报价黄金 3885。Brooks 写回到 4000 下方，下行有限。白银周五将近跌 6%。Tavi Costa 写 2011 年白银上涨时产量大增，这次供应反应缺席，剧烈回调不是周期结束 | [4000](https://x.com/robin_j_brooks/status/2116778807499821175)、[白银](https://x.com/TaviCosta/status/2116642668818403508) |
| 融资与上市说法 | OpenAI、Anthropic | 最多 200 亿美元，估值 1.25 万亿美元。经常性收入 500 亿美元，年底目标 700 亿美元。11 月 20 日是可能性排序，不是公司公告 | [500 亿](https://x.com/unusual_whales/status/2116595662779462054)、[200 亿](https://x.com/CNBC/status/2116621770811674986) |

## 后续走势：三套可以证伪的剧本

帖文没有给周一的收盘点位。抓取结束时周日晚场期货还没开。周五写下来的现货收盘仍是上一份日报里的标普 7578.14、纳斯达克综合指数 25438.40、道指 51763.41。下面三套的顺序，以“不含人工智能的标普”被写成周五创新高、霍尔木兹的三套口径还没合成、11 月投资级发行被写成 1750 亿美元为前提。

**分化留在指数里面，8500 只作为没有能源危机时的对照。** 触发器是不含人工智能的标普守住 Kobeissi 写的纪录高点，等权相对市值加权维持 Yardeni 的那张 4.9% 对跌 3.1%，医疗和可选消费继续站在财报次日平均上涨的那一组。这条路径上，市场交易的是个股平均涨 0.6%、AWS 过去 12 个月 1610 亿美元、Pompliano 说的收入和利润率还在变好。它失败的条件，是周一能源冲击把 Kobeissi 自己写的“没有能源危机则标普在 8500 上方”倒过来，或者科技财报次日平均跌 1.2% 扩散到已经在涨的那 8 个行业。

**选举之后的热战定价压过“通行量已经恢复”。** 触发器已经写在周六到周日的帖里：Kobeissi 引的“短而激烈”放在 11 月 3 日之后，Blas 写战争若在 11 月 3 日之后重启，原油出口的恢复可能消失。Brooks 的搭配是油价向上、黄金再跌一截但下行有限，10 年期可以在油价上涨时下降。Hanke 站在做多石油和天然气、以及 130 美元的基金组织路径上。Keith 的多头是石油和能源股。这条路径失败的条件，是阿拉格齐写的“按德黑兰条件重开、然后恢复和华盛顿谈话”被交易成通航，Bessent 的“世界离得开伊朗的油”压过 Rezaei 的“条件满足前关闭”，并且黄金按 Brooks 自己的后半句、下行有限之后不再跟随油价下跌。

**选举被债券账户绕开，再融资日程和 8% 的垃圾债收益率先被定价。** 触发器是《金融时报》写债券投资者旁观这场中期选举，同时 Constan 把本周再融资日程写成比选举更重要，Kobeissi 的 11 月 1750 亿美元投资级发行和 8.0% 的垃圾债收益率还在桌上。Quintanilla 把流动性写成最贵的资产，自由现金流差的信用违约互换已经飙升。它失败的条件，是 Yardeni 等的“强于共识的非农”加上 El-Erian 写的增长缓冲，让权益这边开始注意到 RenMac 说的“TINA 已死”，或者现金多的资产负债表把利差重新压回去。El-Erian 自己也问过，周六的悲观会不会做过头。

另有一条白银的供应句子，不并进上面三套。Tavi Costa 写 2011 年的银价高点伴随产量大增，这次供应反应缺席，剧烈回调不是周期结束：[帖](https://x.com/TaviCosta/status/2116642668818403508)。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周一开盘和周二选举。它不决定仓位大小。周日现货不开市。抓取结束时，美东 18:00 的期货晚场还没开始。

**开盘前只核对五样东西。** 不含人工智能的标普还在不在周五那张纪录高点上，等权还在不在相对市值加权正的那一侧；霍尔木兹交易的是 Bessent 的“通行量已恢复”、Blas 的“原油超过战前 90%”，还是 Hanke 的“10 月 30 日只有 1 艘”；黄金是停在周六报价的 3885 附近，还是按 Brooks 的“10% 油价对 4% 金价”继续跟油价反向走；10 年期是继续 Brooks 写的“油价涨、收益率跌”，还是开始反映 1750 亿美元的 11 月投资级供给和 8% 的垃圾债收益率；科技是继续财报次日平均跌 1.2%，还是按 Pompliano 的收入和利润率被买回去。五样里油价叙事留在战争重启、垃圾债收益率留在 8%、科技继续偏离其余行业，这些帖给出的默认顺序是人工智能信用和已经在跌的半导体，低于石油、能源股、医疗和可选消费。通航谈判被当成真的、等权继续强于市值加权、亚马逊按 AWS 的 1610 亿美元被买，默认顺序掉过头来：云和支付网络高于去追从高点已经跌了 50% 的奈飞那种图表。

**已经公开的方向，按账号而不是按共识。**

- Kobeissi：隐蔽熊市。纳斯达克 100 的 4 万亿美元、人工智能股票 10 月跌超过 13%、不含人工智能的标普涨 8% 并创新高：[帖](https://x.com/KobeissiLetter/status/2116567209367445876)。没有能源危机则标普在 8500 上方：[帖](https://x.com/KobeissiLetter/status/2116567243245121613)。11 月投资级发行预期 1750 亿美元，人工智能相关投资级债超过 3000 亿美元：[帖](https://x.com/KobeissiLetter/status/2116614948071539134)。垃圾债有效收益率 8.0%：[帖](https://x.com/KobeissiLetter/status/2116647408465563761)。储蓄率 4.2%：[帖](https://x.com/KobeissiLetter/status/2116630555135517067)。热战放在 11 月 3 日之后：[帖](https://x.com/KobeissiLetter/status/2116687632826605694)。他们没有给周一的标普点位。
- Scott Bessent：霍尔木兹通行量回到冲突前，只是少了伊朗的桶。世界离得开伊朗的油：[帖](https://x.com/SecScottBessent/status/2116581781562368057)。没有指数点位。
- Steve Hanke：10 月 30 日 1 艘对去年 46 艘，海峡功能上关闭：[帖](https://x.com/steve_hanke/status/2116619969119297578)。继续做多石油和天然气，基金组织路径上的油价是 130 美元：[帖](https://x.com/steve_hanke/status/2116705533117776145)。新建住房成本大约多 8200 美元：[帖](https://x.com/steve_hanke/status/2116686658808762408)。巴西政府利息支出占 GDP 的 9%：[帖](https://x.com/steve_hanke/status/2116647651462488260)。没有标普点位。
- Robin Brooks，线外：油价涨、10 年期收益率跌，避险流向美债：[帖](https://x.com/robin_j_brooks/status/2116507185387561305)。黄金回到 4000 下方，布伦特涨 10% 对应黄金跌 4%，下行有限：[帖](https://x.com/robin_j_brooks/status/2116778807499821175)。白银周五将近跌 6%：[帖](https://x.com/robin_j_brooks/status/2116548358021992558)。他没有给周一的标普点位。
- Javier Blas，线外：不含伊朗的中东原油出口月均超过战前 90%，成品油大约在战前的 60% 以上；11 月 3 日之后若重启，恢复可能消失：[帖](https://x.com/JavierBlas/status/2116571020857581818)。美国夏天汽油消费大约 25 年来最弱，2020 年除外：[帖](https://x.com/JavierBlas/status/2116602101434642915)。没有新的油价目标。
- Keith McCullough，线外：做多石油和能源股；离开人工智能泡沫股和比特币更好：[帖](https://x.com/KeithMcCullough/status/2116533627156902043)。散户周五跌 5.6%：[帖](https://x.com/KeithMcCullough/status/2116533103565193353)。一条视频标题是人工智能是否在杀死谷歌最大的业务：[帖](https://x.com/KeithMcCullough/status/2116521606713327834)。窗口内没有新的指数点位。
- firstadopter，线外：110 美元以上的油价是跑道尽头，需要可信的战争解决方案：[帖](https://x.com/firstadopter/status/2116520245741355336)。他贴出的 Warsh 原话是利率对人工智能投资起作用，信用利差已经分化：[帖](https://x.com/firstadopter/status/2116552705887932561)。
- El-Erian：科技信用利差在拉开：[帖](https://x.com/elerianm/status/2116526579232702587)。悲观报道可能做过了头：[帖](https://x.com/elerianm/status/2116563633216122955)。下一周是中期选举、就业数据和央行讲话：[帖](https://x.com/elerianm/status/2116626131906334784)。没有新的指数点位。
- Yardeni，线外：等权涨 4.9%，市值加权从 10 月高点跌 3.1%：[帖](https://x.com/yardeni/status/2116605997837881478)。下一周看就业、美联储讲话和中期选举，他们在等强于共识的非农：[帖](https://x.com/yardeni/status/2116618678007431343)。共识数字不在帖里。
- Andy Constan，线外：本周再融资日程比选举更重要：[帖](https://x.com/dampedspring/status/2116584846084730984)。没有新的指数点位。
- RenMac，线外：障碍利率回来了，TINA 死了，权益这边几乎没注意到：[帖](https://x.com/RenMacLLC/status/2116591155399868703)。2.34% 的盈亏平衡曾经对应 59 到 112 美元的原油：[帖](https://x.com/RenMacLLC/status/2116508777784742337)。
- Carl Quintanilla，线外：自由现金流差的公司信用违约互换飙升，现金多的资产负债表还被护着：[帖](https://x.com/carlquintanilla/status/2116572580349972957)。他转发的问题是，Alphabet、亚马逊或 Meta 再跌 50%，人工智能开支从哪里来：[帖](https://x.com/carlquintanilla/status/2116628358444490913)。
- Charlie Bilello：比特币年内跌 11.7%，黄金跌 10.2%：[帖](https://x.com/charliebilello/status/2116594862942568958)。AWS 过去 12 个月收入 1610 亿美元：[帖](https://x.com/charliebilello/status/2116601170055549390)。没有周一点位。
- Anthony Pompliano：收入和利润率还在变好，市场最终会追上：[帖](https://x.com/APompliano/status/2116677583878422805)。他转发的观点是礼来可能成为全球最有价值的公司，英伟达更容易被颠覆：[帖](https://x.com/APompliano/status/2116608090401542213)。
- Ryan Detrick，线外：科技感冒则指数吃力，表面之下有机会：[帖](https://x.com/RyanDetrick/status/2116559730806059230)。低波动配动量：[帖](https://x.com/RyanDetrick/status/2116540295185621156)。没有新的点位。
- S. Joseph Burns：周五抹掉 1.8 万亿美元：[帖](https://x.com/SJosephBurns/status/2116675992853123097)。他把这一天放进自己见过最差的科技日：[帖](https://x.com/SJosephBurns/status/2116676810922766400)。他的交易句子是对正在发生的事做反应：[帖](https://x.com/SJosephBurns/status/2116532367083086075)。
- The Transcript，线外：六到八个模型、三星 2027 年 HBM 售罄、谷歌自由现金流受压、Generac 积压约 45 亿美元、Visa 和万事达低双位数增长、黑石人工智能敞口约 7%：[模型](https://x.com/TheTranscript_/status/2116564605367709847)、[HBM](https://x.com/TheTranscript_/status/2116579261494735135)、[自由现金流](https://x.com/TheTranscript_/status/2116681635651522734)、[发电机](https://x.com/TheTranscript_/status/2116720122878362096)。
- TrendSpider：英伟达被写成浪潮以来最便宜，没有倍数：[帖](https://x.com/TrendSpider/status/2116595179117326744)。苹果盯着 400 美元：[帖](https://x.com/TrendSpider/status/2116613680037081449)。奈飞较高点超过 50%：[帖](https://x.com/TrendSpider/status/2116557055519502591)。特斯拉摆脱 2026 年下降趋势：[帖](https://x.com/TrendSpider/status/2116651431490916512)。埃克森、雪佛龙、壳牌、康菲被写成高油价里在笑的股东：[帖](https://x.com/TrendSpider/status/2116539432912220448)。
- Sawyer Merritt：SpaceX 大约 42 万颗英伟达 GB300、350 亿美元以上的 GPU，两个集群分别在 11 月末和 12 月：[帖](https://x.com/SawyerMerritt/status/2116592175823642670)。
- Tavi Costa，线外：白银这次没有 2011 年那种供应反应：[帖](https://x.com/TaviCosta/status/2116642668818403508)。
- Danielle DiMartino Booth，线外：高收益债出现转让出价，信用在核心：[帖](https://x.com/DiMartinoBooth/status/2116514754542121024)。
- Luke Gromen：他称一篇西方投资者还很不理解的笔记值得读。帖文本身没有指数点位：[帖](https://x.com/LukeGromen/status/2116529872269185354)。
- Michael Burry：窗口内是“周末长文”四个字，没有新的点位：[帖](https://x.com/michaeljburry/status/2116641060827107468)。
- Ray Dalio：窗口内是一条关于更高层次思考的原则，没有指数句子：[帖](https://x.com/RayDalio/status/2116669943550734470)。
- Bill Ackman：窗口内有一条和挪威主权基金负责人谈投资格局的访谈链接，正文没有摘出点位：[帖](https://x.com/BillAckman/status/2116530906311917912)。其余是纽约政治。
- Jim Cramer、Peter Schiff、Liz Ann Sonders、Kevin O'Leary：窗口内没有新的指数或个股方向。Cramer 的两帖是保护区。Schiff 的两帖是选举广告和联邦援助。Liz Ann 和 O'Leary 是周末随笔。
- Eric Balchunas，线外：窗口内是“Brutal”和一个歌单，没有新的 ETF 资金流数字。
- Hedgeye、Bespoke，线外：窗口内分别是万圣节问候和订阅广告，没有新的指数点位。
- 美联储官方账号、高盛、摩根大通、花旗、美国银行、SEC、欧洲央行：窗口内没有新的利率决定。Warsh 的利率句子出现在 firstadopter 周六贴出的 10 月 28 日问答里。

**财报和数据的顺序。** 先看已经写进周末标题的文件：英特尔跌 29% 的周六标题，OpenAI 最多 200 亿美元和 500 亿美元经常性收入，币安 63 亿美元和周日的提现标题，Meta 周六仍在传播的负面展望：[帖](https://x.com/Investingcom/status/2116644340428857726)。再看已经写出的 9 月储蓄率 4.2% 和 I 债 5.51%。然后才是还没公布、被点了名的就业、美联储讲话、中期选举和再融资日程。线外的 Earnings Whispers 给了一份财报回顾的链接，正文没有列出代码：[帖](https://x.com/eWhispers/status/2116618161890226487)。抓取结束时这些日历项都没有新的公布值。

**明确留在观察、不放进计划的东西。** 周日现货不开市，不用还没开出的晚场期货倒推周一收盘。28447 是周六报价上的纳斯达克，25438.40 是上一份日报的综合指数。10258 按帖面保留。3885 和“4000 下方”分开。63 亿美元和“超过 60 亿美元”分开。200 亿美元的融资额和 500 亿美元的经常性收入分开。11 月 20 日不是公司公告的上市日。德意志银行和 Daniel Newman 的时间线没有读到。彭博主号、markets、BBC Business、CNN Business、纽约时报商业、TradingView、巴菲特账号的时间线对不上这个窗口。Gary Black、SpotGamma、Nick Timiraos、LiveSquawk、Bespoke、Hedgeye 这个窗口没有新的指数点位。Gundlach、Damodaran、Cathie Wood、Minervini、Icahn、Nouriel、Krugman、Chamath、Ackman 的访谈正文、Burry 的“周末长文”这次没有可引用的新判断。

## 帖文索引

周末报价与分化：[道指 51821、纳斯达克 28447、黄金 3885、美油 10258](https://x.com/FirstSquawk/status/2116547100666384737)、[年内涨跌](https://x.com/Investingcom/status/2116650231014338846)、[不含人工智能的标普](https://x.com/KobeissiLetter/status/2116567209367445876)、[8500](https://x.com/KobeissiLetter/status/2116567243245121613)、[等权 4.9%](https://x.com/yardeni/status/2116605997837881478)、[财报次日](https://x.com/KobeissiLetter/status/2116542276738355535)。

霍尔木兹、油和黄金：[通行量](https://x.com/SecScottBessent/status/2116581781562368057)、[原油出口超过战前 90%](https://x.com/JavierBlas/status/2116571020857581818)、[10 月 30 日 1 艘](https://x.com/steve_hanke/status/2116619969119297578)、[选举之后](https://x.com/KobeissiLetter/status/2116687632826605694)、[黄金 4000 下方](https://x.com/robin_j_brooks/status/2116778807499821175)、[130 美元路径](https://x.com/steve_hanke/status/2116705533117776145)。

信用、融资和提现：[1750 亿美元](https://x.com/KobeissiLetter/status/2116614948071539134)、[垃圾债 8%](https://x.com/KobeissiLetter/status/2116647408465563761)、[储蓄率 4.2%](https://x.com/KobeissiLetter/status/2116630555135517067)、[I 债 5.51%](https://x.com/unusual_whales/status/2116610657856393527)、[再融资日程](https://x.com/dampedspring/status/2116584846084730984)、[债券旁观选举](https://x.com/FT/status/2116766641308524667)、[OpenAI 500 亿美元经常性收入](https://x.com/unusual_whales/status/2116595662779462054)、[最多 200 亿美元](https://x.com/CNBC/status/2116621770811674986)、[比特币提现恢复](https://x.com/Reuters/status/2116787463465074766)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-11-01 抓取时的公开读数。原创条数是窗口内、按帖文链接去重后的原创帖，回复和被接口标成转发的不计入。路透 126 条、彭博商业账号 67 条、《华尔街日报》69 条、《金融时报》24 条、FinancialJuice 52 条、零对冲 39 条、unusual_whales 23 条是读穿窗口后的计数。德意志银行和 Daniel Newman 的 0 是读取失败。沃伦·巴菲特的可见时间线停在 2016 年。彭博经济停在 2026 年 7 月。彭博主号、markets、BBC Business、CNN Business、纽约时报商业、TradingView、CNBC Now 的 0 来自对不上这个窗口的时间线。线外的 First Squawk 是 138 条，不在这张表里。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,440,663 | 126 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,325,872 | 76 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,275,614 | 69 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,321,917 | 19 |
| 5 | [@business](https://x.com/business) | 10,487,911 | 67 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,564,264 | 1 |
| 7 | [@FT](https://x.com/FT) | 7,107,563 | 24 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,255,506 | 17 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,391,004 | 23 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,647,017 | 10 |
| 11 | [@IMFNews](https://x.com/IMFNews) | 4,584,067 | 0 |
| 12 | [@paulkrugman](https://x.com/paulkrugman) | 4,425,409 | 0 |
| 13 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,356,617 | 10 |
| 14 | [@zerohedge](https://x.com/zerohedge) | 3,430,846 | 39 |
| 15 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,422,669 | 0 |
| 16 | [@BillAckman](https://x.com/BillAckman) | 3,040,160 | 5 |
| 17 | [@CathieDWood](https://x.com/CathieDWood) | 2,998,542 | 0 |
| 18 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,711,106 | 7 |
| 19 | [@RayDalio](https://x.com/RayDalio) | 2,560,476 | 1 |
| 20 | [@jimcramer](https://x.com/jimcramer) | 2,517,896 | 2 |
| 21 | [@chamath](https://x.com/chamath) | 2,480,690 | 0 |
| 22 | [@APompliano](https://x.com/APompliano) | 2,437,082 | 5 |
| 23 | [@BW](https://x.com/BW) | 2,288,203 | 0 |
| 24 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,418 | 13 |
| 25 | [@BBCBusiness](https://x.com/BBCBusiness) | 2,157,880 | 0 |
| 26 | [@michaeljburry](https://x.com/michaeljburry) | 2,130,388 | 1 |
| 27 | [@YahooFinance](https://x.com/YahooFinance) | 2,076,088 | 5 |
| 28 | [@markets](https://x.com/markets) | 2,047,083 | 0 |
| 29 | [@DeItaone](https://x.com/DeItaone) | 1,968,280 | 18 |
| 30 | [@WarrenBuffett](https://x.com/WarrenBuffett) | 1,793,317 | 0 |
| 31 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,773,568 | 2 |
| 32 | [@WSJbusiness](https://x.com/WSJbusiness) | 1,770,508 | 4 |
| 33 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,709,692 | 2 |
| 34 | [@NYSE](https://x.com/NYSE) | 1,700,893 | 0 |
| 35 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,692,997 | 0 |
| 36 | [@theinformation](https://x.com/theinformation) | 1,611,673 | 17 |
| 37 | [@federalreserve](https://x.com/federalreserve) | 1,601,371 | 0 |
| 38 | [@Investingcom](https://x.com/Investingcom) | 1,534,384 | 28 |
| 39 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,508,784 | 2 |
| 40 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,470,173 | 2 |
| 41 | [@RobinhoodApp](https://x.com/RobinhoodApp) | 1,394,805 | 2 |
| 42 | [@Bloomberg](https://x.com/Bloomberg) | 1,353,351 | 0 |
| 43 | [@PeterLBrandt](https://x.com/PeterLBrandt) | 1,352,780 | 1 |
| 44 | [@kevinolearytv](https://x.com/kevinolearytv) | 1,247,975 | 1 |
| 45 | [@TheStreet](https://x.com/TheStreet) | 1,226,327 | 44 |
| 46 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,193,426 | 0 |
| 47 | [@Stocktwits](https://x.com/Stocktwits) | 1,193,123 | 3 |
| 48 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,187,013 | 0 |
| 49 | [@bbgoriginals](https://x.com/bbgoriginals) | 1,185,378 | 4 |
| 50 | [@USTreasury](https://x.com/USTreasury) | 1,165,451 | 0 |
| 51 | [@nntaleb](https://x.com/nntaleb) | 1,164,686 | 2 |
| 52 | [@StockMKTNewz](https://x.com/StockMKTNewz) | 1,160,357 | 14 |
| 53 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,156,832 | 0 |
| 54 | [@SawyerMerritt](https://x.com/SawyerMerritt) | 1,152,930 | 3 |
| 55 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,141,542 | 0 |
| 56 | [@elerianm](https://x.com/elerianm) | 1,116,747 | 4 |
| 57 | [@SJosephBurns](https://x.com/SJosephBurns) | 1,110,004 | 11 |
| 58 | [@Scaramucci](https://x.com/Scaramucci) | 1,096,609 | 2 |
| 59 | [@BlackRock](https://x.com/BlackRock) | 1,081,457 | 0 |
| 60 | [@aleabitoreddit](https://x.com/aleabitoreddit) | 1,064,648 | 0 |
| 61 | [@Downtown](https://x.com/Downtown) | 1,043,561 | 0 |
| 62 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,383 | 23 |
| 63 | [@SecScottBessent](https://x.com/SecScottBessent) | 1,004,090 | 1 |
| 64 | [@financialjuice](https://x.com/financialjuice) | 954,489 | 52 |
| 65 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,340 | 0 |
| 66 | [@Teslarati](https://x.com/Teslarati) | 935,081 | 4 |
| 67 | [@tradingview](https://x.com/tradingview) | 906,736 | 0 |
| 68 | [@BloombergTV](https://x.com/BloombergTV) | 893,891 | 1 |
| 69 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 890,095 | 0 |
| 70 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,668 | 2 |
| 71 | [@charliebilello](https://x.com/charliebilello) | 873,565 | 3 |
| 72 | [@steve_hanke](https://x.com/steve_hanke) | 862,203 | 23 |
| 73 | [@axios](https://x.com/axios) | 862,101 | 10 |
| 74 | [@jpmorgan](https://x.com/jpmorgan) | 860,006 | 0 |
| 75 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 854,163 | 1 |
| 76 | [@Citi](https://x.com/Citi) | 853,300 | 0 |
| 77 | [@HindenburgRes](https://x.com/HindenburgRes) | 848,282 | 0 |
| 78 | [@themotleyfool](https://x.com/themotleyfool) | 840,781 | 0 |
| 79 | [@ecb](https://x.com/ecb) | 830,266 | 0 |
| 80 | [@ARKInvest](https://x.com/ARKInvest) | 822,511 | 0 |
| 81 | [@bgurley](https://x.com/bgurley) | 812,046 | 0 |
| 82 | [@SECGov](https://x.com/SECGov) | 810,414 | 0 |
| 83 | [@economics](https://x.com/economics) | 806,701 | 0 |
| 84 | [@biancoresearch](https://x.com/biancoresearch) | 790,152 | 0 |
| 85 | [@NasdaqExchange](https://x.com/NasdaqExchange) | 780,198 | 0 |
| 86 | [@leadlagreport](https://x.com/leadlagreport) | 770,018 | 20 |
| 87 | [@markminervini](https://x.com/markminervini) | 767,509 | 0 |
| 88 | [@MorganStanley](https://x.com/MorganStanley) | 758,143 | 0 |
| 89 | [@CNBCnow](https://x.com/CNBCnow) | 751,990 | 0 |
| 90 | [@morganhousel](https://x.com/morganhousel) | 731,355 | 0 |
| 91 | [@TrendSpider](https://x.com/TrendSpider) | 718,794 | 12 |
| 92 | [@CMEGroup](https://x.com/CMEGroup) | 712,122 | 0 |
| 93 | [@Nouriel](https://x.com/Nouriel) | 705,709 | 0 |
| 94 | [@DanielNewman](https://x.com/DanielNewman) | 695,462 | 0 |
| 95 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 673,906 | 8 |
| 96 | [@fundstrat](https://x.com/fundstrat) | 673,152 | 0 |
| 97 | [@amitisinvesting](https://x.com/amitisinvesting) | 672,786 | 0 |
| 98 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,055 | 0 |
| 99 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,736 | 0 |
| 100 | [@LukeGromen](https://x.com/LukeGromen) | 637,234 | 1 |
