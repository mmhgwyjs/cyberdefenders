# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/phishstrike/">Lespion</a>

**Platform:** CyberDefenders

**Scenario:** As a cybersecurity analyst for an educational institution, you receive an alert about a phishing email targeting faculty members. The email, appearing from a trusted contact, claims a $625,000 purchase and provides a link to download an invoice.

Your task is to investigate the email using Threat Intel tools. Analyze the email headers and inspect the link for malicious content. Identify any Indicators of Compromise (IOCs) and document your findings to prevent potential fraud and educate faculty on phishing recognition.

**Category:** Threat Intel

**Difficulty:** Medium

**File:** `194-PhishStrike.eml`

**Tools:** `` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**


## **Questions and Answers**

***Q1: Identifying the sender's IP address with specific SPF and DKIM values helps trace the source of the phishing email. What is the sender's IP address that has an SPF value of softfail and a DKIM value of fail?***  
**Answer:** `18.208.22.104`

![image](https://github.com/user-attachments/assets/b035868b-ce62-4695-ae40-b1c586f0c3b4)

***Q2: Understanding the return path of the email helps in tracing its origin. What is the return path specified in this email?***  
**Answer:** `***********.*****@****.***.**`

***Q3: Identifying the source of malware is critical for effective threat mitigation and response. What is the IP address hosting the malicious file associated with malware distribution?***  
**Answer:** `***.***.***.***`

***Q4: Identifying malware that exploits system resources for cryptocurrency mining is critical for prioritizing threat mitigation efforts. The malicious URL can deliver several malware types. Which malware family is responsible for cryptocurrency mining?***  
**Answer:** `*********`

***Q5: Identifying the specific URLs malware requests is key to disrupting its communication channels and reducing its impact. Based on the previous analysis of the cryptocurrency malware sample, what does this malware request the URL?***  
**Answer:** `****://******.******/******/*******/*********.****`

***Q6: Understanding the registry entries added to the auto-run key by malware is crucial for identifying its persistence mechanisms. Based on the BitRAT malware sample analysis, what is the executable's name in the first value added to the registry auto-run key?***  
**Answer:** `******.***`

***Q7: Identifying the SHA-256 hash of files downloaded from a malicious URL is essential for tracking and analyzing malware activity. Based on the BitRAT analysis, what is the SHA-256 hash of the file previously downloaded and added to the autorun keys?***  
**Answer:** `****************************************************************`

***Q8: Analyzing the HTTP requests made by malware helps in identifying its communication patterns. What is the HTTP request used by the loader to retrieve the BitRAT malware?***  
**Answer:** `****://***.***.***.***/******/******.***`

***Q9: Introducing a delay in malware execution can help evade detection mechanisms. What is the delay (in seconds) caused by the PowerShell command according to the BitRAT analysis?***  
**Answer:** `**`

***Q10: Tracking the command and control (C2) domains used by malware is essential for detecting and blocking malicious activities. What is the C2 domain used by the BitRAT malware?***  
**Answer:** `*****.******.***`

***Q11: Understanding the methods malware uses for exfiltrating data is crucial for detecting and preventing data breaches. According to the AsyncRAT analysis, what is the Telegram Bot ID used by the malware?***  
**Answer:** `***********`
