Role Name
=========

cron: Cron

[![Build Status](https://travis-ci.org/cmihai-ansible/cron.svg?branch=master)](https://travis-ci.org/cmihai-ansible/cron)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.cron](https://galaxy.ansible.com/devopstoolbox.cron)

```bash
ansible-galaxy install devopstoolbox.cron
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
cron_packages_state: present
cron_remove_packages: true
cron_enable_service: true
cron_enable_selinux: true
cron_copy_templates: true
cron_firewall_configure: true
cron_firewall_rules:
  - service: ssh
  - port: 3389
cron_users:
  - user: devops
    group: docker
cron_selinux_booleans:
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
- name: Install cron on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: cron is configured
      import_role:
        name: devopstoolbox.cron
      vars:
        cron_packages_state: present
        cron_remove_packages: true
        cron_enable_service: true
        cron_enable_selinux: true
        cron_copy_templates: true
        cron_firewall_configure: true
        cron_firewall_rules:
          - service: ssh
          - port: 3389
        cron_users:
          - user: devops
            group: docker
        cron_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: cron
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
