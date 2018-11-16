# Creating a Common Media Application Format \(CMAF\) Endpoint<a name="endpoints-cmaf"></a>

Create an endpoint that formats content for devices that support Apple HLS fragmented MP4 \(fMP4\)\.

**To create a CMAF endpoint \(console\)**

1. Access the channel that the endpoint will be associated with, as described in [Viewing Channel Details](channels-view.md)\.

1. On the details page for the channel, choose either **Add and edit endpoint** or **Add endpoints** if there are no existing endpoints\.

1. Complete the fields as described in the following topics:
   + [New Endpoint Fields](endpoints-cmaf-new.md)
   + [Packager Settings Fields](endpoints-cmaf-packager.md)
   + [HLS Manifest Fields](endpoints-cmaf-manifest.md)
   + [Encryption Fields](endpoints-cmaf-encryption.md)
   + [Access Control Fields ](endpoints-cmaf-access-control.md)
   + [Streams to Include Fields](endpoints-cmaf-include-streams.md)

1. Choose **Save endpoints**\.

   If you enabled Amazon CloudFront distribution creation from the AWS Elemental MediaPackage console and this is your first endpoint on the channel, MediaPackage adds an origin to the distribution\. You can view the CloudFront CDN URL and endpoint information in the endpoints section of the channel's details page\.

   The endpoint is active and can deliver content as soon as requests are sent to its URL endpoints\. AWS Elemental MediaPackage scales resources up and down to allow the right amount of capacity for your traffic\.

   When you're creating an endpoint, you will receive an error if you exceed the limits on the account\. An error similar to Too many requests, please try again\. Resource limit exceeded means that either you have exceeded the API request limits, or you have already reached the maximum number of endpoints allowed on this channel\. If you think you received this error wrongfully, contact [AWS Support](https://aws.amazon.com/support)\. For more information about limits in AWS Elemental MediaPackage, see [Limits in AWS Elemental MediaPackage](limits.md)\.