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

File Hash (SHA-256): 191eda0c539d284b29efe556abb05cd75a9077a0

![image](https://github.com/user-attachments/assets/b9726c5b-5453-43df-a164-6515ffb336c8)


## **Questions and Answers**

***Q1: Categorizing malware allows for a quicker and easier understanding of the malware, aiding in understanding its distinct behaviors and attack vectors. What's the identified malware's category?***  
**Answer: `document-1982481273.xlsm`**

![image](https://github.com/user-attachments/assets/2a13ab9f-76f1-42a2-a9dd-7abed02b30a6)


***Q2: What is the name of the file associated with the given hash?***  
**Answer: `doc*****-**********.****`**

***Q3: Can you identify the filename of the gif file that was deployed?***  
**Answer: `****.***`**

***Q4: How many domains does the malware look to download the additional payload file in Q2?***  
**Answer: `*`**

***Q5: What is the MD5 hash of the executable in Q2 downloaded from metaflip.io?***  
**Answer: `********************************`**

***Q6: From the domains mentioned in Q3, a DNS registrar was predominantly used by the threat actor to host their harmful content, enabling the malware's functionality. Can you specify the Registrar INC?***  
**Answer: `*********`**

***Q7: Could you specify the threat actor linked to the sample provided?***  
**Answer: `G*** *****`**

***Q8: In the Execution phase, what function does the malware employ to fetch extra payloads onto the system?***  
**Answer: `*`**
