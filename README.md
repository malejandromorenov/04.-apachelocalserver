# Apache Server
_______

# Microsoft
Downloads Links
https://www.apachelounge.com/download/


This Apache Lounge download allows us to build Apache always with the updated dependencies and the most recent compilers that have been fully tested. The binaries are referenced by ASF, Microsoft, PHP, etc. and more and more software is packaged within these binaries and modules.

These binaries are built with the ASF sources at httpd.apache.org, and contain the latest patches and the latest dependencies such as zlib, openssl, etc. The binaries do not run on Windows XP and 2003 and can run on: 7 SP1, Vista SP2, 8 / 8.1, 10, Server 2008 SP2 / R2 SP1, Server 2012 / R2, Server 2016.
 
There we can choose the 32 or 64 bit version based on the architecture we have. Once we download the .zip file we proceed to its extraction:


* Unzip file and install folder in C:/Apache24
* Play in C:/Apache24/config/httpd.conf
* Edit text file and insert the following lines 
* the line ServerName specific the port -> localhost:80 - To define server port and localhost (127.0.0.1)
* In the line AllowOverride switch "none" for "All"
* Save change

* Define Apache as a service
* Get in in C:/Apache24/bin 
* Run httpd -k install
* Test installation, create a new file in C:/Apache24/htdocs with the next lines

_______________________________________
<html>
<head><title>testing Apache</title></head>
<body><p>¡Apache está trabajando!</p></body>
</html>
_______________________________________

* Reset you computer and run test http://localhost/index.html
or
127.0.0.1:80 and localhost

Also:

* Run C:\Apache24\bin\ApacheMonitor.exe for visualizer task
* And test 
```cmd
netstat -a -p TCP -n 
```
for verify IPs and ports.

____________________________________________________

# Debian

# Update May 2019
In other situation over one instance the software install. Up install Matomo, software can read the host local and remote.
Steps.
1.- Install Apache Server
2.- Install MySQL Server
3.- Configure the installation

## Installing Apache
Apache is available within Debian's default software repositories, making it possible to install it using conventional package management tools.

Let's begin by updating the local package index to reflect the latest upstream changes:
```sh
sudo apt update
```
Then, install the apache2 package:
```sh
sudo apt install apache2
```
After confirming the installation, apt will install Apache and all required dependencies.

Before testing Apache, it's necessary to modify the firewall settings to allow outside access to the default web ports. Assuming that you followed the instructions in the prerequisites, you should have a UFW firewall configured to restrict access to your server.

During installation, Apache registers itself with UFW to provide a few application profiles that can be used to enable or disable access to Apache through the firewall.

List the ufw application profiles by typing:
```sh
sudo ufw app list
```
You will see a list of the application profiles:
```sh
Output
Available applications:
  AIM
  Bonjour
  CIFS
. . . 
 WWW
 WWW Cache
 WWW Full
 WWW Secure
. . . 
```
The Apache profiles begin with WWW:

WWW: This profile opens only port 80 (normal, unencrypted web traffic)
WWW Cache: This profile opens only port 8080 (sometimes used for caching and web proxies)
WWW Full: This profile opens both port 80 (normal, unencrypted web traffic) and port 443 (TLS/SSL encrypted traffic)
WWW Secure: This profile opens only port 443 (TLS/SSL encrypted traffic)
It is recommended that you enable the most restrictive profile that will still allow the traffic you've configured. Since we haven't configured SSL for our server yet in this guide, we will only need to allow traffic on port 80:
```sh
sudo ufw allow 'WWW'
```
You can verify the change by typing:
```sh
sudo ufw status
```
You should see HTTP traffic allowed in the displayed output:
```sh
Output
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
WWW                        ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
WWW (v6)                   ALLOW       Anywhere (v6)
```
As you can see, the profile has been activated to allow access to the web server.

At the end of the installation process, Debian 9 starts Apache. The web server should already be up and running.

