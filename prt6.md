```
        ServerName www.yangqi.com

        ServerAdmin <?>
        DocumentRoot /var/www/html
        <Directory /var/www/html>
                AllowOverride AuthConfig
                AuthName "yangqi.com user auth"
                Authtype Basic
                AuthUserFile /var/.htpasswd
                require valid-user
        </Directory>
root@yangqi:/etc/apache2/sites-enabled# htpasswd -cm /var/.htpasswd who
New password: 
Re-type new password: 
Adding password for user who
root@yangqi:/etc/apache2/sites-enabled# service apache2 restart
root@yangqi:/etc/apache2/sites-enabled# 
```
```
<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	ServerName yangqi.com
	ServerAlias doc.yangqi.com

	ServerAdmin <?>
	DocumentRoot /var/www/html
	#<Directory /var/www/html>
	#	AllowOverride AuthConfig
	#	AuthName "yangqi.com user auth"
	#	Authtype Basic
	#	AuthUserFile /var/.htpasswd
	#	require valid-user
	#</Directory>
	RewriteEngine on
	RewriteCond %{HTTP_HOST} !^yangqi.com$
	RewriteRule ^/(.*)$ http://yangqi.com/$1 [R=301,L]
root@yangqi:/etc/apache2/sites-enabled# curl -x192.168.122.232:80 doc.yangqi.com
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://yangqi.com/">here</a>.</p>
<hr>
<address>Apache/2.4.41 (Ubuntu) Server at doc.yangqi.com Port 80</address>
</body></html>
root@yangqi:/etc/apache2/sites-enabled#
```
```
        RewriteEngine On
        RewriteCond %{HTTP_HOST} !^yangqi.com$
        RewriteRule ^/(.*)$ http://yangqi.com/$1 [R=301,L]

        ExpiresActive On
        ExpiresByType images/jpeg "access plus 2 hours"
        ExpiresDefault "now plus 0 min"

        SetEnvIf Request_URL ".*\.jpeg$" img

root@yangqi:/etc/apache2/sites-enabled# curl -x127.0.0.1:80 yangqi.com/images/this.jpeg -I
HTTP/1.1 200 OK
Date: Thu, 25 Mar 2021 11:18:50 GMT
Server: Apache/2.4.41 (Ubuntu)
Last-Modified: Thu, 25 Mar 2021 11:13:30 GMT
ETag: "0-5be5a815968fc"
Accept-Ranges: bytes
Cache-Control: max-age=0
Expires: Thu, 25 Mar 2021 11:18:50 GMT
Content-Type: image/jpeg

root@yangqi:/etc/apache2/sites-enabled# 
```
```
root@yangqi:~# php -v
PHP 7.4.3 (cli) (built: Oct  6 2020 15:47:56) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
    with Zend OPcache v7.4.3, Copyright (c), by Zend Technologies
root@yangqi:~# php main.php
this is test for php
root@yangqi:~# 
```
