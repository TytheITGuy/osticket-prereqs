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
Navigate to Microsoft Azure and create a virtual machine and a new resource group: 

![01-Creating a VM and Resource Group](https://github.com/user-attachments/assets/6f52402e-e6cf-439c-b99d-dd140e18f522)

<p align="center">
Be sure to pick the correct windows image type

![02-Picking the image Type](https://github.com/user-attachments/assets/4aaecebc-9869-45ba-a15f-1db72cc12cde)

<p align="center">
Now Deployment is in progress

![03-Deployment in progress](https://github.com/user-attachments/assets/cd08245f-c4b7-4deb-8768-14ec61260898)

<p align="center">
Once it has been created I'll use Remote Desktop Connection to connect to the VM: 

![04-Connecting with Remote Desktop](https://github.com/user-attachments/assets/8a8fa616-db6d-46f1-835c-371f62c5e28c)

<p align="center">
Once I've connected to the VM I will install and enable IIS (Internet Information Servies) 

![05-Internet Information Services](https://github.com/user-attachments/assets/b1979dbb-88b3-40c8-8a46-6079cd177a0b)


<p align="center">
DO NOT FORGET to turn on CGI: 

![06-CGI](https://github.com/user-attachments/assets/c8b5023a-bf51-4503-b842-723f5c412db2)

<p align="center">
I can test that the web server installed correctly by typing in the loopback IP (127.0.0.1) in the internet browser and this page should load:  

![07-Loopback Address](https://github.com/user-attachments/assets/2911670f-77c8-43ae-8137-cfa5c85b913e)

<p align="center">
Now I need to install PHP manager for IIS Setup:  

![08-PHP Manager](https://github.com/user-attachments/assets/96a8a03c-1b66-4af0-ae1d-c59169e95a60)

<p align="center">
Install IIS URL Rewrite Module:  

![09-Rewrite Module](https://github.com/user-attachments/assets/c653f688-7efe-42be-b356-7bf073990679)

<p align="center">
Once those have installed I will create a PHP directory on the C drive:  

![10-PHP Folder](https://github.com/user-attachments/assets/d0b393e2-e685-48c2-a837-a1a804673409)

<p align="center">
Download Microsoft Visual C++: 

![11-Installing C++](https://github.com/user-attachments/assets/92c11b3b-deac-40ac-a167-e15ee2ce1566)


<p align="center">
Download MySQL:  
  
![12-Installing My SQL](https://github.com/user-attachments/assets/45d8ef33-fbba-4900-b1b4-016e6bf91a41)


<p align="center">
Next, I have to setup the login credentials and I'll write them down just so I remember, since this is only a project. Do not write passwords down in real life:  <br/>
<img src="https://imgur.com/SeJVW6M.png" height="100%" width="100%" alt="Setting Up in Azure"/>
<br />
<br />

<p align="center">
Open IIS as an admin:  

![14-opening up IIS Manager](https://github.com/user-attachments/assets/ab4c2c1d-dea3-4339-9124-1e4b029d0feb)

<p align="center">
Next go to PHP Manager> Register new PHP version and then select the file shown:  

![15-Register new php version](https://github.com/user-attachments/assets/b88920c0-c46e-431d-94a5-6007b99416ab)

<p align="center">
Next I'll download osTicket and copy the upload file to the wwwroot file in the inetpub directory:

![18- Copy folder into root](https://github.com/user-attachments/assets/216fee10-3849-4136-a5b7-32658c483f03)

<p align="center">
Rename upload file to osTicket:  


![19-Renaming the file](https://github.com/user-attachments/assets/cfeaa177-705a-43ae-8c4a-4f2e4846cbf1)

<p align="center">
Reload IIS and restart the server then click Browse *80 (http) on the right side and this page should open: 

![20-Browsing osTicket Site](https://github.com/user-attachments/assets/989bde8a-0484-4c8c-aaed-7de1707783e6)

<p align="center">
Notice some extensions are not enabled. I'll enable a few of those in IIS. Go to Sites> Default Web Site> osTicket Click PHP Manager> Enable or disable an extension. Enable php_imap.dll, php_intl.dll, and php_opcache.dll: 

![22- Enable these extensions](https://github.com/user-attachments/assets/83a72f20-4b34-4a7b-aa03-c35feac4e9cb)

<p align="center">
Next browse in file explorer to C drive> osTicket> include> ost-sampleconfig.php and remove the "sample" from the name:  

![23- Rename OST config](https://github.com/user-attachments/assets/b4d7bbaa-17a5-4be1-b070-3ebeb9e3a1f6)

<p align="center">
Right-click on ost-config.php> Properties> Security> Advanced> Disable Inheritance> Remove all inherited permissions from this object.
Click on the add buton to add permissions to the file> Select a principle> type "everyone"> Check> OK> check all permissions> OK> apply> OK:  

![24- Assign permissions for all](https://github.com/user-attachments/assets/263de237-d32a-4acc-8b2c-8ae1b9585e23)

<p align="center">
Hit continue on the osTicket web page in the browser and fill out the set up page: 

![24-osTicket Basic installation info](https://github.com/user-attachments/assets/0fa7cd85-4203-4bab-bd7b-c46e833efb02)

<p align="center">
Before database set up we'll have to connect the database using HeidiSQL. Install HeidiSQL from setup links: 

![25-Install Heidi SQL](https://github.com/user-attachments/assets/a914134e-889b-4575-9317-ad00f310576a)

<p align="center">
In HeidiSQL right click Unnamed> Create> New Database> Name it osTicket> OK. 

![26-Create a new SQL database](https://github.com/user-attachments/assets/d9e678b5-f486-4717-8d0f-59f551de415d)

<p align="center">
Then continue to fill out the database portion of osTicket setup. Click Install Now when done.:  <br/>

![27-osTicket is installed](https://github.com/user-attachments/assets/c77f4c32-3b16-4b56-8b99-2de91b6965d8)



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
