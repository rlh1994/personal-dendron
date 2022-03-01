---
id: ogdjcy5vjal8tqomfn3c839
title: Firewall Rules
desc: ''
updated: 1646142844186
created: 1646131086676
---

Firewall rules allow you to define what can/can't access the machine or network or cluster you are applying them to. You can view all firewall rules in a project with the usual `gcloud compute firewall-rules list` or more detail on a specific rule with `gcloud compute firewall-rules describe [FIREWALL_RULE_NAME]`

## Apply to a network
To create a firewall rule and apply it to a network you can use the following code:

```bash
gcloud compute firewall-rules create labnet-allow-internal \
	--network=labnet \
	--action=ALLOW \
	--rules=icmp,tcp:22 \
	--source-ranges=0.0.0.0/0
```
which uses.
- `firewall-rules` is a subcategory of `compute`
- `create` is the action you are taking
- `labnet-allow-internal` is the name of the firewall rule
- `--network=labnet` puts the rule in the `labnet` network
- `--action=ALLOW` must be used with the `--rules` flag, and is either "ALLOW" or "DENY"
- `--rules=icmp,tcp:22` specifies the icmp and tcp protocols and the ports that the rule applies to
- `--source-ranges=0.0.0.0/0` specifies the ranges of source IP addresses in CIDR format (in this case internal only)