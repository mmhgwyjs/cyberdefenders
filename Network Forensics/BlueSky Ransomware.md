# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/bluesky-ransomware/">BlueSky Ransomware</a>

**Platform:** CyberDefenders

**Scenario:** As a cybersecurity analyst on SecureTech's Incident Response Team, you're tackling an urgent case involving a high-profile corporation that suspects a sophisticated cyber attack on its network. The corporation, which manages critical data across various industries, has experienced a ransomware attack, leading to the encryption of files and an immediate need for expert assistance to mitigate the damages and investigate the breach.

Your role in the team is to conduct a detailed analysis of the evidence to determine the extent and nature of the attack. Your objective is to identify the tactics, techniques, and procedures (TTPs) used by the threat actor to help your client contain the threat and restore the integrity of their network.

**Category:** Network Forensics

**Difficulty:** Medium

**Files:** `BlueSkyRansomware.pcap` `BlueSkyRansomware.evtx` `javaw.exe`

**Tools:** `Wireshark`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/0068c36b-9b1e-4764-af19-7f4506015c9f)

![image](https://github.com/user-attachments/assets/4cac96b7-b3cf-4853-9a0b-c0219cb22e3e)

## **Questions and Answers**

Got it! Here’s the complete set with all the original sentences included:

***1. What was the source IP responsible for potential port scanning activity?***  
**Answer: `**.**.**.**`**

***2. During the investigation, it's essential to determine the account targeted by the attacker. Can you identify the targeted account username?***  
**Answer: `**`**

***3. We need to determine if the attacker succeeded in gaining access. Can you provide the correct password discovered by the attacker?***  
**Answer: `**************`**

***4. Attackers often change some settings to facilitate lateral movement within a network. What setting did the attacker enable to control the target host further and execute further commands?***  
**Answer: `_********`**

***5. Process injection is often used by attackers to escalate privileges within a system. What process did the attacker inject the C2 into to gain administrative privileges?***  
**Answer: `********.***`**

***6. Following privilege escalation, the attacker attempted to download a file. Can you identify the URL of this file downloaded?***  
**Answer: `****://**.**.**.**/********.***`**

***7. Understanding which group Security Identifier (SID) the malicious script checks to verify the current user's privileges can provide insights into the attacker's intentions. Can you provide the specific Group SID that is being checked?***  
**Answer: `*-*-*-**-***`**

***8. Windows Defender plays a critical role in defending against cyber threats. If an attacker disables it, the system becomes more vulnerable to further attacks. What are the registry keys used by the attacker to disable Windows Defender functionalities? Provide them in the same order found.***  
**Answer: `******************,****************************,*************************,********************,***************`**

***9. Can you determine the URL of the second file downloaded by the attacker?***  
**Answer: `****://**.**.**.**/***.***`**

***10. Identifying malicious tasks and understanding how they were used for persistence helps in fortifying defenses against future attacks. What's the full name of the task created by the attacker to maintain persistence?***  
**Answer: `\*********\*******\***\********`**

***11. According to your analysis of the second malicious file, what is the MITRE ID of the tactic the file aims to achieve?***  
**Answer: `TA****`**

***12. What's the invoked PowerShell script used by the attacker for dumping credentials?***  
**Answer: `******-*********.***`**

***13. Understanding which credentials have been compromised is essential for assessing the extent of the data breach. What's the name of the saved text file containing the dumped credentials?***  
**Answer: `******.***`**

***14. Knowing the hosts targeted during the attacker's reconnaissance phase, the security team can prioritize their remediation efforts on these specific hosts. What's the name of the text file containing the discovered hosts?***  
**Answer: `*********_*****.***`**

***15. After hash dumping, the attacker attempted to deploy ransomware on the compromised host, spreading it to the rest of the network through previous lateral movement activities using SMB. You’re provided with the ransomware sample for further analysis. By performing behavioral analysis, what’s the name of the ransom note file?***  
**Answer: `# ******* ***** ******* #`**

***16. In some cases, decryption tools are available for specific ransomware families. Identifying the family name can lead to a potential decryption solution. What's the name of this ransomware family?***  
**Answer: `**`**
