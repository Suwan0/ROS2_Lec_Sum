# ROS 2 Foxy 설치 - Windows 10

+ X64 VSCode오류 때문에 3일 내내 골치 아팠던 설치였다.

# Chocolatey 설치

+ 일단 처음에 최신 windows 업데이트를 적용하고, 관리자 권한의 powershell을 실행시켜서  chocolatey를 설치한다.

# Windows terminal 설치

+  powershell을 열고 choco install –y microsoft-windows-terminal 코드를 이용하여 windows terminal을 설치한다.  
+ 전에 2강에서 했던 우분투와 마찬가지로 화면분할 단축키가 있는데 우분투와는 조금 다르다.

# 파이썬 설치

+  windows terminal을 이용하여 choco install -y python —version 3.8.3 을 통해 파이썬을 설치한다.

# git 설치

+ choco install git을 통해 git을 설치한다.

# ROS2 빌드를 위한 C++설치&OpenSSL을 설치

+ 여기서 OpenSSL을 설치할 때는 환경변수에 새로운 Path를 추가해주어야한다.

# Visual Studio 2019 설치(무조건 2019!!!)

+ 꼭 2019 버전을 설치하여야 한다.   
+ 2022 버전으로 해보려고 하다가 계속 오류가 뜨길래 구글링을 해도 나오지 않아서 vscode 2019버전을 설치하고 터미널을 실행시키니 해결이 되었다.  
+ 여기서 실행이 되지 않아 못넘어가고 앓은 시간이 꽤 많다.

# CMake 설치

+ choco install –y cmake을 이용하여 설치한다.

# Install ROS

+ 위의 작업들이 잘 되어 있어야 ROS설치가 수월하게 될 수 있다.   
+ windows terminal을 관리자 권한으로 실행시키고   
+ set ChocolateyInstall=c:\opt\chocolatey  
+ choco source add -n=ros-win –s="https://aka.ms/ros/public" --priority=1  
+ choco upgrade ros-foxy-desktop –y —execution-timeout=0 의 코드를 입력하면 된다.

# workspace 생성 후 colcon build

+ 여기가 문제였다.  
+ visual studio 2022 버전을 설치해서 command를 열게되면 workspace를 만들 수 없으므로 꼭 visual studio 2019 버전을 설치하여 사용해야 한다.  
+ workspace를 만든 후에 windows terminal 환경에 ros2-foxy라는 ROS2를 바로 실행할 수 있는 터미널을 생성한다.

# Gazebo 환경을 Setup

+ Windows Terminal을 열고 다음 커멘드 라인들을 입력한 다음에   
+ setx -m HOME C:\gcamp_ros2_ws  
+ setx -m HOMEPATH C:\gcamp_ros2_ws  
+ setx -m GAZEBO_MASTER_URI http://localhost:11345  
+ setx -m GAZEBO_MODEL_DATABASE_URI http://models.gazebosim.org  
+ setx -m GAZEBO_RESOURCE_PATH C:\opt\ros\foxy\x64\share\gazebo-10  
+ setx -m GAZEBO_PLUGIN_PATH C:\opt\ros\foxy\x64\share\gazebo-10\plugins  
+ setx -m GAZEBO_MODEL_PATH C:\opt\ros\foxy\x64\share\gazebo-10\models  
+ setx -m SDF_PATH C:\opt\ros\foxy\x64\share\sdformat\1.6  
---
+ package build 작업을 한다.   
+ pushd C:\gcamp_ros2_ws  
+ colcon build --symlink-install —packages-select custom_interfaces  
+ colcon build --symlink-install —packages-select py_service_pkg  
+ colcon build --symlink-install —packages-  select gcamp_gazebo  
+ install\setup.bat

# 데모를 실행

+ ros2 launch gcamp_gazebo gcamp_world_windows.launch.py  
+ 이 코드를 통해서 로봇을 움직일 수 있고   
+ ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args –r __ns:=/skidbot  
+ 리눅스 키와는 회전 방향만 다른 것을 알 수 있다.  

+ 잘 작동된다.   
