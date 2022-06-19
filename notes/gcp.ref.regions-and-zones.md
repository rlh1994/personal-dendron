---
id: 6i7j3r80q0yotjhlxcdcw4m
title: Regions and Zones
desc: ''
updated: 1646048742281
created: 1646046013717
---

Certain Compute Engine resources live in regions or zones. A region is a specific geographical location where you can run your resources. Each region has one or more zones. For example, the us-central1 region denotes a region in the Central United States that has zones us-central1-a, us-central1-b, us-central1-c, and us-central1-f.

![](/assets/images/2022-02-28-11-00-27.png)

Resources that live in a zone are referred to as _zonal_ resources. Virtual machine Instances and persistent disks live in a zone. To attach a persistent disk to a virtual machine instance, both resources must be in the same zone. Similarly, if you want to assign a static IP address to an instance, the instance must be in the same region as the static IP.

> Learn more about regions and zones and see a complete list in [Regions & Zones documentation](https://cloud.google.com/compute/docs/regions-zones/).