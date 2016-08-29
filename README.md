# Ansible Role: Accounts

This role to manage user accounts.

* manges sudoers
* manges groups
* manges users
* manages user's private key
* manages user's authorized keys

## Requirements

None.

## Role Variables

```
# Add or remove sudoers
accounts_sudoers: []
#
# accounts_sudoers:
#   # Add the sudoers 'somegroup'
#   - name: somegroup
#     state: present
#     who: "%somegroup"
#     where: "ALL"
#     as_whom: "ALL"
#     what : "NOPASSWD: ALL" 
#   - name: admins
#     state: present
#     who: "%admins"
#     where: "ALL"
#     as_whom: "ALL"
#     what : "NOPASSWD: ALL" 
#   # Remove the sudoers 'somegroup'
#   - name: somegroup
#     state: absent

# Add or remove groups
accounts_groups: []
# @see http://docs.ansible.com/ansible/group_module.html
#
# accounts_groups:
#   # Add the group 'somegroup'
#   - name: somegroup
#   - name: admins
#   - name: developers
#   # Remove the group 'somegroup'
#   - name: somegroup
#     state=absent

# Manage user accounts
accounts_users: []
# @see http://docs.ansible.com/ansible/user_module.html
# @see http://docs.ansible.com/ansible/authorized_key_module.html
#
# accounts_users:
#   # Add the user 'johnd' with a specific uid and a primary group of 'admin'
#   - name: johnd
#     comment: "John Doe"
#     uid: 1040
#     group: admin
#   # Add the user 'james' with a bash shell, appending the group 'admins' and 'developers' to the user's groups
#   - name: james
#     shell: /bin/bash
#     groups:
#       - admins
#       - developers
#     append: yes
#   # Remove the user 'johnd'
#   - name: johnd
#     state: absent
#     remove: yes
#   # Create a 2048-bit SSH key for user jsmith in ~jsmith/.ssh/id_rsa
#   - name: jsmith
#     generate_ssh_key: yes
#     ssh_key_bits: 2048
#     ssh_key_file: .ssh/id_rsa
#   # added a consultant whose account you want to expire
#   - name: james18
#     shell: /bin/zsh
#     groups: developers
#     expires: 1422403387
#   # Adds or removes an SSH authorized key for user charlie in ~charlie/.ssh/authorized_keys
#   - name: charlie
#     authorized_keys:
#       # Example using key data from a local file on the management machine
#       - key: "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
#       # Using github url as key source
#       - key: https://github.com/charlie.keys
#       # Remove the authorized_keys '/home/charlie/.ssh/id_rsa.pub'
#       - key: "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}" state=absent
#       # Using alternate directory locations:
#       - key: "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
#         path: "/etc/ssh/authorized_keys/charlie"
#         manage_dir: no
#       # Using key_options:
#       - key: "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
#         key_options: 'no-port-forwarding,from="10.0.1.1"'
#       # Using validate_certs:
#       - key: https://github.com/user.keys validate_certs=no
#       # Copies the key from the user who is running ansible to the remote machine user ubuntu
#       - key: "{{ lookup('file', lookup('env','HOME') + "/.ssh/id_rsa.pub") }}"
```

## Dependencies

None.

## Example Playbook

```
- hosts: servers
  roles:
     - { role: kotarella1110.accounts }
```

## License

MIT

## Author Information

This role was created in 2016 by Kotaro Sugawara.
