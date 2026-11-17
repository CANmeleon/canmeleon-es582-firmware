# CANmeleon ES582 兼容固件 — ETAS INCA 与 BOA

[English](README.md) · [简体中文](README.zh-CN.md)

CANmeleon ES582 兼容固件让适用的 USB-CAN/CAN FD 硬件在 Windows 上接入 ETAS INCA，进行 CAN 报文收发与 XCP/CCP 标定，也可通过 BOA 开发应用。本仓库提供双通道硬件要求、固件下载和驱动配置说明。

[固件特性与性能参数](#固件特性与性能参数) · [下载与安装](#下载与安装) · [支持设备](https://canmeleon.com/zh/firmware/devices/) · [固件总览](https://github.com/CANmeleon/canmeleon-usb-can-firmware)

## 什么时候选择 ES582 固件

- 将适用的 CANmeleon 硬件接入 ETAS INCA 测量或 XCP/CCP 标定流程。
- 通过 ETAS BOA 开发 Windows 应用，发送与接收 CAN/CAN FD 报文。
- 按下方硬件要求选择双通道接口，再安装 INCA 所需的驱动及 BOA 组件。

## 支持硬件

在 [CANmeleon 设备目录](https://canmeleon.com/zh/firmware/devices/)选择支持 **ES582** 的硬件。按所选模式配备 2 路物理 CAN 接口及对应授权。连接[设备管理器](https://github.com/CANmeleon/canmeleon-device-manager)核对完整型号及可安装固件。

**ES582 提供双通道 CAN/CAN FD。** 可通过 BOA 开发应用，或使用 INCA 进行对应的 CAN 通信操作。

<!-- firmware-parameters:start -->
## 固件特性与性能参数

ES582 模式；需配套具备 2 路 CAN 接口及对应模式授权的设备。

### 通信能力

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| CAN 通道 | 支持 2 路 CAN / CAN FD | 每通道支持发送和接收。 |
| 报文格式 | 11 / 29 位 ID；Classic CAN 0–8 B，CAN FD 最高 64 B | 支持 Classic RTR；CAN FD 支持 BRS 开启 / 关闭。 |
| Classic CAN 速率 | 10 kbit/s–1 Mbit/s | 通过上位机设置总线速率。 |
| CAN FD 数据速率 | 最高 5 Mbit/s（BOA 接口） | 仲裁段与数据段独立配置；需配套支持相应速率的收发器和总线布线。 |

### 时间戳

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| 接收硬件时间戳 | 支持 | 通过 BOA 接收报文的时间戳读取。 |
| 发送完成硬件时间戳 | 支持 | 通过 BOA 的发送回显读取实际发送完成时间。 |
| 时间戳分辨率（BOA） | 0.5 µs | 接收报文和发送回显的时间戳均以 0.5 µs 为步进。 |

### 典型通信性能

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| 8 字节报文单向传输帧率 | 约 18,400–18,900 帧/秒 | BOA 批量收发；CAN FD，启用 BRS；1 Mbit/s 仲裁 / 5 Mbit/s 数据；单条总线、单向。 |

### 软件配套

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| 配套软件 | 支持 ETAS INCA | 安装 ETAS ES582 驱动。 |
| 开发接口 | 支持 ETAS BOA | 用于 CAN / CAN FD 收发应用开发。 |

<!-- firmware-parameters:end -->

## 下载与安装

1. 安装 [Windows x64 设备管理器](https://canmeleon.com/zh/device-manager/#downloads)，连接设备并检查适用固件。
2. 从固件目录选择适用包，或从 [GitHub 固件 Releases](https://github.com/CANmeleon/canmeleon-usb-can-firmware/releases)下载完整包并使用“导入固件 ZIP”。已有下载渠道见 [Gitee Releases](https://gitee.com/sysmax/kpcfg4-canmeleon/releases)。按所选版本说明核对设备及管理器要求。
3. 选择 **ES582**，检查空间和待执行变更，确认安装；保持 USB 连接和供电稳定直至写入完成。
4. 重新连接并切换到所安装的固件，等待 USB 重新识别。
5. 安装 ETAS ES582 驱动及 INCA 所需的 BOA 组件。 参阅[驱动下载页](https://www.etas.com/ww/en/downloads/software-downloads-overview/hsp-hardware-service-pack/)及 [ES582 配置指南](https://canmeleon.com/zh/firmware/es582/)。
6. 按总线配置设置各通道，确认能够正常发送和接收报文。

[固件管理](https://canmeleon.com/zh/device-manager/firmware-management/) · [更新与恢复](https://canmeleon.com/zh/device-manager/updates-and-recovery/)

## 常见问题

**固件安装到什么硬件？** 安装于设备目录和管理器列出的适用 CANmeleon 硬件。模式名称表示软件接口；第三方原厂硬件的升级固件由对应厂商提供。

**ES582 模式有多少路 CAN？** 提供两路 CAN/CAN FD，需要两路物理 CAN 接口及对应模式授权。

**如何使用性能参数表？** 按总线速率、帧长、方向及模式对照自己的场景。可配置速率表示总线设置，报文吞吐表示每秒发送或接收的帧数。

**固件源码在哪里？** 本仓库提供文档、参数数据和二进制下载入口，许可信息以对应组件或发布包为准。

## 问题与新需求反馈

固件相关的问题和新需求可在 [GitHub 固件主仓库提 Issue](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues)。请附设备型号、当前模式、固件与驱动版本、软件/API、总线配置及复现步骤。

[ES582 参数表](docs/parameters/es582.zh-CN.md) · [参数 JSON](docs/parameters/es582.json) · [设备管理器问题](https://github.com/CANmeleon/canmeleon-device-manager/issues)

## 生态参与与商业技术服务

CANmeleon 面向硬件厂商、芯片厂商和开发者。软件/固件集成、芯片平台 CANmeleon 固件移植与维护，以及定制固件开发，可联系 [len2slaw@foxmail.com](mailto:len2slaw@foxmail.com)，并说明板卡/MCU、目标 API、所需功能和计划时间。

[开源硬件项目](https://github.com/CANmeleon/canmeleon-hardware/blob/main/README.zh-CN.md) · [申请开源板卡适配](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues/new?template=open_hardware_adaptation.md)
