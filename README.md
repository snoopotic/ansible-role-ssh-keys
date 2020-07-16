ansible-role-ssh-keys
=========

Ansible Role to Deploy ssh-keys in a way many it-governance models would commit I guess. 

- Locally creates User Accounts with bash and deploys ssh keys there.
- deploys all keys to the connecting/initial ansible_user (may be optional in later version)
- deletes Users/Keys you take out from user List

Requirements
------------

- This Role needs sudo and installs sudo if not yet installed. You need to be fine with sudo.
- You need to place .pub Files into your playbooks 'files/dir' OR in your set ssh_keys_dir
- The .pub Key filenames currently need to follow the syntax \<username\>.pub where 'username' is the same like the list element in ssh_users

Role Variables
--------------

| Variable | Default Value | required/optional | Description |
| --- | --- | --- | --- |
| ssh_users | - | required | List of accountnames that need access to your Systems |
| ssh_keys_dir | - | optional | Set directory relative or absolute in your client's filesystem where you have placed your ssh .pub Files |

Dependencies
------------

Currently none.

Example Playbook
----------------

Best is you create a folder 'files' inside your plays folder and place your .pub keys in there. For more Information you can look into <https://docs.ansible.com/ansible/latest/user_guide/playbook_pathing.html>

    - hosts: servers
      roles:
         - role: ansible-role-ssh-keys
           vars:
             ssh_users:
               - 'samantha'
               - 'bob'
             ssh_keys_dir: ssh-keys/

License
-------

MIT
