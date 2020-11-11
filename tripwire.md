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

```
