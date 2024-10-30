9999 features a 2 stage climber. The only climber which has a generic script. "Two Stage Y Axis Climber"

I Highly advise against starting with any radial/"windmill" style climber. Climbers that feature prominent passive elements like 6328 are also extremely difficult to get right.

To start with add box colliders to each of the three box tubing stages.

Next create a new game object on 9999 name it MiddleClimber then center it on the climber.
Next Select the parts of the climber model that make up the central stage and add them to the climber object. I highly recomend using the eye button (Far left next to the object) to hid objects that have been moved to the climber. Once your happy with everything you have moved go into MiddleClimber, Click the top model, scoll to the bottom, hold Shift and click the last. Then right click and select create empty parent. name it model.
Your scene should now look like this.
![Pasted image 20241024161022](https://github.com/user-attachments/assets/06ea7bd7-89bf-4a9a-9a2c-be6198d21965)


Now Complete the same process for the upper (2nd) stage. Name it Climber.
it should now look like this
![Pasted image 20241024161347](https://github.com/user-attachments/assets/bef621f9-c91e-4f46-9239-9a87cc9f19e3)


Now make everything visible again and click on climber. Add a configurable joint. set the rigid body to interpolate continuous. exclude the robot layer.

Connect the configurable joint to 9999. set the X,Z motion to locked, and the, X,Y,Z, Angular motion to locked.

Scroll down to Y drive and set Spring to 90,000, and damper to 9,000

Now Create a new child on Climber named Hook. add three empty objects and add box colliders. Use these to model the climber hook.
![Pasted image 20241024162010](https://github.com/user-attachments/assets/9cdd2e9e-acdb-43fc-a65b-cbfef7c126e0)

Now return to 9999 and add a Two Stage Y Axis Climber.
set Extend to Climber, Mid Stage to Middle Climber. Usually target distance should be set to 4.0-4.5. Use mid stage offset if the mid stage is not at the right Hight on the climber stage when moving. Then add it to player input under ClimbX.

![Pasted image 20241024162237](https://github.com/user-attachments/assets/d892eb45-ffac-4240-9cfc-e1378fed65c0)


Now For scoring. Add a new game object to Climber then add a box collider and set it to isTrigger. Then map it to roughly matches the hook.
![Pasted image 20241024162735](https://github.com/user-attachments/assets/bb85eb08-b56d-4351-9e46-6ab8eaadff1f)


Returning to 9999, add a climb scoring script. add the scoring to Collider array. Then set Raycast to the LF driveTrain Raycast.
![Pasted image 20241024163236](https://github.com/user-attachments/assets/d0215fd8-a4fa-486e-9577-6b66f7cec312)


Finally, Return to the Crescendo scene, and hit play. Make sure you are playing in windowed mode, so that you can select 9999 when in game. Go climb, if the score contribution increases you are done with the robot.

You are now ready for [[[Finishing up And UI]]](https://github.com/masonmm3/MoSim2022Mod/blob/main/MoSimDocs/Finishing%20up%20And%20UI.md)
