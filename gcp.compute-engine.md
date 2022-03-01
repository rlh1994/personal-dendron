---
id: aridxhn7e3q62gmfne0suti
title: Compute Engine
desc: ''
updated: 1646142845352
created: 1646045282346
---

> Compute Engine lets you create virtual machines that run different operating systems, including multiple flavours of Linux (Debian, Ubuntu, Suse, Red Hat, CoreOS) and Windows Server, on Google infrastructure. You can run thousands of virtual CPUs on a system that is designed to be fast and to offer strong consistency of performance.

# VM Instances
Virtual Machines are great tools to be able to develop on and host various things such as websites; they can scale as required (within reason) and are easy to set up. To set one up in Compute Engine:

1. In the Cloud Console, on the `Navigation menu`, click `Compute Engine` > `VM Instances`.
2. Click `CREATE INSTANCE`.
3. There are many options you can provide here, here are some common ones:

    | Field | Additional Information |
    |-------|------------------------|
    | Name | Name for the VM instance |
    | Region | For more information about regions, see [[Regions and Zones|gcp.ref.regions-and-zones]].   |
    | Zone | Note: Remember the zone that you selected: you'll need it later. For more information about zones, see [[Regions and Zones|gcp.ref.regions-and-zones]]  |
    | Series | Name of the series|
    | Machine Type | This is an (n1-standard-2), 2-CPU, 7.5GB RAM instance. Several machine types are available, ranging from micro instance types to 32-core/208GB RAM instance types. For more information, see [Machine Types](https://cloud.google.com/compute/docs/machine-types). _(Note: A new project has a default [resource quota](https://cloud.google.com/compute/quotas), which may limit the number of CPU cores.)_ |
    | Boot Disk | Several images are available, including Debian, Ubuntu, CoreOS, and premium images such as Red Hat Enterprise Linux and Windows Server. For more information, see Operating System documentation.|
    | Firewall |Select the `Allow HTTP Traffic` option in order to access a web server _(Note: This will automatically create a firewall rule to allow HTTP traffic on port 80.)_ |
4. Click `Create`.
5. To use SSH to connect to the virtual machine, in the row for your machine, click SSH. This launches an SSH client directly from your browser.
![](/assets/images/2022-02-28-11-12-07.png)

# Virtual Private Networks

Virtual Private Networks (VPCs) are global resources that are made up of a list of regional virtual subnetworks (subnets) such as VMs, that are all connected by a global wide area network (WAN). 

In a GCP project you can create an `auto mode` or `custom mode` VPC network. Each network must have a unique name in the project and you can have 4 additional networks (plus the default) in a project.  Auto networks include default rules, custom networks do not include any firewall rules. 

Creating a custom mode network called `labnet` can be done with the following code. 
```bash
gcloud compute networks create labnet --subnet-mode=custom
```

A subnetwork must have a unique name per project per region (must be different across all networks). Each subnet must have a primary range (the range of internal IPs that define the subnet)

Creating a subnet named `labnet-sub` can be done with the following code.
```bash
gcloud compute networks subnets create labnet-sub \
   --network labnet \
   --region us-central1 \
   --range 10.0.0.0/28
```

You can list all networks with the usual style command `gcloud compute networks list` and can get more details using `gcloud compute networks describe NETWORK_NAME`. Add `subnets` after networks for information about the subnets.

