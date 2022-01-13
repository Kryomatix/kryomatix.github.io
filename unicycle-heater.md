# KingSong S18 battery heater
A battery-powered heater for cold weather operation

The KingSong S18 is powered by LG M50T batteries, which have an ideal operating temperature of 25℃.
Since the unicycle charges the batteries when braking, it is important that they are up to proper temperature.

## Heating elements
I originally intended to use nichrome 80 wire powered by a 3s LiPo battery as the heating element, but quickly realized that it was too thick
and would interfere with the body panels. Eventually, I settled on 0.2x4mm flat nichrome as a thinner alternative. 

Since nichrome wire isn't able to be soldered, I used bare copper wire to bind the main copper wire and the nichrome together. 
![20220109_113626](https://user-images.githubusercontent.com/95006894/148979768-49bf3109-6b16-4333-894e-0ac2bf55e757.jpg)

I then folded the nichrome over to prevent the copper wire from slipping out and continued wrapping the copper wire.
![20220109_114028](https://user-images.githubusercontent.com/95006894/148979989-b34fa3ad-3ce7-46a7-a8b0-a293e0d211ef.jpg)

Finally, I added solder to secure the copper in place.
![20220109_115102](https://user-images.githubusercontent.com/95006894/148980118-7564e84b-5e63-4217-a47a-c3b12cc31a81.jpg)

To install the nichrome strips on the unicycle, I first cleaned the battery packs with isopropyl alcohol, and then added double-sided thermal tape.
I then laid the bent nichrome strip down on the adhesive tape. 
![20220109_184247](https://user-images.githubusercontent.com/95006894/148980709-e3649d3f-bcad-4e96-8fcc-10d130e61e61.jpg)

To insulate the other side of the wire, I covered everything in a layer of Kapton tape.
![20220109_185828](https://user-images.githubusercontent.com/95006894/148980928-3803351b-561e-42df-b836-93ab2f669dd5.jpg)

## Electronics

The electronics on this heating system are used for monitoring and do not have direct control over the heating process. 

Using Arduino on a Seeeduino Xiao, this electronics module features a temperature probe, an OLED screen, and a buzzer to let the
user know when the batteries are done heating. 
![20220107_123814](https://user-images.githubusercontent.com/95006894/148981875-2db84fa5-b33e-4a09-9f80-d7e725e5423b.jpg)

The information is displayed neatly on the side of the unicycle
![20220102_133023](https://user-images.githubusercontent.com/95006894/148982234-1c8bb405-64df-4442-b807-23c766a9b50e.jpg)

When plugged into a 3s LiPo, the heating system uses around 60 watts, allowing it to heat up 10℃ in less than 5 minutes

[return to main page](index.md)
