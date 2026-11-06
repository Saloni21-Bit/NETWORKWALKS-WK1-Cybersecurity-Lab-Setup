# 🔐 Cybersecurity Lab Environment Setup

### Kali Linux Network Configuration and Connectivity Testing using Oracle VirtualBox

**Created by:** Saloni Kakkar  
**Program:** B.Tech – Computer Science and Engineering (Cybersecurity)  
**Institution:** Lovely Professional University

---

## 📌 Project Overview

This project documents the setup of a Kali Linux virtual machine using Oracle VirtualBox and the configuration and verification of its network connection.

The practical work included checking the virtual machine's network adapter, configuring a manual IPv4 address, viewing the routing table, checking DNS settings, and testing connectivity to the virtual gateway and an external IP address.

All screenshots in this repository are from my own lab setup.

## 🎯 Objectives

- Set up and run Kali Linux in Oracle VirtualBox.
- Review virtual machine hardware and network settings.
- Configure a manual IPv4 address.
- Identify the default gateway and DNS server.
- Inspect network interfaces and routing information.
- Test gateway and external network connectivity.
- Verify DNS resolution.
- Save a virtual machine snapshot.

## 🧰 Tools and Environment

| Component | Configuration |
|---|---|
| Host computer | Windows Laptop |
| Processor | Intel Core 5 210H (2.20 GHz) |
| Installed RAM | 16 GB |
| Graphics | NVIDIA GeForce RTX 3050 (4 GB), Intel Graphics |
| Virtualization software | Oracle VirtualBox |
| Guest OS | Kali Linux Rolling 2026.3 (x64) |
| VM allocated memory | 2048 MB (2 GB) |
| VM processors | 2 |
| Virtual disk | 80.09 GB |
| Video memory | 128 MB |
| Network attachment | NAT Network |
| NAT network name | NatNetwork |
| NAT network IPv4 prefix | 10.0.0.0/24 |

### Host Laptop Specifications

The host laptop has an Intel Core 5 210H processor and 16 GB of installed RAM.

![Host Laptop Specifications](screenshots/13-host-laptop-specifications.png)

---

## 🏗️ Lab Architecture

The Kali Linux operating system runs as a guest virtual machine inside Oracle VirtualBox on the Windows host laptop.

Its virtual network adapter is connected to the VirtualBox NAT Network named `NatNetwork`.

```text
Windows Host Laptop
        |
        v
Oracle VirtualBox
        |
        v
Kali Linux Virtual Machine
        |
        v
VirtualBox NAT Network
        |
        v
Gateway / External Network
```

![Oracle VirtualBox Manager](screenshots/01-virtualbox-manager.png)

---

## ⚙️ Virtual Machine Configuration

The Kali Linux virtual machine was configured with:

- **RAM:** 2048 MB
- **Processors:** 2
- **Virtual disk:** 80.09 GB
- **Video memory:** 128 MB
- **Network adapter:** NAT Network
- **Network name:** NatNetwork

![Virtual Machine Overview](screenshots/02-virtual-machine-overview.png)

### VirtualBox Network Adapter

The virtual machine's Adapter 1 is attached to the `NatNetwork` NAT Network. The virtual cable is connected.

![VirtualBox Network Adapter Settings](screenshots/03-virtualbox-network-adapter.png)

### NAT Network Details

The VirtualBox NAT Network is configured with the IPv4 prefix `10.0.0.0/24`. Its DHCP server is enabled. In this lab, the Kali guest's IPv4 address was configured manually.

---

## 🪜 Lab Setup and Configuration

### Step 1: Start Kali Linux

I started the Kali Linux virtual machine from Oracle VirtualBox and opened the Kali desktop.

![Kali Linux Desktop](screenshots/04-kali-linux-desktop.png)

### Step 2: Configure IPv4 Settings

I configured the wired connection with the following manual IPv4 settings:

| Setting | Value |
|---|---|
| Method | Manual |
| IPv4 address | `10.0.0.2` |
| Prefix length | `24` |
| Default gateway | `10.0.0.1` |
| DNS server | `10.0.0.1` |

![Kali Manual IPv4 Settings](screenshots/05-kali-manual-ipv4-settings.png)

### Step 3: Verify the IP Address

I used the `ip addr` command to inspect network interfaces and confirm the address assigned to `eth0`.

