compiler vs interpretative language
	Compiler turns source code into assembly and then machine code (why you can't copy over files when compiling on different machines)
	interpreter - program that runs the (python) code line by line and kinda interepts the given code line by line
	line is getting blurry tho
TCP vs UDP
	
C++, C trivia, language trivia
	
experiences
linux commands
given project, how to optimize or do better
How would you compile like a whole project:
	makefile or some kind of dependency checker (if I update a local file then the dependent programs also get updated)
Linker vs Loader:
	Linker "links" dependent files together (basically files will have open holes in them if they can't find a function etc)
	Loader loads the file directly into memory (think about kernel.ld)
Socket programming
	Socket programming is a way for two computers or programs to talk to each other over a network (like the internet or a local network).
### Types of Sockets
There are two main types of sockets:
- ****Stream Sockets (TCP)****  
    Connection-based, reliable communication  
    Guarantees data arrives in order without loss or duplication  
    Used for web browsing, email, and file transfers.
- ****Datagram Sockets (UDP)****  
    Connectionless, unreliable communication  
    Faster but does not guarantee delivery or order.  
    Used for video-streaming, online-gaming, and voice calls.

Threads vs Processes
	threads =  basic unit of a computer program that can be executed independently 
	process = threads + memory space (own virtual memory)
type google.com into browser - how does it work

SPI vs I2C vs UART:
	SPI - no set limit (MOSI, MISO) serial communication, lot of wires
	
[I2C and SPI protocols](https://www.totalphase.com/blog/2021/07/i2c-vs-spi-protocol-analyzers-differences-and-similarities/) specifically are often compared as serial communication protocols because they are simple, low-cost, and are both implemented using master/slave architecture including a clock driven by the master for synchronization. While similar in these regards, they also have many differences, and one is often better suited in certain embedded applications.

I2C uses a two-wire interface where slave devices share the data and clock lines. Because of this, adding multiple devices to the bus is simple and reduces complexity of the circuit. I2C also includes flow control and error handling, making it a more reliable protocol. I2C can support multi-masters in a configuration, while SPI can only support one master.

I2C is often a good choice for connecting short-distanced, low-speed devices like microcontrollers, EEPROMs, I/O interface, and other peripheral devices like sensors in an embedded system.

SPI is superior in speed compared to I2C. Its push-pull drivers offer enhanced speed and signal integrity and its full-duplex support means master and slave devices can send data at the same time, allowing for even quicker data exchanges. While SPI has a speed advantage, it is more difficult and costlier to add multiple slave devices to the bus. This is because each slave needs its own slave select line, so the number of wires needed to communicate increases with each device.

SPI is also often used for connecting short-distanced devices within an embedded system, but it is also ideal for memory applications. For instance, many memory devices like SD cards, multi-media cards, EEPROMs, and [Flash memory](https://www.totalphase.com/blog/2021/10/what-is-flash-memory-introduction-types-examples-applications/) use SPI to store data that can easily be erased/rewritten as needed.



[(21) Calder Coalson | LinkedIn](https://www.linkedin.com/in/caldercoalson/)

![[calder_linkedin.png]]

650 satellites currently gen 1 
7 people 

got rejected LOL
did not prep enough 