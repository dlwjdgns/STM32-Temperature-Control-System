# STM32-Temperature-Control-System

> STM32 MCU를 사용하여 온도와 팬/환풍구를 자동으로 제어하는 펌웨어입니다. 온도 센서(DS18B20)로 내부 온도를 측정하여 설정값에 도달하면 히터를 끄고, 모터 팬과 서보 모터 환풍구를 동작시켜 효율적으로 식품을 건조합니다.

<br>

## ✨ Core Features

- **자동 온도 제어**: 설정된 온도를 기준으로 히터를 자동으로 ON/OFF하여 내부 온도를 유지합니다.
- **팬 및 환풍구 연동 제어**: 설정 온도에 도달하면 히터를 끄고, **DC 모터 팬**을 작동시켜 내부 공기를 순환시키며 동시에 **서보 모터**로 환풍구를 열어  공기를 배출합니다.
- **듀얼 디스플레이**: **OLED 화면**과 **4-Digit 7-Segment(FND)**를 통해 현재 온도와 히터 동작 상태를 실시간으로 표시합니다.
- **직관적인 사용자 인터페이스**: 3개의 푸시 버튼으로 목표 온도를 쉽게 올리고, 내리고, 설정할 수 있습니다.
- **동작 상태 표시**: LED를 통해 히터의 ON/OFF 상태를 시각적으로 확인할 수 있습니다.

<br>

## ⚙️ How It Works (Logic Flow)

1.  **온도 설정**: 사용자가 `UP`/`DOWN` 버튼으로 원하는 건조 온도를 설정하고 `FIX` 버튼으로 확정합니다.
2.  **동작 시작**: 메인 스위치를 `ON` 상태로 전환하면 시스템이 동작을 시작합니다.
3.  **가열 단계**: 시스템은 환풍구(서보)를 닫고 팬(DC 모터)을 정지시킨 상태에서 히터(릴레이)를 켭니다.
4.  **건조/순환 단계**: 내부 온도가 설정 온도에 도달하면, 시스템은 히터를 끄고 **환풍구를 열며 팬을 동작**시킵니다.
5.  **온도 유지**: 내부 온도가 설정값보다 일정 수준 이하로 떨어지면, 다시 **가열 단계**로 돌아가 온도를 유지합니다.

<br>

## 🛠️ Tech Stack & Components

#### Hardware
- **MCU**: `STM32F103C8T6`
- **Sensor**: `DS18B20` Digital Temperature Sensor
- **Display**: 
    - `SSD1306` I2C OLED Display
    - 4-Digit 7-Segment (FND) Display via SPI
- **Actuators**:
    - `5V Relay Module` for Heater Control
    - `DC Motor` for Fan Control (via PWM)
    - `SG90 Servo Motor` for Vent Control (via PWM)
- **Input**: `Push Buttons` (x3), `Toggle Switch` (x1)
- **Indicator**: `LEDs` (x2)

#### Software
- **IDE**: `STM32CubeIDE`
- **Language**: `C`
- **Core Libraries**: `STM32 HAL Library`
- **Debugger**: `ST-LINK/V2`

<br>

## 📜 License

This project is licensed under the **GNU General Public License v3.0**.

The core licensing of this project is determined by its dependencies. The driver for the DS18B20 sensor is based on the work from **[nimaltd/ds18b20](https://github.com/nimaltd/ds18b20)**, which is licensed under GPL-3.0. Consequently, this entire project is also released under the same license.

Additionally, the implementation for the SSD1306 OLED display was referenced from the tutorial provided by **[ControllersTech](https://controllerstech.com/oled-display-using-i2c-stm32/)**.


For the full license text, please see the `LICENSE` file included in this repository.
