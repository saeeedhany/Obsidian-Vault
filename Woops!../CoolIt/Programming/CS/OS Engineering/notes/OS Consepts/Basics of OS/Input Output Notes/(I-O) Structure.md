<font color="#548dd4">--> Storage is only one of many types of <font color="#ffffff">I/O</font> devices within computer.</font>
<font color="#548dd4">--> A large portion of operating system code is dedicated to managing <font color="#ffffff">I/O</font>, both because of its importance to the reliability and performance of a system and because of the varying nature of the device</font>

--> A general-purpose computer system consists of **CPU**s and multiple device controller that are connected through a common bus
--> Each *device controller* is in charge of a specific type of device.
> <font color="#e36c09">device controller</font> -> maintains -> Local Buffer Storage & Set of special purpose register.

--> Typically, operations systems have a device driver for each device controller 
--> This device driver understands the device controller and present a uniform interface to the device to the rest of the operating system.

### **Working of an (I/O) Operation**
![[Working of an (I-O) Operation.canvas]]
 
<font color="#4f81bd">-> To start an <font color="#ffffff" font-weight="bold">I/O</font> operation, the device driver loads the appropriate within the device controller</font>
-> The device controller, in turn examines the contents of these registers to determine what action to take
-> The controller starts the transfer of data from the device to its local buffer
-> Once the transfer of data is complete, the device controller informs the device driver via an interrupt that it has finished its operation 
->The device driver then returns control to the operating system
>**This form of interrupt-driven I/O is fine for moving small amount of data but can produce high overhead when used for bulk data movement.**

*To solve this problem, Direct memory access (DMA) is used*.

-> After setting up buffers, pointers, and counters for the I/O device, the device controller transfer an entire block of data directly to or from its own buffer storage to memory, with no intervention by CPU.

-> Only one interrupt is generated per block, to tell the device driver that the operation has completed
-> while the device controller is performing these operations, the **CPU** is available to accomplish other work





