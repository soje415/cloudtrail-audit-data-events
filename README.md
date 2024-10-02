# Logging and Analyzing S3 Object Delete API Events using AWS CloudTrail Data Events


![mast head](https://github.com/user-attachments/assets/d35db332-f363-43c4-a193-51b8cb18826d)



Project Overview:


This project demonstrates how to use AWS CloudTrail to log and audit S3 object deletion events in real-time. By setting up CloudTrail data events, an S3 bucket, and IAM roles, you will learn to track and analyze API calls made to delete objects from a specific S3 bucket.

# Key Points:

.  CloudTrail captures API activity, including high-volume data operations (like S3 object deletions).
.  The importance of auditing API calls to prevent unauthorized access or modifications.

# Overview of the steps: 

Creating a CloudTrail trail, setting up the S3 bucket, configuring an IAM role, performing a delete action, and auditing the delete event.


Navigate to cloudtrail and create a trail

![trail create](https://github.com/user-attachments/assets/dfe2980e-44af-4e51-9bc8-acf82a84f545)

In the cloud trail GUI select Data Event 

![data event](https://github.com/user-attachments/assets/117bc509-9250-4486-a504-8ef4a0540e25)



Trail created 

![trail created](https://github.com/user-attachments/assets/6818d8b1-3dc7-4b80-8884-025d427700d6)

Configure the advance event selector to include conditions for DeleteObject and DeleteObjects with your s3 bucket ARN to trigger the event

![advance event selector](https://github.com/user-attachments/assets/10bb8b07-ec20-4199-8087-bba651670bc2)


Confirm the creation of the trail bucket

![trail bucket created](https://github.com/user-attachments/assets/3cfd329e-f285-4d2a-9ae7-94bcc3c03b32)


Create a IAM role with S3 nad Cloudtrail full access just for demo purposes

![iam role perm](https://github.com/user-attachments/assets/fa287b9d-7e73-4597-8c6f-3b612d93d1ba)


Craete another S3 bucket with your root acconut and upload a file and delete the delete to trigger the event log API to send log to the trail created for that purpose

![delete file](https://github.com/user-attachments/assets/2d7602c7-0c72-44db-95ab-33b29140ae58)


After deletion of the file, the event have been triggered and below is the cloudtrail logfile that was produce due to that delete event

![logfile gen](https://github.com/user-attachments/assets/0f81339e-6c2a-43bc-9d98-fadf390f55ed)


Download file for further analysis, here are the log files output in JSON. 

![logfile output](https://github.com/user-attachments/assets/20d37acd-14ac-43cf-a99f-13726258cafb)

# Take nor of some key further for auditing purpose,
1. The ARN of the account that deleted the file
2. The IP were the event happened
3. And some other detaild that would help in the audit and analysis

![log output 2](https://github.com/user-attachments/assets/c8ba58c6-a0ea-4c66-8067-1416816032c3)

