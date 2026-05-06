# Linux Essentials (DevOps Quick Notes)

## 🔧 Core Components of Linux

- **Kernel**
  - The core of the OS (runs in privileged mode)
  - Manages CPU, memory, devices, file systems
  - Handles system calls from applications

- **User Space**
  - Where applications run (bash, Python, Docker, etc.)
  - Interacts with kernel via system calls
  - Safer (restricted access vs kernel)

- **init / systemd**
  - First process started (PID 1)
  - Initializes system services and background processes
  - Modern systems use **systemd** instead of legacy init

---

## ⚙️ Process Creation & Management

- New processes are created using:
  - `fork()` → creates a copy of parent process
  - `exec()` → replaces process with a new program

- Each process has:
  - **PID (Process ID)**
  - **PPID (Parent Process ID)**

- Managed by kernel scheduler:
  - Allocates CPU time
  - Handles priorities (nice values)

---

## 🔄 Process States

- **Running (R)** → actively executing on CPU  
- **Sleeping (S)** → waiting for event (e.g., I/O)  
- **Stopped (T)** → paused (e.g., via `kill -STOP`)  
- **Zombie (Z)** → finished execution but still in process table (waiting for parent to read exit status)  
- **Dead (X)** → fully terminated (rarely seen)

---

## 🚀 What systemd Does (Why It Matters)

- Service manager (replaces init scripts)
- Starts services in parallel → faster boot
- Manages:
  - Services (`.service`)
  - Sockets (`.socket`)
  - Timers (`.timer`) → cron alternative
- Provides:
  - Logging via `journalctl`
  - Dependency handling (start order control)
- Central command:
  - `systemctl` (start/stop/status services)

---

## 🧰 5 Daily DevOps Commands

- `ps -ef` → list running processes  
- `top` / `htop` → real-time system monitoring  
- `df -h` → disk usage  
- `free -m` → memory usage  
- `systemctl status <service>` → check service health  

---

## 💡 Practical Tips

- Zombie processes usually indicate a parent process issue
- Use `nice` / `renice` to control CPU priority
- Use `journalctl -u <service>` for debugging services
- Always check system load before scaling or restarting services