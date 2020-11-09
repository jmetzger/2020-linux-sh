# SSH - Hardening 

## endless-ssh 

https://changelog.com/news/endlessh-an-ssh-tarpit-that-slowly-sends-an-endless-banner-gOXl
https://www.youtube.com/watch?v=SKhKNUo6rJU

## documentation 

  * man sshd_config 
  
 ## hardening sshd_config 
 
```
X11Forwarding no
# No sftp please !! comment to set default to no 
# Subsystem     sftp    /usr/lib/openssh/sftp-server
```

## Only specific users 

```
# /etc/ssh/sshd_config 
AllowGroups sshallow
### 
groupadd sshallow
usermod -aG sshallow trainer01
systemctl reload ssh

```

## Work with public / private key 

```
# on server1 
ssh-keygen 
#ssh-keygen -t dsa 
ssh-copy-id training@server2
ssh training@server2
```

## Work with public with password and agent 

```
 eval $(ssh-agent)
 ssh-add
 ssh training@server2
```

