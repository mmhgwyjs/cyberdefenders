# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/amadey/">Amadey</a>

**Platform:** CyberDefenders

**Scenario:** An after-hours alert from the Endpoint Detection and Response (EDR) system flags suspicious activity on a Windows workstation. The flagged malware align with the Amadey Trojan Stealer. Your job is to analyze the presented memory dump and create a detailed report for actions taken by the malware.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `N/A`

**Tools:** `Volatility` 

**Note:** In this walkthrough, CyberDefenders offers a lab environment for us to utilize. This feature is included with the PRO subscription.

## **Preparations** 

![image](https://github.com/user-attachments/assets/e651d0b7-f69c-485a-97e5-3361fdda03ba)

https://blog.onfvp.com/post/volatility-cheatsheet/

![image](https://github.com/user-attachments/assets/145204b0-0838-4561-ab9d-28debfc9bb82)

![image](https://github.com/user-attachments/assets/b8920fe9-c0c3-4f62-8d2c-870441590b18)

![image](https://github.com/user-attachments/assets/072a20f0-3f60-4984-999f-8923b3518d5f)

![image](https://github.com/user-attachments/assets/7c2e2720-e128-4691-aae4-0e8d34945ed8)

The VM is slow
  
## **Questions and Answers**


***1. In the memory dump analysis, determining the root of the malicious activity is essential for comprehending the extent of the intrusion. What is the name of the parent process that triggered this malicious behavior?***


***2. Once the rogue process is identified, its exact location on the device can reveal more about its nature and source. Where is this process housed on the workstation?***

***3. Persistent external communications suggest the malware's attempts to reach out to a Command and Control (C2C) server. Can you identify the Command and Control (C2C) server IP that the process interacts with?***

***4. Following the malware link with the C2C, the malware is likely fetching additional tools or modules. How many distinct files is it trying to bring onto the compromised workstation?***


***5. Identifying the storage points of these additional components is critical for containment and cleanup. What is the full path of the file downloaded and used by the malware in its malicious activity?***


***6. Once retrieved, the malware aims to activate its additional components. Which child process is initiated by the malware to execute these files?***



***7. Understanding the full range of Amadey's persistence mechanisms can help in effective mitigation. Where else might the malware be ensuring its consistent presence?***


