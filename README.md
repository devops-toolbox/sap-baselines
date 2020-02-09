Role Name
=========

sap-baselines: Sap-baselines

[![Build Status](https://travis-ci.org/cmihai-ansible/sap-baselines.svg?branch=master)](https://travis-ci.org/cmihai-ansible/sap-baselines)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.sap-baselines](https://galaxy.ansible.com/devopstoolbox.sap-baselines)

```bash
ansible-galaxy install devopstoolbox.sap-baselines
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
sap-baselines_packages_state: present
sap-baselines_remove_packages: true
sap-baselines_enable_service: true
sap-baselines_enable_selinux: true
sap-baselines_copy_templates: true
sap-baselines_firewall_configure: true
sap-baselines_firewall_rules:
  - service: ssh
  - port: 3389
sap-baselines_users:
  - user: devops
    group: docker
sap-baselines_selinux_booleans:
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
- name: Install sap-baselines on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: sap-baselines is configured
      import_role:
        name: devopstoolbox.sap-baselines
      vars:
        sap-baselines_packages_state: present
        sap-baselines_remove_packages: true
        sap-baselines_enable_service: true
        sap-baselines_enable_selinux: true
        sap-baselines_copy_templates: true
        sap-baselines_firewall_configure: true
        sap-baselines_firewall_rules:
          - service: ssh
          - port: 3389
        sap-baselines_users:
          - user: devops
            group: docker
        sap-baselines_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: sap-baselines
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
