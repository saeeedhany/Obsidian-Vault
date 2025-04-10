## **1. What is an Interrupt Service Routine (ISR)?**

An Interrupt Service Routine (ISR) is a piece of code responsible for handling **interrupts** when they occur during system operation. Interrupts are signals sent to the **CPU** by hardware or software to notify it of an event that needs immediate attention.

### **Steps of ISR Execution:**

1. **Interrupt Detection:** The CPU receives an interrupt signal from a device or software.
2. **Saving CPU State:** The CPU saves its current state to resume later.
3. **Identifying the Appropriate ISR:** The system determines the address of the ISR.
4. **Executing the ISR:** The ISR runs to handle the interrupt.
5. **Restoring CPU State:** The CPU retrieves its previous state.
6. **Resuming Normal Execution:** The CPU continues executing the previous program.

---

## **2. What is a "Fixed Location"?**

A "Fixed Location" is a **predefined memory address** where the system stores information on how to handle interrupts. In early systems, all interrupts were directed to a fixed address known as the **interrupt entry point**.

### **How Does "Fixed Location" Work?**

- When an interrupt occurs, the CPU checks a **predefined memory address** to determine **where the ISR code is stored**.
- This method is called **"Fixed Interrupt Vectoring"**.
- Each type of interrupt was assigned a **predefined fixed address** in memory.

---

## **3. What is a "Starting Address"?**

A "Starting Address" is the address stored within the **Fixed Location**, which points to the actual **ISR code in memory**.

### **How is the "Starting Address" Used?**

1. When an interrupt is detected, the CPU looks up the **Fixed Location** to find the **Starting Address** of the ISR.
2. Once found, the CPU **jumps to that address** and starts executing the ISR.
3. After executing the ISR, the CPU resumes executing the previous program.

---

## **4. Practical Example of "Fixed Location" and "Starting Address"**

### **Example: Pressing a Key on the Keyboard**

1. When you press a key, the **keyboard controller** sends an interrupt to the CPU.
2. The CPU checks the **Fixed Location** for the **Starting Address** of the keyboard ISR.
3. If the Fixed Location contains address **0x0008**, the CPU jumps to **0x0008**, where the keyboard ISR starts executing.
4. The ISR processes the key press and stores the input in memory.
5. After execution, the CPU resumes its previous program.

---

## **5. Modern Interrupt Handling - Moving from "Fixed Location" to "Interrupt Vector Table"**

Modern systems no longer rely on a single "Fixed Location" but instead use a **more flexible mechanism**:

- Instead of storing ISR addresses at fixed locations, they are stored in an **Interrupt Vector Table (IVT)**.
- The CPU uses an **Interrupt Number** to find the exact ISR address in the **IVT**.
- This approach provides **greater flexibility** in handling interrupts, especially in multitasking operating systems.

---

## **6. Summary**

-> **ISR (Interrupt Service Routine)** is a piece of code executed to handle hardware or software events requiring immediate attention.
-> **Fixed Location** is a predefined memory address containing information about ISR locations.
-> **Starting Address** is the address stored in the Fixed Location that points to the actual ISR code.
-> Modern systems use an **Interrupt Vector Table (IVT)** instead of Fixed Locations for more efficient interrupt handling.