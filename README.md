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

 
 <h2>Part 2: Setting Up Remote Desktop for Non-Administrative Users on Client-1</h2>

1. Log in to Client-1

- Use the domain admin account: mydomain.com\jane_admin.

2. Enable Remote Desktop Access for Domain Users

- Open System Properties and navigate to the Remote Desktop tab.
  
- Allow access to Remote Desktop for Domain Users.

![image](https://github.com/user-attachments/assets/03ed532b-ba5b-459c-bac9-72b75ccd982f)

![Screenshot 2025-01-22 070122](https://github.com/user-attachments/assets/53abfa03-143f-4bb3-b9a3-060265610154)

![Screenshot 2025-01-22 070321](https://github.com/user-attachments/assets/2b5b74c0-8b33-41ea-a633-78512df7769f)

3. Test Remote Desktop Access

- Confirm that a normal, non-administrative domain user can now log in remotely to Client-1.
  
![Screenshot 2025-01-22 070505](https://github.com/user-attachments/assets/9eaf9319-1e54-4a5b-be4b-ef84956b3f10)


Note: In a production environment, this configuration is typically managed via Group Policy for multiple systems simultaneously.


 

<h2>Creating Additional Users and Testing Logins</h2>

1. Log in to dc-1
 
- Use the domain admin account: mydomain.com\jane_admin.  

2. Run the User Creation Script
   
- Open PowerShell ISE as an administrator.
   
- Create a new file and paste the provided script into it. You can download/copy script [here](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)

- Execute the script and monitor the creation of user accounts.  

![image](https://github.com/user-attachments/assets/5f061921-4a6b-4fbd-b197-1a00eb9afdc0)

![Screenshot 2025-01-22 071711](https://github.com/user-attachments/assets/1dee2935-9d7e-4421-b30e-9b3c9ed8aace)

![image](https://github.com/user-attachments/assets/f40e22fc-093f-4eff-960b-e81319ade297)

![Screenshot 2025-01-22 072246](https://github.com/user-attachments/assets/05b685c7-7772-434d-9496-a59e4e2f4f1c)

3. Verify Account Creation
   
- Open Active Directory Users and Computers (ADUC).
     
- Confirm the new accounts appear in the _EMPLOYEES Organizational Unit (OU).  

![image](https://github.com/user-attachments/assets/85a38b8c-3dd1-4de9-8a68-f8d691678683)


4. Test User Login on Client-1
     
Attempt to log in to Client-1 using one of the newly created user accounts. (Use the password specified in the script for the login)  

![Screenshot 2025-01-22 072800](https://github.com/user-attachments/assets/037da682-4120-4d7b-8af5-e07c1194404d)

![image](https://github.com/user-attachments/assets/4ac0ff98-20b1-4a3b-b454-de0b8c3e8047)

![image](https://github.com/user-attachments/assets/2f99fa7d-3f63-406c-87eb-2a9f0c4f9e08)

![image](https://github.com/user-attachments/assets/0cb38235-375e-4a80-9cb8-af7b7a58a068)


Congratulations! You have successfully implemented an on-premises Active Directory and created user accounts within an Azure virtual environment!
