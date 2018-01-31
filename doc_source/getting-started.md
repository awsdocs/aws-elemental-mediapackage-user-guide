# Getting Started with AWS Elemental MediaPackage<a name="getting-started"></a>

This Getting Started tutorial shows you how to use the AWS Elemental MediaPackage console to create a channel and endpoints for streaming live videos\.


+ [Prerequisites](#create-iam)
+ [Step 1: Access AWS Elemental MediaPackage](#access-emp)
+ [Step 2: Create a Channel](#create-channel)
+ [Step 3: Create Endpoints](#create-endpoint)
+ [\(Optional\) Step 4: Monitor AWS Elemental MediaPackage Activity](#monitor-emp)
+ [Step 5: Clean Up](#clean-up)

## Prerequisites<a name="create-iam"></a>

Before you can use AWS Elemental MediaPackage, you need an AWS account and the appropriate permissions to access, view, and edit AWS Elemental MediaPackage components\. Complete the steps in [[ERROR] BAD/MISSING LINK TEXT](setting-up.md), and then return to this tutorial\.

## Step 1: Access AWS Elemental MediaPackage<a name="access-emp"></a>

Using your IAM credentials, sign in to the AWS Elemental MediaPackage console:

```
https://<region>.console.aws.amazon.com/mediapackage/home
```

## Step 2: Create a Channel<a name="create-channel"></a>

The channel is the first component in AWS Elemental MediaPackage\. It represents the input to AWS Elemental MediaPackage for incoming content from an encoder such as AWS Elemental MediaLive\. 

**To create a channel**

1. On the AWS Elemental MediaPackage **Channels** page, choose **Create channel**\.

1. For **ID**, type a name that describes the channel, such as **channelHLS1**\. The ID is the primary identifier for the channel, and must be unique for your account in the region\. Supported characters are letters, numbers, underscore \(\_\), and dash \(\-\)\. You cannot use spaces in the ID\.

1. Keep the defaults for the remaining fields, and then choose **Create channel**\.

   AWS Elemental MediaPackage displays the new channel's details page\.

1. On the channel's details page, note the values for **Input URL**, **Username**, and **Password**\. AWS Elemental MediaPackage securely generates these values when it creates the channel\. You can't change the values\. 

   Provide the information from these fields to the person in charge of the upstream encoder\. In the stream configuration in the encoder, this person must type the destination as the input URL, and the WebDAV credentials as the channel's user name and password\. The upstream encoder must push WebDAV over HTTPS to AWS Elemental MediaPackage, and include these credentials\.

## Step 3: Create Endpoints<a name="create-endpoint"></a>

The endpoint is attached to a channel, and represents the output of the content\. You can associate multiple endpoints to a single channel\. Each endpoint gives players and downstream CDNs \(such as Amazon CloudFront\) access to the content for playback\. 

**To create an endpoint**

1. On the **Channels page**, choose the channel that the endpoint will be associated with\.

1. On the details page for the channel, choose either **Add and edit endpoint** or **Add endpoints** if there are no existing endpoints\.

1. For **ID**, type a name that describes the endpoint, such as **HLSendpoint1**\. The ID is the primary identifier for the endpoint, and must be unique for your account in the region\. Supported characters are letters, numbers, underscore \(\_\), and dash \(\-\)\. You cannot use spaces in the ID\.

1. Keep the defaults for the remaining fields, and then choose **Save endpoints**\.

   AWS Elemental MediaPackage displays the channel's details page, including the endpoint that you just created\.

1. On the channel's details page, note the value in the **URL** field for the endpoint\. Provide this information to the person in charge of the downstream device \(CDN or player\)\. In the downstream device, this person must type the request destination as the endpoint's URL\.

## \(Optional\) Step 4: Monitor AWS Elemental MediaPackage Activity<a name="monitor-emp"></a>

Use Amazon CloudWatch to track AWS Elemental MediaPackage activity, such as the counts of ingest and egress bytes, response times, and request counts\.

**To view metrics using the CloudWatch console**  
Metrics are grouped first by the service namespace, and then by the various dimension combinations within each namespace\.

1. Open the CloudWatch console at [https://console.aws.amazon.com/cloudwatch/](https://console.aws.amazon.com/cloudwatch/)\.

1. In the navigation pane, choose **Metrics**\.

1. Under **All metrics**, choose the **AWS/MediaPackage** namespace\.

1. Select the metric dimension to view the metrics \(for example, choose `channel` to view metrics per channel\)\. For a list of AWS Elemental MediaPackage metrics, see [AWS Elemental MediaPackage CloudWatch Metrics](monitoring-cloudwatch.md#metrics)\.

## Step 5: Clean Up<a name="clean-up"></a>

To avoid extraneous charges, be sure to delete all unnecessary channels and endpoints\. You must delete all endpoints on a channel before the channel can be deleted\.

**To delete an endpoint**

1. On the **Channels page**, choose the channel that the endpoint is associated with\.

1. On the channel details page, choose the name of the endpoint to be deleted\.

1. On the endpoint details page, choose **Delete endpoint**\.

1. On the **Delete Endpoints** page, choose **Save all**\.

**To delete a channel**

1. On the **Channels** page, choose the channel using one the following methods: 

   + Choose the channel name

   + Select the check box next to the channel name

1. Choose **Delete selected** or **Delete channel**\.

1. In the confirmation dialog box, choose **Delete**\.

   AWS Elemental MediaPackage removes the channel and all associated endpoints\.