# Face_tracking
本代码使用基于Haar特征的级联分类器对象检测算法进行人脸的捕捉，并将捕捉的人脸用方框框出通过判断方框的面积与原面积大小控制机器人进行前后移动，通过判断方框坐标中心与画面像素中心位置的偏移控制机器人进行左右的移动。

重要文件夹/模块：
arbotix_ros：arbotix控制器是一款比较受欢迎的舵机驱动器，arbotix_ros是arbotix控制器的ros软件包
mbot_description：存放机器人模型建模的相关文件
mbot_gazebo：存放gazebo仿真文件包括gazebo生陈大哥世界文件与打开所需要的launch文件
mbot_teleop：使用键盘控制机器人运动
robot_vision：人脸识别与发布机器人运动信息

robot_vision中的重要脚本:
face_detector.py:订阅话题input_rgb_image获取图像进入回调函数，使用基于Haar特征的级联分类器对象检测算法进行人脸的捕捉，并通过框出的人脸的大小位置并发布机器人运动的信息到话题cmd_vel，同时将识别后的图像通过话题cv_bridge_image发布

使用时
1.编译 
catkin_make

2.设置环境变量
source devel/setup.bash
（每打开一个新的终端都需要）

3.打开gazebo仿真
roslaunch mbot_gazebo view_mbot_with_camera_gazebo.launch
(或随意打开mbot_gazebo文件夹中的launch文件)

4.打开电脑摄像头
roslaunch robot_vision usb_cam.launch

5.打开人脸识别
roslaunnch robot_vision face_detector.launch

6.打开画面显示
rqt_image_view
