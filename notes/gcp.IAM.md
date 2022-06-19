---
id: q8he59u48ffjdio49k8lzcj
title: IAM
desc: ''
updated: 1646158492167
created: 1646044746241
---

[Cloud Identity and Access Management (IAM)](https://cloud.google.com/iam/) defines roles and permissions across a GCP [[project|gcp.projects]]. These can be as specific as required but there are some _basic_ roles that can be used to give high level sweeping access to most resources within a project:

| Name| Title  | Permissions|
|------------|--------|-----------------------------------------|
| roles/viewer | Viewer | Permissions for read-only actions that do not affect state, such as viewing (but not modifying) existing resources or data. |
| roles/editor| Editor | All viewer permissions, plus permissions for actions that modify state, such as changing existing resources.                |
| roles/owner| Owner  | All Editor permissions and permissions for the following actions: <br> - Manage roles and permissions for a project and all resources within the project. <br> - Set up billing for a project.  |

More details about roles can be found [here](https://cloud.google.com/iam/docs/understanding-roles/).

Cloud IAM grants access to members, members could be any of the following types:
- Google Account
- Service Account
- Google Group
- G Suite domain
- Cloud Identity domain

You grant these members roles. There are three kinds of roles:
- **Primitive roles:** The roles historically available in the Cloud Console will continue to work. These are the Owner, Editor, and Viewer roles.
- **Predefined roles:** Predefined roles are the Cloud IAM roles that give finer-grained access control than the primitive roles. For example, the predefined role Pub/Sub Publisher (roles/pubsub.publisher) provides access to only publish messages to a Cloud Pub/Sub topic.
- **Custom roles:** Roles that you create to tailor permissions to the needs of your organization when predefined roles don't meet your needs.

![](/assets/images/2022-03-01-17-53-39.png)

There are two ways to attach a role to a user:
1. To the user and an organisation
2. To the user and a project

## Service accounts
You have an application that will use the Application Programming Interfaces (APIs) to read and write to Cloud Storage buckets. You don't want to have to authenticate every time you launch a new server, that would be both painful and not in the spirit of using the cloud! So, you will use service accounts.

A service account is a special Google account that belongs to your application or a virtual machine (VM) instead of to an individual end user. Your application uses the service account to call the Google API of a service so that the users aren't directly involved.

## Access Scopes
Access scopes are the legacy method of specifying permissions for your instance. Access scopes are not a security mechanism. Instead, they define the default OAuth scopes used in requests from the gcloud tool or the client libraries. They have no effect when making requests not authenticated through OAuth, such as gRPC or the SignBlob APIs.

You must set up access scopes when you configure an instance to run as a service account.

A best practice is to set the full cloud-platform access scope on the instance, then securely limit the service account's API access with IAM roles.

Access scopes apply on a per-instance basis. You set access scopes when creating an instance and the access scopes persist only for the life of the instance.

Access scopes have no effect if you have not enabled the related API on the project that the service account belongs to. For example, granting an access scope for Cloud Storage on a virtual machine instance allows the instance to call the Cloud Storage API only if you have enabled the Cloud Storage API on the project.