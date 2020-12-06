## Date: 23 Nov 2020

# Contents:

1. Introduction
2. Linux Basic Installation on VMware Workstation
3. Terminal
4. Shell

[VMware Workstation 16 pro - Windows/Linux](https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html)

[Centos 8.2 iso image](http://centos.excellmedia.net/8.2.2004/isos/x86_64/CentOS-8.2.2004-x86_64-dvd1.iso)

# Introduction
- Initially released by Linus Torvalds in September 17 1991
- Linux is a community of open-source operating system - It’s a collaborative effort and anyone can contribute.
- Linux is based on kernel called "Linux Kernel"
- Linux mostly used in for systems like cars, phones, webservers, networking

### Benifits:
- Linux is Free and Opensource software (FOSS)
- Security
- starts fast



k3s Installation - Rancher -HA certified - with external server as database



My Machine:

Loadbalancer:

Master1:
Master2:

Worker1:
Worker2:









____________________________________________________________________
Server side:

Install Script:
curl -sfL https://get.k3s.io | sh -

k3s kubectl get nodes

kubeconfig :
/etc/rancher/k3s/k3s.yaml
K3S_TOKEN: 
/var/lib/rancher/k3s/server/node-token

Worker Side:

export K3S_TOKEN=token from server (cat /var/lib/rancher/k3s/server/node-token)
export K3S_URL=https://ipoftheserver:6443

 join a worker node:
 curl -sfL https://get.k3s.io | sh -

 k3s kubectl get nodes

Uninstalling k3s:

/usr/local/bin/k3s-uninstall.sh (On the server)
/usr/local/bin/k3s-agent-uninstall.sh (On the agent)
______________________________________________________________________
 






















Mysql server on linux:

Install MySQL for Debian-based systems:
    sudo apt install mysql-server 

Install MySQL for Red Hat, CentOS, Fedora:
    sudo apt install mysql-server 

    
To start MySQL now:
    sudo systemctl enable --now mysql.service

To check is MySQL is running: 
    systemctl status mysql.service

To allow MySQL through firewall:
    sudo ufw enable
    sudo ufw allow mysql


Optional:

To run secure script (IMPORTANT):
    sudo mysql_secure_installation



Generate Certificates:
https://documentation.datameer.com/documentation/current/Enabling+SSL+for+MySQL+service

cd /etc/mysql/
# Generate CA file
openssl genrsa 2048 > ca-key.pem
openssl req -new -x509 -nodes -days 3650 -key ca-key.pem > ca-cert.pem



Optional:
# Generate server certifacte
openssl req -newkey rsa:2048 -days 3560 -nodes -keyout server-key.pem > server-req.pem
openssl rsa -in server-key.pem -out server-key.pem
openssl x509 -req -in server-req.pem -days 3650 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 > server-cert.pem
# Generate client certificate
openssl req -newkey rsa:2048 -days 3650 -nodes -keyout client-key.pem > client-req.pem
openssl rsa -in client-key.pem -out client-key.pem
openssl x509 -req -in client-req.pem -days 3650 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 > client-cert.pem
# Change access rights
chmod 400 /etc/mysql/*.pem
chown mysql /etc/mysql/*.pem

https://www.youtube.com/watch?v=UoOcLXfa8EU&ab_channel=NetworkChuck
https://www.youtube.com/watch?v=O3s3YoPesKs&ab_channel=AdrianGoins


