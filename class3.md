# Class 3 2/4/2022

## Instruction Cycle
- Instruction cycle aka, fetch-decode-execute cycle
each hexadecimal has a 4 digit binary equivalent number
- data is first brought to mbr and then copied to other registers

=

### Problem 1
Illustrate a partial program execution mechanism showing the contents of memory and processor registers at each step in a hexadecimal format. The program fragment should add the contents of the memory words which are present at address 940 and 941 and obly the final result has to be stored back to memory. Show all the instruction cycles in detail each consisting of a fetch stage and an execute stage. Note that all the values are in hexadecimal format.

The list of opcodes is as follows:
0101 = Add to AC from memory
0010 = Store AC to memory
0001 = Load AC from memory

#### Step 1 Fetch
##### Memory
| Address | Memory Contents |
| ------ | ------ |
| 300 | 1940 |
| 301 | 5941 |
| 302 | 2941 |
| ... | ... |
| 940 | 1A3B |
| 941 | 108A |

##### CPU Registers
| Register Contents | Register |
| ------ | ------ |
| 300 | PC |
|  | AC |
| 1940 | IR |
| 300 | MAR |
| 1940 | MBR |

#### Step 2 Execute
##### Memory
| Address | Memory Contents |
| ------ | ------ |
| 300 | 1940 |
| 301 | 5941 |
| 302 | 2941 |
| ... | |
| 940 | 1A3B |
| 941 | 108A |

##### CPU Registers
| Register Contents | Register |
| ------ | ------ |
| 301 | PC |
| 1A3B | AC |
| 1940 | IR |
| 940 | MAR |
| 1A3B | MBR |

#### Step 3: Fetch
##### Memory
| Address | Memory Contents |
| ------ | ------ |
| 300 | 1940 |
| 301 | 5941 |
| 302 | 2941 |
| ... | |
| 940 | 1A3B |
| 941 | 108A |

##### CPU Registers
| Register Contents | Register |
| ------ | ------ |
| 301 | PC |
| 1A3B | AC |
| 5941 | IR |
| 301 | MAR |
| 5941 | MBR |

#### Step 4: Execute
##### Memory
| Address | Memory Contents |
| ------ | ------ |
| 300 | 1940 |
| 301 | 5941 |
| 302 | 2941 |
| ... | |
| 940 | 1A3B |
| 941 | 108A |

##### CPU Registers
| Register Contents | Register |
| ------ | ------ |
| 302 | PC |
| 2AC5 | AC |
| 5941 | IR |
| 941 | MAR |
| 108A | MBR |

#### Step 5: Fetch
##### Memory
| Address | Memory Contents |
| ------ | ------ |
| 300 | 1940 |
| 301 | 5941 |
| 302 | 2941 |
| ... | |
| 940 | 1A3B |
| 941 | 108A |

##### CPU Registers
| Register Contents | Register |
| ------ | ------ |
| 302 | PC |
| 2AC5 | AC |
| 2941 | IR |
| 302 | MAR |
| 2941 | MBR |

#### Step 6: Execute
##### Memory
| Address | Memory Contents |
| ------ | ------ |
| 300 | 1940 |
| 301 | 5941 |
| 302 | 2941 |
| ... | |
| 940 | 1A3B |
| 941 | 108A |

##### CPU Registers
| Register Contents | Register |
| ------ | ------ |
| 303 | PC |
| 2AC5 | AC |
| 2941 | IR |
|  | MAR |
|  | MBR |


- Learn addition and substraction for hexadecimal
- not multiplaction and division
- should be able to solve problem in 10 minutes





### Q1
Suppose the processor has access to 2 levels of memory. Level 1 contains 1000 bytes of memory and has an  average  access  time  of  0.1 microseconds,  level  2  has  an  average access time  of  1  microsecond  and contains 100,000 bytes. Assume that if a byte to be accessed is in level 1, then the processor accesses it directly If it is in level 2, the byte is first transferred to level 1 and then accessed by the processor. Ignore the time required for the processor to determine whether the byte is in level 1 or level 2. 
If 95% of the memory accesses are found in the level 1, calculate the average effective time of the system to access a byte.

#### A1
<- L1 <- L2
Probabilty/Hit Ration that the word is in L1 = 95/100 = 0.95
Probabilty/Hit Ration that the word is in L2 = 5/100 = 0.05

Average access time = 
(hit ration of first memory * time )
\+ (hit ration of first memory * time )
= (0.95*0.1) + (0.05*(1+0.1)) 
** = 0.15 microseconds **

1 minute = 60 seconds
1 second = 1000 miliseconds
1 milisecond = 1000 microseconds

### Q2
A computer has a cache, main memory and a disk used for virtual memory. If a referenced word is in the cache, 20 ns are required to access it. If it is main memory but not in cache, 60 ns are needed to load it into the cache, then the reference is started again. If the word is not in main memory, 12 ns are required to fetch the word from disk, followed by 60 ns to copy it to the cache, then the reference is started again. 
Also, if the word is not found in the cache or main memory then it has to compulsorily be present in the disk. The cache hit ratio is 0.9 and the main memory hit ratio is 0.6. What is the average time in ns required to access a referenced word on this system.

#### A2
cache <- main <- memory <- disk

P(cache) = 0.9
P(not cache) = 0.1
P(main memory) = 0.6
P(not main memory) = 0.4

