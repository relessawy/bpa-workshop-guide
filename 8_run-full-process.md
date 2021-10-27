
# Deploy and Run the full process (15 mins)

### 8.1 Create new Space

- Using the breadcrumbs navigation, navigate back to Spaces.
- Click on the **Add Space** button to the top right.
- In the **Add Space** dialog, give the new Space the name **NewSpace**.
- Click the **Add** button.
- Click on the **NewSpace** tile.

---

### 8.2 Import Full Project

- Click the **Import Project** button.
- In the **Import Project** Dialog, provide the URL: **https://github.com/relessawy/procurement-process-web**.
- Click on the **Import** button.
- Now click on the **procurement-process**  tile to select it, then click on the **Ok** button to the top right.

---

### 8.3 Deploy full project

- With the full project now loaded in the new Space we created, feel free to explore the complete business process.
- We can now package our project and deploy it on the Execution Server.
- Click on the **Deploy** button in the upper-right corner of the screen. This will package and deploy our project.
- If all goes well, you'll see two green pop-ups verifying the deployment

![SuccessMsg]({% image_path m2p5_SuccessMsg.png %})

---

### 8.4 Run the complete process

- In this section, you will execute the process deployed on the **Execution Server** from the **Order Management** application.
- Open the application from the URL provided in the Google sheet for your user.
- The first thing you will see is the **Home** page.

![HomePage]({% image_path HomePage.png %})

---

### 8.5 Request Laptop

- In this step we will assume the role of the **Employee** and request a laptop.
- Click on the **Employee** view in the top navigation menu.
- In the **Employee** view click on **Request Laptop** from the sidebar.

![EmployeeHome]({% image_path EmployeeHome.png %})

- Select a laptop model from the carousel, then click the **Reuest Laptop** button.

![RequestLaptop]({% image_path NewRequestLaptop.png %})

- Go back to **Business Central**
- Navigate to Menu → Manage → Process Instances.
- Note that a new process is created and as you can expect it is waiting at the **Reuest Offer** task node

![NewProcess]({% image_path NewProcess.png %})

---

### 8.6 Request Offer

- In this step we will assume the role of the **Procurement Manager** and request an Offer.
- Click on the **Procurement Manager** view in the top navigation menu.
- In the **Procurement Manager** view click on **Request Offer** from the sidebar.

- Click on the **Diagram** tab to open the process instance diagram and view the full process

![ProcessDiagram]({% image_path m2p6i5_ProcessDiagram.png %})

- Just like last time, the process is in a **wait** state at the **Request Offer** task. 
- Navigate to Menu → Track -> Task Inbox

![TaskInbox]({% image_path m2p6i6_TaskInbox.png %})


- And again the  **Request Offer** task will be waiting for you in your inbox

![RequestOfferTask]({% image_path m2p6i7_RequestOfferTask.png %})

- Click on the **Request Offer** task to open its task window

![OpenRequestOfferTask]({% image_path m2p6i8_OpenRequestOfferTask.png %})

- Click on the **Start** button to start working on the task. 
- Fill in the request form as follows:
- **Item name**: MackBook Pro
- **Urgency**: high
- **Target Price**: 100
- Then click the Complete button  

![FilledRequestOfferTask]({% image_path m2p6i9_FilledRequestOfferTask.png %})

- The next task **Prepare Offer** is now assigned to you in your inbox

![PrepareOfferTask]({% image_path m2p6i13_PrepareOfferTask.png %})

- Click on the Prepare Offer task in your inbox, then click the **Start** button
- Enter 130 for SupplierPrice
- Ignore the Supplier Name field
- Click the **Complete** button

![PrepareOfferTaskComplete]({% image_path m2p6i14_PrepareOfferTaskComplete.png %})

- Navigate to Menu-> Manage ->Process Instance
- Click on the **OrderAsset** process instance
- In the Process Instance screen, click on the **Diagram** tab
- Notice that because the supplier's offer was higher than target price even with the high tolerance (130 > 100*1.25), so the **Auto Approval** rule was evaluated to **false** and we progressed to the **Manual Approval** task

![ProcessDesignAtManualApproval]({% image_path m2p6i15_ProcessDesignAtManualApproval.png %})

- Navigate back to your Inbox (Menu -> Track -> Task Inbox), and is you might expect the **Manual Approval** task is now waiting for you

![ManualApprovalTask]({% image_path m2p6i16_ManualApprovalTask.png %})

- Click on the **Manual Approval** task in your inbox, then click the **Start** button
- Check the **Approved** field 
- Click the **Complete** button

![ManualApprovalComplete]({% image_path m2p6i17_ManualApprovalComplete.png %})

- Navigate to Menu-> Manage ->Process Instance
- Like last time, in the **Filters list** to the left, click on the **Completed** state, now your completed processes are visible
- Click on the **OrderAsset** process instance with id 2 (or highest id if you ran the process multiple times)
- In the Process Instance screen, click on the **Diagram** tab
- Notice that the process has reach the end event **Send to ERP**

![m2p6i19_FinishProcess]({% image_path m2p6i19_FinishProcess.png %})

- Run a couple more process instances with different values to test, for example, the functionality of the Automated Approval Rules.
- Once you are done, please go ahead and mark this exercise as complete in the google sheet.

