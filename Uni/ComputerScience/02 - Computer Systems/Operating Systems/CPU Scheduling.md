CPU scheduling can be viewed as processes taking turns. It provides a basis of a fair and efficient sharing of system, in this case CPU, resources. As the CPU is a primary computer resource, scheduling is fundamental to operating system design.

# Schedulers
An OS operates three types of scheduler: long-term, medium-term, and short-term (CPU):
The long term scheduler (job scheduler) selects which processes should be brought into the ready queue.
The medium term scheduler is a part of swapping and in charge of handling the swapped out processes.
The short term scheduler (CPU schedule) selects the process to be executed next and allocated to the CPU. E.g. Switch from ready to running state or from running or ready state, or from waiting to ready.

# Dispatcher
Module that gives control of the CPU to the Process selected by the CPU scheduler. Functions involved are:
- Switching content - context switch-time is an overhead: the system undertakes no user processing while switching.
- Switching to user mode
- Jumping to proper location in the user program to restart the program.
Dispatch Latency - Time it takes for the Dispatcher to Stop one process and start another running.

# Scheduling Criteria
- CPU utilisation: keep the CPU busy (max)
- Throughput: number of processes that complete their execution per unit of time. (max)
- Turnaround time: amount of time to execute a particular process (waiting + execute + I/O) (min)
- Waiting time: total amount of time a process has been waiting in the ready queue (min)
- Response time: amount of time it takes from when a request was submitted until the first response (access to the CPU). Not the time to complete the process.(min)

# Scheduling Algorithms
## First come first served (FCFS)
First process to request the CPU is allocated the CPU until it is completed. Simple to implement, but can result in a convoy effect where short processes wait on a long process to finish.

## Shortest job first (SJF)
Associate with each process the length of its next CPU burst. Use these lengths to schedule the shortest time. If two have the same time then FCFS. It is non pre-emptive meaning that once the CPU is given to the process it cannot be pre-empted until the process has completed its CPU burst.

## Shortest Remaining Time First (SRTF)
If a new process arrives in the ready queue with a CPU burst length less than the remaining time of the executing process then pre-empt the running process and run the process with the shorter CPU burst length.

## Round Robin
Each process gets a small unit of CPU time: a time quantum or time slice usually q = 10 to 100 milliseconds. After this time has elapsed, the process is pre-empted and added to the end of the ready queue. If there are n processes in the ready queue and the time quantum is q then each process gets 1/n of the CPU time in chunks at most q time units at once.

Performance of the RR algorithm depends heavily on the size of the time quantum. If the time quantum is extremely large, the RR policy is the same as the FCFS policy. If the time quantum is extremely small, the RR approach can result in a large number of context switches. So, the time quantum should be large compared with the context-switch time but not too large. As a rule of thumb, 80 perfect of the CPU burst should be shorter than the time quantum, so it only splits up the really heavy tasks.

## Priority scheduling
In priority scheduling, the algorithm associates a priority number (integer) for each process. The CPU is allocated by the dispatcher to the process with the highest priority (smallest itneger = highest priority or otherwise). Priority based CPU scheduling can be either pre-emptive for non pre-emptive. 

A problem that this can cause is Starvation (also knowsn as indefinite blocking) where low priority processes may never execute as new ones arrive. A solution to this is ageing, meaning as time progresses the priority of the task will increase. Combining RR with priority executes the highest priority processes and runs processes with the same priority using round-robin scheduling.

## Multilevel queue
The ready queue is partitioned into separate queues (e.g. foreground (interactive) and background (batch)). Each queue has its own scheduling algorithm and scheduling must be undertaken between the queue e.g serve all from foreground then all from background or allocated time slices between each queue.

Problem: provides differentiation but not flexible, since a process remains in the same queue regardless of adapting requirements.

## Multilevel Feedback queue
Feedback queues are an adaptation of multilevel queue scheduling. A process can move between the various queues ; aging can be implemented this way. Multilevel feedback queue scheduler is defined by the following paremeters:
- number of queues
- scheduling algorithms for each queue
- method used to determine when to upgrade / demote a process
- method used to determine which queue a process will enter when that process needs service.
Windows and MacOS use MLFQs

# Algorithm Evaluation
## Deterministic modelling
Take a predetermined workload (case) and analyse the performance of each algorithm. 

# Queueing Models
Queuing network analysis. Little's formula: n = $\lambda$ x W where n is the average long term queue length, W is the average waiting time in queue and $\lambda$ is the average arrival rate for new processes in the queue. E.g. if 7 processes arrive every second on average and normally 14 processes in the queue, then the average waiting time per process is 2 seconds.

## Simulation
Complex model of the system and the way it is used. Beware of Bonini's paradox

## Post-implementation
Examine the running operating system (a.k.a 'live' testing)
