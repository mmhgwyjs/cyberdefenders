# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/hawkeye/">HawkEye </a>

**Platform:** CyberDefenders

**Scenario:** An accountant at your organization received an email regarding an invoice with a download link. Suspicious network traffic was observed shortly after opening the email. As a SOC analyst, investigate the network trace and analyze exfiltration attempts.

**Category:** Network Forensics

**Difficulty:** Medium

**Files:** ``

**Tools:** `Wireshark`

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

## **Questions and Answers**

![image](https://github.com/user-attachments/assets/6f7702b2-4616-4290-990b-2573eb266caa)

***1. How many packets does the capture have?***  
**Answer: `4003`**

***2. At what time was the first packet captured?***
**Answer: `2019-04-10 20:37:07 UTC`**

***3. What is the duration of the capture?***

**Answer: 01:03:41**

***4. What is the most active computer at the link level?***

**Answer: 00:08:02:1c:47:ae**

![image](https://github.com/user-attachments/assets/65899d83-4cb2-46f3-a1d6-aa0ffac5da12)

***5. Manufacturer of the NIC of the most active system at the link level?***

Hewlett-Packard

![image](https://github.com/user-attachments/assets/cc35fd84-0bb6-4060-bb7a-7b325a9bf4a6)

***6. Where is the headquarter of the company that manufactured the NIC of the most active computer at the link level?***

Palo Alto

![image](https://github.com/user-attachments/assets/12053b34-1dbe-4cc9-9722-b716eeca9951)

***7. The organization works with private addressing and netmask /24. How many computers in the organization are involved in the capture?***

3

![image](https://github.com/user-attachments/assets/89f09989-a553-49c1-ad29-ad4e947c46f9)

.255 is not included since it is a broadcast address

***8. What is the name of the most active computer at the network level?***

BEIJING-5CD1-PC

![image](https://github.com/user-attachments/assets/2a7d00bd-2084-410b-98d2-992a36975403)

![image](https://github.com/user-attachments/assets/6c5b3cdb-3a27-4f31-bd98-6c8f30cf8017)

![image](https://github.com/user-attachments/assets/8f2e6dce-e6e9-42e6-96a2-007cb325abdd)

***9. What is the IP of the organization's DNS server?***

10.4.10.4

![image](https://github.com/user-attachments/assets/96ff94f9-a058-4022-84f6-825cd17ecd64)

port 53 - DNS

***10. What domain is the victim asking about in packet 204?***

proforma-invoices.com

![image](https://github.com/user-attachments/assets/c599fca9-64e8-43c1-9f34-1b92c76fc076)

***11. What is the IP of the domain in the previous question?***

![image](https://github.com/user-attachments/assets/d343ee05-ce46-4e5a-8ec6-c82341698483)

217.182.138.150
