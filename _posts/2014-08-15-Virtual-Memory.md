---
title: Virtual Memory of computer
date: 2014-08-15 12:16:00
categories:
- Programming

tags:
- programming
- memory
- virtual memory

---

### Virtual Memory
- CPU accesses main memory by generating a virtual address which is converted to the appropriate physical address before being sent to the memory. 
	- *address translation*: convert the virtual address to an appropriate physical address
- Virtual memory is partitioned into fixed-sized blocks called virtual pages. Similarly , physical memory is partitioned into physical pages. 
- The set of virtual pages is partitioned into three disjoint subset:
	- `unallocated`: Pages that have not yet been allocated
	- `cached`: allocated pages that are currently cached in physical memory
	- `uncached`: allocated pages that are not cached in physical memory
- Page table
	- Page table maps virtual pages to physical pages
	- Operating system provides a separate page table for each process
	- Every process on a given linux system starts at virtual address 0x400000(64bit) 
	- Address translation is a mapping between the elements of an N-element virtual address space and an M-element physical address space
	- A control register in the CPU points to the current page table 
	- The n-bit virtual address has two components: a `p-bit` virtual page offset and an `n-p` bit virtual page number(VPN). The MMU uses the VPN to select the appropriate PTE. 
	- The corresponding physical address is the concatenation of the physical page number from the page table entry and the VPO from the virtual address. 
	- Translation lookaside buffer (TLB): a small virtually addressed cache where each line holds a block consisting a single PTE.  
- Important capabilities for virtual memory system:
	- automatically caches recently used contents of virtual address space stored on disk in main memory
	- simplifies memory management
	- simplifies memory protection by incorporating protection bits into every page table entry
	- most programs rely on a dynamic memory allocator such as malloc, which manages memory in an area of the virtual address space called the heap. 
