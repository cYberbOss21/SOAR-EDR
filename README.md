# SOAR-EDR
Implements an automated cybersecurity response system using LimaCharlie, Tines, and Slack to detect, alert, and isolate threats on a Windows server

SOAR-EDR Implementation Guide

Part 1: Design
Objectives:
  - Create a Playbook Workflow
   - Brainstorm actions to include in the playbook.

Notes:  
   Use draw.io to visualize the workflow.

   ![SOAR-EDR-Playbook](https://github.com/user-attachments/assets/1d2d41b9-b99a-4038-b144-556e1a6d4fb9)


---

Part 2: LimaCharlie Setup

1. Install and Configure LimaCharlie
   - Choose Vultr as the cloud provider to deploy a Windows Server machine.
   - Install LimaCharlie on the Windows Server to log and monitor all events.

Note:  
   Screenshot of the Windows Server setup
   
 ![image](https://github.com/user-attachments/assets/f525a3fc-afa3-43ae-af5b-8992fb4364d6)


2. Setup LimaCharlie
   
 ![image](https://github.com/user-attachments/assets/61c2754d-5516-439a-8659-e98d48daa82f)

---

Part 3: Telemetry Generation

1. Generate Telemetry with Lazagne
   - Disable Windows Security temporarily
   - Download and execute Lazagne.exe (a vulnerability demonstration tool).

*Note*:  
   - Screenshot of Lazagne running in PowerShell

	 ![image](https://github.com/user-attachments/assets/3727b9be-fcc0-4719-9a87-af478251be55)

   - LimaCharlie should detect the download of Lazagne. Include a screenshot of the detection log

![image](https://github.com/user-attachments/assets/6424af0d-fc35-4955-b579-e330df97fda8)
	 

2. Create Detection & Response (D&R) Rule
   - Navigate to Organization > Automation > D&R Rules > New Rule
   - Locate the event in the LimaCharlie logs and add it to the rule.

Note:  
   - Screenshot of the rule creation and test output

  ![image](https://github.com/user-attachments/assets/d4351971-0d40-4b0e-afc1-8d0a83b9bacb)

   ![image](https://github.com/user-attachments/assets/de643a8c-9217-41a9-9c8e-85a81ec44555)

   - Screenshot of the detection result
   
     ![image](https://github.com/user-attachments/assets/40e53b9e-3daf-4a46-840a-1949811d0d8a)

---

Part 4: Slack & Tines Integration

1. Configure Slack and Tines
   - Set up a dedicated Slack channel for notifications.
   - Configure Tines for playbook setup.

Note:  
   - Slack channel setup

      ![image](https://github.com/user-attachments/assets/2f2077dd-95e0-4fee-ac20-9017fe92d978)

 
Tines

 ![image](https://github.com/user-attachments/assets/b0f1e3d5-4c89-4c09-b4bc-ed37fb5c7822)


2. Connect Tines with LimaCharlie
   - Go to Sensors > Outputs > Add Output > Detections > Tines in LimaCharlie.
   
*Note*:  

   ![image](https://github.com/user-attachments/assets/abd036b6-25ec-4af5-9eab-65abdca616f4)

![image](https://github.com/user-attachments/assets/864fce46-d3f8-49d1-9523-35a1ee37eb0f)

---

Part 5: Automation and Playbook Creation

1. Develop the Playbook
   - Objective: Automate responses including sending a Slack message, an email with detection details, and generating a user prompt for machine isolation.
   - If the response is “Yes,” proceed to isolate the affected machine.

Note:  
   - screenshot of the playbook and, a demo video

![image](https://github.com/user-attachments/assets/b0b3f0ed-e56b-41dd-a883-1f933272a0d2)
![image](https://github.com/user-attachments/assets/77f429cf-a6a2-4f25-ad08-7ec6feab94cf)

[Watch the demo video](https://youtu.be/qPmlcFBHhtY)


 
*Note: 
Clicking the link in the Slack message or email takes you directly to the specific LimaCharlie event, providing detailed insights for further investigation.*
---

Takeaways

- Created Custom Detection & Response Rules with LimaCharlie.
- Developed a response playbook incorporating Tines, Slack, and email notifications.
- Enhanced response capabilities to include automated machine isolation based on user prompts.
