## Pre-Security (TRY-HACK-ME)

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
<details>
<summary>Linux Fundamentals Part 1 - Echo </summary>

  ```
  tryhackme@linux1:~$ echo "Hello World"
  ```

  ```
  Hello World
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - Whoami </summary>

  ```
  tryhackme@linux1:~$ whoami
  ```

  ```
  tryhackme
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - Ls </summary>

  ```
  tryhackme@linux1:~$ ls
  ```

  ```html
  access.log  folder1  folder2  folder3  folder4
  ```

  ```
  tryhackme@linux1:~$ ls -lrt
  ```

  ```bsh
  drwxr-xr-x 2 tryhackme tryhackme  4096 May 10  2021 folder1
  drwxr-xr-x 2 tryhackme tryhackme  4096 May 10  2021 folder2
  drwxr-xr-x 2 tryhackme tryhackme  4096 May 10  2021 folder3
  drwxr-xr-x 2 tryhackme tryhackme  4096 May 10  2021 folder4
  -rw-rw-r-- 1 tryhackme tryhackme 65522 May 10  2021 access.log
  ```

  ```
  tryhackme@linux1:~$ ls folder4
  ```

  ```txt
  note.txt
  ```

</details>










## Cyber Security 101 (TRY-HACK-ME)

<details>
<summary>D </summary>

  ```

  ```

  ```

  ```

</details>
















