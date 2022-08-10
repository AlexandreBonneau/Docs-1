---
template: main.html
---

![Setup-Banner](https://raw.githubusercontent.com/ExpressLRS/ExpressLRS-hardware/master/img/quick-start.png)

## Flashing via Wifi

Target: `AXIS_THOR_2400_TX_via_WIFI`

Device Category: `AXIS 2.4 GHz`

Device: `AXIS THOR 2400TX`

![via WiFi](../../assets/images/Method_TX_WiFi.png)

!!! attention
    The methods below applies if you've already updated your Tx modules to 2.x. For modules still in firmwares pre 2.x, you should use 1.x WiFi flashing method to update to 2.x. Or update to 2.x via USB instead.

### Method 1

With the correct target selected and [Firmware Options] set, **Build** your firmware using the ExpressLRS Configurator.

![Build](../../assets/images/Build.png)

Once it's done, it should open the Target folder for you where the `AXIS_THOR_2400_TX-<version>.bin` file is. Do not close this window so you can easily locate the correct file to upload to the module.

The next steps will require the [ExpressRLS Lua Script](https://github.com/ExpressLRS/ExpressLRS/blob/2.1.0/src/lua/elrsV2.lua?raw=true) (right-click, save as). Download the ExpressLRS lua script and save it to your Radio's `/Scripts/Tools` folder. Insert/attach your module into your module bay and make sure it's not loose and there's proper connection with the radio (see the [Radio Preparation](tx-prep.md) page). Execute the ExpressLRS lua script by pressing "System Menu" in your radio and then under Tools, select `ExpressLRS`.

![Lua Script](../../assets/images/lua1.jpg)
![Lua Script T16](../../assets/images/lua2.jpg)

If the script is stuck at `Loading...`, then there's a chance your module is still in v1.x firmware, your External RF module is not set to CRSF or that your module is not well-connected to the module bay pins.

![Lua3](../../assets/images/lua3.jpg)

Select **WiFi Connectivity** from the Lua script and then select **Enable WiFi**. Press OK once more to activate the WiFi on the Tx Module. Connect to the Access Point the module will create called `ExpressLRS TX`, with the password being `expresslrs`.

<figure markdown>
![WiFi Hotspot](../../assets/images/WifiHotspotTX.png)
</figure>

Using your browser, navigate to the correct page (typically http://10.0.0.1/) and it should show an upload form (you will have to scroll down a bit). You can drag-and-drop the `AXIS_THOR_2400_TX-<version>.bin` file that the ExpressLRS Configurator created. You can also click the `Choose File` button and navigate to the folder where the firmware was created. Ensure that you have selected the correct firmware file and click `Update`.

Once the file is uploaded, a pop-up confirmation will show up.

![Update Success](../../assets/images/web-firmwareupdateSuccess.png)

Wait for the Lua script screen to close the "WiFi Running" screen and your module should be updated now.

Verify the version and hash in the main screen of ExpressLRS Lua script.

**Join Local Network**

You can configure Home Network SSID and Password if you chose not to use ExpressLRS Configurator to set them. Once these are set, you can use the next two methods below.

![JoinNetwork](../../assets/images/web-joinnetwork.png)

### Method 2

With the correct target selected and [Firmware Options] set, **Build** your firmware using the ExpressLRS Configurator.

![Build](../../assets/images/Build.png)

Once it's done, it should open the Target folder for you where the `AXIS_THOR_2400_TX-<version>` file is. Do not close this window so you can easily locate the correct file to upload to the module.

Using the [ExpressLRS Lua Script](https://github.com/ExpressLRS/ExpressLRS/blob/2.1.0/src/lua/elrsV2.lua?raw=true) (right-click, save as), select `Wifi Connectivity` then choose `Enable WiFi` and if you have flashed your Tx Module with your Home WiFi Network details or have set it in Join Network section of the Update Page, it will connect to the local network automatically.

Using your browser, navigate to http://elrs_tx.local and the WiFi Update page should show up. Scroll down towards the Firmware Update section, as shown below:

![Firmware Update](../../assets/images/web-firmwareupdate.png)

Drag-and-drop the `AXIS_THOR_2400_TX-<version>.bin`  file created by the ExpressLRS Configurator into the Choose File field, or manually navigate to the Folder by clicking the `Choose File` button. Once the correct file is selected, click the `Update`. Wait for the process to complete, and the module will reboot (~1min).

Verify the version and hash in the main screen of ExpressLRS Lua script.

### Method 3

Using the [ExpressLRS Lua Script](https://github.com/ExpressLRS/ExpressLRS/blob/2.1.0/src/lua/elrsV2.lua?raw=true) (right-click, save as), select `Wifi Connectivity` then choose `Enable WiFi` and if you have flashed your Tx Module with your Home WiFi Network details or have set it in Join Network section of the Update Page, it will connect to the network automatically.

Using the ExpressLRS Configurator, select the correct Target and set your [Firmware Options]. Click **Build and Flash** and wait for the compile process to complete. You should see a section as pictured below and the Success message marking the update process complete.

![Build & Flash](../../assets/images/BuildFlash.png)

![Wifi Update Log](../../assets/images/WifiUpdateLog.png)

Verify the version and hash in the main screen of ExpressLRS Lua script.

## Flashing via USB/UART

Target: `AXIS_THOR_2400_TX_via_UART`

Device Category: `AXIS 2.4 GHz`

Device: `AXIS THOR 2400TX`

![via UART](../../assets/images/Method_TX_UART.png)

Attach a USB Data Cable to your module and Computer. Windows users might have to install [CP210x Drivers](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) to ensure the device is properly detected and initialized. 

![CP210x Drivers](../../assets/images/CP210xDriverDownload.png)

!!! note
    To flash the TX itself, the switch on the back side of the module must be set to the **leftmost** position. To flash the TX backpack, the switch must be set to the **rightmost** position. For normal operation the switch must be **centered**.
    <img src="../../../assets/images/thor-switch.png" width="30%">

Using the ExpressLRS Configurator with the correct Target selected and [Firmware Options] set, hit **Build & Flash**. Wait for the process to finish, and you should be greeted with the "Success" message.

![Build & Flash](../../assets/images/BuildFlash.png)

Verify the version and hash in the main screen of ExpressLRS Lua script.


## Using the module on a DX9

- Install the latest DX9 firmware with CRSF v2 support via Serial port.
- Wire up Power (Vbat & GND) as per Crossfire install instructions.
- Use Signal from DX9 to S.Port pin of the Thor TX module.
- Optional: Connect an external power source via XT30.
- Flash the TX module with `UART_INVERTED` **unchecked**.
- Adjust your Packet Rate to 250Hz using the Screen & Joystick.

This guide is contributed by discord user ChaserP.

[Firmware Options]: ../firmware-options.md
