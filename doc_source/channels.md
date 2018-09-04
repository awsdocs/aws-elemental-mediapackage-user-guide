# Working with Channels in AWS Elemental MediaPackage<a name="channels"></a>

A channel holds all the information that AWS Elemental MediaPackage requires to ingest a live content stream from a source such as AWS Elemental MediaLive or another encoder\. The channel receives content, and after packaging it, outputs it through an endpoint to downstream devices \(such as video players or CDNs\) that request the content\. 

After you create a channel, AWS Elemental MediaPackage provides a pair of ingest URLs that are fixed for the lifetime of the channel, regardless of any failures or upgrades that might happen over time\. The output of the upstream encoder points to the URLs for stream delivery to MediaPackage\.

**Topics**
+ [Creating a Channel](channels-create.md)
+ [Viewing Channel Details](channels-view.md)
+ [Editing a Channel](channels-edit.md)
+ [Rotating Credentials on an Ingest URL](#channels-rotate-creds)
+ [Deleting a Channel](channels-delete.md)
+ [Adding an Endpoint to a Channel](channels-add-endpoint.md)

## Rotating Credentials on an Ingest URL<a name="channels-rotate-creds"></a>

Rotate credentials on an ingest URL to generate a new WebDAV user name and password\.

You can use the AWS Elemental MediaPackage console or the MediaPackage API to rotate credentials\. For information about rotating credentials through the MediaPackage API, see the [AWS Elemental MediaPackage API Reference](http://docs.aws.amazon.com/mediapackage/latest/apireference/)\.

**To rotate credentials \(console\)**

1. Open the AWS Elemental MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

1. If the **Channels** page doesn't appear, on the AWS Elemental MediaPackage home page, choose **Skip and go to console**\.

1. On the **Channels** page, choose the name of the channel that holds the ingest URL that you're rotating the credentials for\.

1. On the channel's details page, choose the ingest URL that you're rotating credentials for, and then choose **Rotate credentials**\.

1. To confirm that you want to generate a new user name and password, choose **Rotate**\.

   AWS Elemental MediaPackage displays the new credentials\.