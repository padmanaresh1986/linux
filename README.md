**Useful Linux Commands**

**Directory Navigation**  


Change to /home directory   
>$ cd /home  

Change to the previous directory  
>$ cd -  

Go up one level of the directory tree  
>$ cd ..     

Print’s current directory you are in  
>$ pwd  

**System Information**  


Display Linux kernel information  
>$ uname -a  

Display kernel release information  
>$ uname -r  

Show how long the system has been running + load  
>$ uptime  

Show system hostname  
>$ hostname  

Display the IP addresses of the host  
>$ hostname -I  

Show system reboot history  
>$ last reboot  

Show the current date and time  
>$ date  

Show this month’s calendar  
>$ cal  

Display who is online  
>$ w  

Who you are logged in as  
>$ whoami  
>$ id  


**Hardware Information**  

Display CPU information  
>$ cat /proc/cpuinfo  

Display number of CPU cores  
>$ nproc  

Display memory information  
>$ cat /proc/meminfo  

Display environment variables of a process, e.g: PID 1  
>$ cat /proc/1/environ  

Display free and used memory ( -h for human-readable, -m for MB, -g for GB.)  
>$ free -h  


**System Monitoring, Statistics, Debugging**  


Display and manage the running processes  
>$ top  

Install and use a friendly interactive process viewer (alternative to top)  
>$ apt install htop  
>$ htop  

Display processor related statistics (refresh every 1 second)  
>$ mpstat 1  

NOTE: If you encounter following error: /usr/bin/mpstat: No such file or directory. Search and install the package that provides mpstat tool.*  
>$ apt-file search bin/mpstat  

sysstat: /usr/bin/mpstat  
>$ apt install sysstat  

Display virtual memory statistics (refresh every 1 second)  
>$ vmstat 1  

Display disk I/O statistics (refresh every 1 second)  
>$ iostat 1  

List all open files on the system  
>$ lsof  

List files opened by the user (e.g: root)  
>$ lsof -u USER

List files opened by a certain process with PID (e.g: 1)  
>$ lsof -p PID  

Display disk space occupied by current directory ( -h for human-readable, -s summarize)  
>$ du -sh  

Execute “df -h”, showing periodic updates every 1 second (pro tip: -d flag shows visual updates)  
>$ watch -n1 df -h  


**File and Directory**  

List all files (including hidden) in a long listing human-readable format in the current directory (specifying . is optional).  
>$ ls -hal .

Display the present working directory  
>$ pwd

Create one or more new empty file 
>$ touch file1 file2

Create a new directory  
>$ mkdir dir1  

Create a directory tree using -p option  
>$ mkdir -p dir1/dir2/dir3

List the directory tree using tree command  
>$ tree dir1

NOTE: Install tree package, if you encounter the following error:
bash: tree: command not found*  
>$ apt install tree

Copy (duplicate) file(s) from one directory to another (-v option for enabling verbose mode)  
>$ cp -v file1 dir1/file1-copy

Copy directory and all it’s content to a new directory  
>$ cp -vr dir1 dir1-copy

Rename or move a file. If file2 is a directory, then file1 into moved into that directory  
>$ mv -v file1 file1-rename
>$ mv -v file1-rename dir1

Remove a file or empty directory (-f option force deletes without asking)  
>$ rm file1

Remove a directory and its contents recursively (-v option for enabling verbose mode) 
>$ rm -vr dir1

Create a symbolic link (pointer) to a file or directory  
>$ ln -s file1 file1-link

Write a simple text to a file  
>$echo "hello, world!" > hello.txt

View the contents of a file  
>$ cat hello.txt

Paginate through a large file  
>$ less hello.txt

Display the first 20 lines of a file  
>$ head -n 20 hello.txt

Display the last 20 lines of a file  
>$ tail -n 20 hello.txt

Display the last 10 lines of a file and follow the file as it updated.  
>$ tail -f hello.txt


**File Permissions** 

Give all permission to the owner, read execute to the group and nothing to others  
>Create a file
>$ touch file1

>Set permission using either of the method
>$ chmod 750 file1
>$ chmod u=rwx,g=rx,o= file1

