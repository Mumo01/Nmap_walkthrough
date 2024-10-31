# LAB 1: Network Scanning and Backdoor Creation

## Objectives

1.1 Basic Scans  
1.2 Nmap Scripting Engine Scripts  
1.3 Zenmap  
1.4 Cheat Sheet  

**Netcat** (essentially opening a “Backdoor” to exfiltrate data from one computer to another and detection using Nmap):  
1.5 Create Netcat listener.  
1.6 Netcat with Nmap  

## Machines Used

- Metasploitable
- Kali Linux Virtual Machine
- Host (Mac)

## Procedure

1. **Ping All VMs**  
   Ensure that the VMs (Kali, Host, Metasploitable) can communicate with each other.
   <img src="https://i.imgur.com/QFvRe4E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   <br>

2. **Scan Metasploitable**  
   Use Kali (Attack Machine) to scan Metasploitable (Target) for open ports.
    <img src="https://i.imgur.com/c3O8THZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   <br>
     ```bash
   nmap -sV --script=vulners <IP>
    ```
     - **nmap**: The command-line tool for network scanning and discovery.
     - **-sV**: Enables version detection, which attempts to determine the versions of services running on open ports, 
     which is crucial for vulnerability assessment.
     - **--script=vulners**: Tells Nmap to use the `vulners` NSE (Nmap Scripting Engine) script. This checks for known 
     vulnerabilities in services and software versions detected on open ports by referencing the Vulners.com vulnerability 
     database.
    - **<IP>**: Replace `<IP>` with the target IP address you want to scan for vulnerabilities. 

   <br><img src="https://i.imgur.com/cDfsssS.png" height="80%" width="80%" alt=""/>
   <br>
    
## Nmap Vulnerability Scanning Procedure

4. **Search for Nmap Vulnerabilities**  
   Look for Nmap scripts on various sites (like Google). You can find scripts that are not included with Nmap by default.
   <img src="" height="80%" width="80%" alt=""/><br>

   - Add the cloned Git repository to the Kali machine and redo the scan using the new script **“vulscan.nse.”**
   - Redo the Nmap scan with the new script. 

5. **Run the “Vulscan.nse” Script**  
   Execute the script in the Kali terminal. All discovered vulnerabilities will be listed by this new script.
     <img src="" height="80%" width="80%" alt=""/><br>

7. **Zenmap**  
   Use Zenmap to visualize the GUI scan results of the Meta IP, which is the vulnerable VM.
     <img src="" height="80%" width="80%" alt=""/><br>

9. **Cheat Sheet**  
   Create a self-made cheat sheet showcasing the most common switches and options used with Nmap for reference.
     <img src="" height="80%" width="80%" alt=""/><br>
       <img src="" height="80%" width="80%" alt=""/><br>
         <img src="" height="80%" width="80%" alt=""/><br>
   
11. **Netcat**  
   In this scenario, the **Meta VM** (presumably located in the US) is the victim machine, while the **Kali** VM (presumably located in Australia) acts as the attacker.

   **Note**: Opening a port (e.g., 80000) is significant because TCP/UDP ports range from 1 to 65535. Using a port outside of this range (like 80000) means it's not an expected port for communication.
     <img src="" height="80%" width="80%" alt=""/><br>
  <img src="" height="80%" width="80%" alt=""/><br>

   This technique creates a backdoor such that the listening port (80000) is not visible in the Nmap scan results. If an Intrusion Detection/Prevention System (IDS/IPS) is in place, it may not detect this port, creating a loophole.

   This technique can be utilized by both "good" and "bad" end users.


 
