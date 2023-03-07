---
label: Setup an ItemUI Prefab
layout: default
order: 2
---
# Setup an ItemUI Prefab

This section describes setting up the ItemUI Prefabs created in the previous section. This tutorial assumes all the necessary GameObjects and components have been added to the Item UI Prefab and that the user has the necessary data and images required to complete the Prefab.

![](/static/image14.png)

At this point, your ItemUI prefab should look like the above image.

1. The image of the ItemUI Prefab should not be modified, except for the 0 value for the transparency we applied earlier. It does sound intuitive to attach the picture or icon of the image there, but the Image component of the Prefab is only for handling user interactions.

2. Modify the values of the Item UI Component

There are three sections for this.

=== 2a. Item Attributes

- Set the Item Name
- Drag and drop the Image child GameObjectinto the Image field
- Set the Rarity (We will cover how to apply new rarities in a later section)
- Set the Item Tag. An Item Tag determines where the item will be equipped. Typically the "Any" Item Tag will go wherever it is allowed to go. (We will cover how to apply new Item Tags in a later section)
- Stack Limit is defaulted to 1. The system will treat the ItemUI as if it is a singular non-stackable item. Change the value if it is meant to stack and hold a larger quantity.
- Width is the space an item will take up in a Grid system. Recommend setting to 1 if unknown. Otherwise, put the value in units of 1 cell. I.e. if an item is meant to take up 2 cells in width, then assign 2 as the value.
- Height, similar width, except vertically inclined.

=== 2b. Container Prefab

- ContainerUI Prefab refers to the storage capacity of the prefab. I.e. a backpack, a pouch, or some other container. We will discuss the creation of this at a later section. For now, it can be left blank if the item is a generic item OR drag and drop a Backpack or Pouch cells prefab from the folder [!badge variant="info" icon="file-directory-open-fill" text="SimpleInventorySystem/Prefabs/UI Elements/Cells" margin="0 8 0 0"]

=== 2c. Required Component Links

Simply drag and drop the child GameObjects of the ItemUI Prefab.

- Backdrop Image
- Empty Grid Container

===

3. Modify the Rect Transform of the ItemUI Prefab

All the values should still be the same from the previous section. The only changes that will be made are to Width and Height.

Width should be the desired pixel size of each cell in the Grid system multiplied by the ItemUI component's Width.

!!!
If our system is using 75 pixels and the ItemUI's component's Width value is 2, then
the ItemUI Prefab's Width = 75 * 2 = 150
!!!

The same goes for the Height value.

The image below assumes the width and height of the ItemUI component are 2x2. And shows a complete ItemUI component.

![](/static/image17.png)

4. If an empty grid with the correct dimensions was previously placed, then this step and substeps can be skipped. Proceed to Step 5.

!!!
In our example, I decided to change the dimensions of the ItemUI Prefab to 2x2. Therefore, I will need to manually change the GameObject as well.
!!!

!!! Warning
These following substeps assume we are modifying a ItemUI with a cell size of 2x2 and a grid system with each cell being 75x75 pixels.
!!!

4a. Right click the Empty Grid GameObject and choose the option Unpack Prefab Completely. This assures us that we will not be modifying the source Prefab, or allow this GameObject to be updated by any changes made to the source Prefab.

4b. Modify the Rect Transform Component

||| Rect

axis | value
--- | ---
Width | 150
Height | 150
|||

4c. Duplicate the Image child GameObject under the Empty Grid GameObject. We will need to do this 3 times, to make a total of 4 child GameObjects.

If done correctly, the cells should be nicely fit inside the ItemUI Prefab. Compare to the image before with the following image.

![](/static/image23.png)

4d. Optional. You may rename the Empty Grid GameObject to better reflect the dimensions.

4e. Optional. You may drag and drop the GameObject into the Project window to turn it into a Prefab.

5. Modify the Rect Transform of the Image GameObject under the ItemUI Prefab

Similar to the ItemUI Prefab, the Width and Height should correspond to the dimensions of a cell and the units of the ItemUI Prefab.

!!!
In our example, the item is 2x2, therefore the width and height should be 150
!!!

6. Modify the Image Component of the Image GameObject under the ItemUI Prefab

Change the Source Image attribute to whatever you want for your Item.

!!! Warning
In the example, we will be using a placeholder icon.
!!!

After the steps are completed, the ItemUI should be finished and look similar to the image below.

![](/static/image22.png)