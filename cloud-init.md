# cloud-init / userdata bei digitalocean 

```
#cloud-config  
users:
  - name: meinname22
    groups: sudo
    shell: /bin/bash
    sudo: ['ALL=(ALL) NOPASSWD:ALL']
    ssh-authorized-keys:
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDf0q4PyG0doiBQYV7OlOxbRjle026hJPBWD+eKHWuVXIpAiQlSElEBqQn0pOqNJZ3IBCvSLnrdZTUph4czNC4885AArS9NkyM7
      
packages:
  - git
  - wget 
  
runcmd:
  - cd /root; echo "cloud-init rolled out ssh and ran ansible" >> 'ansible-deploy-done'

```

