<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory - Deployment and Configuration</h1>
In this guided lab, we will install Active Directory Domain Services (AD DS) on the Server VM, create a new domain, establish an administrative user, and join the Client VM to the newly created domain.<br />

<br />This project is a continuation of [Active Directory: Infrastructure Setup](https://github.com/YohanLB09/Active-Directory-Infrastucture-Setup), so this project picks up where we left off.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Active Directory Users and Computers

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro, version 22H2

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Install Active Directory Domain Services 
- Step 2: Promote the Domain Controller VM 
- Step 3: Log back in the Domain controller
- Step 4: Create two Organizational Units (OUs)
- Step 5: Create a Domain Admin user within the domain
- Step 6: Login back in as the Domain admin user
- Step 7: Join the Client VM to your domain

<h2>Project Walkthrough</h2>

<h3>Step 1: Install Active Directory Domain Services</h3>

<p>
<img src="https://i.imgur.com/v4Xd5W0.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Log in the Domain controller VM, navigate to "Server Manager" -> click on "Add roles and features" -> click on "Next" until you get to "Server Roles; check the box for "Active Directory and Domain Services" -> click on "Next" again until you get to "Confirmation"; check the box for "Restart the destination server automatically if required"  -> "Yes"  -> click on "Install" to confirm the installation process.

This step installs the Active Directory Domain Services (AD DS) software on the Domain controller VM. Once configured with the Domain controller VM, the AD DS will allow the server to function as a domain controller, capable of managing users, computers, and security policies within a domain. The automatic restart ensures the installation completes properly.
</p>
<br />




<h3>Step 2: Promote the Domain Controller VM </h3>

<p>
<img src="https://i.imgur.com/RWEPWGQ.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
From within Server Manager, click on the flag (left side of the "Manage tab"  -> "Promote this server to a domain controller"  ->  select "Add a new forest"  ->  Create a "Root domain name" (e.g.: mydomain.com)  ->  "Next"  ->  create a password for the Directory Services Mode (DSRM) password  ->  "Next"  ->  Uncheck the box for "Create DNS delegation"  ->  "Next"  ->  click on "Next" again until you get to "Prerequisites Check"  -> click on "Install" to confirm the forest installation (tbc).
</p>
<br />


<p>
<img src="https://i.imgur.com/0LC4vBk.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-You should be automatically logged off the Domain Controller VM.

This step officially promotes the Server VM to a domain controller by installing the necessary domain services and configuring it as the root of a new Active Directory forest (e.g., mydomain.com). This establishes the foundational structure for the domain, including the domain naming system and security boundaries. The automatic logoff indicates the server is restarting to finalize the domain controller configuration.
</p>
<br />





<h3>Step 3: Log back in the Domain controller</h3>

<p>
<img src="https://i.imgur.com/XW4KeRE.png" height="30%" width="60%" alt="Configuration step"/>
</p>
<p>
-Restart and then log back into the Domain controller VM (previously called Server VM). Instead of logging in as a local user, we will connect as "mydomain.com\labuser007 (you username may be different after the "\").

After promoting the server to a domain controller in Step 2, the authentication mechanism changes. Instead of logging into the local machine's user database, the server now authenticates against the newly created domain (mydomain.com). Logging in as "mydomain.com\labuser007" verifies that the domain services are running correctly and that domain-based user authentication is now active. This is different from local login because the user's credentials are being checked against the domain's directory, not just the local server's user accounts.
</p>
<br />




<h3>Step 4: Create two Organizational Units (OUs)</h3>

<p>
<img src="https://i.imgur.com/TsH7u6u.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Once logged in to the domain controller account, navigate to "Active Directory Users and Computers" (ADUC) from the Windows search bar.

-Before creating a domain admin user, we have to create an Organizational Unit (OU). To do so, from within ADUC, right click on "mydomain" -> "New" -> "Organizational Unit" -> type " _EMPLOYEE" -> "OK"

-Create a another OU for "_ADMINS". 

The purpose of creating these Organizational Units (OUs) is to organize and manage objects (like users, computers, and groups) within the Active Directory domain. OUs act as folders that help logically structure network resources.

In this step, we are creating two OUs: "_EMPLOYEES" and "_ADMINS". This allows to group employee accounts separately from administrator accounts, making it easier to apply specific policies, delegate administrative tasks, and manage these groups effectively in the future. The underscore at the beginning of the names often helps to keep these important OUs at the top of the list in ADUC for easy access.
</p>
<br />




<h3>Step 5: Disable the Server VM's Firewall</h3>

<p>
<img src="https://i.imgur.com/tR8CUix.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Connect to the Server VM using its public IP address via Remote Desktop Connection.
</p>
<br />


<p>
<img src="https://i.imgur.com/atfLXeH.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Once logged in, use the "Windows key" + "R", then type "wf.msc" (shortcut to access the Windows Defender firewall).

-From there, disable the firewall (all profiles).

For the specific testing objectives of this lab only, we are deviating from security best practices.
</p>
<br />




<h2>Active Directory Deployment and Configuration completed!</h2>

<b>Remember to stop the VMs in the Azure Portal when not in use to manage costs effectively.</b>
<br />
<br />
</p>
