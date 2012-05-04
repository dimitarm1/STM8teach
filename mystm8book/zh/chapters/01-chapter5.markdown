# STM8编程实战之基础篇 #
本章从一个呼吸灯实验入手，再逐步加入中断、计时器等。带







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

## 时钟 ##


分为Fmaster、Fcpu

Master时钟源有四种选择:

*1-24MHz高速外加晶振震荡时钟源（HSE）

*低于24Mhz一个外加时钟频率信号（HSE user-ext）

*芯片自带的一个16MHz高速RC震荡时钟源（HSI）

*芯片自带的一个128KHz低速RC震荡时钟源（LSI）


默认情况下，系统默认使用HSI/8的时钟源，也就是说系统默认的运行速率是2Mhz。

### 时钟树 ###




## GPIO ##

### GPIO的几种状态 ###



## 中断 ##


## 计时器 ##
