# mmwave_realsense_mapping
## Realsense d435 - repo : robotx-2022
#### Run docker 
```bash
$ cd robotx-2022
```
```bash
$ source Docker/nano-d435/docker_run.sh
```
#### In docker container 
```bash
wget -O - https://raw.githubusercontent.com/sunfu-chou/realsense-apriltag-ros-jetson/master/rs_at.bash | bash
```
```bash
source /opt/ros/melodic/setup.bash
```
```bash
source realsense-apriltag-ros-jetson/catkin_ws/devel/setup.bash
```
#### set up ROS_MASTER_URI and ROS_HOSTNAME
```bash
export ROS_MASTER_URI=http://:11311
```
```bash
export ROS_HOSTNAME=
```
#### Install launch file for pointcloud
```bash
sudo apt update
```
* for / distro / , we use melodic here. 
```bash
sudo apt install ros-<distro>-rgbd-launch 
```
```bash
roslaunch realsense2_camera rs_rgbd.launch
```
After setup, we can see pointcloud with rviz by the topic / camera/depth_registered/points /.
