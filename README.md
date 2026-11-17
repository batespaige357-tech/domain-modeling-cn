# Domain Modeling CN

**把中文业务术语说清楚，让词汇表与代码使用同一种含义。**

基于 [mattpocock/skills 的 domain-modeling](https://github.com/mattpocock/skills/tree/main/skills/engineering/domain-modeling) 的小幅中文适配。独立维护、非官方。

## 保留什么

挑战模糊术语、用具体场景检验边界、对照代码、及时记录明确的定义。保留按上下文组织词汇表的方法和两个原始格式文件；只有难逆转、有上下文价值且存在真实取舍时才提出 ADR。

## 中文补充

- 区分中文业务称谓、英文领域名和代码标识，避免机械直译。
- 在既有上下文中消歧，不把所有同名词强行合并。
- 假设与已明确的定义分开，不把待确认内容写成决策。
- 中文解释不擅自触发代码改名、模块重构或数据库变更。

## 安装与调用

```bash
npx skills add batespaige357-tech/domain-modeling-cn --skill domain-modeling-cn
```

对助手说“用 domain-modeling-cn 澄清这些业务概念，先对照已有词汇表和代码”；Codex 可使用 `$domain-modeling-cn`。也可将 `skills/domain-modeling-cn` 整个文件夹复制到助手技能目录，保留两个格式文件。

这是业务概念建模与文档工作流，不自带代码生成器、数据库或 ADR 平台。没有脚本、示例网页、截图或前后对比。

## 来源与检查

MIT，保留 Matt Pocock 版权和完整许可证。[CHANGES.md](CHANGES.md) 记录来源提交与具体变化。

已检查原正文、两个格式文件、UTF-8、本地引用及技能格式。尚未进行真实团队建模会话或助手行为评估；没有自动对齐代码或改善架构的效果成绩。未运行前端编译。
