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
**Answer: `fa1002b02fc5551e075ec44bb4ff9cc13d563dcf`**

using AmcacheParser.exe

AmcacheParser.exe -f C:\Users\flrvm2\Documents\CD\100-SysInternals\Amcache.hve --csv C:\Users\flrvm2\Documents\CD\100-SysInternals --csvf amcache.csv

![image](https://github.com/user-attachments/assets/b8fc24cf-27c8-4691-9d84-5f738df28cea)

![image](https://github.com/user-attachments/assets/ed8f7756-f3ae-4fc5-a672-4eaf08e60375)


***4. What is the malware's family?***  
**Answer: `rozena`**

![image](https://github.com/user-attachments/assets/e0acfd5c-0bf1-4c04-8919-bd86d1b489fe)

***5. What is the first mapped domain's Fully Qualified Domain Name (FQDN)?***  
**Answer: `www.malware430.com`**

![image](https://github.com/user-attachments/assets/aa830c75-81fa-4bad-b196-20bfb66f28bc)

Users\IEUser\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine

![image](https://github.com/user-attachments/assets/46427452-1893-4ee6-83a3-15d64c474b19)

***6. The mapped domain is linked to an IP address. What is that IP address?***  
**Answer: `192.168.15.10`**


***7. What is the name of the executable dropped by the first-stage executable?***  
**Answer: `vmtoolsIO.exe`**

Users/IEUser/AppData/Local/Packages/Microsoft.MicrosoftEdge_8wekyb3d8bbwe/AC/#!001/MicrosoftEdge/Cache/WMFWC1O7/SysInternals[1].exe

![image](https://github.com/user-attachments/assets/1fd6c5f4-4d71-4734-ad8a-4acec6be740d)

![image](https://github.com/user-attachments/assets/fc28cc3c-e623-4d7a-8c93-b78ecff759e1)

strings.exe "C:\Users\flrvm2\Documents\CD\100-SysInternals\SysInternals[1].exe" > sysint.txt

![image](https://github.com/user-attachments/assets/3bc9ae08-552f-4060-9d8c-f555fedc125d)

***8. What is the name of the service installed by the 2nd stage executable?***  
**Answer: VMwareIOHelperService

![image](https://github.com/user-attachments/assets/6ed6fa76-0d1a-4b61-b53f-2281bc8ba668)


***9. What is the extension of files deleted by the 2nd stage executable?***  
**Answer: `**********`**

pf
