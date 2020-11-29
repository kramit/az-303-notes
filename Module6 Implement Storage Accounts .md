Module 3 Notes
Storage
v1 v2 differences table

https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview#recommendations

Storage Exporer Download

https://azure.microsoft.com/en-gb/features/storage-explorer/

Blobs and Files
BLOB = Binary Large Object

List all Object in a BLOB

https://docs.microsoft.com/en-us/rest/api/storageservices/list-blobs

Blobs access by URL

Use storage explorer to show blobs, with files talk about azure file sync as a dropbox/gdrive/onedrive for servers in a cache and sync model.

https://docs.microsoft.com/en-us/azure/storage/files/storage-sync-files-deployment-guide?tabs=azure-portal

Map a file store from azure to a mapped drive

Table storage
noSQL table storage in the cloud

https://docs.microsoft.com/en-us/azure/cosmos-db/table-storage-overview

Add data to Azure table storage via PS

https://docs.microsoft.com/en-us/azure/storage/tables/table-storage-how-to-use-powershell

There is a PS1 script to add data to an azure table in this GitHub folder

```
# Azure Table storage powershell script to add data to a table

# Step 1, Set variables
# Enter Table Storage location data 
$storageAccountName = '<Enter Storage Account Here>'
$tableName = '<Enter Table Name Here>'
$sasToken = '<Enter SAS Token Here>'
$dateTime = get-date
$partitionKey = 'ComputerPerfData'
$processes = @()

# Step 2, Connect to Azure Table Storage
$storageCtx = New-AzureStorageContext -StorageAccountName $storageAccountName -SasToken $sasToken
$table = Get-AzureStorageTable -Name $tableName -Context $storageCtx

# Step 3, get the data 
$processes = get-process | Sort-Object CPU -descending | select-object -first 10

foreach ($process in $processes) {
 Add-StorageTableRow -table $table -partitionKey $partitionKey -rowKey ([guid]::NewGuid().tostring()) -property @{
 'Time' = $dateTime.ToString("yyyymmdd:hhmmss")
 'ProcessName' = $process.Name
 'ID' = $process.Id
 'CPUTime' = $process.TotalProcessorTime.Minutes
 'Memory' = $process.WS 
 } | Out-Null
}
```
