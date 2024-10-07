
# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/danabot/">DanaBot</a>

**Platform:** CyberDefenders

**Scenario:** Our SOC team detected suspicious activity in the network traffic. A machine has been compromised, and company information that should not have been there has now been stolen. It’s up to you to determine what happened and what data was taken.

**Category:** Network Forensics

**Difficulty:** Easy

**Files:** `205-DanaBot.pcap`

**Tools:** `Wireshark`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/0068c36b-9b1e-4764-af19-7f4506015c9f)

![image](https://github.com/user-attachments/assets/4cac96b7-b3cf-4853-9a0b-c0219cb22e3e)

## **Questions and Answers**

***1. What is the IP address used by the attacker in initial access?***

![image](https://github.com/user-attachments/assets/8d95c4d0-19b4-4e9e-a6c2-57eba967da5f)

62.173.146.41

***2. What is the malicious file name used for initial access?***

![image](https://github.com/user-attachments/assets/c22864af-8457-4078-b71d-f505a9e061b7)

allegato_708.js

![image](https://github.com/user-attachments/assets/d9c0cd78-ab6a-4596-bb85-ac1da0abc65f)

***3. What is the SHA256 hash of the mentioned file?***

![image](https://github.com/user-attachments/assets/370ea879-2fa7-4e7b-b5f6-c1da8f844de8)

![image](https://github.com/user-attachments/assets/57d06e33-9d1d-4585-88fd-4f7859b0177f)

847B4AD90B1DABA2D9117A8E05776F3F902DDA593FB1252289538ACF476C4268

 Get-FileHash .\login.php -Algorithm SHA256

 ![image](https://github.com/user-attachments/assets/d6ffff11-52d4-4fc5-bca1-ca0aead004bc)

***4. What is the process used to execute the malicious file?***

![image](https://github.com/user-attachments/assets/e7f6ae3a-af18-4381-b327-3e49fba5341f)

![image](https://github.com/user-attachments/assets/6cf6e723-716b-4e98-9d49-84303d825d0d)


wscript.exe


***5. What is the extension of the second malicious file used by the attacker?***

![image](https://github.com/user-attachments/assets/36ca0e14-88cb-426f-90fd-00b7a855ce35)

![image](https://github.com/user-attachments/assets/26504c3b-4a15-42af-ad32-89f272840ec5)

.dll

***6. What is the MD5 hash of the second malicious file?***
![image](https://github.com/user-attachments/assets/4a465890-d1bb-41bc-a9df-2ecba6f0819d)

Get-FileHash .\resources.dll -Algorithm MD5

E758E07113016ACA55D9EDA2B0FFEEBE


***7. What is the last malicious IP address in the PCAP that is known to be used as CnC by DanaBot?***

91.201.67.85

![image](https://github.com/user-attachments/assets/70d6f546-2b14-4265-8920-85ddbc967705)

ip.src == 10.2.14.101

![image](https://github.com/user-attachments/assets/810989fd-2bdb-4588-a9ec-ff7edaaf8083)

ip.addr == 62.173.146.41
