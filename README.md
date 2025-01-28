**_Tutorial: Applying Baked LiveLink Face Animations to Metahumans in Unreal Engine 5.3_**

1. _Record Face Animation_


I used a seperate project to record face animations with LiveLink. Bake the animation in the project that you recorded face animations. To do this,open the level sequencer of the recorded face animation. Right click on "Face" in the level sequecer and select "Bake Animation Sequence".

<img src="./images/1.png" alt="1" width="500"/> <img src="./images/2.png" alt="2" width="500"/><img src="./images/3.png" alt="3" width="500"/>

2. _Export the baked animation_
 
 
 Select "Asset Actions", then select "Export". There will be a pop up window named "FBX Export Options", select everything in the pop up and click on "Export to Animation"

<img src="./images/4.png" alt="4" width="500"/> <img src="./images/5.png" alt="5" width="500"/><img src="./images/6.png" alt="6" width="500"/>

3. Open the project where you want to apply face animation. Download the metahuman from the Quixel Bridge and add it to the project. 
! Make sure the Metahuman you downloaded is the same one you used used during face recording face animation. 
For this tutorial, I will use the Metahuman named Gavin3.

<img src="./images/7.png" alt="7" width="500"/>

4. I have already created a folder called "Animation Sequences". Create a new folder called "Gavin3" under the Animations Sequences folder. 

<img src="./images/8.png" alt="8" width="500"/>

5. Right-click inside the "Gavin3" folder and select "Import". Choose the baked animation .fbx file you exported earlier. 
There will be a pop up window called "FBX Import Options", make sure you select "Skeletal Mesh". Import mesh and animations. Then, click on "Import All". 

<img src="./images/9.png" alt="9" width="500"/><img src="./images/10.png" alt="10" width="500"/><img src="./images/11.png" alt="11" width="500"/>

6. Open the blueprint of the metahuman that you downloaded. In my project, it is called "BP_Gavin3". Select "Body" in the "Components" section on the left. 
Then, go to "Anim Class" in the "Details" panel and choose "ABP_LookAtMetahuman" for the anim class. 

<img src="./images/12.png" alt="12" width="500"/>

7. Select, "Face" in the "Components" section. Go to "Skeletal Mesh Asset" in the "Details" panel and click on the folder with magnifying glass. 

<img src="./images/13.png" alt="13" width="500"/>

8. Open the "Gavin_3_FaceMesh" file. 

<img src="./images/14.png" alt="14" width="500"/>

9. On the other side, go to "Metahuman sequences" folder, open "Gavin3" folder which you imported, open the "Skeletal Mesh" which is under the folder.

<img src="./images/15.png" alt="15" width="500"/>

10. There are two files now for the face meshes of Gavin3. One of them is original, one of the is the one you imported. The new one is gray. The original face mesh, under the "Material Slots", should have 15 material slots, while the new (gray) one typically has 9 material slots. 
Copy the 15 material slots from the original mesh by going on top of it, do right click and copy. 

<img src="./images/16.png" alt="16" width="500"/>

11. Go to the new mesh, increase the number of material slots from 9 to 15 using the + button. 

<img src="./images/17.png" alt="17" width="500"/>

12. Paste the copied material slots into the gray mesh.  

<img src="./images/18.png" alt="18" width="500"/><img src="./images/19.png" alt="19" width="500"/>

13. Go to the "BP_Gavin3". Change the "Skeletal Mesh Asset" to the new mesh you imported.

<img src="./images/20.png" alt="20" width="500"/>

14. Open another metahuman blueprint. (I will use BP_Rowan).
Copy the locations of all components under the Face and paste them into the corresponding locations in BP_Gavin3.


15. For each face object in BP_Gavin3, copy the "Attachment Name" in the "Details" panel and paste it into the "Parent Socket" field.
Repeat this for all face objects to make sure they remain attached.

<img src="./images/21.png" alt="21" width="500"/><img src="./images/22.png" alt="22" width="500"/>

16. Copy the "Widget" from the Face Component of a ready MetaHuman blueprint (BP_Rowan) and paste it into the same section in BP_Gavin3.

<img src="./images/23.png" alt="23" width="500"/><img src="./images/24.png" alt="24" width="500"/>

17. In BP_Rowan, go to the Event Graph. Copy the "Set Widget for X and O Alignment" nodes and paste them into the Event Graph of BP_Gavin3. Change Custom Event node to Event Begin Play node.

<img src="./images/25.png" alt="25" width="500"/><img src="./images/26.png" alt="26" width="500"/><img src="./images/37.png" alt="37" width="500"/>

18. Create a new variable called Letter with the type Text. Set its default value to “0” in the Details panel.

<img src="./images/27.png" alt="27" width="500"/>

19. In BP_Gavin3, under the Details panel for the Face component, click the magnifying glass next to Face_AnimBP_C to open the file.

<img src="./images/28.png" alt="28" width="500"/><img src="./images/29.png" alt="29" width="500"/>

20. In the Metahuman Sequences/Gavin3 folder, create a new animation blueprint by right clicking. Select the new face mesh you imported.  Name the file "abp_Gavin3_positive".

<img src="./images/30.png" alt="30" width="500"/><img src="./images/31.png" alt="31" width="500"/><img src="./images/32.png" alt="32" width="500"/>

21. Copy the animation graph from Face_AnimBP_C and paste it into new animation blueprint called "abp_Gavin3_positive". Connect all nodes.

<img src="./images/33.png" alt="33" width="500"/> 

22. Create an arrow from Blend Pose 0 uder the Layered blend per bone node and search for Play Gavin3-Fred-Positive_Anim.  

<img src="./images/35.png" alt="35" width="500"/>

23. Go to BP_Gavin3. In the "Details" panel for the Face component, set the Anim Class to "abp_Gavin3_positive".

<img src="./images/36.png" alt="36" width="500"/>

24. Go to BP_Gavin3. Click on Class Settings on the toolbar. In the Details panel on the right side, go to Interfaces, click the + Add button next to the Implemented Interfaces. 
Under the available interfaces select the BPI_State Instructions. 

25. Then, go the Event Graph of the blueprint. Right-click in the graph and type the name of the event you want to implement (from the interface) which is Event Hide Mesh from BPI_Virtual Agent interface. 
On the left side you will see the interfaces which are Hide Mesh, Show Widget, Hide Widget and Get Widget Location. 
Go to ready metahuman and copy and paste the nodes  inside them.  