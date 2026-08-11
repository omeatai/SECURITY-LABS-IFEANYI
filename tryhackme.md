# TRYHACKME.COM | [ONLINE](https://tryhackme.com/paths)

# A. PRE-SECURITY COURSE

## 1-Introduction to Cyber Security

<details>
  <summary>Offensive Security Intro</summary>

## Introduction

Offensive Security is about thinking like an attacker to find weaknesses before real hackers do. In this TryHackMe room, you hack your first website in a safe and legal environment using FakeBank, a fake banking application, to see how ethical hackers operate.

## Detailed Explanation

- [x] **Think like a hacker**
  - Offensive Security means simulating a hacker's actions to find weaknesses
  - The room lets you practice ethical hacking against FakeBank in a controlled lab
- [x] **Starting the lab**
  - The room uses a virtual desktop to simulate a real system
  - A browser opens automatically and displays FakeBank, the target application
  - Your bank account number in FakeBank is **8881**
- [x] **Find hidden pages**
  - A common weakness is leaving hidden pages accessible (e.g. admin or transfer panels)
  - Use the terminal on the machine to run **dirb** (Dirbuster-style directory brute-forcing)
  - Lines in dirb output that start with `+` are pages that were found
  - Dirb finds two URLs on FakeBank: `/images` and `/bank-transfer`
- [x] **Attack the admin page**
  - The hidden admin panel at `/bank-transfer` lets you add money to an account
  - Open `http://fakebank.thm/bank-transfer` in the simulated browser (append `/bank-transfer` to the URL)
  - Use account number **8881** and deposit **$2000** (or more)
  - Return to your account page and confirm the balance is positive
  - When the balance turns positive, a green pop-up appears with the words **BANK-HACKED** (ALL CAPS)

## Terminal Commands

Dirb is used to discover hidden directories and pages on a target website. Pass the target URL; any output lines starting with `+` indicate discovered pages.

```bash
dirb http://fakebank.thm
```

Example idea of what you are looking for: dirb reports existing paths such as `http://fakebank.thm/images` and `http://fakebank.thm/bank-transfer`. Use the hidden `/bank-transfer` path in the browser to continue the attack.

## Code

No code sections in this room; the activity uses terminal commands (dirb) and the FakeBank web interface only.

## Questions and Answers

### Question 1: Which term describes simulating a hacker's actions to find weaknesses?

<details>
<summary>Answer</summary>

- [x] Offensive Security

</details>

### Question 2: What is Defensive Security in contrast to Offensive Security?

<details>
<summary>Answer</summary>

- [x] Defensive Security focuses on protecting systems and responding to threats, rather than simulating attacker actions to find weaknesses.

</details>

### Question 3: What application do you target in this room?

<details>
<summary>Answer</summary>

- [x] FakeBank — a fake banking application in a safe, legal lab environment.

</details>

### Question 4: What is the bank account number in the FakeBank application?

<details>
<summary>Answer</summary>

- [x] 8881

</details>

### Question 5: Why might hidden pages on a website be a security risk?

<details>
<summary>Answer</summary>

- [x] They can leave sensitive functionality (e.g. admin or money-transfer panels) accessible if not properly restricted.

</details>

### Question 6: Which tool do you use in the terminal to find hidden pages on FakeBank?

<details>
<summary>Answer</summary>

- [x] dirb (Dirbuster-style directory brute-forcing)

</details>

### Question 7: What command runs dirb against FakeBank?

<details>
<summary>Answer</summary>

- [x] `dirb http://fakebank.thm`

</details>

### Question 8: How does dirb mark pages it has found in its output?

<details>
<summary>Answer</summary>

- [x] Lines that start with `+` indicate discovered pages.

</details>

### Question 9: Dirb found `http://fakebank.thm/images`. What is the other hidden URL?

<details>
<summary>Answer</summary>

- [x] http://fakebank.thm/bank-transfer

</details>

### Question 10: How do you open the hidden admin panel in the simulated browser?

<details>
<summary>Answer</summary>

- [x] Append `/bank-transfer` to the FakeBank URL in the browser.

