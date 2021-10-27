# Test Scenario Creation (15 mins)

Test scenarios enable you to validate the functionality of the rules you author in Red Hat Process Automation Manager. With a test scenario, you use data from your project to set given conditions and expected results based on one or more defined business rules. When you run the scenario, the expected results and actual results of executing the rule are compared. If the expected results match the actual results, the test is successful, otherwise the test fails.

---

- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project.
- Click on the **Add Asset** button.
- Select **Decision** from the drop-down menu in the upper-left corner, and click on the **Test Scenario** tile.
- Provide input to the dialog as follows then click in the **+OK** button:
  - **Test Scenario:** test-order-approval.
  - **Source type:** DMN.
  - **DMN asset:** order-approval.dmn.

![CreateTSDialog]({% image_path m2p2i1_CreateTSDialog.png %})

---

![Info]({% image_path m0_info.png %}){:align="left"}

Note that the Test Scenario editor has already detected the inputs and output of your rule and created a table for you to provide the input for your test scenarios and the expected output.

---

![TestScenarion]({% image_path m2p2i2_TestScenarion.png %})

- Each row in the table represents a **test scenario**, we will create 4 test scenarios:
  - **High urgency approve:** Order with high urgency, supplierPrice < targetPrice
  - **High urgency reject:** Order with high urgency, supplierPrice > targetPrice
  - **Low urgency approve:** Order with low urgency, supplierPrice < targetPrice
  - **Low urgency reject:** Order with low urgency, supplierPrice > targetPrice

---

- Complete the 4 test scenarios using the details in the following image:

![FullTests]({% image_path FullTests.png %})

---

![Save]({% image_path m0_save.png %}){:align="left"}

Save your progress: Click on the **Save** button at the top of the window.

---

- Once your done, click the **run** button and observe the **Test Report**

![TestResults]({% image_path TestResults.png %})

---

- Select the **Coverage Report** option to see details of each scenario run.

![CoverageReport]({% image_path CoverageReport.png %})

---

- You have now completed this exercise, please go ahead and mark it as complete in the Google sheet.
