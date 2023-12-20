HOW TO FIX ERRORS!
-------------------

----------IF YOU FACE ERRORS LIKE 

YDLidar-SDK/./core/base/thread.h:138:46: warning: format ‘%X’ expects argument of type ‘unsigned int’, but argument 2 has type ‘_size_t’ {aka ‘long unsigned int’} [-Wformat=]
  138 |           printf("[YDLIDAR DEBUG] Thread [0x%X] ready to cancel[%d] time[%u]\n",
      |                                             ~^
      |                                              |
      |                                              unsigned int
      |                                             %lX


      
THAN YOU ARE AT THE RIGHT PLACE. :)
-
ERROR FIXING TESTED! ON YDLIDAR UBUNTU 20.04 WITH ROS2 FOXY AND HUMBLE AND 22.04 WITH ROS2 FOXY AND HUMBLE 
-
VERY EASY ... LETS START FROM THE BEGINING...
-
STEP 1- GO TO INSTALL SDK PAGE AND DO WHATEVER IS SAID. DONT WORRY IF YOU SEE ERROR MESSAGES, KEEP GOING TILL THE END. WE WILL FIX IT AFTER THE INSTALLATION
-
(ORIGINAL INSTRUCTIONS:
-
ydlidar_ros2_driver depends on YDLidar-SDK library. If you have never installed YDLidar-SDK library or it is out of date, you must first install YDLidar-SDK library. If you have installed the latest version of YDLidar-SDK, skip this step and go to the next step.

1. Download or clone the [YDLIDAR/YDLidar-SDK](https://github.com/YDLIDAR/YDLidar-SDK) repository on GitHub.
2. Compile and install the YDLidar-SDK under the ***build*** directory following `README.md` of YDLIDAR/YDLidar-SDK.)
FOLLOW THE INSTRUCTIONS AND INSTALL THE YDLIDAR-SKD!

AFTER YDLIDAR-SDK INSTALLATION GO HOME PLACE
cd           (press enter)

 ----------------------than again the original instructions to follow:

## Clone ydlidar_ros2_driver

1. Clone ydlidar_ros2_driver package for github : 

   `git clone https://github.com/YDLIDAR/ydlidar_ros2_driver.git ydlidar_ros2_ws/src/ydlidar_ros2_driver`

2. Build ydlidar_ros2_driver package :

   ```
   cd ydlidar_ros2_ws
   colcon build --symlink-install

---------------------------------------------------
ABOVE IT SAYS YOU TO DO:
1) cd           		(press enter)
2) cd ydlidar_ros2_ws           (press enter)
3) colcon build  		(press enter)
-----------------------------------------------------

AGAIN YOU WILL SEE LOTS OF ERRORS LIKE THIS... DONT WORRY
-----
s2_driver_node.cpp:16:
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h: In function ‘bool ydlidar::core::base::fileExists(const string&)’:
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_ino’ [-Wmissing-field-initializers]
  183 |   struct stat info = {0};
      |                        ^
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_mode’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_nlink’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_uid’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_gid’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_rdev’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::__pad1’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_size’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_blksize’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::__pad2’ [-Wmissing-field-initializers]
/home/kalyon/robot_ws/install/ydlidar_sdk/include/core/base/ydlidar.h:183:24: warning: missing initializer for member ‘stat::st_blocks’ [-Wmissing-field-initializers]
.
.
.BLA BLA BLA BLA
.
.
      |   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~
/home/kalyon/ydlidar_ros2_ws/src/ydlidar_ros2_driver/src/ydlidar_ros2_driver_node.cpp:180:51: warning: unused parameter ‘response’ [-Wunused-parameter]
  180 |   std::shared_ptr<std_srvs::srv::Empty::Response> response) -> bool
      |   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~

Finished <<< ydlidar_ros2_driver [23.8s]

Summary: 1 package finished [35.2s]
  1 package had stderr output: ydlidar_ros2_driver
source ./install/setup.bash



LET'S KEEP GOING.. TYPE THOSE COMMANDS TOO:

4) source ./install/setup.bash    					 (ENTER)
   
5) echo "source ~/ydlidar_ros2_ws/install/setup.bash" >> ~/.bashrc  	 (ENTER)
   
6) $source ~/.bashrc							 (ENTER)
-------

WE ARE BEGINING TO FIX THE ERRORS!!!!!!!!!!!
NOW THERE ARE 3 FILES TO CHANGE! DESTROY THE OLD ONES!
-
1ST FILE: 
ydlidar.yaml  <<<located under your home/  ydlidar_ws/src/ydlidar_ros2_driver/params   find it and change! what you are changing.. let me explain, i am using X4 lidar, which has a baudrate 128000.. not the other- other values creates errors!!, it changes that and some other work or sensor parameters. 
---------------------------------------
IF YOU ARE USING OTHER MODELS, OPEN THE ydlidar.yaml file, YOU WILL SEE LOTS OF PARAMETERS LIKE  "BAUDRATE",  "SAMPLE RATE" ETC.. FROM ORIGINAL PAGE CHECK YOUR OWN DEVICE'S PARAMETERS AND CONFIGURE YOURS. 
-ORIGINAL PAGE BELOW:
https://github.com/YDLIDAR/ydlidar_ros2_driver/blob/master/details.md#dataset
-----------------------------------------------------

2ND FILE:
ydlidar_launch.py   <<<<<<located under:     home/  ydlidar_ws/src/ydlidar_ros2_driver/launch    change it !
---------------------------------------------------


3RD FILE:
ydlidar_ros2_driver_node.cpp >>>>located under     home/     ydlidar_ws/src/ydlidar_ros2_driver/src     find it and change it. what you are changing: there are declarations in the file. but written wrong. we add if the decleration is a string <std::string> or if it is a boolean <bool> or if it is an integer <int>  or it is a <float>
----------------------------------------------------
THAN FINALLY MAKE A COLCON BUILD --SYMLINK-INSTALL
GO TO:
YOURPC@YOURPC-YOURPC:   ~/ydlidar_ros2_ws$ AND TYPE THE COMMAND>>>>    

colcon build --symlink-install
--
EXAMPLE:
-
kalyon@kalyon-ak:~/ydlidar_ros2_ws$ colcon build --symlink-install
[13.808s] WARNING:colcon.colcon_ros.prefix_path.ament:The path '/home/kalyon/robot_ws/install/ydlidar' in the environment variable AMENT_PREFIX_PATH doesn't exist
[13.809s] WARNING:colcon.colcon_ros.prefix_path.catkin:The path '/home/kalyon/robot_ws/install/ydlidar' in the environment variable CMAKE_PREFIX_PATH doesn't exist
Starting >>> ydlidar_ros2_driver
Finished <<< ydlidar_ros2_driver [8.55s]

CONGS! YOU MADE IT... 

LETS FINALLY DO THE SOURCING!

 source ./install/setup.bash
 -
EXAMPLE:
kalyon@kalyon-ak:~/ydlidar_ros2_ws$ source ./install/setup.bash



...CONTINUE TO THE ORIGINAL INSTRUCTIONS:
-
1. Connect LiDAR uint(s).
   ```
ros2 launch ydlidar_ros2_driver ydlidar_launch.py   <<<<<<YOU CAN CALL YOUR LIDAR WITH THAT COMMAND
---------------------------------------------------------------------------------------------------   
   ```
   or 

   ```
   launch $(ros2 pkg prefix ydlidar_ros2_driver)/share/ydlidar_ros2_driver/launch/ydlidar.py 
   ```
2. RVIZ 
-
ros2 launch ydlidar_ros2_driver ydlidar_launch_view.py    <<<< YOU DONT NEED THAT COMMAND THIS NODE WILL NOT WORK, OR IF YOU CHANGE THE DECLERATIONS THAT YOU MADE TO ydlidar_launch.py 	IT WILL WORK TOO..

1))BUT INSTEAD OF DOING THAT... DO THIS:
ros2 launch ydlidar_ros2_driver ydlidar_launch.py   ><<< CALL YOUR LIDAR..

2))IN ANOTHER COMMAND WINDOW, CALL RVIZ
rviz2

3)) go to rviz
--click Add
--click ByTopic
--scroll down and find /scan LaserScan , choose and click ok
--on the left menu,  2-3 settings needs to be changed!

Global Optipns
Fixed Frame: base_link

LaserScan
Topic: /scan
History Policy: System Default
Reliability Policy: Best Effort
Durability Policy: Volatile

--on the right menu
Current View: Orbit (rviz)
Target Frame: laser_frame or base_link (you choose and try others)








