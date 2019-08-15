# ansible-proxmox-config

## Summary

Ansible playbook to configure freshly installed Proxmox (PVE) (v6.0.1) node(s) for lab environment (somewhat customized for mine), and prep for further Ansible automation. Will install required packages, customize host network config, and enable (Intel) [nested virtualization](https://pve.proxmox.com/wiki/Nested_Virtualization) (for testing Hyper-V, VMWare, etc on Proxmox).


## Requirements

- Install Proxmox on each desired node
- Modify hosts in inventory as appropriate
- Modify vars (packages & IPs) in Ansible playbook as appropriate. 
- Confirm interfaces template will result in desired networking setup (here set for 4 NICs/node, creating 2 bonds, 1 bridge). See [Proxmox Network Config](https://pve.proxmox.com/wiki/Network_Configuration)
- Run Ansible playbook
- Manually create PVE Cluster on single node, join the remaining nodes to cluster
- Manually configure data storage

## Usage

`ansible-playbook -i inventory --ask-pass proxmox-config.yml`

- or to limit to specific host

`ansible-playbook -i inventory -l 192.168.2.31 --ask-pass proxmox-config.yml`

* Provide the root password setup during Proxmox installation

## To-Do

 - [ ] Add cluster setup automation
 - [ ] Add data storage setup (RAID via MDADM) automation
 
## Credit:

Partially based off of https://www.nathancurry.com/blog/14-ansible-deployment-with-proxmox/