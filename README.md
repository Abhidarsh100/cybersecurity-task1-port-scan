
markdown
Copy
Edit
# 🔐 Cybersecurity Internship - Task 1

## 📌 Task Title: Scan Your Local Network for Open Ports

---

## 🎯 Objective

Learn how to discover **open ports** on devices within your **local network** using `nmap`. This task teaches **basic network reconnaissance**, an essential skill in identifying services and potential attack surfaces.

---

## 🛠 Tools Used

| Tool      | Description                                                | Install Command (if not pre-installed)       |
|-----------|------------------------------------------------------------|-----------------------------------------------|
| Nmap      | A powerful network scanner for host discovery and port scanning | `sudo apt update && sudo apt install nmap -y` |
| Wireshark | (Optional) GUI-based packet analyzer to monitor traffic   | `sudo apt install wireshark -y`               |

> ⚠️ Both tools are pre-installed in **Kali Linux**.

---

## 🧭 Step-by-Step Guide

### 📍 Step 1: Identify Your IP and Network Range

Run:
```bash
ip a
Look for the IP assigned to your active interface (usually wlan0 or eth0). Example:

nginx
Copy
Edit
inet 192.168.29.45/24
👉 Your subnet is /24, so your IP range is: 192.168.29.0/24

🚀 Step 2: Perform TCP SYN Scan with Nmap
Run:

bash
Copy
Edit
nmap -sS 192.168.29.0/24
Option	Description
-sS	TCP SYN scan (stealthy and fast)

This scan will list all live hosts and their open TCP ports.

💾 Step 3: Save the Output
🔹 Save to Text File
bash
Copy
Edit
nmap -sS 192.168.29.0/24 -oN scan_results.txt
🔹 Save to HTML Format (requires xsltproc)
bash
Copy
Edit
nmap -sS 192.168.29.0/24 -oX scan_results.xml
xsltproc scan_results.xml -o scan_results.html
🔍 (Optional) Step 4: Packet Analysis with Wireshark
Launch Wireshark with root privileges:

bash
Copy
Edit
sudo wireshark
Start capturing on your network interface.

Run the nmap scan.

Filter for SYN packets:

wireshark
Copy
Edit
tcp.flags.syn == 1 && tcp.flags.ack == 0
This shows SYN packets sent to discover open ports.

🧠 Key Concepts
Port Scanning: Probing ports to identify running services.

TCP SYN Scan: Sends SYN to initiate a connection but doesn’t complete handshake.

IP Range /24: Covers 256 IPs from .0 to .255.

Open Port: Indicates a service is actively listening.

Wireshark: Helps validate scanning behavior and traffic patterns.

🧾 Sample Nmap Output Summary
IP Address	Open Ports	Hostname	MAC Address
192.168.29.1	80, 443, 1900	Arcadyan Router	84:90:0A:DC:86:5C
192.168.29.2	21, 23, 53	Syrotech ONU	38:94:E0:CF:D4:F2
192.168.29.47	7070	Intel Device	30:05:05:D8:DB:FA
192.168.29.155	7676	Samsung Device	FC:8F:90:15:DB:59

⚠️ Risks of Common Open Ports
Port	Service	Risk
21	FTP	Transmits credentials in plaintext
23	Telnet	Unencrypted remote access; susceptible to sniffing
80	HTTP	Can expose web apps to attacks (XSS, SQLi, etc.)
1900	SSDP	Used in DDoS reflection attacks
7070	RealServer	Unknown media service, might allow remote control/backdoor access
