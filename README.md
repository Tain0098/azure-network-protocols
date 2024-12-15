<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [Canva: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.canva.com/design/DAGY83u1CKw/WiSMuRGJmxM_apZaB7YKig/edit?utm_content=DAGY83u1CKw&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1 Create Windows VM
- Step 2 Create Linux VM

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/MUjui37.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Create our Virtual Machines
  
Create a Resource Group

Create a Windows 10 Virtual Machine (VM)

While creating the VM, select the previously created Resource Group

While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet in Networking

Create a Linux (Ubuntu) VM (You pick that in the Image section)


While creating the VM, select the previously created Resource Group and Virtual Network—the Virtual Network MUST BE THE SAME.

Authentication type: Username/Password

Ensure both VMs are in the same Virtual Network / Subnet 

Both VM sizes must be 2 or 4 vcpus, if not they are too slow


*

<p>
<img src="https://i.imgur.com/uFLhDld.png"80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observe ICMP Traffic)
  
If using Mac, install Microsoft Remote Desktop

Use Remote Desktop to connect to your Windows 10 Virtual Machine (Type in on Windows search bar)

You'll need the VM IP address/username/password

Within your Windows 10 Virtual Machine, Install [Wireshark](https://www.wireshark.org)

Open Wireshark

Click on the Ethernet and then the  blue shark fin icon on the top left to run the program 

Within Wireshark, filter for ICMP traffic only

<p>
<img src="https://i.imgur.com/Dd8dntY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM

Now Open Powershell in the Windows Search Bar

Type ping Linux VM private IP(you can get it in Azure)

Observe ping requests and replies within WireShark

From The Windows 10 VM, open the command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in Wireshark

Powershell works best in this case

*

<p>
<img src="https://i.imgur.com/1MXIvHd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observe SSH Traffic
  
In the windows-vm

Back in Wireshark, start a packet capture-up

Filter for SSH traffic only

From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)

Open PowerShell, and type: ssh Linuxusername@(private IP address)

Type "yes" when asked. You can already see changes in Winreshark

Now, This is Important

You can not see the type of the Linux VM's password but it is typing

And for whatever reason sometimes the password will not work even when you got it right.

In that case, go to Azure, to the Linux VM, and click Restart(you can also restart after creating the VM)







Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark

Exit the SSH connection by typing ‘exit’ and pressing [Enter]


