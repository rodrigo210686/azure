## Storage options
###A. Blob Storage:
1-Archive is supported in Blob Storage and General Purpose v2 (GPv2) accounts. Only storage accounts that are configured for LRS, GRS, or RA-GRS support moving blobs to the archive tier.
2-Import supports Azure Blob storage and Azure File storage
3 -Export supports Azure Blob storage
4-support Lifecycle management policies. Lifecycle management policies are supported for block blobs and append blobs in general-purpose v2, premium block blob, and Blob Storage accounts.
5-Object Replication supports General Purpose V2 and Premium Blob accounts.
6-Support both Azure (AD) and SAS (Shared Access Signature) token.
7-Support conditions when added to built-in or custom role assignments that have blob storage or queue storage data actions
8-Encryption scopes support a container or an individual blob
9-Not Support ZRS
10-az support
11-support stored access policies
12-Tieing is supporting only or block blobs
13-Flow logging for Blob Storage accounts has a retention period of 30 days. General Purpose v2 (GPv2) storage accounts instead, which support flow logging with a retention period of up to 365 days.

###B.File storage:
1-az support
2-Support persistent storage.
3-File share Supports Premium file shares (FileStorage), Premium LRS/ZRS for SMB Multichannel
4-File Storage: Only Shared Access Signature (SAS) token is supported.
5-Only Shared Access Signature (SAS)
6-Premium file shares
6-Import supports Azure Blob storage and Azure File storage
7-supports identity-based authentication over Server Message Block (SMB) through on-premises Active Directory Domain Services (AD DS) and Azure Active Directory Domain Services (Azure AD DS).
8-Not support archive
9-Not support condition
10-No support Object Replication
11-No support Lifecycle management policies
12-no support encryption scope

## Storage type
![image](https://github.com/rodrigo210686/azure/assets/59710101/e717fa6c-fda9-4d87-a4ed-8b7fce6401d7)


## Consultar roles
https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#logic-app-contributor

## Login AZ CLI
```ps
az login --use-device-code

ou

Connect-AzAccount -UseDeviceAuthentication


```
## Criando uma VM via CLI
```ps
# Create VM and configuration details for deployment
az vm create `
--resource-group $rgs.ResourceGroupName `
--location $rg.Location `
--name vm-demo-001 `
--image UbuntuLTS `
--admin-username cloudchase `
--generate-ssh-keys `
--no-wait

Get-AzResource | Format-Table # Get all Azure resources in table format

```
## Create TAGs by CLI
```ps
az group update --resource-group "<RESOURCE_GROUP_NAME>" --tags "Environment=Production" "Dept=IT" "CreatedBy=<YourName>"

```
## remnove TAGs by CLI
```ps
#In the Cloud Shell, list the existing virtual machines:
az vm list --query '[].{name:name, resourceGroup:resourceGroup, tags:tags}' -o json

#Remove the existing tags from the VM:
az vm update -g "<RESOURCE_GROUP_NAME>" -n webvm1 --remove tags.defaultExperience

#Mark the VM for deletion
az vm update -g "<RESOURCE_GROUP_NAME>" -n webvm1 --set tags.MarkForDeletion=Yes

```
## CHANGE NETWORK TAG

```ps
az network vnet list --query '[].{name:name, resourceGroup:resourceGroup, tags:tags}' -o json

```
## Overwrite the existing tags
```ps
az resource tag --tags "Dept=IT" "Environment=Production" "CreatedBy=Rodrigo" --resource-group "395-f6789091-add-remove-and-update-tags-for-resou" -n "vnet1" --resource-type "Microsoft.Network/virtualNetworks"
```

## Check VM CPU metrics, replacing with the VM subscription name and <RESOURCE_GROUP_NAME> with the group name you just copied:


```ps
Get-AzVM

Get-AzSubscription

## replace data below
az monitor metrics list --resource /subscriptions/<ID>/resourceGroups/<RESOURCE_GROUP_NAME>/providers/Microsoft.Compute/virtualMachines/labVM0

```
Resize VMs in the Availability Set

```ps
#Assign the value to the $vm variable:

$vm = Get-AzVM -ResourceGroupName <RESOURCE_GROUP_NAME> -VMName labVM0
#Perform the PowerShell commands to resize the VM(s):

$vm.HardwareProfile.VmSize = "Standard_B1s"
Update-AzVM -VM $vm -ResourceGroupName <RESOURCE_GROUP_NAME>

```
```ps
```
```ps
```

