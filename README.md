<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

Steps to Set Up a Domain Controller in Azure

Create a Resource Group

![Screenshot 2025-01-16 055658](https://github.com/user-attachments/assets/f158ca8e-5359-483c-bd46-1313dfebb8af)
![Screenshot 2025-01-16 060000](https://github.com/user-attachments/assets/6980a569-46b7-4a2a-ac05-8150f5bf45c0)

Begin by creating a dedicated resource group to organize and manage related resources.

Create a Virtual Network and Subnet
![Screenshot 2025-01-16 060300](https://github.com/user-attachments/assets/7335a377-c2b9-4869-ac26-784c8184bdca)
![Screenshot 2025-01-16 060457](https://github.com/user-attachments/assets/7895b55a-5449-4b82-a88b-290e4c9b8cbc)

Configure a virtual network and a subnet to establish the necessary infrastructure for the domain controller.

Deploy the Domain Controller VM

Create a Virtual Machine using Windows Server 2022 and name it "DC-1".

-Username: labuser

Password: Cyberlab123!

![Screenshot 2025-01-16 060741](https://github.com/user-attachments/assets/6e24c5c8-3e17-40a7-b6e9-378a4c5a4732)
![Screenshot 2025-01-16 061258](https://github.com/user-attachments/assets/abb23de1-a7f3-4228-b846-6c5fdfc275be)
![Screenshot 2025-01-16 061408](https://github.com/user-attachments/assets/eed0ddba-be41-426b-a266-108478558320)
![image](https://github.com/user-attachments/assets/957fea81-cc2b-4916-832f-a7129efed024)
![Screenshot 2025-01-16 061921](https://github.com/user-attachments/assets/31d9841e-74bf-4116-9b1e-1f42c9bf9e02)





Set a Static Private IP for the Domain Controller

Once the VM is created, configure the NIC (Network Interface Card) to use a static private IP address for consistent network connectivity.
Disable Windows Firewall (Testing Purposes)

Log in to the VM and temporarily disable the Windows Firewall to test connectivity during setup.
This process establishes the foundation for a domain controller within a virtualized environment.

<h2>Deployment and Configuration Steps</h2>
