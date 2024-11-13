# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/icedid/">IcedID</a>

**Platform:** CyberDefenders

**Scenario:** A cyber threat group was identified for initiating widespread phishing campaigns to distribute further malicious payloads. The most frequently encountered payloads were IcedID. You have been given a hash of an IcedID sample for the purpose of analyzing and monitoring the activities of this advanced persistent threat (APT) group.

**Category:** Threat Intel

**Difficulty:** Easy

**File:** `Hash.txt`

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

File Hash (SHA-1): 191eda0c539d284b29efe556abb05cd75a9077a0

![image](https://github.com/user-attachments/assets/b9726c5b-5453-43df-a164-6515ffb336c8)


## **Questions and Answers**

***Q1: What is the name of the file associated with the given hash?***  
**Answer: `document-1982481273.xlsm`**

![image](https://github.com/user-attachments/assets/2a13ab9f-76f1-42a2-a9dd-7abed02b30a6)

***Q2: Can you identify the filename of the gif file that was deployed?*** 
**Answer: `3003.gif`**

![image](https://github.com/user-attachments/assets/109a2f81-df13-436d-b181-8088073989fe)

https://www.trendmicro.com/en_us/research/21/d/a-spike-in-bazarcall-and-icedid-activity.html

***Q3: How many domains does the malware look to download the additional payload file in Q2?***  
**Answer: `5`**

![image](https://github.com/user-attachments/assets/3a79bd44-02e3-46a8-a806-bf6847f5418b)

***Q4: What is the MD5 hash of the executable in Q2 downloaded from metaflip.io?***  
**Answer: `964a0015332ec2cc13ab12b8d85f29ff`**

google dorking

site: https://twitter.com "3003.gif"

![image](https://github.com/user-attachments/assets/595a0935-cf3e-49f0-96f3-8714c788df16)

![image](https://github.com/user-attachments/assets/05ff3486-3702-4bd2-b688-ca191372e949)

https://app.any.run/tasks/fe428f01-7d47-4123-9c65-d86f7fcd281a

https://tria.ge/210330-gbdr6k9jxx

![image](https://github.com/user-attachments/assets/2afbf996-71fa-4f44-94d8-7b803180a124)

![image](https://github.com/user-attachments/assets/bebe5a4e-0dea-4c42-9230-cfffd3ffdfb9)


***Q5: From the domains mentioned in Q3, a DNS registrar was predominantly used by the threat actor to host their harmful content, enabling the malware's functionality. Can you specify the Registrar INC?***  
**Answer: NAMECHEAP

![image](https://github.com/user-attachments/assets/8cdd4aad-41bc-4ccf-a12d-b5e14e04dcba)

![image](https://github.com/user-attachments/assets/a3c86625-bf2b-484a-9fba-da5da9543a2e)

***Q6: Could you specify the threat actor linked to the sample provided?***  
**Answer: `GOLD CABIN`**

![image](https://github.com/user-attachments/assets/3f1a567b-d5a0-4105-83b2-2001b25f89ab)
https://www.trendmicro.com/en_us/research/21/d/a-spike-in-bazarcall-and-icedid-activity.html

![image](https://github.com/user-attachments/assets/d0ca687b-e797-45d5-8c68-5e118906e2d5)
https://attack.mitre.org/groups/G0127/

***Q8: In the Execution phase, what function does the malware employ to fetch extra payloads onto the system?***  
**Answer: `*`**
