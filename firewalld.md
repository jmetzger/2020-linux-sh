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





