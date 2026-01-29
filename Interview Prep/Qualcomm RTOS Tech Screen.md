#### Preparation:
embedded software engineer with 0-3 yrs of exp for core platform kernel software team
develops/deploys QuRT OS and ZephyrOS


QuRT OS:
https://www.qualcomm.com/news/onq/2019/07/role-realtime-operating-system-rtos-mobile
https://research.checkpoint.com/2021/pwn2own-qualcomm-dsp/
Qualcomm-developed real time operating system optimized for the Qualcomm Hexagon processor and AI, 5G modem and low power audio- and sensors workloads
enhance OS to expose power of the hexagon processor, 
high-performance, low-power edge AI use cases, high performance 5G and secure low-power audio and sensors use cases

Zephyr OS:
deploying this open source RTOS to multiple subsystems on Qualcomm SoCs

**Things to review:**
Basic OS concepts - RISCV (if time then ARM)
	interrupts
	syscalls 
	virtual memory
	memory management
	synchronization primitives 
	threads
	thread synchronization
	multithreading -> preemptive/cooperative
	scheduling (priority)
	pipes
	timers
	cache
basic c 
	run time stack 
	heap vs stack
	memory management
	pointers
	linker vs loader
	bss, code, text, etc

computer architecture

RMS scheduler from 423

Prepare for DS and algos

Special focus should be on queues, stack, hash map and linked list (single and double), sorting etc...

System programming: file operation, mutexes, semaphores, pipes, message queues, mmap, shared memory and other ipc concepts and programs based on them.

Memory management: malloc internals, virtual memory, cache etc...

Byte order format: little vs big endian programs

C programming specifics: macros as functions, volatile, bit fields, structure padding, volatile , static, const, register keywords, bitwise operations, string operations, arrays etc...

Serial interfaces: I2C/I2S, SPI, UART, USB etc..

Scheduling algorithms: round robin, sjf, cooperative.

Linux kernel internals: character drivers, kernel sub system working and basics like buddy etc...

C++: design patterns, class hierarchy etc...


**Possible coding questions:**
atoi 
reverse uint32_t
linked list operations - leetcode
rbuf from memory + atomic/etc



**ChatGPT notes/information**:
link: https://chatgpt.com/share/696ec935-56ac-800d-9693-5407cc6b25c8



Notes:
