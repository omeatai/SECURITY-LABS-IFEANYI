## Pre-Security (TRY-HACK-ME)

<details>
<summary>Offensive Security Intro - Using Gobuster To Find Hidden Website Pages</summary>

  ```sh
  gobuster -u http://fakebank.thm -w wordlist.txt dir
  ```
  - [ ] -u is used to state the website we're scanning
  - [ ] -w takes a list of words to iterate through to find hidden pages.

</details>

<details>
<summary>DNS in Detail -  CNAME, TXT, Numerical priority value, IP address for the A record  </summary>

  #### CNAME of shop.website.thm

  ```sh
  $ nslookup --type=CNAME shop.website.thm

  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  shop.website.thm canonical name = shops.myshopify.com
  ```

  #### TXT record of website.thm

  ```sh
  $ nslookup --type=TXT website.thm

  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  website.thm text = "THM{7012BBA60997F35A9516C2E16D2944FF}"
  ```

  #### Numerical priority value for the MX record

  ```sh
  $ nslookup --type=MX website.thm

  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  website.thm mail exchanger = 30 alt4.aspmx.l.google.com
  ```

  #### IP address for the A record of www.website.thm

  ```sh
  $ nslookup --type=A website.thm

  Server: 127.0.0.53
  Address: 127.0.0.53#53
  
  Non-authoritative answer:
  Name: website.thm
  Address: 10.10.10.10
  ```

</details>

<details>
<summary>Linux Fundamentals Part 1 - echo, whoami </summary>

  #### echo
  
  ```sh
  tryhackme@linux1:~$ echo "Hello World"

  Hello World
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - whoami (check username) </summary>

  ```sh
  tryhackme@linux1:~$ whoami

  tryhackme
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - ls (list files) </summary>

  ```sh
  tryhackme@linux1:~$ ls

  access.log  folder1  folder2  folder3  folder4
  ```

  ```sh
  tryhackme@linux1:~$ ls folder4

  note.txt
  ```

  ```sh
  tryhackme@linux2:~$ ls -a

  .   .bash_logout  .cache    important  myfolder
  ..  .bashrc       .profile  myfile     unknown1
  ```

  ```sh
  tryhackme@linux2:~$ ls -l
  
  total 16
  -rw-r--r-- 1 user2     user2       14 May  5  2021 important
  -rw-r--r-- 1 tryhackme tryhackme   16 May  5  2021 myfile
  drwxr-xr-x 2 tryhackme tryhackme 4096 May  4  2021 myfolder
  -rw-r--r-- 1 tryhackme tryhackme   17 May  4  2021 unknown1
  ```

  ```sh
  tryhackme@linux2:~$ ls -lrt
  
  total 16
  -rw-r--r-- 1 tryhackme tryhackme   17 May  4  2021 unknown1
  drwxr-xr-x 2 tryhackme tryhackme 4096 May  4  2021 myfolder
  -rw-r--r-- 1 user2     user2       14 May  5  2021 important
  -rw-r--r-- 1 tryhackme tryhackme   16 May  5  2021 myfile
  ```

  ```sh
  -l: Long listing format (shows details like permissions, owner, size, modification date)
  -r: Reverse order while sorting
  -t: Sort by modification time, newest files first
  ```

  ```sh
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

  ```sh
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

  ```sh
  ls --help
  man ls
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - cd (change directory) </summary>

  ```sh
  tryhackme@linux1:~$ ls
  access.log  folder1  folder2  folder3  folder4

  tryhackme@linux1:~$ cd folder4
  tryhackme@linux1:~/folder4$ ls
  note.txt
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - cat (show file data) </summary>

  ```sh
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

  ```sh
  tryhackme@linux1:~$ ls
  access.log  folder1  folder2  folder3  folder4

  tryhackme@linux1:~$ cd folder4
  tryhackme@linux1:~/folder4$ pwd
  /home/tryhackme/folder4
  ```

</details>
<details>
<summary>Linux Fundamentals Part 1 - find (find file) </summary>

  ```sh
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

  ```sh
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

  ```sh
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

  ```sh
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

  ```sh
  ssh tryhackme@10.10.185.226
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - touch (Create file) </summary>

  ```sh
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  unknown1

  tryhackme@linux2:~$ touch note.txt
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  note.txt  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - mkdir (Create a folder) </summary>

  ```sh
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  note.txt  unknown1

  tryhackme@linux2:~$ mkdir mydirectory
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - cp (Copy a file or folder) </summary>

  ```sh
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  unknown1

  tryhackme@linux2:~$ cp note.txt note2.txt
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  note2.txt  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - mv (Move a file or folder) </summary>

  ```sh
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  note2.txt  unknown1

  tryhackme@linux2:~$ mv note2.txt mydirectory/note2.txt
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  unknown1
  tryhackme@linux2:~$ ls mydirectory/
  note2.txt
  ```

  ```sh
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note.txt  unknown1

  tryhackme@linux2:~$ mv note.txt note_updated.txt
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note_updated.txt  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - rm (Remove a file or folder) </summary>

  ```sh
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  note_updated.txt  unknown1

  tryhackme@linux2:~$ rm note_updated.txt 
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  unknown1
  ```

  ```sh
  tryhackme@linux2:~$ ls
  important  mydirectory  myfile  myfolder  unknown1

  tryhackme@linux2:~$ rm -R mydirectory/
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  unknown1
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - file (Determine the type of a file) </summary>

  ```sh
  tryhackme@linux2:~$ ls
  important  myfile  myfolder  unknown1

  tryhackme@linux2:~$ file myfile 
  myfile: ASCII text
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - su (Switch between Users) </summary>

  ```sh
  tryhackme@linux2:~$ su -l user2
  Password: 
  user2@linux2:~$

  user2@linux2:~$ su tryhackme
  Password:
  tryhackme@linux2:/home/user2$
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - etc (etcetera folder - system files) </summary>

  ```sh
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

