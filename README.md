<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>

<h2>Description</h2>
Project consists of setting up all the prerequisites and installing osTicket from scratch. This was done on a Windows 10 Virtual Machine I created in Azure. osTicket is a widely used and trusted open source Help Desk ticketing system. <br/>
<br/>


<h2>Environments and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Virtual Machines</b>
- <b>Remote Desktop Connection</b>
- <b>Internet Information Services</b>
- <b>MySQL</b>


<h2>Operating Systems Used </h2>

- <b>Windows 10</b>

<h2>Project Walk-through:</h2>

<p align="center">
Navigate to Microsoft Azure and create a resource group: <br/>
<img src="https://imgur.com/Hq1tcrY.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<img src="https://i.imgur.com/WDCHbEa.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Once my resource group is created, next I'll create the virtual machine:  <br/>
<img src="https://i.imgur.com/agXJt2C.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Setting up the virtual machine:  <br/>
<img src="https://i.imgur.com/NliPCEk.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<img src="https://imgur.com/QvyoJhd.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
I'll leave all other settings to default and create this VM. Once it has been created I'll use Remote Desktop Connection to connect to the VM:  <br/>
<img src="https://imgur.com/E9lD900.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Once I've connected to the VM I will install and enable IIS (Internet Information Servies) by going to Control Panel> Programs> Turn Windows Features On or Off> Internet Information Services and enable it then World Wide Web Services> Application Development Features and enable CGI:  <br/>
<img src="https://imgur.com/0MyNsKC.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Then go to Common HTTP Features dropdown and enable all features. Then apply the changes:  <br/>
<img src="https://imgur.com/6Y6VzZH.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
I can test that the web server installed correctly by typing in the loopback IP (127.0.0.1) in the internet browser and this page should load:  <br/>
<img src="https://imgur.com/XdKGpGl.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Now I need to install PHP manager for IIS Setup:  <br/>
<img src="https://imgur.com/RuAUGw1.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Install IIS URL Rewrite Module:  <br/>
<img src="https://imgur.com/465p9DH.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Once those have installed I will create a PHP directory on the C drive:  <br/>
<img src="https://imgur.com/CEsoJp6.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Now I'll download PHP and extract the zip file in the PHP directory I just made:  <br/>
<img src="https://imgur.com/LoYw0cZ.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Download Microsoft Visual C++:  <br/>
<img src="https://imgur.com/SocF97p.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Download MySQL:  <br/>
<img src="https://imgur.com/dFdQagT.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next, I have to setup the login credentials and I'll write them down just so I remember, since this is only a project. Do not write passwords down in real life:  <br/>
<img src="https://imgur.com/SeJVW6M.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Open IIS as an admin:  <br/>
<img src="https://imgur.com/gFmrka6.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next go to PHP Manager> Register new PHP version and then select the file shown:  <br/>
<img src="https://imgur.com/nlD4F1L.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Go back to osticketVM Home and hit Restart under Manage Server on the right side:  <br/>
<img src="https://imgur.com/F83Qw2a.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next I'll download osTicket and copy the upload file to the wwwroot file in the inetpub directory:  <br/>
<img src="https://imgur.com/op4Cs2g.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Rename upload file to osTicket:  <br/>
<img src="https://imgur.com/ZBLsJsB.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Reload IIS and restart the server as I did before, then click Browse *80 (http) on the right side:  <br/>
<img src="https://imgur.com/JnqQOJD.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
This page should open:  <br/>
<img src="https://imgur.com/J4E020x.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Notice some extensions are not enabled. I'll enable a few of those in IIS. Go to Sites> Default Web Site> osTicket Click PHP Manager> Enable or disable an extension. Enable php_imap.dll, php_intl.dll, and php_opcache.dll:  <br/>
<img src="https://imgur.com/ZJCdcDV.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Note the changes here:  <br/>
<img src="https://imgur.com/yZbaGml.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next browse in file explorer to C drive> osTicket> include> ost-sampleconfig.php and remove the "sample" from the name:  <br/>
<img src="https://imgur.com/k6cfJaY.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Right-click on ost-config.php> Properties> Security> Advanced> Disable Inheritance> Remove all inherited permissions from this object:  <br/>
<img src="https://imgur.com/G154DIx.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Click on the add buton to add permissions to the file> Select a principle> type "everyone"> Check> OK> check all permissions> OK> apply> OK:  <br/>
<img src="https://imgur.com/clvmCHq.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Hit continue on the osTicket web page in the browser and fill out the set up page:  <br/>
<img src="https://imgur.com/dYLO5Ot.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Before database set up we'll have to connect the database using HeidiSQL. Install HeidiSQL from setup links:  <br/>
<img src="https://imgur.com/tyyovzJ.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
In HeidiSQL click New> Username = root> Password = mySQL password from mySQL setup> Open:  <br/>
<img src="https://imgur.com/xoW0TMX.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
In HeidiSQL right click Unnamed> Create> New Database> Name it osTicket> OK. Then continue to fill out the database portion of osTicket setup. Click Install Now when done.:  <br/>
<img src="https://imgur.com/w4VpziO.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Last steps, for clean up go to C drive> inetpub> wwwroot> osTicket and look for the setup file and delete it. Then go to C drive> inetpub> wwwroot> osTicket> include right click on ost-config.php> Properties> Security> Advanced> Select Everyone and click edit> only leave Read & Execute and Read checked, then apply settings:  <br/>
<img src="https://imgur.com/o4GB231.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
  
<h2>osTicket Installed!</h2>

<b>osTicket is now installed and ready for use! In the next project I will walk you through how to configure agents, their permissions and access, users, and more!  </b>
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
