# JSS_JSSN_Servo_Skill.xml 摘要

## 文件用途

`JSS_JSSN_Servo_Skill.xml` 是金三士 JSS N 系列伺服驱动器 EtherCAT ESI 文件，可在客户需要 ESI/XML 原始文件时作为附件提供，也可用于回答主站导入、设备识别、ProductCode、RevisionNo、PDO 和对象字典相关问题。

## 供应商信息

- Vendor Id: `#x00400000`
- English Name: `Jinsanshi Co.,Ltd`
- 中文名称: `金三士`
- EtherCATInfo Version: `1.6`

## 设备节点

| 设备型号 | ProductCode | RevisionNo | Name |
| --- | --- | --- | --- |
| JSS715N Servo Driver | `#x00000715` | `#x00002EF8` | `JSS715N_sAxis_V0.10` |
| JSS760N Servo Driver | `#x00000760` | `#x00005608` | `JSS760N_sAxis_V0.10` |

## JSS760N 使用重点

回答 JSS760N 的 ESI/XML 问题时，优先定位 XML 中以下设备节点：

- Type: `JSS760N Servo Driver`
- ProductCode: `#x00000760`
- RevisionNo: `#x00005608`
- Name: `JSS760N_sAxis_V0.10`
- Comment: `JSS760N Servo Driver`

## 回答规则

- 客户要 ESI/XML 文件时，直接提供 `references/JSS_JSSN_Servo_Skill.xml`，不要把 XML 全文粘贴到回答里。
- 客户问主站扫描不到、设备识别不一致、ProductCode/RevisionNo 不匹配时，先核对实际设备是否选择了 `JSS760N Servo Driver` 节点。
- 客户问 PDO、对象字典、同步管理器、DC、FMMU、邮箱配置等精确条目时，必须读取原始 XML 对应设备节点，不要只依赖本摘要。
- 该 XML 只保留 `JSS715N` 与 `JSS760N` 两个设备节点；回答 JSS760N 时不要混用 JSS715N 的 ProductCode/RevisionNo。
