# System Info 
- ubuntu 24.04.1 
- Nothing Phone 1 (Global)
- For Windows OS or Europe based Nothing phones refer to this [blog](https://techibee.in/how-to-install-stock-nothing-os-on-nothing-phone-1-if-running-custom-rom/)

# Prerequisite to Install Stock OS on Nothing Phone (1)
- Download the latest Platform tool: [Download](https://developer.android.com/studio/releases/platform-tools)
- Download Stock Nothing OS 1.1.4 Firmware (Global) : [Download](https://android.googleapis.com/packages/ota-api/package/54b8dbd1c303be00ef156c602b756c76d8d9b6e1.zip)
- Clone / Download the boot.img , vendor_boot.img , Stock Nothing OS 1.1.4 Firmware in the same directory you have extracted above adb files

# Reverting Back To Nothing OS 
- Make sure your phone has developer settings and enable usb debugging
- Connect your phone to your pc , open terminal and cd into the adb direcrtory in which you have cloned .img and firmware
- To check if check adb connected devices :
```
adb devices
./fastboot devices
```
- ERROR : if you cant see device after fastboot devices , try reconnecting your phone

- To boot into fastboot mode run the following adb command

```
  adb reboot bootloader
```
![image](https://github.com/user-attachments/assets/083ab657-9e75-4cfa-9b49-db28ee6d594d)

- Now to boot the boot image and vendor boot image
```
./fastboot flash boot boot.img
./fastboot flash vendor_boot vendor_boot.img
```
- Once completed we have to boot our device into fastbootd mode
```
./fastboot reboot fastboot
```

- Now your device will boot into fastbootd
- From here your volume buttons to navigate and select `Enter Recovery` by pressing power button
- Now scroll down again and select `apply update from adb`



- Now For sideloading the firmware (that you have already cloned into adb directory)
```
adb sideload 54b8dbd1c303be00ef156c602b756c76d8d9b6e1.zip
```

- ERROR : the sideloading might end at 94% with error `adb:failed to read command` but that is totally fine and you can move forward
- Now using Volume keys and power key select `wipe data/factory reset` -> `factory reset data`
- Finally select `reboot system`


- WARNING : BOOTLOADER WILL NOT BE CLOSED , YOU WILL HAVE TO CLOSE IT YOURSELF

