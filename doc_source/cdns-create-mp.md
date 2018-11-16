# Creating a Distribution from AWS Elemental MediaPackage<a name="cdns-create-mp"></a>

AWS Elemental MediaPackage communicates with Amazon CloudFront on your behalf to create a distribution for a channel and its endpoints\. When you enable the feature, MediaPackage creates a distribution in CloudFront when you save the channel, and then adds an origin and updates cache behaviors when you save an endpoint\. Because the creation process is automated and initiated from your actions in MediaPackage, there is no additional action required from you\. 

**Important**  
You need additional permissions to create distributions in CloudFront\. Have an admin user add the correct level of permissions through AWS Identity and Access Management \(IAM\) using the steps described in [Creating a Policy for Amazon CloudFront](setting-up-create-non-admin-iam-cf.md)\.

**To create a distribution from the AWS Elemental MediaPackage console**

1. Start a new channel as described in [Creating a Channel](channels-create.md), and then choose **Create a CloudFront distribution**\. 

   You can also edit an existing channel to add a distribution\. For instructions on editing a channel, see [Editing a Channel](channels-edit.md)\.

1. When you've completed the channel, choose **Save**\. AWS Elemental MediaPackage communicates with CloudFront to create a distribution\. CloudFront uses placeholder values for settings that require information from the endpoint in MediaPackage, such as the origin domain name and caching behaviors\. 

   If you receive an error message that CloudFront couldn't create the distribution, choose **Edit** on the channel and save it again to restart the creation process\.

   Note that when the distribution is first created, it isn't fully functional until it has an origin, which AWS Elemental MediaPackage creates in the next step \(when you create an endpoint in MediaPackage\)\.

1. Create an endpoint on the channel, as described in [Creating an Endpoint](endpoints-create.md)\. AWS Elemental MediaPackage updates the origin and cache behaviors with information from the endpoint, and configures the distribution with settings that optimize live video streaming, as described in [Serving Live Video Formatted with AWS Elemental MediaPackage](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/live-streaming.html#live-streaming-with-mediapackage) of the *Amazon CloudFront Developer Guide*\.

   If you're adding a distribution to an existing channel with endpoints, AWS Elemental MediaPackage automatically adds the origin for you\.

   AWS Elemental MediaPackage communicates with CloudFront to add an origin to the distribution, and to update the settings on the distribution\. 

   When the distribution status on the channel's details page says **Deployed**, you can start using the distribution\. From the details page, note the CloudFront CDN URL and provide it for downstream devices to send playback requests\.
**Note**  
AWS Elemental MediaPackage adds only one origin to the distribution\. All endpoints on the channel are served by the same origin on the distribution\.