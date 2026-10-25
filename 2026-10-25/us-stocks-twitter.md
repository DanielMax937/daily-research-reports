# 美股 Twitter 观点日报 · 2026-10-25

周日美股现货不开市。到北京时间 10 月 25 日 20:20 为止，时间线上没有人给出周一的指数点位。能对上的是三件事：伊朗仍同时存在着“再打一次”和“做成交易”两条说法，但一艘俄罗斯柴油船已经朝纽约出发；AI 产能被说成卖到了 2028 年，信用市场和 neocloud 的债却在被当成建不成的证据；标普自己几乎没动，底下的股票和期权偏度却在问，这是轮动还是科技带着整个市场一起掉。周三是美联储，同一周还有 Alphabet、微软、亚马逊的财报。

下面每一条归纳都附有帖文链接。油价出现“接近 117 美元”时，那是访谈里的说法，不是收盘价。媒体标题里没有写出的目标价，这里不补。这是公开帖文的整理，不是投资建议。

## 抓取口径

- 报告日期按北京时间 **2026-10-25**。触发时刻约 12:03 UTC，时间线补抓到 **12:20 UTC（北京时间 20:20）**。观察窗口是 **2026-10-24 16:00 UTC 至抓取结束**，也就是北京时间周日零点到晚上 8 点 20 分。美东此时是周日早上。
- X 的官方连接器这次没有搜索和时间线工具。帖文用公开时间线接口读取，链接都是 `x.com/{账号}/status/{id}`。同一时段的全站搜索接口返回空结果。美国和全球趋势榜读到的是人名、餐饮和体育，没有美股话题。所以“当前讨论”指的是这 100 个账号窗口内的帖，加上文中标明的、粉丝数刚好落在前 100 之外的市场账号。它不是全站每一条提及。
- 不存在官方的“美股 Top 100”。样本是金融媒体、宏观、投资者、交易员、交易所和投行账号，成功读到粉丝数的有 **194** 个，再按抓取当时的粉丝数取前 100。福布斯、英国《金融时报》、雅虎财经、《财富》这次排进了前 100，一批粉丝较少的交易员账号因此落在线外。线外账号的帖如果被引用，正文会写明。排序不代表预测准确度。
- 100 个账号里，**50 个**在窗口内有原创帖，合计 **698** 条原创。First Squawk 读到 80 条后分页失败，最老一条仍在 10 月 25 日 00:34 UTC，所以它的条数是下限，周六下午到周日零点的快讯有缺口。德意志银行的时间线返回失败，表里的 0 不是确认沉默。彭博主号这次可见时间线的最新一条停在 10 月 12 日，和它平时的发帖密度对不上，0 同样不能当成确认沉默。
- 窗口内确认没有市场原创的包括 Jim Cramer、Cathie Wood、ARK 官方账号、Liz Ann Sonders、Charlie Bilello、Gary Black、Raoul Pal、Luke Gromen、Alf、Nick Timiraos、Aswath Damodaran、Hedgeye 官方账号、高盛官方账号、摩根大通官方账号。Ray Dalio 发的是一条原则短帖。Bill Ackman 写的是以色列联合政府，不是仓位。Keith McCullough 有帖，Hedgeye 主号没有。

## 周日还在交易的，是头条不是指数

