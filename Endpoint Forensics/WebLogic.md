# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/weblogic/">WebLogic</a>

**Platform:** CyberDefenders

**Scenario:** The #NSM gear flagged suspicious traffic coming from one of the organization's web servers. As a soc analyst, analyze the server's captured memory logs files and figure out what happened.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `N/A`

**Tools:** `Volatility` `CobaltStrikeParser`

**Note:** In this walkthrough, CyberDefenders offers a lab environment for us to utilize. This feature is included with the PRO subscription.

## **Preparations** 
  
## **Questions and Answers**

***1. What is the version of the WebLogic server installed on the system?***

***2. The admin set a port forward rule to redirect the traffic from the public port to the WebLogic admin portal port. What is the public and WebLogic admin portal port number? Format PublicPort:WebLogicPort (22:1337)***

***3. The attacker gained access through WebLogic Server. What is the PID of the process responsible for the initial exploit?***

***4. The attacker used the vulnerability he found in the webserver to execute a reverse shell command to his own server. Provide the IP and port of the attacker server? Format: IP:port***

***5. Multiple files were downloaded from the attacker's web server. Provide the command used to download the PowerShell script used for persistence?***

***6. What is the MITRE ID related to the persistence technique the attacker used?***

***7. After maintaining persistence, the attacker dropped a Cobalt Strike beacon. Try to analyze it and provide the User-Agent.***

***8. What is the URL of the exfiltrated data?***
