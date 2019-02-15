# How Input Redundancy Works<a name="what-is-flow-ir"></a>

Achieve input redundancy in AWS Elemental MediaPackage by sending two streams to separate input URLs on a channel in MediaPackage\. One of the streams becomes the primary, active source of content for the endpoints, while the other continues to passively receive content\. If MediaPackage stops receiving content from the active stream, it switches over to the other input stream so that content playback isn't interrupted\.

If you use AWS Elemental MediaPackage with AWS Elemental MediaLive \(for example\), here is the flow of input redundancy:

1. You create a channel in AWS Elemental MediaPackage, as described in [Creating a Channel](channels-create.md)\. When MediaPackage provisions the channel, it creates two input URLs for the channel\. If you're not using input redundancy, you can send a stream to either input URL\. There is no requirement that you send content to both URLs\.
**Note**  
When input redundancy became available, AWS Elemental MediaPackage added a second input URL to existing channels and updated the existing URL to a new format\. You can use either the existing URL or the new URLs for content input\. 

1. You create an endpoint in AWS Elemental MediaPackage as described in [Creating an Endpoint](endpoints-create.md)\. 
**Important**  
If you use short output segments, depending on your playback device, you might see buffering when AWS Elemental MediaPackage switches inputs\. You can reduce buffering by using the time delay feature on the endpoint\. Be aware that using a time delay introduces latency to end\-to\-end delivery of the content\. For help enabling time delay, see [Creating an Endpoint](endpoints-create.md)\.

1. You create an input and channel in AWS Elemental MediaLive, and you add two HLS output groups to the channel in MediaLive, as described in [Getting Started](https://docs.aws.amazon.com/medialive/latest/ug/getting-started.html) in the *AWS Elemental MediaLive User Guide*\. When you're setting up MediaLive, remember these important points:
   + The streams must have identical encoder settings for input redundancy to work correctly and playback to be maintained\. 
   + The input loss behavior on the channel in AWS Elemental MediaLive must not be set to emit a black frame if the service doesn’t receive input\. If MediaLive sends a black frame or some other filler frame when it’s missing input, then AWS Elemental MediaPackage can't tell when segments are missing, and subsequently can't perform failover\. For more information about setting the input loss behavior in MediaLive, see [Complete the General Settings](http://docs.aws.amazon.com/medialive/latest/ug/creating-a-channel-step3.html) in the *AWS Elemental MediaLive User Guide*\. 

1. You start the channel in AWS Elemental MediaLive to send the streams to AWS Elemental MediaPackage\.

1. AWS Elemental MediaPackage receives content on both of the input URLs, but only one of the streams is used for source content at a time\. If the active stream is missing any segments, then MediaPackage automatically fails over to the other stream\. MediaPackage continues to use this stream until failover is needed again\.

   The formula that is used to determine if an input is missing segments is based on the segment lengths on the inputs and the endpoints\. If an input is missing segments and quickly recovers, an endpoint with longer segment lengths won't switch inputs\. This might result in different endpoints on the channel using different inputs \(if one endpoint switches and the other doesn't\)\. This is expected behavior and should not affect the content workflow\.