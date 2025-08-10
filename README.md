<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Deployment and Configuration Steps</h2>

In this lab, we will create two VMs in the same VNet. One is used as the domain controller, while the other VM is the client machine. We change the DC's private IP address to static because it provides Active Directory services to the client machine. We change the DNS settings on the client machine so it uses the DC as its DNS server. 
<p>
<img width="840" height="718" alt="image" src="https://github.com/user-attachments/assets/d2b7ac02-348f-4176-8cbe-359629fa0373" />
</p>
<p>
Make sure DC-1 has a static IP address. Client-1 will connect to DC-1. To ensure connectivity, we have to ping DC-1 from Client-1. The ping will NOT work at first. Enable ICMPv4 on the firewall of DC-1. Then, you should ping DC-1 successfully from Client-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Log back into DC-1 and install AD Users and Computers. Promote VM to DC, make a new forest called "mydomain.com" then restart DC-1. Log back with the username: "mydomain.com/labuser" OR you may have to log in as just "labuser". You should be able to run AD Users and Computers as shown below.
</p>
<br />

<p>
<img <img width="935" height="314" alt="image" src="https://github.com/user-attachments/assets/8bb7727a-3525-4212-85b8-b1e3a04cd6a2" />

</p>
<p>
We will create 2 different Organizational Units (OU) named "_ADMINS" and "_EMPLOYEES". Right click on mydomain.com, click new -> Organizational Unit. Right click on "_ADMINS" folder, click new -> User. For this example, name the user as "Jane Doe" and put her username as "jane_admin" since she will be the admin. Finally, you add her to the domain admins group. 
  
</p>
<br />

<p>
<img <img width="940" height="656" alt="image" src="https://github.com/user-attachments/assets/915328e5-2db2-48ad-8a21-f8982a3e0b14"
  <img width="1079" height="683" alt="image" src="https://github.com/user-attachments/assets/db6cb720-c627-4e39-8745-91c0cb3b208e" />
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
