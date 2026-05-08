[oracle@devops-automation-11 tmp]$ touch notes.txt
[oracle@devops-automation-11 tmp]$ echo "Line 1" > notes.txt
[oracle@devops-automation-11 tmp]$ echo "Line 2" >> notes.txt
[oracle@devops-automation-11 tmp]$ echo "Line 3" | tee -a notes.txt
Line 3
[oracle@devops-automation-11 tmp]$ cat notes.txt
Line 1
Line 2
Line 3
[oracle@devops-automation-11 tmp]$ head -n 2 notes.txt
Line 1
Line 2
[oracle@devops-automation-11 tmp]$ tail -n 2 notes.txt
Line 2
Line 3
[oracle@devops-automation-11 tmp]$
