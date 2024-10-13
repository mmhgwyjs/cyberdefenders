![image](https://github.com/user-attachments/assets/fa1c35f7-b1c0-49f9-af5c-e841b27c749e)# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/red-stealer//">Red Stealer</a>

**Platform:** CyberDefenders

**Scenario:** Open-source intelligence (OSINT) exercise to practice mining and analyzing public data to produce meaningful intel when investigating external threats as a security blue team analyst.

**Category:** Threat Intel

**Difficulty:** Easy

**File:** `FileHash.txt`

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

File Hash (SHA-256): 248FCC901AFF4E4B4C48C91E4D78A939BF681C9A1BC24ADDC3551B32768F907B

## **Questions and Answers**

***Q1: Categorizing malware allows for a quicker and easier understanding of the malware, aiding in understanding its distinct behaviors and attack vectors. What's the identified malware's category?***  
**Answer: `trojan`**

![image](https://github.com/user-attachments/assets/c78af3ba-e07e-4ffc-b093-995614ed2739)



***Q2: Clear identification of the malware file name facilitates better communication among the SOC team. What's the file name associated with this malware?***  
**Answer: `WEXTRACT`**

![image](https://github.com/user-attachments/assets/c8f1b182-881c-48ed-938c-8838168622be)


***Q3: Knowing the exact time the malware was first seen can help prioritize actions. If the malware is newly detected, it may warrant more urgent containment and eradication efforts compared to older, well-known threats. Can you provide the UTC timestamp of first submission of this malware on VirusTotal?***  
**Answer: `2023-10-06 04:41:50 UTC`**

![image](https://github.com/user-attachments/assets/320cedc7-dd3b-4b7e-82ff-1eb2a6cb511f)


***Q4: Understanding the techniques used by malware helps in strategic security planning. What is the MITRE ATT&CK technique ID for the malware's data collection from the system before exfiltration?***  
**Answer: `T1005`**

![image](https://github.com/user-attachments/assets/77cfaf7e-5f9e-415d-a533-584550a104f1)

![image](https://github.com/user-attachments/assets/4066e8a9-3f6d-441a-9647-3e4a59519c6e)

***Q5: Following execution, what domain name resolution is performed by the malware?***  
**Answer: `facebook.com`**

![image](https://github.com/user-attachments/assets/ec542739-1ac7-491a-98fd-14d8eae726c3)


![image](https://github.com/user-attachments/assets/411eb2c8-de90-4fa2-bf73-cc7d89dfad7f)


***Q6: Once the malicious IP addresses are identified, network security devices such as firewalls can be configured to block traffic to and from these addresses. Can you provide the IP address and destination port the malware communicates with?***  
**Answer: `77.91.124.55:19071`**

![image](https://github.com/user-attachments/assets/9065fe28-a5e5-4d5d-a92f-d4d01f83af5b)


***Q7: YARA rules are designed to identify specific malware patterns and behaviors. What's the name of the YARA rule created by "Varp0s" that detects the identified malware?***  
**Answer: `detect_Redline_Stealer`**

![image](https://github.com/user-attachments/assets/336e015e-889b-41c6-bcf8-66abf466c15a)
https://bazaar.abuse.ch/sample/248fcc901aff4e4b4c48c91e4d78a939bf681c9a1bc24addc3551b32768f907b/

![image](https://github.com/user-attachments/assets/f44f8744-5fbc-4a1a-8d38-387af30bf131)


***Q8: Understanding which malware families are targeting the organization helps in strategic security planning for the future and prioritizing resources based on the threat. Can you provide the different malware alias associated with the malicious IP address?***  
**Answer: `RECORDSTEALER`**

![image](https://github.com/user-attachments/assets/8462a38a-05f4-4d55-9bd8-c6f6a037af3b)
https://threatfox.abuse.ch/ioc/1167880/

***Q9: By identifying the malware's imported DLLs, we can configure security tools to monitor for the loading or unusual usage of these specific DLLs. Can you provide the DLL utilized by the malware for privilege escalation?***  
**Answer: `advapi32dll`**

![image](https://github.com/user-attachments/assets/b35d28d9-7daa-492c-a4a0-cad53f7a954b)

![image](https://github.com/user-attachments/assets/ff71a41c-aee7-4936-a767-b83cc3bd1e2f)

https://stackoverflow.com/questions/9194638/does-anyone-know-what-advapi-stands-for
