role_bi_sysctl
=========

Sets sysctl values.

Requirements
------------

n.a.

Role Variables
--------------

The variable "baseinstall_type" should be set in the host_vars and contain one of the following values:
- virtualmachine
- default

With this variable different sets of sysctl values are read from different files in ./var/baseinstall_type_*.yml.

```
- name: Gather machine type specific variables
  include_vars: "{{ item }}"
  with_first_found:
    - "baseinstall_type_{{ baseinstall_type }}.yml"
```
These sets of sysctl values are defined by the variable "role_bi_sysctl_sysctl_values":

```
cat ./vars/baseinstall_type_virtualmachine.yml 
---
# vars file for role_bi_sysctl
role_bi_sysctl_sysctl_values:
    vm.swappiness: 1
```

Dependencies
------------

n.a.

Example Playbook
----------------

n.a.

License
-------

GNU Public License v3.0

Author Information
------------------

Melanie Desaive, m.desaive@mailbox.org 
