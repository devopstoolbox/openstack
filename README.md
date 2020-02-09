Role Name
=========

openstack: Openstack

[![Build Status](https://travis-ci.org/cmihai-ansible/openstack.svg?branch=master)](https://travis-ci.org/cmihai-ansible/openstack)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.openstack](https://galaxy.ansible.com/devopstoolbox.openstack)

```bash
ansible-galaxy install devopstoolbox.openstack
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
openstack_packages_state: present
openstack_remove_packages: true
openstack_enable_service: true
openstack_enable_selinux: true
openstack_copy_templates: true
openstack_firewall_configure: true
openstack_firewall_rules:
  - service: ssh
  - port: 3389
openstack_users:
  - user: devops
    group: docker
openstack_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install openstack on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: openstack is configured
      import_role:
        name: devopstoolbox.openstack
      vars:
        openstack_packages_state: present
        openstack_remove_packages: true
        openstack_enable_service: true
        openstack_enable_selinux: true
        openstack_copy_templates: true
        openstack_firewall_configure: true
        openstack_firewall_rules:
          - service: ssh
          - port: 3389
        openstack_users:
          - user: devops
            group: docker
        openstack_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: openstack
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
