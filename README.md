# Azure SAS Token Exposure Demo

This repository demonstrates how an improperly configured Azure SAS Token can expose sensitive data in an Azure Storage Account.

## Exposed SAS URL
The following SAS URL grants full access to the storage account, including listing containers, enumerating blobs, and downloading files:

https://storageaccountdemopre.blob.core.windows.net/?comp=list&sv=2022-11-02&ss=bfqt&srt=sco&sp=rwdlacupiytfx&se=2025-02-28T21:40:59Z&st=2025-01-28T13:40:59Z&spr=https&sig=h2duBPllGCee29Y89vd%2FZxVxfeE8Gic4GVKv082au4Y%3D


## Steps to Reproduce

### 1. List All Containers
Use the SAS URL to list all containers in the storage account:
```bash
https://storageaccountdemopre.blob.core.windows.net/?comp=list&sv=2022-11-02&ss=bfqt&srt=sco&sp=rwdlacupiytfx&se=2025-02-28T21:40:59Z&st=2025-01-28T13:40:59Z&spr=https&sig=h2duBPllGCee29Y89vd%2FZxVxfeE8Gic4GVKv082au4Y%3D
```

### 2. List Blobs in Container

Using the name of the private container demo-container, list the blobs it contains:
```bash 
https://storageaccountdemopre.blob.core.windows.net/demo-container?restype=container&comp=list&sv=2022-11-02&ss=bfqt&srt=sco&sp=rwdlacupiytfx&se=2025-02-28T21:40:59Z&st=2025-01-28T13:40:59Z&spr=https&sig=h2duBPllGCee29Y89vd%2FZxVxfeE8Gic4GVKv082au4Y%3D
```

### 3. Download the Files in the container

```bash
https://storageaccountdemopre.blob.core.windows.net/demo-container/accesskeys.txt?sv=2022-11-02&ss=bfqt&srt=sco&sp=rwdlacupiytfx&se=2025-02-28T21:40:59Z&st=2025-01-28T13:40:59Z&spr=https&sig=h2duBPllGCee29Y89vd%2FZxVxfeE8Gic4GVKv082au4Y%3D
```
