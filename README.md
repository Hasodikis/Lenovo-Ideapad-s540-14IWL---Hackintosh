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

It is still a work in progress but so far.... 
1. Everything works except of fingerprint sensor (which will never work). You can disable it the easy way by adding to boot arguments in config.plist the following (uia_exclude=HS07;) minus the brackets.
2. HDMI is in progress.  (It works with sound, but there is a bit of yellow tint on the laptop display that is solved for the time being by changing display profilein settings)

However, the most serious problem so far is the touchpad(VoodooI2C), which works perfectly well apart of a strange input issue.
Saddly this problem consumes a lot of power due to cpu usage (for the issue see here: https://github.com/alexandred/VoodooI2C/issues/250)  

Bear in mind that I am novice and my coding skills are next to zero. 
Therefor you will probably find a lot of errors in the files and I will probably need your help way more than my abillity to answer to any questions.

Finaly, this whole project would not be possible whithout the help and patience of marianopela (https://github.com/marianopela/Lenovo-Ideapad-S540-14IML-Hackintosh) and the geniuses of Rehabman and Daliansky

# Bear in mind that from 10-4-2020 onwards this guide is based on a disabled CFG lock. There are details below on how to access hidden bios settings.

GUIDE for people with the same laptop:

# BE VERY CAREFULL, THIS PART IS IMPORTANT
Credit goes to Diliansky (https://github.com/daliansky) https://github.com/daliansky/Lenovo-Air13-IWL-Hackintosh/blob/master/Advanced/ReadMe.md
I am not responsible if you mess it up!!!!!!!

Power off the laptop. Power button to turn on → F2 to enter the normal BIOS → Power button to turn off → then press the following keys in sequence

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


# UPDATE 16-3-2020: 
Latest EFI: 1) Much better power consumption.At idle in Intel Power Gadget PKG is at around 1.10 Watts, core is at around 0,30 Watts. Very good thermals. CPU idles at 0,8 Ghz (lower than the apple default of 1,2Ghz. Display reduces brightness much more than default "AddPNLF".  Only 1 ACPI error at boot. Touchpad in polling mode until the kexts for GPIO are fixed. Everything else works. 

# UPDATE 19-3-2020:
HDMI WORKS!!!!
No HDMI sound yet ....... 
Slighlty better power consumption. Working on solving ACPI errors when booting with HWPEnable and no Plugintype and cpufirend kexts.

# UPDATE 20-3-2020:
Final ACPI Error (MCHC) corrected (thanks to ... Marianopela .... again!!!!)

# UPDATE 24-3-2020:
HDMI AUDIO WORKS. 
Also initialization of HDMI is smoother...
There is only one problem .... everything has a bit of a yellow tint !!!!!!
Untill this is solved, it can be corrected by choosing a different display profile and only the login screen will be a bit yellowish.
Slightly better power consumption. 

# UPDATE 7-4-2020
Updated clover to r5018
Updated kexts
System updated to 10.15.4
Installed DW1820a (wifi and bluetooth working normally)
Updated CPUFriend and created a new CPU Friend data provider kexts with low battery consumption in mind
With wifi and bluetooth power consumption is much higher, I am working on it. 
As always create your own S/N, SmUUID and Custom UUID

# UPDATE 10-4-2020 
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

You can choose which option you like.

# UPDATE 12-4-2020
Updated kexts 
F1 now truly mutes sound (credits: lietxia https://github.com/lietxia for the patched AppleALC)

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
  
