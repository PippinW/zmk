# Building ZMK for the Rebound 4-3

Some general notes/commands for building the Montsinger Rebound from the assembly documentation.

## Layouts Using 1u and/or 2u Thumb Keys

If you built your Rebound with 2u keys on the bottom row, key-presses of the inside/second column key on the bottom row will be redundant.

If your Rebound is built with hotswap support, you may wish to assign key-press behaviours to all four 1u keys to allow switching between 1u and 2u layouts without having to rebuild and reflash the firmware.

As an example template of each layout, the default keymap uses a uniform 1u layout on the left portion of the pcb, and a 2u layout on the right portion with the redundant key labelled as "optional" and assigned with key-press "&none".

```
    keymap {
        compatible = "zmk,keymap";

        default_layer {
// -------------------------------------------------------------------------------------
// |   Q   |   W   |   E   |    R   |  T  |  1   |                |  1  |    Y   |    U   |   I   |   O   |   P   |
// | CMD/A | ALT/S | CTL/D | SHFT/F |  G  |  2   |    | TAB  |    |  2  |    H   | SHFT/J | CTL/K | ALT/L | CMD/' |
// |   Z   |   X   |   C   |    V   |  B  |  3   |    | RET  |    |  3  |    N   |    M   |   ,   |   .   |   /   |
// | CTRL  |  ALT  |  CMD  |  SHFT  | DEL | BSPC |    | CAPS |    | SPC |optional|  CMD   |  ALT  |  CTRL |   ;   |
//                         					  
		bindings = <
   &kp Q       &kp W      &kp E       &kp R       &kp T   &mo 1               &mo 1     &kp Y     &kp U       &kp I       &kp O      &kp P
   &hm LGUI A  &hm LALT S &hm LCTRL D &hm LSHFT F &kp G   &mo 2     &kp TAB   &mo 2     &kp H     &hm RSHFT J &hm RCTRL K &hm RALT L &hm RGUI SQT
   &kp Z       &kp X      &kp C       &kp V       &kp B   &mo 3     &kp RET   &mo 3     &kp N     &kp M       &kp COMMA   &kp DOT    &kp FSLH  
   &kp LCTRL   &kp LALT   &kp LGUI    &kp LSHFT   &kp DEL &kp BSPC  &kp CAPS  &kp SPACE &none     &kp RGUI    &kp RALT    &kp RCTRL  &kp SEMI                   
                        >;

			sensor-bindings = <&inc_dec_kp DEL BSPC>;
                };
```

## Encoder Notes

If you built your Rebound without encoders, you will need to change the following in your local Rebound config or add them to the end of the file.

```
CONFIG_EC11=y
CONFIG_EC11_TRIGGER_GLOBAL_THREAD=y
```

