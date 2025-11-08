<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Manage Users in Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the management of users accounts in Active Directory within Azure Virtual Machines.<br />


<h2>💻⚙️ Software and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Windows Server (2022)
- Windows 10 Pro (22H2)
- Remote Desktop
- Group Policy Management 
- Active Directory Users and Computers (ADUC)
- PowerShell

<h2>💻 Operating Systems Used</h2>

- **Windows Server (2022)**
- **Windows 10 Pro (22H2)**

<h2>Configuration Steps</h2>

- Configure Group Policy
- Dealing with Account Lockouts
- Password Reset
- Enabling and Disabling Accounts 
- Observing Logs
<br />

<h2>Deployment and Configuration Steps</h2>

<h3>🔵 Dealing with Account Lockouts</h3>
<p>
  
  Get logged into "**DC-1**" **Server VM**,
  
 Pick a random user account we created previously 
 
 – *User*: **"BODI-VOBA"**

Account Lockout Policy is not set in Active Directory. 

To do so, type "**gpmc.msc**" in Run (`Windows key + R` or Search for "**Run**"), right-click an existing GPO, and select Edit to modify it.

*How To Configure **Account Lockout Threshold** in **Group Policy*** : https://docs.google.com/document/d/1msUMWaPDMR1hPYxzGOlgN4KpUjnyyYEv3vvOQXkSpLQ/edit?tab=t.0 

Then we'll Configure **Group Policy** to lock out the account after **5** attempts: 
</p>
<p>
  <img src="https://i.imgur.com/2w9IPHR.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/8Dw2gBK.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/27Lp6G6.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/gbKznvW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Log in to **Client-1** as Domain Admin “Jane Doe” to force the PC to update the policy quickly using the command prompt.

  Use the command: `gpupdate /force`
</p>
<p>
  <img src="https://i.imgur.com/yENE6eR.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  Sign out of Client-1 VM and attempt to log in with a bad password **6** times. 
  
  After **5** times, the Client-1 VM should lock you out on the 6th attempt for that user's account ❌️.
</p>
<p>
  <img src="https://i.imgur.com/s6jgOCa.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Observe that the account has been locked out within **Active Directory Users and Computers (ADUC)**, it says 
  
  "*This Account is currently Locked out on this Active Directory Domain Controller!* "
</p>
<p>
  <img src="https://i.imgur.com/x8n0WiM.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Now let's unlock the account. Check✅️ "**Unlock Account**", then click **Apply** & **OK**.
</p>
<p>
  <img src="https://i.imgur.com/tlEkJ86.png" height="100%" width="90%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Now the user can log into the Client-1 VM.
</p>
<br />

<h3>🟢 Password Reset</h3>
<p>
  
  After the failed login attempts, you could reset the Password for the end-user here in the **ADUC**.

  Set a temporary password for the end-user that complies with the company's password policy.

  Right-click the user and select the "**Reset Password**" option. Then, attempt to log in with it.
</p>
<p>
   <img src="https://i.imgur.com/2py9SSb.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  You must also be sure to check✅️ the highlighted boxes to ensure the user’s account is **unlocked** and enable them to set their own password rather than the temporary one. 
</p>
<p>
  <img src="https://i.imgur.com/IwlC6Sx.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

  To provide excellent **Customer Service** for the end-user, be sure to 

  - Communicate the temporary password to the end-user through a secure channel and instruct them to change it immediately upon login, ensuring that the new password is strong and complies with the company's password policy, and not to forget it.
    
  - Provide guidance on how to change the password using the company's self-service password reset tool if available.
    
  - Document the date and time of account creation for auditing purposes.
</p>
<br />

<h3>🔴 Enabling and Disabling Accounts</h3>
<p>
  
  Disable the same account in **Active Directory Users and Computers (ADUC)**.
</p>
<p>
  <img src="https://i.imgur.com/xa2gLNW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Attempt to log in with it, and observe the error message,
</p>
<p>
  <img src="https://i.imgur.com/AOLT2lx.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Then, **Re-enable** the account and attempt to log in.
</p>
<p>
  <img src="https://i.imgur.com/EtUx8Uk.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>Observe Logs</h3>
<p>
  
Observe the logs on the Client-1 VM,
  
Log in as the *User* - "**bodi.voba**",

Type “**eventvwr.msc**” in the search bar.
</p>
<p>
  <img src="https://i.imgur.com/0HBLhZB.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  We can’t see Log Events as a normal user. Open as **Administrator**, and sign in as the Domain Admin, "Jane Doe". 
  
  We can still log in even though we’re signed in as someone else.
</p>
<p>
  <img src="https://i.imgur.com/ffGnlta.png" height="100%" width="90%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/qyBJTZA.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Here you can view events from Windows Logs. 
</p>
<br />

### 📊 Results & Observations  
- **Group Policy** provides centralized control over lockout rules.  
- **Account lockouts** are logged in Event Viewer with detailed audit trails.  
- **Unlocking & Resetting passwords** restore access without recreating accounts.
- **Disabled accounts** block logins instantly.    


