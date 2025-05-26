
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

| Tool      | Description                                                | Install Command (Kali Linux)                  |
|-----------|------------------------------------------------------------|-----------------------------------------------|
| Nmap      | A powerful network scanner for host discovery and port scanning | `sudo apt update && sudo apt install nmap -y` |
| Wireshark | (Optional) GUI-based packet analyzer to monitor traffic   | `sudo apt install wireshark -y`               |

> ⚠️ Both tools are usually pre-installed in **Kali Linux**.

---

## 🧭 Step-by-Step Guide

### 📍 Step 1: Identify Your IP and Network Range

Run:
```bash
ip a
Look for the IP assigned to your active interface (e.g., wlan0 or eth0).
Example:

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

This scan lists all live hosts and their open TCP ports.

💾 Step 3: Save the Output
🔹 Save to Text File
bash
Copy
Edit
nmap -sS 192.168.29.0/24 -oN scan_results.txt
🔹 Save to HTML Format
bash
Copy
Edit
nmap -sS 192.168.29.0/24 -oX scan_results.xml
xsltproc scan_results.xml -o scan_results.html
🔍 (Optional) Step 4: Analyze Packets with Wireshark
Start Wireshark with:

bash
Copy
Edit
sudo wireshark
Select your active network interface.

Begin packet capture and perform the nmap scan.

Use this filter to see SYN packets:

ini
Copy
Edit
tcp.flags.syn == 1 && tcp.flags.ack == 0
🧠 Key Concepts
Port Scanning: Checking which ports are open on a target system.

TCP SYN Scan: Sends SYN packets and identifies if a port is open by response type.

IP Range /24: A block of 256 IPs from .0 to .255.

Open Port: A port that is accepting connections and may be running services.

Wireshark: A tool to inspect raw network traffic for analysis.

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
7070	RealServer	Might allow remote control or media streaming abuse

💬 Interview Questions & Answers
What is an open port?
A network port that is actively listening for incoming connections.

How does Nmap perform a TCP SYN scan?
It sends a SYN packet to a port; if SYN-ACK is returned, the port is open. The connection is never completed (stealthy).

What risks are associated with open ports?
Open ports may expose services vulnerable to attacks, especially if misconfigured or outdated.

Explain the difference between TCP and UDP scanning.
TCP is connection-oriented with SYN/ACK handshakes; UDP is connectionless and relies on timeouts or ICMP responses.

How can open ports be secured?
Disable unused ports, use firewalls, restrict access, and keep software updated.

What is a firewall's role regarding ports?
A firewall controls traffic by allowing or blocking connections to specific ports.

What is a port scan and why do attackers perform it?
It's a method to detect services running on systems. Attackers use it to find vulnerabilities.

How does Wireshark complement port scanning?
It helps visualize traffic patterns and analyze how scans interact with the network.

📁 Repository Contents
bash
Copy
Edit
.
├── scan_results.txt       # Saved Nmap output
├── scan_results.xml       # XML output
├── scan_results.html      # HTML output
├── screenshots/           # Wireshark or terminal screenshots (optional)
├── README.md              # This file
✅ Outcome
Performed a TCP SYN scan using nmap.

Identified open ports and live hosts.

Learned how to analyze scans and understand network exposure.

📤 Submission Guidelines
Create a GitHub repository (e.g., cybersecurity-task-1).

Upload all related files:

README.md

Nmap outputs (.txt, .xml, .html)

Any screenshots

Submit your repo link before 10:00 PM on the task date.

🔒 Ethical Notice
⚠️ Only scan networks you own or have permission to test. Unauthorized scanning is illegal and unethical.

🙌 Happy Learning!
python
Copy
Edit

Let me know if you'd like help generating:
- Sample `scan_results.txt`
- Sample screenshots or dummy data
- GitHub repository structure as a ZIP or template

I'm here to assist you step-by-step.
