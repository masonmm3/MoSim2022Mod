Back in the Crescendo scene click Robot spawn controller and drag the new bot back to the bottom of the list..

Next find some photos of the robot and import them to Imports>2022>Images. Then click it and set it to Sprite2d single
![[Pasted image 20241024164313.png]]

Now go to Other and click Blue Robot Selector. Click the plus to add a new robot to the list then fill out the information and add your photo you imported. then repeat with the Red Selector
![[Pasted image 20241024164545.png]]
Now change to the Main Menu scene. Make sure to save the Crescendo scene If you haven't already.

Click play and change robot. This will throw errors we will deal with them latter.

Click play. Once in game click the scene button to change to scene view while playing. Depending on your hardware there may be some lag. Then click the circle with the three dots in the top right corner of the scene view. to remove all the markers.

Find a flattering image of the robot for the menu. Following the 3rds rule will help with framing in the menu.

While in scene view collect images for climbing as well. remember, you only have up to 6 steps with images.

Once done you will need to open The menu image in Gimp or Photoshop or whatever your preferred image program is (paint should work as well). Then add the banner in the top right to the image.

Export then import to the same place as the previous, then open canvas and click panel in the main menu scene.

Replace the source image to make sure it looks good, once your happy add it to the BackDrop Selctor script on panel.
![[Pasted image 20241024170529.png]]

Now Import your Climb Images to Imports>2022>ClimbTutorials>(newFolder)9999

You will now want to change those to sprites and re enable the sphere with the dots in the top Right.

Then Click MainMenu. Uncheck the checkbox next to the name, That will make it disapear, Then Check the checkBox on tutotials. Now open the tutorials, In this scenario we will copy Rembrandts. Uncheck (disable) The old one, and rename the new one to OffseasonShowcase. Then replace the images by doing the same thing as Panel. (there is no script this time though). 

Once done click on the tutorial card, and add the OffseaosnShowcase game object to the array.

Disable the tutorial card, enable the main menu object, and You are done creating the first robot in your mod.