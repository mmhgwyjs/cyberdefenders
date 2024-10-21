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

***3. What was the DHCP LeaseObtainedTime?***

***4. What is the computer SID?***

***5. What is the Operating System(OS) version?***

***6. What was the computer timezone?***

***7. How many times did this user log on to the computer?***

***8. When was the last login time for the discovered account? Format: one-space between date and time***

***9. There was a “Network Scanner” running on this computer, what was it? And when was the last time the suspect used it? Format: program.exe,YYYY-MM-DD HH:MM:SS UTC***

***10. When did the port scan end? (Example: Sat Jan 23 hh:mm:ss 2016)***

***11. How many ports were scanned?***

***12. What ports were found "open"?(comma-separated, ascending)***

***13. What was the version of the network scanner running on this computer?***

***14. The employee engaged in a Skype conversation with someone. What is the skype username of the other party?***

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
