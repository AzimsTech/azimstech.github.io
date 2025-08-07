---
title: How to Unlock Windows 11 SE's Exclusive Themes
description: Before It's Gone
date: 2025-07-3 00:00:00 +0800
categories: [How-to, Software, Windows]
tags: [windows]     # TAG names should always be lowercase
media_subpath: /azimstech.github.io/
image:
  path: 11se.png
---

![preview](win-11-se-themes.png){: width="972" height="589" .w-50 .right}
Many people may not know about Windows 11 SE. It is a special edition that was introduced in 2021 and comes preinstalled on the Surface Laptop SE.  

It is designed to run on inexpensive, low-end laptops for students from kindergarten through 12th grade. It is basically Microsoft's answer to Chromebooks.  

It is set to be discontinued in October 2026. If you would like to learn more about Windows 11 SE, [click here](https://archive.is/2Be3J).  

## How to get it?

Here's how to get the six special Windows 11 SE themes (exclusive to the Surface Laptop SE). 

1. Simply Copy & Paste this command in CMD/PowerShell:

    ```console
    reg add "HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\Education" /v EnableEduThemes /t REG_DWORD /d 1 /f
    ```
2. Reboot and wait a moment — the themes will automatically download.
downloaded once you sign in.

## Note
In case you don't want it anymore: Here's the command to undo it:

```console
reg delete "HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\Education" /f
```