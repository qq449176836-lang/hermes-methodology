# 二十九、VikingDB 双库集成

> 返回 [目录](../README.md) | [Hermes Methodology](https://github.com/qq449176836-lang/hermes-methodology)

---

## 二十九、VikingDB 双库集成

VikingDB 是火山引擎向量数据库，作为知识库与记忆库的云端底座，
替代已废弃的 IMA 知识库，提供语义搜索能力。

### 双库架构

```
┌──────────────────────────────────────────────────────────┐
│                    VikingDB 同一项目                      │
├─────────────────────────┬────────────────────────────────┤
│  📖 知识库               │  🧠 记忆库                      │
│  ali_heyuan_hermes_notes │  ali_heyuan_hermes_memory     │
│  kb-4821f4b0271aefe4     │  mem-114f8698                 │
├─────────────────────────┼────────────────────────────────┤
│  存: 8 份方法论文档      │  存: 会话经验、踩坑记录、       │
│      技术方案、规范       │      关键决策、修复方案         │
│  搜索: knowledge search  │  搜索: memory search           │
│  更新: 每日 08:00        │  更新: 每 6h + 会话结束即时触发  │
│  文档: 22 切片索引       │  索引: 自动管道，无需手动        │
└─────────────────────────┴────────────────────────────────┘
```

### 认证方式

- **HTTP API Key**（优先）：直接调用 REST API，效率高
- **viking-cli**（fallback）：`~/.local/bin/vikingdb` + `~/.viking/config`
- API Key 存储在 `~/.viking/api-keys`，脚本自动加载

### 主要操作

```bash
# ── 知识库 ──
vikingdb knowledge list                           # 列出文档
vikingdb knowledge search "棘轮循环ENP流程"        # 语义搜索
vikingdb knowledge add-doc --title "xxx" --file doc.md  # 添加文档

# ── 记忆库 ──
vikingdb memory list                              # 列出记忆事件
vikingdb memory search "Flask 重启"               # 搜索历史经验
vikingdb memory add-event --title "xxx" --content "..."  # 写入记忆

# ── HTTP API 直调（推荐，更快）──
curl -X POST "https://api-knowledgebase.mlp.cn-beijing.volces.com/..." \
  -H "Authorization: Bearer $(cat ~/.viking/api-keys | grep knowledge | cut -d' ' -f2)"
```

### 同步机制（全自动）

| 时间 | 触发 | 做什么 |
|:----:|------|--------|
| 🕗 08:00 | Windows 计划任务 `VikingDB-KB-Sync` | 检查 GitHub 更新 → 上传知识库 |
| 🕑 02:00 | 计划任务 `VikingDB-Mem-Sync` | 记忆蒸馏 E→N→P |
| 🕗 08:00 | 计划任务 `VikingDB-Mem-Sync` | 记忆蒸馏 |
| 🕑 14:00 | 计划任务 `VikingDB-Mem-Sync` | 记忆蒸馏 |
| 🕗 20:00 | 计划任务 `VikingDB-Mem-Sync` | 记忆蒸馏 |
| 🚀 按需 | 会话结束 / 用户指令 | 即时触发同步 |

同步脚本：`~/.viking/kb-sync.sh`、`~/.viking/mem-sync.sh`（日志 `tee -a` 追加，永不清除）

### 三层检索中的位置

四层检索中的 **L0（记忆库）和 L1（知识库）**。优先在这两层进行语义搜索，
L0 命中则直接复用历史经验（「错题本」），L1 命中则融合方法论文档。

### 费用与策略

| 维度 | 说明 |
|------|------|
| 💰 日费用 | ~¥0.01（按需触发，不空搜索） |
| 🔍 检索策略 | 先记忆库 → 后知识库 → 最后推理 |
| ✍️ 写入规则 | 仅记录：错误修复、新发现、用户纠正、高价值经验 |
| 🗑️ 日志 | `tee -a` 追加，永不自动清除 |

---
