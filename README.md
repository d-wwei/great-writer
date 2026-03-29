<p align="center">
  <h1 align="center">Great Writer</h1>
  <p align="center">让 AI 写出人愿意读的内容</p>
  <p align="center">
    <a href="#三大核心能力">核心能力</a> · <a href="#8-种写作模式">写作模式</a> · <a href="#增强能力">增强能力</a> · <a href="#安装">安装</a> · <a href="./README.en.md">English</a>
  </p>
</p>

---

## 一句话总结

一套通用 AI 写作技能，覆盖**技术文章、营销文案、研究报告、小红书笔记、技术文档、改写润色、编辑审稿、创意写作**八大场景，配备风格学习、多平台适配、写作记忆、SEO 优化、数据可视化五大增强模块。调研驱动、全链路管道、去 AI 味。

## 它解决什么问题

让 AI 写东西，你大概率会收到这种东西：

> "随着人工智能技术的快速发展，XX 产品凭借其强大的功能和出色的性能，为用户带来了前所未有的体验..."

> "In today's rapidly evolving technological landscape, our product leverages cutting-edge AI capabilities..."

**没人想读。** 没有数据、没有痛点、没有画面感，纯粹的 AI 套话堆砌。而且不管你写的是公众号、落地页、研究报告还是小红书笔记，AI 吐出来的东西都是同一个味——空洞、模式化、一眼假。

**加载 Great Writer 之后：**

| 你在写什么 | 没有 Great Writer | 有 Great Writer |
|-----------|------------------|----------------|
| 技术文章 | "随着云计算技术的蓬勃发展，我们推出了一款强大的产品..." | "你的服务器账单上个月涨了 3 倍。不是流量涨了——是你在为空转算力买单。" |
| 营销文案 | "我们的产品功能强大、性能出色，为您提供一站式解决方案..." | "3 分钟部署。零运维。每月省 $2,400。" |
| 研究报告 | "综合以上分析，该行业具有广阔的发展前景和巨大的市场潜力..." | "2025 年 Q4 该赛道融资总额 $4.7B，同比增长 340%。三个信号值得关注。" |
| 小红书笔记 | "这款产品真的非常好用，强烈推荐给大家！" | "用了两周，说说真实感受。先说结论：值，但有一个坑你要避开。" |
| 技术文档 | "本文档旨在为开发者提供全面的API使用指南..." | "5 分钟跑通。安装 → 配置 → 第一个请求 → 处理错误 → 生产部署。" |
| 改写润色 | "以下是修改后的版本：[几乎原封不动]" | "诊断：3 个结构问题、5 处 AI 套话、2 个逻辑断裂。逐条修复，附修改说明。" |
| 编辑审稿 | "文章写得很好，建议适当增加一些数据支撑。" | "结构 7/10、论证 5/10、节奏 6/10、去 AI 味 4/10。四层审稿报告 + 优先修复清单。" |
| 创意写作 | "月光洒在湖面上，如同银色的绸缎，美得令人窒息。" | "湖面没有月光。只有码头尽头那盏快烧坏的灯，把水照成生锈的颜色。" |

## 三大核心能力

### 1. 调研驱动：不调研不动笔

大部分 AI 写作的问题不是文笔差，而是**内容空**。AI 只从训练数据或你那句简短的 prompt 出发，写出来的东西放到任何产品上都能套用。

Great Writer 强制走三步调研协议：
- **受众定位** — 谁在读？技术水平如何？在什么场景下看到这篇内容？
- **排除分析** — 现有方案把谁挡在门外了？这群人就是你最有力的切入点
- **深度素材挖掘** — 有搜索工具就主动查竞品、找数据；没有工具就向用户要素材，绝不凭空编

不完成调研，不允许动笔。

### 2. 全链路管道：5 个阶段，每步可独立重跑

```
调研 → 起稿 → 审校 → 去AI味 → 终检
```

| 阶段 | 做什么 | 加载模块 |
|------|--------|---------|
| 调研 | 受众分析、排除分析、素材挖掘 | `core/research-protocol.md` |
| 起稿 | 按模式模板 + 写作 DNA 输出初稿 | `core/writing-dna.md` + `modes/*.md` |
| 审校 | 结构审查 + 逻辑审查 + 事实核查 | `core/review-protocol.md` |
| 去AI味 | 黑名单拦截 + 节奏重塑 | `core/humanizer.md` |
| 终检 | 跑模式自检清单，不过不发 | 各 mode 文件内的 checklist |

