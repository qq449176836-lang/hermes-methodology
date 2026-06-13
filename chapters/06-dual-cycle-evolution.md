# 六、双循环进化引擎

> 返回 [目录](../README.md) | [Hermes Methodology](https://github.com/qq449176836-lang/hermes-methodology)

---

## 六、双循环进化引擎

Hermes Evolution Engine — 7 个 Cron 任务驱动的自主进化系统。

### 循环 A：即时进化（短周期）

```
触发: 每次任务结束 / 每次错误修复
目的: 快速微调，不犯相同错误

执行路径:
  遭遇问题 → 诊断根因 → 修复 → 记录到记忆库 (mem-sync)
  └─ 如果是新发现的能力/模式 → 提炼为 Skill

关键机制:
  □ Skill 自动加载（AutoLoader）：新 Skill 放入 ~/.hermes/skills/ 即生效
  □ 会话检查点（session-checklist）：每次启动强制检视三层检索/VikingDB/状态
  □ Context Squeezer：对话上下文过长时自动压缩，保留关键信息
```

### 循环 B：深度进化（长周期）

```
触发: Cron 定时任务（7 个计划任务）
目的: 系统性升级，能力持续增长

三模块架构:
┌─────────────────────────────────────────────────────────┐
│ 📡 Explorer（探索者）                                    │
│  ├─ 扫描 GitHub Trending / Hacker News                  │
│  ├─ 追踪竞品 Agent 新能力                                │
│  ├─ 发现可集成的新工具/框架/API                           │
│  └─ cron: explorer-daily（每日 09:00）                   │
├─────────────────────────────────────────────────────────┤
│ ⚙️ AutoLoader（自动加载器）                              │
│  ├─ 评估新发现→自动安装/配置                             │
│  ├─ 生成适配 Skill                                       │
│  ├─ 注册到 auto-load.json                                │
│  └─ cron: autoloader-hourly（每小时）                    │
├─────────────────────────────────────────────────────────┤
│ 🔍 Reviewer（评审者）                                    │
│  ├─ 回顾所有会话，蒸馏最有价值经验                         │
│  ├─ 推荐 E→N→P 升级路径                                  │
│  ├─ 生成每日/每周复盘报告                                 │
│  └─ cron: reviewer-daily（每日 23:00）                   │
└─────────────────────────────────────────────────────────┘
```

### 棘轮防退机制

```
E 层（Episodic）    → 单次经验，原始记录
  │ 同类问题 ≥3 次触发提炼
  ▼
N 层（Narrative）   → 精炼笔记，结构化叙事
  │ 质量四要素齐全（情境/行动/结果/教训）
  ▼
P 层（Procedural）  → 标准化 Skill，可自动执行
  │ 存入 ~/.hermes/skills/
  ▼
被三层检索消费 → 下次遇到同类问题，L0 记忆库直接命中 ✓
```

### 实际部署

| 组件 | 文件 | 状态 |
|------|------|------|
| Evolution Engine 核心 | `~/.hermes/skills/hermes-evolution-engine/SKILL.md` | ✅ 就绪 |
| AutoLoader 配置 | `~/.hermes/auto-load.json` | ✅ 就绪 |
| Explorer 探索脚本 | `explorer-daily.sh` | 按需触发 |
| Context Squeezer | `~/.hermes/skills/context-squeezer/` | ✅ 就绪 |
| Session Checklist | `~/.hermes/skills/session-checklist/` | ✅ 就绪 |

## 关联章节

- [03-ratchet-enp-cycle](./03-ratchet-enp-cycle.md) — ENP循环是双循环进化中经验升级的基本路径
- [04-auto-review-rhythm](./04-auto-review-rhythm.md) — 复盘节奏为双循环中的Reviewer模块提供定时触发机制
- [29-vikingdb-integration](./29-vikingdb-integration.md) — VikingDB为双循环的知识同步提供存储和检索底座

---
