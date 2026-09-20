# 论文架构：从“领域背景”到“证据闭环”

## 1. 高水平论文常见的叙事主线

优秀工程论文通常不是“我用了 A+B+C”，而是：

```text
应用价值
→ 现有方法优势
→ 在目标场景中发生的具体失效
→ 为什么已有修补仍不够
→ 一个不可回避的技术矛盾
→ 新方法如何解除这个矛盾
→ 分层验证
```

典型技术矛盾包括：

- 大动态范围 vs 亚像素精度
- 稳像 vs 保留真实结构振动
- 高频灵敏度 vs 噪声放大
- 局部高精度 vs 长期跟踪鲁棒性
- phase sensitivity vs phase wrapping
- 去干扰 vs 不误删真实响应
- 现场可部署性 vs 外部参考/额外硬件依赖

## 2. 标题

优先使用：
- 核心能力：wide-range / reference-free / direction-aware / reliability-guided / coarse-to-fine
- 核心机制：phase optical flow / hybrid tracking / nonlinear suppression
- 应用对象：bridge deflection / cable vibration / stereo 3D motion

避免：
- 一长串模块名
- vague 的 “an improved method”
- 标题声称超出实验范围

## 3. 摘要模板

### Sentence 1: significance
说明目标物理量为什么重要。

### Sentence 2: bottleneck
用“现有方法虽然 X，但在 Y 下因为 Z 失败”形成冲突。

### Sentence 3–4: method
先讲总体框架，再讲两三个真正决定性能的机制。

### Sentence 5–6: evidence
给真实实验层级、ground truth 和最关键数字。

### Sentence 7: implication
说拓展了什么能力，不说“可用于所有场景”。

## 4. 引言六段式

### P1 应用与任务
只写与本文测量量直接相关的意义。

### P2 方法谱系
按机制分类：接触式、DIC、tracking、phase-based 等。

### P3 最接近的方法族
先承认优势，再进入 failure mode。

### P4 gap 收束
不要写“few studies”。要写一个可被实验验证的矛盾。

例如：
> Pixel-level trackers tolerate large displacement but lack sensitivity to micro-motion; phase-based estimators offer sub-pixel sensitivity but fail outside their phase-linear range. Hence, a single conventional estimator cannot simultaneously provide wide dynamic range and sub-pixel precision.

### P5 本文方案
每一模块必须与 P4 的 gap 对应。

### P6 contributions
每条贡献包含：
- 解决对象
- 新机制
- 带来的能力

## 5. Related work 的“比较轴”

不要按作者年份流水账。优先围绕：
- precision
- dynamic range
- reference dependence
- robustness to camera motion
- texture dependence
- computational burden
- physical interpretability

每类方法最后一句都要说明“为何仍不足以解决本文任务”。

## 6. 方法章节的总览图与文字

总览段先交代：
- 输入
- stage 1
- stage 2
- 信息回流或 confidence
- 输出
- 坐标系/物理量

高水平论文常用 coarse-to-fine、detect-repair、localize-detect-correct 这类架构，是因为每一 stage 都有明确职责边界。

## 7. Discussion 的成熟写法

不要重复 Results。

Discussion 应主动说明：
- 哪个假设最关键
- 哪个参数最敏感
- 哪个场景会失败
- 为什么某 baseline 在某场景接近本文
- ground truth 有何偏差来源
- 下一步如何解除当前边界

## 8. 结论

推荐四句结构：
1. 问题；
2. 方法；
3. 最关键验证数字；
4. 限制/下一步。

避免重新写一遍摘要。
