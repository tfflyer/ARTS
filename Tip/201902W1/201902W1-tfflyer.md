网络仿真工具NS-3

​	NS3是一款网络仿真模拟软件，可以让人们在一台计算机中搭建出不同规模和类型的网络，从而以一种经济的方式模拟物理网络环境，为人们研究和学习网络协议提供一种方法与平台。

​	首先说一下NS3支持的网络协议：

应用层         分组产生器、应用层协议等

-------------------------------------------------------------

传输层	   		TCP、UDP

-----------------------------------------------------------------

网络层      	IPV4、IPV6、ICMP、ICMPv6、路由协议

----------------------------------------------------------------------------

链路物理层    无线有线的链路层协议等



目前，NS3被广泛应用在第五代移动通信、物联网、软件定义网络、数据中心等计算机网络的前沿研究领域。



NS3通过C++编写仿真脚本，横向上过节点仿真现实网络中的网络实体，纵向上通过在节点的协议栈安装不同的协议实现网络功能。

下面说一说在安装NS3过程中学习到的一点小技巧

编写shell脚本程序一次安装多个软件，主要用于一些软件依赖环境配置。

1、shell脚本程序必须以下面的行开始（必须方在文件的第一行）：

　　#!/bin/sh

 

符号#!用来告诉系统它后面的参数是用来执行该文件的程序。在这个例子中我们使用/bin/sh来执行程序。

2、当编辑好脚本后，还必须使其可执行。

使脚本可执行：

　　chmod +x filename

3、然后，您可以通过输入： ./filename 来执行您的脚本。



如下：

下面是我安装NS3之前，安装NS3依赖的多个软件包：

1、在vi中编辑如下文件

#!/bin/sh
sudo apt-get install gcc g++ python -y
sudo apt-get install gcc g++ python python-dev -y
sudo apt-get install mercurial -y
sudo apt-get install bzr -y
sudo apt-get install gdb valgrind -y
sudo apt-get install gsl-bin libgsl0-dev libgsl0ldbl -y
sudo apt-get install flex bison libfl-dev -y
sudo apt-get install g++-3.4 gcc-3.4 -y
sudo apt-get install tcpdump -y
sudo apt-get install aqlite aqlite3 libsqlite3-dev -y
sudo apt-get install libxml2 libxml2-dev -y
sudo apt-get install libgtk2.0-0 libgtk2.0-dev -y
sudo apt-get install vtun lxc -y
sudo apt-get install uncrustify -y
sudo apt-get install doxygen grphviz imagemagick -y
sudo apt-get install texlive texlive-extra-untils texlive-latex-extra -y
sudo apt-get install python-sphinx dia -y
sudo apt-get install python-pygraphviz python-kiwi python-pygoocanvas libgoocanvas-dev -y
sudo apt-get install libboost-signals-dev libboost-filesystem-dev -y
sudo apt-get install openmpi* -y

：wq mysetup      #（注释）保存为以mysetup为名字的文件

2、终端中编译： chmod +x mysetup 

3、运行安装，终端中输入： ./mysetup

