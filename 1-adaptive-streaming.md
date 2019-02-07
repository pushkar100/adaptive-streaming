## Adaptive Streaming

[Source](http://www.streamingmedia.com/Articles/Editorial/What-Is-.../What-is-Adaptive-Streaming-75195.aspx)

**1. What is Adaptive Streaming?** 

- Enables the optimum streaming video viewing experience 
	- for a diverse range of devices
	- over a broad set of connection speeds

**2. Critical aspects of adaptive streaming:**

1. *Multiple Sources*: Produce multiple files from the same source file to distribute to viewers watching on different powered devices via different connection speed
2. *Adaptive*: Distribute the files adaptively, changing the stream that’s delivered to adapt to changes in effective throughput and available CPU cycles on the playback station.
3. *Transparency*: Operate transparently to the user. All stream switching occurs behind the scenes (The viewer may notice a slight change in quality)

**3. Common Metrics used by AS Technologies:**

Most streaming tech is same, with the following considerations taken into account to decide quality of video to be shared:

- Video buffer status
- CPU utilisation
- Dropped frames, etc.

**4. Key difference between different adaptive streaming technologies:**

1. Streaming server: Constant communication between server and player. If switch is required, server sends a different stream (Ex: For RTMP)
2. No streaming server: Different streams are hosted in multiple locations. The player monitors and decides from which location to stream (Ex: For HTTP, a normal web server is enough)
3. **4.1. What is a streaming server? (Not valid for HTTP based protocols)** 
   - It is an application on a web server
   - The service the application provides is that of video streaming
   - Ex: Adobe Media Server (Flash Media Server)

**5. Advantages of Adaptive Stream:**

- Not only caters to high end users but to low end users as well
- Without it, you would need to supply a mid level stream which is not optimum

**6. Adaptive Streaming Vendors:**

- HLS (Apple) (Apple is trying to push this as a standard to IETF) (Uses HTTP)
- Microsoft Smooth Streaming for Silverlight (Uses HTTP)
- Adobe with Flash-based dynamic streaming (Uses RTMP)

**7. Adaptive Streaming Service Providers:**

- Akamai HD Network (Primarily deliver to iOS, Flash and Silverlight clients)

Netflix has developed their own adaptive streaming technologies for internal use.

Considerations: ***You need at least 2 adaptive streaming tech - if you want to support mobile***

1. Flash/Silverlight is not supported on iOS (bad)
2. Android has implemented HLS (good)
3. HLS requires QuickTimeX player (Mostly lacking on windows)
4. Multi-platform capabilities like those offered by Akamai are becoming more mainstream (good)

**8. HTTP vs RTMP**: ***HTTP is better***

1. RTMP requires a persistent connection between server and player (increasing cost, limiting scalability)
2. A near-continuous connection means that RTMP can’t take advantage of caching on plain-vanilla servers like those used for Hypertext Transfer Protocol (HTTP) deliver. Using an HTTP cache server:
	- Decreases total bandwidth costs associated with delivering the video
	- Improves quality of service (Since cache servers are closer to viewer and easily retrievable)
3. RTMP packets have difficulty getting through firewalls as compared to HTTP packets
4. *People feel chunk-based delivery used by HTTP-based adaptive streaming technologies is better*

**Note**: What finally put the RTMP vs. HTTP debate to bed was Adobe announcing and shipping an HTTP version of Dynamic Streaming. So now if you want to deliver to the Flash Player via HTTP, you have an Adobe option. Adobe HTTP Dynamic Streaming (HDS)

**9. DRM**: 

Digital Rights Management - features to protect the media content that is being served.

*DRM offerings:*

1. Adobe offers Flash Access
2. Microsoft offers PlayReady content protection
3. HLS doesn’t support DRM. But, it:
	1. Enables encryption
	2. HTTPS authentication,
	3. etc
