# <p align="center">
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

- Prepare AD Infrastructure
- Deploy Active Directory
- Create Users with PowerShell
- Group Policy and Managing Accounts

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/D33mC3E.png"
</p>
<p>
Created a Domain Controller running windows server and VM running window 10 Pro along with a VNET (Step-1)
</p>
<br />

<p>
<img src="https://i.imgur.com/G9sodJC.png"
</p>
<p>
Clicked on Virtual NIC that dc-1 uses to configure its IP settings (change it from dynamic to static) (Step-2)
</p>
<br />

<p>
<img src="https://i.imgur.com/YcQpod6.png"
</p>
<p>
Changed Private IP settings for dc-1 (Step-3)
</p>
<br />

<p>
<img src="https://i.imgur.com/oLudK3x.png"
</p>
<p>
Logged into our domain controller (dc-1) using Windows Remote Desktop (Step-4)
</p>
<br />

<p>
<img src="https://i.imgur.com/6lcQUz3.png"
</p>
<p>
Used run command to bring up Windows Firewall inside our domain controller (Step-5)
</p>
<br />

<p>
<img src="https://i.imgur.com/YkUed7H.png"
</p>
<p>
Turned all firewalls off inside dc-1 (for the sake of the lab) (Step-6)
</p>
<br />

<p>
<img src="https://i.imgur.com/5XFWK07.png"
</p>
<p>
Copied dc-1s private IP address and made client-1 point to that DNS server by adding private IP address to client-1s DNS servers inside its Network Interface Card look to dc-1 for info (Step-7)
</p>
<br />

<p>
<img src="https://i.imgur.com/hP8oLnJ.png"
</p>
<p>
Logged into client-1 VM using Remote Desktop opened Windows Powershell to successfully ping dc-1s private IP (Step-8)
</p>
<br />

<p>
<img src="https://i.imgur.com/mtXwF60.png"
</p>
<p>
Ran a command in Windows Powershell to observe that client-1s DNS server is pointing to our domain controller (dc-1) (Step-9)
</p>
<br />

<p>
<img src="https://i.imgur.com/xtWaMJI.png"
</p>
<p>
Back in dc-1 we ran the same command and observed dc-1s DNS server is still the VNet server (Step-10)
</p>
<br />

<p>
<img src="https://i.imgur.com/tMNR0XF.png"
</p>
<p>
Within dc-1 using Server Manager we installed Active Directory Domain Services feature to our server (Step-11)
</p>
<br />

<p>
<img src="https://i.imgur.com/5ao53OS.png"
</p>
<p>
Promoted dc-1 to a Domain Controller by adding a new forest within Server Manager (mydomain) (Step-12)
</p>
<br />

<p>
<img src="https://i.imgur.com/x2xQgPf.png"
</p>
<p>
Logged back in to dc-1 using domain name and username (not signing in locally) (Step-13)
</p>
<br />

<p>
<img src="https://i.imgur.com/6RAb0a5.png"
</p>
<p>
Inside dc-1 Active Directory Users and Computers we added two new organizational Units (OU) (Step-14)
</p>
<br />

<p>
<img src="https://i.imgur.com/tbAykVd.png"
</p>
<p>
Created a new admin user and named it Jane Doe (Step-15)
</p>
<br />

<p>
<img src="https://i.imgur.com/73334oo.png"
</p>
<p>
Made Jane a member of the Domain Admins Security Group to officially make her an admin then logged back in as jane_admin (Step-16)
</p>
<br />

<p>
<img src="https://i.imgur.com/b3hkeLt.png"
</p>
<p>
Added client-1 to the domain server in system settings using jane_admins account we created (Step-17)
</p>
<br />

<p>
<img src="https://i.imgur.com/AAdf4e8.png"
</p>
<p>
Went back into dc-1 in AD users and computers to observe that client-1 now shows up in the Domain Controller (Step-18)
</p>
<br />

<p>
<img src="https://i.imgur.com/v6GI91h.png"
</p>
<p>
Back in dc-1 as jane admin we copied a script into powershell ISE to add 10000 users to our Active Directory (Step-19)
</p>
<br />

<p>
<img src="https://i.imgur.com/zrh54Kg.png"
</p>
<p>
Picked a random user the script created in ADUC and logged onto client-1 with that users name and set password (with mydomain.com as context) (Step-20)
</p>
<br />

<p>
<img src="https://i.imgur.com/X2uDJHz.png"
</p>
<p>
Using Group Policy Management we configured the account lockout settings for users (Step-21)
</p>
<br />

<p>
<img src="https://i.imgur.com/21IBvIS.png"
</p>
<p>
Used a command to force the grop policy update as jane admin in client-1 (Step-22)
</p>
<br />

<p>
<img src="https://i.imgur.com/0NMwoCd.png"
</p>
<p>
Using a fake user we created in ADUC we successfully locked out the account with too many failed logon attempts (Step-23)
</p>
<br />

<p>
<img src="https://i.imgur.com/dbvIcp1.png"
</p>
<p>
In dc-1 ADUC we went into the locked out users account and proceeded to unlock it as jane admin (Step-24)
</p>
<br />

<p>
<img src="https://i.imgur.com/IbyRqId.png"
</p>
<p>
Successfully logged into user account after unlocking (Step-25)
</p>

