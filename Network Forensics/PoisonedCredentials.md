# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/poisonedcredentials/">PoisonedCredentials</a>

**Platform:** CyberDefenders

**Scenario:** Your organization's security team has detected a surge in suspicious network activity. There are concerns that LLMNR (Link-Local Multicast Name Resolution) and NBT-NS (NetBIOS Name Service) poisoning attacks may be occurring within your network. These attacks are known for exploiting these protocols to intercept network traffic and potentially compromise user credentials. Your task is to investigate the network logs and examine captured network traffic.

**Category:** Network Forensics

**Difficulty:** Easy

**Files:** `BlueSkyRansomware.pcap` `BlueSkyRansomware.evtx` `javaw.exe`

**Tools:** `Wireshark`

**Note:** In this walkthrough, we will use the Remnux to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/5dfa04b5-38e3-4875-9ac1-337f7dcc97ab)

```
7z x 146-poisonedcredentials.zip 
```

https://attack.mitre.org/techniques/T1557/001/

## **Questions and Answers**

***1. In the context of the incident described in the scenario, the attacker initiated their actions by taking advantage of benign network traffic from legitimate machines. Can you identify the specific mistyped query made by the machine with the IP address 192.168.232.162?***  
**Answer:** `FILESHAARE`

![image](https://github.com/user-attachments/assets/59bf2a9a-ba0c-40f3-9146-cabb7d31290a)
ip.src == 192.168.232.162

***2. We are investigating a network security incident. For a thorough investigation, we need to determine the IP address of the rogue machine. What is the IP address of the machine acting as the rogue entity?***  
**Answer:** `192.168.232.215`

![image](https://github.com/user-attachments/assets/be6dbf1b-1ed5-4e66-99db-aac7c3f7428f)

![image](https://github.com/user-attachments/assets/03549929-1a27-4adb-b8f3-2db1e297a88f)

***3. During our investigation, it's crucial to identify all affected machines. What is the IP address of the second machine that received poisoned responses from the rogue machine?***  
**Answer:** `192.168.232.176`

***4. We suspect that user accounts may have been compromised. To assess this, we must determine the username associated with the compromised account. What is the username of the account that the attacker compromised?***  
**Answer:** `janesmith`

![image](https://github.com/user-attachments/assets/2659c439-fd8a-4116-ba3d-e1ad9b862cec)

***5. As part of our investigation, we aim to understand the extent of the attacker's activities. What is the hostname of the machine that the attacker accessed via SMB?***  
**Answer:** ACCOUNTINGPC

![image](https://github.com/user-attachments/assets/40eaf268-97f1-4e0d-89a8-74b8935223bd)

