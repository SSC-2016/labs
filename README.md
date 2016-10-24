# lab 5. 25-26 October - Format String Vulnerabilities

This week we will be building on our knowledge gained from the previous lab and attempt to do a `Return-to-libc` attack.

## Required Reading
- [SEED lab materials on format string vulnerabilities](http://www.cis.syr.edu/~wedu/seed/Labs/Vulnerability/Format_String/)
- [the class materials from weeks 3-5](http://staff.cs.upt.ro/~marius/curs/sec/index.html)
  - [SEED lab materials on buffer overflow](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Vulnerability/Buffer_Overflow/)
  - [SEED lab materials on Return-to-libc](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Vulnerability/Return_to_libc/)
- [gdb tutorial](https://www.youtube.com/watch?v=sCtY--xRUyI)
	- know what the gdb is
	- know how to use the gdb
	- [gdb cheat-sheet](http://darkdust.net/files/GDB%20Cheat%20Sheet.pdf)
- [functions and stack frames](https://en.wikibooks.org/wiki/X86_Disassembly/Functions_and_Stack_Frames)

## Additional Information 
- [program vulnerabilities] (http://blog.fkraiem.org/2013/10/08/exploiting-basic-vulnerabilities/)
   - [stack theory] (http://blog.fkraiem.org/2013/10/08/the-stack-theory/)
   - [stack practice] (http://blog.fkraiem.org/2013/10/08/the-stack-practice/)
   - [shellcodes] (http://blog.fkraiem.org/2013/10/09/shellcodes/)
   - [NOP slides] (http://blog.fkraiem.org/2013/10/25/nop-sleds/)
   - [return-to-libc] (http://blog.fkraiem.org/2013/10/26/return-to-libc/)

## Reminder - Security Talk (presentation)
- this is the final week for choosing a topic
- in week 6 topic list should already be final 

### What is needed to understand Buffer Overflow and Return-to-libc 
- Understanding C functions and the stack.
	- https://en.wikibooks.org/wiki/X86_Disassembly/Functions_and_Stack_Frames
	- http://www.cs.virginia.edu/~evans/cs216/guides/x86.html
- Some familiarity with machine code.
- Know how systems calls are made. 
- The exec() system call.
- Details vary slightly between CPU’s and OS:
  - Stack growth direction.
  - big endian vs. little endian.

### Lab tasks and checkpoints
Tuesday and Wednesday (08-10)
- tasks 1-2.4
	- write the report as lab4-student-name.txt
	- submit source code
- demonstrate the use of the gdb
- demonstrate knowledge of how the stack is working

### Example makefile to ease compilation
Save the following content into a file named `Makefile` (yes, with capital `M`) in your working folder containing your source code (in this example, the C file is named `main.c`)
```
main:	main.c
			gcc -o main -fno-stack-protector main.c

s:
			gcc -S -fno-stack-protector main.c


randoff:
			sudo sysctl -w kernel.randomize_va_space=0

randon:
			sudo sysctl -w kernel.randomize_va_space=1	
```

### Quizz

Please remember there will be a quizz at the start of this lab. Therefore, try to understand the core concepts.

On Tuesday and Wednesday morning, the quiz will be given in the first 10 minutes of the lab. 
Please make sure to make it on time. 

### Installing the Virtual Machine

You can even learn by practicing at home. In order to do that, [follow the instructions on how to set up your environment, and download the correct VM](https://github.com/SSC-2016/lab-rules/blob/master/README.md#general-workflow).

Bring a USB stick with the VM as a backup to the lab.

### Currated collection of useful links
- [SSC lab rules](https://github.com/SSC-2016/lab-rules)
- [SEED labs](http://www.cis.syr.edu/~wedu/seed/labs.html)
- [Setting up VMs](http://www.cis.syr.edu/~wedu/seed/lab_env.html)
- [the class materials from weeks 3-4](http://staff.cs.upt.ro/~marius/curs/sec/index.html)
- [SEED lab materials on buffer overflow](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Vulnerability/Buffer_Overflow/)
- [SEED lab materials on Return-to-libc](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Vulnerability/Return_to_libc/)
- [gdb tutorial](https://www.youtube.com/watch?v=sCtY--xRUyI)
- [gdb cheat-sheet](http://darkdust.net/files/GDB%20Cheat%20Sheet.pdf)
