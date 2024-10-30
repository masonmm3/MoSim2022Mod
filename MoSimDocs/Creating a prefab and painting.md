#frc #MoSim #RapidReact

We create a Prefab by going to 
	Prefabs>Robots in the Project list in the bottom Left
	Then right clicking the the area where the other robots are Create>Prefab
	![[Pasted image 20241023195939.png]]
	Name the prefab your robot number (for future reference 9999)

**Starting The robot**
	Double click the prefab to open it.
	Once in drag 9999 Cad in the Custom Folder into the scene
	It should look like this
	![[Pasted image 20241023200105.png]]
	Set positions to zero
	select 9999 (The prefab) And change the scale to 5.85 on all axis
	Then double click a part to open it up. on The right hand side you have the inspector.
	Within the inspector you will see an ID number next to a color
	![[Pasted image 20241023200508.png]]
	In this case 0.917647
	Back in Custom>Robots select the robot model in the inspector you will see a list.
	Find the previous id number. And click material and change it to an existing material of the right color. Then scroll to the bottom and click apply
	Repeat until most major components are recolored
	Think of this as a first pass to decrease the work for the rest.
	Once happy Return to the prefab and right click the model in the scene. using the search bar find and click Unpack.

Now is when you should adjust/correct missing or duplicate parts it may also be worth doing some minor simplification.
	It might be faster to uncheck Auto save. Dont forget to save later though.
	To paint the remaining parts you want to open up your Materials folder.
	To "paint" a part you simply drag the desired color from the material folder on to the part

Unity should now look like this
![[Pasted image 20241023202453.png]]

next step [[Actually making the robot play]]