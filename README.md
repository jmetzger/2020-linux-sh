# Linux Security and Hardening 

  1. [OpenVAS](openvas.md)) 



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

## Systemd 

### units 

```
service 
mounts
target
timer 
```

### systemctl 

```
systemctl tab-taste tab-taste -> zeigt alle subcommands 
systemctl get-default # default runlevel -> default target 
systemctl set-default multi-user  
systemctl isolate multi-user.target 
# 
systemctl list-unit-files -t target # show all targets 
systemctl list-units -t target # 

systemctl status sshd 

```

## OpenVAS 
