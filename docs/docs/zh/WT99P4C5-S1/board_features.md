---
title: WT99P4C5-S1 功能介绍
tags: WT99P4C5-S1, esp32p4, esp32c5
keywords: WT99P4C5-S1 , ESP32P4, ESP32-P4, esp32p4, esp32-p4, esp32c5, ESP32C5, esp32-c5, ESP32-C5
update:
  - date: 2025-06-24
    author: 沧御
    version: 1.0.0
    content: 首次更新文档
---


## 简介

`WT99P4C5-S1` 是深圳市启明云端公司推出的一款高性能多媒体开发板，基于乐鑫 `ESP32-P4` 芯片（`RISC-V` 双核处理器，主频 `400MHz`）设计，核心板型号为 `WT0132P4-A1`。该开发板主打全功能接口与多媒体处理能力。应用场景覆盖智能家居控制、工业 HMI、医疗设备、安防监控及多媒体终端，强调低成本、低功耗与高集成度，适合快速开发`IPC`、`AIoT`等产品原型。

---

### 🔧 核心硬件配置

- **主控芯片**：采用 乐鑫 `ESP32-P4` + `ESP32-C5` 双核异构架构，集成 双频 `Wi-Fi 6`（802.11ax 2.4/5GHz） 与 `蓝牙 5.0`（BR/EDR + BLE） 无线通信，支持高吞吐量数据传输与低延迟物联交互，同时搭载 `RISC-V 400MHz` 高性能处理器，兼顾射频稳定性与边缘计算能力。

- **网络接口**：集成 `RJ45` 以太网口（通过 `IP101GRI PHY` 芯片实现 `10/100Mbps` 自适应），支持有线网络高速直连；同时可选配 `Wi-Fi 6` 双频无线模组（2.4/5GHz 802.11ax），实现 有线/无线双栈协同，确保工业场景下的网络冗余与可靠传输。

- **多协议数据通道**：原生支持 `串口（UART×3）`、`以太网`、`Wi-Fi 6`、`蓝牙 5.0`、`USB 2.0 OTG` 及 `RS-485` 六类通信端口，开发者可通过 `ESP-IDF SDK` 自由实现端口间数据路由与协议转换（如 `UART ↔ 以太网透传`），满足定制化工控逻辑需求。

---

### 🛠️ 设计特点

1. `RS-485` 接口，通过 `SIT3088EESA` 收发器。功能符合 `TIA/EIA-485` 标准，实现 `14Mbps` 的独立首发。通过 `UART` 与 `WT0132P4-A1` 核心板上的 `ESP32-P4` 芯片连接。满足工业化通讯的需求。
2. 板载 `RJ45` 以太网口，与 `WT0132P4-A1` 核心板上的 `ESP32-P4` 芯片连接。满足以太网通讯的需求。
3. 全速 `USB 2.0 Type-C` 接口，可以通过 `ESP-IDF` 进行开发。
4. 板载电源指示灯与物理开关，方便电源断电控制。
5. 高速 `USB 2.0 Type-C/Type-A` 接口。
6. 开发板支持 `4-bit` 模式的 `MicroSD` 卡，可以存储或播放 `MicroSD` 卡中的音频文件。
7. `MIPI CSI FPC`（间距`0.5mm`，管脚数量`22`）连接器，用以连接外部摄像头模组，实现图像传输。
8. `MIPI DSI FPC` （间距`0.5mm`，管脚数量`22`）连接器连接器，用以连接 `LCD` 扩展板。
9. 板载 `ES8311` 低功耗单声道音频编解码器。`I2S` 通讯。对我通过板载麦克风与扬声器（最大支持`4 Ω` `3.0W`）。
10. `WT0132P4-A1` 核心板上的 `ESP32-C5` 与 `ESP32-P4` 芯片通过 `SIDO` 连接。为开发板提供 `Wi-Fi 6` 能力。

---

### 📡 主要应用场景

- **工业控制**：通过 `RS-485` 接口 连接 `PLC`/传感器，`以太网`+`Wi-Fi 6` 双冗余网络保障数据传输可靠性。
- **HMI 人机交互**：7 英寸 `RGB` 屏幕+电容触控支持本地化监控界面开发（基于 `LVGL` 等嵌入式 `GUI` 框架）。
- **安防与视觉处理终端**：`MIPI-CSI/DVP`双摄像头接口支持`1080P@30fps`图像采集，搭配`ESP32-P4`的`400MHz RISC-V`核实现边缘`AI`推理（如人脸识别）。
- **智能家居中控系统**：`ES8311` 音频编解码器支持语音播报与本地指令识别，配合 `HMI 人机交互` 实现：带屏智能音箱、家庭能源管理主机等功能。

---

### ⚙️ 开发优势

- 主控 `ESP32-P4` 可以通过乐鑫 SDK `ESP-IDF` 开发。而 `ESP32-C5` 可以通过 `AT` 命令进行控制。
- 协处理器 `ESP32-C5` 可以通过 `ESP-IDF` 进行二次开发。
- 官方提供基础功能例程，方便学习参考。

---

## 引脚描述

| 名称 | 功能                         |
| ---- | ---------------------------- |
| 3V3  | 3.3 V 电源                   |
| NC   | 空管脚                       |
| 3v3  | 3.3 V 电源                   |
| IO0  | GPIO0，LP_GPIO0              |
| 5V   | 5 V 电源                     |
| IO1  | GPIO1，LP_GPIO               |
| 5V   | 5 V 电源                     |
| IO2  | GPIO2，MTCK，LP_GPIO2        |
| NC   | 空管脚                       |
| IO4  | GPIO4，MTMS，LP_GPIO4        |
| GND  | 电源地                       |
| IO5  | GPIO5，MTDO，LP_GPIO5        |
| GND  | 电源地                       |
| IO6  | GPIO6，SPI2_HOLD_PAD         |
| GND  | 电源地                       |
| IO7  | GPIO7，SPI2_CS_PAD，LP_GPIO7 |
| GND  | 电源地                       |

---

## 电源特性

可以从以下供电方式中任选其一给 `WT99P4C5-S1` 系列开发板供电：
- 通过 `Type-C` 调试接口外接供电；
- 通过 `USB Type-C` 接口外接供电；
- 通过 `USB Type-A` 接口外界电源供电;
- 找到 `3V3` 电源输入口，采用杜邦线连接对应电压；
