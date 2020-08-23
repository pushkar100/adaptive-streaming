## MPEG 2 Transmission Stream

**MPEG2 is**

- It is a standard that defines the following:
	- How to format various components of a media programme (Includes compressed audio, video, and data)
	- How the components are combined into a single synchronous transmission bit stream, known as *Multiplexing*
		- Multiplexed streams can be sent over cable TV, Satellite broadcasts, IPv6 (Internet), etc.

**MPEG2 Bit Stream**

- Most basic component is an ***Elementary Stream*** (Example: In one program, the video is one ES, audio is one ES, control is on ES)
- For audio/video, each ES is one *access unit* - Every access unit is fundamental unit of encoding
	- For video, an ES access unit will usually be a complete encoded video frame. (Ex: H264 encoded frame)
- An MPEG2 Processor takes in a set of Elementary Streams and creates a ***Packetised Elementary Stream***. 
	- It can be a fixed or variable block stream of max block size of 2^16 bytes
	- One PES contains an integral number of ES access units.
	- Each PES block (with header) identifies if it is an audio stream block (or video or some other control)

### Program Stream vs Transport Stream

Both these are forms of multiplexing the various data into one stream:

- PS is Program Stream which can be used for storage applications such as DVD
	- Such streams are suited for transmission in a relatively error-free environment and 
	- Enable easy software processing of the received data
- TS is Transport Stream which are aimed for communication and broadcasting application
	- This is suited for transmission in which there may be potential packet loss or corruption by noise, or / and 
	- Where there is a need to send more than one programme at a time.

