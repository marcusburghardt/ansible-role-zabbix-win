Role Name
=========

This role will:
- Ensure the download of the latest Agent ZIP and his presence in Windows machines;
- Ensure the installation of the agent in a standard folder;
- Ensure the presence of extra folders for templates, extra configurations, logs and scripts.
- Ensure the presence of standard Windows Service for the agent.
- Ensure the firewall rule for Zabbix Agent communication with the server.
- Ensure the agent service is running with the last version.
- Ensure the presence of the host in Zabbix Server.
- Ensure the right Windows Temapletes for this host.
- Ensure the all necessary files for the signed templates are in the host.

Admins:
To use this role you just need to adjust the vars in its files:
- defaults/main.yml
- vars/windows-NNN [optional]
And organize you inventory and group_vars, as showed in examples.
You can get an inventory example from tests/inventory.example.

Developers:
The role was wrote to be the more flexible possible. You can add tamplates and new features just editing
the "inventory file", creating a new task file for the new template and your respectivaly vars file.
Just take care of the names used for files and inventory group.

Requirements
------------

WinRM should be configured and working on Windows Machines.
Please, read the README.md to know how to do that in a more efficient way.

Role Variables
--------------

In the defaults/main.yml and vars/main.yml there are some interesting variables that should be set.
- 

Dependencies
------------

None

Example Playbook
----------------

1) Install and use in a playbook.

```
- name: Download, install and Configure the last version of Zabbix Agent for Windows.
  hosts: ansible-server, zabbix-win
  roles:
    - ansible-role-zabbix-win

```

2) group_vars tree example:
.
├── all.yml
├── linux.yml
└── windows.yml
...

3) var files examples:
cat group_vars/linux.yml
...
ansible_connection: ssh
ansible_ssh_user: ansible
ansible_ssh_pass: password
...

cat group_vars/windows.yml
...
# Authentication
ansible_user: administrator
ansible_password: password
ansible_port: 5986
ansible_connection: winrm
ansible_winrm_transport: credssp
ansible_winrm_server_cert_validation: ignore
...

License
-------

MIT

Author Information
------------------

Marcus Burghardt - marcus.apb@gmail.com
@MBSEC - marcus@mbsec.com.br
https://mbsec.com.br

