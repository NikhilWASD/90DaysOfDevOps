# 🐧 Linux Command Cheat Sheet (DevOps Focus)

---

## ⚙️ Process Management

- `ps -ef` → List all running processes  
- `ps aux --sort=-%cpu` → Show processes sorted by CPU usage  
- `top` → Real-time process monitoring  
- `htop` → Interactive process viewer (better UI than top)  
- `kill <PID>` → Terminate a process  
- `kill -9 <PID>` → Force kill a process  
- `pkill <name>` → Kill processes by name  
- `pgrep <name>` → Find process IDs by name  
- `nice -n 10 <cmd>` → Start process with lower priority  
- `renice 5 -p <PID>` → Change priority of running process  
- `jobs` → List background jobs  
- `bg` → Resume job in background  
- `fg` → Bring job to foreground  

---

## 📂 File System

- `ls -lh` → List files with sizes in human-readable format  
- `pwd` → Show current directory  
- `cd <dir>` → Change directory  
- `du -sh *` → Show size of files/directories  
- `df -h` → Disk space usage  
- `cp <src> <dest>` → Copy files/directories  
- `mv <src> <dest>` → Move or rename files  
- `rm -rf <dir>` → Delete directory recursively (use carefully)  
- `find /path -name "*.log"` → Search files by name  
- `grep "text" file` → Search text inside files  
- `chmod 755 file` → Change file permissions  
- `chown user:group file` → Change ownership  

---

## 🌐 Networking Troubleshooting

- `ping <host>` → Check connectivity to a host  
- `ip addr` → Show network interfaces & IP addresses  
- `ss -tuln` → List listening ports and connections  
- `netstat -tulnp` → Show active connections (legacy but useful)  
- `curl -I <url>` → Fetch HTTP headers (check service response)  
- `dig <domain>` → DNS lookup information  
- `traceroute <host>` → Trace network path to host  

---


