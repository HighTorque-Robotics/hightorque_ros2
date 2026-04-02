# HighTorque ROS2 工作空间

本仓库是 HighTorque 人形机器人 ROS2 工作空间的**元仓库**。你**不需要 clone 这个仓库**——只需要获取 `hightorque.repos` 文件即可搭建工作空间。

## 快速开始

### 1. 安装 vcstool

`vcstool` 是一个支持 svn、git、hg 和 bzr 的 VCS/SCM Python 源码控制库：

```bash
sudo apt install python3-vcstool
```

### 2. 创建工作空间

```bash
mkdir -p ~/colcon_ws
cd ~/colcon_ws
```

### 3. 下载仓库清单文件

```bash
wget https://raw.githubusercontent.com/HighTorque-Robotics/hightorque_ros2/refs/heads/main/hightorque.repos
```

### 4. 导入所有仓库

```bash
vcs import ./ < hightorque.repos
```

这条命令会根据清单文件将所有需要的仓库克隆到你的工作空间中。

### 5. 编译工作空间

```bash
source /opt/ros/foxy/setup.bash
colcon build
```

## 启动机器人

实际的启动文件位于 [hightorque_bringup](https://github.com/HighTorque-Robotics/hightorque_bringup) 仓库。

具体的启动方法请查看该仓库的 README。

## 什么是 hightorque.repos？

`hightorque.repos` 文件是一个 YAML 清单，定义了 HighTorque ROS2 工作空间中的所有仓库，包括：

- 包名称
- 仓库 URL
- 目标分支
- 工作空间中的相对路径

通过使用 `vcs import`，你可以用一条命令搭建整个工作空间，确保所有开发者使用相同的仓库结构和版本。

## 工作空间结构

运行 `vcs import` 后，你的工作空间将包含：

```
~/colcon_ws/
├── hightorque.repos
├── hightorque_bringup/
├── hightorque_controller/
├── hightorque_midware/
├── hightorque_msgs/
├── hightorque_robot/
├── humanoid_driver/
└── ... (其他包)
```

## 为什么不需要 clone 这个仓库？

这个仓库的主要作用是托管 `hightorque.repos` 清单文件。克隆整个仓库是不必要的——你只需要清单文件来引导工作空间的搭建。这种方式：

- 减少冗余的数据传输
- 保持工作空间整洁
- 遵循使用 vcstool 的标准 ROS2 工作空间搭建模式

## 其他资源

- [vcstool 文档](https://github.com/dirk-thomas/vcstool)
- [ROS2 工作空间教程](https://docs.ros.org/en/foxy/Tutorials.html)
