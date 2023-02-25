# mmwave_realsense_mapping
## Realsense d435 - repo : duckiepont-nctu
#### Run docker 
```bash
cd duckiepont-nctu
```
```bash
source docker/nx-d435/docker_run.sh
```
#### In docker container 
```bash
source environment.sh
```
```bash
roslaunch realsense2_camera rs_rgbd.launch
```

## mmWave & LiDAR- repo : duckiepont-nctu
#### Should setup connection with LiDAR first.
#### Run docker 
```bash
cd duckiepont-nctu
```
```bash
source nano_run.sh
```
#### In docker container 
```bash
source environment.sh
```
#### set up ROS_MASTER_URI and ROS_HOSTNAME
```bash
export ROS_MASTER_URI=http://your_ip:11311
```
```bash
export ROS_IP=your_ip
```
#### set up mmwave (usually don't need to do these steps)
To change the name of the port  for mmwave, we use the file in **~/duckiepond-nctu/script/99-robotx_port.rules** , and do that by the command only outside docker container.
```bash
source set_usb_port.sh
```
We can see the serial number by 
```bash
udevadm info --attribute-walk /dev/ttyUSB01
```
After changing, we can use the command to see it.
```bash
ll |grep mm_ 
 ```
 #### open mmwave
```bash
roslaunch ti_mmwave_rospkg multi_6843_2.launch veh:=husky2 serial:=00AB4BE1
```
```bash
roslaunch ti_mmwave_rospkg multi_6843_3.launch veh:=husky2 serial:=00789E0C
```
#### open tf
```bash
roslaunch sensor_tower_description description_with_jackal.launch
```
#### process with mmwave pointcloud & mapping pointcloud
```bash
roslaunch lidar_crop d435_crop.launch
```
```bash
roslaunch ti_mmwave_rospkg mmwave_d435_map.launch
```
### transfer poindcloud to laserscan
```bash
roslaunch subt_rl pcToLaser_mmwave.launch veh:=husky2
```
### open LiDAR
```bash
roslaunch velodyne_pointcloud  VLP16_points_wamv.launch
```
## We need LiDAR to train the data or be the baseline
### LiDAR crop & laserscan
```bash
roslaunch lidar_crop lidar_tower_crop.launch
```
## All commands can be replaced by the following command
```bash
source start_mmwave.launch
```
