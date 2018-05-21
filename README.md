# DevOps kick-start platform

This repo contains a few basic helper scripts to install Vagrant & Virtualbox on a local laptop or desktop computer. Once installed, Vagrant can then be used to launch a Virtualbox instance with some standard DevOps tooling (provisioned via Ansible). The Vagrantfile for this is included in this repository. A basic Ansible playbook is used to provision the vagrant box with a set of tools required to bootstrap your ICT eco-system.

The deployed virtual machine acts as a staring point from which further infrastructure / services can be deployed in an agnostic way, while limiting the number of dependencies on the host OS.

Its purpose is to address the "chicken / egg" problem for rolling out core services such as DHCP / LDAP / DNS / Proxies / Firewalls / PXE / TFTP or basic infrastructure resources like logical networking / ESXI / OpenStack / Openshift / Kubernetes etc. whether local or in the cloud. While one might be tempted to leave the deployment of these basic building blocks to manual intervention, this is certainly not the DevOps way.

### The Tooling:

* Git for checking out your publicly hosted repositories required to drive further automation
* Terraform for deploying infrastructure
* Ansible for configuring hosts
* Packer for packaging appliances, binaries, templates, container images, AMI's and other early stage deployable artifacts.
* Google Cloud / Azure / AWS SDK's for interacting with common cloud providers
* Helm for managing Kubernetes charts
* Docker engine / Docker compose for local testing of containers
* GOVC CLI for interacting with VMWare/vSphere API's

When following strict "infrastructure as code" and "configuration as code" practices, the kick-start platform should be used in tandem with a set of well developed, external repositories to effectively build out the ICT infrastructure of even the most complex and distributed organizations.

Once core-services and infrastructure has been rolled out, it may be appropriate to abandon it's usage. Instead it may make more sense to leverage a central automation server such as Ansible Tower, Foreman or a DIY solution making use of something like Jenkins perhaps.

### Install Dependencies (Vagrant / Virtualbox):

#### Windows:
```
cd <this-repo-location>\dependencies\windows
install.ps1
```
#### Mac:
```
cd <this-repo-location>/dependencies/windows
install.sh
```
#### Ubuntu/Debian:
```
cd <this-repo-location>/dependencies/windows
install.sh
```

### Launch the box (All platforms)
```
cd <this-repo-location>
vagrant up
```

#### To SSH into the box
```
vagrant ssh
```
