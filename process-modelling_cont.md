# Process Modelling Cont. (30 mins)


### 1.7.1 Create Converge Approval gateway

- In this step we want to create converging gateway to allow the path coming from the auto approval and manual approval (that we will create in scenario 2) to converge at one **end event**
- Click on **Check Auto Approval** gateway to show it’s mini icons, click on the **Create Parallel** icon
- Convert the new gateway to an Exclusive Gateway (X-OR) 
- Name this gateway **Converge Approval**
- With the **Properties** pane open click on the **Sequence Flow** between the **Check Auto Approval** gateway and **Converge Approval** gateway, in the **Properties** pane give the **Sequence Flow** the name **auto approved**

![CreateConvergeApprovalGW]({% image_path m1p7i40_CreateConvergeApprovalGW.png %})


---
![Info]({% image_path m0_info.png %}){:align="left"} 

To open the **Diagram Properties** pane of a **Sequence Flow** without triggering its format feature (creating a binding point), click on it’s arrowhead instead of its body with the **Properties** pane already opened

---

### 1.7.2 Create Send to ERP end event

- Click on **Converge Approval** gateway to show it’s mini icons
- Click on Create End 
- Double click on the end event to name it **Send to ERP**

![CreateSendToERP]({% image_path m1p7i41_CreateSendToERP.png %})


We have now finished modeling our first scenario **Auto-Approval** and we will start modeling our second scenario **Manual-Approval** in the next section

![ManualApproveFlow]({% image_path m1p7i42_ManualApproveFlow.png %})

###  1.7.3 Create Manual Approval user task

- Using the left menu, create a user task in the **Purchasing Manager** lane, under the **Check Auto Approval** gateway 
- Double Click on the user task and name it **Manual Approval** 
- Click on the **Check Auto Approval** gateway and use the **Create Sequence** Flow icon to connect the **Check Auto Approval** gateway to the **Manual Approval** user task
- Name this Sequence Flow: **manual approval required**

![ManualApprovalRequired]({% image_path m1p7i43_ManualApprovalRequired.png %})

- Open the **Properties** pane for the **Manual Approval** task, and expand the **Implementation/Execution** section to provide the following properties: 
  - **Task Name**: ApproveOffer
  - **Subject**: Approve Offer of #{orderInfo.item}
  - **Actors**: pamAdmin
  - **Assignments**: As per the following tables

**Manual Approval Inputs**

|      Name    |    Data Type   |      Source   |
|     :---:    |     :---:      |     :---:     |
| orderInfo_in | OrderInfo      | orderInfo     |
| approved     |    Boolean     | approved      |

**Manual Approval Outputs**

|      Name    |    Data Type   |      Target   |
|     :---:    |     :---:      |     :---:     |
| approved     |    Boolean     | approved      |

###  1.7.4 Create Check Manual Approval gateway

- We now want to create another **Exclusive Gateway (X-OR)** in the **Purchasing Manager** swimlane, after the **Manual Approval** node.
- Click on the **Manual Approval** node, and then click on the the **Create Parallel** mini icon
- Hover over the settings icon under the gateway and click on **Convert into Exclusive** mini icon
- Name the X-OR gateway: **Check Manual Approval**

![CreateCheckManualApproval]({% image_path m1p7i46_CreateCheckManualApproval.png %})

- Click on the **Check Manual Approval** gateway to show it’s mini icons, click on **Create Sequence Flow** and connect the **Check Manual Approval** gateway with the **Converge Approval gateway**
- Name the **Sequence flow** connecting the **Check Auto Approval** gateway and the **Converge Approval** gateway: **manually approved**

![ManuallyAprrovedSequence]({% image_path m1p7i47_ManuallyAprrovedSequence.png %})

- Select the **Check Auto Approval** gateway
- Open the **Properties** pane, and expand the **Implementation/Execution** section
- Set the **Default Route** property to **Manual Approval**

![CheckAutoApprovalDefaultRoute]({% image_path m1p7i48_CheckAutoApprovalDefaultRoute.png %})

- Open the **Properties** pane for the **auto approved**  sequence flow, and expand the **Implementation/Execution** section
- We want to set the following condition, this path should be taken when the order is approved by the system:
 - **Process Variable**: approved
 - **Condition**: Is true

![AutoApproveCondition]({% image_path m1p7i49_AutoApproveCondition.png %})


---
![Tip]({% image_path m0_tip.png %}){:align="left"} 

It may seem counterintuitive at first, however the conditions for these X-OR statements don't go into the details on the Gateway properties, rather the conditions are placed on the sequence flows.  If you think that you are setting a direction path, and on that direction path line you are telling the system under what conditions it should go this way, and on the other pathway under what conditions the system should go that way - thinking of it this way makes it seem intuitive.

---

- Similarly set the following conditions for the **manually approved** sequence flow:
  - **Process Variable**: approved
  - **Condition**: Is true
 
 
We have now finished modeling our second scenario Manual-Approval and we will start modeling our final scenario Rejection

![RejectionFlow]({% image_path m1p7i50_RejectionFlow.png %})

###  1.7.5 Create Rejected end event

- Create an **End Event** node after the **Check Manual Approval** gateway and name it **Rejected**.
- Select the **Check Manual Approve** gateway, and set it’s **Default Route** to **Rejected**

![RejectionEndNode]({% image_path m1p7i51_RejectionEndNode.png %})


---
![Save]({% image_path m0_save.png %}){:align="left"} 

Remember to save your progress 

---

Your finished process diagram should like something like this


![FinalFlow]({% image_path m1p7i52_FinalFlow.png %})

With the overall layout of the process definition complete, the routing logic implemented, and the I/O assignments defined, we can now implement the business rules of our automated approval decision.
