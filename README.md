<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Manage Users in Active Directory Deployed in the Cloud (Azure)</h1>
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

- Configure Group Policy
- Dealing with Account Lockouts
- Enabling and Disabling Accounts 
- Observing Logs
<br />

<h2>Deployment and Configuration Steps</h2>

<h3>Dealing with Account Lockouts</h3>
<p>
  Get logged into DC-1,
  
 Pick a random user account we created previously 
 
 – User: "bodi-voba"

Account Lockout Policy is not set in Active Directory. 

To do so, type "gpmc.msc" in Run (Windows key + R or Search for "Run"), right-click an existing GPO and select Edit to modify it.

How To Configure Account Lockout Threshold in Group Policy: https://docs.google.com/document/d/1msUMWaPDMR1hPYxzGOlgN4KpUjnyyYEv3vvOQXkSpLQ/edit?tab=t.0 

Then we'll Configure Group Policy to lock out the account after 5 attempts: 
</p>
<p>
  <img src="https://i.imgur.com/2w9IPHR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/8Dw2gBK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/27Lp6G6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/gbKznvW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Log into Client-1 as Domain Admin “Jane Doe” to force the PC to update the policy quickly using the command prompt.

  Use the command "gpupdate /force"
</p>
<p>
  <img src="https://i.imgur.com/yENE6eR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Sign out of Client-1 VM and attempt to log in with it 6 times with a bad password. 
  
  After 5 times, the Client-1 VM should lock you out on the 6th attempt for that user's account.
</p>
<p>
  <img src="https://i.imgur.com/s6jgOCa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Observe that the account has been locked out within Active Directory Users and Computers (ADUC),
</p>
<p>
  <img src="https://i.imgur.com/x8n0WiM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Now let's unlock the account. Check "Unlock Account", then click Apply & OK.
</p>
<p>
  <img src="https://i.imgur.com/tlEkJ86.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Now the user can log into the Client-1 VM.
</p>
<br />
<p>
  After the failed login attempts, you could reset the Password here,

  Right click the user and select "Reset Password" option. Then attempt to login with it.
</p>
<p>
   <img src="https://i.imgur.com/2py9SSb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<h3>Enabling and Disabling Accounts</h3>
<p>
  Disable the same account in Active Directory Users and Computers (ADUC).
</p>
<p>
  <img src="https://i.imgur.com/xa2gLNW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Attempt to login with it, observe the error message
</p>
<p>
  <img src="https://i.imgur.com/AOLT2lx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Then, re-enable the account and attempt to log in.
</p>
<p>
  <img src="https://i.imgur.com/EtUx8Uk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
