Task 1: Create Users
[oracle@devops-automation-01 ~]$ sudo useradd tokyo
[oracle@devops-automation-01 ~]$ sudo useradd berlin
[oracle@devops-automation-01 ~]$ sudo useradd perth

[oracle@devops-automation-01 ~]$ sudo cat /etc/passwd

tokyo:x:1006:1007::/home/tokyo:/bin/bash
berlin:x:1007:1008::/home/berlin:/bin/bash
perth:x:1008:1009::/home/perth:/bin/bash

[oracle@devops-automation-01 ~]$ ll /home/
total 3

drwx------.  2 berlin   berlin     62 May 13 12:53 berlin
drwx------.  2 perth    perth      62 May 13 12:54 perth
drwx------.  2 tokyo    tokyo      62 May 13 12:53 tokyo


Task 2: Create Groups

[oracle@devops-automation-01 ~]$ sudo groupadd developers
[oracle@devops-automation-01 ~]$ sudo groupadd admins
[oracle@devops-automation-01 ~]$ cat /etc/group
developers:x:1010:
admins:x:1011:


[oracle@devops-automation-01 ~]$ sudo cat /etc/passwd
tokyo:x:1006:1007::/home/tokyo:/bin/bash
berlin:x:1007:1008::/home/berlin:/bin/bash
perth:x:1008:1009::/home/perth:/bin/bash


Task 3: Assign to Groups

[oracle@devops-automation-01 ~]$ sudo usermod -aG developers tokyo
[oracle@devops-automation-01 ~]$ sudo usermod -aG admins berlin
[oracle@devops-automation-01 ~]$ sudo usermod -aG developers berlin
[oracle@devops-automation-01 ~]$ sudo usermod -aG admins perth

[oracle@devops-automation-01 ~]$ pwd
/home/oracle
[oracle@devops-automation-01 ~]$ cd ..
[oracle@devops-automation-01 home]$ ll
total 3

drwx------.  2 berlin   berlin     62 May 13 12:53 berlin
drwx------.  2 perth    perth      62 May 13 12:54 perth
drwx------.  2 tokyo    tokyo      62 May 13 12:53 tokyo


Task 4: Shared Directory 

[oracle@devops-automation-01 home]$ sudo mkdir -p /opt/dev-project
[oracle@devops-automation-01 home]$ sudo chgrp developers /opt/dev-project
[oracle@devops-automation-01 home]$ ll
total 3

drwx------.  2 berlin   berlin     62 May 13 12:53 berlin
drwx------.  2 perth    perth      62 May 13 12:54 perth
drwx------.  2 tokyo    tokyo      62 May 13 12:53 tokyo

[oracle@devops-automation-01 home]$ cd /opt/
[oracle@devops-automation-01 opt]$ ll
total 11888
drwxr-x---. 8 oracle oracle          119 Jul  8  2025 ADO
drwxr-x---. 2 root   developers        6 May 13 13:03 dev-project
drwxr-x---. 9 oracle oracle         4096 Mar  6 05:19 EAC
-rw-r-----. 1 oracle oracle     12157680 Sep  8  2025 EAC.zip
drwxr-xr-x. 6 root   root           4096 Mar 20 11:24 oracle
drwxr-xr-x. 4 root   root             50 Apr  3  2023 rh
drwxr-xr-x. 3 root   root           4096 May 12 19:00 snow
drwxr-xr-x. 6 root   root            169 May  4 14:01 unified-monitoring-agent

[oracle@devops-automation-01 opt]$ sudo chmod -R 775 dev-project/
[oracle@devops-automation-01 opt]$ ll
total 11888
drwxr-x---. 8 oracle oracle          119 Jul  8  2025 ADO
drwxrwxr-x. 2 root   developers        6 May 13 13:03 dev-project
drwxr-x---. 9 oracle oracle         4096 Mar  6 05:19 EAC
-rw-r-----. 1 oracle oracle     12157680 Sep  8  2025 EAC.zip
drwxr-xr-x. 6 root   root           4096 Mar 20 11:24 oracle
drwxr-xr-x. 4 root   root             50 Apr  3  2023 rh
drwxr-xr-x. 3 root   root           4096 May 12 19:00 snow
drwxr-xr-x. 6 root   root            169 May  4 14:01 unified-monitoring-agent

[oracle@devops-automation-01 opt]$ sudo su tokyo
[tokyo@devops-automation-01 opt]$ cd dev-project/
[tokyo@devops-automation-01 dev-project]$ touch tokyo_file
[oracle@devops-automation-01 opt]$ sudo su berlin
[berlin@devops-automation-01 dev-project]$ touch berlin_file
[berlin@devops-automation-01 dev-project]$ ll
total 0
-rw-r-----. 1 berlin berlin 0 May 13 13:08 berlin_file
-rw-r-----. 1 tokyo  tokyo  0 May 13 13:05 tokyo_file

Task 5: Team Workspace

[oracle@devops-automation-01 opt]$ sudo useradd nairobi
[oracle@devops-automation-01 opt]$ sudo groupadd project-team
[oracle@devops-automation-01 opt]$ sudo usermod -aG project-team nairobi
[oracle@devops-automation-01 opt]$
[oracle@devops-automation-01 opt]$ sudo usermod -aG project-team tokyo
[oracle@devops-automation-01 opt]$ sudo mkdir -p team-workspace
[oracle@devops-automation-01 opt]$ sudo chgrp project-team team-workspace
[oracle@devops-automation-01 opt]$ ll
total 11888
drwxr-x---. 8 oracle oracle            119 Jul  8  2025 ADO
drwxrwxr-x. 2 root   developers         43 May 13 13:08 dev-project
drwxr-x---. 9 oracle oracle           4096 Mar  6 05:19 EAC
-rw-r-----. 1 oracle oracle       12157680 Sep  8  2025 EAC.zip
drwxr-xr-x. 6 root   root             4096 Mar 20 11:24 oracle
drwxr-xr-x. 4 root   root               50 Apr  3  2023 rh
drwxr-xr-x. 3 root   root             4096 May 12 19:00 snow
drwxr-x---. 2 root   project-team        6 May 13 13:32 team-workspace
drwxr-xr-x. 6 root   root              169 May  4 14:01 unified-monitoring-agent
[oracle@devops-automation-01 opt]$ chmod 775 team-workspace/
[oracle@devops-automation-01 opt]$ sudo chmod 775 team-workspace/
[oracle@devops-automation-01 opt]$ ll
total 11888
drwxr-x---. 8 oracle oracle            119 Jul  8  2025 ADO
drwxrwxr-x. 2 root   developers         43 May 13 13:08 dev-project
drwxr-x---. 9 oracle oracle           4096 Mar  6 05:19 EAC
-rw-r-----. 1 oracle oracle       12157680 Sep  8  2025 EAC.zip
drwxr-xr-x. 6 root   root             4096 Mar 20 11:24 oracle
drwxr-xr-x. 4 root   root               50 Apr  3  2023 rh
drwxr-xr-x. 3 root   root             4096 May 12 19:00 snow
drwxrwxr-x. 2 root   project-team        6 May 13 13:32 team-workspace
drwxr-xr-x. 6 root   root              169 May  4 14:01 unified-monitoring-agent
[oracle@devops-automation-01 opt]$ cd team-workspace/
[oracle@devops-automation-01 team-workspace]$ sudo su nairobi
[nairobi@devops-automation-01 team-workspace]$ touch nairobi_file
[nairobi@devops-automation-01 team-workspace]$ ll
total 0
-rw-r-----. 1 nairobi nairobi 0 May 13 13:33 nairobi_file
