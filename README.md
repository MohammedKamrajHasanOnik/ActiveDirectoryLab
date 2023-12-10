<h1>Active Directory Home Lab With Bulk User Creation(Educational Purposes followed credit to JonCyberGuy)</h1>

<h2>Description</h2>
This project is a guide of how I created an Active Directory home lab Environment using VMWare. I set up a Microsoft Server to run Active Directory on it. I then configure a Domain Controller this will allow me to run a domain. After that I ran a Powershell script to create users in Active Directory and executed those log into to the new created accounts on another client that uses the domain I set up to connect to the internet. This lab simulates a business environment. Within this lab I will need as follows  Microsoft Server 2019 ISO, A Windows 10 Enterprise ISO, VMWare and a Powershell script.
<br />

<h2>Languages and Utilities Used</h2>

- <b>Active Directory</b> 
- <b>PowerShell</b>
- <b>CMD</b>

<h2>Environments Used </h2>

- <b>Oracle VM VirtualBox</b>
- <b>Microsoft Server 2019</b>
- <b>Windows 10</b> (21H2)

<h2>Links to programs and scripts required</h2>

- <b>Oracle Virtual Box VMWare:</b> https://download.virtualbox.org/virtualbox/7.0.12/VirtualBox-7.0.12-159484-Win.exe
- <b>Oracle Virtual Box Extension Pack:</b> https://download.virtualbox.org/virtualbox/7.0.12/Oracle_VM_VirtualBox_Extension_Pack-7.0.12.vbox-extpack
- <b>Microsoft 2019 Server ISO:</b> https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019
- <b>Windows 10 ISO:</b> https://www.microsoft.com/en-us/software-download/windows10

<h2 align="center">Program guide</h2>

<p align="center">
<b>The network diagram as shown I will be utilizing for the project</b> <br/>
<img src="https://i.imgur.com/ceuZrI3.jpg"/>
<br />
<br />
<br />
<b>Creating Server 2019, assigning it 2048mb memory ram approx 2gb and 3 processors VM</b> <br/>
<img src="https://i.imgur.com/nqjMOCy.jpg"/>
<br />
<br />
<br/>
<b>Assigning it 2048mb memory ram approx 2gb and 3 processors VM</b> <br/>
<img src="https://i.imgur.com/3rNQbeE.jpg"/>
<br />
<br />
<br/>
<b>Allocating virtual hard disk size of 20gb</b> <br/>
 <img src="https://i.imgur.com/37XGBtj.jpg" height="80%" width="80%" alt="Configuring the Network Adapter for the Domain Controller Virtual Machine"/>
<br />
<br />
<br />
<b>Succesfully Installed Windows 10 on Server 2019 ISO on Windows 10</b> <br/>
<img src="https://i.imgur.com/KU3zbLY.jpg" height="80%" width="80%" alt="Configuring the Network"/>
<br />
<br />
<br />
<b>After downloading Windows Server 2019 on the Virtual Machine the first thing I have to do as follows is too configure the two network Adapters I have. One is dedicated to the internet which is running NAT and one is the dedicated internal VM network</b> <br/>
<img src="https://i.imgur.com/ZbMWVag.jpg" height="80%" width="80%" alt="Configuring the Network"/>
<br />
<br />
<br />
<b>Now I have to figure out which NIC is Internet and which NIC is internal. Ethernet 1 renamed to _INTERNET1_ It is internet NIC because its a COMCAST DNS Server IPv4 address</b> <br/>
<img src="https://i.imgur.com/v3nA5qW.jpg" height="80%" width="80%" alt="Configuring the Network"/>
<br />
<br />
<br />
<b>Ethernet 2 Nic is Internal Nic because of the Autoconfiguration IPv4 has been sent to the DHCP and unable to find IPv4 address and returned by the server as automatically assigned and Ethernet 2 has been renamed to X_Internal_X1</b> <br/>
<img src="https://i.imgur.com/5reINZo.jpg" height="80%" width="80%" alt="Configuring the Network"/>
<br />
<br />
<br />
<b/> As both of the ethernet adapters names have changed and visible as depicted Ethernet 1 named as _INTERNET1_ and Ethernet 2 named as X_Internal_X1</b> <br/>
<img src="https://i.imgur.com/9T3ZnJl.jpg" height="80%" width="80%" alt="Configuring the Network"/>  
<br />
<br />
<br />
<b> I resolve the Internal network adapter and assign it the IP address based on the diagram above (172.16.0.1) I do not have to give it a default gateway because the Domain Controller as such is the gateway. As for the DNS server I assign it an IP based on the diagram insinuated, a loop back address which will ping itself as required for installing Active Directory. </b> <br/>
<img src="https://i.imgur.com/FZ1VhvZ.jpg"/>
<br />
<br />
<br />
<b>Since I know which network adapter is Internet NIC and Internal NIC Internal and External. I rename the pc from Domain Controller to DController as shown I have also restarted it as required and went back into settings and checked. This prompts a restart which is required</b> <br/>
<img src="https://i.imgur.com/zGWGDNS.jpg" height="80%" width="80%" alt="Renaming the PC"/>
<br />
<br />
<br />
<b>After rebooting in I download Active Directory with its additional required features.</b> <br/>

