# Step 3: Create endpoints<a name="create-endpoint"></a>

The endpoint is attached to a channel, and represents the output of the live content\. You can associate multiple endpoints to a single channel\. Each endpoint gives players and downstream CDNs \(such as Amazon CloudFront\) access to the content for playback\. 

MediaPackage does not require that you supply any customer data\. There are no fields in endpoints where there is an expectation that you will provide customer data\.

**To create an endpoint**

1. On the **Channels** page, choose the channel that the endpoint will be associated with\.

1. On the details page for the channel, under **Origin endpoints**, choose **Manage endpoints**\.

1. For **ID**, enter a name that describes the endpoint, such as **HLSendpoint1**\. The ID is the primary identifier for the endpoint, and must be unique for your account in the AWS Region\. Supported characters are letters, numbers, underscores \(\_\), and dashes \(\-\)\. You can't use spaces in the ID\.

1. Keep the defaults for the remaining fields, and then choose **Save**\.

   MediaPackage displays the channel's details page, including the endpoint that you just created\.

1. On the details page for the channel, note the value in the **URL** field for the endpoint\. Provide this information to the person in charge of the downstream device \(CDN or player\)\. In the downstream device, this person must enter the request destination as the endpoint's URL\.