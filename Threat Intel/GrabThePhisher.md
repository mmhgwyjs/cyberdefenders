# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/grabthephisher/">GrabThePhisher</a>

**Platform:** CyberDefenders

**Scenario:** An attacker compromised a server and impersonated https://pancakeswap.finance/, a decentralized exchange native to BNB Chain, to host a phishing kit at https://apankewk.soup.xyz/mainpage.php. The attacker set it as an open directory with the file name "pankewk.zip".  Provided the phishing kit, you as a soc analyst are requested to analyze it and do your threat intel homework.

**Category:** Threat Intel

**Difficulty:** Easy

**File:** `hash.txt`

**Tools:** `Google` 

**Note:** In this walkthrough, we will use our OSINT skills. All we need is the Internet.

---

## **Preparations**

MD5 Hash: 12c1842c3ccafe7408c23ebf292ee3d9 

## **Questions and Answers**

***Q1:What wallet is used for asking the seed phrase?***
**Answer: `metamask`**

![image](https://github.com/user-attachments/assets/47be8401-4ba7-4c1f-82df-22240f3ec34e)

***Q2 What is the file name that has the code for the phishing kit?***

**Answer: `metamask.php`**

![image](https://github.com/user-attachments/assets/b0735c66-95fb-4774-a73c-ceaef92d82a2)


***Q3: In which language was the kit written?***

**Answer: `php`**

***Q4: What service does the kit use to retrieve the victim's machine information?***

sypex geo

![image](https://github.com/user-attachments/assets/6cb60321-9544-4ab9-90ff-abd6122ebe91)

https://github.com/hostbrook/sypex-geo

***Q5: How many seed phrases were already collected?***

3

![image](https://github.com/user-attachments/assets/be692910-397a-4d79-8450-0254363335dd)


***Q6: Write down the seed phrase of the most recent phishing incident?***

`father also recycle embody balance concert mechanic believe owner pair muffin hockey`

***Q7: Which medium had been used for credential dumping?***
telegram

***Q8: What is the token for the channel?***
5457463144:AAG8t4k7e2ew3tTi0IBShcWbSia0Irvxm10

***Q9: What is the chat ID of the phisher's channel?***
5442785564

***Q10: What are the allies of the phish kit developer?***
 
***Q11: What is the full name of the Phish Actor?***

***Q12: What is the username of the Phish Actor?***
