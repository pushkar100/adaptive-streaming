## HLS

[Source](http://www.streamingmedia.com/articles/editorial/what-is-.../what-is-hls-(http-live-streaming)-78221.aspx)

**1. What is HLS?**

- An Adaptive Streaming Protocol
- Created by Apple (for iOS/AppleTV initially) (2009)
- Works for both:
	- Live content, and
	- On demand files

**2. Support:**

- Support for HLS in streaming servers:
	- Adobe
	- Microsoft
	- Wowza, etc...
- Distribution Support:
	- Akamai
- Support on the player side:
	- iOS (Especially Safari Browser)
	- Android (3.0+)

**3. How it works:** 

1. *No* streaming server required since HLS is HTTP based (Can use standard HTTP web servers to deliver streaming content). 
2. The *switching logic* is implemented on the *player side* (resides in the player)
3. The HTTP Server contains:
	1. A manifest text file (`.m3u8` extension)
	2. Multiple encoded files for distribution. Each file has
		1. Different data rate
		2. Is divided into short chunks (usually 5-10 seconds long)

Basically, you 

(a) Encode source file into 

​	(b) Multiple files at different data-rates and

​		(c) split them into short chunks

**Note**: The main manifest file will redirect the player to additional manifest files (additional `.m3u8` files) for each of the encoded streams (each of the multiple files)

**4. Preparing the files**

1. A single source file is split into multiple files (of different data-rates)
	- Uses ***H.264*** video codec
	- Uses ***AAC*** audio codec
2. But, the multiple files above (in 1) are converted to segments/chunks:
	- That is, chunks in an ***MPEG 2 Transport Stream*** (`.ts` extension)
3. These *chunks* and *manifest files* are placed on an HTTP server

**Example of a certain media's multiple resolution files @ Hotstar**

- 416x234
- 640x360
- 720x404
- 1280x720
- 1600x900
- 1920x1080

**5. Content Protection**

No Native support for DRM. Can use third party tools + HTTPS authentication + encryption

**6. Closed Captions**

Supports closed captions in MPEG 2 Transport streams

**7. Deploying HLS Streams**

- Delivery via HTTP:
	1. No streaming server required (good)
	2. Can leverage HTTP caching servers (serve viewers content from these caches) (good)
	3. Must pass through most firewalls (good)

**Note**: Apple recommends playing video via the HTML5 tag `<video>` player

**8. Playback side**

No issue on safari browser and apple systems which come with an *HTTP Live Streaming Client*

**9. Apple tools for producing HLS files:**

**For On-Demand Environment:**

1. *Media Stream Segmenter* - inputs an MPEG-2 transport stream and produces chunked `.ts` files and index files. It can also encrypt the media and produced encryption keys.
2. *Media File Segmenter* - Inputs H.264 files and produces chunked `.ts` files and index files. It can also encrypt the media and produced encryption keys.
3. *Variant Playlist Creator* - Compiles the individual index files created by the Media Stream or Media File Segmenter into a master `.m3u8` file that identifies the alternate streams.
4. *Metadata Tag Generator* - Creates ID3 metadata tags that can either be written to a file or inserted into outgoing stream segments.
5. *Media Stream Validator* - Examines index files, stream alternates, and chunked `.ts` files to validate HLS compatibility.

**For Live Streaming**

You need an *encoding* tool that can :
1. Encode the files into H.264 format, 
2. Create the MPEG-2 transport stream chunks and 
3. Create and Update the manifest files

Many vendors exist that do this live encoding:

- [Cisco](http://www.cisco.com/web/about/ac49/ac0/ac1/ac259/inlet.html)
- [Envivio](http://www.envivio.com/)
- [Digital Rapids](http://www.digital-rapids.com/Home/Products/IndividualProducts/StreamZHDLiveABR.aspx)
- [Elemental Technologies](http://www.elementaltechnologies.com/products/live/specs)
- [Haivision](http://www.haivision.com/products/kulabyte_encoder)
- [Seawell Networks](http://www.seawellnetworks.com/products/spectrum)
- [ViewCast](http://www.viewcast.com/products/niagara-systems/niagara4100)

**10. Real Time Transmuxing**

An alternative to producing HLS files

1. Offered by multiple streaming server vendors and CDNs
2. These servers input an H.264-stream and then dynamically re-wrap the file into the required MPEG-2 transport stream chunks and create the required manifest files.
3. Used for both live or on-demand streaming

***Akamai offers “in the network” repackaging of H.264 input files for HLS deployment.***