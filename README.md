AutoFS Role
=========

A role setting up autofs configuration on a debian linux box

The role creates the general configuration file (auto.master) and a file for each box containing
all the mountpoints in this file.

Requirements
------------
none

Role Variables
--------------

box - the box definition like:

```yaml
        boxes:
          - box: fb.local
            name: fotobook
            folder: /mnt/fotobook
            fstype: nfs4
            options: "--timeout 15 browse"
            mountpoints:
            - source: fotos
              target: Bilder
            - source: shares
              target: share
            - source: library
              target: Buecher
              mods: r 
          - box: nas.local
            name: nas
            fstype: nfs4
            mountpoints:
            - source: backup
              target: Sicherung
```

Dependencies
------------

none

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
    - hosts: servers
      roles:
         -role: chof.autofs
          vars:
            boxes:
            - box: fb.local
              name: fotobook
              folder: /mnt/fotobook
              fstype: nfs4
              options: "--timeout 15 browse"
              mountpoints:
              - source: fotos
                target: Bilder
              - source: shares
                target: share
```
License
-------

BSD

Author
------

Christian https://github.com/chof747