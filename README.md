![CAPE Logo](https://raw.githubusercontent.com/ctxis/CAPE/master/docs/_static/cape-logo.png)

# CAPEv2 Sandbox Installation from Begin

This repository provides an automated script for installing and configuring CAPE Sandbox.  
I used this sandbox as part of my thesis to extract network traffic.  
This repository also includes a documentation of errors encountered during the installation process, serving as a guide for others who might face similar issues.

## What is CAPEv2

CAPE Sandbox is an Open Source software for automating analysis of suspicious files.  
To do so it makes use of custom components that monitor the behavior of the malicious processes while running in an isolated environment.

## Prepare Requirement

For installing CAPEv2 I used nested virtualization format.  
At first, I used Ubuntu 22.04.4 as my base operating system and faced errors, so I decided to use nested virtualization.

For installing you can follow this path:

```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo chmod -R a+rwx /opt/
cd /opt
sudo apt install git
git clone https://github.com/kevoreilly/CAPEv2.git
cd CAPEv2/installer
sed -i 's/<WOOT>/BXPC/g' kvm-qemu.sh
chmod a+x kvm-qemu.sh
chmod a+x cape2.sh
