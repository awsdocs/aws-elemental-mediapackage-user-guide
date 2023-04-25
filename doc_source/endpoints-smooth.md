# Creating a Microsoft Smooth Streaming endpoint<a name="endpoints-smooth"></a>

Create an endpoint that formats content for devices that support Microsoft Smooth Streaming\.

**To create a Microsoft Smooth Streaming endpoint \(console\)**

1. Access the channel that the endpoint will be associated with, as described in [Viewing channel details](channels-view.md)\.

1. On the details page for the channel, under **Origin endpoints**, choose **Manage endpoints**\.

1. Complete the fields as described in the following topics:
   + [New endpoint fields](endpoints-smooth-new.md)
   + [Packager settings fields](endpoints-smooth-packager.md)
   + [Package encryption fields](endpoints-smooth-encryption.md)
   + [Access control settings fields](endpoints-smooth-access-control.md)
   + [Stream selection fields](endpoints-smooth-include-streams.md)

1. Choose **Save**\.

   If you enabled Amazon CloudFront distribution creation from the AWS Elemental MediaPackage console and this is your first endpoint on the channel, MediaPackage adds an origin to the distribution\. You can view the CloudFront CDN URL and endpoint information in the endpoints section of the channel's details page\.

   The endpoint is active and can deliver content as soon as requests are sent to its URL endpoints\. MediaPackage scales resources up and down to allow the right amount of capacity for your traffic\.

   When you're creating an endpoint, you will receive an error if you exceed the quotas on the account\. An error similar to Too many requests, please try again\. Resource limit exceeded means that either you've exceeded the API request quotas, or you've already reached the maximum number of endpoints allowed on this channel\. If you think you received this error wrongfully, use the Service Quotas console to [request quota increases](https://console.aws.amazon.com/servicequotas/home?region=us-east-1#!/services/mediapackage/quotas)\. For more information about quotas in MediaPackage, see [Quotas in AWS Elemental MediaPackage](quotas.md)\.