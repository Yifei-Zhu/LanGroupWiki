---
layout: page
title: How To Use SSHFS to Mount Remote File Systems Over SSH
author: Yifei Zhu
comments: true
tags:
 - Author Guidelines
 - Ubuntu
---
## Introdcution
SSHFS itself is a file system in user space (FUSE) that uses the SSH File Transfer Protocol (SFTP) to mount a remote file system.
SSHFS command is a client tool for using SSHFS to mount a remote file system from another server locally on your machine.

## Configuration on Ubuntu
### 1 Installation
```Bash
sudo apt update
sudo apt-get install sshfs
```
### 2 Creat a local directory for remote mounting
For example:
```Bash
mkdir /mnt/local/path
```
### 3 Mount Remote File Systems
```Bash
sshfs username@1:/your/remote/path /mnt/local/path
```
For example:
```Bash
sshfs zhuyf@192.168.5.200:/data/home/zhuyf /mnt/local/path
```

### 4 Check mounting
```Bash
df -hT 
```

### 5 Auto mount configuration
You can mount the remote directory without manually typing the command always by adding a `fstab` method.
You should open the `/etc/fstab` file to edit:
```bash
sudo vim /etc/fstab
```
Then you should add the following command at the end of the file.
```bash
username@1:/your/remote/path /mnt/local/path fuse.sshfs noauto,x-systemd.automount,_netdev,IdentityFile=/home/name/.ssh/id_rsa,allow_other,reconnec
```
Finally, Use the following command to make the configuration take effect.

```Bash
sudo mount -a
```
