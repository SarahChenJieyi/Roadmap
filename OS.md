# Operating System
## Management of processes

### Processes and threads 
A process is a unit of resources, while a thread is a unit of scheduling and execution.  
At the kernel level, a process contains one or more kernel threads, which share the process's resources, such as memory and file handles. 

Threads vs processes:
1. processes are typically independent, while threads exist as subsets of a process. 
2. processes carry considerably more state information than threads, whereas multiple threads within a process share process state as well as memory and other resources. 
3. processes have separate address spaces, whereas threads share their address space.
4. processes interact only through system-provided inter-process communication mechanisms.
5. context switching between threads in the same process typically occurs faster than context switching between processes. 

### Process states
![image](https://user-images.githubusercontent.com/52988403/197447189-7b7e6a2d-71b0-4dd9-91ba-7503410de2f0.png)
- ready (waiting)
- running
- blocked  

What you need to pay attention:  
- Only "ready" and "running" can be switching between each other, the others can only change from one to another.
- Only "ready" and "running" can be switching between each other, the others can only change from one to another.
- A "ready" process is awaiting execution on a CPU which is determined by computer scheduling. 
- A blocked state transitions from a running state due to a lack of needed resources, but this resource does not include CPU time, which is converted from a running state to a ready state

### CPU Scheduling(调度算法)
1. First come, first served (FCFS)  
Throughput can be low, because long processes can be holding the CPU, causing the short processes to wait for a long time (known as the convoy effect).  
2. Shortest job first (SJF).   
It has the potential for process starvation for processes which will require a long time to complete if short processes are continually added.  
SJN is a non-preemptive(非抢占式) algorithm. Shortest remaining time is a preemptive variant of SJN.
3. Shortest remaining time first(SRTF)  
If a shorter process arrives during another process' execution, the currently running process is interrupted (known as preemption), dividing that process into two separate computing blocks. 
4. Round-robin scheduling(时间片轮转)  
The scheduler assigns a fixed time unit per process, and cycles through them. If process completes within that time-slice it gets terminated otherwise it is rescheduled after giving a chance to all other processes.
5. Fixed priority pre-emptive scheduling  
The operating system assigns a fixed priority rank to every process, run in order of their priority.  
To prevent the starvation of lower-priority processes, the system can gradually increments the priority of waiting processes and threads.  
6. Multilevel queue scheduling
A combination of Round-robin scheduling and fixed priority pre-emptive scheduling.
