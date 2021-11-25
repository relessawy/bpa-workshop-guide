# Data Modeling (15 mins)

With the project imported, we can now start building our solution starting with the data model that will be used in our process. Each process creates, and manipulates data. This data is defined by process variables stored within the process. In **Process Automation Manager**, these process variables can be either pre-defined types, like String, Date, Boolean … etc, or you can create new data objects for your project. In this lab we are going to create a new data object called **OrderInfo**.

---

### 2.1 Create Data Object

- In this lab, we will create a new data object to capture the order information. This data object will have four attributes:

  1. Item Name: The name of the item we want to order.
  2. Supplier Name: The name of the supplier to provide the offer.
  3. Urgency: The level of urgency for this order, this can be either high or low.
  4. Target Price: The desired price for purchasing the item as determined by the procurement department.
  5. Supplier Price: The price provided in the supplier's offer.

---

- In your project, click on the **Add Asset** button to the top right of the screen.

![AddAsset]({% image_path AddAssetButton.png %})

---

- In the drop-down menu **All** in the upper-left corner, select **Model**.

![AddModelMenu]({% image_path m1p6i2_DataObjectTile.png %})

---

- Click on the **Data Object** tile.

![DataObjectTile]({% image_path DataObjectTile.png %}){:width="600px”}

---

- Fill in the data object details as follows and then click the **+OK** button.
  - **Name**: OrderInfo
  - **Package**: Leave the default value.
  - **JPA Persistable**: Leave unchecked.

![CreateDataObject]({% image_path m1p6i3_CreateDataObject.png %}){:width="600px”}

---

### 2.2 Add fields to OrderInfo

- You are now using the **Data Modeler** component.

![DataModeller]({% image_path m1p6i4_DataModeller.png %}){:width="600px”}

- In the **general properties** input the label **Order Info**

![AddLabel]({% image_path m1p6i5_AddLabel.png %}){:width="600px”}

---

- Click on the **+add field** button to open the **New Field** dialog, and start adding fields to the job object.

![AddFIELD]({% image_path m1p6i11_AddField2.png %}){:width="600px”}

- Add the first field **item** to the **OrderInfo** object, with the following details:

  - Id: item
  - Label: Item Name
  - Type: String

- Click the **Create and Continue** button to continue adding fields.

![AddFieldDialog]({% image_path m1p6i7_AddFieldDialog.png %}){:height="600px" width="700px"}

---

- Continue adding the **OrderInfo** object fields as shown in the table below.
- Be careful when selecting data types, make sure you select **float** and not **Float**.
- Once you provide the input for the last field **supplierPrice**, click **Create** instead of **Create and Continue**.

|  Identifier   |     Label      |  Type  |
| :-----------: | :------------: | :----: |
|   supplier    | Supplier Name  | String |
|    urgency    |    Urgency     | String |
|  targetPrice  |  Target Price  | float  |
| supplierPrice | Supplier Price | float  |

---

![Info]({% image_path m0_info.png %}){:align="left"}

If you make a mistake, you can edit the fields by clicking into the field you want to modify and then the field properties will show on the right. In this case where the targetPrice was mistakenly created as a String, you can edit and change it to float as desired

![EDITFIELD]({% image_path m1p6i8_EditField.png %}){:width="600px”}

---

- When you’ve added all the fields, save the data object by clicking on the **Save** button in the top menu.

![SaveDataObject]({% image_path SaveDataObject.png %}){:width="600px”}

---

![Info]({% image_path m0_info.png %}){:align="left"}

This has saved your changes and created a save entry called a **Commit** into the internal source control repository (what the developer persona will call a GIT repo) of **Red Hat Process Automation Manager**.

---

- Click on the **Source** tab, notice that **Red Hat Process Automation Manager (RH PAM)** generated the Java code on your behalf. This is an example of how **RH PAM** supports the developer’s persona, where a developer can collaborate with a business analyst using his/her favorite IDE to build the data model.

---

- Congratulations! You’ve just created your first asset in **Red Hat Process Automation Manager**.
- Now mark Exercise 2 Data Modeling as complete for your user in the Google sheet.
- We are now ready to start with our process design, let’s get started!
