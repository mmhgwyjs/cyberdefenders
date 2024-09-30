# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/redline/">RedLine</a>

**Platform:** CyberDefenders

**Scenario:** As a member of the Security Blue team, your assignment is to analyze a memory dump using Redline and Volatility tools. Your goal is to trace the steps taken by the attacker on the compromised machine and determine how they managed to bypass the Network Intrusion Detection System "NIDS". Your investigation will involve identifying the specific malware family employed in the attack, along with its characteristics. Additionally, your task is to identify and mitigate any traces or footprints left by the attacker.

**Category:** Endpoint Forensics

**Difficulty:** Easy

**File:** `memory.dmp`

**Tools:** `Volatility 3` `VirusTotal` `Exiftool`

> [Volatility](https://github.com/volatilityfoundation/volatility3) is the world's most widely used framework for extracting digital artifacts from volatile memory (RAM) samples.  

**Note:** In this walkthrough, I will use the SIFT Workstation from SANS to analyze the provided file. If you have not set it up yet, I highly recommend following this [forensics lab](https://github.com/mmhgwyjs/forensics-lab/blob/main/README.md) guide for assistance with your installation.

---

## **Preparations**


## **Questions and Answers**

***1. What is the name of the suspicious process?***

oneetx.exe

![image](https://github.com/user-attachments/assets/0b7f9ac2-c828-43c8-a289-6ee6242a701a)

![image](https://github.com/user-attachments/assets/4c896ef4-6b6f-42cc-acc0-2d704c08f5ef)

![image](https://github.com/user-attachments/assets/180f555e-ce7d-426b-a188-09a073bd5855)

![image](https://github.com/user-attachments/assets/741a374c-819d-47aa-bed4-dae1f2fc5687)

sudo python3 /opt/volatility/volatility3/vol.py -f MemoryDump.mem windows.pslist > pslist.txt

sudo python3 /opt/volatility/volatility3/vol.py -f MemoryDump.mem windows.psscan > psscan.txt

sudo python3 /opt/volatility/volatility3/vol.py -f MemoryDump.mem windows.netscan > netscan.txt

***2. What is the child process name of the suspicious process?***

![image](https://github.com/user-attachments/assets/f60184fe-feae-4423-8bdb-bd381a51edc4)

rundll32.exe

***3. What is the memory protection applied to the suspicious process memory region?***

![image](https://github.com/user-attachments/assets/82cc0b21-f9f9-4cff-b71f-bc5090969d3a)

sudo python3 /opt/volatility/volatility3/vol.py -f MemoryDump.mem windows.malfind > malfind.txt

![image](https://github.com/user-attachments/assets/c902b83d-1af0-4d2b-ae6a-f7a4ed3bddf6)

https://www.garykessler.net/library/file_sigs.html

PAGE_EXECUTE_READWRITE

***4. What is the name of the process responsible for the VPN connection?***

![image](https://github.com/user-attachments/assets/6e3b8579-4740-468d-87df-3f496b845456)

![image](https://github.com/user-attachments/assets/e361690b-67de-4285-9d60-d76f1db15de4)

Outline.exe

***5. What is the attacker's IP address?***

77.91.124.20

***6. Based on the previous artifacts, what is the name of the malware family?***

sudo python3 /opt/volatility/volatility3/vol.py -f MemoryDump.mem -o ./dump windows.dumpfiles --pid 5896

![image](https://github.com/user-attachments/assets/745b5542-fa64-4e4d-85fa-ee0e8535b068)

sudo sha256sum file.0xad818da36c30.0xad818ca48660.ImageSectionObject.oneetx.exe.img

![image](https://github.com/user-attachments/assets/a87509ae-e58a-486e-b00b-a4dda3d7896a)

![image](https://github.com/user-attachments/assets/a37a1982-5aad-4764-9b43-934239941670)

![image](https://github.com/user-attachments/assets/f1942c47-a32e-4a46-8258-6d84e6fb5f16)

RedLine Stealer

***7. What is the full URL of the PHP file that the attacker visited?***
![image](https://github.com/user-attachments/assets/b1ba2d99-121a-4f78-88df-900e7c530614)

http://77.91.124.20/store/games/index.php


***8. What is the full path of the malicious executable?***

![image](https://github.com/user-attachments/assets/dac3c48a-234b-4e3b-89ab-0d67a8b37605)
sudo strings pid.5896.dmp | grep "oneetx.exe" 

C:\Users\Tammam\AppData\Local\Temp\c3912af058\oneetx.exe
