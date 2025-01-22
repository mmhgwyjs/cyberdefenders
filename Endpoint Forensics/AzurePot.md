# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/azurepot/">AzurePot</a>

**Platform:** CyberDefenders

**Scenario:** This Ubuntu Linux honeypot was put online in Azure in early October to watch what happens with those exploiting CVE-2021-41773.

Initially, there was a large number of crypto miners that hit the system. You will see one cron script meant to remove files named kinsing in /tmp. This was a way of preventing these miners so more interesting things could occur.

There are three files:
    – sdb.vhd.gz – VHD of the main drive obtained through an Azure disk snapshot 
    – ubuntu.20211208.mem.gz – Dump of memory using Lime
    – uac.tgz – Results of UAC running on the system

Items were obtained in the order above – the drive was snapshotted, memory was grabbed, then UAC was run.

As a SOC Analyst, analyze the artifacts and answer the questions.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**File:** `memory.dmp`

**Tools:** 
FTK Imager
Notepad++
grep
awk

**Note:** In this walkthrough, I will use our Forensic Workstation to analyze the provided file. If you have not set it up yet, I highly recommend following this [forensics lab](https://github.com/mmhgwyjs/forensics-lab/blob/main/README.md) guide for assistance with your installation.

---

## **Preparations**


## **Questions and Answers**

***1. `File => sdb.vhd` There is a script that runs every minute to do cleanup. What is the name of the file?***  

.remove.sh

/var/spool/cron/crontabs/

![image](https://github.com/user-attachments/assets/034c20d6-b8af-45b8-aa9f-208fd6cb53c3)

![image](https://github.com/user-attachments/assets/0d288c15-92c5-4af3-a5dd-85dc0ae1ce49)

***2. `File => sdb.vhd` The script in Q#1 terminates processes associated with two Bitcoin miner malware files. What is the name of 1st malware file?***  

kinsing

![image](https://github.com/user-attachments/assets/63a16bb6-f8b2-404a-a36a-b9cea01553a4)


***3. `File => sdb.vhd` The script in Q#1 changes the permissions for some files. What is their new permission?***  
Solved: 455  

444

![image](https://github.com/user-attachments/assets/77505a86-1bd9-4b3d-b9d5-d85fa695604e)

***4. `File => sdb.vhd` What is the sha256 of the botnet agent file?***  
Solved: 410  
`SHA256 Hash`  

***5. `File => sdb.vhd` What is the name of the botnet in Q#4?***  
Solved: 406  
`*******`  

***6. `File => sdb.vhd` What IP address matches the creation timestamp of the botnet agent file in Q#4?***  
Solved: 390  
`***.***.**.**`  

***7. `File => sdb.vhd` What URL did the attacker use to download the botnet agent?***  
Solved: 368  
`URL(e.g.,http://138.1...)`  

***8. `File => sdb.vhd` What is the name of the file that the attacker downloaded to execute the malicious script and subsequently remove itself?***  
Solved: 330  
`.*******`  

***9. `File => sdb.vhd` The attacker downloaded sh scripts. What are the names of these files?***  
Solved: 333  
`*_****.**, *_*****.**, **.**`  

***10. `File => UAC` Two suspicious processes were running from a deleted directory. What are their PIDs?***  
Solved: 330  
`****, *****`  

***11. `File => UAC` What is the suspicious command line associated with the 2nd PID in Q#10?***  
Solved: 325  
`** .***.**`  

***12. `File => UAC` UAC gathered some data from the second process in Q#10. What is the remote IP address and remote port that was used in the attack?***  
Solved: 316  
`***.***.***.**:*****`  

***13. `File => UAC` Which user was responsible for executing the command in Q#11?***  
Solved: 317  
`******`  

***14. `File => UAC` Two suspicious shell processes were running from the tmp folder. What are their PIDs?***  
Solved: 297  
`*****, *****`  

***15. `File => ubuntu.20211208.mem` What is the MAC address of the captured memory?***  
Solved: 296  
`**:**:**:**:**:**`  

***16. `File => ubuntu.20211208.mem` From Bash history. The attacker downloaded an sh script. What is the name of the file?***  
Solved: 301  
`*******`  


This should now be ready for you to copy and paste directly!
