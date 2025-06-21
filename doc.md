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
  -l: Long listing format (shows details like permissions, owner, size, modification date)
  -r: Reverse order while sorting
  -t: Sort by modification time, newest files first
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

<details>
<summary>Linux Fundamentals Part 2 - touch (Create file) </summary>

  ```
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  unknown1

  tryhackme@linux2:~$ touch note.txt
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  note.txt  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - mkdir (Create a folder) </summary>

  ```
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  note.txt  unknown1

  tryhackme@linux2:~$ mkdir mydirectory
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - cp (Copy a file or folder) </summary>

  ```
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  unknown1

  tryhackme@linux2:~$ cp note.txt note2.txt
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  note2.txt  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - mv (Move a file or folder) </summary>

  ```
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  note2.txt  unknown1

  tryhackme@linux2:~$ mv note2.txt mydirectory/note2.txt
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  unknown1
  tryhackme@linux2:~$ ls mydirectory/
  note2.txt
  ```

  ```
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  unknown1

  tryhackme@linux2:~$ mv note.txt note_updated.txt
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note_updated.txt  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - rm (Remove a file or folder) </summary>

  ```
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note_updated.txt  unknown1

  tryhackme@linux2:~$ rm note_updated.txt 
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  unknown1
  ```

  ```
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  unknown1

  tryhackme@linux2:~$ rm -R mydirectory/
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - file (Determine the type of a file) </summary>

  ```
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  unknown1

  tryhackme@linux2:~$ file myfile 
  myfile: ASCII text
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - su (Switch between Users) </summary>

  ```
  tryhackme@linux2:~$ su -l user2
  Password: 
  user2@linux2:~$

  user2@linux2:~$ su tryhackme
  Password:
  tryhackme@linux2:/home/user2$
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - etc (etcetera folder) </summary>

  ```
  tryhackme@linux2:~$ cd /etc
  tryhackme@linux2:/etc$ ls
  
  ModemManager                   console-setup         fuse.conf            issue.net        mailcap                 pam.d                    rpc           timezone
  NetworkManager                 cron.d                fwupd                kernel           mailcap.order           passwd                   rsyslog.conf  tmpfiles.d
  PackageKit                     cron.daily            gai.conf             kernel-img.conf  manpath.config          passwd-                  rsyslog.d     ubuntu-advantage
  X11                            cron.hourly           groff                landscape        mdadm                   perl                     screenrc      ucf.conf
  acpi                           cron.monthly          group                ld.so.cache      mime.types              pki                      security      udev
  adduser.conf                   cron.weekly           group-               ld.so.conf       mke2fs.conf             pm                       selinux       udisks2
  alternatives                   crontab               grub.d               ld.so.conf.d     modprobe.d              polkit-1                 services      ufw
  apache2                        cryptsetup-initramfs  gshadow              ldap             modules                 pollinate                shadow        update-manager
  apparmor                       crypttab              gshadow-             legal            modules-load.d          popularity-contest.conf  shadow-       update-motd.d
  apparmor.d                     dbus-1                gss                  libaudit.conf    mtab                    profile                  shells        update-notifier
  apport                         dconf                 hdparm.conf          libblockdev      multipath               profile.d                skel          usb_modeswitch.conf
  apt                            debconf.conf          hibagent-config.cfg  locale.alias     multipath.conf          protocols                sos           usb_modeswitch.d
  at.deny                        debian_version        hibinit-config.cfg   locale.gen       nanorc                  python3                  ssh           vim
  bash.bashrc                    default               host.conf            localtime        netplan                 python3.8                ssl           vmware-tools
  bash_completion                deluser.conf          hostname             logcheck         network                 rc0.d                    subgid        vtrgb
  bash_completion.d              depmod.d              hosts                login.defs       networkd-dispatcher     rc1.d                    subgid-       wgetrc
  bindresvport.blacklist         dhcp                  hosts.allow          logrotate.conf   networks                rc2.d                    subuid        xattr.conf
  binfmt.d                       dpkg                  hosts.deny           logrotate.d      newt                    rc3.d                    subuid-       xdg
  byobu                          e2scrub.conf          init.d               lsb-release      nsswitch.conf           rc4.d                    sudoers       zsh_command_not_found
  ca-certificates                ec2_version           initramfs-tools      ltrace.conf      opt                     rc5.d                    sudoers.d
  ca-certificates.conf           environment           inputrc              lvm              os-release              rc6.d                    sysctl.conf
  ca-certificates.conf.dpkg-old  ethertypes            iproute2             machine-id       overlayroot.conf        rcS.d                    sysctl.d
  calendar                       fonts                 iscsi                magic            overlayroot.local.conf  resolv.conf              systemd
  cloud                          fstab                 issue                magic.mime       pam.conf                rmt                      terminfo

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
















