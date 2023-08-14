<h1>Active Directory & Powershell</h1>



<h2>Description</h2>
First I will set up a windows server virtual machine with one internal and one external Network Adapter. After that I will assign a new IP address to the internal network and change its DNS server address to the loopback address (itself). The next step includes installing Active Directory Domain Services and create a Domain + an admin account. Furthermore I install Remote Access Server (RAT) + Network Adress Translation (NAT) so that the Windows 10 Client can access the private network, but still get access to the internet via the Domain Controller. After setting up a DHCP server the windows 10 client should be able to get an IP address and browse the internet successfully, even though it is on the internal network. Now I am ready to add users with the help of a quick powershell script. The final step is to add the second windows 10 VM that poses as the client to the network and test, if I have internet access via the domain controller.
<br />


<h2>Languages, Applications and Utilities Used</h2>

- <b>Active Directory</b>
- <b>Powershell</b>


<h2>Environments Used </h2>

- <b>Windows 10 Client & Server</b>
- <b>Oracle VM VirtualBox</b>

  
<h2>What I learned</h2>

- <b>Setting up a windows server, with DNS, DHCP, RAT&NAT</b>
- <b>Using Powershell to write and execute a script</b>
- <b>Adding users to Active Directory</b>

<h2>Program walk-through:</h2>

<p align="center"> 
 <b>On the windows server, check which one is the internal and external network</b>
  
  ![1 checking which one is internal and external network](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/1811229b-7999-4d66-bfce-a55cc96d943e)

  <p align="center"> 
 <b>Rename the PC to domainc</b>

![2 rename the pc](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/8b7bb82c-f5d7-4366-80b9-f14cd912a7e7)

<p align="center"> 
 <b>Assigning an ip address to the internal network and setting its DNS server address to the loopback address (itself)</b>

 ![3 assigning an ip address to the internal network and setting its DNS server address to the loopback address](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/59685102-9e45-4a65-9b2f-b05dc20d704d)

 <p align="center"> 
 <b>Installing active directory on the server</b>

![4 select the server to add to](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/29ec7f1d-cba3-4179-8a51-d89b5c808684)

![5 select Active directory domain services](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/557e9d41-08b6-4b3c-9b0e-97b5aac484f3)

![6 installing AD DS](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/6f1ede5c-6832-46f8-a008-5cfdb7e97869)

 <p align="center"> 
 <b>Creating the domain</b>

![7 creating the domain](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/a640014a-c42a-457e-a681-267030e438a4)

 <p align="center"> 
 <b>Creating an organisational unit called _ADMINS</b>

![8 creating an OU called _ADMINS](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/44f6079e-fc5d-4b13-a75a-32cf36aec5ed)

 <p align="center"> 
 <b>Creating an admin user called jpukall </b>

![9 creating an admin user called jpukall](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/391aa4da-4d84-4600-9d20-87df826b7d91)

 <p align="center"> 
 <b>Making this account an admin</b>

![10 making this account an admin](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/78c423b1-817d-426e-af05-dfac14d84c29)

 <p align="center"> 
 <b>Logging in as that user</b>

![11 logging in as that user](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/7e125181-af5b-401b-bcc7-459727027e0b)

 <p align="center"> 
 <b>Installing RAT/NAT</b>

![12 installing rat and nat](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/d1f5b311-16d6-448c-bad2-92bedd049270)

 <p align="center"> 
 <b>Enable and configure routing & remote access</b>

![13 configure and enable routing](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/931e492e-396f-47c0-90af-5e0d31ec12a0)

 <p align="center"> 
 <b>Allow internal clients to connect to the internet using one public ip address</b>

![14 allow internal clients to connect to the internet using one public ip address](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/922a0a88-80ae-44de-9609-fd9a47268947)

 <p align="center"> 
 <b>Select the internet network</b>

 ![15 select the internet Network interface](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/a54c28dc-037b-4006-84dd-1857c2a69c33)

  <p align="center"> 
 <b>It worked!</b>

 ![16 it worked great](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/3c4c90d8-a7eb-4bf6-b3c2-38a155d9e5eb)

  <p align="center"> 
 <b>Add DHCP to the server</b>

 ![17 add dhcp to the server](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/48e2d7aa-09dd-4130-ad2c-4c122f533668)

  <p align="center"> 
 <b>The DHCP server is down, we have to change that.</b>

 ![18 dhcp server is down, we have to change that](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/8c7e936d-3acb-4568-b062-7c24ae11a5ad)

  <p align="center"> 
 <b>Configuring DHCP</b>

![19 configurating dhcp](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/5fc7bef0-2de0-41e9-be36-d5dc7debb505)

 <p align="center"> 
 <b>Ip address with NAT</b>

![20 dc ip adress with nat on it](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/3d8c491a-439c-4da3-8ef6-6455e8aa2851)

 <p align="center"> 
 <b>It seems to be working</b>

![21 its working!](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/bf1abf29-beeb-4ec9-b70e-57cedba8745c)

 <p align="center"> 
 <b>Time to use a powershell script to add users to Active Directory</b>

![22 use powershell script to add users](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/12dfc882-a0e4-461c-84ed-7cf297578356)

 <p align="center"> 
 <b>Names.txt is referencing this name list with 1000 users</b>

 ![23 names txt is referencing this wordlist with 1000 users](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/480e5565-df7d-4bf0-8e14-c0349eccc448)

  <p align="center"> 
 <b>The loop will run for every single user in the names.txt file</b>

![24 the foreach loop will run for every single user in the names txt list](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/45786f7b-0789-4630-a8d3-b27b57bac802)

 <p align="center"> 
 <b>Lets run the script. It seems to be working.</b>

![25 script is running and working](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/9f5e9579-d805-438d-b278-df4c41bea8fd)

 <p align="center"> 
 <b>Yes it worked!</b>

![26 it worked!](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/a8488ef4-1a32-400d-bff5-a5839715cbc1)

 <p align="center"> 
 <b>Look, that's me!</b>

 ![27 hey thats me!](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/d90a0a74-c102-44b5-bde9-44ee32256eed)

 <p align="center"> 
 <b>The client should now have internet access. Sadly my windows10.iso file is defaulting to the home version of windows (because my main PC has windows Home and it registers the key), so i currently cant conclude the final test. I tried a workaround but I didnt get it to work yet. I am pretty sure it works though. I will finish this task later.
   
  
     
 [-------->Workaround](https://community.spiceworks.com/topic/1902013-windows-10-pro-install-on-home-system)
 
 </b>

 ![28 this should work](https://github.com/ArtyWatts/ActiveDirectory-Powershell/assets/141881183/cfb1c9b6-e247-4f61-963a-1b28145d7f21)


<p align="center">
  












 


 
