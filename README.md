# 天穹飞控
							
## 飞控简介

近10年来，小型多旋翼飞行器发展迅猛，国外涌现出无数开源项目，其中不乏一些耳熟能详的优秀开源飞控项目。而在中国，消费级多旋翼更是发展得如火如荼，其中DJI一枝独秀，占据了国内外80%的市场。然而有一点值得我们深思的是，即使到今天，国内仍然没有一个像样的开源飞控项目，只有少部分存在于淘宝上的收费开源项目，而且质量极其堪忧，其中大部分连最基本的定点悬停功能都无法实现，且代码架构混乱，缺少文档和资料，少数带有定点功能的，其效果也远远不及普通的商业飞控，更不用说和DJI之类的进行对比。更糟糕的一点是，这些收费开源飞控项目基本上都是一锤子买卖，缺少后续更新维护及性能优化，少数一些更新仅仅是小BUG修复。

在这个背景下，本飞控项目诞生了，其目的不仅仅是为了做出一款性能逼近甚至超越DJI的飞控，而是想让更多的中国人参与进飞控项目的开发，包括大学生们，各行各业的爱好者，还有各地区的行业从业者等。国外的APM/PX4飞控也是经过数百人多年的维护和优化，才有了今天的成果，但是也不得不说国外的大部分开源飞控在性能细节上的优化还没有到位，性能难以与DJI之类经过深度优化的飞控同台竞技。

而本项目的最终目标，是打造出一套易于使用和开发，且飞行性能比肩商业产品的中国本土化开源多旋翼飞控平台，为中国的多旋翼无人机产业添砖加瓦。

>飞控交流Q群：472648354

>[飞控交流论坛](http://bbs.loveuav.com/forum-68-1.html)

## 飞控特色

- 功能丰富，除了最基础的自稳、定高、定点飞行之外，还支持自动降落、自动返航、航线规划、兴趣点环绕等高级功能，其余功能如编队飞行、智能避障还在陆续开发中

- 飞控上使用硬件恒温，传感器零漂更加稳定

- 飞控的姿态估计中使用了运动加速度补偿和自适应卡尔曼滤波器，极大提升了飞机在各种机动飞行状况下的姿态精度，并直接提升了惯导性能。导航方面使用了基于飞行状态误差模型的自适应卡尔曼滤波器，提升动态刹车精度以及悬停精度。飞行性能方面还在持续优化中

- 加速度与地磁传感器的校准均使用Levenberg-Marquardt算法拟合椭球误差方程，校准精度基本达到了廉价MEMS传感器的极限

- 位置环与姿态环均使用串级PID控制算法，悬停姿态控制精度可达0.1°，且控制方面将算法实现与操控逻辑实现分开，方便代码理解及后期扩展开发

- 使用了轻量级RTOS：FreeRTOS，实现抢占式任务调度，提高系统实时性

- 使用自定义的轻量级通信协议bsklink，配合自主开发的天穹地面站软件，可实现飞控参数设置、传感器校准、波形显示分析和航线规划等功能

- 兼容mavlink协议，可使用QGroudControl及Mission Planner地面站的大部分功能如传感器校准，数据波形分析，航线规划等

- 支持FatFs文件系统和飞行日志功能（ulog格式），可使用FlightPlot工具查看并分析飞行日志

- 飞控整体架构极其清晰，代码逐行注释，功能模块化且尽可能降低各模块之间的耦合程度，方便新手理解及代码移植

## 下载与编译

- 使用git克隆项目到本地

- 安装Keil MDK 5.25，编译飞控工程

>[详细图文说明](http://bbs.loveuav.com/thread-11422-1-1.html)


## 飞控硬件配置

![飞控配置](https://github.com/loveuav/BlueSkyFlightControl/blob/master/PIC/飞控配置.jpg)

[购买飞控板](https://item.taobao.com/item.htm?spm=a1z10.3-c-s.w4002-1694068282.10.3d006ada1kJAJG&id=580800534157)

## 天穹地面站

已在飞控Q群发布测试版，有需要的移步Q群（群文件）下载

![天穹地面站](https://github.com/loveuav/BlueSkyFlightControl/blob/master/PIC/BlueSkyPilot.jpg)

## QGroundControl地面站

QGroundControl是一个在QT跨平台环境下开发的开源无人机地面站项目，支持windows，linux，android、ios等，使用mavlink协议。

>[【天穹飞控】QGroundControl地面站使用教程](http://bbs.loveuav.com/thread-11450-1-1.html)

![QGroundControl](https://github.com/loveuav/BlueSkyFlightControl/blob/master/PIC/QGroudControl.jpg)

## 作者相关

BlueSky

QQ:352707983

## 【深入浅出多旋翼飞控开发】

针对飞控初学者编写的一系列教程，可配合开源飞控项目：[天穹飞控](https://github.com/loveuav/BlueSkyFlightControl)一起学习，效率更高。

作者：**BlueSky**

欢迎斧正和指导，QQ:352707983 

先挖个坑，再慢慢来填······

### 目录

#### 【概述篇】

##### [一.多旋翼飞控发展史](http://bbs.loveuav.com/thread-693-1-1.html)

##### [二.多旋翼飞控技术综述](https://blog.csdn.net/loveuav/article/details/81605417)

#### 【预备篇】

##### [一.元器件选型及飞控电路设计](http://bbs.loveuav.com/thread-11314-1-1.html)
##### [二.飞控代码下载与编译](http://bbs.loveuav.com/thread-11422-1-1.html)
##### 三.天穹地面站的使用
##### [四.QGroundControl地面站的使用](http://bbs.loveuav.com/thread-11450-1-1.html)

#### 【姿态篇】
##### [一.初识姿态估计](https://blog.csdn.net/loveuav/article/details/81713015)
##### 二.卡尔曼滤波
##### 三.最优估计与卡尔曼滤波推导
##### [四.非线性最小二乘与飞控传感器校准](https://blog.csdn.net/loveuav/article/details/81592870)
##### 五.运动中的传感器误差分析和优化

#### 【导航篇】

#### 【控制篇】

#### 【系统篇】

#### 【诊断篇】
