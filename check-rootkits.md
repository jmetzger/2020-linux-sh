# Check rootkits

## rkhunter 

```
root@server2:/etc# cat rkhunter.conf.local
PKGMGR=DPKG
UPDATE_MIRRORS=1
MIRRORS_MODE=0
WEB_CMD=""
root@server2:/etc#

rkhunter --update
rkhunter --propupd
rkhunter --versioncheck 
rkhunter --check 

```

## chkrootkit 

```
apt install chkrootkit 

```
