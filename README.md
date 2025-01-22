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

<h2>Create a Domain Admin User</h2>
1. Access Active Directory Users and Computers (ADUC)

- Open ADUC on DC-1.
  
![Screenshot 2025-01-21 063516](https://github.com/user-attachments/assets/22242a69-adbd-423c-b590-82097beb7201)

  
2. Create Organizational Units (OUs)
   
![Screenshot 2025-01-21 063729](https://github.com/user-attachments/assets/06bb652d-94a0-40c6-9dd2-5fcc9b5a7d2c)

- Create an OU named _EMPLOYEES.
  
  ![image](https://github.com/user-attachments/assets/9fd2370c-bc6f-41ce-aecf-6f9e4519535a)

  
- Create another OU named _ADMINS.
  
![image](https://github.com/user-attachments/assets/cb10b75b-2872-40cf-b2c9-c9bc36736d6e)

  
3. Add a New Employee

- Create a user named Jane Doe in the _ADMINS OU with the following credentials:
  
 - Username: jane_admin
   
 - Password: Cyberlab123!
   
![image](https://github.com/user-attachments/assets/30d7dae2-da91-4dcf-80ad-58cfa78a0dda)

![image](https://github.com/user-attachments/assets/b7cf0999-fbe4-4067-8aff-90391a786d0d)

![image](https://github.com/user-attachments/assets/d3c4833a-8d8e-4bff-9d6a-9442c76d7211)

4. Assign Administrative Permissions

- Add jane_admin to the Domain Admins security group.

![image](https://github.com/user-attachments/assets/e980c355-fdf3-4a2e-b667-7f5b8ab4465d)

![Screenshot 2025-01-21 064608](https://github.com/user-attachments/assets/b4bf0d54-fcf2-48ea-b857-32e846ff1b61)


5. Switch to the New Admin Account

- Log out of DC-1 and reconnect using the account: mydomain.com\jane_admin.
  
![image](https://github.com/user-attachments/assets/1cc60582-9072-41d7-b766-d4f39a2a3e7d)

6. Use jane_admin Moving Forward

- Use the jane_admin account as the primary administrator for future tasks.

<h2>Joining Client-1 to the Domain</h2>

1. Log In to Client-1

2. Join Client-1 to the Domain

3. Add Client-1 to the domain (this will trigger a restart).
   
![Screenshot 2025-01-22 063318](https://github.com/user-attachments/assets/c6acc1af-d04d-4917-a6d5-3ad07f7fcbc8)

![Screenshot 2025-01-22 063747](https://github.com/user-attachments/assets/c8e2c51d-508f-4d4c-9e55-54e55963722a)

![image](https://github.com/user-attachments/assets/94922281-d439-46df-b9ee-8cfdc9a5d0b8)

![image](https://github.com/user-attachments/assets/1874120c-7d7b-4fb7-9490-37f9685e4304)

![image](https://github.com/user-attachments/assets/531dcccc-4f2d-4531-8b0a-1345a5781b6d)

4. Verify Domain Membership

5. Log in to the Domain Controller and open Active Directory Users and Computers (ADUC).
   
![Screenshot 2025-01-22 064418](https://github.com/user-attachments/assets/d7cbde26-f8ad-42db-83a8-1a785f2c8419)
   
6. Confirm that Client-1 appears in the default Computers container.
   
![image](https://github.com/user-attachments/assets/a1b96c39-bcb8-46af-bf39-5911954cb2e4)
   
7. Organize Client-1 in Active Directory

- Create a new Organizational Unit (OU) named _CLIENTS.

- Move Client-1 into the _CLIENTS OU.
  
![image](https://github.com/user-attachments/assets/eaae2e62-5d29-4b55-bbd8-f23fb3c3de4d)

![image](https://github.com/user-attachments/assets/cc6b820b-1ad1-40ec-b25e-6b59158a8073)

![image](https://github.com/user-attachments/assets/2269fd3a-389f-475d-8548-13c3d977995f)

  
