# Radiomaster Tx16s charging fix
The Radiomaster Tx16s radio transmitter features a USB-C port for charging. Unfortunately, it doesn't work properly. It only accepts charging from 5V-only USB chargers,
and won't charge when used with certain power-delivery protocol enabled chargers. 

The problem: The Radiomaster Tx16s doesn't properly adhere to USB-C standards. The USB-C port on the device should feature a 5.1k pull-down resistor on its CC1 and CC2
pins. However, I found using my multimer that it only features a 5.1k resistor on one of those pins. For whatever reason, the other pin isn't connected to anything. As a result, the charger dosn't
properly recognize the device and won't charge it.

The fix: Solder on a 5.1k pull-down resistor

## Before the modification:
![20220328_175141 1](https://user-images.githubusercontent.com/95006894/167707483-bf7fa2c7-a901-4cb6-a41f-895d21829a5a.jpg)
I used my multimeter to find a the pad of a nearby capacitor that was connected to ground
## The modification:
![20220328_182240 1](https://user-images.githubusercontent.com/95006894/167707857-8ef85e45-a115-4b76-8b98-0ce383540bbc.jpg)
I used a standard 5.1k 0805 SMD resistor connected to ground and a piece of enameled wire to connect to the pin.

The soldering job is certainly not the prettiest, since I was soldering to a huge ground plane while simultaneously trying not to melt the radio's plastic shell.
In the end, everything works and the radio now charges properly. 

[return to main page](index.md)
