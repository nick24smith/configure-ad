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
<img <img width="668" height="498" alt="image" src="https://github.com/user-attachments/assets/d3970b6f-2445-4c69-b331-b17d7375d36f" />

</p>
<p>

  </p>
<br />

<p>
<img <img width="532" height="394" alt="image" src="https://github.com/user-attachments/assets/8822c466-7c45-4006-a109-6a2d98ab668a" />


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
<img <img width="1079" height="683" alt="image" src="https://github.com/user-attachments/assets/db6cb720-c627-4e39-8745-91c0cb3b208e" " />

</p>
<p>

  </p>
<br />

<p>
<img <img width="692" height="367" alt="image" src="https://github.com/user-attachments/assets/c8aec21a-9970-415b-ae4b-d13b134f0e89" />

</p>
  
Now you can use "jane_admin" as the administrator account. Join Client-1 to the domain (mydomain.com) by changing Client-1's DNS settings to the DC private IP address in Azure. Then, restart Client-1 from the Azure portal. Your screen should look like the pictures below to know it's verified. 

</p>
<br />

<p>
<img <img width="799" height="718" alt="image" src="https://github.com/user-attachments/assets/a95111d3-c1fd-4f63-9d9d-0f75a0ea3185" />
</p>
<p>

</p>
<br />

</p>
<br />

<p>
<img <img width="783" height="599" alt="image" src="https://github.com/user-attachments/assets/b56024b4-403c-4553-809e-59022cfbc592" />

</p>
<p>
We have to join Client-1 to the domain next. Go to your system settings, click "About", then click "Rename this PC(advanced)". Now we select "Change", then change your domain to "mydomain.com". Fill in your credentials for "mydomain.com/labuser". Your VM is going to restart, and then Client-1 will be a part of the domain.
</p>
<br />

</p>
<br />

<p>
<img <img width="1024" height="582" alt="image" src="https://github.com/user-attachments/assets/195827a5-13b4-4e5c-926c-6b252c0a2712" />

</p>
<p>
We will set up remote desktop for non-admin users on Client-1. Log in to Client-1 as an admin user. Open system properties, click "Open Remote Desktop", then allow "Domain Users" access to Remote Desktop. Now you can log into Client-1 as a normal user. 
</p>
<br />

</p>
<br />

</p>
<br />

<p>
<img <img width="604" height="674" alt="image" src="https://github.com/user-attachments/assets/63145d3b-f1d8-4320-9165-1db5c143984a" />

</p>
<p>
We will use a script to verify that normal users can use Remote Desktop in Client-1. We will input the script into Powershell ISE (run as administrator). After we create the users, they will have access to Remote Desktop in Client-1.
</p>
<br />

</p>
<br />

</p>
<br />

<p>
<img <img width="1046" height="812" alt="image" src="https://github.com/user-attachments/assets/1ada433a-18fd-45a1-96a9-368749b13da2" />

</p>
<p>

</p>
<br />

</p>
<br />

</p>
<br />

<p>
<img <img width="474" height="267" alt="image" src="https://github.com/user-attachments/assets/59215f4f-b08e-4cb1-8d32-bc448c205677" />

</p>
<p>

  </p>
<br />

</p>
<br />

<p>
<img <img width="428" height="136" alt="image" src="https://github.com/user-attachments/assets/4a0c79d8-75c6-43d6-9c6c-000ae2e99e33" />


</p>
<p>
As you can see, the script created a user named "bape.jive" and we were able to access Client-1 as a regular user.
</p>
<br />
