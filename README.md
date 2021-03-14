[![Build Status](https://travis-ci.org/servisys/ispconfig_setup.svg?branch=master)](https://travis-ci.org/servisys/ispconfig_setup)

# README #

[![PayPayl donate button](https://www.paypalobjects.com/it_IT/IT/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=TB4Q3UJDC5JDJ "Help US support this project using Paypal")

# Newsletter #
Subscribe to our newsletter to receive information about new version of the script
The link is here: http://eepurl.com/cAzq95
We'll use only to inform you on new version of the script :)


# Version #
<b>v.3.0.6</b>

Debian 10 fix for Debian 10

<b>v.3.0.5</b>

Debian 10 changes file path, for root use :

	su -
	
Added support for Debian 10 Buster and php7.3
	service changed to systemctl for all service functions (start,stop,restart etc)
	few other minor changes to accommodate Debian 10

<b>v.3.0.4</b>

This is a system to automate the installation of ISPConfig 3 control Panel ( http://www.ispconfig.org/page/home.html ).

Tested on:
- Debian 10 Busty ([Servisys VPS](https://www.servisys.it/), VmWare Esxi, Amazon AWS, Virtualbox, OVH VPS, Hetzner, Digital Ocean)
- Debian 9 Stretch ([Servisys VPS](https://www.servisys.it/), VmWare Esxi, Amazon AWS, Virtualbox, OVH VPS, Hetzner, Digital Ocean)
- Debian 8 Jessie ([Servisys VPS](https://www.servisys.it/), VmWare Esxi, Amazon AWS, Virtualbox, OVH VPS, Hetzner, Digital Ocean)
- Debian 7 Wheezy ([Servisys VPS](https://www.servisys.it/), VmWare Esxi, Amazon AWS, Virtualbox, OVH VPS, Hetzner, Digital Ocean)
- Ubuntu 14.04 Trusty ([Servisys VPS](https://www.servisys.it/), VmWare Esxi, Amazon AWS, Virtualbox, OVH VPS, Hetzner, Digital Ocean)
- Ubuntu 15.10 Willy ([Servisys VPS](https://www.servisys.it/), VmWare Esxi, Amazon AWS, Virtualbox, OVH VPS, Hetzner, Digital Ocean)
- Ubuntu 16.04 Xenial Xerus ( [Servisys VPS](https://www.servisys.it/), VmWare Esxi, Amazon AWS, Virtualbox, OVH VPS, Hetzner, Digital Ocean)
- Ubuntu 18.04 Bionic Beaver ( [Servisys VPS](https://www.servisys.it/), VmWare Esxi, Amazon AWS, Virtualbox, OVH VPS, Hetzner, Digital Ocean)
- CentOS 7 ([Servisys VPS](https://www.servisys.it/), Vitualbox)
- Raspbian
- ISPConfig 3.*

### What is this repository for? ###

This repository contains some scripts for the automation of installation of ISPConfig 3 control panel.

Before starting, be sure to follow one of these guides to install a supported Linux distribution:

- Debian 7: https://www.howtoforge.com/tutorial/debian-7-wheezy-minimal-server/
- Debian 8: https://www.howtoforge.com/tutorial/debian-8-jessie-minimal-server/
- Debian 9: https://www.howtoforge.com/tutorial/debian-minimal-server/
- Debain 10: https://www.howtoforge.com/tutorial/debian-10-buster-minimal-server/
- Ubuntu 14.10: https://www.howtoforge.com/tutorial/ubuntu-14.10-utopic-unicorn-server
- Ubuntu 15.10: https://www.howtoforge.com/tutorial/ubuntu-15.10-wily-werewolf-minimal-server/
- Ubuntu 16.04: https://www.howtoforge.com/tutorial/ubuntu-16.04-xenial-xerus-minimal-server/
- Ubuntu 16.10: https://www.howtoforge.com/tutorial/ubuntu-16.10-yakkety-yak-minimal-server/
- Ubuntu 17.10: https://www.howtoforge.com/tutorial/ubuntu-minimal-server-install/
- Ubuntu 18.04: https://www.howtoforge.com/tutorial/ubuntu-lts-minimal-server/
- CentOS 7: https://www.howtoforge.com/tutorial/centos-7-minimal-server/

#### Supported Software and Linux distributions
<table cellpadding="0" cellspacing="0">
	<tr>
		<td rowspan="2"><strong>Component</strong></td>
		<td rowspan="2"><strong>Software</strong></td>
		<td colspan="4"><strong>Debian/Raspbian</strong></td>
		<td colspan="6"><strong>Ubuntu</strong></td>
		<td><strong>CentOS</strong></td>
		<td colspan="2"><strong>openSUSE Leap</strong></td>
		<td><strong>Fedora</strong></td>
	</tr>
	<tr>
		<td>7</td>
		<td>8</td>
        <td>9</td>
        <td>10</td>
		<td>14.04</td>
		<td>15.10</td>
		<td>16.04</td>
		<td>16.10</td>
		<td>17.10</td>
		<td>18.04</td>
		<td>7</td>
		<td>42.1-3</td>
		<td>15.0</td>
		<td>22-28</td>
	</tr>
	<tr>
		<td rowspan="2">Web: HTTP</td>
		<td>Apache</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>nginx</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Mail: SMTP</td>
		<td>Postfix</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td rowspan="2">Mail: POP3/IMAP</td>
		<td>Courier</td>
		<td>✔</td>
		<td></td>
        <td></td>
        <td></td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Dovecot</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>FTP</td>
		<td>Pure-FTPd</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td rowspan="3">DNS</td>
		<td>Bind</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>PowerDNS</td>
		<td></td>
		<td></td>
        <td></td>
        <td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>MyDNS</td>
		<td></td>
		<td></td>
        <td></td>
        <td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td rowspan="2">Database</td>
		<td>MySQL</td>
		<td>✔</td>
		<td>✔</td>
        <td></td>
        <td></td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>MariaDB</td>
		<td></td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td rowspan="2">Webmail client</td>
		<td>Roundcube</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td></td>
		<td></td>
		<td>✔*</td>
		<td></td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>SquirrelMail</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td></td>
		<td>✔</td>
		<td>✔</td>
		<td>✔*</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Chat: XMPP</td>
		<td>Metronome</td>
		<td></td>
		<td></td>
        <td></td>
        <td></td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔*</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Mailing lists</td>
		<td>Mailman</td>
		<td></td>
		<td></td>
        <td></td>
        <td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td rowspan="2">Antivirus</td>
		<td>Amavisd</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>ClamAV</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Spam filtering</td>
		<td>SpamAssassin</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Greylisting</td>
		<td>Postgrey</td>
		<td></td>
		<td>✔</td>
        <td>✔</td>
        <td></td>
		<td></td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td rowspan="2">Mail signing</td>
		<td>OpenDKIM</td>
		<td></td>
		<td>✔</td>
        <td>✔</td>
        <td></td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>OpenDMARC</td>
		<td></td>
		<td>✔</td>
        <td>✔</td>
        <td></td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Firewall</td>
		<td>UFW</td>
		<td></td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td></td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Intrusion protection</td>
		<td>Fail2Ban</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Rootkit detection</td>
		<td>rkhunter</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td rowspan="2">Statistics</td>
		<td>Webalizer</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>AWStats</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td></td>
		<td>Quota</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔*</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Let's Encrypt</td>
		<td>Certbot/letsencrypt</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td></td>
		<td>Jailkit</td>
		<td>✔</td>
		<td>✔</td>
        <td>✔</td>
        <td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td></td>
		<td>HHVM</td>
		<td></td>
		<td>✔^</td>
        <td>✔^</td>
        <td></td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td>✔</td>
		<td></td>
		<td>✔</td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>MultiServer</td>
		<td></td>
		<td></td>
        <td>✔</td>
        <td>✔</td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td></td>
	</tr>
</table>
* Not yet enabled.
^ Not yet enabled on Raspbian.


You can choose during install:
- Apache or nginx
- Dovecot or Courier
- Quota
- Jailkit
- SquirrelMail or Roundcube
- ISPConfig 3 Standard / Expert mode
- ISPConfig 3 Multiserver Setup (* Debian 8 only for now)

### How do I get set up? ###

Follow one of the above guides to install a fresh copy of a supported Linux distribution.

Run the following command as root user:

* Debian/Raspbian 7, 8, 9 and 10 and Ubuntu 14.04, 15.10, 16.04, 16.10 and 18.04

```shell
cd /tmp; wget -O installer.tgz "https://github.com/servisys/ispconfig_setup/tarball/master"; tar zxvf installer.tgz; cd *ispconfig*; bash install.sh
```
* CentOS 7

```shell
cd /tmp; sudo yum install wget unzip net-tools; wget -O installer.tgz "https://github.com/servisys/ispconfig_setup/tarball/master"; tar zxvf installer.tgz; cd *ispconfig*; sudo install.sh
```

CentOS 7 is in a very early stage, we got to test a bit, any help will be appreciated. 
Some features are missing for now, only implemented Apache and Dovecot, no webmail.

If `wget` fails, try adding the `--no-check-certificate` parameter.

===========Gr88er Specific Configs=====================================================

sudo apt install ntp ntpdate nfs-common ssh openssh-server cockpit cockpit-packagekit -y
sudo dpkg-reconfigure dash
sudo service apparmor stop
sudo update-rc.d -f apparmor remove 
sudo apt-get remove apparmor apparmor-utils -y
sudo apt update && sudo apt upgrade -y

comment out RANDFILE in /etc/ssl/openssl.cnf

sudo unlink /etc/localtime
sudo ln -s /usr/share/zoneinfo/Asia/Hong_Kong /etc/localtime
sudo timedatectl
sudo locale-gen
sudo dpkg-reconfigure locales

set hostname using
sudo hostnamectl set-hostname sample.gr88er.com

modify /etc/apt/source.list
deb http://ports.ubuntu.com/ubuntu-ports/ focal multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ focal multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ focal-updates multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-updates multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ focal-backports multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-backports multiverse

---not applicable to odroid---------------------------------------------------------------------------------------------------------------------
echo "deb https://deb.goaccess.io/ $(lsb_release -cs) main" | sudo tee -a /etc/apt/sources.list.d/goaccess.list
wget -O - https://deb.goaccess.io/gnugpg.key | sudo apt-key --keyring /etc/apt/trusted.gpg.d/goaccess.gpg add -
sudo apt-get update
sudo apt-get install goaccess
------------------------------------------------------------------------------------------------------------------------------------------------

apt-get -y install mailman
------------------------------------------------------------------------------------------------------------------------------------------------
Languages to support: <-- en (English)
Missing site list <-- Ok
------------------------------------------------------------------------------------------------------------------------------------------------

newlist mailman
------------------------------------------------------------------------------------------------------------------------------------------------
Enter the email of the person running the list: <-- admin email address, e.g. listadmin@example.com
Initial mailman password: <-- admin password for the mailman list
------------------------------------------------------------------------------------------------------------------------------------------------

newaliases
service postfix restart
ln -s /etc/mailman/apache.conf /etc/apache2/conf-available/mailman.conf
a2enconf mailman
service apache2 restart
service mailman start

cd /tmp; git clone https://github.com/agentfrostyqueen/ispconfig_amd64_single-server_ubuntu20.04; cd ispconfig_amd64_single-server_ubuntu20.04/; bash install.sh
