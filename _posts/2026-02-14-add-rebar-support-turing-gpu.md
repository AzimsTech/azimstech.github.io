---
title: Here's how I added Resizable BAR (ReBAR) support to NVIDIA Turing GPUs 
description: on a Gigabyte H410M H V3
date: 2026-02-14 20:00:00 +0800
categories: [How-to, Software, Hardware]
tags: [hardware]     # TAG names should always be lowercase
media_subpath: /2026-02-14-add-rebar-support-turing-gpu/
image:
  path: Giga-H410-H-V3-banner.jpg
---
NVIDIA Turing GPUs (RTX 20 / GTX 16 series) don’t officially support Resizable BAR (ReBAR).
While ReBAR is natively supported in PCIe 3.0, it requires GPU and motherboard manufacturers to add BIOS support.

## 🖥️ My Test Setup

- Motherboard: Gigabyte H410M H V3 (rev. 1.0)
- BIOS: F10b (June 10, 2023)
- GPU: ASUS PHOENIX GTX 1650 OC GDDR6
- CPU: Intel Core i3-10100

## 📋 Preparation

- [BIOS file from Gigabyte](https://www.aorus.com/en-my/motherboards/H410M-H-V3-rev-10/Support)
- [CSME System Tools v15.0 r15.rar](https://mega.nz/folder/qdVAyDSB#FLCPaDVIsPYiy2TAUjD7RQ)
- [UEFITool_0.28.0_win32.zip](https://github.com/LongSoft/UEFITool/releases/tag/0.28.0)
- [NvStrapsReBar.exe](https://github.com/terminatorul/NvStrapsReBar/releases/tag/v0.3)
- [NvStrapsRebar.ffs](https://github.com/terminatorul/NvStrapsReBar/releases/tag/v0.3)
- [modGRUBShell.efi](https://github.com/datasone/grub-mod-setup_var/releases/tag/1.4)
- [Ventoy](https://www.ventoy.net/en/download.html)
- USB drive
  
---

## 📃 Steps

### 1. Adding NvStrapsRebar FFS module

- **Open** `UEFITool.exe`
- **Drag and Drop** the stock BIOS file into the `UEFITool` window.
- `Ctrl` + `F` → GUID → `3C1DE39F-D207-408A-AACC-731CFB7F1DD7`  
  ![search GUID](image.png){: .rounded-4}
- **Double-click** on `"GUID pattern "3C1DE39F-D207-408A-AACC-731CFB7F1DD7..."`message below.  
  ![GUID message](image-1.png){: w="500" .rounded-4}
- **Scroll** to the end until you find `"Volume free spa.."`  
  ![Scroll entry](image-2.png){: w="500" .rounded-4}
- **Right-click** on the last module and select Insert after. Pick the `NvStrapsRebar.ffs` file and click Open.  
  ![Insert after](image-3.png){: w="500" .rounded-4}
- After that, you should see like this  
  ![Inserted](image-4.png){: w="500" .rounded-4}
- `Ctrl` + `S` to **save** the modified BIOS file.
- Now, proceed to [the next step.](#2-unlocking-intel-flash-descriptor-readwrite)

### 2. Unlocking Intel Flash Descriptor Read/Write  

  You have to do this for Gigabyte motherboard because it prevents you to flash modified BIOS official way.

- **Install** `Ventoy` in your USB drive
- **Copy & Paste** `modGRUBShell.efi` in Ventoy USB drive
- **Reboot**
- **Press** `F12` for boot selection menu and choose Ventoy USB drive
- choose `modGRUBShell.efi`
- When EFI shell appear **type** the command below:

  ```console
  setup_var_cv MeSetup 0x3 0x1 0x1
  ```

- Now you can **flash** the modified bios in [Step 3.](#3-flashing-the-modified-bios)

### 3. Flashing the modified BIOS  

> Flashing a modified BIOS can permanently brick your device. Proceed at your own risk.
{: .prompt-danger }

- **Go to** `CSME System Tools v15.0 r15\Flash Programming Tool\WIN64`
- **Right click** → `Ctrl` + `Shift` + **Click** `Open in Terminal`  
  ![Open in Terminal](image-5.png){: .rounded-4}
- In `Terminal`, **type** the command below:

  ```console
  FPTW64.exe -d backup.bin
  FPTW64.exe -f <BIOSNAME.bin>
  FPTW64.exe -greset
  ```

- That's it. Continue to [Final step.](#4-activate-rebar)

### 4. Activate ReBar  

- **Run** `NvStrapsReBar.exe` as Administrator.
- **Press** `E` to enable
- Then **Press** `S` to save
- **Reboot**

## ❓Did it work?

Absolutely! Here's the result in `GPU-Z`  
  ![GPU-Z result](image-6.png){: .rounded-4}

> This was tested on Gigabyte H410M H V3 (rev. 1.0)  
> BIOS version: F10b (June 10, 2023)
{: .prompt-info }