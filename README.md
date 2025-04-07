<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Managing Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the management of users accounts in Active Directory within Azure Virtual Machines.<br />


<h2>Software and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Windows Server (2022)
- Windows 10 Pro (22H2)
- Remote Desktop
- Group Policy Management 
- Active Directory Users & Computers (ADUC)
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server (2022)
- Windows 10 Pro (22H2)

<h2>Configuration Steps</h2>

- Dealing with Account Lockouts
- Configure Group Policy 
- Enabling and Disabling Accounts 
- Observing Logs
<br />

<h2>Deployment and Configuration Steps</h2>

<h3>Dealing with Account Lockouts</h3>
<p>
  Get logged into DC-1
  
 Pick a random user account we created previously – User: bodi-voba

Account Lockout Policy is not set in Active Directory, 

To do so, type "gpmc.msc" in Run (Windows key + R or Search for "Run"), right-click an existing GPO and select Edit to modify it.

How To Configure Account Lockout Threshold in Group Policy: https://docs.google.com/document/d/1msUMWaPDMR1hPYxzGOlgN4KpUjnyyYEv3vvOQXkSpLQ/edit?tab=t.0 

Then we'll Configure Group Policy to lock out the account after 5 attempts: 
</p>
<p>
  <img src="https://i.imgur.com/2w9IPHR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
