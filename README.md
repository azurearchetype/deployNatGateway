# Azure NAT Gateway Deployment

This custom Azure template deploys a NAT gateway and associates it with multiple subnets in the specified virtual network.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fazurearchetype%2FdeployNatGateway%2Fmain%2FmainTemplate.json/createUIDefinitionUri/https%3A%2F%2Fraw.githubusercontent.com%2Fazurearchetype%2FdeployNatGateway%2Fmain%2FcreateUiDefinition.json)


## Instructions
1. Click the **Deploy to Azure** button above.
2. Sign in to the Azure portal.
3. Select a resource group or choose to create a new one for deployment of the NAT Gateway
   and public IP resources.
4. Choose/verify the Azure region for deployment of the NAT gateway. This region must match the
   the region of the virtual netowrk you specify in the next step.
5. Enter the name of an esiting virtual network and one or more subnets using the custom UI form.
   * This name must match exactly or the deployment will fail. It is case-sensitive.
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

## Purpose

The **Azure NAT Gateway** is a fully managed service that provides **outbound Internet connectivity** for resources in a **private virtual network (VNet)**. It enables secure and scalable outbound access without requiring public IPs on individual resources.

---

## Benefits
### ✅ Static Outbound IP Addressing
- Assign one or more **static public IPs** or a **public IP prefix**.
- Ensures **predictable outbound IPs** for whitelisting and compliance.

### ✅ High Scalability
- Handles **millions of concurrent flows**.
- Ideal for large-scale deployments such as **AKS**, **VMSS**, and **ASE**.

### ✅ Improved SNAT Port Management
- Efficient **Source Network Address Translation (SNAT)**.
- Reduces risk of **SNAT port exhaustion** in high-throughput environments.

### ✅ Enhanced Security
- Resources remain **private** (no public IPs).
- Only **outbound traffic** is allowed; inbound traffic is blocked.
- Integrates with **NSGs** and **UDRs** for traffic control.

### ✅ Simplified Management
- Centralized outbound connectivity for all resources in a subnet.
- No need to manage individual public IPs or load balancers.

### ✅ Cost Efficiency
- Reduces need for multiple public IPs or outbound load balancers.
- Optimizes IP usage with support for **IP prefixes**.

---

## Supported Azure Resources

Resources in a subnet associated with a NAT Gateway can use it for outbound connectivity:

- **Virtual Machines (VMs)**
- **Virtual Machine Scale Sets (VMSS)**
- **Azure Kubernetes Service (AKS)**
- **App Service Environment (ASE) v3**
- **Azure Batch**
- **Azure Container Instances (ACI)**
- **Azure Functions (Premium or App Service Plan with VNet Integration)**

---

## Notes

- NAT Gateway is **not used for inbound traffic**.
- Must be associated with a **subnet**, not individual resources.
- Supports **multiple public IPs** or **IP prefixes** for scaling.

---

## Example Use Cases

- AKS clusters needing stable outbound IPs for API access.
- VMs requiring secure outbound Internet access without public IPs.
- App Services integrated with VNets for controlled outbound traffic.

