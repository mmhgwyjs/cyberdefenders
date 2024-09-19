# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/qradar101/">Qradar101</a>

**Platform:** CyberDefenders

**Scenario:** A financial company was compromised, and they are looking for a security analyst to help them investigate the incident. The company suspects that an insider helped the attacker get into the network, but they have no evidence.
 
The initial analysis performed by the company's team showed that many systems were compromised. Also, alerts indicate the use of well known malicious tools in the network. As a SOC analyst, you are assigned to investigate the incident using QRadar SIEM and reconstruct the events carried out by the attacker.

**Category:** Threat Hunting

**Difficulty:** Medium

**File:** `CD.Qradar.ova`

**Tools:** `tool1` `tool2`

**Note:** For this walkthrough, CyberDefenders has provided a pre-defined VM that we will use for the lab.

---

## **Instructions**

This lab is designed to work with VirtualBox. Download lab VM and uncompress it using the password 'cyberdefenders.org'

> You can download VirtualBox from [here](https://www.virtualbox.org/wiki/Downloads).

- Please make sure to watch the instructional video under the Walkthroughs section.
  
  > I did not see the instructional video, but you can follow along using this guide.
  
- Make sure you have a host-only subnet within the following IP range 192.168.20.0/24.

  ![image](https://github.com/user-attachments/assets/1f2fdd44-a3c3-42fa-b3e0-dd82f971387a)

  > File -> Tools -> Network Manager -> Create

  ![image](https://github.com/user-attachments/assets/8571f362-4077-4278-8067-460c55c96e7a)

  ![image](https://github.com/user-attachments/assets/e11716ed-7950-4256-8a00-8310a2bf9ee0)

  ![image](https://github.com/user-attachments/assets/9d3652bb-96af-4cf5-a310-3c6366113564)

- Assign the proper network adapter (192.168.20.0/24) to the VM before starting it.

  ![image](https://github.com/user-attachments/assets/3b198425-3863-4ac8-8aee-d515aef1b019)

  > Settings -> Network -> Select the adapter we created.

- Wait for some minutes after the import completes then visit: https://192.168.20.21/.
- Challenge credentials: QRadar Dashboard: admin:Admin@123 - SSH: root:cyberdefenders
- In case you face a license issue, please go to > License Pool Management. Edit and set eps > 0 and edit the FPM and set it to 0. This will ensure you will not have a license problem.

> Hardware Requirements: 8GB of memory and 65GB of disk space.

## **Questions and Answers**

***1. How many log sources available?***

***2. What is the IDS software used to monitor the network?***

***3. What is the domain name used in the network?***

***4. Multiple IPs were communicating with the malicious server. One of them ends with "20". Provide the full IP.***

***5. What is the SID of the most frequent alert rule in the dataset?***

***6. What is the attacker's IP address?***

***7. The attacker was searching for data belonging to one of the company's projects, can you find the name of the project?***

***8. What is the IP address of the first infected machine?***

***9. What is the username of the infected employee using 192.168.10.15?***

***10. Hackers do not like logging, what logging was the attacker checking to see if enabled?***

***11. Name of the second system the attacker targeted to cover up the employee?***

***12. When was the first malicious connection to the domain controller (log start time - hh:mm:ss)?***

***13. What is the md5 hash of the malicious file?***

***14. What is the MITRE persistence technique ID used by the attacker?***

***15. What protocol is used to perform host discovery?***

***16. What is the email service used by the company?(one word)***

***17. What is the name of the malicious file used for the initial infection?***

***18. What is the name of the new account added by the attacker?***

***19. What is the PID of the process that performed injection?***

***20. What is the name of the tool used for lateral movement?***

***21. Attacker exfiltrated one file, what is the name of the tool used for exfiltration?***

***22. Who is the other legitimate domain admin other than the administrator?***

***23. The attacker used the host discovery technique to know how many hosts available in a certain network, what is the network the hacker scanned from the host IP 1 to 30?***

***24. What is the name of the employee who hired the attacker?***

---

## **Additional Analysis/Artifacts**

### Static Analysis

**VirusTotal:** 

### Dynamic Analysis

***1. sample testing.***