</p> 
https://github.com/MohammedKamrajHasanOnik/ActiveDirectoryLab/assets/152878913/8623891a-753f-4bea-8382-be9387843ae5

<br />
<br />
<p align="center">
<b>I installed Active Directory Domain Services, but have not let the computer account be as the domain. Now I have to actually create the domain, (video is a bit lengthy skipped video however reboot needed)</b> <br/>
</p>

https://github.com/MohammedKamrajHasanOnik/ActiveDirectoryLab/assets/152878913/de7bcc0a-6816-4b25-9ca3-066591356c31

<br />
<br />
<p align="center">
<b> The server has been upgraded to a domain, it forces a restart, I log in and I see MYDOMAIN in front of my administrator</b> <br/>
</p>
<img src="https://i.imgur.com/BNoPFbh.jpg" height="80%" width="80%" alt="Renaming the PC"/>
<br />
<br />
<p align="center">
<b>Now the opposite of using the built in Admin account, I will create a dedicated  Admin account a-monik as illustrated in the video as well as assign with active directory user and computers organizational unit and create the account, passwords and add the admin privillage in group setting assigning Domain Admin, I also have logged into windows 10 with the new a-monik account </b> <br/>
</p>

https://github.com/MohammedKamrajHasanOnik/ActiveDirectoryLab/assets/152878913/ad7d5ce9-5db4-419e-b480-c58d979874a1

<br />
<br />
<p align="center">
<b>I created a remote access server/ network address translation, the purpose of this is to allow when we make our windows 10 client to allow this client to be in this private virtual network in an analogy, but still have the benefits to access the internet through the domain controller, routing and remote access application settings, through RAS/NAS!</b> <br/>
</p>

https://github.com/MohammedKamrajHasanOnik/ActiveDirectoryLab/assets/152878913/92d1d0b7-4283-4763-9dc2-a77562b30657

<br />
<br />
<p align="center">
<b> Setting up the dhcp server in our domain controller, which will allow our windows 10 clients get an ip address to let them browse the internet just like an anology of a school account, DHCP DNS is set up now</b> <br/>
</p>

https://github.com/MohammedKamrajHasanOnik/ActiveDirectoryLab/assets/152878913/b88997b0-3d8d-49b7-8c48-a8c728c3e404

<br />
<br />
<p align="center">

 <br />
 <br />
 <br />
  <b> Making a configuration to not get spam messages and let us browse the internet through the domain controller by turning of IE Enhanced Security Configuration feature </b> <br/>
</p>

https://github.com/MohammedKamrajHasanOnik/ActiveDirectoryLab/assets/152878913/c199bda1-07e8-48dc-868d-8a28abf385f8
  <br />
  <br />
 <br />
 <b>Creating powershell script for all our 1000 more or less users in active directory, sample users</b> <br/>
</p>
https://github.com/MohammedKamrajHasanOnik/ActiveDirectoryLab/assets/152878913/cb95f1ec-affb-4521-9719-2f6b1fda925b

<br />
<br />
<p align="center">

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
