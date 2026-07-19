# 🌐 Networking Commands

This section covers essential Linux networking commands used to troubleshoot connectivity, verify DNS resolution, inspect network interfaces, and diagnose network-related issues. These commands are commonly used by DevOps Engineers while managing servers and cloud infrastructure.

---

# ping

**Purpose:** Checks connectivity between your system and another host.

**Syntax**
```bash
ping <hostname/IP>
```

**Example**
```bash
ping google.com
```

**Output**
```text
64 bytes from google.com: icmp_seq=1 ttl=118 time=15.2 ms
```

**DevOps Use Case:** Verify whether a server or service is reachable.

---

# netstat

**Purpose:** Displays network connections, routing tables, and listening ports.

**Syntax**
```bash
netstat -tuln
```

**Example**
```bash
netstat -tuln
```

**Output**
```text
tcp   0   0 0.0.0.0:80   LISTEN
```

**DevOps Use Case:** Check if an application is listening on the expected port.

> 💡 `netstat` is deprecated on many Linux distributions. Use `ss` instead.

---

# ifconfig

**Purpose:** Displays or configures network interfaces.

**Syntax**
```bash
ifconfig
```

**Example**
```bash
ifconfig
```

**Output**
```text
eth0: inet 192.168.1.10
```

**DevOps Use Case:** View the server's IP address and network interface details.

> 💡 Modern Linux systems use the `ip` command instead.

---

# traceroute / tracepath

**Purpose:** Shows the path packets take to reach a destination.

**Syntax**
```bash
traceroute <hostname>
```

**Example**
```bash
traceroute google.com
```

**Output**
```text
1 192.168.1.1
2 10.0.0.1
3 ...
```

**DevOps Use Case:** Troubleshoot network latency or routing issues.

---

# mtr

**Purpose:** Combines `ping` and `traceroute` for real-time network diagnostics.

**Syntax**
```bash
mtr <hostname>
```

**Example**
```bash
mtr google.com
```

**Output**
```text
Displays packet loss and latency for each network hop.
```

**DevOps Use Case:** Identify unstable network connections between servers.

---

# nslookup

**Purpose:** Queries DNS records for a domain.

**Syntax**
```bash
nslookup <domain>
```

**Example**
```bash
nslookup google.com
```

**Output**
```text
Address: 142.250.xxx.xxx
```

**DevOps Use Case:** Verify that a domain resolves to the correct IP address.

---

# telnet

**Purpose:** Tests connectivity to a specific port.

**Syntax**
```bash
telnet <host> <port>
```

**Example**
```bash
telnet google.com 80
```

**Output**
```text
Connected to google.com
```

**DevOps Use Case:** Check whether a service port is accessible.

---

# hostname

**Purpose:** Displays the system hostname.

**Syntax**
```bash
hostname
```

**Example**
```bash
hostname
```

**Output**
```text
web-server-01
```

**DevOps Use Case:** Identify the server while working across multiple environments.

---

# ip

**Purpose:** Displays and manages network interfaces and IP addresses.

**Syntax**
```bash
ip addr
```

**Example**
```bash
ip addr
```

**Output**
```text
inet 192.168.1.10/24
```

**DevOps Use Case:** View IP addresses and troubleshoot network configuration.

---

# iwconfig

**Purpose:** Displays wireless network interface information.

**Syntax**
```bash
iwconfig
```

**Example**
```bash
iwconfig
```

**Output**
```text
wlan0  IEEE 802.11
```

**DevOps Use Case:** Verify Wi-Fi configuration on Linux systems.

---

# ss

**Purpose:** Displays active network connections and listening ports.

**Syntax**
```bash
ss -tuln
```

**Example**
```bash
ss -tuln
```

**Output**
```text
LISTEN 0 128 *:22
```

**DevOps Use Case:** Check whether services like Nginx, Apache, or SSH are listening on the correct ports.

---

# dig

**Purpose:** Retrieves detailed DNS information.

