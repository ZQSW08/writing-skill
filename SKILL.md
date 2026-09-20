---
name: writing-skill
description: 面向工程、计算机视觉、结构动力学、信号处理与视觉测量论文的高水平科研写作技能。用于从研究问题、创新点、方法公式、实验数据与图表中构建可投稿的论文叙事，尤其适合 MSSP、Measurement、Journal of Sound and Vibration、Advanced Engineering Informatics 等期刊风格。触发场景包括：规划或重写标题、摘要、引言、相关工作、方法、贡献点、实验、结果、讨论、结论；提炼创新；建立 claim-evidence 链；把代码/实验结果转成论文；审查“创新是否站得住、证据是否闭环、行文是否像高水平期刊”。不得编造数据、实验、引用或结论。
---

# Scientific Paper Writing Skill

## 目标

依据实际证据，说明方法的技术必要性、已验证收益和未解决问题；证据不足时交付研究计划或有边界的阶段结论，不预设一定存在可投稿的新贡献。

核心不是辞藻，而是构建一条可审查的因果链：

```text
真实场景 / 科学任务
→ 已有方法的具体失效机制
→ 尚未解决的技术矛盾
→ 针对失效机制设计的新方法
→ 每个模块为什么必要
→ 逐层证据验证
→ 适用边界与局限
```

优先保证：**问题真实、创新可定位、方法可解释、实验可复现、结论不越界。**

---

## 使用前先建立四张“隐形表”

写正文前，先在草稿区完成以下四项；信息不足时明确列出缺口，不要自行补造。

### 1. Thesis sentence

用一句话写清：

> 在【场景】中，已有【方法类别】因【失效机制】无法同时满足【目标 A】与【目标 B】；本文通过【核心原理/架构】解决该矛盾，并在【验证层级】上证明【主要收益】。

这句话是整篇论文的主轴。

### 2. Claim–evidence matrix

使用 `assets/claim-evidence-matrix.md`。

每个 contribution 必须至少对应一个“直接证据”，重要 contribution 应有机制证据 + 定量证据 + 真实场景证据。

### 3. Method dependency map

为每个模块写：

```text
输入 → 失败模式 → 设计动作 → 输出 → 给下游解决什么
```

若一个模块无法回答“删掉它会怎样”，它很可能不是有效创新点，而只是实现细节。

### 4. Evidence ladder

实验按论证问题组织，而不是按“做实验的时间顺序”组织；下列是互补证据类型，不是适用于所有研究的强弱排序：

1. mechanism / toy / controlled simulation
2. controlled laboratory ground truth
3. ablation
4. parameter sensitivity / robustness
5. fair baseline comparison
6. real or field validation
7. efficiency / complexity
8. limitations / failure cases

详细写法见 `references/experiments-results.md`。

---

## 论文总体结构

### 标题

标题优先表达：

```text
核心能力 + 方法原理 + 应用对象/困难条件
```

避免只堆算法名。除非缩写已形成清晰方法身份，否则标题不要出现过多内部模块缩写。

### 摘要：五步压缩结构

按下列顺序写，通常 180–260 英文词内完成：

1. **任务价值**：一句，建立研究对象与实际意义。
2. **关键缺口**：一句到两句，指出现有方法在具体困难条件下为什么失败。
3. **方法主张**：先给整体架构，再给 2–3 个真正的创新模块。
4. **验证与数字**：说明实验层级，并给最有解释力的 2–3 个量化结果。
5. **意义/边界**：说明方法拓展了什么能力，不做超出证据的泛化。

不要把摘要写成“背景 + 模块清单 + 很好”。

### 引言：从“领域”收束到“不可回避的矛盾”

推荐六段逻辑：

1. **场景与测量量**：为什么这个物理量值得测。
2. **技术版图**：按机制分类已有方法，而不是按作者逐篇罗列。
3. **最接近本文的方法族**：承认其优势，再指出在目标场景的具体失效。
4. **关键矛盾/空缺**：把 gap 写成可验证的技术命题，例如“动态范围与亚像素精度无法由单一主流算法同时满足”。
5. **本文方案**：每个新模块必须一一对应前文某个 gap。
6. **Contributions**：2–4 条，每条采用“问题 → 动作 → 能力/证据”的结构。

引言写作细则见 `references/article-architecture.md`。

---

## 创新点写法

不要写：

> We propose a novel framework combining A, B and C.

优先写：

> Existing X fails when Y because Z. We therefore introduce A, which changes/estimates/constrains B so that C remains valid under D.

下列是可能的贡献类型，不构成通用的创新强弱排名：

```text
组合机制 / 等价加速 / 失效机制改造 / 可靠性诊断 / 约束模型 / 可辨识性分析
```

对“组合创新”，必须解释为什么模块间存在**互补性与依赖关系**，而非仅仅串联。

