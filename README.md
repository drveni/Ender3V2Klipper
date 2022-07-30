
Ender3V2Klipper
Klipper Config For ender 3 V2

changed mainboard to 4.2.7! now printer is on this setup. old files renamed!

Fluidd Klipper for ender3 v2

Filament runout sensor whit encoder BIGTREETECH BTT SFS V1.0 Smart Filament Sensor
----
added new size calibration od stock motors X Y ... for superslicer need to change Inner X Y Compesation 0.115 for correct size of holes.
For SuperSlicer (Klipper Support)

NEW NEW NEW NEW NEW  FROM 6.6.2022 !!!

for https://gist.github.com/ChipCE/95fdbd3c2f3a064397f9610f915f7d02 printed part, het mesh only for printed pard/object on plate. faster print and mesh.

new gcode for start/ end SuperSLicer
_________

;START
SKEW_PROFILE LOAD=my_skew_profile

M104 S160
M140 S[first_layer_bed_temperature] ; start heating bed so it heats up at same time as nozzle
M190 S[first_layer_bed_temperature] ; wait for bed to hit temperature

;G29
;BED_MESH_PROFILE LOAD=default

BED_MESH_CALIBRATE AREA_START={first_layer_print_min[0]},{first_layer_print_min[1]} AREA_END={first_layer_print_max[0]},{first_layer_print_max[1]}

G90
G1 X244 Y225 Z10.8 F4000
G1 X244 Y0 Z0.8 F4000

M109 S[first_layer_temperature] ; wait for nozzle to heat up

G92 E0
;pocne grijati filament
G90
G1 X244 Y41 Z0.8 F4000
G1 X238 Y41 Z0.8 F4000
G1 X238 Y10 Z0.8 F4000

;i drugi puta ocisti
G1 X243 Y2 Z0.8 F4000
G1 X243 Y41 Z0.8 F4000
G1 X240 Y41 Z0.8 F4000
G1 X240 Y10 Z0.8 F4000
G1 X244 Y41 Z10 F4000

___________

;END GCODE

G91 ; Set coordinates to relative
G1 F1800 E-3 ; Retract filament 3 mm to prevent oozing
G1 F3000 Z20 ; raise head
G90 ; Set coordinates to absolute
G1 X10 Y200 F5000.0 ; Move to start position
M84

BED_MESH_PROFILE REMOVE=default

M106 S0 ;Turn-off fan
M104 S0 ;Turn-off hotend
M140 S0 ;Turn-off bed


SET_SKEW CLEAR=1

_____________





OLD OLD OLD OLD till 6.6.2022 !!!
Start G-code:

_________
M140 S[first_layer_bed_temperature] ; start heating bed so it heats up at same time as nozzle
M109 S[first_layer_temperature] ; wait for nozzle to heat up
M190 S[first_layer_bed_temperature] ; wait for bed to hit temperature
G29
BED_MESH_PROFILE_LOAD=default
_________



End G-code
_________
G91 ; Set coordinates to relative
G1 F1800 E-3 ; Retract filament 3 mm to prevent oozing
G1 F3000 Z20 ; raise head
G90 ; Set coordinates to absolute
G1 X10 Y200 F5000.0 ; Move to start position
M106 S0
M84

BED_MESH_PROFILE REMOVE=default
FIRMWARE_RESTART
_________


For PrusaSlicer/Cura
Start G-code:
_________
;za klipper
G29
BED_MESH_PROFILE LOAD=default
_________



End G-code
_________
G91 ; Set coordinates to relative
G1 F1800 E-3 ; Retract filament 3 mm to prevent oozing
G1 F3000 Z20 ; raise head
G90 ; Set coordinates to absolute
G1 X10 Y200 F5000.0 ; Move to start position
M106 S0
M84

BED_MESH_PROFILE REMOVE=default
FIRMWARE_RESTART
_________
