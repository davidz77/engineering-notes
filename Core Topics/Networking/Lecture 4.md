length vs sentinel value for framing

**sentinel framing:**

sentinel value -> NUL at the end of C strings (tells us that a string is finished)
need to use escape character \ to prevent actual data from being interpreted as sentinel value
double up or "stuff" it so data doesn't get confused

example:
DLE = data link escape
input data: 0x48 -> DLE -> 0x69
transmitted data: 0x48 -> DLE -> DLE -> 0x69

we are basically "escaping" out the DLE so not a control signal but actual data


bit stuffing:
purpose: if we wanna use an control signal in data, we gotta setup a whole **byte** to escape it (not very efficient)


frame marker -> marker for a frame (replaces start and stop) = 0111 1110 
bit stuffing: insert 0 after pattern 0111 11 in data 

0111 1110 -> end of frame
0111 1111 -> error! lose one or two frames 
can't resync with sender/receiver

![[Pasted image 20260129144631.png]]
0111 1110 (control character) next frame is acting as the end marker for prev frame and then the start marker for the next frame

**Length-based framing:**
add more notes here


Encoding translates symbols to signals
Framing demarcates units of transfer
Error detection validates correctness of
each frame