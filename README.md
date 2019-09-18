# localshift
Deploy an OpenShift cluster on Linux locally using Ansible and libvirt.

## Background
As a solution architect for Red Hat, I want to use a real OpenShift cluster on my - [powerful](https://www.msi.com/Laptop/GT75-Titan-9SX) - laptop.

Though there are [minishift](https://github.com/minishift/minishift)/CDK and [crc/CodeReady Containers](https://github.com/code-ready/crc), these approaches miss my needs because they install the entire cluster in one big (libvirt/HyperV/VirtualBox/xhyve) virtual machine.

Minishift furthermore uses ```oc cluster up``` to initialize and run the cluster, whereas ~crc~ is a comprehensive go application.

But I like also show more advanced functionality (affinity pod placement, killing nodes, distributing workload over multiple nodes).

Here's is my try to get an OpenShift cluster running as per the default recommended installation method.
