RSync-Backup-Docker
=========

A role to backup important docker configurations to a remote server using the RSync protocol. 

Requirements
------------

This role installs RSync on the server being backed up, as well as the RSync server if it is not installed.

Role Variables
--------------

Required variables are listed here, along with default values (specific to my environment, see defaults/main.yml).

    rsync_server: rsync.domain.local

This is the RSync server. This needs to be a host in the ansible inventory (I think).

    backup_dir: /opt

This is the local directory to be backed up. Most of my docker configuration data is stored in /opt/docker_name . This backs that up by default.

    backup_storage_dir: /mnt/fileserver/backups

This is the storage location on the RSync server where the data is backed up to. 

Dependencies
------------

None.

Example Playbook
----------------

    - name: Connect the vm to the Media share on my TrueNAS vm.
      hosts: nfs_client_media
      become: true
      vars:
        nfs_mounts:
          - { mnt_path: "/mnt/media", nfs_host: "truenas.plumbus.lab", share_path: "/mnt/Media" }
      roles:
      - role: nfs_client

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/