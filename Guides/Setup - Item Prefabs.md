# Setting Up Items

## Creating an ItemUI Prefab

This section describes creating prefabs with the ItemUI component. The ItemUI Component is necessary for handling user interaction with the inventory system.

## Quick Creation

1. Duplicate TEMPLATE\_ItemUI in the folder SimpleInventorySystem/Prefabs/ItemUI

2. Rename the newly duplicated Prefab

You may skip this section and proceed to Setup ItemUI Prefab if you duplicated the template and renamed the Prefab.

![](RackMultipart20230306-1-qkwvwt_html_6e8828a9f60fdfba.png)

## Manual Creation

1. Create a new empty GameObject in the scene and attach an Image Component.

![](RackMultipart20230306-1-qkwvwt_html_d0a6791b5967ceac.png) ![](RackMultipart20230306-1-qkwvwt_html_d5aac59ba30ba143.png)

2. Next, drag and drop the newly created GameObject into a prefabs folder in the Project window. In this example, the GameObject Sample ItemUI will be placed in the folder SimpleInventorySystem/Prefabs/ItemUI

![](RackMultipart20230306-1-qkwvwt_html_449d2aa18ebe1dfd.png)

3. You may delete the GameObject in the Scene now that there is a Prefab for it.

4. Rename the Prefab to whatever your item's name will be.To differentiate it from the prefab containing the model that we will create later, you can include the word UI in the name.

i.e. Potion\_UI, Backpack\_UI, Rifle\_UI, etc.

5. Open the Prefab by double clicking the Prefab or by Right Clicking the Prefab and choosing the Open option.

6. Change the Image's transparency to 0. You may save this step for later if you would like to reference the overall image size during the setup phase. ![](RackMultipart20230306-1-qkwvwt_html_498e281080801018.png)

7. Modify the Rect Transform's values with the following:

- Pos X: 0
- Pos Y: 0
- Pos Z: 0
- Anchors
  - Min
    - X: 0
    - Y: 1
  - Max
    - X: 0
    - Y: 1
- Pivot
  - X: 0
  - Y: 1

Modifying the Width and Height depends on the size that the Item UI will take up in the grid system. For now, set Width and Height to 75.

![](RackMultipart20230306-1-qkwvwt_html_9bddd3aebcaee61f.png)

8. Add an ItemUI Component

![](RackMultipart20230306-1-qkwvwt_html_97e2580e52cc4130.png)

9. Drag and drop an Empty Grid of your item's desired size under the Item UI Prefab. The Empty Grid Prefabs can be found in the folder SimpleInventorySystem/Prefabs/UI Elements/Empty Grid

If there is no empty grid that matches your size, please see the section Creating an Empty Grid.

![](RackMultipart20230306-1-qkwvwt_html_22ee08e862523ed3.png)

10. Drag and drop a Backdrop prefab under the ItemUI Prefab. The ItemUI Prefab should contain 2 children at this point, the Empty Grid Prefab and the Backdrop Prefab. The Backdrop Prefab can be found in the folder SimpleInventorySystem/Prefabs/UI Elements

![](RackMultipart20230306-1-qkwvwt_html_75a57a49623dbae.png)

The following instructions are necessary steps for creating stackable items. If your items are not meant to be stackable, then steps 11-14 can be skipped. These steps also assume the user has the TextMeshPro package installed in their project.

11. Add a new Game Object under the ItemUI Prefab. ItemUI Prefab should now have 3 children. The new Game Object should contain an attached Text Component. One way to do this is to right click the ItemUI Prefab and choose the option UI \> Text - Text Mesh Pro

![](RackMultipart20230306-1-qkwvwt_html_f609d9e2b8cfeefe.png)

12. Rename the text's Game Object to "Stack Count" for clarity's sake.

13. Modify the Rect Transform of Stack Count

- Pivot
  - X: 1
  - Y: 0
- Anchors
  - Min
    - X: 0
    - Y: 0
  - Max
    - X: 1
    - Y: 0
- Left: 0
- Pos Y: 0
- Pos Z: 0
- Right: 0
- Height: 50 (could be any number)

It should look like the following image.

![](RackMultipart20230306-1-qkwvwt_html_f1effa4c0acdb3f1.png)

14. Modify the TextMeshPro - Text (UI) component

- Text Input

Change the text field to a number. Try 0.

