# SECURITY-LABS-IFEANYI
by Ifeanyi Omeata

##### Introduction to Cyber Security

<details>
  <summary>Gobuster</summary>
  
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
  <summary>The four major phases of the incident response process </summary>
 
  ##### The four major phases of the incident response process are:

- [ ] Preparation: This requires a team trained and ready to handle incidents. Ideally, various measures are put in place to prevent incidents from happening in the first place.
- [ ] Detection and Analysis: The team has the necessary resources to detect any incident; moreover, it is essential to analyze any detected incident further to learn about its severity.
- [ ] Containment, Eradication, and Recovery: Once an incident is detected, it is crucial to stop it from affecting other systems, eliminate it, and recover the affected systems. For instance, when we notice that a system is infected with a computer virus, we would like to stop (contain) the virus from spreading to other systems, clean (eradicate) the virus, and ensure proper system recovery.
- [ ] Post-Incident Activity: After a successful recovery, a report is produced, and the lesson learned is shared to prevent similar future incidents.


</details>
