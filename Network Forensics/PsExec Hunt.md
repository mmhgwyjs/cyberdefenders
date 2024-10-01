# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/psexec-hunt/">PsExec Hunt</a>

**Platform:** CyberDefenders

**Scenario:** Our Intrusion Detection System (IDS) has raised an alert, indicating suspicious lateral movement activity involving the use of PsExec. To effectively respond to this incident, your role as a SOC Analyst is to analyze the captured network traffic stored in a PCAP file.

**Category:** Network Forensics

**Difficulty:** Easy

**Files:** `WebInvestigation.pcap`

**Tools:** `Wireshark` `Network Miner`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/352834a7-e182-4286-b803-daac6596980f)

![image](https://github.com/user-attachments/assets/0f7e896c-4f08-413a-9087-fbfd29d74501)

## **Questions and Answers**

***1. In order to effectively trace the attacker's activities within our network, can you determine the IP address of the machine where the attacker initially gained access?***

10.0.0.130

![image](https://github.com/user-attachments/assets/6b0a4634-584c-4f7c-b3c7-35c302e85522)

![image](https://github.com/user-attachments/assets/c8358aec-e02b-4ac2-b04a-8881797982c4)

***2. To fully comprehend the extent of the breach, can you determine the machine's hostname to which the attacker first pivoted?***
![image](https://github.com/user-attachments/assets/23572acf-e9b6-4010-bdae-db3872341324)

sales-pc

***3. After identifying the initial entry point, it's crucial to understand how far the attacker has moved laterally within our network. Knowing the username of the account the attacker used for authentication will give us insights into the extent of the breach. What is the username utilized by the attacker for authentication?***

***4. After figuring out how the attacker moved within our network, we need to know what they did on the target machine. What's the name of the service executable the attacker set up on the target?***

***5. We need to know how the attacker installed the service on the compromised machine to understand the attacker's lateral movement tactics. This can help identify other affected systems. Which network share was used by PsExec to install the service on the target machine?***

***6. We must identify the network share used to communicate between the two machines. Which network share did PsExec use for communication?***

***7. Now that we have a clearer picture of the attacker's activities on the compromised machine, it's important to identify any further lateral movement. What is the machine's hostname to which the attacker attempted to pivot within our network?***
