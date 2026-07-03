text file --> **preprocessor**, which makes modifications according to # directives --> **compiler**, which outputs assembly language --> **assembler**, which translates this into machine code that is gibberish to us in movable executable files --> **linker**, puts executable files together to run 

process vs. thread
- a process is simply an **abstraction** over a program's access to and control over processor cores, virtual memory, and I/O devices. a process does not get scheduled to run, it is a container
- a thread lives within a process potentially alongside other threads, and is actually scheduled and **executed**. it shares memory and processor core with other threads, keeping only its own register set, stack, and program counter. this makes context switching very easy between threads, but risks data pollution

virtual memory
- an abstraction over main memory and I/O-contained memory that provides a contiguous address space to processes. managed by the OS to efficiently combine the benefits of caches with disk memory
- does not include caches as part of its abstraction