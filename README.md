AdGuard on Fedora CoreOS in VMware with Static IP
===========================================

## Description
------------

The goal of this repository is to provide a simple, reproducible way to deploy AdGuard on a Fedora CoreOS server inside of VMware with Static IPs.

## Quickstart

Start by editing the `group_vars/all.yml` file:

+ Set the vCenter variables
    1. IP/Host Name of vCenter
    2. vCenter Network
    3. Datastore name
    4. Datacenter name
    5. username and passwords of vCenter Account
    6. Absoluate folder path - e.g /DataCenter/vm/Folder/
    7. VM Power state after being deployed

+ Configure your Fedora CoreOS URL and govc version.
    1. To get the URL for VMware ova of the latest stable release of visit this link: [Download Fedora CoreOS](https://getfedora.org/en/coreos/download?tab=metal_virtualized&stream=stable)

+ Configure your AdGuard VM Settings
    1. VM and Host Name
    2. IP Addr, Gateway, Net Mask, DNS
    3. Number of CPUs
    4. Amount of Memory in MB
    5. Size of the HDD in GBs

## Infrastructure Prerequisites

1. vSphere ESXi and vCenter 6.7 or 7.0 installed.
2. A datacenter created with a vSphere host added to it and a datastore exists that has adequate capacity.
3. Ansible (preferably latest) on the machine where this repo is cloned.
    1. Before you install Ansible, install the `epel-release`, run `yum -y install epel-release`

## USAGE

### Run Deploy Playbook
```sh
# Deploy the Lab and all components
ansible-playbook deploy-adguard.yml
```
### deploy-aio-lab.yml Extra Variables

`skip_ova=true` - Skips downloading and deploying the OVA if previous deployed to vCenter.
`redeploy=true` - Deletes existing AdGuard vm

### Expected Outcome

1. Necessary Linux packages installed for the installation
2. Necessary folders [bin, downloads] created
3. govc downloaded and extracted
4. FCOS ova downloaded to the **downloads** folder
5. AdGuard VM is created in the designated folder and (in state of) **poweredon**

AUTHOR
------
Morgan Peterman