**Syntax**
```bash
dig <domain>
```

**Example**
```bash
dig google.com
```

**Output**
```text
ANSWER SECTION:
google.com. 300 IN A 142.250.xxx.xxx
```

**DevOps Use Case:** Troubleshoot DNS issues in cloud environments.

---

# whois

**Purpose:** Displays domain registration information.

**Syntax**
```bash
whois <domain>
```

**Example**
```bash
whois google.com
```

**Output**
```text
Registrar: MarkMonitor Inc.
```

**DevOps Use Case:** Check domain ownership and registration details.

---

# arp

**Purpose:** Displays the ARP (Address Resolution Protocol) table.

**Syntax**
```bash
arp -a
```

**Example**
```bash
arp -a
```

**Output**
```text
192.168.1.1 at aa:bb:cc:dd:ee:ff
```

**DevOps Use Case:** Verify communication between devices on the local network.

---

# ifplugstatus

**Purpose:** Checks whether a network cable is connected.

**Syntax**
```bash
ifplugstatus
```

**Example**
```bash
ifplugstatus eth0
```

**Output**
```text
eth0: link beat detected
```

**DevOps Use Case:** Verify physical network connectivity.

---

# curl

**Purpose:** Sends HTTP requests and retrieves responses.

**Syntax**
```bash
curl <URL>
```

**Example**
```bash
curl https://example.com
```

**Output**
```text
<html>...</html>
```

**DevOps Use Case:** Test APIs, health endpoints, and web applications.

---

# wget

**Purpose:** Downloads files from the internet.

**Syntax**
```bash
wget <URL>
```

**Example**
```bash
wget https://example.com/app.zip
```

**Output**
```text
Saving to: app.zip
```

**DevOps Use Case:** Download application packages, scripts, or installation files.

---

# iptables

**Purpose:** Configures Linux firewall rules.

**Syntax**
```bash
iptables -L
```

**Example**
```bash
sudo iptables -L
```

**Output**
```text
Chain INPUT (policy ACCEPT)
```

**DevOps Use Case:** Check firewall rules while troubleshooting blocked connections.

---

# watch

**Purpose:** Repeatedly runs a command at regular intervals.

**Syntax**
```bash
watch <command>
```

**Example**
```bash
watch df -h
```

**Output**
```text
Updates disk usage every 2 seconds.
```

**DevOps Use Case:** Monitor changing system metrics during deployments.

---

# nmap

**Purpose:** Scans hosts for open ports and services.

**Syntax**
```bash
nmap <host>
```

**Example**
```bash
nmap 192.168.1.10
```

**Output**
```text
22/tcp open ssh
80/tcp open http
```

**DevOps Use Case:** Verify which ports are open on a server.

---

# route

**Purpose:** Displays the system's routing table.

**Syntax**
```bash
route -n
```

**Example**
```bash
route -n
```

**Output**
```text
Destination  Gateway  Genmask
```

**DevOps Use Case:** Troubleshoot routing issues between networks.

---

## 🎯 Quick Revision Tips

- **ping** → Check connectivity.
- **ss -tuln** → View listening ports (**Most Used**).
- **ip addr** → View IP addresses (**Most Used**).
- **curl** → Test APIs and websites (**Most Used**).
- **wget** → Download files.
- **dig / nslookup** → DNS lookup.
- **nmap** → Scan open ports.
- **traceroute** → Trace network path.
- **iptables** → View firewall rules.
- **watch** → Continuously monitor a command.

---

## 💡 Common DevOps Workflow

```bash
ping google.com
ip addr
ss -tuln
curl http://localhost:8080/health
dig example.com
```

This workflow helps verify network connectivity, server IP, listening ports, application health, and DNS resolution.

---

> 💡 **Interview Tip:** The networking commands you'll use most often in DevOps are **ping**, **ip**, **ss**, **curl**, **dig**, and **nmap**. Mastering these commands will help you troubleshoot the majority of network and application connectivity issues on Linux servers.