# Computer Fundamentals

*This module ...*

[Inside a Computer System](#inside-a-computer-system) · [Computer Types](#computer-types) · [Client-Server Basics](#client-server-basics) · [Virtualization Basics](#virtualization-basics) · [Cloud Computing Fundamentals](#cloud-computing-fundamentals)

> Notes from the second section of TryHackMe's **Pre Security** learning path.

## Inside a Computer System

*This room covers the basic components of a computer system.*

### Core Components of the Computer System

**Central Processing Unit** (CPU): The "brain" of the computer. It executes instructions and performs the calculations and logical operations that drive every task the system carries out.

**Motherboard**: The main circuit board that connects and lets all the other components communicate. Everything plugs into it (CPU, RAM, storage, expansion cards).

**Random Access Memory** (RAM):  Fast, temporary storage that holds data and programs the CPU is actively using. It's volatile, meaning its contents are lost when the machine powers off.

**Storage** (SSD/HDD):  Non-volatile storage that retains data long-term, even without power. HDDs use spinning magnetic disks, while SSDs use flash memory.

**Power Supply** (PSU):  Converts mains electricity from the wall into the regulated low-voltage power the internal components need, and distributes it to them.

**Network Adapter**: The component that connects the computer to a network, enabling communication with other devices. It can be wired (Ethernet) or wireless (Wi-Fi).

**Graphics Card**: Handles rendering images, video, and graphics for display. It offloads visual processing from the CPU and is essential for graphics-intensive work like gaming or 3D rendering.

**Input/Output** (I/O):  The mechanisms by which a computer receives data and sends it back out. Input devices (keyboard, mouse) feed data in, while output devices (monitor, printer) deliver results.

### What Happens When you Press the Start Button?

Once the core components are installed in the computer system, it is time to boot up the system.

###### The steps a computer system goes through before it shows you a working interface (in the form of an Operating System) is as follows:

**Step 1: Press the power button**
> When we press the power button on our computer system, a signal is sent to the PSU to allow power to flow. Once power is distributed to the components, the system begins to boot up.

**Step 2: Firmware starts**
> Once the system has power, its core components are up and running, but the operating system is not yet loaded. A computer system contains firmware that allows all its components to start up. The central system that manages this is called the Unified Extensible Firmware Interface (UEFI).

**Step 3: Power-on self test**
> Now that the system is up and running, it is time to test if everything is functioning as it should. If something isn't, alarm signals (such as beep codes) are raised. One of the routines that the UEFI loads is the Power-On Self Test (POST), which checks that every required component is present, configured correctly, and functioning.

**Step 4: Select boot device**
> Once the system is up and running, configured correctly, and fully functional, it searches for the location of the bootup routine to start loading the operating system. The UEFI holds an ordered list which prioritizes which device to look at first for the boot-up routine.

**Step 5: Initiate bootloader**
> Now that the system knows which device holds the boot-up routine, it initiates the load routine to start it. On the selected boot device, the bootloader is initiated. This bootloader transfers the operating system from the selected boot device to the Random Access Memory (RAM). Once the OS is transferred, the UEFI hands over control of the different components to the OS.

### Key Takeaways

## Computer Types

*This room covers ...*

### Key Takeaways

## Client-Server Basics

*This room covers ...*

### Key Takeaways

## Virtualization Basics

*This room covers ...*

### Key Takeaways

## Cloud Computing Fundamentals

*This room covers ...*

### Key Takeaways
