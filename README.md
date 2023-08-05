# Project Mole

![Deploy a wordpress on (10)](https://github.com/e-miguel/Mole-Project-S3/assets/134418850/60935eda-1ce4-4068-bacd-f133d8a69d5e)

In this assignment, challenge your learning in hosting an HTML website on a single EC2 instance in the default VPC.This repository contains a script for setting up an Apache HTTP server with the Project Mole web application from Amazon S3.

## Prerequisites

Before running the script, ensure that you have the following:

- Complete my project here https://medium.com/system-weakness/how-to-host-an-html-website-on-an-ec2-instance-new-console-36560c9ac208
- AWS and GitHub accounts
- Root access or sudo privileges on the target system
- AWS CLI configured with appropriate credentials and access to the S3 bucket containing the Project Mole files

## Reference Architecture

![Project Mole Reference Architecture](https://github.com/e-miguel/Mole-Project-S3/assets/134418850/9dc446a9-ad4c-4057-84db-6db854513473)
## Objectives

1. Choose your region
2. Create security groups
3. Create IAM role
4. Create an Amazon S3 bucket
5. Upload the web files to the S3 bucket
6. Write your script
7. Add your script and launch your Amazon EC2 instance
8. Launch your HTML website using your instance's public IPv4 address.

## Setup

1. Create security group
2. Make the script executable by running the following command:

   ```shell
   chmod +x setup.sh
   ```

3. Execute the script as root or with sudo privileges:

   ```shell
   sudo ./setup.sh
   ```

   The script performs the following steps:

   - Updates the system packages using `yum update -y`.
   - Installs the Apache HTTP server using `yum install -y httpd`.
   - Changes the working directory to `/var/www/html`.
   - Syncs the Project Mole files from the S3 bucket to the local system using `aws s3 sync`.
   - Extracts the contents of the `mole.zip` archive using `unzip`.
   - Copies the extracted files to the Apache web server's document root using `cp`.
   - Cleans up the downloaded files and extracted directory using `rm`.
   - Enables the Apache service to start on system boot using `systemctl enable httpd`.
   - Starts the Apache service using `systemctl start httpd`.

4. After the script completes successfully, you should be able to access the Project Mole web application by navigating to `http://<your-server-ip>` in a web browser.

## Summary of Scripts

- #!/bin/bash
- sudo su
- yum update -y
- yum install -y httpd
- cd /var/www/html
- aws s3 sync s3://project-mole /var/www/html
- unzip mole.zip
- cp -r /var/www/html/mole-main/* /var/www/html
- rm -rf mole.zip mole-main
- systemctl enable httpd 
- systemctl start httpd

## Contributing

Contributions to this project are welcome. If you encounter any issues or have suggestions for improvement, please open an issue or submit a pull request.
