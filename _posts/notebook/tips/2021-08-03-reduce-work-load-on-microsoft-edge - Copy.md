---
layout: post
title: Reduce workload in Microsoft Edge and Monitor PC with Open Hardware Monitor
categories: tips
author: "Son Pham"
meta: How to reduce workload in Microsoft Edge and avoid suddenly shutdown
description: "How to reduce workload in Microsoft Edge and avoid suddenly shutdown"
comments: false
---



A few days ago, while browsing on MS Edge, my laptop suddenly shut down. I didn't notice anything out of the ordinary except that the fan was running loudly and the room temperature was over 85 degrees Fahrenheit.  
  
After rebooting my laptop and checking the hard drive and RAM, everything seemed to be fine. I opened MS Edge again and restored the tabs that were open. However, I quickly realized that the fan was running faster and the laptop shut down again suddenly.  
  
I suspected there was an issue with MS Edge, so I conducted some research and found a solution by following these steps:  

1. On MS Edge, access `edge://settings/system`
2. Disable `Use hardware accleration when available`  
  
After making these changes, my laptop was running well. However, I still thought that the CPU's temperature was causing the laptop to shut down. So, I installed Open Hardware Monitor [here]([Open Hardware Monitor - Core temp, fan speed and voltages in a free software gadget](https://openhardwaremonitor.org/)), an open source software with great features such as a gadget that allows you to add all temperature sensors. Open Hardware Monitor also lets you to `Run a remote server` and monitor over the internet.  

![Gadget 1](https://raw.githubusercontent.com/lamegaton/lamegaton.github.io/gh-pages/_posts/notebook/assets/OHM_gadget_1.png)



