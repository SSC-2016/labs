# lab 3. 11-12 October

This week we will be trying to gain understanding of buffer overflow issues and potential attacks. 
Please focus on understanding how the stack is working, and the principle way of attacking them. 
From here on out, we will be following the guides, and materials made available by the SEED labs.

## Required Reading
- [the class materials from week 3](http://staff.cs.upt.ro/~marius/curs/sec/index.html)
- [SEED lab materials on buffer overflow](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Vulnerability/Buffer_Overflow/)
- hint: if for some reason the lecture/lab page is not updated in time, please check out last year's resources
- [gdb tutorial](https://www.youtube.com/watch?v=sCtY--xRUyI)

### What is needed to understand Buffer Overflow
- Understanding C functions and the stack.
- Some familiarity with machine code.
- Know how systems calls are made. 
- The exec() system call.
- Details vary slightly between CPU’s and OS:
  - Stack growth direction.
  - big endian vs. little endian.

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

Please remember that starting this lab we will be doing a very short quizz about the topic of the week. 
So try to read carefully the materials, and understand the concepts.

On Tuesday and Wednesday morning, the quiz will be given in the first 10 minutes of the lab. 
Please make sure to make it on time. 

### Installing the Virtual Machine

You can even learn by practicing at home. In order to do that, [follow the instructions on how to set up your environment, and download the correct VM](https://github.com/SSC-2016/lab-rules/blob/master/README.md#general-workflow).

Bring a USB stick with the VM as a backup to the lab.

### Useful links
- [SSC lab rules](https://github.com/SSC-2016/lab-rules)
- [SEED labs](http://www.cis.syr.edu/~wedu/seed/labs.html)
- [Setting up VMs](http://www.cis.syr.edu/~wedu/seed/lab_env.html)
- [the class materials from week 3](http://staff.cs.upt.ro/~marius/curs/sec/index.html)
- [SEED lab materials on buffer overflow](http://www.cis.syr.edu/~wedu/seed/Labs_12.04/Vulnerability/Buffer_Overflow/)
