# Features of AWS Elemental MediaPackage<a name="what-is-features"></a>

AWS Elemental MediaPackage supports the following features:

Audio  
AWS Elemental MediaPackage supports multi\-language audio inputs, as well as the following audio codecs:  

+ AAC stereo

+ Dolby AC3 and E\-AC3 \(Dolby Digital and Dolby Digital\+\)
AWS Elemental MediaPackage accepts these codecs from the input source and passes them through to the output stream\.

Captions  
AWS Elemental MediaPackage supports input 608/708 captions and passes them through to the output stream\.

DRM  
AWS Elemental MediaPackage supports content protection through digital rights management \(DRM\)\.

Subtitles  
AWS Elemental MediaPackage supports input WebVTT text\-based subtitles\. AWS Elemental MediaPackage translates the subtitles to the appropriate format based on the packager that is used on the endpoint:  

+ For HLS: WebVTT is passed through

+ For DASH: subtitles are translated to EBU\-TT

+ For Microsoft Smooth Streaming: subtitles are translated to DFXP

Time\-shift Viewing  
AWS Elemental MediaPackage allows playback of a stream at a time earlier than the current time\. Start\-over, catch\-up TV, and time delay are all supported\. For more information about setting up time\-shift capabilities, see [[ERROR] BAD/MISSING LINK TEXT](time-shifted.md)\.

Video  
AWS Elemental MediaPackage supports the input H\.264 video codec and passes it through to the output stream\. H\.265/HEVC is also supported with restricted playback devices\. 