# my_master_thesis_ros
In this repository, I compiled the source code using ROS for the master thesis.

- camera_velodyne_calibration
	- camera_velodyne_calibration_gazebo
	- my_but_calibration_camera_velodyne
- deep_learning_object_recognition

## Hardware Spec
- PC
	- OS : Ubuntu 14.04 LTS
	- Memory : 32GB
	- CPU : Intel® Core™ i7-4790K CPU @ 4.00GHz × 8 
	- GPU : GeForce GTX TITAN X
	- Strage : 2TB

- Robot
	- Sensors
		- ZED(Stereolabs)
		- HDL-32e(Velodyne)
		- AMU-1802BR(IMU)
	- Vehcle
		- Differential drive

## Requirements
- ROS indigo(Ubuntu 14.04)
- CUDA 7.5+
- [Chainer](https://github.com/pfnet/chainer) 2.0.0+
- OpenCV 2.4+, 3.1+
- PCL 1.7+, 1.8+

## How to setup dependencies
### Install ROS indigo for Ubuntu 14.04
```
$ sudo apt-get install ros-indigo-desktop-full
```
**NOTE: Please see the details [Install ROS indigo](http://wiki.ros.org/ja/indigo/Installation/Ubuntu).**

### Install CUDA and cuDNN
- Install CUDA
	- Download CUDA 8.0 deb file(local) on [developer.nvidia.com/cuda](https://developer.nvidia.com/cuda-downloads) and run the following command
		```
		$ sudo dpkg -i cuda-repo-ubuntu1604_8.0.*_amd64.deb
		$ sudo apt update
		$ sudo apt install cuda
		```
- Install cuDNN 5.1
	- Download cuDNN 5.1 on [developper.nvidia.com/cudnn](https://developer.nvidia.com/rdp/cudnn-download) and run the following command
		```
		tar xzvf cudnn-8.0-linux-x64-v5.1.tgz 
		sudo cp -a cuda/lib64/* /usr/local/cuda/lib64/
		sudo cp -a cuda/include/* /usr/local/cuda/include/
		sudo ldconfig
		```

- Set CUDA and cudnn path(add .bashrc)
	```
	$ cd $HOME
	$ vim .bashrc
	```
	added bellow
	```
	## CUDA and cuDNN paths
	export PATH=/usr/local/cuda/bin:${PATH}
	export LD_LIBRARY_PATH=/usr/local/cuda/lib64:${LD_LIBRARY_PATH}
	```
	check CUDA path
	```
	$ echo $PATH             # output "/usr/local/cuda/bin"？
	$ echo $LD_LIBRARY_PATH  # output "/usr/local/cuda/lib64"？
	$ which nvcc             # output "/usr/local/cuda/bin/nvcc"？
	$ nvidia-smi             # output nvidia GPU information？
	```
**NOTE: Please see the details [CUDA and cudnn install](http://qiita.com/JeJeNeNo/items/05e148a325192004e2cd).**

### Install chainer
```
pip install numpy
pip install cupy
pip install cython
pip install chainer
```
**NOTE: Please see the details [chainer install guide](https://docs.chainer.org/en/v2.0.0/install.html) and [cupy install guide](https://docs-cupy.chainer.org/en/stable/install.html).**
### Install PCL 1.8.0
```
$ cd $HOME
$ git clone -b pcl-1.8.0 https://github.com/PointCloudLibrary/pcl.git
$ mkdir build
$ cd build
$ cmake ..
$ make
```
after compiling it, install
```
$ sudo make install
```

### Install OpenCV 3.1.0
```
$ cd $HOME/Downloads
$ git clone -b 3.1.0 https://github.com/opencv/opencv.git
$ cd opencv
$ mkdir build
$ cd build
$ cmake ..
$ make
```
after compiling it, install
```
$ sudo make install
```

### Setup sensors
- HDR-32e
	```
	$ cd $HOME
	$ cd ros_catkin_ws/src
	$ git clone https://github.com/ros-drivers/velodyne
	$ cd ../
	$ catkin_make
	```

- ZED
	- Downlowd the ZED SDK on [stereolabs.com](https://www.stereolabs.com/developers/release/2.1/#sdkdownloads_anchor) and setup the ZED SDK
	- Download zed-ros-wrapper
		```
		$ cd $HOME
		$ cd ros_catkin_ws/src
		$ git clone https://github.com/stereolabs/zed-ros-wrapper
		$ cd ../
		$ catkin_make
		```
**NOTE: Please see the details [ZED Documentation](https://www.stereolabs.com/documentation/overview/getting-started/introduction.html).**

## How to Build
```
$ cd $HOME
$ cd ros_catkin_ws/src
$ git clone https://github.com/aoyan27/my_master_thesis_ros master_thetis/
$ cd ../
$ catkin_make
```

## Preperation for the execution
### Calibrate camera and Velodyne
Under review

### Estimate human trajectory
- deep_leaning_object_detection
	- my_faster_rcnn_with_ros.py
		This code needs pre-trained model.
		- Download pre-trained model
		```
		$ cd $HOME
		$ cd ros_catkin_ws/src/master_thesis/deep_leaning_object_detection/data/faster_rcnn
		$ curl https://dl.dropboxusercontent.com/u/2498135/faster-rcnn/VGG16_faster_rcnn_final.model?dl=1 -o VGG16_faster_rcnn_final.model
		```

## How to run
### Calibrate Camera and Velodyne
Under review

### Estimate human trajectory


