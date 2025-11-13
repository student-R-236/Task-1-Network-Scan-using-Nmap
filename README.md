# Task-1-Network-Scan-using-Nmap
Nmap TCP SYN scan on local network with analysis.  
This project involves performing a TCP SYN scan on a local network to identify connected devices, open ports, 
and potential security risks.  
All IP addresses, MAC addresses, and device identifiers have been masked for privacy.  

# Tools Used
-> Nmap 7.98  
-> Windows Command Prompt  
-> Local Wi-Fi Network  

# Command Executed
nmap -sS 192.168.x.x/24 -oN scan.txt  
-sS - TCP SYN scan  
-oN scan.txt - saves the output in a text file  

# Scan Results
# NMAP SCAN REPORT (Hidden IP and MAC addresses for privacy)
Scan Type: TCP SYN Scan (-sS)  
Network Range: 192.168.x.x/24  
Devices Detected: 8 hosts online.  

# 1.Device A (Router) - 192.168.x.x
Open Ports:  
->21/tcp-FTP  
->80/tcp-HTTP(Web Interface)  
->443/tcp-HTTPS(Secure Web Interface)  
This is likely the Wi-Fi router. Open HTTP/HTTPS ports are normal for router admin pages. FTP being open   can be a security risk if enabled unnecessarily.

# 2.Device B - 192.168.x.x
All ports closed. No responsive services detected.  
MAC Address: Hidden  

# 3.Device C - 192.168.x.x  
Open Ports:  
->22/tcp-SSH  
->80/tcp-HTTP  
->443/tcp-HTTPS   
This devices is probably a smart device, a local server or an IoT device.  

# 4-7. Devices D,E,F,G - 192.168.x.x  
All ports closed. No active services detected.  
These are likely phones, TVs, IoT devices or devices connected but idle.  

# 8. Device H (My Laptop) - 192.168.x.x  
Open Ports:  
->135/tcp-MSRPC  
->139/tcp-NetBIOS  
->445/tcp-SMB  
->2869/tcp-UPnP/DLNA  
These are default Windows services and file-sharing ports. They can be considered medium-risk if exposed   publicly, but safe inside a home LAN.  

# SUMMARY  

->The network contains 8 active hosts.  
->The router exposes typical web and FTP services.  
->One device uses SSH + HTTP + HTTPS (likely a smart device).  
->Four devices are idle with no open ports.  
->The Windows laptop exposes standard SMB, RPC, and UPnP services.  

# SECURITY RECOMMENDATIONS

->Disable FTP on the router if not needed.  
->Restrict SMB(445) sharing on Windows.  
->Ensure router admin panel uses strong password & HTTPS.  
->Keep all IoT device interfaces password protected.


# Task 1: Wireshark Packet Capture (Optional)

This task demonstrates basic packet capture and network analysis using Wireshark.  

# Tools Used

-> Wireshark  
-> Npcap (for packet capturing)  

# Steps Performed

->Opened Wireshark  
->Selected the active Wi-Fi interface  
->Started packet capture  
->Generated traffic by visiting a website    
->Stopped the capture  

# Applied filters:

dns (Domain Name System)  
tcp.flags.syn==1 (TCP SYN packets)  
Saved capture as wireshark_capture.pcapng  

# Observations
-> DNS Traffic  
DNS queries and responses were visible.  
Showed domain names the device requested.  
Demonstrates how name resolution works on the network.  

-> TCP Handshakes  
SYN packets identified using filters.  
Shows how initial connections are established.  
Relates to how Nmap performs SYN scanning.  

