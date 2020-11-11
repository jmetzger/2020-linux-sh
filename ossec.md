# OSSEC and Wazuh 

## Wazuh

```
# Fork / Weiterentwicklung
https://wazuh.com/

```

## OSSEC -> Installation 

```
## Install on 2 servers 
## server 1: ossec-hids-server
## server 2: ossec-hids-agent 

# https://www.ossec.net/downloads/#apt-automated-installation-on-ubuntu-and-debian
# Installs repo-config but not correctly ! 
wget -q -O - https://updates.atomicorp.com/installers/atomic | sudo bash

# add [arch=amd64] to line 
root@server1:/etc/apt/sources.list.d# cat atomic.list
deb [arch=amd64] https://updates.atomicorp.com/channels/atomic/ubuntu focal main
```

```
# Install ossec-hids-server 
apt install ossec-hids-server 

# adjust /var/ossec/etc/ossec.conf 
<ossec_config>
  <global>
    <email_notification>yes</email_notification>
    <email_to>root@localhost</email_to>
    <smtp_server>127.0.0.1</smtp_server>
    <email_from>ossec@localhost</email_from>
  </global>
  
```

```
# Start 
/var/ossec/bin/ossec-control start 
```

## Testing on server 1

```
ssh root@localhost 
# enter wrong password 3 times 

# alert is logged to 
 tail alerts.log
2020 Nov 11 13:48:59 server2->/var/log/auth.log
Rule: 5710 (level 5) -> 'Attempt to login using a non-existent user'
Src IP: 127.0.0.1
Nov 11 13:48:59 server2 sshd[56463]: Failed password for invalid user root from 127.0.0.1 port 44032 ssh2

** Alert 1605098949.1127: - syslog,sshd,invalid_login,authentication_failed,
2020 Nov 11 13:49:09 server2->/var/log/auth.log
Rule: 5710 (level 5) -> 'Attempt to login using a non-existent user'
Nov 11 13:49:07 server2 sshd[56463]: message repeated 2 times: [ Failed password for invalid user root from 127.0.0.1 port 44032 ssh2]
```

## Installation server 1 (agent) 

```
apt install ossec-hids-agent 

# vi /var/ossec/etc/ossec.conf 
# change to ip of server 2 
<!-- OSSEC example config -->

<ossec_config>
  <client>
    <server-ip>10.10.11.142</server-ip>
  </client>

```

## Manage Agent (server 1) on server2 (ossec-server) 

```
 /var/ossec/bin/manage_agents


****************************************
* OSSEC HIDS v3.6.0 Agent manager.     *
* The following options are available: *
****************************************
   (A)dd an agent (A).
   (E)xtract key for an agent (E).
   (L)ist already added agents (L).
   (R)emove an agent (R).
   (Q)uit.
Choose your action: A,E,L,R or Q: A

- Adding a new agent (use '\q' to return to the main menu).
  Please provide the following:
   * A name for the new agent: server1
   * The IP Address of the new agent: 10.10.11.141
   * An ID for the new agent[001]:
Agent information:
   ID:001
   Name:server1
   IP Address:10.10.11.141

Confirm adding it?(y/n): y
Agent added with ID 001.


****************************************
* OSSEC HIDS v3.6.0 Agent manager.     *
* The following options are available: *
****************************************
   (A)dd an agent (A).
   (E)xtract key for an agent (E).
   (L)ist already added agents (L).
   (R)emove an agent (R).
   (Q)uit.
Choose your action: A,E,L,R or Q: e

Available agents:
   ID: 001, Name: server1, IP: 10.10.11.141
Provide the ID of the agent to extract the key (or '\q' to quit): 1

Agent key information for '001' is:
MDAxIHNlcnZlcjEgMTAuMTAuMTEuMTQxIDkyMjAyMGQ5NzNjODE4NDM3YmIxZmU5ZDBjMmFmYmMwY2JmMmE2Y2EzNjllMGU5Y2MxNmJkYTc4OTdhYTJmNzc=

** Press ENTER to return to the main menu.



****************************************
* OSSEC HIDS v3.6.0 Agent manager.     *
* The following options are available: *
****************************************
   (A)dd an agent (A).
   (E)xtract key for an agent (E).
   (L)ist already added agents (L).
   (R)emove an agent (R).
   (Q)uit.
Choose your action: A,E,L,R or Q: q

** You must restart OSSEC for your changes to take effect.

manage_agents: Exiting.
manage_agents: Exiting.
root@server2:/var/ossec/logs/alerts#
```

