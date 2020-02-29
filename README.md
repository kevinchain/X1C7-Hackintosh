# X1C7-Hackintosh
Hackintosh build for Lenovo X1 Carbon 7th Gen

## Before You Start
**!! DO WITH YOUR OWN RISK !!**
<br> You won't damage your laptop by installing macOS, but its clearly out of warranty.

## Check your model

While Lenovo has configure to order (CTO) option, your laptop may have diffrent specs even it has same name. I'll write down my specs below. If you have diffrent specs, you may (or may not) experience random error. 
<br>
<br>
| Model Name       | Lenovo ThinkPad X1 Carbon 7th Gen (20QD-S0QG00) |
| ---------------- | ----------------------------------------------- |
| Processor        | Intel Core i7-8565U (Whiskey-Lake)              |
| Memory           | 16GB LPDDR3 2133MHz                             |
| Storage          | Western Digital PC SN730 NVMe SSD 512GB         |
| Graphics         | Intel UHD Graphics 620                          |
| Display          | 14.0" 4K (3840x2160) UHD 500nit IPS             |
| Audio            | Realtek Audio ALC 285                           |
| Ethernet         | Intel Ethernet Connection I219-V                |
| WLAN & Bluetooth | Intel Dual Band Wirless-AC 9560                 |
| WWAN             | Fibocom LTE Modem                               |
| Security         | Windows Hello IR Camera, Fingerprint Reader     |
| Others           | LED Backlit Korean Keybaord                     |
<br>

## Current Compatibility

**Connectivty (I/O, Networking)**

* WiFi/Bluetooth card is soldered in board, and its whitelisted on BIOS. 

* WWAN slot can be used for 2nd SSD, however network card will not be accepted.

| Feature                     |     | Dependences     | Notes                            |
| --------------------------- | --- | --------------- | -------------------------------- |
| WiFi                        | ❌   | No Driver       | Not Swappable, Use dongle        |
| Bluetooth                   | ❌   | No Driver       | Not Swappable, Use dongle        |
| Ethernet                    | ✅   | `IntelMausi.kext` |                                  |
| USB 3.0 / Type-C            | ✅   |                 | Tested all ports with Samsung T5 |
| Thunderbolt 3               | -   |                 |                                  |
| WWAN (LTE Cellular-Network) | ❌   | No Driver       | Can be used for 2nd SSD          |
<br>

**Input Devices**

* Trackpad could not work while installation process. <br> You can finish installation by trackpoint and go to troubleshooting to get trackpad work. 

| Feature    |     | Dependences                                                  | Notes                                                    |
| ---------- | --- | ------------------------------------------------------------ | -------------------------------------------------------- |
| Trackpoint | ✅   | `VoodooPS2Controller.kext`                                     |                                                          |
| Trackpad   | ✅   | `VoodooI2C.kext`, `VoodooI2CHID.kext`, Kext Patch on `config.plist` | Gesture works fine.                                      |
| Keyboard   | ✅   |                                                              | Ony F1~F6 works. Print Screen key will disable trackpad. |
| Webcam     | ❌   |                                                              |                                                          |
<br>

**Audio & Graphics**
<br>

| Feature                       |     | Dependences                                                                | Notes                                          |
| ----------------------------- | --- | -------------------------------------------------------------------------- | ---------------------------------------------- |
| Hardware Acceleration (QE/CI) | ✅   | `WhateverGreen.kext` `Liliu.kext`, Device properties on `config.plist`          | Whiskey-lake uses CFL (Coffelake) hardware ID. |
| Brightness Control            | ✅   | Brightness fix from RehabMan's DSDT patch, `igfxcflbklt=1` on boot arguments |                                                |
| HDMI Out                      | ❌   | Don't know how to fix                                                      |                                                |
| HiDPI (Retina Mode)           | ✅   | Don't know how to fix                                                      | UI will show up as 1920x1080 by default        |
| Audio Playback / Record       | ⚠️   | `AppleALC.kext` (Layout-ID 21)                                                    | No Subwoofer                                               |
<br>

**Power Management**
<br>

| Feature           |     | Dependences                                         | Notes                                  |
| ----------------- | --- | --------------------------------------------------- | -------------------------------------- |
| Battery Indicator | ✅   | Lenovo X230i battery fix from RehabMan's DSDT patch |                                        |
| Sleep / Wake      | ✅   |                                                     | Press power button 2-3 secs to wake up |
<br>

## Troubleshoot

I'm not an hackintosh expert, I cannot give you any kind of solution.<br>
I'll write down when I found any issues, and solution (if its possible to fix).
<br>

**Q. Trackpads are not working**
<br> A. Use trackpoint or USB mouse to get fully installed. After installation, open up terminal and type `sudo kextcache -i /` after reboot your trackpad should work. 
