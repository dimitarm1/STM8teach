# 基于STM8单片机的开源学习平台构建 #

#### Construction of STM8 learning Platform ####

## 项目简介 ##
> STM8性能很强大，但是缺少对应的教材。ST的英文文档各种多，看得比较累。空下来就想，如果能有本教材就好了。毕设选题时，因为自己也做过一些研发类的项目，想换种形式，想到了这件事，就决定干脆自己写本册子，写点相关的内容。

> 在惠普以及爱立信的实习过程中，我接触了很多软件方面好用的工具，成熟的软件工程思想。比如说git，就是非常好的版本控制管理软件，比如说agile，消除了传统软件开发过程中的部分问题。我觉得，软件开发中的诸多问题，随着编程规模的扩大，参与人数的增多，在硬件开发中也会逐步地体现出来。所以，这些工具及思想方式引入到嵌入式编程，将是一种趋势。本手册亦不指望能够引领什么潮流，只希望能对STM8的学习者，有一个有益的指导，仅此而已。
 

## 怎样参与该项目 ##
>由于时间仓促，水平有限，希望大家有兴趣的话能加入这个项目，和我一起完善它。下面是这个项目的一些细节：

### 生成手册前的准备工作 ###

编译环境使用linux，以下命令运行于ubuntu12.04下，仅供参考。

~~~~~~~~~~
$ sudo apt-get install ruby1.9.1
$ sudo apt-get install pandoc
$ sudo apt-get install texlive-xetex
$ sudo apt-get install texlive-latex-recommended # 主要的Latex包
$ sudo apt-get install texlive-latex-extra # titlesec包，先不用知道
$ sudo apt-get install ttf-arphic-gbsn00lp ttf-arphic-ukai # 文鼎字体
$ sudo apt-get install ttf-wqy-microhei ttf-wqy-zenhei # 文泉驿字体
$ sudo gem install mkbok
~~~~~~~~~~ 

将msfonts文件夹复制到/usr/share/fonts/（注意要加sudo），安装Times New Roman以及微软雅黑字体。当然，也可通过修改config.yml文件，配置系统已有字体，这样就不需要专门安装msfonts的字体了。

要生成电子书，直接在mystm8book目录下输入命令 `mkbok` 就好了。


### 目录结构 ###

> code：STM8学习手册配套例程；

> mystm8book：开源STM8学习手册；

> paper：本人本科毕业论文，因一些特殊原因2012年7月之前处于加密状态。7月之后如果有需要，我会解除密码限制；

> pcbLib：资源板与核心版的pcb库；

> cover：手册的封面，以及曾经写过的几篇开题报告；

> resource：资源板原理图；

> stm8core：STM8S208MB核心版原理图以及PCB；

> STM8reference：在此可以找到关于该芯片的一些参考文档。

> drivers：在此可以找到该芯片相关的驱动代码（现在刚刚开始）

### 相关软件及工具 ###
> 原理图及PCB图:Altium

> 手册: 手册编写格式是MARKDOWN, 但是这个与GITHUB所支持的MARKDOWN格式有一些区别。具体的格式说明可以从<http://www.github.com/larrycai/kaiyuanbook>获得。

> 封面: 因为喜欢排版，就自己设计了一个。封面封底的图片都是取景自华师大校园的风景，本手册封面、封底都是使用COREDRAW设计的。


## 完成之事 ##

> 资源板设计
> > LM4861音频功放模块

> > IO口拓展模块

> > 矩阵键盘（4*4）

> > 独立按键（4个）

> > 液晶屏LCD12864模块

> > DS18B20温度传感模块

> > CD4060信号产生模块

> > max3232模块

> > PCF8563时钟模块（I2C）

> > ULN2803驱动模块

> > 串转并74HC164模块

> > AT24C02存储模块

> > 点阵模块（由热心网友katrina提供）

> > 蜂鸣器模块（有源、无源）（由热心网友katrina提供）

> > 八段数码管（由热心网友katrina提供）

> > AT45DB021存储模块（由热心网友katrina提供）

> STM8核心板设计

> 学习指导手册
>> 前言

>>重读C语言

>>软件开发那些事

>>STM8芯片简介

> 封面设计

> 毕业论文

## 待做之事 ##

> 驱动代码
>> 12864驱动

> 资源板设计
>> 暂无，欢迎建议

> 学习指导手册
>>实战基础篇各外设详解及例程

>>实战高级篇各外设详解及例程

>>补遗篇各外设详解

> ...


## 联系方式 ##

> Emaill地址:laser5295(AT)gmail.com

> QQ:肆79陆10贰14


