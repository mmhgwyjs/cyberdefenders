# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/yellow-rat/">Yellow RAT</a>

**Platform:** CyberDefenders

**Scenario:** A large multinational corporation heavily relies on the 3CX software for phone communication, making it a critical component of their business operations. After a recent update to the 3CX Desktop App, antivirus alerts flag sporadic instances of the software being wiped from some workstations while others remain unaffected. Dismissing this as a false positive, the IT team overlooks the alerts, only to notice degraded performance and strange network traffic to unknown servers. Employees report issues with the 3CX app, and the IT security team identifies unusual communication patterns linked to recent software updates.

As the threat intelligence analyst, it's your responsibility to examine this possible supply chain attack. Your objectives are to uncover how the attackers compromised the 3CX app, identify the potential threat actor involved, and assess the overall extent of the incident. 

**Category:** Threat Intel

**Difficulty:** Easy

**File:** `3CXDesktopApp-18.12.416.msi`

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

malware hash: 30E527E45F50D2BA82865C5679A6FA998EE0A1755361AB01673950810D071C85

## **Questions and Answers**

***Q1: Understanding the adversary helps defend against attacks. What is the name of the malware family that causes abnormal network traffic?***  
**Answer: `****** ******** ***`**  

***Q2: As part of our incident response, knowing common filenames the malware uses can help scan other workstations for potential infection. What is the common filename associated with the malware discovered on our workstations?***  
**Answer: `********-****-****-****-************.***`**  

***Q3: Determining the compilation timestamp of malware can reveal insights into its development and deployment timeline. What is the compilation timestamp of the malware that infected our network?***  
**Answer: `****-**-** **:**:**`**  

***Q4: Understanding when the broader cybersecurity community first identified the malware could help determine how long the malware might have been in the environment before detection. When was the malware first submitted to VirusTotal?***  
**Answer: `****-**-** **:**:**`**  

***Q5: To completely eradicate the threat from Industries' systems, we need to identify all components dropped by the malware. What is the file name dropped by the malware in the Appdata folder?***  
**Answer: `***********.***`**  

***Q6: It is crucial to identify the C2 servers with which the malware communicates to block its communication and prevent further data exfiltration. What is the C2 server that the malware is communicating with?***  
**Answer: `*****://*******.***`**  
