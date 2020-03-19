# This is about an installation of Mac Os X on a Lenovo Ideapad s540-14IWL. 
The specs of the machine are as follows:
(CPU) Intel Core i5-8265U
IPS Panel 14 "
1920x1080
RAM 8 GB DDR4
Intel UHD Graphics 620
SSD 256 GB (and a second added by me) 
Card Reader
Bluetooth, HDMI, USB 3.1, USB-C, Wi-Fi
fingerprint sensor.

It is still a work in progress but so far.... 
everything works except of 
1. firgerprint sensor (which will never work). You can disable it the easy way by adding to boot arguments in config.plist the following (uia_exclude=HS07;) minus the brackets.
2. HDMI which is in progress. 
3. Wifi - bluetooth, since I haven' t received the replacement card yet.

However, the most serious problem so far is the touchpad(VoodooI2C), which works perfectly well apart of a strange input issue.
Saddly this problem consumes a lot of power due to cpu usage (for the issue see here: https://github.com/alexandred/VoodooI2C/issues/250)  

Bear in mind that I am novice and my coding skills are next to zero. 
Therefor you will probably find a lot of errors in the files and I will probably need your help way more than my abillity to answer to any questions.

Important: This build does not contain any wifi capabillities. I am still waiting for the DW1820a I ordered and will update the EFI as soon as it arrives and is installed. 

Finaly, this whole project would not be possible whithout the help and patience of marianopela (https://github.com/marianopela/Lenovo-Ideapad-S540-14IML-Hackintosh). 

GUIDE for people with the same laptop:
1. Create a bootable installation of Mac os x Catalina. 
2. Mount EFI partition of the bootable media. 
3. Replace EFI file with my EFI. 
4. Open config.plist with clover configurator, go to SMBIOS and press several times the Generate New button under serial number, check validity, save. Create new SMUUID. At System Parameters create new Custom UUID. Save changes. 
5. Boot from the bootable media, install, boot again, mount EFI partition of the laptop, replace the EFI folder with my EFI, enjoy.
6. You might want to change clover boot entries, since I have a manjaro linux installation on the second NVME.  


UPDATE 16-3-2020: 
Latest EFI: 1) Much better power consumption.At idle in Intel Power Gadget PKG is at around 1.10 Watts, core is at around 0,30 Watts. Very good thermals. CPU idles at 0,8 Ghz (lower than the apple default of 1,2Ghz. Display reduces brightness much more than default "AddPNLF".  Only 1 ACPI error at boot. Touchpad in polling mode until the kexts for GPIO are fixed. Everything else works. 

UPDATE 19-3-2020:
HDMI WORKS!!!!
No HDMI sound yet ....... 
Slighlty better power consumption. Working on solving ACPI errors when booting with HWPEnable and no Plugintype and cpufirend kexts.

Next milestones:
1. Update kexts and drivers
2. Get HDMI working (DONE)
3. Fix last ACPI error

DISCLAIMER:
1. This project started for educational purposes. 
2. The data, guides etc of this project are provided as they are. 
3. I take no responsibility for any problem or damage to any person or property caused directly or indireclty because of the use of any data or guide etc of this project. 
  
