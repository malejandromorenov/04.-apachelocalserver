#Apache Server
_______

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

-----
<html>
<head><title>testing Apache</title></head>
<body><p>¡Apache está trabajando!</p></body>
</html>
-----

* Reset you computer and run test http://localhost/index.html

Also:

* Run C:\Apache24\bin\ApacheMonitor.exe for visualizer task
* And test 'netstat -a -p TCP -n' for verify IPs and port