- Font Size

Change the size to whatever number to fit the text. We are using size 12.

- Alignment

The alignment should be Right aligned and Bottom aligned. Clicking the third buttons of the top and bottom row should do the trick.

![](RackMultipart20230306-1-qkwvwt_html_9abb3b06b39018b2.png)

15. Add a GameObject with an attached Image component under the ItemPrefab. The ItemUI Prefab should contain 3 children, or 4 if the Stack Count text was added from the last steps.

16. Modify the RectTransform component of the Image GameObject.

- PosX: 0
- PosY: 0
- PosZ: 0
- Width: 75
- Height: 75
- Anchors
  - Min
    - X: 0
    - Y: 1
  - Max
    - X: 0
    - Y: 1
  - Pivot
    - X: 0
    - Y: 1

![](RackMultipart20230306-1-qkwvwt_html_2a9586c2349ad94e.png)

With this section complete, we will continue with setting up the Item UI.

## Setup an ItemUI Prefab

This section describes setting up the ItemUI Prefabs created in the previous section. This tutorial assumes all the necessary GameObjects and components have been added to the Item UI Prefab and that the user has the necessary data and images required to complete the Prefab.

![](RackMultipart20230306-1-qkwvwt_html_720d576e6dbe3cdc.png)

At this point, your ItemUI prefab should look like the above image.

1. The image of the ItemUI Prefab should not be modified, except for the 0 value for the transparency we applied earlier. It does sound intuitive to attach the picture or icon of the image there, but the Image component of the Prefab is only for handling user interactions.

2. Modify the values of the Item UI Component

There are three sections for this.

2a. Item Attributes

- Set the Item Name
- Drag and drop the Image child GameObjectinto the Image field
- Set the Rarity (We will cover how to apply new rarities in a later section)
- Set the Item Tag. An Item Tag determines where the item will be equipped. Typically the "Any" Item Tag will go wherever it is allowed to go. (We will cover how to apply new Item Tags in a later section)
- Stack Limit is defaulted to 1. The system will treat the ItemUI as if it is a singular non-stackable item. Change the value if it is meant to stack and hold a larger quantity.
- Width is the space an item will take up in a Grid system. Recommend setting to 1 if unknown. Otherwise, put the value in units of 1 cell. I.e. if an item is meant to take up 2 cells in width, then assign 2 as the value.
- Height, similar width, except vertically inclined.

2b. Container Prefab

- ContainerUI Prefab refers to the storage capacity of the prefab. I.e. a backpack, a pouch, or some other container. We will discuss the creation of this at a later section. For now, it can be left blank if the item is a generic item OR drag and drop a Backpack or Pouch cells prefab from the folder SimpleInventorySystem/Prefabs/UI Elements/Cells

2c. Required Component Links

Simply drag and drop the child GameObjects of the ItemUI Prefab.

- Backdrop Image
- Empty Grid Container

3. Modify the Rect Transform of the ItemUI Prefab

All the values should still be the same from the previous section. The only changes that will be made are to Width and Height.

Width should be the desired pixel size of each cell in the Grid system multiplied by the ItemUI component's Width. So if our system is using 75 pixels, then multiply that with the ItemUI's component's Width value.

i.e.Width = 75 \* 2 = 150

The same goes for the Height value.

The image below assumes the width and height of the ItemUI component are 2x2. And shows a complete ItemUI component.

![](RackMultipart20230306-1-qkwvwt_html_76816956b9a801b8.png)

4. If an empty grid with the correct dimensions was previously placed, then this step and substeps can be skipped. Proceed to Step 5.

In our example, I decided to change the dimensions of the ItemUI Prefab to 2x2. Therefore, I will need to manually change the GameObject as well.

These following substeps assume we are modifying a ItemUI with a cell size of 2x2 and a grid system with each cell being 75x75 pixels.

4a. Right click the Empty Grid GameObject and choose the option Unpack Prefab Completely. This assures us that we will not be modifying the source Prefab, or allow this GameObject to be updated by any changes made to the source Prefab.

4b. Modify the Rect Transform Component

- Width: 150
- Height: 150

4c. Duplicate the Image child GameObject under the Empty Grid GameObject. We will need to do this 3 times, to make a total of 4 child GameObjects.

If done correctly, the cells should be nicely fit inside the ItemUI Prefab. Compare to the image before with the following image.

