# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/krakenkeylogger/">KrakenKeylogger</a>

**Platform:** CyberDefenders

**Scenario:** An employee at a large company was assigned a task with a two-day deadline. Realizing that he could not complete the task in that timeframe, he sought help from someone else. After one day, he received a notification from that person who informed him that he had managed to finish the assignment and sent it to the employee as a test. However, the person also sent a message to the employee stating that if he wanted the completed assignment, he would have to pay $160.

The helper's demand for payment revealed that he was actually a threat actor. The company's digital forensics team was called in to investigate and identify the attacker, determine the extent of the attack, and assess potential data breaches. The team must analyze the employee's computer and communication logs to prevent similar attacks in the future.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `challenge directory`

**Tools:** `FTK Imager` `Autopsy` `Registry Explorer` `MFTECmd.exe` `Timeline Explorer`

> [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) is a free data preview and imaging tool used to acquire electronic evidence in a forensically sound manner by creating copies of computer data without making changes to the original evidence.

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided files. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**


## **Questions and Answers**

***1. What is the the web messaging app the employee used to talk to the attacker?***

***2. What is the password for the protected ZIP file sent by the attacker to the employee?***

***3. What domain did the attacker use to download the second stage of the malware?***

***4. What is the name of the command that the attacker injected using one of the installed LOLAPPS on the machine to achieve persistence?***

***5. What is the complete path of the malicious file that the attacker used to achieve persistence?***

***6. What is the name of the application the attacker utilized for data exfiltration?***

***7. What is the IP address of the attacker?***
