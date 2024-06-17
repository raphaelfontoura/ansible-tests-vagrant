
### Comandos

> Vagrant

```bash
vagrant up 
```

```bash
vagrant up server1
```

```bash
vagrant destroy
```

```bash
vagrant reload
```

```bash
vagrant ssh ansiblesrv
```

> Ansible

```bash
ansible-playbook -i inventory.ini site.yml
```

```bash
ansible -i inventory.ini all -m gather_facts
```

```bash
ansible-playbook --list-tags site.yml
```

```bash
ansible-playbook -i inventory.ini --tags centos --ask-become-pass site.yml
```

```bash
ansible-playbook -i inventory.ini --tags "apache,db" --ask-become-pass site.yml
```
