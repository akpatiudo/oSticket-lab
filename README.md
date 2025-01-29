## osTicket Helpdesk Ticketing System Lab: From Installation to Ticket Lifecycle

![ost](https://i.imgur.com/rxF1Ihj.png)

### osTicket - Prerequisites and Installation
### Introduction:
The osTicket lab is an engaging journey through the core processes of a Helpdesk ticketing system. Though detailed, it’s a rewarding challenge that requires focus and patience. To simplify the experience, the lab is divided into three clear sections, each addressing a key phase of the system's setup and operation, with step-by-step guidance to make complex tasks manageable and easy to follow.

### Section 1: Setting Up the Environment
This section focuses on creating the Azure Virtual Machine and preparing the environment for osTicket installation.

### List of Prerequisites

1)  Operating system, Window 11 Pro version 24Hz-x64 Gen2 

2)  Azure Vitual Machine Configure the VM with 4 vCPUs.

3)  osTicket Installation [click here](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

### Prepare for osTicket Installation:

  Use Remote Desktop (RDP) to connect to your VM 

  Download the osTicket-Installation-Files.zip to your desktop within the VM.

  Unzip the file and ensure the folder is named osTicket-Installation-Files.
  
### Enable IIS (Internet Information Services) With GCI
  - click turn Window feature on or off > expand internet information services  > expand World Wide Web Services > expand Application Development Features check CGI click ok
  - brows 127.0.0.1 if the dependencise are well insall you have the IIS web
    ![IIS](https://i.imgur.com/X8t0u5D.png)

### Install Dependencies from osTicket-Installation-Files:

![](https://i.imgur.com/XKpzIOw.png)
-  Install PHP Manager for IIS:  (PHPManagerForIIS_V1.5.0.msi).
-  Install Rewrite Module: (rewrite_amd64_en-US.msi.)
-  Create a  directory C:\PHP
    
    - Unzip PHP 7.3.8: (php-7.3.8-nts-Win32-VC15-x86.zip.)
    - Destination folder: C:\PHP. (right click, extract all, browse to the PHP folder you created)

- Install Visual C++ Redistributable: (VC_redist.x86.exe.)
- Install MySQL 5.5.62: (mysql-5.5.62-win32.msi.) Choose "Typical Setup".

### Launch Configuration Wizard after installation:
-  Standard
-  Username: root
-  Password: root.

### Prepare IIS for osTicket:
-  Open IIS Manager as an Administrator.
-  Register PHP in IIS using PHP Manager:
-  Path: C:\PHP\php-cgi.exe.
-  Reload IIS (Open IIS, Stop and Start the server by right clicking and click stop or start) this allows the web server to locate PHP

### Install osTicket v1.15.8

![osTicket](https://i.imgur.com/jAV5l57.png)

⁃ From the "osTicket-Installation-Files" folder, unzip "osTicket-v1.15.8.zip
- copy the ‘’upload" folder into "c:\inetpub\wwwroot" 
⁃ Within "c:\inetpub\wwwroot", Rename "upload" to "osTicket

![](https://i.imgur.com/o7emYBx.png)

-  Reload IIS (Open IIS, Stop and Start the server)
-  Go to sites > Default > osTicket On the right click "Browse *:80"

![](https://i.imgur.com/52Zc0sO.png)

 Note that some extensions are not enabled 

### Enable Extensions in IIS

![](https://i.imgur.com/1m6IQ2K.png)

-Go back to IIS, sites -> Default -> osTicket 
- Double-click PHP Manager
⁃ Click on  "Enable or disable an extension (search for the dependencies you need to enable)
  -  Enable: php_imap.dll 
  -  Enable: php_intl.dll 
  -  Enable: php_opcache.dll
 ![](https://i.imgur.com/t084XHB.png)
    
### Refresh the osTicket Site in your browser.

![](https://i.imgur.com/HbSuXG9.png)

The three above extension should now have a green checkmark

### Rename Configuration File:

Rename: ost-config.php  
-	From: C:\inetpublwwwroot\osTicket\include\ost-sampleconfig.php  
-	To: C:\inetpubwwwroot\osTicket\ost-config.php  

### Assign Permissions: ost-config.php 
⁃ Disable inheritance > Remove All 
- (Right click on ost-config.php, properties, security, disable inheritance, remove all inherited permissions)  
⁃ New Permissions > Everyone > All
- (Add, select a principle, under enter the subject name put everyone, check name)
  -  Allow everyone full control (check all boxes) > Select apply > OK  

![](https://i.imgur.com/IoRkxFn.png)


Continue Setting up osTicket in the browser (click Continue)  
-	Name Helpdesk  
-	Default email (receives email from customers)  
From the "osTicket-Installation Files" folder, install HeidiSOL  
-	Open Heidi SQL  
-	Create a new session, root/root  
-	Connect to the session  
⁃	 Create a database called "osTicket"  

### Complete osTicket Setup in the Browser:
-  Go back to the browser and click Continue
-  Name: Helpdesk
-  Email: whichever email you want
-  First Name: your first name
-  Last Name: your last name
-  Email Address: whichever email you want (needs to be different from the Helpdesk's default email)
-  Username: admainuser
-  Password: Password1

### Download and Install HeidiSQL
-  Head to osTicket site [here](https://www.heidisql.com/download.php,)
-  Download and install HeidiSQL
-  Open HeidiSQL > Select "New" at the bottom-left corner of the screen
-  User: root
-  Password: Password

![](https://imgur.com/uRKkCKO.png)

-  Select Open
On the left side,
  -  right-click Unnamed > select Create New > Database
  -  Name it “osTicket” and select OK

![](https://i.imgur.com/sA2dOjF.png)

You data base should looke like this after set up

![](https://imgur.com/qplxpvo.png)

## Continue Setting up osTicket in the browser 
-	 MySOL Database: osTicket 
-	 MySQL Username: root 
-	 MySQL Password: root  
Click "Install Nowl"

![](https://imgur.com/MxGJtGP.png)

Congratulations, you have successfully install osTicket on your Machine!  

![](https://i.imgur.com/ADRrJ0R.png)

Browse to your help desk login page http://localhost/osTicket/scp/login.phe  
End Users osTicket URL http://localhost/osTicket/

### Post-Intallation Cleanup
-  Go to C: > inetpub > wwwroot > osTicket > Setup
-  Delete the contents in the Setup folder
-  Afterwards, delete the Setup folder
-  Go to C: > Inetpub > wwwroot > osTicket > Include

Checking the permision
-  Right-click on ost-config.php
-  Select Securities > Advanced > Click on "everyone" > edit to change permissions
-  Allow everyone to only have "Read and execute" permission, then select OK > Apply > OK

[Click Here](https://github.com/akpatiudo/osTicket_post-Installation) to move on to section two:(Post Installation Configuration)


