# SiberianCMS-Docker
Docker repository for SiberianCMS

#!/bin/sh

apt update -y
apt-get upgrade -y 
apt install build-essential checkinstall
apt install ubuntu-restricted-extras
apt install software-properties-common
apt upgrade -o APT::Get::Show-Upgraded=true
apt-show-versions | grep upgradeable
apt install apt-show-versions
apt update -y
apt-get upgrade -y 
add-apt-repository ppa:nilarimogard/webupd8
apt update -y
apt install launchpad-getkeys
launchpad-getkeys 
add-apt-repository ppa:git-core/ppa
apt update -y
apt install git
git config --global user.name "masum"
git config --global user.email mail@domain.com
apt upgrade -y
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat /root/.ssh/id_rsa.pub

####### CREATE USER #######
groupadd app
useradd -d /home/app -s `which bash` -g app -m app
echo "app ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers 
passwd app
usermod -aG sudo app

####### Enable SSH ########
apt-get install openssh-server
nano /etc/ssh/sshd_config
# Find (ctrl+w) this line and set
PermitRootLogin yes
PubkeyAuthentication yes
PasswordAuthentication yes
# Save & exit ctrl+s and ctrl+x then hit enter
service ssh restart


apt -f install 
apt autoremove 
apt -y autoclean 
apt -y clean 
apt update
reboot

# Docker Install

apt-get update -y
apt-get upgrade -y
apt-get install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg |  apt-key add -

add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
   stable"

apt-get update -y
apt install docker-ce -y   
systemctl start docker
systemctl enable docker
usermod -aG docker ${USER}
systemctl restart docker
systemctl status docker
docker --version

# Docker Compose Install
curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
apt-get update -y
apt-get upgrade -y
docker-compose --version


