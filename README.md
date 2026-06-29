# React2Shell

## Objective

The objective of this lab is to identify and exploit a vulnerable web application to achieve Remote Code Execution (RCE). The assessment demonstrates the complete penetration testing process, including reconnaissance, vulnerability validation, exploitation, and post-exploitation verification in a controlled lab environment.

## Skills Learned

- Web application reconnaissance and enumeration
- Identifying web application vulnerabilities
- Remote Code Execution (RCE) exploitation
- Authentication bypass techniques (where applicable)
- Exploit research and validation
- Executing public proof-of-concept (PoC) exploits
- Session and cookie manipulation
- Command execution on a compromised target
- Verifying successful exploitation
- Documenting security findings and impact

## Tools Used

- Nmap
- Burp Suite
- Firefox/Chrome Developer Tools
- Python
- Public Proof-of-Concept (PoC) exploit
- Linux Terminal (Kali Linux)
- Wappalyzer
  
## Steps
==> This lab was completed as part of the TryHackMe room "React2Shell: CVE-2025-55182" 
link: https://tryhackme.com/room/react2shellcve202555182

<img width="2542" height="1347" alt="Screenshot 2026-06-29 082939" src="https://github.com/user-attachments/assets/397bb19f-2306-4d9d-ad35-30c4c64db946" />

Next, we perform an **Nmap** scan to discover the open ports and exposed services on the target system.

<img width="1714" height="848" alt="Screenshot 2026-06-29 083510" src="https://github.com/user-attachments/assets/7dbfd9d9-5c7c-4935-8f41-ad60a0c79f5f" />

The scan results show that two ports are open:

* **Port 22** – SSH (Secure Shell)
* **Port 3000** – Web application

Next, open a web browser and access the application using **port 3000**.

<img width="1716" height="888" alt="Screenshot 2026-06-29 083816" src="https://github.com/user-attachments/assets/683129a6-1432-4a96-9400-fae42ba76f5a" />

Next, use **Wappalyzer** to fingerprint the target web application and identify the technologies, frameworks, and software versions it exposes. This information can help with technology identification and further vulnerability research.

<img width="1718" height="736" alt="Screenshot 2026-06-29 084024" src="https://github.com/user-attachments/assets/ca02a9eb-e0f9-4409-95b5-7fb8217c2802" />

The target web application is running Next.js version 16.0.6. Based on vulnerability research, this version is associated with CVE-2025-66478.

<img width="1714" height="923" alt="Screenshot 2026-06-29 084451" src="https://github.com/user-attachments/assets/b95d68ae-98e5-423e-8b99-b6112aacc42f" />


