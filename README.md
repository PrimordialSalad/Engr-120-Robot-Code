# Engr 120 Robot
For Engr 120, my team was tasked with designing an autonomous robot.  The robot had to, autonomously, find a beacon that outputted infrared light(IR) and connect something to it, in this case string.  Here is an angled top view of the final prototype:

![Engr 120 Robot Angled Top View](http://i.imgur.com/uy0K6FY.jpg)

Sheathed in the cardboard housings were the IR phototransistors, one on each of the 4 cardinal directions, totalling to 4 in use.  These were used to detect the beacon.  The phototransistors on the back and sides were used to calculate ambient light levels which in turn would help mitigate the reflection of the testing area's walls.  This left the front phototransistor for beacon detection.  Here is a side view of the prototype:

![Engr 120 Robot Side View](http://i.imgur.com/DvyTudR.jpg)

The electromagnet, which can be seen at the end of the linear arm was used to carry the string for connection.  The string had metal attached to the end which could be detached once the electromagnet was turned off.  Not visible in this second picture but visible in the first is the black toggle switch, located under the arm, which was physically turned off by the arm lowering and toggling it off.  The 4 D Cell batteries were used for the purpose of powering the electromagnet.  A angled front view can be seen pictured here:

![Engr 120 Robot Angled Front View](http://i.imgur.com/7FiAwIx.jpg)

In this photo, the bumper switches can be seen which were used in conjucntion with the sonar sensor and, not pictured, back limit switches to detect wall collisions.  The sonar was also used to detect, after the beacon was located, the distance the robot needed to travel until it was close enough for detachment onto the beacon.  Here is the angled back view of the robot:

![Engr 120 Robot Angled Back View](http://i.imgur.com/dJC9N54.jpg)

Not very visible in the picture but the locomotion style of the robot is tank-drive.  This means there are 3 gears per side meshed together and powered by a back motor that spins both wheels on one side together.  If one side is spun opposite the other, the robot will turn.  Also pictured is the motor that lowers the arm for electromagnet shutoff.  The breadboard was used to house the circuits for the IR phototransistors.  So what is pictured here is the breadboard with 4 of the same circuit hooked up to it.

# Engr 120 Robot Code

The code was run from a VEX microcontroller which was located under the central platform.  The cortex is an ARM-cortex and the firmware to run the robot was written in RobotC, a derivative of C.  The rest of the robot was either built with a VEX kit or built with extra parts like the electormagnet.  In the code, I include a rudimentary finite-state machine style format to the code.  The code is not efficient by any means but it effectively get the job done.  If I had had more time I would probably refactor the code into smaller functions and fix the issues described below.

## Features
* Reliable connection mechanism using an electormagnet.
* Effective tank-drive style locomotion
* Practical beacon acquisition system using IR phototransistors and a sonar sensor.
* Sturdy design and quick task completion.

## Issues
* It performs adequately well in high-intensity sunlight situations but can get confused as there might be little difference in IR light readings from the beacon and the ambient light.
* It can refind the beacon if they beacon is moved slightly outside its detection range but any excessive movement of the beacon outside its detection range will cause the robot to endlessly search for it agian.  This might be caused by the robot getting stuck in the searching state and the conditions for exit from the searching state never again being met.

## Robot Code Logic Flow

Included below is a logic flowchart that is somewhat a visual representation of the finite-state machine format of the code:

![Engr 120 Robot Logic Flowchart](http://i.imgur.com/cA7CGhN.png)
