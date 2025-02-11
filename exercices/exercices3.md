# Exercice 3

1. Démarrez la VM ubuntu depuis le répertoire atelier-01.
```
vagrant up rocky
```

2. Connectez-vous à cette VM.
```
vagrant ssh rocky
```

3. Installation de pip.
```
sudo dnf install -y python3-pip
```

4. Initialisation venv.
```
python3 -m venv ~/.venv/ansible
```

5. Lancement venv.
```
source ~/.venv/ansible/bin/activate
```

6. Mise à jour pip.
```
pip install --upgrade pip
```

7. Installation ansible.
```
pip install ansible
```

8. Vérification de la version d'ansible.
```
(ansible) [vagrant@rocky ~]$ ansible --version
ansible [core 2.15.13]
  config file = None
  configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/vagrant/.venv/ansible/lib64/python3.9/site-packages/ansible
  ansible collection location = /home/vagrant/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/vagrant/.venv/ansible/bin/ansible
  python version = 3.9.21 (main, Dec  5 2024, 00:00:00) [GCC 11.5.0 20240719 (Red Hat 11.5.0-2)] (/home/vagrant/.venv/ansible/bin/python3)
  jinja version = 3.1.5
  libyaml = True
```