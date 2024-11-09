# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/red-stealer//">Red Stealer</a>

**Platform:** CyberDefenders

**Scenario:** You are part of the Threat Intelligence team in the SOC (Security Operations Center). An executable file has been discovered on a colleague's computer, and it's suspected to be linked to a Command and Control (C2) server, indicating a potential malware infection.

Your task is to investigate this executable by analyzing its hash. The goal is to gather and analyze data that is beneficial to other SOC members, including the Incident Response team, in order to efficiently respond to this suspicious behavior.

**Category:** Threat Intel

**Difficulty:** Easy

**File:** `Hash.txt`

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

File Hash (SHA-256): 191eda0c539d284b29efe556abb05cd75a9077a0

## **Questions and Answers**

***Q1: Categorizing malware allows for a quicker and easier understanding of the malware, aiding in understanding its distinct behaviors and attack vectors. What's the identified malware's category?***  
**Answer: `trojan`**

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
