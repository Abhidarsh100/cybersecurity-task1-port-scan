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
**`sudo`**: Runs the command with superuser (administrator) privileges, which is often required for some types of network scans.   

**`nmap`**: The Network Mapper tool, used for network discovery and security auditing.    

**`-sS`**: Performs a "TCP SYN scan" (also known as a stealth scan). This is fast and less likely to be detected by the target system because it doesn’t complete the full TCP handshake.    

**`192.168.29.0/24`**: The target network range. This specifies all IP addresses from 192.168.29.0 to 192.168.29.255 (a typical local network).    

**`-oN network_scan_results.txt`**: Outputs the scan results to a file named network_scan_results.txt in a human-readable (normal) format.  

#### In summary:
This command runs an nmap stealth scan on all devices in the 192.168.29.0/24 network and saves the results to a file called network_scan_results.txt.

 ## Research: Common Services & Potential Risks  
 
| Port   | Service/Protocol                | Common Use                 | Risks if Open                                                                                                 |
|--------|---------------------------------|----------------------------|--------------------------------------------------------------------------------------------------------------|
| 20, 21 | FTP (File Transfer Protocol)    | File transfer              | Plaintext credentials (username/password), vulnerable to sniffing, brute force attacks, anonymous access risks. |
| 22     | SSH (Secure Shell)              | Secure remote login        | Brute force attacks, weak passwords, outdated SSH versions can have vulnerabilities.                         |
| 23     | Telnet                          | Remote login (insecure)    | Sends data in plaintext, vulnerable to sniffing and MITM (man-in-the-middle) attacks.                        |
| 25     | SMTP (Simple Mail Transfer)     | Email sending              | Used for spam, open relays can be abused, exploits via buffer overflows.                                     |
| 53     | DNS (Domain Name System)        | Domain name resolution     | DNS amplification DDoS attacks, cache poisoning, zone transfer leaks.                                        |
| 80     | HTTP                            | Web traffic                | Vulnerable to web app attacks (XSS, SQLi), outdated servers, directory traversal.                            |
| 110    | POP3 (Post Office Protocol 3)   | Email retrieval            | Plaintext credentials, vulnerable to interception.                                                           |
| 143    | IMAP (Internet Message Access)  | Email retrieval            | Plaintext or weak encryption, vulnerable to credential theft.                                                |
| 443    | HTTPS                           | Secure web traffic         | Vulnerabilities in SSL/TLS implementation, outdated ciphers can be exploited.                                |
| 445    | SMB (Server Message Block)      | Windows file sharing       | Remote code execution, ransomware spread (e.g., WannaCry), SMB exploits.                                     |
| 3389   | RDP (Remote Desktop Protocol)   | Remote desktop access      | Brute force attacks, weak passwords, exploits in older versions.                                             |
| 3306   | MySQL                           | Database service           | Weak authentication, SQL injection vectors, data leakage.                                                    |
| 8080   | HTTP alternative/Proxy          | Web servers, proxies       | Same risks as HTTP (port 80), plus misconfigured proxies can expose internal services.                       |
### Key Learnings:  

- Open ports reveal the network services running on devices, such as FTP, HTTP, HTTPS, DNS, Telnet, and others.
- Each service has associated security risks, for example:
  - FTP and Telnet transmit data in plaintext, exposing credentials.
  - DNS can be vulnerable to cache poisoning.
  - UPnP and SIP services have known exploit paths if not properly secured.
- Understanding these risks is essential for network defense and hardening exposed services.
- Performing scans in a controlled environment builds foundational skills in network reconnaissance and penetration testing.
This task provided practical experience with essential cybersecurity tools and concepts, reinforcing the importance of proactive network security assessments.
