# 🔐 Cybersecurity Internship - Task 1

## 📌 Task Title: Scan Your Local Network for Open Ports

---

## 🎯 Objective

Learn how to discover **open ports** on devices within your **local network** using `nmap`. 
This task teaches **basic network reconnaissance**, an essential skill in identifying services and potential attack surfaces.

---

## 🛠 Tools Used

| Tool      | Description                                                               | Install Command (if not pre-installed)        |
|-----------|---------------------------------------------------------------------------|-----------------------------------------------|
| Nmap      | A powerful network scanner for host discovery and port scanning           | sudo apt update && sudo apt install nmap -y   |
| Wireshark | (Optional) GUI-based packet analyzer to monitor traffic                   | sudo apt install wireshark -y                 |

> ⚠️ Both tools are pre-installed in **Kali Linux**.

---

## 🧭 Step-by-Step Guide

### 📍 Step 1: Identify Your IP and Network Range

command: ip a  
----> gives the ip address with subnet. We can find the ip range from that. 

### Step 2: Perform TCP SYN Scan with Nmap
nmap -sS 192.168.29.0/24
# -sS : TCP SYN scan (stealthy and fast)
This scan will list all live hosts and their open TCP ports.

###  Step 3: Save the Output
         Save to Text File
command :  nmap -sS 192.168.29.0/24 -oN scan_results.txt

        save to xml format 
command :  nmap -sS 192.168.29.0/24 -oX scan_results.xml
