# This is about an installation of Mac Os X (Catalina with Clover and BigSur with OpenCore) on a Lenovo Ideapad s540-14IWL. 
The specs of the machine are as follows:
(CPU) Intel Core i5-8265U
IPS Panel 14 "
1920x1080
RAM 8 GB DDR4
Intel UHD Graphics 620
SSD 256 GB (and a second added by me) 
DW1820a wifi and bluetooth
Card Reader
Bluetooth, HDMI, USB 3.1, USB-C, Wi-Fi
fingerprint sensor.


1. Everything works except of fingerprint sensor (which will never work). You can disable it the easy way by adding to boot arguments in config.plist the following (uia_exclude=HS07;) minus the brackets.

This whole project would not be possible whithout the help and patience of marianopela (https://github.com/marianopela/Lenovo-Ideapad-S540-14IML-Hackintosh) 

# Bear in mind that from 10-4-2020 onwards this guide is based on a disabled CFG lock. There are details below on how to access hidden bios settings.

GUIDE for people with the same laptop:

# BE VERY CAREFULL, THIS PART IS IMPORTANT
Credit goes to Diliansky (https://github.com/daliansky) https://github.com/daliansky/Lenovo-Air13-IWL-Hackintosh/blob/master/Advanced/ReadMe.md
I am not responsible if you mess it up!!!!!!!

Enter BIOS->desable OneKeyBattery -> save and exit. Power off the laptop. Power button to turn on → F2 to enter the normal BIOS → Power button to turn off → then press the following keys in sequence

         F1 → 1 → Q → A → Z
         
         F2 → 2 → W → S → X
         
         F3 → 3 → E → D → C
         
         F4 → 4 → R → F → V
         
         F5 → 5 → T → G → B
         
         F6 → 6 → Y → H → N
         

 Turn on the power button → F2 enters the hidden BIOS (if unsuccessful, please speed up your hand and try again).
Then go to 
# Advanced → Power & Performance → CPU-Power Management Control → CPU Lock Configuration → CFG Lock → Disabled

As always then 
1. Create a bootable installation of Mac os x Catalina. 
2. Mount EFI partition of the bootable media. 
3. Replace EFI file with my EFI. 
4. Open config.plist with clover configurator, go to SMBIOS and press several times the Generate New button under serial number, check validity, save. Create new SMUUID. Save changes. 
5. Boot from the bootable media, install, boot again, mount EFI partition of the laptop, replace the EFI folder with the  EFI on the usb, enjoy.
6. You might want to change clover boot entries, since I have a manjaro linux installation on the second NVME.  

# UPDATE 12-4-2020 
(Importand!!!!! From now on builds will be based on an unlocked CFG so please, if you don't have one modify config.plist settings.)
Updated kexts 
changed config.plist settings for unlocked CFG  (see above for method).
Included a SSDT-PLUD for cpu 
Recreated CPUFriend Data Provider kext
Installed 10.15.4 supplemental update with no problem
# Options
In my EFI you will find an SSDT-PLUG.aml
1. CpuFriend kexts in kexts folder and SSDT-PLUG.aml in ACPI/Patched folder,  with plugintype1=false in config.plist
2. CpuFriend kexts in kexts folder, NO SSDT-PLUG.aml in ACPI/Patched folder,  with plugintype1=true in config.plist
(these two options give the same results. CPU base freq at 600Mhz, idle freq at 600mhz, core watts 0,30 at idle, PKG watts 1.70 at idle, cpu utilazation at 4,70 % and a bit more at idle. 
3.CpuFriend kexts in kexts folder, NO SSDT-PLUG.aml in ACPI/Patched folder and plugintype1=false in config.plist
(this option has CPU base freq at 600Mhz, but idle req freq is never bellow 1,2Gmhz.  Core watts 0,30 and bellow at times at idle, PKG watts 1.70 at idle, cpu utilization is less than 3 % at idle



# MAJOR UPDATE 30-11-2020
Transition to OpenCore and installation of MacOs 11 BigSur. 

I attach the EFI. In config.plist, I have removed all platform data, so you have to fill in your own.

Make an installation USB for BigSur, mount its EFI partition, copy my EFI file on the EFI partition of your USB, install, copy my EFI file on the EFI partition of your HD. Done. 
Up to now everything works. 

# As always, this whole project would not be possible whithout the help and patience of marianopela (https://github.com/marianopela/Lenovo-Ideapad-S540-14IML-Hackintosh)

DISCLAIMER:
1. This project started for educational purposes. 
2. The data, guides etc of this project are provided as they are. 
3. I take no responsibility for any problem or damage to any person or property caused directly or indireclty because of the use of any data or guide etc of this project. 
  
