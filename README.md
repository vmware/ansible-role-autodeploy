# ansible-role-autodeploy

[Ansible](https://github.com/ansible/ansible) module for installing,
configuraing and manipulating VMware AutoDeploy.

## Requirements

This role currently supports Debian/Ubuntu and CentOS distros.

The role also requires a valid install of PowerCLI.

## Role Variables

Documentation here is under way . . . in flux as the vars get integrated into SuperVIO UI.

## Example playbook

```
---
- name: prepare vcenter for autodeploy
  hosts: vcsa
  remote_user: root
  roles:
    - autodeploy
  vars:
    - autodeploy_vcsa: true
    - autodeploy_rules: false
  vars_files:
    - /var/lib/supervio/answerfile.yml

- name: prepare autodeploy rules
  hosts: ruleshost
  roles:
    - autodeploy
  vars:
    - autodeploy_vcsa: false
    - autodeploy_rules: true
    - ansible_ssh_user: administrator
    - ansible_ssh_pass: VMware1!
    - ansible_ssh_port: 5986
    - ansible_connection: winrm
  vars_files:
    - /var/lib/supervio/answerfile.yml
```

## License

TBD

## Author Information

This role was created in 2015 by [Jake Dupuy / VMware](http://www.vmware.com/).