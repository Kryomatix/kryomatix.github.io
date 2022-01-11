# Keyboard 3.0
(legacy)

This was my first time building a keyboard, so not everything turned out as expected

The original V1 concept for this keyboard was a unibody design with an ergodox layout and a custom tilt
![20210318_150203](https://user-images.githubusercontent.com/95006894/149004340-c6e6d537-5152-417a-b3b9-ba2c72a1db26.jpg)

Prototype V2.0 featured an altered layout derived from the ergodox but modified to accommodate ortholinear keys, as well as a more ergonomic thumb position when gaming with WASD
- V2.0 added independently movable halves connected by a TRRS cable
- V2.0 also used an ATMEGA32U4 in a QFN package to fit in the space by the thumb keys
- The design also features rotary encoders in the corners of the keyboard

![20210405_092546](https://user-images.githubusercontent.com/95006894/149004612-d8ee4036-f415-40ab-886b-3807106e41a3.jpg)

Version 3.0 made significant changes to make the PCB easier to design.
- The USB-C port was moved to the outside corners to accommodate an extra key in the top inside corners
- V3.0 also switches back to the ATMEGA32U4 in a TQFP package to allow trace routing directly under the chip
- This version also switched to using a custom magnetic connector, but ultimately the magnets ended up being too weak
- All PCB design was done in KICAD

![image](https://user-images.githubusercontent.com/95006894/149005883-685d2841-5d0b-4c37-a71b-f78e8181d3c9.png)

PCBs were manufactured by JLCPCB. The left and right were combined using break-away tabs to save on manufacturing and stencil costs. 
![image](https://user-images.githubusercontent.com/95006894/149006092-0e267311-ef16-4fd6-b158-2ccb960034ac.png)

After using a saw and sandpaper to separate the left and right boards, I made a jig out of the extra boards to hold it under the stencil
![image](https://user-images.githubusercontent.com/95006894/149006561-09d0a7b1-44c2-442e-a10a-be2f7841a6c1.png)

Solder paste after the stencil was removed
![image](https://user-images.githubusercontent.com/95006894/149006853-01902f83-8737-429f-b91f-31fa5119f6ae.png)

I placed all of the components using tweezers
![image](https://user-images.githubusercontent.com/95006894/149006930-5b37e049-619b-4c09-ab49-9e94e3df0c3d.png)

I reflowed the solder using a cheap hot plate
![image](https://user-images.githubusercontent.com/95006894/149007201-7ce9ff0b-c394-40c4-89dd-6a1f5bd0fe35.png)

![image](https://user-images.githubusercontent.com/95006894/149007321-1ffdb203-1eee-48d7-b28f-d417fe73611f.png)

This keyboard used SK6812mini LEDs since SK6812min-e LEDs were out of stock at the time. 
Soldering in the LEDs in reversed orientation was difficult, and lead to many of the LEDs overheating and failing. 
I strongly recommend against trying this. (Left has no LEDs, right has LEDs soldered)
![image](https://user-images.githubusercontent.com/95006894/149007808-1587fd13-e6b0-4e51-9aa4-89ae39e9ef2e.png)

This keyboard used an ABS 3d-printed frame and laser cut acrylic bottom plate
![image](https://user-images.githubusercontent.com/95006894/149008154-f216602b-cde0-49cb-95ae-2aef109699d0.png)

Internal wiring and sound dampening foam
![image](https://user-images.githubusercontent.com/95006894/149008198-c5344646-c7ff-4ab5-8379-dd2a94075241.png)

I used Matt30 Mt3 Susuwatari keycaps and Zealio V2 switches on this build
![image](https://user-images.githubusercontent.com/95006894/149009778-705a0988-b9b5-480d-8f23-86df73a2e3cb.png)

![image](https://user-images.githubusercontent.com/95006894/149009811-e98b0008-27c7-4655-bc50-652102ac533f.png)

The software for this keyboard was coded using Arduino. In hindsight, I should have used the QMK toolkit or a similar library. 

[return to main page](index.md)
