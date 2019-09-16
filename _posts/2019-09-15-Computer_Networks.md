---
layout:     post
title: 计算机网络第一章作业
subtitle: Computer Networks
date:       2019-09-15
author:     Musen
header-img: img/home-bg-art.jpg
catalog: true
tags:
    - Computer Networks
---

## 1. 使用层次协议的两个理由是什么？使用层次协议的一个可能缺陷是什么？
理由：

（1）可以把难以管理的任务分解成几个较小的，易于处理的设计问韙，降低网络设计复
杂性

（2）某个层次的协议可以改变而不影响它的上层和下层

缺陷：降低络性能

## 2. Specialty，Paint公司的总裁打与一个本地的无形啤酒酿造商合作生产一种无形嘧酒毖作为防止乱拐垃圾的一种措施。总紱告诉她的法律部门调研此事，后者又请工程部帮忙·结果总工程师打电话给啤酒酿造公司讨论该顶目的技木问题。然后两位工程师又各自问他们的法律部口作了汇报。然后，法律部门通过电话安排了有关的法方面的事宜。最后，两位公司总裁讨论了这次作在经济方面的问题。试问这个通信机制讳反了OSI模型意义上的哪个多层议原理？

违反了物理层。

## 3. 试问TCP和UDP的主要不同是什么？

TCP提供的是面向连接的、可靠的数据流传输，而UDP提供的是非面向连接的、不可靠的数据流传输。
简单的说，TCP注重数据安全，而UDP数据传输快点，但安全性一般。

## 4. lnternet由大量的网络构成。这些网络的布局决宇了lnternet的拓扑结构。网上供了大單有关lnternet拓扑结构的可用信息。请用搜索引找出更多有关lnternet的拓扑结构信息，并根据你的发现写一个概述报告。

因特网逐渐演变成基于ISP和NAP的多层次结构网络。但今日的因特网由于规模太大，己经很难对整个网络的结构给出细致的描述。但网络是把许多计算机连接在一起，而因特网(lnternet)则把许多网络连接在一起。所以，我们可以从网络的拓扑结构，了解lnternet的拓扑结构。

计算机网络的拓扑结构是引用拓扑学中研宄与大小，形状无关的点，线关系的方法。把网络中的计算机和通信设备抽象为一个点，把传输介质抽象为一条线，由点和线组成的几何图形就是计算机网络的拓扑结构。网络的拓扑结构反映出网中个实体的结构关系，是建设计算机网络的第一步，是实现各种网络协议的基础，它对网络的性能，系统的可靠性与通信费川都有重大影响。

网络拓扑结构定义了网络中各种设备的连接方式，根据网络拓扑结构划分，可以将计算
机网络分为总线拓扑结构、星型拓扑结构、环形拓扑结构、树型拓扑结构和网格型网络五
种类型。

## 5. 写一个程序现7层议模型中从顶层到层的报文流。针对每一层，程序应包恬一个单独的协议函数。协议头为64个字符序列。每个协议函数有两个参数：从高层议传下来的报文（一个char缓冲区}），和报文的大小。这个函数在报文前面貼上报文头，并在标准输出上打印出新的报文，然后调用较低层协议的协议函数。程片输入是一个应用程序的报文（一个至多80字符的序列）。

```C++
#include "stdio.h"    
#include "stdlib.h"    
#include "string.h"    
#include "assert.h"    
void application_layer_send(char *buffer, int len);    
void presentation_layer_send(char *buffer, int len);    
void session_layer_send(char *buffer, int len);    
void transport_layer_send(char *buffer, int len);    
void network_layer_send(char *buffer, int len);    
void datalink_layer_send(char *buffer, int len);    
void physical_layer_send(char *buffer, int len);    
char* attach_header(char *buffer, char *header, int *len2) {    
int len = strlen(buffer);    
int hlen = strlen(header);    
*len2 = len + hlen;    
char *buffer2 = (char*)malloc(*len2 + 1);    
memcpy(buffer2, header, hlen);    
memcpy(buffer2 + hlen, buffer, len);    
buffer2[*len2] = '\0';    
return buffer2;    
}    
void application_layer_send(char *buffer, int len) {    
static char header[] = "application_layer_header;";    
assert(strlen(buffer) == len);    
int len2 = 0;    
char *buffer2 = attach_header(buffer, header, &len2);    
printf("%s\n", buffer2);    
presentation_layer_send(buffer2, len2);    
free(buffer2);    
}    
void presentation_layer_send(char *buffer, int len) {    
char header[] = "presentation_layer_header;";    
assert(strlen(buffer) == len);    
int len2 = 0;    
char *buffer2 = attach_header(buffer, header, &len2);    
printf("%s\n", buffer2);    
session_layer_send(buffer2, len2);    
free(buffer2);    
}    
void session_layer_send(char *buffer, int len) {    
char header[] = "session_layer_header;";    
assert(strlen(buffer) == len);    
int len2 = 0;    
char *buffer2 = attach_header(buffer, header, &len2);    
printf("%s\n", buffer2);    
transport_layer_send(buffer2, len2);    
free(buffer2);    
}    
void transport_layer_send(char *buffer, int len) {    
char header[] = "transport_layer_header;";    
assert(strlen(buffer) == len);    
int len2 = 0;    
char *buffer2 = attach_header(buffer, header, &len2);    
printf("%s\n", buffer2);    
network_layer_send(buffer2, len2);    
free(buffer2);    
}    
void network_layer_send(char *buffer, int len) {    
char header[] = "network_layer_header;";    
assert(strlen(buffer) == len);    
int len2 = 0;    
char *buffer2 = attach_header(buffer, header, &len2);    
printf("%s\n", buffer2);    
datalink_layer_send(buffer2, len2);    
free(buffer2);    
}    
void datalink_layer_send(char *buffer, int len) {    
char header[] = "datalink_layer_header;";    
assert(strlen(buffer) == len);    
int len2 = 0;    
char *buffer2 = attach_header(buffer, header, &len2);    
printf("%s\n", buffer2);    
physical_layer_send(buffer2, len2);    
free(buffer2);    
}    
void physical_layer_send(char *buffer, int len) {    
char header[] = "physical_layer_header;";    
assert(strlen(buffer) == len);    
int len2 = 0;    
char *buffer2 = attach_header(buffer, header, &len2);    
printf("%s\n", buffer2);    
free(buffer2);    
}    
void application_routine() {    
char message[] = "Hello World!";    
application_layer_send(message, strlen(message));    
}    
int main(int argc, char *argv[]) {    
application_routine();    
return 0;    
}
```





