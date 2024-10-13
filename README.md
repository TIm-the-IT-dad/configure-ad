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
