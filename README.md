# Bluetooth-Multiboot

This tutorial shows that how to configure your bluetooth devices in order to use them in multi-boot system without pairing them again.

## Principle
Different OS generates new linkkey when pairing with your divice. We need to synchronize the linkkey saved in different OS.

## Tutorial
1. Pair your bluetooth device in order of Ubuntu, Windows, macOS.
(optinal) Find and memorize MAC addresses of your bluetooth adapter and devices. 
2. Extract linkkeys by following this [guide](https://github.com/ichicho/BT-LinkkeySync).
   Import linkkeys into Windows by using the method offered in the guide.
3. Boot to Ubuntu and edit the linkkey saved in `/var/lib/bluetooth/<MAC address of bluetooth adapter>/<MAC address of bluetooth device>/info` 
