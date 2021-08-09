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
># Create a file
>$ touch file1

># Set permission using either of the method
>$ chmod 750 file1
>$ chmod u=rwx,g=rx,o= file1

># List the file permission
>$ ls -lh file1

Change ownership of a file or directory to a given user and group  
>$ chown user:group file1  



