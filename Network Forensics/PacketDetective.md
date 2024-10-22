# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/packetdetective/">PacketDetective</a>

**Platform:** CyberDefenders

**Scenario:** As a SOC analyst, explore a collection of Wireshark pcap files that delve into various attack tactics, including evasion and lateral movement. Analyze network traffic captured within these pcaps to uncover valuable insights and detect potential command and control (C&C) activities.

**Category:** Network Forensics

**Difficulty:** Easy

**Files:** `Traffic-1.pcapng` Traffic-2.pcapng Traffic-3.pcapng

**Tools:** `` 

**Note:** In this walkthrough, CyberDefenders offers a lab environment for us to utilize. This feature is included with the PRO subscription.

## **Preparations** 

![image](https://github.com/user-attachments/assets/20de9680-a5fd-42b0-a14e-ce4f1507465f)

![image](https://github.com/user-attachments/assets/954ccb4b-93c8-4938-91a2-7bcc834d1885)
Traffic-1.pcapng


![image](https://github.com/user-attachments/assets/e51a4169-583c-4595-914d-21af3c380666)
Traffic-2.pcapng

![image](https://github.com/user-attachments/assets/bdaf8087-9425-4e65-bd5f-b895261c8d20)
Traffic-3.pcapng


## **Questions and Answers**

***1. What is the amount of bandwidth being used by the SMB protocol in bytes? (Traffic-1)***  
**Answer:** 4406

![image](https://github.com/user-attachments/assets/99edf574-1582-448f-a9e0-ed14b2fcce40)


***2. Which username was utilized for authentication via SMB?***  
**Answer:** administrator

![image](https://github.com/user-attachments/assets/075f5e61-1807-4861-a3dc-9605d3570b55)


***3. What is the name of the file that was opened?***  
**Answer:** eventlog

![image](https://github.com/user-attachments/assets/96aff1d9-b2a7-4b9d-b146-a90974c5bae8)

***4. What is the timestamp of the attempt to clear the event log? (24H-UTC)***  
**Answer:** 2020-09-23 16:50:16  

![image](https://github.com/user-attachments/assets/7362e389-f902-4f38-a9a3-bc1056ba7599)

![image](https://github.com/user-attachments/assets/586453b7-7d6c-418c-96de-999a2e2219d9)

![image](https://github.com/user-attachments/assets/31ad756f-fcd6-41dc-bbee-e814d6a71e65)

![image](https://github.com/user-attachments/assets/1f84e4b3-2734-4ac8-9bc7-c35fea365550)

![image](https://github.com/user-attachments/assets/967480ce-b54d-41b9-ba30-7e2a7075e544)

***5. An attacker used a named pipe for communication to blend in and evade detection. What is the name of the service that utilized this pipe for communication?***   Traffic-2
**Answer:** atsvc  
![image](https://github.com/user-attachments/assets/09f41ace-9cf9-4eb2-a867-b40dc5430b61)


***6. What was the duration of communication between 172.16.66.1 and 172.16.66.36?***  Traffic-2

**Answer:** 11.7247  

![image](https://github.com/user-attachments/assets/3904366d-e64f-4c69-81f0-03a87039548b)


***7. Which username is used to set up requests that may be considered suspicious?***  Traffic-3
backdoor

![image](https://github.com/user-attachments/assets/d6cc808f-e4d5-4f1b-9f8f-0d6f4be4b046)


***8. What is the name of the executable file utilized to execute processes remotely?***  Traffic-3
**Answer:** psexesvc.exe

![image](https://github.com/user-attachments/assets/41b62cf5-a23a-424d-b0d4-a2614c1a9525)


