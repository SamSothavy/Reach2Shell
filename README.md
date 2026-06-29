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

Next, clone the scanner repository from GitHub using the following command:

```bash
git clone https://github.com/SamSothavy/customized_exploit.git
```

<img width="1710" height="905" alt="Screenshot 2026-06-29 085609" src="https://github.com/user-attachments/assets/54d79721-77c0-4019-9fc9-e31aee0b0f54" />

The exploit is executed using Python, specifying the target URL and a command parameter to confirm remote command execution:

<img width="1710" height="846" alt="Screenshot 2026-06-29 090731" src="https://github.com/user-attachments/assets/57e5cb89-9473-4291-8d24-2ee9ac2dc209" />

There are two methods available to compromise the target server:

1. **Raw Execution** – Directly execute commands on the target system.
2. **Download with Auto-Execution** – Download a payload to the target system and execute it automatically.

Both methods can be used depending on the lab scenario and exploitation approach.

<img width="1280" height="746" alt="photo_2026-05-09_11-19-43" src="https://github.com/user-attachments/assets/5993e6ff-1108-42b9-a97f-7f9dc8c4667d" />

**Raw Execution**

Port 4444 is opened to listen for incoming connections from the target system.

<img width="1710" height="439" alt="Screenshot 2026-06-29 091611" src="https://github.com/user-attachments/assets/95cd84b1-772d-49f5-827b-c0fe9ef05899" />

Then, we use a reverse shell script

<img width="1710" height="862" alt="Screenshot 2026-06-29 091801" src="https://github.com/user-attachments/assets/411e9270-8768-4ccb-bf65-45a09a64ea67" />

Failed attempt

<img width="1710" height="530" alt="Screenshot 2026-06-29 092136" src="https://github.com/user-attachments/assets/91efeefc-3427-43c5-94d1-9449f04d9c12" />

Encoded not working

<img width="1712" height="501" alt="Screenshot 2026-06-29 092311" src="https://github.com/user-attachments/assets/61f1b254-5a31-4fd5-8303-e33fb773273c" />

The Raw Execution method was unsuccessful in this scenario.

 **Download with Auto-Execution**
 
We create a `.sh` file that contains a reverse shell script.

<img width="1709" height="497" alt="Screenshot 2026-06-29 092800" src="https://github.com/user-attachments/assets/3bd4a148-0719-4f89-956d-71080e41b452" />

Then, hosting it

<img width="1715" height="499" alt="Screenshot 2026-06-29 093745" src="https://github.com/user-attachments/assets/c607e5ed-1ab1-4131-a2b3-fcaf0fbdbe9f" />


<img width="1714" height="499" alt="Screenshot 2026-06-29 093403" src="https://github.com/user-attachments/assets/0b808de2-8838-4cd4-82f0-f1836a9399b3" />

<img width="1713" height="766" alt="Screenshot 2026-06-29 094449" src="https://github.com/user-attachments/assets/ac7acc00-5bb8-4d14-a640-254a3195655a" />

We have successfully gained access to the target server.

<img width="1717" height="619" alt="Screenshot 2026-06-29 094548" src="https://github.com/user-attachments/assets/b02b0eec-8d57-48fa-8eb8-6ac768178187" />




 

