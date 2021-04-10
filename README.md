# Hexapod

## About The Project
This ROS package contains the rosinstall file that has all the dependencies for the hexapod project and contains the launch files
to start the hexapod robot.
At the moment, the package is meant for the [Freenove Big Hexapod kit](https://github.com/Freenove/Freenove_Big_Hexapod_Robot_Kit_for_Raspberry_Pi) and is meant for their custom Raspberry-pi shield.

## Getting Started
To use this package, ROS needs to be installed on your Raspberry-pi.
For more detail about ROS, please refer to the [ROS documentations](http://wiki.ros.org/).
This project was built with ROS Noetic release.

## Prerequisite
For communicating over I2C and GPIO, install the Wiring Pi library:
```bash
sudo apt-get install wiringpi
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
mkdir ~/my_workspace
cd ~/my_workspace

# clone this repo
git clone https://github.com/PeterL328/hexapod.git
cp hexapod/hexapod_main.rosinstall .

# Initialize the workspace from a rosinstall file
wstool init src hexapod_main.rosinstall
wstool update -t src

# Assuming all the dependencies are resolved
# Double check in each of the packages
roslaunch hexapod hexapod.launch
```
