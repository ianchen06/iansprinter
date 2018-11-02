# start g-code
G21 ;metric values
G90 ;absolute positioning
M82 ;set extruder to absolute mode
M107 ;start with the fan off
G28 X0 Y0 ;move X/Y to min endstops
G0 X110 Y60 F3600;
G28 Z0 ;move Z to min endstops
G0 X0 Y15 F9000 ; Go to front
G0 Z0.15 ; Drop to bed
G92 E0 ; zero the extruded length
G1 X40 E30 F500 ; Extrude 25mm of filament in a 4cm line
G92 E0 ; zero the extruded length
G1 E-1 F500 ; Retract a little
G1 X80 F4000 ; Quickly wipe away from the filament line
G1 Z0.3 ; Raise and begin printing.

# end g-code
M104 S0 ;extruder heater off
M140 S0 ;heated bed heater off (if you have it)
G91 ;relative positioning
G1 E-1 F300  ;retract the filament a bit before lifting the nozzle, to release some of the pressure
G1 Z+0.5 E-5 X-20 Y-20 F4000 ;move Z up a bit and retract filament even more

G90 ;absolute positioning
G0 X0 Y200 F9000 ;move X/Y to min endstops, so the head is out of the way
M84 ;steppers off
G90 ;absolute positioning
M82 ;absolute extrusion mode

# Extruder start g-code
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;↑↑↑ YOUR CODE ↑↑↑

M83                ;extruder relative positioning
G90                ;absolute positioning
G1 X38 Y162 F3600  ;move ON the waste block
G91                ;relative positioning
G1 Z-2 F3600       ;touch the waste block
G1 E150 F5000     ;undo storage position
G1 E6 F500         ;extrude another 5mm
G1 E8 F200         ;extrude last 10 - 3 mm to finish safe undo storage
G92 E0             ;zero the extruded length again
G90                ;absolute positioning
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

# Extruder end g-code
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
M83                       ;extruder relative positioning
G91                       ;relative positioning
G1 E-7 F5000             ;stage 1 of 3 stage retraction
G1 X+0.5 Y+0.5 F5000     ;move/clean nozzle little bit
G1 Z+2 F5000             ;move up far from object
G1 E4 F5000              ;stage 2 of 3 stage retraction
G1 E-155 F6000           ;stage 3, this keeps from producing "hair"
G92 E0                    ;zero the extruded length again
G90                       ;absolute positioning

;↓↓↓ YOUR CODE ↓↓↓
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
