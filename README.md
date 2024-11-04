# OpenVPN-CLI

This project provides a comprehensive guide on how to set up a VPN server on a VPS using OpenVPN. Follow the instructions below to deploy and configure your VPN server.

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

``` bash
sudo apt install neovim
```

## Create a non-root user
``` bash
sudo useradd -G sudo -m  <username> -s /bin/bash
```
### Change the password
``` bash
sudo passwd <username>
```

## Installing the server
``` bash
sudo apt install wget
```

``` bash
wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
``` bash
sudo bash openvpn-install.sh
```
### Follow the steps, it's on default settings if you press enter

## Changing the directory for the ovpn file
``` bash
sudo mv /root/<VPN file name example Aftershock.ovpn> .
```

## Disable Logs
``` bash
sudo nvim /etc/openvpn/server/server.conf
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

## How to download the files to your windows machine

### Open CMD
``` ruby
pscp username@public_ip_address:/path/to/file C:\Downloads
```

#### This is the example of the command
``` ruby
pscp CLF@52.123.45.67:thinkpad.ovpn C:\chanl\Downloads
```

## If you are lost follow this
[YT video](https://www.youtube.com/watch?v=gxpX_mubz2A&ab_channel=Wolfgang%27sChannel)

[Repository](https://github.com/Nyr/openvpn-install)
