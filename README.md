### Version 3.0.6 #
<b>v.3.0.6</b>

Run the following command as root user:

### Gr88er Specific Configs #  
sudo apt install ntp ntpdate nfs-common ssh openssh-server git cockpit cockpit-packagekit -y  
sudo dpkg-reconfigure dash  
sudo service apparmor stop  
sudo update-rc.d -f apparmor remove  
sudo apt-get remove apparmor apparmor-utils -y  
sudo service cockpit start
sudo systemctl enable cockpit.socket
sudo apt update && sudo apt upgrade -y  

### comment out RANDFILE in /etc/ssl/openssl.cnf ##
sudo unlink /etc/localtime  
sudo ln -s /usr/share/zoneinfo/Asia/Hong_Kong /etc/localtime  
sudo timedatectl  
sudo locale-gen  
sudo dpkg-reconfigure locales  

### set hostname using ##
sudo hostnamectl set-hostname sample.gr88er.com  
-modify /etc/hosts  
-enable keyless login  

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
Note: remove hhvm on odroid  

### Run this after the script ##
fix /etc/postfix/master.cf  
openssl dhparam -out /etc/ssl/private/pure-ftpd-dhparams.pem 3072  
create phpmyadmin table in DB  
Fix phpmyadmin bugs  
> /usr/share/phpmyadmin/libraries/plugin_interface.lib.php  
From  
> if ($options != null && count($options) > 0) {  
To  
> if ($options != null && count((array)$options) > 0) {  

> /usr/share/phpmyadmin/libraries/sql.lib.php  
From  
> || (count($analyzed_sql_results[‘select_expr’] == 1)  
To  
> || (count($analyzed_sql_results[‘select_expr’]) == 1  

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

Install ISPConfig on server1 and prepare the slave server using the instruction above without ISPConfig  

## MySQL Master-Master Replication #  

### Prepare Server1 ##  

Login into MySQL and create an account specifically for replication in MySQL. I use a separate user for the replication to minimize the possibility of compromise to other accounts (username and password are stored in plain text in the master info repository file or table):  
> CREATE USER 'slaveuser2'@'server2.example.tld' IDENTIFIED BY 'slave_user_password';  
> CREATE USER 'slaveuser2'@'192.168.0.106' IDENTIFIED BY 'slave_user_password';  
> CREATE USER 'slaveuser2'@'2001:db8::2' IDENTIFIED BY 'slave_user_password';  

and grant the REPLICATION SLAVE privilege:  
> GRANT REPLICATION SLAVE ON *.* TO 'slaveuser2'@'server2.example.tld';  
> GRANT REPLICATION SLAVE ON *.* TO 'slaveuser2'@'192.168.0.106';  
> GRANT REPLICATION SLAVE ON *.* TO 'slaveuser2'@'2001:db8::2';  
> QUIT;  

Make some changes for the replication to your MySQL-Config:  
> vi /etc/mysql/my.cnf  

Search for the section that starts with [mysqld], and put the following options into it (commenting out all existing
conflicting options):  
> [...]  
> [mysqld]  
> server-id = 1  
> replicate-same-server-id = 0  
> auto-increment-increment = 2  
> auto-increment-offset = 1  
> log_bin = mysql-bin.log  
> expire_logs_days = 10  
> max_binlog_size = 100M  
> binlog_format = mixed  
> sync_binlog = 1  
> relay-log = slave-relay.log  
> relay-log-index = slave-relay-log.index  
> slave_skip_errors = 1007,1008,1050, 1396  
> bind-address = ::  

and restart MySQL afterwards:  
> service mysql restart   

### Prepare Server2 ##
Make some changes for the replication to your MySQL-Config:  
> nano /etc/mysql/my.cnf  

Search for the section that starts with [mysqld], and put the following options into it (commenting out all existing conflicting options):  
> [...]  
> [mysqld]  
> server-id = 2  
> log_bin = mysql-bin.log  
> expire_logs_days = 10  
> max_binlog_size = 100M  
> binlog_format = mixed  
> sync_binlog = 1  
> slave_skip_errors = 1007,1008,1050,1396  

## Create a snapshot of the existing databases on server1 #  
Dump the databases on server1 and enter the MySQL root password:  

> mysqldump -p --all-databases --allow-keywords --master-data --events --single-transaction > /root/mysqldump.sql  

Copy the dump to server2:  
> scp /root/mysqldump.sql root@192.168.0.106:/root  

### Import the dump on server2 ##  
> mysql -u root -p < /root/mysqldump.sql  

Shutdown mysql on server2:  
> service mysql stop  

Copy the defaults-file for MySQL from server1 to server2. Switch to server1 and run  
> scp /etc/mysql/debian.cnf root@192.168.0.106:/etc/mysql/debian.cnf  

Start MySQL on server2:  
> service mysql start  

and login into MySQL to set the master-server with:  
> CHANGE MASTER TO MASTER_HOST="server1.example.tld", MASTER_USER="slaveuser2", MASTER_PASSWORD="slave_user_password";  

Start the slave:  
> START SLAVE;  

and check the slave-status  
And compare the Replication Master Binary Log Coordinates.  
We are running a MySQL Master-Slave-Replication where server1 is the master and server2 the slave.  

## MySQL Master-Master-Replication #
Create the MySQL-User for the replication and grant the privileg in MySQL:  
> CREATE USER 'slaveuser1'@'server1.example.tld' IDENTIFIED BY 'slave_user_password';  
> CREATE USER 'slaveuser1'@'192.168.0.105' IDENTIFIED BY 'slave_user_password';  
> CREATE USER 'slaveuser1'@'2001:db8::1' IDENTIFIED BY 'slave_user_password';  
> GRANT REPLICATION SLAVE ON *.* TO 'slaveuser1'@'server1.example.tld';  
> GRANT REPLICATION SLAVE ON *.* TO 'slaveuser1'@'192.168.0.105';  
> GRANT REPLICATION SLAVE ON *.* TO 'slaveuser1'@'2001:db8::1';  
> QUIT;  

Make some changes for the replication to your MySQL-Config on server2:  
> vi /etc/mysql/my.cnf  

Search for the section that starts with [mysqld], and put the following options into it (commenting out all existing
conflicting options):  

> [...]  
> [mysqld]  
> [...]  
> replicate-same-server-id = 0  
> auto-increment-increment = 2  
> auto-increment-offset = 2  
> relay-log = slave-relay.log  
> relay-log-index = slave-relay-log.index  

and restart MySQL:  
> service mysql restart  

Login into MySQL and get the Master Binary Log Coordinates:  
> SHOW MASTER STATUS \G  

Login into MySQL on server1 and set the master-server with  
> CHANGE MASTER TO MASTER_HOST="server2.example.tld", MASTER_PASSWORD="slave_user_password", MASTER_USER="slaveuser1", MASTER_LOG_FILE='mysql-bin.000002',
MASTER_LOG_POS=326;  

Start the slave:  
> START SLAVE;  

and check the slave-status with  
> SHOW SLAVE STATUS G  
 
## Install ISPConfig on the Slave Server #

Login into MySQL and create a root-user for server2:  

> CREATE USER 'root'@'192.168.0.106' IDENTIFIED BY 'myrootpassword';  
> GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.0.106' WITH GRANT OPTION MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0;  
> CREATE USER 'root'@'server2.example.tld' IDENTIFIED BY 'myrootpassword';  
> GRANT ALL PRIVILEGES ON *.* TO 'root'@'server2.example.tld' WITH GRANT OPTION MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0;  
> CREATE USER 'root'@'2a01:dddd::2' IDENTIFIED BY 'myrootpassword';  
> GRANT ALL PRIVILEGES ON *.* TO 'root'@'2001:db8::2' WITH GRANT OPTION MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0;  
> QUIT;  

The replication covers all database. Copy the db-configs for PHPMyAdmin and roundcube from server1 to server2.  
On server1:  

> scp /etc/dbconfig-common/phpmyadmin.conf root@192.168.0.106:/etc/dbconfig-common/phpmyadmin.conf  
> scp /etc/phpmyadmin/config-db.php root@192.168.0.106:/etc/phpmyadmin/config-db.php  
> scp /etc/dbconfig-common/roundcube.conf root@192.168.0.106:/etc/dbconfig-common/roundcube.conf  
> scp /etc/roundcube/debian-db.php root@192.168.0.106:/etc/roundcube/debian-db.php  
 
On server2:  Install ISPConfig on server 2  
Login into ISPConfig on server1 and go to _System / Server Services_ and choose server2.example.tld and set _Is
mirror of Server_ to server1.example.tld:  
Go to _Server Config_, choose Tab _Web_ and set the permissions for both servers:  
If you have already data (Websites, Mail....) running on server1, go to _Tools / Resync_ and start a full resync (enable all checkboxes).  

## Sync Emails with Dovecot #

Since Dovecot 2 it's possible to use Dovect's dsync to keep the main base in sync. If you have already mail's on server1, they will be replicated to server2 without any further interaction.  
You must use the same port (4711) and the same password (replication_password) on both servers.  
server1:  

Open /etc/dovecot/dovecot-sql.conf  
> nano /etc/dovecot/dovecot-sql.conf  

and enable the iterate_query:  
old:  
> #iterate_query = SELECT email as user FROM mail_user  

new:  
> iterate_query = SELECT email as user FROM mail_user  

modify /etc/dovecot/dovecot.conf  
> nano /etc/dovecot/dovecot.conf  

restart Dovecot:  
> service dovecot restart  

server2:  
modify /etc/dovecot/dovecot-sql.conf  
> nano /etc/dovecot/dovecot-sql.conf  

and enable the iterate_query:  
old:  
> #iterate_query = SELECT email as user FROM mail_user  

new:  
> iterate_query = SELECT email as user FROM mail_user  

modify /etc/dovecot/dovecot.conf  
> nano /etc/dovecot/dovecot.conf  

restart Dovecot:  
> service dovecot restart  

You can check the replication on each server:  
> doveadm replicator status '*'  
