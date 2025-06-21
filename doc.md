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
  $ nslookup --type=CNAME shop.website.thm

  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  shop.website.thm canonical name = shops.myshopify.com
  ```

</details>
<details>
<summary>DNS in Detail - TXT record of website.thm </summary>

  ```
  $ nslookup --type=TXT website.thm

  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  website.thm text = "THM{7012BBA60997F35A9516C2E16D2944FF}"
  ```

</details>
<details>
<summary>DNS in Detail - numerical priority value for the MX record </summary>

  ```
  $ nslookup --type=MX website.thm

  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  website.thm mail exchanger = 30 alt4.aspmx.l.google.com
  ```

</details>
<details>
<summary>DNS in Detail - IP address for the A record of www.website.thm </summary>

  ```
  $ nslookup --type=A website.thm

  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  Name: website.thm
  Address: 10.10.10.10
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - echo </summary>

  ```
  tryhackme@linux1:~$ echo "Hello World"

  Hello World
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - whoami (check username) </summary>

  ```
  tryhackme@linux1:~$ whoami

  tryhackme
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - ls (list files) </summary>

  ```
  tryhackme@linux1:~$ ls

  access.log  folder1  folder2  folder3  folder4
  ```

  ```
  tryhackme@linux1:~$ ls folder4

  note.txt
  ```

  ```
  tryhackme@linux2:~$ ls -a

  .   .bash_logout  .cache    important  myfolder
  ..  .bashrc       .profile  myfile     unknown1
  ```

  ```
  tryhackme@linux2:~$ ls -l
  
  total 16
  -rw-r--r-- 1 user2     user2       14 May  5  2021 important
  -rw-r--r-- 1 tryhackme tryhackme   16 May  5  2021 myfile
  drwxr-xr-x 2 tryhackme tryhackme 4096 May  4  2021 myfolder
  -rw-r--r-- 1 tryhackme tryhackme   17 May  4  2021 unknown1
  ```

  ```
  tryhackme@linux2:~$ ls -lrt
  
  total 16
  -rw-r--r-- 1 tryhackme tryhackme   17 May  4  2021 unknown1
  drwxr-xr-x 2 tryhackme tryhackme 4096 May  4  2021 myfolder
  -rw-r--r-- 1 user2     user2       14 May  5  2021 important
  -rw-r--r-- 1 tryhackme tryhackme   16 May  5  2021 myfile
  ```

  ```
  tryhackme@linux2:~$ ls -la
  
  total 40
  drwxr-xr-x 4 tryhackme tryhackme 4096 Jun 21 14:48 .
  drwxr-xr-x 5 root      root      4096 May  4  2021 ..
  -rw-r--r-- 1 tryhackme tryhackme  220 May  4  2021 .bash_logout
  -rw-r--r-- 1 tryhackme tryhackme 3771 May  4  2021 .bashrc
  drwx------ 2 tryhackme tryhackme 4096 Jun 21 14:48 .cache
  -rw-r--r-- 1 tryhackme tryhackme  807 May  4  2021 .profile
  -rw-r--r-- 1 user2     user2       14 May  5  2021 important
  -rw-r--r-- 1 tryhackme tryhackme   16 May  5  2021 myfile
  drwxr-xr-x 2 tryhackme tryhackme 4096 May  4  2021 myfolder
  -rw-r--r-- 1 tryhackme tryhackme   17 May  4  2021 unknown1
  ```

  ```
  tryhackme@linux2:~$ ls -lart

  total 40
  -rw-r--r-- 1 tryhackme tryhackme  807 May  4  2021 .profile
  -rw-r--r-- 1 tryhackme tryhackme 3771 May  4  2021 .bashrc
  -rw-r--r-- 1 tryhackme tryhackme  220 May  4  2021 .bash_logout
  -rw-r--r-- 1 tryhackme tryhackme   17 May  4  2021 unknown1
  drwxr-xr-x 2 tryhackme tryhackme 4096 May  4  2021 myfolder
  drwxr-xr-x 5 root      root      4096 May  4  2021 ..
  -rw-r--r-- 1 user2     user2       14 May  5  2021 important
  -rw-r--r-- 1 tryhackme tryhackme   16 May  5  2021 myfile
  drwx------ 2 tryhackme tryhackme 4096 Jun 21 14:48 .cache
  drwxr-xr-x 4 tryhackme tryhackme 4096 Jun 21 14:48 .
  ```

  ```
  ls --help
  man ls
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - cd (change directory) </summary>

  ```
  tryhackme@linux1:~$ ls
  access.log  folder1  folder2  folder3  folder4

  tryhackme@linux1:~$ cd folder4
  tryhackme@linux1:~/folder4$ ls
  note.txt
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - cat (show file data) </summary>

  ```
  tryhackme@linux1:~/folder4$ ls
  note.txt
  tryhackme@linux1:~/folder4$ cat note.txt 
  Hello World!

  tryhackme@linux1:~$ ls
  access.log  folder1  folder2  folder3  folder4
  tryhackme@linux1:~$ cat folder4/note.txt
  Hello World!
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - pwd (print working directory) </summary>

  ```
  tryhackme@linux1:~$ ls
  access.log  folder1  folder2  folder3  folder4

  tryhackme@linux1:~$ cd folder4
  tryhackme@linux1:~/folder4$ pwd
  /home/tryhackme/folder4
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - find (find file) </summary>

  ```
  tryhackme@linux1:~$ ls
  access.log  folder1  folder2  folder3  folder4

  tryhackme@linux1:~$ find -name note.txt
  ./folder4/note.txt
  tryhackme@linux1:~$ find -name *.txt
  ./folder4/note.txt
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - wc (line entries) </summary>

  ```
  tryhackme@linux1:~$ cd folder4
  tryhackme@linux1:~/folder4$ ls
  note.txt

  tryhackme@linux1:~/folder4$ cat note.txt 
  Hello World!
  tryhackme@linux1:~/folder4$ wc -l note.txt 
  1 note.txt
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - {echo >>} (Append contents to file) </summary>

  ```
  tryhackme@linux1:~/folder4$ ls
  note.txt

  tryhackme@linux1:~/folder4$ cat note.txt 
  Hello World!

  tryhackme@linux1:~/folder4$ echo '81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET / HTTP/1.1" 200' >> note.txt 
  tryhackme@linux1:~/folder4$ cat note.txt 
  Hello World!
  81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET / HTTP/1.1" 200

  tryhackme@linux1:~/folder4$ wc -l note.txt 
  2 note.txt
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - grep (search for contents in file) </summary>

  ```
  tryhackme@linux1:~/folder4$ ls
  note.txt

  tryhackme@linux1:~/folder4$ cat note.txt 
  Hello World!
  81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET / HTTP/1.1" 200

  tryhackme@linux1:~/folder4$ grep "81.143.211.90" note.txt 
  81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET / HTTP/1.1" 200
  ```

</details>


<details>
<summary>Linux Fundamentals Part 2 - ssh (login using Secure Shell) </summary>

  ```
  ssh tryhackme@10.10.185.226
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
















