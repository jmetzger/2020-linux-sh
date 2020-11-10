# Unattendend Upgrades (ubuntu/debian) 

## Setup for automatically installing security updates 

```
# sudo nano /etc/apt/apt.conf.d/50unattended-upgrades
# Set allowed origins in here 

# sudo nano /etc/apt/apt.conf.d/20auto-upgrades
APT::Periodic::Unattended-Upgrade "1";

# dry run 
sudo unattended-upgrades --dry-run -–debug

# log
/var/log/unattended-upgrades/unattended-upgrades.log

```

## Docs: 

  * https://phoenixnap.com/kb/automatic-security-updates-ubuntu