<details>
<summary>Linux Fundamentals Part 2 - /var (variable folder - Application data) </summary>

  ```sh
  tryhackme@linux2:/etc$ cd .. && cd /var

  tryhackme@linux2:/var$ ls
  backups  cache  crash  lib  local  lock  log  mail  opt  run  snap  spool  tmp  www

  tryhackme@linux2:/var$ ls  log/
  alternatives.log       apache2     auth.log.2.gz          cloud-init.log  dmesg.1.gz  dpkg.log       kern.log       lastlog   syslog.2.gz           wtmp
  alternatives.log.1     apt         btmp                   dist-upgrade    dmesg.2.gz  dpkg.log.1     kern.log.1     private   syslog.3.gz
  alternatives.log.2.gz  auth.log    btmp.1                 dmesg           dmesg.3.gz  dpkg.log.2.gz  kern.log.2.gz  syslog    ubuntu-advantage.log
  amazon                 auth.log.1  cloud-init-output.log  dmesg.0         dmesg.4.gz  journal        landscape      syslog.1  unattended-upgrades
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - /root (root folder - home directory for the "root" user) </summary>

  ```sh
  root@linux2:~# ls
  myfile myfolder passwords.xlsx
  ```

</details>

<details>
<summary>Linux Fundamentals Part 2 - /tmp (temporary folder - ram temporary data) </summary>

  ```sh
  tryhackme@linux2:/$ cd /tmp

  tryhackme@linux2:/tmp$ ls
  snap-private-tmp                                                              systemd-private-0886ccb76384493bbc69c4ba48766cb4-systemd-logind.service-wXpcmh
  systemd-private-0886ccb76384493bbc69c4ba48766cb4-ModemManager.service-1pxeJh  systemd-private-0886ccb76384493bbc69c4ba48766cb4-systemd-resolved.service-zp0jOi
  systemd-private-0886ccb76384493bbc69c4ba48766cb4-apache2.service-BDYx8f       systemd-private-0886ccb76384493bbc69c4ba48766cb4-systemd-timesyncd.service-c83qlg
  ```

</details>

<details>
<summary>Linux Fundamentals Part 3 - wget (Download Files from linux HTTP Servers) </summary>

  ```sh
  wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt
  ```

</details>

<details>
<summary>Linux Fundamentals Part 3 - SCP/SSH (Transfer Files Remotely) </summary>

  ## let's copy an example file from our machine to a remote machine

  ```sh
  scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
  ```

  - [ ] The IP address of the remote system = 192.168.1.30
  - [ ] User on the remote system	= ubuntu
  - [ ] Name of the file on the local system = important.txt
  - [ ] Name that we wish to store the file as on the remote system =	transferred.txt

  ## let's copy a file from a remote computer to our local machine 

  ```sh
  scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt 
  ```

  - [ ] The IP address of the remote system = 192.168.1.30
  - [ ] User on the remote system	= ubuntu
  - [ ] Name of the file on the remote system = documents.txt
  - [ ] Name that we wish to store the file as on our system =	notes.txt

</details>

<details>
<summary>Linux Fundamentals Part 3 - HTTPServer with wget </summary>

  ## Using Python to start a web server

  ```sh
  tryhackme@linux3:~$ ls
  task3

  tryhackme@linux3:~$ python3 -m http.server
  Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
  10.10.176.37 - - [22/Jun/2025 13:38:23] "GET /task3 HTTP/1.1" 200 -
  ```

  ## Downloading a file from our webserver using wget

  ```sh
  root@ip-10-10-176-37:~# ls
  burp.json   Desktop    Instructions  Postman  Scripts  thinclient_drives
  CTFBuilder  Downloads  Pictures      Rooms    snap     Tools

  root@ip-10-10-176-37:~# wget http://10.10.58.204:8000/task3
  --2025-06-22 14:38:25--  http://10.10.58.204:8000/task3
  Connecting to 10.10.58.204:8000... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 18 [application/octet-stream]
  Saving to: \u2018task3\u2019
  
  task3               100%[===================>]      18  --.-KB/s    in 0s      
  
  2025-06-22 14:38:25 (118 KB/s) - \u2018task3\u2019 saved [18/18]
  ```  

</details>

<details>
<summary>Linux Fundamentals Part 3 - Processes </summary>

  ## ps

  - [ ] What it does: Shows your processes (by default, only those associated with the current terminal/session).
  - [ ] Limited view: If you just run ps alone, it won’t show background daemons or other users’ processes.

  ```sh
  tryhackme@linux3:~$ ps

  PID TTY       TIME CMD
  3540 pts/0    00:00:00 bash
  3571 pts/0    00:00:00 ps
  ```

  ## ps aux

  - [ ] What it does: Shows all running processes on the system, regardless of who owns them or their terminal association.
  - [ ] Comprehensive: Includes system daemons, root processes, and background tasks.
  - [ ] Detailed info: Gives memory and CPU usage, user, PID, start time, command, and more.
  - [ ] Breakdown of ps aux:
    - [ ] a – Show processes for all users
    - [ ] u – Display process owner/user
    - [ ] x – Include processes not attached to a terminal

  ```sh
  ps aux

  USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
  root         1  0.0  0.1 225200  9056 ?        Ss   Jun22   0:03 /sbin/init
  yourname  5678  0.2  1.3 300000 50000 pts/0    Sl   20:20   0:05 firefox
  ```

  ## Top

  - [ ] Top gives real-time statistics about the processes running on your system
  - [ ] What it does: Displays a real-time, dynamic list of processes sorted by CPU usage (by default).
  - [ ] Use case: Monitor system performance, view resource usage, find processes to kill or investigate.
  - [ ] Interactive: You can sort, search, and kill processes directly from the top interface.
  - [ ] While inside top:
    - [ ] Press k to kill a process (it will ask for a PID).
    - [ ] Press q to quit.
    - [ ] Press P to sort by CPU usage, M by memory.

  ```sh
  top
  ```

  ## kill & pkill

  - [ ] Syntax: kill [signal] PID

  ```sh
  ps aux | grep firefox  # Find PID of Firefox
  kill -9 12345          # Force-kill the Firefox process with PID 12345
  ```

  - [ ] Syntax: pkill [options] pattern

  ```sh
  pkill firefox                   # Terminates all processes with the name 'firefox'
  pkill -f "python my_script.py"  # Match full command line
  pkill -u username processname   # Killing specific users' processes
  ```

  ## fg

  - [ ] What it does: Brings a background job to the foreground in the terminal.
  - [ ] Use case: Resume a paused or backgrounded process (like after pressing Ctrl+Z or running a job with &).
  - [ ] Works only in the current shell session.

  ```sh
  fg

  sleep 60 &
  jobs           # Show background jobs
  fg %1          # Brings job number 1 to the foreground
  
  python my_script.py
  ^Z             # Ctrl+Z to suspend the process
  bg             # Resume it in the background
  fg             # Bring it back to foreground
  ```

  # systemctl

  - [ ] systemctl is the main command-line tool used to manage system services on Linux systems that use systemd (which most modern Linux distributions do, like Ubuntu, Fedora, CentOS, Debian, etc.).
  - [ ] It interacts with the systemd init system and service manager, allowing you to:
    - [ ] Start, stop, enable, or disable services
    - [ ] Check service status
    - [ ] Reboot or shut down the system
    - [ ] Analyze boot performance
    - [ ] List running services and units

  ```sh
  sudo systemctl status nginx	  = Check the status of the nginx service
  sudo systemctl start nginx	  = Start the service now
  sudo systemctl stop nginx	    = Stop the service
  sudo systemctl restart nginx	= Restart the service
  sudo systemctl enable nginx	  = Enable service to start at boot
  sudo systemctl disable nginx	= Prevent service from starting at boot
  sudo systemctl is-enabled nginx	= Check if it's set to start on boot
  sudo systemctl is-active nginx	= Check if it’s currently running
  sudo systemctl list-units --type=service = Show all active services
  sudo systemctl daemon-reload	= Reload service files after editing systemd units
  sudo systemctl reboot	  = Reboot the system
  sudo systemctl poweroff	= Power down the system
  sudo systemctl suspend	= Suspend (sleep) mode
  sudo systemctl list-timers	= Show all active timers (scheduled tasks)
  ```

</details>

<details>
<summary>Linux Fundamentals Part 3 - Cron Jobs </summary>

  - [ ] To open & edit crontab:
        
  ```sh
  crontab -e
  ```
  
  - [ ] A crontab is simply a special file with formatting that is recognised by the cron process to execute each line step-by-step.
  - [ ] Crontabs require 6 specific values:
    - [ ] MIN	  = What minute to execute at
    - [ ] HOUR	= What hour to execute at
    - [ ] DOM	  = What day of the month to execute at
    - [ ] MON	  = What month of the year to execute at
    - [ ] DOW	  = What day of the week to execute at
    - [ ] CMD	  = The actual command that will be executed.

  ```sh
  [MIN] [HOUR] [DOM] [MON] [DOW] {CMD....}
  ```

  ```sh
  0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
  ```

  ## Crontab Generators

  - [ ] [Crontab Generator Online](https://crontab-generator.org/)
  - [ ] [Cron Guru](https://crontab.guru/)

</details>

<details>
<summary>Windows Fundamentals Part 1 - Windows User Manager </summary>

  ```sh
  lusrmgr.msc
  ```

  <img width="1680" alt="image" src="https://github.com/user-attachments/assets/b674f133-797e-4032-a3f9-7330cd7c3a2d" />

</details>

<details>
<summary>Windows Fundamentals Part 2 - Windows Utilities</summary>
  
  ### System Configuration utility 

  ```sh
  msconfig
  ```

  <img width="664" alt="image" src="https://github.com/user-attachments/assets/e6d95d50-75e9-4938-ace8-fa7eceae394a" />

  ### Performance Monitor 
  
  ```sh
  perfmon
  ```

  <img width="840" alt="image" src="https://github.com/user-attachments/assets/fa2d7f89-7b31-4f7e-ac4c-4b45c1e01984" />

  ### Computer Management
  
  ```sh
  compmgmt
  ```

  <img width="837" alt="image" src="https://github.com/user-attachments/assets/5bd492b8-46c2-410e-993c-5f48cbed29af" />

  ### System Information
  
  ```sh
  msinfo32
  ```

  <img width="761" alt="image" src="https://github.com/user-attachments/assets/00f0d5fd-c241-49f5-8c5f-6264fae0b7b5" />

  ### Resource Monitor
  
  ```sh
  resmon
  ```

  <img width="811" alt="image" src="https://github.com/user-attachments/assets/df2166a6-17c2-4ac6-8b47-52052ea92f7e" />

  ### Registry Editor
  
  ```sh
  regedit
  ```

  <img width="633" alt="image" src="https://github.com/user-attachments/assets/58ff5b33-42da-408a-af04-dd5f7dc92f65" />

</details>

















## Cyber Security 101 (TRY-HACK-ME)

<details>
<summary>Windows Fundamentals Part 1 - Processes </summary>

  ```

  ```

  ```

  ```

</details>
















