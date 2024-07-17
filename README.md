<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

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

- Create a resource group and 2 Virtual Machines
- Login into Windows 10 Virtual Machine
- Download Wireshark on Window's 10 Virtual Machine
- Track certain Network Protocols with Wireshark

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/LM2rhcd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I first created my Windows virutal machine, as you can already see I already created the resource group called "labcc1133". I am going to use this virtual machine to track network traffic by using Wireshark. 
</p>
<br />

<p>
<img src="https://i.imgur.com/0ROvHEL.pngg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next I created an Ubuntu Virtual Machine. I am going to use this virtual machine's private IP address and ping it on the Windows VM to see if the network connection is responsive.
</p>
<br />

<p>
<img src="https://i.imgur.com/2iCwfpb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I logged into the Windows 10 VM by pasting it's public IP address into the Remote Desktop Connection and used my azure login credentials that I created when I was setting up the Windows 10 VM in Azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/VboTUV7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step was to download Wireshark on the Windows 10 VM by typing wireshark on the google.com search bar and downloading it from it's website. I am going to use Wireshark to track specific types of network traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/ojOqPi4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The first thing I did was ping the private IP address of my Ubuntu server on the Window's 10 powershell and observed the traffic on Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/vCfkpud.png"80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I then pinged the private IP address of the Ubuntu server forever on the Windwow's virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/3kW6AF8.png"80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I went to Network Security Groups for the Ubuntu server on Azure and created a new inbound security rule, denying any ICMP traffic. Meaning when I go back to my Window's powershell the request should time out and Wireshark should not be tracking any ICMP traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/G4HeXfF.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
As you can see the request timed out on the window's powershell.
</p>
<br />

<p>
<img src="https://i.imgur.com/aZR4JLW.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I am going back to the inbound rules of the Ubuntu server in Azure and allow ICMP traffic again. This should allow Wireshark to track the ICMP traffic again and allow Powershell to receive a response from this IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/9X3Vy9P.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Wireshark can track ICMP traffic and Powershell can now receive response from this IP address again.
</p>
<br />

<p>
<img src="https://i.imgur.com/cgwWNB4.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I am now typing in the code "ssh" username, VM2's private ip address and typed in my password in powershell to access VM2.Now you can see that I have access to VM2 through powershell.
</p>
<br />

<p>
<img src="https://i.imgur.com/3FifhpA.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I exited out of VM2 by typing in the exit command in powershell and now I am back on VM 1.
</p>
<br />

<p>
<img src="https://i.imgur.com/c579Brs.png"80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next network protocol, I am going to track is the dhcp protocol, which basically assigns your computer a new IP address. So I typed in the powershell command ipconfig /renew for a new ip address. And now you can see that it gave me a new IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/6DxEatc.png" alt="Disk Sanitization Steps"/>
</p>
<p>
The DNS network protocol gives you the IP address of a domain name like for example say www.google.com. So what I am going to do is type in nslookup www.google.com in powershell command to find out what the IP address is for this domain name and also see how Wireshark tracks this.
</p>
<br />

<p>
<img src="https://i.imgur.com/matK5pS.png" alt="Disk Sanitization Steps"/>
</p>
<p>
The last network protocol is RDP and this protocol essentially tracks every live action you are doing on your computer so let's say I am on youtube it tracks that if my files are open it tracks that also. So this is it for Tracking certain network protocols on Wireshark, and configuring Azure firewall rules on a virtual machine and learning some new commands as well. I hope this was clear and easy to understand. Good bye!
</p>
<br />








