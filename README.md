# Hexapod

## About The Project
This ROS package contains the rosinstall file that has all the dependencies for the hexapod project and contains the launch files
to start the hexapod robot.
At the moment, the package is meant for the [Freenove Big Hexapod kit](https://github.com/Freenove/Freenove_Big_Hexapod_Robot_Kit_for_Raspberry_Pi) and is meant for their custom Raspberry-pi shield.

## Getting Started
To use this package, ROS needs to be installed on your **Raspberry-pi**.
For more detail about ROS, please refer to the [ROS documentations](http://wiki.ros.org/).
This project was built with ROS Noetic release.

## Prerequisite
```bash
# I2C and GPIO
sudo apt-get install wiringpi

# Eigen3 library (Used in hexapod_control)
# Should install to /usr/include/eigen3
sudo apt install libeigen3-dev
```

The following ROS packages are likely not installed by default and needs to be installed:
```
compressed_image_transport
camera_info_manager
dynamic_reconfigure
diagnostic_updater
async_web_server_cpp
```
There are many ways to install ROS packages. You can search for pre-compiled binaries for you system or you can build them from source.
[See this post](https://industrial-training-master.readthedocs.io/en/melodic/_source/session1/Installing-Existing-Packages.html) for more details.

## Installation and Usage
```bash
# Create a catkin workspace 
mkdir -p ~/my_workspace/src # (Can rename my_workspace)
cd ~/my_workspace/
catkin_make

# clone this repo
cd ~/my_workspace/src
git clone https://github.com/PeterL328/hexapod.git
cp hexapod/hexapod_main.rosinstall .rosinstall

# Initialize the workspace from a rosinstall file
cd ~/my_workspace/
wstool init src src/.rosinstall
wstool update -t src

# Build the catkin workspace
cd ~/my_workspace/

# If you are developing on your local machine and not the Raspberry Pi, then you will not
# be able to build the hexapod_driver package because you can't install wiringpi.
# You can build packages selectively using
catkin_make --only-pkg-with-deps <target_package>
# else you are building on the Raspberry Pi:
catkin_make

# Assuming all the dependencies are resolved
# Double check in each of the packages
# Assuming you built all the packages and are on the Raspberry Pi.
roslaunch hexapod hexapod.launch
```
