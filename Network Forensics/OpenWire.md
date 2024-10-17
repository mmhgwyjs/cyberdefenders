# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/openwire/">OpenWire</a>

**Platform:** CyberDefenders

**Scenario:** During your shift as a tier-2 SOC analyst, you receive an escalation from a tier-1 analyst regarding a public-facing server. This server has been flagged for making outbound connections to multiple suspicious IPs. In response, you initiate the standard incident response protocol, which includes isolating the server from the network to prevent potential lateral movement or data exfiltration and obtaining a packet capture from the NSM utility for analysis. Your task is to analyze the pcap and assess for signs of malicious activity.

**Category:** Network Forensics

**Difficulty:** Medium

**Files:** `WebInvestigation.pcap`

**Tools:** `Wireshark` `Network Miner`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/abcdd1df-b1a2-4f19-8bb0-96b18378c474)

![image](https://github.com/user-attachments/assets/ee9a2443-0f3b-4b54-92d6-a35eeb1d0f91)


## **Questions and Answers**

***Q1: By identifying the C2 IP, we can block traffic to and from this IP, helping to contain the breach and prevent further data exfiltration or command execution. Can you provide the IP of the C2 server that communicated with our server?***  
**Answer: `146.190.21.92`**

![image](https://github.com/user-attachments/assets/14195a22-1e41-4e11-a240-756f14493720)

![image](https://github.com/user-attachments/assets/e83a8bd1-e611-48bb-9cc6-aeb6b7a59deb)

***Q2: Initial entry points are critical to trace back the attack vector. What is the port number of the service the adversary exploited?***  
**Answer: 61616

![image](https://github.com/user-attachments/assets/7f668fdf-6cd4-4ba1-9e78-4ecf0984f3bc)
ip.src == 146.190.21.92

***Q3: Following up on the previous question, what is the name of the service found to be vulnerable?***  
**Answer: `apache activemq`**

![image](https://github.com/user-attachments/assets/0e6a19b1-9426-4e1b-89e6-bb6acfd5d6f3)

![image](https://github.com/user-attachments/assets/8e66c886-431b-40be-9870-c3446c499105)

![image](https://github.com/user-attachments/assets/5ce5ea8d-b2f9-4a68-8cca-8d0d2c78dd6d)

![image](https://github.com/user-attachments/assets/c4b79527-b01b-4459-a09b-6081dee4a51d)

https://activemq.apache.org/components/classic/documentation/openwire

***Q4: The attacker's infrastructure often involves multiple components. What is the IP of the second C2 server?***  
**Answer: `128.199.52.72`**

![image](https://github.com/user-attachments/assets/7ac7ae6b-7f02-46f8-95da-de4e0223f3b5)

![image](https://github.com/user-attachments/assets/b65e67d9-d864-467c-9b62-1427cc5f984c)

134.209.197.3 is the victim


***Q5: Attackers usually leave traces on the disk. What is the name of the reverse shell executable dropped on the server?***  
**Answer: `docker`**

![image](https://github.com/user-attachments/assets/b45f6596-c0bf-4fcc-9b5b-bcc3c5126eb2)

File > Export Objects > HTTP

![image](https://github.com/user-attachments/assets/496e971c-21e0-4146-a5e6-37c9b8f88dad)

This command sequence downloads a script from a specified URL, gives it execute permissions, and then runs it.

![image](https://github.com/user-attachments/assets/693596e1-212e-4856-977e-57a590224968)
http.request.method == GET

***Q6: What Java class was invoked by the XML file to run the exploit?***  
**Answer: `java.lang.ProcessBuilder`**

![image](https://github.com/user-attachments/assets/51ce7db4-7ac2-4cf9-926b-52999a594317)


***Q7: To better understand the specific security flaw exploited, can you identify the CVE identifier associated with this vulnerability?***  
**Answer: `CVE-2023-46604`**

google

![image](https://github.com/user-attachments/assets/4a446b6a-5f9d-4170-b2e2-d91703409104)

https://activemq.apache.org/news/cve-2023-46604

***Q8: What is the vulnerable Java method and class that allows an attacker to run arbitrary code? (Format: Class.Method)***  
**Answer: `BaseDataStreamMarshaller.createThrowable`**

![image](https://github.com/user-attachments/assets/f9b35f1b-6de4-480c-8253-1bbab134bf69)

https://www.trendmicro.com/en_us/research/23/k/cve-2023-46604-exploited-by-kinsing.html

https://paper.seebug.org/3058/

