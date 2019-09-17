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

缺陷：降低络性能（分层协议和网络协议的性能会降低）

## 2. Specialty，Paint公司的总裁打与一个本地的无形啤酒酿造商合作生产一种无形嘧酒毖作为防止乱拐垃圾的一种措施。总紱告诉她的法律部门调研此事，后者又请工程部帮忙·结果总工程师打电话给啤酒酿造公司讨论该顶目的技木问题。然后两位工程师又各自问他们的法律部口作了汇报。然后，法律部门通过电话安排了有关的法方面的事宜。最后，两位公司总裁讨论了这次作在经济方面的问题。试问这个通信机制讳反了OSI模型意义上的哪个多层议原理？

这个协议违反了物理层的协议。

## 3. 试问TCP和UDP的主要不同是什么？

TCP提供的是面向连接的、可靠的数据流传输，而UDP提供的是非面向连接的、不可靠的数据流传输。
简单的说，TCP注重数据安全，而UDP数据传输快点，但安全性一般。

## 4. lnternet由大量的网络构成。这些网络的布局决宇了lnternet的拓扑结构。网上供了大單有关lnternet拓扑结构的可用信息。请用搜索引找出更多有关lnternet的拓扑结构信息，并根据你的发现写一个概述报告。

拓扑是研究几何图形或空间在连续改变形状后还能保持不变的一些性质的一个学科。它只考虑物体间的位置关系而不考虑它们的形状和大小。

拓扑这个名词是从几何学中借用来的。网络拓扑是网络形状，或者是网络在物理上的连通性。网络拓扑结构是指用传输媒体互连各种设备的物理布局，即用什么方式把网络中的计算机等设备连接起来。拓扑图给出网络服务器、工作站的网络配置和相互间的连接。网络的拓扑结构有很多种，主要有星型结构、环型结构、总线结构、分布式结构、树型结构、网状结构、蜂窝状结构等。

因特网逐渐演变成基于ISP和NAP的多层次结构网络。但今日的因特网由于规模太大，己经很难对整个网络的结构给出细致的描述。但网络是把许多计算机连接在一起，而因特网(lnternet)则把许多网络连接在一起。所以，我们可以从网络的拓扑结构，了解lnternet的拓扑结构。

计算机网络的拓扑结构是引用拓扑学中研宄与大小，形状无关的点，线关系的方法。把网络中的计算机和通信设备抽象为一个点，把传输介质抽象为一条线，由点和线组成的几何图形就是计算机网络的拓扑结构。网络的拓扑结构反映出网中个实体的结构关系，是建设计算机网络的第一步，是实现各种网络协议的基础，它对网络的性能，系统的可靠性与通信费川都有重大影响。

网络拓扑结构定义了网络中各种设备的连接方式，根据网络拓扑结构划分，可以将计算机网络分为总线拓扑结构、星型拓扑结构、环形拓扑结构、树型拓扑结构和网格型网络五种类型。
常用的计算机网络拓扑结构有五种：

1、总线型拓扑结构，总线型网络结构是指所以设备共用一条物理传输线路，都通过相应的硬件接口连接，在一根传输线路是，这根线路被称为总线。传递方式是指总是从发送信息的结点开始，向两端扩散该传输方式又称 “广播式网络”。

2、星行拓扑结构，有一个唯一的中心结点，每个外围结点都通过一条点对点的链路直接与中心结点连接，各外围结点间不能直接通信，所以数据需要经过中心结点。

3、环形拓扑结构，由网络中若干结点，通过环接口连在一条首尾，相连形成的闭合环的通信链路上，这种结构使用公共传输，电缆组成环形连接。

4、树状拓扑结构，树状拓扑结构可以看作是星形结构的扩展，是一种分层结构，具有根结点和各分支结点，比星状结构更为负责，数据在传输的过程中需要经过多条链路，时延较大，所以根结点和分支结点，都具有转发功能。

5、网状拓扑结构，网状拓扑结构是一种不规则的结构。该结构由分布在不同地点、各自独立的结点链路连接而成，每一个结点至少有一条链路，与其他结点相连，两个结点之间的通信链路不止一条，需进行路由选择。


## 5. 写一个程序现7层议模型中从顶层到层的报文流。针对每一层，程序应包恬一个单独的协议函数。协议头为64个字符序列。每个协议函数有两个参数：从高层议传下来的报文（一个char缓冲区}），和报文的大小。这个函数在报文前面貼上报文头，并在标准输出上打印出新的报文，然后调用较低层协议的协议函数。程片输入是一个应用程序的报文（一个至多80字符的序列）。

```cpp   
#include <cstring> 

#include <iostream>
 	
using namespace std; 
/*函数声明*/
void first_layer(string message);
void second_layer(string message);
void third_layer(string message);
void fourth_layer(string message);
void fifth_layer(string message);
void sixth_layer(string message);
void seventh_layer(string message);      
/*应用层实现*/
void first_layer(string message) {    
	static string header= "application_layer_header;";       	    
	string new_message = message + ' '+ header;  
	cout<<new_message<<endl;   
	second_layer(new_message);       
} 
/*表示层实现*/   
void second_layer(string message) {    
	string header = "presentation_layer_header;";       	    
	string new_message = message + ' '+ header;
	cout<<new_message<<endl;      
	third_layer(new_message);       
}  
/*会话层实现*/  
void third_layer(string message) {    
	string header = "session_layer_header;";       	    
	string new_message = message + ' '+ header;
	cout<<new_message<<endl;      
	fourth_layer(new_message);       
} 
/*传输层实现*/   
void fourth_layer(string message) {    
	string header = "transport_layer_header;";       	    
	string new_message = message + ' '+ header; 
	cout<<new_message<<endl;     
	fifth_layer(new_message);       
} 
/*网络层实现*/   
void fifth_layer(string message) {    
	string header = "network_layer_header;";       	    
	string new_message = message + ' '+ header; 
	cout<<new_message<<endl;       
	sixth_layer(new_message);       
}   
/*链路层实现*/ 
void sixth_layer(string message) {    
	string header = "datalink_layer_header;";       	    
	string new_message = message + ' '+ header;  
	cout<<new_message<<endl;    
	seventh_layer(new_message);       
} 
/*物理层实现*/   
void seventh_layer(string message) {    
	string header = "physical_layer_header;";       	    
	string new_message = message + ' '+ header;
	cout<<new_message<<endl;         
}     
int main() { 
	string message = "This is a new message!"; 
	first_layer(message);  
	return 0;    
}
```





