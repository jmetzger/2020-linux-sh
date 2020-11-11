# OSSEC and Wazuh 

## Wazuh

```
# Fork / Weiterentwicklung
https://wazuh.com/

```

## OSSEC -> Installation 

```
# https://www.ossec.net/downloads/#apt-automated-installation-on-ubuntu-and-debian
# Installs repo-config but not correctly ! 
wget -q -O - https://updates.atomicorp.com/installers/atomic | sudo bash

# add [arch=amd64] to line 
root@server1:/etc/apt/sources.list.d# cat atomic.list
deb [arch=amd64] https://updates.atomicorp.com/channels/atomic/ubuntu focal main
```

