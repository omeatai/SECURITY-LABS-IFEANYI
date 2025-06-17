# SECURITY-LABS-IFEANYI
by Ifeanyi Omeata

## Pre-Security (TRY-HACK-ME)

- [ ] 1-Introduction to Cyber Security
  - [x] [Offensive Security Intro](https://tryhackme.com/room/offensivesecurityintro)
  - [x] [Defensive Security Intro](https://tryhackme.com/room/defensivesecurityintro)
  - [x] [Careers in Cyber Security](https://tryhackme.com/room/careersincyber)
- [ ] 2-Network Fundamentals
  - [x] [What is Networking?](https://tryhackme.com/room/whatisnetworking)
  - [x] [Intro to LAN](https://tryhackme.com/room/introtolan)
  - [x] [OSI Model](https://tryhackme.com/room/osimodelzi)
  - [x] [Packets & Frames](https://tryhackme.com/room/packetsframes)
  - [x] [Extending Your Network](https://tryhackme.com/room/extendingyournetwork)
- [ ] 3-How The Web Works
  - [x] [DNS in Detail](https://tryhackme.com/room/dnsindetail)
  - [ ] [HTTP in Detail](https://tryhackme.com/room/httpindetail)
  - [ ] [How Websites Work]()
  - [ ] [Putting it all together]()
- [ ] 4-Linux Fundamentals
  - [ ] [Linux Fundamentals Part 1]()
  - [ ] [Linux Fundamentals Part 2]()
  - [ ] [Linux Fundamentals Part 3]()
- [ ] 5-Windows Fundamentals
  - [ ] [Windows Fundamentals Part 1]()
  - [ ] [Windows Fundamentals Part 2]()
  - [ ] [Windows Fundamentals Part 3]()

<details>
<summary>Offensive Security Intro - Using Gobuster To Find Hidden Website Pages</summary>

  ```
  gobuster -u http://fakebank.thm -w wordlist.txt dir
  ```
  - [ ] -u is used to state the website we're scanning
  - [ ] -w takes a list of words to iterate through to find hidden pages.

</details>
<details>
<summary>DNS in Detail - CNAME of shop.website.thm </summary>

  ```
  nslookup --type=CNAME shop.website.thm
  ```

  ```
  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  shop.website.thm canonical name = shops.myshopify.com
  ```

</details>
<details>
<summary>DNS in Detail - TXT record of website.thm </summary>

  ```
  nslookup --type=TXT website.thm
  ```

  ```
  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  website.thm text = "THM{7012BBA60997F35A9516C2E16D2944FF}"
  ```

</details>
<details>
<summary>DNS in Detail - numerical priority value for the MX record </summary>

  ```
  nslookup --type=MX website.thm
  ```

  ```
  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  website.thm mail exchanger = 30 alt4.aspmx.l.google.com
  ```

</details>
<details>
<summary>DNS in Detail - IP address for the A record of www.website.thm </summary>

  ```
  nslookup --type=A website.thm
  ```

  ```
  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  Name: website.thm
  Address: 10.10.10.10
  ```

</details>
  

## Cyber Security 101 (TRY-HACK-ME)

- [ ] 1-Start Your Cyber Security Journey
  - [ ] [Offensive Security Intro]()
  - [ ] [Defensive Security Intro]()
  - [ ] [Search Skills]()
- [ ] 2-Linux Fundamentals
  - [ ] [Linux Fundamentals Part 1]()
  - [ ] [Linux Fundamentals Part 2]()
  - [ ] [Linux Fundamentals Part 3]()
- [ ] 3-Windows and AD Fundamentals
  - [ ] [Windows Fundamentals 1]()
  - [ ] [Windows Fundamentals 2]()
  - [ ] [Windows Fundamentals 3]()
  - [ ] [Active Directory Basics]()
- [ ] 4-Command Line
  - [ ] [Windows Command Line]()
  - [ ] [Windows PowerShell]()
  - [ ] [Linux Shells]()
- [ ] 5-Networking
  - [ ] [Networking Concepts]()
  - [ ] [Networking Essentials]()
  - [ ] [Networking Core Protocols]()
  - [ ] [Networking Secure Protocols]()
  - [ ] [Wireshark: The Basics]()
  - [ ] [Tcpdump: The Basics]()
  - [ ] [Nmap: The Basics]()
- [ ] 6-Cryptography
  - [ ] [Cryptography Basics]()
  - [ ] [Public Key Cryptography Basics]()
  - [ ] [Hashing Basics]()
  - [ ] [John the Ripper: The Basics]()
- [ ] 7-Exploitation Basics
  - [ ] [Moniker Link (CVE-2024-21413)]()
  - [ ] [Metasploit: Introduction]()
  - [ ] [Metasploit: Exploitation]()
  - [ ] [Metasploit: Meterpreter]()
  - [ ] [Blue]()
- [ ] 8-Web Hacking
  - [ ] [Web Application Basics]()
  - [ ] [JavaScript Essentials]()
  - [ ] [SQL Fundamentals]()
  - [ ] [Burp Suite: The Basics]()
  - [ ] [OWASP Top 10 - 2021]()
- [ ] 9-Offensive Security Tooling
  - [ ] [Hydra]()
  - [ ] [Gobuster: The Basics]()
  - [ ] [Shells Overview]()
  - [ ] [SQLMap: The Basics]()
- [ ] 10-Defensive Security
  - [ ] [Defensive Security Intro]()
  - [ ] [SOC Fundamentals]()
  - [ ] [Digital Forensics Fundamentals]()
  - [ ] [Incident Response Fundamentals]()
  - [ ] [Logs Fundamentals]()
- [ ] 11-Security Solutions
  - [ ] [Introduction to SIEM]()
  - [ ] [Firewall Fundamentals]()
  - [ ] [IDS Fundamentals]()
  - [ ] [Vulnerability Scanner Overview]()
- [ ] 12-Defensive Security Tooling
  - [ ] [CyberChef: The Basics]()
  - [ ] [CAPA: The Basics]()
  - [ ] [REMnux: Getting Started]()
  - [ ] [FlareVM: Arsenal of Tools]()
- [ ] 13-Build Your Cyber Security Career
  - [ ] [Security Principles]()
  - [ ] [Careers in Cyber]()
  - [ ] [Training Impact on Teams]()








## C

##### N
 
<details>
  <summary>W </summary>

   - [ ] Network

</details>






