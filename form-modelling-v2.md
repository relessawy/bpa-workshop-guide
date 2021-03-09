# Form Modelling (15 mins)

In this section we are going to create the **Process Start** and **Request Offer** user-task forms.

### 1.7.1 Create Process Start form

- Let’s start by modeling the form that triggers the process to start
- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project
- click on the **Add Asset** button to the top right of the screen.

![AddAsset]({% image_path AddAssetButton.png %})

- In the drop-down menu in the upper-left corner, select **Form**
- Click on the **Form** tile
- In the **Create new Form** dialog, provide the following input
  - Form: Leave empty, this will be auto populated when you finish select the business process
  - Package: Leave default value
  - Keep the Business Prrocess radio box selected
  - Select Process: select **OrderAsset** from the drop down list
  - Select Form: select **Start Process Form**
  - Do not change the Form name that is generated for you
  - Click the **+Ok** button

![StartForm]({% image_path m2p3i9_StartForm.png %})
- In the **Form Modeler** expand the **Form Controls** sections to the left

![HTMLControl]({% image_path m2p3i16_HTMLControl.png %})

- Drag an HTML control to the canvas
- Click on the **Insert Image** icon

![InsertImage]({% image_path m2p3i10_InsertImage.png %})
- Enter the following URL in the **Image:** field
`https://static.redhat.com/libs/redhat/brand-assets/latest/corp/logo.svg`

- **Alignment**: Default 
- Remove the text "Add your HTML here..." at the bottom
- Click the **OK** button

![ImageDialog]({% image_path m2p3i11_ImageDialog.png %})

- Drag another HTML control to the canvas, in the white area below the image HTML you just created
- Type "To start the procurement process click on the Submit button"
- Highlight the text
- Modify your text format to H3 + Bold 
- Click the **OK** button

![TextDialog]({% image_path m2p3i12_TextDialog.png %})

---
![Save]({% image_path m0_save.png %}){:align="left"}

Remember to save your form.
---

- Your form should now look like this screenshot

![FinishedStartForm]({% image_path m2p3i13_FinishedStartForm.png %})


### 1.7.2 Create Request Offer user form

- Now let's model the form that the **Purchasing Manager** will use to request an asset e.g. laptop
- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project
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


- You are now in the **Form Modeler** view
- Expand the Model Fileds list to the left of the **Form Modeler**

![ModelFieldsList]({% image_path ModelFieldsList.png %})

- Drag the **item** field from the list to your form
- Change the properties of the **item** field as follows
  - Field Type: select **ListBox** from drop down list
  - Label: Leave default value
  - Click the **+New Instance** button, provide the input **macbook pro** for both the **Value** and **Text** fields, then press the **Accept** button
  - Once again click the **+New Instance** button, provide the input **microsoft surface** for both the **Value** and **Text** fields, then press the **Accept** button
  - Check the **Required** checkbox
  - Help Message: List of assets to request
  - Click the **+OK** button

![ItemFieldProperties]({% image_path ItemFieldProperties.png %})

- Now drag the **urgency** filed from the list to your form below the **item** field
- Change the properties of the **item** field as follows
  - Field Type: Radio Group 
  - Click the **+New Instance** button, provide the input **low** for both the **Value** and **Text** fields, then press the **Accept** button
  - Once again click the **+New Instance** button, provide the input **high** for both the **Value** and **Text** fields, then press the **Accept** button
  - Check the **Show Options inline** checkbox
  - Check the **Required** checkbox
  - Help Message: Level of request urgency, high or low. 
  - Click the **+OK** button

![UrgencyFieldProperties]({% image_path UrgencyFieldProperties.png %})

- Finally drag the **targetPrice** filed from the list to your form below the **item** field
- Change the properties of the **item** field as follows
  - Field Type: Keep as **DecimalBox**
  - Check the **Required** checkbox
  - Help Message: The target price for the requested asset.
  - Click the **+OK** button

![targetPriceFieldProperties]({% image_path targetPriceFieldProperties.png %})

- Your form should look like this when you're done

![CompletedRequestForm]({% image_path CompletedRequestForm.png %})

- Save your form 
- Navigate back to the **procurement-process** project 
- click on the **Add Asset** button to the top right of the screen.
- In the drop-down menu in the upper-left corner, select **Form**
- Click on the **Form** tile
- Provide the following input
  - Form: Leave empty, this will be auto populated
  - Package: Leave default value
  - Keep the Business Process radio box selected
  - Select Process: select **OrderAsset** from the drop down list
  - Select Form: select **Task Form for Request Offer**
  - Click the **+Ok** button

![RequestFormDialog]({% image_path RequestFormDialog.png %})

- In the **Form Modeler** view, expand the Model Fileds list to the left of the **Form Modeler**
- Drag the **orderinfo_in** component to the form
- In the Field Properties dialog, change the following fields
  - Change the label to be **Request Order Form**
  - Expand the **Nested Form** drop down list and select the value **OrderForm-RequestAsset**
- Click the **+Ok** button

---
![Save]({% image_path m0_save.png %}){:align="left"}

Remember to save your form.
---

 - Now mark Excercise 4 Form Modeling as complete for your user in the etherpad.
 - In the next exercise we will get to see our process in action as we test the first use case 




















