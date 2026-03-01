# 🤖 LABUBOT

**LABUBOT** is a high-performance, precision-tuned line follower robot system. It features a custom Android dashboard inspired by the "Opera GX" aesthetic and a robust MicroPython-based firmware for the ESP32-S3.

With LABUBOT, you can tune PID values in real-time, drive manually using an on-screen joystick, or take full control with a DualShock 4 controller.

---

## ✨ Key Features

### 📡 Advanced Connectivity
*   **Zero-Lag BLE:** Uses a specialized command queue and "Write Without Response" mode for high-frequency updates.
*   **Dual-Layer Discovery:** Scans via both Device Name ("LABUBOT") and Service UUID for rock-solid pairing.
*   **Watchdog Recovery:** Automatic connection stabilization to prevent stalls during fast inputs.

### 🎮 Control Modes
*   **PID Tuner:** Real-time adjustment of $K_p$, $K_d$, Base Speed, and Pivot Speed.
*   **Profile System:** Save and load custom tuning presets (e.g., "Sharp Turns", "Speed Bridge").
*   **Arcade Drive:** On-screen joystick for simple manual navigation.
*   **Tank Drive (DS4 Support):** Full DualStick control using a physical DualShock 4 controller (Left Stick = Left Motor, Right Stick = Right Motor).

### 🎨 Premium UI
*   **Opera GX Inspired:** Deep black background (`#0B0B0D`) with neon red accents and glowing cards.
*   **Full-Screen Dashboard:** Immersive, distraction-free interface.
*   **Smooth UX:** Fade-in startup animations and real-time visual feedback for connection status.

---

## 🛠 Hardware Requirements
*   **Microcontroller:** ESP32-S3
*   **Motors:** Dual DC motors with an H-Bridge driver (L298N, DRV8833, etc.)
*   **Sensors:** 6-Array IR Reflectance Sensor
*   **Gamepad (Optional):** Sony DualShock 4 (PS4 Controller)

---

## 🚀 Getting Started

### 1. ESP32-S3 Setup (MicroPython)
1.  Flash your ESP32-S3 with the latest [MicroPython firmware](https://micropython.org/download/ESP32_GENERIC_S3/).
2.  Copy `labubot_main.py` from this repo to your device and rename it to `main.py`.
3.  Ensure your motor pins match the GPIOs defined in the script (Default: 7, 6, 14, 8).

### 2. Android App Setup
1.  Install the `LABUBOT.apk` on your Android device (ensure "Install from Unknown Sources" is enabled).
2.  Enable **Bluetooth** and **Location Services** (GPS is required for BLE scanning on Android).
3.  Open the app and tap **INITIALIZE CONNECTION**.

### 3. DualShock 4 Pairing
1.  Hold **PS + Share** buttons on your controller until it flashes.
2.  Pair it in your phone's Bluetooth settings as "Wireless Controller".
3.  The LABUBOT app will automatically detect inputs and switch to Tank Drive mode.

---

## 📟 Communication Protocol (BLE)

LABUBOT uses a simple string-based protocol over the Nordic UART Service:

| Command | Action | Example |
| :--- | :--- | :--- |
| `P[val]` | Set Kp | `P0.65` |
| `D[val]` | Set Kd | `D0.55` |
| `B[val]` | Set Base Speed | `B150` |
| `V[val]` | Set Pivot Speed | `V140` |
| `S[0/1]` | Stop / Start | `S1` |
| `J[x,y]` | Arcade Drive | `J100,-50` |
| `T[l,r]` | Tank Drive | `T80,80` |

---

## 📂 Project Structure
*   `/app`: Android Studio project (Kotlin/Jetpack).
*   `labubot_main.py`: ESP32-S3 MicroPython firmware.
*   `/res`: UI assets, including the custom glow drawables and Opera GX theme.

---

## 📜 License
MIT License - Feel free to use this for your own robot competitions!
