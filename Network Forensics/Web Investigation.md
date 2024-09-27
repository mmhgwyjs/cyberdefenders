# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/web-investigation/">Web Investigation</a>

**Platform:** CyberDefenders

**Scenario:** You are a cybersecurity analyst working in the Security Operations Center (SOC) of BookWorld, an expansive online bookstore renowned for its vast selection of literature. BookWorld prides itself on providing a seamless and secure shopping experience for book enthusiasts around the globe. Recently, you've been tasked with reinforcing the company's cybersecurity posture, monitoring network traffic, and ensuring that the digital environment remains safe from threats.

Late one evening, an automated alert is triggered by an unusual spike in database queries and server resource usage, indicating potential malicious activity. This anomaly raises concerns about the integrity of BookWorld's customer data and internal systems, prompting an immediate and thorough investigation.

As the lead analyst on this case, you are required to analyze the network traffic to uncover the nature of the suspicious activity. Your objectives include identifying the attack vector, assessing the scope of any potential data breach, and determining if the attacker gained further access to BookWorld's internal systems.

**Category:** Network Forensics

**Difficulty:** Easy

**Files:** `WebInvestigation.pcap`

**Tools:** `Wireshark` `Network Miner`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/352834a7-e182-4286-b803-daac6596980f)

## **Questions and Answers**

***1. By knowing the attacker's IP, we can analyze all logs and actions related to that IP and determine the extent of the attack, the duration of the attack, and the techniques used. Can you provide the attacker's IP?***
![image](https://github.com/user-attachments/assets/6f2ed75f-6102-41cc-9f98-a2ed4b95bdaf)
![image](https://github.com/user-attachments/assets/5f7170ce-ad3f-4d1a-a787-ffa9b3c54266)

111.224.250.131

***2. If the geographical origin of an IP address is known to be from a region that has no business or expected traffic with our network, this can be an indicator of a targeted attack. Can you determine the origin city of the attacker?***

![image](https://github.com/user-attachments/assets/d79a17d4-fbc8-4f7f-afbc-bc04b1919d29)

![image](https://github.com/user-attachments/assets/40605334-dc29-4501-84ad-3f35fd51640a)

Shijiazhuang

***3. Identifying the exploited script allows security teams to understand exactly which vulnerability was used in the attack. This knowledge is critical for finding the appropriate patch or workaround to close the security gap and prevent future exploitation. Can you provide the vulnerable script name?***

````search.php````

![image](https://github.com/user-attachments/assets/17af35c9-7ecf-4287-a63f-c386de91991a)

***4. Establishing the timeline of an attack, starting from the initial exploitation attempt, What's the complete request URI of the first SQLi attempt by the attacker?***

search.php?search=book%20and%201=1;%20--%20-

![image](https://github.com/user-attachments/assets/ceedec88-bdb0-4c3c-a068-fac2e6f89862)

***5. Can you provide the complete request URI that was used to read the web server available databases?***

search.php?search=book%27%20UNION%20ALL%20SELECT%20NULL%2CCONCAT%280x7178766271%2CJSON_ARRAYAGG%28CONCAT_WS%280x7a76676a636b%2Cschema_name%29%29%2C0x7176706a71%29%20FROM%20INFORMATION_SCHEMA.SCHEMATA--%20-

![image](https://github.com/user-attachments/assets/4f598782-a7ba-4034-932f-a74644daf8c7)

ip.src==73.124.22.98 && ip.dst==111.224.250.131 and http.response.code == 200 and http.request.uri matches "from"

![image](https://github.com/user-attachments/assets/21bd5059-1f58-4568-9173-14300670042d)


***6. Assessing the impact of the breach and data access is crucial, including the potential harm to the organization's reputation. What's the table name containing the website users data?***

![image](https://github.com/user-attachments/assets/5cd3d575-b8b5-45e3-b029-c278212a7563)


```ip.src==73.124.22.98 && ip.dst==111.224.250.131 and http.response.code == 200 and http.response_for.uri contains "FROM"```

![image](https://github.com/user-attachments/assets/e97a95f3-5b78-4ad8-be63-80f24f75f278)

![image](https://github.com/user-attachments/assets/5cf4ba13-e34d-414e-9f2c-6d3ce1dccf6e)

![image](https://github.com/user-attachments/assets/60a962c2-a1da-47bf-9bb0-2cd106b4afb4)


***7. The website directories hidden from the public could serve as an unauthorized access point or contain sensitive functionalities not intended for public access. Can you provide the name of the directory discovered by the attacker?***

admin

![image](https://github.com/user-attachments/assets/9b2d1cc4-5ad5-480f-96ae-7f2efa5d5de6)

```ip.addr==73.124.22.98 && ip.addr==111.224.250.131 and http.request.method == "POST"```

***8. Knowing which credentials were used allows us to determine the extent of account compromise. What's the credentials used by the attacker for logging in?***

![image](https://github.com/user-attachments/assets/6fbff07b-ea22-4c36-9019-c5c6d88f158f)

![image](https://github.com/user-attachments/assets/d3662827-ef35-432f-b96a-1e53e72dac65)

![image](https://github.com/user-attachments/assets/8f174f2f-72e1-4acc-b4b2-1f5c01146218)

![image](https://github.com/user-attachments/assets/e93c005e-5209-434e-91f9-3189846f4f66)

![image](https://github.com/user-attachments/assets/09f1f03a-cb58-4dcc-96a9-578ff1c7fd3e)

![image](https://github.com/user-attachments/assets/0b2f7720-0818-44e8-8a55-7377e936949e)

admin:admin123!

***9. We need to determine if the attacker gained further access or control on our web server. What's the name of the malicious script uploaded by the attacker?***

![image](https://github.com/user-attachments/assets/de201046-de2e-4a03-bf2b-5a717c58f1d0)

![image](https://github.com/user-attachments/assets/b828473a-9d23-44a7-87db-3200061fc8a5)

![image](https://github.com/user-attachments/assets/fffaa74a-d7ed-489d-8f9a-cb967edc17a2)


NVri2vhp.php
