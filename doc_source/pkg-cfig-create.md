# Creating a packaging configuration<a name="pkg-cfig-create"></a>

Create a packaging configuration to define how AWS Elemental MediaPackage prepares content for delivery from an asset\. 

To create a packaging configuration, you can use the MediaPackage console, the AWS CLI, or the MediaPackage API\. For information about creating a packaging configuration with the AWS CLI or MediaPackage API, see [Packaging\_configurations](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_configurations.html) in the *AWS Elemental MediaPackage VOD API Reference*\.

When you're creating a packaging configuration, don't put sensitive identifying information like customer account numbers into free\-form fields, such as the **ID** field\. This applies when you're using the MediaPackage console, REST API, AWS CLI, or AWS SDKs\. Any data that you enter into MediaPackage might get picked up for inclusion in diagnostic logs or Amazon CloudWatch Events\.

**Topics**
+ [Creating an HLS packaging configuration](pkg-cfig-create-hls.md)
+ [Creating a DASH packaging configuration](pkg-cfig-create-dash.md)
+ [Creating a Microsoft Smooth packaging configuration](pkg-cfig-create-mss.md)
+ [Creating a CMAF packaging configuration](pkg-cfig-create-cmaf.md)