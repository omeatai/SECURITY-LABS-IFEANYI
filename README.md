# SECURITY-LABS-IFEANYI
by Ifeanyi Omeata

##### Pre-Security

<details>
  <summary>1-Introduction to Cyber Security</summary>

<details>
  <summary>Gobuster Offensive Attack</summary>
  
  ##### 1. What is Gobuster?
  - [ ] [Gobuster](https://github.com/OJ/gobuster) is a tool used to brute-force: 
      - [ ] URIs (directories and files) in web sites.
      - [ ] DNS subdomains (with wildcard support).
      - [ ] Open Amazon S3 buckets
      - [ ] Open Google Cloud buckets
      - [ ] TFTP servers
  - [ ] Gobuster will take a list of potential page or directory names and try accessing a website with each of them; if the page exists, it tells you.

  
  ##### 2. Using Gobuster To Find Hidden Website Pages
  - [ ] Type the following command into the terminal to find potentially hidden pages on website
  ```
  gobuster -u http://fakebank.thm -w wordlist.txt dir
  ```
  - [ ] -u is used to state the website we're scanning
  - [ ] -w takes a list of words to iterate through to find hidden pages.

</details>

<details>
  <summary>The 4 phases of the incident response process </summary>
 
  ##### The four major phases of the incident response process are:

- [ ] Preparation: This requires a team trained and ready to handle incidents. Ideally, various measures are put in place to prevent incidents from happening in the first place.
- [ ] Detection and Analysis: The team has the necessary resources to detect any incident; moreover, it is essential to analyze any detected incident further to learn about its severity.
- [ ] Containment, Eradication, and Recovery: Once an incident is detected, it is crucial to stop it from affecting other systems, eliminate it, and recover the affected systems. For instance, when we notice that a system is infected with a computer virus, we would like to stop (contain) the virus from spreading to other systems, clean (eradicate) the virus, and ensure proper system recovery.
- [ ] Post-Incident Activity: After a successful recovery, a report is produced, and the lesson learned is shared to prevent similar future incidents.

![image](https://github.com/user-attachments/assets/fe934afc-6615-4bcb-9c21-526d89042fd5)

</details>

<details>
  <summary>The 3 Types of Malicious Software </summary>
 
  ##### The 3 Types of Malicious Software are:

- [ ] A virus - is a piece of code (part of a program) that attaches itself to a program. It is designed to spread from one computer to another and works by altering, overwriting, and deleting files once it infects a computer. The result ranges from the computer becoming slow to unusable.
- [ ] Trojan Horse - is a program that shows one desirable function but hides a malicious function underneath. For example, a victim might download a video player from a shady website that gives the attacker complete control over their system.
- [ ] Ransomware - is a malicious program that encrypts the user’s files. Encryption makes the files unreadable without knowing the encryption password. The attacker offers the user the encryption password if the user is willing to pay a “ransom.”

</details>

<details>
  <summary>The 2 ways to learn about malicious programs </summary>
 
  ##### The 2 ways to learn about malicious programs are:

- [ ] Static analysis - works by inspecting the malicious program without running it. This usually requires solid knowledge of assembly language (the processor’s instruction set, i.e., the computer’s fundamental instructions).
- [ ] Dynamic analysis - works by running the malware in a controlled environment and monitoring its activities. It lets you observe how the malware behaves when running.

</details>

<details>
  <summary>What would you call a team of cyber security professionals that monitors a network and its systems for malicious events? </summary>
 
  ##### Security Operations Center

  - [ ] A Security Operations Center (SOC) is a team of cyber security professionals that monitors the network and its systems to detect malicious cyber security events. Some of the main areas of interest for a SOC are:
      - [ ] Vulnerabilities: Whenever a system vulnerability (weakness) is discovered, it is essential to fix it by installing a proper update or patch. When a fix is unavailable, the necessary measures should be taken to prevent an attacker from exploiting it. Although remediating vulnerabilities is vital to a SOC, it is not necessarily assigned to them.
      - [ ] Policy violations: A security policy is a set of rules required to protect the network and systems. For example, it might be a policy violation if users upload confidential company data to an online storage service.
      - [ ] Unauthorized activity: Consider the case where a user’s login name and password are stolen, and the attacker uses them to log into the network. A SOC must detect and block such an event as soon as possible before further damage is done.
      - [ ] Network intrusions: No matter how good your security is, there is always a chance for an intrusion. An intrusion can occur when a user clicks on a malicious link or when an attacker exploits a public server. Either way, when an intrusion occurs, we must detect it as soon as possible to prevent further damage.

</details>

<details>
  <summary>What does DFIR stand for?</summary>
 
  ##### Digital Forensics and Incident Response

  - [ ] Forensics is the application of science to investigate crimes and establish facts. With the use and spread of digital systems, such as computers and smartphones, a new branch of forensics was born to investigate related crimes: computer forensics, which later evolved into digital forensics.
  - [ ] In defensive security, the focus of digital forensics shifts to analyzing evidence of an attack and its perpetrators and other areas such as intellectual property theft, cyber espionage, and possession of unauthorized content. 
  - [ ] An incident usually refers to a data breach or cyber attack; however, in some cases, it can be something less critical, such as a misconfiguration, an intrusion attempt, or a policy violation.
  - [ ] Examples of a cyber attack include an attacker making our network or systems inaccessible, defacing (changing) the public website, and data breach (stealing company data).
  - [ ] How would you respond to a cyber attack? Incident response specifies the methodology that should be followed to handle such a case.
  - [ ] The aim is to reduce damage and recover in the shortest time possible. Ideally, you would develop a plan that is ready for incident response.

</details>

<details>
  <summary>Which kind of malware requires the user to pay money to regain access to their files?</summary>
 
  ##### Ransomware

  - [ ] Ransomware - is a malicious program that encrypts the user’s files. Encryption makes the files unreadable without knowing the encryption password. The attacker offers the user the encryption password if the user is willing to pay a “ransom.”

</details>

<details>
  <summary>Open-source databases for searching for malicious IPs </summary>
 
  ##### There are many open-source databases out there for searching for malicious IPs:

   - [ ] VirusTotal
   - [ ] AbuseIPDB
   - [ ] Cisco Talos Intelligence

</details>

</details>

<details>
  <summary>2-Network Fundamentals</summary>
 
<details>
  <summary>What is the key term for devices that are connected together? </summary>

   - [ ] Network

</details>

<details>
  <summary>Who invented the World Wide Web? </summary>

   - [ ] Tim Berners-Lee

</details>



























</details>

<details>
  <summary>3-How The Web Works</summary>
 
  ##### Ransomware

  - [ ] Ransomware 

</details>

<details>
  <summary>4-Linux Fundamentals</summary>
 
  ##### Ransomware

  - [ ] Ransomware 

</details>

<details>
  <summary>5-Windows Fundamentals</summary>
 
  ##### Ransomware

  - [ ] Ransomware 

</details>









