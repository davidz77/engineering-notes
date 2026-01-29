identify hosts with addresses/names
IP addresses -> routers/computers read this (32 bit integer)
DNS -> domain name space (human readable)

divide traffic into IP packets (used to denote which connection packet belongs to )
	header + payload/data

host runs multiple applications/processes (server)
	process -> UDP, 16-bit port number (distinguish different apps)

content corrupted?
	checksum -> help recover flip bits, error detection

UDP (User Datagram Protocol) -> low latency apps (zoom call -> voice packet)
	properties:
		unreliable - no guaranteed deliery
		unordered - no guarantee of 
		unlimited tranmission
		no connections 
	bare min tool (basically just using IP)
unit of transfer is "datagram"

network congested?
TCP! (Transport control protocol)
	reliable, ordering/integrity
	connection oriented 
	establish connection before communication/data transfer
	backs off when there is congestion

client server model -> model for sockets programming
	server passively listening/waiting for data (send replies)
	client initiates a request (send requests)

server needs to use well-known name/port so its easy to find?

sockets:
stream sockets
	send a long stream of bytes/chars
	implemented on top of TCP
datagram sockets
	UDP (datagram!)
	send a packet 

