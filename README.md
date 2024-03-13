# Hosting an HTML Website

![Deploy a wordpress on (10)](https://github.com/e-miguel/Mole-Project-S3/assets/134418850/60935eda-1ce4-4068-bacd-f133d8a69d5e)

In this task, challenge your learning in hosting an HTML website on a single EC2 instance in the default VPC.This repository contains a script for setting up an Apache HTTP server with the Project Mole web application from Amazon S3.

## Prerequisites

Before running the script, ensure that you have the following:

- Complete my project here https://medium.com/system-weakness/how-to-host-an-html-website-on-an-ec2-instance-new-console-36560c9ac208
- AWS and GitHub accounts
- Root access or sudo privileges on the target system
- AWS CLI configured with appropriate credentials and access to the S3 bucket containing the Project Mole files

## Reference Architecture

![Task 2 - Project X-Men - AOS (1)](https://github.com/e-miguel/Task-Mole/assets/134418850/23cb78c5-dc4a-46f7-8631-a7d0c42ce108)

## Objectives

1. Choose your region
2. Create security groups
3. Create IAM role
4. Create an Amazon S3 bucket
5. Upload the web files to the S3 bucket
6. Write your script
7. Add your script and launch your Amazon EC2 instance
8. Launch your HTML website using your instance's public IPv4 address.
9. Conclusion and clean up

## Task 1

1. Create security groups with ports 80 and 22 opened.
2. Create IAM role with S3FullAccess
3. Create an amazon S3 bucket and attach the role you just created
4. Download the mole.zip file and upload it on your S3 bucket
5. Create a script that downloads the web files from the S3 bucket and hosts the HTML website on an EC2 instance. Refer to the sample script provided below.

   ```shell
   #!/bin/bash
   sudo su
   yum update -y
   yum install -y httpd
   cd /var/www/html
   aws s3 sync s3://project-mole /var/www/html
   unzip mole.zip
   cp -r /var/www/html/mole-main/* /var/www/html
   rm -rf mole.zip mole-main
   systemctl enable httpd
   systemctl start httpd
   ```

6. Launch your EC2 instance and add the script to the user data.
   - Use Amazon Linux 2 AMI
   - Use the default VPC
   - Use the security groups you created

7. After the script completes successfully, launch the HTML website using the public IPv4 address of your EC2 instance.
8. You should get the website below. It must show the public IPv4 address of your instance.

![Finished Project Mole](https://github.com/e-miguel/Mole-Project-S3/assets/134418850/fcc78910-b190-48f0-a0c2-f00ece3abd38)

## Task 2

1. Download the web files
2. Upload the web files to a public GitHub repository.
3. Create a script that downloads the web files from the GitHub repository and hosts the HTML website on an EC2 instance. Refer to the sample script provided above.
4. Add the script to the EC2 user data at launch to host the HTML website.

## Conclusion and Clean Up

This project is a valuable addition to your portfolio. It can help you prepare for your AWS Certified Cloud Practitioner CLF-C01 and AWS Certified Solutions Architect Associate SAA-C03 exams. Let me know if you have any questions. To clean up your resource/s to avoid further cost, terminate your EC2 instance.

Ready to further your professional experience? Sign up here for more constructive real-world projects https://www.aosnote.com/a/2147524876/WLBooyWz

Stay tuned for our next challenge project!
