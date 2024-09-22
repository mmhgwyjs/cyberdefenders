# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/insider//">Insider Lab</a>

**Platform:** CyberDefenders

**Scenario:** Our intrusion detection system has alerted us to suspicious behavior on a workstation, pointing to a likely malware intrusion. A memory dump of this system has been taken for analysis. Your task is to analyze this dump, trace the malware’s actions, and report key findings. This analysis is critical in understanding the breach and preventing further compromise.

**Category:** Endpoint Forensics

**Difficulty:** Easy

**File:** ``

**Tools:** ``

> [Volatility](https://github.com/volatilityfoundation/volatility3) is the world's most widely used framework for extracting digital artifacts from volatile memory (RAM) samples.  

**Note:** In this walkthrough, I will use the SIFT Workstation from SANS to analyze the provided file. If you have not set it up yet, I highly recommend following this [forensics lab](https://github.com/mmhgwyjs/forensics-lab/blob/main/README.md) guide for assistance with your installation.

## **Questions and Answers**

***1. What distribution of Linux is being used on this machine?***

***2. What is the MD5 hash of the apache access.log?***

***3. It is believed that a credential dumping tool was downloaded. What is the file name of the download?***

***4. There was a super-secret file created. What is the absolute path?***

***5. What program used didyouthinkwedmakeiteasy.jpg during execution?***

***6. What is the third goal from the checklist Karen created?***

***7. How many times was apache run?***

***8. It is believed this machine was used to attack another. What file proves this?***

***9. Within the Documents file path, it is believed that Karen was taunting a fellow computer expert through a bash script. Who was Karen taunting?***

***10. A user su'd to root at 11:26 multiple times. Who was it?***

***11. Based on the bash history, what is the current working directory?***
