# 安装ROS

## 一、配置Ubuntu仓库
配置你的Ubuntu仓库，允许"restricted"、"universe"和"multiverse"
## 二、安装sources.list
获取安装包，输入以下命令行：
** sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' **
## 三、安装密钥
安装密钥，输入以下命令行：
** udo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116 **
## 四、安装

1. 首先，确定Debian package index是最新的：
** sudo apt-get update **
2. 以推荐配置安装：
** sudo apt-get install ros-jade-desktop-full **
## 五、初始化rosdep
输入以下命令行初始化rosdep:
** sudo rosdep init
rosdep update **
## 六、环境配置
** echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
source ~/.bashrc **
## 七、获取rosinstall
** sudo apt-get install python-rosinstall **
## 八、测试安装成功
** $ apt-get source ros-jade-laser-pipeline **