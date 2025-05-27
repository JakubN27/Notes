# Disk Structure
Disks are organised into cylinders, tracks and sectors.
Performance Metrics:
- Seek Time: time to move the disk head to the target track.
- Rotational Latency: Time for the target sector to rotate under the head.
- Access Time = Seek Time + Rotational Latency.
- Transfer Time: Time to read/write data.

# Disk Scheduling
Algorithms with the goal of minimising seek time and improving disk bandwidth (total number of bytes transferred divided by the total time between the first request for service and completion of the last transfer).
- FCFS - simple but inefficient (high seek time)
- Shortest Seek Time First - Minimises seek time but may cause starvation.
- SCAN - Moves back and forth servicing requests along the way.
- C-SCAN - variant of SCAN which returns to the start without servicing requests.
- LOOK and CLOOKL Optimised versions of SCAN/C-SCAN that reverse direction after the last request.
## Storage Systems
- Storage Arrays: Controllers manage multiple disks, supporting RAID, hot spares, and shared storage. Simply attaches disks.
- Storage Area Network(SAN): High-speed network connecting multiple hosts to storage arrays.
- Network Attached Storage (NAS: Storage accessed over a network (e.g., NFS, CIFS, iSCSI).

## Redundant Array of Inexpensive Disks
Purpose: Improve performance and reliability through redundancy (data is stored in multiple disks ensuring data protection in case of a drive failure).
Levels:
- RAID 0: Striping (no redundancy, high performance).
- RAID 1: Mirroring (duplicate data, high reliability)
- RAID 3/4/5 Parity- based redundancy (balance of performance and fault tolerance).
- RAID 6: Dual parity (handles two disk failures)
- RAID 0+1 and 1+0: Nested configurations combining striping and mirroring.
