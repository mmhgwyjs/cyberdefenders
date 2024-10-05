# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/hireme/">HireMe</a>

**Platform:** CyberDefenders

**Scenario:** Karen is a security professional looking for a new job. A company called "TAAUSAI"  offered her a position and asked her to complete a couple of tasks to prove her technical competency. As a soc analyst Analyze the provided disk image and answer the questions based on your understanding of the cases she was assigned to investigate.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `Horcrux.ad1` `Horcrux.ad1.txt`

**Tools:** `FTK Imager` `Autopsy` `Registry Explorer` `MFTECmd.exe` `Timeline Explorer`

> [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) is a free data preview and imaging tool used to acquire electronic evidence in a forensically sound manner by creating copies of computer data without making changes to the original evidence.

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

![image](https://github.com/user-attachments/assets/4bf64fe1-a4fe-4aff-87b5-203e723327ca)

![image](https://github.com/user-attachments/assets/dc44ae38-7f37-4c85-81b0-19260a6a5c24)

![image](https://github.com/user-attachments/assets/1d9cb1e8-df64-43e2-a09d-26be927d9997)

![image](https://github.com/user-attachments/assets/5e4d3005-8020-4519-8972-5d4df9cd9674)

![image](https://github.com/user-attachments/assets/6dd9a4a0-8e3b-4bd4-95e9-9b24dd6934a9)

![image](https://github.com/user-attachments/assets/32adc44c-f019-4102-bac8-3b98aae2bcf2)

![image](https://github.com/user-attachments/assets/e225f870-b472-45e4-b725-d8a3efe1684a)

## **Questions and Answers**

***1. What is the administrator's username?***
karen
![image](https://github.com/user-attachments/assets/ba8dbc4e-e781-479a-9f27-986b8764d380)

![image](https://github.com/user-attachments/assets/3ce788a0-7de3-44d3-9a02-66fec86ce10f)

***2. What is the OS's build number?***
![image](https://github.com/user-attachments/assets/803a8525-0be2-4d29-bbdf-4c0b182f5516)

![image](https://github.com/user-attachments/assets/6ee71c2f-7837-478c-bafa-dbe96651e28f)
![image](https://github.com/user-attachments/assets/8f4a3f56-3b27-4855-b71f-db2aeb7c4cfd)


***3. What is the hostname of the computer?***
![image](https://github.com/user-attachments/assets/4c0f8d21-6b49-46ca-893e-5342f2f470bf)

TOTALLYNOTAHACK

![image](https://github.com/user-attachments/assets/eb6858d6-5079-4490-a3a0-529e15723666)

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName
![image](https://github.com/user-attachments/assets/44951541-1e05-4f8b-96e7-0f7997bcf602)

***4. A messaging application was used to communicate with a fellow Alpaca enthusiast. What is the name of the software?***
![image](https://github.com/user-attachments/assets/bbabde94-6393-4fbb-a708-8327af56fc80)

HLKM\Software\Microsoft\Windows\CurrentVersion\Uninstall
WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall
skype

![image](https://github.com/user-attachments/assets/d0de6ab3-c9b6-478f-ad4c-11ded9144c90)


***5. What is the zip code of the administrator's post?***

![image](https://github.com/user-attachments/assets/f3fbca21-81b7-4c68-bf6e-e7da65e52188)
19709

***6. What are the initials of the person who contacted the admin user from TAAUSAI?***

MS

![image](https://github.com/user-attachments/assets/fc3c6dc3-0952-400c-a250-78c98e65370c)

![image](https://github.com/user-attachments/assets/7903d4f6-cc71-42aa-a022-291b67b6905d)

![image](https://github.com/user-attachments/assets/48708747-f84d-4a9d-b38b-1921d127fac4)

***7. How much money was TAAUSAI willing to pay upfront?***
150000
![image](https://github.com/user-attachments/assets/4a61e5e1-43e0-484d-8cdf-d24a5a488c5e)

![image](https://github.com/user-attachments/assets/49ec9a79-e991-429f-8893-e66ea3c8aff0)

***8. What country is the admin user meeting the hacker group in?***

egypt

![image](https://github.com/user-attachments/assets/5e53ac9b-ceec-4ab6-bed5-646d01290b3e)

![image](https://github.com/user-attachments/assets/8fd7d1a0-200a-439b-889c-69e4b24ab4b7)

***9. What is the machine's timezone? (Use the three-letter abbreviation)***
![image](https://github.com/user-attachments/assets/10c4cdda-143a-4d49-bd63-67755b20741d)

HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation
UTC

***10. When was AlpacaCare.docx last accessed?***

![image](https://github.com/user-attachments/assets/102cc8e4-634b-4cf2-be07-a7d0858b0b6e)

![image](https://github.com/user-attachments/assets/8b427533-66d3-4ecb-ada9-3910cfd3dcaa)

3/17/2019 9:52:20 PM

03/17/2019 09:52 PM

![image](https://github.com/user-attachments/assets/4c1653ea-3fe2-4f58-bd77-f07f9eeb8b9c)

mftecmd.exe
mftecmd.exe -f $MFT --csv C:\Users\flrvm2\Documents\CD\62-HireMe --csvf mft.csv

![image](https://github.com/user-attachments/assets/baa684e2-76f2-4b4d-9d03-b9ed8d81186a)

![image](https://github.com/user-attachments/assets/e0acb166-421b-4248-a7b3-39574f7b40fe)

![image](https://github.com/user-attachments/assets/303d9241-f13f-4b9d-a2e2-afc08146ea65)

***11. There was a second partition on the drive. What is the letter assigned to it?***
A

![image](https://github.com/user-attachments/assets/84c3eea0-875b-4649-9568-bca0e46e5d32)

***12. What is the answer to the question Company's manager asked Karen?***
TheCardCriesNoMore


![image](https://github.com/user-attachments/assets/dcdce0db-8b4f-49e7-acef-4523701b80ce)

![image](https://github.com/user-attachments/assets/deb9aadc-3f93-470b-90cb-bcd01b5f9752)

VGhlQ2FyZENyaWVzTm9Nb3Jl

***13. What is the job position offered to Karen? (3 words, 2 spaces in between)***
cyber security analyst

![image](https://github.com/user-attachments/assets/3d59498b-e4b8-4cef-9f58-3fbe807e2ac8)

***14. When was the admin user password last changed?***
03/21/2019 19:13:09
![image](https://github.com/user-attachments/assets/bcf902d6-2bb3-4ae8-bc4a-c5fc2a2baf5c)

![image](https://github.com/user-attachments/assets/ce216516-bb6e-47fa-ba73-ca0c9b9b5202)

***15. What version of Chrome is installed on the machine?***
72.0.3626.121
![image](https://github.com/user-attachments/assets/64339bc1-9cea-43a3-b13f-3221120c5452)

***16. What is the URL used to download Skype?***

![image](https://github.com/user-attachments/assets/4464d26c-ac78-4f0c-a4bf-4add056906f1)

https://download.skype.com/s4l/download/win/Skype-8.41.0.54.exe

![image](https://github.com/user-attachments/assets/2402bce8-3227-4f55-b1db-e8359883fd5d)

***17. What is the domain name of the website Karen browsed on Alpaca care that the file AlpacaCare.docx is based on?***

![image](https://github.com/user-attachments/assets/b6b5a823-d260-4e8a-95c5-329e1a8c9c8a)

![image](https://github.com/user-attachments/assets/f9dfa490-220a-4182-8548-630ababde606)

![image](https://github.com/user-attachments/assets/53c49a75-146e-44dd-b570-43f50bcaff74)

![image](https://github.com/user-attachments/assets/d96e433d-e73f-49f3-aedc-09f1fe9aa6fe)

palominoalpacafarm.com
