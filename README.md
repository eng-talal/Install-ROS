# Installing ROS and ROS 2
to install ROS and ROS2 We recommend using Linux Ubuntu, either as the primary operating system or on a virtual machine, and we recommend version 20.04.6 (Focal Fossa) Because it is the version supported by ROS1.
 
## Introduction
This guide provides step-by-step instructions on how to install both ROS (Robot Operating System) and ROS 2 on Ubuntu 20.04.6. ROS is an open-source framework widely used in robotics research and development, while ROS 2 is its next-generation counterpart with improvements in performance, flexibility, and support for real-time systems.

## Prerequisites
Before proceeding with the installation, ensure that your system is up-to-date  
using the terminal or command-line in Ubuntu (shell) :
```sh
sudo apt update
sudo apt upgrade
```

## Step-by-Step Installation
### 1. Install ROS Noetic
#### Step 1: Set up the sources list
```sh
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
#### Step 2: Set up the keys
```sh
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
#### Step 3: Update your package list
```sh
sudo apt update
```
#### Step 4: Install ROS Noetic (Desktop-Full) Everything in Desktop plus 2D/3D simulators and 2D/3D perception packages
```sh
sudo apt install ros-noetic-desktop-full
```
#### Step 5: Set up the environment
```sh
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
#### Step 6: Install dependencies for building packages
```sh
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
#### Step 7: Initialize (rosdep)
```sh
sudo rosdep init
rosdep update
```

### 2. Install ROS 2 Foxy Fitzroy
#### Pre-installation
first you need to set locale which which supports UTF-8  
to check UTF-8 use the following commandn in shell 
```sh
locale 
```








#### Step 1: Set up the sources list
```sh
sudo sh -c 'echo "deb http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
```
#### Step 2: Set up the keys
```sh
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
#### Step 3: Update your package list
```sh
sudo apt update
```
#### Step 4: Install ROS 2 Foxy
```sh
sudo apt install ros-foxy-desktop
```
#### Step 5: Set up the environment
Add the following line to your ~/.bashrc file:
```sh
echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
#### Step 6: Install dependencies for building packages
```sh
sudo apt install python3-colcon-common-extensions
```
### 3. Verifying the Installation
#### Verifying ROS Noetic
To verify your ROS Noetic installation, you can run:
```sh
roscore
```
This should start the ROS master node.

#### Verifying ROS 2 Foxy
To verify your ROS 2 Foxy installation, you can run:
```sh
ros2 run demo_nodes_cpp talker
```
This should start a simple publisher node.

## Conclusion
You have now installed both ROS Noetic and ROS 2 Foxy on Ubuntu 20.04.6. For more information and tutorials, refer to the [ROS](https://wiki.ros.org/Installation) and [ROS2](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html) documentation.

