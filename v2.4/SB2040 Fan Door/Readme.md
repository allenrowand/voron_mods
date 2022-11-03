A modification of the Stealthburner PCB cover door to add a cooling fan. There are two versions: one for a 20mm x 10mm fan, the other for a 30mm x 10mm fan. Both versions use a 5v fan.

Pre-fan, the SB2040 went over 90ºC printing this door. With the 20mm fan it maxed at 68ºC printing the same file.

The fan should be oriented to blow on the board, you'll need to remove the wires from the fan's strain relief.

20mm x 10mm:

![image](https://github.com/allenrowand/voron_mods/blob/main/v2.4/SB2040%20Fan%20Door/images/image_01.jpg)
![image](https://github.com/allenrowand/voron_mods/blob/main/v2.4/SB2040%20Fan%20Door/images/image_02.jpg)

30mm x 10mm:

![image](https://github.com/allenrowand/voron_mods/blob/main/v2.4/SB2040%20Fan%20Door/images/image_03.jpg)
![image](https://github.com/allenrowand/voron_mods/blob/main/v2.4/SB2040%20Fan%20Door/images/image_04.jpg)



Thanks to garbqgebag V2.1135 V0.610 on the VoronDesign Discord for early testing.

Usage:
- Solder the fan to 5v and AGND pads at the top of the SB2040
- For automatic control, add this to your printer.cfg:
    
    ```
    [controller_fan controller_fan]
    ##  SB2040 cooling fan - SB2040 FAN2
    pin: SB2040: gpio15
    kick_start_time: 0.1
    heater: heater_bed
    fan_speed: 1.0
    ```

The fan will automatically switch on. For the 30mm version you can probably run the fan at .75 speed.

- For GCODE control add this to your printer.cfg:
    ```
    [fan_generic SB2040]
    ##  SB2040 cooling fan - SB2040 FAN2
    pin: SB2040: gpio15
    max_power: 1.0
    kick_start_time: 0.1
    ```

Use SET_FAN_SPEED FAN=SB2040 SPEED=x.x in your macros to control the fan.