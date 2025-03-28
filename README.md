Azure VNet Architecture: Bastion Host + Private VM Lab
This project demonstrates how to manually build a secure, production-style Azure Virtual Network (VNet) environment with public and private subnets, using Azure Bastion to access private resources without public IPs.

📐 Architecture Overview
Custom VNet: 10.1.0.0/16
├── 🌐 Public Subnet: 10.1.1.0/24
│ └── 🟢 Azure Bastion Host (Provides SSH access to private VM)
└── 🔒 Private Subnet: 10.1.2.0/24
  └── 🔵 private-vm (No public IP, accessed via Bastion)

🔧 What You Set Up
✅ Networking
Virtual Network (VNet): cloud-vnet → 10.1.0.0/16

Public Subnet: public-subnet → 10.1.1.0/24

Private Subnet: private-subnet → 10.1.2.0/24

Azure Bastion Subnet: AzureBastionSubnet → 10.1.3.0/24

✅ Network Security Groups (NSGs)
public-nsg: Allows SSH (22) & HTTP (80) from anywhere

private-nsg: Allows SSH only from inside the VNet (10.1.0.0/16)

✅ Virtual Machines
private-vm

Ubuntu Server 22.04

Deployed in private-subnet

No public IP

Authentication via SSH key (my-linux-key.pem)

✅ Bastion Host
cloud-vnet-bastion

Deployed in AzureBastionSubnet

Connected to cloud-vnet

Public IP: cloud-vnet-ip

SKU: Standard

🔐 How to Connect to Private VM
Go to Virtual Machines → private-vm → Connect → Bastion

Select SSH Private Key (from local file)

Upload your my-linux-key.pem

Username: azureuser

Click Connect

This opens an SSH session in your browser without needing a public IP on the VM.

🧠 Skills Practiced
✅ Azure Virtual Network architecture design
✅ Subnetting and NSG configuration
✅ Private VM isolation
✅ Azure Bastion deployment and access
✅ Secure SSH key authentication
✅ Real-world cloud security patterns
