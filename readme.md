# Linux Process Monitoring and Control System

## 1. About the Project
This project is a lightweight, terminal-based process manager built in C for Linux environments. It monitors active system processes and provides administrative controls such as pausing, resuming, or terminating specific tasks.

Instead of relying on third-party libraries, the application directly navigates and parses the Linux `/proc` virtual filesystem to extract metrics like Process ID (PID), Parent Process ID (PPID), execution state, and memory usage. It features a multi-process design where a frontend user interface communicates with a background daemon using unnamed pipes (`pipe()`) for Inter-Process Communication (IPC). It also includes a memory watchdog that automatically flags high-memory processes and logs administrative actions to a local file.

---

## 2. Technologies Used
* **Operating System:** Linux / Ubuntu (via Windows Subsystem for Linux - WSL)
* **Programming Language:** C (Standard POSIX APIs)
* **Compiler:** GCC (GNU Compiler Collection)
* **Core Concepts & APIs:**
  * Virtual Filesystem (`/proc` directory traversal via `<dirent.h>`)
  * Inter-Process Communication (`pipe()`, `fork()`)
  * Signal Handling (`kill()`, `SIGSTOP`, `SIGCONT`, `SIGKILL`)
  * Low-level & Standard File I/O (`read()`, `write()`, `fopen()`, `fprintf()`)

---

## 3. Output

### Terminal Interface (Interactive Menu)
```text
=== LINUX MULTI-FILE IPC MONITOR ===

PID        PPID       STATE      NAME                
------------------------------------------------------
1          0          S          systemd             
742        1          S          dbus-daemon         
1289       1          S          sshd                
2410       1289       R          python3             
------------------------------------------------------

Options: [0] Refresh | [PID] Control Process | [-1] Exit
Choice: 2410
Action for PID 2410 -> 1:STOP 2:CONT 3:KILL : 1
Signal command sent via IPC pipe...
Press Enter to continue...
