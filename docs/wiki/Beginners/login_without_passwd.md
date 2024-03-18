---
layout: page
title: How to connect without password using SSH
author: Yifei Zhu
comments: true
tags:
 - Author Guidelines
 - Linux
---

## Make sure that SSH server is running
Check service status using: `sudo service sshd status or` or `sudo systemctl status sshd`

If the SSH service is closed, run the following command to start the ssh service: `sudo service sshd start` or `sudo systemtcl start sshd`.

## Connect to remote machine

Run the command `ssh remote_username@remote_server_ip_address` if it is the first time you logged into this host, you will get something like this :

```Bash
The authenticity of host XXXXXX can’t be established.

RSA key fingerprint is 7c:e7:51:3b:86:70:07:ab:65:a9:bf:2d:c0:7b:1b:a7.

Are you sure you want to continue connecting (yes/no)?
```
Type `yes` and then it will ask you to enter the password.
You are now connected to the remote machine with the password.

## Generate private and public keys

Let’s back to our localhost machine, a key pair must be created with the command
```Bash
ssh-keygen -t rsa
```
Press Enter three times until the command finishes.
A public key file `~/.ssh/id_rsa.pub` and a private key file `~/.ssh/id_rsa` will be generated.

If your more interested in private and public keys using ssh please referee to this [article](https://www.ssh.com/academy/ssh-keys#:~:text=An%20SSH%20key%20is%20an,system%20administrators%20and%20power%20users.).

## Copy the public key file to the remote machine
Now that you have generated an SSH key pair, in order to be able to login to your machine without a password you need to copy the public key to the server you want to manage.
```Bash
ssh-copy-id remote_username@remote_server_ip_address
```
You should be able to get onto the remote server without being requested for a password once you’ve followed the preceding instructions.

To test it just try to login to your server via SSH:
```Bash
ssh remote_username@remote_server_ip_address
```