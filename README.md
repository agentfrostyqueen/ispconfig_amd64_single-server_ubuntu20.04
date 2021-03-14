### Version 3.0.6 #
<b>v.3.0.6</b

Run the following command as root user:

### Gr88er Specific Configs ###  
sudo apt install ntp ntpdate nfs-common ssh openssh-server cockpit cockpit-packagekit -y  
sudo dpkg-reconfigure dash  
sudo service apparmor stop  
sudo update-rc.d -f apparmor remove  
sudo apt-get remove apparmor apparmor-utils -y  
sudo apt update && sudo apt upgrade -y  

### comment out RANDFILE in /etc/ssl/openssl.cnf ##
sudo unlink /etc/localtime  
sudo ln -s /usr/share/zoneinfo/Asia/Hong_Kong /etc/localtime  
sudo timedatectl  
sudo locale-gen  
sudo dpkg-reconfigure locales  

### set hostname using ##
sudo hostnamectl set-hostname sample.gr88er.com  

### modify /etc/apt/source.list ##
deb http://ports.ubuntu.com/ubuntu-ports/ focal multiverse  
deb-src http://ports.ubuntu.com/ubuntu-ports/ focal multiverse  
deb http://ports.ubuntu.com/ubuntu-ports/ focal-updates multiverse  
deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-updates multiverse  
deb http://ports.ubuntu.com/ubuntu-ports/ focal-backports multiverse  
deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-backports multiverse


### not applicable to odroid ##
echo "deb https://deb.goaccess.io/ $(lsb_release -cs) main" | sudo tee -a /etc/apt/sources.list.d/goaccess.list  
wget -O - https://deb.goaccess.io/gnugpg.key | sudo apt-key --keyring /etc/apt/trusted.gpg.d/goaccess.gpg add -  
sudo apt-get update  
sudo apt-get install goaccess  
cd /tmp; git clone https://github.com/agentfrostyqueen/ispconfig_amd64_single-server_ubuntu20.04; cd ispconfig_amd64_single-server_ubuntu20.04/; bash install.sh  

### Run this after the script ##
apt-get -y install mailman  
Languages to support: <-- en (English)  
Missing site list <-- Ok  

newlist mailman
Enter the email of the person running the list: <-- admin email address, e.g. listadmin@example.com  
Initial mailman password: <-- admin password for the mailman list  

newaliases  
service postfix restart  
ln -s /etc/mailman/apache.conf /etc/apache2/conf-available/mailman.conf  
a2enconf mailman  
service apache2 restart  
service mailman start  

