
## DRM

[Source](http://www.streamingmedia.com/Articles/ReadArticle.aspx?ArticleID=112279&PageNum=1)

Stands for *Digital Rights Management*. DRM is a content protection scheme, usually employed when watching premium content (Ex: English Content / Live Sports)

It is better than just simple encryption (more sophisticated).

### DRM has 4 components

1. Digital Rights to Manage
2. Encryption
3. License management
4. DRM-enabled client

**Digital Rights to Manage**: 

- Business model related to purchase, subscription, gifting, rental, etc
- Specifies playback restrictions (like if playback via HDMI port is allowed, etc)

**Encryption**: 

- Provide content encryption during download, stream, etc

**License management**: 

- A platform (Server) to manage *requests for & issuance of licenses*
- It can be used to do other things as well:
	- *Domain Controllers*: Manage multiple user devices to play under on single license
	- *Metering Server*: To track usage data for royalty purposes
	
**A DRM-capable player (DRM-enabled client)**:

- A player that can communicate with a DRM platform (server) and enforce the SW & HW restrictions
- The industry is moving (from plugin-based DRM to browser-based DRM which required a separate download of the DRM client) via the Media Source Extensions (MSE) and Encrypted Media Extensions (EME), where the DRM must be integrated into the browser.
	- This means that we do not have to download a separate plugin
	- Instead applications/devices will or should come integrated with the DRM client
	- *Ex 1*: Smart TVs and similar devices come integrated with a DRM
	- *Ex 2*: Apple devices provide the DRM **FairPlay** via the Safari Browser
	- *Ex 3*: Google provides the WideVine Modular DRM that works only with DASH protocol for streaming via HTML5 video on Chrome

### The DRM Marketplace

1. **Companies providing the DRM software (tool/client)**
	- *Apple FairPlay Streaming (FPS)*:
		- Works with HLS
		- Works on most Apple devices and Safari Browser
	- *Google WideVine*:
		- Works with HTML5 on Google Chrome
		- *WideVine Modular* is what is called and works only with DASH
		- It may soon support HLS
	- Others: *Microsoft PlayReady*, *Adobe Primetime*, *DivX*
2. **Companies Providing the Licensing Functions**: The DRM platform
3. **Other Companies that touch upon the the DRM workflow**: Like packaging/encryption/etc.

### How DRM Works

1. Third party tool (Packager) is used to encrypt the video and a decryption key gets created
	- Encryption services/tools: 
		- Encoding.com
		- Elemental encoder
		- Wowza Streaming Engine, ...
	- Deals with:
		- Encoding (Transcoding)
		- Codecs (Audio/video codecs)
		- Encryption
2. The decryption key is shared with the DRM Platform
	- Remember that the platform is responsible for
		- Licensing
		- Metering/Domain Control, ...
	- The platform acts as a proxy between user and your system (server)
3. The user computer has a DRM player/client which makes a
	- License request
	- The request is handled by DRM platform
	- DRM platform checks with a running authentication process on our system (Server)
	- Once it gets approval, it sends the Decryption key to the user
	- The DRM player/client gets access to this key

For offline access, the above steps occur *before download begins* with *playback rights* and *restrictions information* also passed to the client.

### DRM on the Browser

DRM player has been integrated into the browser itself in order to enable DRM protected content playback. For this purpose, several standards-based technologies have been implemented:

1. **Media Source Extensions (MSE):** 
	- A JavaScript interface to playback media data
	- A standard that enables full adaptive streaming (as well as progressive download) on HTML5
2. **Dynamic Adaptive Streaming over HTTP (DASH):** 
	- A standardised file format for HTTP-based adaptive streaming
	- Similar in form and function to Apple's HLS
	- Most DASH content consists of separate:
		- MP4 files (one for each encoded stream in the adaptive group), and 
		- MPD (Media Presentation Description) manifest files.
	- MSE and DASH fit together like hand in glove. 
		- That is, for a browser or device to play DASH files, it must support MSE. 
			- So MSE provides the playback capabilities, while 
			- DASH is one of the supported file formats that MSE can play
3. Encrypted Media Extensions (EME): another JavaScript API that enables HTML5-based DRM by extending MSE with APIs
4. Common Encryption Scheme (CENC): CENC details the standard encryption and key mapping techniques used to store the DRM-related data for one or more DRM technologies with the compressed audio/video data
	- The ability to manage multiple DRMs is critical because most browsers or other devices will only support one DRM flavor, making multi-DRM support a necessity for most video producers
5. ISO Base Media File Format (ISO-BMFF)

### DRM Steps

1. Choose a playback platform (browser? OTT devices? etc)
	- Which DRMs does the playback platform support? 
	- To support all the major browsers on computers, you'll need to support multiple DRMs
	- Therefore, choosing a playback platform also includes choosing the DRMs (client) you want to support
2. Choose a licensing provider
	- BuyDRM
	- DRMToday
	- Microsoft Azure, ... etc
	- *Note:* These usually have deployment supports on AWS, Akamai, etc (need to check)

3. Packaging Content (Encoding/Encryption) with DRM
	- Some licensing providers (DRM platforms) themselves provide packaging services
	- Others use 3rd party tools
		- We will need to check what type of licensing this 3rd party packager supports
		- Ex: Encoding.com supplies Widevine licensing directly, but integrates with BuyDRM to manage PlayReady licensing
		
**Note:**
Netflix has licensed FairPlay from Apple for the playback of DASH-encoded files using EME and MSE (Only it has the privilege to do this - others can use FairPlay only with HLS)

### Dynamic Encryption

- Only a single copy of the unencrypted content needs to reside on the server.
- *Advantage*: Don't have to create and store the final encrypted packages for all technologies for all content, which would multiply your storage costs.
- *Disadvantage*: The potential downside of dynamic packaging is a slight playback latency, which will vary by technology provider.
- Check if service providers give you Dynamic Encryption
