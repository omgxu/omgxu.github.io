---
title: "我的第一台DIY电脑：500元预算还带独显"
date: 2025-06-24T22:01:04+08:00
lastmod: 2025-06-24T22:01:04+08:00
draft: false
keywords: [DIY, 电脑]
description: ""
tags: [DIY, 电脑]
categories: [经验分享]
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

## 前言
这台电脑是我在2025年寒假（1~2月）组装的，当时我只带一台轻薄本回家，很多游戏玩不了，于是我想到了组装一台电脑。我对这台电脑的要求是：
1. 足够小、足够轻；
2. 价格尽可能低；
3. 性能尚可，可以满足游戏需求；
4. 有Nvidia独显，支持深度学习。

## 硬件配置
在网上寻找了许多低价装机教程后，我确定了以下硬件配置：
| 硬件 | 型号 | 价格（元） | 备注 |
|:---:|:---:|:---:|:---:|
| CPU | Intel E3 1225v3 | 70 | 二手，与内存条打包购买 |
| 显卡 | Nvidia P106-90 3G | 61 | 二手，单风扇短卡版本 |
| 主板 | 铭瑄H81 ITX 17*17cm | 88 | 二手 |
| 内存 | 金士顿4G*2 | \ | 二手，与CPU打包购买 |
| 硬盘 | 杂牌SATA 480G | 98 | 二手 |
| 电源 | 杂牌小1u 350W | 50 | 二手 |
| 散热器 | 杂牌 | 27.9 | 一手 |
| 机箱 | 杂牌ITX | 62.8 | 一手 |

![硬件](/images/diy_computer/hardwares.jpg)

需要注意的是
1. Nvidia P106是计算卡，没有显示输出接口，CPU必须要有核显；此外，Nvidia官方不提供P106的驱动，Windows上需要装第三方驱动（Linux无需另装）。
2. 我的额外花销：换了两条一手8G的内存条，花费47.5元；显卡延长线，33.44元；SATA 3.0线，1.9元；主板蜂鸣器，1.74元；SATA转6PIN供电，2.84元。

总计545.12元（若不换内存条，总计497.62元）。

## 组装效果
组装效果图如下：
![组装效果](/images/diy_computer/assembled.jpg)

## 性能测试
鲁大师软件跑分：
![鲁大师软件跑分](/images/diy_computer/ludashi.jpg)

《我的世界》游戏开启光影：
![我的世界开启光影](/images/diy_computer/minecraft.jpg)

实测《CS2》也是可以玩的，低画质可以保持60帧。