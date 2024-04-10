<h1>Microsoft Azure Network Security Groups (NSGs) and Network Protocol Analysis.</h1>

![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/96f1d514-19b0-4b34-97f1-0627885fb888)

<h2>Project Summary:</h2>
This project highlights the role of NSGs in Microsoft Azure Virtual Machines and how I used a protocol analyzer application (Wireshark), to inspect the flow of network traffic between virtual machines and the internet. 

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
  ![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/32677767-c9d2-48d7-8031-90b9bfb0f017)

- On the Windows 10 VM, I downloaded and installed the Wireshark protocol analyser application. This tool helps to visualise the flow of raw traffic between the VMs.
  ![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/d31bb4e5-dd14-4141-910c-ac36a2c2d123)

- I opened the Wireshark tool and filtered Ethernet traffic to display only Internet Control Message Protocol (ICMP) traffic, the network protocol that the 'ping' command uses. The 'ping' command is used to test connectivity between hosts.
- From the Windows 10 VM, I ran Microsoft PowerShell as administrator and proceeded to ping the Linux VM with its private IP address 10.0.0.4. By doing this, I captured the raw data packets being sent from the Windows 10 VM to the Linux VM on Wireshark.
  ![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/8cef79fc-44f3-40c4-a2ce-68fccf6e8b06)
  
- I also pinged 'www.google.com' to display and observe the ICMP data packets transmitted between the Windows VM (10.0.0.4) and Google's IP address (142.250.200.36).
  ![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/a7179c2e-0893-4ccd-bdef-ce075c512003)

- I accessed the Linux VM's NSG on Microsoft Azure and added a new 'inbound security rule' to deny all inbound ICMP traffic. Thus configuring the access control list/firewall. I also set the priority to a lower number (higher priority) ensuring that this rule is followed first.
  ![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/3ceaa35e-664e-4154-8ad9-39d4f299f625)

- Finally, to inspect SSH data packets transmission, I filtered traffic by SSH on Wireshark and typed the command 'ssh Linuxuser@51.143.189.179' on PowerShell, entered the password for the Linux VM and connected to its CLI. Whenever I inputted commands like print working directory 'pwd' and 'exit' on the Linux CLI, I observed SSH packets being transmitted between the Windows 10 and Linux VMs. Data packet transmissions across various ports between endpoints can be analysed simply by filtering with the corresponding port name e.g. RDP or TCP port number e.g. 3389.
  ![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/bba75542-7aa0-4b5a-bdf4-de2e03143650)
  ![image](https://github.com/patrickoigwilo/AzureNSGs-NetworkProtocols/assets/162601853/0b8326d6-d418-4a8b-b814-29f185ab5942)
