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

