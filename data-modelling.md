#  Data Modelling (15 mins)

With the project created, we can now start building our solution starting with the data model to be used in our process and rules. Each process creates, and manipulates data. This data is defined by process variables stored within the process. In **Process Automation Manager**, these process variables can be either pre-defined types, like String, Date, Boolean … etc, or you can create new data objects for your project. 

In this workshop, we will create a new data object to capture the order information.

- In your project, click on the **Add Asset** button in the middle of the screen.
- In the drop-down menu in the upper-left corner, select **Model**. 

![AddModelMenu]({% image_path m1p6i1_AddModelMenu.png %})

- Click on the **Data Object** tile

![DataObjectTile]({% image_path m1p6i2_DataObjectTile.png %}){:width="600px”}

- Give the Data Object the name **OrderInfo**. Leave the package set to default, and leave the JPA Persistable option unchecked.
- Click the **+OK** button

![CreateDataObject]({% image_path m1p6i3_CreateDataObject.png %}){:width="600px”}

- You are now using the **Data Modeler** component 

![DataModeller]({% image_path m1p6i4_DataModeller.png %}){:width="600px”}

- In the **general properties** input the label ‘Order Info’ 

![AddLabel]({% image_path m1p6i5_AddLabel.png %}){:width="600px”}

-- Click on the **+add field** button to open the pop-up editor, and start adding properties to the job object

![AddFIELD]({% image_path m1p6i6_AddField.png %}){:width="600px”}

- Add the first property ‘orderId’ to the OrderInfo object, with the details shown below
  - Id: item
  - Label: item name
  - Type: String
  
- Click the Create and Continue button to continue adding properties

![AddFieldDialog]({% image_path m1p6i7_AddFieldDialog.png %}){:width="400px”}

-- Continue adding the ‘Order Info’ object properties as shown in the table below
-- Once you provide the input for the last attribute ‘approved’, click **Create** instead of **Create and Continue**

|  Identifier   |    Label       |      Type     |
| ------------- | -------------- | ------------- |
|    item       |  Item Name     |     String    |
|   supplier    | Supplier Name  |     String    |
|   urgency     |    Urgency     |     String    |
| targetPrice   | Target Price   |     float     |
| supplierPrice | Supplier Price |     float     |

