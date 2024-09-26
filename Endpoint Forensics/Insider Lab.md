# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/insider/">Insider Lab</a>

**Platform:** CyberDefenders

**Scenario:** Our intrusion detection system has alerted us to suspicious behavior on a workstation, pointing to a likely malware intrusion. A memory dump of this system has been taken for analysis. Your task is to analyze this dump, trace the malware’s actions, and report key findings. This analysis is critical in understanding the breach and preventing further compromise.

**Category:** Endpoint Forensics

**Difficulty:** Easy

**Files:** `FirstHack.ad1` `FirstHack.ad1.txt`

**Tools:** `FTK Imager`

> [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) is a free data preview and imaging tool used to acquire electronic evidence in a forensically sound manner by creating copies of computer data without making changes to the original evidence.

**Note:** In this walkthrough, we will use the FlareVM to analyze the provided file. If you have not set it up yet, I highly recommend following this [malware analysis lab](https://github.com/mmhgwyjs/malware-analysis-lab/blob/main/README.md) guide for assistance with your installation.

## **Preparations**

***1. Open the provided image file using FTK Imager.***

  ![image](https://github.com/user-attachments/assets/ac5fc7db-f268-4dab-b09b-e363f70e1702)

  > File -> Add Evidence Item

***2. Select the Source Evidence Type as `Image File`.***

  ![image](https://github.com/user-attachments/assets/fbd8d7bf-1cb6-405d-9762-030bdb2c52c0)

***3. Select the provided image file: `FirstHack.ad1`.***

  ![image](https://github.com/user-attachments/assets/4a943cfb-6aac-4fd3-9974-27fdcf6c7518)

***Now we are ready to analyze the image file.***

![image](https://github.com/user-attachments/assets/ca277dda-35c8-4604-a0b9-0ca4ebe06de4)

## **Questions and Answers**

***1. What distribution of Linux is being used on this machine?***

- The `/boot` directory contains the files of the kernel and boot image, in addition to LILO and Grub.

  ![image](https://github.com/user-attachments/assets/7ba2f50a-e1cb-43c2-8897-f6985120a4dd)

  **Answer: `Kali`**

***2. What is the MD5 hash of the apache access.log?***

- Var, short for variable, is where programs store runtime information like system logging, user tracking, caches, and other files that system programs create and manage.

  ![image](https://github.com/user-attachments/assets/a3cac3c5-eb4a-4328-80f0-5267b749945c)

  > /var/log/apache2/

- We can export the file itself or extract the hashes only.

  ![image](https://github.com/user-attachments/assets/1215ce4b-8711-4d28-8958-882a268b8c8c)

  **Answer: `d41d8cd98f00b204e9800998ecf8427e`**

***3. It is believed that a credential dumping tool was downloaded. What is the file name of the download?***

- Since it is a Kali machine, it has a predefined Downloads folder.

  ![image](https://github.com/user-attachments/assets/09a9ea51-ee00-4b9b-b2da-b693d3bbac5b)

  **Answer: `mimikatz_trunk.zip`**

***4. There was a super-secret file created. What is the absolute path?***

- The bash shell is the standard terminal for most Linux distributions, macOS, and is available for installation on Windows 10. It remembers your commands and stores them in a history file.

  ![image](https://github.com/user-attachments/assets/998c3af2-cd1b-457a-aa1e-70fa230d47d2)

  > `Touch` command in Linux is used for changing file timestamps however one of the most common usages of touch command includes creating a new empty file.

  **Answer: `/root/Desktop/SuperSecretFile.txt`**

***5. What program used didyouthinkwedmakeiteasy.jpg during execution?***

- Using the same bash history.

  ![image](https://github.com/user-attachments/assets/1426b923-c709-454d-9bf9-baa4a0a41a52)

  > `Binwalk` is a tool for searching a given binary image for embedded files and executable code.

  **Answer: `binwalk`**

***6. What is the third goal from the checklist Karen created?***

- We will need to do a manual search; it is located on the Desktop.
  
  ![image](https://github.com/user-attachments/assets/d0be96df-fe5e-4bde-a16b-64c4e2d191e1)

  **Answer: `profit`**

***7. How many times was apache run?***

- Going back to the Apache access logs, we see no entries, which means Apache did not run.
  
  ![image](https://github.com/user-attachments/assets/e6808be5-dc2e-4fbd-92f7-0e49a0841ec6)

  **Answer: `0`**
  
***8. It is believed this machine was used to attack another. What file proves this?***

- We can find an unusual file in the root directory.

  ![image](https://github.com/user-attachments/assets/556eb6e1-3035-4324-b6c3-3e7e870baecb)

  **Answer: `irZLAohL.jpeg`**

***9. Within the Documents file path, it is believed that Karen was taunting a fellow computer expert through a bash script. Who was Karen taunting?***

- We have a clue from the question that it is in the Documents folder. Additionaly, the file's creation is also recorded in the bash history we checked earlier.

  ![image](https://github.com/user-attachments/assets/a4e61264-cdfe-4002-99d5-122b63819c74)

  **Answer: `Young`** 

***10. A user su'd to root at 11:26 multiple times. Who was it?***

- The activity of using `su` to switch to the `root` user is typically logged in the authentication logs, commonly found in files like `/var/log/auth.log`.
  
  ![image](https://github.com/user-attachments/assets/4a6f9dbb-63ff-4355-9820-ed7a8a0797e0)

  **Answer: `postgres`**
  
***11. Based on the bash history, what is the current working directory?***

- We just need to follow the `cd` commands.
  
  ![image](https://github.com/user-attachments/assets/87960020-7782-4f97-a768-295d2234e119)

  > The `cd` `change directory` command is used to change the current working directory in Linux and other Unix-like operating systems. 

  **Answer: `/root/Documents/myfirsthack/`**

## **References**

- https://linuxhandbook.com/linux-directory-structure/#:~:text=The%20%E2%80%98/boot%E2%80%99%20directory%20contains%20the%20files%20of%20the
- https://linuxize.com/tags/terminal/
- https://www.kali.org/tools/

