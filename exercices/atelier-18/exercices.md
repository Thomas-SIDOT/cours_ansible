# Exercice

1. Voici les fichiers de variables utilisé avec le playbook chrony.yml

vars/chrony_debian.yml 
```
chrony_package_name: chrony
chrony_service_name: chrony
chrony_config_path: /etc/chrony/chrony.conf
```
vars/chrony_rocky.yml
```
chrony_package_name: chrony
chrony_service_name: chronyd
chrony_config_path: /etc/chrony.conf
```
vars/chrony_opensuse-leap.yml
```
chrony_package_name: chrony
chrony_service_name: chronyd
chrony_config_path: /etc/chrony.conf
```
vars/chrony_ubuntu.yml
```
chrony_package_name: chrony
chrony_service_name: chrony
chrony_config_path: /etc/chrony/chrony.conf
```

2. Voici le template utilisé.
templates/chrony.conf.j2
```
# chrony.conf
server 0.fr.pool.ntp.org iburst
server 1.fr.pool.ntp.org iburst
server 2.fr.pool.ntp.org iburst
server 3.fr.pool.ntp.org iburst
driftfile /var/lib/chrony/drift
makestep 1.0 3
rtcsync
logdir /var/log/chrony
```