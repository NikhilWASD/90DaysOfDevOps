[oracle@devops-automation-11 ~]$ ps aux --sort=-%cpu
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
oracle     59645  8.5  1.9 274487868 151144 ?    Sl   08:17   0:03 /home/oracle/myagent/bin.4.268.0/Agent.Worker spawncl
root        2147  0.1  0.4 408060 31332 ?        Ssl  04:31   0:14 /usr/libexec/platform-python -Es /usr/sbin/tuned -l -
oracle     59236  0.1  0.0  15020  3672 ?        Ss   08:16   0:00 bash -c while true; do sleep 1;head -v -n 8 /proc/mem
oracle     59730  0.1  0.9 1429588 75824 ?       Sl   08:17   0:00 /home/oracle/myagent/externals/node24/bin/node /home/
root           1  0.0  0.1 247040 15160 ?        Ss   04:31   0:06 /usr/lib/systemd/systemd --switched-root --system --d


[oracle@devops-automation-11 ~]$ top
top - 08:18:35 up  3:47,  1 user,  load average: 0.08, 0.04, 0.00
Tasks: 219 total,   1 running, 218 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.1 us,  0.2 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   7646.2 total,    533.6 free,   1101.9 used,   6010.7 buff/cache
MiB Swap:   4096.0 total,   4075.9 free,     20.1 used.   6106.9 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
      1 root      20   0  247040  15160   9456 S   0.0   0.2   0:06.18 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.02 kthreadd
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 slub_flushwq
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri
     10 root       0 -20       0      0      0 I   0.0   0.0   0:00.10 kworker/0:1H-kblockd
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq
     13 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_rude_
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_trace


