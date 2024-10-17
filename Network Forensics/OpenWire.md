# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/openwire/">OpenWire</a>

**Platform:** CyberDefenders

**Scenario:** During your shift as a tier-2 SOC analyst, you receive an escalation from a tier-1 analyst regarding a public-facing server. This server has been flagged for making outbound connections to multiple suspicious IPs. In response, you initiate the standard incident response protocol, which includes isolating the server from the network to prevent potential lateral movement or data exfiltration and obtaining a packet capture from the NSM utility for analysis. Your task is to analyze the pcap and assess for signs of malicious activity.

**Category:** Network Forensics

**Difficulty:** Medium

**Files:** `WebInvestigation.pcap`

**Tools:** `Wireshark` `Network Miner`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/352834a7-e182-4286-b803-daac6596980f)

## **Questions and Answers**

***Q1: By identifying the C2 IP, we can block traffic to and from this IP, helping to contain the breach and prevent further data exfiltration or command execution. Can you provide the IP of the C2 server that communicated with our server?***  
**Answer: `***.***.**.**`**

***Q2: Initial entry points are critical to trace back the attack vector. What is the port number of the service the adversary exploited?***  
**Answer: `*****`**

***Q3: Following up on the previous question, what is the name of the service found to be vulnerable?***  
**Answer: `****** ********`**

***Q4: The attacker's infrastructure often involves multiple components. What is the IP of the second C2 server?***  
**Answer: `***.***.**.**`**

***Q5: Attackers usually leave traces on the disk. What is the name of the reverse shell executable dropped on the server?***  
**Answer: `******`**

***Q6: What Java class was invoked by the XML file to run the exploit?***  
**Answer: `****.****.**************`**

***Q7: To better understand the specific security flaw exploited, can you identify the CVE identifier associated with this vulnerability?***  
**Answer: `***-****-*****`**

***Q8: What is the vulnerable Java method and class that allows an attacker to run arbitrary code? (Format: Class.Method)***  
**Answer: `************************.***************`**
