---
title: Linker
date: 2014-08-15 11:16:00
categories:
- Notes

tags:
- programming

---

### How does a linker work?
- `Relocatable object file`: contains binary code and data in a form that can be combined with other relocatable files at compile time to create an executable object file
	- `.text`: the machine code of the compiled program
	- `.rodata`: read-only data such as the format string in the printf statement
	- `.data`: initialized global C variable
	- `.bss`: uninitialized global C variable. It’s merely a placeholder. 
	- `.symtab`: A symbol table with information about functions and global variables. 
	- `.rel.text`: a list of locations in the .text section that will need to be modified when the linker combines this object file with others
	- `.rel.data`: relocation information for any global variables that are referenced or defined by the module
	- `.debug`: It’s only present if the compiler driver is invoked with `-g` option 
	- `.line`: A mapping between line numbers in the original C source program and machine code instructions in the `.text` section
	- `.strtab`: a string table for the symbol tables in the `.symtab` and `.debug` sections. 
	- *local procedure variables* that are defined with C static attribute are not managed on stack. 

- `Executable object file`: contains binary code and data in a form that can be copied directly into memory and executed
- `Shared object file`: a special type of relocatable object file that can be loaded into memory and linked dynamically
- `Shared library`:  an object module that can be loaded at an arbitrary memory address and linked with a program in memory. 
- `Position-Independent Code`: A key purpose of shared libraries is to allow multiple running processes to share the same library code in memory. We can assign a priori a dedicated chunk of the address space to each shared library, and then require the loader to always load the shared library at that address. A better approach is to compile library code so that it can be loaded and executed at any address without being modified by the linker. 
- No matter where we load an object module in memory, the distance between any instruction in the code segment and any variable in the data segment is a run-time constant. Thus, the compiler creates a table called the `global offset table` at the beginning of the data segment. 
