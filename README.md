#                                                    JETSCAN 

                    A standalone portable 3D reconstruction system with Intel realsense and Jetson Nano
 
<p align="center">
 <img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/jetscan.JPG" width="480" />
</p>

***
## Motives 

* Standalone 3D reconstruction system 
* Instant 3D reconstruction 
* Metrically accurate
* Low power consuming
* Offline and online (both)
* Cost effective 
* Modular approach 
* Deep learning integration (3D deep learning for registration)
***

**Hardware built:**
<p align="center">
 <img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Jetscan.jpeg" width="260" /><img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/34.jpg" width="260" /><img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/j1.jpg" width="260" />
</p>

**Reconstructed results:**
<p align="center">
<img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/78.png" width="260" /><img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/12.png" width="260" /><img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/23.png" width="260" />
</p>

----
## Introduction

**Jetscan is a portable 3D dense reconstruction system based on**

1. [Jetson nano by NVIDIA](https://developer.nvidia.com/embedded/jetson-nano-developer-kit)
2. [Intel Realsense D400 series depth camera](https://www.intelrealsense.com/depth-camera-d435i/)
3. [Open3D ](http://www.open3d.org/) by INTEL ISL
4. [theNded's CUDA implementation](https://github.com/theNded/Open3D)

----

## Schematic sketch

<p align="center">
<img src="https://github.com/devshank3/JetScan/blob/master/Schematic/Capture.PNG" width="380" />
</p>

----
## Software Setup

* For setting up the software stack, follow instructions in 
  
  Sofware_O3D - [Software setup](https://github.com/devshank3/JetScan/blob/master/Software_O3D/Readme.md)

* Complete software repo is [here](https://github.com/devshank3/Open3D-for-Jetson) (forked from Open3D) 

    https://github.com/devshank3/Open3D-for-Jetson

    its built on [theNded's](https://github.com/theNded) CUDA implementation 
----

## Hardware Setup

Follow instructions in 

1. Hardware_electronics - [Electronics setup](https://github.com/devshank3/JetScan/blob/master/Hardware_electronics/Readme.md)

2. Hardware_casing - [Case/Closure setup](https://github.com/devshank3/JetScan/blob/master/Hardware_casing/Readme.md)

----

Follow **https://github.com/devshank3/JetScan/blob/master/Software_O3D/Readme.md** for Software Setup

## Usage 

* Step 1 : Go to **Open3D-for-Jetson/Reconstruction_Jetscan_Hybrid/**

* Step 2 : Edit **Main_gui.py**

    set your system executable path to Run_MakeFragments,ViewPoseGraph,Run_IntegrateScene

    eg.

       os.system('/home/shank/Projects/3D_processing/jetscan/jetscan-final-edit/Open3D-for-Jetson/build/bin/examples/./Run_MakeFragments')

                                                              ⇩⇩⇩ to ⇩⇩⇩                       

       os.system('your_system _path/Open3D-for-Jetson/build/bin/examples/./Run_MakeFragments')

 * Step 3: Run the UI (in  virtual env if setup)

   > $ python3 Main_gui.py

* Step 4 : Start the Reconstruction

     **Capture RGB-D**

     Captures the RGB-D sequence

     **Reconstruct Scene**

     The hybrid reconstruction system starts with the RGB-D sequence recorded

     **View**

     View the latest reconstructed 3D Model


----
## Development

----

## Contribute

----
## License

----


