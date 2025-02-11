#Exercice 1

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
apt-cache search --names-only ansible
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
ansible 2.10.8
  config file = None
  configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.10.12 (main, Mar 22 2024, 16:50:05) [GCC 11.4.0]

```
8. Déconnectez-vous et supprimez la VM.
vagrant destroy ubuntu