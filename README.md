# sinerla 

An AirPlay bridge for legacy **Sonos Connect:Amp (Gen 1)** hardware using a **Raspberry Pi**, **Shairport-sync**, and **Python**.

This project breathes new life into older Sonos devices by capturing AirPlay audio, converting it into an HTTP live stream that Sonos can play, and handling smart automation like input switching and volume synchronization.

---

## 🚀 Features

* **AirPlay for Sonos Gen 1:** Stream audio from any Apple device to your legacy Sonos Connect:Amp.
* **Automatic Input Switching:** Automatically switches the Sonos source to the HTTP stream when AirPlay starts, and restores the previous input/source when the stream ends.
* **State & Volume Memory:** Remembers the previous input and automatically restores your old volume levels after the session.
* **Smart Volume Sync:** Synchronizes iPhone/AirPlay volume changes directly with the Sonos hardware and output stream.

---

## 🛠️ How It Works (Architecture)

1. **AirPlay Receiver:** The Raspberry Pi runs `shairport-sync` to act as an AirPlay target.
2. **HTTP Stream:** Audio captured by Shairport is converted into an HTTP audio stream accessible by Sonos.
3. **Python Automation:** Background Python scripts monitor the Shairport state and use the Sonos API (SoCo) to orchestrate everything.

### ⚠️ Note on Volume Control (Known Limitation)
Due to the binary nature of iOS/iPhone volume steps, volume control behavior is currently a bit unique:
* Volume scaling works **linearly** with the iPhone volume slider.
* The script adjusts both the *output source volume* and the *Sonos hardware volume* simultaneously. 
* *Result:* The volume curve works perfectly, but may feel a bit "funny" or non-standard when looking at the sliders.

---

## 📋 Prerequisites

To get this running, you will need:
* A **Raspberry Pi** (connected to the same local network as your Sonos).
* **Sonos Connect:Amp (Gen 1)**.
* `shairport-sync` installed on the Pi.
* Python 3 with required libraries (e.g., `soco` for Sonos control).

---
