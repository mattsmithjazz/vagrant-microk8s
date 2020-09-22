# vagrant-microk8s
Ansible automated two-node microk8s cluster on Vagrant

This project is largely inspired by the tutorial here ... https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/

Requirements: Ansible, Vagrant, and Virtualbox
              
I only configured this for two nodes, since pods are schedulable on the master node by default.

This works with https://kubesail.com, an awesome tool if you haven't checked it out!
