Essential Linux Directories

Core Directories (Must Know)
/ (Root Directory)
The top-level directory in Linux — everything starts from here.
All files, directories, devices, and system resources exist under the root directory structure.

/home
Contains personal home directories for regular users.
Each user typically has their own folder here for documents, downloads, scripts, and personal configurations.
Example:
/home/gavi

/root
Home directory of the root (administrator) user.
Separate from /home for security and administrative isolation.

/etc
Stores system-wide configuration files and service settings.
DevOps engineers frequently work here to configure applications, networking, SSH, services, and system behavior.
Examples:
/etc/ssh//etc/nginx//etc/passwd

/var/log
Contains system and application log files.
Very important for troubleshooting, monitoring, debugging, and incident analysis in DevOps/SRE work.
Examples:
/var/log/syslog/var/log/messages/var/log/nginx/

/tmp
Used for temporary files created by applications and users.
Files here may be automatically deleted during reboot or cleanup operations.

Additional Directories (Good to Know)
/bin
Contains essential command binaries needed for basic system operation.
Commands like ls, cp, mv, and cat are traditionally stored here.

/usr/bin
Stores most user-level command binaries and applications.
This directory contains the majority of standard Linux commands and utilities.
Examples:
/usr/bin/python/usr/bin/git/usr/bin/docker

/opt
Used for optional or third-party software installations.
Commonly used for manually installed applications or enterprise tools.
Examples:
/opt/tomcat/opt/google/chrome

#################### Hands on task outputs- ############################

[oracle@devops-automation-06 oracle]$ du -sh /var/log/* 2>/dev/null | sort -h | tail -5
23M     /var/log/messages-20260419
36M     /var/log/cloud-init.log
64M     /var/log/oracle-cloud-agent
103M    /var/log/sudo.log
1.4G    /var/log/journal

[oracle@devops-automation-06 oracle]$ cat /etc/hostname
devops-automation-06

[oracle@devops-automation-06 oracle]$ ls -la ~
total 173684
drwx------. 18 oracle oracle     4096 May 11 10:15 .
drwxr-xr-x.  7 root   root         76 Sep 26  2025 ..
drwxr-xr-x.  4 oracle oracle       34 May 11 10:15 ADO_WorkSpace
drwx------.  4 oracle oracle       27 Jun 18  2025 .ansible
drwxr-x---.  5 oracle oracle      100 Jun 18  2025 ansible-venv
-rw-------.  1 oracle oracle    56980 May 11 13:36 .bash_history
-rw-r--r--.  1 oracle oracle       18 Aug  2  2022 .bash_logout
-rw-r--r--.  1 oracle oracle      141 Aug  2  2022 .bash_profile
-rw-r--r--.  1 oracle oracle      376 Aug  2  2022 .bashrc
drwx------.  4 oracle oracle       35 Aug  7  2024 .cache


Scenario 1: Service Not Starting

# 1. Check service status
systemctl status myapp

# 2. View detailed logs for the service
journalctl -u myapp -n 50 --no-pager

# 3. Check if the application process is running
ps -ef | grep myapp

# 4. Check if the required port is already in use
ss -tulnp | grep <PORT>

# 5. Review application-specific logs
tail -50 /var/log/myapp.log

# 6. Try starting the service manually and observe errors
systemctl start myapp

# 7. Recheck service status after manual start
systemctl status myapp


What each command helps identify

systemctl status myapp
Shows whether the service failed, exited, or is inactive along with recent error messages.

journalctl -u myapp
Displays detailed systemd logs for the service startup process.

ps -ef | grep myapp
Verifies whether any process related to the application is running or stuck.

ss -tulnp | grep <PORT>
Checks if another process is already using the application's required port.

tail -50 /var/log/myapp.log
Reviews application logs for configuration issues, crashes, or dependency failures.

systemctl start myapp
Attempts a manual restart to reproduce and observe the failure in real time.

Scenario 2: High CPU Usage

# 1. View real-time CPU usage of processes
top

# 2. Alternative improved process viewer (if installed)
htop

# 3. List top CPU-consuming processes
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head

# 4. Check overall system load average
uptime

# 5. Monitor CPU statistics continuously
vmstat 2

# 6. Identify process details using PID
ps -fp <PID>

# 7. Check if a specific service is causing the issue
systemctl status <service-name>

What these commands help with

top
Shows live CPU and memory consumption of running processes.

htop
Interactive and more user-friendly version of top with sorting/filtering.

ps -eo ... --sort=-%cpu
Quickly lists the highest CPU-consuming processes.

uptime
Displays system load averages to understand server stress levels.

vmstat 2
Shows CPU, memory, IO, and process statistics every 2 seconds.

ps -fp <PID>
Gives detailed information about the suspicious process.

systemctl status <service-name>
Helps verify whether a service related to the high-CPU process is unhealthy or repeatedly restarting.

Scenario 3: Finding Service Logs

# 1. View logs for the docker service
journalctl -u docker

# 2. View the most recent docker logs
journalctl -u docker -n 50

# 3. Follow logs in real time
journalctl -u docker -f

# 4. Check service status with recent logs
systemctl status docker

# 5. View logs since last boot
journalctl -u docker -b

# 6. Search for errors or warnings
journalctl -u docker | grep -i error

What these commands help with
journalctl -u docker
Displays all logs collected by systemd for the Docker service.

journalctl -u docker -n 50
Shows the latest 50 log entries for quick troubleshooting.

journalctl -u docker -f
Streams logs live as new events occur.

systemctl status docker
Shows current service status along with recent log messages.

journalctl -u docker -b
Displays logs generated since the last server boot.

grep -i error
Filters logs to quickly identify failures or warnings.

Scenario 4: File Permissions Issue

# 1. Check current file permissions
ls -l /home/user/backup.sh

# 2. Add execute permission to the script
chmod +x /home/user/backup.sh

# 3. Verify permissions were updated
ls -l /home/user/backup.sh

# 4. Execute the script
./backup.sh

What these commands do

ls -l
Displays file permissions and ownership.

chmod +x
Adds executable permission to the script.

./backup.sh
Runs the script from the current directory.