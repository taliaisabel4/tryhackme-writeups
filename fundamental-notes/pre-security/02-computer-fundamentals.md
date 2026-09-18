# Computer Fundamentals

> **This module moves from the components inside a single computer to how machines communicate with each other, and finishes with virtualization and the cloud.**

[Inside a Computer System](#-inside-a-computer-system) · [Computer Types](#-computer-types) · [Client-Server Basics](#-client-server-basics) · [Virtualization Basics](#-virtualization-basics) · [Cloud Computing Fundamentals](#-cloud-computing-fundamentals)

`Notes from the second section of TryHackMe's Pre Security learning path.`

## <img src="https://github.com/user-attachments/assets/d6d04e77-bb23-4336-accf-24059a0d8334" width="50" height="50" align="middle" alt="Inside a Computer System room icon"> Inside a Computer System

> **This room covers the core hardware components inside a computer system and the boot sequence it runs through from power button to operating system.**

### Core Components of the Computer System

**Central Processing Unit** (CPU): The component that executes program instructions, often described as the brain of the computer. It fetches each instruction from memory, decodes it, and performs the arithmetic and logic that produce a result.

**Motherboard**: The main circuit board that every other component connects to, through a socket, a slot, or a cable. It carries the pathways that let the CPU, RAM, storage, and expansion cards exchange data and receive power.

**Random Access Memory** (RAM): Fast, temporary storage that holds the data and programs the CPU is actively working on. It is volatile, so everything in it is lost the moment the system loses power.

**Storage** (SSD/HDD): Non-volatile storage that keeps data between sessions, including the operating system, applications, and user files. HDDs write to spinning magnetic disks, while SSDs use flash memory with no moving parts, which makes them faster and more durable.

**Power Supply** (PSU): Converts the alternating current from a wall outlet into the regulated low-voltage direct current the internal components require. It then distributes that power across the motherboard, drives, and other hardware.

**Network Adapter** (NIC): The component that connects the computer to a network and handles sending and receiving data across it. It can be wired through an Ethernet port or wireless through Wi-Fi.

**Graphics Card** (GPU): Handles rendering the images, video, and 3D graphics sent to a display. It takes that work off the CPU, which matters most for graphics-intensive tasks such as gaming, video editing, and 3D rendering.

**Input/Output** (I/O): The exchange of data between the computer and the outside world. Input devices such as a keyboard or mouse send data into the system, while output devices such as a monitor or printer deliver results back to the user.

### Boot Process of the Computer System

Once the core components are in place, the system needs a way to bring them online and hand control to an operating system. That sequence is the **boot process**, and it runs the same way every time the machine is powered on.

###### The steps a computer system goes through before it shows you a working interface (in the form of an operating system) are as follows:

**Step 1: Press the power button**
> Pressing the power button signals the PSU to begin supplying power to the motherboard and everything attached to it. Once power is flowing and stable, the system starts the boot sequence.

**Step 2: Firmware starts**
> At this point the components have power but nothing is loaded yet, since the operating system still sits on storage. Firmware built into the motherboard takes over first and initializes the hardware so it can be used. On modern systems that firmware is the Unified Extensible Firmware Interface (UEFI), which replaced the older BIOS.

**Step 3: Power-on self test**
> One of the first routines the UEFI runs is the Power-On Self Test (POST), which confirms that every required component is present, configured correctly, and responding. If something fails the test, the system reports it through beep codes or on-screen error messages instead of continuing. Catching a fault here stops the machine from trying to boot on hardware that cannot support it.

**Step 4: Select boot device**
> With the hardware verified, the UEFI has to find where the operating system lives. It works through an ordered boot list, checking each device in priority order, such as an internal drive, a USB drive, or a network location, until it finds one that holds a valid boot routine.

**Step 5: Initiate bootloader**
> The UEFI then hands off to the bootloader stored on the selected device. The bootloader copies the operating system from storage into RAM and starts it. Control passes from the firmware to the operating system, which takes over managing the hardware and presents the interface you log in to.

### Key Takeaways

A computer system is built from components with distinct jobs: the CPU executes instructions, RAM holds what is in active use, storage keeps data without power, the motherboard connects everything, and the PSU supplies electricity. Booting is a fixed sequence that moves from power, to firmware initialization, to hardware verification through POST, to selecting a boot device, to the bootloader loading the operating system into RAM. Each stage depends on the one before it, which is why a failure early in the chain halts the process rather than producing a partly working system. Knowing this sequence makes it easier to reason about where a machine can fail and where firmware-level tampering would sit.

## <img src="https://github.com/user-attachments/assets/4090bd2d-f3eb-49f6-b09a-befeb687f41c" width="50" height="50" align="middle" alt="Computer Types room icon"> Computer Types

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
| IoT device | Network-connected device with a single purpose. | Thermostat, smart doorbell |
| Embedded computer | Computer built into another device. | Coffee maker controller, automatic door sensor |

> The difference between IoT devices and embedded computers is that IoT devices connect to a network to report data or receive commands, while embedded computers might not connect to anything and simply do their job inside the machine.

### Key Takeaways

Computers come in many forms, each shaped by its purpose: portable laptops, fixed desktops and workstations for sustained or precise work, and servers that provide services to many users over a network. Computing also extends into everyday objects, from smartphones and tablets to IoT and embedded devices built for narrow, dedicated tasks. The key distinction among those smaller devices is connectivity: IoT devices communicate over a network, whereas embedded computers may operate entirely inside the device they control.

## <img src="https://github.com/user-attachments/assets/e910d8f9-d08a-4cea-8069-a8b9da79f119" width="50" height="50" align="middle" alt="Client-Server Basics room icon"> Client-Server Basics

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

The client-server model underpins web communication: a client such as a browser sends requests, and a server responds with the requested resource. HTTP is the protocol governing this exchange, and it is stateless, meaning each request is handled on its own without the server remembering previous ones. Requests use defined methods such as `GET`, which retrieves a resource, and each response carries a status code indicating the outcome along with any requested data.

## <img src="https://github.com/user-attachments/assets/aa020d09-3bdd-45de-992e-0767ca74a35d" width="50" height="50" align="middle" alt="Virtualization Basics room icon"> Virtualization Basics

*This room covers the basics of virtualization, including hypervisors, virtual machines, and containers.*

### Virtualization Overview

Before the concept of virtualization, the rule of thumb in IT was: *"One server = one application."*

> Virtual computers act as independent systems, each with its own operating system, applications, and settings, even though they all share the same physical hardware underneath.

### Virtualization Components

A **hypervisor** is the core technology behind virtualization. It's the software that creates and manages virtual machines.

###### It is a special piece of software that:

- Divides a physical computer into multiple virtual ones.
- Gives each virtual machine its own share of CPU, memory, and storage.
- Keeps everything isolated and safe.
- Manages the lifecycle of virtual machines (start, stop, pause, clone, delete).

###### Hypervisors have two main types of implementation, each of which is used for specific scenarios:

- **Type 1 Hypervisors**: Run directly on the physical hardware, making them fast, efficient, and ideal for servers and professional environments.
- **Type 2 Hypervisors**: Run within an existing operating system, making them easier to install and ideal for learning, testing, or small setups.

A **Virtual Machine** (VM) is a virtual computer created by the hypervisor.

> You can deploy VMs on your own computer using tools such as Oracle VirtualBox and VMware Workstation.

###### Even though it's virtual, it behaves as a real machine:

- It has its own virtual CPU, RAM, storage, and network.
- It can run any operating system (Windows, Linux, etc.).
- It's completely isolated from other VMs.

A **container** is a lightweight, isolated environment that runs a single application and all the necessary components to support it. Instead of bringing a whole separate operating system, a container borrows the core of the existing system by running on the kernel, which is the part of an operating system that communicates with the hardware and manages resources such as memory and running programs.

> Because containers share this kernel, they start quickly and use fewer resources than full virtual machines. However, this also means they must match the host system's type.

###### Containers behave like small, self-contained spaces because:

- They package the application and its dependencies (libraries, tools, versions).
- They share the host's operating system, so they start almost instantly.
- They remain isolated from each other, so a misbehaving container doesn't affect the others.
- They can run consistently on any machine, making them perfect for development, testing, and scalable deployments.

### Key Takeaways

Virtualization lets a single physical machine run multiple isolated systems, each with its own operating system and share of the hardware, managed by a hypervisor that runs either directly on the hardware (Type 1) or on top of an existing operating system (Type 2). Containers take a lighter approach, packaging a single application with its dependencies and sharing the host's kernel, which makes them start faster and use fewer resources than full virtual machines.

## <img src="https://github.com/user-attachments/assets/2d8962f4-73d4-41ee-b85f-d92a3f5e6e7a" width="50" height="50" align="middle" alt="Cloud Computing Fundamentals room icon"> Cloud Computing Fundamentals

*This room covers the fundamentals of cloud computing, including its benefits, deployment types, and service models.*

### Cloud Computing Overview

**Cloud computing** is the delivery of computing resources, such as servers, storage, and software, over the internet on demand. Instead of owning and maintaining physical hardware, you can rent what you need and access it from anywhere.

### Cloud Benefits and Characteristics

The cloud was designed to address common problems, including limited capacity, high costs, and slow growth.

###### The following benefits and characteristics explain how cloud computing makes applications easier to run, scale, and manage:

- **Scalability**: Easily scale up or down as your application's needs change.
- **On-demand self-service**: Create or remove servers and storage instantly, without waiting for hardware.
- **Pay only for what you use**: You are charged based on usage, not upfront costs.
- **Security**: Cloud providers protect the infrastructure with strong security measures.
- **High availability**: Applications keep running even if part of the system fails.
- **Global access**: Your application can be accessed by users anywhere in the world.

### Types of Cloud

The flexibility provided by cloud computing allows applications to be run in different ways, depending on your needs and level of control. Because of this, cloud providers offer multiple models for deploying and using applications, each suited to different scenarios.

###### The deployment types you can choose for a cloud environment:

- **Public cloud**: Computing resources (servers, storage, applications) owned and operated by a third-party cloud provider and delivered over the internet.
- **Private cloud**: Cloud infrastructure dedicated to a single organization. It can be hosted on-premises or by a third party, but the resources aren't shared with anyone else.
- **Hybrid cloud**: A combination of public and private cloud that lets data and applications move between the two.

Just like there are different ways to deploy a cloud environment, there are also different ways to use cloud services. Depending on your experience and needs, you can choose the level of responsibility that fits your application.

###### The main cloud service models:

- **Infrastructure as a Service** (IaaS): The provider gives you the raw infrastructure (virtual machines, storage, networking); you manage the OS, runtime, and applications on top.
- **Platform as a Service** (PaaS): The provider manages the infrastructure and platform (OS, runtime, tools); you just build and deploy your applications.
- **Software as a Service** (SaaS): The provider delivers a complete, ready-to-use application over the internet; you simply use it, usually through a browser.

### Key Takeaways

Cloud computing delivers computing resources such as servers and storage over the internet on demand, removing the need to own and maintain physical hardware. Its main advantages are scalability, pay-as-you-go pricing, high availability, and global access, which let applications grow and adapt without large upfront investment. Cloud environments can be deployed as public, private, or hybrid models, and consumed through service models offering increasing levels of provider management: IaaS, PaaS, and SaaS.
