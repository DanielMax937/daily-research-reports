# AI论文日报｜2026-10-28
## 本次交付性质与实际覆盖

**受限报告，不是已核验的 alphaXiv 热门 Top10。** 本次没有取得可确认排序与时间窗口的当日热榜，不能完成十篇按榜深读；以下仅保留当天普通首页观察，以及一篇明确标注为“榜外补充”的原文与代码定向阅读。没有用旧榜、搜索摘要或个人偏好补足名次。

- 报告所属日期：北京时间 2026-10-28（Asia/Shanghai）。
- 正常首页抓取：北京时间约 11:27（原始 UTC 03:27）；原文与代码阅读：11:28–11:30（UTC 03:28–03:30）。
- 实际入口：[alphaXiv 首页](https://www.alphaxiv.org/)，页面标题 Explore，页面文案为 Follow the latest research。
- 排序名称、热度时间窗口：本次均未核实；**默认研究流不能视为 Trending / Popular / Hot**。
- 既有访问限制：昨日 Most Liked / 7 Days 页面遭遇安全验证，已停止该受限榜单访问。本次没有重试该地址、换路恢复同一受限榜单、解决验证码或绕过验证。正常首页可读不代表热榜权限或可用性已经恢复。
- 未执行任何论文代码、安装依赖、训练或复现实验。正文中的实验结论均为作者报告，而非独立复现。
- 不把网页读取失败解释为“没有论文”“没有讨论”或“热度下降”。

## 一、当天可见研究卡片（不是热榜排名）

下表顺序仅记录正常首页出现顺序；第五项来自会议推荐区域。指标为单次页面显示快照，不代表新增量、增长率或全站热度。日期沿用页面显示，未给时区或精确发布时间的，不擅自换算为北京时间发布时间。

| 首页位置 | 论文/页面 | 页面日期 | Likes / Views | 本次阅读深度 |
|---|---|---|---|---|
| 普通卡片1 | [Learning Force-Reactive Humanoid Loco-Manipulation](https://www.alphaxiv.org/abs/2610.35862) | 2026-10-26 | 8 / 241 | 仅卡片；原文未读 |
| 普通卡片2 | [Work Agents: Systems, Capabilities, and Optimization](https://www.alphaxiv.org/abs/2610.35845) | 2026-10-26 | 18 / 279 | 仅卡片；本次 arXiv HTML 请求返回404，未据卡片评审方法 |
| 普通卡片3 | [How High Can GPT-6 Astra Climb in Contact-Rich Manipulation? PhysLadder: A Hierarchical, Matched Sim-Real Benchmark for Physical Interaction](https://www.alphaxiv.org/abs/2610.34527) | 2026-10-25 | 18 / 292 | 仅卡片；原文未读 |
| 普通卡片4 | [Profiling a Frontier Agent with EBench: From Direct Control to Harness with Policy](https://www.alphaxiv.org/abs/2610.35832) | 2026-10-26 | 12 / 108 | 下文榜外补充，读取原文方法、实验与代码入口 |
| 会议推荐卡片 | [An Efficient Algorithm for Thresholding Monte Carlo Tree Search](https://www.alphaxiv.org/abs/2601.22600) | 2026-01-30 | 1 / 未显示 | 仅卡片；非当天新论文，未纳入深读 |

以上卡片只能证明本次页面可见这些条目。其作者完整名单、论文修订日期、榜单位置及传播因果，除下文单独核实者外均未确认。未读的四篇不生成七段伪评审；第6–10名未知，不占位造题。

## 二、榜外补充：EBench 原文与代码定向阅读

> 选题来自当天默认流，**没有证据证明其进入当日热门Top10**。这不是对完整基准、所有附录与全仓库的审查。

### 1. 基本信息
- 标题：Profiling a Frontier Agent with EBench: From Direct Control to Harness with Policy。
- 作者：Yifei Yao、Yude Zou、Guanbo Jiao 等；完整名单见[原文](https://arxiv.org/html/2610.35832)。
- [arXiv](https://arxiv.org/abs/2610.35832)；[alphaXiv](https://www.alphaxiv.org/abs/2610.35832)。
- 本次读取版本：HTML标记 v1，2026-10-26；精确提交时刻未核实。
- 领域：Robotics、Agents、Evaluation、AI Systems。

### 2. 解决的问题
研究通用模型直接控制与调用已训练机器人策略的能力差别，而非只比较一个总体分数。阅读依据：[§1、§3](https://arxiv.org/html/2610.35832#S3)。

### 3. 核心方法
直接控制：RGB/机器人状态→模型→航点→执行→新观察。混合控制增加冻结策略调用，每次1–300步，仍使用固定任务指令，不能传入新子目标。[§4、§6.1](https://arxiv.org/html/2610.35832#S4)

### 4. 最大亮点
价值在配对诊断：既记录组合新增成功，也检查组合破坏原有成功的情况；不是“工具越多越强”的单向展示。[§6.2–6.4](https://arxiv.org/html/2610.35832#S6)

### 5. 实验能否支持结论
作者在26任务、510回合中报告任务等权成功率：直接控制46.7%，加入两种策略分别53.0%、56.0%。高精度组仍弱。单模型、单同步仿真基准不足以证明真实机器人安全、异步表现或端到端成本优势。未独立复现。[表1–2、§7限制](https://arxiv.org/html/2610.35832#S7)

### 6. 现在为何热门
只能确认首页可见12 Likes、108 Views；热榜地位与传播原因均未证实。没有读取到可支持“突然爆火”的原始讨论或连续Star增长，不用机构与模型名称代替因果证据。

### 7. 工程价值
**dot的迁移推断，不是论文已验证的通用结论：** coding agent、MCP或工作流代理也宜把“执行成功”和“系统最终状态正确”分开；先设计工具入口条件、退出验收及交接状态，再比较组合收益。不能从机器人实验直接推定网页Agent或RAG会提升相同比例。

#### 代码实际检查与复现边界

读取仓库：[InternRobotics/EBench](https://github.com/InternRobotics/EBench)，固定到本次读取的 main commit [355fe56d17eee77c659df5cdda980b205bdba3ce](https://github.com/InternRobotics/EBench/commit/355fe56d17eee77c659df5cdda980b205bdba3ce)。

实际检查：
1. 根目录与 scripts 目录。
2. [README.md](https://github.com/InternRobotics/EBench/blob/355fe56d17eee77c659df5cdda980b205bdba3ce/README.md)：该仓库是基准入口，仿真服务、Python客户端和数据分别在关联项目；不能把入口仓库等同所有运行代码。
3. [scripts/launch_pi_onlineeval.sh](https://github.com/InternRobotics/EBench/blob/355fe56d17eee77c659df5cdda980b205bdba3ce/scripts/launch_pi_onlineeval.sh)：脚本先逐客户端启动策略服务器，端口按8000+2×索引分配，再启动评测客户端，将horizon、模型地址及评测运行参数传入，等待客户端结束后清理策略进程。默认重规划horizon为30，实际环境/模型路径仍需填写。
4. README列出基线包装层、子模块及GenManip客户端；本次**没有**递归检查这些关联仓库、模型权重、依赖锁定、完整Astra harness或全部任务判分代码。

**可确认：**公开入口及启动脚本存在；**不可确认：**按论文结果完整复现所需材料是否齐全、当前环境可运行性、具体GPU总成本。本次未提交评测或使用任何服务凭证。

**日期差异需保留：**读取到的仓库commit时间为2026-09-24 12:21:09 UTC（北京时间20:21:09），README更新表把Astra报告列在2026-09；本次arXiv HTML标记v1为2026-10-26。这些可分别属于不同发布阶段，也可能存在资料日期差异；未核实首发链路，不能将其合并成“今天发布”。

#### 阅读记录
- 已读：Abstract、Introduction；§3定义与控制接口；§4实验设置及表1；§6方法与表2、表3、失败诊断、成本和交接限制；§7结论与限制。
- 关键量采用HTML表格文字，不从缩略图估数。
- 未完整阅读：§5全部案例、附录A–E、全部相关工作全文；未检查PDF图像、项目demo或可复现实验日志。
- [作者项目页（原文给出的链接，本次未深读）](https://internrobotics.github.io/EBench-Astra-Tech-Report/)。
- 论文发布和作者实验报告是可读事实；模型通用能力、真实硬件可靠性与跨领域迁移仍不是已证实结论。

## 三、跨论文总结

### A. 今天最值得深入读的3篇
**无法负责任地选满3篇。** 当日Top10未知，仅有一篇完成上述定向原文阅读。
- 当前可推荐继续读EBench报告的§4、§6和§7：先对照指标口径，再检查执行器交接与失败定义。代码先打开上述启动脚本，但完整复现应另行审阅关联客户端和仿真端。
- Work Agents仅列为待取得原文的候选，不作为已深读推荐；其本次[HTML入口](https://arxiv.org/html/2610.35845)返回404，不能据此断言论文不存在。

### B. 今天的研究趋势
没有经过核验的当日十篇样本，**不提炼3–5条行业趋势**。
唯一有限观察是：正常首页中可见多项机器人/控制相关题目，EBench补充材料具体涉及代理与策略的交接。前者是页面构成，后者是一篇研究；二者都不足以证明全站研究方向持续升温。

### C. 和昨天相比
比较依据为已留存并读取的[2026-10-27实际报告](https://github.com/DanielMax937/daily-research-reports/blob/b8ae0ee0fa34a2474365fe61fe5fd2f13de66d91/2026-10-27/ai-papers.md)，而非虚构昨日榜单。

- 昨日同样未核得当日热榜；其默认流出现PhysLadder，本次默认流再次可见。**只能称再次可见，不能称连续热门或连续Top10。**
- Work Agents、Force-Reactive、EBench报告是相对昨日留存默认卡片观察的新增可见条目，不等于新进入热榜。
- 昨日留存卡片中未在本次首页看到的条目，不能据此判定降温或出榜。
- 最近一份已留存的确认热榜基线是[2026-10-26报告](https://github.com/DanielMax937/daily-research-reports/blob/b158867ba91e01a45a7afa22d9478f0dcb283f8a/2026-10-26/ai-papers.md)。它不是昨日或今日榜单，故不计算今日名次升降。
- 今日新增的是EBench原文/代码的定向阅读证据，不是热榜状态改善。已建立今天的“默认流观察+榜单缺口”基线，供后续准确区分页面观察和排名恢复。

## 四、未完成项与后续确认条件

1. 当天真实热门排序、窗口及前10仍未取得；因此十篇完整七段评审、按热榜挑选三篇及跨日排名比较均未完成。
2. 只有在允许访问的正常页面明确显示热榜排序及时间窗口，并能读到前10时，才能恢复正式Top10报告；本次不试图恢复已停止的受限入口。
3. 工程阅读仅为单篇定向分析，没有运行验证。若未来要复现，需单独核验环境、权重与评价协议，不自动安装或执行未知代码。
4. 本报告不自动改变其他任务、提醒设置、代码、账户或任何外部研究对象。

