# STM8资源补遗 #

本章从例子着手，向读者介绍了IWDG、WWDG、AWU、BEEP、FLASH、RST这块的使用方法和注意事项，每个部分后面会有ST官方给出的范例代码地址，可以供读者自行借鉴。

## IWDG独立看门狗 ##
使用独立晶振，可靠性高。

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\IWDG\` 提供的例程

## WWDG窗口看门狗 ##

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\WWDG\` 提供的例程

## AWU自动唤醒单元 ##

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\AWU\` 提供的例程

## BEEP ##

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\BEEP\` 提供的例程

## FLASH ##

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\FLASH\` 提供的例程

## RST复位 ##

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第八章。

*阅读库函数文件夹下 `STM8S_StdPeriph_Lib_V2.1.0\Project\STM8S_StdPeriph_Examples\RST\` 提供的例程

## 电源管理 ##

我们程序运行的时候，芯片一般处于Run模式，此时，消耗电流过大。

为了降低能源消耗，我们一般采取以下几种方法：

*降低芯片运行速率。

*关闭不需要使用的外设的时钟。

*如果不使用，关闭ADC模块。

除了Run模式之外，STM8还可以运行在以下Wait、Active-halt、Halt这几个模式。

### 接下来要做的 ###

*阅读[《RM0016: STM8S and STM8A microcontroller families》](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/REFERENCE_MANUAL/CD00190271.pdf)第十章《Power management》。

