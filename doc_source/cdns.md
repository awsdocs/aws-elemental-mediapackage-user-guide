# Working with Content Delivery Networks \(CDNs\)<a name="cdns"></a>

You can use a content delivery network \(CDN\) such as [Amazon CloudFront](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/) to serve the content that you store in AWS Elemental MediaPackage\. A CDN is a globally distributed set of servers that caches content such as videos\. When a user requests your content, the CDN routes the request to the edge location that provides the lowest latency\. If your content is already cached in that edge location, the CDN delivers it immediately\. If your content is not currently in that edge location, the CDN retrieves it from your origin \(the MediaPackage endpoint, in this case\) and distributes it to the user\. The following illustration shows this process\.

![\[This illustration shows how content stored in AWS Elemental MediaPackage is distributed using a CDN.\]](http://docs.aws.amazon.com/mediapackage/latest/ug/images/cf_flow.png)

**Using AWS Elemental MediaPackage as an Origin in Amazon CloudFront**  
After you create a channel and its endpoints in AWS Elemental MediaPackage, note the URLs for each of the endpoints\. These URLs are what you use for the origin domain names for your CloudFront distribution\. You need one origin for each endpoint on the channel in MediaPackage\. 

For detailed steps about creating a distribution with AWS Elemental MediaPackage endpoints as the origins, see [Delivering Live Streaming Video](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/live-streaming.html) in the *Amazon CloudFront Developer Guide*\.