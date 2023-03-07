---
label: Create an ItemUI Prefab
layout: default
order: 3
---
# Create an ItemUI Prefab

This section describes creating prefabs with the ItemUI component. The ItemUI Component is necessary for handling user interaction with the inventory system.

## Quick Creation

1. Duplicate ```TEMPLATE_ItemUI``` prefab in the folder [!badge variant="info" icon="file-directory-open-fill" text="SimpleInventorySystem/Prefabs/ItemUI" margin="0 8 0 0"]

2. Rename the newly duplicated prefab

!!! Success
You may skip this section and proceed to Setup ItemUI prefab if you duplicated the template and renamed the prefab.
!!!

![](/static/image6.png)

## Manual Creation

1. Create a new empty GameObject in the scene and attach an Image Component.

![](/static/image16.png)
![](/static/image4.png)

2. Next, drag and drop the newly created GameObject into a prefabs folder in the Project window. In this example, the GameObject Sample ItemUI will be placed in the folder [!badge variant="info" icon="file-directory-open-fill" text="SimpleInventorySystem/Prefabs/ItemUI" margin="0 8 0 0"]

![](/static/image19.png)

3. You may delete the GameObject in the Scene now that there is a Prefab for it.

4. Rename the Prefab to whatever your item's name will be.To differentiate it from the prefab containing the model that we will create later, you can include the word UI in the name.

i.e. Potion\_UI, Backpack\_UI, Rifle\_UI, etc.

5. Open the Prefab by double clicking the Prefab or by Right Clicking the Prefab and choosing the Open option.

6. Change the Image's transparency to 0. You may save this step for later if you would like to reference the overall image size during the setup phase.

![](/static/image20.png)

7. Modify the RectTransform's values with the following:

||| Position

axis | value
--- | ---
X | 0
Y | 0
Z | 0
||| Anchors
Min

axis | value
--- | ---
X | 0
Y | 1

Max

axis | value
--- | ---
X | 0
Y | 1
||| Pivot

axis | value
--- | ---
X | 0
Y | 1
|||

Modifying the Width and Height depends on the size that the Item UI will take up in the grid system. For now, set Width and Height to 75.

![](/static/image7.png)

8. Add an ItemUI Component

![](/static/image5.png)

9. Drag and drop an Empty Grid of your item's desired size under the Item UI Prefab. The Empty Grid Prefabs can be found in the folder [!badge variant="info" icon="file-directory-open-fill" text="SimpleInventorySystem/Prefabs/UI Elements/Empty Grid" margin="0 8 0 0"]

If there is no empty grid that matches your size, please see the section Creating an Empty Grid.

![](/static/image8.png)

10. Drag and drop a Backdrop prefab under the ItemUI Prefab. The ItemUI Prefab should contain 2 children at this point, the Empty Grid Prefab and the Backdrop Prefab. The Backdrop Prefab can be found in the folder [!badge variant="info" icon="file-directory-open-fill" text="SimpleInventorySystem/Prefabs/UI Elements" margin="0 8 0 0"]

![](/static/image1.png)

The following instructions are necessary steps for creating stackable items. If your items are not meant to be stackable, then steps 11-14 can be skipped. These steps also assume the user has the [!badge variant="info" icon="package" text="TextMeshPro" margin="0 8 0 0"] package installed in their project.

11. Add a new Game Object under the ItemUI Prefab. ItemUI Prefab should now have 3 children. The new Game Object should contain an attached Text Component. One way to do this is to right click the ItemUI Prefab and choose the option UI \> Text - Text Mesh Pro

![](/static/image12.png)

12. Rename the text's Game Object to "Stack Count" for clarity's sake.

13. Modify the Rect Transform of Stack Count
!!!primary Primary
In this example, we use 50 for the TransformRect's Height. This number could be anything the developer needs it to be.
!!!

||| Rect

axis | value
--- | ---
Left | 0
Right | 0
Height | 50
||| Position

axis | value
--- | ---
Y | 0
Z | 0
||| Anchors
Min

axis | value
--- | ---
X | 0
Y | 0

Max

axis | value
--- | ---
X | 1
Y | 0
||| Pivot

axis | value
--- | ---
X | 1
Y | 0
|||

It should look like the following image.

![](/static/image10.png)

14. Modify the TextMeshPro - Text (UI) component

- Text Input

Change the text field to a number. Try 0.

- Font Size

Change the size to whatever number to fit the text. We are using size 12.

- Alignment

The alignment should be Right aligned and Bottom aligned. Clicking the third buttons of the top and bottom row should do the trick.

![](/static/image13.png)

15. Add a GameObject with an attached Image component under the ItemPrefab. The ItemUI Prefab should contain 3 children, or 4 if the Stack Count text was added from the last steps.

16. Modify the RectTransform component of the Image GameObject.
!!!
In this example, we use 75 for the TransformRect's Width and Height. This number could be anything the developer needs it to be.
!!!

||| Rect

axis | value
--- | ---
Width | 75
Height | 75
||| Position

axis | value
--- | ---
X | 0
Y | 0
Z | 0
||| Anchors
Min

axis | value
--- | ---
X | 0
Y | 1

Max

axis | value
--- | ---
X | 0
Y | 1
||| Pivot

axis | value
--- | ---
X | 0
Y | 1
|||

![](/static/image3.png)

With this section complete, we will continue with setting up the Item UI.