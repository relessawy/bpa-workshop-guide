# Process Modelling (30 mins)

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



### 1.6.1 Create OrderAsset process

- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project view

![BreadcrumbNav]({% image_path m1p7i3_BreadcrumbNav.png %})

- Click on the Add Asset button

![AddAsset]({% image_path m1p7i4_AddAsset.png %})

- In the drop-down menu in the upper-left corner, select Process

![AddProcessMenu]({% image_path m1p7i5_AddProcessMenu.png %})

- Click on the **Business Process** tile

![ProcessTile]({% image_path m1p7i6_ProcessTile.png %})

Name your process **OrderAsset**, and click on the **+OK** button

![AddProcessDialog]({% image_path m1p7i7_AddProcessDialog.png %}){:height="300px" width="500px"}


---
![Info]({% image_path m0_info.png %}){:align="left"} 

It is common practice to use [Pascal](https://techterms.com/definition/pascalcase) case for business process names i.e. the practice of writing compound words or phrases in which the first letter of each concatenated word is capitalized.

---

- The **OrderAsset** process opens in the **Process Designer**

![ProcessDesigner]({% image_path m1p7i8_ProcessDesigner.png %})

### 1.6.2 Define Process Variables

- Our process will manipulate two variables throughout it’s execution
  - The **OrderInfo** data object that we created in part 1.5.1 of this module.
  - A variable **approved**, that will hold the result of evaluating the supplier's offer. The result can either be true or false, this type of variable is called a boolean variable
- Open the properties editor for our process
  - Firstly click your mouse anywhere on the blank canvas of the editing screen. This will ensure you are editing the properties of the entire process rather than the variables of one element.
  - hover on top right pencil icon in designer
  - click to open the **Properties pane** on the right
 
 ![PropertiesPane]({% image_path m1p7i9_PropertiesPane2.png %})

- Scroll down in the property panel on the right side of the screen, until you see the section **Process Data**.
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

- Define a process variable as shown in the following table:

|      Name    |     Data Type  |
|     :---:    |     :---:      |
| orderInfo    | OrderInfo      |
| approved     | Boolean        |

- Your **Process Variables** should like the following screenshot when your done:


![ProcessVariable]({% image_path m1p7i13_ProcessVariable.png %})



### 1.6.3 Create Swim Lanes

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

![SwimLanes]({% image_path m1p7i17_SwimLanes.png %}){:height="300px" width="500px"}



### 1.6.4 Create Start Event

- In the palette on the left-side of the editor, click on the **Start Events** icon then select the **Start** node

![StartEventMenu]({% image_path m1p7i18_StartEventMenu.png %})

- Click again inside the Purchasing Manager lane to place a start node there

![StartEvent]({% image_path m1p7i19_StartEvent.png %})


---
![Info]({% image_path m0_info.png %}){:align="left"} 

Clicking on a node/event displays a set of mini icons that you can use to configure the node/event or create the next task in the process. This is another way to add nodes/events in addition to the left side menu

![MiniIcons]({% image_path m1p7i20_MiniIcons.png %})

---

### 1.6.5 Create Request Offer user task

- Click on the **Start Event** node, and click **Create Task**
- Click on the task node again and using the configuration icon below it, convert this node into a **Usertask** by clicking on the **Convert Into User** mini icon
- Double Click on the node to give it the name **Request Offer**

![RequestOfferTask]({% image_path m1p7i21_RequestOfferTask.png %})

- With the **Request Offer** node selected Open the **Properties pane** for this node 
- Expand the **Implementation/Execution** section
- Set the **Task Name** to: RequestOffer
- Set the **Subject** to: Request Offer for #{orderInfo.item}
- Click on the **+Add** button under **Actors** and choose **pamAdmin** (your user)

![pamAdmin]({% image_path m1p7i22_pamAdmin.png %})

- The next step is to pass our process variable **orderInfo** to the **Request Offer** task (task input), this will hold the information that a user will provide in the **Request Offer** task and then return it to the process (task output) to be available for the next steps in the flow
- Click on the pencil icon under **Assignments**

![Assignments]({% image_path m1p6i70_assignments.png %})

- This generates a pop-up: **Request Offer Data I/O** dialog
- Click the **+Add** button next to **Data Inputs and Assignments** 
- Provide the input as follows:

Request Offer Input

|      Name    |    Data Type   |      Source   |
|     :---:    |     :---:      |     :---:     |
| orderInfo_in | OrderInfo      | orderInfo     |

- You will only need to provide the Name, the Data Type and Source are selected from dropdown menus. You are selecting the OrderInfo data type and the orderInfo process variable that we created in previous steps.
- Now click the **+Add** button next to **Data Outputs and Assignments**
- Like you did before provide the input as follows and then click **OK**
- It is very important that the name in the input assignments is the same as the name in the output assignments i.e. orderInfo_in

Request Offer Output


|      Name    |    Data Type   |      Target   |
|     :---:    |     :---:      |     :---:     |
| orderInfo_in | OrderInfo      | orderInfo     |

- Your **RequestOffer Data I/O** should look something like this:

![RequestOfferAssignments]({% image_path m1p7i28_RequestOfferAssignments.png %})


### 1.6.6 Create Prepare Offer user task

- Now that the Purchasing Manager has requested an offer, the next step in our process is that the chosen Supplier prepares an offer
- In the palette on the left-side of the editor, click on the **Tasks** icon then select the User task

![UserTaskMenu]({% image_path m1p7i29_UserTaskMenu.png %})

- Click within the **Supplier** lane to place the **User** task
- Double click to give it the name **Prepare Offer**

![PrepareOfferTask]({% image_path m1p7i30_PrepareOfferTask.png %})

- Click on the **Request Offer** task and click on the mini icon **Create Sequence Flow**
- Drag the sequence flow to connect the **Request Offer** task to the **Prepare Offer** task
- Click on the **Sequence Flow** to create a bending point
- Click on the bending point and drag it along tha canvas (across lanes) to shape the **Sequence Flow** as shown in the below screenshots

![PrepareOfferSequenceFlow]({% image_path m1p7i31_PrepareOfferSequenceFlow.png %})

- With the **Prepare Offer** node selected Open the **Properties** pane for this node, and expand the **Implementation/Execution** section and set the the attributes as follows:
  - **Task Name**: PrepareOffer
  - **Subject**: Prepare Offer for #{orderInfo.item}
  - **Actors**: pamAdmin
  - **Assignments**: Same as before, and as per the following tables
 
 **Prepare Offer Data Inputs**


|      Name    |    Data Type   |      Source   |
|     :---:    |     :---:      |     :---:     |
| orderInfo_in | OrderInfo      | orderInfo     |
 
 **Prepare Offer Data Outputs**


|      Name    |    Data Type   |      Target   |
|     :---:    |     :---:      |     :---:     |
| orderInfo_in | OrderInfo      | orderInfo     |
 
 

---
![Save]({% image_path m0_save.png %}){:align="left"} 

Remember to save your progress 

---

### 1.6.7 Create AutoApproval business rule task 

- In this step we will create the task that calls the business rule to decide whether the order can be auto -approved or not
- In the palette on the left-side of the editor, click on the **Tasks** icon then select the Business Rule task

 ![businessRuleTaskMenu]({% image_path m1p7i35_businessRuleTaskMenu.png %})

- Click within the **System** lane to place the User task
- Double click to give it the name **Auto Approval**
- Click on the **Prepare Offer** task and click on the mini icon **Create Sequence Flow**
- Drag the sequence flow to connect the **Prepare Offer** task to the **Auto Approval** task and shape it like in the following screenshot

  ![AutoApprovalFlow]({% image_path m1p7i36_AutoApprovalFlow.png %})
  
- Select the  **Auto Approval** node, and then open the **Properties** pane for this node
- Expand the **Implementation/Execution** section
- Set **Rule language** to **DMN**
- Now expand the **Data Assignments** section and provide the following assignments and then click the **Ok** button

**Auto Approval Data Inputs**

|      Name         |    Data Type   |      Source   |
|     :---:         |     :---:      |     :---:     |
| Order Information | OrderInfo      | orderInfo     |

**Auto Approval Data Outputs**

|      Name    |    Data Type   |      Target   |
|     :---:    |     :---:      |     :---:     |
| Approve      |   Boolean     |   approved     |

---
![Info]({% image_path m0_info.png %}){:align="left"} 

In module 2 after we finish modeling our rules, we will revisit the configuration of this node to reference the rule we create

---


### 1.6.8 Create Check Auto Approval gateway

- We will now create a diverging bridge to allow the process to progress in one of two directions:
 - Auto Approval is true -> Go ahead and insert the order in the [Enterprise Resource System (ERP)](https://en.wikipedia.org/wiki/Enterprise_resource_planning)
 - Auto Approval is false -> Assign the order to the **Purchasing Manager** for review 
- Click on the **Auto Approval** task to show it’s mini icons
- Click on **Create Parallel**
- Click on the newly created gateway to show it’s mini icons
- Use it’s configuration icon (the one below the gateway) to convert it into an **Exclusive Gateway (X-OR)** by clicking on the **Convert Into Exclusive** icon
- Name this X-OR gate: **Check Auto Approval**

![CreateAutoApprovalTask]({% image_path m1p7i39_CreateAutoApprovalTask.png %})

### 1.6.9 Import Complete Project

- Now that you've had a chance to try the **Process Designer**, you can do one of two things
  - Import the full project, skip module 1 part 7 and move on to module 2 (Recommended)
  - Continue to build the process step by step in module 1 part 7
 
 
- In this section we will guide you through the steps to import the complete project, if you want to build the process yourself skip this section and move on to module 1 part 7
   - Before you import the full **OrderAsset** process, you will need to delete the one you already created. It's a good idea to keep a copy of your process
   - Download the process you created by clicking the **Download** button in the upper menu
   - Delete the the current **OrderAsset** process by clicking the **Delete** button in the upper menu
  
  ![DownloadDelete]({% image_path m1p7i91_Download_Delete.png %})
  
  - Download the full process from [here](https://drive.google.com/file/d/1VMdU5T16dRBYqIAQz9JnYoi5O3INWnx7/view?usp=sharing)
  - Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project view
  - Click on the **Import Asset** button 
  - Select the **Choose File** button, below the **Please select a file to upload** field
  
  ![ChooseFile]({% image_path m1p7i90_choosefile.png %})

- Select the OrderAsset.bpmn from the path you downloaded the file to, then click the **Open** button
- Provide the name **OrderAsset** in the **Import Asset** field
- Click the **+OK** button

![ImportProcess]({% image_path m1p7i92_ImportProcess.png %})

---
![Save]({% image_path m0_save.png %}){:align="left"} 

Remember to save your progress 

---

Your finished process diagram should like something like this


![FinalFlow]({% image_path m1p7i52_FinalFlow.png %})

With the overall layout of the process definition complete, the routing logic implemented, and the I/O assignments defined, we can now implement the business rules of our automated approval decision.

