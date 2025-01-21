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

<h2>Starting the VMs</h2>

Ensure the DC-1 and Client-1 VMs are powered on in the Azure Portal.

If you need help creating your virtual machines and  Active Directory Infrastructure in Azure, please see my tutorial [here](https://github.com/DariuszProcelewski/prepinf-ad)

<h2>Part 1: Installing Active Directory</h2>

1. Log in to DC-1. Access the DC-1 virtual machine using Remote Desktop Protocol (RDP).

2. Install Active Directory Domain Services (AD DS)

Add the Active Directory Domain Services role to the server.
![Screenshot 2025-01-21 055457](https://github.com/user-attachments/assets/abf1dd23-0fd5-41eb-a185-71d90d91fb7f)
![Screenshot 2025-01-21 055636](https://github.com/user-attachments/assets/a27bde57-ca16-48a9-b26a-1709024f31ce)
![Screenshot 2025-01-21 055743](https://github.com/user-attachments/assets/9b0a1ed7-da09-43c9-accf-d95e44f655fb)
![Screenshot 2025-01-21 055904](https://github.com/user-attachments/assets/c8ceb9f5-b659-4e22-b73a-4ed89f211fad)
![Screenshot 2025-01-21 060009](https://github.com/user-attachments/assets/9906470f-cf66-425d-bc3a-9358c7298a02)
![Screenshot 2025-01-21 060200](https://github.com/user-attachments/assets/10fce2c6-3c68-49a2-ae82-8acdcaad245a)


3. Promote DC-1 to a Domain Controller

![Screenshot 2025-01-21 060737](https://github.com/user-attachments/assets/bba23e09-522f-48b0-9c4c-b40ad1eb2754)

- Set up a new forest with the domain name of your choice (e.g., mydomain.com).
  
- Make a note of the domain name for future use.

![Screenshot 2025-01-21 061021](https://github.com/user-attachments/assets/5df78d3f-f5dd-44fa-9799-cc9b041e71c3)
![image](https://github.com/user-attachments/assets/eac46e35-df3d-45a3-acca-13e641e27227)
![Screenshot 2025-01-21 061306](https://github.com/user-attachments/assets/28505971-776d-4dbb-82eb-448f04b4f648)
![Screenshot 2025-01-21 061531](https://github.com/user-attachments/assets/c44ef408-113e-417d-ba01-5e9c78e7c041)
![Screenshot 2025-01-21 061703](https://github.com/user-attachments/assets/ee786c49-473a-4f40-9812-d8e5709e959d)

4. Machine will restart your VM automaticly. Log Back In

- Restart DC-1 after promotion.

- Log back in using the domain account: mydomain.com\labuser.
  
![image](https://github.com/user-attachments/assets/1b2d58e3-118a-4de2-b62c-e5a35d268916)
![Screenshot 2025-01-21 062447](https://github.com/user-attachments/assets/79750a77-24c6-4135-9cbb-94119ac9e229)

  