</details>

### Question 11: What do you do on the `/bank-transfer` page to complete the hack?

<details>
<summary>Answer</summary>

- [x] Use account number 8881
- [x] Deposit $2000 (or more)
- [x] Return to your account page and confirm the balance is positive

</details>

### Question 12: When your balance turns positive, what appears and what is the answer flag?

<details>
<summary>Answer</summary>

- [x] A pop-up with green text
- [x] BANK-HACKED (ALL CAPS)

</details>

### Question 13: What is the main goal of Offensive Security as described in this room?

<details>
<summary>Answer</summary>

- [x] Think like an attacker to find weaknesses before real hackers do.

</details>

### Question 14: What environment does this room use so you can practice safely?

<details>
<summary>Answer</summary>

- [x] A virtual desktop that simulates a real system, with FakeBank opened in a browser.

</details>

### Question 15: After depositing money, where do you confirm success?

<details>
<summary>Answer</summary>

- [x] On your account page — confirm the balance is now positive and note the green pop-up text.

</details>

## Summary

This room introduces Offensive Security by having you think like a hacker against FakeBank. You start a virtual lab, note account **8881**, use **dirb** to find hidden pages (`/images` and `/bank-transfer`), abuse the exposed transfer panel to deposit funds, and capture the green flag **BANK-HACKED** when the balance turns positive.

## References

