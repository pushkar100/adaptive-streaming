## MPEG DASH

DASH: Dynamic Adaptive Streaming over HTTP

**1. Advantage of Using DASH:** 

A unified standard would be a boon to content publishers, who could produce one set of files that play on all DASH-compatible devices.

In contrast, Apple's HLS is proprietary software that can become a standard!

**2. DASH (common points with HLS)**

- Adaptive Streaming
- Uses HTTP protocol
- No streaming server required (Since it is HTTP based - Can use standard HTTP web servers to deliver streaming content)
- Used for both on-demand and live streams

**3. Problems with DASH**

- Standard has not yet been widely accepted
- Not sure if it going to be royalty-free
- DASH is ***codec agnostic***. It means codec can be H264 or WebM or anything, it does not care. Although this seems like an advantage, it is a disadvantage because:
  - Neither of these two codecs are universally accepted
  - We will have to keep multiple files (& their chunks) for each of the codecs
  - And supply files from whichever codec has support

**4. How DASH Works**

1. Similar to HLS (& other HTTP based streaming), it consists of: 
	1. Encoded chunks (the encoded Audio / Video streams themselves) and 
	2. Manifest files that identify the streams for the player and contain their URL addresses
2. The actual A/V streams are called the **Media Presentation**
3. The manifest file is called the **Media Presentation Description** (`.mpd` file)

**4. Breakup of the MPD**

MPD is an **XML** file that contains data related to the whole video.

![MPD Image](https://images.slideplayer.com/15/4556938/slides/slide_15.jpg)

- The whole video is broken up into *Periods*
	- Each Period consists of multiple *Adaptation Sets*
		- Each Adaptation Set consists of multiple *Representations*
		- Each Representation is a single stream in the adaptive streaming experience 
		- (Ex: Each representation is a stream of a certain resolution)
			- Each Representation consists of media *Segments* (Held in "segment info" of Reprsnttn.)
			- These are the same chunks used in all adaptive streaming protocols (Ex: HLS)
			- These segments can be separate files (as in HLS) or byte ranges in a single media file

**MPD Top Level**: Splicing of arbitrary content
**Period**:  Selection of components of a video
**Adaptation Set**: Select/Switch of Bandwidth 
**Representation**: Contains individual Segments (Chunks of adaptive streaming)

**Note**: 

- Each period contains multiple adaptation sets that contain the content that comprises the audio/video experience. 
	- This content can be **muxed (mulitplexed)**, in which case there might be *one* adaptation set, (or represented in elementary streams) 
		- This enables features like multiple language support for audio.

**5. Advantages of a single MPD**

- Presentation in a single file helps improve file administration
- Improves caching efficiency (as compared to chunked technologies that can create hundreds of thousands of files for a single audio/video event)

**6. Advantages of the MPD structure**

- We can identify the various content components (Periods)
- & Location of alternative streams
	- This helps identify and start playback of the initial segments
	- Switch between representations as necessary to adapt to changing CPU and buffer status
	- Change adaptation sets to respond to user input, like enabling/disabling subtitles or changing languages.

**7. Features of DASH**

1.  DASH is **codec-independent**, and will work with H.264, WebM and other codecs
2.  DASH supports both the ISO Base Media File Format (essentially the **MP4** format) and **MPEG-2 transport streams** (HLS supports only MPEG-2 Transport Streams)
3.  DASH does not specify a DRM method but **supports all DRM techniques** specified in ISO/IEC 23001-7: Common Encryption
4.  DASH supports **trick modes** for seeking, fast forwards and rewind
5.  DASH supports **advertising insertion**

**8. Some Intellectual Property issues with DASH**

- If DASH uses MPEG Transport Streams, they are *not* royalty free! (Underlying codec might not be free)
- It is straight-forward to use HLS on Apple Systems and Software (iOS, Safari)
- Mozilla might not support DASH (again, because of royalty issues with underlying technologies)

