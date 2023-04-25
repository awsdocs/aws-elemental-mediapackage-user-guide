# Features of AWS Elemental MediaPackage<a name="what-is-features"></a>

MediaPackage supports the following features:

**Audio**  
MediaPackage supports multi\-language audio inputs and the following audio codecs:  
+ AAC stereo
+ Dolby AC3 and E\-AC3 \(Dolby Digital and Dolby Digital\+\)
MediaPackage accepts these codecs from the input source and passes them through to the output stream\.  
MediaPackage doesn't support audio\-only inputs\. The stream configuration from the encoder must include at least one video track\.

**Captions**  
Your embedded source captions can be CEA\-608 captions, CEA\-708 captions, or both CEA\-608 and CEA\-708\. MediaPackage will pass through these captions in the media segments on HLS, CMAF, and DASH endpoints, and generate the appropriate manifest signaling\.  
Your input HLS playlist must include captions signaling tags\. If not present, MediaPackage will not be able to generate the corresponding output manifest signaling\.

**CDN Authorization**  
MediaPackage supports content delivery network \(CDN\) authorization\. For information, see [CDN authorization in AWS Elemental MediaPackage](cdn-auth.md)\.

**DRM**  
MediaPackage supports content protection through digital rights management \(DRM\)\. For information, see [Content encryption and DRM in AWS Elemental MediaPackage](using-encryption.md)\.

**HLS Rendition Groups**  
MediaPackage supports rendition groups for incoming and outgoing HLS content\. For information about output rendition groups, see [Rendition groups reference in AWS Elemental MediaPackage](rendition-groups.md)\.

**Live to VOD**  
Use the harvest job resource to extract a live\-to\-VOD \(video on demand\) asset from a live content stream\. MediaPackage creates the asset and stores it in an Amazon S3 bucket\. You can use the VOD functionality in MediaPackage to deliver the asset to end users\.

**Input Redundancy**  
Input redundancy is available with only live workflows in MediaPackage\.  
MediaPackage creates two input URLs on every channel so that you can create input redundancy by sending two identical streams to the same channel\. For information about how input redundancy works, see [Live input redundancy AWS Elemental MediaPackage processing flow](what-is-flow-ir.md)\.

**Subtitles**  
MediaPackage supports input WebVTT text\-based subtitles\. MediaPackage translates the subtitles to the appropriate format based on the packager that's used on the endpoint:  
+ For HLS and CMAF: WebVTT is passed through
+ For DASH: subtitles are translated to EBU\-TT
+ For Microsoft Smooth Streaming: subtitles are translated to DFXP
 MediaPackage supports accessibility signaling in HLS, CMAF, and DASH manifests only for VOD assets created from an HLS source\. The EXT\-X\-MEDIA line in the HLS source playlist must include a `public.accessibility.describes-music-and-sound` and/or `public.accessibility.transcribes-spoken-dialog` CHARACTERISTICS attribute\.

**Time\-shift Viewing**  
Time\-shift viewing is available with only live workflows in MediaPackage\.  
MediaPackage allows playback of a stream at a time earlier than the current time\. Start\-over, catch\-up TV, and time delay are all supported\. For more information about setting up time\-shift capabilities, see [Time\-shifted viewing reference in AWS Elemental MediaPackage](time-shifted.md)\.

**Video**  
MediaPackage supports the input H\.264 video codec and passes it through to the output stream\. CMAF endpoints in MediaPackage also support H\.265/HEVC and HDR\-10, following the Apple specification to applicable playback devices\.  
MediaPackage requires at least one video track to be present in the stream configuration from the encoder\. The service doesn't support audio\-only ingest\.

**Whitelisting**  
Whitelisting is available with only live workflows in MediaPackage\.  
MediaPackage supports restricting network access to the endpoint\. To take advantage of this feature, you must enter the allowed IP addresses on the endpoint\. For more information about adding whitelisting information, see [Access control settings fields](endpoints-hls-access-control.md)\.