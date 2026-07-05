# Operating System Basics

*This module ...*

[Operating Systems: Introduction](#operating-systems-introduction) · [Windows Basics](#windows-basics) · [Linux CLI Basics](#linux-cli-basics) · [Windows CLI Basics](#windows-cli-basics) · [Operating System Security](#operating-system-security)

> Notes from the third section of TryHackMe's **Pre Security** learning path.

## Operating Systems: Introduction

*This room covers what an operating system is, the core duties it performs, and the different types of OS in use today.*

### The Invisible Manager

An **Operating System** (OS) is the core software that coordinates everything happening on a computer. It sits between the user, applications, and the system's physical hardware, acting as the invisible manager that keeps the entire machine running as one unified system.

#### System Privilege Layers

Inside a modern computer, different parts of the system operate at various permission levels. Some components can communicate directly with the hardware, while regular applications run in a safer, restricted environment.

> This separation is intentional and helps prevent conflicts and security issues.

**Kernel space**: The privileged, locked-down core of the OS. This is where the kernel, the part of the operating system that directly manages hardware and system resources, runs. It has unrestricted access to the CPU, memory, storage, and all hardware components.

**User space**: Where all standard applications run. Applications in the user space are deliberately prevented from accessing hardware directly. Whenever they need to open or save a file, play a sound, or connect to Wi-Fi, they must make a system call and request that the kernel act on their behalf.

#### Operating System Duties

Every OS is responsible for a few core duties that allow your computer to run safely, efficiently, and predictably.

###### OS responsibilities and what it does:

| **OS Responsibility** | **What the OS Does** | **Example** |
| --- | --- | --- |
| Process Management | Creates, schedules, prioritizes, and terminates running programs. The OS decides how much CPU time each process gets, making multitasking feel seamless. | Opening multiple apps, like your browser, music player, and social media, without your computer freezing. |
| Memory Management | Allocates RAM to processes, protects the app's memory from other processes, and reclaims memory when apps are closed. When RAM runs low, the OS uses virtual memory to keep your system stable. | Opening multiple apps at once, the OS allocates RAM to each one and keeps them isolated so they don't interfere or crash each other. |
| File System Management | Organizes files into directories, handles naming, paths, permissions, metadata (name, size, type, timestamps). | Creating a new folder, saving a photo, or setting a file to "read only". |
| User Management | Handles multiple user accounts, authentication, and permissions to determine who can access what. | Logging in with your password and keeping your files inaccessible to other user accounts. |
| Device Management | Loads drivers and provides a universal interface (hardware abstraction layer), so apps can say "print this" or "play this sound". | Plugging in a new mouse, printer, or external hard drive and having it work immediately. |

#### Operating System Built-In Security

Every OS performs essential security functions.

###### At a basic level, your operating system handles:

- **Authentication**: Verifies who you are through login passwords and biometrics.
- **Permissions**: Controls exactly what each user and app is allowed to read, write, or execute.
- **Isolation**: Keeps every process in its own protected box (kernel/user space separation).
- **System Protection**: Safeguards critical system files and settings from unauthorized changes.

### OS Interaction and Landscape

Interaction with the OS can be divided into two main parts: the Graphical User Interface (GUI) and the Command-Line Interface (CLI).

**Graphical User Interface** (GUI): A visual way of interacting with a computer through graphical elements like windows, icons, menus, and buttons, typically navigated with a mouse and keyboard. It's intuitive and beginner-friendly, since you can see and click what you want rather than memorizing commands.

**Command-Line Interface** (CLI): A text-based way of interacting with a computer, where you type commands to tell the system what to do. It has a steeper learning curve than a GUI, but it's faster, more powerful, and more precise for many tasks, such as automation, remote administration, and much of the security work you'll be doing.

Not all operating systems are the same. Different devices and jobs demand different designs.

###### Operating system types with their use and characteristics:

| **Operating System Type** | **Primary Use Case** | **Key Characteristics** |
| --- | --- | --- |
| Desktop | PCs, daily work, gaming, content creation | Graphical, runs many apps at once, user-focused |
| Server | Databases, cloud services, back-end | Headless (no GUI), maximum uptime, multi-user, remote access |
| Mobile | Smartphones and tablets | Touch-based UI, power efficient, app sandboxing |
| Embedded | Appliances, cars, IoT devices, smart TVs | Tiny footprint, runs on limited hardware |
| Virtual/Cloud | VMs, containers, cloud instances | Lightweight, scalable, rapid deployment |

#### Real World Operating Systems

In the real world, there are many operating systems in use,

###### The common versions and distributions:

- **Desktop**
  - **Windows**: The most widely used operating system on personal computers.
    - *Windows 10 (end-of-life), Windows 11*
  - **macOS**: Apple's desktop OS, known for its polished GUI and integration with other Apple devices.
    - *Sonoma (14), Sequoia (15), Tahoe (26)*
  - **Linux**: Not a single OS but a family of open-source operating systems called distributions.
    - *Ubuntu, Debian, Fedora*
- **Server**
  - **Windows**: Used in large networks, data centers, and corporate environments.
    - *Server 2016, 2019, 2022, 2025*
  - **Linux**: The vast majority of web servers, trusted for its reliability and open-source nature.
    - *Ubuntu Server, Debian, CentOS, Red Hat*
  - **Unix**: Large enterprises, finance, telecom, and government.
    - *IBM AIX, Oracle Solaris*
- **Mobile**
  - **Android**: The most widely used mobile OS, which runs on phones, tablets, and smart devices.
    - *Android 14 - 16, Manufacturer versions*
  - **iOS**: Apple's mobile OS running on iPhones, iPads, and other devices.
    - *iOS 17, 18, 26*
- **Embedded**
  - **Linux**: Specialized OS built into devices with dedicated functions.
    - *OpenWrt, Ubuntu Core, Yocto Project*
  - **Real-Time OS**: Designed for apps where tasks need guaranteed response times.
    - *FreeRTOS, VxWorks, QNX*
- **Virtual/Cloud**
  - **Cloud/VM**: Massive data centers that host websites, apps, and streaming services.
    - *Ubuntu LTS, Amazon Linux, Rocky Linux*
  - **Container-Optimized**: Lightweight alternatives to VMs that package just the app and its dependencies.
    - *Alpine Linux, Bottlerocket AWS, Flatcar Linux*

### Key Takeaways

An operating system is the core software sitting between users, applications, and hardware, coordinating the whole machine while enforcing a strict separation between privileged kernel space and restricted user space. Its core duties span process, memory, file system, user, and device management, alongside security functions such as authentication, permissions, and process isolation. Operating systems come in many forms, from desktop and server to mobile, embedded, and cloud, and are interacted with through either a graphical (GUI) or command-line (CLI) interface.

## Windows Basics

*This room covers ...*

### Key Takeaways

## Linux CLI Basics

*This room covers ...*

### Key Takeaways

## Windows CLI Basics

*This room covers ...*

### Key Takeaways

## Operating System Security

*This room covers ...*

### Key Takeaways
