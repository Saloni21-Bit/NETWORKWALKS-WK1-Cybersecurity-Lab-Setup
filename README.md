# NETWORKWALKS-WK1-Cybersecurity-Lab-Setup
My home cybersecurity lab with VirtualBox, Kali Linux and a vulnerable VM.
# 🔐 Cybersecurity & Penetration Testing Lab Setup

*Building a virtual lab, understanding networks, and exploring cybersecurity through hands-on practice.*

## 📌 1. Project Overview

As part of my Week 1 Cybersecurity Internship at **NETWORKWALKS**, I worked on setting up a virtual cybersecurity and penetration testing lab using **Oracle VirtualBox**.

The main idea behind this project was to create a controlled virtual environment where multiple operating systems could run together and communicate over a virtual network.

For this setup, I worked with **Kali Linux, Windows 10, and Android virtual machines**. I configured the virtual network, checked IP addressing, verified DNS resolution, tested network connectivity, and explored snapshot management.

This practical exercise helped me understand how virtual machines communicate with each other and how networking concepts are applied in a cybersecurity environment.

## 🎯 2. Objectives of the Project

The major objectives of this project were:

- 🐉 To configure Kali Linux in Oracle VirtualBox.
- 🌐 To understand different virtual networking modes available in VirtualBox.
- ⚙️ To create and configure a NAT Network.
- 💻 To connect multiple virtual machines to the same network.
- 📡 To understand IP addressing, subnetting, and default gateways.
- 🔎 To verify routing information and DNS resolution.
- 🧪 To test network connectivity using basic networking commands.
- 📸 To create a virtual machine snapshot for recovery purposes.

## 🌐 3. Network Configuration

An important part of this project was configuring the virtual network so that different virtual machines could communicate with each other.

### 🔄 3.1 Understanding NAT and NAT Network

While working with Oracle VirtualBox, I explored the difference between NAT and NAT Network.

**🔹 NAT (Network Address Translation)**

NAT allows a virtual machine to access external networks through the host machine. However, virtual machines using separate individual NAT connections are not automatically placed on the same private network for direct communication.

**🔹 NAT Network**

NAT Network allows multiple virtual machines connected to the same NAT Network to communicate with each other while also providing external network access.

For this project, I selected **NAT Network** because the objective was to connect Kali Linux, Windows 10, and Android virtual machines within a common virtual network.

### ⚙️ 3.2 Creating a NAT Network

The following configuration process was performed:

1. Opened Oracle VirtualBox.
2. Navigated to the Network Manager section.
3. Created a new NAT Network.
4. Configured the network settings.
5. Enabled DHCP where applicable.
6. Connected the required virtual machines to the same NAT Network.

**📋 Network Configuration Details**

| Parameter        | Configuration |
| Network Mode     | NAT Network |
| Network Name     | As configured in VirtualBox |
| DHCP             | Enabled where configured |
| Virtual Machines | Kali Linux, Windows 10, Android |

### 💻 3.3 Connecting Virtual Machines

After creating the NAT Network, I configured the network adapter settings of the virtual machines.

The same NAT Network was selected for the required virtual machines to allow communication between them.

The connected systems included:

- 🐉 **Kali Linux:** Used as the primary cybersecurity testing environment.
- 🪟 **Windows 10:** Used as a secondary operating system for connectivity testing.
- 📱 **Android:** Included to understand connectivity between different operating system environments.

## 🛠️ 4. Implementation Procedure

This section explains the practical steps I followed while setting up the virtual cybersecurity lab.

### 🐉 Step 1: Setting Up Kali Linux

I started by configuring Kali Linux in Oracle VirtualBox.

After launching the virtual machine, I checked whether the operating system was working properly and verified its network connectivity.

Kali Linux was selected as the primary environment for performing networking-related tasks and exploring cybersecurity tools.

### 🔧 Step 2: Configuring Network Settings

Next, I configured the network adapter of Kali Linux and connected it to the previously created NAT Network.

After applying the configuration, I checked the network interface to verify whether the virtual machine had received the required network settings.

**Command Used:**

```bash
ip addr
```

This command displays the available network interfaces along with their assigned IP addresses.

### 🌍 Step 3: Checking IP Configuration

To understand the network configuration, I checked the assigned IP address and network interface details.

**Command Used:**

```bash
ip a
```

This helped me identify the active network interface and verify its IP configuration.

Understanding IP addressing is important because it helps determine how devices identify and communicate with each other over a network.

### 🛣️ Step 4: Verifying the Routing Table

