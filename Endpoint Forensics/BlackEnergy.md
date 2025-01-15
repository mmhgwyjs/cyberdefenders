# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/blackenergy/">BlackEnergy</a>

**Platform:** CyberDefenders

**Scenario:** A multinational corporation has been hit by a cyber attack that has led to the theft of sensitive data. The attack was carried out using a variant of the BlackEnergy v2 malware that has never been seen before. The company's security team has acquired a memory dump of the infected machine, and they want you, as a soc analyst, to analyze the dump to understand the attack scope and impact.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**File:** `memory.dmp`

**Tools:** `Volatility 3` `VirusTotal` `Exiftool`

> [Volatility](https://github.com/volatilityfoundation/volatility3) is the world's most widely used framework for extracting digital artifacts from volatile memory (RAM) samples.  

**Note:** In this walkthrough, I will use our Forensic Workstation to analyze the provided file. If you have not set it up yet, I highly recommend following this [forensics lab](https://github.com/mmhgwyjs/forensics-lab/blob/main/README.md) guide for assistance with your installation.

---

## **Preparations**


## **Questions and Answers**

***1. Which volatility profile would be best for this machine?***  

WinXPSP2x86

![image](https://github.com/user-attachments/assets/f63975b3-6b71-436c-9395-dfd4fa13fb1a)

vol -f CYBERDEF-567078-20230213-171333.raw windows.info

I am using Volatility 3, and the profile is not visible with the info plugin. Instead, I use ChatGPT to determine it based on the results above.

***2. How many processes were running when the image was acquired?***  

19

![image](https://github.com/user-attachments/assets/e3e232aa-921a-4d4d-bd18-8d5bf8314d79)

vol -f CYBERDEF-567078-20230213-171333.raw windows.psscan

check the exit column, it will show the exit time

***3. What is the process ID of cmd.exe?***  

1960 

![image](https://github.com/user-attachments/assets/b4ed01cf-66a5-4933-987f-efebb5def62d)

***4. What is the name of the most suspicious process?***  

rootkit.exe

![image](https://github.com/user-attachments/assets/bd0e1529-3ecf-4fad-b66e-5f9cdebd8f74)

***5. Which process shows the highest likelihood of code injection?***  

***6. There is an odd file referenced in the recent process. Provide the full path of that file.***  
Example Full Path: `C:\Windows\...\file.sys`  

***7. What is the name of the injected DLL file loaded from the recent process?***  

***8. What is the base address of the injected DLL?***  
