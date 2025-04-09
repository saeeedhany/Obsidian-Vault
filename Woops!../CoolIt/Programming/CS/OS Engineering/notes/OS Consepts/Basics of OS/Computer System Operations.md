*Some basic knowledge of the structure of computer system is required to understand how operating system work.*

--> A modern *General-Purpose* Computer system consists of one or more *[[CPU]]* s and a number of device controllers connected through a common bus that provides access to shared memory.
![[OSoperations.png]]
- Each device controller is in charge of a specific type of device.
- The *CPU* and the device controllers can execute concurrently, competing for memory cycles
- To ensure orderly access to the shared memory, a memory controller is provided whose function is to synchronize access to the memory.

**<u>Some important terms :</u>**
*1)* Bootstrap Program : 
- The initial program that runs when a computer is powered up or rebooted.
- It is stored in the **[[ROM]]**.
- It must know how to load into memory the OS and start executing that system.
- It must locate and load into memory of **[[ The Kernel]]** of an OS.

*2)* Interrupt : 
- The occurrence of an event is usually signaled by an Interrupt from Hardware or Software.
- Hardware may trigger an interrupt at any time by sending a signal to the *CPU*, usually by the way of the system bus.

*3)* System Call (Monitor call) :
- Software may trigger an interrupt by executing a special operation called system call.

When The **CPU** is interrupted, it stops what it is doing and immediately transfers execution to a *Fixed Location*.
                --> The fixed location usually contains the starting address where the [[Interrupt Service Routine (ISR)]] of the interrupt is located.
The Interrupt Service Routine executes.
On completion, the CPU resumes the interrupted computation.
