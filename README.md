# writing-skill

面向工程、计算机视觉、结构动力学、信号处理与视觉测量论文的高水平科研写作 Skill。

目标不是模仿某一篇论文的句子，而是蒸馏 MSSP、Measurement、JSV、AEI 等高水平论文中反复出现的**论证结构、创新表达、公式组织、实验闭环和结果写法**。

## 核心能力

- 从研究问题提炼“技术矛盾”
- 将创新从“模块堆叠”提升为“机制闭环”
- 规划标题、摘要、引言、方法、实验、讨论和结论
- 建立 claim–evidence matrix
- 设计消融、鲁棒性、参数敏感性和真实场景验证
- 审查是否存在过度宣称、证据不足、参数无依据或 baseline 不公平

## 目录

- `SKILL.md`：主技能
- `references/article-architecture.md`：全文结构与段落功能
- `references/innovation-method.md`：创新点、方法、公式写法
- `references/experiments-results.md`：实验与结果证据链
- `references/corpus-patterns.md`：高水平视觉测振论文的可迁移叙事模式
- `assets/manuscript-blueprint.md`：从零写论文的模板
- `assets/claim-evidence-matrix.md`：创新—证据映射表
- `assets/reviewer-pressure-test.md`：投稿前 reviewer 式审查

## 使用建议

先让模型读取 `SKILL.md`，再根据任务加载对应 reference 或 asset。不要一次性把所有文件都塞进上下文。

## 设计原则

1. 不复制论文措辞，只蒸馏结构。
2. 不编造引用、数据、实验或显著性。
3. 每一个创新点都必须回答“解决哪个具体 failure mode”。
4. 每一个主要结论都必须找到对应直接证据。
5. 真实实验不是装饰，而是验证实验室结论能否迁移。
