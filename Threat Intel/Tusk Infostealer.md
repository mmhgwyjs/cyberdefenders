# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/tusk-infostealer/">Tusk Infostealer</a>

**Platform:** CyberDefenders

**Scenario:** A blockchain development company detected unusual activity when an employee was redirected to an unfamiliar website while accessing a DAO management platform. Soon after, multiple cryptocurrency wallets linked to the organization were drained. Investigators suspect a malicious tool was used to steal credentials and exfiltrate funds.

Your task is to analyze the provided intelligence to uncover the attack methods, identify indicators of compromise, and track the threat actor’s infrastructure.

**Category:** Threat Intel

**Difficulty:** Easy

**File:** `hash.txt`

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

MD5: E5B8B2CF5B244500B22B665C87C11767

## **Questions and Answers**

***Q1: What is the size of the malicious file?***  
**Answer:** `921.36 KB`

![image](https://github.com/user-attachments/assets/9274f8fe-17e2-44e0-bd07-d6f88ca9fafb)

***Q2: What word does the threat actor use in log messages to refer to victims, drawing inspiration from ancient tusk hunters?***  
**Answer:** `Mammoth`  

![image](https://github.com/user-attachments/assets/f4b29104-bd29-4893-9ad4-c9686961c573)

https://www.infostealers.com/article/tusk-unraveling-a-complex-infostealer-campaign/

***Q3: The threat actor created a malicious website to simulate a platform specialized for creating and managing decentralized autonomous organizations (DAOs) on the MultiversX blockchain. What is the name of the malicious website?***  
**Answer:** `tidyme[.]io` 

![image](https://github.com/user-attachments/assets/988bb782-4f77-4aa0-8b99-bc480f644c4d)

***Q4: Where are malware samples hosted for both macOS and Windows?***  
**Answer:** `Dropbox`

![image](https://github.com/user-attachments/assets/c077d941-19a9-41d4-a4d9-772d5ad14bb8)

***Q5: The malicious executable contains a configuration file that includes base64-encoded URLs and a password used for archived data decompression, enabling the download of second-stage payloads. What is the password for decompression found in this configuration file?***  
**Answer:** `newfile2024`

![image](https://github.com/user-attachments/assets/cd89018d-c178-443f-8448-700a0c996ae9)

***Q6: What is the name of the function responsible for retrieving the field archive from the configuration file?***  
**Answer:** `*************************` / `*************************`  

***Q7: In the Third Sub-Campaign, the attacker simulated an AI translator. What is the name of the legitimate translator and the name of the malicious translator?***  
**Answer:** `****, *****` / `****, *****`  

***Q8: What are the IP Addresses of the StealC C2 Server?***  
**Answer:** `**.*.***.***, **.**.***.***` / `**.*.***.***, **.**.***.***`  

***Q9: What is the address of the Ethereum cryptocurrency wallet used in this campaign?***  
**Answer:** `*************`  
