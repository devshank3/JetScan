# Software stack setup (Open3D-for-Jetson) : JetScan

## **Jetson Nano setup**

1. Collect Jetson nano and a > 64 gb Class 10 sd Card and other pheripherals for initial setup

2. Follow the official Nvidia jetpack install steps from the link below:

   https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#intro

3. Setup the dev kit by following [Jetsonhacks tutorials : Getting started ](https://www.youtube.com/watch?v=km0yT99eVTY)

4. Make sure you power up at max mode and operate in max mode [Jetsonhacks tutorials : use more power](https://www.youtube.com/watch?v=jq1OqBe267A)

5. Update & Upgrade

	```
	$ sudo apt-get update & upgrade
	$ sudo apt-get install python3-pip
	$ sudo apt-get install python-pip
	```

6. Cuda path setup/check

	```
	$ sudo ln -s /usr/local/cuda-10.2 /usr/local/cuda
	$ export CPATH=/usr/local/cuda-10.2/targets/aarch64-linux/include:$CPATH
	$ export LD_LIBRARY_PATH=/usr/local/cuda-10.2/targets/aarch64-linux/lib:$LD_LIBRARY_PATH
	$ export PATH=/usr/local/cuda-10.2/bin:$PATH
	```
### **Use More Memory**

  * Jetson nano offers 4 GB of RAM, out of which 1.1 GB is always occupied
  * By following the below process and installing a LXDE desktop env only 450 MB is occupied out of 4 GB

    https://www.zaferarican.com/post/how-to-save-1gb-memory-on-jetson-nano-by-installing-lubuntu-desktop

  * Allocate swap memory by following the below link

    https://www.jetsonhacks.com/2019/04/14/jetson-nano-use-more-memory/

***
## **Pre - setup ( dependency corrections Cmake & EIGEN3 )**


#### 1. Purge inbuilt Cmake and install latest

```
$ cmake --version
$ sudo apt remove --purge cmake
$ wget https://gitlab.kitware.com/cmake/cmake/-/archive/v3.18.2/cmake-v3.18.2.tar.bz2
$ tar xvf cmake-v3.18.2.tar.bz2
$ sudo apt install libssl-dev libcurl4-openssl-dev qt4-qmake
$ sudo apt autoremove
$ cd cmake-v3.18.2/
$ ./bootstrap --system-curl
$ make -j3
$ sudo make install
$ which cmake
$ cmake --version
```

#### 2. Purge inbuilt eigen3 and install latest

```
$ wget https://gitlab.com/libeigen/eigen/-/archive/3.3.7/eigen-3.3.7.tar.bz2
$ tar xvf eigen-3.3.7.tar.bz2
$ sudo apt remove --purge libeigen3-dev
$ sudo apt autoremove
$ cd eigen-3.3.7/
$ mkdir build && cd build
$ cmake .. -DCMAKE_INSTALL_PREFIX=/usr/local
$ sudo make install
```
**Eigen3 edit/patch for supressing warning**
```
$ sudo nano /usr/local/include/eigen3/Eigen/Core
```
**in line 257 change**

```
#include <host_defines.h>    to    #include <cuda_runtime_api.h>
```
***
## **Main Software stack setup**

**Recomended to install python packages compiled below in new Virtual Env**

```
$ pip3 install --upgrade pip
$ pip3 install wheel
$ pip3 install numpy
$ pip3 install matplotlib
$ pip3 install cython
$ pip3 install joblib
```

## **Install OpenCV with CUDA ON (python package)**
```
$ git clone https://github.com/mdegans/nano_build_opencv.git
$ cd nano_build_opencv
$ ./build_opencv.sh

update the global lib path in your venv

$ ln -s /usr/local/lib/python3.6/dist-packages/cv2/python-3.6/cv2.cpython-36m-aarch64-linux-gnu.so cv2.so
```

## **Open3D Original (CPU Only) (python package)**

 * Download the .whl pacakge from [this link](https://drive.google.com/file/d/1FhxkHadRMDqJsMjr4aRMilOgPXIEdh0H/view?usp=sharing)

 ```
 pip3 install open3d-0.10.1.0-cp36-cp36m-linux_aarch64.whl
 ``` 

## **Open3D-for-Jetson Build (CUDA Reconstruction pipeline)**

```
$ git clone --recursive https://github.com/devshank3/Open3D-for-Jetson.git
$ cd Open3D_for_Jetson/
$ cd util/scripts/
$ ./install-deps-ubuntu.sh
$ cd ..
$ mkdir build
$ cd build
$ cmake ..
$ make -j3
```
## **Librealsense Install by Jetsonhacks (python package)**

**Follow this [Jetson hacks tutorials : Librealsense Jetson nano](https://www.youtube.com/watch?v=lL3zxwN5Lnw)**

```
$ git clone https://github.com/JetsonHacksNano/installLibrealsense.git
$ cd installLibrealsense
```
**edit buildLibrealsense.sh with**

```
$ nano  buildLibrealsense.sh
```
```
line 6  # Jetson Nano; L4T 32.2.3   to    # Jetson Nano; L4T 32.4.3
line 9  LIBREALSENSE_VERSION=v2.31.0   to   LIBREALSENSE_VERSION=v2.38.1
line 11 NVCC_PATH=/usr/local/cuda-10.0/bin/nvcc  to  NVCC_PATH=/usr/local/cuda-10.2/bin/nvcc
```

**Finally build the Librealsense**
```
$ ./buildLibrealsense.sh

update the global lib path in your venv

$ ln -s /usr/lib/python3/dist-packages/pyrealsense2/python-3.6/pyrealsense2.cpython-36m-aarch64-linux-gnu.so pyrealsense2.so
```

***
## **Check in virtual env created**

```
$ python3
$ import Open3D
$ import cv2
$ import pyrealsense2
```
***
### Credits:

Few clean dependencies & installation steps are inspired by [Nanotuxi](https://github.com/nanotuxi/jetsonNanoPatches):
https://github.com/nanotuxi/jetsonNanoPatches 

***