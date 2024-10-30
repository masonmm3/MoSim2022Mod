First thing is to rename the imported model to Model

The next step is to setup the drive train.
	Start by adding a rigid body to 9999(your robot)
	Set the mass to 100 +- 10 depending on robot weight 90 being really light 110 being really heavy.
	Set Drag to 3 for both types.
	Set Interpolate to interpolate
	Set Collision Detect. to continuous
	Next set the Layer (just below the name to the right) to robot. hit yes when asked to set children to as well
	Then we can look at copying the drivetrain from other robots
	When doing so we need to look at speed and drivetrian type.
	Swerve
		High speed robots <=18 fts should copy Drivetrain from 6800 (also set Drag (not angular) to 2)
		Other speeds should copy from 1678/2974/06366 whoever has the closest shape.
	Tank
		6366/6328
	Once you have copy and pasted driveTrain into the new prefab you want to first make sure the model is roughly centered on the existing wheels then open the drop down. on Drive Train
	![[Pasted image 20241023203610.png]]
	This will reveal Raycast and Wheels. Open these drop down and line the wheels up appropriatly. ( do not change height)
	Then check the height and lower the model if its too high or raise the model if its too low
	Copy and paste bumpers over from any robot other than 1678
	Adjust the number locations and text along with the bumper colliders to match
	Next we want to double click frame rails and add box colliders too them. if the green lines dont closely match use a mesh collider but make sure to check Convex.
	Reminder if you disabled auto save to save.
	You now want to click back on 9999 and add another two components.
		Drive Controller
		Player Input
	Your inspector should now look like this
	![[Pasted image 20241023204442.png]]
	Starting with Drive Controller we need to do the following
		Robot Type: leave as is
		Drive Train: Swerve
		Bumper Numbers: Drag each BumberNumber object over to the Bumper Numbers list in the inspector to have them auto added
		Drive Train Parent: Drag teh DriveTrain object we pasted earlier over
		Raycast Distance: set to 0.25 for 4in diameter wheels. adjust for larger
		Skip the next two
		Max speed should be the max freespeed in Ft/s in our case (16)
		Acceleration speed: this is unitless so 2300 seems to be about right for 15-16ft/s adjust to your liking though.
		Steer Multiplyer: Mainly for tank drives and high acceleration robots. leave to 1 for now
		Skip the next two
		Bumper: Same thing as Bumper Numbers but the bumper models that change color from blue to red
	Your Drive Controller should now look like this.
	![[Pasted image 20241023204954.png]]
	Next step is to set up the player input. This is what actually tells the robot to do things.
	 First:
		 set actions to Crescendo by clicking the circle on the right
		 set Default scheme to 1
		 disable auto switch
		 set behavior to "Invoke Unity Events"
	Second:
		Open the "Events" dropdown at the bottom followed by "Robot"
		Once in you want to hit + on Translate, Rotate, Restart, and Move Camera
		Then drag 9999 over to each in the bottom left where it says None(Object)
		Then on Translate you want to click "No Function">"Drive Controller">"OnTranslate"
		Do the same for Rotate and Restart
		For move camera select "Walk" from the list of options on DriveController
	Player Input Should now Look Like This
	![[Pasted image 20241023205313.png]]

Now is a good time to test.
	To do so we want to save. then go to the Scenes folder and double click Crescendo
	Select RobotSpawnController
	Drag your robot to the list of PreFabs.
	Use the two bars to move it up one element on the list
	Take note of the last in the list. You want to pick that robot in the main menu.
	Click "Play" the arrow in the top center.
	return to menu as you would in a game and select the robot. Then click play to begin testing.
	Ideally everything works and you have no issues. However if you do. Make sure to check the console for Grey boxes as these are custom error reports that identify common issues.

Time to deal with Cargo movements.
	For this you want to copy and paste "Paths" "HiddenCargo" and Intake from another robot. It is extremely important you don't rename any of the "Hidden Cargo" as that is how they are added to the script

When Setting up your paths its important to understand that its a three step proccess. Intake (ground to robot), Centering(Indexes the cargo to the same spot everytime) and Stow(Moves the cargo within the robot to final resting place.)

The center of the arrows on Intake path point and Centering path is the target location for the path. Intake path will move along the x axis to match cargo

To set paths move intake and centering to their end locations then click on them to reveal two red dots and two blue dots. the Red dots are positions, the blue direction of travel. Simply adjust these for all paths until it moves to roughly the correct place.

Next move the hidden cargo by moving their parents Cargo1 and Cargo2
Cargo 1 should be closest to the shooter its the (1st cargo in and 1st cargo out)
Cargo 2 should be closest to intake It might be easier to change pivot local to center local.

Your prefab should now look something like this
![[Pasted image 20241023210322.png]]

We now want to add a CargoHandler script to the 9999 object similar to the drive controller
Setup:
	HiddenCargoParent: assign to HiddenCargo you pasted
	Intake Path. and Centering path. If single intake just drag over and dont worry. if its a double intake. they need to match number
	Leave eject as none if the robot doesnt feature a dedicated eject path.
	PathSpeed: the speed at which the cargo moves through the robot. Usually 1.0-1.5;
	ShootSpawn: Right click on 9999 and hit create empty. name it shoot spawn. Drag the arrows, making sure the top left says pivot,local to the shoot point and angle the blue arrow roughly in line with the shoot direction. then assign the new object
	Shoot Speed: The default speed of the shooter. only important if not using speed adjust.
	Low Shoot Speed: Speed to make low shots. This is not currently modified by any scripts.
	Back Spin Speed: The amount of backspin a shooter puts on to the cargo. Some backspin is required really just play around with it. 20-60 normally
	Flywheel target: Target RPM of the flywheel 4000 normally
	Flywheel Acceleration: constant acceleration in RPM/s 6500/7500
	Flywheel resource: set to shooting.sfx unless custom flywheel sounds are wanted
Your Cargo Handler should now look something like this 
![[Pasted image 20241023210630.png]]
Now setup the player input for shoot, lowShoot and intake
	Once done click on the intake collider you pasted and adjust the sizing. set it to the element num +1 (1 for single intakes) of the intake path you want it to use

This is another good opportunity to test.
	In this scenario I wont worry with making sure shots go in but if you want a fixed speed you may need to.

Next step
[[Unique Robot Systems]]
