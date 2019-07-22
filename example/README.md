# Deploying the role

Initial preparation consists of installing Ansible and
dependent modules (probably into a Python virtual environment).

    $ pip install -r requirements.txt
    $ ansible-galaxy install -r requirements.yml

>   You probably need a VM like [VirualBox] (tested with v6.0.8) for
    MiniKube and MiniShift.

## Deploying to MiniKube

Ensure [Minikube] is running...

    $ minikube start --cpus 4 --memory 8192 --disk-size 40g \
        --kubernetes-version v1.15.0 \
        --vm-driver virtualbox

>   Tested using Minikube v1.2.0 and Kubernetes v1.15.0

and then to deploy via the ansible playbook (where you may need
to provide the location of your Python installation)...

    $ ansible-playbook site.yml -e ansible_python_interpreter=???

and un-deploy...

    $ ansible-playbook site.yml  -e ansible_python_interpreter=??? \
        -e state=absent

## Deploying to MiniShift

Ensure [MiniShift] is running and a project exists: -

    $ minishift start --cpus 4 --memory 8GB --disk-size 40GB \
        --openshift-version 3.11.0 \
        --vm-driver virtualbox
    $ eval $(minishift oc-env)
    $ oc new-project pysimple

>   Tested using Minishift v1.34.0 and OpenShifft v3.11

and then to deploy via the ansible playbook (where you may need
to provide the location of your Python installation)...

    $ ansible-playbook site.yml -e ansible_python_interpreter=???

and un-deploy playbook...

    $ ansible-playbook site.yml -e ansible_python_interpreter=??? \
        -e state=absent

## Deploying to PiKs

Ensuring your [PiKs] cluster is running: -

    $ export KUBECONFIG=/Users/alan/.kube/k3s.yaml

and then to deploy via the ansible playbook (where you may need
to provide the location of your Python installation)...

    $ ansible-playbook site.yml -e ansible_python_interpreter=??? \
        -e image_tag=arm2v7-latest

and un-deploy...

    $ ansible-playbook site.yml -e ansible_python_interpreter=??? \
        -e image_tag=arm2v7-latest \
        -e state=absent
    
---

[minikube]: https://kubernetes.io/docs/tutorials/hello-minikube
[minishift]: https://github.com/minishift/minishift
[piks]: https://gitlab.com/a.b.christie/piks
[virtualbox]: https://www.virtualbox.org
