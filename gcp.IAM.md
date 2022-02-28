---
id: q8he59u48ffjdio49k8lzcj
title: IAM
desc: ''
updated: 1646045298617
created: 1646044746241
---

[Cloud Identity and Access Management (IAM)](https://cloud.google.com/iam/) defines roles and permissions across a GCP [[project|gcp.projects]]. These can be as specific as required but there are some _basic_ roles that can be used to give high level sweeping access to most resources within a project:

| Name| Title  | Permissions|
|------------|--------|-----------------------------------------|
| roles/viewer | Viewer | Permissions for read-only actions that do not affect state, such as viewing (but not modifying) existing resources or data. |
| roles/editor| Editor | All viewer permissions, plus permissions for actions that modify state, such as changing existing resources.                |
| roles/owner| Owner  | All Editor permissions and permissions for the following actions: <br> - Manage roles and permissions for a project and all resources within the project. <br> - Set up billing for a project.  |

More details about roles can be found [here](https://cloud.google.com/iam/docs/understanding-roles/).