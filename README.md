<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure free acount
- Knowledge of Windows Operating System
- [Installation Files](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

List of Steps
Create a Resource Group in Azure Virtual Machine
![Screenshot 2023-11-03 083331](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/68404bf5-9919-4bef-88ac-5cce5addbaf4)
Create a Windows 10 Pro Virtual Machine with 4 VCPUs (it will also create a new Virtual Network - VNET)
![Screenshot 2023-11-03 083503](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/a3e830fd-e019-44b2-9cdc-c33ba179a791)
![Screenshot 2023-11-03 083525](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/a13ca906-a90f-4e54-9568-9b28aab3375b)
Once the virtual machine is up and running, copy the IP address and connect via the remote desktop app. You will need to login with the credentials you setup for the VM.
![Screenshot 2023-11-03 091234](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/d88473a8-b371-41c1-8e34-ed4fce1540ce)
Install and Enable IIS in Windows with CGI and Common HTTP Features
![Screenshot 2023-11-03 092330](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/6301cfef-beab-474d-830a-93bbe4cf1c89)
From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
![Screenshot 2023-11-03 094230](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/bc2a5db0-ab0f-49c4-ab7d-d346cda8a5dc)
From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
![Screenshot 2023-11-03 094735](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/e392ed4a-af0e-4d17-8ea0-a781bc76eb26)
Create the directory C:\PHP
From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
![Screenshot 2023-11-03 094928](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/13b18f25-44d4-49f5-98a3-bc827da92b8b)
![Screenshot 2023-11-03 095025](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/753acb35-c855-41d6-9e22-b4b9521c5f79)
From the Installation Files, download and install VC_redist.x86.exe.
![Screenshot 2023-11-03 100050](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/ee1c70fa-3910-4ede-b1f3-82bf3ea5ca20)
From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Password1
![Screenshot 2023-11-03 100823](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/1b67fab8-2095-44f5-9ca4-a1d3e53881d0)
![Screenshot 2023-11-03 100939](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/3496a837-54d8-4c16-a29b-6bf1424a0647)
![Screenshot 2023-11-03 101006](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/013fcd5c-7452-4366-8db0-8cfb036d3aad)
Open IIS as an Admin
Register PHP from within IIS
![Screenshot 2023-11-03 101541](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/c36cf8e8-deca-4c06-9789-da540339a6ed)
Reload IIS (Open IIS, Stop and Start the server)
Install osTicket v1.15.8
Download osTicket from the Installation Files Folder
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
![Screenshot 2023-11-03 102357](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/a4e0cc11-273f-4ada-83f5-d943cf813baf)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
![Screenshot 2023-11-03 101959](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/39750286-a95b-4d38-ab40-d9fa5b46c7c1)
Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes
![Screenshot 2023-11-03 103835](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/29cf258c-9b57-45a8-ac0d-7bfb772da0ba)
Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
![Screenshot 2023-11-03 104241](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/25324c2f-ffe0-4e29-90fb-23507be012e7)
![Screenshot 2023-11-03 104316](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/b4e4e324-7293-483d-844c-689273614b80)
Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All
![Screenshot 2023-11-03 104357](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/922074b5-39b7-4f4e-b1eb-26f322b78503)
Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)
![Screenshot 2023-11-03 104815](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/c6cfb388-f5b9-44e9-bfb7-771f436c412b)
From the Installation Files, download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”
![Screenshot 2023-11-03 104815](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/94bd2c7b-27e0-4065-a9f8-561a26ab7af3)
![Screenshot 2023-11-03 105107](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/e1fe64ea-fa55-4e7e-acf7-fd9c6d8bb47e)
![Screenshot 2023-11-03 105454](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/b6663428-ed3c-4239-8e40-f9b5c013f0ba)
Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”
![Screenshot 2023-11-03 105718](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/c8504aa5-686e-4bb3-bee8-3010d03fea0d)
Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php
![Screenshot 2023-11-03 110100](https://github.com/jachinrupe/osticket-prereqs/assets/149485790/0cc384ef-c5ee-4ca5-a831-8c9162d36001)






