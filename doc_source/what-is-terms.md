# Concepts and Terminology<a name="what-is-terms"></a>

AWS Elemental MediaPackage includes the following components:

**Just\-in\-time packaging**  
AWS Elemental MediaPackage performs *just\-in\-time packaging* \(JITP\)\. When a playback device requests content, MediaPackage dynamically customizes the live video streams and creates a manifest in a format that is compatible with the requesting device\.

**Origination service**  
AWS Elemental MediaPackage is considered an *origination service* because it is the point of distribution for media content delivery\.

**Packager**  
A *packager* prepares output streams for access by different types of players\. The packager type specifies the streaming format that AWS Elemental MediaPackage delivers from the endpoint \(either DASH\-ISO, Microsoft Smooth Streaming, CMAF, or Apple HLS\)\. Additional packager settings include buffer and update durations and manifest tag handling instructions\.   
A packager is a part of an endpoint\. Each endpoint must have one, and only one, packager\. To use different packager types for the same content, create multiple endpoints on the channel\.

**Stream**  
A *stream* refers to the content input and output of AWS Elemental MediaPackage\. An upstream encoder sends a live stream as an input to MediaPackage to the channel\. When a downstream device requests playback of the content, MediaPackage dynamically packages the stream \(including specifying the packager type, adding encryption, and configuring track outputs\) and delivers it to the requesting device as an output of the endpoint\. An endpoint can produce multiple streams\.

**Track**  
*Tracks* make up the output content stream\. AWS Elemental MediaPackage includes selected video, audio, and subtitles or captions tracks in the output stream\. The stream delivers the tracks to the player \(either directly or through a CDN\), and the player plays back the tracks based on player logic or network conditions \(such as available bandwidth\)\.

## Live Components<a name="what-is-terms-live"></a>

The following components apply to live workflows in AWS Elemental MediaPackage:

**Channel**  
A *channel* represents the entry point for a content stream into AWS Elemental MediaPackage\. Upstream encoders such as AWS Elemental MediaLive send content to the channel\. When MediaPackage receives a content stream, it packages the content and outputs the stream from an endpoint that you create on the channel\. There is one channel for each incoming set of ABR streams\.

**Endpoint**  
An *endpoint* is part of a channel and represents the packaging aspect of AWS Elemental MediaPackage\. When you create an endpoint on a channel, you indicate what streaming format, packaging parameters, and features the output stream will use\. Downstream devices request content from the endpoint\. A channel can have multiple endpoints\.

## VOD Components<a name="what-is-terms-vod"></a>

The following components apply to video on demand \(VOD\) workflows in AWS Elemental MediaPackage:

**Asset**  
An *asset* represents the entry point for file\-based content into AWS Elemental MediaPackage\. MediaPackage uses the information in the asset to locate and ingest your source content from Amazon S3\. When you create an asset in MediaPackage, you associate it with a *packaging group*, which holds one or more *packaging configurations*\. Each asset and packaging configuration combination provides a URL for playback of repackaged content\. Each asset is associated with all the packaging configurations within one packaging group\.

**Packaging Configuration**  
A *packaging configuration* defines how MediaPackage formats, encrypts, and delivers source content to viewers\. The packaging configuration includes settings such as stream selection, encryption, segment duration and combining, as well as one or more HLS, DASH, CMAF, or MSS manifest definitions\.

**Packaging Group**  
A *packaging group* is a set of one or more packaging configurations\. Because you can associate the group to more than one asset, the group provides an efficient way to associate multiple packaging configurations with multiple assets\. 

**Source Content**  
*Source contents* are video files that AWS Elemental MediaPackage ingests\. The source content resides in an Amazon S3 bucket in your AWS account\. Each source content is composed of a set of related manifest and segment objects\. MediaPackage supports HLS source content\.