# ros_mpu6050_arduino
Install Arduino IDE Latest Version
$ sudo apt-get update
$ sudo apt-get install ros-noetic-rosserial-arduino
$ sudo apt-get install ros-noedic-rosserial
$ cd ~/Arduino/libraries
$ rosrun rosserial_arduino make_libraries.py
$ mkdir -p ~/<work space>/src
$ git clone 

$ cd <work space>
$ catkin_make
$ gedit ~/.bashrc  
and paste [source ~/<work space>/devel/setup.bash] at the last line

$ sudo ls -l /dev/ttyACM* 
$ sudo chmod 777 /dev/ttyACM0
or
$ ls -l /dev |grep ttyUSB
$ sudo chmod 777 /dev/ttyUSB0

$ roscore 
$ rosrun rosserial_python serial_node.py /dev/ttyUSB0 _baud:=500000
or 
$ rosrun rosserial_python serial_node.py /dev/ttyACM0 _baud:=500000
$ roslaunch mpu6050_imu_driver mpu6050_imu.launch
