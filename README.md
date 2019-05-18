# microk8s test project

While trying to figure out the ins and outs of kubernetes, I ran into microk8s.
This is a Canonical project for running a single host kubernetes "cluster" which can be
used for development and testing with kubernetes.

I've added a Vagrantfile, so the installation can easily be set up locally.

## Setting up

Steps to setup the microk8s cluster:

1. Install [vagrant](https://www.vagrantup.com/)
1. Clone this repo
1. Start the VM: `vagrant up`
1. ssh into the VM: `vagrant ssh`
1. dump the configuration: `microk8s.kubectl config view --raw`

The last command will dump the default kubernetes configuration to stdout.
On your local machine (this outside the VM) you can configure this in \${HOME}/.kube/config. If this file doesn't exist, you can just create it.
If it does exist, you need to merge it to be able to connect to the cluster.

Also, the dumped config points to https://127.0.0.1:16443 for the kubernetes API. As you'll want to contact kubernetes from outside the VM, replace 127.0.0.1 with 192.168.34.10. This is the default IP configured in the host only network in Vagrantfile.
