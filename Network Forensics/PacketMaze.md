# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/packetmaze/">PacketMaze</a>

**Platform:** CyberDefenders

**Scenario:** A company's internal server has been flagged for unusual network activity, with multiple outbound connections to an unknown external IP. Initial analysis suggests possible data exfiltration. Investigate the provided network logs to determine the source and method of compromise.

**Category:** Network Forensics

**Difficulty:** Medium

**Files:** ``

**Tools:** `Wireshark`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**



## **Questions and Answers**

***1. What is the FTP password?***

AfricaCTF2021

***2. What is the IPv6 address of the DNS server used by 192.168.1.26?***

fe80::c80b:adff:feaa:1db7

***3. What domain is the user looking up in packet 15174?***

www.7-zip.org

***4. How many UDP packets were sent from 192.168.1.26 to 24.39.217.246?***

10

***5. What is the MAC address of the system under investigation in the PCAP file?***

c8:09:a8:57:47:93
