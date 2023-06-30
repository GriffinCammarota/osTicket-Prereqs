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

- PHP Manager for ISS
- Rewrite Module
- PHP 7.3.8
- VC Redist
- MySQL
- osTicket v1.15.8
- Heidi SQL

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install/Enable IIS in windows (files come with windows you just need to find and install)
	
-In control panel: Programs>Turn windows feature on or off>select Internet Information services>world wide web services>application development features>check cg. Then under common http services check all the boxes

-click okay and it will install

-Then you can test it to make sure it installed properly by opening a web browser and type 127.0.0.1 (if it doesn’t work then uncheck “Internet Information services” and click ok to uninstall then redo the previous steps)
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
For the next few just download from the project link or the original source and run the install:

All files needed for project: https://drive.google.com/drive/folders/1uWpd6rXrmiXGWFYEkKGxre7VsjBRfnEl?usp=sharing 

-PHP Manager for ISS: https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10
	
-Rewrite Module: https://www.iis.net/downloads/microsoft/url-rewrite

-PHP 7.3.8: https://www.php.net/releases/ (use ctrl+f to search “7.3.8”)
	-unzip to C:\PHP

-VC Redist: https://aka.ms/vs/17/release/vc_redist.x86.exe

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
-MySQL: https://downloads.mysql.com/archives/community/ 
	-Typical Install
-After installing launch configuration wizard
	-Standard Configuration
	-create a root password (eg. Password1)

<li>Open ISS as admin</li>

<li>Register PHP from within IIS</li>

<li>Open the PHP file from earlier (C:\PHP)</li>

<li>Then select php-cgi and click “open”</li>

<li>Restart IIS (Open IIS, then on the right of the window there is the option to restart)</li>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<li>osTicket v1.15.8: https://drive.google.com/file/d/1eDguKryHPJIDWPrzZyRcgWQDxqPQxs-1/view?usp=drive_link (couldn’t find a download link from osTicket)
-Extract and copy “upload” folder to c:\inetpub\wwwroot
-Within c:\inetpub\wwwroot, Rename “upload” folder to “osTicket”</li>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Restart ISS
	-In ISS go to sites>Default>osTicket
	-On the right click “Browse *.80”
	-This opens osTicket in the browser and it will show that we need to enable some 
extensions

-In IIS go to: sites>Default>osTicket
-Double-click PHP Manager
-Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
-Refresh the osTicket site in your browse and all the extensions that previously had an “X” should have a check mark now
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Now open your file browser and navigate to: (C:)>inetpub>wwwroot>osTicket>include
-In this folder find the file “ost-sampleconfig.php”
-Rename it to “ost-config.php”

-On that same file right click and go to properties>security>advanced
-Disable inheritance>remove all
-New permissions>Everyone>All (this is so that the osTicket installer has   permission to manipulate this file) 

-Back on the browser click “continue” 
-Name Helpdesk (eg. Griffin Helpdesk)
-fill in the email line (for the project its offline so it doesn’t have to be a real email)
-Before you continue you have to install a database for osTicket (SQL)
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Heidi SQL: https://www.heidisql.com/download.php
-Click “New”, username: root, password:Password1, now click “open”
-right click Unnamed and select “Create database” and name it osTicket

-Now back on the browser fill in the database name, username, and password that we just used in SQL and click “Install Now”

-Now we can test to make sure our URL works: http://localhost/osTicket/ 

-Now that it’s working we can delete the setup file in osTicket: C:\inetpub\wwwroot\osTicket\setup
-And go to “C:\inetpub\wwwroot\osTicket\include\ost-config.php” and set permissions to “Read Only”
</p>
<br />

