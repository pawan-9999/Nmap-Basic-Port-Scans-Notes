# Nmap-Basic-Port-Scans-Notes
Port scanning is a fundamental phase in reconnaissance and enumeration. It helps identify:  Open ports Running services Potential attack surfaces  Nmap (Network Mapper) is one of the most powerful tools used by penetration testers and security professionals for this purpose.
⚡ 1. TCP Connect Scan (-sT)
🔹 Concept:
Uses full 3-way handshake (SYN → SYN-ACK → ACK)
Establishes a complete connection with the target
🔹 Working:
Attacker sends SYN
Target responds with SYN-ACK
Attacker sends ACK → connection established
🔹 Use Case:
When no raw packet privileges (non-root user)
🔹 Pros:

✔ Reliable results
✔ Works on all systems

🔹 Cons:

❌ Easily detectable (fully logged)
❌ Slower than SYN scan

⚡ 2. TCP SYN Scan (-sS) — Stealth Scan
🔹 Concept:
Also known as Half-Open Scan
Does NOT complete full handshake
🔹 Working:
SYN sent
SYN-ACK received (port open)
RST sent instead of ACK → connection not completed
🔹 Use Case:
Preferred in real-world pentesting
🔹 Pros:

✔ Faster than TCP Connect
✔ Less likely to be logged (stealthier)

🔹 Cons:

❌ Requires root/admin privileges
❌ Can still be detected by advanced IDS/IPS

⚡ 3. UDP Scan (-sU)
🔹 Concept:
Scans UDP ports (connectionless protocol)
🔹 Working:
Sends UDP packet
If no response → may be open
If ICMP “Port Unreachable” → closed
🔹 Common UDP Services:
DNS (53)
SNMP (161)
DHCP (67/68)
🔹 Pros:

✔ Identifies critical UDP services

🔹 Cons:

❌ Slow and unreliable
❌ Difficult to interpret results

📊 Port States in Nmap

Nmap classifies ports into different states:

Open → Service is running
Closed → No service, but reachable
Filtered → Blocked by firewall
Unfiltered → Accessible but unclear state
Open|Filtered → Cannot determine
Closed|Filtered → Cannot determine
🧠 Key Learning Takeaways
Different scan types serve different purposes (speed vs stealth vs reliability)
TCP SYN scan is widely used in real-world engagements
UDP scanning is important but time-consuming and tricky
Understanding port states is critical for accurate analysis
💻 Basic Commands
# TCP Connect Scan
nmap -sT <target>

# TCP SYN Scan (Stealth)
sudo nmap -sS <target>

# UDP Scan
sudo nmap -sU <target>
🚀 Final Thoughts

Mastering Nmap scanning techniques is a core skill in cybersecurity. These concepts form the foundation for:

Vulnerability assessment
Network reconnaissance
Ethical hacking engagements
