Ender3V2Klipper
Klipper Config For ender 3 V2

17.4.2022
changer mainboard to 4.2.7! now printer is on this setup. old files renamed!

Fluidd Klipper for ender3 v2

Filament runout sensor whit encoder BIGTREETECH BTT SFS V1.0 Smart Filament Sensor

For SuperSlicer (Klipper Support)

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
