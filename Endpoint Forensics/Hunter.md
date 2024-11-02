# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/hunter//">Hunter</a>

**Platform:** CyberDefenders

**Scenario:** The SOC team got an alert regarding some illegal port scanning activity coming from an employee's system. The employee was not authorized to do any port scanning or any offensive hacking activity within the network. The employee claimed that he had no idea about that, and it is probably a malware acting on his behalf. The IR team managed to respond immediately and take a full forensic image of the user's system to perform some investigations.

There is a theory that the user intentionally installed illegal applications to do port scanning and maybe other things. He was probably planning for something bigger, far beyond a port scanning!

It all began when the user asked for a salary raise that was rejected. After that, his behavior was abnormal and different. The suspect is believed to have weak technical skills, and there might be an outsider helping him!

Your objective as a soc analyst is to analyze the image and to either confirm or deny this theory.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `Hunter.ad1` `Hunter.ad1.txt`

**Tools:** `FTK Imager` `Autopsy` `Registry Explorer` `MFTECmd.exe` `Timeline Explorer`

> [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) is a free data preview and imaging tool used to acquire electronic evidence in a forensically sound manner by creating copies of computer data without making changes to the original evidence.

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Questions and Answers**

***1. What is the computer name of the suspect machine?***

4ORENSICS
Windows/System32/config/System
![image](https://github.com/user-attachments/assets/09bdb1d1-216a-468f-9fe7-3690231011ca)
ftk

![image](https://github.com/user-attachments/assets/87a3f39a-1953-40c4-973f-1d9e9585ab9d)
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName
registry explorer

***2. What is the computer IP?***

10.0.2.15

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces

![image](https://github.com/user-attachments/assets/61066529-ecf7-4e4e-a17e-babdfb19f7ae)

***3. What was the DHCP LeaseObtainedTime?***
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces

21/06/2016 02:24:12 UTC

![image](https://github.com/user-attachments/assets/6365d6f6-0070-4d2b-a166-61b18b7ef8ba)
1466475852

![image](https://github.com/user-attachments/assets/3b421103-d60e-4516-8977-e1ea1a792af8)
using DCODE tool

***4. What is the computer SID?***

S-1-5-21-2489440558-2754304563-710705792

![image](https://github.com/user-attachments/assets/2f519c14-526a-4df7-b737-db25a3c539fe)

![image](https://github.com/user-attachments/assets/97b9204f-4a9c-4b62-af9e-cc246a675218)

***5. What is the Operating System(OS) version?***
8.1

![image](https://github.com/user-attachments/assets/c7d0732a-2af7-4103-b794-076170d72426)

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProductName

***6. What was the computer timezone?***

UTC-07:00

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation\TimeZoneKeyName

![image](https://github.com/user-attachments/assets/6c1f3717-74e8-40aa-8393-54a73684043e)



***7. How many times did this user log on to the computer?***

3

![image](https://github.com/user-attachments/assets/0b78669d-b287-4b44-ae1f-54db445d88e9)

evtxecmd.exe -f Security.evtx --csv . --csvf security.csv

![image](https://github.com/user-attachments/assets/0b648cdf-4a43-4896-9357-9713c373d284)


![image](https://github.com/user-attachments/assets/454af54f-8041-4dce-a481-9154caba7c38)

SAM\Domains\Account\Users

***8. When was the last login time for the discovered account? Format: one-space between date and time***

![image](https://github.com/user-attachments/assets/c7be30f3-c133-4b77-8a5b-4cf826fcbbe3)

2016-06-21 01:42:40

***9. There was a “Network Scanner” running on this computer, what was it? And when was the last time the suspect used it? Format: program.exe,YYYY-MM-DD HH:MM:SS UTC***

zenmap.exe,2016-06-21 12:08:13 UTC

![image](https://github.com/user-attachments/assets/4fb7192f-7582-486e-a652-b91272b3a355)

pecmd -f ZENMAP.EXE-56B17C4C.pf

![image](https://github.com/user-attachments/assets/6054212e-c7c8-4bbe-b64c-625d6f83bcb8)

***10. When did the port scan end? (Example: Sat Jan 23 hh:mm:ss 2016)***

Tue Jun 21 05:12:09 2016

![image](https://github.com/user-attachments/assets/09e631aa-5a55-4505-8f23-8f4e32579dfb)

![image](https://github.com/user-attachments/assets/a6388224-7d6e-4943-b2a9-2e7602c39a93)

![image](https://github.com/user-attachments/assets/67cfee78-bc70-49a3-9b2c-1674b09b63de)

***11. How many ports were scanned?***

1000

![image](https://github.com/user-attachments/assets/b540b5ba-5906-4bc9-9dab-9348ebea4eec)

***12. What ports were found "open"?(comma-separated, ascending)***

![image](https://github.com/user-attachments/assets/0d9ec4c7-7373-48a5-98d2-16444baeb4f9)

22,80,9929,31337

***13. What was the version of the network scanner running on this computer?***

7.12

![image](https://github.com/user-attachments/assets/ec342eec-0641-4b5f-9ef5-4dbfd8937ed9)

***14. The employee engaged in a Skype conversation with someone. What is the skype username of the other party?***

linux-rul3z

![image](https://github.com/user-attachments/assets/e1a4e934-b262-452b-b826-42d2306b87a3)

![image](https://github.com/user-attachments/assets/239b43d0-b8c5-4099-8b88-dfd9aff3af9a)

/Users/Hunter/AppData/Roaming/Skype/hunterehpt

Chatgpt
![image](https://github.com/user-attachments/assets/0d71bc9b-a0d6-4a06-a456-16621ffd9bdc)


***15. What is the name of the application both parties agreed to use to exfiltrate data and provide remote access for the external attacker in their Skype conversation?***

***16. What is the Gmail email address of the suspect employee?***

***17. It looks like the suspect user deleted an important diagram after his conversation with the external attacker. What is the file name of the deleted diagram?***

***18. The user Documents' directory contained a PDF file discussing data exfiltration techniques. What is the name of the file?***

***19. What was the name of the Disk Encryption application Installed on the victim system? (two words space separated)***

***20. What are the serial numbers of the two identified USB storage?***

***21. One of the installed applications is a file shredder. What is the name of the application? (two words space separated)***

***22. How many prefetch files were discovered on the system?***

***23. How many times was the file shredder application executed?***

***24. Using prefetch, determine when was the last time ZENMAP.EXE-56B17C4C.pf was executed?***

***25. A JAR file for an offensive traffic manipulation tool was executed. What is the absolute path of the file?***

***26. The suspect employee tried to exfiltrate data by sending it as an email attachment. What is the name of the suspected attachment?***

***27. Shellbags shows that the employee created a folder to include all the data he will exfiltrate. What is the full path of that folder?***

***28. The user deleted two JPG files from the system and moved them to $Recycle-Bin. What is the file name that has the resolution of 1920x1200?***

***29. Provide the name of the directory where information about jump lists items (created automatically by the system) is stored?***

***30. Using JUMP LIST analysis, provide the full path of the application with the AppID of "aa28770954eaeaaa" used to bypass network security monitoring controls.***
