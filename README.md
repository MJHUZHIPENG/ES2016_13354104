# DOL开发环境配置

## 一、准备工作
**1.使用虚拟机安装Ubuntu**

* 安装虚拟机:VMWARE或VIRTUALBOX
[VMWARE教程](http://jingyan.baidu.com/article/0320e2c1ef9f6c1b87507bf6.html)
[VIRTUALBOX教程](http://jingyan.baidu.com/article/cdddd41c5eea3153ca00e160.html)
* 安装Ubantu
[Ubuntu下载](http://www.ubuntu.com/download/desktop)

**2.安装一些必要的环境(ubuntu为例)：**

**$ sudo apt-get update**
**$ sudo apt-get install ant**
**$ sudo apt-get install openjdk-7-jdk**
**$ sudo apt-get install unzip**


## 二、配置步骤
**1.下载文件**(使用Vmware虚拟机，也可以从主机拷贝到虚拟机中去  
http://jingyan.baidu.com/article/c33e3f48a5c153ea15cbb5b2.html )：

**$ sudo wget** http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz

**$ sudo wget** http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip

**2.解压文件**

* 新建dol的文件夹: **$ mkdir dol**
* 将dolethz.zip解压到 dol文件夹中: **$ unzip dol_ethz.zip -d dol**
* 解压systemc: **$ tar -zxvf systemc-2.3.1.tgz**

**3.编译systemc**

* 解压后进入systemc-2.3.1的目录下: **$ cd systemc-2.3.1**
* 新建一个临时文件夹objdir: **$ mkdir objdir**
* 进入该文件夹objdir: **$ cd objdir**
* 运行configure (能根据系统的环境设置一下参数，用于编译): **$ ../configure CXX=g++ --disable-async-updates**
* 编译: **$ sudo make install**
* 编译完后文件目录如下:
**$ cd ..        
$ ls**
* 记录当前的工作路径(会输出当前所在路径，记下来，待会有用): 
**$ pwd**

**4.编译dol**

* 进入刚刚dol的文件夹: **$ cd ../dol**
* 修改*build_zip.xml*文件:
找到下面这段话，就是说上面编译的*systemc*位置在哪里，把YYY改成上页pwd的结果（注意，对于64位 系统的机器，lib-linux要改成lib-linux64）
>property name="systemc.inc" value="YYY/include"
>property name="systemc.lib" value="YYY/lib-linux/libsystemc.a" 


* 然后是编译: **$ ant -f build_zip.xml all**
若成功会显示build successful

**5.接着可以试试运行第一个例子**

* 进入build/bin/mian路径下: **$ cd build/bin/main**
* 然后运行第一个例子: **$ ant -f runexample.xml -Dnumber=1**

