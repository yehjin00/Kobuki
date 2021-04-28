# Kobuki(Turtlebot2)-On-Melodic
Make your Kobuki run on ROS Melodic (Ubuntu 18.04).

![](https://www.turtlebot.com/assets/images/turtlebot_2_lg.png)

## Prerequisites

- ROS Melodic on Ubuntu 18
- Kobuki(Turtlebot2)

## How to build Kobuki ROS package
```
Clone this project to your catkin's workspace scr folder
 $ cd catkin_ws
 $ cd src
 $ git clone https://github.com/yehjin00/Kobuki.git
 $ catkin_make
```

## How to build YDLIDAR ROS package
```
1. Clone this project to your catkin's workspace scr folder
    $ git clone https://github.com/YDLIDAR/ydlidar_ros
2. Running catkin_make to build ydlidar_node and ydlidar_client
    $ catkin_make
3. Create the name "/dev/ydlidar" for YDLIDAR
    $ roscd ydlidar_ros/startup
    $ sudo chmod 777 ./*
    $ sudo sh initenv.sh
```

## How to run Kobuki
```
$ roscore
$ roslaunch kobuki_node minimal.launch
$ roslaunch ydlidar_ros lidar.launch
$ roslaunch kobuki_keyop keyop.launch
```

## How to run slam & navigation
#### slam
```
$ roslaunch turtlebot3_slam turtlebot3_slam.launch
```
if you want to use rosbag
```
$ mkdir ~/bagfiles
$ cd ~/bagfiles
$ rosbag record -a

when the recording is over, in a new terminal
$ rosbag info <your bagfile>  (This is for data verification, so it doesn't matter if you don't run it.)
$ rosbag play <your bagfile>
$ roslaunch turtlebot3_slam turtlebot3_slam.launch
```


if you want to save the map (with rviz on)
```
$ rosrun map_server map_server -f ~/map_server
```
#### navigation
```
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch
```
