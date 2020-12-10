## 描述
	**本版本只验证了机械32线雷达双端口，单双回波，垂直角度均匀1度和0.33度**
	**驱动用ros1进行开发，支持ubuntu14.04,ubuntu16.04,ubuntu18.04下运行**
## 建立工作空间
```
mkdir -p ~/leishen_ws/src
cd ~/leishen_ws/src
tar –xvf lslidar_c32_V2.01.tar
```
## 编译打包
```
cd ~/leishen_ws
catkin_make
```	
	
## 运行: 
```
source ~/leishen_ws /devel/setup.bash
roslaunch lslidar_c32_decoder lslidar_c32.launch
```



## lslidar_c32.launch配置文件说明: 
~~~xml
	<arg name="device_ip" default="192.168.1.206" />	//设置为雷达对应的IP
	<arg name="msop_port" default="2366" />	//数据包对应的端口
	<arg name="difop_port" default="2367" />	//设备包对应的端口
	<param name="rpm" value="600"/>	//设置为雷达对应的转速，600表示1分钟600转
	<param name="frame_id" value="laser_link"/>	//设置rviz中Fixed Frame的名称
	<param name="add_multicast" value="false"/>	//关闭组播
	<param name="group_ip" value="224.1.1.2"/>	//组播IP设置
	<param name="min_range" value="0.15"/>	//距离小于0.15米的点不显示
	<param name="max_range" value="150.0"/>	//距离大于150米的点不显示
	<param name="scan_start_angle" value="1000.0"/>	//只显示从10度到300度范围的点
	<param name="scan_end_angle" value="30000.0"/>
	<param name="distance_unit" value="0.25"/>		//距离单位为0.25cm
    	<param name="degree_mode" value="1"/>	//1 表示垂直角度均匀1度,2 表示垂直角度均匀0.33度
	<param name="return_mode" default="1"/>	//1 表示单回波,2 表示双回波
	<param name="time_synchronization" default="false" />	//false表示使用电脑本地时间,true表示使用GPS时间
	<param name="publish_scan" value="true"/>	//true表示开启scan点云显示
	<param name="scan_num" value="15"/>	//15表示显示第15条线对应的scan点云
	<param name="config_vert" value="true"/>	//开启垂直角度校准
~~~







