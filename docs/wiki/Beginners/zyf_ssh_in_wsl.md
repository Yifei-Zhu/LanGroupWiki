---
layout: page
title: How to use SSH in WSL
author: Yifei Zhu
comments: true
tags:
 - Linux
 - Windows
---
Here's a practical example to demonstrate how to connect to Windows Subsystem for Linux (WSL) using SSH, within a local area network.
For this setup, we use a computer running Windows 11 with the following details:

- Windows 11 Host Machine
    - Local Area Network (LAN) IP Address: 192.168.5.32
- WSL Instance on the Above Windows Machine
    - IP Address: 172.29.76.19

This case study outlines the necessary steps to enable SSH connectivity to the WSL from other devices within the same network.


## Step1: Install SSH Server in WSL
If you haven't installed the SSH server in WSL yet, you can install it with the following commands:

```Bash
sudo apt update
sudo apt install openssh-server
```

##  Step2: Configure SSH Service

Ensure that the SSH service is configured in the   `/etc/ssh/sshd_config` file in WSL. Check the following settings:

- **PermitRootLogin no** (recommended to be set to no for increased security)
- **PasswordAuthentication yes** (if you wish to authenticate using a password)
- **ListenAddress 0.0.0.0** (ensure SSH listens on all interfaces, this setting helps achieve better connectivity in some network configurations)
- **Port 2222** (set up your port according to your needs, default is 22)

Then, restart the SSH service:

```bash
sudo service ssh restart
```

## Step3: Set Up Port Forwarding
Since WSL is typically in a virtual network, its IP address might not be directly visible to the local network. You can set up port forwarding on Windows so that connections to a specific port on Windows are forwarded to the SSH port in WSL (default is 22).

Before setting up port forwarding, you should verify the IP address of your WSL instance by using the `ip a` or `ifconfig` command.
In this example, the IP address of WSL is `172.29.76.19`.

Open PowerShell **with administrator privileges**, and set up port forwarding:

```bash
netsh interface portproxy add v4tov4 listenaddress=0.0.0.0 listenport=3333 connectaddress=172.29.76.19 connectport=2222
```

Here, `listenport` can be any port you choose (in this example, 3333), and connectaddress should be the IP address of WSL.

## Step4: Configure Windows Firewall
Make sure that the Windows Firewall allows access to the port you set for port forwarding (in this case, 3333).
You can set an inbound rule to allow this port through "Control Panel" > "System and Security" > "Windows Defender Firewall" > "Advanced Settings" > "Inbound rule" > "New Rule"

## Step5: Connect to WSL from Other Devices
Use an SSH client to connect to your WSL instance from other devices in the local network, using the following command:

```bash
ssh username_in_WSL@192.168.5.32 -p 3333
```