工程等价加速可以是独立价值，但不是自动获得新的物理可辨识性；更复杂的滤波器、贝叶斯名称或更多模块也不自动意味着更强贡献。不得为了符合叙事而改变算法、选择性保留结果或将经典组件改名为原创。

详细规则见 `references/innovation-method.md`。

---

## 方法章节写法

### 先总览，后公式

方法章开头先用 1 张总览图和 1 段文字回答：

- 输入是什么；
- 最困难的干扰是什么；
- 方法分几个 macro stages；
- 每阶段输出什么；
- 数据/坐标/置信度如何流向下一阶段；
- 最终输出什么物理量。

不要一上来就推公式。

### 每个方法小节检查六项（按需要合并，不强制六段）

1. **Problem/Fault**：本小节解决上一阶段留下的什么失败模式。
2. **Rationale**：为什么选这个物理/统计原理。
3. **Definition**：给变量、公式、算法。
4. **Interpretation**：解释每个关键项的物理含义，不只解释符号。
5. **Parameters and boundary**：参数从哪里来；极端情况会怎样。
6. **Output**：本模块输出如何被下一模块使用。

### 公式的四类角色

每个关键公式至少属于以下一种：

- measurement equation：观测量怎样映射到目标物理量；
- constraint equation：什么先验限制了解空间；
- objective equation：优化究竟在最小化/最大化什么；
- reliability equation：哪些观测可信、哪些应降权或拒绝。

公式后必须写“为什么这能处理前述 failure mode”。

---

## 实验章节

实验不是“证明我们最好”，而是回答 reviewer 的一组问题：

- 方法真的按声称的机制工作吗？
- 每个新模块有必要吗？
- 参数是不是靠碰巧调出来的？
- 与强 baseline 比较是否公平？
- 在噪声、光照、模糊、遮挡、大运动、频率接近等困难条件下何时退化？
- 能否在真实系统中输出目标物理量？
- 计算成本是否与应用场景匹配？

优先采用“一个实验对应一个主张”的结构。

---

## 结果段落：Claim → Evidence → Why → Boundary

每一段结果优先按：

1. **Claim**：这一段要证明什么。
2. **Evidence**：指向 Fig./Table，并给关键数字。
3. **Why**：用方法机制解释趋势。
4. **Boundary/Exception**：异常点、失败点或与 baseline 接近时如实说明。

不要逐曲线念图，也不要用“clearly / obviously / significantly”代替数字。

---

## 讨论与结论

### Discussion 必须区分

- **已证明**：被当前实验直接支持；
- **合理解释**：由机制与观察推断，但未被单独实验隔离；
- **未来假设**：需要新实验验证。

主动写出：

- 依赖的先验；
- 有效工作区间；
- 未覆盖的 motion / noise / geometry；
- ground truth 的局限；
- 与真实部署的差距。

### Conclusion

只回答三件事：

1. 解决了什么明确问题；
2. 通过什么核心机制；
3. 在什么验证条件下取得什么结果。

不要在结论中第一次提出新创新点。

---

## 语言原则

- 先写逻辑，后润色语言。
- 一段只承担一个 rhetorical job。
- 用因果连接词而非空泛形容词。
- “robust / accurate / efficient / general” 后面优先跟条件或指标。
- 不把 correlation 写成 causation。
- 不把“在本数据集有效”写成“普遍有效”。
- 不复制参考论文句子；只学习其结构与论证逻辑。
- 如果没有数据，不生成虚构百分比、小数、p 值或误差。
- 如果没有引用来源，用 `[CITATION NEEDED]` 标记，不编造 DOI。

---

## 按任务加载参考文件

- 写摘要、引言、标题：读 `references/article-architecture.md`
- 提炼创新、写方法与公式：读 `references/innovation-method.md`
- 设计实验、写结果/讨论：读 `references/experiments-results.md`
- 需要模仿高水平视觉测振论文的“论证套路”而非文字：读 `references/corpus-patterns.md`
- 视频测量、跟踪、滤波、模态/波形或可靠性论文：读 `references/measurement-validation.md`，区分接口等价、测量精度和来源识别。
- 从零规划全文：复制并填写 `assets/manuscript-blueprint.md`
- 审查 contribution 是否有证据：使用 `assets/claim-evidence-matrix.md`
- 投稿前自审：使用 `assets/reviewer-pressure-test.md`

---

## 完成前的强制检查

在交付论文段落或整稿前，检查：

- [ ] Introduction 的每个 gap 都被某个 method module 回答。
- [ ] 每个 contribution 都有直接 evidence。
- [ ] 每个关键参数都有来源、推导、经验依据或 sensitivity。
- [ ] Ablation 能分离新模块的作用，而不是只比较完整模型。
- [ ] Baseline 使用相同输入、数据范围、采样率、评价指标和后处理原则。
- [ ] 结果文字包含数字，不靠形容词。
- [ ] 失败案例没有被隐藏。
- [ ] 结论范围不超过实验范围。
- [ ] 没有虚构引用、数据、实验或不存在的图。

