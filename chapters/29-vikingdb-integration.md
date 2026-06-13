# 二十九、VikingDB 双库集成

> 返回 [目录](../README.md) | [Hermes Methodology](https://github.com/qq449176836-lang/hermes-methodology)

---

## 二十九、VikingDB 双库集成

VikingDB 是火山引擎向量数据库，作为知识库与记忆库的云端底座，
提供语义搜索能力。如果你没有部署 VikingDB，可以跳过本章，
或使用本地文件搜索（`grep` / `ripgrep`）替代。

### 双库架构（参考）

```
┌──────────────────────────────────────────────────────────┐
│                    VikingDB 同一项目                      │
├─────────────────────────┬────────────────────────────────┤
│  📖 知识库               │  🧠 记忆库                      │
│  {你的知识库集合名}       │  {你的记忆库集合名}              │
│  {your-kb-collection-id} │  {your-mem-collection-id}      │
├─────────────────────────┼────────────────────────────────┤
│  存: 方法论文档          │  存: 会话经验、踩坑记录、         │
│      技术方案、规范       │      关键决策、修复方案           │
│  搜索: knowledge search  │  搜索: memory search            │
│  更新: 定期同步           │  更新: 定时 + 会话结束即时       │
└─────────────────────────┴────────────────────────────────┘
```

### 认证方式

| 方式 | 说明 |
|:----|:-----|
| **HTTP API Key**（推荐） | 直接调用 REST API，效率高，参数名 `VIKING_SERVICE_API_KEY` |
| **viking-cli** (fallback) | 通过 `~/.viking/config` 配置，部分平台预装 |
| **AK/SK** (传统) | 部分 SDK 需要，但不推荐用于 Agent 场景 |

认证凭证应存储在环境变量或独立配置文件中，**禁止硬编码**。

### 主要操作（通用示例）

```bash
# ── 知识库（以下为 CLI 示例，具体命令以你的 SDK/CLI 为准）──
vikingdb knowledge list                           # 列出文档
vikingdb knowledge search "你的查询"               # 语义搜索
vikingdb knowledge add-doc --title "xxx" --file doc.md  # 添加文档

# ── 记忆库 ──
vikingdb memory list                              # 列出记忆事件
vikingdb memory search "关键字"                    # 搜索历史经验
vikingdb memory add-event --title "xxx" --content "..."  # 写入记忆

# ── HTTP API 直调（推荐，更快）──
curl -X POST "https://api-knowledgebase.mlp.cn-beijing.volces.com/{your-endpoint}" \
  -H "Authorization: Bearer ${VIKING_SERVICE_API_KEY}"
```

> 💡 如果你使用自定义脚本（如 `vikingdb.js`），替换为你的脚本路径即可。

### 同步机制（建议节奏）

| 时间 | 做什么 |
|:----:|--------|
| 🕗 每日 08:00 | 知识库同步：检查文档更新 → 上传/更新到知识库 |
| 🕑 每 6h | 记忆库蒸馏：会话经验 E→N→P 三层提炼上传 |
| 🚀 按需 | 会话结束 / 关键事件 → 即时触发同步 |

### 在四层检索中的位置

VikingDB 对应四层检索中的 **L0（记忆库）和 L1（知识库）**：

```
L0: VikingDB 记忆库（mem-search）
    → 命中则直接复用历史经验（「错题本」）

L1: VikingDB 知识库（kb-search）
    → 命中则融合方法论文档和经验笔记

检索顺序：先记忆库 → 后知识库 → 最后 L2~L4
```

### 费用参考

| 维度 | 说明 |
|:----|------|
| 💰 典型日费用 | ~¥0.01（按需触发，不空搜索） |
| 🔍 检索策略 | 只在有明确问题时触发，寒暄跳过 |
| ✍️ 写入规则 | 仅记录：错误修复、新发现、用户纠正、高价值经验 |
| 🗑️ 日志策略 | `tee -a` 追加，永不自动清除 |

## 关联章节

- [02-four-layer-retrieval](./02-four-layer-retrieval.md) — 四层检索中L0记忆库和L1知识库由VikingDB提供底层支持
- [07-knowledge-layering](./07-knowledge-layering.md) — 知识分层中L3知识库的语义存储依赖VikingDB实现

---

> ⚠️ 本章中的集合 ID、API 端点、脚本路径为通用示例。
> 实际部署时请替换为你自己的 VikingDB 项目配置。
