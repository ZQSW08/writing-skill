# 实验、结果与讨论的证据链

## 1. 一条 contribution 至少配一条直接证据

示例：

| Claim | 最直接证据 |
|---|---|
| 解决 phase wrapping | 大位移 sweep + wrapping baseline |
| 抑制 weak-texture outlier | confidence map + outlier spatial distribution + error |
| 提升长期跟踪 | long sequence + failure/recovery statistics |
| 抑制 camera disturbance | disturbance-intensity sweep |
| 保留微振动 | amplitude/frequency preservation before/after compensation |

## 2. 推荐实验顺序

### E1 Mechanism
人工可控输入，只验证某个机制。

### E2 Ablation
删掉一个模块，观察 failure mode 是否回来。

### E3 Baseline
和最接近、最强且公平的 baseline 比。

### E4 Sensitivity
扫关键参数和先验宽度。

### E5 Robustness
噪声、光照、运动模糊、遮挡、低纹理、非线性运动。

### E6 Real/field
真实结构、真实相机、真实干扰。

### E7 Downstream task
modal frequency、mode shape、cable tension、damage index 等。

## 3. Baseline 公平性

必须对齐：
- 同一视频
- 同一 ROI 或解释差异
- 同一 frame rate
- 同一目标方向
- 同一滤波/后处理权限
- 同一 ground truth
- 同一评价时间段

若某 baseline 原生依赖不同先验，应如实说明。

## 4. Ablation 不是“完整模型 vs 去一模块”就够了

若方法有 A→B→C，优先：
- baseline
- +A
- +A+B
- +A+B+C

必要时再做：
- B only
- C only

这样可以看到“可检测性恢复”和“结果净化”分别由谁贡献。

## 5. 结果图应该回答一个问题

每张图标题先写成一句问题：

> Does the proposed reliability map actually identify weak-texture failures?

然后再决定画什么。

若一张图不能回答一个明确问题，它往往只是装饰。

## 6. 结果文字模板

> Under [condition], method A reduces [metric] from x to y compared with baseline B (Fig. X). The largest improvement occurs when [failure mode], consistent with the proposed mechanism because [mechanistic reason]. When [boundary], the margin narrows, indicating [limitation].

## 7. 不只报告平均值

优先增加：
- worst case
- P95
- median
- variance / error bar
- failure rate
- recovery time
- outlier count

尤其是鲁棒性算法。

## 8. Ground truth 适用范围

下列来源不能机械排成通用强弱顺序：
1. 同步高精度传感器/编码器；
2. 受控 synthetic truth；
3. 固定参考相机；
4. 静止条件参考；
5. 另一视觉算法结果。

论文应说明真值对应的物理量、标定、同步、带宽、噪声和不确定度。受控合成可以有精确数值真值，但不能替代真实成像泛化；传感器必须测到可比较的物理量，另一算法不能自动作为真值。

不把“同代码接口输出逐点一致”写成测量精度通过；不把“滤波内部约束通过”写成来源已识别。纯噪声、纯大运动和无可辨识信息的反例单独计入误放行。拒识不应填零，也不能从总体分母中悄悄删除。

## 9. 失败案例

至少回答：
- failure 是因为观测缺失还是算法估计错？
- 是先验违反还是参数不合适？
- 是否可检测失败？
- 是 silent failure 还是 explicit invalid？

能检测并拒绝错误输出，通常比“永远输出一个值”更可信。

## 10. 复杂度

不要只写运行时间。

至少说明：
- hardware
- frame size
- number of frames
- GPU/CPU
- per-frame or total
- optimization 是否仅初始化一次
- 哪一步占主要开销

分开冷启动、预热后的重复运行、读帧/解码、跟踪、选带、滤波、绘图与视频编码。对比时对齐完整帧数、分辨率、有效覆盖与输出任务；关闭一个额外对照臂的收益应称工作量减少，而不是相同算法提速。精度或覆盖下降时，不能单独宣传更快。

## 11. Discussion 中的因果克制

如果没有单独实验隔离机制，用：
- “is consistent with”
- “may be attributed to”
- “suggests that”

不要写：
- “proves that”

