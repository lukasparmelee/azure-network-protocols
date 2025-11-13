<p align="center">
  <img src="https://i.imgur.com/zL7zK4Z.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines using Wireshark and experiment with Network Security Groups (NSGs) to understand how traffic filtering impacts communication between systems. <br />

---

<h2>🎥 Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

---

<h2>🧠 Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines / Compute)
- Remote Desktop Protocol (RDP)
- PowerShell & Linux Command-Line Tools
- Wireshark (Protocol Analyzer)
- Network Protocols: ICMP, SSH, DHCP, DNS, RDP

---

<h2>💻 Operating Systems Used</h2>

- Windows 10 (21H2)
- Ubuntu Server 22.04 LTS

---

<h2>⚙️ High-Level Steps</h2>

- Create Resource Group and Virtual Machines in Azure  
- Capture and Analyze Network Traffic with Wireshark  
- Configure Network Security Groups (Firewall)  
- Observe Network Protocols (ICMP, SSH, DHCP, DNS, RDP)  
- Clean Up Azure Resources  

---

<h2>🧩 Actions and Observations</h2>

### **Part 1: Creating Virtual Machines**

<p align="center">
  <img src="./windows-vm.png" height="80%" width="80%" alt="Azure VM Creation"/>
  <img src="./linux-vm.png" height="80%" width="80%" alt="Azure VM Creation"/>
</p>

<p>
In the Azure Portal, a new Resource Group was created along with two Virtual Machines: a Windows 10 VM and an Ubuntu (Linux) VM. Both were placed within the same Virtual Network (VNet) and Subnet to enable internal communication.
</p>

- Resource Group: <code>RG-Network-Activities</code>  
- Network: <code>lab2-vnet</code>  
- Authentication: Username: labuser / Password: Cyberlab123!
- Validation: Both VMs successfully connected within the same private network.  

✅ **Result:** Two connected VMs in one virtual network.

---

### **Part 2: Observing ICMP Traffic**

<p align="center">
  <img src="https://i.imgur.com/hvZL0KP.png" height="80%" width="80%" alt="ICMP Ping Capture"/>
</p>

<p>
Wireshark was installed on the Windows 10 VM to capture ICMP traffic. A ping command was sent to the Ubuntu VM's private IP address, and ICMP Echo Requests and Replies were successfully observed in real-time within Wireshark.
</p>

<p align="center">
  <img src="https://i.imgur.com/rRS7oRt.png" height="80%" width="80%" alt="Network Security Group Rules"/>
</p>

<p>
A continuous ping was initiated from the Windows VM to the Ubuntu VM.  
The inbound ICMP rule was then disabled in the Ubuntu VM’s Network Security Group (NSG).  
Ping requests immediately began timing out, and Wireshark confirmed that no ICMP replies were received.
</p>

