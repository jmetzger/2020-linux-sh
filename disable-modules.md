# Disabled kernel modules 



## Howto // with install

```
modprobe -r i2c_piix4
lsmod  | grep i2c
cd /etc/modprobe.d/


nano disable-i2c.conf
# insert into file 
# install i2c_piix4 /bin/true 

modprobe -v i2c-piix4
lsmod | grep i2c

```

## Howto // disable loading perms after having loaded modules 

```
modprobe -r i2c_piix4
lsmod | grep i2c
cd /proc/sys/kernel/
pwd
ls -la modules_disabled
cat modules_disabled
echo 1 > modules_disabled
# does not work 
modprobe i2c_piix4
# not working 
echo 0 > modules_disabled
ls -la modules_disabled

```

