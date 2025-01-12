# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/phishstrike/">Lespion</a>

**Platform:** CyberDefenders

**Scenario:** As a cybersecurity analyst for an educational institution, you receive an alert about a phishing email targeting faculty members. The email, appearing from a trusted contact, claims a $625,000 purchase and provides a link to download an invoice.

Your task is to investigate the email using Threat Intel tools. Analyze the email headers and inspect the link for malicious content. Identify any Indicators of Compromise (IOCs) and document your findings to prevent potential fraud and educate faculty on phishing recognition.

**Category:** Threat Intel

**Difficulty:** Medium

**File:** `194-PhishStrike.eml`

**Tools:** `` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**


## **Questions and Answers**

***Q1: Identifying the sender's IP address with specific SPF and DKIM values helps trace the source of the phishing email. What is the sender's IP address that has an SPF value of softfail and a DKIM value of fail?***  
**Answer:** `18.208.22.104`

![image](https://github.com/user-attachments/assets/b035868b-ce62-4695-ae40-b1c586f0c3b4)

***Q2: Understanding the return path of the email helps in tracing its origin. What is the return path specified in this email?***  
**Answer:** `erikajohana.lopez@uptc.edu.co`

![image](https://github.com/user-attachments/assets/d7894352-e464-4e1e-8819-9d2ee7aa938a)

***Q3: Identifying the source of malware is critical for effective threat mitigation and response. What is the IP address hosting the malicious file associated with malware distribution?***  
**Answer:** `107.175.247.199`

![image](https://github.com/user-attachments/assets/49dd087d-d9f8-49e9-b37a-89de61055ed7)

![image](https://github.com/user-attachments/assets/d76a7d05-01dd-4567-8113-3d0d40bc9088)

***Q4: Identifying malware that exploits system resources for cryptocurrency mining is critical for prioritizing threat mitigation efforts. The malicious URL can deliver several malware types. Which malware family is responsible for cryptocurrency mining?***  
**Answer:** coinminer

https://bazaar.abuse.ch/sample/ee1e5fcaf442282176717ce59cc1993b6ec84317669ab6fa66633d9b5c8e172d#comments

![image](https://github.com/user-attachments/assets/f3108c4f-b619-4368-ac31-b95d2d003c26)

https://bazaar.abuse.ch/sample/453fb1c4b3b48361fa8a67dcedf1eaec39449cb5a146a7770c63d1dc0d7562f0/

***Q5: Identifying the specific URLs malware requests is key to disrupting its communication channels and reducing its impact. Based on the previous analysis of the cryptocurrency malware sample, what does this malware request the URL?***  
**Answer:** `****://******.******/******/*******/*********.****`

http://ripley.studio/loader/uploads/Hjvnp.png

https://www.joesandbox.com/analysis/730933/0/executive

http://ripley.studio/loader/uploads/Zcpbmqlst.bmp

https://any.run/report/5ca468704e7ccb8e1b37c0f7595c54df4e2f4035345b6e442e8bd4e11c58f791/63ecee5c-854f-4157-a5f2-698f1cbb3b3f

`http://ripley.studio/loader/uploads/Qanjttrbv.jpeg`

![image](https://github.com/user-attachments/assets/f5b4aa6d-3289-4a9f-a9ac-fec376ec719a)

https://www.virustotal.com/gui/file/453fb1c4b3b48361fa8a67dcedf1eaec39449cb5a146a7770c63d1dc0d7562f0/relations

***Q6: Understanding the registry entries added to the auto-run key by malware is crucial for identifying its persistence mechanisms. Based on the BitRAT malware sample analysis, what is the executable's name in the first value added to the registry auto-run key?***  
**Answer:** `******.***`

Jzwvix.exe

![image](https://github.com/user-attachments/assets/ef48d270-d8a6-4aa9-87a5-c60eeef7b462)

![image](https://github.com/user-attachments/assets/22c11ba9-02b9-4d1d-a952-1b3f286078e3)

![image](https://github.com/user-attachments/assets/ba713486-1a9e-4563-836d-e1fa9b1bee16)

***Q7: Identifying the SHA-256 hash of files downloaded from a malicious URL is essential for tracking and analyzing malware activity. Based on the BitRAT analysis, what is the SHA-256 hash of the file previously downloaded and added to the autorun keys?***  
**Answer:** bf7628695c2df7a3020034a065397592a1f8850e59f9a448b555bc1c8c639539

![image](https://github.com/user-attachments/assets/d2bbace6-5b26-485f-8aee-d698b0eb491e)

https://www.virustotal.com/gui/file/bf7628695c2df7a3020034a065397592a1f8850e59f9a448b555bc1c8c639539/details

***Q8: Analyzing the HTTP requests made by malware helps in identifying its communication patterns. What is the HTTP request used by the loader to retrieve the BitRAT malware?***  
**Answer:** `http://107.175.247.199/loader/server.exe`

![image](https://github.com/user-attachments/assets/5f4e789f-cb6f-4c00-863a-508f4ef7d2ec)

***Q9: Introducing a delay in malware execution can help evade detection mechanisms. What is the delay (in seconds) caused by the PowerShell command according to the BitRAT analysis?***  
**Answer:** 50

![image](https://github.com/user-attachments/assets/df1d6613-8f61-4124-a793-48efe31e53b2)

![image](https://github.com/user-attachments/assets/57e8b84e-0c53-409f-926e-d1734fd70d3d)

***Q10: Tracking the command and control (C2) domains used by malware is essential for detecting and blocking malicious activities. What is the C2 domain used by the BitRAT malware?***  
**Answer:** `gh9st.mywire.org`

![image](https://github.com/user-attachments/assets/38399f90-6783-4f17-ac24-5f86b94e2065)

https://tria.ge/221026-gxvytsehdp/behavioral1

***Q11: Understanding the methods malware uses for exfiltrating data is crucial for detecting and preventing data breaches. According to the AsyncRAT analysis, what is the Telegram Bot ID used by the malware?***  
**Answer:** bot5610920260

![image](https://github.com/user-attachments/assets/b77a2cb9-07a4-4905-88c6-6d51af86fa12)

https://tria.ge/221025-a5kz9sbbcm/behavioral1

![image](https://github.com/user-attachments/assets/28a66ae3-1ea1-46b5-a25f-13dc1cdd88b4)
