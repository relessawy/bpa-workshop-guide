# Process Modelling (40 mins)

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

### 1.3.1 Create OrderAsset process

- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project view

![BreadcrumbNav]({% image_path m1p7i3_BreadcrumbNav.png %})

- Click on the Add Asset button

![AddAsset]({% image_path m1p7i4_AddAsset.png %})

- In the drop-down menu in the upper-left corner, select Process

![AddProcessMenu]({% image_path m1p7i5_AddProcessMenu.png %})

- Click on the **Business Process** tile

![ProcessTile]({% image_path m1p7i6_ProcessTile.png %})

Name your process **OrderAsset**, and click on the **+OK** button

![AddProcessDialog]({% image_path m1p7i7_AddProcessDialog.png %})


---
![Info]({% image_path m0_info.png %}){:align="left"} 

It is common practice to use [Pascal](https://techterms.com/definition/pascalcase) case for business process names i.e. the practice of writing compound words or phrases in which the first letter of each concatenated word is capitalized.

---

- The **OrderAsset** process opens in the **Process Designer**

![ProcessDesigner]({% image_path m1p7i8_ProcessDesigner.png %})

### 1.3.2 Define Process Variables

- Our process will manipulate two variables through it’s execution
 - The **OrderInfo** data object that we created in part 1.2 of this lab.
 - A bollean variable **approved**, that will hold the result of evaluating the supplier's offer
- Open the properties editor for our process
 - Firstly click your mouse anywhere on the blank canvas of the editing screen. This will ensure you are editing the properties of the entire process rather than the variables of one element.
 - hover on top right pencil icon in designer
 - click to open the **Properties pane** on the right
 
 ![PropertiesPane]({% image_path m1p7i9_PropertiesPane.png %})

- Scroll down in the property panel on the right side of the screen, until you see the section Process Data.
![ProcessVariables]({% image_path m1p7i10_ProcessVariables.png %})


---
![Info]({% image_path m0_info.png %}){:align="left"} 

HINT: Don’t see a process data screen like this? 
If you see something that looks like the screen below, then you will need to select the BPMN canvas. Just click your mouse anywhere in that blank on the editing grid.

![WrongProperties]({% image_path m1p7i11_WrongProperties.png %})

---

- Expand the **Process Data** section
- Next click on the plus sign ‘+’ to define a new process variable


