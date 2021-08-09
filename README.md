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
