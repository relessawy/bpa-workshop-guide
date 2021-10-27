# Form Modeling (10 mins)

- In this section we are going to create the **Request Offer** user-task form.
- The rest of the forms have been already created for you and you will see them in action in **Exercise 5 Run Process**

### 4.1 Create Request Offer user form

- Let's model the form that the **Procurement Manager** will use to request an asset e.g. laptop.
- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project.
- click on the **Add Asset** button to the top right of the screen.

![AddAsset]({% image_path AddAssetButton.png %})

- In the drop-down menu in the upper-left corner, select **Form**
- Click on the **Form** tile
- In the **Create new Form** dialog provide the following input
  - Form: **OrderForm-RequestAsset**
  - Package: Leave default value
  - Select Model type: Click the **Data Object** radio button
  - Select Data Object from project: select **com.myspace.procurement_process.OrderInfo** from the drop down list
- Click the **+OK** button

---

- You are now in the **Form Modeller** view
- Expand the Model Fields list to the left of the **Form Modeller**

![ModelFieldsList]({% image_path ModelFieldsList.png %})

- Drag the **item** field from the list to your form
- Change the properties of the **item** field as follows:
  - Field Type: select **ListBox** from drop down list.
  - Label: Leave default value.
  - Click the **+New Instance** button, provide the input **macbook pro** for both the **Value** and **Text** fields, then press the **Accept** button.
  - Once again click the **+New Instance** button, provide the input **microsoft surface** for both the **Value** and **Text** fields, then press the **Accept** button.
  - Check the **Required** checkbox.
  - **Do not** check the **Read Only** checkbox.
  - Help Message: **List of assets to request**.
  - Click the **+OK** button.

![ItemFieldProperties]({% image_path ItemFieldProperties.png %})

---

- Now drag the **urgency** filed from the list to your form below the **item** field.
- Change the properties of the **urgency** field as follows:
  - Field Type: **Radio Group**.
  - Click the **+New Instance** button, provide the input **low** for both the **Value** and **Text** fields, then press the **Accept** button.
  - Once again click the **+New Instance** button, provide the input **high** for both the **Value** and **Text** fields, then press the **Accept** button.
  - Check the **Show Options inline** checkbox.
  - Check the **Required** checkbox.
  - **Do not** check the **Read Only** checkbox.
  - Help Message: **Level of request urgency, high or low**.
  - Click the **+OK** button.

![UrgencyFieldProperties]({% image_path UrgencyFieldProperties.png %})

---

- Finally drag the **targetPrice** filed from the list to your form below the **urgency** field
- Change the properties of the **targetPrice** field as follows:
  - Field Type: Keep as **DecimalBox**.
  - Check the **Required** checkbox.
  - **Do not** check the **Read Only** checkbox.
  - Help Message: **The target price for the requested asset**.
  - Click the **+OK** button.

![targetPriceFieldProperties]({% image_path targetPriceFieldProperties.png %})

- Your form should look like this when you're done

![CompletedRequestForm]({% image_path CompletedRequestForm.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

- Now mark Exercise 4 Form Modeling as complete for your user in the Google sheet.
- In the next exercise we will get to see our process in action as we test the first use case.