用户可以随时跳转到任意阶段：说"重新调研"就回第 1 步，说"去 AI 味"就直接跳第 4 步。每个阶段独立运行，不需要从头来过。

### 3. 去 AI 味：双语黑名单 + 节奏重塑

**Level 1 — 硬规则：黑名单拦截**

中文禁用："随着...的发展"、"众所周知"、"在当今时代"、"不言而喻"、"值得一提的是"、"毋庸置疑"...
英文禁用："In today's rapidly evolving..."、"It's worth noting..."、"Game-changing"、"Delve into"、"Robust"、"Seamless"...

无数据支撑的形容词一律禁用：强大的、出色的、卓越的、创新的、领先的、赋能、颠覆...

**Level 2 — 软规则：节奏重塑**

- 句长变化：短句打骨架，长句给喘息空间，不允许连续三句差不多长
- 非对称结构：AI 最爱完美并列的三点列表，人类不那么写
- 具体细节替换抽象表述："很多用户反馈" → "上线第一周 2,847 个用户"
- 反问句制造节奏：每篇 1-2 个，不滥用
- 模式专属覆写：小红书允许更多 emoji 和网络用语，技术文档禁止反问句和闲话

## 8 种写作模式

| 模式 | 说明 | 典型平台 |
|------|------|---------|
| **技术产品文章** | 数据驱动的技术产品介绍，9 模块结构，痛点开场 | 微信公众号、技术博客、产品发布 |
| **营销文案** | 转化导向，CTA 驱动，支持落地页/社交媒体/广告多种格式 | Landing Page、社交媒体、广告投放 |
| **研究报告** | 深度分析，数据严谨，有结论有建议，适合决策层阅读 | 白皮书、竞品分析、行业研究、投研 |
| **小红书笔记** | 有用+真实+好看，个人视角种草，视觉化排版 | 小红书、种草社区 |
| **技术文档** | 清晰 > 完整 > 优雅，5 分钟可上手，面向开发者 | README、API 文档、Changelog、内部指南 |
| **改写润色** | 诊断现有文稿的问题并修复，不从零写起，保留原文意图 | 邮件、备忘录、已有草稿、任意文本 |
| **编辑审稿** | 四层审稿框架（结构 / 论证 / 节奏 / 去 AI 味），给反馈不代笔 | 审稿、内容质检、写作教练 |
| **创意写作** | 小说、散文、演讲稿、剧本，画面感优先，show don't tell | 个人公众号、文学创作、演讲、脚本 |

## 架构

```
great-writer/
├── SKILL.md                    # 入口：路由 + 管道定义
├── core/                       # 通用核心模块（所有模式共享）
│   ├── writing-dna.md          #   6 条写作原则
│   ├── research-protocol.md    #   调研协议（3 步）
│   ├── review-protocol.md      #   审校协议（3 维度）
│   ├── humanizer.md            #   去 AI 味协议（2 级）
│   ├── style-learner.md        #   风格学习：提取参考文本的风格指纹
│   ├── adapt-protocol.md       #   多平台适配：一稿转 9 个平台
│   ├── writing-memory.md       #   写作记忆：跨会话持久化
│   ├── seo-layer.md            #   SEO/GEO 优化层（可选）
│   └── visualization.md        #   数据可视化建议
├── modes/                      # 写作模式模板
│   ├── tech-article.md         #   技术产品文章
│   ├── marketing-copy.md       #   营销文案
│   ├── research-report.md      #   研究报告
│   ├── xiaohongshu.md          #   小红书笔记
│   ├── technical-docs.md       #   技术文档
│   ├── rewrite.md              #   改写润色
│   ├── editorial-review.md     #   编辑审稿
│   └── creative-writing.md     #   创意写作
└── README.md / README.en.md    # 你正在读的文件
```

分层设计：`SKILL.md` 负责路由和管道编排，`core/` 是所有模式共享的写作基因和增强能力模块，`modes/` 是各场景的结构模板和自检清单。每个文件独立可读，按需加载。

## 增强能力

以下模块按需激活，不触发则不加载：

| 能力 | 触发方式 | 模块 |
|------|---------|------|
| **风格学习** | "学习这个风格" / "match this style" / 提供参考文本 | `core/style-learner.md` |
| **多平台适配** | "转成小红书版" / "adapt for Twitter" / "发到所有平台" | `core/adapt-protocol.md` |
| **写作记忆** | "记住这个风格" / "save writing memory" / 任务结束时自动提供 | `core/writing-memory.md` |
| **SEO/GEO 优化** | "SEO优化" / "关键词" / "SEO" / 面向网页发布的内容 | `core/seo-layer.md` |
| **数据可视化** | 数据密集内容自动触发，或 "加图表建议" / "visualize this" | `core/visualization.md` |

