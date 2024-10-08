# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/reveal/">Reveal</a>

**Platform:** CyberDefenders

**Scenario:** As a cybersecurity analyst for a leading financial institution, an alert from your SIEM solution has flagged unusual activity on an internal workstation. Given the sensitive financial data at risk, immediate action is required to prevent potential breaches.

Your task is to delve into the provided memory dump from the compromised system. You need to identify basic Indicators of Compromise (IOCs) and determine the extent of the intrusion. Investigate the malicious commands or files executed in the environment, and report your findings in detail to aid in remediation and enhance future defenses.

**Category:** Endpoint Forensics

**Difficulty:** Easy

**File:** `192-Reveal.dmp`

**Tools:** `Volatility 3` `VirusTotal` 

> [Volatility](https://github.com/volatilityfoundation/volatility3) is the world's most widely used framework for extracting digital artifacts from volatile memory (RAM) samples.  

**Note:** In this walkthrough, I will use the SIFT Workstation from SANS to analyze the provided file. If you have not set it up yet, I highly recommend following this [forensics lab](https://github.com/mmhgwyjs/forensics-lab/blob/main/README.md) guide for assistance with your installation.

---

## **Preparations**

![image](https://github.com/user-attachments/assets/fb1b7b47-20f5-4e77-9f69-459e2bfffbbe)

/opt/volatility/volatility3/vol.py -f 192-Reveal.dmp windows.info > info1.txt

## **Questions and Answers**

Sure! Here’s the information in the requested format:

---

***1. Identifying the name of the malicious process helps in understanding the nature of the attack. What is the name of the malicious process?***  
**Answer: `powershell.exe`**

![image](https://github.com/user-attachments/assets/cb2eea47-a4ac-4ee2-8a85-4d0a4ce6786d)

![image](https://github.com/user-attachments/assets/6907005a-5839-44cf-b2bb-8d195d32a9c0)

![image](https://github.com/user-attachments/assets/1824bf6d-e5c7-444a-a37b-5108bd39df05)

---

***2. Knowing the parent process ID (PPID) of the malicious process aids in tracing the process hierarchy and understanding the attack flow. What is the parent PID of the malicious process?***  
**Answer: `4120`**

![image](https://github.com/user-attachments/assets/0a6c8829-2259-47af-a84e-ca04567890b7)

---

***3. Determining the file name used by the malware for executing the second-stage payload is crucial for identifying subsequent malicious activities. What is the file name that the malware uses to execute the second-stage payload?***  
**Answer: `3435.dll`**

![image](https://github.com/user-attachments/assets/da89c275-b6d9-4084-8c0c-91d2961173c6)


---

***4. Identifying the shared directory on the remote server helps trace the resources targeted by the attacker. What is the name of the shared directory being accessed on the remote server?***  
**Answer: `davwwwroot`**


---

***5. What is the MITRE sub-technique ID used by the malware to execute the second-stage payload?***  
**Answer: `T1218.011`**

![image](https://github.com/user-attachments/assets/d344012a-aef2-4266-bbe1-cd8c556b46bf)

https://attack.mitre.org/techniques/T1218/011/

---

***6. Identifying the username under which the malicious process runs helps in assessing the compromised account and its potential impact. What is the username that the malicious process runs under?***  
**Answer: `Elon`**

/opt/volatility/volatility3/vol.py -f 192-Reveal.dmp -o /home/sansforensics/Documents/cd/192-Reveal/ windows.memmap --dump --pid 3692

![image](https://github.com/user-attachments/assets/4a988b58-0cd8-4767-8b3b-07aeeadd78bc)

![image](https://github.com/user-attachments/assets/ed0cf1a1-d593-4596-93b9-f1a5b7658aa8)
strings pid.3692.dmp | grep -iE "C*users" > user.txt


---

***7. Knowing the name of the malware family is essential for correlating the attack with known threats and developing appropriate defenses. What is the name of the malware family?***  
**Answer: [Not provided]**

strelastealer

![image](https://github.com/user-attachments/assets/875bf5fb-58e6-4622-afe0-b847b4fa98af)

![image](https://github.com/user-attachments/assets/7515437c-0f94-4c0b-93b5-69fd4158e674)


![image](https://github.com/user-attachments/assets/8f6bf488-7669-4760-8f87-8f5ccfdac2b2)

/opt/volatility/volatility3/vol.py -f 192-Reveal.dmp -o ./file windows.dumpfiles --pid 3692


---

https://unit42.paloaltonetworks.com/strelastealer-campaign/
