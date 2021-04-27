# Tagging AWS Elemental MediaPackage resources<a name="tagging"></a>

A *tag* is a metadata label that you assign or that AWS assigns to an AWS resource\. Each tag consists of a *key* and a *value*\. For tags that you assign, you define the key and value\. For example, you might define the key as `stage` and the value for one resource as `test`\.

Tags help you do the following:
+ Identify and organize your AWS resources\. Many AWS services support tagging, so you can assign the same tag to resources from different services to indicate that the resources are related\. For example, you could assign the same tag to an AWS Elemental MediaPackage channel and endpoint that you assign to an AWS Elemental MediaTailor configuration\.
+ Track your AWS costs\. You activate these tags on the AWS Billing and Cost Management dashboard\. AWS uses the tags to categorize your costs and deliver a monthly cost allocation report to you\. For more information, see [Use cost allocation tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html) in the [AWS Billing and Cost Management User Guide](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.

The following sections provide more information about tags for AWS Elemental MediaPackage\.

## Supported resources in AWS Elemental MediaPackage<a name="supported-resources"></a>

The following resources in AWS Elemental MediaPackage support tagging: 
+ Assets
+ Channels
+ Endpoints
+ PackagingConfigs
+ PackagingGroups

For information about adding and managing tags, see [Managing tags](#tagging-add-edit-delete)\.

## Tag restrictions<a name="tagging-restrictions"></a>

The following basic restrictions apply to tags on AWS Elemental MediaPackage resources:
+ Maximum number of tags that you can assign to a resource – 50 
+ Maximum key length – 128 Unicode characters 
+ Maximum value length – 256 Unicode characters 
+ Valid characters for key and value – a\-z, A\-Z, 0\-9, space, and the following characters: \_ \. : / = \+ \- and @
+ Keys and values are case sensitive
+ Don't use `aws:` as a prefix for keys; it's reserved for AWS use
+ Can't be used for harvested live\-to\-VOD assets

## Managing tags<a name="tagging-add-edit-delete"></a>

Tags are made up of the `Key` and `Value` properties on a resource\. You can use the AWS Elemental MediaPackage API or the AWS CLI to add, edit, or delete the values for these properties\.

For more information, see the following resources:
+ [AWS Elemental MediaPackage live API reference](https://docs.aws.amazon.com/mediapackage/latest/apireference/resources.html)
+ [AWS Elemental MediaPackage VOD API reference](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/resources.html)
+ [AWS CLI MediaPackage reference](AWS CLI Command Referencelatest/reference/mediapackage/index.html)