```bash
ip addr
```
<img width="1917" height="1140" alt="Ip configuration" src="https://github.com/user-attachments/assets/b31fa6fb-6b75-4b91-abea-9b0e8818aab2" />


The output shows:

- Interface: `eth0`
- IPv4 address: `10.0.0.2/24`

![Kali IP Address Output](screenshots/06-kali-ip-address.png)

### Step 4: Check the Routing Table

I used the following command to view the routing table:

```bash
ip route
```
<img width="1917" height="747" alt="Routing table" src="https://github.com/user-attachments/assets/b22fb282-e90c-452d-bac9-da81daf59a42" />


The output shows the default route through `10.0.0.1` using interface `eth0`.

![Kali Routing Table](screenshots/07-kali-routing-table.png)

### Step 5: Verify DNS Configuration

I checked the resolver configuration:

```bash
cat /etc/resolv.conf
```
<img width="1917" height="1141" alt="DNS configuration" src="https://github.com/user-attachments/assets/b4cf56a1-144d-47d1-a9a9-bd77b4dfdf56" />

I also inspected the active connection's gateway and DNS information:

```bash
nmcli device show | grep -E 'GENERAL.DEVICE|IP4.DNS|IP4.GATEWAY'
```

The captured output shows `10.0.0.1` as the gateway and DNS server.

![DNS and Gateway Configuration](screenshots/08-kali-dns-configuration.png)

### Step 6: Test Gateway Connectivity

I sent four ICMP echo requests to the configured gateway:

```bash
ping -c 4 10.0.0.1
```

The screenshot shows **4 packets transmitted, 4 received, and 0% packet loss**, confirming that the gateway responded to the test.

![Gateway Ping Test](screenshots/09-gateway-ping-test.png)

### Step 7: Test External IP Connectivity

I tested connectivity to the public IP address `8.8.8.8`:

```bash
ping -c 4 8.8.8.8
```

The screenshot shows **4 packets transmitted, 4 received, and 0% packet loss**.

![Internet Connectivity Test](screenshots/10-internet-connectivity-test.png)

### Step 8: Verify DNS Resolution

I used `nslookup` to check whether the DNS server could resolve `google.com`:

```bash
nslookup google.com
```

The output identifies the DNS server as `10.0.0.1` and returns IP addresses for `google.com`.

![DNS Resolution Output](screenshots/11-dns-resolution-test.png)

---

## ✅ Verification Summary

| Verification | Result |
|---|---|
| Kali network interface | `eth0` is up |
| Kali IPv4 address | `10.0.0.2/24` |
| Default gateway | `10.0.0.1` |
| DNS server | `10.0.0.1` |
| Gateway ping | 4 received, 0% packet loss |
| External IP ping | 4 received, 0% packet loss |
| DNS lookup | `google.com` resolved successfully |

These results document successful gateway reachability, external IP connectivity, and DNS resolution at the time the screenshots were captured.

---

## 💾 Virtual Machine Snapshot

I saved a VirtualBox snapshot named **Network Walks** to preserve a point-in-time state of the virtual machine.

![VirtualBox Snapshot](screenshots/12-virtualbox-snapshot.png)

---

## 💡 What I Learned

Through this practical lab, I gained experience with:

1. **Virtualization:** Running Kali Linux as a guest operating system in Oracle VirtualBox.
2. **Virtual Networking:** Understanding how a NAT Network connects a virtual machine to an external network.
3. **IPv4 Configuration:** Setting an IP address, prefix length, gateway, and DNS server manually.
4. **Linux Network Commands:** Using `ip addr`, `ip route`, and `nmcli` to inspect network configuration.
5. **Connectivity Testing:** Using `ping` to test gateway and external IP reachability.
6. **DNS Troubleshooting:** Using `nslookup` and checking `/etc/resolv.conf`.
7. **Snapshots:** Saving a VirtualBox snapshot as a recovery point.

---

## 🔗 Tools and Resources

- [Oracle VirtualBox](https://www.virtualbox.org/)
- [Kali Linux](https://www.kali.org/)
- [Kali Linux Documentation](https://www.kali.org/docs/)
- [Linux IP Command Manual](https://man7.org/linux/man-pages/man8/ip.8.html)

---

## 👤 Author

**Saloni Kakkar**  
B.Tech – Computer Science and Engineering (Cybersecurity)  



---

*Learning networking and cybersecurity through practical, documented lab work.*
