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

