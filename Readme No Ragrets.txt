Release AutoBot v3.3

Done:


- Laser readings reformatted with last 10 timestamps

To Do:

- State machine logic
- Communications heartbeat on HQ JAIDEV
- Battery % checker (integrate power consumption and log it) JAIDEV
- Pod health with min max next to it 
- Integrate accelerometer data into pod code & HQ main JOHN
- Read distance, velocity, and acceleration from lasers BEN
- Logic to always count with wheel lasers BEN
- Packaging UDP data JOHN D
- Countdown clock to braking, adjustable during run. Start after 2 tape counts
- HQ UI for competition

- Calibration for ToFs BEN
- Detect emag engagement through dip in current
- Stream data to HQ

Jaidev_v2 Edits
- Move Position/Velocity/Accel telementry out of non-critical section. Changing to always send
- Added selector for which laser calculates velocity/accel. Selectors on HQ main
- surfaced stripe distance and prior lows on HQ main
- removed FP controls from high speed timed loop
- added UDP sender and integrated John D's UDP packet creation
-- UDP initialization not working in deployed code. BYpassing error from UDP initalize works fine.
-Need to reolve pod state command and status


Jaidev_v3 Edits
- Added state machine logic
- Validated state machine in static tests on pod
!! Still TODO: brake settings in Brake phase, Pod health inputs in state machine, 
keep/remove ignore rip cord, hard limits for stripe and timer count

- Added Operator Interface on HQMain
- Added ping logic in HQMain to ensure connectivity
- "Waiting for connection" logic to HQMain so HQMain can be started at any time without waiting on myRIO

Bug Fixes:
- wrt. v1: timer calculation - divide by 1000 instead of multiply [fixed]
- Fixed analog pressure scaling and changed terminology on James's request Tank, Utility, Brake, Levitation

Open Questions:
!!velocity calculations are slow, is this a problem?
!!laser selection logic - right = 1, left = 2?
!!brake states are flexible - is that OK?

Jaidev_v7 Edits
- Changed OR condition for ToFs in Pod Health to AND - ALL ToFs need to work right for Pod Health Green
- Timer start when velocity is greater than 5m/s
- Timer starts when pushing is detected
- Changed velocity input from NSV to local var in ready state to evaluate for pushing
- Commented out redundant rip cord check in pod-stop state
- Added calculated position, velocity and accel to critical telemetry
- Vars duplicated in Critical telemetry (like velocity, accel, position) made non NC (pu them in non-crit case and removed attached indicators on HQMain, except in Telemetry tab)
- Reading all vars on Operator tab and always visible screen from critical telemetry
- Force stripe limit and timer limit values in order and then change state command to ready (clicking ready in phase control will not yield same effect)
- Added "Add to timer" "Add to stripe" inputs on HQMain and event cases

!! still left - for NSVs that take safe default values from HQMain (everything on configuration tab, stripe limit, timer limit), it seems wrong to initialize in pod code. What should we do?
!! Battery monitor
!!fault logic
!! reset count in ready- take it out? or write false somwhere else. Or leave as is cos it works?


Help:

- Syncing timestamp to myRIO from HQ

- Set up new router

- Wire everything in

- Stopping all the loops

- UDP communications

- Lasers
  
- Moving down to FPGA

- What is our team ID?



NOT doing:

- Live video stream with USB endoscope cam


- Replay Run UI




- Write Data to jumpdrive
- Logging

