# Python-Intrusion-Detection-System
Similar to a guard dog or a security booth, an **Intrusion Detection System (IDS)** looks for potential signs of intruders. By utilizing **Scapy**, a Python library, one can develop an IDS tool that sniffs live network traffic and flags SYN port scans to help prevent potential SYN flood attacks from occurring. It is crucial to prevent SYN flood attacks because of their ability to prevent new client-server connections, cause server crashes, and slow network functionality.

**Author:** @J-Hwang7 **Date:** July 2026

# How it works
By utilizing **scan_tracker**, the IDS maps each source IP to the port and timestamp at which it recently sent a SYN request. Afterwards, **is_syn_scan_packet** and **detect_port_scan(src_ip, dst_port)** are used to verify if the connection has an **ACK** flag and count the distinct ports that an IP address has SYN requests, within the last few seconds, to determine if a SYN port scan occurs. 

# Python IDS Procedures
**Prerequisite Installation**
- Npcap 1.88 for Windows

**Creating IDS**

1. In an Administrator PowerShell terminal, create a new directory to house this project.

2. Afterwards, run these commands in the directory to install **Scapy** onto your machine.
```
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install scapy
```

3. To code the IDS, run the following command to open the file that the code will be stored in.
 * **See** [sniffer.py](sniffer.py) **for example code**
```
notepad sniffer.py
```

# Testing IDS

1. To run an IDS test, first run the following command to receive the router IP address.
  * The IP address is in the **Wireless LAN adapter Wi-Fi: Default Gateway** section
```
ipconfig
```

2. In another Administrator PowerShell terminal, run the following command to launch the IDS and sniff for packets.
```
python sniffer.py
````

3. Switch to the other PowerShell terminal. To receive a flag in the IDS, **Nmap** will be used to run a port scan of the first 200 ports.
```
 nmap -p 1-200 [IP Address]
```

4. Switch back to the terminal running the IDS and run ***Ctrl+C** to cancel the packet sniffing.
   * Shift through the logs and find the flag. (Should have an alert on it)

 # Licenses
The content of this repository is to be used for educational purposes. Nmap and Scapy have their own licenses (View Respective GitHub repositories).
   
