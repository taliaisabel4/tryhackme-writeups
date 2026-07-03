# Computer Fundamentals

*This module ...*

[Inside a Computer System](#inside-a-computer-system) · [Computer Types](#computer-types) · [Client-Server Basics](#client-server-basics) · [Virtualization Basics](#virtualization-basics) · [Cloud Computing Fundamentals](#cloud-computing-fundamentals)

> Notes from the second section of TryHackMe's **Pre Security** learning path.

## Inside a Computer System

*This room covers the basic components of a computer system and the boot process it runs through on startup.*

### Core Components of the Computer System

**Central Processing Unit** (CPU): The "brain" of the computer. It executes instructions and performs the calculations and logical operations that drive every task the system carries out.

**Motherboard**: The main circuit board that connects all the other components and lets them communicate. Everything plugs into it (CPU, RAM, storage, expansion cards).

**Random Access Memory** (RAM): Fast, temporary storage that holds data and programs the CPU is actively using. It's volatile, meaning its contents are lost when the machine powers off.

**Storage** (SSD/HDD): Non-volatile storage that retains data long-term, even without power. HDDs use spinning magnetic disks, while SSDs use flash memory.

**Power Supply** (PSU): Converts mains electricity from the wall into the regulated low-voltage power the internal components need, and distributes it to them.

**Network Adapter**: The component that connects the computer to a network, enabling communication with other devices. It can be wired (Ethernet) or wireless (Wi-Fi).

**Graphics Card**: Handles rendering images, video, and graphics for display. It offloads visual processing from the CPU and is essential for graphics-intensive work like gaming or 3D rendering.

**Input/Output** (I/O): The mechanisms by which a computer receives data and sends it back out. Input devices (keyboard, mouse) feed data in, while output devices (monitor, printer) deliver results.

### Boot Process of the Computer System

Once the core components are installed in the computer system, it is time to boot up the system.

###### The steps a computer system goes through before it shows you a working interface (in the form of an operating system) are as follows:

**Step 1: Press the power button**
> When we press the power button on our computer system, a signal is sent to the PSU to allow power to flow. Once power is distributed to the components, the system begins to boot up.

**Step 2: Firmware starts**
> Once the system has power, its core components are up and running, but the operating system is not yet loaded. A computer system contains firmware that allows all its components to start up. The central system that manages this is called the Unified Extensible Firmware Interface (UEFI).

**Step 3: Power-on self test**
> Now that the system is up and running, it is time to test if everything is functioning as it should. If something isn't, alarm signals (such as beep codes) are raised. One of the routines that the UEFI loads is the Power-On Self Test (POST), which checks that every required component is present, configured correctly, and functioning.

**Step 4: Select boot device**
> Once the system is up and running, configured correctly, and fully functional, it searches for the location of the boot-up routine to start loading the operating system. The UEFI holds an ordered list which prioritizes which device to look at first for the boot-up routine.

**Step 5: Initiate bootloader**
> Now that the system knows which device holds the boot-up routine, it initiates the load routine to start it. On the selected boot device, the bootloader is initiated. This bootloader transfers the operating system from the selected boot device to the Random Access Memory (RAM). Once the OS is transferred, the UEFI hands over control of the different components to the OS.

### Key Takeaways

A computer system is built from core hardware components that each serve a distinct purpose: the CPU executes instructions, RAM provides fast volatile working memory, storage retains data without power, the motherboard connects everything, and the PSU supplies power. Startup follows a defined sequence: the power button engages the PSU, UEFI firmware brings the components up and runs POST to verify them, a boot device is selected, and the bootloader loads the operating system into RAM. Understanding both the parts and the boot chain is the foundation for reasoning about how a system behaves and where it can fail or be interfered with.

## Computer Types

*This room covers the different types of computers and the purposes they serve.*

All computer types serve different purposes such as portable everyday computing and sustained performance at a fixed location.

###### The different types of computers:

| **Computer Type** | **Screen and Keyboard** | **Main Purpose** |
| --- | --- | --- |
| Laptop | Yes | Portable everyday computing. |
| Desktop | Yes | Sustained performance at a fixed location. |
| Workstation | Yes | Precision and reliability for professional tasks. |
| Server | No | Providing services to many users over a network. |

###### Computers in everyday objects:

| **Type** | **Purpose** | **Examples** |
| --- | --- | --- |
| Smartphone | Pocket-sized computer optimized for battery life and connectivity. | iPhone, Android phone |
| Tablet | Touch-first computer with a larger screen. | iPad, drawing tablet |
| IoT device | Network-connected device with a single purpose. | Thermostat, smart doorbell |
| Embedded computer | Computer built into another device. | Coffee maker controller, automatic door sensor |

> The difference between IoT devices and embedded computers is that IoT devices connect to a network to report data or receive commands, while embedded computers might not connect to anything and simply do their job inside the machine.

### Key Takeaways

Computers come in many forms, each shaped by its purpose: portable laptops, fixed desktops and workstations for sustained or precise work, and servers that provide services to many users over a network. Computing also extends into everyday objects, from smartphones and tablets to IoT and embedded devices built for narrow, dedicated tasks. The key distinction among those smaller devices is connectivity: IoT devices communicate over a network, whereas embedded computers may operate entirely inside the device they control.

## Client-Server Basics

*This room covers the basics of the client-server model.*

### Web Communication

**Hypertext Transfer Protocol** (HTTP) is a stateless client-server protocol used for the World Wide Web. This means that each request is processed independently, without the server retaining information about previous requests.

> Although the protocol itself is stateless, modern websites and web applications implement mechanisms to introduce statefulness at the application level.

###### The core methods HTTP defines:

- `GET`
- `POST`
- `PUT`
- `DELETE`
- `PATCH`
- `HEAD`
- `OPTIONS`
- `CONNECT`
- `TRACE`

#### GET

The **`GET`** method can retrieve a resource from a web server.

###### An example of using the `GET` method:

`GET https://tryhackme.com/index.php`

This request retrieves the TryHackMe website's homepage. When you open a browser (this is the client) and type "https://tryhackme.com," the browser constructs the message behind the scenes using information you provide and other fields defined in the HTTP specifications. When the web server receives the request, it sends a response that includes a status code (indicating the type of response) and the requested information.

### Key Takeaways

The client-server model underpins web communication: a client such as a browser sends requests, and a server responds with the requested resource. HTTP is the protocol governing this exchange, and it is stateless, meaning each request is handled on its own without the server remembering previous ones. Requests use defined methods such as GET, which retrieves a resource, and each response carries a status code indicating the outcome along with any requested data.

## Virtualization Basics

*This room covers the basics of virtualization, including hypervisors, virtual machines, and containers.*

### Virtualization Overview

Before the concept of virtualization, the rule of thumb in IT was: *“One server = one application.”*

Virtual computers act as independent systems, each with its own operating system, apps, and settings, even though they all share the same physical hardware underneath.

### Virtualization Components

A **hypervisor** is the core technology behind virtualization. It's the software that creates and manages virtual machines.

###### It is a special piece of software that:

- Divides a physical computer into multiple virtual ones.
- Gives each virtual machine its own share of CPU, memory, and storage.
- Keeps everything isolated and safe.
- Manages the lifecycle of virtual machines (start, stop, pause, clone, delete).

Hypervisors have two main types of implementation, each of which is used for specific scenarios:

- **Type 1 Hypervisors**: Run directly on the physical hardware, making them fast, efficient, and ideal for servers and professional environments.
- **Type 2 Hypervisors**: Run within an existing operating system, making them easier to install and ideal for learning, testing, or small setups.

A **Virtual Machine** (VM) is a virtual computer created by the hypervisor.

> You can deploy VMs on your own computer using tools such as Oracle VirtualBox and VMware Workstation.

###### Even though it’s virtual, it behaves as a real machine:

- It has its own virtual CPU, RAM, storage, and network.
- It can run any operating system (Windows, Linux, etc.).
- It’s completely isolated from other VMs.

A **container** is a lightweight, isolated environment that runs a single application and all the necessary components to support it. Instead of bringing a whole separate operating system, a container borrows the core of the existing system by running on the kernel, which is the part of an operating system that communicates with the hardware and manages resources such as memory and running programs.

> Because containers share this kernel, they start quickly and use fewer resources than full virtual machines. However, this also means they must match the host system's type.

###### Containers behave like small, self-contained spaces because:

- They package the application and its dependencies (libraries, tools, versions).
- They share the host’s operating system, so they start almost instantly.
- They remain isolated from each other, so a misbehaving container doesn’t affect the others.
- They can run consistently on any machine, making them perfect for development, testing, and scalable deployments.

### Key Takeaways

Virtualization lets a single physical machine run multiple isolated systems, each with its own operating system and share of the hardware, managed by a hypervisor that runs either directly on the hardware (Type 1) or on top of an existing operating system (Type 2). Containers take a lighter approach, packaging a single application with its dependencies and sharing the host's kernel, which makes them start faster and use fewer resources than full virtual machines.

## Cloud Computing Fundamentals

*This room covers ...*

### Key Takeaways
