# Packet Tracer Lab: Configure Secure Passwords and SSH
This a basic network-device Configuration that any computer Network practitioner must know.
## Project Overview

This repository contains files and documentation for a Cisco Packet Tracer lab focused on implementing essential security measures on network devices (a router and a switch). The lab covers configuring secure administrative passwords, enabling SSH for secure remote access, and hardening device configurations against common vulnerabilities.

## Scenario

The network administrator requires RTA (Router A) and SW1 (Switch 1) to be prepared for deployment with enabled security measures before they can be connected to the broader network.

## Objectives

* Configure IP addressing on end devices (PCA) and network devices (RTA, SW1).
* Secure administrative access on RTA and SW1 using strong passwords.
* Encrypt all plaintext passwords.
* Disable insecure services like DNS lookup where not needed.
* Configure SSH on both RTA and SW1 for secure remote management.
* Create local user accounts for SSH authentication.
* Generate RSA cryptographic keys for SSH.
* Implement login security features (e.g., blocking failed attempts).
* Configure VTY line properties (e.g., timeout, transport input).
* Disable unused switch ports for enhanced security.
* Save configurations to NVRAM.

## Topology

A simple network topology consisting of:
* **RTA:** Cisco Router
* **SW1:** Cisco Switch
* **PCA:** End Host (PC)
* [Screenshot: PCA SSH Connection to RTA](screenshots/pca_ssh_rta.png)

## Configuration Details

Below are the key configuration commands applied to RTA and SW1. Full configuration files are available in the repository.

### RTA (Router) Configuration Highlights:
* Hostname: `RTA`
* IP Address: `G0/0 - 172.16.1.1/24`
* `service password-encryption`
* `security password min-length 10`
* `enable secret YOUR_STRONG_SECRET_PASSWORD` 
* `no ip domain-lookup`
* `ip domain-name CCNA.com`
* `username [your_chosen_user] secret [your_chosen_password]`
* `crypto key generate rsa modulus 1024`
* `login block-for 180 attempts 4 within 120`
* `line vty 0 4`
* `transport input ssh`
* `login local`
* `exec-timeout 6 0`

### SW1 (Switch) Configuration Highlights:
* Hostname: `SW1`
* IP Address: `VLAN 1 - 172.16.1.2/24`
* Default Gateway: `172.16.1.1`
* `interface range F0/2-24, G0/2`
* `shutdown` (Disabling unused ports)

## Verification & Screenshots

1.  **IP Connectivity:** Confirmed PCA could ping RTA and SW1.
2.  **SSH Connection:** Successfully established an SSH connection from PCA to RTA using the configured local user.
3.  **Password Encryption Verification:** Checked `show running-config` to ensure passwords were encrypted.
4.  **Unused Port Status:** Verified unused ports on SW1 were administratively down.

## Files in this Repository

* `PacketTracer_SecurePasswords_SSH.pka`: The Packet Tracer lab file.
* `screenshots/`: Directory containing images of the lab setup and score.
* `lab_instructions.md`: Original lab instructions (optional).

## Key Lessons Learned

* The critical importance of encrypting all passwords on network devices.
* SSH provides a secure alternative to Telnet for remote administration, protecting sensitive login credentials.
* Disabling unused switch ports is a simple yet effective hardening measure against unauthorized access.
* Implementing login blocking mechanisms helps mitigate brute-force attacks.
* The use of local user accounts and strong RSA keys is fundamental for robust device security.
* Understanding `exec-timeout` for preventing unauthorized access to idle sessions.

---
**Philiphine Cheptanui | Information Scientist, BSc | Computer Network | Cybersecurity | WordPress | Data Entry | Research | Writer.**


---

## 🌐 Connect with me:

 [LinkedIn](https://linkedin.com/in/philiphinecheptanui) &emsp;&emsp;
 [Email](koimaphilipine@gmail.com) &emsp;&emsp;
 [PortFolio Blog](https://compnetworksecurity.blogspot.com/) &emsp;&emsp;
 [Repository](https://github.com/philiphineck/Use-Wireshark-to-View-Network-Traffic) 
