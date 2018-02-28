
<a name="Top"></a>
[\<< 返回主页](http://www.github.com/birlrobotics/birl_baxter/wiki/mainpage_cn)

EN | [中文](https://github.com/birlrobotics/birl_baxter/wiki/yolo_for_ros_cn)

## Contents
1.  [Summary](#Summary)
2.  [Video](#Video)
3.  [Quickstart](#Quickstart)
4.  [Structure](#Structure)
5.  [FAQ](#FAQ)



<a name="user-content-Summary"></a>
### [<span class="octicon octicon-link"></span>](#summary)Summary
***
An important aspect of human perception is anticipation, which we use extensively in our day-to-day activities when interacting with other humans as well as with our surroundings. Anticipating which activities will a human do next (and how to do them) can enable an assistive robot to plan ahead for reactive responses in the human environments. Furthermore, anticipation can even improve the detection accuracy of past activities. In this work, we represent each possible future using an anticipatory temporal conditional random field (ATCRF) that models the rich spatial-temporal relations through object affordances. We then consider each ATCRF as a particle and represent the distribution over the potential futures using a set of particles

More details can see (http://pr.cs.cornell.edu/anticipation/)

<a name="user-content-Video"></a>
### [<span class="octicon octicon-link"></span>](#video)Video

* * *
<a href="http://v.youku.com/v_show/id_XMzM4MzA5ODAyNA==.html?spm=a2hzp.8244740.0.0"></a>

[![IMAGE ALT TEXT](http://static.youku.com/index/img/header/yklogo_h.png)](http://v.youku.com/v_show/id_XMzM4MzA5ODAyNA==.html?spm=a2hzp.8244740.0.0 "CMU openpose")

<a name="user-content-Quickstart"></a>

### [<span class="octicon octicon-link"></span>](#quickstart)Quickstart

* * *
Before run this package,you need to install the CUDA8.0 that has a long progress,and modify the workspace name:

Git clone the package into your catkin workspace.

`cd catkin_ws/src`

`git clone --recursive https://github.com/Jiajie-Ye/darknet_ros.git`

Then,open the yolo_ros.cpp file and modify the workspace name.(default workspace name:catkin_ws)

`char *cfg = "/home/catkin_ws/src/darknet_ros/cfg/yolo.cfg";`

`char *weights = "/home/catkin_ws/src/darknet_ros/weights/yolo.weights";`

Compile the package.

Last,run the yolo_ros node and camera.

`roslaunch darknet_ros yolo_kinect_ros.launch`

![image](https://github.com/Jiajie-Ye/YOLO_for_ROS/blob/master/1298236437.jpg)


<a name="user-content-Structure"></a>

### [<span class="octicon octicon-link"></span>](#structure)Structure

* * *
When you run the launch file above, it starts up 2 nodes.

The 1st one turn on the camera.

The 2nd node it starts the YOLO that subscribe the camera topic.We use it to recognize the object in the image.
![image](https://github.com/Jiajie-Ye/YOLO_for_ROS/blob/master/yolo%20node%20and%20topic%20from%202018-01-25%2022:29:17.png)

<a name="user-content-FAQ"></a>

### [<span class="octicon octicon-link"></span>](#faq)FAQ

* * *


**Q1**. How to use other camera.

**A1**.In order to use other camer,you need to modify the camera topic name and the launch file.

for example,I want to use the webcam,modify the name just like the following lines ①②③：

`const std::string CAMERA_TOPIC_NAME = "/camera/rgb/image_raw";//1`

`const std::string CAMERA_WIDTH_PARAM ="/yolo_ros/image_width";//2`

`const std::string CAMERA_HEIGHT_PARAM ="/yolo_ros/image_height";//3`

`//const std::string CAMERA_TOPIC_NAME = "/usb_cam/image_raw";//①`

`//const std::string CAMERA_WIDTH_PARAM = "/usb_cam/image_width";//②`

`//const std::string CAMERA_HEIGHT_PARAM = "/usb_cam/image_height";//③`

Then,run the following command:

`roslaunch darknet_ros yolo_webcam_ros.launch`
 


**Q2**. How to use other training weights.

**A2**. Firstly,you need to provide the weights and cfg files into the directories:

`catkin_ws/src/darknet_ros/weights/`

`catkin_ws/src/darknet_ros/cfg/`

Then,open the yolo_ros.cpp file and modify the current path of the weights and cfg files.

`char *cfg = "/home/catkin_ws/src/darknet_ros/cfg/yolo.cfg";`

`char *weights = "/home/catkin_ws/src/darknet_ros/weights/yolo.weights";`

Compile with catkin_make and run it.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk3OTQ3OTQ5Ml19
-->