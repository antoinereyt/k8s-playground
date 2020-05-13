# k8s playground

Experiment what I learned in an Udemy course about k8s.

The final goal is to deploy a CI/CD, to be able to deploy stateful distributed apps.

## Setup

I will use my old HP proliant ml350-G6 for this. The server runs an EXSi server.

Specs:
 * 2x Xeon E5504
 * 32Gb RAM
 * 6x360Gb SAS 15k

This server have the following VMs:

| Hostname    | vCPU | RAM |   HDD | Description                           |
|-------------|-----:|-----|------:|---------------------------------------|
| k8s-master  |    2 | 6Gb |  32Gb | k8s master node                       |
| k8s-worker1 |    2 | 6Gb |  32Gb | k8s worker node                       |
| k8s-worker2 |    2 | 6Gb |  32Gb | k8s worker node                       |
| nfs-storage |    1 | 4Gb | 200Gb | NFS server for the persistant storage |

All the VMs are on Ubuntu server 18.04

## Install k8s

Based on this this [tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-18-04#step-1-%E2%80%94-installing-ansible)

To make it compatible with kubernetes 1.18, I changed a few things:
 * upgrade the kubectl, kubeadm and kubelet version to 1.18
 * disable the swap
 * update the CNI (Flannel) resource url

TODO:
 * [ ] - add a vm with an NFS server for the persistant storage