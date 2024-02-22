<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

Part 1 (Create Virtual Machine in Azure)
Create a Resource Group
Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
When creating the VM, allow it to create a new Virtual Network (Vnet)

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/aa420e0f-c9f1-464b-b626-e402be1d4d36)


Part 2 (Installation)


Create an Azure Virtual Machine Windows 10, 4 vCPUs
Name: Vm-osticket
Username: labuser (for example/whatever you chose)
Password: osTicketPassword1! (for example/whatever you chose)



Install / Enable IIS in Windows WITH
CGI and Common HTTP Features
World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
AND IIS Management Console
Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/dede9d75-bb58-455f-b93e-cc789b595cd4)


Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

Download and install the Rewrite Module (rewrite_amd64_en-US.msi)

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/201a3b72-32e7-452e-8edd-1474683d18e1)

Create the directory C:\PHP

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/0c32b468-da5e-407a-bd17-a865067b1718)

Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
!! ATTENTION !!
If this appears, choose to “Keep” the file:

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/95bc0fdb-f56e-48d2-b332-a7f5d089b624)


If you are still having trouble downloading PHP 7.3.8, please try downloading and installing Google Chrome and doing it from within there. 

From the Installation Files, download and install VC_redist.x86.exe.
![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/95bc0fdb-f56e-48d2-b332-a7f5d089b624)
Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Password1

Open IIS as an Admin

Register PHP from within IIS

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/a8ab226f-0842-41d8-90e6-52215a77ebcc)

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/71bd55b5-ae7f-495a-b31e-d540c94c54ff)


Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/ed004cfa-510c-4abd-89ef-262ba114a85d)

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

 download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/74fd2f4a-c0a4-4a6c-a0de-9b8967697126)


Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”

Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/b3ea90d8-31ea-4583-9a65-c8bcb65e43f8)

End Users osTicket URL:
http://localhost/osTicket/ 

![image](https://github.com/Tomcruztech/osticket-prereqs/assets/160645953/907f8006-dbae-4db2-b99e-21e865941f6b)

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Notes:
Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
End Users osTicket URL: http://localhost/osTicket/ 
