# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/sysinternals/">Sysinternals</a>

**Platform:** CyberDefenders

**Scenario:** A user thought they were downloading the SysInternals tool suite and attempted to open it, but the tools did not launch and became inaccessible. Since then, the user has observed that their system has gradually slowed down and become less responsive.

As a SOC Analyst, analyze the artifacts and answer the questions.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `SysInternals.E01`

**Tools:** `FTK Imager` `Autopsy` `Registry Explorer` `MFTECmd.exe` `Timeline Explorer`

> [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) is a free data preview and imaging tool used to acquire electronic evidence in a forensically sound manner by creating copies of computer data without making changes to the original evidence.

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/ab7c4e12-adec-419b-8f1c-8ef0f61776cf)


## **Questions and Answers**

***1. What was the malicious executable file name that the user downloaded?***  
**Answer: `SysInternals.exe`**

![image](https://github.com/user-attachments/assets/8ba97c14-6021-438b-b8dc-109bbae05b4e)

***2. When was the last time the malicious executable file was modified?***  
**Answer: `11/15/2022 09:18:51 PM`**

![image](https://github.com/user-attachments/assets/5c62e966-e4c1-4a04-a148-7c76fbf1eded)

***3. What is the SHA1 hash value of the malware?***  
**Answer: `****************************************`**

***4. What is the malware's family?***  
**Answer: `******`**

***5. What is the first mapped domain's Fully Qualified Domain Name (FQDN)?***  
**Answer: `***.**********.***`**

***6. The mapped domain is linked to an IP address. What is that IP address?***  
**Answer: `***.***.**.**`**

***7. What is the name of the executable dropped by the first-stage executable?***  
**Answer: `*********.***`**

***8. What is the name of the service installed by the 2nd stage executable?***  
**Answer: `*********************`**

***9. What is the extension of files deleted by the 2nd stage executable?***  
**Answer: `**********`**
