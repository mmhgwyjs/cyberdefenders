# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/amadey/">Amadey</a>

**Platform:** CyberDefenders

**Scenario:** An after-hours alert from the Endpoint Detection and Response (EDR) system flags suspicious activity on a Windows workstation. The flagged malware align with the Amadey Trojan Stealer. Your job is to analyze the presented memory dump and create a detailed report for actions taken by the malware.

**Category:** Endpoint Forensics

**Difficulty:** Easy

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

![image](https://github.com/user-attachments/assets/d4b2e29e-1bc8-4503-bf02-4c358417d750)

/home/ubuntu/Desktop/Start\ here/Tools/volatility3/vol.py -f Windows\ 7\ x64-Snapshot4.vmem windows.info > info.txt
![image](https://github.com/user-attachments/assets/83794ca7-3df7-4ced-a638-19683f224c5e)
![image](https://github.com/user-attachments/assets/fb8c82b7-2888-415e-8775-29a19e6f9fbf)

/home/ubuntu/Desktop/Start\ here/Tools/volatility3/vol.py -f Windows\ 7\ x64-Snapshot4.vmem windows.psscan > psscan.txt
/home/ubuntu/Desktop/Start\ here/Tools/volatility3/vol.py -f Windows\ 7\ x64-Snapshot4.vmem windows.pslist > pslist.txt

  
## **Questions and Answers**

***1. In the memory dump analysis, determining the root of the malicious activity is essential for comprehending the extent of the intrusion. What is the name of the parent process that triggered this malicious behavior?***

![image](https://github.com/user-attachments/assets/c7cec646-1a50-455f-a3e0-f0974fc69209)

![image](https://github.com/user-attachments/assets/ea34f8b1-7253-48a9-936b-31b910d9f2a3)

lssass.exe

![image](https://github.com/user-attachments/assets/b12046c8-d9e6-450e-8d71-8941802670d4)

***2. Once the rogue process is identified, its exact location on the device can reveal more about its nature and source. Where is this process housed on the workstation?***

C:\Users\0XSH3R~1\AppData\Local\Temp\925e7e99c5\lssass.exe

![image](https://github.com/user-attachments/assets/78487975-0e50-4cee-a6dd-7a94a61bc41e)
/home/ubuntu/Desktop/Start\ here/Tools/volatility3/vol.py -f Windows\ 7\ x64-Snapshot4.vmem windows.cmdline > cmdline.txt

***3. Persistent external communications suggest the malware's attempts to reach out to a Command and Control (C2C) server. Can you identify the Command and Control (C2C) server IP that the process interacts with?***

![image](https://github.com/user-attachments/assets/2f8cc3c6-bdaa-478a-838c-20800a32fe32)

41.75.84.12

***4. Following the malware link with the C2C, the malware is likely fetching additional tools or modules. How many distinct files is it trying to bring onto the compromised workstation?***

/home/ubuntu/Desktop/Start\ here/Tools/volatility3/vol.py -f Windows\ 7\ x64-Snapshot4.vmem -o /home/ubuntu/Desktop/Start\ here/Artifacts/ windows.memmap --dump --pid 2748 

![image](https://github.com/user-attachments/assets/24afd034-89d2-46f0-bce8-943f89436986)

2

strings pid.2748.dmp | grep 41.75.84.12

***5. Identifying the storage points of these additional components is critical for containment and cleanup. What is the full path of the file downloaded and used by the malware in its malicious activity?***


C:\Users\0xSh3rl0ck\AppData\Roaming\116711e5a2ab05\clip64.dll

![image](https://github.com/user-attachments/assets/4adc6150-1066-4d13-89c4-af12ab24c865)


***6. Once retrieved, the malware aims to activate its additional components. Which child process is initiated by the malware to execute these files?***

rundll32.exe

![image](https://github.com/user-attachments/assets/2ab18f41-d628-451c-afc9-c3d9477c56f6)

![image](https://github.com/user-attachments/assets/80308066-7f73-4e7c-8d5b-6c7a34bba299)


***7. Understanding the full range of Amadey's persistence mechanisms can help in effective mitigation. Where else might the malware be ensuring its consistent presence?***

![image](https://github.com/user-attachments/assets/5370106c-fe38-4505-ac2e-e37e74d40856)

C:\Windows\System32\Tasks\lssass.exe

