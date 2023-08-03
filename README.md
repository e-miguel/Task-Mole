# Project Mole

![Deploy a wordpress on (10)](https://github.com/e-miguel/Mole-Project-S3/assets/134418850/60935eda-1ce4-4068-bacd-f133d8a69d5e)

This repository contains a script for setting up an Apache HTTP server with the Project Mole web application from Amazon S3.

## Prerequisites

Before running the script, ensure that you have the following:

- An Amazon Linux or CentOS system
- Root access or sudo privileges on the target system
- Internet connectivity on the target system
- AWS CLI configured with appropriate credentials and access to the S3 bucket containing the Project Mole files

## Usage

1. Clone this repository or download the script to your target system.
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
