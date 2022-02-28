---
id: ad4k09849lkib6mnfbe6trm
title: Commands
desc: ''
updated: 1646050554476
created: 1646045591055
---

### General
To access help type `-h` or `--help` after any command, to exit `help`, press `ctrl+c` or `Q`.

#### Create Environment Variables
```bash
export VAR_NAME = <var_value>
```

### Auth

#### List Active Account

```bash
gcloud auth list
```

### Config

#### Get Project Info
```bash
gcloud compute project-info describe --project <your_project_ID>
```

#### View all properties
```bash
gcloud config list --all
```

#### List Active Project ID
```bash
gcloud config list project
```

#### Get Values
Get zone and region:
```bash
gcloud config get-value compute/zone
gcloud config get-value compute/region
```

#### Set Values
```bash
gcloud config set compute/zone us-central1-a
```

### Compute

#### Create new VM
Generate with specific config:
```bash
gcloud compute instances create gcelab2 --machine-type n1-standard-2 --zone us-central1-f
```

- `gcloud compute` allows you to manage your Compute Engine resources in a format that's simpler than the Compute Engine API.

- `instances create` creates a new instance.

- `gcelab2` is the name of the VM.

- The `--machine-type` flag specifies the machine type as `n1-standard-2`.

- The `--zone` flag specifies where the VM is created.

- If you omit the `--zone` flag, the `gcloud` tool can infer your desired zone based on your default properties. Other required instance settings, such as `machine type` and `image`, are set to default values if not specified in the `create` command.

#### SSH into VM
```bash
gcloud compute ssh gcelab2 --zone us-central1-f
```

### gcloud Interactive
Install beta components
```bash
sudo apt-get install google-cloud-sdk
```

Enable interactive mode
```bash
gcloud beta interactive
```

Exist interactive mode
```bash
exit
```

Enable/disable help: `F2`

### Vim
Open a file in vim
```bash
vi ./.file_name
```

Exit vim
```vim
:wq
```