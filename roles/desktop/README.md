Ubuntu desktop workstation role
===============================

A basic setup for an Ubuntu (Gnome) Desktop (16.04, maybe others),
geared toward a personal machine used by one user ('main_user').

Requirements
------------

A pre-installed Ubuntu distro.

Role Variables
--------------

In `vars/main.yml`

`main_user `- the usename of the main user of this machine.
`smartgit_version`
`smartgit_checksum`
`crashplan_version`
`jetbrains_toolbox_version`

Dependencies
------------

None known.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
- name: apply common configuration to workstations
  hosts: workstations
  user: root

  roles:
    - common
    - { role: desktop, main_user: perry }
```

License
-------

BSD

Author Information
------------------

ajperry@pansapiens.com
