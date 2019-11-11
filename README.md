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

The user account used for controlling Ghost:

    user_name: ghost

Dependencies
------------

- for tests: `geerlingguy.nodejs`

Example Playbook
----------------

tbd

License
-------

GPL3
