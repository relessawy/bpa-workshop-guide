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
