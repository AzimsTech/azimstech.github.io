---
title: Bring back the shortened date and time format in Windows 11
date: 2025-07-18 23:00:00 +0800
categories: [How-to, Software, Windows]
tags: [windows]     # TAG names should always be lowercase
media_subpath: /azimstech.github.io/
image:
  path: time-date-format-preview-out.png
---

![show-abbreviated-time-date-setting.png](show-abbreviated-time-date-setting.png){: .right }
Since Microsoft has [abandoning the ship](https://x.com/zacbowden/status/1943829158238298488), here's a manual way to retain the shortened date and time format.

Okay, before we start, make sure we have a backup of the old format.  

## Backup

Use the following commands to retrieve the current values of `sShortTime` and `sShortDate`:  

For `sShortTime`:
```console
reg query "HKCU\Control Panel\International" /v sShortTime
```
For `sShortDate`:
```console
reg query "HKCU\Control Panel\International" /v sShortDate
```

## Show the Shortened Time and Date Command

Enter the following command in PowerShell/CMD as an administrator:

```console
 reg add "HKCU\Control Panel\International" /v sShortTime /t REG_SZ /d "hh:mm" /f
 reg add "HKCU\Control Panel\International" /v sShortDate /t REG_SZ /d "d/MM" /f
 ```


To restore back to Defaults

```console
 reg add "HKCU\Control Panel\International" /v sShortTime /t REG_SZ /d "h:mm tt" /f
 reg add "HKCU\Control Panel\International" /v sShortDate /t REG_SZ /d "d/M/yyyy" /f
```

> This time and date format is for Malaysian Standard Time (MST). Yours might be a little different, so change accordingly.
{: .prompt-info }