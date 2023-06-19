# This is a "guide" (well sort of) for the installation of macos Ventura (as of June 2023 and onwards) on a Lenovo Ideapad s540-14IWL. 

The specs of the machine are:

| Specifications | Details |
|:-: |:-: |
| Processor | Intel Core i5-8265U  |
| RAM | 8gb DDR4 (4gb soldered on board) |
| SSD | SSD 256 GB (and a second added by me) |
| Graphics Card | Intel UHD Graphics 620 |
| Monitor | 14" IPS 1920x1080 |
| Sound Card | layout-id 15 |
| Card reader | working |
| Finger print reader | not working (will never) |
| Network Card | Intel (replaced with DW1820A) |


1. Everything works except of fingerprint sensor (which will never work). You can disable it the easy way by adding to boot arguments in config.plist the following (uia_exclude=HS07;) minus the brackets.
2. If you need HDMI at boot or after wake up without unpluggin - pluggin the cable, add to boot arguments "igfxonln=1" (without brackets). System will be a bit chopy for a few seconds but it works normally afterwards.  


## Bear in mind that this guide and its settings are based on a disabled CFG lock. There are details below on how to access hidden bios settings.

# BE VERY CAREFULL, THIS PART IS IMPORTANT
Credit goes to @Daliansky https://github.com/daliansky/Lenovo-Air13-IWL-Hackintosh/blob/master/Advanced/ReadMe.md
I am not responsible if you mess it up!!!!!!!

Enter BIOS → disable OneKeyBattery → save and exit. Poweroff the laptop. Power button to turn on → F2 to enter the normal BIOS → Power button to turn off → then press, moving fast, the following keys in sequence

         F1 → 1 → Q → A → Z
         
         F2 → 2 → W → S → X
         
         F3 → 3 → E → D → C
         
         F4 → 4 → R → F → V
         
         F5 → 5 → T → G → B
         
         F6 → 6 → Y → H → N
         

Turn on the power button → F2 enters the hidden BIOS (if unsuccessful, please speed up your hand and try again).
Then go to 
## Advanced → Power & Performance → CPU-Power Management Control → CPU Lock Configuration → CFG Lock → Disabled
save and exit 

## THEN: 
1. Create a bootable installation of Mac os 11 Big Sur. 
2. Mount EFI partition of the bootable media. 
3. Replace EFI file with my EFI. 
4.Open config.plist and insert appropriate platform info (serial, UUID etc).
5. Boot from the bootable media, install, mount EFI partition of the installation HD of your laptop, replace the EFI folder with the EFI on the USB, enjoy.  

I have chosen to work with CPUFried kexts since I get the best power consumption with them. 
Even better results can be achieved with voltageshilft. 

## NOTES ON VENTURA 13.4
1. There is a bug in 13.4 that messes up backlight after boot. After a boot (randomnly but it happens a lot, the screen will remain black for about to -3 minutes and then the loggin screen will come up. Just wait a bit. This bug is not present in 13.5 beta do it will probably be fixed. 
2. In order for the bluetooth to work I had to add this patch in config.plist --> NVRAM
   
   
				<key>bluetoothExternalDongleFailed</key>
				<data>
				AA==
				</data>
				<key>bluetoothInternalControllerInfo</key>
				<data>
				AAAAAAAAAAAAAAAAAAA=
				</data>


I dont know if 13.5 breaks things again. 

## This whole project would not be possible without the help and patience of: [marianopela](https://github.com/marianopela/Lenovo-Ideapad-S540-14IML-Hackintosh), [lietxia](https://github.com/lietxia/XiaoXinAir14IML_2019_hackintosh) and [Lorys89](https://github.com/Lorys89)

# DISCLAIMER:
1. This project started for educational purposes. 
2. The data, guides etc of this project are provided as they are. 
3. I take no responsibility for any problem or damage to any person or property caused directly or indirectly because of the use of any data or guide etc of this project.
  
