# Basic details<a name="hj-create-basic"></a>

The basic details of a harvest job define its identifier and the source for the live\-to\-VOD asset\.

1. For **ID**, enter a name that describes the harvest job\. The ID is the primary identifier for the harvest job\. You can reuse the ID when the harvest job expires from your account\. Supported characters are letters, numbers, underscores \(\_\), and dashes \(\-\)\.

1. For **Origin endpoint**, select the endpoint that serves the live stream that you're harvesting the live\-to\-VOD asset from\.

    Note the following considerations\. 
   + Your harvest job must fall within your MediaPackage endpoint's **startover window**\. The startover window determines the time frame that assets can be harvested from your endpoint\. For example, if your endpoint has a startover window of three days, you can harvest your asset anytime within that time frame\.

      A MediaPackage endpoint can have a startover window between zero and 14 days\. To adjust your endpoint's startover window, see [Viewing a single endpoint](endpoints-view-one.md)\. 
   + Your harvested live\-to\-VOD asset can have a maximum duration of 24 hours\. To set the live\-to\-VOD asset duration, see [Start and end date and time](hj-create-time.md) in this chapter\.
   + Your endpoint must serve either clear \(unencrypted\) or encrypted DASH or HLS content\.
   + MediaPackage VOD doesn't currently support the ingestion of encrypted assets\. If you're using your harvested assets in an MediaPackage video on demand workflow and your endpoint is encrypted, create an unencrypted shadow endpoint on the same channel\. To do this, deselect **allow origination** so that the new endpoint can't be used for playback\. MediaPackage creates the URL for endpoints that don't have origination enabled, but MediaPackage responds with an error to playback requests sent to this endpoint\. For more information, see [Creating live\-to\-VOD assets with AWS Elemental MediaPackage](ltov.md)\.