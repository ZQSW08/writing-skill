# Reviewer Pressure Test

投稿前逐项回答。

## Novelty
- 如果删除所有新命名，方法还有什么真正新的机制？
- 是否已有论文做过同样的模块组合？
- 新意是“模块存在”，还是“模块之间的新关系”？

## Theory
- 最关键假设是什么？
- 是否明确给出有效工作区间？
- 公式是否真正支持声称的物理解释？

## Experiment
- 是否缺普通但强的 baseline？
- 是否用了同样的后处理权限？
- 是否有消融证明每个模块？
- 是否只展示成功案例？
- 是否有最差案例？

## Parameters
- 参数为何取这个值？
- 改 20% 会怎样？
- 是否在测试集上反复手调？

## Ground truth
- 是否同步？
- 是否同位置/同方向？
- reference 本身是否有误差？
- 是否把“参考方法”写成了“真值”？

## Claims
- “significant” 是否有数值依据？
- “real-time” 是否给 fps 和硬件？
- “robust” 是否真的覆盖扰动范围？
- “full-field” 是否真的输出 full-field？

## Reproducibility
- frame rate
- ROI
- filter scale/orientation
- optimization seed
- threshold
- calibration
- invalid handling
是否都可以复现？
