# Creating an Endpoint<a name="endpoints-create"></a>

Create an endpoint on a channel to define how AWS Elemental MediaPackage prepares content for delivery\. Content can't be served from a channel until it has an endpoint\.

When you create an endpoint, AWS Elemental MediaPackage assigns it a public URL that is fixed for the lifetime of the endpoint, regardless of any failures or upgrades that might happen over time\. This URL is how the player or CDN accesses the stream from the endpoint\.

You can use the AWS Elemental MediaPackage console, the AWS CLI, or the AWS Elemental MediaPackage API to create an endpoint\.

For information about creating an endpoint through the AWS CLI or AWS Elemental MediaPackage API, see the [AWS Elemental MediaPackage API Reference](http://docs.aws.amazon.com/mediapackage/latest/apireference/)\.

**Topics**
+ [Creating an HLS Endpoint](endpoints-hls.md)
+ [Creating a Microsoft Smooth Streaming Endpoint](endpoints-smooth.md)
+ [Creating a Common Media Application Format \(CMAF\) Endpoint](endpoints-cmaf.md)
+ [Creating a DASH Endpoint](endpoints-dash.md)