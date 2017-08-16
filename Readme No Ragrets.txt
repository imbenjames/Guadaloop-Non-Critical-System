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

Jaidev_v1 Edits
- Move Position/Velocity/Accel telementry out of non-critical section. Changing to always send
- Added selector for which laser calculates velocity/accel. Selectors on HQ main
- surfaced stripe distance and prior lows on HQ main
- removed FP controls from high speed timed loop
- added UDP sender and integrated John D's UDP packet creation
-- UDP initialization not working in deployed code. BYpassing error from UDP initalize works fine.
-Need to reolve pod state command and status


Jaidev_v2 Edits
- Added state machine logic
- Validated state machine in static tests on pod
!! Still TODO: brake settings in Brake phase, Pod health inputs in state machine, 
keep/remove ignore rip cord, hard limits for stripe and timer count

- Added Operator Interface on HQMain
- Added ping logic in HQMain to ensure connectivity
- "Waiting for connection" logic to HQMain so HQMain can be started at any time without waiting on myRIO

Bug Fixes:
- wrt. v1: timer calculation - divide by 1000 instead of multiply [fixed]

Open Questions:
!!velocity calculations are slow, is this a problem?
!!laser selection logic - right = 1, left = 2?
!!brake states are flexible - is that OK?




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

