Now its time to start working on robot subsystems.
	Step 1 is to give colliders to everything. Use box colliders where possible and mesh colliders where box doesn't work
	Starting with the intake create a new GameObject named intake and align it to the intake pivot. Then add a hinge joint to it. Set the rigid body it adds to interpolate continuous, I also highly recommend setting exclude layers to robot
	![[Pasted image 20241023212034.png]]
	 Then connect the joint to the robot. (Four bar is more difficult look at an existing bot for an example)
	Go to 9999 then add a flip intake to the component list. add the hinge joint. if its already deployed check flipped state. assign it to the player input and adjust from there.
	![[Pasted image 20241023212221.png]]
	Once you have identified your setpoints I highly recommend setting limits on the intake joint.

The next step of an intake is giving it an attraction force. open 1678s prefab. Intake>MainFourBar Then capy RollerBar

Paste and make it a child of intake pivot
![[Pasted image 20241023212802.png]]
Within Roller bar is a bunch of models. just delete these. now move the roller bar and reconnect the joint on it, this time to Intake Pivot.

now return to 9999 and add a roller bar intake script. set this up like the others. abs(rpm) is usually 5000-10000. make - if it pushes away. If your struggling to get the intake where you want it, increase the weight of the intake. Unity simulates the gyroscopic affect seen in high rpm objects.


At this point the robot is completely capable of playing. Time to make it good at playing

The robot we are working on doesn't have a hood, but its the same setup process as the intake. Offset is in deg, typical aim point is 0,13,0.

9999, will use the speed adjust script with limits set. This will allow for range using variable speed.

on 9999 add a speed adjust script. set base speed to around 45, then speed multiplier to about 0.5 (distance x this)+basespeed is formula the formula. We want about Tarmac range so set max speed to 0,50. No need to add to player input its always checking.

After some tuning I landed on these settings for a tarmac shooter
![[Pasted image 20241023221100.png]]

Next on the list, is Rotat To Target. This script is what handles auto aiming. if uses a P and a Max. formula P x Distance = raw. (raw <= max) = steering input. p = 0.04 and max = 0.05 are usually good starting spots for swerve. Unlike previous scripts You access this through DriveControler.OnAlign when assigning it in playerInput.

Next we want to add a box collider to 9999, set it to is trigger then shape it loosely around the outside of the robot.
![[Pasted image 20241024152829.png]]

Lastly we want to deal with LEDs. Go to 6366/06366 and copy a set of LEDs. then paste and align them in 9999. Led1 shows the state of cargo 1 Led2 shows the state of cargo2. Add the LEDs script to 9999. Then set up the script.
![[Pasted image 20241024153423.png]]

finally for the robot we want to go to [[Climbing and scoring.]]