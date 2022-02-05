# class 2 1/28/22

### Cache and main memory

#### Aspects of cache
- maping function 
- replacement 
- block size and cache size
- read and write policy

#### Cache and main memory
- cache has multiple levels
- the more you increase the level of caches the more you increase the complexity of the architecture
- cache levels have different access times.
- hard disks also have cache in order to secrease time searching. Most relevant information is stored.
- Cache can maximum be 1/3 of the main memrory
- memory stored in blocks are relevant to each other.
- if first block doesnt contain all relevant to data the next block must contain it.
- maping function
- fifo and lifo are some of the algorithms used for replacement.
- decrease block size increases search time and increase relavent information per block
- Only OS kernel is loaded into the main memory

### Interupts
- if more than one iterupt arrives at the same time  then priority must be assesed.
- highest priority interupt is system shutdown aside from kernel

#### ways of handeling interupts
- disable interupts
- define priorities
- Interupt - disturbance to the normal execution of the cpu

#### Types of Interupts
- Program interupts - division by zero, array out of bounds ... logical errors
- Timer interupts - timer within the processor allowing 
- IO Interupts - keyboards are an example that interupt when keys are pushed.
- Hardware failure - 

### Types fo computers

#### Multicore Processors
- multiple processors on a single chip. all work together for a single process.

#### Super Computers
- multiple process inorder to make calculation
- symmetric multiprocessors
- 2 or more similar processes
- Advantages - performance, availability, scalling

### Techniques for IO Operations
- Programmed IO technique
- Interupt driven IO technique - will not interupt the processor
- Direct Memory Access Technique - 
