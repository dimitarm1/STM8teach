# STM8编程实战之基础篇 #

本章首先介绍了STM8库函数及编写代码的环境，然后从例子着手，向读者介绍了时钟、GPIO、中断、计时器、ADC这块的使用方法和注意事项，每个部分后面会有ST官方给出的范例代码地址，可以供读者自行借鉴。







## STM8官方库函数简介 ##
为了便于使用者快速开发程序，意法半导体公司为STM8开发了库函数，并带有详尽的使用文档和使用案例。这样一来程序
我们要找的库函数文件在<http://www.st.com/internet/com/SOFTWARE_RESOURCES/SW_COMPONENT/FIRMWARE/stm8_stdperiph_lib.zip>。这个库函数适用于STM8S以及STM8A的芯片

![库函数结构](figures/stm8_lib_architecture.jpg)

![库函数中各文件依赖关系](figures/stm8_lib_relationship.jpg)

## STVD以及STVP##

要对我们的STM8芯片编程，自然一个合适的开发环境是少不了的。STM8的开发环境有IAR、Raisonance、以及STVD。其中，STVD是ST官方出品的，对用户免费，并且其提供了汇编编译器。
STVD可以从下面网址获得：<http://www.st.com/internet/com/SOFTWARE_RESOURCES/TOOL/TOOLSET/sttoolset.zip>。这是一个ST的工具集，安装好后，除了STVD外，还有一个程序叫STVP的，我们一般使用这个程序向芯片下载程序。

### 使用STVD建立自己的工程文件 ###


![STVD的界面](figures/stvd.jpg)

先留个作业，根据上节所讲的知识，自己试试看建立自己的工程文件吧。

## COSMIC编译器 ##

在这个案例开始前，我们必须要清楚STM8的时钟以及GPIO。

## 编程之前要知道的 ##

### STM8软件编写注意事项[^25] ###

[^25]:摘自2009年ST MCU巡回演讲PPT

1.主时钟是否正常起振并稳定，各个外设时钟是否开启。

2.在Option Bytes中，I/O重映射功能状态是否与实际项目相符合？如果看门狗使用硬件方法使能，则看门狗在复位后立即有效，主程序必须喂狗。

3.如果MCU主频高于16MHz，则需要配置Option Bytes的MCU等待周期为1

4.有一些状态寄存器的位的清零是通过读该寄存器来实现的，所以对这样的寄存器操作要清楚其后果。

5.建议将常用的变量分配在Zero page中，这样可以提高这些变量的访问速度。对于不常用的变量可以用@near定义在0xFF以外区域（相对来说，访问速度略慢）。用户可以根据实际情况决定。

### 变量 ###

left                right       left
--------------		--------	--------
signed char         int8_t      s8
signed short        int16_t     s16
signed long         int32_t     s32
unsigned char       uint8_t     u8
unsigned short      uint16_t    u16
unsigned long       uint32_t    u32
--------------		--------	--------


## 时钟 ##


分为Fmaster、Fcpu

Master时钟源有四种选择:

*1-24MHz高速外加晶振震荡时钟源（HSE）

*低于24Mhz一个外加时钟频率信号（HSE user-ext）

*芯片自带的一个16MHz高速RC震荡时钟源（HSI）

*芯片自带的一个128KHz低速RC震荡时钟源（LSI）


默认情况下，系统默认使用HSI/8的时钟源，也就是说系统默认的运行速率是2Mhz。


*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\CLK\` 提供的例程

## GPIO ##

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\GPIO\` 提供的例程

### GPIO的几种状态及其应用 ###



## 中断 ##

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\ITC\` 提供的例程

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\EXTI\` 提供的例程




## 计时器 ##

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\TIM*\` 提供的例程


## ADC ##

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\ADC2\` 提供的例程
