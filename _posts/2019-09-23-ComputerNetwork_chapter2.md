---
layout:     post
title: Computer Networks Chapter2
subtitle: Computer Networks
date:       2019-09-23
author:     Musen
header-img: img/post-bg-hacker.jpg
catalog: true
tags:
    - Computer Networks
---
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { inlineMath: [ ['$','$'], ['\\(','\\)'] ], processEscapes: true } }); </script> <script type="text/javascript" async src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script>

# Chapter 2
## 1. It is desired to send a sequence of computer screen images over an optical fiber. The screen is 2560 × 1600 pixels, each pixel being 24 bits. There are 60 screen images per second. How much bandwidth is needed, and how many microns of wavelength are needed for this band at 1.30 microns?

- Assume 1 bps per Hz.
- As the formula says: 
  
$$Max.data.rate = B \cdot log_2(1+S/N) bits/sec$$

- We can deduce the formula of bandwidth:
 
$$ B=\frac{Max.data.rate}{log_2(1+S/N)}$$

- And:

$$Max.data.rate = Resolution \times pixel \times n$$ 

- So:
 
$$Max.data.rate = 2560 \times 1600 \times 24 \times 60=5898.24 Mbps$$

$$B=\frac{5898.24Mbps}{log_2(1+S/N)}$$

- I give a table to show the change of bandwidth as the $(S/N)$ changes:
  
|   S/N  | Minimum bandwidth(Mbps) |
|:------:|:-----------------------:|
|  0.01  |          193000         |
|   0.1  |          20100          |
|    1   |           2770          |
|   10   |           799           |
|   100  |           415           |
|  1000  |           277           |
|  10000 |           208           |
| 100000 |           166           |

## 2. What is the difference, if any, between the demodulator part of a modem and the coder part of a codec? (After all, both convert analog signals to digital ones.)

- Demodulator can only receive the sine wave which has been modulated and then generates the digital signals. But coder can receive all the signals.

## 3.Three packet-switching networks each contain n nodes. The first network has a star topology with a central switch, the second is a (bidirectional) ring, and the third is fully interconnected, with a wire from every node to every other node. What are the best-, average-, and worst-case transmission paths in hops?

|	|Best case|Average case|Worst case|
|:-:|:-------:|:----------:|:--------:|
|star topology|	2|2|2|
|ring|1|n/4|n/2|
|fully interconnected|1|1|1|

## 4. Compare the delay in sending an x-bit message over a k-hop path in a Circuit-switched network and in a (lightly loaded) packet-switched network. The circuit setup time is sec, the propagation delay is sec per hop, the packet size is bits, and the data rate is bps. Under what condition does the packet network have a lower delay? Also, explain the conditions under which a packet-switched network is preferable to a circuit switched network.

- **Circuit-switched network:**
  
  Setting up lasts for $s$ sec:   $t=s$ 
  
  Time of sending data:   $t=\frac{x}{b}$
  
  Total time: $t=s+\frac{x}{b}+k\cdot d$   
- **Packet-switched network:**
  
  Time of sending data: $t=\frac{x}{b}$   
  
  Last packet will be retransmitted k-1 times: $t=(k-1)\cdot \frac{p}{b}$  
  
  Total time:$t=\frac{x}{b}+(k-1)\cdot \frac{p}{b}+k\cdot d$ 

**So, if$\frac{x}{b}\lt s$  , Packet-switched network is faster than Circuit-switched network.**

## 5. A CDMA receiver gets the following chips(-1 +1 -3 +1 -1 -3 +1 +1) Assuming the chip sequences defined in Fig. 2-28(a), which stations transmitted, and which bits did each one send?

$$Chip A: (-1 -1 -1 +1 +1 -1 +1 +1).(-1 +1 -3 +1 -1 -3 +1 +1)/8=1$$

$$Chip B: (-1 -1 +1 -1 +1 +1 +1 -1).(-1 +1 -3 +1 -1 -3 +1 +1)/8=-1$$

$$Chip C: (-1 +1 -1 +1 +1 +1 -1 -1).(-1 +1 -3 +1 -1 -3 +1 +1)/8=0$$

$$Chip D: (-1 +1 -1 +1 +1 +1 -1 -1).(-1 +1 -3 +1 -1 -3 +1 +1)/8=1$$

**Conclusion:**
- Chip A ,chip B and chip C transmitted.
- A and B transmitted 1 bit
- C transmitted -1 bit.

