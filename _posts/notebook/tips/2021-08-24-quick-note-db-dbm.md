---
layout: post
title: Quick Note - Decibel dB vs dBm
categories: tips
author: "Son Pham"
meta: what are the difference between dbm and db
description: "what are the difference between dbm and db"
comments: false
---
Most of us have heard about decibels in our daily life. It can be used to describe the loudness of your speaker, the strength of your antenna. Or can be the signal strength from transceiver. So what is decibel (dB) and dBm?  Let's the neuron roaming!  
 
## Explanation
Deci-bel is ten time of a Bel (10 x Bel)  
Bel is named after an inventor Alexander Graham Bell, in Bell Lab.  
It is an unit of a ratio on base 10 logarithm scale  
Bel is defined as $$X = \log\frac{P2}{P1} $$  
- P1: Reference Power  
- P2: Measured Power  
  
Now we have 
$$ 
Decibel = 10 Bel = 10\log\frac{P2}{P1} 
$$  
  
So what is the difference between dB and dBm?  
  
dBm stands for decibel in miliwat. That means, our Reference Power will be 1 mW  
  
$$
Y = 10 \log\frac{P2}{P1} = 10 \log\frac{P2}{1 mW}
$$  
  
We can find Y by raise them to the power of 10  
  
$$
10^{\frac{Y}{10}} = 10^{\log\frac{P2}{1 mW}} => P2 = 10^{\frac{Y}{10}} 1 mW
$$  
  
So in communication, we usually use dBm because we know the reference power which is 1 mW.  

*Notice:  
Sometime, you will see SNR = 20*log10(RMS(signal)/RMS(noise))  
So why do we have 20 here instead of 10?
- As I understand, RMS is an amplitude value, and in this case we want to see the ratio in power.
- Because power proportional to amplitude square so if we square both (RMS(signal)/RMS(noise)) we will get 20
## In Summary:
dB, decibel is any ratio in term of base-10-logarithm, dimensionless unit.  
dBm, decibel-milliwatt is any ratio with 1 mW as a reference power, dimensioned unit.
