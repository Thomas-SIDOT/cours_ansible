# Exercice 2

1. Démarrez la VM ubuntu depuis le répertoire atelier-01.
```
vagrant up ubuntu
```

2. Connectez-vous à cette VM.
```
vagrant ssh ubuntu
```

3. Rafraîchissez les informations sur les paquets.
```
sudo apt update
```

4. Recherchez le paquet ansible avec les options qui vont bien.
```
sudo apt-add-repository ppa:ansible/ansible
```

5. Installez le paquet officiel fourni par la distribution.
```
sudo apt install -y ansible
```

6. Vérifiez si l’installation s’est bien déroulée.
```
ansible --version
```

7. Notez la version d’Ansible.
```
ansible [core 2.17.8]
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vagrant/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible
  python version = 3.10.12 (main, Mar 22 2024, 16:50:05) [GCC 11.4.0] (/usr/bin/python3)
  jinja version = 3.0.3
  libyaml = True
  ```

8. Déconnectez-vous et supprimez la VM.
```
vagrant destroy ubuntu
```