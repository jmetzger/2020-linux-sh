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
