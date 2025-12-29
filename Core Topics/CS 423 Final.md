### Midterm 1 Content:

### Midterm 1:
Q1 - kernel interface:
mmap understanding - MP3
file descriptors/syscalls
syscall serializing, context switching
Q2 - memory management:
calculate memory space size given 
merging page tables - need to review! **REVIEW**
improve VM translation overhead
most expensive page fault
Q3 - MP1:
critical section for process list
two-halves approach 
why can't we use mutex?
debugging help 
Q3 - MP2: **REVIEW!!!**
RT applications breaking if RMS not correct
point out problem
consequences of early/late yield in RMS
possible solution for problem in code? Yes/no?
### MP3:
minor page faults: 
major page faults: 
multiprogramming vs cpu utilization:

summarize importance and why we implemented certain features:

### MP4:
loadable kernel modules are inherently unsafe - bugs in module can crash kernel
rust does not fix issue - still interfacing directly with kernel = big issue

eBPF = Extended Berkeley Packet Filter (safety shield between kernel and module)
principle of eBPF - safety verification 
	turn source code into eBPF byte, that gets verified by the kernel and calls helper functions
benefits of eBPF:
memory, type, resource, runtime safety

safety at the cost of usability
language verifier gap ^ basically compiler might do some optimizations that the verifier does not know/understand -> error out 

Solution? Rex - safe usable Rust kernel extensions

### Virtualization:
OS served as illusionist (basically give illusion to all programs)
need another level of indirection

create an isomorphism (mapping) that maps virtual system to real host

**Application Programmer Interface (API)**
	high level language library
	OS/language level abstraction
**Application Binary Interface (ABI)**
	user instructions (user ISA)
	syscalls? (why?)
	calling/register usage conventions, elf, syscall interface (syscall numbers) 
**Hardware-software interface**
	ISA (instruction set architecture)
	think of 411 and what we use in there

from chat:
API does not tell us how things run on hardware, tied to source code
VMs must ensure env behind API behaves consistently/correctly

ABI tells us interface between OS/CPU and programs
you need a specific CPU to match the guest ABI (or give an emulation of one)

##### Machine entity:
machine provides API for language
machine provides ABI for process
machine provides ISA for OS

emulation - illusion of another machine on top of another
replication/multiplexing - illusion of multiple smaller guest machines on host 
optimization - optimize generic guest interface for a host
##### Virtual Machines:
emulate (API/ABI/ISA) for 3 purposes (above) on top of the same/different one
process/language VMs - emulate ABI/API
system VMs - emulate ISA

##### Process/Language VMs Examples: 
1. Emulation
emulate ABI on top of another - run window apps on MacOS
run a process compiled for IA-32/Windows on PowerPC/MacOS
	interpreters: take guest instruction and update host state using a set of host instructions
	binary translation: convert blocks of guest ISA to host ISA at runtime (dynamic)

2. Binary Optimization
emulate ABI on top of itself for purposes of optimization
	run process binary, collect profiling data, then implement it more efficiently on top of same machine/OS interface

3. Language VMs
emulate API on top of different ABIs
	compile guest API to intermediate form (java source code to java byte code)
	interpret the bytecode on top of different host ABIs (interpreter)
JAVA, Microsoft Common Language Infrastructure (CLI)
#####  System VMs Examples:
implement VMM (ISA emulation) on bare hardware - **Type 1 hypervisor**
	best efficiency 
	must support drivers and wipe current OS
implement VMM on top of host OS - **type 2 hypervisor**
	less efficient
	easy to install on top of host OS
	able to use host OS drivers

##### Emulation Solutions:
Problem: emulate guest ISA on host ISA
switch on each specific instruction opcode

direct threaded implemenation:
given an opcode, send it to a emulating subroutine

big problems:
how do we know if something is code/data?
how do we map source PC to target PC?

Solutions:
only need to map source-target PC for locations that are target of jumps
know something is an instruction if the source PC will point it

Another problem:
we don't know targets of jumps at static analysis time

Solution:
SPC - source PC
TPC - target PC
![[Pasted image 20251126154338.png]]
Can only do the thing above on fixed destination jumps

