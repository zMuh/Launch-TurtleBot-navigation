# Launch TurtleBot Navigation

## Installing Dependencies

To install the necessary packages, run the following commands:

```bash
sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy \
  ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc \
  ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan \
  ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python \
  ros-kinetic-rosserial-server ros-kinetic-rosserial-client \
  ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server \
  ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro \
  ros-kinetic-compressed-image-transport ros-kinetic-rqt* \
  ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers
```

Additionally, install the following packages:

```bash
sudo apt-get install ros-kinetic-dynamixel-sdk
sudo apt-get install ros-kinetic-turtlebot3-msgs
sudo apt-get install ros-kinetic-turtlebot3
```

### Clone Repositories

Open a terminal and navigate to your Catkin workspace's `src` directory, then clone the required repositories:

```bash
cd ~/catkin_ws/src
git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git
git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations
cd .. && catkin_make
```

## Opening Gazebo

Set the TurtleBot model and launch the Gazebo simulation:

```bash
export TURTLEBOT3_MODEL=burger
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

![Gazebo](https://drive.google.com/uc?export=view&id=1ghDZbwN2kZLA1jPcQK9h7cbVOxgGRl1N)

## Opening SLAM

Launch the SLAM algorithm using Gmapping:

```bash
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```

![SLAM](https://drive.google.com/uc?export=view&id=1P6zUD9RhPyQjzqz2vE9TIcYjhATpI2g3)

Now, move around to create a map and save it using the following command:

```bash
rosrun map_server map_saver -f ~/map
```

To control the robot, run:

```bash
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

![Teleoperation](https://drive.google.com/uc?export=view&id=1ioQuyStFWdGhVa6ayfnaM9l7qjOLCyQ3)

## Start Navigation

To start the navigation process and load the saved map, use:

```bash
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:='/home/muh/map.yaml'
```

![Navigation](https://drive.google.com/uc?export=view&id=1T1yw3D7MsgFYplwMvD_ea-2hz54MxtXR)

After launching, select the 2D Pose button from the top bar to set the robot's location. You can then move the robot around using the 2D Nav Goal feature.

![Moving](https://drive.google.com/uc?export=view&id=1az6VePMxwIiayoP6KBD6_t28-PVapXG9)
