# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/ramnit/">Ramnit</a>

**Platform:** CyberDefenders

**Scenario:** Our intrusion detection system has alerted us to suspicious behavior on a workstation, pointing to a likely malware intrusion. A memory dump of this system has been taken for analysis. Your task is to analyze this dump, trace the malware’s actions, and report key findings. This analysis is critical in understanding the breach and preventing further compromise.

**Category:** Endpoint Forensics

**Difficulty:** Easy

**File:** `memory.dmp`

**Tools:** `Volatility 3` `VirusTotal` `Exiftool`

> [Volatility](https://github.com/volatilityfoundation/volatility3) is the world's most widely used framework for extracting digital artifacts from volatile memory (RAM) samples.  

**Note:** In this walkthrough, I will use the SIFT Workstation from SANS to analyze the provided file. If you have not set it up yet, I highly recommend following this [forensics lab](https://github.com/mmhgwyjs/forensics-lab/blob/main/README.md) guide for assistance with your installation.

---

## **Preparations**

***1. Download `Volatility 3` from [this](https://github.com/volatilityfoundation/volatility3?tab=readme-ov-file#downloading-volatility) GitHub repository. Volatility 3 requires Python 3.8.0 or later. More details can be found [here](https://github.com/volatilityfoundation/volatility3?tab=readme-ov-file#requirements).***

  ![image](https://github.com/user-attachments/assets/5a104ad1-deae-4371-9266-6a7ada45c94f)

  > Check python version: `python3 --version`.
  
  ![image](https://github.com/user-attachments/assets/0f68e428-5da4-4cbc-9cae-91784456bd71)

  > Download Volatility 3: `sudo git clone https://github.com/volatilityfoundation/volatility3.git`.

  ![image](https://github.com/user-attachments/assets/9177f63d-87eb-434f-9d93-9b624d6e1c1c)

  > `python3 vol.py -h`
  
***Please note that the SIFT Workstation includes a prebuilt version of Volatility; however, it is version 2, so the syntax differs. You may refer to this [cheatsheet](https://blog.onfvp.com/post/volatility-cheatsheet/) for the differences.***  

***2. Gather OS information.***
  
- For Volatility 2, we can use `imageinfo` and `kdbgscan`. However, it seems that Volatility 2 is not functioning as expected with this memory dump.

  > `imageinfo` and `kdbgscan` are used to obtain the profiles that will later be used for other plugins; however, Volatility 3 saves them automatically, so we will not need to input them each time.
  
  ![image](https://github.com/user-attachments/assets/9164e6e0-5c67-45c9-8863-002281af3faa)

  > `vol.py -f memory.dmp imageinfo > imageinfo.txt`
  
  ![image](https://github.com/user-attachments/assets/8c2a8115-b261-47c3-b0a1-d55525d62092)

  > `vol.py -f memory.dmp kdbgscan > kdbgscan.txt`

- For Volatility 3, use `windows.info` plugin.

  ![image](https://github.com/user-attachments/assets/0945bdc4-8d5e-42f6-b702-85648638172b)

  > `python3 vol.py -f “/path/to/file” windows.info`

***3. Gather Process information.***

   > Since Volatility 2 is not functioning as expected, we will use Volatility 3 throughout this lab.

- Use the following plugins to check the running processes at the time the memory dump was acquired.

  ![image](https://github.com/user-attachments/assets/af64014a-913e-4e02-81c7-05167289f3c8)

  > `sudo python3 /opt/volatility/volatility3/vol.py -f memory.dmp windows.pslist > pslist.txt`
  >
  > `sudo python3 /opt/volatility/volatility3/vol.py -f memory.dmp windows.psscan > psscan.txt`
  >
  > `sudo python3 /opt/volatility/volatility3/vol.py -f memory.dmp windows.pstree > pstree.txt`
  
## **Questions and Answers**

***1. We need to identify the process responsible for this suspicious behavior. What is the name of the suspicious process?***

- We will now look for suspicious processes. SANS has a [cheatsheet](https://www.sans.org/posters/hunt-evil/) that we can use as our baseline. It is also available on the Desktop of your SIFT Workstation.

  ![image](https://github.com/user-attachments/assets/6b8fb63b-af4f-4d5b-ac62-b8e83461bb14)

- By checking the `pstree` results, I found these two processes suspicious, and it also provides the associated user.

  ![image](https://github.com/user-attachments/assets/d217e90a-9c47-4bb3-bddb-12aa522e77d7)

  **Answer: `ChromeSetup.exe`**

***2. To eradicate the malware, what is the exact file path of the process executable?***

- We will use the information we gathered in question number 1.

  **Answer: `C:\Users\alex\Downloads\ChromeSetup.exe`**

***3. Identifying network connections is crucial for understanding the malware's communication strategy. What is the IP address it attempted to connect to?***

- We have two plugins available for gathering network information: `netscan` and `netstat`.

  ![image](https://github.com/user-attachments/assets/c04fbc76-f82e-425f-b033-a11174bd8798)

  > `sudo python3 /opt/volatility/volatility3/vol.py -f memory.dmp windows.netscan > netscan.txt`
  >
  > `sudo python3 /opt/volatility/volatility3/vol.py -f memory.dmp windows.netstat > netstat.txt`

- By examining `ChromeSetup.exe`, we can identify that there is network traffic using a high port, which can be flagged as suspicious. Typically, it should be using port 443.
  
  **Answer: `58.64.204.181`**

***4. To pinpoint the geographical origin of the attack, which city is associated with the IP address the malware communicated with?***

- Using `VirusTotal`.

  ![image](https://github.com/user-attachments/assets/fa66a402-b028-4a3e-b7c2-24266e1e72c7)

  **Answer: `Hong kong`**

***5. Hashes provide a unique identifier for files, aiding in detecting similar threats across machines. What is the SHA1 hash of the malware's executable?***

- To obtain the hash value, we first need to dump the file itself using the `dumpfiles` plugin. We will need the process ID or PID.

  ![image](https://github.com/user-attachments/assets/a4de4a6d-0f29-41aa-9d1d-04c55fc270b4)

  > This is from `pslist`.

- Use the `dumpfiles` plugin.

  ![image](https://github.com/user-attachments/assets/98c52a9c-ca1d-485c-a556-12189b865d5f)

  > sudo python3 /opt/volatility/volatility3/vol.py -f ~/Documents/cd/159-Ramnit/memory.dmp -o . windows.dumpfiles --pid 4628 > dumpfiles.txt
  
- If you encounter an error stating that `Volatility could not import a necessary module: capstone`, install it using the following command: `sudo pip install capstone`.

- Use `sha1sum` command of `ChromeSetup.exe` to get the required hash value.

  ![image](https://github.com/user-attachments/assets/6b4a15c1-5469-4f10-9168-7153f4c34f64)

  **Answer: `280c9d36039f9432433893dee6126d72b9112ad2`**

***6. Understanding the malware's development timeline can offer insights into its deployment. What is the compilation UTC timestamp of the malware?***

- Let us use the tool called `exiftool` to get the metadata of the file.

  ![image](https://github.com/user-attachments/assets/10aed292-20ff-42b6-9b47-14f587c63917)

  **Answer: `2019-12-01 08:36:04`**

***7. Identifying domains involved with this malware helps in blocking future malicious communications and identifying current possible communications with that domain in our network. Can you provide the domain related to the malware?***

- Using the hash value we obtained, we can utilize `VirusTotal` for further checks.

  ![image](https://github.com/user-attachments/assets/2bc68947-6e77-4632-a1be-a6faca26111d)

  **Answer: `dnsnb8.net`**

---

## **Additional Analysis/Artifacts**

- `memory.dmp`
  SHA256: 928134a5e56f9bd1837a9d1c4cd83d4ede1482c2c07825a8805bc4ee99fc4506

  > sha256sum `filename`