Check with the systemd init system to make sure the service is running by typing:
```sh
sudo systemctl status apache2
```
Output
```sh
● apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2018-09-05 19:21:48 UTC; 13min ago
 Main PID: 12849 (apache2)
   CGroup: /system.slice/apache2.service
           ├─12849 /usr/sbin/apache2 -k start
           ├─12850 /usr/sbin/apache2 -k start
           └─12852 /usr/sbin/apache2 -k start

Sep 05 19:21:48 apache systemd[1]: Starting The Apache HTTP Server...
Sep 05 19:21:48 apache systemd[1]: Started The Apache HTTP Server.
```

As you can see from this output, the service appears to have started successfully. However, the best way to test this is to request a page from Apache.

You can access the default Apache landing page to confirm that the software is running properly through your IP address. If you do not know your server's IP address, you can get it a few different ways from the command line.

Try typing this at your server's command prompt:
```sh
hostname -I
```
You will get back a few addresses separated by spaces. You can try each in your web browser to see if they work.

An alternative is using the curl tool, which should give you your public IP address as seen from another location on the internet.

First, install curl using apt:
```sh
sudo apt install curl
```
Then, use curl to retrieve icanhazip.com using IPv4:
```sh
curl -4 icanhazip.com
```
When you have your server's IP address, enter it into your browser's address bar:

http://your_server_ip

![Apache default page](https://github.com/malejandromorenov/apache-local-server/blob/master/small_apache_default_debian9.png)

You should see the default Debian 9 Apache web page:

This page indicates that Apache is working correctly. It also includes some basic information about important Apache files and directory locations.

# MySQL Server

Step 1 – Prerequisites
Login to your Debian 9 system using shell access. For remote systems connect with SSH. Windows users can use Putty or other alternatives applications for SSH connection.

ssh root@debian9
Run below commands to upgrade the current packages to the latest version.

sudo apt update 
sudo apt upgrade
Step 2 – Configure MySQL PPA
MySQL team provides official MySQL PPA for Debian Linux. You can download and install the package on your Debian system, which will add PPA file to your system. Run below command to enable PPA.

wget http://repo.mysql.com/mysql-apt-config_0.8.9-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.9-1_all.deb
During installation of MySQL apt config package, It will prompt to select MySQL version to install. Select the MySQL 5.7 or 5.6 option to install on your system.

Install MySQL on Debian 9 Stretch

Step 3 – Install MySQL on Debian 9
Your system is ready for the MySQL installation. Run the following commands to install MySQL on a Debian machine.

sudo apt update 
sudo apt install mysql-server
The installation process will prompt for the root password to set as default. Input a secure password and same to confirm password window. This will be MySQL root user password required to log in to MySQL server.

Install MySQL on Debian 9

Install MySQL on Debian Stretch

Step 4 – Secure MySQL Installation
Execute the below command on your system to make security changes on your Database server. This will prompt some questions. The do the high security provide all answers to yes.

First start the MysQL service if not started:

sudo systemctl restart mysql
Then run below command:

sudo mysql_secure_installation

#### Install the PHP Packages
Sure, you'll be basing this on either a standard LAMP or LEMP stack, but Matomo is a fairly large application with its own requirements. Before you get started, install these PHP dependencies.

```bash
sudo apt install php-curl php-gd php-cli php-geoip php-mysql php-mbstring php-xml unzip
```

# Create A Database
Unless you created a database specifically for Matomo during your LAMP/LEMP setup, you're going to need to create a new one for Matomo to use. Sign in to MySQL as your root user.
```bash
mysql -u root -p
```
Once you're in the MySQL console, create a new database.
```bash
CREATE DATABASE matomo;
```
Create a new user for it too.
```bash
CREATE USER `matomo_admin`@`localhost` IDENTIFIED BY 'yourpass';
```
Grant your new user permissions on the DB.
```bahs
GRANT ALL ON matomo.* TO `matomo_admin`@`localhost`;
```
Flush your privileges and exit.
```bash
FLUSH PRIVILEGES;
```
# Matomo
Matomo is free and open source, but it's better to get it directly from the developers than from any distribution repositories. It just ensures that the version that you get is current. Grab the latest release with wget.
```bash
wget https://builds.matomo.org/piwik.zip
```
That link might change to reflect the name change from Piwik to Matomo in the near future. Be sure to look out for that. Unzip your file and copy it into your web root directory. 
```bash
unzip piwik.zip
sudo cp -r piwik /var/www/
```
The result should be a piwik directory at /var/www/piwik. Change ownership of it to the web server.
```cmd
sudo chown -R www-data:www-data /var/www/piwik
```

# Configure The Web Server
Your web server configuration is going to depend on whether you're using Apache or Nginx. Either one will assume that you're going to host on a server with more than one site using virtual hosts.
Apache
You're going to need to create a new virtual host for your site. Start by copying either the default configuration or a previous configuration to modify to host Matomo.

```cmd
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/matomo.conf
```
Open your configuration and modify the DocumentRoot to point at where you unpacked the piwik directory.
DocumentRoot /var/www/piwik
Set the ServerName to your site's domain(or localhost if you're just testing). This would most likely be the subdomain that you've chosen for your analytics.
ServerName analytics.your-site.com
When you're done, save your file and exit. Enable your site in Apache.
```cmd
sudo a2ensite matomo.conf
```
Reload Apache.
```cmd
sudo systemctl reload apache2
```

