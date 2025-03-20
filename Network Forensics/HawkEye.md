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


***12. Indicate the country to which the IP in the previous section belongs.***

France

![image](https://github.com/user-attachments/assets/fa6822dd-dcd0-41ad-b526-a7ebafefd773)

217.182.138.150

***13. What operating system does the victim's computer run?***

windows NT 6.1

![image](https://github.com/user-attachments/assets/bcabb029-1f7d-4059-a6f8-3a70cf7abf7e)

![image](https://github.com/user-attachments/assets/bbaeba5a-b03a-45c2-99b2-36e2196997e9)

***14. What is the name of the malicious file downloaded by the accountant?***

tkraw_Protected99.exe

http.request.method == "GET"

![image](https://github.com/user-attachments/assets/107fbd98-5eef-4093-a26f-3bdda3caa9d8)

![image](https://github.com/user-attachments/assets/2dadbc9c-8a9d-44a1-9a77-2b278bfc0935)

***15. What is the md5 hash of the downloaded file?***

File > Export Objects > HTTP

![image](https://github.com/user-attachments/assets/b0d40e27-0e69-4acb-8687-312afe93853e)

![image](https://github.com/user-attachments/assets/a605aa6c-eb3c-46ef-8b47-674dd901f835)

Get-FileHash .\tkraw_Protected99.exe -Algorithm MD5

71826BA081E303866CE2A2534491A2F7

![image](https://github.com/user-attachments/assets/fae1c8ec-a415-48b1-a8f4-37c5367574de)

***15. What software runs the webserver that hosts the malware?***

LiteSpeed

![image](https://github.com/user-attachments/assets/481da200-1dd1-4c69-82b1-453b376cbb4d)

***16. What is the public IP of the victim's computer?***

173.66.146.112

![image](https://github.com/user-attachments/assets/11eb77a6-0a40-435d-96ee-17d088ca8d39)

***18. In which country is the email server to which the stolen information is sent?***

United States

![image](https://github.com/user-attachments/assets/59846e45-dbe2-48a7-b812-93672aa8d23b)
