# Features of AWS Elemental MediaPackage<a name="what-is-features"></a>

AWS Elemental MediaPackage supports the following features:

**Audio**  
AWS Elemental MediaPackage supports multi\-language audio inputs, as well as the following audio codecs:  
+ AAC stereo
+ Dolby AC3 and E\-AC3 \(Dolby Digital and Dolby Digital\+\)
AWS Elemental MediaPackage accepts these codecs from the input source and passes them through to the output stream\.  
MediaPackage does not support audio\-only inputs\. The stream configuration from the encoder must include at least one video track\.

**Captions**  
AWS Elemental MediaPackage supports input 608/708 captions and passes them through to the output stream\.

**DRM**  
AWS Elemental MediaPackage supports content protection through digital rights management \(DRM\)\.

**Input Redundancy**  
Input redundancy is available with only live workflows in AWS Elemental MediaPackage\.  
AWS Elemental MediaPackage creates two input URLs on every channel so that you can create input redundancy by sending two identical streams to the same channel\. For information about how input redundancy works, see [Live Input Redundancy AWS Elemental MediaPackage Processing Flow](what-is-flow-ir.md)\.

**Subtitles**  
AWS Elemental MediaPackage supports input WebVTT text\-based subtitles\. MediaPackage translates the subtitles to the appropriate format based on the packager that is used on the endpoint:  
+ For HLS and CMAF: WebVTT is passed through
+ For DASH: subtitles are translated to EBU\-TT
+ For Microsoft Smooth Streaming: subtitles are translated to DFXP

**Time\-shift Viewing**  
Time\-shift viewing is available with only live workflows in AWS Elemental MediaPackage\.  
AWS Elemental MediaPackage allows playback of a stream at a time earlier than the current time\. Start\-over, catch\-up TV, and time delay are all supported\. For more information about setting up time\-shift capabilities, see [Time\-shifted Viewing Reference in AWS Elemental MediaPackage](time-shifted.md)\.

**Video**  
AWS Elemental MediaPackage supports the input H\.264 video codec and passes it through to the output stream\. Common Media Application Format \(CMAF\) endpoints in MediaPackage also support H\.265/HEVC and HDR\-10, following the Apple specification to applicable playback devices\.  
MediaPackage requires at least one video track to be present in the stream configuration from the encoder\. The service does not support audio\-only ingest\.

**Whitelisting**  
Whitelisting is available with only live workflows in AWS Elemental MediaPackage\.  
AWS Elemental MediaPackage supports restricting network access to the endpoint\. To take advantage of this feature, you must enter the allowed IP addresses on the endpoint\. For more information about adding whitelisting information, see [Access Control Fields](endpoints-hls-access-control.md)\.