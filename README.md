# Bluetooth-Multiboot

This tutorial shows that how to configure your bluetooth devices in order to use them in multi-boot system without pairing them again.

## Principle
Different OS generates new linkkey when pairing with your divice. We need to synchronize the linkkey saved in different OS.

## Tutorial
1. Pair your bluetooth device in order of Ubuntu, Windows, macOS.
(optinal) Find and memorize MAC addresses of your bluetooth adapter and devices. 
2. Extract linkkeys by following this [guide](https://github.com/ichicho/BT-LinkkeySync).
   Import linkkeys into Windows by using the method offered in the guide.
3. Open `btkeys.reg` generated by step2 and find the linkkey.
   
   Contents in `btkeys.reg` must like:
   ```
   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTHPORT\Parameters\Keys\<MAC Address of Bluetooth Adapter>]
   "<MAC Address of Bluetooth Device>"=hex:<linkkey>
   ```
   Example:
   ```
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTHPORT\Parameters\Keys\000000aaaaaa]
   "111111bbbbbb"=hex:0a,1b,2c,3d,4e,5f,6g,7h,8i,9j,0k,1l,2m,3n,4o,5p
   ```
   Memorize the linkeys.
4. Boot to Ubuntu and edit linkkeys saved in system with nano/vim as root:
   ```
   sudo nano /var/lib/bluetooth/<MAC Address of Bluetooth Adapter>/<MAC Address of Bluetooth Device>/info
   ```
   Example:
   ```
   sudo nano /var/lib/bluetooth/<00:00:00:aa:aa:aa>/<11:11:11:bb:bb:bb>/info
   ```
   Find the linkkey saved in file:
   ```
   [LinkKey]
   Key=<LINKKEY>
   ```
   Example:
   ```
   [LinkKey]
   Key=0000000000000000AAAAAAAAAAAAAAAA
   ```
   Replace contents after `Key=` with the linkkey you memorized in step3. Remove `,`(commas) and change lower case letters to UPPER CASE.
   After replacement, file should look like:
   ```
   [LinkKey]
   Key=0A1B2C3D4E5F6G7H8I9J0K1L2M3N4O5P
   ```
   Reboot your system. Every device must work.

## Problem
   Cannot deal with Bluetooth LE devices.
