---
id: jvrhnjfx99u3xi9f5gm7s66
title: Commands
desc: ''
updated: 1646307572109
created: 1646304356707
---

#### Create a bucket
```bash
gsutil mb -c multi_regional gs://${BUCKET}
```

####  List objects
```bash
gsutil ls gs://${BUCKET}/*
```

#### Copy objects
```bash
gsutil -m cp -r endpointslambda gs://${BUCKET}
```
`-m` allows for multi-threaded copying, and `-r` is to recursively copy directories.

#### Synchronise local folder and bucket
```bash
gsutil -m rsync -d -r endpointslambda gs://${BUCKET}/endpointslambda
```
`-d` to delete anything in the bucket not in the local folder.

#### Change access control list
```bash
gsutil -m acl set -R -a public-read gs://${BUCKET}
```
`-a` for all object versions.

#### Copy a file with a different storage class
```bash
gsutil cp -s nearline file_name gs://${BUCKET}
```

#### View object storage classes
```bash
gsutil ls -Lr gs://${BUCKET} | more
```

#### Empty a bucket
```bash
gsutil rm -rf gs://${BUCKET}/*
```

#### Delete a bucket 
```bash
gsutil rm -rf gs://${BUCKET}/*
```