---
title: Exception Control Flow
date: 2014-08-15 12:16:00
categories:
- Notes

tags:
- programming

---

### How does OS control exception?
- Each type of possible exception in a system is assigned a unique nonnegative integer exception number. 
- At run time, the processor detects that an event has occurred and determines the corresponding exception number. 
- **Interrupts**: result from signals from I/O devices that are external to the processor.
- **Traps and system calls**: occur as a result of executing an instruction. User program often need to request services from the kernel: read a file, create a new process, terminate current process etc. A system call runs in kernel mode, allowing it to execute instructions and accesses a stack defined in the kernel. 
- **Faults**: When a fault occurs, the processor transfer control to the fault handler. For example, page fault exception occurs when an instruction references a virtual address whose corresponding physical page is not resident in memory and must therefore be retrieved from disk. The page fault handler loads the appropriate page from disk and then returns control to the instruction that caused the fault. 
- **Aborts**: result from unrecoverable fatal errors.  
