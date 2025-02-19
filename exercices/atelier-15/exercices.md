# Exercice

1. Voici le playbook kernel.yml
```
---  # kernel.yml

- hosts: all
  gather_facts: false

  tasks:

    - name: Noyaux
      command: uname -a
      changed_when: false
      register: uname_cmd

    - debug:
        msg: "{{uname_cmd}}"

...
```

2. Avec le paramètre var.

```
 - debug:
        var: uname_cmd.stdout_lines
```

3. Voici le playbook packages.yml
```
---  # packages.yml

- hosts: rocky,suse
  gather_facts: false

  tasks:

    - name: Paquets totaux
      shell: rpm -qa | wc -l
      changed_when: false
      register: package_total_cmd

    - debug:
        msg: "{{package_total_cmd}}"
...
```