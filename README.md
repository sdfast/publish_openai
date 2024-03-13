# publish_openai

Let's say you have an Azure ARM template resource like this:
```json
{
  "type": "Microsoft.Compute/virtualMachines",
  "apiVersion": "2021-03-01",
  "name": "myVM",
  "location": "East US",
  "dependsOn": [],
  "properties": {
    // VM properties
  }
```
In ARM template, you might use res
ourceId() like this to reference this VM's ID:

"vmResourceId": "[resourceId('Microsoft.Compute/virtualMachines', 'myVM')]"
In Terraform, you might do something like this:

```terraform
data "azurerm_virtual_machine" "my_vm" {
  name                = "myVM"
  resource_group_name = azurerm_resource_group.example.name
}
```

```terraform
output "vm_resource_id" {
  value = data.azurerm_virtual_machine.my_vm.id
}
```
In this Terraform configuration:
We're using azurerm_virtual_machine data source to fetch information about the virtual machine named "myVM".
The output block is just to demonstrate how you can use the ID of the virtual machine elsewhere in your Terraform configuration.
This is just a basic example. Depending on your specific use case, you might need to adjust this approach accordingly.
