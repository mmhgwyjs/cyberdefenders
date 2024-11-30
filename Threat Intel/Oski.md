# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/oski/">Oski</a>

**Platform:** CyberDefenders

**Scenario:** The accountant at the company received an email titled "Urgent New Order" from a client late in the afternoon. When he attempted to access the attached invoice, he discovered it contained false order information. Subsequently, the SIEM solution generated an alert regarding downloading a potentially malicious file. Upon initial investigation, it was found that the PPT file might be responsible for this download. Could you please conduct a detailed examination of this file?

**Category:** Threat Intel

**Difficulty:** Easy

**File:** `hash.txt`

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

MD5 Hash: 12c1842c3ccafe7408c23ebf292ee3d9 

## **Questions and Answers**

***Q1: To better categorize and comprehend the behavior and intent of this potential malware, it's essential to identify its family. What is the malware family name for the malicious executable found within the PPT?***  
**Answer: `stealc`**

![image](https://github.com/user-attachments/assets/df87c71c-edb5-456b-b5b8-fef35f219b96)

https://any.run/report/a040a0af8697e30506218103074c7d6ea77a84ba3ac1ee5efae20f15530a19bb/d55e2294-5377-4a45-b393-f5a8b20f7d44

***Q2: Determining the creation time of the malware can provide insights into its origin. When was the malware creation time?***  
**Answer: `2022-09-28 17:40:46 UTC`

![image](https://github.com/user-attachments/assets/9284008f-54c3-4607-8f95-a1633378b152)


***Q3: Identifying the command and control (C2C) server that the malware communicates with can help trace back to the attacker. Which C2C server does the malware in the PPT file communicate with?***  
**Answer: `http://171.22.28.221/5c06c05b7b34e8e6.php`  

![image](https://github.com/user-attachments/assets/ea1c553a-fe35-4a29-90cb-8551fefd358a)

***Q4: Identifying the initial actions of the malware post-infection can provide insights into its primary objectives. What is the first library that the malware requests post-infection?***  
**Answer: `sqlite3.dll`

![image](https://github.com/user-attachments/assets/34596f06-1e72-439d-9d44-5d61f8087195)


***Q5: Upon examining the malware, it appears to utilize the RC4 key for decrypting a base64 string. What is the specific RC4 key used by this malware?***  
**Answer: `5329514621441247975720749009`

![image](https://github.com/user-attachments/assets/705d8e89-3daf-45a1-b07a-1ac7a4770d02)

`https://any.run/report/a040a0af8697e30506218103074c7d6ea77a84ba3ac1ee5efae20f15530a19bb/d55e2294-5377-4a45-b393-f5a8b20f7d44`

***Q6: Identifying an adversary's techniques can aid in understanding their methods and devising countermeasures. Which MITRE ATT&CK technique are they employing to steal a user's password?***  
**Answer: `*****`  

***Q7: Malwares may delete files left behind by the actions of their intrusion activity. Which directory or path does the malware target for deletion?***  
**Answer: `*:\***********`  
`*:\***********`**

***Q8: Understanding the malware's behavior post-data exfiltration can give insights into its evasion techniques. After successfully exfiltrating the user's data, how many seconds does it take for the malware to self-delete?***  
**Answer: `326`**
