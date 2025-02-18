# Exercice
1. myvars1.yml avec les extravars
```
ansible-playbook myvars1.yml -e moto=yamaha -e voiture=audi
```
```
TASK [Voiture] *******************************************************************************************************
ok: [localhost] => {
    "msg": "Voiture: audi"
}
TASK [Moto] **********************************************************************************************************
ok: [localhost] => {
    "msg": "Moto: yamaha"
}  
```

2. myvars2.yml avec les extravars
```
ansible-playbook myvars2.yml -e moto=yamaha -e voiture=audi
```
```
TASK [Voiture] *******************************************************************************************************
ok: [localhost] => {
    "msg": "Voiture: audi"
}
TASK [Moto] **********************************************************************************************************
ok: [localhost] => {
    "msg": "Moto: yamaha"
}
```

3. Fichiers nécessaires à myvars3.yml
```
[vagrant@control ema]$ cat group_vars/all.yml 
---  # group_vars/all.yml

mycar: "VW"
mybike: "BMW"

...
```
```
[vagrant@control ema]$ cat host_vars/target02.yml 
---  # host_vars/target02.yml

mycar: Mercedes
mybike: Honda

...
```
