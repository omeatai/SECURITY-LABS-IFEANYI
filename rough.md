<!-- Paste the TryHackMe/Let's Defend page URL at the top -->
<!-- Then paste your raw notes, explanations, commands, and code below -->

https://tryhackme.com/room/offensivesecurityintro

# Offensive Security Intro

YouTube Video: None

## Think like a Hacker

Offensive Security is about thinking like an attacker to find weaknesses before real hackers do.

In this room, you'll hack your first website in a safe and legal environment to see how ethical hackers operate.

Answer the questions below
Which term describes simulating a hacker's actions to find weaknesses?

Offensive Security
Defensive Security

ANS: Offensive Security

## Starting the Lab

This room uses a virtual desktop to simulate a real system. A browser will automatically open, displaying FakeBank, a fake banking application. This is what you will be targeting.

View Site
Answer the questions below
What is the bank account number in the FakeBank application?

ANS: 8881

## Find Hidden Pages

Goal
Find a weakness in the FakeBank application. One common mistake is leaving hidden pages accessible.

View Site
Open the Terminal
Open the terminal on the machine. You will be using this to run your first hacking tool, dirbuster. The terminal icon looks like this:

Finding Hidden Pages
To find hidden pages using Dirbuster, we will use dirb and the URL that we wish to search:

dirb http://fakebank.thm
Any lines from the output that start with + are pages that have been found. Dirb will find two URLs.

Answer the questions below
Dirb found one URL, http://fakebank.thm/images.
What is the other hidden URL?

ANS: http://fakebank.thm/bank-transfer

## Attack the Admin Page

You should now have found a hidden admin panel that lets you add money to your account.

View Site
To open this URL in the browser of the simulated desktop:

Add the following:
/bank-transfer
to the URL in the browser.

Use your account number 8881 and deposit $2000 (or more). After depositing, return to your account page and confirm the balance is now positive.

Answer the questions below
When your balance turns positive, a pop-up with green text appears.

Enter the green words as the answer (ALL CAPS)

ANS: BANK-HACKED
