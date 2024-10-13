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

![image](https://github.com/user-attachments/assets/8496118d-a955-4214-8789-850b8ffa292e)

![image](https://github.com/user-attachments/assets/1cf84ff5-6418-48b9-9cbc-6f732b2b7b53)



## **Questions and Answers**

Got it! Here’s the complete set with all the original sentences included:

***1. What was the source IP responsible for potential port scanning activity?***  
**Answer: `87.96.21.84`**

![image](https://github.com/user-attachments/assets/a112d499-52cc-4ebb-addc-a032c575d4fc)

![image](https://github.com/user-attachments/assets/47ff6201-bd90-45f8-9d9c-a74956ccbc76)

![image](https://github.com/user-attachments/assets/b02727b6-ed1b-444f-bbd8-d7b70545acaa)


***2. During the investigation, it's essential to determine the account targeted by the attacker. Can you identify the targeted account username?***  
**Answer: `sa`**

![image](https://github.com/user-attachments/assets/637bc72c-b8d7-4567-b910-3538d77e13cb)

![image](https://github.com/user-attachments/assets/db20bda3-9b18-4b39-9c30-b7d1ca64112c)

Statistics > Protocol Hierarchy

***3. We need to determine if the attacker succeeded in gaining access. Can you provide the correct password discovered by the attacker?***  
**Answer: cyb3rd3f3nd3r$

![image](https://github.com/user-attachments/assets/1a4c4fcc-3cdb-4219-905e-83b067cc373c)


***4. Attackers often change some settings to facilitate lateral movement within a network. What setting did the attacker enable to control the target host further and execute further commands?***  
**Answer: `xp_cmdshell`

![image](https://github.com/user-attachments/assets/cb9aadfc-7a20-4e53-9d31-4294456215e6)

***5. Process injection is often used by attackers to escalate privileges within a system. What process did the attacker inject the C2 into to gain administrative privileges?***  
**Answer: `winlogon.exe`**

evtxecmd.exe -f BlueSkyRansomware.evtx --csv ./. --csvf event1.csv

![image](https://github.com/user-attachments/assets/93e7b838-b74f-4e3b-b243-f53619988753)

https://docs.rapid7.com/metasploit/msf-overview/

***6. Following privilege escalation, the attacker attempted to download a file. Can you identify the URL of this file downloaded?***  
**Answer: `http://87.96.21.84/checking.ps1`**

![image](https://github.com/user-attachments/assets/75047abe-a78b-40bc-b00c-f32a38c027b3)

http.request.method == GET

***7. Understanding which group Security Identifier (SID) the malicious script checks to verify the current user's privileges can provide insights into the attacker's intentions. Can you provide the specific Group SID that is being checked?***  
**Answer: `S-1-5-32-544**

![image](https://github.com/user-attachments/assets/e1bc11ff-79a1-4ddf-8365-94884ce012fa)
follow http stream

***8. Windows Defender plays a critical role in defending against cyber threats. If an attacker disables it, the system becomes more vulnerable to further attacks. What are the registry keys used by the attacker to disable Windows Defender functionalities? Provide them in the same order found.***  
**Answer: `DisableAntiSpyware,DisableRoutinelyTakingAction,DisableRealtimeMonitoring,SubmitSamplesConsent,SpynetReporting`**

![image](https://github.com/user-attachments/assets/78306e87-3524-4dfb-85aa-9333f361b9d1)


***9. Can you determine the URL of the second file downloaded by the attacker?***  
**Answer: `http://87.96.21.84/del.ps1`**

![image](https://github.com/user-attachments/assets/16e57295-8c47-4c76-aa29-58eab14b29f1)


***10. Identifying malicious tasks and understanding how they were used for persistence helps in fortifying defenses against future attacks. What's the full name of the task created by the attacker to maintain persistence?***  
**Answer: `\Microsoft\Windows\MUI\LPupdate`**

![image](https://github.com/user-attachments/assets/968d7445-9862-4dd8-8c5b-ed1be3866538)


***11. According to your analysis of the second malicious file, what is the MITRE ID of the tactic the file aims to achieve?***  
**Answer: `TA0005`**

![image](https://github.com/user-attachments/assets/ca486946-eb69-4a28-8b48-c5390c13dfda)

![image](https://github.com/user-attachments/assets/47b4275a-0ca2-41a0-bc38-d95f450ab007)

![image](https://github.com/user-attachments/assets/159a5b77-8d82-48bf-a27d-7107efa10181)

https://attack.mitre.org/techniques/T1562/001/

***12. What's the invoked PowerShell script used by the attacker for dumping credentials?***  
**Answer: `Invoke-PowerDump.ps1`**

![image](https://github.com/user-attachments/assets/72ee4f85-46fb-432a-bce9-835cddbf343d)

![image](https://github.com/user-attachments/assets/b476f8a2-9de0-4826-a183-475f3a3bef2b)

***13. Understanding which credentials have been compromised is essential for assessing the extent of the data breach. What's the name of the saved text file containing the dumped credentials?***  
**Answer: `hashes.txt`**
![image](https://github.com/user-attachments/assets/85f1ff36-db35-45fc-bcc4-c3b8b2235fd2)

![image](https://github.com/user-attachments/assets/4c2ab60d-7fc4-4865-855f-b0a262662ca4)


***14. Knowing the hosts targeted during the attacker's reconnaissance phase, the security team can prioritize their remediation efforts on these specific hosts. What's the name of the text file containing the discovered hosts?***  
**Answer: `extracted_hosts.txt`**

![image](https://github.com/user-attachments/assets/b7f0914e-a8f8-4544-9132-c46681752f5d)


![image](https://github.com/user-attachments/assets/d6a32e8d-bff2-467f-b7f9-4d80dbb0f522)


![image](https://github.com/user-attachments/assets/405f3d9e-c12b-47a8-9a0b-d78863cadd62)


***15. After hash dumping, the attacker attempted to deploy ransomware on the compromised host, spreading it to the rest of the network through previous lateral movement activities using SMB. You’re provided with the ransomware sample for further analysis. By performing behavioral analysis, what’s the name of the ransom note file?***  
**Answer: `# DECRYPT FILES BLUESKY #`**

Get-FileHash .\javaw.exe -Algorithm SHA256

![image](https://github.com/user-attachments/assets/e5ed7c4a-23c1-4be5-a36d-fb516414309b)

3e035f2d7d30869ce53171ef5a0f761bfb9c14d94d9fe6da385e20b8d96dc2fb

![image](https://github.com/user-attachments/assets/015dcd1d-7c25-4a96-8084-3b8d218864d7)

![image](https://github.com/user-attachments/assets/f3519c58-9c77-4b5d-923b-a5dcec2f9ad9)


***16. In some cases, decryption tools are available for specific ransomware families. Identifying the family name can lead to a potential decryption solution. What's the name of this ransomware family?***  
**Answer: `conti`**

![image](https://github.com/user-attachments/assets/3d0ea06b-b850-4b82-914e-e650a55d1568)
