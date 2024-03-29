# Creating the Operating System Image
## Install the IoT Dashboard
Download the IoT Dashboard application
[IoT Dashboard Application](https://docs.microsoft.com/en-us/windows/iot-core/downloads)
## Prepare the SD Card
* Insert micro-SD card into the SD card adapter and insert it into the SD Card Reader
* Open the IoT Dashboard application, and sign in using your Microsoft Account
* From the IoT Dashboard application menu, select **Setup a new Device**
* In the Operating system drop down, select **Broadcomm [Rasbperry Pi 2 & 3]**
* For OS Build, select **Windows 10 IoT Core (Build 17763)**
* Ensure your SD card is correctly selected for the Drive (this should be detected automatically)
* Give your device a unique name on the network, for the context of this lab - please use your 3 initials followed by the month and day of your birth - for instance CEP0516
* Provide and confirm a password for the *Administrator* user of the Raspberry Pi - please make it something that you will remember.
* Ensure the WiFi connection box is checked and select our lab network WiFi connection. Please note, the IoT Dashboard application sometimes has trouble identifying WiFi networks, rest assured you can set this up later on the device itself. If no networks are displayed, simply ignore this step.
* Accept the license terms
* Click the download and install - the image will download and install on the SD card. A Command window will appear to complete the installation. At any time multiple File Explorer windows may open, simply close them. If prompted to format a drive in these File explorer windows, select cancel. This is due to a bug and Microsoft is aware - it has to do with the SD card being partitioned into multiple drives to support Microsoft IoT Core.

![Setting up a new device](./images/IoTDashboardSetUpANewDevice.png)

![Installation Console Window](./images/InstallationConsoleWindow.png)

## (Alternative) Installing image manually from the command prompt
(obtained from [Microsoft Documentation](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/dism)) 

* Open an administrator command prompt and navigate to the folder containing your local flash.ffu file.
* Plug-in your SD card to your machine.
* Find the disk number that your SD card is on your computer. This will be used when the image is applied in the next step. To do this, you can use the diskpart utility. Run the following commands:

```
 c:\FFUFolder>diskpart

  DISKPART>list disk
```
It should list all the storage devices attached to the computer.

![diskpartlistdisk.png](./images/diskpartlistdisk.png)

Exit diskpart by typing *exit*

```
DISKPART>exit
```

* Using the administrator command prompt, apply the image to your SD card by running the following command (be sure to replace PhysicalDriveN with the value you found in the previous step, for example, in this case SD card is disk number 4, so we will use /ApplyDrive:\\.\PhysicalDrive4 below)

```
dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck 
```

* Click on the "Safely Remove Hardware" icon in your task tray and select your USB SD card reader to safely remove it from the system. Failing to do this can cause corruption of the image.

## Install the Screen
Follow your screen's instructions.


## Plug in the Keyboard and optional Mouse  
Utilize the on-board USB ports to plug in a keyboard and mouse to aid in navigating the Windows IoT Core operating system on the device.

# Next Up
[Lab 2 - Configuring the Device](../Lab%202%20-%20Configuring%20the%20Device/index.md)

