Ansible Role - alanbchristie.pysimple
=====================================

A Role for the installation of the PySimple application into a Kubernetes
(or OpenShift) cluster.

Requirements
------------

-   Kubernetes or OpenShift 

Role Variables
--------------

    # The container image reference,
    # the default is the author's image on Docker Hub.
    image: docker.io/alanbchristie/pysimple
    
    # The image tag, typically 'latest'.
    # Alternative tags include '2019.3' and,
    # for ARM-based deployments, 'arm32v7-latest'
    image_tag: 2019.5

    # The PySimple Kubernetes Ingress host domain.
    # This sets the host domain in the ingress rule.
    # Using the default the ingress host will be empty
    ingress_host:

    # The ingress certificate issuer (cert-manager)
    ingress_issuer: acme-production

    # The ingress class
    ingress_issuer: nginx

    # Add a persistent volume to the deployment?
    # If so, what storage class?
    use_persistent_volume: no
    volume_class: longhorn

    # Pod Security Policy
    # Blank to avoid deploying roles and role-bindings
    psp: ''

    # To uninstall from the cluster
    # state: absent
    state: present
    
    # The size of the deployment
    size: 1

Dependencies
------------

-   (none)

Example Playbook
----------------

**NOTE** The example below assumes that you have a running Kubernetes|OpenShift
cluster and that you have sufficient permissions in the `pysimple` namespace.

    - hosts: servers
      tasks:
      - include_role:
          name: alanbchristie.pysimple
        vars:
          image_tag: '2019.3'
          use_persistent_volume: yes
          volume_class: ebs

License
-------

MIT License

Author Information
------------------

alanbchristie
