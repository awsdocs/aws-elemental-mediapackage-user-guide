# Tagging AWS Elemental MediaPackage resources<a name="tagging"></a>

A tag is a label that you assign to an AWS resource\. Each tag consists of a *key* and a *value*, both of which you define\. For example, the key might be "stage" and the value might be "test"\. You can use tags for a variety of purposes\. One common use is to control access to AWS resources using tags\. For information, see the [Controlling access to AWS resources using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) topic in the *IAM User Guide*\.

 Another common use of tags is to categorize and track your MediaPackage costs\. When you apply cost allocation tags to MediaPackage channels, endpoints, and packaging configurations, AWS generates a cost allocation report as a comma\-separated value \(CSV\) file with your usage and costs aggregated by your tags\. You can apply tags that represent business categories \(such as cost centers, application names, or owners\) to organize your costs across multiple services\. For more information about using tags for cost allocation, see [Using cost allocation tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html) in the [AWS Billing User Guide](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\. 

## Tag restrictions<a name="tagging-restrictions"></a>

The following restrictions apply to tagging AWS Elemental MediaPackage resources:
+ Cost allocation tagging is only available for channel, endpoint, and packaging configuration resources\. You can't use cost allocation tags for asset or packaging group resources\.
+ Maximum number of tags that you can assign to a resource – 50\.
+ Maximum key length – 128 Unicode characters\.
+ Maximum value length – 256 Unicode characters\.
+ Valid characters for key and value – a\-z, A\-Z, 0\-9, space, and the following characters: \_ \. : / = \+ \- and @\.
+ Keys and values are case sensitive\.
+ Don't use `aws:` as a prefix for keys; it's reserved for AWS use\.
+ Can't be used for harvested live\-to\-VOD assets\.

## Managing tags<a name="tagging-add-edit-delete"></a>

You can use the AWS Elemental MediaPackage API or the AWS CLI to add, edit, or delete the values for these properties\.

For more information, see the actions related to tags in the following reference documentation:
+ [Tags resource\-arn](https://docs.aws.amazon.com/mediapackage/latest/apireference/tags-resource-arn.html) in the *AWS Elemental MediaPackage live API reference*\. 
+  [Tags resource\-arn](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/tags-resource-arn.html) in the *AWS Elemental MediaPackage VOD API reference*\.
+ [tag\-resource](https://docs.aws.amazon.com/cli/latest/reference/mediapackage/tag-resource.html) in the AWS CLI *MediaPackage reference*\.