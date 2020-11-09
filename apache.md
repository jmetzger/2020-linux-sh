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
