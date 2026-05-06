uname -a
Linux devops-automation-11 5.15.0-318.199.3.2.1.el8uek.x86_64 #2 SMP Wed Mar 11 18:06:41 PDT 2026 x86_64 x86_64 x86_64 GNU/Linux


[oracle@devops-automation-11 ~]$ cat /etc/os-release
NAME="Oracle Linux Server"
VERSION="8.8"
ID="ol"
ID_LIKE="fedora"
VARIANT="Server"
VARIANT_ID="server"
VERSION_ID="8.8"
PLATFORM_ID="platform:el8"
PRETTY_NAME="Oracle Linux Server 8.8"
ANSI_COLOR="0;31"
CPE_NAME="cpe:/o:oracle:linux:8:8:server"
HOME_URL="https://linux.oracle.com/"
BUG_REPORT_URL="https://github.com/oracle/oracle-linux"

ORACLE_BUGZILLA_PRODUCT="Oracle Linux 8"
ORACLE_BUGZILLA_PRODUCT_VERSION=8.8
ORACLE_SUPPORT_PRODUCT="Oracle Linux"
ORACLE_SUPPORT_PRODUCT_VERSION=8.8


mkdir /tmp/runbook-demo
[oracle@devops-automation-11 ~]$ cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo
total 4
-rw-r-----. 1 oracle oracle 253 May  6 11:59 hosts-copy


[oracle@devops-automation-11 ~]$ ps -o pid
    PID
  59159
 166367
[oracle@devops-automation-11 ~]$ ps -o pcpu
%CPU
 0.0
 0.0
[oracle@devops-automation-11 ~]$ ps -o pmem
%MEM
 0.0
 0.0
[oracle@devops-automation-11 ~]$ ps -o comm
COMMAND
bash
ps
[oracle@devops-automation-11 ~]$ free -h
              total        used        free      shared  buff/cache   available
Mem:          7.5Gi       1.3Gi       581Mi       156Mi       5.6Gi       5.7Gi

