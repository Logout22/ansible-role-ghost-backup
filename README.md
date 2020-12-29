Ghost Backup
============

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

The file name of the backup archive:

    destination_file: /var/www/ghost.tar.gz

The user account used for controlling Ghost:

    user_name: ghost

The address of the local Ghost server:

    ghost_address: http://localhost:2368/ghost/

Enable upload of archive to AWS S3 bucket:

    aws_s3_upload_enabled: no

Optional: AWS S3 credentials used for upload:

    aws_s3_upload_bucket_name: ""
    aws_access_key: ""
    aws_secret_key: ""

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

For AWS upload to work,
make sure that Python and pip are installed on your hosts.

    ---
    - hosts: all
      roles:
      - role: ansible-role-ghost-backup
        destination_file: /home/ubuntu/ghost.tar.gz
        user_name: ubuntu
        aws_s3_upload_enabled: yes
        aws_s3_upload_bucket_name: "my-bucket-for-backup"

Invoke this playbook passing your AWS key and secret key:

    ansible-playbook -e aws_access_key=$AWS_ACCESS_KEY_ID -e aws_secret_key=$AWS_SECRET_ACCESS_KEY playbook.yml

License
-------

GPL3
