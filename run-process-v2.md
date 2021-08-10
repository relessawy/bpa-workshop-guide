# Deploy and Run the Process (5 mins)

### 1.8.1 Deploy the process

- With our process, data model and forms ready, we can now package our project and deploy it on the Execution Server. To do this:
- Go back to our project’s Library View, by clicking on the **procurement-process** link in the breadcrumb navigation in the upper-left of the screen.
- Click on the **Deploy** button in the upper-right corner of the screen. This will package our project in a Deployment Unit called KJAR and deploy it onto the Execution Server (KIE-Server).

![DeployProcess]({% image_path m2p4_DeployProcess.png %})

- If all goes well, you'll see two green pop-ups verifying the deployment

![SuccessMsg]({% image_path m2p5_SuccessMsg.png %})

### 1.8.2 Run the process

- In this section, you will execute the process deployed on the Process Execution Server via the Business Central workbench
- Navigate to Menu → Manage → Process Definitions. 

![ProcessDef]({% image_path m2p6_ProcessDef.png %})

- If everything is correct, the order-management process will be listed. 
- Click on the kebab icon of the order-management process and click on **Start** to run the process.

![StartProcess]({% image_path m2p6i2_StartProcess.png %})

- You will be greeted with the start form that we created in the previous step
- Click the **Submit** button

![StartForm]({% image_path m2p6i3_StartForm.png %})

- You are now in the **Process Instance Details** screen, note that the instance state is active and the active user task is **Request Offer** as expected

![ProcessInstance]({% image_path m2p6i4_ProcessInstance.png %})


- Click on the **Diagram** tab to open the process instance diagram
- The process instance Diagram shows the current state of the process, which path was taken, and what is the current active step

![ProcessDiagram]({% image_path ProcessDiagram.png %})

- The process is in a **wait** state at the **Request Offer** task. 
- Navigate to Menu → Track -> Task Inbox

![TaskInbox]({% image_path m2p6i6_TaskInbox.png %})


- Remember when we set the actor for the **Request Offer** task to pamAdmin (your user) in the process model?  This is why **RH PAM** assigned this task to your user and notified you with message in your inbox

![RequestOfferTask]({% image_path m2p6i7_RequestOfferTask.png %})

- Click on the **Request Offer** task to open its task window

![OpenRequestOfferTask]({% image_path TestRequestForm.png %})

- Click on the **Start** button to start working on the task. 
- Fill in the request form as follows:
- **Item name**: macbook pro
- **Urgency**: high
- **Target Price**: 100
- Then click the **Complete** button  

- Navigate to Menu-> Manage ->Process Instances
- Click on the **OrderAsset** process instance

![OrderAssetProcessInstance]({% image_path m2p6i10_OrderAssetProcessInstance.png %})

- In the Process Instance screen, click on the **Diagram** tab
- The process has now progressed to the **Prepare Offer** task node. 

![ProcessProgressToPrepareOffer]({% image_path ProcessDiagram_PrepareOffer.png %})

- You can also click on the Logs tab to get more details on which user claimed a task, when it was started, updated, and completed

![Logs]({% image_path m2p6i12_Logs.png %})

- Now navigate to Menu -> Track -> Task Inbox again, where you'll find the next task **Prepare Offer** waiting for you

![PrepareOfferTask]({% image_path m2p6i13_PrepareOfferTask.png %})

- Click on the Prepare Offer task in your inbox, then click the **Start** button
- Enter 130 for SupplierPrice
- Do not worry about the Supplier Name, it has been intentionally left out of this lab
- Click the **Complete** button

![PrepareOfferTaskComplete]({% image_path m2p6i14_PrepareOfferTaskComplete.png %})

- Navigate to Menu-> Manage ->Process Instance
- In the **Filters** to left select the **Completed** status to be part of the **Active filters**
- The **Order Asset** will now appear, click on it's process instance
- In the Process Instance screen, click on the **Diagram** tab
- Notice that because the supplier's offer was approved the process reached the end state **Send to ERP**

![ProcessDesignAtManualApproval]({% image_path testProcessFinished.png %})


- This concludes the exercises for this module, please go ahead and mark exercise 5 Deploy and Run the process as completed in the googles sheet.






