# Disabled kernel modules 

## Howto

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
