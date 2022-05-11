# Backpack Light V1.0
This project is a very early prototype of my concept for a backpack-mounted light. I had a deadline of 2 weeks to complete the project, so I ended up choosing
choosing components that were guaranteed to work, including the Attiny85 and 5050 RGBW neopixels. What I ended up with is a light that attaches magnetically and is
powered externally with USB-C. I carry a USB power bank in my backpack anyways, so powering the light externally isn't a big deal.
![PackLight_exploded](https://user-images.githubusercontent.com/95006894/167876380-a33b358f-1aa4-444b-88d1-8ef005931328.PNG)
The assembly features strong neodymium magnets to hold the light in place. There is a backplate section which goes inside the backpack with magnets
for the light to stick to. 
The 3D printed housing was modeled with Fusion 360, and the circuit board and schematic were created with KiCad.
![image](https://user-images.githubusercontent.com/95006894/167881981-2724794b-a5ed-461a-87e2-7d2695baba29.png)
![image](https://user-images.githubusercontent.com/95006894/167881709-26db6cff-e7f5-4346-b5cf-8f3c1506022c.png)

I soldered the pins of the USB-C connector individually using the T15-JS02 bent tip on my Hakko soldering station. The rest of the components were soldered with
a medium sized chisel tip. 
![20220314_204021 1](https://user-images.githubusercontent.com/95006894/167877013-e60de3a6-6b06-426a-85d3-0af8a00c40a0.jpg)
![20220314_205424](https://user-images.githubusercontent.com/95006894/167878229-4327e5b3-ac99-41be-b8b9-483c1189ed8d.jpg)
![20220511_105556](https://user-images.githubusercontent.com/95006894/167881250-9adc304d-1f84-4b09-9206-259efee533ab.jpg)

Due to a difference in labeling between the schematic symbol and datasheet, I accidentally connected the mode button to the reset pin. 
This prevented any code from executing, as the chip was in a constant state of resetting. Fortunately, my hot air station came to the rescue and I removed the Attiny85
so I could cut the trace underneath and run a jumper wire to an unused pin.
![20220314_215355](https://user-images.githubusercontent.com/95006894/167877766-8631147e-9ca8-4e13-867d-62f597a231fb.jpg)
![20220314_220122](https://user-images.githubusercontent.com/95006894/167877815-8b47940d-8122-4f1c-971c-1b771b208d80.jpg)

The chip covers up the jumper wire, so everything looks normal except for the slightly angled chip.
![20220314_224141](https://user-images.githubusercontent.com/95006894/167877899-a74ec0c0-02f5-4dfa-bb5c-dde8ec68bdce.jpg)

![20220310_142325](https://user-images.githubusercontent.com/95006894/167877599-75cf017e-54b0-4b8f-b60f-7f67a6280f7c.jpg)
No glue needed -- everything is held together with some well-measured 3D printed tabs
![20220310_144117](https://user-images.githubusercontent.com/95006894/167878058-88cd24ef-797d-441c-96a1-79ad6a3830f2.jpg)
![20220310_144138](https://user-images.githubusercontent.com/95006894/167878335-dc7558fa-e231-4c5d-9396-74d9d526da0c.jpg)
This version is just a very early prototype. I'm currently working on a version which uses proper, bright red LEDs that
will be bright enough for daytime use. 

[return to main page](index.md)
