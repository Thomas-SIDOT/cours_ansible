# Exercice

1. J'ai commencé par modifier le fichier /etc/hosts en ajoutant les lignes suivantes.
```
192.168.56.10 control
192.168.56.20 target01
192.168.56.30 target02
192.168.56.40 target03
```

2. Collecter les clefs publiques des cibles
```
ssh-keyscan -t rsa target01 target02 target03 >> .ssh/known_hosts
```

3. Génération d'une clef ssh
```
ssh-keygen
```

4. Distribution de la clef publique du contrôleur.
```
ssh-copy-id vagrant@target01
ssh-copy-id vagrant@target02
ssh-copy-id vagrant@target03
```

5. Je commence par déterminer l'os du contrôleur.
```
vagrant@control:~$ cat /etc/os-release 
PRETTY_NAME="Ubuntu 22.04.4 LTS"
```
6. Installation d'ansible
```
sudo apt update
sudo apt install -y ansible
ansible --version
ansible 2.10.8
  config file = None
  configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.10.12 (main, Mar 22 2024, 16:50:05) [GCC 11.4.0]
```
7. Test de ping
```
ansible all -i target01,target02,target03 -m ping
```
8. Vérification si le fichier de configuration est bien pris en compte par ansible.
```
vagrant@control:~$ ansible --version | head -n 2
ansible 2.10.8
  config file = /home/vagrant/ansible.cfg
```
9. Extrait de ansible.cfg.
```
[defaults]
inventory = ./hosts
log_path = ~/journal/ansible.log
```
10. Test de la journalisation.
```
vagrant@control:~$ ansible all -i target01,target02,target03 -m ping
vagrant@control:~$ cat ~/journal/ansible.log 
2025-02-12 10:59:12,968 p=3774 u=vagrant n=ansible | target03 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
2025-02-12 10:59:12,995 p=3774 u=vagrant n=ansible | target02 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
2025-02-12 10:59:13,013 p=3774 u=vagrant n=ansible | target01 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```
11. Modification du fichier hosts.
```
vagrant@control:~$ cat hosts 
[testlab]
target01
target02
target03

[testlab:vars]
ansible_user=vagrant
```
12. Ping du group all
```
vagrant@control:~$ ansible all -m ping
target01 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
target03 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
target02 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```
13. Élévation des droits pour l'utilisateur vagrant sur les cibles.
Ajout de la ligne dans les variables du fichier hosts.
```
ansible_become=yes
```
14. Affichage de la première ligne de /etc/shadow.
```
vagrant@control:~$ ansible all -a "head -n 1 /etc/shadow"
target01 | CHANGED | rc=0 >>
root:*:19769:0:99999:7:::
target02 | CHANGED | rc=0 >>
root:*:19769:0:99999:7:::
target03 | CHANGED | rc=0 >>
root:*:19769:0:99999:7:::
```