# OpenVPN-CLI

This project provides a comprehensive guide on how to set up a VPN server on a VPS using OpenVPN. Follow the instructions below to deploy and configure your VPN server.

## Introduction to OpenVPN

OpenVPN is a robust and highly flexible open-source VPN (Virtual Private Network) software that enables secure point-to-point or site-to-site connections. It provides a secure and encrypted connection over the internet, ensuring privacy and data integrity. OpenVPN is widely used for remote access, secure communications, and bypassing geo-restrictions.

## Benefits of OpenVPN

- **Security**: OpenVPN uses strong encryption protocols to protect your data from unauthorized access.
- **Flexibility**: It can be configured to work on various platforms and devices.
- **Reliability**: OpenVPN is known for its stability and performance.
- **Open Source**: Being open-source, it is continuously improved and audited by the community.

## Prerequisites

Before you begin, ensure you have the following:

- A VPS (Virtual Private Server) with a fresh installation of a supported Linux distribution (e.g., Ubuntu, Debian).
- An Azure account to deploy the VM.
- Putty installed on your local machine for SSH access.
- Basic knowledge of Linux command-line operations.

## Table of Contents
- [Deploy the VM on Azure](#deploy-the-vm-on-azure)
- [How to connect using Putty](#how-to-connect-using-putty)
  - [Step 1: Connect to the VM](#step-1-connect-to-the-vm)
  - [Step 2: Click on SSH](#step-2-click-on-ssh)
  - [Step 3: Open Putty and paste the SSH command](#step-3-open-putty-and-paste-the-ssh-command)
  - [Step 4: Click on Yes](#step-4-click-on-yes)
  - [Step 5: Login](#step-5-login)
  - [Step 6: You are in the VM now](#step-6-you-are-in-the-vm-now)
- [Basic Start Command (Must do!!!)](#basic-start-command-must-do)
- [Create a non-root user](#create-a-non-root-user)
  - [Change the password](#change-the-password)
- [Installing the server](#installing-the-server)
  - [Follow the steps, it's on default settings if you press enter](#follow-the-steps-its-on-default-settings-if-you-press-enter)
- [Changing the directory for the ovpn file](#changing-the-directory-for-the-ovpn-file)
- [Disable Logs](#disable-logs)
  - [Change Verb 3 to Verb 0](#change-verb-3-to-verb-0)
- [Restart the VPN Server](#restart-the-vpn-server)
- [How to download the files to your windows machine](#how-to-download-the-files-to-your-windows-machine)
  - [Open CMD](#open-cmd)
  - [This is the example of the command](#this-is-the-example-of-the-command)
- [If you are lost follow this](#if-you-are-lost-follow-this)
- [Troubleshooting](#troubleshooting)

## Deploy the VM on Azure

![Azure VM Deployment](<Image/Screenshot 2023-07-02 034823.png>)

- Make sure this is in username rather than SSH public key

## How to connect using Putty

### Step 1: Connect to the VM
![Connect to VM](<Image/Screenshot 2023-07-02 035317.png>)
- After creating the VM, click on connect 

### Step 2: Click on SSH
![Click on SSH](<Image/Screenshot 2023-07-02 035339.png>)
- Copy the SSH command only behind

### Step 3: Open Putty and paste the SSH command
![Paste SSH command](<Image/Screenshot 2023-07-02 035403.png>)

### Step 4: Click on Yes

### Step 5: Login
![Login](<Image/Screenshot 2023-07-02 035423.png>)

### Step 6: You are in the VM now
![In the VM](<Image/Screenshot 2023-07-02 035435.png>)

## Basic Start Command (Must do!!!)
``` bash
sudo apt-get update && apt-get upgrade
```
Example output:
``` bash
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]
...
```

``` bash
sudo apt install neovim
```
Example output:
``` bash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libmsgpackc2 libtermkey1 libvterm0 neovim-runtime
...
```

## Create a non-root user
``` bash
sudo useradd -G sudo -m  <username> -s /bin/bash
```
Example output:
``` bash
```

### Change the password
``` bash
sudo passwd <username>
```
Example output:
``` bash
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
```

## Installing the server
``` bash
sudo apt install wget
```
Example output:
``` bash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libpsl5 publicsuffix wget
...
```

``` bash
wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
Example output:
``` bash
--2023-07-02 03:48:23--  https://git.io/vpn
Resolving git.io (git.io)... 140.82.113.21
Connecting to git.io (git.io)|140.82.113.21|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh [following]
--2023-07-02 03:48:23--  https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.108.133, 185.199.109.133, 185.199.110.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15345 (15K) [text/plain]
Saving to: ‘openvpn-install.sh’

openvpn-install.sh  100%[===================>]  15.00K  --.-KB/s    in 0.001s  

2023-07-02 03:48:23 (11.4 MB/s) - ‘openvpn-install.sh’ saved [15345/15345]

```

``` bash
sudo bash openvpn-install.sh
```
Example output:
``` bash
Welcome to the OpenVPN installer!
The git repository is available at: https://github.com/angristan/openvpn-install
I need to ask you a few questions before starting the setup.
You can use the default options and just press enter if you are unsure.
...
```

### Follow the steps, it's on default settings if you press enter

## Changing the directory for the ovpn file
``` bash
sudo mv /root/<VPN file name example Aftershock.ovpn> .
```
Example output:
``` bash
```

## Disable Logs
``` bash
sudo nvim /etc/openvpn/server/server.conf
```
Example output:
``` bash
```

### Change Verb 3 to Verb 0

After entering insert mode by pressing the "i" key in Nvim, you can type or modify the text as needed. To save the changes and exit the editor, you can follow these steps:

1. Press the "Esc" key on your keyboard to exit insert mode and return to normal mode in Nvim.
2. Once you're in normal mode, you can save the changes by typing `:w` (colon followed by the letter "w"). This command tells Nvim to write (save) the file.
3. After entering `:w`, press the "Enter" key to execute the command. You should see a message indicating that the file has been saved.
4. To exit Nvim, type `:q` (colon followed by the letter "q") and press "Enter". This command tells Nvim to quit the editor.
   - If you have unsaved changes and want to quit without saving, you can use `:q!` instead, which discards the changes and forces the exit.

By following these steps, you should be able to save your changes and exit the Nvim editor.

## Restart the VPN Server
``` bash
sudo systemctl restart openvpn-server@server.service
```
Example output:
``` bash
```

## How to download the files to your windows machine

### Open CMD
``` ruby
pscp username@public_ip_address:/path/to/file C:\Downloads
```
Example output:
``` ruby
```

#### This is the example of the command
``` ruby
pscp CLF@52.123.45.67:thinkpad.ovpn C:\chanl\Downloads
```
Example output:
``` ruby
```

## If you are lost follow this
[YT video](https://www.youtube.com/watch?v=gxpX_mubz2A&ab_channel=Wolfgang%27sChannel)

[Repository](https://github.com/Nyr/openvpn-install)

## Troubleshooting

### Common Issues and Solutions

#### Issue: Unable to connect to the VM using SSH
- **Solution**: Ensure that the VM is running and the SSH port (usually port 22) is open in the VM's network security group settings.

#### Issue: Permission denied when running commands
- **Solution**: Make sure you are using a user with sudo privileges. If you are using a non-root user, prefix the commands with `sudo`.

#### Issue: OpenVPN service not starting
- **Solution**: Check the OpenVPN server logs for any error messages. You can view the logs using the following command:
  ``` bash
  sudo journalctl -u openvpn-server@server.service
  ```

#### Issue: Unable to download files using `pscp`
- **Solution**: Ensure that the `pscp` command is installed on your Windows machine. You can download it from the official PuTTY website. Also, verify that the file path and IP address are correct.

For further assistance, refer to the official OpenVPN documentation or seek help from the OpenVPN community.

