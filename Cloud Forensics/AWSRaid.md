# <a href="https://cyberdefenders.org/blueteam-ctf-challenges/awsraid/">AWSRaid</a>

**Platform:** CyberDefenders

**Scenario:** Your organization uses AWS for hosting critical data and applications. An incident has been reported involving unauthorized data access and potential exfiltration. The organization's security team has detected unusual activities and needs to investigate the incident to understand the scope, identify the attacker, and prevent further data breaches.

**Category:** Cloud Forensics

**Difficulty:** Easy

**Files:** `N/A`

**Tools:** `Splunk Enterprise`

> [Splunk Enterprise](https://www.splunk.com/en_us/products/splunk-enterprise.html) is a platform for analyzing machine-generated big data. It indexes data from various sources, providing real-time insights, visualizations, and alerts, primarily for IT operations and security monitoring.

**Note:** In this walkthrough, CyberDefenders offers a lab environment for us to utilize. This feature is included with the PRO subscription.

## **Preparations**

![image](https://github.com/user-attachments/assets/cd388953-a6e6-4cb2-9861-9685cd750d7d)

![image](https://github.com/user-attachments/assets/82c002d5-f7af-4098-893e-0bff0bb74412)



![image](https://github.com/user-attachments/assets/f8d717dd-d918-442c-89d2-82fabcef95b5)
index=*
| stats by index

## **Questions and Answers**

***1. Knowing which user account was compromised is essential for understanding the attacker's initial entry point into the environment. What is the username of the compromised user?***

![image](https://github.com/user-attachments/assets/8caa398a-4ddb-4956-ad55-18da9cfce711)
index="aws_cloudtrail" eventType=AwsConsoleSignIn
| stats count by userIdentity.userName responseElements.ConsoleLogin eventTime
| sort -eventTime

helpdesk.luke

***2. We must investigate the events following the initial compromise to understand the attacker's motives. What's the UTC timestamp of the attacker's first access to an S3 object?***

![image](https://github.com/user-attachments/assets/cbec1e74-bd6d-4e92-a6d3-75ed7b398d4e)

index="aws_cloudtrail" userIdentity.userName=helpdesk.luke
| stats min(eventTime) as FirsteventTime count by eventName 
| sort +FirsteventTime

02-11-2023 09:55:53

***3. Among the S3 buckets accessed by the attacker, one contains a DWG file. What is the name of this bucket?***

![image](https://github.com/user-attachments/assets/43e4abc1-02d1-484c-b015-c0795cb384eb)

index="aws_cloudtrail" userIdentity.userName=helpdesk.luke eventName=GetObject dwg

product-designs-repository31183937

***4. We've identified changes to a bucket's configuration that allowed public access, a significant security concern. What is the name of this particular S3 bucket?***
index="aws_cloudtrail" userIdentity.userName=helpdesk.luke eventName="*bucket*"
| stats count by eventName
![image](https://github.com/user-attachments/assets/1eaeb602-0164-4703-a593-6e0f6b070cf7)

![image](https://github.com/user-attachments/assets/464eecdb-28a6-40e5-9630-724d8ae71d86)
index="aws_cloudtrail" userIdentity.userName=helpdesk.luke eventName="PutBucketPublicAccessBlock"

backup-and-restore98825501

***5. Creating a new user account is a common tactic attackers use to establish persistence in a compromised environment. What is the username of the account created by the attacker?***

![image](https://github.com/user-attachments/assets/77986c18-a89c-4f12-a5f0-abe83d207121)

![image](https://github.com/user-attachments/assets/b8eb4883-58ff-486b-b83d-240e84cda5dc)

index="aws_cloudtrail" userIdentity.userName=helpdesk.luke eventName="*create*"
| stats count by eventName

marketing.mark

***6. What is the name of the group to which the account was added?***

index="aws_cloudtrail" userIdentity.userName=helpdesk.luke eventName="*group*" marketing.mark

![image](https://github.com/user-attachments/assets/f5943f9a-1f00-4385-af9a-a21065a67635)

Admins

## **References**

https://docs.aws.amazon.com/AmazonS3/latest/API/API_Operations_Amazon_Simple_Storage_Service.html
