# TKB mini 7x3
A 3d-printed keyboard based on the [TKB mini](https://github.com/Bastardkb/TBK-Mini/)

![image](https://user-images.githubusercontent.com/95006894/148988769-16dda837-1a53-4945-a170-a8af8a00de50.png)

This design adds an extra column of keys for the index finger, as well as custom electronics.
This keyboard uses individual PCBs to optimize costs and prototyping time. 
Each half runs on an Adafruit feather rp2040 using Circuit Python and the [KMK library](https://github.com/KMKfw/kmk_firmware)

PCBs were designed in KICAD to have hot-swap sockets and SK6812mini-e LEDs, while also being as small and cheap as possible.
![image](https://user-images.githubusercontent.com/95006894/148989108-bdbb451c-9263-417a-af24-52daab705306.png)

The 48 individual PCBs were manufactured by OSH Park
![20211126_174420](https://user-images.githubusercontent.com/95006894/148989272-a3c8826e-3007-43d4-89b5-a0abe943982c.jpg)

I used a PCB stencil from OSH Stencils to apply the solder paste
![20211227_144318](https://user-images.githubusercontent.com/95006894/148989635-a17fbe24-7579-4025-99f0-67a1a476e7b3.jpg)

PCB component placement and hot-plate soldering
![20211128_123214](https://user-images.githubusercontent.com/95006894/148989712-83e8b8d3-4964-42ad-bc37-11cd230571ee.jpg)

The PCB columns were soldered together using 2.54mm header pins that were trimmed down in length
![20211130_132931](https://user-images.githubusercontent.com/95006894/148990070-416cd75c-8802-47ed-a834-467573ff9c86.jpg)

Once soldered, I removed the entire electronics assembly and moved it to a new frame printed out of matte gray PLA
![20211229_213022](https://user-images.githubusercontent.com/95006894/148990815-7f7ce1fe-d370-430b-879c-98bc33c9677c.jpg)

I used ZealPC Zealio V2 switches
![20211230_202703](https://user-images.githubusercontent.com/95006894/148990874-9f771136-0c0c-422d-b5c7-7a8bd41bc45f.jpg)

![20220103_094709](https://user-images.githubusercontent.com/95006894/148991087-d73b7433-e0e7-4090-98b3-93344b4b6e77.jpg)

The keycaps are MT3 Cyber keycaps with dampening O-rings underneath
![20220103_094612](https://user-images.githubusercontent.com/95006894/148991161-a7263157-93ff-42a6-9798-aafd313f3ed6.jpg)
![20220103_094826](https://user-images.githubusercontent.com/95006894/148991259-8947aa99-93db-402f-ab51-40c5309c80c4.jpg)

The code is relatively simple
```
print("Starting left side....")
import board

from kb import KMKKeyboard
from kmk.keys import KC
from kmk.modules.layers import Layers
from kmk.extensions.media_keys import MediaKeys
from kmk.modules.mouse_keys import MouseKeys
from kmk.modules.split import Split, SplitSide

import neopixel
from kmk.extensions.RGB import RGB
from kmk.extensions.RGB import AnimationModes

keyboard = KMKKeyboard()

rgb = RGB(pixel_pin=keyboard.rgb_pixel_pin, num_pixels=keyboard.rgb_num_pixels, animation_mode=AnimationModes.RAINBOW, val_default=50, animation_speed=0.25)

# TODO Comment one of these on each side
split_side = SplitSide.LEFT
#split_side = SplitSide.RIGHT
split = Split(split_side=split_side,split_flip=False)

layers_ext = Layers()
media_keys_ext = MediaKeys()
mouse_keys = MouseKeys()

keyboard.modules = [layers_ext, split, mouse_keys]
keyboard.extensions = [rgb, media_keys_ext]

#Key names
NUMS = KC.MO(1)
FN = KC.MO(2)
XXXX = KC.NO
____ = KC.TRNS

CLIPBRD = KC.LGUI(KC.V)
ESC = KC.LT(3, KC.ESC)
DSKTPL = KC.LCTRL(KC.LGUI(KC.LEFT))

#--------------------------------------Left Side------------------------------------------------<<<<===>>>>---------------------------------------Right Side--------------------------------------------
keyboard.keymap = [
    #Qwerty layer
    [KC.TAB,    KC.Q,       KC.W,       KC.E,       KC.R,       KC.T,       KC.BKSP,    NUMS,               KC.ENTER,   KC.B,       KC.Y,       KC.U,       KC.I,       KC.O,       KC.P,       KC.DEL,
    ESC,        KC.A,       KC.S,       KC.D,       KC.F,       KC.G,       DSKTPL,     KC.SPACE,           NUMS,       KC.BKSP,    KC.H,       KC.J,       KC.K,       KC.L,       KC.SCLN,    KC.QUOTE,
    KC.LSHIFT,  KC.Z,       KC.X,       KC.C,       KC.V,       KC.B,       KC.ENTER,   KC.LCTRL,           FN,         KC.B,       KC.N,       KC.M,       KC.COMMA,   KC.DOT,     KC.SLASH,   KC.RSHIFT,],

    #Numbers and symbols
    [XXXX,      KC.EXLM,    KC.AT,      KC.HASH,    KC.DLR,     KC.PERC,    ____,       XXXX,               XXXX,       XXXX,       KC.CIRC,    KC.AMPR,    KC.ASTR,    KC.LPRN,    KC.RPRN,    KC.PLUS,
    DSKTPL,     KC.N1,      KC.N2,      KC.N3,      KC.N4,      KC.N5,      KC.N0,      ____,               XXXX,       ____,       KC.N6,      KC.N7,      KC.N8,      KC.N9,      KC.N0,      KC.EQUAL,
    ____,       KC.GRV,     KC.TILD,    KC.MINS,    KC.UNDS,    KC.PIPE,    KC.BSLS,    XXXX,               XXXX,       XXXX,       KC.LBRC,    KC.RBRC,    KC.LCBR,    KC.RCBR,    KC.BSLS,    ____,],

    #Function keys
    [XXXX,      KC.F1,      KC.F2,      KC.F3,      KC.F4,      KC.F5,      KC.F11,     XXXX,               XXXX,       KC.F12,     KC.F6,      KC.F7,      KC.F8,      KC.F9,      KC.F10,     XXXX,
    XXXX,       KC.LGUI,    CLIPBRD,    KC.VOLD,    KC.VOLU,    KC.MUTE,    KC.MPLY,    KC.CAPS,            XXXX,       KC.RGB_VAI, KC.LEFT,    KC.DOWN,    KC.UP,      KC.RIGHT,   KC.HOME,    KC.END,
    XXXX,       XXXX,       XXXX,       XXXX,       XXXX,       XXXX,       XXXX,       XXXX,               XXXX,       KC.RGB_VAD, KC.RGB_TOG, KC.PGDN,    KC.PGUP,    KC.DOT,     KC.SLASH,   XXXX,],


    [____,      ____,       ____,       KC.UP,      KC.MW_UP,   ____,       ____,       ____,               ____,       ____,       ____,       ____,       ____,       ____,       ____,       ____,
    ____,       ____,       KC.LEFT,    KC.DOWN,    KC.RIGHT,   ____,       ____,       ____,               ____,       ____,       ____,       ____,       ____,       ____,       ____,       ____,
    ____,       ____,       ____,       ____,       KC.MW_DN,   ____,       ____,       ____,               ____,       ____,       ____,       ____,       ____,       ____,       ____,       ____,],
]


if __name__ == '__main__':
    keyboard.go()

```

Here is the configuration file kb.py
```
#Left side
import board

from kmk.kmk_keyboard import KMKKeyboard as _KMKKeyboard
from kmk.matrix import DiodeOrientation
from kmk.matrix import intify_coordinate as ic


class KMKKeyboard(_KMKKeyboard):
    row_pins = (board.A2,board.A3,board.D24,)
    col_pins = (board.A1,board.A0,board.D5,board.D6,board.D9,board.D10,board.D11,board.D12,)
    diode_orientation = DiodeOrientation.COL2ROW
    rgb_pixel_pin = board.D13
    rgb_num_pixels = 28
    data_pin2 = board.TX
    data_pin = board.RX

    coord_mapping = []
    coord_mapping.extend(ic(0, x) for x in range(16))
    coord_mapping.extend(ic(1, x) for x in range(16))
    coord_mapping.extend(ic(2, x) for x in range(16))

```

The result is a keymap that looks something like this:
![image](https://user-images.githubusercontent.com/95006894/148992526-e02e26c1-b640-4a4c-8fa3-80d7a7c7d9da.png)

[return to main page](index.md)
