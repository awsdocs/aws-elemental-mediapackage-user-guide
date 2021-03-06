# Creating a Microsoft Smooth packaging configuration<a name="pkg-cfig-create-mss"></a>

Create a packaging configuration that formats content for devices that support Microsoft Smooth\.

**To create a Microsoft Smooth packaging configuration \(console\)**

1. Open the MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

1. In the navigation pane, under **Video on demand**, choose **Packaging groups**\.

1. On the **Packaging groups** page, choose the group that will contain the configuration that you're creating\.

1. On the details page for the packaging group, in the **Packaging configurations** section, choose **Add or remove configs**\.

1. On the **Add or remove packaging configurations** page, in the **Packaging configurations** section, choose **Add** and select **New config**\.

1. Complete the fields as described in the following topics:
   + [General settings fields](cfigs-mss-new.md)
   + [Manifest settings fields](cfigs-mss-manset.md)
   + [Stream selection fields](cfigs-mss-include-streams.md)
   + [Encryption fields](cfigs-mss-encryption.md)

1. Choose **Save**\.

If you exceed the quotas for your account when you're creating a packaging configuration, you get an error\. If you get an error similar to Too many requests, please try again\. Resource limit exceeded, either you have exceeded the API request quota, or you have already reached the maximum number of packaging groups allowed on your account\.If this is your first group, or if you think you mistakenly received this error, use the Service Quotas console to [request quota increases](https://console.aws.amazon.com/servicequotas/home?region=us-east-1#!/services/mediapackage/quotas)\. For more information about quotas in MediaPackage, see [Quotas in AWS Elemental MediaPackage](quotas.md)\.