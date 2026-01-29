security/resilience = very important from the very beginning of networking
monotholic solutions = bad, need modularity -> TCP/IP
OSI reference model's layers

OSI Protocol Stack -> focus on top 4 in class
	Physical -> transmission of raw bits
	data link -> framing of data bits (reliability?)
	network -> can we give the data to the right people?
	transport -> process-to-process channels
	session 
	presentation
	application

network is a funnel -> bottom of funnel/transmission rate = limiting factor

bandwidth = throughput
	data transmitted per unit time
	example: 10 Mbps
	link bandwidth vs end to end bandwidth

latency/delay
	time from A to B
	example: 30 msec
	many apps depend on round trip time (RTT)

Notation: 
	KB = $2^{10}$ bytes
	Mbps = $10^6$ bits per second

Mbps = Megabits **BITS** per second
MB/s = Megabytes **BYTES** per second
KB/s = Kilobytes **BYTES** per second