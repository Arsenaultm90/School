#### Basic Concepts

**CPU–I/O Burst Cycle**
A **CPU burst** is simply the **period of time a process spends actively executing on the CPU** before it either:
1. **Needs I/O** (e.g., reading/writing a file, waiting for user input), or
2. **Terminates** (process finishes execution).

- Programs alternate between CPU bursts (computation) and I/O bursts (waiting for input/output).
- **Implications for scheduling:**
	- **Waiting time (WT):** Time spent in the ready queue waiting for CPU.
	- **Turnaround time (TAT):** Total time from submission to completion, including CPU bursts, I/O bursts, and waiting time. (Completion Time - Arrival Time)
	- **Response time (RT):** Time from submission until the **process first gets the CPU**. (Just the first time it gets to CPU. Non-Cumulative).
- **Special case (CPU-bound process):**
	- If I/O bursts are disregarded, then:
		Response time=Turnaround time−Waiting time
- **Scheduling relevance:**
	- Short CPU bursts → more frequent preemption (affects RR or SRTF).
	- Long CPU bursts → can cause convoy effect in FCFS.
	- **Visualization:**
```
Time → |CPU| I/O | CPU | I/O | CPU |
WT   →  ^     ^     ^     ^  
RT   →  ^ (time to first CPU)
TAT  →  |------------------|

```

- **Scheduler’s role:** Decide which process gets the CPU when multiple are ready.
- **Dispatcher:** Gives control of CPU to the process chosen by the scheduler (context switch).

**Types of schedulers:**
- **Long-term:** Selects jobs to enter system (controls degree of multiprogramming).
- **Medium-term:** Suspends/resumes processes to optimize performance.
- **Short-term (CPU scheduling):** Chooses from the ready queue which process runs next.

| **Scheduler**                  | **When it Runs / Purpose**                                                   | **Key Points**                                                                   |
| ------------------------------ | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| **Long-term scheduler**        | When new jobs are admitted to the system (job queue → ready queue)           | Controls degree of multiprogramming; runs infrequently                           |
| **Medium-term scheduler**      | Occasionally suspends/resumes processes (ready ↔ suspended)                  | Helps balance CPU and memory usage; may swap processes in/out                    |
| **Short-term (CPU) scheduler** | Only when CPU becomes idle, or a running process blocks/terminates/preempted | Chooses next process from **ready queue**; very frequent; ensures CPU stays busy |


---
#### Determining CPU Burst Length

CPU/IO cycle – many CPU bursts from the same proc
	• Keep track of their size and run a statistic....  
	• Then pick process with shortest predicted (statistic) next CPU burst  
Can be done by using the length of previous CPU bursts,  
	• E.g. using exponential averaging

1. $t_{n}$ = actual length of $n^{th}$ CPU burst
2. $T_{n+1}$ = predicted value for the next CPU burst
3. $\alpha, 0 \le \alpha \le 1$
4. Define : $T_{n+1} = \alpha t_{n} + (1 - \alpha)T_{n}$

Commonly $\alpha$ set to $\frac{1}{2}$. 


---
#### Scheduling Criteria

How we measure a “good” scheduling algorithm:
- **CPU Utilization:** Keep CPU as busy as possible.
- **Throughput:** Number of processes completed per unit time.
- **Turnaround Time:** Total time from submission to completion.
- **Waiting Time:** Total time a process spends in the ready queue.
- **Response Time:** Time from request submission until the first response (important for interactive systems).
- **Fairness:** Ensure no process starves.



---
#### Scheduling Algorithms

 **Non-preemptive:**
- **First-Come, First-Served (FCFS):**
    - Processes scheduled in order of arrival.
    - Simple, but can suffer from **convoy effect** (slow process delays others).

- **Shortest Job Next (SJN) / Shortest Job First (SJF):**
    - Process with the smallest CPU burst runs next.
    - Optimal for minimizing waiting time.
    - Requires knowing burst length in advance (not realistic).


**Preemptive (Process Scheduling Discipline):**
A **preemptive scheduling discipline** is one where the OS **can interrupt (preempt) a currently running process** in order to give the CPU to another process.

The decision to preempt depends on the discipline (the scheduling algorithm):
- **Shortest Remaining Time First (SRTF):**
    - Preemptive version of SJF.
    - If a new process has a shorter burst than remaining time of current process → preempt.

- **Round Robin (RR):**
    - Each process gets a small time quantum.
    - Good for time-sharing systems.
    - Performance depends on quantum size (too small = too many context switches, too large = FCFS).

- **Priority Scheduling:**
    - Each process assigned a priority. Highest priority runs first.
    - Can cause **starvation**; solved with **aging** (gradually increasing waiting process priority).

- **Multilevel Queue Scheduling:**
    - Separate queues for different classes of processes (foreground, background).
    - Each queue can have its own scheduling algorithm.

- **Multilevel Feedback Queue:**
    - Processes can move between queues based on behavior.
    - More flexible, used in many real OSes.

| **Aspect**                   | **Preemptive**                                                                                                                          | **Non-Preemptive**                                                                              |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Definition**               | OS can interrupt a running process and switch to another if scheduling rules demand it                                                  | Once a process gets the CPU, it keeps it until completion or it blocks voluntarily              |
| **Control**                  | CPU allocation decided dynamically by the scheduler                                                                                     | CPU allocation decided only at process arrival or completion                                    |
| **Response to new arrivals** | New process can immediately preempt if it has higher priority/shorter time                                                              | New arrivals must wait until the current process finishes                                       |
| **Examples**                 | - Round Robin (quantum expiration)- Shortest Remaining Time First (SRTF)- Preemptive Priority Scheduling- Earliest Deadline First (EDF) | - First-Come, First-Served (FCFS)- Shortest Job First (SJF)- Non-preemptive Priority Scheduling |
| **Overhead**                 | Higher (context switches, preemption handling)                                                                                          | Lower (fewer context switches)                                                                  |
| **Fairness**                 | More fair for interactive/short processes                                                                                               | Long jobs may cause short jobs to starve (convoy effect)                                        |
| **Use Cases**                | Time-sharing systems, interactive environments, real-time systems                                                                       | Batch systems, simpler embedded systems                                                         |



