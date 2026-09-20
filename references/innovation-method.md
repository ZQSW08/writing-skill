# 创新点、方法与公式写作

## 1. 创新不是“用了新组件”

审查一个创新点时问五个问题：

1. 原方法具体在哪里失败？
2. 失败原因是数学、物理、统计还是工程机制？
3. 新模块改变了哪个变量/约束/观测关系？
4. 为什么这个改变正好针对该 failure mode？
5. 有什么实验能单独证明它有效？

五问答不全，不要把它作为主要 contribution。

## 2. 常见高质量创新范式

### A. Coarse-to-fine / cross-scale
大运动交给强动态范围模块，小残差交给高精度模块。

关键写法：
- 明确两阶段各自工作区间
- 明确 residual 如何构造
- 明确最终如何合成
- 证明第一阶段没有吞掉第二阶段的目标信号

### B. Reliability-aware
不是强行让所有像素都“输出结果”，而是定义可信度。

需要：
- reliability observable
- normalization
- rejection/down-weighting rule
- repair or fallback
- calibration/sensitivity

### C. Physics/morphology-aware
利用对象固有几何或振动方向，而不是泛化视觉先验。

需要解释：
- 先验如何获得
- 是否随时间变化
- 错误先验会怎样
- 为什么它不删除真实结构响应

### D. Detect–repair
先定义异常，再修复异常，而不是一刀切过滤。

尤其适合 camera disturbance、short transient、phase outlier。

### E. Hybrid tracking
将“全局不丢目标”和“局部高精度”分开。

必须说明：
- localization 何时触发
- detection/repair 何时接管
- confidence 如何控制 template update
- 长期 drift 如何限制

## 3. 方法小节六步模板

### 3.1 Problem
一句话承接上一节留下的问题。

### 3.2 Mechanistic rationale
解释采用该机制的理由。

### 3.3 Mathematical definition
公式前先定义对象，公式后解释意义。

### 3.4 Boundary
指出近似条件、线性范围、采样约束、Nyquist 或 geometry 假设。

### 3.5 Parameter
参数分四类：
- physically determined
- analytically derived
- empirically fixed
- adaptively estimated

不要把经验参数写成“optimal”除非做了充分 sweep。

### 3.6 Output
说明给下一模块的变量、单位、坐标系和置信度。

## 4. 公式写法

坏写法：
> where α is a parameter and β is a coefficient.

好写法：
> α controls the trade-off between edge saliency and spatial continuity. As α approaches 1, the confidence map increasingly favors high-response structural edges; lower values assign greater weight to local flow smoothness.

公式后优先解释：
- 极限情况
- 参数增大/减小时发生什么
- 与 failure mode 的联系

## 5. “为什么有效”的三层解释

一个重要模块尽量同时给：

1. 数学解释：约束或目标函数如何变化；
2. 信号/物理解释：哪些真实成分被保留/抑制；
3. 实验解释：中间变量是否确实朝预期方向变化。

## 6. 组合算法如何避免“拼凑感”

不要把 A、B、C 并列写。

改成依赖链：

```text
A 将问题压缩到 B 的有效工作区间
B 产生高精度但带有可靠性差异的估计
C 使用 B 的可靠性信息纠正异常
```

这样组合才有结构性。

## 7. 算法框

算法框只放：
- inputs
- essential loop
- trigger/fallback
- outputs

不要把论文所有公式重复搬进 pseudocode。

## 8. Innovation claim 用词

根据证据强度选词：
- establishes / derives：有明确理论推导
- introduces / proposes：新设计
- enables：有实验显示此前不能、现在可以
- improves：有直接 baseline 数字
- demonstrates potential：只有初步验证

慎用：
- fundamentally solves
- universally robust
- state-of-the-art
除非比较范围和证据足够。
