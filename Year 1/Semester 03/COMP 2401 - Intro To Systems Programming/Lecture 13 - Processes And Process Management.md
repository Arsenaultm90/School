#### Process Fundamentals

A **process** is a running program with:
- Its own memory
- Control flow
- A process ID (PID)
- A parent process ID (PPID)


---
#### Process Management

**Fork**
`fork()` – Create a New Process

```
pid_t fork(void);
```

- Duplicates the calling process.
- Return Values:
    - `0` → in the **child**
    - `> 0` → in the **parent** (child's PID)
    - `-1` → error


**Exec**
`exec()` – Replace Process with New Program

```
execvp("ls", (char*[]){"ls", "-l", NULL});
```

Replaces the current process memory with a new program (same PID).

|Function|Uses PATH|Args Format|
|---|---|---|
|`execv()`|❌|Array|
|`execvp()`|✅|Array|
|`execl()`|❌|List (varargs)|
|`execlp()`|✅|List (varargs)|

**Wait and Waitpid**
`wait()` and `waitpid()` – Wait for Child Processes

```
pid_t wait(int* status);
pid_t waitpid(pid_t pid, int* status, int options);
```

- `wait()` → wait for any child to finish.
- `waitpid()` → wait for a specific child.


**System**
`system()` – Run Shell Commands

```
int system(const char *command);
```

- Internally uses `fork()`, `exec()`, and `waitpid()`.
- Runs a command in a shell.
- Blocks until the command finishes


---
#### Signals and Process Control

- Integer values sent from one process to another or from the kernel.
- Defined in `<signal.h>` (from `signum.h`).

- Examples:
    - `SIGINT` (Interrupt) → `Ctrl+C`
    - `SIGSTOP` (Stop) → `Ctrl+Z`

- **User-defined signals**: Only two available.
- Use `kill(pid, signal)` to send



---
#### Shell and Process Interaction

**Foreground vs Background Execution**
- **Foreground**: `./program`
- **Background**: `./program &`

**Shell Behaviour with System Calls**
- Shell **forks** a new process.
    - In **child**: runs program using `exec()`.
    - In **parent**:
        - Waits if foreground
        - Continues if background



---
#### Summary Table Of System Calls

| System Call | Description                        |     |
| ----------- | ---------------------------------- | --- |
| `fork()`    | Clone current process              |     |
| `exec()`    | Replace current process image      |     |
| `wait()`    | Wait for child process termination |     |
| `system()`  | Run command via shell              |     |
| `kill()`    | Send signal to a process           |     |
