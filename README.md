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

<p>
In this lab, I will be observing various network traffic and experiment with the network security groups using Azure. 
</p>
<img width="2560" alt="1" src="https://github.com/user-attachments/assets/ca5f46db-3f95-4127-9611-0d77a3e3bf52" />
<p>
You first need to create a resource group on Azure for the virtual network and the virtual machines to live in. 
</p>
<img src=<img width="2560" alt="2" src="https://github.com/user-attachments/assets/f23eea2e-7b18-4935-b860-5322bdaf1c9e" />
</p>
<p>
I will create two virtual machines. First, I will create the Windows 10 virtual machine. 
</p>
<img src=<img width="2560" alt="3" src="https://github.com/user-attachments/assets/1ba4afdf-c7ba-47df-b437-0d18155c6e6f" />
</p>
<p>
Then, I will create a Linux virtual machine. The important thing for these virtual machines is that the virtual network needs to be the same so they can talk to each other.  
</p>

<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
