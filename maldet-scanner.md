# Maldet Malware Scanner 

```
https://www.hostwinds.com/guide/how-to-install-maldet-on-ubuntu/

# Developer 
https://www.rfxn.com/projects/linux-malware-detect/
```

## Installation (Ubuntu/Debian) - with inotify (Live scan)  

```
apt install inotify-tools 

cd /opt/
wget http://www.rfxn.com/downloads/maldetect-current.tar.gz
tar xfz maldetect-current.tar.gz
cd maldetect-*
# Run the installation script
./install.sh
# Once the installation script has finished you can then modify the configuration file using your preferred text editor. Use the following link for more info on how to edit files in the Linux shell here.
/usr/local/maldetect/conf.maldet
 
# Recommended configurable options:
#Enable email alerts
email_alert=1
#Enter the destination address for email alerts
email_addr=”user@yourdomain.tld”
#Quarantine any detected malware and send an alert
quarantine_hits=1
#Clean the detected malware injections
quarantine_clean=0
#The default suspend action for infected users. Change to 1 if you wish to suspend the user
quarantine_suspend_user=0
# mode 
default_monitor_mode="/usr/local/maldetect/monitor_paths"

# Testing 
echo "/var/www" >> /usr/local/maldetect/monitor_paths 

# 
apt install apache2 

# 
systemctl start maldet.service 

# 
cd /var/www/html 
wget https://secure.eicar.org/eicar.com.txt

# 
maldet --report list 
# detected malware !! 

```

## Alternative manual start

```
 
# Be sure to have the newest signatures
maldet -d && maldet -u

# Scanning Directories For Malware
Scan a particular path.
maldet -a /home/username
 
# Scan all user directories in /home
maldet --scan-all /home
 
#Reporting
#List all scan reports
maldet --report list
 
#Display the details for a specific report. Note, modify the SCAN-ID with the one you intend to use.
maldet --report SCAN-ID

```