# Nginx
Create a new site configuration for Matomo in the /etc/nginx/sites-available directory. Open that file. Everything here is completely standard for a PHP configuration. Create a new server block for your analytics site. It should look similar to this one. 

```notes
server {
	listen 80;
	listen [::]:80;
	server_name analytics.your_site.com;

	index index.php;
	root /var/www/piwik;

	access_log /var/log/nginx/analytics.your-site.com.access_log;
	error_log /var/log/nginx/analytics.your-site.com.error_log;

	location / {
		try_files $uri $uri/ =404;
	}

	location ~ \.php$ {
		include snippets/fastcgi-php.conf;
		fastcgi_pass unix:/var/run/php/php7.1-fpm.sock;
	}
}
```

If you're using SSL(like Matomo recommends), include that and the 301 redirect as well. Don't forget to link your site configuration and restart Nginx. 

```cmd
sudo ln -s /etc/nginx/sites-available/matomo /etc/nginx/sites-enabled/matomo
sudo systemctl restart nginx
```

# Matomo Setup
Now that you have your web server and database configured, you can start to set up Matomo with it's web based installer. Navigate to the address where you configured your server to host Matomo. 

Ubuntu Bionic Begin Matmomo Install
The first screen will welcome you to Matomo and prompt you to begin the install process. After that, Matomo will perform a full system check for its requirements. This should be fine, since you installed them at the beginning of the process. 

Ubuntu Bionic Matomo System Check


Ubuntu Bionic Matomo Database Setup
Next, Matomo will ask you to connect to the database. Enter the information that you used to set up your database earlier. It will take a couple of seconds to connect and tell you when it has done so successfully. 

Ubuntu Bionic Create Matomo Superuser

 
Then, you'll be asked to create a superuser account. This is the main account that you'll use to manage everything on the platform. 

Ubuntu Bionic Matomo Website Setup
After your superuser, Matomo will ask to set up a website. This will add a site to the roster that Matomo will monitor and provide analytic data for. It will use the information that you provide to generate JavaScript tracking code. 

Ubuntu Bionic JavaScript Tracking Code
Matomo will give you a block of JavaScript to insert into your site. Paste the code into your website's source in a place that will appear on every page. When you're done inserting the JavaScript into your site, you can click through the rest of the setup. Matomo will congratulate you on completing it when you're done. 

Ubuntu Bionic Matomo Dashboard
It'll then send you to the login screen. Use the account that you created for yourself to sign in. When you do, you'll get a message that Matomo hasn't collected any data yet. That's fine. You just set it up. Tell Matomo not to show the message again for the next hour, and you can progress through to your dashboard. Matomo is running successfully on your server!
Closing Thoughts
Explore the Matomo dashboard. It provides you with loads of different options. It records a lot of useful information and organizes it for you in about as many ways as you're ever going to need. You can generate additional JavaScript code for additional sites too. Matomo is more than capable of monitoring multiple websites at once. So, once you've set up Matomo once, you have your own self hosted analytics service for as many websites as you need.