现货点位仍是周五那根 K 线，窗口内的帖没有再报一套收盘价。新的价格语言集中在油和柴油。彭博新兴市场首席经济学家 Ziad Daoud 在彭博的访谈里说，伊朗战争“所有迹象都指向升级”，没有正在进行的谈判，只有威胁和军事集结，油价接近每桶 117 美元：[帖](https://x.com/business/status/2114030414805225572)。这是访谈用语。

袭击没有停。FinancialJuice 记录胡塞武装称打击了延布的沙特阿美设施、达曼的法赫德国王国际机场、纳季兰机场和海米斯穆谢特空军基地，并称将继续把利雅得的哈立德国王机场当军事目标：[延布](https://x.com/financialjuice/status/2114070031604838740)、[机场与基地](https://x.com/financialjuice/status/2114070063456112964)、[利雅得机场](https://x.com/financialjuice/status/2114103924437168540)。沙特领导的联军称拦截了射向利雅得的弹道导弹，民防随后说利雅得危险已过：[拦截](https://x.com/financialjuice/status/2114196573383196719)、[危险已过](https://x.com/financialjuice/status/2114193677799096694)。伊朗防空在阿巴斯港附近击落一架无人机：[帖](https://x.com/financialjuice/status/2114320441376379312)。zerohedge 的标题是胡塞宣布对沙特境内包括东西管道在内的大规模导弹袭击：[帖](https://x.com/zerohedge/status/2114051826123210973)，以及“纪录油价、空油罐”的阿联酋供应标题：[帖](https://x.com/zerohedge/status/2114107192898994349)。

特朗普的原话被快讯收成两头。DeItaone 写“有可能打击伊朗”，以及“也许得把伊朗这件事做完，或者做成交易，怎么都是我们赢”：[可能打击](https://x.com/DeItaone/status/2114091547763585258)、[做完或做交易](https://x.com/DeItaone/status/2114090697406271754)。Investing.com 用了同一组话：[帖](https://x.com/Investingcom/status/2114119773986632154)。First Squawk 另有一条“一次解决，或者达成协议”：[帖](https://x.com/FirstSquawk/status/2114169160175632566)。伊朗外长阿巴斯·阿拉格齐说，不能这边打仗、那边指望和平，战争必须在每条战线上结束：[帖](https://x.com/FirstSquawk/status/2114272192188010848)。议长称不会被吓住，并准备对领土受侵作出意外回应：[帖](https://x.com/FirstSquawk/status/2114305447121633790)。zerohedge 的另一条标题把下一站写成古巴：[帖](https://x.com/zerohedge/status/2114122291835551885)。

柴油是周日新出现的对冲。福克斯商业频道写，特朗普与普京的协议之后，第一艘俄罗斯柴油船驶向纽约，目标是把燃料价格打下来：[帖](https://x.com/FoxBusiness/status/2114122284411576830)。彭博主站的商业账号写同一艘船已经在路上：[帖](https://x.com/business/status/2114035449047978082)。First Squawk 转述俄罗斯副总理，称俄方准备向美国供应任何数量的柴油：[帖](https://x.com/FirstSquawk/status/2114316719170924976)，并转述鲁比奥为放松俄罗斯柴油出口制裁辩护，用词是“非常明智”：[帖](https://x.com/FirstSquawk/status/2114286034150383854)。特朗普对高油价的说法被 Unusual Whales 记下：美国在赚钱，他不在乎别人说他在油泵前炫耀：[帖](https://x.com/unusual_whales/status/2114214871374127238)。伊朗国内也有柴油紧张。First Squawk 转述卡拉季司机因柴油短缺罢工：[帖](https://x.com/FirstSquawk/status/2114276929708888550)，伊朗议长呼吁把天然气消费至少砍 10%：[帖](https://x.com/FirstSquawk/status/2114271933714022476)。利雅得主机场在持续袭击中重开国际流量，此前关了两周：[帖](https://x.com/FirstSquawk/status/2114272053960560988)。

需求侧的冷数字来自 Real Vision 对 Commodity Context 的 Rory Johnston 的转述：中国把海运原油进口从 12 月到 2 月的日均水平，压到 6、7 月的底部，大约每天 550 万桶，比国际能源署全体成员的战略储备释放加在一起还多。他用的词是“巨大”：[帖](https://x.com/RealVision/status/2114296969686307239)。近月的战争溢价和中国进口的下降，在这些帖里是同时存在的。

## 观点分成四组

### 1. 指数平，大多数股票已经在自己走

Kobeissi 写，标普成分股里站上 50 日均线的比例周五跳了 5 个百分点，到 61%，为 8 月中以来最高；10 月 1 日盘中低点以来这个比例增加了两倍多。站上 200 日均线的比例到 57%。标普自己在这三周里大致没变。周四指数跌 1.2% 的那天，有 335 只成分股收涨。他们把这叫做表面之下在变强：[帖](https://x.com/KobeissiLetter/status/2114083152419316145)。

粉丝数在前 100 之外的 Ryan Detrick 用上周的数字说同一件事：大约 350 只股票的表现好于标普 0.47% 的下跌，平均一只股票涨了 1% 以上，科技和通信服务再次落后，体感比指数差：[帖](https://x.com/RyanDetrick/status/2114108495851110406)。同样在线外的 Bespoke 把 1999 年底到 2001 年底的等权指数拿出来：标普等权在那两年不是下跌，而是上涨 5%。他们把这写成互联网泡沫里“跟建设和移动无关的股票可以走出自己的行情”：[帖](https://x.com/bespokeinvest/status/2114128495324610626)。zerohedge 的标题直接叫“大规模轮动的早期迹象”：[帖](https://x.com/zerohedge/status/2114032951503569310)。

期权账本问的是轮动会不会失败。线外的 SpotGamma 写，纳指波动率相对标普波动率的缺口很宽；上一次类似的“股票涨、波动率也涨”出现在 4 月和 5 月。他们留下的问题是：其余市场会跟着科技一起掉，还是继续轮动：[帖](https://x.com/spotgamma/status/2114137872857006405)。同一账号写周五的一个月 25-delta 认沽相对平值的偏度：QQQ 加 3.64 个波动率点，处在过去一年的第 81 百分位；标普加 3.84，第 77 百分位。道指和罗素 2000 低得多，分别在第 64 和第 50 百分位：[帖](https://x.com/spotgamma/status/2114034437444997177)。认沽买在市值加权的大盘上，没有同样买在小盘和道指上。

Michael Burry 把窄度说得更硬。他写，1980 年以来 982 次标普纪录收盘里，包括后来走进熊市或接近熊市的 10 次，2026 年 10 月 6 日那次和 2000 年 3 月并列，是最窄、最薄、最软的新高：[帖](https://x.com/michaeljburry/status/2114118998392758386)。Kobeissi 的“底下在变强”和 Burry 的“高点窄得像 2000 年 3 月”指的不是同一天，可以同时为真：高点形成的时候很窄，过去三周等权在修复。

Mohamed El-Erian 的一周总结是：市场在重新检查科技投资回报和融资需求这些原先让人安心的假设，纳斯达克走弱，同时有避险，但大家对这个行业长期增长的信心还在。往前看，他称为数据、政策会议和财报都挤在一起的一周：[帖](https://x.com/elerianm/status/2114071006633501034)。

### 2. 产能卖光了，信用在用脚投票

看多需求的一侧有具体的公司原话，但是转述。Puru Saxena 写下三句：亚马逊首席执行官 Andy Jassy 说，即使 2026 年资本开支 2200 亿美元，需求仍然接不住，2026 年卖光、2027 年大体卖光、2028 年已经订出相当一部分；SpaceX 的埃隆·马斯克说需求远超供给，新算力不到一年回本，瓶颈在电力和施工；英伟达的黄仁勋说 neocloud 需求“爆表”，瓶颈会从芯片转到封装、高带宽内存和电力，缺的是资本不是需求。Saxena 的结论是，下跌来自融资压力、利率和自由现金流的观感，不是利用率和租金塌了，并写成“买恐惧”：[帖](https://x.com/saxena_puru/status/2114203315563057399)。

粉丝数在前 100 之外的 Andreas Steno 当天只对马斯克这句下了一个注脚：马斯克现在有动机这么说，因为他本质上是 neocloud 的竞争对手：[帖](https://x.com/AndreasSteno/status/2114326677379780630)。这句没有否定 Jassy 或黄仁勋，它把马斯克的短缺声明从“行业事实”改成“竞争对手的话”。

看空融资的一侧同样具体。Unusual Whales 转述彭博：博通同意最多借给 Anthropic 420 亿美元，用来买芯片和计算硬件；英伟达今年已经向 AI 公司投了超过 400 亿美元，其中 300 亿在 OpenAI。他们把这叫做循环的钱，并写有人因此想到 2008 年：[帖](https://x.com/unusual_whales/status/2114114963803406482)。The Information 写，CoreWeave 的命运已经变成整场 AI 建设能不能融到资的风向标，投资者开始押“不能”：[帖](https://x.com/theinformation/status/2114039262072934873)。路透的评论栏目标题是 neocloud 的股票和无担保债近几周一起跌，并问管道上的裂缝会不会再打到 Anthropic 放缓的增长：[帖](https://x.com/Reuters/status/2114273274938929506)。

信用的原话来自 Lisa Abramowicz 对 Apollo 的 Torsten Slok 的引用：AI 相关信用利差已经扩到足以让一些项目慢下来；“对 AI 来说利率也许不重要，收益率重要”；信用市场开始用脚投票：[帖](https://x.com/lisaabramowicz1/status/2114029845823004932)。DeItaone 转述的是 Slok 的另一面：AI 在大型科技以外的回报是“零”；收入利润率和人均收入在“七巨头”上升，在标普其余 493 家持平；高德纳估计到 2030 年有 3.5 万亿美元的 AI 基础设施开支面临减值风险：[帖](https://x.com/DeItaone/status/2114301898060611618)。《财富》引的是同一逻辑的学术表述：需要多少算力和数据中心，取决于企业用这些算力能产生多少回报；到目前为止 AI 的回报实现得很慢，意味着为 AI 服务付费的意愿在下降：[帖](https://x.com/FortuneMagazine/status/2114103642466746729)。

zerohedge 把高盛的交易台放在买跌的一侧。一条标题是“AI 宿醉：高盛说买跌，对冲基金止损把净敞口打到一年低点”：[帖](https://x.com/zerohedge/status/2114099642304466972)。另一条是高盛的 Pasquariello 说 AI 抛售“切到了骨头”，他自己在往岸边游：[帖](https://x.com/zerohedge/status/2114064415435731206)。还有一条标题把下一场房利美式的信用故事写成 GPU：[帖](https://x.com/zerohedge/status/2114092092112650688)。彭博商业账号写，高盛策略师把韩国综指的目标砍了 25%，理由是 AI 交易的担忧在加剧：[帖](https://x.com/business/status/2114273297370087607)。

需求没有被这些帖写成消失。《经济学人》的标题是算力是新的石油，但这个市场规模虽大，却还没有一个够成熟的市场：[帖](https://x.com/TheEconomist/status/2114240550761030015)。Chamath Palihapitiya 写“电力是绑定约束，所以价格还在猛涨”：[帖](https://x.com/chamath/status/2114093525059174868)。这句没有展开标的。zerohedge 的能源标题是亚马逊、加拿大方面和海军都想在印第安纳建反应堆：[帖](https://x.com/zerohedge/status/2114114742159610028)。福布斯写，大麻价格崩了之后，那些带电力和暖通的厂房想转去接 AI，地方禁令和电力限制打碎了大多数这类打算：[帖](https://x.com/Forbes/status/2114235555416613042)。另一条福布斯写，49% 的小企业 AI 买家收到的账单高于预期：[帖](https://x.com/Forbes/status/2114144915248820641)。

Anthony Pompliano 站在“多数 AI 公司被低估”一侧，并引用 Peter Thiel：上一轮融资越陡，公司越便宜：[帖](https://x.com/APompliano/status/2114114108736082047)。他同时问礼来会不会在五年内成为全球市值最大的公司，转述 Jordi Visser 的理由是“未来五年打不破的是让人变好”，并说英伟达倍数下降是因为市场在给“它最终会被颠覆”定价：[帖](https://x.com/APompliano/status/2114082310366629911)。Keith McCullough 贴出的 Hedgeye 客座文章标题是，Anthropic 在大型 IPO 之前有一个重大的中国问题：[帖](https://x.com/KeithMcCullough/status/2114320767148023853)。The Information 写，Anthropic 员工绝大多数相信 AI 会在 2030 年前做出诺贝尔奖级别的突破，华尔街远没有这么信，而公司准备下个月上市：[帖](https://x.com/theinformation/status/2114031679538921755)。

线外的 The Transcript 贴出的公司原话把“谁真正在用”说窄了。埃森哲首席 AI 与数据官说，他们的研究证明只有 10% 到 20% 的企业工作流配得上前沿模型：[帖](https://x.com/TheTranscript_/status/2114129815729250542)。同一账号转发的 Meta 首席财务官口径是，2026 年资本开支包括融资租赁本金在 1350 亿到 1450 亿美元，从原先的 1300 亿到 1450 亿收窄：[帖](https://x.com/TheTranscript_/status/2114039248756314401)。SpaceX 首席运营官说，Grok 机器人 8 月上线，本月早些时候付费周活 80 万，一个月内翻倍有余：[帖](https://x.com/TheTranscript_/status/2114054324078997650)。

### 3. 美联储被写成“按兵不动”，黄金和比特币在过周末

First Squawk 的标题是，美联储预计在美国中期选举前几天维持利率不变：[帖](https://x.com/FirstSquawk/status/2114244165420855399)。zerohedge 的另一条标题是，尽管 CPI 偏热，美联储躲开了加息，高盛警告分布的两端都变肥了：[帖](https://x.com/zerohedge/status/2114026660236239248)。这两条都是标题，帖文里没有写出会议日期和新的点阵。Pompliano 把背景收成“油价超过 115 美元，情绪接近纪录低位，美联储决定就在前面”：[帖](https://x.com/APompliano/status/2114103890551492655)。

线外的 Peruvian Bull 写，联邦基金利率 3.75%，CPI 3.7%，油价在 100 美元以上时实际利率基本是零；沃尔克在 1981 年把利率放到通胀上方 9 个点以上：[帖](https://x.com/peruvian_bull/status/2114060545284538816)。这是他的比较，不是美联储的声明。

黄金的周末读数偏空。线外的 Kitco 写，华尔街怀疑黄金的近端强度，油价、通胀担忧和“进一步收紧”的预期盖过了避险，周四的科技抛售触发另一轮清算，金价回到每盎司 4000 美元下方：[帖](https://x.com/KitcoNewsNOW/status/2114117204698403006)。“进一步收紧”是这篇周评的解释，和 First Squawk“预计维持不变”并列，不互相替换。TheStreet 的标题是金价击穿 4000 美元、投资者在等一场关键测试，正文没有方向和点位：[帖](https://x.com/TheStreet/status/2114190277900402789)。Bespoke 写 GLD 在 11 月到 1 月的三个月里涨了 30% 以上，这轮涨幅已经来回打掉，同比为负：[帖](https://x.com/bespokeinvest/status/2114177285871816934)。过去六个月他们写比特币涨 5%、GLD 跌 15%：[帖](https://x.com/bespokeinvest/status/2114176858703147033)。

Gold Telegraph 不谈周一的价位。他们转述高盛：央行买金的速度是 2022 年前月度节奏的四倍以上，而且更多央行拒绝披露存放地点：[帖](https://x.com/GoldTelegraph/status/2114093155394146401)。Kobeissi 写的是白银空头拥挤：三个月认沽相对认购的偏度到 -3，为 7 月初以来最高，过去四周升了 10 个点；投机账户在截至 10 月 13 日的三周里卖出 22 亿美元白银期货，净多头降到 17 亿美元，为至少两年最低：[帖](https://x.com/KobeissiLetter/status/2114037773447372865)。

比特币是周末能卖的风险资产。Peter Schiff 写，比特币终于破位，跌到 8 万美元以下，下一站很可能是 7.5 万美元；如果这个位置当天守不住，比特币持有者会过一个很长的周末，尤其是要等到周一才能卖的 ETF 投资者：[帖](https://x.com/PeterSchiff/status/2114034479949848775)。他窗口内的其余帖是诉讼和银行，不是新的黄金号召。Benzinga 另有标题说他警告中期选举前的股市崩盘“不是不可能”，那是媒体转述，窗口内没有他本人的对应帖：[Benzinga](https://x.com/Benzinga/status/2114265715142218150)。

线外的 Tavi Costa 写，矿工里只剩 10% 还在 200 日均线之上，历史上这么低的读数曾经对应这个行业的重要底部：[帖](https://x.com/TaviCosta/status/2114105738943680850)。这是矿工股票的位置，不是金价的目标。

### 4. 法国债、住房和中期选举占着周一的风险预算

法国是这些账号里除了油以外最密的宏观标题。《华尔街日报》市场账号写，法国的挥霍让它成为全球债券收益率抬升后的第一个受害者，作者是 James Mackintosh：[帖](https://x.com/WSJmarkets/status/2114289024718324004)。《财富》写穆迪没有降级，但负面展望的理由是政治碎片化还会妨碍立法机构运转：[帖](https://x.com/FortuneMagazine/status/2114066395923124287)。Robin Brooks 预告周日美东上午 9:30 的直播主题是，如果情况变差，欧洲央行能怎样帮法国；他提醒 2022 年欧洲央行给意大利和西班牙收益率封顶，市场是几个月后才知道的：[帖](https://x.com/robin_j_brooks/status/2114063282080522538)。线外的 Santiago Capital 转发 Ken Griffin 的一句：“法国是社会主义梦想成真”：[帖](https://x.com/SantiagoAuFund/status/2114158413559275924)。巴黎超过 11 万人上街后的冲突，Jim Bianco 用来提醒 NFL 还要在法兰西大球场开球：[帖](https://x.com/biancoresearch/status/2114183193276350789)。

住房是收益率进美国消费的另一条腿。Unusual Whales 写十年前按揭利率 3.4%、房价中位数 23.5 万美元、月供约 830 美元；现在是 7.4%、41.8 万美元、约 2300 美元，房价涨 78%：[帖](https://x.com/unusual_whales/status/2114160261921685902)。福克斯商业频道写，住房在月供之外还有每月 1380 美元的隐性成本，Zillow 和 Thumbtack 的报告称这项成本五年涨了近 32%：[帖](https://x.com/FoxBusiness/status/2114113981547778082)。zerohedge 的标题是住房市场深度冻结的最初迹象：[帖](https://x.com/zerohedge/status/2114137396304392681)。线外的圣路易斯联储写，9 月新屋开工经季调年率 122.1 万套，比 8 月低 5.2%，比一年前低 7.4%；许可 140 万套，比 8 月低 0.2%：[开工](https://x.com/stlouisfed/status/2114115976648171979)、[许可](https://x.com/stlouisfed/status/2114137114077991321)。同一账号写，截至 10 月 17 日当周初请失业金人数降 6000 人，到 19.4 万：[帖](https://x.com/stlouisfed/status/2114212611298361820)。线外的 The Transcript 转述黑石联合创始人 Stephen Schwarzman：2025 年美国建的房子和 1960 年一样多，人口已经翻倍有余，答案是多建：[帖](https://x.com/TheTranscript_/status/2114314379181318599)。

中期选举被写成仓位事件，不是政策细节。特朗普周六已在佛罗里达提前投票：[帖](https://x.com/business/status/2114099682976633003)。《财富》引 Nationwide：72% 的 Z 世代投资者说自己已经为 11 月选举调整了退休金或投资组合，婴儿潮一代是 17%：[帖](https://x.com/FortuneMagazine/status/2114055576053256267)。Investor's Business Daily 的标题是，中期选举通常对市场有利，今年也许不同，帖文没有展开历史表：[帖](https://x.com/IBDinvestors/status/2114084590973231478)。Saxena 写的是选举之后到 6 月底历史上偏正、不确定性去掉以后回报强，这是选举后的季节性，不是周一的季节性：[帖](https://x.com/saxena_puru/status/2114326120258494878)。

Kobeissi 的增长帖和“表面熊”并列。标普全球美国制造业 PMI 初值 10 月升 0.1 到 56.0，为 2022 年 5 月以来最高，预期是下降 0.4；就业分项为 2012 年 3 月以来最强。服务业降 0.9 到 57.9，综合降 0.8 到 57.6，仍是四年来第二高。他们据此写四季度实际 GDP 年化可以到 5.0%，三季度是 4.0%：[帖](https://x.com/KobeissiLetter/status/2114113892385464685)。MarketWatch 的标题是，经济健康为什么不再决定股市回报，正文没有数字：[帖](https://x.com/MarketWatch/status/2114327171560825001)。

## 要盯住的五件事

1. **柴油船和胡塞的导弹，哪一个先改写周一的油。** 升级的证据是延布、达曼、利雅得机场和东西管道这些地名，加上“接近 117 美元”和“没有谈判”。缓和的证据是驶向纽约的俄罗斯柴油、鲁比奥称放松柴油制裁明智、中国海运进口每天少大约 550 万桶。两条都在周日的帖里，没有一条是收盘价。
2. **CoreWeave 和 AI 信用利差，而不是“泡沫”两个字。** The Information 把 CoreWeave 写成融资能不能继续的风向标。Slok 的利差已经在拖项目。Saxena 转述的卖光了的订单，和 Steno 对马斯克动机的注脚，要一起看。
3. **认沽买在 QQQ 和标普上，没有同样买在罗素和道指上。** 这是 SpotGamma 的偏度。如果周一小盘和道指的认沽偏度追上来，Kobeissi 的“底下在变强”就少了一个支柱。
4. **周三的美联储，以及同一周的 Alphabet、微软、亚马逊。** CNBC 的财报日程帖只点了这三个名字和“还有更多”：[帖](https://x.com/CNBC/status/2114325598310969717)。First Squawk 的基准是维持利率不变。Kitco 用来解释黄金下跌的“进一步收紧”是另一套叙事。
5. **比特币 8 万美元和黄金 4000 美元，是周一开盘前已经能交易的风险偏好。** Schiff 把 ETF 投资者的卖出时点明确写到周一。金价在 Kitco 的周评里已经回到 4000 美元下方。

劳动数据没有一起差。初请 19.4 万是圣路易斯联储的帖。住房开工在降，初请没有升。这是周日帖文里的组合，不是新的非农。

## 尤其值得看的股票和板块

下表只收本窗口里被点名、并带有方向、位置或事件的名字。媒体标题若没有在帖文正文里写出公司，就不补代码。粉丝数在前 100 之外的账号单独标出。

| 方向 | 名字 | 帖文里的说法 | 链接 |
|---|---|---|---|
| 柴油与原油的对冲 | 柴油船、胡塞袭击的沙特设施、中国进口 | 福克斯写第一艘俄罗斯柴油船驶向纽约。FinancialJuice 记录胡塞称打了延布阿美和多座机场。Real Vision 转述中国海运原油进口每天少约 550 万桶。线外的 Seeking Alpha 有一篇标题是油价在飙、无论接下来怎样都能做的 USO 文章，这是平台文章标题，不是仓位 | [柴油船](https://x.com/FoxBusiness/status/2114122284411576830)、[延布](https://x.com/financialjuice/status/2114070031604838740)、[中国进口](https://x.com/RealVision/status/2114296969686307239)、[USO 标题](https://x.com/SeekingAlpha/status/2114076973433802887) |
| 融资压力下的 AI 基础设施 | AVGO、NVDA、AMZN、CRWV、Anthropic | 博通最多借给 Anthropic 420 亿美元；英伟达今年投向 AI 公司超过 400 亿美元，其中 300 亿在 OpenAI。CoreWeave 被写成建不建得成的风向标。Jassy 的 2200 亿美元资本开支和“卖到 2028”是 Saxena 的转述。Anthropic 被 The Information 写成下个月上市 | [循环融资](https://x.com/unusual_whales/status/2114114963803406482)、[CoreWeave](https://x.com/theinformation/status/2114039262072934873)、[卖光](https://x.com/saxena_puru/status/2114203315563057399)、[上市](https://x.com/theinformation/status/2114031679538921755) |
| 财报周点名 | GOOGL、MSFT、AMZN、AMAT | CNBC 点名 Alphabet、微软、亚马逊在本周财报。线外的 Seeking Alpha 有两篇贡献者文章，标题分别是微软一季度一场 7440 亿美元的 AI 清算，以及应用材料财报前应该加仓。文章标题不是公司指引 | [日程](https://x.com/CNBC/status/2114325598310969717)、[微软标题](https://x.com/SeekingAlpha/status/2114122270767738993)、[AMAT 标题](https://x.com/SeekingAlpha/status/2114221675474764278) |
| 图表账号的周日标题 | GOOG、AAPL、NFLX、WDAY、DUOL、GEV、COST | TrendSpider 写谷歌终于选了方向，苹果配上“现金为王”，奈飞配上“准备爆米花”，Workday“回到工作”，多邻国被定价成 AI 已经赢了，GE Vernova 被写成拔掉 50 周指数均线。这些是图说，没有价位 | [GOOG](https://x.com/TrendSpider/status/2114133585758462405)、[AAPL](https://x.com/TrendSpider/status/2114076963661033604)、[NFLX](https://x.com/TrendSpider/status/2114039219589202411)、[WDAY](https://x.com/TrendSpider/status/2114152460411408670)、[DUOL](https://x.com/TrendSpider/status/2114171334582505594)、[GEV](https://x.com/TrendSpider/status/2114114714032832621) |
| 信用和资本开支的平台 | META、CRM、DDOG | The Transcript 转发的 Meta 2026 年资本开支区间是 1350 亿到 1450 亿美元。The Information 写 Salesforce 将要求客户登记外部 AI 代理。Datadog 近 40 亿美元收购 Upwind，大约 80 倍经常性收入，被写成 AI 安全需求的证据。Thoma Bravo 准备再做一笔与 63 亿美元 Varonis 同量级的网络安全交易 | [Meta](https://x.com/TheTranscript_/status/2114039248756314401)、[Salesforce](https://x.com/theinformation/status/2114115763380338703)、[Datadog](https://x.com/theinformation/status/2114069452874518712)、[Thoma Bravo](https://x.com/theinformation/status/2114092071136985448) |
| 标题里有、正文没写代码 | ZETA、WDC、JBLU、SCHD、CELH、VSCO | TheStreet 标题写高盛看到一只被忽视的 AI 股票有 41% 上行，链接指向 Zeta Global，正文没有代码。线外的 Benzinga 标题写西部数据称硬盘价格上涨最终会放缓，但 AI、推理和机器人还在撑需求。zerohedge 标题写捷蓝债权人请来重组顾问，股票和债券大跌。TheStreet 写 SCHD 跌 6% 进入一个熟悉的区域。Brian Feroldi 把 28 美元的 Celsius 写成平庸生意、估值合理。Business Insider 写 Victoria's Secret 的股票有望创下最好的一年，没有数字 | [Zeta 标题](https://x.com/TheStreet/status/2114280888594751663)、[西部数据](https://x.com/Benzinga/status/2114084514318422110)、[捷蓝](https://x.com/zerohedge/status/2114084542269005880)、[SCHD](https://x.com/TheStreet/status/2114296023350743180)、[CELH](https://x.com/BrianFeroldi/status/2114084513827705081)、[VSCO](https://x.com/BusinessInsider/status/2114286081151561973) |
| 五年叙事，不是周一 | LLY、SPCX | Pompliano 问礼来会不会五年内成为市值第一，并转述英伟达倍数下降是在定价被颠覆。SpaceX 出现在 Saxena 对马斯克的转述和 The Transcript 的 Grok 周活里，没有目标价 | [礼来](https://x.com/APompliano/status/2114082310366629911)、[Grok](https://x.com/TheTranscript_/status/2114054324078997650) |
| 周一开盘前的海外事件 | EWZ、奢侈品集团 | The Stalwart 转发的一张图写，Kalshi 上 Flávio Bolsonaro 获胜概率 84%，巴西 ETF EWZ 周五收在 42.60 美元，周一才重新交易。这是转发，不是他的预测。First Squawk 转述《金融时报》：中国消费放缓抹掉奢侈品集团 2500 亿欧元市值，帖文没有公司代码 | [转发](https://x.com/M_McDonough/status/2114069600056844791)、[奢侈品](https://x.com/FirstSquawk/status/2114228898909323507) |
| 指数期权而不是个股 | QQQ、SPX、DIA、IWM | 见上一节 SpotGamma 的偏度。线外账号 | [偏度](https://x.com/spotgamma/status/2114034437444997177) |
| 贵金属的位置 | 黄金、白银、矿工 | Kitco：黄金回到 4000 美元下方。Kobeissi：白银空头拥挤、投机净多头为两年最低。Tavi Costa：只有 10% 的矿工还在 200 日均线之上。Bespoke：GLD 同比为负 | [Kitco](https://x.com/KitcoNewsNOW/status/2114117204698403006)、[白银](https://x.com/KobeissiLetter/status/2114037773447372865)、[矿工](https://x.com/TaviCosta/status/2114105738943680850) |

TheStreet 另有一篇标题是华尔街老将下调标普目标、但仍保留很大的赌注，帖文没有写出新目标，这里不补数字：[帖](https://x.com/TheStreet/status/2114144977122902524)。高盛对霍尔木兹和燃料成本的警告同样只以标题出现：[帖](https://x.com/TheStreet/status/2114114796316492234)。

Benzinga 转述 Gene Munster 站在马斯克、扎克伯格和黄仁勋一侧，称“我们还早”，并点名 Meta 和英伟达领跌。这是媒体转述，窗口内没有 Munster 本人的帖：[帖](https://x.com/Benzinga/status/2114129819298607264)。

## 后续走势：两套可以证伪的剧本

帖文没有给出周一的点位。能整理出来的是两套条件，加上一套不依赖头条的结构判断。

**升级剧本。** 触发器已经写在周日的帖里：没有谈判、可能再打、胡塞继续打机场和东西管道、伊朗称回应会是意外的。这条路径上，近月原油维持战争溢价，能源股继续排在高融资 AI 前面，黄金继续被油价而不是避险需求定价，法国债利差继续充当全球收益率抬升的薄弱环节。Kobeissi 的四季度 GDP 年化 5% 如果和油价一起留下来，实际利率的讨论会更尖锐，而不是更松。Peruvian Bull 的“实际利率基本为零”就是这条路径上的反对意见：名义利率没跟上油价。

**柴油和交易剧本。** 触发器是驶向纽约的那艘船、鲁比奥称放松柴油制裁明智、特朗普“做成交易也算赢”，以及中国进口每天少 550 万桶。这条路径上，周五那种能源领先会遇到柴油这一条具体的供给新闻。Steno 把随后可能出现的科技反弹留了一个前提：不要把马斯克的短缺声明当成中立的行业事实。Saxena 转述的 Jassy 和黄仁勋没有这个利益冲突。如果信用利差不再扩，被融资叙事打过的大型云比追近月原油更符合这一侧的帖。CoreWeave 若再出现融资断裂的标题，这一侧就失败。

**不依赖头条的结构判断。** 指数平、站上 50 日均线的成分股到了 61%、周四指数跌的时候 335 只股票在涨、认沽偏度集中在 QQQ 和标普而不是罗素。Detrick、Kobeissi、Bespoke、SpotGamma 站在这一侧。Burry 的约束是：10 月 6 日的新高窄得像 2000 年 3 月。El-Erian 的约束是：纳斯达克的弱来自回报和融资假设被重新检查，不是来自对长期增长失去信心。高盛被 zerohedge 写成在对冲基金净敞口降到一年低点之后建议买跌。这是交易台的标题，不是目标点位。

选举后的季节性不要提前用。Saxena 的正回报窗口是中期选举之后到 6 月底。选举还没发生，特朗普周六才去提前投票。

## 从这些帖归纳的交易计划

这一节只整理上述账号已经公开的条件和标题，方便对照周一开盘。它不决定仓位大小。

**开盘前只核对四样东西。** 俄罗斯柴油船的消息有没有被新的胡塞或伊朗袭击盖过；CoreWeave、博通对 Anthropic 的融资、以及 Slok 说的 AI 信用利差有没有再扩一截；QQQ 和标普的认沽偏度有没有扩散到罗素和道指；比特币在 Schiff 写下的 8 万美元下方、黄金在 Kitco 写下的 4000 美元下方，这两样周末读数开盘时还在不在。四样都变差，这些帖给出的默认顺序是能源和已经修复的广度高于高融资科技。柴油船的新闻站住、信用利差不再扩、偏度仍只集中在纳指，默认顺序掉过头来：被砸过的大型云高于近月原油。

**已经公开的方向，按账号而不是按共识。**

- Saxena：把卖光了的订单当成“这不是需求气穴”，并写买恐惧。他的选举后季节性要等中期选举过去。Steno 要求把其中马斯克的那一句单独打折。
- Kobeissi：广度改善是机会的语言，白银空头拥挤是他们写下的商品事实。他们没有在这些帖里给标普目标。
- Schiff：8 万美元以下看 7.5 万美元，并提醒 ETF 要等到周一。他的股市崩盘警告只出现在 Benzinga 的标题里。
- SpotGamma：问题是轮动还是科技带着市场一起掉。计划是看偏度扩散，而不是看纳指波动率单独升高。
- Bespoke：等权在上一次科技泡沫里可以不跌。这是类比，不是“因此买入等权”的指令。GLD 同比转负是他们写下的价格事实。
- Tavi Costa：矿工极低的 200 日均线站上比例，被他写成历史上的底部区。这和他“黄金已经跌破 4000”的 Kitco 读数可以并存：金价弱、矿工超卖。
- El-Erian：这一周用数据、政策会议和财报去检验科技的回报和融资，而不是用一条油价头条结束讨论。
- Pompliano：油价超过 115 美元、情绪极低、美联储在前面。他的交易表达是 AI 公司被低估，以及礼来的五年问题。礼来不是周一的事件。
- Keith McCullough：窗口内的市场帖是 Anthropic 上市前的中国问题。他写自己的“家庭账户”当前前三大 ETF，帖文没有列出代码，这里不猜。
- The Information：融资压力看 CoreWeave，安全需求看 Datadog 和 Thoma Bravo，上市看 Anthropic。三件事不要收成“AI 结束了”。

**财报周的顺序。** 先看已经写进信用和循环融资的名字，博通、英伟达、Anthropic、CoreWeave，再看 CNBC 点名的 Alphabet、微软、亚马逊。Meta 的 1350 亿到 1450 亿美元是 The Transcript 贴出的已经收窄的区间，用来对照这三家会不会给出更大的资本开支，而不是用来重做 Meta 的交易。应用材料只出现在 Seeking Alpha 的贡献者标题里。

**明确留在观察、不放进计划的东西。** Cramer、Cathie Wood、ARK、Gary Black、Liz Ann Sonders、Timiraos、Gromen、Raoul Pal 这天没有可引用的新判断。Ackman 的帖是以色列政治。Dalio 的帖是原则。Hedgeye 主号沉默，只有 Keith 的一条客座链接。彭博主号和德意志银行的时间线这次没有形成可用的周日样本。Benzinga 对 Schiff 崩盘警告和 Munster“还早”的转述，保持为媒体标题。

## 帖文索引

地缘与柴油：[油价接近 117、没有谈判](https://x.com/business/status/2114030414805225572)、[做完或做交易](https://x.com/DeItaone/status/2114090697406271754)、[柴油船驶向纽约](https://x.com/FoxBusiness/status/2114122284411576830)、[鲁比奥谈柴油制裁](https://x.com/FirstSquawk/status/2114286034150383854)、[胡塞打延布](https://x.com/financialjuice/status/2114070031604838740)、[中国进口](https://x.com/RealVision/status/2114296969686307239)、[特朗普谈油泵](https://x.com/unusual_whales/status/2114214871374127238)。

广度与结构：[50 日均线 61%](https://x.com/KobeissiLetter/status/2114083152419316145)、[10 月 6 日的窄高点](https://x.com/michaeljburry/status/2114118998392758386)、[平均股票上涨](https://x.com/RyanDetrick/status/2114108495851110406)、[等权在 2000 年](https://x.com/bespokeinvest/status/2114128495324610626)、[QQQ 与标普的认沽偏度](https://x.com/spotgamma/status/2114034437444997177)、[El-Erian 的一周](https://x.com/elerianm/status/2114071006633501034)。

AI 与信用：[卖到 2028](https://x.com/saxena_puru/status/2114203315563057399)、[马斯克的动机](https://x.com/AndreasSteno/status/2114326677379780630)、[博通与英伟达的循环融资](https://x.com/unusual_whales/status/2114114963803406482)、[CoreWeave](https://x.com/theinformation/status/2114039262072934873)、[Slok 论收益率](https://x.com/lisaabramowicz1/status/2114029845823004932)、[大型科技以外回报为零](https://x.com/DeItaone/status/2114301898060611618)、[高盛说买跌](https://x.com/zerohedge/status/2114099642304466972)、[电力是约束](https://x.com/chamath/status/2114093525059174868)。

交叉资产：[美联储预计不动](https://x.com/FirstSquawk/status/2114244165420855399)、[比特币 8 万美元](https://x.com/PeterSchiff/status/2114034479949848775)、[黄金回到 4000 下方](https://x.com/KitcoNewsNOW/status/2114117204698403006)、[白银空头](https://x.com/KobeissiLetter/status/2114037773447372865)、[法国债](https://x.com/WSJmarkets/status/2114289024718324004)、[制造业 PMI](https://x.com/KobeissiLetter/status/2114113892385464685)、[财报周](https://x.com/CNBC/status/2114325598310969717)。

## 附录：按粉丝数排列的 100 个账号

粉丝数为 2026-10-25 抓取时的公开读数。原创条数是北京时间当天窗口内的原创帖。First Squawk 的 80 是分页下限。德意志银行的 0 是读取失败。彭博主号的 0 来自一条明显不完整的时间线，最新可见帖停在 10 月 12 日。

| 排名 | 账号 | 粉丝 | 窗口内原创 |
|---:|---|---:|---:|
| 1 | [@Reuters](https://x.com/Reuters) | 26,432,478 | 87 |
| 2 | [@TheEconomist](https://x.com/TheEconomist) | 26,317,475 | 66 |
| 3 | [@WSJ](https://x.com/WSJ) | 22,277,711 | 61 |
| 4 | [@Forbes](https://x.com/Forbes) | 20,323,441 | 13 |
| 5 | [@business](https://x.com/business) | 10,483,265 | 46 |
| 6 | [@mcuban](https://x.com/mcuban) | 8,558,995 | 0 |
| 7 | [@FT](https://x.com/FT) | 7,100,992 | 22 |
| 8 | [@CNBC](https://x.com/CNBC) | 6,257,798 | 14 |
| 9 | [@unusual_whales](https://x.com/unusual_whales) | 5,423,386 | 13 |
| 10 | [@MarketWatch](https://x.com/MarketWatch) | 4,645,274 | 1 |
| 11 | [@paulkrugman](https://x.com/paulkrugman) | 4,420,920 | 0 |
| 12 | [@BusinessInsider](https://x.com/BusinessInsider) | 4,362,953 | 15 |
| 13 | [@zerohedge](https://x.com/zerohedge) | 3,433,233 | 30 |
| 14 | [@ReutersBiz](https://x.com/ReutersBiz) | 3,419,848 | 0 |
| 15 | [@BillAckman](https://x.com/BillAckman) | 3,034,672 | 1 |
| 16 | [@CathieDWood](https://x.com/CathieDWood) | 2,995,240 | 0 |
| 17 | [@KobeissiLetter](https://x.com/KobeissiLetter) | 2,696,898 | 4 |
| 18 | [@RayDalio](https://x.com/RayDalio) | 2,554,055 | 1 |
| 19 | [@jimcramer](https://x.com/jimcramer) | 2,504,747 | 0 |
| 20 | [@chamath](https://x.com/chamath) | 2,471,636 | 4 |
| 21 | [@APompliano](https://x.com/APompliano) | 2,437,392 | 3 |
| 22 | [@FortuneMagazine](https://x.com/FortuneMagazine) | 2,244,833 | 12 |
| 23 | [@michaeljburry](https://x.com/michaeljburry) | 2,133,357 | 1 |
| 24 | [@YahooFinance](https://x.com/YahooFinance) | 2,072,827 | 1 |
| 25 | [@markets](https://x.com/markets) | 2,045,345 | 0 |
| 26 | [@DeItaone](https://x.com/DeItaone) | 1,966,319 | 6 |
| 27 | [@PeterSchiff](https://x.com/PeterSchiff) | 1,770,747 | 7 |
| 28 | [@RampCapitalLLC](https://x.com/RampCapitalLLC) | 1,734,461 | 1 |
| 29 | [@NYSE](https://x.com/NYSE) | 1,699,357 | 0 |
| 30 | [@CNNBusiness](https://x.com/CNNBusiness) | 1,693,548 | 0 |
| 31 | [@theinformation](https://x.com/theinformation) | 1,606,585 | 12 |
| 32 | [@federalreserve](https://x.com/federalreserve) | 1,598,660 | 0 |
| 33 | [@Investingcom](https://x.com/Investingcom) | 1,531,407 | 9 |
| 34 | [@RaoulGMI](https://x.com/RaoulGMI) | 1,507,694 | 0 |
| 35 | [@WSJmarkets](https://x.com/WSJmarkets) | 1,469,006 | 3 |
| 36 | [@Bloomberg](https://x.com/Bloomberg) | 1,350,066 | 0 |
| 37 | [@TheStreet](https://x.com/TheStreet) | 1,228,852 | 41 |
| 38 | [@SquawkCNBC](https://x.com/SquawkCNBC) | 1,193,983 | 0 |
| 39 | [@Stocktwits](https://x.com/Stocktwits) | 1,192,496 | 0 |
| 40 | [@andrewrsorkin](https://x.com/andrewrsorkin) | 1,181,197 | 0 |
| 41 | [@USTreasury](https://x.com/USTreasury) | 1,163,673 | 0 |
| 42 | [@GoldmanSachs](https://x.com/GoldmanSachs) | 1,156,103 | 0 |
| 43 | [@LynAldenContact](https://x.com/LynAldenContact) | 1,142,976 | 3 |
| 44 | [@elerianm](https://x.com/elerianm) | 1,117,121 | 2 |
| 45 | [@BlackRock](https://x.com/BlackRock) | 1,080,955 | 0 |
| 46 | [@SCMPNews](https://x.com/SCMPNews) | 1,038,142 | 25 |
| 47 | [@financialjuice](https://x.com/financialjuice) | 954,135 | 16 |
| 48 | [@BankofAmerica](https://x.com/BankofAmerica) | 946,740 | 0 |
| 49 | [@tradingview](https://x.com/tradingview) | 906,543 | 0 |
| 50 | [@BloombergTV](https://x.com/BloombergTV) | 892,953 | 1 |
| 51 | [@nytimesbusiness](https://x.com/nytimesbusiness) | 889,331 | 0 |
| 52 | [@FoxBusiness](https://x.com/FoxBusiness) | 879,746 | 5 |
| 53 | [@charliebilello](https://x.com/charliebilello) | 873,453 | 0 |
| 54 | [@axios](https://x.com/axios) | 861,353 | 0 |
| 55 | [@jpmorgan](https://x.com/jpmorgan) | 859,398 | 0 |
| 56 | [@Citi](https://x.com/Citi) | 853,469 | 0 |
| 57 | [@LizAnnSonders](https://x.com/LizAnnSonders) | 846,362 | 0 |
| 58 | [@ARKInvest](https://x.com/ARKInvest) | 822,367 | 0 |
| 59 | [@biancoresearch](https://x.com/biancoresearch) | 791,444 | 3 |
| 60 | [@MorganStanley](https://x.com/MorganStanley) | 757,748 | 0 |
| 61 | [@CNBCnow](https://x.com/CNBCnow) | 752,474 | 0 |
| 62 | [@morganhousel](https://x.com/morganhousel) | 724,386 | 0 |
| 63 | [@TrendSpider](https://x.com/TrendSpider) | 718,830 | 9 |
| 64 | [@Nouriel](https://x.com/Nouriel) | 700,876 | 0 |
| 65 | [@BrianFeroldi](https://x.com/BrianFeroldi) | 673,520 | 6 |
| 66 | [@Carl_C_Icahn](https://x.com/Carl_C_Icahn) | 646,260 | 0 |
| 67 | [@LukeGromen](https://x.com/LukeGromen) | 638,694 | 0 |
| 68 | [@DeutscheBank](https://x.com/DeutscheBank) | 637,898 | 0 |
| 69 | [@EricBalchunas](https://x.com/EricBalchunas) | 629,446 | 1 |
| 70 | [@garyblack00](https://x.com/garyblack00) | 584,232 | 0 |
| 71 | [@Barchart](https://x.com/Barchart) | 577,315 | 1 |
| 72 | [@FirstSquawk](https://x.com/FirstSquawk) | 574,384 | 80 |
| 73 | [@eWhispers](https://x.com/eWhispers) | 571,945 | 0 |
| 74 | [@MadMoneyOnCNBC](https://x.com/MadMoneyOnCNBC) | 543,552 | 0 |
| 75 | [@AswathDamodaran](https://x.com/AswathDamodaran) | 520,823 | 0 |
| 76 | [@carlquintanilla](https://x.com/carlquintanilla) | 514,593 | 0 |
| 77 | [@LiveSquawk](https://x.com/LiveSquawk) | 505,741 | 0 |
| 78 | [@UBS](https://x.com/UBS) | 499,499 | 0 |
| 79 | [@NickTimiraos](https://x.com/NickTimiraos) | 493,781 | 0 |
| 80 | [@NikkeiAsia](https://x.com/NikkeiAsia) | 489,303 | 40 |
| 81 | [@KeithMcCullough](https://x.com/KeithMcCullough) | 478,462 | 6 |
| 82 | [@Fxhedgers](https://x.com/Fxhedgers) | 472,096 | 1 |
| 83 | [@MacroAlf](https://x.com/MacroAlf) | 465,601 | 0 |
| 84 | [@IBDinvestors](https://x.com/IBDinvestors) | 456,010 | 5 |
| 85 | [@TheStalwart](https://x.com/TheStalwart) | 453,354 | 5 |
| 86 | [@CNBCFastMoney](https://x.com/CNBCFastMoney) | 451,619 | 1 |
| 87 | [@Hedgeye](https://x.com/Hedgeye) | 447,532 | 0 |
| 88 | [@GoldTelegraph](https://x.com/GoldTelegraph) | 447,330 | 3 |
| 89 | [@lisaabramowicz1](https://x.com/lisaabramowicz1) | 444,851 | 1 |
| 90 | [@BeckyQuick](https://x.com/BeckyQuick) | 440,488 | 0 |
| 91 | [@barronsonline](https://x.com/barronsonline) | 408,021 | 2 |
| 92 | [@JavierBlas](https://x.com/JavierBlas) | 404,946 | 0 |
| 93 | [@saxena_puru](https://x.com/saxena_puru) | 403,552 | 4 |
| 94 | [@Vanguard_Group](https://x.com/Vanguard_Group) | 399,878 | 0 |
| 95 | [@robin_j_brooks](https://x.com/robin_j_brooks) | 398,377 | 1 |
| 96 | [@Fidelity](https://x.com/Fidelity) | 398,371 | 0 |
| 97 | [@awealthofcs](https://x.com/awealthofcs) | 395,782 | 0 |
| 98 | [@RealVision](https://x.com/RealVision) | 392,247 | 3 |
| 99 | [@Schuldensuehner](https://x.com/Schuldensuehner) | 385,493 | 0 |
| 100 | [@GuyAdami](https://x.com/GuyAdami) | 382,224 | 0 |
