# Reverse Engineering a Trackpoint

Trackpoints are a force sensitive joystick that function as a mouse, unique to lenovo and thinkpad laptops. I wanted to add one to 
my own custom keyboard, so I bought a replacement thinkpad keyboard and ripped the trackpoint module out of it. 
![20230104_222238](https://user-images.githubusercontent.com/95006894/212996637-1c414bc0-fb3e-4973-a06e-5c3d08e6a356.jpg)

![20221106_152928](https://user-images.githubusercontent.com/95006894/212996008-a6f6717d-7bf0-4366-804a-e86000cfe683.jpg)

The one I recieved looked like it might be a cloned knockoff, so I used my oscilloscope to make sure that it actually works. 
The trackpoint is supposed to communicate with the ps2 protocol. Looking at the waveform, it was high when idle, and there were
data packets being sent when I applied force to the joystick, so it appeared to be working.
![20221231_162213](https://user-images.githubusercontent.com/95006894/212997028-2a19b4de-aae6-4870-b78b-0e2a78ca5f36.jpg)

According to the limited pinout information I found, the device requires 5V power. However, I wanted to use it with an rp2040 microcontroller
which has a 3.3v logic level. When testing, I changed the power input to 3.3v, and observed that the data packets were still being sent
and the voltage of the logic level pins didn't seem to have changed. After examining the board, I managed to locate a 3.3v regulator and discovered that the
entire board actually runs on 3.3v. 
![20221231_163641](https://user-images.githubusercontent.com/95006894/212996254-7b76d98e-85d4-454f-9bfb-bb94c5780e96.jpg)

I found out that circuitpython doesn't support ps2 input on the rp2040, so I wanted to try interfacing with the joystick directly instead of through ps2 module. 

None of the chips had any markings that allowed me to identify them, so I had to start reverse engineering the rest of the circuit using my multimeter.
I ended up with this diagram, showing that the joystick itself has a power and ground input, and 2 outputs. This suggests that it works like any other
analog joystick, which outputs an analog voltage relative to its position. Based on the configuration of the resistors, the mystery chip
is an inverting op amp with a gain of about 10. 
![image](https://user-images.githubusercontent.com/95006894/212998209-094f9c1d-65b6-438b-b2a0-be5dd234eb05.png)

I tested the output of the op amp using my oscilloscope, and concluded that even with the op amp it wasn't sensitive enough.
I decided to double the gain of the op amp by soldering a 5.1k ohm resistor in place of the 10k ohm resistors. 

![20230104_211812](https://user-images.githubusercontent.com/95006894/212996349-79e84558-9d77-404f-8763-e5015065198f.jpg)
I only had 0805 sized resistors, but I managed to squeeze them on. 
![20230104_213345](https://user-images.githubusercontent.com/95006894/213003852-f7e97970-9403-4ff9-a92b-84ff66720805.jpg)

Since I'm only using the op amp and not the ps2 communication chip, I cut the circuit board in half and created new solder points. 
![20230117_152209](https://user-images.githubusercontent.com/95006894/213004893-759dd425-0963-46b2-b35d-3fce79d67ecf.jpg)

After testing using the rp2040's analog inputs, it seems to work fine, although I may add capacitors or shielding to decrease interference. 

[return to main page](index.md)
