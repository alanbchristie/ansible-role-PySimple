Role Name
=========

A Role for the installation of the PySimple application into a Kubernetes
(or OpenShift) cluster.

Requirements
------------

-   Kubernetes or OpenShift 

Role Variables
--------------

See [defaults/main.yml](defaults/main.yml).

Dependencies
------------

-   (none)

Example Playbook
----------------

**NOTE** The example below assumes that you have a running Kubernetes|OpenShift
cluster and that you have sufficient permissions in the
`pysimple` namespace.

    - hosts: servers
      tasks:
      - include_role:
          name: alanbchristie.pysimple
        vars:
          image_tag: '2019.1'

License
-------

MIT License

Author Information
------------------

alanbchristie
