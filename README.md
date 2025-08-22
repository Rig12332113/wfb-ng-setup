# WFB-ng setup 
This is the quick setup for running wfb-ng on Raspberry Pi. 

The main feature contain long range image transfer, camera switching and channel switching.

**Hardware**: Raspberry Pi 4 and 5 (verified). 

**OS**: Rpi OS bookworm 64 bits version.

**Note: Please make sure using wifi adapter suppoted by RTL8812au driver. RTl8812eu might need further adjustment.**


## Drone side:
Download (clone) the wfb-ng_setting repository to your drone computer (Rpi). After download, move to the directory and give permission to run the setdrone.sh.

```
cd wfb-ng_setting
sudo chmod +x ./setdrone.sh
sudo ./setdrone.sh
```
Finish running the script, the Rpi should reboot and start running wfb-ng.

To check wfb-ng drone running correctly, run following command:
```
wfb-cli drone
```
You should able to see the connection and the information of video sending rate, channel... 

<p align="center">
  <img width="800" height=1000" alt="image" src="https://github.com/user-attachments/assets/318497fc-b5a6-45b7-be7c-05a0825034ea" />
</p>

If you get wifibroadcast@drone.service failed, please check the wifi adapter is connecting and the service is running without errors.

## Ground station side:
Recommend installing Rpi OS with desktop, because the script set the display to monitor by default. Rtsp broadcast required further adjustment.

Download (clone) the wfb-ng_setting repository to your ground station (PC). After download, move to the directory and give permission to run the setgs.sh.

**Note: Please make sure plug in the wifi adapter before running the script. Otherwise, the script might fail to install wfb-ng**
```
cd wfb-ng_setting
sudo chmod +x ./setgs.sh
sudo ./setgs.sh
```
Finish running the script, the Rpi should reboot and start running wfb-ng.

To check wfb-ng gs running correctly, run following command:
```
wfb-cli gs
```
You should able to see the connection and the information of video recieving rate, channel... 

<p align="center">
  <img width="800" height="1000" alt="image" src="https://github.com/user-attachments/assets/d46a2f64-9f26-46c6-bd95-88f56c3f8e43" />
</p>

If you get wifibroadcast@gs failed, please check the wifi adapter is connecting and the service is running without errors.

## Application:
In wfb-ng_setting repository, there is a camctl.py script providing simple application.
```
python3 camctl.py
```

**Command:**

start csi/usb: start or switch to the video captured by camera connected through csi/usb port.

stop csi/usb: stop playing the video captured by camera connected through csi/usb port.

shutdown: stop both cameras.

hop {channel}: hop to certain channel.
