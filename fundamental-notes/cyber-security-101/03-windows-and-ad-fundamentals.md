# Windows and AD Fundamentals

*This module ...*

[Windows Fundamentals 1](#-windows-fundamentals-1) · [Windows Fundamentals 2](#-windows-fundamentals-2) · [Windows Fundamentals 3](#-windows-fundamentals-3)

> Notes from the third section of TryHackMe's **Cyber Security 101** learning path.

## Windows Fundamentals 1
<img width="96" height="96" alt="1773338771062-windowsfundamentals1xbx" src="https://github.com/user-attachments/assets/41700e63-a48d-4d28-ab0a-5f2ff080fc53" />

### Windows Editions

The Windows operating system (OS) is a complex product with many system files, utilities, settings, features, etc.

Windows has been the dominant OS for home and corporate use since 1985, which also makes it a primary target for hackers and malware writers. Its version history moved from Windows XP to the poorly received Vista, then the widely adopted Windows 7, the short-lived Windows 8.x, and on to Windows 10 and the current desktop version, Windows 11. Microsoft has improved usability and security with each release.

###### About Windows:

- Windows 11 editions comes in two flavors: Home and Pro.
- Pro supports BitLocker encryption, which Home cannot enable.
- The current server OS is Windows Server 2025.

### The Desktop (GUI)

The **Desktop (GUI)** is the graphical user interface shown after logging in with valid credentials (a local account or an Active Directory account on a domain-joined machine).

###### Main GUI components:

- **The Desktop**: Holds shortcuts to programs, folders, and files for quick access; right-clicking gives a context menu, and appearance can be changed via Display settings (resolution/orientation) and Personalize (wallpaper, fonts, themes, colors).
- **Start Menu**: Opened via the Windows logo; provides access to apps, files, and utilities. Split into account/session shortcuts (settings gear, power options), recently added and installed apps (alphabetical), and tiles (pinned app shortcuts on the right).
- **Search Box (Cortana)** Task View, Taskbar, Toolbars, and the Notification Area make up the rest of the interface.
- **Taskbar**: Shows open apps; hovering gives a preview thumbnail and tooltip. Right-click it to enable/disable components.
- **Notification Area**: usually bottom-right; displays date/time plus icons like volume and network. Icons are managed in Taskbar settings.

### The File System

Modern Windows uses the NTFS (New Technology File System). Earlier systems were FAT16/FAT32 (File Allocation Table) and HPFS (High Performance File System). FAT is still common on USB drives and MicroSD cards but not on modern Windows PCs/servers.

The **NTFS** is a journaling file system it can automatically repair files/folders after a failure using a log file (FAT cannot do this).

###### NTFS advantages include:

- Supporting files larger than 4GB
- Setting folder/file permissions and folder/file compression
- Encryption via Encryption File System (EFS)

### The Windows\System32 Folders

The **Windows** folder `C:\Windows` traditionally contains the OS. It doesn't have to sit on the C drive, its location is referenced by the system environment variable `%windir`.

**Environment variables**: Store information about the OS environment, such as the OS path, number of processors used, and location of temporary folders.

The **System32** folder holds critical OS files. Deleting files here can render Windows inoperable, so proceed with extreme caution. Many Windows tools live in System32.

### User Accounts, Profiles, and Permissions

Local Windows accounts are one of two types: **Administrator** and **Standard User**.

**Administrator**: Can make system-level changes; add/delete users, modify groups, change settings, and install programs.

**Standard User**: Can only change their own files/folders and cannot make system-level changes (e.g., cannot install programs).

When an account is created, a profile is created under `C:\Users`, built on first login by the **User Profile Service**.

> Each profile has the same default folders, including Desktop, Documents, Downloads, Music, and Pictures.

**Groups**: Each group has set permissions; when the Administrator adds a user to a group, the user inherits that group's permissions, and a user can belong to multiple groups.

The command `lusrmgr.msc` or **Local User and Group Management**, shows two folders, **Users** and **Groups**, listing local accounts and groups with descriptions.

> Run dialog box lets you quickly open items.

### User Account Control (UAC)

Many home users run as local administrators, but running with elevated privileges all the time increases risk; malware would run in the context of the logged-in user and could more easily compromise the system.

**User Account Control** (UAC) helps prevent malware from damaging a PC and helps organizations deploy a better-managed desktop. With UAC, apps and tasks always run in the security context of a non-administrator account, unless an administrator specifically authorizes administrator-level access to the system.

> UAC can block the automatic installation of unauthorized apps and prevent inadvertent changes to system settings.

### Settings and the Control Panel

The two primary places to make system changes are the **Settings menu** and the **Control Panel**, both accessible from the **Start Menu**.

**Control Panel**: the long-standing location for more complex settings and actions.

**Settings menu**: Introduced in Windows 8 and is now the primary place users go to change the system.

> Some **Settings** actions redirect into the **Control Panel**.

## Task Manager

The **Task Manager** shows information about the applications and processes currently running on the system, including resource usage such as CPU and RAM.

> Accessed by right-clicking the taskbar; opens in Simple View, and clicking **More details** expands it to show full information.

## Windows Fundamentals 2
<img width="96" height="96" alt="1773338774698-windowsfundamentals2x0x" src="https://github.com/user-attachments/assets/3011cf4b-ec7e-425f-9de4-477c12e4f539" />

## Windows Fundamentals 3
<img width="96" height="96" alt="1773338778881-windowsfundamentals3xzx_" src="https://github.com/user-attachments/assets/ede1e7d7-4484-4547-97a4-a871f73af11e" />
