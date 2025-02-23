![image](https://github.com/user-attachments/assets/32b30870-4d06-45e9-8ec7-bd0835648031)![image](https://github.com/user-attachments/assets/3ce6cfdc-36af-4805-9262-d18f252dc1b0)![image](https://github.com/user-attachments/assets/55707645-1c62-468e-b549-75783c04adfb)![image](https://github.com/user-attachments/assets/5ec93d1a-8b9f-4389-90b5-1cb3b7101540)# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/mrgamer/">MrGamer</a>

**Platform:** CyberDefenders

**Scenario:** This #Linux image belongs to a user who likes to play games and communicate with friends. Is there something happening under the hood? Test drive your #LinuxForensics skills and identify anomalies!

As a soc analyst, analyze the artifacts and answer the questions.

Resources: [Linux Artifacts - Targeted Locations Quick Reference Guide](https://www.magnetforensics.com/resources/targeted-locations-quick-reference-guide-for-linux-artifacts/)

**Category:** Endpoint Forensics

**Difficulty:** Medium

**Files:** `N/A`

**Tools:** `` 

**Note:** In this walkthrough, CyberDefenders offers a lab environment for us to utilize. This feature is included with the PRO subscription.

## **Preparations** 
  
## **Questions and Answers**

***1. I use print statements for my logging -> What is the name of the utility/library the user was looking at exploits for?***  
log4j

![image](https://github.com/user-attachments/assets/4f7dbcd4-0bbe-4bcb-a0ed-fcf03f808f8e)

/home/rafael/.bash_history

port 4444 - It's frequently used with tools like Metasploit, where it serves as the default port for payloads like meterpreter.

***2. Mischievous Lemur -> What is the version ID number of the operating system on the machine?***  
21.10

![image](https://github.com/user-attachments/assets/0689e3c4-2ece-4d4b-bd7f-baf14f4f5dcb)
/etc/os-release

![image](https://github.com/user-attachments/assets/6ebcd38d-f1c9-4703-ba62-27d88e1b2a61)
/usr/lib/os-release

***3. $whoami -> What is the hostname of the computer?***  
rshell-lenovo

![image](https://github.com/user-attachments/assets/c7c55fd7-8fa7-47c1-911a-450fcaf5a410)
/etc/hostname

***4. A little blue birdie told me -> What is one anime that the user likes?***  

attack on titan

![image](https://github.com/user-attachments/assets/98806e01-78ee-4de5-b1ba-4975c88002f2)

I thought Twitter first then I saw thunderbird mail which is a blue bird as well. Then I checked the mailbox and see the Twitter-related events.

/home/rafael/.thunderbird/vrvcx2qf.default-release/ImapMail/imap.gmail.com/INBOX.msf

***5. Into the Matrix, we go -> What is the UUID for the attacker's Minecraft account?***  

8b0dec19-b463-477e-9548-eef20c861492

![image](https://github.com/user-attachments/assets/d5557ea1-6573-48d6-9250-707e082922b7)

/home/rafael/.minecraft/user-cache.json

***6. Today's Youtube video is sponsored by... -> What VPN client did the user install and use on the machine?***  

zerotier

![image](https://github.com/user-attachments/assets/fbd2ddbc-a275-4f1d-b491-58d570f217bf)

/home/rafael/.bash_history

![image](https://github.com/user-attachments/assets/3600f51c-a137-4f96-9e2b-1e407d63b21a)

***7. Be our guest -> What was the user's first password for the guest wifi?***  

![image](https://github.com/user-attachments/assets/c1649231-1a59-4c83-9390-26932b923b06)

/etc/NetworkManager/system-connections/Ezmoneynmconnection

093483

![image](https://github.com/user-attachments/assets/bda51ff7-82ec-49f4-ae0f-77ef010ba3bf)

but not the first

/home/rafael/.thunderbird/vrvcx2qf.default-release/ImapMail/imap.gmail.com/INBOX

![image](https://github.com/user-attachments/assets/1ce86d6a-990f-475b-9633-e48d610389ba)

***8. If a picture is worth a thousand words, how many is a video worth? -> The user watched a video that premiered on Dec 11th, 2021. How many views did it have when they watched it on February 9th?***  

I first look into mozilla files but did not find it

![image](https://github.com/user-attachments/assets/e685cda2-2df7-48ff-b66e-8d65a3ea0c6d)

265342

/home/rafael/pictures/Screenshot from 2022-02-09 16-42-10.png

***9. I'm hungry for videos -> What is the new channel name for the YouTuber whose cookbook is shown on the device?***  

Babish Culinary Universe

***10. Hunt the Wumpus -> What is the module with the highest installed version for the chat application with the mascot Wumpus?***  

***11. It's raining ocelots and wolves -> According to Windows, what was the temperature in Fahrenheit on February 11th, 2022, at 6:30 PM?***  

***12. Never gonna give... up on this question -> What is the upload date of the second YouTube video on the channel from which the user downloaded a YouTube video?***  

***13. Buzzy Bees -> What is the SHA-1 hash of Minecraft's "latest" release according to the system?***  
SHA1 Hash SHA1 Hash  

***14. The RCE is base(64)d on what? -> What were the three flags and their values that were passed to powercat? The answer must be provided in the same format as the entered command. (For example, if the command was "powercat -D Y -l a -n," the answer would be "-D Y -l a -n")***  
Flags(e.g.,-c 192.**...) Flags(e.g.,-c 192.**...)  

***15. Hello (New) World -> How many dimensions (including the overworld) did the player travel to in the "oldest of the worlds"?***  

***16. Matrix_1999 is the key! -> What is the mojangClientToken stored in the Keystore?***  
