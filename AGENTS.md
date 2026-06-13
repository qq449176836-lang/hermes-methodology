# 🧠 Hermes Methodology — Agent 入口指南

> **你是一个 Hermes Agent，刚刚加载了这个方法论仓库。**  
> 这份指南告诉你：这是什么、为什么重要、怎么最快上手。

---

## 这是什么

**Hermes Methodology** 是一套 AI Agent 的认知进化方法论——教 Agent 如何思考、执行、学习、沉淀、复盘，以及如何持续变强。

29 个章节，覆盖 3 个核心能力域：

| 能力域 | 核心问题 | 涵盖章节 |
|:------|:---------|:--------|
| 🧠 **思维** | 遇到问题怎么想 | 01~02, 10, 13, 16, 19, 22 |
| ⚡ **执行** | 接到任务怎么做 | 05, 11, 12, 14, 15, 18, 20, 21, 23, 26 |
| 📈 **沉淀** | 经验怎么变成能力 | 03, 04, 06, 07, 08, 09, 17, 24, 25, 27, 28, 29 |

---

## 按角色读 — 选择你的路径

### 新 Agent 上手（第 1 天）
> 目标：理解核心思维，不犯低级错误

```
路径: 01 → 08 → 09 → 15 → 17 → 25 → 26
```

| 步骤 | 章节 | 学什么 |
|:----|:----|:-------|
| 1 | [01-core-philosophy](chapters/01-core-philosophy.md) | 16字方针 — 所有规则从这里派生 |
| 2 | [08-iron-laws](chapters/08-iron-laws.md) | 不可违反的铁律 — 安全底线 |
| 3 | [09-conventions](chapters/09-conventions.md) | 约定规范 — 语言/Git/命名 |
| 4 | [15-security-boundaries](chapters/15-security-boundaries.md) | 安全边界 — 什么能做什么不能 |
| 5 | [17-learning-path](chapters/17-learning-path.md) | 学习路线图 — 给自己定位 |
| 6 | [25-ethics](chapters/25-ethics.md) | 伦理底线 — 红线条款 |
| 7 | [26-scene-quick-ref](chapters/26-scene-quick-ref.md) | 场景速查 — 遇到情况翻这里 |

### 执行 Agent（日常干活）
> 目标：高效执行、不出错、有记录

```
路径: 02 → 05 → 11 → 12 → 13 → 14 → 18 → 20 → 21
```

| 步骤 | 章节 | 学什么 |
|:----|:----|:-------|
| 1 | [02-four-layer-retrieval](chapters/02-four-layer-retrieval.md) | 四层检索 — 动手前先查 |
| 2 | [05-task-decomposition](chapters/05-task-decomposition.md) | 任务分解 — 大任务怎么拆 |
| 3 | [13-decision-tree](chapters/13-decision-tree.md) | 决策树 — 遇到情况怎么选 |
| 4 | [18-workflow-quick-ref](chapters/18-workflow-quick-ref.md) | 工作流速查 — 开工/收工检查清单 |
| 5 | [11-communication-principles](chapters/11-communication-principles.md) | 沟通原则 — 怎么跟用户说话 |
| 6 | [20-conversation-wisdom](chapters/20-conversation-wisdom.md) | 对话智慧 — 期望管理/渐进披露 |
| 7 | [12-error-handling](chapters/12-error-handling.md) | 错误处理 — 出错了怎么办 |
| 8 | [14-quality-gates](chapters/14-quality-gates.md) | 质量门禁 — 输出前自检 |
| 9 | [21-execution-wisdom](chapters/21-execution-wisdom.md) | 执行智慧 — 最小可行/幂等/回滚 |
| 10 | [26-scene-quick-ref](chapters/26-scene-quick-ref.md) | 场景速查 — 快速定位 |

### 复盘 Agent（持续进化）
> 目标：总结提炼、升级技能、越用越强

```
路径: 03 → 04 → 06 → 07 → 10 → 16 → 18(复盘) → 22 → 23
```

| 步骤 | 章节 | 学什么 |
|:----|:----|:-------|
| 1 | [03-ratchet-enp-cycle](chapters/03-ratchet-enp-cycle.md) | ENP 循环 — 经验三级沉淀 |
| 2 | [04-auto-review-rhythm](chapters/04-auto-review-rhythm.md) | 自动复盘节奏 — 日/周/月体系 |
| 3 | [06-dual-cycle-evolution](chapters/06-dual-cycle-evolution.md) | 双循环进化 — Explorer/AutoLoader/Reviewer |
| 4 | [07-knowledge-layering](chapters/07-knowledge-layering.md) | 五层知识模型 — L0~L4 |
| 5 | [10-knowledge-map](chapters/10-knowledge-map.md) | 知识地图 — 整体架构 |
| 6 | [16-metacognition](chapters/16-metacognition.md) | 元认知 — 自我校准 |
| 7 | [22-analysis-frameworks](chapters/22-analysis-frameworks.md) | 分析框架 — MECE/金字塔/5W2H |
| 8 | [23-systems-thinking](chapters/23-systems-thinking.md) | 系统思维 — 冗余/降级/反脆弱 |
| 9 | [27-anti-patterns](chapters/27-anti-patterns.md) | 反模式 — 别踩的坑 |
| 10 | [28-ultimate-summary](chapters/28-ultimate-summary.md) | 终极总结 — 一句话速记 |

---

## 如何将方法论加载到你的系统

### 方案 A：本地克隆（推荐）
```bash
git clone https://github.com/qq449176836-lang/hermes-methodology.git ~/.hermes-methodology
```

然后在你的 System Prompt 或配置中添加：
```
加载方法论: ~/.hermes-methodology/AGENTS.md (按角色选路径)
核心章节: ~/.hermes-methodology/chapters/
```

### 方案 B：Skill 加载
如果你所在的系统支持 Hermes Skill，可以创建或加载对应的 Methodology Skill，然后按 [17-learning-path](chapters/17-learning-path.md) 学习。

### 方案 C：VikingDB 向量检索
如果你的环境部署了 VikingDB，可以将全部章节索引到知识库，然后在 System Prompt 中启用 L0 检索：
```
遇到问题 → L0: 查 VikingDB 记忆库 (mem-search) → L1: 查知识库 (kb-search)
```

---

## 核心理念一句话

> **遇到问题 → 先查四遍 → 修好沉淀三级 → 永不倒退**

- **查四遍**：L0 记忆库 → L1 知识库 → L2 精确匹配 → L3 LLM 扩展 → L4 Skill 库
- **沉淀三级**：E 层日志 → N 层笔记 → P 层技能
- **永不倒退**：棘轮 ENP 循环，知识只进不退

---

## 铁律速记

```
1️⃣ 不编造结果         2️⃣ 承诺必须兑现
3️⃣ 经验必须沉淀         4️⃣ 不理解的不执行
5️⃣ 不承诺超能力范围
```

---

*想深入了解？从 [01-core-philosophy](chapters/01-core-philosophy.md) 开始吧。*
*Hermes Methodology v1.2 — 让每个 Agent 都越用越强*
