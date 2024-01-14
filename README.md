# simple-touch-soundscpr
A plugdata patch as a base for my Soundscpr project. Daisy seed + MPR121 on Synthux Simple Touch


## TLDR;

- Install Plugdata
- Choose the compile option in the menu
- Download the toolchain
- Edit `plugdata\Toolchain\usr\bin\Heavy\json2daisy\resources\component_defs.json`
    - delete the part referring to the pins in the “map_init” **line 558**, leave the line “pin” as is:
    - delete: `{name}_config.scl = som.GetPin({pin_scl});\n    {name}_config.sda = som.GetPin({pin_sda});\n`
- Create a custom json file with all the components connected to the Daisy ([download below](https://www.notion.so/Plugdata-and-daisy-seed-mpr121-touch-sensor-41be6a24dc0b4dc4bdd2fffbe4763dee?pvs=21))
- Start patching
    - Use this block in the patch `r mpr121_driver_ch0 @hv_param`
    - to refer to touch pads 0 - 11 change `_ch0` , `_ch…` up to `_ch11`
    - To use the knobs and faders and switch use the names you’ve added in the custom json file
        - e.g. `r toggle1left @hv_param` or `r knob1@hv_param`
- Go to the compiler menu and pick the right options and flash!
    - note I’m using a Custom Linker, but you should check first if the small, big or huge modes work for you, more [on the use of memory below](https://www.notion.so/Plugdata-and-daisy-seed-mpr121-touch-sensor-41be6a24dc0b4dc4bdd2fffbe4763dee?pvs=21).

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/183357c7-1e01-4c65-a869-200d788b649c/c62f8951-c1d5-4924-bf65-4cc3dad890c4/Untitled.png)

---

# Intro - about this page