Register Indirect Jumps?
Check slides (add caching/branch prediction if we have seen it already)

##### Hypervisor Issues:
what happens if guest OS/app tries to perform privileged ops (update TLB)
VMM/Hypervisor must intercept attempts to perform privileged ops
Priv Ops:
	done syscalls (interrupt/trap)
	OS establishes address of a (ISR/trap) routine with hardware 
VMM calls OS trap handler at reduced priv (intercepted it)
OS tried to return from trap - VMM will handle that

guest physical addr != host physical addr (issue with virtualization)
**Shadow PT**
hypervisor has a shadow page table
SPT can directly translate gVA to hPA
*Benefits:* EPT requires hardware supp

**Extended Page Table/Translation**
for every gPA (guest phys addr) and gL (guess level page table), extend translation and find the actual hPA (host phys addr) and hL - 2D Page walk 
Super long (check slides for diagram)
*Benefits:* eliminated VM exits/ctx switches/tlb switches, smaller mem footprint, simpler hypervisor design

Issues with EPT:
lot more translations needed
worse with nested virtualization, more page tables

**Summary:**
Shadow PT: original software approach to build a shadow PT.
EPT: hardware approach to extend the PW and removed the excessive VM exits.

HugeGPT: software approach to put guest PTs on hugepages, improved the address translation overhead of EPT.
DMT: hardware approach to build VMA to last-level PTE mappings, support both native, virtualized, and nested virtualized systems; improved the address translation overhead of EPT
### Disk:
sequential IO on HDDs much better
seek + rotation dominate random IO, while sequential IO is just transfer time

**Disk Scheduling Algos:**
[EASY-HOW-TO Disk Scheduling Algorithm (FCFS, SCAN, and C-SCAN) Tutorial (Manual)](https://www.youtube.com/watch?v=yrO5fvXlESE)

DAT = seek time + rotation delay + transfer time

Schedulers are at multiple layers of the stack 
need to think together (Linux NOOP)
### Filesystem:
Inodes, dentries, data nodes

three types of names - unique id (inode #), path, file descriptor

open - give us fd so we can do read/write, use path since string name = better

do expensive traversal once (open file)
store inode in descriptor object (kept in memory)
do reads/writes via descriptor which tracks offset
first time process opens file - fd will be 3 
0 - stdin
1 - stdout
2 - stderr

lseek = `off_t lseek(int filedesc, off_t offset, int whence)`
whence = **SEEK_SET**, offset of file = offset bytes
whence = **SEEK_CUR** offset of file = curr pos + offset bytes
whence = **SEEK_END** offset of file = sizeof(file) + offset bytes

OFT = open file table
fork() causes the parent and child to share the same open file table entry until one of them calls dup(), open(), or closes the descriptor

dup() just creates another pointer (fd) that points to the same OFT
must call open() to have independent offsets

fsync forces write buffers to flush to disk, makes data durable (less issues if system crashes!)

inodes/file are garbage collected when no references
paths deleted when unlink called

hardlink = points directly to file's data on same filesys
softlink = points to file's path (can be cross-fs)

allocation structure - bitmaps (inode bitmap or data bitmap)
superblock - how many data blocks/inode blocks, general metadata

#### FAT (File allocation table)
linked list index structure - thumb drives
linear map of all blocks on disk
file = linked list of blocks (block1 -> block2 -> block3)

Pros:
 ■ Easy to find free block
 ■ Easy to append to a file
 ■ Easy to delete a file
Cons:
 ■ Small file access is slow
 ■ Random access is very slow
 ■ Fragmentation
 ■ File blocks for a given file may be scattered
 ■ Files in the same directory may be scattered
 ■ Problem becomes worse as disk fill

What might happen if we get a crash when updating a file?
all data structures must be update (bitmaps, inode, data blocks, etc) - must agree
FS metadata consistency - internal structures agree with each other
data consistency - data must make sense to apps/users

fsck - filesystem consistency check
way too slow, not obvious how to fix FS (does not know the "correct" state)

Journaling - write a note to well-known location before writing to blocks (basically a heads-up notice) 
write actual data to a separate location before writing it back to disk (staging?)