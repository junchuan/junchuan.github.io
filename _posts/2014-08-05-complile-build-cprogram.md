---
title: Compile and build program using gcc
date: 2014-08-05 09:16:00
categories:
- Notes

tags:
- programming

---

### Four steps:
1. **preprocessing**: based on the `#`directives, modify the original C program. Usually, the result of this step is a `.i` file;
2. **compile**: translate `.i` file into `.s` file. Assembler provides different language and different platform with a common output;
3. **assembling**: assembles the program into machine command. The output file will be a `.o` file, which is a binary file;
4. [**link**]({% post_url 2014-08-15-Program-Linker %}) 

  

