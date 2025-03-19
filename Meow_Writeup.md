#🐱 Meow - Hack The Box Writeup
##Machine Information
- **Platform:** Hack The Box
- **Difficulty Level:** Very Easy
- **Machine IP Address:** `10.129.167.74`
- **Tools Used:** nmap, telnet
- **Key Concepts:** Open ports, weak credentials

1. Scanning
First, we performed an nmap scan to identify open ports and running services:
nmap -sC -sV -Pn -T4 10.129.167.74
The scan results showed a single open port:
PORT   STATE SERVICE VERSION
23/tcp open  telnet  Linux telnetd

2. Exploitation
Since Telnet was open, we attempted to connect to the machine:
telnet 10.129.167.74
When prompted for a username, we entered root, and surprisingly, no password was required to gain access.

3. Capturing the Flag
After gaining shell access, we checked the home directory:
ls -la
A file named flag.txt was found. We displayed its contents using:
cat flag.txt
Flag:
b40abdfe23665f766f9c61ecba8a4c19

Conclusion
This machine demonstrated a critical misconfiguration where the Telnet service was running with root login enabled and no password required. This highlights the importance of:
✅ Disabling obsolete services like Telnet
✅ Enforcing strong authentication mechanisms
✅ Using SSH instead of Telnet for secure remote access
