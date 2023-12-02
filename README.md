# Kubernetes The Hard Way in Ansible

*Kubernetes The Hard Way in Ansible* is a collection of Ansible playbooks which deploy a Kubernetes cluster made by 2 master 1 load balancer and 2 worker. This playbook is an ansible transposition of the
project [Kubernetes The Hard Way](https://github.com/mmumshad/kubernetes-the-hard-way/tree/master).

## Prerequisites

* 5 hosts, VMs or bare metal with Ubuntu 22.02\*.
* hosts needs to have static IPs. The IPs can be found in the [`group_vars/k8s`](./group_vars/k8s.yml). Check the [Kubernetes The Hard Way](https://github.com/mmumshad/kubernetes-the-hard-way/blob/master/docs/02-compute-resources.md) for more info.
* the hosts must already have a user with `sudo` and `NO PASSWD` privileges. The user will execute the ansible playbook.   

*Probably most of Debian based distro would work. The playbook needs to be adapted to other distros.

## Usage

To deploy the cluster:
```bash
ansible-playbook -i inventory/inventory.yaml k8s_main.yml
```

The `k8s_main.yml` playbook is a collection of playbooks. A partial playbook can be executed:
```bash
ansible-playbook -i inventory/inventory.yaml k8s_basic.yml
```

The hosts IPs might be changed in the [`group_vars/k8s`](./group_vars/k8s.yml) file. However, different IPs have not been tested. The host name cannot be changed, the roles would need to be modified to work correctly

## Future steps

* Remove the shell based role in the last two playbook and find a way to make them idempotent
* Adapt the playbook to RHEL based distros
