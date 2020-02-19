#                                                    JETSCAN 

                        A standalone portable 3D scanner with Intel realsense and Jetson Nano
 

<p align="center">
 <img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/jetscan.JPG" width="480" />
</p>



## Motives 

* Standalone 3D scanner 
* Instant 3D reconstruction 
* Metrically accurate
* low power 
* offline and online (both)
* cost effective 
* Modular approach 
* Deep learning integration (3D deep learning )


<p align="center">
 <img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Jetscan.jpeg" width="480" />
</p>

<p align="center">
<img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/34.jpg" width="320" /><img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/j1.jpg" width="320" />
</p>

<p align="center">
<img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/78.png" width="400" /><img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/12.png" width="400" /><img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/23.png" width="400" />
</p>



----

## Introduction

Jetscan is an open source 3D scanner based on 

1. [Jetson nano by NVIDIA](https://developer.nvidia.com/embedded/jetson-nano-developer-kit)
2. [Intel Realsense D400 series depth camera](https://www.intelrealsense.com/depth-camera-d435i/)
3. [Open3D ](http://www.open3d.org/) by INTEL ISL

----


## Schematic sketch

![N|Solid]( https://github.com/devshank3/JetScan/blob/master/Schematic/Capture.PNG )


----
## Software Setup



For setting up the software stack 

Follow instructions in Sofware_O3D/ 


[Software setup](https://github.com/devshank3/JetScan/blob/master/Software_O3D/Readme.md)

Complete software repo is here 


https://github.com/devshank3/Open3D-for-Jetson



its built on [theNded's](https://github.com/theNded) 


https://github.com/theNded/Open3D

----

## Hardware Setup :

Follow instructions in 

Hardware_electronics/

[Electronics setup](https://github.com/devshank3/JetScan/blob/master/Hardware_electronics/Readme.md)

Hardware_casing/

[case setup](https://github.com/devshank3/JetScan/blob/master/Hardware_casing/Readme.md)


----

## Usage

After following **https://github.com/devshank3/JetScan/blob/master/Software_O3D/Readme.md** for Software Setup 

* Step 1 : Open **Open3D-for-Jetson/examples/Python/ReconstructionSystem/**

* Step 2 : Copy or Cut GUI2.py to the build **Open3D-for-Jetson/build/bin/examples/**

* Step 3 :   Open **Open3D-for-Jetson/examples/Cuda/ReconstructionSystem/config/intel/test.json**

**Assign the preset path for **

* Path data
* Camera intrinsic data

**"path_dataset": " Python dataset path of D435i capture",**  
This directry with your system path "Open3D-for-Jetson/examples/Python/ReconstructionSystem/dataset/realsense/"  

**"path_intrinsic": " intel D435i intrinsics either from CUDA config file or Captured dateset intrinsic file",**
 Usually "Open3D-for-Jetson/examples/Python/ReconstructionSystem/dataset/realsense/camera_intrinsic.json"
 
 * Step 4: Run the GUI
 
**In the respective directive path run the GUI.py files**

Open3D-for-Jetson/examples/Python/ReconstructionSystem/

> $ python3 GUI.py

Open3D-for-Jetson/build/bin/examples/

> $ python3 GUI2.py

**Two Graphical user interfaces pop up:**

<p align="center">
<img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/IMG_20200218_065556.jpg" width="340" /><img src="https://raw.githubusercontent.com/devshank3/JETSCAN/master/Scanned_result/IMG_20200218_064923.jpg" width="340" />
</p>

* Step 5

**Recording**
In **GUI**
click on **Recorder** 

recording of **RGB** and it alligned **Depth** starts 
you can see the no of frames being captured in the terminal 

**Insruction while capturing **

* For Small environment captiure less than 1000 frames
* For detailed capture make sure less blackish area in the capture frame 
* make sure of backlits (lights / CFL / LED etc ) while capturing scenes
* Do not shake the module much 
* Can capture both Indoor and Outdoor as D435i supports both 

-----

* Max distance of capture of depth can be adjusted by 
This snippet in 

Open3D-for-Jetson/examples/Python/ReconstructionSystem/realsense_recorder.py

```
# We will not display the background of objects more than
#  clipping_distance_in_meters meters away
clipping_distance_in_meters = 3 # 3 meter
clipping_distance = clipping_distance_in_meters / depth_scale
```
mode setting snippet

```
class Preset(IntEnum):
Custom = 0
Default = 1
Hand = 2
HighAccuracy = 3
HighDensity = 4
MediumDensity = 5
.
.
.
.
.
.
.
.
.
# Using preset HighAccuracy for recording
if args.record_rosbag or args.record_imgs:
depth_sensor.set_option(rs.option.visual_preset, Preset.HighAccuracy)
```

* Step  6

After capturing the RGBD sequence 

**IN GUI2**
Click on **Fragment Construction**

In the terminal you can look for completion and time taken 

* Step 7

after Fragment / submap generation 

**IN GUI**
Click on **3D construct**

In the terminal you can look for completion and time taken 

* Step 8

after 3D scene final integration 

**IN GUI**
Click on **View**

**Your high resolution 3D model is ready in  point cloud format for view !!!!**



----
## Development

----

## Contribute

----
## License

----


