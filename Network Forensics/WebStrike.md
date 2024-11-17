# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/webstrike/">WebStrike</a>

**Platform:** CyberDefenders

**Scenario:** An anomaly was discovered within our company's intranet as our Development team found an unusual file on one of our web servers. Suspecting potential malicious activity, the network team has prepared a pcap file with critical network traffic for analysis for the security team, and you have been tasked with analyzing the pcap.

**Category:** Network Forensics

**Difficulty:** Easy

**Files:** `BlueSkyRansomware.pcap` `BlueSkyRansomware.evtx` `javaw.exe`

**Tools:** `Wireshark`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/e16226da-0fac-46f9-8ceb-dbfa3148de51)

## **Questions and Answers**

***1. Understanding the geographical origin of the attack aids in geo-blocking measures and threat intelligence analysis. What city did the attack originate from?***  
**Answer: `tianjin`**

Statistics > Conversations > IPv4

![image](https://github.com/user-attachments/assets/8d89ae9c-149f-4af8-8dac-4524281fe69e)

![image](https://github.com/user-attachments/assets/76f859e1-2ab6-4afc-bcbe-73eb9c1803e0)

***2. Knowing the attacker's user-agent assists in creating robust filtering rules. What's the attacker's user agent?***  
**Answer: `Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0`**

![image](https://github.com/user-attachments/assets/e659665f-74dd-438f-910f-3f59800aefd9)

Follow TCP stream 
                                         
***3. We need to identify if there were potential vulnerabilities exploited. What's the name of the malicious web shell uploaded?***  
**Answer: `image.jpg.php`**

![image](https://github.com/user-attachments/assets/9348fff3-50a8-4363-b410-9b1e58bb569f)

![image](https://github.com/user-attachments/assets/01b8ec5b-0497-47e4-9c97-21d77d73bcc7)

***4. Knowing the directory where files uploaded are stored is important for reinforcing defenses against unauthorized access. Which directory is used by the website to store the uploaded files?***  
**Answer: `/*******/*******/`**

***5. Identifying the port utilized by the web shell helps improve firewall configurations for blocking unauthorized outbound traffic. What port was used by the malicious web shell?***  
**Answer: `****`**

***6. Understanding the value of compromised data assists in prioritizing incident response actions. What file was the attacker trying to exfiltrate?***  
**Answer: `******`**
