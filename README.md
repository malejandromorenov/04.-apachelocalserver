# adventure_server

--------Apache-------
Downloads Links
https://www.apachelounge.com/download/


Esta descarga de Apache Lounge nos permite construir Apache siempre con las dependencias actualizadas y los compiladores más recientes que han sido probados de forma completa. Los binarios son referenciados por ASF, Microsoft, PHP, etc. y cada vez más software se empaqueta dentro de estos binarios y módulos.

Estos binarios son construidos con las fuentes de ASF en httpd.apache.org, y contienen los últimos parches y las últimas dependencias como zlib, openssl, etc. Los binarios no se ejecutan en Windows XP y 2003 y se pueden ejecutar en: 7 SP1, Vista SP2, 8 / 8.1, 10, Server 2008 SP2 / R2 SP1, Server 2012 / R2, Server 2016.
 
Allí podremos elegir la versión de 32 o 64 bits en base a la arquitectura que dispongamos. Una vez descarguemos el archivo .zip procedemos a su extracción:

a) Unzip file and install folder in C:/Apache24
b) Play in C:/Apache24/config/httpd.conf
c) Edit text file and insert the following lines 
- In the line ServerName specific the port -> localhost:80 - To define server port and localhost (127.0.0.1)
- In the line AllowOverride switch "none" for "All"
- Save change
d) Define Apache as a service
e) Get in in C:/Apache24/bin 
f) Run httpd -k install
g) Test installation, create a new file in C:/Apache24/htdocs with the next lines

-----
<html>
<head><title>testing Apache</title></head>
<body><p>¡Apache está trabajando!</p></body>
</html>
-----

h) Reset you computer and run test http://localhost/index.html
