### Get the location of a resource group and set it as a variable
`$location = (Get-AzResourceGroup -Name [resource group name]).Location`
### Create new resource group
`New-AzResourceGroup -Name [resource group name] -Location [resource group location/look above]`
### Get a resource group
`Get-AzResourceGroup -Name [resource group name]`
### Create a Disk config
`````
$diskConfig = New-AzDiskConfig `
-Location $location `
-CreateOption Empty `
-DiskSizeGB 32 `
-Sku Standard_LRS
`````
### Create a new disk
```
New-AzDisk `
-ResourceGroupName [resource group name] `
-DiskName [Choose a disk name] `
-Disk $diskConfig
```
### Get a disk
`Get-AzDisk -ResourceGroupName [resource group name] -Name $diskName`
### Update properties on a disk. This updates disk size
`New-AzDiskUpdateCongig -DiskSizeGB 64 | Update-AzDisk -ResourceGroupName [resource group name] -Diskname $diskName`
### Get a property on a disk
`(Get-AzDisk -ResourceGroupName [resource group name] -Name $diskName).[property here. Ex: .Sku]`
