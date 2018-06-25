# Editing a Channel<a name="channels-edit"></a>

Edit a channel's description for easier identification later\. You can edit only the description on a channel\.

You can use the AWS Elemental MediaPackage console, the AWS CLI, or the MediaPackage API to edit a channel\. For information about editing a channel through the AWS CLI or MediaPackage API, see the [AWS Elemental MediaPackage API Reference](http://docs.aws.amazon.com/mediapackage/latest/apireference/)\.

When you're editing a channel, do not put sensitive identifying information like customer account numbers into free\-form fields such as the **Name** field\. This includes when you work with AWS Elemental MediaPackage using the console, REST API, AWS CLI, or AWS SDKs\. Any data that you enter into MediaPackage might get picked up for inclusion in diagnostic logs or Amazon CloudWatch Events\.

**To edit a channel \(console\)** 

1. Open the AWS Elemental MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

1. If the **Channels** page doesn't appear, on the AWS Elemental MediaPackage home page, choose **Skip and go to console**\.

1. On the **Channels** page, choose the name of the channel that you want to edit\.

1. On the channel's details page, choose **Edit channel**\.

1. Revise the description\.

1. Choose **Save changes**\.