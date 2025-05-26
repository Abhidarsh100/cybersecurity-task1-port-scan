#  Cybersecurity Internship - Task 1: Scanning Local Network for Open Ports

##  Objective:
Scan the local network to discover open ports and understand network exposure using Nmap and optional analysis with Wireshark.

---

##  Tools Used:
- Kali Linux (OS)
- Nmap (Port Scanner)
- Wireshark (Optional - Packet Analysis)

---

##  Tool Installation:
Nmap and wireshark are pre-installed on Kali Linux. 

## Find Local IP Range

```  
ip a
```
 
Look for your local IP and subnet, e.g., 192.168.29.0/24

## Run TCP SYN Scan  
```
sudo nmap -sS 192.168.29.0/24
```

### Explanation:  

**`sudo`:** Required for privileged scans.

**`nmap`:** The scanning tool.

**`-sS`:** TCP SYN (half-open) scan.

**`192.168.29.0/24`:** Scans all IPs from 192.168.29.1 to 192.168.29.254.  
## Save Scan Results
```
sudo nmap -sS 192.168.29.0/24 -oN network_scan_results.txt
 ```
`sudo`: Runs the command with superuser (administrator) privileges, which is often required for some types of network scans.  
`nmap`: The Network Mapper tool, used for network discovery and security auditing.  
`-sS`: Performs a "TCP SYN scan" (also known as a stealth scan). This is fast and less likely to be detected by the target system because it doesn’t complete the full TCP handshake.  
`192.168.29.0/24`: The target network range. This specifies all IP addresses from 192.168.29.0 to 192.168.29.255 (a typical local network).  
`-oN network_scan_results.txt`: Outputs the scan results to a file named network_scan_results.txt in a human-readable (normal) format.
#### In summary:
This command runs an nmap stealth scan on all devices in the 192.168.29.0/24 network and saves the results to a file called network_scan_results.txt.

 ## Research: Common Services & Potential Risks  
 
|    **Port**    |    **Service**    |   **Risk**        |                
|--------|---------|--------------|
|21   | FTP	  |Plaintext credentials   |  
|23	|Telnet	|Unencrypted access|
|53	|DNS|	DNS poisoning|
|80	|HTTP	|Unencrypted web traffic|
|443	|HTTPS|	Secure, but version/config may be vulnerable|
|1900	|UPnP|	Vulnerable to external attack|
|5060	|SIP|	VoIP abuse, eavesdropping|
|7070	|RealServer|	Media server exploits|
|7443/8080/8443|	Proxy/Alt HTTPs|	Misconfiguration, unauth access|
|7676|	Messaging	|Middleware vulnerabilities|
