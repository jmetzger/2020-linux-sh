# firewalld (ubuntu 20.04)  

## Install firewalld and restrict ufw 

```
apt install firewalld 
systemctl status firewalld 
systemctl status ufw 

# ufw service is still running, but :
ufw status
-> disabled # this has to be the case 
```


## Is firewalld running ?
```
# is it set to enabled ?
systemctl status firewalld 
firewall-cmd --state
```

## Command to control firewalld 
  
  * firewall-cmd 

## Best way to add a new rule 
```
# Step1: do it persistent -> written to disk 
firewall-cmd --add-port=82/tcp --persistant 

# Step 2: + reload firewall 
firewall-cmd --reload 
```

## Zones available 

```
firewall-cmd --get-zones 
block dmz drop external home internal public trusted work
```

## Active Zones 

```
firewall-cmd --get-active-zones
# in our case empty 
```

## Add Interface to Zone ~ Active Zone 

```
firewall-cmd --zone=public --add-interface=enp0s3 --permanent 
firewall-cmd --reload 
firewall-cmd --get-active-zones 
public
  interfaces: enp0s3

```
## Default Zone 

```
# if not specifically mentioned when using firewall-cmd
# .. add things to this zone 
firewall-cmd --get-default-zone
public

```

## References 

  * https://www.linuxjournal.com/content/understanding-firewalld-multi-zone-configurations#:~:text=Going%20line%20by%20line%20through,or%20source%20associated%20with%20it.
  * https://www.answertopia.com/ubuntu/basic-ubuntu-firewall-configuration-with-firewalld/
