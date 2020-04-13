## Installation Instructions

This was installed when librealsense was on v2.33.1.

* ### Install the ROS distribution

    Install [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu) on Ubuntu 18.04.

* ### Install the usual apt-requirements.txt and pip-pacakges.txt.

* ### Install the debian package for librealsense

  * `sudo apt-get install software-properties-common`
  * Register the public key:
    `sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE`
  * Add the librealsense melodic repo:
    `sudo add-apt-repository "deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic main" -u`
  * Install the libraries:
    `sudo apt-get update`
    `sudo apt-get install librealsense2-utils`
    `sudo apt-get install ros-melodic-librealsense2`

* ### Clone the realsense_ros pacakge

  * Create a catkin workspace
    `mkdir -p catkin_ws/src`
    `cd catkin_ws/src/`
    `cd ..`
  * Clone Intel/realsense_ros package
    `git clone https://github.com/IntelRealSense/realsense-ros.git`
    `cd realsense-ros/`

* ### Install realsense_ros dependencies

  * `sudo apt-get install ros-melodic-ddynamic-reconfigure ros-melodic-nodelet ros-melodic-image-geometry ros-melodic-cv-bridge ros-melodic-image-transport`

* ### Install realsense_ros

  * `source /opt/ros/melodic/setup.bash`
  * `catkin build`
  * `source devel/setup.bash`

* ### Running

  * `roslaunch realsense2_camera rs_camera.launch`
  * To visualize laserscan, and if you have the depthimage_to_laserscan package installed, run
    `roslaunch realsense2_camera laserscan_from_realsense.launch`
  
  * #### Note 1
    Similar instructions can be used for installing on kinetic for dev laptops too. Replace bionic with xenial and melodic with
    kinetic.

  * #### Note 2
    If running in docker, the docker container might need to be privileged with access to the USB bus and the host network (for ROS visualization from a remote computer). Something like:
    docker run -it --privileged --net=host -v /dev/bus/usb:/dev/bus/usb cd0c427c0648 /bin/bash
