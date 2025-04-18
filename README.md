# SECURITY-LABS-IFEANYI
by Ifeanyi Omeata

##### Introduction to Cyber Security

<details>
  <summary>Offensive Security Intro </summary>
  
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
  <summary>Defensive Security Intro </summary>
 
  ##### 1. Some of the tasks that are related to defensive security include:
  - [ ] User cyber security awareness: Training users about cyber security helps protect against attacks targeting their systems.
  - [ ] Documenting and managing assets: We need to know the systems and devices we must manage and protect adequately.
  - [ ] Updating and patching systems: Ensuring that computers, servers, and network devices are correctly updated and patched against any known vulnerability (weakness).
  - [ ] Setting up preventative security devices: firewall and intrusion prevention systems (IPS) are critical components of preventative security.
  - [ ] Firewalls control what network traffic can go inside and what can leave the system or network.
  - [ ] IPS blocks any network traffic that matches present rules and attack signatures.
  - [ ] Setting up logging and monitoring devices: Proper network logging and monitoring are essential for detecting malicious activities and intrusions.
  - [ ] If a new unauthorized device appears on our network, we should be able to detect it.

  ##### 2. Security Operations Center (SOC)
  - [ ] A Security Operations Center (SOC) is a team of cyber security professionals that monitors the network and its systems to detect malicious cyber security events.
  - [ ] Some of the main areas of interest for a SOC are:
      - [ ] Vulnerabilities: Whenever a system vulnerability (weakness) is discovered, it is essential to fix it by installing a proper update or patch. When a fix is unavailable, the necessary measures should be taken to prevent an attacker from exploiting it. Although remediating vulnerabilities is vital to a SOC, it is not necessarily assigned to them.
      - [ ] Policy violations: A security policy is a set of rules required to protect the network and systems. For example, it might be a policy violation if users upload confidential company data to an online storage service.
      - [ ] Unauthorized activity: Consider the case where a user’s login name and password are stolen, and the attacker uses them to log into the network. A SOC must detect and block such an event as soon as possible before further damage is done.
      - [ ] Network intrusions: No matter how good your security is, there is always a chance for an intrusion. An intrusion can occur when a user clicks on a malicious link or when an attacker exploits a public server. Either way, when an intrusion occurs, we must detect it as soon as possible to prevent further damage.

  ##### 3. Threat Intelligence
  - [ ] In this context, intelligence refers to information you gather about actual and potential enemies.
  - [ ] A threat is any action that can disrupt or adversely affect a system.
  - [ ] Threat intelligence collects information to help the company better prepare against potential adversaries.
  - [ ] The purpose would be to achieve a threat-informed defence. Different companies have different adversaries.
  - [ ] Some adversaries might seek to steal customer data from a mobile operator; however, other adversaries are interested in halting the production in a petroleum refinery.
  - [ ] Example adversaries include a nation-state cyber army working for political reasons and a ransomware group acting for financial purposes.

  ##### 4. Digital Forensics
  - [ ] In this context, intelligence refers to information you gather about actual and potential enemies.
  - [ ] A threat is any action that can disrupt or adversely affect a system.
  - [ ] Threat intelligence collects information to help the company better prepare against potential adversaries.
  - [ ] The purpose would be to achieve a threat-informed defence. Different companies have different adversaries.
  - [ ] Some adversaries might seek to steal customer data from a mobile operator; however, other adversaries are interested in halting the production in a petroleum refinery.
  - [ ] Example adversaries include a nation-state cyber army working for political reasons and a ransomware group acting for financial purposes.

</details>
