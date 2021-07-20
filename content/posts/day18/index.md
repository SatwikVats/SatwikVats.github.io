---
title: "30 June 2021"
date: 2020-06-08T08:06:25+06:00
description: Introduction to Sample Post
menu:
  sidebar:
    name: Introduction
    identifier: introduction
    weight: 10
---

- Working with VM.
 
  - Created a tag for VM.
    ```
    aws ec2 create-tags --resource i-08431b825258399a3 --tags Key=Name,Value=SkvInstance
    
    ```
  - Stopped the VM once I was done with my experimentation.
    ```
    aws ec2 stop-instances --instance-ids i-08431b825258399a3
    
    ```
    {{<asciinema VMQMuurIEmpWMjYilA6kZMgTZ>}}
    
  - Terminated an instance created previously.
    ```
    aws ec2 terminate-instances --instance-ids i-09165cb7fe11c4b0b
    
    ```
    {{<asciinema 9kjpixqG7CCenXz0HTBwQSlft>}}
    
- Experimentation with S3 Storage Buckets.

  - Made a Bucket manually on Console. Later deleted it to repeat the process on AWS.
  
  - Made a bucket on CLI.
    ```
    aws s3 mb s3://skvfirstbucket
    
    ```
  - The following command lists down all the buckets.
    ```
    aws s3 ls
    
    ```
  - Copied a file to bucket.
    ```
    aws s3 cp file.txt s3://skvfirstbucket/
    
    ```
    Here, `file.txt` is the filename and `skvfirstbucket` is the bucket name.
    
  - Synced one of my local Directories to AWS Bucket. Here, I created a backup for my Hugo Site content.
    ```
    aws s3 sync /home/satwik/HugoFirstSite.io/content s3://skvfirstbucket/HugoSiteContent
    
    ```
    Here, I have specified the path of directory as source along with bucket as target.
    
    {{<asciinema YYBpkYtuZl4M9KxwPnbpYY7Du>}}
    
  - If any changes are made to the local directory, those changes are updated in the bucket as well, on syncing again.
  
  - Removed a file from local directory and tried syncing, though it didn't work as expected.
  
  - To sync delete operations, `--delete` must be used in the command to enforce removal of file.
    ```
    aws s3 sync /home/satwik/HugoFirstSite.io/content s3://skvfirstbucket/HugoSiteContent --delete
    
    ```
    {{<asciinema t1Wep6MQMI1rqkFjTECm5xOKn>}}
    
  - Removed a sample file from bucket.
    ```
    aws s3 rm s3://skvfirstbucket/file.txt
    
    ```
    {{<asciinema 0CvOHDL3VH6v6bFvPmAPvrXGA>}}
    
  - Attempted removing an entire bucket after I was done with experimentation, which didn't work out as expected. AWS doesn't permit removal of non-empty buckets directly.
  
  - `--force` must be used in the command to enforce removal.
    ```
    aws s3 rb s3://skvfirstbucket --force 
    
    ```
    {{<asciinema mNnKXPVitpnwIwnG0viwK5hFS>}}
    
- References:

  - [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/index.html)
    
    
    


    





