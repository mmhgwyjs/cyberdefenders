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

![image](https://github.com/user-attachments/assets/19064b2e-c120-4759-8ec8-9a4b228f2ce5)


## **Questions and Answers**

***Q1: Understanding the adversary helps defend against attacks. What is the name of the malware family that causes abnormal network traffic?***  
**Answer: `Yellow Cockatoo RAT`**  

![image](https://github.com/user-attachments/assets/1238bc83-c3ca-47df-97f4-6d0dd018156b)

https://redcanary.com/blog/threat-intelligence/yellow-cockatoo/

***Q2: As part of our incident response, knowing common filenames the malware uses can help scan other workstations for potential infection. What is the common filename associated with the malware discovered on our workstations?***  
**Answer: `111bc461-1ca8-43c6-97ed-911e0e69fdf8.dll`**

![image](https://github.com/user-attachments/assets/80fa6e1f-f590-4a07-9a7e-4ec75888883b)

https://otx.alienvault.com/indicator/file/30e527e45f50d2ba82865c5679a6fa998ee0a1755361ab01673950810d071c85

***Q3: Determining the compilation timestamp of malware can reveal insights into its development and deployment timeline. What is the compilation timestamp of the malware that infected our network?***  
**Answer: `2020-09-24 18:26:47`**

![image](https://github.com/user-attachments/assets/ec086cd1-ddfd-4739-8de9-9247bc6ea6ae)

***Q4: Understanding when the broader cybersecurity community first identified the malware could help determine how long the malware might have been in the environment before detection. When was the malware first submitted to VirusTotal?***  
**Answer: `2020-10-15 02:47:37`**  

![image](https://github.com/user-attachments/assets/83119fcd-861c-4bd5-a99c-633c043af79d)
creation time can also be seen here

***Q5: To completely eradicate the threat from Industries' systems, we need to identify all components dropped by the malware. What is the file name dropped by the malware in the Appdata folder?***  
**Answer: `solarmarker.dat`**

![image](https://github.com/user-attachments/assets/51dcdedf-3221-4e3e-8f19-cc7ccd8f2aba)


***Q6: It is crucial to identify the C2 servers with which the malware communicates to block its communication and prevent further data exfiltration. What is the C2 server that the malware is communicating with?***  
**Answer: `https://gogohid.com`**

![image](https://github.com/user-attachments/assets/908636df-7c72-4eae-aae8-72ce0f6ba528)


## **References**

https://www.virustotal.com/gui/file/30e527e45f50d2ba82865c5679a6fa998ee0a1755361ab01673950810d071c85/detection

https://redcanary.com/blog/threat-intelligence/yellow-cockatoo/

https://otx.alienvault.com/indicator/file/30e527e45f50d2ba82865c5679a6fa998ee0a1755361ab01673950810d071c85

https://bazaar.abuse.ch/sample/30e527e45f50d2ba82865c5679a6fa998ee0a1755361ab01673950810d071c85/

