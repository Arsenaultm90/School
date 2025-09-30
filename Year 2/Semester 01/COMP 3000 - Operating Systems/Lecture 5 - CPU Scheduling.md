#### Basic Concepts

- **CPU–I/O Burst Cycle**
    - Programs alternate between CPU bursts (computation) and I/O bursts (waiting for input/output).
- **Scheduler’s role:** Decide which process gets the CPU when multiple are ready.
- **Dispatcher:** Gives control of CPU to the process chosen by the scheduler (context switch).

**Types of schedulers:**
- **Long-term:** Selects jobs to enter system (controls degree of multiprogramming).
- **Medium-term:** Suspends/resumes processes to optimize performance.
- **Short-term (CPU scheduling):** Chooses from the ready queue which process runs next.


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


**Preemptive:**
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