- [Offensive Security Intro – TryHackMe](https://tryhackme.com/room/offensivesecurityintro)

</details>

<details>
  <summary>Defensive Security Intro</summary>

## Introduction

Defensive security is about defending and securing devices and systems by detecting and investigating attacks, then responding before damage occurs. Unlike offensive security, you do not attack systems—you monitor and protect them. In this TryHackMe room, you help apprentice SOC analyst Joe use a monitoring dashboard to spot suspicious traffic, identify the attack, and contain it against FakeBank.

## Detailed Explanation

- [x] **Think like a Defender**
  - Defensive security is the process of defending and securing devices and systems
  - Focus areas: detecting attacks, investigating them, and responding before damage occurs
  - Contrast with offensive security: defenders monitor and protect; they do not attack systems
- [x] **Detect Suspicious Activity**
  - Joe is an apprentice SOC analyst on his first solo shift
  - Real SOC analysts use monitoring dashboards to separate normal activity from suspicious behaviour
  - Lab steps:
    - Open the monitoring dashboard
    - Review recent alerts
    - Identify the suspicious source IP
  - Monitoring tools show what activity is taking place on computing devices so defenders can confirm legitimacy and investigate the rest
  - Suspicious source IP generating the traffic: **32.122.195.63**
- [x] **Identify the Attack**
  - Knowing something is wrong is only half the battle—you must determine what the attacker is trying to do
  - Lab steps:
    - Investigate the attack that has occurred
    - View the "URL Discovery Attempts" list
    - Look at the latest "URL Discovery Attempts" entry
  - The dashboard history shows the attacker rapidly trying many attempts to access hidden pages
  - Once you know the attacker's goal, you can stop them and fix the weakness that allowed the attack
  - Latest URL the attacker tried to find: **https://fakebank.com/admin**
- [x] **Stop the Attack (containment)**
  - Immediate priority in defensive security is **containment**—stopping the attack while it is happening to protect the organisation
  - Joe has already completed some security updates; you complete the last action
  - Lab steps:
    - Review the security actions (two already done for you)
    - Block the attacker's IP **32.122.195.63** via "Add Firewall Rule"
    - Select **BLOCK** from the dropdown and press **Apply**
  - Measures this monitoring tool supports:
    - **Blocking the IP address** — prevents the attacker's device from accessing systems entirely (good immediate step)
    - **Applying rate limiting** — limits connections in a given time for everyone; useful when the attacker rapidly hits many pages
    - **Updating security rules** — tightens access controls to sensitive pages the attacker slipped through
  - Success flag: **THM{FAKEBANK-SECURED}**

## Terminal Commands

This room uses an interactive monitoring dashboard in the browser (View Site). There are no primary command-line tools; investigation and response happen through the SOC-style UI (alerts, URL discovery list, and firewall rules).

```bash
# No primary terminal commands in this defensive dashboard lab.
```

## Code

No code sections in this room; the activity uses the monitoring dashboard and firewall rule controls only.

## Questions and Answers

### Question 1: What is the main goal of defensive security?

<details>
<summary>Answer</summary>

- [x] Detect and respond to attacks

</details>

### Question 2: How does defensive security differ from offensive security?

<details>
<summary>Answer</summary>

- [x] Defensive security monitors and protects systems
- [x] Offensive security attacks or simulates attacks to find flaws
- [x] Defenders do not attack systems; they detect, investigate, and respond

</details>

### Question 3: What is defensive security defined as in this room?

<details>
<summary>Answer</summary>

- [x] The process of defending and securing devices and systems

</details>

### Question 4: Who is Joe in this room's scenario?

<details>
<summary>Answer</summary>

- [x] An apprentice SOC analyst on his first solo shift

</details>

### Question 5: Why do SOC analysts use monitoring dashboards?

<details>
<summary>Answer</summary>

- [x] To separate normal activity from suspicious behaviour
- [x] To see what activity is taking place on computing devices
- [x] To confirm legitimate activity and investigate what looks suspicious

</details>

### Question 6: Which source IP address generates the suspicious traffic?

<details>
<summary>Answer</summary>

- [x] 32.122.195.63

</details>

### Question 7: What three steps do you take to detect suspicious activity in the lab?

<details>
<summary>Answer</summary>

- [x] Open the monitoring dashboard
- [x] Review recent alerts
- [x] Identify the suspicious source IP

</details>

### Question 8: After spotting suspicious activity, what must Joe figure out next?

<details>
<summary>Answer</summary>

- [x] What the attacker is actually trying to do

</details>

### Question 9: Where do you look to see what the attacker is searching for on the site?

<details>
<summary>Answer</summary>

- [x] The "URL Discovery Attempts" list
- [x] Specifically the latest "URL Discovery Attempts" entry

</details>

### Question 10: What behaviour does the dashboard show about the attacker's URL attempts?

<details>
<summary>Answer</summary>

- [x] Many attempts to access hidden pages
- [x] Attempts happening very quickly

</details>

### Question 11: What is the latest URL the attacker tried to find?

<details>
<summary>Answer</summary>

- [x] https://fakebank.com/admin

</details>

### Question 12: What is the immediate priority in defensive security once you know who the attacker is and what they want?

<details>
<summary>Answer</summary>

- [x] Containment — stopping the attack while it is happening to protect the organisation

</details>

### Question 13: How do you block the attacker in the practical lab?

<details>
<summary>Answer</summary>

- [x] Add the IP 32.122.195.63 into the "Add Firewall Rule" textbox
- [x] Select BLOCK from the dropdown
- [x] Press Apply

</details>

### Question 14: What does blocking the IP address achieve?

<details>
<summary>Answer</summary>

- [x] Prevents the attacker's device from accessing our systems entirely
- [x] It is a good immediate containment step

</details>

### Question 15: Why is rate limiting effective against this attack?

<details>
<summary>Answer</summary>

- [x] The attacker was rapidly accessing many pages at once
- [x] Rate limiting limits how many connections are possible in a given time
- [x] That can reduce overload from rapid probing

</details>

### Question 16: What does updating security rules do in this context?

<details>
<summary>Answer</summary>

- [x] Tightens access controls to sensitive pages the attacker was able to slip through

</details>

### Question 17: What flag appears when the attack is successfully stopped?

<details>
<summary>Answer</summary>

- [x] THM{FAKEBANK-SECURED}

</details>

### Question 18: After containment, what should defenders still do according to the room?

<details>
<summary>Answer</summary>

- [x] Investigate the finer details
- [x] Fix any vulnerabilities that allowed the attack in the first place

</details>

## Summary

This room introduces defensive security by having you think like a defender with SOC analyst Joe. You use a monitoring dashboard to find the suspicious source IP **32.122.195.63**, identify URL discovery toward **https://fakebank.com/admin**, and contain the attack by blocking that IP with a firewall rule. Success yields the flag **THM{FAKEBANK-SECURED}**. Core idea: detect and respond—monitor, investigate, then contain before damage spreads.

## References

- [Defensive Security Intro – TryHackMe](https://tryhackme.com/room/defensivesecurityintro)

</details>

<details>
  <summary>Careers in Cyber</summary>

## Introduction

Cyber security careers are in high demand and often offer high salaries. Roles span offensive work (pentesting and reporting vulnerabilities) through defensive work (defending against and investigating attacks). This TryHackMe room explains why people enter cyber, outlines major job roles and responsibilities, and links learning paths and career guides so you can start building skills toward a target role.

## Detailed Explanation

- [x] **Why get a career in cyber**
  - **High pay** — security jobs often have high starting salaries
  - **Exciting** — work can include legally hacking systems or defending against cyber attacks
  - **Be in demand** — there are over 3.5 million unfilled cyber positions
  - The room helps you break in by covering roles and linking learning paths for skill building
- [x] **Security Analyst**
  - Responsible for maintaining the security of an organisation's data
  - Builds security measures across organisations to protect against attacks
  - Explores and evaluates company networks for actionable data and recommendations for engineers
  - Works with stakeholders to understand security requirements and the security landscape
  - Responsibilities:
    - Analyse cyber security across the company with stakeholders
    - Compile ongoing reports on network safety, issues, and responses
    - Develop security plans using research on new attack tools, trends, and cross-team measures
  - Learning Paths: Pre Security, Cyber Security 101, SOC Level 1
  - Career Guides: Becoming a Cyber Security Analyst; How to Become a Level 1 SOC Analyst; A Day in the Life of a SOC Analyst; The Ultimate SOC L1 Analyst Interview Guide; From Student to SOC Analyst: Hayden’s Success Story
- [x] **Security Engineer**
  - Designs, monitors, and maintains security controls, networks, and systems to help prevent cyberattacks
  - Develops and implements solutions using threat and vulnerability data (often from other security staff)
  - Works across web application attacks, network threats, and evolving tactics
  - Goal: retain and adopt measures that mitigate attack and data-loss risk
  - Responsibilities:
    - Test and screen security measures across software
    - Monitor networks and reports to update systems and mitigate vulnerabilities
    - Identify and implement systems needed for optimal security
  - Learning Paths: SOC Level 1, JR Penetration Tester, Offensive Pentesting
  - Career Guides: Becoming a Security Engineer; How to Become a Security Engineer; A Day in the Life of a Security Engineer; Preparing for a Security Engineering Interview; Becoming a Security Engineer: Richárd’s Success Story
- [x] **Incident Responder**
  - Identifies and mitigates attacks while an attacker’s operations are still unfolding
  - Responds productively to breaches; creates plans, policies, and protocols for during and after incidents
  - Often high-pressure: assessments and responses happen in real time as attacks unfold
  - Metrics: **MTTD** (meantime to detect), **MTTA** (meantime to acknowledge), **MTTR** (meantime to recover)
  - Aim: swift effective response, protect financial standing, avoid negative breach impact; protect data, reputation, and finances
  - Responsibilities:
    - Develop and adopt a thorough, actionable incident response plan
    - Maintain strong security best practices and support IR measures
    - Post-incident reporting and preparation for future attacks using learnings
  - Learning Path: SOC Level 1
- [x] **Digital Forensics Examiner**
  - Uses digital forensics to investigate incidents and crimes
  - Law-enforcement focus: collect and analyse evidence to help solve crimes—charge the guilty and exonerate the innocent
  - Corporate/defence focus: analyse incidents such as policy violations
  - Responsibilities:
    - Collect digital evidence while observing legal procedures
    - Analyse digital evidence to answer case-related questions
    - Document findings and report on the case
- [x] **Malware Analyst**
  - Analyses all types of malware to learn how they work and what they do
  - Studies suspicious programs, discovers behaviour, and writes reports
  - Sometimes called a reverse-engineer: convert compiled programs from machine language to readable low-level code
  - Needs a strong programming background, especially assembly and C
  - Goal: learn all activities a malicious program carries out, how to detect it, and report findings
  - Responsibilities:
    - Static analysis of malicious programs (reverse-engineering)
    - Dynamic analysis by observing samples in a controlled environment
    - Document and report all findings
- [x] **Penetration Tester**
  - Tests technology products for security loopholes; also called pentesting or ethical hacking
  - Tests security of systems and software by uncovering flaws through systemised hacking
  - Exploits vulnerabilities to evaluate risk so the company can fix issues before real attacks
  - Responsibilities:
    - Conduct tests on computer systems, networks, and web-based applications
    - Perform security assessments, audits, and analyse policies
    - Evaluate and report insights with recommended actions for attack prevention
  - Learning Paths: Jr Penetration Tester, Offensive Pentesting
  - Career Guides: Becoming a Penetration Tester; How to Become a Penetration Tester; Preparing for a Junior Penetration Tester Interview; From IT Support to Pentester: Tom’s Success Story
- [x] **Red Teamer**
  - Plays the adversary: attacks an organisation and gives feedback from an enemy’s perspective
  - Similar to pentesters but more targeted: tests detection and response, not just finding many vulns
  - Imitates cyber criminals: emulate malicious attacks, retain access, avoid detection
  - Assessments can run up to a month, typically by a team external to the company
  - Best suited to organisations with mature security programs
  - Responsibilities:
    - Emulate a threat actor to uncover exploitable vulnerabilities, maintain access, and avoid detection
    - Assess security controls, threat intelligence, and incident response procedures
    - Evaluate and report insights with actionable data to avoid real-world instances
  - Learning Paths: JR Penetration Tester, Offensive Pentesting, Red Teamer
  - Career Guides: Red Teaming: Job Roles, Salaries & Opportunities

## Terminal Commands

This room is informational and career-focused. It does not centre on specific terminal commands; later learning paths introduce hands-on labs and CLI work.

```bash
# No primary terminal commands for this careers overview room.
```

## Code

No code sections in this room; the focus is understanding cyber security job roles, responsibilities, learning paths, and career resources.

## Questions and Answers

### Question 1: Why are cyber security careers considered attractive?

<details>
<summary>Answer</summary>

- [x] High pay — jobs in security often have high starting salaries
- [x] Exciting — work can include legally hacking systems or defending against cyber attacks
- [x] Be in demand — over 3.5 million unfilled cyber positions

</details>

### Question 2: What two broad sides of cyber security work does this room contrast?

<details>
<summary>Answer</summary>

- [x] **Offensive** — pentesting (hacking machines and reporting vulnerabilities)
- [x] **Defensive** — defending against and investigating cyberattacks

</details>

### Question 3: What is a Security Analyst mainly responsible for?

<details>
<summary>Answer</summary>

- [x] Maintaining the security of an organisation’s data
- [x] Exploring and evaluating company networks
- [x] Providing actionable recommendations for preventative measures

</details>

### Question 4: Name three responsibilities of a Security Analyst.

<details>
<summary>Answer</summary>

- [x] Working with stakeholders to analyse cyber security throughout the company
- [x] Compiling ongoing reports about network safety, issues, and responses
- [x] Developing security plans based on research into new attack tools and trends

</details>

### Question 5: Which TryHackMe learning paths are suggested for a Security Analyst?

<details>
<summary>Answer</summary>

- [x] Pre Security
- [x] Cyber Security 101
- [x] SOC Level 1

</details>

### Question 6: What is the primary focus of a Security Engineer?

<details>
<summary>Answer</summary>

- [x] Design, monitor, and maintain security controls, networks, and systems to help prevent cyberattacks

</details>

### Question 7: What kinds of attacks do Security Engineers work across?

<details>
<summary>Answer</summary>

- [x] Web application attacks
- [x] Network threats
- [x] Evolving trends and tactics

</details>

### Question 8: Which learning paths are suggested for a Security Engineer?

<details>
<summary>Answer</summary>

- [x] SOC Level 1
- [x] JR Penetration Tester
- [x] Offensive Pentesting

</details>

### Question 9: What does an Incident Responder do while an attack is still unfolding?

<details>
<summary>Answer</summary>

- [x] Identifies and mitigates attacks while the attacker’s operations are still underway
- [x] Creates plans, policies, and protocols for during and after incidents
- [x] Responds under pressure in real time

</details>

### Question 10: What do MTTD, MTTA, and MTTR stand for?

<details>
<summary>Answer</summary>

- [x] **MTTD** — meantime to detect
- [x] **MTTA** — meantime to acknowledge
- [x] **MTTR** — meantime to recover

</details>

### Question 11: What is the core work of a Digital Forensics Examiner?

<details>
<summary>Answer</summary>

- [x] Using digital forensics to investigate incidents and crimes
- [x] Collecting digital evidence while observing legal procedures
- [x] Analysing evidence and documenting/reporting findings

</details>

### Question 12: How can a Digital Forensics Examiner’s context differ between law enforcement and company defence?

<details>
<summary>Answer</summary>

- [x] **Law enforcement** — collect and analyse evidence to help solve crimes (charge the guilty, exonerate the innocent)
- [x] **Company defence** — use forensic skills to analyse incidents such as policy violations

</details>

### Question 13: Why is a Malware Analyst sometimes called a reverse-engineer?

<details>
<summary>Answer</summary>

- [x] Their core task is converting compiled programs from machine language to readable code
- [x] Usually in a low-level language
- [x] They need strong programming skills, especially assembly and C

</details>

### Question 14: What are the two main analysis types a Malware Analyst performs?

<details>
<summary>Answer</summary>

- [x] **Static analysis** — reverse-engineering malicious programs
- [x] **Dynamic analysis** — observing malware activities in a controlled environment

</details>

### Question 15: What is a Penetration Tester responsible for?

<details>
<summary>Answer</summary>

- [x] Testing technology products for security loopholes
- [x] Uncovering flaws and vulnerabilities through systemised hacking
- [x] Evaluating risk and reporting insights so issues can be fixed before real attacks

</details>

### Question 16: Which learning paths are suggested for a Penetration Tester?

<details>
<summary>Answer</summary>

- [x] Jr Penetration Tester
- [x] Offensive Pentesting

</details>

### Question 17: How does a Red Teamer differ from a typical Penetration Tester?

<details>
<summary>Answer</summary>

- [x] **Penetration Tester** — uncover many vulnerabilities across systems to keep cyber-defence in good standing
- [x] **Red Teamer** — more targeted; tests the company’s detection and response capabilities
- [x] Red teamers emulate malicious attacks, retain access, and avoid detection

</details>

### Question 18: Why are Red Team assessments often best suited to organisations with mature security programs?

<details>
<summary>Answer</summary>

- [x] They test detection and response capabilities that assume monitoring and IR processes already exist
- [x] Assessments can run for up to a month and are typically run by an external team

</details>

### Question 19: Which learning paths are suggested for a Red Teamer?

<details>
<summary>Answer</summary>

- [x] JR Penetration Tester
- [x] Offensive Pentesting
- [x] Red Teamer

</details>

### Question 20: What is the overall aim of incident response metrics and practice described in the room?

<details>
<summary>Answer</summary>

- [x] Achieve a swift and effective response
- [x] Retain financial standing and avoid negative breach implications
- [x] Protect the company’s data, reputation, and financial standing from cyber attacks

</details>

## Summary

Careers in Cyber explains why security work is high-pay, exciting, and in demand (over 3.5 million unfilled roles), then surveys major roles: Security Analyst, Security Engineer, Incident Responder, Digital Forensics Examiner, Malware Analyst, Penetration Tester, and Red Teamer. For each role you get core purpose, responsibilities, and (where listed) TryHackMe learning paths and career guides to start building the right skills.

## References

- [Careers in Cyber – TryHackMe](https://tryhackme.com/room/careersincyber)

</details>

## 2-Computer Funamentals

