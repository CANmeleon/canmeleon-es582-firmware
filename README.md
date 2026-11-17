# CANmeleon ES582-Compatible Firmware — ETAS INCA and BOA

[English](README.md) · [简体中文](README.zh-CN.md)

CANmeleon ES582-compatible firmware connects supported USB-CAN/CAN FD hardware to ETAS INCA for CAN traffic and XCP/CCP calibration, and to BOA for application development on Windows. Start here for two-channel hardware requirements, firmware downloads and driver setup.

[Features and performance](#features-and-performance) · [Download and install](#download-and-install) · [Supported devices](https://canmeleon.com/en/firmware/devices/) · [Firmware catalog](https://github.com/CANmeleon/canmeleon-usb-can-firmware)

## When to choose ES582 firmware

- Connect hardware with a matching CANmeleon firmware port to an ETAS INCA measurement or XCP/CCP calibration workflow.
- Develop Windows applications that send and receive CAN/CAN FD frames through ETAS BOA.
- Select a two-channel interface using the hardware requirements below, then install the driver and BOA components required by your INCA setup.

## Supported hardware

Choose a device listed for **ES582** in the [CANmeleon device catalog](https://canmeleon.com/en/firmware/devices/). This mode requires 2 physical CAN channels as applicable, and a license for the selected mode. Connect the device in [CANmeleon Device Manager](https://github.com/CANmeleon/canmeleon-device-manager) to check its exact model and available firmware.

**ES582 provides two CAN/CAN FD channels.** Use BOA for application development or INCA for the corresponding CAN workflow.

<!-- firmware-parameters:start -->
## Features and performance

ES582 mode; requires a device with 2 CAN interfaces and a license for this mode.

### Communication capabilities

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| CAN channels | 2 CAN / CAN FD channels supported | Each channel supports transmission and reception. |
| Frame formats | 11 / 29-bit IDs; Classic CAN 0–8 B, CAN FD up to 64 B | Classic RTR supported; CAN FD supports BRS enabled or disabled. |
| Classic CAN bit rate | 10 kbit/s–1 Mbit/s | Configure the bus bit rate in the host software. |
| CAN FD data-phase bit rate | Up to 5 Mbit/s (BOA interface) | Configure arbitration and data phases independently; use transceivers and bus wiring suitable for the selected rates. |

### Timestamps

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| Hardware receive timestamps | Supported | Read timestamps from frames received through BOA. |
| Hardware transmit-completion timestamps | Supported | Read actual transmission completion times from BOA transmit echo frames. |
| Timestamp resolution (BOA) | 0.5 µs | Received frames and transmit echo frames both have timestamps in 0.5 µs steps. |

### Typical communication performance

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| 8-byte frame rate, one direction | approximately 18,400–18,900 frames/s | BOA batch transmission/reception; CAN FD with BRS; 1 Mbit/s arbitration / 5 Mbit/s data; one bus, one direction. |

### Software and APIs

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| Software | ETAS INCA supported | Install the ETAS ES582 driver. |
| Development API | ETAS BOA supported | For developing applications that transmit and receive CAN / CAN FD frames. |

<!-- firmware-parameters:end -->

## Download and install

1. Install [CANmeleon Device Manager for Windows x64](https://canmeleon.com/en/device-manager/#downloads), connect the device and check the available firmware.
2. Choose an applicable package in **Firmware Catalog**, or download a complete package from the [GitHub firmware Releases](https://github.com/CANmeleon/canmeleon-usb-can-firmware/releases) and use **Import firmware ZIP**. [Gitee releases](https://gitee.com/sysmax/kpcfg4-canmeleon/releases) provide the existing download channel. Follow the chosen release's device and manager requirements.
3. Select **ES582**, review storage and pending changes, and confirm installation. Keep the USB connection and power stable until writing finishes.
4. Reconnect and switch to the installed firmware. Wait for USB re-enumeration.
5. Use the ETAS ES582 driver and the BOA components required by your INCA installation. Use the [driver download page](https://www.etas.com/ww/en/downloads/software-downloads-overview/hsp-hardware-service-pack/) and the [ES582 setup guide](https://canmeleon.com/en/firmware/es582/).
6. Configure each channel for your bus, then verify frame transmission and reception.

[Firmware management](https://canmeleon.com/en/device-manager/firmware-management/) · [Updates and recovery](https://canmeleon.com/en/device-manager/updates-and-recovery/)

## Frequently asked questions

**Which hardware receives this firmware?** Install it on compatible CANmeleon devices selected through the catalog and Device Manager. The mode name identifies the software interface; firmware updates for third-party-manufactured devices come from their manufacturers.

**How many CAN channels does ES582 mode provide?** Two CAN/CAN FD channels, requiring two physical CAN interfaces and the corresponding mode license.

**How do I read the performance table?** Match the bus rates, frame length, direction and mode to your workload. Configurable bit rate describes the bus setting; frame throughput describes transmitted or received frames per second.

**Where is the source code?** This repository contains documentation, parameter data and binary-download links. Refer to the component or release for its license.

## Feedback and related resources

Firmware problems and new feature requests can be submitted as [Issues in the CANmeleon firmware main repository](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues). Include the device model, active mode, firmware and driver versions, software/API, bus configuration and steps to reproduce.

[ES582 parameter table](docs/parameters/es582.md) · [Parameter JSON (Chinese)](docs/parameters/es582.json) · [Device Manager issues](https://github.com/CANmeleon/canmeleon-device-manager/issues)

## Ecosystem participation and commercial services

CANmeleon works with hardware makers, chip vendors and developers. For software/firmware integration, CANmeleon firmware porting and maintenance on your chip platform, or custom firmware development, contact [len2slaw@foxmail.com](mailto:len2slaw@foxmail.com). Include your board/MCU, target API, required features and schedule.

[Open-source hardware projects](https://github.com/CANmeleon/canmeleon-hardware) · [Request an open-source board adaptation](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues/new?template=open_hardware_adaptation.md)
