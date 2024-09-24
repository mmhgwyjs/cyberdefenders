# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/kerberoasted/">Kerberoasted</a>

**Platform:** CyberDefenders

**Scenario:** Our intrusion detection system has alerted us to suspicious behavior on a workstation, pointing to a likely malware intrusion. A memory dump of this system has been taken for analysis. Your task is to analyze this dump, trace the malware’s actions, and report key findings. This analysis is critical in understanding the breach and preventing further compromise.

**Category:** Threat Hunting

**Difficulty:** Medium

**Files:** `FirstHack.ad1` `FirstHack.ad1.txt` ``

**Tools:** `FTK Imager`

> [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) is a free data preview and imaging tool used to acquire electronic evidence in a forensically sound manner by creating copies of computer data without making changes to the original evidence.

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Questions and Answers**

***1. What encryption type is currently in use within the network?***

![image](https://github.com/user-attachments/assets/c51b8cae-c5e0-4578-8e54-a9ee89e8a1dd)
![image](https://github.com/user-attachments/assets/2b4bba81-3fd9-47c1-8106-68f566019503)
![image](https://github.com/user-attachments/assets/87376024-19bf-4651-adee-9a9691ad226a)


RC4-HMAC

***2. What is the username of the account that sequentially requested Ticket Granting Service (TGS) for two distinct application services within a short timeframe?***

![image](https://github.com/user-attachments/assets/51c8b736-6a5a-4751-a328-1ae96b025d42)


***3. Can you provide the account name of the compromised service account?***

***4. What is the machine's IP address?***

***5. Can you specify the service name installed on the Domain Controller (DC)?***

***6. What's the complete registry key path where the attacker modified the value to enable Remote Desktop Protocol (RDP)?***

***7. What is the UTC timestamp of the first recorded Remote Desktop Protocol (RDP) login event?***

***8. What is the name of the WMI event consumer responsible for maintaining persistence?***

***9. Which class does the WMI event subscription filter target in the WMI Event Subscription you've identified?***
