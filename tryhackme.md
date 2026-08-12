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

## 2-Computer Fundamentals

<details>
  <summary>Inside a Computer System</summary>

## Introduction

Before securing systems, you need to understand what you are securing. This TryHackMe room is the first in the Computer Fundamentals module and uses a castle analogy: you cannot defend a castle you have never seen. You learn the building blocks of a computer, how they connect, and what happens from power-on to a running operating system—kept at a fundamentals level without deep jargon.

**Learning objectives:** recognize and understand the functions of various computing components.

## Detailed Explanation

- [x] **Why fundamentals matter**
  - Defending without understanding components is like defending an unseen castle
  - You need the layout (where things live), who enters and how, and who can move or change “treasure”
  - After this room you should have a general idea of how components interact to serve users
- [x] **Shared building blocks**
  - Nearly every computer system includes the same core parts, each with its own job
  - The room maps PC components to a human-body analogy (skeleton/nerves, brain, short-term memory, etc.)
  - Interactive static site: identify components to earn the flag `THM{4llpccomp0n3nts1d3nt1f13d}`
- [x] **Motherboard**
  - Like the skeleton and nervous system: holds components and connects them
  - Typical desktop board: CPU socket, RAM slots, expansion slots, ports
  - Every other component plugs into or connects through the motherboard
- [x] **CPU (Central Processing Unit)**
  - Comparable to part of the brain: continuously executes instructions
  - Modern CPUs have multiple cores that handle instructions in parallel
  - Connects via the CPU socket on the motherboard
- [x] **RAM (Random Access Memory)**
  - Like short-term / working memory: holds data the CPU needs quickly
  - **Volatile** — contents are lost when power is lost
  - Modern modules use technologies such as DDR5 or DDR6 for speed
- [x] **Storage (SSD / HDD)**
  - Like long-term memory: data saved permanently (until deleted or overwritten)
  - **HDD** — older tech with moving parts; large capacity at lower cost, slower
  - **SSD** — no moving parts; memory chips; much faster
  - Connects via SATA cables or PCI Express slots
- [x] **Network Adapter**
  - Like vocal cords for communication with other systems
  - Wired and wireless variants; often embedded on the motherboard or added as expansion cards
  - Typically connects via PCI Express
- [x] **Power Supply (PSU)**
  - Like the heart pumping blood: supplies energy to all components
  - Must provide enough wattage; undersized PSU can cause failure
  - Takes outlet power and distributes it via connectors (main motherboard connector, Molex, etc.)
- [x] **Graphics Card**
  - Like the visual cortex: turns OS/program data into images for a monitor
  - Connects to PCI Express slots on the motherboard
- [x] **Input / Output**
  - Input: keyboard, microphone, mouse, scanner
  - Output: monitor, printer, speakers
  - Common connectors: USB, HDMI, DisplayPort
- [x] **Boot sequence (press Start / power button)**
  - Analogy: waking up and checking that everything works before starting the day
  - **Step 1 — Press the power button:** signal to the PSU to allow power to flow
  - **Step 2 — Firmware starts:** UEFI (Unified Extensible Firmware Interface) manages startup; BIOS does a similar job but has largely been replaced by UEFI
  - **Step 3 — Power-On Self Test (POST):** checks that required components are present, configured, and working
  - **Step 4 — Select boot device:** UEFI uses an ordered priority list of devices to find the OS boot routine
  - **Step 5 — Initiate bootloader:** bootloader loads the OS from the boot device into RAM; UEFI then hands control of components to the OS
  - Boot-exercise flag: `THM{pc5ucce55fully5t4rt3d}`
- [x] **Why this matters for cyber security**
  - Later topics often require recalling what each component does and how they interact
  - The boot process is especially important because it can be targeted by attackers
  - Next room (coming soon): Computer Types — how component combinations create different system types

## Terminal Commands

This room is conceptual and uses interactive static-site exercises in the browser (View Site). There are no primary command-line tools.

```bash
# No primary terminal commands in this computer-components and boot-sequence room.
```

## Code

No programming component; learning is through explanations, diagrams, and static-site identification exercises.

```py
# No code snippets for the Inside a Computer System room.
```

## Questions and Answers

### Question 1: Why does the room say you must understand a computer before securing it?

<details>
<summary>Answer</summary>

- [x] Trying to defend what you don't understand is like defending a castle you have never seen
- [x] You need the layout, who enters and how, and who can access or change important resources

