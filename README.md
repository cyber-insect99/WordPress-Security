![Logo](https://github.com/cyber-insect99/photo-gallery-/blob/main/link-in-bio-securing--wordpress.png?raw=true)
# Securing a WordPress website by injecting code into .htaccess


## 1. Configuring the .htaccess file
Below are the .htaccess codes provided by our default WordPress. First, we need to edit the website's .htaccess file and insert these codes:

```bash
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ – [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>
# END WordPress
```





## 2. Protect .htaccess



```bash
# Protect .HTACCESS
<Files ~ “^.*\.([Hh][Tt][Aa])”>
order allow,deny
deny from all
satisfy all
</Files>
```
## 3. Protect wp-config.php


Prevent to access data form server


```bash
# WP-CONFIG BLOCK
<Files wp-config.php>
order allow,deny
deny from all
</Files>

```
##  4. No directory browsing: It will block browsing directories





```bash
# directory browsing block
Options All -Indexes

```
   -   [Check directory indexing is blocked  ](https://hackertarget.com/wordpress-security-scan/)

##  5. Disable XMLRPC.PHP



Preventing sql injection and cookies hijacking .
Block WordPress xmlrpc.php requests
Check your domain.com/xmlrpc.php (Its open normally for attacks)

```bash
# Disable XMLRPC.PHP
<Files xmlrpc.php>
order deny,allow
deny from all
</Files>

```

##  6. Disable scanners in Your Website:






```bash
# BEGIN block author scans
RewriteEngine On
RewriteBase /
RewriteCond %{QUERY_STRING} (author=\d+) [NC]
RewriteRule .* – [F]
# END block author scans


```
##  7. Block Suspicious IP






```bash
 # IP block
Order Allow,Deny
Allow from all
Deny from 1.186.48.58, 65.30.114.186, 69.143.222.95



```
## 8. Individual File Protection






```bash

# Protect the .htaccess
<files .htaccess=””>
order allow,deny
deny from all
</files>
```
## 8. wp-content Access Prevention



So that any unexpected file can enter in wp-content


```bash

create a new .htaccess file in wp-content directory & put the code there
```
![Logo](https://github.com/cyber-insect99/photo-gallery-/blob/main/lik.png?raw=true)


## 10. Uploads Directory Access Blocking



Disable PHP and Other Files Upload on (wp-content/uploads) folder:


```bash

# uploads directory access deny
<Files *.php>
deny from all
</Files>
# Block executables
<FilesMatch “\.(php|phtml|php3|php4|php5|pl|py|jsp|asp|html|htm|shtml|sh|cgi|suspected)$”>
deny from all
</FilesMatch>
```
![Logo](https://github.com/cyber-insect99/photo-gallery-/blob/main/lik2.png?raw=true)
