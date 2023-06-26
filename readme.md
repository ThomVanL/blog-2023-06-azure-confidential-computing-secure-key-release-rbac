# Azure Confidential Computing: Azure RBAC for Secure Key Release

## Description

A few months ago, I wrote [a blog post](https://thomasvanlaere.com/posts/2022/12/azure-confidential-computing-secure-key-release/) detailing how to leverage Azure Key Vault's secure key release feature. Upon revisiting that post, I realized that I had utilized Key Vault's access policy feature to enable a specific security principal for the release operation. While Key Vault access policies are an older method of managing permissions, they have the advantage of immediate propagation, unlike RBAC assignments which may take a minute to process.

At any rate, this prompted me to pause and reconsider how I could configure the release operation using a more modern approach through Azure RBAC.

To facilitate a secure key release via Azure RBAC, we need the following components:

- Role Assignment: We must assign a role that allows the data action `Microsoft.KeyVault/vaults/keys/release/action`. This role will grant the necessary permissions for the key release operation.
- Scope: For the purposes of this demonstration, we will set the scope at the __resource group__ level. By specifying the scope, we can control access to the secure key release operation within a defined boundary.
- Security Principal: In this case, we can leverage the system-assigned identity of the confidential virtual machine as the security principal.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FThomVanL%2Fblog-2023-06-azure-confidential-computing-secure-key-release-rbac%2Fmain%2Fbicep%2Fmain.json)

## 🔗 Links

- [Full blog post](https://thomasvanlaere.com/posts/2023/06/azure-confidential-computing-secure-key-release-rbac/)
