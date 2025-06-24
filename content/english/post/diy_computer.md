---
title: "My first DIY computer: ¥500 budget with a discrete graphics card"
date: 2025-06-24T22:06:16+08:00
lastmod: 2025-06-24T22:06:16+08:00
draft: false
keywords: [DIY, computer]
description: ""
tags: [DIY, computer]
categories: [experience sharing]
author: "Jinhao Xu"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: true
postMetaInFooter: true
hiddenFromHomePage: false
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: false
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: false
  options: ""

sequenceDiagrams: 
  enable: false
  options: ""

---

<!--more-->

## Preface 
I assembled this computer over winter break (Jan~Feb) in 2025, when I could not play many games with just a light laptop home, so I thought of assembling a computer. My requirements for this computer were:
1. small enough and light enough;
2. as low a price as possible;
3. have decent performance for gaming;
4. have Nvidia solo display and support deep learning.

## Hardware Configuration 
After searching for many low-cost installation tutorials online, I settled on the following hardware configuration: 
| Hardware | Models | Price (¥) | Remarks | 
|:---:|:---:|:---:|:---:| 
| CPU | Intel E3 1225v3 | 70 | Used, purchased as a package with RAM sticks | 
| Graphics Card | Nvidia P106-90 3G | 61 | Used, single fan short card version | 
| Motherboard | Maxthon H81 ITX 17*17cm | 88 | Used | 
| Memory | Kingston 4G*2 | \ | Used, purchased as a package with CPU | 
| Hard Drive | Miscellaneous SATA 480G | 98 | Used | 
| Power Supply | Miscellaneous Small 1u 350W | 50 | Used | 
| Heatsinks | Miscellaneous | 27.9 | One Handed | 
| Chassis | Miscellaneous ITX | 62.8 | Used |

![Hardware](/images/diy_computer/hardwares.jpg)

Things to note
1. Nvidia P106 is a compute card, there is no display output interface, the CPU must have a core display; in addition, Nvidia does not provide official drivers for the P106, you need to install a third-party driver on Windows (Linux does not require a separate installation).
2. My extra spending: replaced two first-hand 8G memory sticks, costing ¥47.5; graphics card extension cable, ¥33.44; SATA 3.0 cable, ¥1.9; motherboard buzzer, ¥1.74; SATA to 6PIN power supply, ¥2.84.

Total 545.12 yuan (if do not change the memory stick, the total 497.62 yuan).

## Assembly effect 
The assembly effect is as follows: 
![Assembly effect](/images/diy_computer/assembled.jpg)

## Performance test 
Ludashi software score: 
![Ludashi Software Score](/images/diy_computer/ludashi.jpg)

Minecraft game with shaders turned on: 
![Minecraft turn on shaders](/images/diy_computer/minecraft.jpg)

It was tested that CS2 is also playable and can hold 60 fps at low quality.