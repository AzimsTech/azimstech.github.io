---
title: Clean Install Windows 11 My Way
description: Simple & Clean
author: Azims
date: 2026-09-11 11:33:00 +0800
categories: [How-to, Windows]
tags: [windows]
media_subpath: /azimstech.github.io/
image:
  path: install-win11-cover.png
---

## Objectives

- [x] No USB flash drive needed
- [x] No bloatware
- [x] No Microsoft account required
- [x] No third-party software involved

## Prepare Windows 11 Installer Partition

1. [Download Windows 11 ISO](https://www.microsoft.com/en-us/software-download/windows11#:~:text=Download%20Now-,Download%20Windows%2011%20Disk,unlock%20the%20correct%20edition.,-Windows%2011%20ISOs)
2. Mount the ISO and note the drive letter, e.g., `F:`
3. Press `Win + X`, then open **Disk Management**
4. Right-click a volume → **Shrink Volume...** → **Shrink** → Note the drive letter of the new partition, e.g., `G:`
5. Navigate to the ISO drive:

        cd F:\boot

6. Make the new partition bootable:

        bootsect /nt60 G:

7. Copy all files from the ISO to the new partition:

        xcopy F:*.* G: /E /F /H

    > `F:` = mounted ISO, `G:` = new partition
    {: .prompt-info }

## Install Windows 11 Without Bloat & Microsoft Account

1. On the **"Is this the right country or region?"** screen, press `Shift + F10` to open **Command Prompt**
2. Type the following command and press `Enter`. Your computer will reboot:

        OOBE\BYPASSNRO

3. Make sure the computer is offline. If not, press `Shift + F10` and type:

        ipconfig /release

    > You can just unplug the Ethernet cable and skip this step.
    {: .prompt-tip }
4. On the **"Is this the right country or region?"** screen, select **German** again:
    > We choose German because it forces Windows to comply with EEA laws, which prevent Windows from installing bloatware and let you uninstall the Edge browser.
    > Don't worry, you can change this later in **Settings**.
    {: .prompt-info }
5. Follow the setup prompts and be sure to click **"I don’t have internet"** and **"Continue with limited setup"**.
