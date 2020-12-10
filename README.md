#describe: 
	**This version only verifies the mechanical 32 line radar with dual ports, single and double echoes, vertical angle of 1 degree and 0.33 degree**
	**The driver is developed with ros1, and supports running under Ubuntu 14.04, Ubuntu 16.04, and Ubuntu 18.04**

##1. Set up the workspace and build the compiling environment
	mkdir -p ~/leishen_ws/src
	cd ~/leishen_ws/src
	tar –xvf lslidar_c32_V2.01.tar

##2. Compile and package
	cd ~/leishen_ws
	catkin_make
	
##3. Run: 
	source ~/leishen_ws /devel/setup.bash
	roslaunch lslidar_c32_decoder lslidar_c32.launch



##4. lslidar_c32.launch Configuration file description: 
	<arg name="device_ip" default="192.168.1.206" />	//Set to the corresponding IP of radar
	<arg name="msop_port" default="2366" />	//The port corresponding to the data packet
	<arg name="difop_port" default="2367" />	//The port corresponding to the device package
	<param name="rpm" value="600"/>	//Set to the speed corresponding to radar, 600 means 600 rpm in 1 minute
	<param name="frame_id" value="laser_link"/>	//Set the name of the fixed frame in rviz
	<param name="add_multicast" value="false"/>	//false means Turn off multicast
	<param name="group_ip" value="224.1.1.2"/>	//Multicast IP settings
	<param name="min_range" value="0.15"/>	//Points less than 0.15 meters are not displayed
	<param name="max_range" value="150.0"/>	//Points greater than 150 meters are not displayed
	<param name="scan_start_angle" value="1000.0"/>	//Only points from 10 to 300 degrees are displayed
	<param name="scan_end_angle" value="30000.0"/>
	<param name="distance_unit" value="0.25"/>		//The unit of distance is 0.25cm
    	<param name="degree_mode" value="1"/>	//1 means vertical angle 1 degree, 2 means vertical angle 0.33 degree
	<param name="return_mode" default="1"/>	//1 means single echo, 2 means double echo
	<param name="time_synchronization" default="false" />	//False means to use the local time of the computer, and true means to use the GPS time
	<param name="publish_scan" value="true"/>	//True means to turn on scan point cloud display
	<param name="scan_num" value="15"/>	//15 means The scan point cloud corresponding to the 15th line is displayed
	<param name="config_vert" value="true"/>	//True meansTurn on vertical angle calibration








