# Tripwire (Debian)

## Install / config 

```
# Debian
apt install tripwire
# Answer the questions as follows:
# Site
# Schlüssel erzeugen -> Ja
# Lokalen Schlüssel erzeugen -> Ja
# Tripwire - Konfigurationsdatei erzeugen -> Ja
# Policies -> Ja

#Tripwire - What is where ?
Binaries: /usr/sbin
Database: /var/lib/tripwire

# Tripewire - Keys
site key : Secure configuration files (may not be modified)
local key: Protect binary files

# Change pol-file 
# vi /etc/tripwire/twpol.txt 

# after 
twadmin --create-polfile /etc/tripwire/twpol.txt
# or to just update the db 
# like so--->
tripwire --update-policy --secure-mode low /etc/tripwire/twpol.txt
# or so ---->
twadmin -m P /etc/tripwire/twpol.txt

# check again 
tripwire --check 
```
