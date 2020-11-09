# Linux Security and Hardening 

  1. [Security Principles](security-principles.md)
  1. [Systemd](systemd.md) 
  1. [OpenVAS](openvas.md)
  1. [Apache](apache.md) 
  1. [SSH-Absicherung](ssh.md) 

  
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


