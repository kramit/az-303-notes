Azure VM Comparison
https://azureprice.net/


Inside Azure Datacenters with Mark Russinovich: Part 1 | Ignite 2020
https://www.youtube.com/watch?v=v990MJXuj8Q
Inside Azure Servers with Mark Russinovich: Part 2 | Ignite 2020
https://www.youtube.com/watch?v=bV2Rb_LJRQ4


An introduction to Azure Dedicated Hosts | Azure Friday
https://www.youtube.com/watch?v=5qegfWl5woo


Vsphere in Azure
https://www.youtube.com/watch?v=-yLgduCVPRk

https://azure.microsoft.com/en-us/services/azure-vmware/

Azure Disk Encryption (requires a keyvault)
https://docs.microsoft.com/en-us/azure/virtual-machines/windows/disk-encryption-portal-quickstart#:~:text=%20Quickstart%3A%20Create%20and%20encrypt%20a%20Windows%20virtual,resource.%20On%20the%20left-hand%20sidebar%2C%20select...%20More%20


Pricing and types
https://azure.microsoft.com/en-gb/pricing/details/virtual-machines/series/

List Image publishers in a region

Get-AzureRmVMImagePublisher -Location westeurope | select publishername | fw -column 5

List images offered by Microsoft

Get-AzVMImageOffer -Location westeurope -PublisherName Microsoftwindowsserver

Making a VM in Powershell

New-AzResourceGroup -Name myResourceGroup -Location EastUS

New-AzVm -ResourceGroupName "myResourceGroup" -Name "myVM" -Location "East US" -VirtualNetworkName "myVnet" -SubnetName "mySubnet" -SecurityGroupName "myNetworkSecurityGroup" -PublicIpAddressName "myPublicIpAddress" -OpenPorts 80,3389

AutoScale and Scalesets
Virtical +- Power to vms Horizonal +- VM count with loadbalancer infront

Deploy a VM and turn on autoscales from the portal

Scale set demo

https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-portal

Powershell DSC docs

https://docs.microsoft.com/en-gb/powershell/dsc/overview/overview