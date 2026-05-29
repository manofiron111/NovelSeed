# 🌱 NovelSeed

[![license](https://img.shields.io/badge/license-AGPL--3.0-green)](LICENSE)
[![version](https://img.shields.io/badge/version-0.1.0-blue)]()

**种下一颗种子，长出一部小说。** / **Plant a seed, grow a novel.**

NovelSeed is an open-source AI agent that takes a single story premise and generates a complete novel — from world-building and character design to chapter-by-chapter writing with built-in quality checks and AI-style removal.

## 这是什么

你只需要一句话：「我想写一个都市悬疑小说，主角是个退役刑警」

NovelSeed 会：

1. 🎯 **检测类型** — 自动匹配悬疑模板
2. ❓ **三层问答** — 帮你锁定核心设定
3. 🌍 **世界观构建** — 72 项设定自动填充
4. 👤 **人物设计** — 主角、反派、配角完整卡片
5. 📋 **大纲生成** — 雪花写作法 12 步
6. ✍️ **逐章写作** — 写 → 质检 → 去 AI 味 → 循环
7. ✅ **质量把关** — 五维评分 + 流水账检测
8. 🔗 **钩子注入** — 13 种结尾钩子，章章有悬念

## 快速开始

将本仓库作为 Claude Code / Cursor / Hermes 等 AI Agent 的技能加载：

```bash
# Claude Code
/plugin marketplace add your-username/NovelSeed

# 或手动
git clone https://github.com/your-username/NovelSeed
```

然后对 Agent 说：

> "帮我写一部修仙小说，主角是一个被逐出师门的废柴弟子，在凡间靠风水术逆袭"

## 支持的类型

| 类型 | 模板 | 特点 |
|------|------|------|
| 🏙️ 都市 | `urban.md` | 现实背景、人际关系、职场 |
| ⚔️ 修仙 | `fantasy.md` | 境界体系、力量规则、奇遇 |
| 🔍 悬疑 | `suspense.md` | 线索节奏、反转设计、真相揭露 |
| 💕 言情 | `romance.md` | 感情线、误会、关系进阶 |
| 🚀 科幻 | `scifi.md` | 科技规则、世界观逻辑 |
| 📜 历史 | `historical.md` | 时代考证、权力结构 |

## 核心方法论

- **雪花写作法** — 从一句话扩展为完整小说的 12 步流程
- **六阶段节奏控制** — 开篇→发展→高潮→收尾，每阶段该做什么、不该做什么
- **五维质量评分** — 冲突强度/情绪密度/期待感/节奏/钩子，写后自检
- **24 种 AI 味检测** — 写完后去除模板化表达
- **四条铁律** — 人物大于情节、不对称冲突、每章有不确定、对话是战场

## 项目结构

```
NovelSeed/
├── skills/novelseed/
│   ├── SKILL.md              ← Agent 主提示词
│   └── references/           ← 详细参考资料
│       ├── genres/           ← 类型模板
│       ├── hook-techniques.md
│       ├── ai-detection-patterns.md
│       ├── quality-checklist.md
│       └── ...
├── examples/                 ← 示例（不含作者真实作品）
└── docs/                     ← 架构文档
```

## 贡献

欢迎 PR！详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 许可证

[AGPL-3.0](LICENSE) — 你可以自由使用、修改、分发，但修改后的代码也必须以相同许可证开源。

## 交流

- Issue：https://github.com/manofiron111/NovelSeed/issues

---

*NovelSeed is inspired by the Snowflake Method,番茄小说 writing guides, and open-source novel-writing tools. Made with ❤️ for storytellers.*
