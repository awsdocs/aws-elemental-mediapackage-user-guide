# Concepts and Terminology<a name="what-is-terms"></a>

AWS Elemental MediaPackage includes the following components:

Channel  
A *channel* represents the entry point for a content stream into AWS Elemental MediaPackage\. Upstream encoders such as AWS Elemental MediaLive send content to the channel\. When AWS Elemental MediaPackage receives a content stream, it packages the content and outputs the stream from an endpoint that you create on the channel\. There is one channel for each incoming set of ABR streams\.

Endpoint  
An *endpoint* is part of a channel and represents the packaging aspect of AWS Elemental MediaPackage\. When you create an endpoint on a channel, you indicate what streaming format, packaging parameters, and features the output stream will use\. Downstream devices request content from the endpoint\. A channel can have multiple endpoints\.

Just\-in\-time packaging  
AWS Elemental MediaPackage performs *just\-in\-time packaging* \(JITP\)\. When a playback device requests content, AWS Elemental MediaPackage dynamically customizes the live video streams and creates a manifest in a format that is compatible with the requesting device\.

Origination service  
AWS Elemental MediaPackage is considered an *origination service* because it is the point of distribution for media content delivery\.

Packager  
A *packager* prepares output streams for access by different types of players\. The packager type specifies the streaming format that AWS Elemental MediaPackage delivers from the endpoint \(either DASH\-ISO, Microsoft Smooth Streaming, or Apple HLS\)\. Additional packager settings include buffer and update durations and manifest tag handling instructions\.   
A packager is a part of an endpoint\. Each endpoint must have one, and only one, packager\. To use different packager types for the same content, create multiple endpoints on the channel\.

Stream  
A *stream* refers to the content input and output of AWS Elemental MediaPackage\. An upstream encoder sends a live stream as an input to AWS Elemental MediaPackage to the channel\. When a downstream device requests playback of the content, AWS Elemental MediaPackage dynamically packages the stream \(including specifying the packager type, adding encryption, and configuring track outputs\) and delivers it to the requesting device as an output of the endpoint\. An endpoint can produce multiple streams\.

Track  
*Tracks* make up the output content stream\. AWS Elemental MediaPackage includes selected video, audio, and subtitles or captions tracks in the output stream\. The stream delivers the tracks to the player \(either directly or through a CDN\), and the player plays back the tracks based on player logic or network conditions \(such as available bandwidth\)\.