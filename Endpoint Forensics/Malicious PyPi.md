# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/malicious-pypi/">Malicious PyPi</a>

**Platform:** CyberDefenders

**Scenario:** On a Monday afternoon, Dr. Alex Rivera, a data scientist, observed that the CPU utilization on their main development server was persistently exceeding 90%, coupled with a noticeable decline in network connectivity speed, falling well below standard performance levels. This situation was unusual, as the team had not launched any new operations that could account for the increased CPU demand.

A triage image has been taken from his computer, and it is imperative to swiftly determine the root cause, extent, and potential repercussions of this issue to prevent any adverse effects on the company's activities.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `N/A`

**Tools:** `` 

**Note:** In this walkthrough, CyberDefenders offers a lab environment for us to utilize. This feature is included with the PRO subscription.

## **Preparations** 

![image](https://github.com/user-attachments/assets/bc3c12fb-0680-4ce0-a2e7-a1f1a28f1bac)

  
## **Questions and Answers**

***1. Dr. Alex Rivera recently downloaded an external library that raised suspicions about system security. Can you identify the specific command used for this download?***  
pip install git+https://github.com/a1l4m/TensorFlow.git#egg=TensorFlow

![image](https://github.com/user-attachments/assets/cba54d19-7ad6-458b-ac61-9c525a65b243)

C:\Users\Administrator\Desktop\Start Here\Artifacts\C\Users\Administrator\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline

***2. During the investigation, you uncover a command that modified the system's security settings, resulting in the deactivation of Windows Defender in a manner that could assist an attacker. What was this command?***  
***-************ -************************* $*******  

***3. Based on your timeline analysis, at what date and time did you first observe unauthorized changes to the security settings that led to the disabling of Windows Defender? Provide the exact UTC timestamp.***  
YYYY-MM-DD HH:MM:SS  
Answer Format: YYYY-MM-DD HH:MM:SS  

***4. After the security settings were compromised, a new file appeared on the system. What is the md5 hash of this file, indicating its unique identity?***  
********************************  

***5. Investigate the origin of the malicious file detected on the server. What was the exact URL from which this file was initially downloaded before it started communicating with external C2 servers?***  
****://*.**.**.***:****/****.***  

***6. The file in the previous questions started communicating with an external C2 server. What port was used for this communication?***  
****  

***7. Attackers often ensure their continued access to a compromised system through persistence mechanisms. When was such a mechanism established on Dr. Rivera's system? Provide the UTC timestamp.***  
YYYY-MM-DD HH:MM:SS  
Answer Format: YYYY-MM-DD HH:MM:SS  

***8. After the attacker completed their intrusion, a specific file was left behind on the host system. Based on the information you've gathered, identify the name of this file, which was created shortly after the attacker established persistence on the system.***  
******.***  

***9. Determine the exact moment the malicious file identified in Question 8 began its operation. When was it first executed? Provide the UTC timestamp.***  
YYYY-MM-DD HH:MM:SS  
Answer Format: YYYY-MM-DD HH:MM:SS  

***10. After identifying the malicious file in Question 8, it is crucial to determine the name of the malware family. This information is vital for correlating the attack with known threats and developing appropriate defenses. What is the malware family name for the malicious file in Question 8?***  
******
