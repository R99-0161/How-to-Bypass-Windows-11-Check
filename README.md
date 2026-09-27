# Windows 11 Installation & Setup Guide

A practical guide documenting Windows 11 installation methods for situations where the standard setup process requires a Microsoft account or where a PC does not meet the standard Windows 11 hardware requirements.

## Why I Made This

When refurbishing, selling, or repairing PCs, customers may ask for Windows 11 to be installed on their machine.

Sometimes a PC can have perfectly capable hardware but still be blocked by Windows 11's standard hardware requirements. In other situations, when preparing a PC for sale, I may need to complete Windows setup without linking my own Microsoft account to the machine so that the new owner can set up their own account.

I created this guide to document the installation and troubleshooting methods I use when preparing PCs for customers or personal projects.


---

# How to Bypass Microsoft Login

How to bypass the Microsoft Account login firstly…

### 1. Boot into Windows 11 Setup

Start your PC with the Windows 11 installation media.

### 2. Open Command Prompt

At the Windows 11 setup screen, press:

`Shift + F10`

This opens Command Prompt.

### 3. Execute Bypass Command

Type:

`OOBE\BYPASSNRO`

Then press **Enter**.

> **Note:** Microsoft has been phasing this shortcut out on newer builds. If it doesn't work, open Command Prompt (`Shift + F10`) and run this instead, then restart:
> `reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\OOBE /v BypassNRO /t REG_DWORD /d 1 /f`

### 4. Restart Setup

The system will reboot and return to the Windows setup screen.

### 5. Proceed With Local Account

Choose the option to set up a local account instead of a Microsoft account.

---

# How to Bypass Windows 11 Check

How to bypass **"This PC doesn't meet system requirements"**…

### 1. Open Command Prompt

When the Windows 11 setup says **"Choose operating system type"**, press:

`Shift + F10`

The Command Prompt will open.

### 2. Open Registry Editor

Type:

`regedit`

Then press **Enter**.

### 3. Create the LabConfig Key

Go to:

`HKEY_LOCAL_MACHINE > SYSTEM > Setup`

Right-click **Setup** and select:

**New → Key**

Call this:

`LabConfig`

Then press **Enter**.

### 4. Create DWORD Values

In this folder, right-click in the blank area and select:

**New → DWORD (32-bit) Value**

Create **four** of these.

### 5. Rename the Values

Rename each value to:

`BypassTPMCheck`

`BypassCPU`

`BypassRAMCheck`

`BypassSecureBootCheck`

### 6. Set the Values

Double-click each of these values and set **Value data** to:

`1`

Select **OK** and repeat this for all four values.

### 7. Continue With Setup

You can now safely close the Registry Editor and continue with the Windows setup.

---

# Example Use Case

A typical situation where I may use this process:

**Customer → PC repair/refurbishment → Windows 11 requested → hardware/setup restriction → troubleshoot installation → prepare PC for handover**

For a PC being sold, the aim is to leave the machine ready for the customer to complete their own setup rather than connecting the machine to my personal Microsoft account.

For older hardware, I would also check the machine's specifications and compatibility before deciding whether an unsupported Windows 11 installation is appropriate.

---

## What This Project Demonstrates

This project documents practical Windows installation and troubleshooting techniques, including:

* Windows 11 deployment
* Windows installation media
* Command Prompt
* Registry Editor
* Windows setup and OOBE
* Registry configuration
* Hardware compatibility troubleshooting
* Local account configuration
* PC refurbishment
* Preparing PCs for customers
* Troubleshooting installation restrictions
