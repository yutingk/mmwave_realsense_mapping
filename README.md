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
ˋˋˋ
ˋˋˋbash
export ROS_HOSTNAME=
ˋˋˋ
ˋˋˋbash
roslaunch realsense_apriltag rs_at.launch
ˋˋˋ
