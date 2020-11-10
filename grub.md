# Grub 

## On boot 

```
# kernel-params / kernel boot options 
# in line linux -> add to end 
# Variante 1
init=/bin/bash # <- root password ändern  


# Variante 2a
# system wird gemountet und die wichtigsten services gestartet
# aber: kein Netzwerk und Single-User 
systemd.unit=emergency.target # password wird verlangt 

# Variante 2b
emergency 

# Variante 3 
# System wird gemountet, services gestartet
# aber: kein Netzwerk und Single-User  
systemd.unit=rescue.target 
```

## man-page kernel parameters 

```
man kernel-command-line # debian/ubuntu
man kernel-params # centos / redhat 
```
