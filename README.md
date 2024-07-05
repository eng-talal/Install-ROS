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
first, you need to set locale which supports UTF-8  
to check UTF-8 use the following command in shell 
```sh
locale 
```
if you don't have UTF-8 use the following commands 
```sh
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

#### Set up sources 
##### You will need to add the ROS 2 apt repository to your system.  
ensure that the Ubuntu Universe repository is enabled.
```sh
sudo apt install software-properties-common
sudo add-apt-repository universe
```

#### Step 1: Set up the keys
```sh
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
#### Step 2: Add the repository to your sources list
```sh
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
#### Step 3: Update your package list
```sh
sudo apt update
```
#### Step 4: Install ROS 2 Foxy
```sh
sudo apt install ros-foxy-desktop python3-argcomplete
```
#### Step 5: Install development tools (Compilers and other tools to build ROS packages)
```sh
sudo apt install ros-dev-tools
```
#### Step 6: Set up the environment
Set up your environment by sourcing the following file.  
Replace ".bash" with your shell if you're not using bash  
Possible values are: setup.bash, setup.sh, setup.zsh
```sh
source /opt/ros/foxy/setup.bash
```

### 3. Verifying the Installation
#### Verifying ROS Noetic
To verify your ROS Noetic installation, you can run:
```sh
roscore
```
This should start the ROS master node.

#### Verifying ROS 2 Foxy
To verify your ROS 2 Foxy installation, you can run a C++ talker:
```sh
source /opt/ros/foxy/setup.bash
ros2 run demo_nodes_cpp talker
```
This should start a simple publisher node.

## Conclusion
You have now installed both ROS Noetic and ROS 2 Foxy on Ubuntu 20.04.6. For more information and tutorials, refer to the [ROS](https://wiki.ros.org/Installation) and [ROS2](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html) documentation.

