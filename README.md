# localshift
Deploy an OpenShift cluster on Linux locally using Ansible and libvirt.

## Background
As a solution architect at Red Hat, I want to use a real OpenShift cluster on my - [powerful](https://www.msi.com/Laptop/GT75-Titan-9SX) - laptop.

Though there are [minishift](https://github.com/minishift/minishift)/CDK and [crc/CodeReady Containers](https://github.com/code-ready/crc), these approaches miss my needs because they install the entire cluster in one big (libvirt/HyperV/VirtualBox/xhyve) virtual machine.

Minishift furthermore uses ```oc cluster up``` to initialize and run the cluster, whereas ~crc~ is a comprehensive go application.

What I need and like to hack around with is more advanced functionality (affinity pod placement, killing nodes, distributing workload over multiple nodes).

Here's is my try to get an OpenShift cluster running as per the default recommended installation method.

## Plan (as of 2019-09-20)

  1. Create multiple libvirt VMs for later deployment within a usable kvm network and attached libvirt storage.
  1. Run the OpenShift [OpenShift libvirt installer](https://github.com/openshift/installer/blob/master/docs/dev/libvirt/README.md) against these machines.

## Design dreams
Not sure if this can be achieved, but I like to implement 
  
  * Deployment profiles (
    * mini: 1 master, 1 infra, 2 worker; 
    * default: 2 master, 2 infra, 3 worker; 
    * ha: 3 (?) master, 3 (?) infra, 4 worker).
  * Dynamic host naming convention (later)
  * IP range specification

in a way, that the base information can be specified in an external file.

## Giant's shoulder
Links to external articles/projects that could be useful:

### Articles/Documentation

[Bare metal installation of OpenShift (official docs)](https://docs.openshift.com/container-platform/4.1/installing/installing_bare_metal/installing-bare-metal.html)
[Ales Nosek: Installing OpenShift 4.1 Using Libvirt and KVM](http://alesnosek.com/blog/2019/07/08/installing-openshift-4-dot-1-using-libvirt-and-kvm/)

[Red Hat EMEA Services libvirt section for ocp 4](https://github.com/RedHat-EMEA-SSA-Team/hetzner-ocp4#initialize-tools)

https://github.com/jkhelil/openshift-poc/blob/master/openshift-ansible/README_libvirt.md

### Projects
https://github.com/RedHat-EMEA-SSA-Team/hetzner-ocp4

https://github.com/jkhelil/openshift-poc