![](RackMultipart20230306-1-qkwvwt_html_a73332bdc4dd3e81.png)

4d. Optional. You may rename the Empty Grid GameObject to better reflect the dimensions.

4e. Optional. You may drag and drop the GameObject into the Project window to turn it into a Prefab.

5. Modify the Rect Transform of the Image GameObject under the ItemUI Prefab

Similar to the ItemUI Prefab, the Width and Height should correspond to the dimensions of a cell and the units of the ItemUI Prefab.

I.e. In my example, my item is 2x2, therefore the width and height should be 150

6. Modify the Image Component of the Image GameObject under the ItemUI Prefab

Change the Source Image attribute to whatever you want for your Item.

I.e. In my example, I will be using a placeholder icon.

After the steps are completed, the ItemUI should be finished and look similar to the image below.

![](RackMultipart20230306-1-qkwvwt_html_b93a24b14f9d2dcd.png)

## Creating an Item Prefab

This section describes creating an Item. The Item is interactable in the game world that will include an ItemUI Prefab as its child.

1. Create the Prefab with a model. If the prefab is already created, skip this step. Otherwise, drag and drop a model onto the Scene View. Then drag and drop it from the Scene Hierarchy into the Project Window to create a prefab.

![](RackMultipart20230306-1-qkwvwt_html_6d6781adcab274e.png)

2. Open the newly created Item Prefab

![](RackMultipart20230306-1-qkwvwt_html_8d38b36be1cfcc77.png)

3. Drag and drop the PickUp Prefab under the Item Prefab.The Item Prefab should now contain 1 child GameObject. The PickUp Prefab can be found in the folder SimpleInventorySystem/Prefabs

If done correctly, you should see 2 Sphere Colliders. One larger collider encompassing the other smaller collider.

![](RackMultipart20230306-1-qkwvwt_html_c39748c9db5ecbd4.png)

![](RackMultipart20230306-1-qkwvwt_html_9ac8e676ce7ed1bb.png)

4. Drag and drop the respective ItemUI Prefab under the Item Prefab.The Item Prefab should now contain 2 children GameObjects

In this example, I will be using the 2x2 ItemUI that I created earlier.

![](RackMultipart20230306-1-qkwvwt_html_cd151be5e7cbc25b.png)

5. Modify the PickUp Component under the PickUp GameObject

The component has 3 sections

5a. Pickup Attributes

- Drag and drop the ItemUI child GameObject to the ItemUI attribute.
- The PickUp Range attribute has already been completed. If the user has another collider they want to connect, then they may replace that value.

5b. Item Game Object Attributes

These refer to the GameObject holding the ItemUI Prefab or the Rigid Body component. In most cases, it will be the Item Prefab in question. Ensure that the Item Prefab has a RigidBody.

- Drag and Drop the Item Prefab to the Item Game Object attribute.
- Drag and Drop the Item Prefab with a Rigid Body to the Item Rigid Body attribute.

5c. Item Game Object Transform Modifications

Sometimes an item carried on a person will be smaller or larger than how its being represented on the screen. It may have a certain rotation or position on the person's body. Assign the values here to alter how an item is positioned, rotated, or scaled on a character. This section will not go in-depth with setting this up since its use case is too specific.

- Alter Position: Changes where the item is positioned in respect to where it will be parented once equipped.
- Alter Rotation: Changes how the item is rotated in respect to where it will be parented once equipped.
- Changes the scale of an item in respect to where it will be parented once equipped.

6. A Sphere Collider should be attached to the Pickup GameObject. You can change the radius to increase its detection by a RayCast. Ensure that Is Trigger is checked.

7. The PickUpRange GameObject should be a child of the PickUp GameObject

7a. The PickUpRange GameObject should simply have a Pick Up Range Component attached.

7b. A Sphere Collider should be attached to the Pickup Range GameObject. During gameplay, a GameObject with the Player\_IS Component will check for collisions with GameObjects containing the PickUp Range Component. Decrease the radius to shrink the distance required for a player to be within pick. If the Player\_IS is not colliding with the PickUpRange, then the item will not be picked up. Ensure that Is Trigger is checked.

![](RackMultipart20230306-1-qkwvwt_html_b86531a9f16a4c76.png)

If done successfully,the PickUp Prefab should look like the above image and the PickUp component should be filled out as such.