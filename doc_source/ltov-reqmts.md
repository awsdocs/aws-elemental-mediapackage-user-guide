# Live\-to\-VOD requirements<a name="ltov-reqmts"></a>

Keep in mind these requirements when you're creating live\-to\-VOD assets in AWS Elemental MediaPackage\.

**Endpoint requirements**  
The endpoint that you're harvesting the live\-to\-VOD asset from must meet these requirements:
+ It must have a **startover window** of 14 days or less\. To check or change the size of the window, see [Viewing a single endpoint](endpoints-view-one.md)\.
+ It must serve clear \(unencrypted\) HLS content\. If the live stream that you harvest from is served on an encrypted endpoint, create an identical, unencrypted endpoint on the same channel\. Disable **allow origination** so that the new endpoint can't be used for playback\. MediaPackage creates the URL for endpoints that don't have origination enabled, but MediaPackage responds with an error to playback requests sent to this endpoint\. For information about creating endpoints, see [Creating an HLS endpoint](endpoints-hls.md)\. 

**Live\-to\-VOD asset requirements**  
The live\-to\-VOD asset must meet these requirements:
+ Its start time must fall on or after the encoder's start time\.
+ Its start and end times must be within the startover window on the endpoint\.
+ Its duration must not exceed the maximum live\-to\-VOD manifest length\. For information about the maximum live\-to\-VOD manifest length, see [Live hard quotas](live-quotas.md#live-hard-quotas)\.