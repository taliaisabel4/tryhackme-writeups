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

### Logging In and Authentication

The authentication process verifies your identity and determines the actions you're allowed to take once logged in. When a Windows system starts, it displays a login screen where a user account must be selected and authenticated with a password, PIN, or another verification method.

###### Windows uses these account types:

- **Guest**: A restricted account intended for temporary access, with minimal permissions and no ability to change system settings.
- **Standard**: A user account for everyday tasks, such as running applications and changing personal settings, without access to system-wide changes.
- **Administrator**: A privileged account with full control over the system, including software installation, configuration changes, and user management.

#### Windows Desktop

The **Windows Desktop** is the first thing that shows up once you log in.

###### You're presented with two main areas:

- **Desktop**: The main workspace where files, folders, and shortcuts live.
- **Taskbar**: A control strip that provides access to applications, system tools, settings, and notifications.

###### While newer Windows versions may differ slightly, these core components and concepts remain consistent:

- **Desktop Icons**: Shortcuts to items like the Recycle Bin, folders, and frequently used applications. It is fully customizable.
- **Start Menu**: Primary way to access applications, settings, and power options. From here, you can log out, restart, or power off your machine.
- **Search**: Quickly find applications, files, folders, and system settings by using keywords.
- **Task View**: Allows you to see all currently open windows and quickly switch between them.
- **Pinned Applications and Folders**: Your most used applications and folders can be pinned here.
- **Network and Audio Settings**: This section can be customized to suit your needs.
- **Date and Time**: Opens up to a full calendar. Date and time settings can be accessed here.
- **Notifications**: Displays computer or application notifications. Network and other settings can also be accessed.

#### Build-In Tools and Apps

Windows also includes simple but powerful tools such as **Notepad** for editing text files and **File Explorer** for navigating and managing files. These tools are available immediately and form the foundation of everyday Windows usage. All of them can be accessed via the Start Menu and search bar.

#### Getting System Information

Windows includes a built-in Settings application that allows you to configure and view information about your system.

> Within the Settings app, there's a helpful section called **About your PC**, that provides an overview of security, device, and operating system information.

#### File Exploration and Management

Windows uses a hierarchical folder structure, meaning folders can contain other folders and files inside them. This structure helps keep data organized and makes it easier to locate information as systems grow larger.

> Common locations, such as the **Desktop**, **Documents**, and **Downloads**, serve as primary directories for storing files.

### Configuring and Securing Applications

**Applications** are the programs and tools you use to perform tasks on your computer. These processes enable you to make the necessary changes to your system, ensuring you have exactly what you need and that your system remains secure.

#### Updating Your Applications

Keeping your operating system and applications up to date is an important part of maintaining a secure and stable system. Updates will often include security patches, performance updates, and bug fixes.

#### Windows Updates

Windows includes a built-in update tool called **Windows Update**, which keeps the OS and some native applications and security features up to date.

> Windows Update can be accessed through the Settings app and may install updates automatically, depending on your configuration.

#### Updating Applications

Application updates work differently depending on how the software is installed.

###### These include:

- Built-in applications may update automatically in the background.
- Third-party applications often include their own update mechanisms.
- Some applications will prompt you to update upon launch.
- Some require you to check for updates or download a new installer manually.

#### Installing and Uninstalling Applications

Installing applications...

###### There are two ways to install applications:

- **Microsoft Store**: Provides a curated and safe option for installing apps to Windows, although it is not available by default on Windows Server.
- **From the Internet**: In many environments, apps are installed by downloading an installer directly from a trusted vendor's website. They usually come in an `.exe` or `.msi` file and guide the user through the installation process.

###### There are multiple ways to uninstall programs:

- Using the Microsoft Store for installed applications.
- Add or remove programs feature in system settings.
- Uninstall a program section of the Control Panel.
- Using an application's built-in uninstaller.

#### Diving into Settings

There are two primary ways in which a Windows user can modify their environment.

###### There are existing shortcuts for each of the tools below placed on your Desktop:

- **Windows Settings**: A modern, centralized location for configuring system, device, personalization, and security settings in Windows.
- **Control Panel**: A legacy management interface that provides access to older system configuration tools still required for specific administrative tasks.

> **Windows Settings** and the **Control Panel** enable you to view and modify how your Windows system operates.

#### The Task Manager

**Task Manager** is a built-in Windows tool that allows you to monitor what is happening on your system in real time. It allows you to view running applications and background processes, as well as check system performance, including CPU and memory usage.

###### Task Manager has five tabs to help you keep track of your system:

- **Processes**: Currently running apps and background processes, and their resource usage.
- **Performance**: Graphs and statistics for system resources such as CPU, memory, and network.
- **Users**: Currently logged-in users and used resources .
- **Details**: A more technical view of running processes, including process IDs (PIDs).
- **Services**: Windows services and their current status (running or stopped).

#### Native Windows Security

Windows offers built-in security tools designed to help protect your system from threats such as malware, insecure applications, and unauthorized network access. These are enabled by default and allow the monitoring and control of your system's security. 

The **Windows Security** application is your central dashboard for managing Windows' built-in protection measures.

###### It is divided into four main sections, each focusing on a different area of system security:

- **Virus & threat protection**: Helps detect and remove malicious software using real-time protection and customizable scans.
- **Firewall & network protection**: Controls incoming and outgoing network traffic to help prevent unauthorized access.
- **App & browser control**: Protects users from potentially unsafe apps, files, and websites.
- **Device security**: Provides hardware-based protections that help secure the system.

#### Windows Defender Firewll

**Windows Defender Firewal**l is a built-in firewall designed to help protect your computer from unauthorized network traffic. It monitors network connections and applies rules that determine whether the connections are allowed or denied. 

###### The firewall operates on different network profiles, allowing you to create custom rules or specify applications that are permitted:

- **Domain**: Used when a system is connected to an organization’s domain network.
- **Private**: Intended for trusted networks, such as a home or lab environment.
- **Public**: Used for untrusted networks, such as public Wi-Fi.

### Key Takeaways

## Linux CLI Basics

*This room covers ...*

### Interacting with the Terminal using Linux Commands

These are the Linux core navigation commands that every Linux users use.

###### Core navigation commands:

- **`pwd`**: 
- **`ls`**:
- **`cd`**:
- **`find`**:
- **`cat`**:
- **`whoami`**
- **`uname`**

### Key Takeaways

## Windows CLI Basics

*This room covers ...*

### Interacting with the Terminal using Windows Commands

These are the Windows core navigation commands that every Window users use.

###### Core navigation commands:

- **`cd`**: 
- **`dir`**:
- **`type`**:
- **`whoami`**:
- **`hostname`**:
- **`systeminfo`**
- **`ipconfig`**

### Key Takeaways

## Operating System Security

*This room covers ...*

### Key Takeaways
