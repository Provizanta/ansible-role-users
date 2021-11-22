Ansible role: users
=========

![main Build status](https://github.com/Provizanta/ansible-role-users/actions/workflows/main.yml/badge.svg)

Setup users idempotently. The current configuration is the source of truth. Any users not present will be set up, any users not present will be removed.

By default at least 1 superuser has to be present inside the user list.

Requirements
------------

None

Role Variables
--------------

These variables are defined in [defaults/main.yml](./defaults/main.yml):

    users_list: []
    # - name: str
    #   pass: str             # default(omit)
    #   ssh_pubkey: str       # default(omit)
    #   shell: str            # default(users_shell)
    #   groups: list          # default([])
    #   create_home: bool     # default(users_create_home)

    users_password_hash: 'sha512'

    users_shell: '/usr/bin/bash/'

    users_create_home: true

    users_use_passwordless_sudo: true

    users_append_groups: false

    users_require_superuser: true

Dependencies
------------

None

Example Playbook
----------------

    - hosts: localhost
      roles:
        - role: users
          vars:
            users_list:
              - name: abc
                pass: abc
              - name: def
                ssh_pubkey: "ecdsa-sha2-nistp521 AAAAE2VjZHNhdXNoYTItbmlzdHA1MjEB\
                CDEIbmlzdHA1MjEAAACFBACJbg5bryhqXcYAzJdWm1NC+\
                7XaF7SDo5pXGIDhCu2dfKV6BkeeSvA6l96f20DzleRVez\
                ji8Swcq5LsfCuiLw1SHAAO59vK6iroMfMzJl8ZaSt1Uo41\
                09XezVl7aIJ9bO0IamXkFXa4S65WON3c7s2WinRk2skcb\
                miOkD55uS44vhPHNA=="
              - name: ghi
                pass: ghi
                shell: /bin/sh
              - name: jkl
                ssh_pubkey: "ecdsa-sha2-nistp521 AAAAE2VjZHNhdXNoYTItbmlzdHA1MjEB\
                CDEIbmlzdHA1MjEAAACFBACJbg5bryhqXcYAzJdWm1NC+\
                7XaF7SDo5pXGIDhCu2dfKV6BkeeSvA6l96f20DzleRVez\
                ji8Swcq5LsfCuiLw1SHAAO59vK6iroMfMzJl8ZaSt1Uo41\
                09XezVl7aIJ9bO0IamXkFXa4S65WON3c7s2WinRk2skcb\
                miOkD55uS44vhPHNA=="
                groups:
                  - root
              - name: mno
                pass: mno
                create_home: false

License
-------

MIT

Author Information
------------------

Tibor Csóka
