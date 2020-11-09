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
sudo apt install -y gvm
# only from one machine (when same source ip) at a time 
greenbone-nvt-sync
sudo greenbone-scapdata-sync
sudo greenbone-certdata-sync

You can access the Greenbone Security Assistant web interface at:

https://localhost:9392

The default username/password is as follows:

Username: admin
Password: admin

You can check the status of greenbone daemons with systemctl:

systemctl status ospd-openvas # scanner
systemctl status gvmd # manager
systemctl status gsad # web ui

# change /etc/default 
https://<ip>:9392

```

Documentation 
https://docs.greenbone.net/GSM-Manual/gos-20.08/en/web-interface.html

## Security 

```
Assets -> Software Development -> Policies -> Roles & Responsibilites 
```

### Basic Principles 

```
Assessment -> Prevention -> Detection -> Reaction 
```

### Classes of attackers 

```
White hat
Black Hat
Script Kiddie 
Hacktivist 
Nation state 
Organized crime
Bots 
```

### Sources of attacks 

```
inside 
outside
```

### Type of attacks 

```
Active (ddos lahmlegen) 
Passive (backdoor) 
```

### Evaluation of costs 

```
Money
Time 
Convenience 
Performance 
```

### Asset value (zu beschützende Werte ### 

```
How much effort for which system ?
```

### Business Impact 
```
Cost of system repair/replacement
Lost business due to disruption 
Lost production of employees 
Loss of current customers 
Loss of future customers / business partners 
Legal liability (rechtliche Konsequenzen) 
```

### Security Costs 
```
Software 
Staff 
Training 
Time of implementation 
Impact to customers, users, workers 
Network,Compute und Storage
Support costs
Insurance costs 
````

## Kill chain 

```
Reconnaisance (Informationen beschaffen)
      |
      v
Weaponization (Waffenbau: Übertragungsweg und was ist der Payload)
      |
      v
Delivery (Ausliefern) 
      |
      v 
Exploitation (führt den Schadcode aus) 
      |
      v
Installation (backdoor) 
      |
      V
Command / Control (C2) 
```
