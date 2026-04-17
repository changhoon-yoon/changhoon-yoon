<!--
  Upload this file as README.md to your github.com/<changhoon-yoon>/<changhoon-yoon> repo.
  It will render as your GitHub profile homepage. Mermaid diagrams are rendered
  automatically by GitHub.

  ⚠️ Before uploading:
  1. Replace <changhoon-yoon> in the links below with your actual GitHub handle
  2. The "Featured Projects" section lists planned/ongoing demo repos.
     Only keep the entries that have actual repos — otherwise visitors hit 404.
-->

<h1 align="center">👋 Hi, I'm ChangHoon Yoon</h1>

<p align="center">
  <b>Embedded Firmware Engineer</b> · STM32 · FreeRTOS · Bare-metal
  <br/>
  Shipping firmware to commercial vehicles 🚌, construction equipment 🚜, and industrial IoT 📡
</p>

<p align="center">
  <img src="https://img.shields.io/badge/MCU-STM32-03234B?logo=stmicroelectronics&logoColor=white"/>
  <img src="https://img.shields.io/badge/Language-C-A8B9CC?logo=c&logoColor=white"/>
  <img src="https://img.shields.io/badge/RTOS-FreeRTOS-8CC84B"/>
  <img src="https://img.shields.io/badge/Wireless-LoRa%20%7C%20LTE%20%7C%20MQTT-blue"/>
  <img src="https://img.shields.io/badge/Fieldbus-RS485%20%7C%20Modbus%20RTU%20%7C%20CAN%20%7C%20J1939-orange"/>
  <img src="https://img.shields.io/badge/Domain-Commercial%20Vehicle%20%7C%20Construction%20Equipment-9B30FF"/>
</p>

---

## 🎯 What I Do

I design and ship STM32-based firmware **end-to-end** — from bootloader to application — for industrial products. Currently in mass production across three verticals via Tier-1 Korean OEMs:

```
🚌 Commercial Vehicle  →  Electric / hydrogen bus OEM          (mass production, 2026-04~)
🚜 Construction        →  Excavator OEM                        (mass production, 2026-04~)
🏠 Home Appliance      →  Major home-appliance OEM + SMEs      (310+ units in field)
```

---

## 🗺️ My Product Map

```mermaid
flowchart LR
    Me([👨‍💻 Firmware])
    Me --> K[Matrix Keypad HMI<br/>bare-metal]
    Me --> S[SAP-100 Sensor Family<br/>FreeRTOS]
    Me --> L[Bolus<br/>LoRa Node]
    Me --> C[YNU Control Box<br/>LTE+MQTT+OTA]
    Me --> I[YNU Ionizer<br/>Air Quality]

    K --> WJ[🚌 Electric/Hydrogen Bus OEM<br/>mass production]
    K --> HD[🚜 Excavator OEM<br/>mass production]
    S --> HA[🏠 Home Appliance OEM<br/>+ SMEs]
    S --> SME[🏭 310+ units<br/>in field]
    L --> Met[📡 Long-range IoT]
    C --> Rem[🌐 Remote OTA]
    I --> Air[💨 Air Quality]

    style Me fill:#03234B,stroke:#03234B,color:#fff
    style WJ fill:#0af,color:#fff
    style HD fill:#f80,color:#fff
    style HA fill:#e00,color:#fff
```

---

## 🧠 Architecture Choice: Bare-metal vs FreeRTOS

I don't pick an architecture by default — I pick it for the product.

```mermaid
flowchart TD
    Q{Product<br/>Requirements}
    Q -->|Deterministic timing<br/>Certification friendly| BM[Bare-metal<br/>ISR + Timer + State Machine]
    Q -->|Concurrent protocols<br/>Sensor + Comm + Control| RT[FreeRTOS<br/>Tasks + Queues + Priority]
    BM --> KP[🎹 Matrix Keypad<br/>commercial vehicle HMI]
    RT --> SAP[🧪 SAP-100<br/>sensor+modbus]
    RT --> YNU[☁️ YNU Control Box<br/>LTE+MQTT+OTA]
    style BM fill:#2a6
    style RT fill:#28c
    style KP fill:#fff
    style SAP fill:#fff
    style YNU fill:#fff
```

> 💡 **The story behind the choice**: On the SAP-100 product line, the original IAR EWARM bare-metal build had intermittent sensor-data-loss issues in the field. I traced the root cause to timing coupling between sensor sampling and Modbus handling, and resolved it by re-architecting to STM32CubeIDE + FreeRTOS with task priorities and queues. This taught me to treat architecture as a problem-solving tool, not a default.

---

## 🔧 Toolbelt

| Layer          | Stack                                                                |
| -------------- | -------------------------------------------------------------------- |
| **MCU**        | STM32 F0/F4 — F030, F071, F072, F429                                 |
| **Firmware**   | Bare-metal, FreeRTOS, HAL / LL / CMSIS                               |
| **Wireless**   | LoRa, LTE, MQTT / MQTTS                                              |
| **Fieldbus**   | RS485 / Modbus RTU, CAN, J1939, UART + DMA, SPI, I2C                 |
| **System**     | Bootloader + OTA (SPI Flash staging, W25Q64, SHA-256 integrity)      |
| **Sensors**    | PM3006S / PM5000S (PM2.5), HTU31D (T&H), BMI270 (IMU)                |
| **Toolchain**  | STM32CubeIDE, IAR EWARM, Git, GDB                                    |
| **Languages**  | C (daily), C++ (occasional)                                          |

---

## 🏆 Recognition

- **Grand Prize** · 2025 President's Cup Software Competition — Korea National Open University
- **People's Choice Award** · 2025 President's Cup Software Competition — Korea National Open University

> **BLE-based accessibility solution for the visually impaired** — Bluetooth RSSI proximity detection + automatic Braille conversion in the user's native language. Designed for multi-national users.
> **Solo project** — planning, design, and implementation all single-handed.

---

## 📌 Featured Projects

> 💡 Proprietary production code is private. The repos below are **open-source demos distilled from the core design patterns** — coming soon. Links become live once each repo is published.

<!--
  Replace <changhoon-yoon> below with your actual GitHub changhoon-yoon.
  Remove any entry whose repo does not yet exist — dead links hurt credibility more than an empty list.
-->

- 🎹 **stm32-bare-metal-keypad-demo** — Deterministic matrix keypad scanning (variant of industrial HMI) · _coming soon_
- 🧪 **stm32-freertos-sensor-modbus-demo** — FreeRTOS tasks + Modbus RTU slave (SAP-100 architecture pattern) · _coming soon_
- ☁️ **stm32-ota-bootloader-demo** — Dual-slot SPI Flash staging bootloader · _coming soon_
- 📡 **stm32-lora-lowpower-demo** — LoRa + low-power sleep (Bolus pattern) · _coming soon_

---

## 📫 Contact

- 📧 changhoon.yoon.eng@gmail.com
- 💼 [LinkedIn](https://www.linkedin.com/in/changhoon-yoon-893199243)
- 🌐 Based in Seoul, South Korea

<p align="center">
  <i>Open to roles and collaboration in commercial vehicle / construction equipment / industrial IoT firmware.</i>
</p>

<!--
GitHub Stats (uncomment and replace <changhoon-yoon> if you want to display them)
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?changhoon-yoon=<changhoon-yoon>&show_icons=true&theme=dark"/>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?changhoon-yoon=<changhoon-yoon>&layout=compact&theme=dark"/>
</p>
-->