I checked the routing table to understand how network traffic was being directed.

**Command Used:**

```bash
ip route
```

The routing table helped me identify the default gateway and understand how the virtual machine could communicate with other networks.

It also helped me understand the role of routing in sending data to the correct destination.

### 📡 Step 5: Testing Gateway Connectivity

After checking the IP configuration and routing table, I tested connectivity to the default gateway.

**Command Used:**

```bash
ping <gateway-ip>
```

This test helped verify whether Kali Linux could communicate with the virtual network gateway.

Successful responses indicate that the gateway is reachable from the virtual machine.

### 🌐 Step 6: Testing External Network Connectivity

I then checked whether the virtual machine could reach an external IP address.

**Command Used:**

```bash
ping 8.8.8.8
```

This helped verify external network connectivity without depending on DNS resolution.

It was useful for understanding the difference  between IP connectivity and domain name resolution.

🔎 Step 7: Verifying DNS Resolution

To check whether domain names were resolving correctly, I used:

Command Used:

ping google.com

This helped me understand how DNS translates human-readable domain names into IP addresses.

It also provided a basic way to check whether DNS resolution was functioning properly.

🪟 Step 8: Connecting Windows 10 and Android

After configuring Kali Linux, I connected the Windows 10 and Android virtual machines to the same NAT Network.

I checked their network configurations and performed connectivity tests where supported.

This helped me understand how different virtual machines can operate within a shared virtual network.

📶 Step 9: Testing Network Connectivity Using Ping

The ping command was used to test communication between systems.

Command Used:

ping <target-ip>

It sends ICMP echo requests to the target and checks whether responses are received.

This is one of the basic methods used in networking to identify connectivity issues and verify communication between devices.

📸 Step 10: Creating a Kali Linux Snapshot

Finally, I created a snapshot of the Kali Linux virtual machine.

A snapshot saves the current state of a virtual machine and provides a recovery point.

This is particularly useful in cybersecurity labs because experiments and configuration changes can sometimes affect the working environment.

Having a snapshot makes it easier to return to a previously saved state when needed.

🧪 5. Testing and Verification

After completing the configuration, I performed several checks to verify the virtual lab setup.

The following commands were used during the testing process:

Command              | Purpose
ip addr              | Check assigned IP addresses
ip a                 | Display network interfaces
ip route             | Verify routing information
ping <gateway-ip>    | Test gateway connectivity
ping 8.8.8.8         | Test external IP connectivity
ping google.com      | Check DNS resolution
ping <target-ip>     | Test communication with another system

These tests helped me understand whether the network configuration was working as expected.

⚠️ 6. Challenges Faced

During the setup, I explored some common networking and virtual machine configuration issues.

Some of the areas that required attention included:

🔹 Understanding the difference between NAT and NAT Network.

🔹 Ensuring all required virtual machines were connected to the correct network.

🔹 Verifying IP address allocation.

🔹 Understanding the default gateway and routing information.

🔹 Checking DNS resolution separately from basic IP connectivity.

🔹 Managing virtual machine states and snapshots.

Working through these checks improved my understanding of network troubleshooting and virtual lab management.

💡 7. Key Learnings

This project provided practical exposure to several important networking concepts.

Through this activity, I learned:

🌐 How virtual machines work inside Oracle VirtualBox.

🔄 How NAT and NAT Network differ.

📡 How IP addresses are assigned to virtual machines.

🛣️ How routing tables help direct network traffic.

🔑 Why default gateways are important.

🔎 How DNS resolution works.

🧪 How to test network connectivity using the ping command.

📸 How snapshots help maintain a safe virtual lab environment.

Most importantly, I got the opportunity to apply networking concepts practically instead of only studying them theoretically.

🧰 8. Tools and Technologies Used

The following tools and technologies were used during this project:

Tool / Technology             | Purpose
Oracle VirtualBox             | Creating and managing virtual machines
Kali Linux                    | Cybersecurity and networking practice
Windows 10                    | Secondary operating system for connectivity testing
Android VM                    | Exploring connectivity across operating systems
Linux Terminal                | Executing networking commands
Ping                          | Testing network connectivity

# Author
Name: Gurleen Kaur
Field: Cybersecurity
Project: Virtual Cybersecurity Lab Setup
Platform: GitHub

⭐ Learning by doing, growing with every challenge, and building a stronger foundation in cybersecurity.

#Cybersecurity #NetworkWalks #KaliLinux #VirtualBox #Networking #EthicalHacking #LearningByDoing
