---
layout: post
title: Reduce workload in Microsoft Edge and Monitor PC with Open Hardware Monitor
categories: en tip
author: "Son Pham"
meta: 
description: "How to reduce workload in Microsoft Edge and avoid suddenly shutdown"
---



Couple days ago when browsing on MS Edge, my laptop suddenly shutdown. I did not aware of anything except the fan was running fast and the room temperature is over 85.   

So I rebooted my laptop, checked hard drive and rams, everything was fine. Then, I opened MS Edge again restored tabs that were open. I noticed the fan ran faster; laptop was shutdown suddenly.  

Something was wrong with MS Edge, so I did a little research and solve problem with these steps.

1. On MS Edge access `edge://settings/system`
2. Disable `Use hardware accleration when available`

The laptop was running well, but I thought CPU's temps also cause the laptop to shutdown. So I installed Open Hardware Monitor [here]([Open Hardware Monitor - Core temp, fan speed and voltages in a free software gadget](https://openhardwaremonitor.org/)). This is an open source software, and has great features such as gadget.

With Gadget, you can add all temperature sensor like this  

![Gadget 1](/assets/OHM_gadget_1.png)

