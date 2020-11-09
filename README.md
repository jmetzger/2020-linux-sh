# Linux Security and Hardening 

## OpenVAS 

## openvas -> gvm (Greenbone Vulnerability Management) / mrazavi 

```
Installation on Ubuntu 20.04 LTS
https://launchpad.net/~mrazavi/+archive/ubuntu/gvm
# https://www.osboxes.org/ubuntu/
# Done with vagrant init ubuntu/focal64 instead 

# postgresql is needed
sudo apt install -y postgresql 
sudo add-apt-repository ppa:mrazavi/gvm
sudo apt install gvm
# only from one machine (when same source ip) at a time 



https://<ip>:9392

(The port number has changed according to the upstream in the new version and the old 4000 port number is no longer the default)

The default username/password is as follows:

Username: admin
Password: admin

You can check the status of greenbone daemons with systemctl:

systemctl status ospd-openvas # scanner
systemctl status gvmd # manager
systemctl status gsad # web ui

```

Documentation 
https://docs.greenbone.net/GSM-Manual/gos-20.08/en/web-interface.html
