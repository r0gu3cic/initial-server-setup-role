# Role Name

=========

This Ansible role is designed for the initial and secure setup of an Ubuntu server. It configures essential services, sets up a sudo user, and applies basic security measures to ensure the server is ready for production use.

## Requirements

------------

This role is designed to work with Ubuntu distributions. It requires the following:

- Ansible 2.10.8 or higher
- `sshpass` for running the playbook with SSH password authentication.

## Role Variables

------------

The following variables can be configured for this role:

- **`user`**: The name of the sudo user to be created.
- **`user_sudo_password`**: The password for the sudo user.
- **`user_public_key`**: Path to the SSH public key to be added to the sudo user's `~/.ssh/authorized_keys`.
- **`journalctl_max_disk_usage`**: Max disk space that could be used by journal.

These variables can be defined in the playbook or in a `vars` file.

## Dependencies

------------

This role has no dependencies on other roles.

## Example Playbook

------------

```yaml
- hosts: servers
  become: yes
  vars:
    sudo_user: "admin"
    sudo_password: "$6$rounds=656000$saltsalt$xxxx"
    user_public_key: "/home/stefan/.ssh/id_rsa.pub"
    journalctl_max_disk_usage: 1G
  roles:
    - role: your_username.role_name
```

## License

------------

MIT License

## Testing Guide

------------

To run a local test for this role, use the following command:

```bash
ansible-playbook tests/test.yml -i tests/local_inventory.ini -u root -k
```

## Author Information

------------

This role was created by Stefan, aka enabler, aka r0gu3cic. For any inquiries or further information, please reach out via [GitHub](https://github.com/r0gu3cic).
