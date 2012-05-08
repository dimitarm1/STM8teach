# STM8芯片简介 #

本章从STM8的优势说起，向读者介绍了STM8的芯片资源、制作开发板的方式、下载程序的方法。旨在让读者对芯片有一个基本认识。如果急于学习芯片相关的知识，本章可跳过，但请一定不要忘记回头看看。

## STM8的优势 ##
STM8S是意法半导体推出的一款8位高性能单片机。它基于哈弗结构，指令与数据存储空间分开，指令与数据可以同时存取，因而具有更高的执行效率。与AVR、51单片机比较，STM8拥有更为丰富的外设，更强大的主频、更优秀的特性。更重要的是，STM8供货稳定，性价比高。其中高端的STM8S208MB也就15元，低端的STM8S103F2系列一般也就2、3元左右，而AVR高端的mega128价格就在20元左右，且性能只能勉强赶得上ST的中端产品。更重要的是，STM8的编程方法与ST的高端产品，cortexM3市场的主流：STM32极其相似（但更简单点）。这种相似，给我们后来升级到STM32奠定了基础，要知道STM32最高端的F4系列具有150Mhz的主频，这样的升级，可以大大提升我们以后做应用的范围。

## STM8编程——寄存器or库函数？ ##
和STM32一样，历来STM8存在两种编程方式：寄存器直接编程和库函数编程。寄存器的优势在于，这样的编程方法和传统的8位单片机编程方法较一致，初学者容易适应，而且普遍认为寄存器编程的人不容易出错，程序执行效率较高。库函数的优势在于程序员开发效率高，ST将一些常用的方法封装起来，这样寄存器开发者几句话（可能还得经常查手册找参数）才能搞定的事情，库函数直接一个函数就搞定了，而且所有的参数设定都可以在库函数附带的使用手册中找到，方便快捷。

事实上，因为开发效率在实际应用中往往起着决定性的作用，比如大家同样做一个新产品，只有第一个做出来的才能在很早的时候抢占市场。等市场有了，在对产品维护的过程中优化程序运行效率。同时，使用库函数的方式能更好适应以后STM32，甚至DSP、ARM的编程方式。基于上述两个原因，本手册建议使用库函数编程方式。

## 芯片资源简介 ##
一般来说，学习的时候可以用芯片功能强大一点，具体开发产品的时候可以根据官方给的[选型指南](http://www.st.com/internet/com/SALES_AND_MARKETING_RESOURCES/MARKETING_COMMUNICATION/MARKETING_BROCHURE/brstm8.pdf)，来选择对应的芯片。本手册选用的是STM8S208MB芯片，它具有：
*最大24Mhz的运行速率
*80个引脚（其中68个可用作IO引脚）
*37个外部中断引脚
*128K可编程Flash，2MB的EEPROM
*6KB的RAM
*并拥有CAN总线接口……
具体资源可以从STM8S208MB的[数据手册](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/DATASHEET/CD00197787.pdf)获取，该芯片的APPLICATION NOTES、PROGRAMMING MANUALS、REFERENCE MANUALS等信息，可以从[芯片的主页](http://www.st.com/internet/mcu/product/190232.jsp)下载。


![芯片的电路图](figures/circuit_diagram.jpg)

## 制作自己STM8开发板 ##
项目网站上有做好的STM8核心板，可以直接发到制版厂制版，每块板平均成本也就10快左右。当然如果条件允许的话，最好能够自己画一块STM8开发板。具体可以参考ST的文档[AN2752:Getting started with STM8S and STM8A](http://www.st.com/internet/com/TECHNICAL_RESOURCES/TECHNICAL_LITERATURE/APPLICATION_NOTE/CD00194637.pdf)。

## 如何下载程序 ##
STM8有两种下载方式，一种叫SWIM，还有一种叫DM。一般SWIM的方式用的比较多，但是需要ST开发的ST-link下载器。ourdev[^21]上的网友提供了[一种方案](http://www.ourdev.cn/forum.php?mod=viewthread&tid=4209177)，通过使能bootloader，能够使用串口直接对单片机烧写程序。项目网站上的核心板出于这种方案的考虑，加入了pl2303，方便用户直接烧录。后面要讲过的STVP可不能用到这个方案，应该使用的软件叫[STM32 and STM8 Flash loader demonstrator](http://www.st.com/internet/com/SOFTWARE_RESOURCES/SW_COMPONENT/SW_DEMO/stm32-stm8_flash_loader_demo.zip)。

[^21]:ourdev是个非常有意思的网站，上面有很多网友自己设计的项目，以及针对电子方面的讨论。站长阿莫也是一个很有性格的人。有空建议大家多上这个网站逛逛。

