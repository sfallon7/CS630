# Chapter 2

## Quiz Questions 
- bankers algorithm
- PCB the significant point about PCB is that it contains sufficient information so that it is possible to interupt a running process and later resune execution as if the interuption had not occured.  When a process is interiupted the current values of the program counter are saved in the appropriate fields of the PCB and the state of the process is changed to something else.

Processors that are not running must be kept in some sort of a queue waiting for them to execute. In the 2 state model this is called ready state.  If the process is completed it is discarded and the dispatcher takes another from the queue for execution.

## What is an operating system
- a computer is a set of applications 
- applications that are being used are stored in main memory and brought into cache and registers
- operating system is an INTERFACE between io devices and user applications

## What is a bios?
- basic io system
- kernel is the smallest part of the kernel


| Applications |
| Libraries |
| OS |
| Bios/System Hardware |
| Buses |
| IO Devices | Memory |

When you start the OS only the kernel is needed to load the bios

## How have OS's evolved
1 Serial processing
2 Batch processing
3 Batch multiprogramming 
- multiple jobs 

## Functions
1 Process management
- - FCFS
- - SJF
- - Round Robin
- - Priority

2 IO Management
- - 

3 Memory Management
- - segmentation
- - static partition
- - dynamic partition
- - paging

Resource Management
- - deadlock
- - starvation

Information Security and Privacy
- - hash functions are ireversable functions
- - f(password) -> x

Fault Tolerance
- - temporary faults from which the system can recover from
- - permanant faults degrade the system without human intervention

# Chapter 2 Practice questions
Q. No. 1)
Three programs, Job 1, Job 2 and Job 3 are submitted for execution at the same time. For a simple batch 
Uni-programming environment, these jobs will be executed in a sequence i.e. Job 1 then Job 2 and then 
Job 3. It is noted that Job 1 completes in 5 minutes, Job 2 completes in 15 minutes and Job 3 completes in 
10 minutes from the time they start execution. 

job1 = 5 mins
job2 = 15 mins
job3 = 10 mins

Throughput = 6 jobs/hour

Mean response time = time required for the process to give its first output/response

Uni-programming
R1 = 5 mins
R2 = 20 mins
R3 = 30 mins

(5 + 20 + 30)/3 = 18.33 mins

Multi-programming
Throughput = 12 jobs/hour
Mean response time 
R1 = 5 mins
R2 = 15 mins
R3 = 10 mins

10 minutes

# Chapter 3: Process Description & Control
- A program in execution is a process
- - can be on the cpu or io device

- IO bound  and CPU bound
- - majority of the time is run by IO or CPU

-  Every process has 2 parts
| process |
| program code | Context Data | 

- PID - every process has a unique PID
- Process Control Block (PCB)
| Process ID |
| State |
| Priority |
| Program Counter |
| Memory Pointers |
| Context Data |
| IO Status Information |
| Accounting Information |

System and PCB both have a program (PC)

## 2 state model 
- process is either running or not runnning
- any process entering the system enters a queue and enters a not running state until it is dispatched from the queue and it switches to the running state
- dispatcher sends from running to not running
- pause sends it from running to not running and process enters the queue again.
(runnning) -dispactch-> (running) -> exit
(runnning) <-pause- (running) -> exit

Processors that are not running must be kept in some sort of a queue waiting for them to execute. In the 2 state model this is called ready state.  If the process is completed it is discarded and the dispatcher takes another from the queue for execution.