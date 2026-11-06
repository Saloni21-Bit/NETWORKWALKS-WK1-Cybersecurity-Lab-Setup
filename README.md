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

<img width="1240" height="277" alt="image" src="https://github.com/user-attachments/assets/e73791bd-d7ad-480b-b7e0-c708b08c14a2" />


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

## ⚙️ Virtual Machine Configuration

The Kali Linux virtual machine was configured with:

- **RAM:** 2048 MB
- **Processors:** 2
- **Virtual disk:** 80.09 GB
- **Video memory:** 128 MB
- **Network adapter:** NAT Network
- **Network name:** NatNetwork


### VirtualBox Network Adapter

The virtual machine's Adapter 1 is attached to the `NatNetwork` NAT Network. The virtual cable is connected.

<img width="1912" height="1157" alt="VirtualBox Setting" src="https://github.com/user-attachments/assets/10ac120a-5cfd-4611-bb5d-e722ac966334" />


### NAT Network Details

The VirtualBox NAT Network is configured with the IPv4 prefix `10.0.0.0/24`. Its DHCP server is enabled. In this lab, the Kali guest's IPv4 address was configured manually.

---

## 🪜 Lab Setup and Configuration

### Step 1: Start Kali Linux

I started the Kali Linux virtual machine from Oracle VirtualBox and opened the Kali desktop.
<img width="1897" height="1141" alt="Kali Linux Desktop" src="https://github.com/user-attachments/assets/98aa1768-2e24-4992-b1b9-5f935dc1fa65" />


### Step 2: Configure IPv4 Settings

I configured the wired connection with the following manual IPv4 settings:

| Setting | Value |
|---|---|
| Method | Manual |
| IPv4 address | `10.0.0.2` |
| Prefix length | `24` |
| Default gateway | `10.0.0.1` |
| DNS server | `10.0.0.1` |

<img width="1917" height="1145" alt="Kali Network Settings" src="https://github.com/user-attachments/assets/52add116-eb5b-4edc-9aa1-e5b3b5972574" />


### Step 3: Verify the IP Address

I used the `ip addr` command to inspect network interfaces and confirm the address assigned to `eth0`.

```bash
ip addr
```
The output shows:

- Interface: `eth0`
- IPv4 address: `10.0.0.2/24`

<img width="1917" height="1140" alt="Ip configuration" src="https://github.com/user-attachments/assets/b31fa6fb-6b75-4b91-abea-9b0e8818aab2" />



### Step 4: Check the Routing Table

I used the following command to view the routing table:

```bash
ip route
```
The output shows the default route through `10.0.0.1` using interface `eth0`.

<img width="1917" height="747" alt="Routing table" src="https://github.com/user-attachments/assets/0a567848-f84d-4ba1-9caa-75c1b649af65" />


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

<img width="1917" height="1141" alt="DNS configuration" src="https://github.com/user-attachments/assets/b2f0ac56-d192-4314-8c73-513c26a56aa6" />

### Step 6: Test Gateway Connectivity

I sent four ICMP echo requests to the configured gateway:

```bash
ping -c 4 10.0.0.1
```

The screenshot shows **4 packets transmitted, 4 received, and 0% packet loss**, confirming that the gateway responded to the test.

<img width="1916" height="1142" alt="Gateway test ping" src="https://github.com/user-attachments/assets/7a97afed-dfa4-41ef-b847-314bab8b5c2e" />


### Step 7: Test External IP Connectivity

I tested connectivity to the public IP address `8.8.8.8`:

```bash
ping -c 4 8.8.8.8
```

The screenshot shows **4 packets transmitted, 4 received, and 0% packet loss**.

<img width="1917" height="1145" alt="Internet Connectivity" src="https://github.com/user-attachments/assets/f4eff7e8-1b4a-4ede-8506-88b484a575d6" />


### Step 8: Verify DNS Resolution

I used `nslookup` to check whether the DNS server could resolve `google.com`:

```bash
nslookup google.com
```

The output identifies the DNS server as `10.0.0.1` and returns IP addresses for `google.com`.

<img width="1917" height="1140" alt="DNS resolution" src="https://github.com/user-attachments/assets/ee2934e0-e70c-4136-96aa-2e65ec3c9b1e" />

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

<img width="1917" height="1142" alt="Snapshots" src="https://github.com/user-attachments/assets/f41543da-4005-4656-b8bb-0de09bf43021" />


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
