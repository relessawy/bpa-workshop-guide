# Rule Authoring (20 mins)

In this section we will implement the automatic approval rule in the form of a DMN model.

---

### 6.1 Create a new DMN rule

- Navigate back to your project, Menu-> Design-> Projects.
- Use the breadcrumb navigator at the top-left of the screen to navigate back to our **procurement-process** project.
- Click on the blue **Add Asset** button in the top-right corner.
- Select **Decision** from the drop-down menu in the upper-left corner.
- Click on the **DMN** tile.

![DMNTile]({% image_path m2p1i1_DMNTile.png %}){:width="600px”}

- In the **Create new DMN** dialog give the rule the name **order-approval** , and click the **+OK** button.

![DMNNewDialog]({% image_path m2p1i1_CreateNewDMN.png %})

- You now see the **DMN Editor** view.
- In the **DMN Editor**, open the **Properties** pane on the right-side of the screen.
- Copy the URL **http://www.redhat.com/pam-workshop/procurement-process-dmn** to the **Namespace** field.

![NameSpace]({% image_path m2p1i3_NameSpace.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

### 6.2 Create Data Types for rule

- We will use two data types in our **DMN Model**.
  - An enumerator called **urgency** to restrict the possible values to high or low.
  - The data model **OrderInfo** that we created in the previous module.
- We will start by creating the **urgency** enumerator.
- In the **DMN editor**, click on the Data Types tab

![DataTypes]({% image_path m2p1i4_DataTypes.png %})

- Click on the **Add a custom Data Type** button

![AddCustomerDataType]({% image_path m2p1i5_AddCustomerDataType.png %})

- In the editor provide the following:
  - **Name**: urgency
  - **Type**: string (from the drop down list).

![UrgencyType]({% image_path m2p1i6_UrgencyType.png %})

- Click the **Add Constraints** link.
- Select constraint type as **Enumeration** from the drop down list.
- Provide the value **high**, then click on the check mark.
- Click the **+Add** button.
- Provide the value **low**, then click on the check mark.
- Click the **OK** button.

![AddConstraintsDialog]({% image_path m2p1i7_AddConstraintsDialog.png %})

- Click the check mark to the far right to save the new data type.

![SaveConstraint]({% image_path m2p1i8_SaveConstraint.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

- Next we want to import the **OrderInfo** data object into our DMN model.
- Click on the **Import Data Object** button.
- Select the **OrderInfo** object, and click the **Import** button.

![ImportData]({% image_path m2p1i9_ImportData.png %})

- If all goes well you should see a confirmation in green indicating that the Data Object was converted into a DMN data type successfully.

![ImportSuccess]({% image_path m2p1i10_ImportSuccess.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

### 6.3 Create Order Info Input

- The next sep is to create the input to our rule.
- Navigate back to the DMN model by clicking on the **Model** tab.
- From the left menu, drag a **DMN input** data to the canvas.

![DMNInputMenu]({% image_path m2p1i60_DMNInputData.png %})

- Double click on the DMN input, and give it the name **Order Information**

---

![Info]({% image_path m0_info.png %}){:align="left"}

Unlike many traditional expression languages, Friendly Enough Expression Language (FEEL) supports spaces and a few special characters as part of variable and function names.

---

- Open **Diagram Properties** for this input, click the **Data Type** drop down list and select the new data type we just imported: **OrderInfo**.

![OrderInfoInput]({% image_path m2p1i12_OrderInfoInput.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

### 6.4 Create Price Tolerance Business Knowledge Model

- We now want to create a **Business Knowledge model** that calculates the price tolerance based on the urgency of the order

---

![Info]({% image_path m0_info.png %}){:align="left"}

A Business Knowledge Model element (BKM) represents a reusable piece of decision logic. Typically, it is connected to a Decision element which invokes the BKM and passes on a set of inputs. The BKM, using it's internal logic, evaluates an output which is passed back to the Decision.

---

- From the left menu, drag a **DMN Business Knowledge Model** element to the canvas.
- Double click on it to give it the name **Price Tolerance**.

![BKM]({% image_path m2p1i13_BKM.png %})

- Click on the **Price Tolerance** node, and the click on the **Edit** button to start editing the node

![BKMEdit]({% image_path m2p1i14_BKMEdit.png %})

- You now see the boxed expression of this node, feel free to resize it to your convenience

![PriceToleranceBoxedEx]({% image_path m2p1i15_PriceToleranceBoxedEx.png %})

- Click on the **Edit Parameters** link, an editor will open.
- Click on **Add parameter** button.
- Name the parameter **order info**.
- Set the type to **OrderInfo** from the drop down list.
- Click anywhere outside the **Edit Parameters** dialog to return to the **Price Tolerance Function editor**.

![PriceTolerance_Input]({% image_path m2p1i16_PriceTolerance_Input.png %})

- Right click in the empty white cell under the parameter definitions and select **Clear**. The text **Select expression** will appear in the cell.
- Click on the cell and select **Decision Table**.

![DecisionTableExpression]({% image_path m2p1i17_DecisionTableExpression.png %})

- Click in the header of the first column (input-1) to add an input to the decision table
- The name of the input clause is **order info.urgency**, which references the urgency attribute of the order information parameter.
- Set the type to **urgency**, which references the **urgency** enumeration we created earlier.
- The first column of a decision table is the condition that will be evaluted, i.e. high or low.

![orderinfo_urgency]({% image_path m2p1i18_orderinfo_urgency.png %})

- Similarly set the name of the output clause to **Price Tolerance** and data type to **number**.
- The last column of a decision table is the action that will be taken, i.e. set the value for  Price Tolerance.

![DecisionTableOutput]({% image_path m2p1i19_DecisionTableOutput.png %})

- Click on the Price Tolerance cell (top cell of the table), and set the data type to number. This means that our decision table will return a number.

![BKM_Output]({% image_path m2p1i20_BKM_Output.png %})

- Implement the first row of the decision table as follows:

![DT_FirstRow]({% image_path m2p1i21_DT_FirstRow.png %})

- Note that you must inclue the quotes for the value "high".
- Now click the validate button in the upper right menu.

![ValidateButton]({% image_path m2p1i22_ValidateButton.png %})

- Review the alerts listed at the bottom of the screen.
- Note that the modeler detects a gap in the rules you specified in the table because one of the possible values of the enumerator Urgency is missing, i.e. you need to define a rule for the value “low”.
- The warnings "Missing DMNShape" can be ignored.

![ValidateError]({% image_path m2p1i23_ValidateError.png %})

- Define the second rule in the decision table as follows and save your model.
- To add a rule, right click on the Decision table and click on **insert below**.
- Note that you must inclue the quotes for the value "low".

![FinalDecisionTable]({% image_path m2p1i24_FinalDecisionTable.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

### 6.5 Create Approve Decision Node

- Navigate back to the model by clicking on the **Back to order-approval** link at the top-left of the editor.
- Drag a **DMN Decision** node to the canvas.
- Double click on it to nd name it **Approve**.

![ApproveDecisionNode]({% image_path m2p1i25_ApproveDecisionNode.png %})

- Connect the **Order Information** input and the **Price Tolerance** business knowledge model node to the **Approve** decision node.

![ConnectDMNModel]({% image_path m2p1i26_ConnectDMNModel.png %})

- Select the **Approve** decision node and click on the **Edit** button.
- Click on **Select Expression**, and set the logic type to **Literal Expression**.

![DecisionLiteralExpression]({% image_path m2p1i27_DecisionLiteralExpression.png %})

- Click on the **Approve** cell (top cell of the table), and set the data type to **boolean**.
- Click anywhere in the canvas outside of the **Edit Expression** dialog.
- Copy the following expression, then Double click on the white cellto paste it inside that cell.

`Order Information.supplierPrice < Price Tolerance(Order Information) * Order Information.targetPrice`

- Again feel free to resize the boxed expression.
- On the right hand side of this expression we are calling our Business Knowledge Model **Price Tolerance** to calculate the price tolerance, i.e. if the order is urgent we will have a tolerance of 25%.
- So this expression is evaluated to true if the supplier price is less than the target price multiplied by the price tolerance.
- Let's assume that the target price is 4000 and the urgency is high, then the right hand side evaluates to 5000.
- The rule will then evaluate if the supplier price is less than 5000 and return true or false.

![RuleExpression]({% image_path m2p1i28_RuleExpression.png %})

- Navigate back to the model by clicking on the **Back to order-approval** link at the top-left of the editor.
- Our DMN model is now complete.

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

- Mark **Exercise 6 Rule Authoring** as complete for your user in the Google sheet.
- We are now ready to test the rule we just created in the next exercise.