> List the file permission
>$ ls -lh file1

Change ownership of a file or directory to a given user and group  
>$ chown user:group file1  

**Networking**  

Display information of all available network interfaces  
>$ ip addr
>$ ifconfig -a    # deprecated

Display information of eth0 interface  
>$ ip addr show eth0
>$ ifconfig eth0  # deprecated

Display IP routing table  
>$ ip route
>$ route   # deprecated

Ping a hostname or IP address  
>$ ping google.com
>$ ping 8.8.8.8

Display registration information of a domain  
>$ whois medium.com

DNS lookup a domain  
>$ dig medium.com A     # IPv4 addresses
>$ dig medium.com AAAA  # IPv6 addresses
>$ dig medium.com NX    # Nameservers
>$ host medium.com     # IPv4 addresses

Display hostname and IP address of the local machine  
>$ hostname
>$ hostname -i

Download files from a remote HTTP server  
>$ wget [http://ipv4.download.thinkbroadband.com/5MB.zip](http://ipv4.download.thinkbroadband.com/5MB.zip)
>$ curl --output 5MB.zip [http://ipv4.download.thinkbroadband.com/5MB.zip](http://ipv4.download.thinkbroadband.com/5MB.zip)

Display all process listening on TCP or UDP ports  
>$ netstat -plunt
>$ lsof -i
>$ lsof -i tcp     # only TCP ports

**Text Search**  

Search for a pattern in a text file  
>$ grep pattern file
>For example:
>$ grep root /etc/passwd

Search recursively for a pattern in a text file inside a directory  
>$ grep -R "/bin/bash" /etc

Search for pattern and output N lines before (B) or after (A) pattern match  
>$ grep -B 5 root /etc/passwd
>$ grep -A 3 root /etc/passwd

Find files within a directory with a matching filename  
>find /etc -iname 'passwd'
>find /etc -iname 'pass*'  # glob pattern

Find files based on filesize  
>find / -size +1M #  larger than 1MB
>find / -size -1M # smaller than 1MB


**Disk Usage**  

Show free and used space of disk storages  
>df -h

Show disk space consumed by a directory or file  
>du -sh /var/log
>du -h 5MB.zip

Interactive disk usage explorer  
>apt install ncdu
>ncdu


**Pipes and Redirection**  

REDIRECTION Redirect normal output (stdout) from a command to a file  
>echo "hello" > hello.stdout.txt
>echo "world" > hello.stdout.txt

Redirect error output (stderr) from a command to a file  
>cat somefile 2> cat.stderr.txt

Redirect both normal and error output from a command to a file. Useful for logging.  
>ps auxf >& processes.txt

Append normal output (stdout) from a command to a file unlike > which overwrites the file  
>echo "hello" >> hello2.stdout.txt
>echo "world! >> hello2.stdout.txt

Append error output (stderr) from a command to a file  
>cat some-unknown-file 2>> cat2.stderr.txt

Append both normal and error output (stderr) from a command to a file  
>ps auxf &>> processes.txt  

**PIPES**  

The shell pipe **is a way to **communicate between commands.  
Create a dummy file to learn to pipe  

>mkdir pipes-example
>cd pipes-example
>touch {1..10}.txt

Example 1: Let’s use sort command  
>ls -1 *.txt | sort -n    # sorts the output in ASC order
>ls -1 *.txt | sort -nr   # sorts the output in DESC order

Example 2: Let’s use head & tail command  
>ls -1 *.txt | sort -n | head -n 5  # show the first 5 lines
>ls -1 *.txt | sort -n | tail -n 5  # show the last 5 lines

Example 3: Search for a pattern in a text file  
>cat /etc/passwd | grep root    # show lines containing string 'root'


**Environment Variables**  

List all environment variables  
>$ env

Display value of an environment variable  
>echo $HOME
>echo $SHELL 

Create an environment variable  
>export PORT=80
>export PLATFORM=medium.com

Delete an environment variable  
>unset PORT  

PATH is one of the common and important environment variables. What do you think will happen if you unset it?  
>$ echo $PATH
>$ unset PATH




