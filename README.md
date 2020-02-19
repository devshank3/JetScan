# JETSCAN 

A standalone portable 3D scanner with Intel realsense and Jetson Nano. 
 

![N|Solid]( https://github.com/devshank3/JETSCAN/blob/master/jetscan.JPG )


## Motives 

* Standalone 3D scanner 
* Instant 3D reconstruction 
* Metrically accurate

![N|Solid]( https://github.com/devshank3/JETSCAN/blob/master/Jetscan.jpeg )

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
## Usage 

###
> Install Jetpack from NVIDIA jetson platform 

 Follow the below link 
 https://developer.nvidia.com/embedded/jetpack
 Burn  SD card with JETPACK  -- Minimum of 64 GB class 10 

> Uninstall / Purge Cmake Install Cmake 3.14

1. Download cmake3.14 from 'https://cmake.org/files/v3.14/cmake-3.14.0.tar.Z'
2. tar -zxvf cmake-3.14.0.tar.gz
3. cd cmake-3.14.0
4. sudo ./bootstrap 
5. sudo make
6. sudo make install

> Installing Open3D from Source 

git clone --recursive https://github.com/devshank3/Open3D.git




----

## Hardware used :

### Portable jetson nano module 

* [Jetson Nano](https://developer.nvidia.com/buy-jetson)

* [AC8265 Wireless NIC  WiFi / Bluetooth](https://www.waveshare.com/wireless-ac8265.html)

* [5.0" 40-pin 800x480 TFT Display without Touchscreen](https://www.adafruit.com/product/1680)

* [TFP401 HDMI/DVI Decoder to 40-Pin TTL Breakout - Without Touch](https://www.adafruit.com/product/2218)

* [HDMI FPV Flat HDMI](https://www.amazon.com/dp/B06XRVC2VV/ref=sspa_dk_detail_0?psc=1&pd_rd_i=B06XRVC2VV&pd_rd_w=byqi5&pf_rd_p=45a72588-80f7-4414-9851-786f6c16d42b&pd_rd_wg=Hzr7I&pf_rd_r=8WHPN6ME290WF1Q7JJD6&pd_rd_r=d0c2b721-1cce-47d2-bba7-dac0a12f7b81&spLa=ZW5jcnlwdGVkUXVhbGl)

* [DC-DC 9V/12V to 5V 4A Mini Buck Module Converter Step-down Module](https://www.banggood.in/DC-DC-9V12V-to-5V-4A-Mini-Buck-Module-Converter-Step-down-Module-p-1343488.html?rmmds=search&cur_warehouse=CN)

### Others 

* [Intel realsense D435i](https://store.intelrealsense.com/buy-intel-realsense-depth-camera-d435i.html?_ga=2.118782729.109480876.1578129593-1156130352.1574240129)

----

## Software used 


