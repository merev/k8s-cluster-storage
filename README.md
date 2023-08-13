# Kubernetes Cluster Deployment Guide

Welcome to the automated deployment solution for a Kubernetes (K8S) cluster with integrated NFS Storage. This solution employs `kubeadm` and Vagrant for cluster creation. To proceed, kindly follow these steps:

 - Clone the repository containing the necessary resources.
 - Open the directory within your terminal application.
 - Execute the command `vagrant up` to initiate the deployment process.
 - Wait until the cluster initialization process is completed.

Should you desire to install a different Kubernetes version, you can achieve this by modifying the `box_version` settings within the Vagrantfile. Available box versions are accessible at: https://app.vagrantup.com/merev/boxes/k8s-node

#### System Requirements:

For a seamless experience, ensure your computing device (laptop or PC) meets the following specifications:

 - RAM: 8 GB or more
 - Disk Space: 80 GB or more
 - CPU: Intel/AMD x64 with virtualization support

Furthermore, the following software is essential for the deployment process:

 - VirtualBox 6.1+: https://www.virtualbox.org/wiki/Downloads
 - Vagrant 2.1+: https://developer.hashicorp.com/vagrant/downloads

## Cluster Details:

Every node within the cluster is established using the same Vagrant box (*merev/k8s-node*). Comprehensive details regarding this box are available here: https://app.vagrantup.com/merev/boxes/k8s-node

### Node Information:

All nodes operate on the Debian 11 operating system. Each node boasts the following specifications:

 - 2 GB RAM
 - 2 CPUs
 - 60 GB disk space

It is pertinent to note that these hardware parameters can be adjusted before provisioning by configuring the `config.vm.provider` section in the Vagrantfile. Each node has two network interfaces:

 - 1 NIC in NAT Mode: Connected to the host machine
 - 1 NIC in Bridge Mode: Connected to the local network (Cluster Network)

The second NIC (Bridge mode) is assigned a static IP address within the local network. Please remember to replace the IPs with addresses pertinent to your network, both in the initial configuration scripts and the Vagrantfile.

#### Security Note:

The network configuration described above introduces security vulnerabilities and is strongly discouraged for production environments. However, it can be employed for testing, home-based exercises, or scenarios involving a standard laptop.

For comprehensive software details, refer to the box specification.

### Storage Information:

The NFS Server, an integral part of the network, shares the same parameters as the other VMs. It's equipped with NFS-server functionality and includes a shared directory accessible via the Cluster Network.

### Initial Configuration:

The initial cluster configuration encompasses the following steps:

 - Control Plane Initialization
 - Network Plugin Installation
 - Addition of Worker Nodes
 - Storage Configuration

Optional additional configuration steps include:

 - Deploying the K8s Dashboard
 - Setting up a 2-component test application (consumer-producer app)

To enable the additional configuration, simply uncomment rows 54 and 55 within the Vagrantfile.