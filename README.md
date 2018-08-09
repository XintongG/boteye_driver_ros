README
==========

The orginal version of Baidu Boteye driver: https://github.com/baidu/boteye_driver

This is a ROS version of Baidu Boteye XP3 Camera. For other camera model, please test the code by your self!

Due to the special circumstances of my computer, I change some .h file of the driver, please use code compare tool for more information.

You can still show image or save data as I try to keep the original function while changing the driver

This driver is only for study, which stability cannot be guaranteed.

XintongG, DLUT

==========

Following is the README of the orginal repository.

This is xPerception's driver for multiple types of camera modules.

## Required dependencies (built from source): ##
 You can git clone the XP_3rdparty repo, which has all the source code of needed 3rdparty dependencies by other repos, but that's an overkill. You can just download the Opencv.

- Opencv 3.0.0

## Optional dependencies (built from source): ##
 To run an application of the driver, glog and gflags are needed. You can get them from the XP_3rdparty repo, or use apt-get:
  ```
  apt-get install -y --allow-unauthenticated \
    libgflags-dev \
    libgoogle-glog-dev
  ```

## Setup steps: ##
  ```
  mkdir ~/Development; cd ~/Development
  git clone [the git repo of driver]
  cd driver
  mkdir build; cd build;
  cmake ..
  make -j4
  ```

  Currently, we only enable pre-commit hook for cpplint.To enable the git hook, you need to do the following (You only need to config git hook once per fresh clone):
  ```
  cd ~/Development/driver/utils
  source config_githook.sh
  ```

## Optional setup steps: ##
 Build a simple binary that depends on the driver library. The binary can show and record the raw image and imu data from the sensor.
 ```
 cd app/
 mkdir build; cd build;
 cmake ..
 make -j4
 ```
