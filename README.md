<h1>Microsoft Azure Network Security Groups (NSGs) and Network Protocol Analysis.</h1>

![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/96f1d514-19b0-4b34-97f1-0627885fb888)

<h2>Project Summary:</h2>
This project highlights the role of NSGs in Microsoft Azure Virtual Machines and how I used a protocol analyzer application (Wireshark), to inspect the flow of network traffic between virtual machines/networks. 

<h2>Environments, Applications and Technologies Used:</h2>

- Microsoft Azure cloud environment
- Azure virtual machines (Windows and Linux)
- Remote Desktop Connection application
- Wireshark protocol and traffic analyser
- Microsoft PowerShell

<h2>What are NSGs?</h2>
NSGs or Network Security Groups are essentially firewalls within virtual networks. They are mechanisms for access control within a virtual network and between a virtual network and other external network resources such as the Internet or other virtual networks. They aid granular level segmentation by defining perimeters.

<h2>Walk-through:</h2>

- Using Microsoft Azure, I created two virtual machines - the first running Windows 10 and the second running Linux Ubuntu 20.04.
- I remotely connected to the Windows 10 virtual machine, using the Remote Desktop Connection application.
- On the Windows 10 VM, I downloaded and installed the Wireshark protocol analyser application.
- From the Windows 10 VM, I ran Microsoft PowerShell as administrator and 
