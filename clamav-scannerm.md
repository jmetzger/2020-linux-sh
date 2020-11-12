# Clamav 

## Install 

```
# also install other pacakges like freshclam 
apt install clamav-daemon

## 
apt install clamav-daemon
systemctl list-units | grep clamav
systemctl list-unit-files | grep clamav
systemctl status clamav-*
## virus definitions 
cd /var/lib/clamav/
ls -lah
cd /etc/
cd clamav/
ls -la
# config for loading virus definitions 
cat /etc/clamav/freshclam.conf
# enable and start clamav-daemon
# also loads virus definition from freshclam into memory 
systemctl enable --now clamav-daemon
systemctl status
# clamd = clam-daemon creates socket when ready 
ls -la /var/run/clamav/clamd.ctl

```

## Exclude specific non-usable (for scanning) directories 
```
# tail -n 8 clamd.conf
ExcludePath ^/proc
ExcludePath ^/sys
ExcludePath ^/run
ExcludePath ^/dev
ExcludePath ^/snap
ExcludePath ^/var/lib/lxcfs/cgroup
ExcludePath ^/root/quarantine

# AFter that restart daemon
systemctl restart clamav-daemon 
```

## Do weekly scan 

```
root@server2:/etc/cron.d# cat clamdscan
0 1 * * * root /usr/bin/clamdscan --fdpass --log=/var/log/clamav/clamdscan.log --move=/root/quarantine /
root@server2:/etc/cron.d#
```

## Do manual scan (using clam-daemon ~ clamd) 

```
/usr/bin/clamdscan --fdpass --log=/var/log/clamav/clamdscan.log --move=/root/quarantine /
```

## On-Access-Scanning 

```
# Eventually increase number of possible directories to be obeyed by inotify 
echo 524288 > /proc/sys/fs/inotify/max_user_watches

# Change /etc/clamav/clamd.conf
# to end of file 
OnAccessIncludePath /home
OnAccessIncludePath /var/www
OnAccessExcludeUname clamav
OnAccessExcludeRootUID true

# Erstellen eines services 
