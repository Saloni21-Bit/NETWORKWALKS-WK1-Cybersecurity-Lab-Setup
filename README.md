# NETWORKWALKS-WK1-Cybersecurity-Lab-Setup
# 🖥️ Cybersecurity & Pentesting Lab Setup

**NetworkWalks | Week 1 | Tools: VirtualBox + Kali Linux**

---

📌 About This Project

In this project I built a safe virtual hacking lab on my own laptop using
VirtualBox and Kali Linux. Everything runs inside a virtual machine, so I can
practise security tools without putting my real computer or my home network
at risk.

The lab runs on a private virtual network (a VirtualBox NAT Network), so I can
add more machines later and use them as practice targets.

---

 🎯 What I Wanted to Achieve

- Install VirtualBox on my laptop
- Create a private NAT Network for the lab
- Set up Kali Linux as a virtual machine
- Give the Kali VM a fixed (static) IP address
- Check that the network, internet and DNS all work
- Save a snapshot so I can go back to a clean setup
- Document every step with my own screenshots

---

## 🛡️ Why Build a Lab?

A lab gives me a safe place to practise things like:

- Network scanning and port scanning
- Vulnerability checking
- Packet analysis
- Web security testing
- Trying out security tools

⚠️ **Note:** I only use this lab on systems I own or have permission to test.
Testing other people's systems without permission is illegal.

---

## 🏗️ Lab Layout

```
 My Laptop (Windows 11 + VirtualBox)
        │
        └── NatNetwork  (10.0.0.0/24)
               │
               ├── Gateway / DNS ......... 10.0.0.1
               ├── Kali Linux VM ......... 10.0.0.2
               └── Future target VMs ..... (to be added)
```

---

## ⚙️ My Lab Configuration

| Component | Details |
|---|---|
| Laptop | ASUS TUF Gaming F16 (FX607VBR) |
| Host OS | Windows 11 Home, version 25H2 |
| Processor | Intel Core 5 210H, 2.20 GHz |
| RAM | 16 GB |
| Graphics | NVIDIA GeForce RTX 3050 A (4 GB) |
| Storage | 954 GB |
| Security OS | Kali Linux 2026.3 (Rolling, x64) |
| Kali VM RAM | 2048 MB |
| Kali VM CPUs | 2 |
| Kali VM disk | 80 GB (VDI) |
| Network type | NAT Network (`NatNetwork`) |
| Network range | 10.0.0.0/24 |
| Kali IP address | 10.0.0.2/24 |
| Gateway | 10.0.0.1 |
| DNS server | 10.0.0.1 |

![Laptop specs](screenshots/01-laptop-specs.png)

---

## 🪜 Setup Steps

### Step 1: Create the NAT Network
In VirtualBox I opened the Network manager and created a NAT Network.

```
Name:        NatNetwork
IPv4 Prefix: 10.0.0.0/24
DHCP:        Enabled
IPv6:        Disabled
```

I chose a NAT Network because VMs on the same NAT Network can talk to each
other and can still reach the internet. This lets me add more machines to
the lab later.

![NAT Network](screenshots/02-virtualbox-nat-network.png)

### Step 2: Set up the Kali Linux VM
I used the pre-built Kali Linux VirtualBox image from the official Kali website
and gave the VM these resources:

```
RAM:        2048 MB
Processors: 2
Video:      VMSVGA, 128 MB
Disk:       80 GB
```

![Kali VM details](screenshots/03-kali-vm-details.png)

### Step 3: Connect Kali to the NAT Network
In the VM settings, under Network, Adapter 1:

```
Attached to:  NAT Network
Name:         NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
```

![Kali network adapter](screenshots/04-kali-vm-network-adapter.png)

### Step 4: Start Kali Linux
Kali booted to its desktop without problems.

![Kali desktop](screenshots/05-kali-desktop.png)

### Step 5: Set a static IP address
I opened the network connection editor ("Wired connection 1") and set the
IPv4 method to Manual:

```
Address: 10.0.0.2
Netmask: 24
Gateway: 10.0.0.1
DNS:     10.0.0.1
```

A fixed IP makes the lab easier to document and to reuse in future exercises.

![Static IP settings](screenshots/06-static-ip-settings.png)

### Step 6: Take a snapshot
I took a VirtualBox snapshot named **Network Walks** so I can restore the
VM if I break something later.

![Snapshot](screenshots/13-snapshot.png)

---

## 🔎 Testing the Lab

| Test | Command | Result |
|---|---|---|
| Check my IP | `ip addr` | `eth0` has 10.0.0.2/24 |
| Check routes | `ip route` | Default route via 10.0.0.1 on eth0 |
| Ping the gateway | `ping -c 4 10.0.0.1` | 4 sent, 4 received, 0% loss |
| Ping the internet | `ping -c 4 8.8.8.8` | 4 sent, 4 received, 0% loss |
| Check DNS config | `cat /etc/resolv.conf` and `nmcli device show` | Nameserver and DNS are 10.0.0.1 |
| Test DNS lookup | `nslookup google.com` | google.com resolved to IP addresses |

**IP address**
![ip addr](screenshots/07-ip-addr.png)

**Routing table**
![ip route](screenshots/08-ip-route.png)

**Ping to gateway**
![Ping gateway](screenshots/09-ping-gateway.png)

**Ping to internet**
![Ping internet](screenshots/10-ping-internet.png)

**DNS configuration**
![DNS config](screenshots/12-dns-config.png)

**DNS lookup**
![DNS lookup](screenshots/11-dns-lookup.png)

---

## 🐞 Problems I Faced and How I Fixed Them

### Problem 1: (write your real problem here)
**What happened:** (your own words)
**How I fixed it:** (your own words)

---

## 💡 What I Learned

1. **NAT vs NAT Network:** a NAT Network lets several VMs share one private
   network and still reach the internet, which is what a multi-machine lab needs.
2. **Static IPs:** I learned to set an IP address, netmask, gateway and DNS
   by hand in Kali and to check them with `ip addr` and `ip route`.
3. **Testing in layers:** I tested my gateway first, then the internet, then
   DNS, so I know exactly which part works.
4. **Snapshots:** taking a snapshot early gives me a safe point to return to.
5. **Documentation:** writing down commands, results and screenshots is part of
   doing a project properly.

---

## 🔐 Ethical Use

This lab is for learning only. I only test systems that I own or have
permission to test.

---

## 🔗 Tools and Downloads

- VirtualBox: https://virtualbox.org/wiki/Downloads
- Kali Linux: https://kali.org/get-kali

---

## 👤 Author

**Saloni Kakkar**
B.Tech CSE student, Lovely Professional University
GitHub: https://github.com/Saloni21-Bit
LinkedIn: (add your link)

**Program:** NetworkWalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup
