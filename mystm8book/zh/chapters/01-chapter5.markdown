# STM8编程实战之基础篇 #

本章首先介绍了STM8库函数及编写代码的环境，然后从例子着手，向读者介绍了时钟、GPIO、中断、计时器、ADC这块的使用方法和注意事项，每个部分后面会有ST官方给出的范例代码地址，可以供读者自行借鉴。

## STM8官方库函数简介 ##
为了便于使用者快速开发程序，意法半导体公司为STM8开发了[官方库函数](http://www.st.com/internet/com/SOFTWARE_RESOURCES/SW_COMPONENT/FIRMWARE/stm8_stdperiph_lib.zip)[^26]，并带有详尽的使用文档和使用案例。

[^26]:这个库函数同时适用于STM8S以及STM8A的芯片.

![库函数结构](figures/stm8_lib_architecture.jpg)

![库函数中各文件依赖关系](figures/stm8_lib_relationship.jpg)

## STVD以及STVP##

要对我们的STM8芯片编程，自然一个合适的开发环境是少不了的。STM8常用的开发环境有IAR、Raisonance、以及STVD。其中，STVD是ST官方出品的，对用户免费，并且其提供了汇编编译器。

STVD被包含在一个叫[ST Toolset](http://www.st.com/internet/com/SOFTWARE_RESOURCES/TOOL/TOOLSET/sttoolset.zip)的工具集中。除了STVD外，还有一个程序叫STVP的，我们一般使用这个程序向芯片下载程序。

### 使用STVD建立自己的工程文件 ###


![STVD的界面](figures/stvd.jpg)

先留个作业，根据上节所讲的知识，自己试试看建立自己的工程文件吧。

## 安装COSMIC编译器 ##

ST Toolset只提供免费的汇编编译器，并没有提供C语言编译器。而我们编写程序都是依靠C语言，所以需要安装另外的C语言编译器。

一般情况下，我们可以安装[COSMIC](http://www.cosmicsoftware.com/download_stm8_32k.php)或者[Raisonance](http://www.raisonance.com/~rkit-stm8-lite-32kb-software-toolset__microcontrollers__product~product__T017:4dap2028hdu9.html)的编译器。这两款编译器都是免费的，但是生成代码得小于32k，不过对于我们初期学习还算够用。我用的是COSMIC，下载时得填写个人信息（可能需要注册），此外安装完成后还得给官方发送一个指定格式的邮件（具体格式安装完程序后会提示你），顺利的话一两天内就能收到license了。

安装完编译器后，安装目录中有些编译器相关的C语言指南。把它放在你的参考文档目录下吧[^27]，经常看看。

[^27]:事实上，在本手册编写的同时，会将相应的文档放在 `STM8teach/STM8reference` 文件夹下。

## 编程之前要知道的 ##

### STM8软件编写注意事项[^28] ###

[^28]:摘自2009年ST MCU巡回演讲PPT

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


![时钟树](figures/clocktree.jpg)


分为Fmaster、Fcpu

Master时钟源有四种选择:

*1-24MHz高速外加晶振震荡时钟源（HSE）

*低于24Mhz一个外加时钟频率信号（HSE user-ext）

*芯片自带的一个16MHz高速RC震荡时钟源（HSI）

*芯片自带的一个128KHz低速RC震荡时钟源（LSI）


默认情况下，系统默认使用HSI/8的时钟源，也就是说系统默认的运行速率是2Mhz。

HSI的启动时间远小于HSE外接晶振的启动时间。

### CSS时钟安全系统 ###
当我们使用外部晶振提供时钟源的时候，一旦时钟源出现故障，系统工作就会出现问题。STM8提供CSS（Clock Security System）功能。它能够在HSE外部时钟源出现问题时，迅速监测并将时钟源切换至芯片内时钟HSI/8。HSI的高启动速度，能够确保无缝切换的实现。

### Option Bytes ###
Option Bytes有点类似于AVR的熔丝位，可以通过SWIM的方式进行读写。还记得前面讲过的SWIM使能BOOTLOADER吗?其实它就是通过SWIM改写Option Bytes的一个过程。

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第九章《Clock Control(clk)》。

*阅读芯片手册第八章《Option bytes》，了解Option Bytes相关内容。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\CLK\` 提供的例程

## GPIO ##

### GPIO的几种状态及其应用 ###


### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\GPIO\` 提供的例程





## 中断 ##

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\ITC\` 提供的例程

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\EXTI\` 提供的例程




## 计时器 ##

STM8S208MB有TIM1、TIM2、TIM3、TIM4。

TIM1是16位高级定时器，TIM2、TIM3是16位通用目的定时器，TIM4是8位基本定时器。

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。


*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\TIM*\` 提供的例程


## ADC ##

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\ADC2\` 提供的例程
