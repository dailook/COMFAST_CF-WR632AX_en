# COMFAST CF-WR632AX DHCP U-Boot

This U-Boot supports three flash layouts:  
- Stock UBI layout 64 MB  
- Expanded UBI partition layout 112 MB  
- Maximum UBI partition layout 114 MB  

The U-Boot web page has been beautified, leaving behind the factory's single-function and crude interface.  
It supports booting and flashing stock firmware; after flashing this U-Boot the stock firmware can still be started directly.

SPI-NAND flashing is NOT applicable to this model. Do NOT attempt it; forcibly flashing the full 128 MB stock backup will report ECC errors and the device will not work—absolutely do not try!

## Enter U-Boot
With power off, first connect the router’s LAN port to the computer with a network cable (the cable MUST be connected before power-on, otherwise the router will auto-reboot after entering U-Boot; if it does reboot, don’t panic, power off and enter U-Boot again).  
Keep holding the RESET button, apply power; after four red flashes the light turns solid blue, meaning U-Boot has been entered. Release RESET.  
Open a browser and go to 192.168.1.1 to enter the web flashing interface.  
U-Boot supports DHCP, no need to set a static IP on the computer.  
If the U-Boot web page looks abnormal, clear the browser cache and re-enter.

## Flash U-Boot
1. Extract the downloaded archive, enter the router’s management interface, import the extracted "backup.file" configuration file, and wait for the router to restore the configuration successfully.  
2. Open an SSH client (MobaXterm for example), username root, no password, log in to the router via SSH, drag the U-Boot file mt7981_comfast_cf-wr632ax-fip-fixed-parts-multi-layout.bin into the router’s /tmp folder.  
3. Type the following command and press Enter; if the output looks like the picture, the U-Boot has been flashed successfully. After flashing, power off and enter U-Boot again by the method above.
4. ```bash
   mtd write /tmp/mt7981_comfast_cf-wr632ax-fip-fixed-parts-multi-layout.bin FIP
   ```

## Flash back to stock
Enter U-Boot, select the default stock partition layout, choose the stock firmware file downloaded from COMFAST’s official site, upload and flash it; the device will return to stock while keeping this U-Boot.

Stock firmware download address:  
http://www.comfast.com.cn/index.php?m=content&c=index&a=show&catid=31&id=862