这些模块扩展管道，不替代管道。风格学习影响起稿+去AI味阶段，SEO 增强终检阶段，可视化强化起稿阶段。

## 安装

### Claude Code

```bash
# 克隆仓库
git clone https://github.com/d-wwei/great-writer.git

# 创建软链接（macOS / Linux）
ln -sf "$(pwd)/great-writer" ~/.claude/skills/great-writer
```

安装完成后，Claude Code 会在对话中检测到触发词时自动加载该技能。

### Codex / agentskills.io

Great Writer 使用标准的 Skill 目录结构（`SKILL.md` 入口 + 模块文件），兼容 agentskills.io 格式。直接导入仓库即可。

### 其他 Agent

将 `SKILL.md` 的内容作为 system prompt 或上下文注入。核心模块文件（`core/` 和 `modes/`）按 `SKILL.md` 中的引用路径一并提供。

如果你的 Agent 不支持多文件加载，可以将 `SKILL.md` + 所有 `core/*.md` + 对应的 `modes/*.md` 合并为一个文件使用。

## 使用

### 触发词

对话中出现以下关键词会自动激活对应模式：

| 模式 | 中文触发词 | 英文触发词 |
|------|-----------|-----------|
| 技术文章 | 写文章、公众号、博客、产品介绍 | write article, blog post, product article |
| 营销文案 | 文案、推广文、产品文案 | marketing copy, ad copy, landing page |
| 研究报告 | 白皮书、研究报告、竞品分析、投研 | whitepaper, research report, competitive analysis |
| 小红书 | 小红书、种草、笔记 | xiaohongshu |
| 技术文档 | 技术文档、内部文档 | README, API docs, changelog, technical docs |
| 改写润色 | 改写、润色、帮我改 | rewrite, polish, improve this, edit this |
| 编辑审稿 | 审稿、帮我看看 | editorial review, critique this |
| 创意写作 | 写小说、写故事、写散文、写演讲稿 | creative writing, fiction, short story, essay, speech |

### 示例对话

```
你：帮我写一篇公众号文章介绍我们的新产品，核心卖点是速度快 10 倍、价格低 80%
AI：[识别为「技术产品文章」模式]

    好，先做调研。几个问题：
    1. 目标读者是谁？开发者、产品经理、还是决策层？
    2. 主要竞品是哪些？
    3. "快 10 倍"的基准是什么？有具体 benchmark 数据吗？

你：面向开发者，竞品是 XX 和 YY，benchmark 在这个链接：...
AI：[完成调研 → 按 9 模块结构起稿 → 审校 → 去 AI 味 → 终检 → 输出成品]
```

### 阶段跳转

写完之后想单独重跑某个阶段：

| 你说 | 执行 |
|------|------|
| "重新调研" / "re-research" | 回到调研阶段 |
| "重写" / "rewrite" | 回到起稿阶段 |
| "审校" / "review" | 跑审校协议 |
| "去AI味" / "humanize" | 跑去 AI 味协议 |
| "自检" / "check" | 跑终检清单 |

## 兼容性

| 平台 | 支持程度 | 说明 |
|------|---------|------|
| Claude Code | 完整支持 | 原生 Skill 格式，自动触发，多文件按需加载 |
| Claude (chat) | 手动加载 | 将 SKILL.md 内容粘贴到对话开头 |
| Cursor / Windsurf | 完整支持 | 作为 rules 或 context 文件加载 |
| ChatGPT | 手动加载 | 作为 Custom Instructions 或对话上下文注入 |
| Codex / agentskills.io | 兼容 | 标准 Skill 目录结构 |
| 其他 LLM Agent | 手动加载 | 注入 SKILL.md 作为 system prompt |

## 工具集成

Great Writer 不依赖任何外部工具，但有工具时效果更好：

| 能力 | 可用工具 | 没有工具时 |
|------|---------|-----------|
| 网页搜索 | Tavily, WebSearch, Brave | 引导用户提供素材 |
| 内容提取 | Firecrawl, WebFetch, Jina | 请用户粘贴内容 |
| 学术引用 | Scholar, Semantic Scholar | 标记为"需验证" |

## License

MIT
