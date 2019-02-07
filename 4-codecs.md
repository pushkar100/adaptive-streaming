## Codecs

Codecs are an important part of streaming media. Modern video/audio production techniques all use codecs.

**What is a Codec?**

- It is a compression technology
- Every codec has 2 components:
	1. Encoder (to compress files)
	2. Decoder (to decompress files)

**Codecs for each content type:**

1. Data (`PKZIP`)
2. Still Images (`JPEG`, `PNG`, `GIF`)
3. Audio (`MP3`, `AAC`)
4. Video (`Cinepak`, `MPEG-2`, `H.264`, `VP8`)

**Lossless versus Lossy Compression:**

1. Lossless: Results in same file as original upon decompression (`PNG`, `PKZIP`). Lossless compression for videos don't match the data rates that need to be low for streaming.
2. Lossy: Result is a copy of original but not original! 
	- Lower the data rate, less identical to original
	- That is, more the compression, higher the loss!

All popular video codecs are lossy!

**Lossy compression techniques:**

1. Intra-frame: Image compression applied to each frame of video. It's not dependent on other frames (Ex: `Motion-JPEG`)
2. Inter-frame: Uses redundancy between frames to compress video. Static content that doesn't change (Ex: Background) need not be stored repeatedly; once is enough.

Interframe is better than Intraframe compression (`Inter-frame > Intra-frame`)

**Interframe compression:**

There are usually 2 types of frames:

1. Key frames: Store the complete frame using intra-frame compression techniques
2. Delta frames: Compares data to previous frame and removes redundant data. Only changing pixels are saved and this too is intra-frame compressed!

Key + Delta frame technique is very efficient for static backgrounds where redundancy is high (For example: It is good for a video of a person talking rather than a Formula 1 telecast where background changes fast!)

**Long GOP Format**

- It is an inter-frame (key + delta) format
- It uses 3 frames for compression:
	- *I frame*: Frame with intra-frame compression (not delta) (`I = Intra-coded`)
	- *P frame*: Frame holding changes from previous image (delta) (`P = Predicted`)
	- *B frame*: Frame holding differences in current, previous as well as subsequent frames (delta) (`B = Bidirectional`) 
- `An I frame` + `P frame(s)...` + `B frame(s)...` until the next `I frame` (not included) form something known as a group of photos or **GOP**

B frame saves the max space.

`H264`, `MPEG-2`, etc are Long GOP Formats!

*Note*: Long GOP => More complexity => Better quality (Adv.) => Harder to decode (Disadv.)

`H264`, `MPEG-2` are used mainly in:

- Camcorders
- DSLRs
- Delivery (Streaming media)

**Container Formats vs Codecs**

- Containers are file formats containing a specific type of data (incl. audio, video, captioning, metadata, etc) (Ex: `QuickTime`)
- Sometimes the container format name is the same as the codec that it specifies - leading to the confusion between the two!
- One container format might specify (use) more than one codec!
- It is *critical* to choose a codec and container format that’s compatible with the playback capabilities of your target viewers.

**`H.264`**

This codec has passed through ISO and ITU standards certification and dominates the codec market (Except for 'intermediate codecs')

**Audio Codecs**

The `PCM` Pulse-code Modulation format is used in many platforms:

- stored in either `WAV` or `AVI` format on Windows
- stored in either `AIFF` or `MOV` on the Mac

PCM is considered uncompressed!

- H264 is coupled with `AAC` (Advanced Audio Compression Standard)
- WebM pairs the VP8 codec with the open-source Vorbis codec.


