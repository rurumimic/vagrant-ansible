# Vagrant with ansible

To [Vagrant with ansible_local](https://github.com/rurumimic/vagrant-ansible-local)

---

Vagrant: [Ansible Provisioner](https://www.vagrantup.com/docs/provisioning/ansible)

## Downloads

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

---

## Files

### Current directory

- [.gitignore](.gitignore): Ignore [Vagrant, Ansible](https://www.toptal.com/developers/gitignore/api/vagrant,macos,code,ansible)
- [Vagrantfile](Vagrantfile): Set VMs (instances, cpu, memory, network, security...)
- **provision**: Ansible configurations
  - [playbook.yml](provision/playbook.yml)
    - Doc: [Working with playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html)
- `.vagrant/provisioners/ansible/inventory`: Auto-Generated

---

## Set up

## Start

### Provision

```bash
vagrant up
```

**Result**:

```bash
PLAY [all]

TASK [Gathering Facts]
ok: [node1]
ok: [node2]
ok: [node3]

TASK [Who am I?]
changed: [node1]
changed: [node3]
changed: [node2]

TASK [Ensure ntpd is at the latest version]
changed: [node1]
changed: [node2]
changed: [node3]

RUNNING HANDLER [Restart ntpd]
changed: [node1]
changed: [node2]
changed: [node3]

PLAY RECAP
node1: ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
node2: ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
node3: ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

### Retry Ansible playbook

### Host machine

```bash
vagrant reload node3 --provision
```

### Other commands

```bash
vagrant status
vagrant up
vagrant ssh node1
vagrant ssh node2
vagrant ssh node3
vagrant halt
vagrant destroy [-f]
```
