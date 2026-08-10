<!-- Paste the TryHackMe/Let's Defend page URL at the top -->
<!-- Then paste your raw notes, explanations, commands, and code below -->

https://tryhackme.com/room/defensivesecurityintro

# Defensive Security Intro

YouTube Video: None

## Think like a Defender

Think like a Defender depicting a person sitting at a desk, with multiple monitors stacked on one another showing various cybersecurity and data iconograhpy such as a map, bar charts, etc.

Defensive security is the process of defending and securing devices and systems.

Before you can defend a system, you need to understand what defenders are responsible for. Defensive security focuses on detecting and investigating attacks, and responding before damage occurs.

Unlike offensive security, you do not attack systems, instead, you monitor and protect them.

Answer the questions below
What is the main goal of defensive security?

Detect and respond to attacks
Attack systems to find flaws
ANS: Detect and respond to attacks

# Detect Suspicious Activity

Detect Suspicious Activity
Joe is an apprentice SOC analyst on his first solo shift. A moment ago, his monitoring dashboard lit up - something doesn't look right. Real SOC analysts rely on tools like this every day to separate normal activity from suspicious behaviour, and right now Joe needs your help to investigate before it becomes a serious incident.

View Site
This room uses a lab machine to simulate a real system.
Character

You'll need to...

1. Open the monitoring dashboard
2. Review recent alerts
3. Identify the suspicious source IP.
   Why you're doing this
   Monitoring tools such as the one you'll be using provide insights as to what activity is taking place on computing devices. Defenders use tools like this dashboard to make sure that all activity taking place on these systems is legitimate, and investigate activity that is suspicious.

Answer the questions below
Which source IP address is generating the suspicious traffic?
32.122.195.63

# Identify the Attack

Identify the Attack
Joe has spotted the suspicious activity, but knowing something is wrong is only half the battle. He now needs to figure out what the attacker is actually trying to do. The monitoring dashboard has been tracking every move, and the answers are in there.

Help Joe dig into the data and work out what kind of attack is underway before the attacker finds what they're looking for.

View Site
Character

You'll need to...

1. Investigate the attack that has occured.
2. View the "URL Discovery Attempts" list.
3. Look at the latest "URL Discovery Attempts" entry to answer the question.
   Why you're doing this
   The monitoring dashboard shows a history of what the attacker is trying to find on our website. You will see that the dashboard has captured the attacker trying many attempts to access hidden pages, very quickly.

Once we know what the attacker is trying to achieve, we can then begin to take measures to stop the attacker and then finally fix the problem that allowed this attack in the first place.

Answer the questions below
Copy the latest URL that the attacker has tried to find and paste it below.

https://fakebank.com/admin

# Stop the Attack

Stop the Attack
Joe knows who the attacker is and what they're trying to do. Now it's time to act. In defensive security, the immediate priority is containment (stopping the attack while it's happening) to protect the organisation.

For this stage of the practical, Joe has already completed some security updates, but needs your help to complete the last.

View Site
Character

You'll need to...

1. Review the security actions. Joe has done two of these for you.
2. Block the attacker's IP address below by adding it into the "Add Firewall Rule" textbox on the practical.
   32.122.195.63

3. Make sure to select "BLOCK" from the dropdown and press "Apply".
   Why you're doing this
   Now that we know who the attacker is and what they're attempting, we can stop them. The immediate priority in defensive security is containment to protect the organisation. We can investigate the finer details and fix any vulnerabilities after.

This monitoring tool lets you implement several measures to stop the attacker:

Blocking the IP address: Prevents the attacker's device from accessing our systems entirely. A good immediate step.
Applying Rate Limiting: Limits the number of connections possible in a given time for everyone. Effective here because the attacker was rapidly accessing many pages at once, potentially overwhelming our systems.
Updating Security Rules: Tightens access controls to sensitive pages that the attacker was able to slip through.
Answer the questions below
When the success message appears, copy the flag and paste it below.

THM{FAKEBANK-SECURED}
