## Resource Groups

What is a Resource Group?

A Resource Group in Azure is a logical container used to manage and organize related Azure resources. Think of it as a folder where you group resources that share the same lifecycle, permissions, and policies. These resources could include virtual machines (VMs), storage accounts, virtual networks, databases, and more.

Key Points:
- Resource group lifecycle: The lifecycle of a Resource Group is tied to the resources within it. When you delte a resource group, all the resources inside it are deleted as well, unless you use features like resource locks to prevent deletion of individual resources. It's important to group resources together based on their lifecycle needs. For instance, resources that need to be delployed and managed together (e.g., a web app and its database) should be in the same resource group.

- Resource Group Location: The resource group itself has a location (region), but the resources within the group can be in different regions. The location of the resource group is used for metadata and management operations (like access control and monitoring). However, resources like VMs or storage accounts will reside in the region they are deployed to.

- Management and Access Control: Resource groups help you manage resources with role-based access control (RBAC). By assigning roles to users, groups, or servic principals at the resource group level, you can control who has access to teh resources within that group. For example, you could give a user access to manage only the resources within a specific resource group, but not other resource groups.

- Tagging Resources: You can assign tags to resource groups and their contained resources. Tags are key-value pairs that can be used for organizing and tracking reousrces based on cost, department, environment, or other criteria. For example, you might tag resources with keys like "Environment: Production" or "Department: Finance" for easier cost management and reporting.

- Deployment and Automation: Resource groups are used in Azure Resource Manager (ARM) templates to define, deploy and manage Azure resources in a declarative way. By defining resources in an ARM template, you can automate the deployment of entire resource groups and their associated resources. You can also use Azure Blueprints to apply consistent configurations across multiple resource groups, ensuring governance and compliance.

- Resource Group Limits: There are some limits on teh number of resources per resource group. For example, the maximum number of resources per resource group is 800, although the exact limits can vary depending on the resource type.

## Best Practices for Resource Groups:
- Group resources by lifecycle: Resources that share the asame lifecycle, such as development, testing, and production environments, should ideally be placed in different resource groups to manage their lifecycle more effectively.
- Use Resource Locks: If you have critical resources that should not be delted or modified accidentally, you can apply a lock at the resource group level. There are two types of locks:
  1. CanNotDelete: Prevents accidental deletion.
  2. ReadOnly: Prevents modification of resources within the group.
- Consider management overhead: If you have many resources to manage and scale, having too many resource groups might add complexity. ensure you balance organizations with operational ease.
- Compliance and Security: You can apply policies to a resource group to ensure that only compliant resources are deployed, based on organizational security and govenance policies.

Example:
Image you have an application with the following components:
- Virtual machines (VMs) for app servers
- A storage accoutn for file storage
- A SQL database for storing data
- A virtual network for networking

You might place all these resources into a single resource group, say MyAppRG, because they are all part of the same application, share the same lifecycle, and need to be managed together.

## How to Create a Resource Group (CLI Example):
```
az group create --name MyResourceGroup --location eastus
```
This command creates a new resource group named MyResourceGroup in the eastus region.

## arm templates


