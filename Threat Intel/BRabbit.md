# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/brabbit/">BRabbit</a>

**Platform:** CyberDefenders

**Scenario:** You are an investigator assigned to assist Drumbo, a company that recently fell victim to a ransomware attack. The attack began when an employee received an email that appeared to be from the boss. It featured the company’s logo and a familiar email address. Believing the email was legitimate, the employee opened the attachment, which compromised the system and deployed ransomware, encrypting sensitive files. Your task is to investigate and analyze the artifacts to uncover information about the attacker.

**Category:** Threat Intel

**Difficulty:** Medium

**File:** ``

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

MD5: E5B8B2CF5B244500B22B665C87C11767

## **Questions and Answers**

***1. The phishing email used to deliver the malicious attachment showed several indicators of a potential social engineering attempt. Recognizing these indicators can help identify similar threats in the future.
What is the suspicious email address that sent the attachment?***

theceojamessmith@drurnbo.com

***2. The ransomware was identified as part of a known malware family. Determining its family name can provide critical insights into its behavior and remediation strategies.
What is the family name of the ransomware identified during the investigation?***

badrabbit

***3. Upon execution, the ransomware dropped a file onto the compromised system to initiate its payload. Identifying this file is essential for understanding its infection process.
What is the name of the first file dropped by the ransomware?***

infpub.dat

***4. Inside the dropped file, the malware contained hardcoded artifacts, including usernames and passwords that could provide clues about its origins or configuration.
What is the only person's username found within the dropped file?***

alex

***5. After execution, the ransomware communicated with a C2 server. Recognizing its communication techniques can assist in mitigation.
What MITRE ATT&CK sub-technique describes the ransomware’s use of web protocols for sending and receiving data?**

T1071.001
