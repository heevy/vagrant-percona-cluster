vagrant-percona-cluster
=======================

A Vagrant sandbox for testing Percona XtraDB Cluster with Ansible provisioner.

Requirements
------------

* [VirtualBox](https://www.virtualbox.org/)
* [Vagrant](http://vagrantup.com/)
* [Ansible](http://docs.ansible.com/ansible/intro_installation.html)

Usage
-----

```
$ vagrant up
$ ansible-playbook pxc-bootstrap.yml
```

Reference
---------

- [Percona yum Repository](https://www.percona.com/doc/percona-xtradb-cluster/5.5/installation/yum_repo.html)
- [Installing Percona XtraDB Cluster on CentOS](https://www.percona.com/doc/percona-xtradb-cluster/5.5/howtos/centos_howto.html)
- [Manual bug on CentOS Tutorial](https://bugs.launchpad.net/percona-xtradb-cluster/+bug/1354413)
