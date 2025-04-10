
# 🖥️ I/O Operation in Computer System Architecture

This document provides a detailed, step-by-step explanation of the I/O operation, particularly focusing on how a USB keyboard input is processed from the mechanical press to the final CPU handling, including the role of each hardware and software component involved.

---

## 1. 🔧 Mechanical Action of the Keyboard

- When a key is pressed, a **mechanical switch** inside the keyboard is activated.
- This switch closes an electrical circuit corresponding to the pressed key.
- The resulting electrical signal is sent to a small microcontroller inside the keyboard.

---

## 2. 🧠 Microcontroller and Scan Code Generation

- The keyboard’s **microcontroller** detects which row and column of the matrix are closed (based on which key is pressed).
- It maps this location to a **Scan Code**.
- The Scan Code is a hardware-level representation of the key's physical location, not the actual character (e.g., the letter 'A').

---

## 3. 🔌 Signal Transmission via USB

- The scan code is sent over USB as a **serial signal** using the USB protocol.
- The data is packed into packets and transmitted to the computer.

---

## 4. 🌳 USB Root Hub

- The USB signal first reaches the **Root Hub** built into the motherboard.
- The Root Hub acts as a **signal distributor**, forwarding the USB packet to the appropriate **USB Host Controller**.

---

## 5. 🧰 USB Host Controller

- The **Host Controller** receives the packet and:
  - Verifies it (including **CRC checking**).
  - Extracts the scan code.
  - Stores it in a **Memory-Mapped I/O register**.
- Then, it raises an **interrupt signal** to inform the CPU of the new data.

---

## 6. 🚨 Interrupt Generation

- The Host Controller raises an **Interrupt Request (IRQ)** to the CPU via the interrupt controller (like APIC).
- This signals that new I/O data is ready to be processed.

---

## 7. 🧠 CPU Interrupt Handling

- The CPU suspends its current task and jumps to the **[[Interrupt Service Routine (ISR)]]**.
- The ISR for USB keyboard is part of the **Device Driver**.

---

## 8. 📦 Role of the Device Driver

- The **Device Driver** is a software component loaded by the OS.
- It is responsible for:
  - Translating scan codes into actual characters (or commands).
  - Interfacing with user-level software or the kernel.
- The OS uses **enumeration** during device connection to load the appropriate driver based on the **Vendor ID** and **Product ID**.

---

## 9. 🧵 Summary of the Flow

```
[Key Pressed] 
    ↓
[Keyboard Microcontroller → Scan Code]
    ↓
[USB Transmission]
    ↓
[Root Hub]
    ↓
[Host Controller → CRC Check + Store in Memory]
    ↓
[Interrupt Raised]
    ↓
[CPU Interrupt Handler]
    ↓
[Device Driver Handles the Code]
    ↓
[System Reacts (e.g., types letter)]
```

---

## 10. 🧠 Additional Clarifications

- **Memory-Mapped I/O:** Host Controller uses specific physical addresses to communicate with the CPU.
- **CRC Check:** Ensures data integrity during transmission.
- **Interrupts:** Efficient mechanism to avoid CPU polling.

---

## ✅ Final Notes

This pipeline reflects a deep understanding of how I/O works from physical action to OS response. All of it fits within the broader scope of Computer Architecture and Operating System design.

