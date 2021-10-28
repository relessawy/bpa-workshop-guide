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
- In the **Import Project** Dialog, provide the URL: **https://github.com/relessawy/procurement-process-web**
- Click on the **Import** button.
- Now click on the **procurement-process** tile to select it, then click on the **Ok** button to the top right.

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

- Select a laptop model from the carousel, then click the **Request Laptop** button.

![RequestLaptop]({% image_path NewRequestLaptop.png %})

- Go back to **Business Central**
- Navigate to Menu → Manage → Process Instances.
- Note that a new process is created and as you can expect it is waiting at the **Reuest Offer** task node

![NewProcess]({% image_path NewProcess.png %})

---

### 8.6 Request Offer

- In this step we will assume the role of the **Procurement Manager** and request an Offer.
- Click on the **Procurement Manager** view in the top navigation menu.
- In the **Procurement Manager** view, click on **Request Offer** from the sidebar.

![NewRequestOffer]({% image_path NewRequestOffer.png %})

- The **Procurement Manager** can now pick a laptop request to work on.
- Click the **Go** button next to a request.

![GoButton]({% image_path GoButton.png %})

- You are now in the **Request Offer** form.
- Keep the urgency as high.
- Enter the **Target Price** as 4000.
- Click the **Submit Offer** button.

![RequestOfferForm]({% image_path RequestOfferForm.png %})

- You are now in the **Orders** view
- Click on the **View** button next to your Order.
- Note that the process has progressed and is now waiting at the **Prepare Offer** step.

![ViewOrder]({% image_path ViewOrder.png %})

### 8.7 Prepare Offer

- In this step we will assume the role of the **Supplier** and prepare an Offer.
- In the **Supplier** view, click on **Prepare Offer** from the sidebar.
- Click the **Go** button next to a request.

- You are now in the **Prepare Offer** form.
- Enter the **Supplier Price** as 6000.
- Click the **Submit Offer**"** button.

- You are now in the **Orders** view
- Click on the **View** button next to your Order.
- Note that the process has progressed and is now waiting at the **Manual Approval** step.

---

### 8.8 Manual Approval

- In this step we will assume the role of the **Procurement Manager** and manually approve an Offer.
- Click on the **Procurement Manager** view in the top navigation menu.
- In the **Procurement Manager** view, click on **Approve Offers** from the sidebar
- Choose whether to approve the offer or not, them click the **Approve Order** button.
- You can now check your process status from **Business Central**
