# 视觉测振高水平论文语料的可迁移模式

本文件提炼的是**结构模式**，不是可复制措辞。

## 1. M-PME：先把理论失效可视化，再提出 coarse-to-fine

该类文章的强点是：
1. 先用简单 Gaussian target 展示 PME 在运动增大后出现 phase wrap；
2. 明确 measurement range 与 wavelength/phase range 的关系；
3. 再引入 Gaussian pyramid；
4. 每层只估计 small sub-motion；
5. 最终融合。

可迁移写法：
> 先把“为什么老方法不行”做成一幅非常简单、无法争辩的机制图，再给新架构。

## 2. APM-IPOF：把“两种方法各自的长处”写成技术矛盾

其叙事不是 NCC + phase 简单拼接，而是：
- pixel matching：wide-range 但精度有限；
- phase：sub-pixel 但有 wrapping；
- integer compensation 把 residual 强制压回 phase-linear range；
- 再做 phase refinement。

关键点：
> 第一阶段不是“辅助”，而是主动改变第二阶段的适用条件。

## 3. SPOF：从“算法误差”上升为“结构先验”

原始 phase optical flow 的 outlier 不是只靠阈值处理，而是定义：
- edge concentration
- local smoothness
再形成 confidence，并用于 GMM/EM 异常建模和修复。

关键点：
> 好创新往往不是再加一个滤波器，而是找到“哪些观测应该可信”的结构性判断。

## 4. BPAF：把干扰拆成两种不同机制

- 近线性大运动：frequency/acceleration characteristic
- 非线性 transient：amplitude characteristic

因此 BP 与 NS 分工清楚。

关键点：
> 若一个干扰包含两种 failure mode，应使用两个正交判据，而不是让一个模块承担全部职责。

## 5. DA-ViReS：真实工程对象的 morphology 可以成为创新来源

线缆本身具有：
- slender geometry
- 明确方向
- 振动方向与 cable axis 有关系

文章把这些 physical/morphological facts 转成：
- direction detection
- normalization
- directional magnification
再加 background-reference-free repair。

关键点：
> 工程论文的创新不一定来自复杂数学，也可以来自把“对象固有物理属性”正式编码进算法。

## 6. Reliability under camera disturbance：把“稳定化”与“测量”区分开

这是非常成熟的论证方式：
> 视频看起来稳定，并不等于真实振动被正确保留。

可迁移到任何“去噪/去抖/补偿”问题：
- visual quality objective
- measurement preservation objective
不是同一目标。

## 7. UAV L-D-C：大型系统论文靠“职责解耦”避免模块堆积感

Localization：
- 大范围不丢目标

Detection：
- 局部重新获得高精度几何

Correction：
- 消除 deformation-induced bias

后续 ego-motion 又 coarse→fine。

关键点：
> 当算法模块多时，用“职责边界”和“触发关系”组织，不按代码调用顺序组织。

## 8. Crossline phase center：设计可测特征也是算法创新

与其继续让 generic tracker 在所有场景都鲁棒，不如设计：
- crossline
- phase zero-crossing
让 measurement target 更适合 phase localization。

关键点：
> Measurement-oriented feature design 往往比 generic CV benchmark 思路更适合工程测量论文。

## 9. PNL stereo：先定义诊断量，再用它指导抑制

高质量方法常先回答：
> “什么时候 phase 估计会坏？”

再定义 PNL 等可量化 indicator，然后才做 suppression。

关键点：
> 如果能把 failure 从“结果不好”变成“有量可诊断”，创新会更扎实。

## 10. LoG-Gabor many-task optimization：参数优化论文要证明“任务相关性”

如果优化不同 ROI/scale/filter：
- 不只说 GA 找到最优；
- 要解释不同 task 为什么共享知识；
- transfer 是否真的加速/提高质量；
- optimization cost 是否值得。

## 11. 反复出现的写作模式

这些论文普遍有以下共同点：

1. Introduction 中先承认相关方法优势。
2. Gap 用“specific failure mechanism”而不是“accuracy insufficient”。
3. Method overview 图先于细节公式。
4. 新方法常有 2–3 个 major modules，职责互补。
5. 实验包含中间过程图，而不仅是最终误差表。
6. 真实实验使用传感器、固定相机或物理模型形成 reference。
7. 图文讨论异常点，而不是隐藏。
8. Conclusion 主动给 limitation。
