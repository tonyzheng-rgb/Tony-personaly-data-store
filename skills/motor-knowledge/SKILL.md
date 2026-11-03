---
name: motor-knowledge
description: 电机原理与选型知识（步进、无刷 BLDC、伺服）。当用户询问步进电机、无刷直流电机、交流伺服电机的工作原理、结构、控制方式（细分、六步换相、FOC、三环控制）、编码器、选型计算（转矩、转速、惯量匹配）、接线与信号基础，或需要解释某类电机为什么丢步、抖动、发热、啸叫等原理层问题时使用。本技能只讲原理与通用方法；金三士具体产品的参数、拨码、报警代码以各 JSS FAE 技能和说明书为准。
---

# 电机原理与选型知识（步进 / 无刷 / 伺服）

## 知识文件

- `references/stepper-motors.md` 混合式步进电机的结构、矩频特性、细分与斩波恒流、共振与丢步机理、开环与闭环的区别、选型要点。

- `references/bldc-motors.md` 无刷直流电机的结构、霍尔 60°/120°、六步换相与 FOC、无感反电动势控制与启动问题、Kv 与转矩常数、常见故障的原理。

- `references/servo-motors.md` 交流伺服（PMSM 加编码器）的三环控制、增益与惯量比、编码器类型（含 17 位多圈磁编）、脉冲与总线控制、回零与报警处理思路、选型步骤。

- `references/selection-and-wiring.md` 三类电机共用的选型流程、电源与线缆、脉冲信号电平与限流电阻、RS485 与 CAN 与 EtherCAT 接线要点、接地与 EMC、安全注意。

## 使用规则

- 先讲原理再落到产品：用户问具体型号的参数、拨码、寄存器或报警代码时，转到对应的 JSS 技能（伺服驱动 JSS760N 与 JSS715N 用 jss760n_fae，JSS770P 与 JSS715P 用 jss770p_fae；无刷驱动用 jss_bldc_fae；EtherCAT 步进用 jss_ethercat_fae；一体化闭环电机用 jss_integrated_fae；独立式开环与闭环步进驱动用 jss_stepper_driver_manuals），不要用本技能的通用数值代替说明书数据。

- 做选型计算时把公式和代入过程写出来，注明每个数值的来源（用户给定、说明书查得、还是估算），估算值明确标注为估算。

- 进一步阅读的开放资料：SimpleFOC 文档（docs.simplefoc.com，MIT，覆盖 BLDC 与步进的 FOC 闭环原理与接线）和 ODrive 官方文档（docs.odriverobotics.com，伺服三环整定与编码器校准实操）。引用时注明出处，不整段复制。
