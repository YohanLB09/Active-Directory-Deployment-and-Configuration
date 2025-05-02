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

-Step 1: Install Active Directory Domain Services 
-Step 2: Promote the Domain Controller VM 
-Step 3: Log back in the Domain controller
-Step 4: Create two Organizational Units (OUs)
-Step 5: Create a Domain Admin user within the domain
-Step 6: Login back in as the Domain admin user
-Step 7: Join the Client VM to your domain

<h2>Project Walkthrough</h2>

<h3>Step 1: Install Active Directory Domain Services</h3>

<p>
<img src="https://i.imgur.com/h3N5bbe.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Once logged in to your Azure account, browse to "Resource groups" from the navigation pane.

-Click on "Create".

-Make sure the correct Subscription is choosen.

-Enter a Resource group name.

-Choose the appropriate region depending on your needs

-Click on "Review + Create" to complete the configuration process.
</p>
<br />




<h3>Step 2: Create a Virtual Network and Subnet</h3>

<p>
<img src="https://i.imgur.com/RWi9J3w.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Browse to "Virtual Networks" from the navigation pane.

-Click on "Create".

-Select the previously created Resource group.

-Create a name for the Virtual Network.

-Choose the same Region as the Resouce group.

-Leave all other settings as default and click on "Review + Create".

The virtual network and subnet provide an isolated network space in Azure, enabling communication between hosts within the same logical network.
</p>
<br />




<h3>Step 3: Create a Server VM</h3>

<p>
<img src="https://i.imgur.com/OdBIFfT.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Browse to "Virtual machines" from the navigation pane.

-Click on "Create".

-Select the previously created Resource Group.

-Create a name for the Server VM (e.g.: dc-1).

-Pick the same Region as the Resource group and Virtual network.

-For the image, choose: "Windows Server 2022 Datacenter: Azure Edition - x64 Gen2".

-Select a VM size; having at least 2 vcpus and 8 GiB memory is recommended.

-Create a username and a password (write them down in Notepad for futur use).

-Leave the other options at their default configuration and move on to the Networking section.

-In the Networking section, select the previously created Virtual network.

-Leave all the other options at their default configuration and click on "Review + create".

This step creates an Azure virtual machine using Windows Server 2022 within your existing resource group and virtual network. This VM, with specified size and initial credentials, is being provisioned to later be configured as the domain controller.
</p>
<br />




<h3>Step 4: Set a static IP address for the Server VM</h3>

<p>
<img src="https://i.imgur.com/en3mRbS.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-From within the Server VM's settings in Azure, select "Networking" -> "Network settings" -> click on the "link" under Network interface / IP configuration to access the NIC settings -> "ipconfig1" -> Next to Allocation, select "Static" ->  "Save".

-Additionally, take note of the Server VM's private IP address, as we will need it for later (use Notepad).

We set a static IP address for Server VM because the client VM needs a reliable and unchanging address to consistently locate the domain services, especially for DNS resolution which is crucial for joining the domain.
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

<b>We've successfully deployed the foundational virtual machine infrastructure, establishing a Server VM that will eventually be promoted as a Domain controller and a Client VM within the same Azure virtual network, configured for basic communication. (Next lab description). Remember to stop the VMs in the Azure Portal when not in use to manage costs effectively.</b>
<br />
<br />
</p>
