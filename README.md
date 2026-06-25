# Edge-to-Cloud-Heat-Monitoring-For-Industrial-Environments
## 📖 Overview

This project is an **IoT-enabled Environmental Monitoring System** built using the **LPC2148 ARM7 Microcontroller**, **ESP8266 (ESP-01 Wi-Fi Module)**, **MQ2 Smoke Sensor**, **LM35 Temperature Sensor**, and a **16x2 LCD**.

The system continuously monitors room temperature and smoke levels. Whenever smoke is detected, an alarm is activated through a buzzer and the event is immediately uploaded to **ThingSpeak Cloud** using the ESP8266 Wi-Fi module. Temperature data is also periodically sent to ThingSpeak for remote monitoring and analysis.

---

## ✨ Features

* 🌡 Real-time temperature monitoring using LM35
* 🚭 Smoke detection using MQ2 sensor
* 📺 Live status display on 16x2 LCD
* 🔔 Buzzer alert during smoke detection
* 📡 Wi-Fi connectivity using ESP8266 (ESP-01)
* ☁ ThingSpeak cloud integration
* 📈 Remote monitoring of sensor data
* ⏰ RTC support for periodic cloud updates
* 🔄 Automatic data upload at fixed intervals

---

## 🛠 Hardware Components

| Component      | Description          |
| -------------- | -------------------- |
| LPC2148        | ARM7 Microcontroller |
| ESP8266 ESP-01 | Wi-Fi Module         |
| MQ2 Sensor     | Smoke/Gas Detection  |
| LM35           | Temperature Sensor   |
| 16x2 LCD       | Local Display        |
| Buzzer         | Smoke Alert          |
| RTC            | Time Tracking        |
| Power Supply   | 5V Regulated         |

---

## 💻 Software Requirements

* Keil µVision
* Embedded C
* Flash Magic
* ThingSpeak Cloud Platform

---

## 📂 Project Structure

```text
MAJOR/
│
├── main.c
├── esp01.c
├── esp01.h
├── rtc.c
├── rtc.h
├── lcd.c
├── lcd.h
├── ADC.C
├── adc_defines.h
├── uart0.c
├── uart0.h
├── delay.c
├── delay.h
├── defines.h
├── types.h
├── Startup.s
└── ESP01.uvproj
```

---

## 🔄 System Workflow

```text
START
   |
Initialize LCD
Initialize UART
Initialize ADC
Initialize RTC
Initialize ESP8266
   |
Connect Wi-Fi
   |
Read Temperature
Read Smoke Sensor
   |
Display Values on LCD
   |
Smoke Detected?
   |
  YES ------------------- NO
   |                       |
Activate Buzzer            |
Upload Alert              Continue Monitoring
to ThingSpeak              |
   |                       |
Periodic Temperature Upload
   |
Repeat Forever
```

---

## 📺 LCD Display

### Normal Condition

```text
TEMP: 28°C
SMOKE: NDETECTED
```

### Smoke Detected

```text
TEMP: 28°C
SMOKE: DETECTED
```

---

## ☁ ThingSpeak Integration

The system uploads:

### Field 1

* Temperature Value

### Field 2

* Smoke Detection Status

Example API Request:

```http
GET /update?api_key=YOUR_API_KEY&field1=28
```

```http
GET /update?api_key=YOUR_API_KEY&field2=1
```

---

## 📡 Wi-Fi Configuration

Update the following credentials inside `esp01.c`:

```c
UART0_Str("AT+CWJAP=\"YOUR_WIFI_NAME\",\"YOUR_PASSWORD\"\r\n");
```

Update ThingSpeak API Key:

```c
GET /update?api_key=YOUR_API_KEY
```

---

## 🔔 Alert Mechanism

When smoke is detected:

* LCD displays **DETECTED**
* Buzzer turns ON
* Smoke status uploaded to ThingSpeak
* Alarm automatically resets after processing

---

## 🌡 Temperature Measurement

Temperature is measured using the LM35 sensor:

```text
Temperature (°C) = Sensor Voltage × 100
```

The ADC value is converted into voltage and then into temperature.

---

## 🏗 Pin Configuration

| Device     | LPC2148 Pin   |
| ---------- | ------------- |
| MQ2 Sensor | P0.10         |
| Buzzer     | P0.15         |
| LCD Data   | P0.16 – P0.23 |
| LCD RS     | P0.8          |
| LCD EN     | P0.9          |
| LCD RW     | P0.10         |
| ESP8266    | UART0         |
| LM35       | ADC Channel 1 |

---

## 🚀 Build & Flash

### Build

1. Open `ESP01.uvproj` in Keil µVision.
2. Select LPC2148 device.
3. Compile the project.
4. Generate HEX file.

### Flash

1. Connect LPC2148 board.
2. Open Flash Magic.
3. Select generated HEX file.
4. Program the controller.

---

## 📊 Applications

* Industrial Safety Monitoring
* Fire Detection Systems
* Smart Home Automation
* Laboratory Monitoring
* Warehouse Safety
* Environmental Monitoring

---

## 🔮 Future Enhancements

* SMS Alert using GSM
* Mobile App Dashboard
* Email Notifications
* MQTT Cloud Integration
* Multi-Sensor Monitoring
* OLED/TFT Display Support

---

## 👨‍💻 Author

**IoT-Based Smoke & Temperature Monitoring System**
Developed using **LPC2148 ARM7**, **ESP8266**, **MQ2 Smoke Sensor**, **LM35**, and **ThingSpeak Cloud** for real-time environmental monitoring and alert generation.

---

### Project Output

✅ Temperature Monitoring
✅ Smoke Detection
✅ LCD Status Display
✅ Cloud Data Logging
✅ Buzzer Alarm System
✅ Wi-Fi Connectivity
✅ ThingSpeak Integration

