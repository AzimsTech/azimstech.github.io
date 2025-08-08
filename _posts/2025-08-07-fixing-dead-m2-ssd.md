---
title: How I Brought a “Dead” M.2 SSD Back to Life
date: 2025-08-07 20:00:00 +0800
categories: Tech-blog
tags: [hardware]     # TAG names should always be lowercase
media_subpath: /azimstech.github.io/
image:
  path: fixing-dead-m2-ssd.png
---

A friend came to me recently because his laptop wouldn't boot into Windows at all.  
The first thing I did was check the BIOS, and right away I noticed the problem: the SSD wasn’t even being detected.

---

### 🛠️ Quick Hardware Check

I disassembled the laptop to inspect the M.2 SSD. At first, everything looked normal. But then I noticed something odd…  
There was a small burn mark on the SSD sticker. I peeled it back and found a tiny component, likely a capacitor, that burned to a crisp.

![burned-sticker](burned-sticker.jpg){:  w="281" h="379" .normal .me-2 }
![peeled-sticker](peeled-sticker.jpg){:  w="281" h="379" .normal }

---

### 🔍 Diagnosis

My guess? That burned capacitor was causing a short and preventing the drive from being recognized.

---

### ✂️ The Fix

To test the theory, I gently pulled the damaged component out using a pair of pliers.
Then I reinserted the SSD into the laptop and powered it on.

Boom! **the SSD was detected in BIOS again.**

---

### ✅ Recap

To recap on what I did:

1. Laptop wouldn’t boot
2. SSD not detected in BIOS
3. Found a burned capacitor on the SSD
4. Removed it
5. SSD came back to life

---

### ⚠️ Final Thoughts

This kind of fix isn't guaranteed. I figured that if the SSD was dead anyway, what the hell, I might as well try. In this case, however, it saved the data and the SSD.

The moral of the story is: If your SSD is "dead," a visual inspection might reveal the problem.

---

