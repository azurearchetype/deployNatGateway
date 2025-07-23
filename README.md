# Azure NAT Gateway Deployment

This custom Azure template Deploys a NAT gateway and associates it with multiple subnets in the specified virtual network.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fazurearchetype%2FdeployNatGateway%2Fmain%2FmainTemplate.json/createUIDefinitionUri/https%3A%2F%2Fraw.githubusercontent.com%2Fazurearchetype%2FdeployNatGateway%2Fmain%2FcreateUiDefinition.json)


## Instructions
1. Click the **Deploy to Azure** button above.
2. Sign in to the Azure portal.
3. Select a resource group or choose to create a new one for deployment of the NAT Gateway
   and public IP resources.
4. Choose/verify the Azure region for deployment of the NAT gateway. This region must match the
   the region of the virtual netowrk you specify in the next step.
5. Enter the name of an esiting virtual network and one or more subnets using the custom UI form.
   * This name must match exactly or the deployment will fail. case-sensitive.
6. Enter names for the NAT Gateway and Public IP resources respectively.
7. Complete the deployment to create the NAT gateway and associate it with the selected subnets.

## Key Notes

1. NAT Gateway is not used for inbound traffic—it only handles outbound connections.
2. It is associated with a subnet(s), not individual resources.
3. Becasue a NAT gateway is assoicated with subnet, a gateway instance is required for each
   virtual network you a providing outbound connectivity for.
4. It can support multiple public IPs or IP prefixes for scaling outbound connections.


## Architecture

<img width="500" height="400" alt="deployNatGateway" src="https://github.com/user-attachments/assets/28cfdcce-284e-4b4a-967e-9f41042a42f7" />

