# eNav Rig: Clock Rescue for the Si4732 Receiver

## The problem
The Si4732 FM/AM receiver normally takes its reference clock from a 32.768 kHz crystal (FC-135R, CL = 12.5 pF). Crystal networks are easy to get subtly wrong and hard to fix after fab, and on a fleet board a bad one means a respin.

## The design choice
Next to the crystal network I added a pair of 0 ohm DNP pads (R3/R4, routed to ESP32 GPIO27 and GPIO32). They cost nothing and are left unpopulated. If the crystal doesn't work, the ESP32 can drive the receiver's reference clock instead.

## What happened
One assembled unit had a crystal backup issue and the receiver wouldn't run properly. I populated the 0 ohm pads, drove the clock from the MCU, and ran data collection for several days next to reference boards in the same location to check the data quality, resulting in the board collecting data at an accurate rate.


## Why I like it
- A dead board became a working one with two resistors and no respin.
- The fix was planned at the schematic stage, not improvised at the bench.
- It is invisible on boards that don't need it.

## Image
<img width="411" height="302" alt="image" src="https://github.com/user-attachments/assets/f231cf0c-28ff-4b5c-825d-dc98f608b1a2" />

