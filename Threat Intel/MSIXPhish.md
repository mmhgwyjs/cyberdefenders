# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/msixphish/">MSIXPhish</a>

**Platform:** CyberDefenders

**Scenario:** As a Threat Intelligence Analyst at a major security firm, you play a role in efficiently gathering intel about potential threats. During your work day, an incident responder has provided you with a hash associated with a malicious software installer detected in your organization's network. Your task is to analyze this hash to gather valuable threat intelligence and enhance your organization's defenses.

**Category:** Threat Intel

**Difficulty:** Easy

**File:** `FileHash.txt`

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

File Hash (SHA-256): 11b71429869f29122236a44a292fde3f0269cde8eb76a52c89139f79f4b97e63

## **Questions and Answers**

***Q1: To effectively mitigate the threat, it's important to determine the origin or category of this malware. Can you identify which malware family this sample is associated with to better understand its typical behaviors and associated risks?***  
**Answer: `Batloader`**

![image](https://github.com/user-attachments/assets/e62b98b2-2dd4-4727-aba9-78b50fe73d47)


***Q2: It's important to identify the malware's first public appearance to effectively track its history and spread. Can you provide the initial submission date and time of this malware on VirusTotal?***  
**Answer: `12-12-2023 18:08:13`**  

![image](https://github.com/user-attachments/assets/918fa587-d5c5-436d-ae8b-007068d35283)


***Q3: Recognizing a specific MITRE technique employed by the malware helps develop targeted defense strategies. What's the MITRE ID of the technique used by the malware for data collection?***  
**Answer: `T1056`**  

![image](https://github.com/user-attachments/assets/d9b9f036-afe9-4560-8058-10fe2778387e)

***Q4: Knowing the names of executable files dropped by the malware aids in detecting and isolating infected machines. What is the executable file name dropped by the malware?***  
**Answer: `Install.exe`**  

![image](https://github.com/user-attachments/assets/792c418c-3231-406f-8db3-51069f8a2924)

***Q5: Continuing on the previous question. Can you identify the name of the second execution parent observed in the wild for the executable discovered?***  
**Answer: `parent_process.exe`**  

***Q6: Identifying the domains used in attacks can help block future malicious communication and understand attacker infrastructure. What domain is used by the threat actor to host the illegitimate application installer?***  
**Answer: `maliciousdomain.com`**  

***Q7: We need to identify the access vector abused by the malware to mitigate it. What protocol handler is exploited by the malware?***  
**Answer: `http`**  

***Q8: Uncovering the threat actor associated with this malware is key to understanding their tactics, techniques, and procedures (TTPs) and bolstering defenses against future attacks. Can you provide the name of the threat actor?***  
**Answer: `APT28`**  
