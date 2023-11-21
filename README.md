# ros_mpu6050_arduino
## Install Arduino IDE Latest Version 
 download Arduino IDE 2 appimage file from [https://downloads.arduino.cc/arduino-ide/arduino-ide_2.2.1_Linux_64bit.AppImage?_gl=1*1f4iy9f*_ga*NDM5OTIwMzQzLjE2OTk3NTk1MzM.*_ga_NEXN8H46L5*MTcwMDMxMjA3NC4xMS4wLjE3MDAzMTIwNzQuMC4wLjA.] 
 
 Then right click on the downloaded file / properties / permissions  select allow executing file system.
 
## Dependency for arduino
  ```
  sudo apt-get update
  sudo apt-get install ros-noetic-rosserial-arduino
  sudo apt-get install ros-noetic-rosserial
 ```
create a libraries folder inside arduino folder and then
  ```
  cd ~/Arduino/libraries
  rosrun rosserial_arduino make_libraries.py <path of arduino libraries>
  ```

## Install

Use the following commands to download and compile the package.

```
cd ~/<work space>/src
git clone https://github.com/asimfathekhani/ROS_MPU6050
```
Open your <work_space>/src/ros_mpu6050_arduino/ and copy "ros.h" and "Arduinohardware.h" and paste it in Arduino/libraries/ros_lib/

[delete the previous file in that location]
now open new terminal 
```
cd <work space>
catkin_make
gedit ~/.bashrc
```
and paste ```source ~/< work_space >/devel/setup.bash``` at the last line
## Arduino code
Connect Your Arduino with mpu6050 board to your PC And upload the code given in this repository.
**Download Mpu6050 lib by Electronicscat**(https://github.com/ElectronicCats/mpu6050)
```
sudo ls -l /dev/ttyACM* 
sudo chmod 777 /dev/ttyACM0
```
or
```
ls -l /dev |grep ttyUSB
sudo chmod 777 /dev/ttyUSB0
```
**Note:** Do not use Serial.begin or serial.print in the code

## Run the package
1. Start the ROS master
```
roscore
```
2. start the serial communication in ros:
``` 
rosrun rosserial_python serial_node.py /dev/ttyUSB0 _baud:=500000
```
or 
```
rosrun rosserial_python serial_node.py /dev/ttyACM0 _baud:=500000
```
2. Run the launch file:
```
roslaunch mpu6050_imu_driver mpu6050_imu.launch
```
