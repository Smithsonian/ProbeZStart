# ProbeZStart
GMT ProbeZ Prototype Startup

Control the Parker XY stage w/ TwinCAT & OPC-UA

## Drive Parameters ##
Drives set up with 5mm drive pitch, maximum travel of +/- 75mm
Lag monitor set to disable drive with error if tracking error exceeds 0.1mm
Other motor and drive parameters default for Beckhoff AM8132-0JH0 motor + EL7221 drive
Maximum allowed velocity is 93.6 mm/s

X-axis encoder set for -25.4mm offset to center the stage
Y-axis to be calibrated

## OPC-UA ##
OPC-UA server connectable at opc.tcp://192.168.1.235:4840

The following OPC-UA variables are writable:
* inputEnableDrive (BOOL) - TRUE to enable drive; default FALSE
* inputResetDrive (BOOL) - TRUE to reset drive (after an error); default FALSE
* inputXPos (REAL) - target X axis position in mm; default 0
* inputYPos (REAL) - target Y axis position in mm; default 0
* inputXVel (REAL) - target X axis velocity in mm/s; default 10
* inputYVel (REAL) - target Y axis velocity in mm/s; default 10

The following OPC-UA variables are read-only:
* XPos - X axis position
* YPos - Y axis position
* XVel - X axis velocity
* YVel - Y axis velocity
* XLag - X axis tracking error
* XLagMax - maximum X axis tracking error, absolute value
* YLag - Y axis tracking error
* YLagMax - maximum Y axis tracking error, absolute value
* XError - last error code on X axis drive
* YError - last error code on Y axis drive
* state - system state:
  - 0 off
  - 1 reset
  - 2 ready
  - 3 moving
  - 9 error