</details>

### Question 2: What is the motherboard compared to in the human-body analogy, and what does it do?

<details>
<summary>Answer</summary>

- [x] Skeleton and nervous system
- [x] Holds components in place and connects them (CPU socket, RAM slots, expansion slots, ports)

</details>

### Question 3: What does the CPU do, and how do modern CPUs improve throughput?

<details>
<summary>Answer</summary>

- [x] Executes instructions (like part of the brain)
- [x] Multiple cores handle instructions in parallel
- [x] Connects via the CPU socket on the motherboard

</details>

### Question 4: What is RAM, and why is it called volatile?

<details>
<summary>Answer</summary>

- [x] Short-term / working memory that holds data the CPU needs quick access to
- [x] Volatile means contents are lost when power is lost
- [x] Modern modules use technologies such as DDR5 or DDR6

</details>

### Question 5: How do HDDs and SSDs differ as long-term storage?

<details>
<summary>Answer</summary>

- [x] **HDD** — moving parts; typically slower; popular for large capacity at low cost
- [x] **SSD** — no moving parts; memory chips; much faster
- [x] Both connect via SATA or PCI Express

</details>

### Question 6: What is the role of a network adapter?

<details>
<summary>Answer</summary>

- [x] Lets computers communicate with other systems (wired or wireless)
- [x] Often embedded on the motherboard or added as an expansion card
- [x] Typically connects via PCI Express

</details>

### Question 7: Why must the PSU be sized carefully for a system?

<details>
<summary>Answer</summary>

- [x] It supplies power to all components
- [x] If components need more power than the PSU can provide, the system will fail
- [x] It takes outlet power and distributes it through connectors (motherboard, Molex, etc.)

</details>

### Question 8: What does a graphics card do, and how does it usually connect?

<details>
<summary>Answer</summary>

- [x] Processes visual data from the OS and programs for output to a monitor
- [x] Comparable to the visual cortex
- [x] Connects to PCI Express slots on the motherboard

</details>

### Question 9: Give examples of input devices, output devices, and common connectors.

<details>
<summary>Answer</summary>

- [x] **Input** — keyboard, microphone, mouse, scanner
- [x] **Output** — monitor, printer, speakers
- [x] **Connectors** — USB, HDMI, DisplayPort

</details>

### Question 10: What happens in Step 1 when you press the power button?

<details>
<summary>Answer</summary>

- [x] A signal is sent to the PSU to allow power to flow to the system

</details>

### Question 11: What firmware manages component startup, and how does BIOS relate?

<details>
<summary>Answer</summary>

- [x] **UEFI** (Unified Extensible Firmware Interface) is the central system that manages startup
- [x] **BIOS** does a similar job but has mainly been replaced by UEFI

</details>

### Question 12: What is POST (Power-On Self Test)?

<details>
<summary>Answer</summary>

- [x] A UEFI routine that tests whether every required component is present
- [x] Checks that components are configured correctly and functioning

</details>

### Question 13: How does the system choose where to boot from?

<details>
<summary>Answer</summary>

- [x] UEFI holds an ordered priority list of devices
- [x] It looks first (then next) for the boot routine for the operating system

</details>

### Question 14: What does the bootloader do in the final boot step?

<details>
<summary>Answer</summary>

- [x] On the selected boot device, the bootloader is initiated
- [x] It transfers the Operating System into RAM
- [x] UEFI then gives control of the components to the OS

</details>

### Question 15: What flag do you get after identifying all PC components on the static site?

<details>
<summary>Answer</summary>

- [x] `THM{4llpccomp0n3nts1d3nt1f13d}`

</details>

### Question 16: What flag do you get after completing the boot-sequence static-site exercise?

<details>
<summary>Answer</summary>

- [x] `THM{pc5ucce55fully5t4rt3d}`

</details>

### Question 17: Why is the boot process especially relevant later in cyber security?

<details>
<summary>Answer</summary>

- [x] You will often need to recall how core components interact
- [x] The boot process is sometimes targeted by attackers

</details>

### Question 18: What learning objective does the room state after completion?

<details>
<summary>Answer</summary>

- [x] Recognize and understand the functions of various computing components

</details>

## Summary

