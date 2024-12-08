# Administering Windows Server: Comprehensive Step-by-Step Guide

## Table of Contents
- [Project Overview](#project-overview)
- [Network and ADDS Setup](#network-and-adds-setup)
  - [Server #1 Configuration](#server-1-configuration)
  - [Server #2 Configuration](#server-2-configuration)
  - [Server #3 Configuration](#server-3-configuration)
  - [Client Workstation Setup](#client-workstation-setup)
- [Active Directory Organizational Units](#active-directory-organizational-units)
- [Screenshots and Observations](#screenshots-and-observations)
  - [Server Configurations](#server-configurations)
  - [DHCP and ADUC](#dhcp-and-aduc)
  - [Shared Folder Configuration](#shared-folder-configuration)

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

4. **Create Shared Folders**:
   - Open **File and Storage Services** > "Shares."
   - Create a new SMB share, assign permissions, and set a test folder named `TestFolder`.

### Client Workstation Setup
#### Installation and DHCP Configuration:
1. **Install Windows 10**:
   - Load the Windows 10 ISO and create a virtual machine named `Yardrat24F`.

2. **Enable DHCP**:
   - Verify that the client receives an IP address dynamically from Server #2.

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

---

## Screenshots and Observations

### Server Configurations
1. **Server #1**: Local server configuration with ADDS and DNS roles.
   ![Server #1 Local Configuration](./screenshots/server1.png)

2. **Server #2**: DHCP role setup and connectivity test.
   ![Server #2 DHCP Setup](./screenshots/server2_dhcp.png)

3. **Server #3**: FRSM configuration and shared folder management.
   ![Server #3 FRSM Dashboard](./screenshots/server3_frsm.png)

### DHCP and ADUC
- **DHCP Scope**: Server #2 successfully manages the DHCP range.
- **ADUC Verification**: Server #2 is visible as a domain controller under ADUC.

### Shared Folder Configuration
1. **Folder Access**: The `TestFolder` created on Server #3 is accessible to domain users.
2. **Client Verification**: The client machine, `Yardrat24F`, connects to the shared folder via SMB.
   ![Shared Folder Access](./screenshots/shared_folders.png)

---

This technical guide provides an extensive, step-by-step process for configuring a Windows Server environment, suitable for IT professionals and advanced users.
