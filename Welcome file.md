
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

More details you can check the link (http://pr.cs.cornell.edu/anticipation/)

<a name="user-content-Video"></a>
### [<span class="octicon octicon-link"></span>](#video)Video

* * *
<a href="http://v.youku.com/v_show/id_XMzM4MzA5ODAyNA==.html?spm=a2hzp.8244740.0.0"></a>

[![IMAGE ALT TEXT](http://static.youku.com/index/img/header/yklogo_h.png)](https://www.youtube.com/watch?time_continue=9&v=dZyp41qBZBE "cornell anticipation project")

<a name="user-content-Quickstart"></a>

### [<span class="octicon octicon-link"></span>](#quickstart)Quickstart

* * *
Before run this package,you need to install the required dependencies:
-   OpenCV version 2.4 or greater (dev version or install from source)
-   PCL 1.7
-   Boost version 1.50 or greater
----------
Commands to install the required dependencies and run anticipation code on CAD-120 Subject 1 data:

```
# install pcl
sudo add-apt-repository ppa:v-launchpad-jochen-sprickerhof-de/pcl 
sudo apt-get update
sudo apt-get install libpcl-all

# install opencv
sudo apt-get install libopencv-dev
#install boost 1.50
wget http://sourceforge.net/projects/boost/files/boost/1.50.0/boost_1_50_0.tar.bz2
tar --bzip2 -xf boost_1_50_0.tar.bz2
#If you prefer to install boost to a specific directory use the following instead
# ./bootstrap.sh --prefix=path/to/installation/prefix
./bootstrap.sh
./b2
sudo ./b2 install

# download code 
git clone https://github.com/nathantsoi/human_activity_anticipation

# compile
cd human_activity_anticipation/build
cmake ..
make
cd ../src/pyobjs
make

#install learning code dependencies
cd ../../
sh install_dependencies.sh

# download data
cd data/
wget http://web3.cs.cornell.edu/pr/CAD-120/data/Subject1_rgbd_rawtext.tar.gz
wget http://pr.cs.cornell.edu/humanactivities/data/Subject1_annotations.tar.gz
tar -xvzf Subject1_annotations.tar.gz
tar -xvzf Subject1_rgbd_rawtext.tar.gz
mv  Subject1_rgbd_rawtext/*/*rgbd.txt  .
mkdir objects
mkdir objects_tracked
cp Subject1_annotations/*/objects/* objects/
cp Subject1_annotations/*/objects_tracked/* objects_tracked/
cp Subject1_annotations/*/*.bag .
cp Subject1_annotations/*/*.txt .
cat Subject1_annotations/*/activityLabel.txt  | grep -v END > activityLabel.txt
cat Subject1_annotations/*/labeling.txt > labeling.txt


# run anticipation code 
cd ../build/
./predict_seg ../data/ activityLabel.txt 1
```



<a name="user-content-Structure"></a>

### [<span class="octicon octicon-link"></span>](#structure)Structure

* * *
![image](https://github.com/Jiajie-Ye/YOLO_for_ROS/blob/master/yolo%20node%20and%20topic%20from%202018-01-25%2022:29:17.png)

<a name="user-content-FAQ"></a>

### [<span class="octicon octicon-link"></span>](#faq)FAQ

* * *


**Q1**. When run the code, you may meet the error,
COULD NOT LOAD MODULE "*svmstruct_mrf_act_dyn*"!
perhaps module is not in module search path?

**A1**. First, you should make sure that you executed the script *install_dependencies.sh* successfully. It's best to install the libraries with the same version listed in the script.
 Second, you should modify the path（*PYTHONPATH*） at the bottoｍ of the script.
 
**Q2**. How to understand the code?

**A2**. You can download the papers listed in the following websites:
http://pr.cs.cornell.edu/humanactivities/index.php
http://pr.cs.cornell.edu/anticipation/index.php
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM5Nzk0NTI5MF19
-->