Inside a Computer System covers the core PC building blocks—motherboard, CPU, RAM, storage (HDD/SSD), network adapter, PSU, graphics card, and I/O—using a human-body analogy, then walks through the five-step boot path from power button to UEFI/POST, boot-device selection, bootloader, and OS in RAM. Interactive static sites reinforce component ID and boot order; flags `THM{4llpccomp0n3nts1d3nt1f13d}` and `THM{pc5ucce55fully5t4rt3d}` mark completion. These fundamentals matter later because component roles and the boot process underpin many security topics.

## References

- [Inside a Computer System – TryHackMe](https://tryhackme.com/room/insideacomputer)

</details>

<details>
  <summary>Inside a Computer System</summary>

## Introduction

Sophia was connecting a new device to her home WiFi when she noticed “NexusCool Fridge X17”—her neighbor’s smart refrigerator. The moment underscored a core idea of this TryHackMe room: computers are no longer only laptops and phones; they also hide in everyday objects (appliances, doorbells, and more). Through Sophia’s summer internship story at Nova Labs, the room teaches you to identify and distinguish computers you use directly (laptops, smartphones) and indirectly (servers, IoT devices, embedded systems), and why each type fits its purpose.

**Learning objectives:** identify and distinguish types of computers used directly and indirectly, and understand what makes each suited to its purpose.

## Detailed Explanation

- [x] **Sophia’s insight — computers everywhere**
  - Smart devices (e.g. a network-connected fridge) show that “computer” is broader than screens and keyboards
  - Many systems are used indirectly—you never sit in front of them, but they still process data and act in the world
- [x] **Month 1 — computers you sit in front of (and ones you don’t)**
  - Not all computers are meant to move
  - Not all computers are meant for people to sit in front of
  - Four similar-looking types serve different purposes: laptop, desktop, workstation, server
- [x] **Laptop**
  - Screen and keyboard: yes
  - Main purpose: portable everyday computing (email, documents, general work)
  - Trade-off: small, battery-powered form factor makes sustained cooling hard; long heavy tasks can slow the machine
- [x] **Desktop**
  - Screen and keyboard: yes
  - Main purpose: sustained performance at a fixed location
  - Wall power and better cooling support longer, steadier workloads than a typical laptop
  - Designed for consistency rather than mobility
- [x] **Workstation**
  - Screen and keyboard: yes
  - Main purpose: precision and reliability for professional tasks (simulations, 3D models)
  - Looks like a desktop but uses specialized components to reduce errors during long or complex computations
- [x] **Server**
  - Screen and keyboard: usually no dedicated ones
  - Main purpose: providing services to many users over a network
  - Runs continuously, answering many requests at once; users often never touch the hardware directly
- [x] **Month 2 — computers hiding in everyday objects**
  - The most powerful computer many people own fits in a pocket
  - Millions more hide in doors, lamps, coffee machines, and similar devices
- [x] **Smartphone**
  - Pocket-sized computer optimized for battery life and connectivity
  - Examples: iPhone, Android phone
  - Currently the most popular pocket-sized computer
- [x] **Tablet**
  - Touch-first computer with a larger screen
  - Examples: iPad, drawing tablet
- [x] **IoT device**
  - Network-connected device with a single purpose
  - Examples: thermostat, smart doorbell, fitness tracker
  - Reports data or receives commands over a network
- [x] **Embedded computer**
  - Computer built into another device
  - Examples: coffee maker controller, automatic door sensor, lamp dimmer chip
  - May not connect to a network; often runs silently for years inside the host machine
- [x] **IoT vs Embedded**
  - Both can be small and single-purpose
  - Key difference is **connectivity**: IoT devices join a network; embedded computers may not connect to anything
  - Example: automatic doors use an embedded computer to detect movement and open—invisible, reliable, everywhere
- [x] **Why computers come in different flavors**
  - There is no single “best” computer that does everything well
  - Every design is a **trade-off**
  - Mobility costs power: smaller portable systems sacrifice sustained performance
  - Reliability costs money: servers and critical systems add redundancy (extra power supplies, disks)
  - Purpose shapes interaction: you touch a phone; you ask a server for information; an IoT device works quietly without demanding attention
  - Right tool for the job—not one machine for all jobs
- [x] **Interactive challenge**
  - Complete the static site (View Site) on computer types
  - Flag: `THM{8_computer_types}`

## Terminal Commands

This room is conceptual and uses an interactive static-site exercise in the browser (View Site). There are no primary command-line tools.

```bash
# No primary terminal commands in this computer-types room.
```

## Code

No programming component; learning is through the Sophia narrative, comparison tables, and the static-site challenge.

```py
# No code snippets for this computer-types room.
```

## Questions and Answers

### Question 1: What learning objective does this room emphasize?

<details>
<summary>Answer</summary>

- [x] Identify and distinguish computers you use directly (e.g. laptops, smartphones) and indirectly (e.g. servers, IoT, embedded systems)
- [x] Understand what makes each type suited to its purpose

</details>

### Question 2: What two lessons did Sophia learn in Month 1 about computers?

<details>
<summary>Answer</summary>

- [x] Not all computers are meant to move
- [x] Not all computers are meant for people to sit in front of

</details>

### Question 3: What is the main purpose of a laptop?

<details>
<summary>Answer</summary>

- [x] Portable everyday computing

</details>

### Question 4: What is the main purpose of a desktop?

<details>
<summary>Answer</summary>

- [x] Sustained performance at a fixed location

</details>

### Question 5: Which computer type usually runs without a dedicated screen and keyboard?

<details>
<summary>Answer</summary>

- [x] Server

</details>

### Question 6: What kind of computer with specialized components would one buy for precision work?

<details>
<summary>Answer</summary>

- [x] Workstation

</details>

### Question 7: How do servers typically serve users?

<details>
<summary>Answer</summary>

- [x] They provide services to many users over a network
- [x] They run continuously and answer multiple requests at once
- [x] Users often never touch the hardware directly

</details>

### Question 8: What is the currently most popular pocket-sized computer?

<details>
<summary>Answer</summary>

- [x] Smartphone

</details>

### Question 9: What kind of computer would you expect to find in a coffee machine?

<details>
<summary>Answer</summary>

- [x] Embedded computer

</details>

### Question 10: How do a smartphone and a tablet differ in the room’s framing?

<details>
<summary>Answer</summary>

- [x] **Smartphone** — pocket-sized; optimized for battery life and connectivity
- [x] **Tablet** — touch-first computer with a larger screen

</details>

### Question 11: What is an IoT device, and what are examples?

<details>
<summary>Answer</summary>

- [x] A network-connected device with a single purpose
- [x] Examples: thermostat, smart doorbell, fitness tracker

</details>

### Question 12: What is an embedded computer, and what are examples?

<details>
<summary>Answer</summary>

- [x] A computer built into another device
- [x] Examples: coffee maker controller, automatic door sensor, lamp dimmer chip

</details>

### Question 13: What is the key difference between IoT and embedded computers?

<details>
<summary>Answer</summary>

- [x] **Connectivity** — IoT devices connect to a network to report data or receive commands
- [x] Embedded computers might not connect to anything; they do their job inside the machine

</details>

### Question 14: Why not build one computer that does everything?

<details>
<summary>Answer</summary>

- [x] Every design is a trade-off
- [x] Mobility costs power (portable systems sacrifice sustained performance)
- [x] Reliability costs money (redundancy such as extra power supplies and disks)
- [x] Purpose shapes how you interact with each type

</details>

### Question 15: What eight computer types does the room cover?

<details>
<summary>Answer</summary>

- [x] Laptop
- [x] Desktop
- [x] Workstation
- [x] Server
- [x] Smartphone
- [x] Tablet
- [x] IoT device
- [x] Embedded computer

</details>

### Question 16: What flag do you get from the computer-types static site?

<details>
<summary>Answer</summary>

- [x] `THM{8_computer_types}`

</details>

### Question 17: According to Sophia’s final report, what misconception did she leave behind?

<details>
<summary>Answer</summary>

- [x] She arrived thinking computers had screens and keyboards
- [x] She left knowing computers are everywhere—especially where you do not see them

</details>

### Question 18: Why are “silent” computers often among the most critical?

<details>
<summary>Answer</summary>

- [x] The most critical computers are not always the fastest or flashiest
- [x] Silent chips keep doors opening, planes flying, and coffee machines brewing

</details>

## Summary

Through Sophia’s Nova Labs internship, this room maps eight computer types—laptop, desktop, workstation, server, smartphone, tablet, IoT device, and embedded computer—and shows why purpose and trade-offs (mobility vs power, reliability vs cost, connectivity vs isolation) drive design. Interactive static-site completion yields `THM{8_computer_types}`. The takeaway: there is no best computer, only the right tool for the job—and many of the most important systems are the ones you never see.

## References

- [Inside a Computer System – TryHackMe](https://tryhackme.com/room/insideacomputer)

</details>
