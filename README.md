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
 <b>Creating powershell script for all our users in active directory, sample users</b> <br/>
</p>
https://user-images.githubusercontent.com/108043108/176961801-c6ed71d1-4f12-4775-82d5-853cac5260da.mp4
<br />
<br />
<p align="center">
<b>Great! Now that Remote Access is installed and configured, it is now time to Install a DHCP Server. This will allow our Windows 10 clients to be assigned an IP address and allow them to browse the internet.</b> <br/>
</p>

https://user-images.githubusercontent.com/108043108/176962485-229ae237-b9e9-4178-b857-4741d318d33e.mp4

<br />
<br />
<p align="center">
<b>Now to configure the DHCP and setup a scope. The whole purpose of DHCP is to allows computers on the network to automatically be assigned an IP address. The scope I will be creating will give assign IP addresses in a range, the range being 172.16.0.100-200 so the DHCP will effectively be able to give out 100 IP addresses. I also set the amount of time the IP addresses can be leased out to 20 days. The reason for the lease is when an IP address is assigned, it can't be used by other devices. So if I only have 100 IP addresses and 100 are used, new devices can't be assigned an IP address on the network meaning they can't connect to the internet. A lease is just an amount of time an IP address can be owned (leased) by a device before being recycled. If this was for example a Café that offers wifi and the average time a person spent inside said Café was 2 hours, it would make no sense to lease an IP address to them for 20 days. That would effectively lock up that IP address for that amount of time and no one else could use it. If this were a Café I would recommend setting the lease duration to under 4 hours and give a bigger range. Since this is only VM, the lease duration doesn't matter.</b> <br/>
</p>

https://user-images.githubusercontent.com/108043108/176962663-866da4fd-de06-4549-9b86-3925a674bb3d.mp4

<br />
<br />
<p align="center">
<b>To get my powershell script from the internet I need to be able to browse the web. I have to disable the security features on the Domain Controller. If this was an actual production environment I would never do this, security risk. Since this is only a lab environment for myself it is not an issue. I could browse the internet without doing this step but it is annoying because it will spam us warnings for every webpage we visit</b> <br/>
</p>

https://user-images.githubusercontent.com/108043108/176964588-4b7ab303-c338-4037-8142-996bde30cac3.mp4

<br />
<br />
<p align="center">
<b>Now that Active Directory is configured and my Domain Controller is configured as well, I use a Powershell script to create over 1000 user accounts</b> <br/>
</p>
<img src="https://i.imgur.com/ISI6fPb.jpg" height="80%" width="80%" alt="Using Powershell to create 1000 user accounts in bulk"/>
<br />
<br />
<p align="center">
<b>Here is a video of the script running!</b> <br/>
</p>

https://user-images.githubusercontent.com/108043108/176953922-60b62f24-fd3f-41b4-ae0c-8780afc7b708.mp4

<br />
<br />
<p align="center">
<b>The script has run successfully and the output confirmations that the user accounts has been created looks amazing. There were some duplicates that were not created, but that is easily solved by adding to the Powershell script a few lines of code that will tell it what to do in case duplicates occur. Perhaps something along the lines of "If a duplicate occurs, add a 1 to the end of the account name" for example. If you want to see the full code used, refer to the top of this repository. The script is under CREATE_USERS.ps1</b> <br/>
</p>
<img src="https://i.imgur.com/MhlDg1o.jpg" height="80%" width="80%" alt="Using Powershell to create 1000 user accounts in bulk"/>
<br />
<br />
<p align="center">
<b>It is now time to create a new Virtual Machine that will act as a user in the domain. I name this machine CLIENT1</b> <br/>
</p>
<img src="https://i.imgur.com/wvBRBWf.jpg" height="80%" width="80%" alt="Setting up new Virtual Machine"/>
<br />
<br />
<p align="center">
<b>I configure the network adapter so that it is not NAT and can't connect to the internet on my local network. The only way this Virtual Machine should be able to connect to the internet is by being assigned an IP from the DC on the Server VM. Refer to the Diagram at the beginning. I have to change the network adapter to be on the same internal network as the Domain Controller, in this case VMnet0</b>  <br/>
</p>
<img src="https://i.imgur.com/6IjDUEj.jpg" height="80%" width="80%" alt="Configuring the VM Network Adapter"/>
<br />
<br />
<p align="center">
<b>After configuring a separate virtual machine that will simulate an employee logging into the domain. Lets kill two birds with one stone by renaming the computer CLIENT1 and clicking the box to become a member of the mydomain.com domain. I am prompted to give my log in credential and I chose to use the Administrator account I set up earlier</b>  <br/>
</p>
<img src="https://i.imgur.com/ceB3tDJ.jpg" height="80%" width="80%" alt="Configuring the Client VM"/>
<br />
<br />
<p align="center">
<b>I Successfully join the domain as a member!</b>  <br/>
</p>
<img src="https://i.imgur.com/euBgIXf.jpg" height="80%" width="80%" alt="Configuring the Client VM"/>
<br />
<br />
<p align="center">
<b>I log into a user account I created from the Powershell script to test if everything is configured correctly. Instead of logging into the user account created when I made the virtual machine, I try to log into a user created account in MYDOMAIN</b>  <br/>
</p>
<img src="https://i.imgur.com/dPeaySX.gif" height="80%" width="80%" alt="Testing The Environment"/>
<br />
<br />
<p align="center">
<b>Running command promt to see if the client VM is getting the IP address properly assigned by the DC. We can see that I was properly leased an IP address by the domain controller (circled red) and when I ping the domain, it works (circled yellow)</b>  <br/>
</p>
<img src="https://i.imgur.com/QBWuCS9.jpg" height="80%" width="80%" alt="Testing The Environment"/>
<br />
<br />
<p align="center">
<b>A final test to see that the work environment and bulk users I created is working</b>  <br/>
</p>
<img src="https://i.imgur.com/j6ZRHPz.jpg" height="80%" width="80%" alt="Testing The Environment"/>
<br />
<br />
<p align="center">
<b>I head back into my server VM and check the DCHP to see how many addresses has been leased. We can see here circled in red that my CLIENT1 Virtual Machine has been leased an address. If this was a real company environment there would be hundreds, if not thousands of leased addresses in this folder depending on what the lease duration is of course! I set mine to 20 days in this environment</b>  <br/>
</p>
<img src="https://i.imgur.com/qvNKa7v.jpg" height="80%" width="80%" alt="Checking leased addresses"/>
<br />
<br />
<p align="center">
<b>Here is another way to check how many computers or devices are currently connected to the domain. We can see that my CLIENT1 computer is being properly recognized in Active Directory. Again, if this was a real environment there would probably be thousands of devices in this folder</b>  <br/>
</p>
<img src="https://i.imgur.com/A2dMovv.jpg" height="80%" width="80%" alt="Checking the computers in Active Dirctory"/>
<br />
<br />
<p align="center">
<b>Here I am scrolling through all the User accounts I created with Powershell. Over 1000 has been created!</b>  <br/>
</p>
<img src="https://i.imgur.com/POpjnf9.gif" height="80%" width="80%" alt="Checking the Users created by Powershell"/>
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