p(cache)\*time + p(not cache\*main memory)\*time + p(not cache \*not main memory \* disk)\*time

(0.9\*20) + (0.1\*0.6)(60+20) + (0.1\*0.4\*1)(60+20+12)

### Q3
Consider a computer system with the following memory access time specifications:                 
Tc = 100 ns
Tm = 1200 ns
where Tc and Tm are the cache memory and main memory access times respectively.
If the effective access time is 110 ns, what is the hit ratio ‘H’?

#### A3
cache <- main
Effective access time = 
(Hit ration of M1 * T1)
\+ (Hit ratio of M2 * T2)

110 = H \*(100) + (1-H)\*(1200+100)
H = 0.9916

### Q4
Consider a hypothetical microprocessor generating a 16-bit address and having a 16-bit data bus.
a) What is the maximum memory address space that the processor can access directly if it is connected to a 16-bit memory?
b) What is the maximum memory address space that the processor can access directly if it is connected 
to an 8-bit memory?
c) What is the maximum no. of memory locations that the processor can access?

#### A4
Addresses bus = 16 bits and Data bus = 16 bits

| Address | Data/Instructions |
| ------ | ------ |
|   | 16 bits |
|   |   |
|   |   |

Since it is 16 bit, then there are 2^16 number of different addresses, that means we have 2^16 different locations in memory

1 byte = 8 bits = 2^3 bits
1 KB = 1024 bytes
1 MB = 1024 KB
1 Kb = 1024 bits
1 Mb = 1024 Kb

a) Maximum memory address space 
= 16 \* 2^16 bits
= 2^4 \* 2^16 bits
= 2^20 bits
= 2^20/2^3 bits
= 2^17 bytes
= 2^17/2^10
= 128 KB

b) Maximum memory address space = 8\*2^16=2^3=2^16
= 8\*2^16
= 2^3bytes 
= 2^16 bytes 
= 2^16/2^10 KB 
= 64 KB

c) Since it is a 16 bit address, we have 2^16 different addresses, that means we have 2^16 different locations in memory which can be accessed.

### Q5
Consider a 32-bit microprocessor, with a 16-bit external data bus, driven by an 8-MHz input clock. 
Assume that this microprocessor has a bus cycle whose minimum duration equals 4-input clock cycles. 
What is the maximum data transfer rate (in bytes/sec) across the bus that this microprocessor can sustain?

#### A5
Data bus = 16 bits
Input clock = 8 MHz = 8\*10^6 Hz
1 Bus cycle = 4 clock cycles

Frequency = 1/T
T = 1/frequency
T = 1/8\*10^6 Hz
T = 0.125\*10^-6 seconds

1 Bus cycle = 4 \* input clock cycles
            = 4\*0.125\*10^-6 seconds 
            = 0.5\*10^-6 seconds

Maximum Data Transfer Rate  = Amount of datatransferred/time taken
                            = 16 bits/0.5\*10^-6 seconds
                            = 2 bytes/0.5\*10^-6 seconds
                            = 4\*10^6 bytes/second

### Q6
Consider a memory system with the following parameters:
Cc=0.01 cents/bit
Cm=0.001 cents/bit
a) What is the cost of 1 Mbyte of main memory?
b) What is the cost of 1 Mbyte of cache memory?

#### A6
1 Mbyte = 1024 KB
        = 1024 \* 1024 Bytes
        = 1024 \* 1024 \* 8 8388608 bits

Cost of 1 MB of main memory = 8388608\*0.001=8388.608 cents

### Q7
A multiprocessor with 8 processors has 20 attached tape drives. There is a large no. of jobs submitted to the system that each require a maximum of 4 tape drives to complete execution. Assume each job starts running with only 3 tape drives for a long period before requiring the 4th tape drive for a short  period towards the end of its operation. Also assume an endless supply of such jobs.

a) Assume the scheduler in the OS will not start a job unless there are 4 tape drives available. When a job is started, 4 drives are assigned immediately and are not released until the job finishes. What is the maximum no. of jobs that can be progress at once? What are the maximum and minimum no. of tape drives that may be left idle as a result of this policy?

b) Suggest an alternative policy to improve tape drive utilization. What is the maximum no. of jobs that can be in progress at once? What are the bounds on the no. of tape drives that are idle?

#### A7
a)  tape drives = 20
    jops = 4 tape drive
    job start = 3 tape drives
    job end = 4 tape drives
    max jobs = 20/4 = 5 jobs
    Maximum no of tapes idle = 5
    Minimum no of tapes idle = 0 

b)  Only require 3 tapes per job to start a job and then set a priority to free tapes drives to finish jobs that are ready to end.

Maximum No. of jobs = 20/3 = 6 jobs
Maximum No of tape drives idle = 2
Minimum no. of tape drives idle = 0

### Q8
A DMA module reads a record from a file and gives it to the processor in 15 microseconds. The processor on an average takes 1 microsecond to execute 100 machine instructions per record and then takes another 15 microseconds to write the record back to the file. Assume that the processor is idle when the 
DMA module reads and writes a record to/from a file. Calculate the percentage of CPU utilization. Has the CPU been utilized efficiently?

reading = 15 microseconds
writing = 15 microseconds
execution = 1 microsecond

utilization = \[1/(15+1+15)\]\*100
            = 3.2258% of CPU utilization
The CPU has to have a more than 90% utilization to be efficient. Instead it is idle more than 96% of the time.
