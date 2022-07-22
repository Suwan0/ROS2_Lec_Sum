# ROS2 Foxy 설치 – Linux 20.04

+ 잿슨 나노에 사용되는 것이 우분투 리눅스 이기 때문에!
+ balenaEtcher를 이용한 set up!


# GRUB을 통한 Windows + Ubuntu 듀얼 부팅 시스템 만들기

+ 듀얼 시스템을 만들고 나니 컴퓨터를 킬 때 우분투와 윈도우 중에서 운영체제를 선택 할 수 있게 되었다.

# Teminator 설치

+ 다중분할 터미널을 위한 프로그램이다. ctrl+shift+o 기능을 이용해 분할을 자주 한다.

+ 아래의 코드를 이용해 우분투에서 다운받아서 사용할 수 있다.
 * sudo apt update
 * terminator 설치
 * sudo apt install terminator -y

# ROS2 Foxy 설치

+ locale  # check for UTF-8

+ sudo apt update && sudo apt install locales
+ sudo locale-gen en_US en_US.UTF-8
+ sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
+ export LANG=en_US.UTF-8

+ locale  # verify settings

+ sudo apt update && sudo apt install curl gnupg2 lsb-release -y
+ sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg

+ sudo sh -c 'echo "deb [arch=$(dpkg --print-architecture)] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
+ sudo apt update

+ Desktop Install (Recommended): ROS, RViz, demos, tutorials.
+ sudo apt install ros-foxy-desktop -y

+ Install argcomplete (optional)
+ sudo apt install -y python3-pip
+ pip3 install -U argcomplete
+ 의 커맨드를 사용한다.


+ 이 프로그램을 설치하는데 너무 많은 시간이 들었다. 이 강의노트에 나온대로 했는데 오류가 나와서 구글링을 통하여 설치를 했다.   
+ 거의 하루종일 설치하다가 끝났다.

# Gazebo 11 설치

+ sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
+ wget https://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
+ sudo apt update

+ sudo apt install gazebo11 libgazebo11-dev -y


+ sudo apt install ros-foxy-gazebo-ros-pkgs -y


+ gazebo 의 커맨드 명령어를 사용한다.
---
+ Ros2 foxy를 설치하지 않으면 설치가 되지 않았다.   
+ 즉, 설치에 있어서는 건너뛰기를 할 수 없었는데 그동안 그 이후의 것을 아무것도 할 수 없었다.   
+ Gazebo 또한 ROS2 Foxy를 설치하고 나니 Gazebo ROS 패키지들도 설치를 할 수 있었고 다행히 잘 했다.

# 개발 환경 Setup

+ Colcon Build System 설치
+ sudo apt update
+ sudo apt install python3-colcon-common-extensions
---
+ workspace 생성
+ source /opt/ros/foxy/setup.bash

+ mkdir -p ~/gcamp_ros2_ws/src
+ cd ~/gcamp_ros2_ws/src

+ mkdir -p ~/test_ros2_ws/src
+ cd ~/test_ros2_ws/src
---
+ 개발환경에서 workspace생성을 하고나서 colcon build system을 통해 빌드를 해주는 순서로 진행되는데 workspace생성 또한 말썽을 부려서 구글링을 통해서 해결했다.
