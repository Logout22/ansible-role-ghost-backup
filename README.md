Ghost Backup
============

[![Build Status](https://travis-ci.org/Logout22/ansible-role-ghost-backup.svg?branch=master)](https://travis-ci.org/Logout22/ansible-role-ghost-backup)

A role to back up a Ghost blog as described on Ghost for Beginners.

Requirements
------------

Ghost needs to be set up and running in a local directory. Right now, only SQLite is supported.

For instructions on how to set up Ghost, consult their excellent [documentation](https://ghost.org/docs/)
or have a look at [Ghost for Beginners](https://www.ghostforbeginners.com/).

Role Variables
--------------

The source directory to back up:

    source_directory: /var/www/ghost

The file name of the backup archive

    destination_file: /var/www/ghost.tar.gz

The user account used for controlling Ghost:

    user_name: ghost

The address of the local Ghost server:

    ghost_address: http://localhost:2368/ghost/

Should Ghost be restarted after backup?
By default, Ghost will be off when the role has finished.
When this option is set, the previous state will be restored.

    restart_after_backup: yes

Warning: Setting this option violates the idempotence
principle: Ghost always modifies its directory
when it is started. Setting `restart_after_backup` will result
in a backup archive which is outdated after the role has finished.
Hence, it will always need updating when the role is run a second time
on the same system.
In order to have this role comply with Ansible standards,
the flag is off by default.

Dependencies
------------

- for tests: `geerlingguy.nodejs`

Example Playbook
----------------

tbd

License
-------

GPL3
