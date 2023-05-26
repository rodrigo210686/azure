# azure

Check VM CPU metrics, replacing <ID> with the VM subscription name and <RESOURCE_GROUP_NAME> with the group name you just copied:

```ps1
 
az monitor metrics list --resource /subscriptions/<ID>/resourceGroups/<RESOURCE_GROUP_NAME>/providers/Microsoft.Compute/virtualMachines/labVM0

  
```
