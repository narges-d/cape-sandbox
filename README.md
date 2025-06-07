![CAPE Logo](https://raw.githubusercontent.com/ctxis/CAPE/master/docs/_static/cape-logo.png)


# CAPEv2 Sandbox Installation from Begin
This repository provides an automated script for installing and configuring CAPE Sandbox. I used this sandbox as part of my thesis to extract network traffic. This repository also includes a documentation of errors encountered during the installation process, serving as a guide for others who might face similar issues.

## What is CAPEv2 :
CAPE Sandbox is an Open Source software for automating analysis of suspicious files. To do so it makes use of custom components that monitor the behavior of the malicious processes while running in an isolated environment.

## Prepare Requirement
for installing CAPEv2 i used nested virtualization format, as firstly i used Ubuntu 22.04.4 as my base operating sysytem faced error for it, so decided to use nested format.
for installing you can follow this path:
sudo apt-get update && sudo apt-get upgrade -y
sudo chmod -R a+rwx /opt/
cd /opt
sudo apt install git
git clone https://github.com/kevoreilly/CAPEv2.git
cd CAPEv2/installer
sed -i 's/<WOOT>/BXPC/g' kvm-qemu.sh
chmod a+x kvm-qemu.sh
chmod a+x cape2.sh
-------------------------------------------------
sudo ./kvm-qemu.sh all cape | tee kvm-qemu.log
sudo reboot

cd /opt/CAPEv2/installer
sudo ./kvm-qemu.sh virtmanager cape | tee kvm-qemu-virt-manager.log
after that you have see :
![kvm-qemu](./image/Capture.PNG)

cd /opt/CAPEv2/installer
sudo ./cape2.sh all cape | tee cape.log
sudo reboot

cd /opt/CAPEv2
poetry install
if you see such result from this command :
![poetry](./image/Capture5.PNG)
check this :
![poetry](./image/Capture6.PNG)
then do like this:
![poetry](./image/Capture7.PNG)
poetry env list
---- poetry run pip install -r requirements.txt -------
sudo -u cape poetry run pip install -r extra/optional_dependencies.txt
sudo -u cape poetry run pip install pyattck==7.1.2
-----------------------------
cd /opt/CAPEv2
sudo apt install dbus-x11
sudo poetry install
-----------------------------
nano /opt/CAPEv2/conf/cuckoo.conf
under [resultserver]
ip = *yourip VM IP* example: 192.168.122.1

nano /opt/CAPEv2/conf/kvm.conf
add VM info like name, label, platfarm, ip ...etc








