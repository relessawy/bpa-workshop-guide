# Process Modeling (15 mins)

- **Red Hat Process Automation Manager (RH PAM)** uses the [BPMN2](https://www.omg.org/bpmn/) standard to define the structure and semantics of the process.
- With the data model defined, we can now sketch out the main flow of the process, the actors, the user task nodes and the required automation decisions.
- Our use case has three main scenarios:
  - Auto-Approval
  - Manual-Approval
  - Rejection
- Let’s start by exploring the process flow for the Auto-Approval scenario

![Scenario1]({% image_path scenario1.png %})

- Once the process is triggered, the first task is for the **Procurement Manager** to **Request an Offer**
- The second task is for the supplier to **Prepare an Offer**
- The system will then auto-approve the offer, this is where the process reaches it's end node.

---

![Info]({% image_path m0_info.png %}){:align="left"}

For the remainder of this workshop we are going to refer to Red Hat Process Automation Manager by it’s short name **RH PAM**.

---

### 3.1 Explore OrderAsset process

- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project view.

![BreadcrumbNav]({% image_path m1p7i3_BreadcrumbNav.png %})

- In the drop-down menu in the upper-left corner, select **Process**.

![AddProcessMenu]({% image_path FindProcessMenu.png %})

- Click on the **OrderAsset** business process to load the process.

![ClickOrderAsset]({% image_path ClickOrderAsset.png %})

- The process will load in the **Prcess Designer** view and will look like the following image.

![IncompleteProcess]({% image_path IncompleteProcessModel.png %})

---

- This is how your process will look like when you finish this exercise, at this point it will be still missing some nodes and configurations.
- In **section 3.2** we will start editing the **OrderAsset** process to configure the missing parts.

![OrderAssetProcess]({% image_path OrderAssetProcess.png %})

---

### 3.2 Define Process Variables

- Our process will use two variables throughout it’s execution
  - The **OrderInfo** data object that we created in **Exercise 2: Data Modeling**.
  - A variable called **approved**, that will hold the result of evaluating the supplier's offer. The result can either be true or false, this type of variable is called a boolean variable.
- Open the properties editor for our process
  - Firstly click your mouse anywhere on the blank canvas of the editing screen (outside of the swimlanes). This will ensure you are editing the properties of the entire process rather than the variables of one element.
  - hover on the pencil icon to the top right of the **Process Designer** window, this is called the **Properties** pane.
  - click to open the **Properties** pane.

![PropertiesPane]({% image_path PropertiesPane.png %})

- Scroll down in the **Properties** pane, until you see the section called **Process Data**.

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

- Define two process variables as shown in the following table:

|   Name    | Data Type |
| :-------: | :-------: |
| orderInfo | OrderInfo |
| approved  |  Boolean  |

- Your **Process Variables** should look like the following screenshot when your done:

![ProcessVariable]({% image_path m1p7i13_ProcessVariable.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window. Note: It is safe to ignore warnings about missing connections for now as we didn't configure them yet.

---

### 3.3 Create Request Offer user task

- Click on the **Start Event** node, and click **Create Task** in the mini-icons (step 1 in the following diagram).
- Click on the newly created **Task** node and using the **configuration icon** below it, convert this node into a **User-task** by clicking on the **Convert Into User** mini icon (step 2 in the following diagram).
- Double Click on the **Task** node to give it the name **Request Offer**.
- Your node will now look like step 4 in the following diagram.

![RequestOfferTask]({% image_path RequestOfferTask.png %})

---

- With the **Request Offer** node selected, open the **Properties pane** for this node.
- Expand the **Implementation/Execution** section.
- Set the **Task Name** to: RequestOffer
- Copy the following text (excluding quotes): "**Request Offer for #{orderInfo.item}**" and paste it in the **Subject** field.
- Click on the **+Add** button under **Actors**.
- Select pamAdmin


---

![Info]({% image_path m0_info.png %}){:align="left"}

If the pamAdmin does not exist, you will need to create using the following steps:

- After clicking the **+Add** button under **Actors**.
- Click on **New** to create a new user.
- Enter **pamAdmin** as the user name, then click on the blue checkmark.

![pamAdmin]({% image_path CreatePamAdmin.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window. Note: It is safe to ignore warnings about missing connections for now as we didn't configure them yet.

---

- The next step is to pass our process variable **orderInfo** to the **Request Offer** task (task input), this will hold the information that the **Procurement Manager** will provide in the **Request Offer** task and then return it to the process (task output) to be available for the next steps in the flow.
- With the **Properties** pane for the **Request Offer** node open, click on the pencil icon under **Assignments**.

![Assignments]({% image_path m1p6i70_assignments.png %})

- This generates a pop-up: **Request Offer Data I/O** dialog
- Click the **+Add** button next to **Data Inputs and Assignments**
- Provide the input as follows:

Request Offer Input

|     Name     | Data Type |  Source   |
| :----------: | :-------: | :-------: |
| orderInfo_in | OrderInfo | orderInfo |

- You will only need to provide the Name, the Data Type and Source are selected from dropdown menus. Here you are selecting the OrderInfo data type and the orderInfo process variable that we created in previous steps.
- Now click the **+Add** button next to **Data Outputs and Assignments**.
- Like you did before provide the input as follows and then click **OK**.

Request Offer Output

|     Name     | Data Type |  Target   |
| :----------: | :-------: | :-------: |
| orderInfo_in | OrderInfo | orderInfo |

- It is very important that the name in the input assignments is the same as the name in the output assignments i.e. orderInfo_in.
- Your **RequestOffer Data I/O** should look something like this:

![RequestOfferAssignments]({% image_path m1p7i28_RequestOfferAssignments.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window. Note: It is safe to ignore warnings about missing connections for now as we didn't configure them yet.

---

- Decrease your Process Designer view (Zoom Out), to about 70%.
- It is important that you can see the full process for the next step to work smoothly

![ZoomOut]({% image_path ZoomOut.png %})

- Click on the **Request Offer** task and click on the mini icon **Create Sequence Flow**
  ![CreateSequenceFlow]({% image_path create_squence_flow.png %})
- Drag the sequence flow to connect the **Request Offer** task to the **Prepare Offer** task
- Click on the **Sequence Flow** to create a bending point
- Click on the bending point and drag it along tha canvas (across lanes) to shape the **Sequence Flow** as shown in the below screenshots

![PrepareOfferSequenceFlow]({% image_path m1p7i31_PrepareOfferSequenceFlow.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

### 3.4 Configure Prepare Offer user task

- Now that the **Purchasing Manager** has requested an offer, the next step in our process is that the **Supplier** prepares an offer.
- Let's configure the **Prepare Offer** user task

- Similar to what we did before, click on the **Prepare Offer** task
- With the **Prepare Offer** node selected, open the **Properties** pane for this node, and expand the **Implementation/Execution** section and set the the attributes as follows:

  - **Actors**: pamAdmin
  - **Assignments**: Same as before, and as per the following tables

  **Prepare Offer Data Inputs**

|     Name     | Data Type |  Source   |
| :----------: | :-------: | :-------: |
| orderInfo_in | OrderInfo | orderInfo |

**Prepare Offer Data Outputs**

|     Name     | Data Type |  Target   |
| :----------: | :-------: | :-------: |
| orderInfo_in | OrderInfo | orderInfo |

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

- At this point you have modeled the process for a happy scenario where the asset will always get approved, since the "Auto Approval" task explicitly sets the variable "approved" to true.
- As part of Exercise 6 **Rule Authoring** you will enrich this process to use business rules to evaluate the received offers and approve or reject offers accordingly.
- In the next exercise you will start creating the forms that allow users to interact with a task in the process.
- Well done! Now go ahead and mark Exercise 3 Process Modeling as complete for your user in the Google sheet.
