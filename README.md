# Wireless-Car-Remote-Hacking
### **Wireless Car Remote Hacking using Replay and Roll Jam Attacks**

## 🛠️ **Project Overview**

This project demonstrates how to exploit wireless car remotes by performing **Replay** and **Roll Jam** attacks using **RTL-SDR** and **Raspberry Pi**. The attack targets car remote systems operating on **433 MHz** frequency, which are commonly used in keyless entry systems. The main goal of this project is to show how vulnerable some wireless car remotes can be to simple hacking techniques.

---

## 🔐 **Key Features**

- **Replay Attack**: Captures and replays the signal from the car remote to unlock the car.
- **Roll Jam Attack**: Intercepts and jams the communication between the car remote and the car, allowing the attacker to send their own signal.
- **Low-Cost Setup**: Uses inexpensive hardware, including RTL-SDR and Raspberry Pi, for signal capturing and manipulation.
- **433 MHz Frequency**: Focuses on 433 MHz frequency, a common band for car remote keyless entry systems.

---

## 💡 **How It Works**

The system primarily relies on two main attacks:

### **Replay Attack**
1. **Capture**: The attacker captures the signal from the legitimate car remote using an RTL-SDR receiver.
2. **Replay**: The signal is then played back to the car, which responds as if the legitimate key was used, unlocking the car.

### **Roll Jam Attack**
1. **Jam**: The attacker jams the signal transmission between the car remote and the car, effectively blocking any legitimate signal.
2. **Capture & Replay**: Once the signal is blocked, the attacker captures the next valid signal from the car remote and replays it to unlock the car.

---

## 🔧 **Tools Used**

- **RTL-SDR**: A software-defined radio receiver used to capture the 433 MHz signals.
- **Raspberry Pi**: The hardware platform used to process the captured signals and execute the attack.
- **433 MHz Transceiver**: A common transceiver for transmitting and receiving signals in this project.
- **Software**: 
  - `gnuradio` for signal processing
  - `rtlsdr` for interacting with the RTL-SDR hardware
  - `python` for controlling the attack logic

---

## 📝 **Setup Instructions**

1. **Hardware Requirements**:
   - RTL-SDR USB Dongle
   - Raspberry Pi (Model 3 or later recommended)
   - 433 MHz Transceiver (compatible with Raspberry Pi)

2. **Software Requirements**:
   - Install the necessary libraries and tools:
     ```bash
     sudo apt-get update
     sudo apt-get install rtl-sdr gnuradio python3-pip
     pip3 install pyserial
     ```
   
3. **Hardware Connections**:
   - Plug the RTL-SDR USB dongle into the Raspberry Pi’s USB port.
   - Connect the 433 MHz transceiver to the GPIO pins on the Raspberry Pi.
   
4. **Capturing the Signal**:
   - Use the RTL-SDR to capture the car remote signal:
     ```bash
     rtl_sdr -f 433920000 -s 250000 -g 20 -n 1000000 captured_signal.raw
     ```
   
5. **Replaying the Signal**:
   - Use the captured signal and replay it to unlock the car:
     ```bash
     python3 replay_attack.py captured_signal.raw
     ```

6. **Executing Roll Jam**:
   - Block the legitimate signal using a jammer, and then replay the captured signal to unlock the car:
     ```bash
     python3 roll_jam_attack.py captured_signal.raw
     ```

---

## 🎯 **Safety & Legal Disclaimer**

This project is intended for educational purposes only. Performing these attacks on any system without permission is illegal and unethical. **Always ensure you have explicit permission from the owner before testing any security system.**

---

## 🚀 **Future Enhancements**

- **Multi-Frequency Support**: Extend support for additional frequencies beyond 433 MHz.
- **Automatic Detection**: Implement automatic detection of car remote signals.
- **Enhanced Jamming Techniques**: Improve jamming reliability with more advanced techniques.

---

## 📝 **References**

- RTL-SDR Documentation: [https://www.rtl-sdr.com/](https://www.rtl-sdr.com/)
- GNU Radio: [https://www.gnuradio.org/](https://www.gnuradio.org/)
- 433 MHz Car Key Fob Signals: [https://en.wikipedia.org/wiki/Keyless_entry](https://en.wikipedia.org/wiki/Keyless_entry)

---

## 📄 **License**

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
