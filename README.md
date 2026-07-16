# master-lyricist

> 渐进式 AI 歌词创作助手 —— 基于 Noema Lab 19 章方法论，从碎片念头到完整歌词定稿。

[![Agent Skills Standard](https://img.shields.io/badge/Agent%20Skills-Standard-blue)](https://agentskills.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-2.0.0-orange)](https://github.com/qq157788394/master-lyricist)

---

## 这是什么

master-lyricist 是一个 Agent Skill，将 Noema Lab《歌词创作教学.md》完整 19 章方法论内化为 AI 的创作能力。用户只需一个模糊的念头（"想写一首关于分手的歌"），AI 即可主动驱动从灵感到定稿的完整 6 阶段渐进式创作流程。

**不是一键式傻瓜生成，而是人机协作的渐进式创作。**

---

## 核心能力

- **灵感挖掘**：基于"物件碰撞法"主动挖掘灵感，即使用户只有一个碎片念头
- **参数自动分析**：基于 5 层创作框架 + 3 个语境坐标，自动填充创作参数
- **音乐模具设计**：曲风推荐、结构模板选择、韵脚策略、字数对仗规则
- **方法论驱动生成**：严格遵循教程全部 19 章方法论生成初稿（词人模式、分镜脚本、修辞技法、交错美学、共鸣密码等）
- **10 维分析报告**：基于专业歌词分析工具的评分体系，对初稿/终稿进行量化分析
- **分层诊断与打磨**：逐段走查 + 分层诊断 + 循环修改
- **渐进式用户确认**：6 个节点各有关键确认点（🔴 CHECKPOINT），用户可随时纠偏

---

## 安装

```bash
npx skills add qq157788394/master-lyricist
```

仓库仅包含源码。发布包（zip）在 **GitHub Release** 提供，安装方式如下。

或手动安装到各 runtime 的 skills 目录：

| Runtime            | 安装路径                              |
| ------------------ | ------------------------------------- |
| Claude Code        | `~/.claude/skills/master-lyricist/`      |
| Trae CN            | `<项目>/.agents/skills/master-lyricist/` |
| Cursor             | `~/.cursor/skills/master-lyricist/`      |
| Codex              | `~/.codex/skills/master-lyricist/`       |
| Gemini CLI         | `~/.gemini/skills/master-lyricist/`      |
| 通用（多 runtime） | `<项目>/.agents/skills/master-lyricist/` |

---

## 依赖文件

本 Skill 依赖以下参考文件（位于 `references/` 子目录，随 Skill 一起分发）：

| 文件                         | 用途                              |
| ---------------------------- | --------------------------------- |
| `references/歌词创作教学.md` | 方法论源头（19 章完整教程）       |
| `references/好歌已死.md`     | 10 维分析报告参考样本（高分歌曲） |
| `references/那鱼完了.md`     | 10 维分析报告参考样本（低分歌曲） |

---

## 使用方式

### 触发词

在对话中输入以下任意内容即可启动：

- "帮我写歌词" / "创作一首歌" / "写一首关于 XX 的歌"
- "我想写歌词但不知道怎么开始"
- 直接提供创作起点（情绪、经历、意象、场景等）

### 6 阶段流程

```
灵感挖掘 → 创作参数 → 音乐参数 → 初稿生成 → 分析打磨 → 终审定稿
```

每个阶段结束后，AI 会输出结构化内容供你确认或调整。你也可以随时说"回到场景设定"、"这句我不喜欢"等指令来纠偏。

### 使用示例

**模糊输入：**

> "最近心情不太好，想写一首歌"

AI 会主动运用"物件碰撞法"挖掘灵感，给出 2-3 个方向提案。

**详细输入：**

> "我想写一首上学时的恋人 20 年后偶遇的歌，怀旧的校园民谣风格，想象成老狼演唱，但不要写成旧情复燃"

AI 会完整解析所有细节作为全局上下文，贯穿全部 6 个阶段，已有信息不重复提问。

---

## 设计理念

### 对话即流程

用户不需要知道"第几步"。AI 在对话中自然引导，但在关键节点停下来让用户确认。

### 方法论绑定

所有创作决策严格锚定《歌词创作教学.md》中的具体章节，不凭"感觉"自由发挥。包含 12 条禁止事项清单（反例黑名单）。

### 全局上下文传递

用户在入口处提供的所有细节（曲风、年代、演唱者、情感边界）贯穿全部 6 个节点，不重复提问。

---

## 仓库结构

```
master-lyricist/
├── SKILL.md                    # Skill 核心文件（元数据 + 完整指令）
├── README.md                   # 项目说明
├── LICENSE                     # MIT 许可证
├── master-lyricist-skill-design.md # Skill 设计文档
└── references/                 # 参考文档
    ├── 歌词创作教学.md          # 方法论源头（19 章完整教程）
    ├── 好歌已死.md              # 10 维分析报告参考样本（高分歌曲）
    └── 那鱼完了.md              # 10 维分析报告参考样本（低分歌曲）
```

> 以上为仓库源码。`dist/` 与发布包（`*.zip`）属于构建 / 发布产物，**不纳入 git 仓库**，仅在 GitHub Release 中提供（详见下文「发布」）。

---

## 10 维评分体系

在打磨阶段，AI 会对歌词进行 10 维量化分析（从专业歌词分析工具反推）：

| 模块 | 维度                       | 满分 |
| ---- | -------------------------- | ---- |
| A    | 文本自足性                 | 8    |
| B    | 押韵与韵律秩序             | 10   |
| C    | 句长、节奏与可唱性         | 8    |
| D    | 意象系统与具体性           | 15   |
| E    | 人称、视角与指代稳定性     | 10   |
| F    | 主题集中度与语义连贯       | 10   |
| G    | 叙事结构与信息增量         | 10   |
| H    | 情绪可信度与情绪支撑       | 12   |
| I    | 语言精度、原创性与套话控制 | 12   |
| J    | Hook、金句与传播适配       | 5    |

---

## 发布

本仓库只托管源码，发布包通过 **GitHub Release** 分发。流程如下：

1. 更新 `SKILL.md` frontmatter 中的 `version` 与设计文档版本号；
2. 提交变更并打 tag：`git tag vX.Y.Z && git push origin vX.Y.Z`；
3. GitHub Actions 自动将 `SKILL.md` / `LICENSE` / `README.md` / `references/` 打包为 `master-lyricist-skill-<版本>.zip`，并作为该 tag 对应 Release 的附件上传；
4. 用户从 Release 页面下载安装，或直接使用 `npx skills add` 从仓库安装。

> 本地 `dist/` 仅为打包中间产物，已纳入 `.gitignore`，不会提交到仓库。

## 版本

- **v2.0.0**（2026-07-01）：全新 6 节点渐进式工作流，整合 10 维分析体系、全局上下文传递、禁止事项清单、异常边界 fallback 机制
- **v1.0.0**：基于《歌词创作教学.md》的初始 5 节点流程

---

## 许可证

MIT © Noema Lab

---

## 致谢

- **Noema Lab**：方法论源头《歌词创作教学.md》19 章完整教程
- **Darwin Skill**：Skill 优化工具，帮助本 Skill 在 9 维 rubric 评估下从 71.4 分优化至 81.2 分
- **Agent Skills Standard**：遵循 [agentskills.io](https://agentskills.io) 规范
