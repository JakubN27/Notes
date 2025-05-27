An operating system is a program that acts as an intermediary between a user and the hardware.
It acts as a resource allocator, control program and a kernel (the one program that runs all the time).

Multi programming is needed for efficiency, since a single user cannot keep CPU and I/O devices busy at all times. Multiprogramming organises jobs (code and data) so CPU always has one to execute. A subset of total jobs in system is kept in memory. One job selected and run via job scheduling and when it has to wait (for I/O for example), OS switches to another job.

CLI or command interpreter allows direct command entry. Sometimes implemented in kerne, sometimes by systems program. Someones multiple flavours implemented (shells). It primarily fetches a command from user and executes it. Sometimes command are built in and sometimes they are just names of programs.

# Process
A program in execution is called a PROCESS. An operating system executes a variety of programs. Batch system - jobs. Time-shared systems - user programs or tasks. Resources needed by the process include: CPOU time, memory files, and I/O devices.

The operating system is responsible for process management including:
- Process creating and deletion
- Process holding and resuming
- Mechanisms for process synchronisation (via priority, scheduling).
A process includes: 
- Code: text section
- Current activity, represented by the program, counter and the content of the CPUs registers.
- Stack: temporary data such as local variables
- Data section: Global variables
- Heaps: memory allocated while the process is running.

Process control block (PCB) holds information about a process. A collection of PCBs form a process table

Information in a PCB includes:
- Unique identifier e.g. PID
- State (~ status)
- CPU registers
- CPU scheduling information e.g. priority
- Memory usage
- Other information: Accounting, I/O status

As the process executes it changes state (~status):
- New - the process is being created
- Running - instructions are being executed
- Waiting - the process is waiting for some event to occur
- Ready - the process is ready to be dispatched to the CPU
- Terminated - the process has completed its execution or some other event causing termination.

## Process Creation
A new process, as a parent process can create a number of child processes which in turn create other processes, forming a tree of processes. Generally, process identifies and managed via a process identifier (pid).

Resource sharing: three possible cases: 
- The parent and child processes share all resources.
- The child process shares a subset of parents resources.
- The parent and child processes share no resources.
Execution: two possible cases:
- The parent and child execute concurrently
- The parent waits until child terminates.


