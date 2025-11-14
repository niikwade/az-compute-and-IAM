## **Project 1: Azure Compute and Identity Management**

**Topics/technologies Covered**: VMs, RBAC, Azure AD, Policies, Encryption, Cost Management

#### **Summary**
This project involves deploying a virtual machine, securing it using RBAC, applying Azure Policies for resource governance, encrypting sensitive data, and monitoring costs.

#### **Scenario**
RadioCity Ltd - a fictitious company - wants to deploy a virtual machine for their web application, secure it with role-based access control, enforce a policy for naming conventions, encrypt sensitive data, and monitor the cost of the deployed resources.

## Prerequisites
- An Azure subscription (Free Trial works)
- Basic understanding of Azure portal
- Permissions to create resources
  
### Project Objective
1. Secure Access: Implementing Role-Based Access Control (RBAC) to enforce the principle of least privilege.
2. Compliance: Applying Azure Policy initiative to enforce organizational tagging standards.
3. Cost Control: Implementing budget alerts to prevent unexpected costs.

### Step-by-step implementation
+ **Create a Virtual Machine**
<img width="1465" height="864" alt="VM creation-1" src="https://github.com/user-attachments/assets/a6a83f72-5ba3-430a-be1f-e9ff92c15e40" />

1. Before this step, I created a resource group to hold all the created resources in this project. At the 'Zone options' section, I chose "Self-service" as that allowed me full control and co-location by allowing me to choose a zonal-managed disk, something I annot do if I had chose "Azure-selected zones".

<img width="1480" height="914" alt="VM creation-2" src="https://github.com/user-attachments/assets/349aa8f6-b0fd-4ea9-a0e2-e36cb70652a4" />
2. For the purpose of this project, I chose 'Zone 1' under "Availability zone, and then kept the default options presented in the other field (plus they were the cheapest option(s) out  of the lot).

<img width="1465" height="867" alt="VM creation-3" src="https://github.com/user-attachments/assets/17b5bbd7-7d7a-4466-950d-627913f45341" />
3. Under "Authentication type" I opted for ssh, since that is more secure than password. Then provided a username, left 'Generate new key pair' under "SSH public key source", then chose RSA SSK format for SSH key Type because it could offer more security with keys longer than 3072 bits compared to 128 bits in a Ed25519 256-bit key. I went with 'RadioCity-VM_key' as the key pair name.
At the 'Public inbound ports' under "Inbound port rules" section, I went witht the 'None' option so I could create an NSG rule to allow only certain types of connections to the VM (e.g. ssh connection). This is enhance security fo the VM resource.

<img width="1358" height="858" alt="VM-disk-1" src="https://github.com/user-attachments/assets/a1f90f6e-1c22-4423-b923-508543da68bf" />
4. I created and attached a disk (to store the web app for RadioCity). I went with a descriptive name for the disk. For "source type" I chose 'None', since I want to have an empty disk to host the web app. I accepted the default disk size, and chose 'Platform-managed key' for "Key management, as I believe that is an easier option for this project. I didn't want the disk to be shared with other VMs so selected 'No' for "Enable shared disk", and ticked the box for "Delete disk for VM", as this option ensure when the resource group is deleted, the VM also gets deleted so I don't incure any cost for the undeleted VM.

<img width="1912" height="872" alt="deployed-vm" src="https://github.com/user-attachments/assets/0f3f7c9a-ae4d-464f-a0ec-4f2d6a319562" />
5. Here is an overview of the deployed VM.


### Lessons Learnt
