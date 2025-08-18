**Definition**: Inter-Process Communication (IPC) is how processes send information to one another.
- Main focus here: **sockets** and **signals**.
- Other methods exist (not assessed in detail).

---
#### Other IPC Methods (Not Assessed)

- **Pipes**
    - OS creates memory for communication between two processes.
    - Typically **one-directional** (can chain multiple).
    - Simple and common.
- **Shared Memory**
    - Reserve memory accessible to multiple processes.
    - Very fast.
    - Requires careful **synchronization**.
- **Memory Maps**
    - Map a file’s memory into a process’s address space.
    - Useful for **large files**.
    - Persistent (data stored in a file).


---
#### Signals

**Definition**: A signal is an **integer value** sent from one process to another.
- Predefined set of signals: found in `<signal.h>` (from `signum.h`).
- Only **two signals** are user-defined.
- Very **limited IPC** (compared to sockets, pipes, etc.).
- Same-host only (not across machines).

---
#### Using Signals (Two Steps)

1. **Install a Signal Handler**
    - Tells the process which function to call when a signal is received.
2. **Send a Signal**
    - Another process triggers the signal.


---
### Installing a Signal Handler

- Each signal has a **default handler** (often terminates process).
- Use `signal()` system call to install a custom handler.

```
sighandler_t signal(int signum, sighandler_t action);
```

- `signum`: predefined signal (e.g., `SIGINT`, `SIGKILL`).
- `action`: what happens when signal received. Options:
    - `SIG_IGN` → Ignore.
    - `SIG_DFL` → Default action.
    - Custom function → Defined by programmer.

```
void handler_name(int signum);
```


---
#### Sending a Signal

- Use the `kill()` system call:

```
int kill(pid_t pid, int signum);
```
- `pid`: Process ID of target.
- `signum`: predefined signal.
- Returns `0` if success, `-1` if error.


---
#### Orphans and Zombies

- **Child exit behavior**:
    - When child exits, most resources freed.
    - Still has a **return code** stored in process table.
    - Parent retrieves it using `wait()`.
- **Orphan process**:
    - Parent terminates before child.
    - Orphan adopted by **PID 1** (init/systemd).
- **Zombie process**:
    - Child exited, but parent hasn’t retrieved exit code.
    - Remains in process table.
    - If parent dies, **grandparent** reaps it


---
#### When Are Signals Useful?

Although limited, signals are handy for:
- Informing parent/child processes to clean up data.
- Notifying when part of a process is done.
- Triggering functions in another process (e.g., logging, shutdown).
- Basic error handling.