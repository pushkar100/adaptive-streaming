## Transcoding, Transrating, and Transmuxing

[SOURCE 1](https://www.oodlestechnologies.com/blogs/Introduction-to-Transmuxing%2C-Transcoding%2C-Transrating)

[SOURCE 2](http://www.streamingmedia.com/Articles/Editorial/What-Is-.../What-is-Encoding-and-Transcoding-75025.aspx)

### Transcoding

To convert to a different format of similar or like quality to gain compatibility with another program or application

- What?: Process of converting a video file from one format to another.
- Why?: Makes content viewable if a file format is not supported by a system.
- How?: 
	1. `Source` video (of some format) is 
	2. `Encoded` say, into H264 + AAC, and sent to 
	3. `Media server` which transmits it to
	4. `Client` which plays the given format.
- Features: 
	- Lossy: each time file is transcoded, there is loss in quality

### Transrating

To convert to a different data rate using the same format.

- What? To create different versions of video, a video file is changed from one bitrate to another.
- Why? Need for different resolutions & bitrates (The increased demand of video technologies like YouTube)
- How?: We perform transrating via an *encoder* for *Adaptive Bitrate System*.
	1. `Source` video (of some format) is 
	2.  `Encoded` say, into H264 + AAC, and sent to
	3. `Media server` which transmits
	4. Different versions (multiple video rates) [720p, 480p, etc] to different clients depending on what is best suited on the client-end.
- Features:
	- Enables the users to fit media content into much lesser storage space
	- Efficient video delivery in reduced bandwidth.

### Transmuxing

Also known as `Transcode-Multiplexing` or `re-packaging`

Convert to a different container format without changing the file contents.

- How?: 
	1. `Source` video (of some format) is 
	2.  `Encoded` say, into H264 + AAC, and sent to
	3. `Media server` which acts as the `transmuxer`
	4. It converts a file to a different container format without changing the file contents. (Ex: `.ts` to `.m4s` file format but content does not change. i.e `H264` content encoding is fine!) (Produces multiple output streams)
	5. Final set of output streams (i.e different file formats) are `published` on a `CDN` (For delivery to client)
- Features:
	- It supports Video On Demand transmission mode.


