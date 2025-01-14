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

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


<h2>Installation Steps</h2>


1.) Start by creating a virtual machine at [https://portal.azure.com/](https://portal.azure.com/). Choose Windows 10 Pro, version 22H2, and configure it with at least 2 vCPUs and 16 GB of memory.

2.) After creating your virtual machine, connect to it using its public IP address. Use the Remote Desktop Connection app to establish the connection. 
</p>
<br />

<p>
<img src="https://i.imgur.com/9dEnp65.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
/>
</p>
<p>
<p>
<img src="https://imgur.com/Zf2jw07.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
3.) After connecting to your virtual machine, open the Control Panel and navigate to "Programs." Then, select "Turn Windows features on or off."

<img width="388" alt="image" src="https://github.com/user-attachments/assets/3253a406-09ab-4c9d-b4f7-f8a1372cba00" />

  <p>
    
  </p>
<img width="389" alt="image" src="https://github.com/user-attachments/assets/d750f5d1-340d-4c96-9a56-3d644b765005" />

  
4.) You will want to install / enable IIS in Windows with CGI and Common HTTP Features
  - World Wide Web Services -> Application Development Features -> 
[X] CGI
[X] Common HTTP Features
  
<p>
<img width="407" alt="image" src="https://github.com/user-attachments/assets/3d9e5921-c10d-4a5b-b210-9c6dc640e478" />

</p>
<p>
  
      
5.) With IIS enabled, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) from the installation files. Follow the installation wizard to complete the setup.
  
6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
  
7.) Create a folder in the C drive called PHP.
  
8.) Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) from the installation files and extract its contents to `C:\PHP`.
  
9.) After extracting the PHP zip file to the `C:\PHP` folder, download and install `VC_redist.x86.exe` from the installation files. Complete the setup by following the installation wizard.
  
10.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  Run the setup wizard:
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->

  Make the new root password: root
  
<p>
<img width="245" alt="image" src="https://github.com/user-attachments/assets/c53735e6-5e41-4092-86d4-89c659e3cd3c" />

</p>
<p>
  
  Execute the process on the next page.
  
  
11.) Now that we have the files downloaded and installed we will want to search for IIS in the windows search bar. Open IIS as an administrator.
  The program should look like this.
  
<p>
<img src="https://imgur.com/rgdZwmM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
12.) We will now want to register PHP from within IIS.
  Click on PHP Manager
  
<p>
<img width="472" alt="image" src="https://github.com/user-attachments/assets/81d25526-9333-4cf3-ba77-324949c94486" />
</p>
<p>
  
Register new PHP version.
  
<p>
<img width="470" alt="image" src="https://github.com/user-attachments/assets/025892f6-34bb-464e-9918-efe9c0d8ad2d" />
</p>
<p>
  
You will want to provide a path to the php executable file (php-cgi.exe)). 
  Go to C Drive -> PHP -> click on php-cgi file.
  
<p>
<img src="https://imgur.com/oJZ0gp9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Restart the IIS server.
  
<p>
<img width="469" alt="image" src="https://github.com/user-attachments/assets/7b77920e-1fb3-46f2-96ed-fa93a7dea211" />
</p>
<p>
  
13.) Install osTicket v1.15.8
  -Download osTicket from the Installation Files Folder
  -Extract and copy "upload" folder to c:\inetpub\wwwroot
  -Within c:\inetpub\root, Rename "upload" to "osTicket"
  
  Reload IIS again.
  
14.) On IIS go to sites -> Default -> osTicket
  -On the right, click “Browse *:80”
  
<p>
<img width="472" alt="image" src="https://github.com/user-attachments/assets/3c71f5a2-1c5f-4e3a-b673-6604c48bfd7d" />
</p>
<p>
  
  Some extensions are not enabled on the osTicket browser.
  
<p>
<img src="https://imgur.com/eJIsGTn.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  To enable the extensions:
  -Go back to IIS, sites -> Default -> osTicket
  -Double click PHP manager
  -Click "Enable or disable an extension"
  
<p>
<img width="472" alt="image" src="https://github.com/user-attachments/assets/87f8c616-020e-4447-b9fa-b44e30e38a67" />
</p>
<p>
  
<p>
<img width="476" alt="image" src="https://github.com/user-attachments/assets/cdfd7fc3-e019-44ae-93fe-bea460ce5c90" />
</p>
<p>
  
  We will want to enable three extensions from here.
  
  1.) php_imap.dll
 
  2.) php_intl.dll
  
  3.) php_opcache.dll
  
<p>
<img width="264" alt="image" src="https://github.com/user-attachments/assets/1aec4aab-1328-4d75-93c8-c45187f8c607" />
</p>
<p>
  
  
15.) Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder.
  Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
  We are going to rename the ost-sampleconfig.php to ost-config.php
  
  Now that we have renamed the files, right click on the file and go to properties.
  From there click security, click on advance, and disable the inheritance.
  We will select Remove all inherited permissions from this object.
  
  Now we will add new permissions.
  
  Click Add
  
<p>
<img width="379" alt="image" src="https://github.com/user-attachments/assets/ef1910e3-ed68-41c6-9acb-34a2578ac090" />
</p>
<p>
  
Select a principal
  
<p>
<img width="454" alt="image" src="https://github.com/user-attachments/assets/c3074262-8369-4ca1-a048-563d04484043" />
</p>
<p>
  
  
 Type "Everyone" in the box.
  
<p>
<img src="https://imgur.com/F4H3ppM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Make sure Full Control and all the other boxes are checked.
  
<p>
<img width="454" alt="image" src="https://github.com/user-attachments/assets/39e873c0-8fc5-42f6-bce0-0d4373d5b361" />
</p>
<p>
  
  Click Apply and Ok.
  
<p>
<img width="379" alt="image" src="https://github.com/user-attachments/assets/a33a36d6-8b9b-4761-b2af-6866ce04e088" />
</p>
<p>
  
  Next we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page.
  Fill out the page as required excluding the Database Settings at the bottom of the page. We will get to that. 
  
  We will want to download and install HeidiSQL from the Installation Files. 
  
<p>
<img src="https://imgur.com/i7a4gWC.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  When the program is open we will create a new session in it.
  
<p>
<img width="340" alt="image" src="https://github.com/user-attachments/assets/f9027f89-c7e9-4ead-a143-aff4974443c5" />
</p>
<p>
  
  We want to make sure the username and the password are root.
  
<p>
<img width="343" alt="image" src="https://github.com/user-attachments/assets/51243636-3a0b-4428-b767-091db577d56f" />
</p>
<p>
  
  After connecting to the session, return to the browser to complete the setup. In the Database Settings section, set the username to `root` and the password to `root`.
  
  Using HeidiSQL, create a new database by right-clicking "Unnamed" on the left panel, selecting "Create New," and then choosing "Database." Name the database `osTicket`. Once the database is created, return to the osTicket browser and enter `osTicket` in the MySQL Database field.
  
<p>
<img width="410" alt="image" src="https://github.com/user-attachments/assets/5eea7085-40e4-4c1b-a664-8dd33609863d" />
</p>
<p>
  
  Now we can log in to osTicket through your web browser.
  
<p>
<img width="199" alt="image" src="https://github.com/user-attachments/assets/d99fcb1d-75a7-4edd-9f30-dc630900bc5c" />
</p>
<p>
  
  Great! You have now successfully installed and setup osTicket!
