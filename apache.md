# Securing Apache (Ubuntu/Debian) 

## Testing 

```
curl -I <ip>

# server token 
# cat /etc/apache2/conf-available/z_db_security.conf 
ServerTokens Prod 

a2enconf z_db_security.conf
systemctl reload apache2 

# 
echo " " > /var/www/html/index.html 
```
## Fixing php 

```
vi /etc/php7.4/apache2/php.ini 
;;
expose_php off 
```
## Disable autoindex globally 

```
a2dismod -f autoindex
systemctl restart apache2
```

## Disable autoindex per Directory 

```
root@server2:/etc/apache2/conf-enabled# cat z_db_security.conf

<Directory /var/www/html>
  Options -Indexes
</Directory>

# After change 
systemctl reload apache2 

```

## Blank Error-Documents 

```
# root@server2:/etc/apache2/conf-enabled# cat z_db_security.conf
ErrorDocument 404 " "
ErrorDocument 403 " "
ErrorDocument 500 " "
# systemctl reload apache2 
```