systemctl status 'vsts.agent.vfuk\x2ddigital.EACP2\x2dDRCC.devops\x2dautomation\x2d11.service'
● vsts.agent.vfuk\x2ddigital.EACP2\x2dDRCC.devops\x2dautomation\x2d11.service - Azure Pipelines Agent (vfuk-digital.EAC>
   Loaded: loaded (/etc/systemd/system/vsts.agent.vfuk\x2ddigital.EACP2\x2dDRCC.devops\x2dautomation\x2d11.service; ena>
   Active: active (running) since Wed 2026-05-06 04:31:26 GMT; 3h 48min ago
 Main PID: 2128 (runsvc.sh)
    Tasks: 21 (limit: 48304)
   Memory: 341.0M
   CGroup: /system.slice/vsts.agent.vfuk\x2ddigital.EACP2\x2dDRCC.devops\x2dautomation\x2d11.service
           ├─2128 /bin/bash /home/oracle/myagent/runsvc.sh
           ├─2641 ./externals/node20_1/bin/node ./bin/AgentService.js
           └─2723 /home/oracle/myagent/bin/Agent.Listener run --startuptype service

May 06 07:15:30 devops-automation-11 runsvc.sh[2641]: 2026-05-06 07:15:30Z: Running job: Preactivation_Order_SanityC2
May 06 07:19:40 devops-automation-11 runsvc.sh[2641]: 2026-05-06 07:19:40Z: Job Preactivation_Order_SanityC2 completed >
May 06 07:30:22 devops-automation-11 runsvc.sh[2641]: 2026-05-06 07:30:22Z: Running job: Preactivation_SUP01_PLAN_A
May 06 07:34:31 devops-automation-11 runsvc.sh[2641]: 2026-05-06 07:34:31Z: Job Preactivation_SUP01_PLAN_A completed wi>
May 06 07:45:33 devops-automation-11 runsvc.sh[2641]: 2026-05-06 07:45:33Z: Running job: Preactivation_SUP01_PLAN_A
May 06 07:49:42 devops-automation-11 runsvc.sh[2641]: 2026-05-06 07:49:42Z: Job Preactivation_SUP01_PLAN_A completed wi>
May 06 08:00:41 devops-automation-11 runsvc.sh[2641]: 2026-05-06 08:00:41Z: Running job: Preactivation_SUP01_PLAN_A
May 06 08:04:51 devops-automation-11 runsvc.sh[2641]: 2026-05-06 08:04:51Z: Job Preactivation_SUP01_PLAN_A completed wi>
May 06 08:17:09 devops-automation-11 runsvc.sh[2641]: 2026-05-06 08:17:09Z: Running job: SBL Upgrade Log Fetch
May 06 08:18:25 devops-automation-11 runsvc.sh[2641]: 2026-05-06 08:18:25Z: Job SBL Upgrade Log Fetch completed with re>
lines 1-21/21 (END)


systemctl list-units
UNIT                                                                  LOAD   ACTIVE SUB       DESCRIPTION
proc-sys-fs-binfmt_misc.automount                                     loaded active running   Arbitrary Executable File>
sys-devices-pci0000:00-0000:00:03.0-virtio0-net-ens3.device           loaded active plugged   Virtio network device
sys-devices-pci0000:00-0000:00:04.0-virtio1-host2-target2:0:0-2:0:0:1-block-sda-sda1.device loaded active plugged   Blo>
sys-devices-pci0000:00-0000:00:04.0-virtio1-host2-target2:0:0-2:0:0:1-block-sda-sda2.device loaded active plugged   Blo>
sys-devices-pci0000:00-0000:00:04.0-virtio1-host2-target2:0:0-2:0:0:1-block-sda-sda3.device loaded active plugged   Blo>
sys-devices-pci0000:00-0000:00:04.0-virtio1-host2-target2:0:0-2:0:0:1-block-sda.device loaded active plugged   BlockVol>
sys-devices-pci0000:00-0000:00:04.0-virtio1-host2-target2:0:1-2:0:1:1-block-sdb.device loaded active plugged   BlockVol>



journalctl -u 'vsts.agent.vfuk\x2ddigital.EACP2\x2dDRCC.devops\x2dautomation\x2d11.service'
Hint: You are currently not seeing messages from other users and the system.
      Users in groups 'adm', 'systemd-journal', 'wheel' can see all messages.
      Pass -q to turn off this notice.
-- Logs begin at Wed 2025-06-18 07:04:44 GMT, end at Wed 2026-05-06 08:18:29 GMT. --
Jun 18 07:04:44 devops-automation-11 runsvc.sh[2637]: 2025-06-18 07:04:44Z: Job Preactivation_SUP01_PLAN_A completed wi>
Jun 18 07:15:31 devops-automation-11 runsvc.sh[2637]: 2025-06-18 07:15:31Z: Running job: Preactivation_SUP01_PLAN_A
Jun 18 07:19:52 devops-automation-11 runsvc.sh[2637]: 2025-06-18 07:19:52Z: Job Preactivation_SUP01_PLAN_A completed wi>
Jun 18 07:30:40 devops-automation-11 runsvc.sh[2637]: 2025-06-18 07:30:40Z: Running job: Preactivation_SUP01_PLAN_A
Jun 18 07:35:00 devops-automation-11 runsvc.sh[2637]: 2025-06-18 07:35:00Z: Job Preactivation_SUP01_PLAN_A completed wi>
Jun 18 08:00:33 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:00:33Z: Running job: Preactivation_SUP01_PLAN_A
Jun 18 08:04:54 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:04:54Z: Job Preactivation_SUP01_PLAN_A completed wi>
Jun 18 08:15:11 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:15:11Z: Running job: Preactivation_SUP01_PLAN_A
Jun 18 08:19:32 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:19:32Z: Job Preactivation_SUP01_PLAN_A completed wi>
Jun 18 08:30:06 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:30:06Z: Running job: Preactivation_Order_SanityE4
Jun 18 08:34:28 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:34:28Z: Job Preactivation_Order_SanityE4 completed >
Jun 18 08:39:14 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:39:14Z: Running job: BRM15_Deploy_Multijob_DB_1
Jun 18 08:48:38 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:48:38Z: Job BRM15_Deploy_Multijob_DB_1 completed wi>
Jun 18 08:48:47 devops-automation-11 runsvc.sh[2637]: 2025-06-18 08:48:47Z: Running job: BRM15_Deploy_Multijob_DB_2


sudo tail -n 50 /var/log/maillog
maillog           maillog-20260413  maillog-20260420  maillog-20260427  maillog-20260504
[oracle@devops-automation-11 ~]$ sudo tail -n 50 /var/log/maillog
May  6 04:34:58 devops-automation-11 postfix/smtp[29920]: C84CE40879DC: to=<mihir.kulkarni@dummy.com>, relay=nlb-rtd2-smtp.oci.dummy.com[104.242.241.27]:587, delay=0.31, delays=0.06/0.02/0.18/0.05, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 4g9MxG0YtdzVhjc)
May  6 04:34:58 devops-automation-11 postfix/smtp[29920]: C84CE40879DC: to=<santosh.vanamkotaiah@dummy.com>, relay=nlb-rtd2-smtp.oci.dummy.com[104.242.241.27]:587, delay=0.31, delays=0.06/0.02/0.18/0.05, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 4g9MxG0YtdzVhjc)
May  6 04:34:58 devops-automation-11 postfix/smtp[29920]: C84CE40879DC: to=<venkatkumar.ramarathinam1@dummy.com>, relay=nlb-rtd2-smtp.oci.dummy.com[104.242.241.27]:587, delay=0.31, delays=0.06/0.02/0.18/0.05, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 4g9MxG0YtdzVhjc)
May  6 04:34:58 devops-automation-11 postfix/qmgr[2821]: C84CE40879DC: removed
May  6 05:03:16 devops-automation-11 sendmail[48104]: 64653CTR048104: from=root, size=12362438, class=-60, nrcpts=1, msgid=<202605060503.64653CTR048104@devops-automation-11.snta006.ie1vcn013205o2.oraclevcn.com>, relay=root@localhost
May  6 05:03:16 devops-automation-11 postfix/smtpd[48105]: connect from localhost[127.0.0.1]
May  6 05:03:16 devops-automation-11 postfix/smtpd[48105]: discarding EHLO keywords: CHUNKING
May  6 05:03:16 devops-automation-11 sendmail[48104]: STARTTLS=client, relay=[127.0.0.1], version=TLSv1.3, verify=FAIL, cipher=TLS_AES_256_GCM_SHA384, bits=256/256
May  6 05:03:16 devops-automation-11 postfix/smtpd[48105]: discarding EHLO keywords: CHUNKING
May  6 05:03:16 devops-automation-11 postfix/smtpd[48105]: 8AD3040879DC: client=localhost[127.0.0.1]
May  6 05:03:16 devops-automation-11 postfix/cleanup[48108]: 8AD3040879DC: message-id=<202605060503.64653CTR048104@devops-automation-11.snta006.ie1vcn013205o2.oraclevcn.com>
May  6 05:03:16 devops-automation-11 sendmail[48104]: 64653CTR048104: to=root, ctladdr=root (0/0), delay=00:00:04, xdelay=00:00:00, mailer=relay, pri=12500438, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (Ok: queued as 8AD3040879DC)
May  6 05:03:16 devops-automation-11 postfix/qmgr[2821]: 8AD3040879DC: from=<root@devops-automation-11.snta006.ie1vcn013205o2.oraclevcn.com>, size=12518780, nrcpt=1 (queue active)
May  6 05:03:16 devops-automation-11 postfix/smtpd[48105]: disconnect from localhost[127.0.0.1] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7

