---
title: Adding the Sovol SV07+ to Cura
date: 2024-02-23
authors:
  - ryan_jones
---

# How to add the Sovol SV06-Plus 3D Printer Profile to Cura Slicing Software

![](https://fundedyouth.org/wp-content/uploads/2024/02/add-sovol-sv07-plus-to-cura-banner.webp){width="500", loading-lazy}

Sovol recently released their SV07-Plus 3D Printer and it’s faster than the SV06-Plus but it’s using the Bed-Sling design. What does this mean? Basically, you need to do some manual tuning and preconfigured leveling before printing. <!-- more -->

The chatter on the web between the SV06-Plus and SV07-Plus is a bit back and forth. Personally, when it comes to the setup process, I prefer the SV06-Plus. It was just easier. Pros and cons, the SV07 and SV07-Plus come with WiFi and the Klipper software which is loved by many. I was fine with using Octoprint on a Raspberry Pi and I didn’t care much for the extra time it took to level the SV07-Plus. The 6 had auto-leveling and it was easy.

More tests need to be run before deciding on the better option. I still need try and install Klipper on the SV06-Plus using a Pi but that will be at a later date.

For now, I’ll provide the basic configuration process for adding the SV07-Plus to the Latest Cura Software.

!!! info "Sovol's Cura Slicing Software"

    - Sovol provides thier own version of the Cura slicing software but it is limited to version 1.5 and it's only available on the Windows Operating System.
    - Instead this tutorial shows you how to add a custom profile to latest version of the Sovol Slicing software.


## SV07 Plus Printer Config for Cura

1) Open the **Cura slicing** software

2) Now, either select Add printer or click on Manage printers ==(For this tutorial we will select: **Manage Printers**)==

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*8YhUVCNC__NVa2w-dJ6yxg.png)

3) In the top-right of the new window, select: **Add New**

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*z0opUqg0IjcIFW-BcieRPQ.gif)

4) Then select: **Non UltiMaker printer**

5) In the **Add printer** window, expand the **Add a non-networked printer**

6) Scroll-briefly down to **Custom** and select: vCustom FFF printer**

7) Name the printer (ex): **Sovol SV07-Plus 0.04mm**

!!! info "The size at the end is for personal use. Tells you the extruder head size"

8) Set the following **Printer Settings**

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*aH1ChocKpfAONMVtCXpQjA.png)

9) Add the following Printer **G-Code**

!!! tip "It is similar to the SV06-Plus but there are a couple of changes"

#### Start G-code

```gcode
G28 ;Home

G92 E0 ;Reset Extruder
G1 Z2.0 F3000 ;Move Z Axis up
G1 X10.1 Y20 Z0.28 F5000.0 ;Move to start position
G1 X10.1 Y200.0 Z0.28 F1500.0 E15 ;Draw the first line
G1 X10.4 Y200.0 Z0.28 F5000.0 ;Move to side a little
G1 X10.4 Y20 Z0.28 F1500.0 E30 ;Draw the second line
G92 E0 ;Reset Extruder
G1 Z2.0 F3000 ;Move Z Axis up
```

#### End G-code

```gcode
G91 ;Relative positioning
G1 E-2 F2700 ;Retract a bit
G1 E-2 Z0.2 F2400 ;Retract and raise Z
G1 Z1 ;Raise Z more
G90 ;Absolute positionning

G1 X0 Y200 ;Present print
M106 S0 ;Turn-off fan
M104 S0 ;Turn-off hotend
M140 S0 ;Turn-off bed

M84 X Y E ;Disable all steppers but Z
```

10) Set the following **Extruder 1 Settings**

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*AQuBvDQgxwPV1_0QkIZwCA.png)

```py
# Nozzle Settings

"Nozzle size": 0.4 mm
"Compatible material diameter": 1.75 mm
"Nozzle offset X": 0.0 mm
"Nozzle offset Y": 0.0 mm
"Cooling Fan Number": 0
```

> That's it! or that's what I copied over from the Sovol Cura Software Configuration.