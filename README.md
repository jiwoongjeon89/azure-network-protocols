<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

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

- Step 1: Create virtual machines on Azure
- Step 2: Observe various network traffics

<h2>Actions and Observations</h2>

<h3>Creating the Virtual Machines on Azure</h3>
<p>
In this lab, I will be observing various network traffic and experiment with the network security groups using Azure. 
</p>
<img width="2560" alt="1" src="https://github.com/user-attachments/assets/ca5f46db-3f95-4127-9611-0d77a3e3bf52" />
<p>
You first need to create a resource group on Azure for the virtual network and the virtual machines to live in. 
</p>
<img width="2560" alt="2" src="https://github.com/user-attachments/assets/2d1dedd6-fb06-4bd6-94c2-c6c12e49d3f5" />
</p>
<p>
I will create two virtual machines. First, I will create the Windows 10 virtual machine. 
</p>
<img width="2560" alt="3" src="https://github.com/user-attachments/assets/37441ed4-2962-4b59-a95b-a5b94ca0c292" />
</p>
<p>
Then, I will create a Linux virtual machine. The important thing for these virtual machines is that the virtual network needs to be the same so they can talk to each other.  
</p>
</p>
<p>

<br />
</p>
<h3>Observing ICMP traffic</h3>
First we will be observing the ICMP traffic. I will try to ping the Linux virtual machine from the Windows virtual machine.  
<img width="1282" alt="4" src="https://github.com/user-attachments/assets/57a8eb13-aa70-4980-982f-e90ba1c840ae" />

</p>
<p>
I am using a MacBook so I downloaded the Windows App to access the virtual machines.  
</p>

<img width="2560" alt="6" src="https://github.com/user-attachments/assets/991094c4-f015-4013-8fb2-06c638eec752" />
<p>
  I have logged into the Windows virtual machine and I’ll be downloading Wireshark so we can track the different network traffics easily.  
</p>
<img src="https://imgur.com/V4RJdqJ.png"/>
I opened up Wireshark and filtered it so we can only see the ICMP traffic.  
<img src="https://imgur.com/uTp75y8.png"/>
I opened PowerShell and pinged the Linux virtual machine using the command ‘ping 10.0.0.5’. 
We can observe that the requested ping from the Windows virtual machine (private address: 10.0.0.4) is getting a response from the Linux virtual machine (private address: 10.0.0.5). 
<p>

  
</p>
<h3>Building a Firewall to block ICMP traffic </h3>
Now, we will configure a Firewall on the Linux virtual machine on Azure and observe what it does.  
<img src="https://imgur.com/BsBsh8h.png"/>
This is the Network Security Group page of the Linux virtual machine on Azure.  
<img src="https://imgur.com/i6uuKr3.png"/>
We are going to add an inbound security rule that will deny any ICMP traffic (pings) from any outside sources.  
<img src="https://imgur.com/d5w9SUz.png"/>
When I ping the Linux virtual machine now, it says request timed out which means that the Firewall that I configured is blocking the incoming pings.  
<p>

  
</p>
<h3>Observing SSH traffic </h3>
Now, we will be making a SSH connection to the Linux virtual machine from the Windows virtual machine.  
<img src ="https://imgur.com/AorC42E.png"/>
To make a SSH connection we need to open PowerShell and use the command ‘ssh <Username>@<private IP address>’. I will also filter Wireshark to only show SSH traffic. 
<img src ="https://imgur.com/00o5YyE.png"/>
Now I am connected to the Linux virtual machine and can perform different commands such as ‘id’, ‘hostname’, ‘uname -a’... etc. 
<p>

  
</p>
<h3>Observing DHCP traffic</h3>
Now, we will be observing the DHCP traffic. 
<img src="https://imgur.com/3wwpsJZ.png"/>
We can just use the command ‘ipconfig \renew’ to observe the DHCP traffic. However, this way doesn’t show all the steps of the DHCP.  
<img src="https://imgur.com/vU6UukW.png"/>
To see all the Release, Discover, Offer and Request steps of the DHCP, you first need to make a .bat file that will perform run the individual commands of release and renew.  
<img src="https://imgur.com/icdMa1a.png"/>
Then, when I ran the .bat file, you can see how the Windows virtual machine lost its IP address and requested the DHCP server for a new address sowing all the steps that it took for the DHCP.
<p>

  
</p>
<h3>Observing DNS traffic </h3>
Now, we will be observing the DNS traffic by using the command ‘nslookup’ on PowerShell. 
<img src="https://imgur.com/m0uJOMv.png"/>
I looked up YouTube’s IP addresses and it gave me these. You can also see the DNS traffic on Wireshark.  
<p>

  
</p>
<h3>Observing RDP traffic </h3>
Now, we will be observing RDP traffic. 
<img src="https://imgur.com/Y97cZ49.png"/>
I am technically already doing remote desktop control on the Windows virtual machine through Windows App. Therefore, when I filter for RDP traffic (tcp.port == 3389), there already is traffic.   
