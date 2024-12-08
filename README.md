# Administering Windows Server: My final project

## Table of Contents
- [Project Overview](#project-overview)
- [Network and ADDS Setup](#network-and-adds-setup)
  - [Server #1 Configuration](#server-1-configuration)
  - [Server #2 Configuration](#server-2-configuration)
  - [Server #3 Configuration](#server-3-configuration)
  - [Client Workstation Setup](#client-workstation-setup)
- [Active Directory Organizational Units](#active-directory-organizational-units)

---

## Project Overview
**Theme**: Dragonball Z

This guide offers an in-depth walkthrough for setting up a Windows Server environment with a Dragonball Z theme. It provides detailed instructions for both beginners and advanced users. This setup simulates a small-scale corporate network environment.

### Tools and Requirements:
- **Software**:
  - Windows Server 2016 ISO
  - Windows 10 ISO for the client machine
- **Hardware/Virtualization**:
  - Virtual environment such as Hyper-V, VMware, or VirtualBox
- **Knowledge Prerequisites**:
  - Basic understanding of networking and server administration

---

## Network and ADDS Setup
We will configure three servers and one client machine. Each server is assigned a distinct role. The following detailed steps ensure functionality and connectivity.

![image](https://github.com/user-attachments/assets/7f1a5064-f4f0-400d-afb0-2dec56a7c471)

### Server #1 Configuration
#### Installation and Role Assignment:
1. **Install Windows Server**:
   - Load the Windows Server 2016 ISO into a virtual machine.
   - Follow the installation wizard, name the server `EarthF24IX`, and configure a strong administrative password.

2. **Assign Server Roles**:
   - Open **Server Manager** and click "Add Roles and Features."
   - Select **Active Directory Domain Services (ADDS)** and **DNS** roles.
   - Confirm installation and wait for completion.

#### Network Configuration:
3. **Configure the IP Address**:
   - Open **Network and Sharing Center** > "Change Adapter Settings."
   - Right-click the network adapter and select "Properties."
   - Assign the following:
     - IP Address: `192.168.0.1`
     - Subnet Mask: `255.255.0.0`
     - Preferred DNS: `192.168.0.1`

#### Domain Controller Setup:
4. **Promote to Domain Controller**:
   - In **Server Manager**, click "Promote this server to a domain controller."
   - Create a new forest with the domain name `Dbz.net`.
   - Configure DNS delegation and set the domain functional level to Windows Server 2016.
   - Restart the server after configuration.

![image](https://github.com/user-attachments/assets/9fc3b5f3-1791-4399-96d3-dc92424f1d79)

![image](https://github.com/user-attachments/assets/6b068e9e-cca3-4031-b727-c60630e50e02)

### Server #2 Configuration
#### Installation and Role Setup:
1. **Install Windows Server**:
   - Assign the name `NamekF24IX` during the installation process.

2. **Add DHCP Role**:
   - In **Server Manager**, click "Add Roles and Features."
   - Select **DHCP Server** and complete the wizard.

#### Network and DHCP Configuration:
3. **Set Static IP**:
   - Configure the IP settings:
     - IP Address: `192.168.0.3`
     - Subnet Mask: `255.255.0.0`
     - Preferred DNS: `192.168.0.1`

4. **Configure DHCP Scope**:
   - Open the **DHCP Management Console.**
   - Create a new scope named "KorinsTower" with the following details:
     - IP Range: `192.168.0.50 - 192.168.0.54`
     - Subnet Mask: `255.255.0.0`
     - Default Gateway: Leave blank for this setup.

![image](https://github.com/user-attachments/assets/ed270ee7-93f2-4a2b-b6a1-6dc523399c5d)

![image](https://github.com/user-attachments/assets/2e03d429-0516-4b25-bbde-ba68039f2555)

![image](https://github.com/user-attachments/assets/c05269fa-3b3b-4bff-b159-b367b0741bc5)

![image](https://github.com/user-attachments/assets/3278df71-34d7-46aa-be25-5861298c6714)


### Server #3 Configuration
#### Installation and Role Assignment:
1. **Install Windows Server**:
   - Set the server name to `SadalaF24IX` during the setup process.

2. **Install FRSM Role**:
   - In **Server Manager**, add the **File Resource Manager (FRSM)** role.

#### Network and Shared Folders:
3. **Configure Static IP**:
   - Assign:
     - IP Address: `192.168.0.5`
     - Subnet Mask: `255.255.0.0`
     - Preferred DNS: `192.168.0.1`

![image](https://github.com/user-attachments/assets/b416b5e6-27af-4488-931d-1089927c1717)

4. **Create Shared Folders**:
   - Open **File and Storage Services** > "Shares."
   - Create a new SMB share, assign permissions, and set a test folder named `TestFolder`.

![image](https://github.com/user-attachments/assets/2f310415-9306-4a59-a900-3f36e15eb95a)

![image](https://github.com/user-attachments/assets/317f2312-c9ae-4f69-935f-46abbfecb54b)

![image](https://github.com/user-attachments/assets/cd43d34e-d541-4027-8ffd-4edb4f46dec7)

![image](https://github.com/user-attachments/assets/1e34a1a9-d166-4500-8ab7-a1b3466414de)

![image](https://github.com/user-attachments/assets/2f4afc87-2582-4707-afcb-55b120561830)

### Client Workstation Setup
#### Installation and DHCP Configuration:
1. **Install Windows 10**:
   - Load the Windows 10 ISO and create a virtual machine named `Yardrat24F`.

2. **Enable DHCP**:
   - Verify that the client receives an IP address dynamically from Server #2.

![image](https://github.com/user-attachments/assets/74ad8447-af58-4d63-9292-f1a5a2efb159)

![image](https://github.com/user-attachments/assets/f6a71ac1-60f9-4f6c-8e64-a1c7a6f6de19)

---

## Active Directory Organizational Units
OUs help manage users and groups effectively. Follow these steps:

1. **Launch ADUC**:
   - Open **Active Directory Users and Computers** on Server #1.
   - Create the following OUs:
     - Saiyans24F
     - Earthlings24F
     - Namekians24F

2. **Add Groups and Users**:
   - Inside each OU, create groups and users with the following:
     - **Saiyans24F**: Son Goku, Prince Vegeta, Son Gohan
     - **Earthlings24F**: Bulma Briefs, Master Roshi, Tien Shinhan
     - **Namekians24F**: Lord Slug, King Piccolo, Elder Guru

3. **Set Group Policies**:
   - Assign basic group policies, such as folder redirection or login scripts, to each group.
   
![image](https://github.com/user-attachments/assets/d84dcf17-b1a7-424c-8227-89e64d887318)

![image](https://github.com/user-attachments/assets/5e40cb6b-b854-4e54-9117-8e56f5df8e1e)

![image](https://github.com/user-attachments/assets/79668ca0-0019-4c1a-b439-852b641fd2aa)


