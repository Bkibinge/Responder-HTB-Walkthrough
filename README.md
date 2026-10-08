# Responder - Hack The Box Walkthrough

![HackTheBox](https://img.shields.io/badge/HackTheBox-Responder-blue)
![Difficulty](https://img.shields.io/badge/Difficulty-Very%20Easy-green)
![OS](https://img.shields.io/badge/OS-Windows-blue)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

## 📌 Machine Information

| Detail | Value |
|--------|-------|
| **Name** | Responder |
| **Difficulty** | Very Easy |
| **Target OS** | Windows |
| **Attacker OS** | Kali Linux |
| **Platform** | Hack The Box |
| **Skills** | RFI, NTLM Hash Capture, Password Cracking, WinRM |

## 🎯 Objective

Capture the flag from the Responder machine by exploiting an RFI vulnerability, capturing an NTLM hash with Responder, cracking the password, and accessing the machine via WinRM.

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **OpenVPN** | Connect to HTB network |
| **Responder** | Capture NTLM hashes |
| **John the Ripper** | Crack NTLMv2 hashes |
| **Evil-WinRM** | Remote Windows management |
| **curl** | Trigger RFI vulnerability |

## 📸 Walkthrough

### 1. VPN Connection
Connected to the HTB Machines network using OpenVPN.

![VPN Connected](images/01-vpn-connected.png)

---

### 2. Target Reconnaissance
Verified target reachability with ping.

![Target Reachable](images/02-target-reachable.png)

---

### 3. Hosts File Configuration
Added `unika.htb` to `/etc/hosts`.

![Hosts Updated](images/03-hosts-file.png)

---

### 4. Responder Setup
Started Responder to capture NTLM hashes on `tun0`.

![Responder Started](images/04-responder-started.png)

---

### 5. RFI Exploitation
Triggered the RFI vulnerability to force SMB authentication.

![RFI Trigger](images/05-rfi-trigger.png)


---

### 6. NTLM Hash Capture
Responder captured the NTLMv2 hash of the Administrator account.

![Hash Captured](images/06-hash-captured.png)

---

### 7. Password Cracking
Cracked the hash with John the Ripper.

![Hash Cracked](images/07-hash-cracked.png)

---

### 8. WinRM Access
Connected to the target via Evil-WinRM.

![WinRM Connected](images/08-winrm-connected.png)

---

### 9. Flag Retrieval
Retrieved the flag from Mike's desktop.

![Flag Retrieved](images/09-flag-retrieved.png)


---

## 📊 Attack Chain

HTB VPN (10.10.14.61)
↓
Target (10.129.106.23)
↓
RFI Vulnerability (//10.10.14.179/test.txt)
↓
SMB Connection to Attacker
↓
NTLM Hash Captured by Responder
↓
Hash Cracked with John (badminton)
↓
WinRM Access as Administrator
↓
Flag: ea81b7afddd03efaa0945333ed147fac


## 🏆 Flag

ea81b7afddd03efaa0945333ed147fac

## 📄 Full Documentation

- **PDF Report:** [Responder-HTB-Walkthrough.pdf](Responder-HTB-Walkthrough.pdf)
- **Editable DOCX:** [Responder-HTB-Walkthrough.docx](Responder-HTB-Walkthrough.docx)

Documented in LibreOffice Writer on Kali Linux.

## 🛡️ Key Takeaways

- RFI vulnerabilities can force servers to authenticate to attacker-controlled resources
- NTLM hashes can be captured and cracked offline
- Weak passwords are easily compromised
- WinRM provides remote access when credentials are obtained

## ⚠️ Disclaimer

This walkthrough is for **educational purposes only**. All testing was performed on Hack The Box, a legal penetration testing platform. Never test systems without explicit authorization.

## 📚 References

- [Hack The Box](https://www.hackthebox.com/)
- [Responder Tool](https://github.com/lgandx/Responder)
- [John the Ripper](https://www.openwall.com/john/)
- [Evil-WinRM](https://github.com/Hackplayers/evil-winrm)




