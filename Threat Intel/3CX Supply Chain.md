# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/3cx-supply-chain/">3CX Supply Chain</a>

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

File Hash (SHA-256): 59E1EDF4D82FAE4978E97512B0331B7EB21DD4B838B850BA46794D9C7A2C0983

![image](https://github.com/user-attachments/assets/1d17898a-0d34-4bc7-900d-3858c3860b33)

Get-FileHash .\3CXDesktopApp-18.12.416.msi -Algorithm SHA256

## **Questions and Answers**

***Q1: Understanding the scope of the attack and identifying which versions exhibit malicious behavior is crucial for making informed decisions if these compromised versions are present in the organization. How many versions of 3CX running on Windows have been flagged as malware?***  
**Answer: `2`**

![image](https://github.com/user-attachments/assets/31172fed-7361-44f6-95b3-d03792c6cb0f)

https://thehackernews.com/2023/03/3cx-supply-chain-attack-heres-what-we.html

***Q2: Determining the age of the malware can help assess the extent of the compromise and track the evolution of malware families and variants. What's the UTC creation time of the .msi malware?***  
**Answer: `2023-03-13 06:33:26 UTC`**

![image](https://github.com/user-attachments/assets/7dc30fbd-457d-4b54-9e98-81b3851b3e4b)
 exiftool .\3CXDesktopApp-18.12.416.msi

 ![image](https://github.com/user-attachments/assets/09f86d3c-edfe-4525-87e8-71ea814c53aa)


***Q3: Executable files (.exe) are frequently used as primary or secondary malware payloads, while dynamic link libraries (.dll) often load malicious code or enhance malware functionality. Analyzing files deposited by the Microsoft Software Installer (.msi) is crucial for identifying malicious files and investigating their full potential. Which malicious DLLs were dropped by the .msi file?***  
**Answer: `ffmpeg.dll d3dcompiler_47.dll`**

![image](https://github.com/user-attachments/assets/ed4d7e56-6794-46fb-8563-a6ca38ea132c)

***Q4: Recognizing the persistence techniques used in this incident is essential for current mitigation strategies and future defense improvements. What is the MITRE sub-technique ID employed by the .msi files to load the malicious DLL?***  
**Answer: `T1574.002`**

![image](https://github.com/user-attachments/assets/35f9c762-c374-4b31-aad3-629412b5edea)

***Q5: Recognizing the malware type (threat category) is essential to your investigation, as it can offer valuable insight into the possible malicious actions you'll be examining. What is the malware family of the two malicious DLLs?***  
**Answer: `trojan`**

![image](https://github.com/user-attachments/assets/95dc716b-481d-4e55-a471-4710d3ec9563)

11be1803e2e307b647a8a7e02d128335c448ff741bf06bf52b332e0bbf423b03
![image](https://github.com/user-attachments/assets/569bd801-d0a1-4f7c-a0e4-c5c728440627)


7986bbaee8940da11ce089383521ab420c443ab7b15ed42aed91fd31ce833896

![image](https://github.com/user-attachments/assets/86aaaa90-1632-4f03-a8cd-b37b4c355a3d)

***Q6: As a threat intelligence analyst conducting dynamic analysis, it's vital to understand how malware can evade detection in virtualized environments or analysis systems. This knowledge will help you effectively mitigate or address these evasive tactics. What is the MITRE ID for the virtualization/sandbox evasion techniques used by the two malicious DLLs?***  
**Answer: `T1497`**

![image](https://github.com/user-attachments/assets/569f6548-e5f3-44ba-a0aa-921ebd2be7a8)

![image](https://github.com/user-attachments/assets/8b188f74-caed-4564-b17e-8eb43f102169)


***Q7: When conducting malware analysis and reverse engineering, understanding anti-analysis techniques is vital to avoid wasting time. Which hypervisor is targeted by the anti-analysis techniques in the ffmpeg.dll file?***  
**Answer: `VMWare`**

![image](https://github.com/user-attachments/assets/d3386185-fe0d-439d-9f22-46636f055b78)


***Q8: Identifying the cryptographic method used in malware is crucial for understanding the techniques employed to bypass defense mechanisms and execute its functions fully. What encryption algorithm is used by the ffmpeg.dll file?***  
**Answer: `RC4 `**

![image](https://github.com/user-attachments/assets/33e57fd2-ece0-4372-8ba5-561d68dcfc7f)


***Q9: As an analyst, you've recognized some TTPs involved in the incident, but identifying the APT group responsible will help you search for their usual TTPs and uncover other potential malicious activities. Which group is responsible for this attack?***  
**Answer: `Lazarus`**

![image](https://github.com/user-attachments/assets/130d528f-1ef7-4aec-83b0-b050ff7dcf88)

https://thehackernews.com/2023/03/3cx-supply-chain-attack-heres-what-we.html

![image](https://github.com/user-attachments/assets/2f30d593-fb42-48a8-991c-233d584c3489)

https://news.sophos.com/en-us/2023/03/29/3cx-dll-sideloading-attack/

using chatgpt

![image](https://github.com/user-attachments/assets/c5b2cb96-2d15-4582-b554-0d933a80efe5)

