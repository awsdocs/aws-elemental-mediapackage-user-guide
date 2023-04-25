# Step 2: Ingest live content<a name="gs-ingest-live"></a>

To ingest a live content stream into AWS Elemental MediaPackage and extract a video on demand \(VOD\) asset from it, create a channel and endpoint\. The channel is the entry point to MediaPackage, and the endpoint provides MediaPackage access to the stream so that it can extract the VOD asset\. The following sections describe how to use the MediaPackage console to create a channel and endpoint\.

## Create a channel<a name="gs-create-channel-ltov"></a>

The channel is the first component in MediaPackage\. It represents the input to MediaPackage for incoming live content from an encoder such as AWS Elemental MediaLive\. 

MediaPackage does not require that you supply any customer data\. There are no fields in channels where there is an expectation that you will provide customer data\.

**To create a channel**

1. On the MediaPackage **Channels** page, choose **Create channel**\.

1. For **ID**, enter a name that describes the channel, such as **channelHLS1**\. The ID is the primary identifier for the channel, and must be unique for your account in the AWS Region\. Supported characters are letters, numbers, underscores \(\_\), and dashes \(\-\)\. You can't use spaces in the ID\.

1. Keep the defaults for the remaining fields, and then choose **Create**\.

   MediaPackage displays the new channel's details page\.

1. On the details page for the channel, note the values for **URL**, **Username**, and **Password**\. If you're using input redundancy, you need this information for both input URLs\. If you're sending only one stream to the channel, you can note the information for either input URL\. 

   MediaPackage securely generates the WebDAV user names and passwords when it creates the channel\. If you need to change these credentials, see [Rotating credentials on an input URL](channels-rotate-creds.md)\.

   Provide the information from these fields to the person in charge of the upstream encoder\. In the stream configuration in the encoder, this person must enter the destination as the input URL, and the WebDAV credentials as the channel's user name and password\. The upstream encoder must use digest authentication and push WebDAV over HTTPS to MediaPackage, and include these credentials\. If you're using input redundancy, the input streams to this channel must have identical encoder settings\. For more information about setting up source streams for input redundancy, see [Live input redundancy AWS Elemental MediaPackage processing flow](what-is-flow-ir.md)\.

## Create an endpoint<a name="gs-create-endpoint-ltov"></a>

The endpoint is attached to a channel, and represents the output of the live content\. When you create a harvest job to extract a VOD asset from the live content, you have to indicate what endpoint you're extracting from\. You can harvest assets from clear \(unencrypted\) or encrypted HLS and DASH endpoints, and the endpoint must have a startover window defined\. If you have only encrypted endpoints, see the [Creating live\-to\-VOD assets with AWS Elemental MediaPackage](ltov.md) feature reference\.

MediaPackage does not require that you supply any customer data\. There are no fields in endpoints where there is an expectation that you will provide customer data\.

**To create an endpoint**

1. On the **Channels** page, choose the channel that the endpoint will be associated with\.

1. On the details page for the channel, under **Origin endpoints**, choose **Manage endpoints**\.

1. For **ID**, enter a name that describes the endpoint, such as **HLSendpoint1**\. The ID is the primary identifier for the endpoint, and must be unique for your account in the AWS Region\. Supported characters are letters, numbers, underscores \(\_\), and dashes \(\-\)\. You can't use spaces in the ID\.

1. Keep the defaults for the remaining fields, and then choose **Save**\.

   MediaPackage displays the channel's details page, including the endpoint that you just created\.

1. On the details page for the channel, note the value in the **URL** field for the endpoint\. Provide this information to the person in charge of the downstream device \(CDN or player\)\. In the downstream device, this person must enter the request destination as the endpoint's URL\.