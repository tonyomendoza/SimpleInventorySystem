---
label: Create an Item Prefab
layout: default
order: 1
---
# Create an Item Prefab

This section describes creating an Item. The Item is interactable in the game world that will include an ItemUI Prefab as its child.

1. Create the Prefab with a model. If the prefab is already created, skip this step. Otherwise, drag and drop a model onto the Scene View. Then drag and drop it from the Scene Hierarchy into the Project Window to create a prefab.

![](/static/image11.png)

2. Open the newly created Item Prefab

![](/static/image2.png)

3. Drag and drop the PickUp Prefab under the Item Prefab.The Item Prefab should now contain 1 child GameObject. The PickUp Prefab can be found in the folder [!badge variant="info" icon="file-directory-open-fill" text="SimpleInventorySystem/Prefabs" margin="0 8 0 0"]

If done correctly, you should see 2 Sphere Colliders. One larger collider encompassing the other smaller collider.

![](/static/image15.png)

![](/static/image21.png)

4. Drag and drop the respective ItemUI Prefab under the Item Prefab.The Item Prefab should now contain 2 children GameObjects

In this example, I will be using the 2x2 ItemUI that I created earlier.

![](/static/image9.png)

5. Modify the PickUp Component under the PickUp GameObject

The component has 3 sections

=== 5a. Pickup Attributes

- Drag and drop the ItemUI child GameObject to the ItemUI attribute.
- The PickUp Range attribute has already been completed. If the user has another collider they want to connect, then they may replace that value.

=== 5b. Item Game Object Attributes

These refer to the GameObject holding the ItemUI Prefab or the Rigid Body component. In most cases, it will be the Item Prefab in question. Ensure that the Item Prefab has a RigidBody.

- Drag and Drop the Item Prefab to the Item Game Object attribute.
- Drag and Drop the Item Prefab with a Rigid Body to the Item Rigid Body attribute.

=== 5c. Item Game Object Transform Modifications

Sometimes an item carried on a person will be smaller or larger than how its being represented on the screen. It may have a certain rotation or position on the person's body. Assign the values here to alter how an item is positioned, rotated, or scaled on a character. This section will not go in-depth with setting this up since its use case is too specific.

- Alter Position: Changes where the item is positioned in respect to where it will be parented once equipped.
- Alter Rotation: Changes how the item is rotated in respect to where it will be parented once equipped.
- Changes the scale of an item in respect to where it will be parented once equipped.

===

6. A Sphere Collider should be attached to the Pickup GameObject. You can change the radius to increase its detection by a RayCast. Ensure that Is Trigger is checked.

7. The PickUpRange GameObject should be a child of the PickUp GameObject

7a. The PickUpRange GameObject should simply have a Pick Up Range Component attached.

7b. A Sphere Collider should be attached to the Pickup Range GameObject. During gameplay, a GameObject with the Player\_IS Component will check for collisions with GameObjects containing the PickUp Range Component. Decrease the radius to shrink the distance required for a player to be within pick. If the Player\_IS is not colliding with the PickUpRange, then the item will not be picked up. Ensure that Is Trigger is checked.

![](/static/image18.png)

If done successfully,the PickUp Prefab should look like the above image and the PickUp component should be filled out as such.