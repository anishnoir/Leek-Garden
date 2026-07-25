# 🥬 散户.skill

##### Leek Garden（韭菜园）

> 理解韭菜，才能不做韭菜。

**Leek Garden** 是一个行为金融学视角的 A 股散户心理分析工具。它帮助你站在大多数人的对立面思考——不是告诉你买什么、卖什么，而是让你看清"大多数散户现在在想什么、会做什么"。

---

## 🎯 这是什么

A 股市场中，散户（个人投资者）贡献了约 60% 的交易量，但只赚到了不到 10% 的利润。一个核心原因是：**散户的行为模式高度可预测**——贪婪、恐惧、FOMO、羊群效应……这些心理模式反复上演。

这个项目是一个 **多 Agent 兼容的知识库**，它帮助你：

- 🔍 **结合实时新闻和行情数据**，推断当前市场环境下散户的心理状态
- 🏷️ **判断散户大概率会选什么标的**，他们的钱在流向哪里
- 🧠 **识别散户的认知偏差**，避免自己陷入同样的陷阱
- 🔄 **以散户一致性行为作为逆向参考**——别人贪婪时恐惧，别人恐惧时贪婪

---

## 📂 项目结构

```
leek-garden/
├── AGENTS.md                             # 通用 Agent 入口（Codex / Cursor / Windsurf 等）
├── SKILL.md                              # Claude Code Skill 入口
├── README.md                             # 本文件
├── prompts/                              # 通用 Prompt 模板
│   └── analyze.md                        # 可直接粘贴使用的分析 Prompt
└── references/                           # 参考知识库
    ├── retail-psychology.md              # 散户核心心理模式（贪婪循环、恐惧循环等）
    ├── market-scenarios.md               # 9种市场场景 × 散户典型反应
    ├── retail-stock-selection.md         # 散户选标的行为模式（怎么选股、偏好什么）
    ├── sentiment-indicators.md           # 散户情绪观测指标（开户数、成交量、百度指数等）
    └── behavioral-biases.md              # 10种行为金融学偏差在A股的具体表现
```

---

## 📦 部署方式

### Claude Code

```bash
# 方式一：克隆到 skills 目录
git clone https://github.com/anishnoir/Leek-Garden.git ~/.claude/skills/leek-garden

# 方式二：在任意位置克隆，Claude Code 中通过 /install 安装
git clone https://github.com/anishnoir/Leek-Garden.git
```

Skill 会通过 `SKILL.md` 的 description 自动触发。当你在对话中提及"散户怎么想"、"市场情绪"等关键词时，Claude Code 会自动加载分析框架。

### OpenAI Codex

Codex 会自动读取项目中的 `AGENTS.md` 文件作为系统指令。将本仓库克隆到你的项目根目录：

```bash
# 在项目根目录
git clone https://github.com/anishnoir/Leek-Garden.git leek-garden

# 或者在 Codex 对话中直接引用
```

Codex 会读取 `AGENTS.md` 中的分析框架，你也可以在对话中手动引导：

```
请按照 leek-garden/AGENTS.md 的分析框架，结合今天的A股行情，
帮我分析一下散户现在的心理状态。
```

### Cursor

**方式一：作为 Docs 索引**

1. 克隆仓库到项目目录
2. 在 Cursor 中，通过 `@Docs` → `Add new doc` → 指向 `leek-garden/` 文件夹
3. 对话时使用 `@Leek-Garden` 引用知识库

**方式二：作为 Rules**

将 `AGENTS.md` 的内容复制到 Cursor Rules（`.cursorrules` 或 Project Rules），Cursor 会在每次对话中自动加载分析框架。

### Windsurf

将 `AGENTS.md` 的内容写入 `.windsurfrules` 文件，Windsurf 会自动遵循其中的指令。

```bash
cat leek-garden/AGENTS.md >> .windsurfrules
```

### GitHub Copilot

将 `AGENTS.md` 复制为 `.github/copilot-instructions.md`，Copilot Chat 会将其作为上下文：

```bash
cp leek-garden/AGENTS.md .github/copilot-instructions.md
```

### 通用方式：直接粘贴 Prompt

如果你使用的是其他 AI 工具，可以直接复制 `prompts/analyze.md` 中的 Prompt 模板，配合 `references/` 中的知识库文件使用：

1. 打开 `prompts/analyze.md`，复制全部内容
2. 将 `{插入当日行情数据}` 替换为你要分析的市场情况
3. 根据需要附上 `references/` 中相关的知识库内容
4. 发送给任意支持长文本的 AI 工具

---

## 🧠 核心分析框架

```
实时数据采集 → 推断标的偏好 → 定位市场场景 → 散户心理画像 → 行为预测 → 逆向参考
```

### 分析流程：

1. **数据驱动**：获取当日指数、成交额、涨跌板块、热点新闻
2. **标的推断**：从领涨板块、涨停特征、资金流向推断散户在买什么
3. **心理画像**：判断主导情绪、典型想法和行为驱动力
4. **逆向参考**：散户一致性越强，反向信号越值得关注

---

## ⚠️ 重要提示

- 本工具是**行为分析工具**，不是选股或择时工具
- 分析结果是基于行为金融学的**推断**，不构成投资建议
- 理解散户心理是为了**避免随波逐流**，而非精准预测市场
- 投资有风险，决策需谨慎

---

## 🤝 贡献

欢迎提交 Issue 和 PR。特别欢迎以下方向的贡献：

- A 股散户行为的新观察和案例
- 更精准的情绪观测指标
- 不同市场环境下的散户心理模式补充
- 更多 Agent 平台的兼容方案

---

## 📜 许可

MIT License

---

> 🌱 在韭菜园里，我们研究韭菜的习性，是为了自己不被收割。
