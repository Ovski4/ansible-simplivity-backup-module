Ansible simplivity backup module
================================

This module can be used to create or delete virtual machine backups using the [HPE SimpliVity OmniStack REST API](https://developer.hpe.com/api/simplivity/).

Setup
-----

Clone this repo and place the **simplivity_backup.py** file in the folder of your choice among **~/.ansible/plugins/modules/**, **/usr/share/ansible/plugins/modules/** or even a **library** folder within a role. Detailed explanation are available directly [from the docs](https://docs.ansible.com/ansible/latest/dev_guide/developing_locally.html#adding-a-module-locally)

Usage in tasks
--------------

```yml
- name: Ensure a simplivity backup is present for the current day
  simplivity_backup:
    backup_name: "Created by Ansible the {{ lookup('pipe','date +%Y-%m-%d') }}"
    omnistack_host: "omnistack_host@your_domain.net"
    virtual_machine_name: "you_vm_name"
    username: "your_username"
    password: "your_password"
    app_consistent: "true"
    retention: 10080 # 7 days
    state: "present"
  delegate_to: localhost
```

```yml
- name: Ensure no simplivity backup is present for the current day
  simplivity_backup:
    backup_name: "Created by Ansible the {{ lookup('pipe','date +%Y-%m-%d') }}"
    omnistack_host: "omnistack_host@your_domain.net"
    virtual_machine_name: "you_vm_name"
    username: "your_username"
    password: "your_password"
    state: "absent"
  delegate_to: localhost
```
