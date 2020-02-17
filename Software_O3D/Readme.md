# Software stack setup : JetScan

### Jetson Nano setup 

Collect the Jetson nano and a min 64 gb Class 10 sd Card and other pheripherals for initial setup

Follow the official Nvidia jetpack install steps from the link below:

https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#intro

and setup credentials in the dev kit follow the [Jetsonhacks tutorials : Getting started ](https://www.youtube.com/watch?v=km0yT99eVTY)

Make sure you power up at max mode and operate in max mode [Jetsonhacks tutorials : use more power](https://www.youtube.com/watch?v=jq1OqBe267A)

### Pre - setups ( dependency correction)

In the terminal

>Sudo apt-get update & upgrade

#### Purge inbuilt Cmake (issue with building) 
>sudo apt-get purge cmake

#### install Install Cmake 3.14

1. >Download cmake3.14 from 'https://cmake.org/files/v3.14/cmake-3.14.0.tar.Z'
2. >tar -zxvf cmake-3.14.0.tar.gz
3. >cd cmake-3.14.0
4. >sudo ./bootstrap 
5. >sudo make
6. >sudo make install

#### uninstall eigen3

>Sudo apt-get uninstall eigen3

#### install eigen3 ver - 3.3.7

>Cmake and install

### open3D for Jetson  

#### Clone the open3D for jetson Github repo

>git clone https://github.com/devshank3/Open3D-for-Jetson.git
-------------------------------------------------------------
>cd Open3D_for_Jetson/
-------------------------------------------------------------
>Install dependencies **util/scripts/install-deps-ubuntu.sh**
-------------------------------------------------------------
>Setup python dependencies 

	1. Numpy
	2. Matplotlib
	3. Opencv 
	4. Joblib
	5. cython
  
-------------------------------------------------------------

>Build the open3d 
```
mkdir build
cd build
cmake -DBUILD_EIGEN3=OFF..
Sudo make -j4 
```


