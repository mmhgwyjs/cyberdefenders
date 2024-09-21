# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/ramnit/">Ramnit</a>

**Platform:** CyberDefenders

**Scenario:** Our intrusion detection system has alerted us to suspicious behavior on a workstation, pointing to a likely malware intrusion. A memory dump of this system has been taken for analysis. Your task is to analyze this dump, trace the malware’s actions, and report key findings. This analysis is critical in understanding the breach and preventing further compromise.

**Category:** Endpoint Forensics

**Difficulty:** Easy

**File:** `file`

**Tools:** `Volatility 3`

**Note:** For this walkthrough, I have created an isolated virtual machine to analyze the provided file. If you have not set it up yet, I highly suggest following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for your setup. 

**Note:** For this walkthrough, I have spun up a Kali Linux virtual machine to utilize its tools. If you haven't set it up yet, I highly suggest following this [pentest lab](https://github.com/mmhgwyjs/pentest-lab) guide for your setup.

---

## **Questions and Answers:**

***1. We need to identify the process responsible for this suspicious behavior. What is the name of the suspicious process?***

***2. To eradicate the malware, what is the exact file path of the process executable?***

***3. Identifying network connections is crucial for understanding the malware's communication strategy. What is the IP address it attempted to connect to?***

***4. To pinpoint the geographical origin of the attack, which city is associated with the IP address the malware communicated with?***

***5. Hashes provide a unique identifier for files, aiding in detecting similar threats across machines. What is the SHA1 hash of the malware's executable?***

***6. Understanding the malware's development timeline can offer insights into its deployment. What is the compilation UTC timestamp of the malware?***

***7. Identifying domains involved with this malware helps in blocking future malicious communications and identifying current possible communications with that domain in our network. Can you provide the domain related to the malware?***

---

## **Additional Analysis/Artifacts**

### Static Analysis

**VirusTotal:** 

### Dynamic Analysis

***1. sample testing.***
