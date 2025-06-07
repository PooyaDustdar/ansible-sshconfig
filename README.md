Role Name
=========

Ansible SSH Config Role (Test Mode)
-----------------------------------

This role provides a complete structure for managing SSH user access using SSH CA, principals, and group-based authorization. It is currently in **test mode** and is designed for demonstration and development purposes only.

Features
--------
- Generates a test CA key and user SSH key pairs automatically.
- Signs user public keys with the CA and sets up SSH certificates.
- Supports detailed user definitions (username, email, multiple groups).
- Manages user grouping (admin, developer [frontend/backend], infra [sysadmins/devops/dbadmins]).
- Ensures admin users are present on all client hosts.
- Configures SSHD to use CA and authorized principals.
- Restricts non-admin users to proxy-only access on gateway hosts.

Requirements
------------
- Ansible 2.9+
- OpenSSH with certificate authentication support

Role Variables
--------------
See `defaults/main.yml` for all configurable variables, including user list, CA key path, and certificate validity.

Inventory Example
-----------------
See `tests/inventory` for a sample inventory with group hierarchy and children.

Example Playbook
----------------
```
- hosts: gateway:client
  become: true
  roles:
    - ansible-sshconfig
```

Limitations
-----------
- This role is in **test mode**: it generates and uses test CA and user keys on localhost.
- Do not use in production without proper review and adaptation.

License
-------
BSD

Author Information
------------------
Pooya Dustdar (github.com/PooyaDustdar)
