# Viewing a single endpoint<a name="endpoints-view-one"></a>

View the details about a specific endpoint to obtain its playback URL and to view the packaging settings that it's currently using\.

You can use the AWS Elemental MediaPackage console, the AWS CLI, or the MediaPackage API to view the details of an endpoint\. For information about viewing endpoint details through the AWS CLI or MediaPackage API, see the [AWS Elemental MediaPackage API Reference](https://docs.aws.amazon.com/mediapackage/latest/apireference/)\.

**To view a single endpoint's details \(console\)**

1. Access the channel that the endpoint is associated with, as described in [Viewing channel details](channels-view.md)\.

1. On the details page for the channel, under **Origin endpoints**, choose the endpoint ID to view details such as package information and playback preview\. For downstream device requests, you must provide the endpoint URL from the **Endpoint URL** field or the CloudFront CDN URL\.