---
#### Multi-Processor Scheduling

- **Types of systems:**
    - **Asymmetric multiprocessing:** One master processor schedules, others execute.
    - **Symmetric multiprocessing (SMP):** Each processor is self-scheduling from a common ready queue.

- **Issues:**
    - Load balancing: Keep all processors busy.
    - Processor affinity: 
	    - Soft Affinity: the operating system attempts to keep a thread running on the same processor, but no guarantees.
	    - Hard Affinity: Keep a process on the same CPU for cache efficiency.
    - Push migration: Periodic task checks load on each processor, and if found pushes task from overloaded CPU to other CPUs
    - Pull migration: Idle processors pulls waiting task from busy processor


---
#### Real-Time CPU Scheduling

Used in systems where tasks must meet deadlines.

**Types of real-time systems:**
    - **Hard real-time:** Must meet deadlines (e.g., flight control).
    - **Soft real-time:** Deadlines preferred but not mandatory (e.g., video streaming).

**Scheduling policies:**
    - **Rate-monotonic:** Static priorities based on frequency (shorter periods = higher priority).
    - **Earliest Deadline First (EDF):** Dynamic priorities; process with closest deadline runs first.

**Event Latency**
- **Definition:** The time between when an event occurs and when it is serviced.
- **Two main types:**
    1. **Interrupt latency** → Time from interrupt arrival to the start of the interrupt service routine (ISR).
    2. **Dispatch latency** → Time it takes the scheduler to stop the current process and start another.




---
#### Algorithm Evaluation

Ways to compare scheduling algorithms:
- **Deterministic modeling:** Simple, uses specific workload examples.
- **Queuing models:** Mathematical modeling of arrivals, service times, and queues.
- **Simulation:** Model real workloads and run scheduling algorithms on them.
- **Implementation & measurement:** Run actual algorithms in OS and measure performance.


---
#### Summary

- CPU scheduling decides which ready process gets CPU.
- Evaluation criteria: utilization, throughput, turnaround, waiting, response, fairness.
- Algorithms: FCFS, SJF, SRTF, RR, Priority, Multilevel Queue, Multilevel Feedback.
- Multiprocessor scheduling needs load balancing & affinity handling.
- Real-time scheduling uses rate-monotonic and EDF.
- Evaluation methods: modelling, simulation, measurement.


| **Algorithm**                            | **Type**             | **How it Works**                                     | **Pros**                             | **Cons**                                                                    | **Use Cases**                                |
| ---------------------------------------- | -------------------- | ---------------------------------------------------- | ------------------------------------ | --------------------------------------------------------------------------- | -------------------------------------------- |
| **First-Come, First-Served (FCFS)**      | Non-preemptive       | Processes run in order of arrival                    | Simple, fair in order                | Convoy effect (long job delays short jobs)                                  | Batch systems                                |
| **Shortest Job First (SJF)**             | Non-preemptive       | Chooses process with shortest burst time             | Optimal for waiting time             | Requires knowing burst time; can starve long jobs                           | Batch jobs with predictable times            |
| **Shortest Remaining Time First (SRTF)** | Preemptive           | Always runs job with shortest remaining time         | Better average response than SJF     | Starvation possible; needs burst prediction                                 | Interactive systems                          |
| **Round Robin (RR)**                     | Preemptive           | Each process gets fixed time quantum                 | Fair, good response for time-sharing | Performance depends on quantum size; too small = overhead, too large = FCFS | Time-sharing OS, general purpose             |
| **Priority Scheduling**                  | Both                 | Highest priority process runs first                  | Flexible, can favor critical tasks   | Starvation possible (low-priority tasks never run)                          | Systems needing prioritization               |
| **Multilevel Queue**                     | Both                 | Separate queues for different process classes        | Organizes jobs by type               | Rigid, fixed queue priorities                                               | Foreground vs. background tasks              |
| **Multilevel Feedback Queue**            | Preemptive           | Processes move between queues based on behavior      | Flexible, adapts to process needs    | Complex to tune                                                             | General-purpose OS (Windows, Linux)          |
| **Rate Monotonic Scheduling (RMS)**      | Real-time (static)   | Fixed priority: shorter period = higher priority     | Easy to implement, widely used       | Can miss deadlines if CPU over-utilized                                     | Hard/soft real-time periodic tasks           |
| **Earliest Deadline First (EDF)**        | Real-time (dynamic)  | Process with earliest deadline gets highest priority | Optimal for meeting deadlines        | More overhead (dynamic priority changes)                                    | Hard real-time systems with strict deadlines |
| **Proportional Share (Fair Share)**      | Real-time / Fairness | Each process gets fixed CPU share (N/T)              | Ensures fairness                     | May not meet strict deadlines                                               | Multimedia, server load balancing            |

**Average Wait Time Example :**
Process | Burst Time  
P1                 24  
P2                  3  
P3                  3  

Suppose that the processes arrive in the order: P1 , P2 , P3
The Gantt Chart for the schedule is:
![[Screenshot 2025-10-15 at 9.42.54 AM.png]]

Waiting time for P1 = 0; P2 = 24; P3 = 27  
Average waiting time: (0 + 24 + 27)/3 = 17