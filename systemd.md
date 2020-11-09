# systemd 

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


### Commands 

```
systemctl is-enabled ssh
systemctl status ssh 
systemctl enable ssh 
systemctl disable ssh 

```


### Important commands II

```
3  hostnamectl set-hostname server1.training.local
    4  hostname -f
    5  find / -name *ctl
    6  localectl
    7  localectl list-locales
    8  timedatectl
    9  timedatectl list-timezones
   10  history
```
