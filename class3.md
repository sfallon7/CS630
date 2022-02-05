# Class 3 2/4/2022

## Instruction Cycle
- Instruction cycle aka, fetch-decode-execute cycle
each hexadecimal has a 4 digit binary equivalent number
- data is first brought to mbr and then copied to other registers

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





### Q.1
Suppose the processor has access to 2 levels of memory. Level 1 contains 1000 bytes of memory and has an  average  access  time  of  0.1 microseconds,  level  2  has  an  average access time  of  1  microsecond  and contains 100,000 bytes. Assume that if a byte to be accessed is in level 1, then the processor accesses it directly If it is in level 2, the byte is first transferred to level 1 and then accessed by the processor. Ignore the time required for the processor to determine whether the byte is in level 1 or level 2. 
If 95% of the memory accesses are found in the level 1, calculate the average effective time of the system to access a byte.

#### A.1
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

### Q.2.
A computer has a cache, main memory and a disk used for virtual memory. If a referenced word is in the cache, 20 ns are required to access it. If it is main memory but not in cache, 60 ns are needed to load it into the cache, then the reference is started again. If the word is not in main memory, 12 ns are required to fetch the word from disk, followed by 60 ns to copy it to the cache, then the reference is started again. 
Also, if the word is not found in the cache or main memory then it has to compulsorily be present in the disk. The cache hit ratio is 0.9 and the main memory hit ratio is 0.6. What is the average time in ns required to access a referenced word on this system.

#### A.2
cache <- main <- memory <- disk

P(cache) = 0.9
P(not cache) = 0.1
P(main memory) = 0.6
P(not main memory) = 0.4

p(cache)*time + p(not cache*main memory)*time + p(not cache *not main memory * disk)*time
=
(0.9*20) + (0.1*0.6)(60+20) + (0.1*0.4*1)(60+20+12)

### Q.3.
Consider a computer system with the following memory access time specifications:                 
Tc = 100 ns
Tm = 1200 ns
where Tc and Tm are the cache memory and main memory access times respectively.
If the effective access time is 110 ns, what is the hit ratio ‘H’?

#### A.3
cache <- main
Effective access time = 
(Hit ration of M1 * T1)
\+ (Hit ratio of M2 * T2)
