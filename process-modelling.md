# Process Modelling (40 mins)

- **Red Hat Process Automation Manager (RH PAM)** uses the [BPMN2](https://www.omg.org/bpmn/) standard to define the structure and semantics of the process
- With the data model defined, we can now sketch out the main flow of the process, the actors, the user task nodes and the required automation decisions
- Our use case has three main scenarios
 - Auto-Approval
 - Manual-Approval
 - Rejection
- Let’s start by modeling the process flow for the Auto-Approval scenario

![Scenario1]({% image_path m1p7i1_Scenario1.png %})


---
![Info]({% image_path m0_info.png %}){:align="left"} 

For the remainder part of this workshop we are going to refer to Red Hat Process Automation Manager by it’s short name **RH PAM**. 

---

- In **RH PAM** the finished **Auto-Approval** scenario will look something like this

![RHPAM_Scenario1]({% image_path m1p7i2_RHPAM_Scenario1.png %})



### 1.3.1 Create OrderAsset process

- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project view

![BreadcrumbNav]({% image_path m1p7i3_BreadcrumbNav.png %})

- Click on the Add Asset button

![AddAsset]({% image_path m1p7i4_AddAsset.png %})

- In the drop-down menu in the upper-left corner, select Process

![AddProcessMenu]({% image_path m1p7i5_AddProcessMenu.png %})

- Click on the **Business Process** tile

![ProcessTile]({% image_path m1p7i6_ProcessTile.png %})

Name your process **OrderAsset**, and click on the **+OK** button

![AddProcessDialog]({% image_path m1p7i7_AddProcessDialog.png %})


---
![Info]({% image_path m0_info.png %}){:align="left"} 

It is common practice to use [Pascal](https://techterms.com/definition/pascalcase) case for business process names i.e. the practice of writing compound words or phrases in which the first letter of each concatenated word is capitalized.

---

- The **OrderAsset** process opens in the **Process Designer**

![ProcessDesigner]({% image_path m1p7i8_ProcessDesigner.png %})

### 1.3.2 Define Process Variables

- Our process will manipulate two variables through it’s execution
 - The **OrderInfo** data object that we created in part 1.2 of this lab.
 - A bollean variable **approved**, that will hold the result of evaluating the supplier's offer
- Open the properties editor for our process
 - Firstly click your mouse anywhere on the blank canvas of the editing screen. This will ensure you are editing the properties of the entire process rather than the variables of one element.
 - hover on top right pencil icon in designer
 - click to open the **Properties pane** on the right
 
 ![PropertiesPane]({% image_path m1p7i9_PropertiesPane.png %})

- Scroll down in the property panel on the right side of the screen, until you see the section Process Data.
![ProcessVariables]({% image_path m1p7i10_ProcessVariables.png %})


---
![Info]({% image_path m0_info.png %}){:align="left"} 

HINT: Don’t see a process data screen like this? 
If you see something that looks like the screen below, then you will need to select the BPMN canvas. Just click your mouse anywhere in that blank on the editing grid.

![WrongProperties]({% image_path m1p7i11_WrongProperties.png %})

---

- Expand the **Process Data** section
- Next click on the plus sign ‘+’ to define a new process variable

![AddProcessVariable]({% image_path m1p7i12_AddProcessVariable.png %})

Define a process variable as shown in the following table

|      Name     |    Data Type   |  
| ------------- | -------------- |
|   orderInfo   |   OrderInfo    |    
|   approved    |    Boolean     |    

![ProcessVariable]({% image_path m1p7i13_ProcessVariable.png %})



### 1.3.3 Create Swim Lanes

- In the palette on the left-side of the editor, click on the **containers** icon then select the **Lane** component

![LaneMenu]({% image_path m1p7i14_LaneMenu.png %})

- To create a **Lane**, move your cursor to the canvas and click on an area to place the lane component on the canvas
- Double click on the lane to give it the name **Supplier**

![NameLane]({% image_path m1p7i15_NameLane.png %})



---
![Info]({% image_path m0_info.png %}){:align="left"} 

You can resize a lane by clicking on it, and using the red dot at the bottom right.

![ResizeLane]({% image_path m1p7i16_ResizeLane.png %})

---

- Repeat the same process again to create two more lanes:
 - System
 - Purchasing Manager
 
- Your lanes should look like this

![SwimLanes]({% image_path m1p7i17_SwimLanes.png %})



### 1.3.4 Create Start Event

- In the palette on the left-side of the editor, click on the **Start Events** icon then select the **Start** node

![StartEventMenu]({% image_path m1p7i18_StartEventMenu.png %})

- Click again inside the Purchasing Manager lane to place a start node there

![StartEvent]({% image_path m1p7i19_StartEvent.png %})


---
![Info]({% image_path m0_info.png %}){:align="left"} 

Clicking on a node/event displays a set of mini icons that you can use to configure the node/event or create the next task in the process. This is another way to add nodes/events in addition to the left side menu

![MiniIcons]({% image_path m1p7i20_MiniIcons.png %})

---

### 1.3.5 Create Request Offer user task

- Click on the **Start Event** node, and click **Create Task**
- Click on the task node again and using the configuration icon below it, convert this node into a **Usertask** by clicking on the **Convert Into User** mini icon
- Double Click on the node to give it the name **Request Offer**

![RequestOfferTask]({% image_path m1p7i21_RequestOfferTask.png %})

- With the **Request Offer** node selected Open the **Properties pane** for this node, and expand the **Implementation/Execution** section
- Set the **Task Name** to: RequestOffer
- Set the **Subject** to: Request Offer for #{orderInfo.item}
- Click on the **+Add** button under **Actors** and choose **pamAdmin** (your user)

![pamAdmin]({% image_path m1p7i22_pamAdmin.png %})

- Click on the **+Add button** under **Groups** then expand the drop down list and click on **+New** 
- Type in the group name as **rest-all**, and then click on the check mark

![restAll]({% image_path m1p7i23_restAll.png %})

- Now select the new group rest-all you just created

![Actors_Groups]({% image_path m1p7i24_actors_groups.png %})

- The next step is to pass our process variable **orderInfo** to the **Request Offer** task (task input), this will hold the information that a user will provide in the **Request Offer** task and then return it to the process (task output) to be available for the next steps in the flow
- Click on the pencil icon under **Assignments**

![Assignments]({% image_path m1p7i25_assignments.png %})
