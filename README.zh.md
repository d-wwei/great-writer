# Great Writer

一个 AI Agent 写作技能。8 种写作模式，9 个核心模块，中英文双语。

<a href="./README.md">English</a>

---

## 解决什么问题

你让 AI 写东西，收到的第一句是：

> "随着人工智能技术的快速发展，XX 产品凭借其强大的功能..."

问题不在模型。问题在于你没给它写作系统。

| 场景 | 没有 Great Writer | 有 Great Writer |
|------|------------------|----------------|
| 技术文章 | "随着云计算的蓬勃发展..." | "你的服务器账单上个月涨了 3 倍。不是流量涨了。" |
| 营销文案 | "一站式解决方案，赋能企业数字化转型..." | "3 分钟部署。零运维。每月省 $2,400。" |
| 研究报告 | "该行业具有广阔的发展前景..." | "Q4 融资 $4.7B，同比增长 340%。三个信号值得关注。" |
| 小红书 | "这款产品真的非常好用！" | "用了两周，说真实感受。值，但有一个坑要避开。" |
| 技术文档 | "本文档旨在为开发者提供全面的指南..." | "安装 → 配置 → 第一个请求 → 处理错误 → 生产部署。" |

Great Writer 给 AI 加载一套写作系统：写前强制调研，写后自动去 AI 味，每个场景有专属模板。

---

## 快速开始

```bash
git clone https://github.com/d-wwei/great-writer.git
ln -sf "$(pwd)/great-writer" ~/.claude/skills/great-writer
```

对话中说"写文章"、"小红书种草"、"write a README"触发。

---

## 能做什么

**写 8 种内容：**

| 模式 | 触发词 | 适用场景 |
|------|--------|---------|
| 技术产品文章 | 写文章、公众号、博客 | 微信公众号、技术博客、产品发布 |
| 营销文案 | 文案、landing page | 落地页、社交媒体、广告 |
| 研究报告 | 白皮书、竞品分析、投研 | 白皮书、竞品报告、行业研究 |
| 小红书笔记 | 小红书、种草 | 种草、干货教程、经验分享 |
| 技术文档 | README、API docs、changelog | README、API 文档、内部指南 |
| 改写润色 | 改写、润色、帮我改 | 现有草稿、邮件、备忘录 |
| 编辑审稿 | 审稿、帮我看看 | 审稿、内容质检 |
| 创意写作 | 写小说、写散文、写演讲稿 | 小说、散文、演讲稿、剧本 |

**每篇内容走 5 步管道：**

```
调研 → 起稿 → 审校 → 去AI味 → 终检
```

每步可独立重跑。说"去 AI 味"直接跳到第 4 步，不用从头来。

**5 个增强能力（按需激活）：**

| 能力 | 触发方式 |
|------|---------|
| 风格学习 | 提供参考文本，说"学习这个风格" |
| 多平台适配 | 说"转成小红书版"或"adapt for Twitter" |
| 写作记忆 | 跨会话记住品牌名、术语、数据、风格 |
| SEO/GEO 优化 | 说"SEO优化"，面向网页发布时自动建议 |
| 数据可视化 | 数据密集内容自动触发图表建议 |

---

## 工作原理

分层架构。SKILL.md 做路由，core/ 放共享能力，modes/ 放场景模板。每次调用只加载需要的模块。

```
great-writer/
├── SKILL.md                    # 路由 + 管道定义
├── core/                       # 共享核心（9 个模块）
│   ├── writing-dna.md          # 6 条写作原则
│   ├── research-protocol.md    # 写前调研协议
│   ├── review-protocol.md      # 审校协议
│   ├── humanizer.md            # 去 AI 味协议
│   ├── style-learner.md        # 风格学习
│   ├── adapt-protocol.md       # 多平台适配
│   ├── writing-memory.md       # 写作记忆
│   ├── seo-layer.md            # SEO/GEO 优化
│   └── visualization.md        # 数据可视化
├── modes/                      # 场景模板（8 个模式）
│   ├── tech-article.md         # 技术产品文章
│   ├── marketing-copy.md       # 营销文案
│   ├── research-report.md      # 研究报告
│   ├── xiaohongshu.md          # 小红书笔记
│   ├── technical-docs.md       # 技术文档
│   ├── rewrite.md              # 改写润色
│   ├── editorial-review.md     # 编辑审稿
│   └── creative-writing.md     # 创意写作
├── scripts/bundle.sh           # 单文件合并脚本
├── great-writer-bundled.md     # 合并版（不支持多文件的 Agent 用）
└── README.md
```

---

## 安装

**Claude Code：**

```bash
git clone https://github.com/d-wwei/great-writer.git
ln -sf "$(pwd)/great-writer" ~/.claude/skills/great-writer
```

**Codex / agentskills.io：** 标准 Skill 目录结构，直接导入。

**其他 Agent：** 用 `great-writer-bundled.md` 作为 system prompt 注入。

---

## 兼容性

| 平台 | 方式 |
|------|------|
| Claude Code | 原生 Skill，自动触发 |
| Cursor / Windsurf | 作为 rules 文件加载 |
| Codex | agentskills.io 格式兼容 |
| ChatGPT | 粘贴 SKILL.md 到 Custom Instructions |
| 其他 LLM | 注入 bundled 版本到 system prompt |

---

## 去 AI 味

内置 30+ 条中英文黑名单。中文禁："随着"、"赋能"、"一站式"。英文禁："leverage"、"delve into"、"game-changing"。

黑名单只是第一层。第二层重塑节奏：打破 AI 偏爱的完美并列结构，制造句长变化，用"上线第一周 2,847 个用户"替代"很多用户反馈"。

---

## 工具集成

不依赖外部工具。有工具时自动增强：

| 能力 | 可用工具 | 没有时 |
|------|---------|--------|
| 搜索 | Tavily, WebSearch, Brave | 引导用户提供素材 |
| 抓取 | Firecrawl, WebFetch | 请用户粘贴内容 |
| 排版 | typeset skill | 输出纯 Markdown |

---

## License

MIT
