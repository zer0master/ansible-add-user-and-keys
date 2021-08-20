Role Name
=========

This role (maybe) creates a (unix) user and associated keypair, optionally with a passphrase for the private key.

Requirements
------------

None.

Role Variables
--------------

Set the following variables via a mechanism like `host_vars/(hostname)`, your playbook, or the ansible command line:
* `target_user`
* `keypair_files`

Dependencies
------------

None.

Limitations
-----------

Assumes RSA key of 4096 bits, which can/should be defaulted for overriding (someday). Investigation is underway to make keypair retrieval optional (currently to `files/hostname/ssh/`), along with applying the passphrase.

Example Playbook
----------------

Example usage:
```
    - hosts: groupNames  # from inventory
      roles:
         - role: adduser  # or renamed role via requirements.yml
           target_user: somebody
           keypair_files:
            - id_rsa.pub
            - id_rsa
```
License
-------

GPL 2.0

Author Information
------------------

No comment.

Installation
------------

As part of a larger playbook, add the following in `requirements.yml` (`name` can be whatever you prefer):
```
- name: adduser
  src: git+https://github.com/zer0master/ansible-add-user-and-keys.git
  scm: git
```
Then from the base of your repo, install with
```
ansible-galaxy role install -vvvv --role-file requirements.yml --roles-path roles/
```
This assumes a playbook layout with `roles`, `host/group_vars`, and possibly similar first-level folders.
