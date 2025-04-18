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
  ```
  gobuster -u http://fakebank.thm -w wordlist.txt dir
  ```
  - [ ] -u is used to state the website we're scanning
  - [ ] -w takes a list of words to iterate through to find hidden pages.


  ##### 1. What is Gobuster?
  - [ ] [Gobuster](https://github.com/OJ/gobuster) is a tool used to brute-force: 
      - [ ] URIs (directories and files) in web sites.
      - [ ] DNS subdomains (with wildcard support).
      - [ ] Open Amazon S3 buckets
      - [ ] Open Google Cloud buckets
      - [ ] TFTP servers
  - [ ] Gobuster will take a list of potential page or directory names and try accessing a website with each of them; if the page exists, it tells you.


</details>
