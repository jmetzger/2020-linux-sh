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
# If you want to block access file when infected 


systemctl restart clamav-daemon 
# testing on commandline 
clamonacc --foreground --verbose

# as root set folder /var/www to 777
sudo chmod 777 /var/www

# second session -> NOT ! with user root BECAUSE: OnAccessExcludeRootUID 
trainer01:$ touch /var/www/ 
# detection will be reported in session 1 

# stop foreground service 
CTRTL + C on session 1 

# Erstellen eines services 
systemctl edit --full --force clamonacc.service 
# content >
# /etc/systemd/system/clamonacc.service
[Unit]
Description=ClamAV on Access Scanner
Requires=clamav-daemon.service
After=clamav-daemon.service syslog.target network.target

[Service]
Type=simple
User=root
ExecStartPre=/bin/bash -c "while [ ! -S /var/run/clamav/clamd.ctl ]; do sleep 1; done"

ExecStart=/usr/bin/clamonacc -F --log=/var/log/clamav/clamonacc --move=/root/quarantine
#Restart=on-failure
#RestartSec=120s

[Install]
WantedBy=multi-user.target

```

```
# Start and enable service 
systemctl enable --now clamonacc.service 

# Ready .. Steady .. Go
```


