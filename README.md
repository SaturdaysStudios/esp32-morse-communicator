<div align="center">

# ⚡ ESP32 Wireless Morse Code Communicator

<img src="https://img.shields.io/badge/Platform-ESP32-blue?style=for-the-badge&logo=espressif" />
<img src="https://img.shields.io/badge/Protocol-ESP--NOW-green?style=for-the-badge" />
<img src="https://img.shields.io/badge/Language-C++-orange?style=for-the-badge&logo=c%2B%2B" />
<img src="https://img.shields.io/badge/License-MIT-purple?style=for-the-badge" />

*A peer-to-peer, bidirectional wireless messaging system powered by ESP-NOW, I2C OLED displays, and custom tactile buttons.*

</div>

---

## 🚀 Features

* **Bidirectional P2P Messaging:** Send and receive text messages wirelessly between two ESP32 boards without needing a Wi-Fi router or internet connection.
* **Gliding Alphabet Cheat Sheet:** The idle screen features an auto-rotating Morse code reference guide that cycles every 2 seconds so anyone can jump in and write.
* **Dynamic Received Messages:** Incoming messages automatically switch to a dedicated full-screen view with automatic font sizing for short or long texts.
* **Visual Status Feedback:** Flashes a confirmation screen upon successful message transmission.
* **High Responsiveness:** Optimized 5ms polling loop for instant button reaction times.

---

## 🛠️ Hardware Requirements

For a complete two-way setup, you will need:

| Quantity | Component | Description |
| :---: | :--- | :--- |
| **2x** | ESP32 DevKit V1 | 30-pin or 38-pin microcontroller boards |
| **2x** | I2C OLED Display | 128x64 pixels, SSD1306 driver |
| **2x** | Tactile Push Buttons | 4-pin momentary switches |
| **2x** | Breadboards & Wires | Half-size breadboards and jumper wires |

---

## 📌 Wiring Diagram

Both ESP32 units use identical wiring. Connect your components as follows:

| Component | Component Pin | ESP32 GPIO Pin | Description |
| :--- | :--- | :--- | :--- |
| **OLED Display** | VCC | 3.3V | Power Supply |
| **OLED Display** | GND | GND | Common Ground |
| **OLED Display** | SCL | **GPIO 19** | I2C Clock |
| **OLED Display** | SDA | **GPIO 22** | I2C Data |
| **Push Button** | Pin 1 (Side A) | **GPIO 21** | Input Signal |
| **Push Button** | Pin 2 (Side B) | **GND** | Pulls Pin LOW on Press |

> **Breadboard Tip:** Make sure your 4-pin push button spans across the center divide (trench) of the breadboard to prevent internal short-circuiting.

---

## ⚙️ Installation & Setup

### 1. Install Dependencies
Open your **Arduino IDE** and install the following libraries via *Sketch > Include Library > Manage Libraries*:
* `Adafruit GFX Library`
* `Adafruit SSD1306`

### 2. Get Your MAC Addresses
Upload a simple Wi-Fi STA sketch to both ESP32 boards and check the Serial Monitor (115200 baud) to record their unique MAC addresses.

### 3. Configure & Flash
1. Open the respective code files for **ESP32 #1** and **ESP32 #2**.
2. Update the `receiverAddress[]` array in each script with the other board's MAC address.
3. Select your board and COM port in Arduino IDE, then flash the code to each board.

---

## 📖 How to Operate

1. **Idle State:** The screen displays incoming messages (if any) and a rotating Morse code alphabet guide.
2. **Typing:** 
   * **Quick tap (< 1 sec):** Inputs a dot (`.`).
   * **Medium hold (1–5 sec):** Inputs a dash (`-`).
   * **Letter conversion:** Pausing for 1.2 seconds automatically converts your code into text.
3. **Sending:** Press and hold the button for **5 seconds**. The screen will display **"SENT!"** for 2 seconds before returning to idle.
