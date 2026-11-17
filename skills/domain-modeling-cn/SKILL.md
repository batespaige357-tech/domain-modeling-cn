---
name: domain-modeling-cn
description: 中文适配：领域术语、业务概念、词汇表与架构决策。Build and sharpen a project's domain model. Use when discussing codebase terminology, writing or editing a GLOSSARY.md, or recording or editing an ADR.
---

# Domain Modeling

Actively build and sharpen the project's domain model as you design. This is the *active* discipline: challenging terms, inventing edge-case scenarios, and writing the glossary and decisions down the moment they crystallise. (Merely *reading* `GLOSSARY.md` for vocabulary is not this skill: that's a one-line habit any skill can do. This skill is for when you're changing the model, not just consuming it.)

## File structure

Most repos have a single context:

```
/
├── GLOSSARY.md
├── docs/
│   └── adr/
│       ├── 0001-event-sourced-orders.md
│       └── 0002-postgres-for-write-model.md
└── src/
```

If a `GLOSSARY-MAP.md` exists at the root, the repo has multiple contexts. The map points to where each one lives:

```
/
├── GLOSSARY-MAP.md
├── docs/
│   └── adr/                          ← system-wide decisions
├── src/
│   ├── ordering/
│   │   ├── GLOSSARY.md
│   │   └── docs/adr/                 ← context-specific decisions
│   └── billing/
│       ├── GLOSSARY.md
│       └── docs/adr/
```

Create files lazily: only when you have something to write. If no `GLOSSARY.md` exists, create one when the first term is resolved. If no `docs/adr/` exists, create it when the first ADR is needed.

## During the session

### Challenge against the glossary

When the user uses a term that conflicts with the existing language in `GLOSSARY.md`, call it out immediately. "Your glossary defines 'cancellation' as X, but you seem to mean Y. Which is it?"

### Sharpen fuzzy language

When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account': do you mean the Customer or the User? Those are different things."

### Discuss concrete scenarios

When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

### Cross-reference with code

When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible. Which is right?"

### Update GLOSSARY.md inline

When a term is resolved, update `GLOSSARY.md` right there. Don't batch these up: capture them as they happen. Use the format in [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md).

`GLOSSARY.md` should be totally devoid of implementation details. Do not treat `GLOSSARY.md` as a spec, a scratch pad, or a repository for implementation decisions. It is a glossary and nothing else.

### Offer ADRs sparingly

Only offer to create an ADR when all three are true:

1. **Hard to reverse**: the cost of changing your mind later is meaningful
2. **Surprising without context**: a future reader will wonder "why did they do it this way?"
3. **The result of a real trade-off**: there were genuine alternatives and you picked one for specific reasons

If any of the three is missing, skip the ADR. Use the format in [ADR-FORMAT.md](./ADR-FORMAT.md).


## 中文术语适配 — domain-modeling-cn 新增

独立社区适配，保留上游澄清术语、具体场景检验、代码对照、即时记录和克制创建 ADR 的方法，不代表原作者官方版本。

### 中文业务词与代码名称分开核对

同一个中文词可能指不同概念，例如账户、账号、用户、客户。先从既有词汇表、业务材料和代码确认含义；不要只靠英文直译认定它们相同，也不默认一个中文词必须对应一个全局代码名称。

同一上下文内确定一个规范中文称谓，必要时保留稳定的英文领域名称或代码标识作为对应说明。对应说明只用于消歧，不能把接口、字段实现和数据库结构灌进业务词汇表。不同上下文的相同词可有不同含义，遵守已有 GLOSSARY-MAP.md。

### 只记录已经明确的含义

中文澄清问题引用当前定义与具体冲突，一次聚焦会影响边界的分歧。已有材料可以回答的问题先自行查明，不反复询问。只有用户或来源已明确的含义才能作为已确定定义写入；待确认假设不伪装成正式术语。

用中文业务场景检验概念边界，保留人的实际表达；代码与业务定义冲突时指出证据，不擅自重命名标识符或修改业务行为。

### 词汇表与决策继续分工

词汇表按原 [GLOSSARY-FORMAT.md](GLOSSARY-FORMAT.md) 描述业务含义。仅在上游三个条件同时满足时提出 ADR，并按 [ADR-FORMAT.md](ADR-FORMAT.md) 记录真实取舍，不为了留痕添加空决策。

尊重项目已有文档语言和路径；新建内容使用 UTF-8。仅在当前任务授权的记录范围内更新文件，不因澄清一个词重写无关文档、创建新模块或执行数据库变更。
