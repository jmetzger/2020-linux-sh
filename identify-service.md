# How to identify and shutdown (including reboot) of service 

## Walkthrough

```
 ss -nlt 2>/dev/null | awk '$1 == "LISTEN" && $4 !~ /127.0.0.*.:./ && $4 !~ /::*.:./{print $4}' | sed 's/.*://' | sort -nu
 # identify cups 
 lsof -i | grep ipp
 systemctl list-units -t service cups*
 systemctl stop cups
 systemctl disable cups
 lsof -i
 ss -nlt 2>/dev/null | awk '$1 == "LISTEN" && $4 !~ /127.0.0.*.:./ && $4 !~ /::*.:./{print $4}' | sed 's/.*://' | sort -nu
```
