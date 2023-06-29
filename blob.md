# Blob Storage



## What is blob storage?
![blob](https://dev.co/wp-content/uploads/2021/05/What-is-Blob-Storage.jpg)
Azure Blob Storage is a cloud storage system for storing massive amounts of unstructured data.

## What is the difference between blob storage and the file system of Linux/Windows/Mac (hierachical file storage)
Blob storage is fir unstructurad data, so it is not organised like files in a file system.

## What are the advantages/disadvantages of blob storage?
### Advantages
Blob storage capacity is practically unlimited and as the amount of stored data grows, it remains easy and fast to save data for later retrieval.

### Sources
<https://dev.co/azure/guide>

## Blob Storage Setup
`az login` to open browser window to login.

Once logged in, on Girbash it has login details in JSON.

Once logged in, need to create storage account.

```
az storage account create --name tech241deannestorage --resource-group tech241 --location uksouth --sku Standard_LRS
```

List all storage accounts in resource group
```
az storage account list --resource-group tech241
```

List them in a clearer way
```
az storage account list --resource-group tech241 --query "[].{Name:name, Location:location, Kind:kind}" --output table
```
The name, location and kind is listed in a table.

Creating a container
```
az storage container create  --account-name tech241deannestorage  --name testcontainer
```
Storage blob upload
```
az storage blob upload  --account-name tech241deannestorage  --container-name testcontainer  --name newname.txt  --file test.txt  --auth-mode login
```
`file` is the name of the file on the computer. `name` is the name given to the file when we upload it.

### Check the blob is in a container.
```
az storage blob list  --account-name tech241deannestorage  --container-name testcontainer  --output table  --auth-mode login
```
### Make blob private
Go to Azure

-> Storage Accounts

-> Own Storage account

-> Containers

-> Test container

-> Uploaded file

-> The file URL

When the URL is pasted into the browser, it's already private! 🤯

### Make blob public

