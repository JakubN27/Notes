A deadlock occurs when a set of processes are blocked, each waiting for a resource held by another process in the set.

The conditions for a deadlock are: 
- Mutual Exclusion: Only one process can use a resource at a time.
- Hold and Wait: A process holds resources while waiting for others.
- No Preemption: Resources cannot be forcibly taken from a process.
- Circular Wait: A cycle exists in the resource-waiting graph (e.g., P1 waits for P2, P2 waits for P1)

# Resource Allocation Graphs
- Vertices: Processes(P) and resources (R)
- Edges:
	- Request edge (P -> R): Process is waiting for a resource. Resources can have multiple instances which can be accessed by more than one process.
	- Assignment edge (R -> P): Resource is allocated to a process.
- Deadlock Detection:
	- Cycle with single-instance resources implies a deadlock
	- Cycle with multi-instance resources implies a possible deadlock.

# Deadlock Handling Approaches
1. Ostrich Algorithm: Ignore deadlocks (used in UNIX/Windows for rare cases).
2. Prevention: Break one of the four conditions (e.g., enforce resource ordering to avoid circular waits. Hold and Wait requires process to request and be allocated all its resources before it begins execution, or allow process to request resources only when the process has none allocated to it. This uses low resources but starvation is possible.
3. Avoidance: Use algorithms to ensure the system never enters such an unsafe state.
	1. Banker's Algorithm: Checks for safe sequences before allocating resources. Safe state is when there exists a sequence P1, P2, ... ,Pn of ALL the processes in the systems such that for each Pi, the resources it can request can be satisfied by currently available resources + resources held by all the Pj with j<i.
4. Detection and Recovery:
	1. Terminate processes or preempt resources to break deadlocks.
5. Bankers algorithm:
	1. Avoids deadlocks by ensuring safe resource allocation.
	2. Max: maximum resources a process may request.
	3. Allocation: Currently assigned resources.
	4. Need: remaining resources required (max - allocation)
	5. Safety check: finds a sequence where all processes can complete without deadlock
6. Deadlock recovery:
	1. Process termination: kill deadlocked procedures (lowest priority first)
	2. Resource preemption: roll back processes to release resources (may cause starvation)

