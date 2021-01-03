# This guides the installation of Mac Os  (X Catalina with Clover and 11 BigSur with OpenCore) on a Lenovo Ideapad s540-14IWL. 
The specs of the machine are:

(CPU) Intel Core i5-8265U

IPS Panel 14 "

1920x1080

RAM 8 GB DDR4

Intel UHD Graphics 620

SSD 256 GB (and a second added by me) 

DW1820a wifi and bluetooth (replaced the original intel one)

Card Reader

Bluetooth, HDMI, USB 3.1, USB-C, Wi-Fi

Fingerprint sensor.

#SINCE DECEMBER 2020, this guide will continue with MacOS 11 Big Sur and OpenCore. However I will keep the clover EFI for Catalina for people who need it. 

1. Everything works except of fingerprint sensor (which will never work). You can disable it the easy way by adding to boot arguments in config.plist the following (uia_exclude=HS07;) minus the brackets.
2. If you need HDMI at boot or after wake up without unpluggin - pluggin the cable, add to boot arguments "igfxonln=1" (without brackets). System will be a bit chopy for a few seconds but it works normally afterwards.  


# Bear in mind that this guide and its settings are based on a disabled CFG lock. There are details below on how to access hidden bios settings.

# BE VERY CAREFULL, THIS PART IS IMPORTANT
Credit goes to Diliansky (https://github.com/daliansky) https://github.com/daliansky/Lenovo-Air13-IWL-Hackintosh/blob/master/Advanced/ReadMe.md
I am not responsible if you mess it up!!!!!!!

Enter BIOS->disable OneKeyBattery -> save and exit. Power off the laptop. Power button to turn on → F2 to enter the normal BIOS → Power button to turn off → then press, moving fast, the following keys in sequence

         F1 → 1 → Q → A → Z
         
         F2 → 2 → W → S → X
         
         F3 → 3 → E → D → C
         
         F4 → 4 → R → F → V
         
         F5 → 5 → T → G → B
         
         F6 → 6 → Y → H → N
         

Turn on the power button → F2 enters the hidden BIOS (if unsuccessful, please speed up your hand and try again).
Then go to 
# Advanced → Power & Performance → CPU-Power Management Control → CPU Lock Configuration → CFG Lock → Disabled
save and exit 

# THEN: 
1. Create a bootable installation of Mac os 11 Big Sur. 
2. Mount EFI partition of the bootable media. 
3. Replace EFI file with my EFI. 
4.Open config.plist and insert appropriate platform info (serial, UUID etc).
5. Boot from the bootable media, install, mount EFI partition of the installation HD of your laptop, replace the EFI folder with the EFI on the USB, enjoy.  

I have chosen to work with CPUFried kexts since I get the best power consumption with them. 
Even better results can be achieved with voltageshilft. 

# This whole project would not be possible whithout the help and patience of marianopela (https://github.com/marianopela/Lenovo-Ideapad-S540-14IML-Hackintosh)

# UPDATE 3-1-2020 

I am uploading a "beta" EFI for testing best power consumption. 

This is tuned to put brakes (in a way) to the system so that I can maximize battery time and run the CPU cooler and ultra quiet. 

Ofcourse it affects performance. 

It is used with voltageshift (command: ./voltageshift offset -120 -50 -100 0 0 0 0 0 1 20 30 0 60  STILL WORKING ON THIS) and with BIOS selection QUIET)

DISCLAIMER:
1. This project started for educational purposes. 
2. The data, guides etc of this project are provided as they are. 
3. I take no responsibility for any problem or damage to any person or property caused directly or indireclty because of the use of any data or guide etc of this project. 
  
