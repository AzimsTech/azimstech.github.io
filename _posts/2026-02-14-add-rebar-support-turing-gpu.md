---
title: Adding Resizable BAR (ReBAR) support to NVIDIA Turing GPUs 
description: on Gigabyte H410M H V3
date: 2025-08-07 20:00:00 +0800
categories: [How-to, Software, Hardware]
tags: [hardware]     # TAG names should always be lowercase
media_subpath: /2026-02-14-add-rebar-support-turing-gpu/
image:
  path: Giga-H410-H-V3-banner.jpg
---

## What You Need

- [BIOS file from Gigabyte](https://www.aorus.com/en-my/motherboards/H410M-H-V3-rev-10/Support)
- [CSME System Tools v15.0 r15.rar](https://mega.nz/folder/qdVAyDSB#FLCPaDVIsPYiy2TAUjD7RQ)
- [UEFITool_0.28.0_win32.zip](https://github.com/LongSoft/UEFITool/releases/tag/0.28.0)
- [NvStrapsReBar.exe](https://github.com/terminatorul/NvStrapsReBar/releases/tag/v0.3)
- [NvStrapsRebar.ffs](https://github.com/terminatorul/NvStrapsReBar/releases/tag/v0.3)
- [modGRUBShell.efi](https://github.com/datasone/grub-mod-setup_var/releases/tag/1.4)
- [Ventoy](https://www.ventoy.net/en/download.html)
- USB drive
  
---

## Steps

### 1. Adding NvStrapsRebar FFS module

- **Open** `UEFITool.exe`
- **Drag and Drop** the stock BIOS file into the `UEFITool` window.
- `Ctrl` + `F` → GUID → `3C1DE39F-D207-408A-AACC-731CFB7F1DD7`  
  ![search GUID](image.png)
- **Double-click** on `"GUID pattern "3C1DE39F-D207-408A-AACC-731CFB7F1DD7..."`message below.  
  ![GUID message](image-1.png)
- **Scroll** to the end until you find `"Volume free spa.."`  
  ![Scroll entry](image-2.png)
- **Right-click** on the last module and select Insert after. Pick the `NvStrapsRebar.ffs` file and click Open.  
  ![Insert after](image-3.png)
- After that, you should see like this  
  ![Inserted](image-4.png)
- `Ctrl` + `S` to **save** the modified BIOS file.

### 2. Unlocking Intel Flash Descriptor Read/Write  

  You have to do this for Gigabyte motherboard because it prevents you to flash modifiled BIOS official way.

- **Install** `Ventoy` in your USB drive
- **Copy & Paste** `modGRUBShell.efi` in Ventoy USB drive
- **Reboot**
- **Press** `F12` for boot selection menu and choose Ventoy USB drive
- choose `modGRUBShell.efi`
- When EFI shell appear **type** the command below:

  ```console
  setup_var_cv MeSetup 0x3 0x1 0x1
  ```

- Now you can **flash** the modifiled bios in Step 3.

### 3. Flashing the modified BIOS  

- **Go to** `CSME System Tools v15.0 r15\Flash Programming Tool\WIN64`
- **Right click** → `Ctrl` + `Shift` + **Click** `Open in Terminal`  
  ![Open in Terminal](image-5.png)
- In `Terminal`, **type** the command below:

  ```console
  FPTW64.exe -d backup.bin
  FPTW64.exe -f <BIOSNAME.bin>
  FPTW64.exe -greset
  ```

- That's it. Continue to Final step.

## 4. Activate ReBar  

- **Run** `NvStrapsReBar.exe` as Administrator.
- **Press** `E` to enable
- Then **Press** `S` to save
- **Reboot**
- Check the result in `GPU-Z`  
  ![GPU-Z result](image-6.png)
