## Jetson Orin Nano Setup Guide

## Downgrade the Snap version to run firefox browser

```bashe
snape download snapd --revision=24724
sudo snap ack snapd_24724.assert
sudo snap install snapd_24724.snap
sudo sudo snap refresh --hold snapd
```

## How to configure GPIO pins
1. Run the following command in a terminal:

```bash
sudo /opt/nvidia/jetson-io/jetson-io.py
```

![System Diagram](images/gpio.png)

## How to configure RpLidar C1

1. Download the github repository to src folder of your workspace

```bash
git clone -b ros2 https://github.com/Slamtec/rplidar_ros.git

```

2. Build the workspace

```bash
colcon build
```
3. check of Lidar is detected on usb port 

```bash
ls /dev/ttyUSB*
```

4. Fix the serial permision

```bash
sudo usermod -a -G dialout $USER
sudo chmod 666 /dev/ttyUSB0
```
5. Launch the rviz

```bash
ros2 launch rplidar_ros view_rplidar_c1_launch.py
```