sudo systemctl status crond
● crond.service - Command Scheduler
   Loaded: loaded (/usr/lib/systemd/system/crond.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2026-05-06 04:31:38 GMT; 3h 53min ago
 Main PID: 3509 (crond)
    Tasks: 1 (limit: 48304)
   Memory: 2.8M
   CGroup: /system.slice/crond.service
           └─3509 /usr/sbin/crond -n

May 06 05:37:02 devops-automation-11 anacron[47949]: Job `cron.daily' terminated
May 06 05:37:02 devops-automation-11 anacron[47949]: Normal exit (1 job run)
May 06 06:01:01 devops-automation-11 CROND[51166]: (root) CMD (run-parts /etc/cron.hourly)
May 06 06:02:01 devops-automation-11 CROND[51253]: (root) CMD (export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/us>
May 06 06:32:01 devops-automation-11 CROND[54376]: (root) CMD (export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/us>
May 06 07:01:01 devops-automation-11 CROND[56109]: (root) CMD (run-parts /etc/cron.hourly)
May 06 07:02:01 devops-automation-11 CROND[56186]: (root) CMD (export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/us>
May 06 07:32:01 devops-automation-11 CROND[57556]: (root) CMD (export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/us>
May 06 08:01:01 devops-automation-11 CROND[58801]: (root) CMD (run-parts /etc/cron.hourly)
May 06 08:02:01 devops-automation-11 CROND[58880]: (root) CMD (export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/us>