[oracle@devops-automation-11 ~]$ df -h
Filesystem                  Size  Used Avail Use% Mounted on
devtmpfs                    3.7G     0  3.7G   0% /dev
tmpfs                       3.8G     0  3.8G   0% /dev/shm
tmpfs                       3.8G  704K  3.8G   1% /run
tmpfs                       3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/mapper/ocivolume-root   36G   31G  4.7G  87% /
tmpfs                       2.0G  144K  2.0G   1% /tmp
/dev/sdb                    100G  809M  100G   1% /opt/oracle
/dev/sda2                  1014M  695M  320M  69% /boot
/dev/mapper/ocivolume-oled   10G  542M  9.5G   6% /var/oled
/dev/sda1                   100M  6.0M   94M   6% /boot/efi
tmpfs                       765M     0  765M   0% /run/user/0
tmpfs                       765M     0  765M   0% /run/user/987
tmpfs                       765M     0  765M   0% /run/user/1002
[oracle@devops-automation-11 ~]$ sudo du -sh /var/log
4.0G    /var/log
[oracle@devops-automation-11 ~]$ iostat
^[[5~Linux 5.15.0-318.199.3.2.1.el8uek.x86_64 (devops-automation-11)    05/06/2026      _x86_64_        (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.60    0.01    0.55    0.22    0.01   97.62

Device             tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              19.63       880.00       106.20   23833540    2876312
sdb               0.08         2.75         0.08      74536       2104
dm-0             19.90       822.51        59.51   22276332    1611684
dm-1              0.25        30.60        46.61     828856    1262444

 journalctl -u 'vsts.agent.vfuk\x2ddigital.SIEBELIP23\x2dEAC.SBL_RELEASE_1.service' -n 50
Hint: You are currently not seeing messages from other users and the system.
      Users in groups 'adm', 'systemd-journal', 'wheel' can see all messages.
      Pass -q to turn off this notice.
-- Logs begin at Wed 2025-06-18 07:04:44 GMT, end at Wed 2026-05-06 12:02:24 GMT. --
Apr 30 22:30:44 devops-automation-11 runsvc.sh[2672]: Exiting...
Apr 30 22:30:45 devops-automation-11 runsvc.sh[2672]: Agent listener exited with error code 0
Apr 30 22:30:45 devops-automation-11 runsvc.sh[2672]: Agent listener exit with 0 return code, stop the service, no retr>
-- Reboot --
May 01 04:31:10 devops-automation-11 runsvc.sh[2160]: .path=/home/oracle/.local/bin:/home/oracle/bin:/usr/share/Modules>
May 01 04:31:14 devops-automation-11 runsvc.sh[2180]: v20.17.0
May 01 04:31:15 devops-automation-11 runsvc.sh[2687]: Starting Agent listener with startup type: service
May 01 04:31:15 devops-automation-11 runsvc.sh[2687]: Started listener process
May 01 04:31:15 devops-automation-11 runsvc.sh[2687]: Started running service
May 01 04:31:29 devops-automation-11 runsvc.sh[2687]: Scanning for tool capabilities.
May 01 04:31:30 devops-automation-11 runsvc.sh[2687]: Connecting to the server.
May 01 04:31:32 devops-automation-11 runsvc.sh[2687]: 2026-05-01 04:31:32Z: Listening for Jobs
May 01 22:30:57 devops-automation-11 runsvc.sh[2687]: Shutting down agent listener
May 01 22:30:57 devops-automation-11 runsvc.sh[2687]: Sending SIGINT to agent listener to stop
May 01 22:30:57 devops-automation-11 runsvc.sh[2687]: Exiting...
May 01 22:30:58 devops-automation-11 runsvc.sh[2687]: Agent listener exited with error code 0
May 01 22:30:58 devops-automation-11 runsvc.sh[2687]: Agent listener exit with 0 return code, stop the service, no retr>
-- Reboot --
May 04 04:31:25 devops-automation-11 runsvc.sh[2067]: .path=/home/oracle/.local/bin:/home/oracle/bin:/usr/share/Modules>
May 04 04:31:28 devops-automation-11 runsvc.sh[2097]: v20.17.0
May 04 04:31:29 devops-automation-11 runsvc.sh[2430]: Starting Agent listener with startup type: service
May 04 04:31:29 devops-automation-11 runsvc.sh[2430]: Started listener process
May 04 04:31:29 devops-automation-11 runsvc.sh[2430]: Started running service
May 04 04:31:41 devops-automation-11 runsvc.sh[2430]: Scanning for tool capabilities.
May 04 04:31:42 devops-automation-11 runsvc.sh[2430]: Connecting to the server.
May 04 04:31:44 devops-automation-11 runsvc.sh[2430]: 2026-05-04 04:31:44Z: Listening for Jobs
May 04 22:30:41 devops-automation-11 runsvc.sh[2430]: Shutting down agent listener
May 04 22:30:41 devops-automation-11 runsvc.sh[2430]: Sending SIGINT to agent listener to stop
May 04 22:30:42 devops-automation-11 runsvc.sh[2430]: Exiting...
May 04 22:30:44 devops-automation-11 runsvc.sh[2430]: Agent listener exited with error code 0
May 04 22:30:44 devops-automation-11 runsvc.sh[2430]: Agent listener exit with 0 return code, stop the service, no retr>
-- Reboot --
May 05 04:31:09 devops-automation-11 runsvc.sh[2149]: .path=/home/oracle/.local/bin:/home/oracle/bin:/usr/share/Modules>
May 05 04:31:12 devops-automation-11 runsvc.sh[2185]: v20.17.0
May 05 04:31:14 devops-automation-11 runsvc.sh[2675]: Starting Agent listener with startup type: service
lines 1-36

Quick findings- Agent Service getting crashed repeatatively

If this worsens (next steps)-

Restart the service manually, increase the log level verbosity, collect stack trace

