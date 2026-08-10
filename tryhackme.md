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
